# White-Label Multi-Tenancy Strategy
### Duke Energy RS Home Services & Warranty Application
### Architecture Decision Reference

**Status:** Confirmed — build multi-tenant from Day 1
**Related:** Initial Solution Architecture (Principle #6), Proposal (Section B: White-Label Platform Foundation)
**Author:** Aksana Rahouski, Product Manager (Orases)

---

## What White-Label Means

White-labeling means taking the same software platform and rebranding it for a different company — so they can offer it as if it were their own product.

**In Duke's context:** Duke wants the option to license this home services app to **other utility companies** in the future. Imagine Florida Power & Light, or Dominion Energy, or any other utility saying "we want the same app Duke has, but with our logo, our colors, our contractors, and our customers."

Instead of rebuilding the app from scratch for each utility, you reskin the same platform:

| | Duke Energy Version | Florida Power & Light Version |
|---|---|---|
| Logo | Duke Energy logo | FPL logo |
| Colors | Duke blues/greens | FPL blues/oranges |
| App name | "Duke Home Services" | "FPL Home Services" |
| Contractors | 125 contractors in NC, SC, FL, OH, IN | Different contractors in FL |
| HPP Plans | Duke's plan catalog and pricing | FPL's plan catalog and pricing |
| Customers | Duke's 800K+ customers | FPL's customers |
| **Codebase** | **Same** | **Same** |
| **Backend** | **Same** | **Same** |
| **Database** | **Same (but data isolated)** | **Same (but data isolated)** |

---

## Why Duke Cares

From the Orases proposal (Section B):

> **White-Label Platform Foundation**
> *Business Need:* Future expansion to other utilities requires scalable architecture
> *Our Solution:* Multi-tenant platform design from Day 1 to support future white-labeling

Duke sees this as a revenue opportunity. If the platform works well for Duke, they can license it to other utilities. That is a new business line for Duke Residential Solutions beyond just their own customers.

The 250K non-native customer acquisition goal is also related. Non-native customers prove the platform works outside Duke's utility territory. That proof of concept is what makes white-labeling attractive to other utilities.

---

## What "From Day 1" Means Technically

It means the `tenant_id` column. Every table in the database has a `tenant_id` field that scopes all data to a specific utility company.

### Without Multi-Tenancy (Built Later — The Expensive Way)

If the team builds the app assuming Duke is the only customer, the code looks like this everywhere:

```sql
-- Get all contractors
SELECT * FROM contractors WHERE active = true;

-- Get all service requests
SELECT * FROM service_requests WHERE user_id = 123;
```

Every query, every API endpoint, every admin screen assumes there is one universe of data. When you later try to add FPL as a second tenant, you have to:

1. Add `tenant_id` to every single table (database migration on live production data)
2. Modify every single query to filter by `tenant_id`
3. Modify every API endpoint to scope by tenant
4. Modify every admin screen to show only that tenant's data
5. Test everything again to make sure Duke's data does not leak to FPL and vice versa

**This takes 3-6 months of rework and is one of the most dangerous refactors you can do on a live system** — because if you miss one query, one customer sees another utility's data. That is a data breach.

### With Multi-Tenancy from Day 1 (The Right Way)

The team builds it correctly from the start:

```sql
-- Get all contractors (always scoped)
SELECT * FROM contractors WHERE tenant_id = 'duke' AND active = true;

-- Get all service requests (always scoped)
SELECT * FROM service_requests WHERE tenant_id = 'duke' AND user_id = 123;
```

Every query, every API call, every screen is **automatically scoped** to the current tenant. The code does not know or care whether there is 1 tenant or 50 — it works the same way.

---

## What It Costs

### To Build From Day 1: ~3-5% Additional Effort

- Add a `tenants` table with brand configuration
- Add `tenant_id` as a foreign key on every table
- Add a Laravel global scope that automatically filters every query by the authenticated user's tenant
- Store brand config (logo URL, primary color, app name) in the tenants table
- Load brand config at app startup to render the correct look

The developer writes `Contractor::where('active', true)->get()` and Laravel automatically adds `AND tenant_id = 'duke'` behind the scenes. They do not even think about it day-to-day.

### To Retrofit Later: 3-6 Months of Rework

- Touch every table, every query, every endpoint, every screen
- Risk data leakage between tenants during migration
- Requires full regression testing of every feature
- Cannot be done incrementally — it is all-or-nothing
- Production data must be migrated with zero downtime

**The math is clear: spend 3-5% more now, or spend 3-6 months later.**

---

## What Gets Configured Per Tenant

The `tenants` table stores a brand configuration that controls everything visual and business-specific:

```
TENANTS table:

  tenant_id: "duke"
  name: "Duke Energy Residential Solutions"
  brand_config: {
    "logo_url": "https://cdn.../duke-logo.png",
    "primary_color": "#00A3E0",
    "secondary_color": "#8CC63F",
    "app_name": "Duke Home Services",
    "support_phone": "1-800-XXX-XXXX",
    "support_email": "support@duke-energy.com",
    "app_store_url": "https://apps.apple.com/...",
    "play_store_url": "https://play.google.com/...",
    "privacy_policy_url": "https://duke-energy.com/privacy",
    "terms_url": "https://duke-energy.com/terms"
  }
  domain: "dukehomeservices.com"
  active: true
```

When FPL wants to launch, you create a new row:

```
  tenant_id: "fpl"
  name: "FPL Home Services"
  brand_config: {
    "logo_url": "https://cdn.../fpl-logo.png",
    "primary_color": "#003DA5",
    "secondary_color": "#F7941D",
    "app_name": "FPL Home Services",
    "support_phone": "1-800-XXX-YYYY",
    "support_email": "support@fpl.com",
    ...
  }
  domain: "fplhomeservices.com"
  active: true
```

The app reads this config at startup and renders accordingly. Same binary, different appearance.

---

## What Is Tenant-Scoped vs. What Is Shared

### Scoped Per Tenant (Data Isolation Required)

| Entity | Why Isolated |
|---|---|
| Users / Customers | Duke customers must never see FPL data and vice versa |
| Properties | Belong to customers, scoped by tenant |
| Home Inventory | Belongs to customers, scoped by tenant |
| HPP Plans (cached) | Different plans, different pricing per utility |
| Service Requests | Tenant's contractors, tenant's customers |
| Contractors | Each utility has its own contractor network |
| Contractor Trade Assignments | Different zip codes, different designations per tenant |
| Ad-Hoc Service Catalog | Different services, different pricing per utility |
| Reminders | May be customized per tenant |
| Loyalty / Gamification | Different point values, different badges per tenant |
| Admin Users | Each utility has its own admin staff |
| Notifications | Sent to that tenant's customers only |
| Escalation Tickets | That tenant's issues only |
| Enrollment Queue | That tenant's pending enrollments |

### Potentially Shared Across Tenants

| Entity | Why Shared |
|---|---|
| DIY Content | Generic home maintenance content could be shared, with tenant-specific content layered on top |
| Barcode / Product Database | Appliance data is universal (a Carrier HVAC is a Carrier HVAC regardless of which utility's app you use) |
| CPSC Recall Data (Phase 2) | Federal recall database is the same for everyone |
| App Infrastructure | Same servers, same database, same codebase |

---

## How It Works in the App (React Native + Vue.js)

### App Startup Flow

```
1. App launches
2. User logs in → JWT token includes tenant_id
3. App calls GET /config → returns brand_config for user's tenant
4. App applies brand config:
   - Logo rendered from brand_config.logo_url
   - Primary color applied to buttons, headers, accents
   - App name displayed in headers and notifications
   - Support contact info populated from config
5. All subsequent API calls automatically scoped by tenant
   (Laravel reads tenant_id from JWT, applies global scope)
```

### What the Developer Experience Looks Like

A developer building a new feature (e.g., adding contractor performance ratings) writes:

```php
// Laravel controller — developer does NOT think about tenants
public function index()
{
    $contractors = Contractor::where('active', true)
        ->with('tradeAssignments')
        ->get();

    return ContractorResource::collection($contractors);
}
```

Behind the scenes, Laravel's `TenantScope` automatically transforms this into:

```sql
SELECT * FROM contractors
WHERE tenant_id = 'duke'   -- auto-added by global scope
AND active = true;
```

The developer never writes `tenant_id` in their query. The framework enforces it. This eliminates the risk of accidentally returning another tenant's data.

---

## What Changes When a New Tenant Onboards

| Step | Who Does It | Time |
|---|---|---|
| 1. Create tenant record with brand config | Orases super admin | 1 hour |
| 2. Create admin user accounts for new utility | Orases super admin | 1 hour |
| 3. Import contractor data (CSV) | New utility provides, Orases imports | 1-2 days |
| 4. Configure trade/zip code assignments | New utility's ops team via admin portal | 1-2 days |
| 5. Define HPP plan catalog (or equivalent) | New utility provides | 1-2 weeks |
| 6. Configure integration with new utility's CRM | Orases dev team | 2-4 weeks (depends on their API) |
| 7. Create branded app store listing | Orases + new utility marketing | 1-2 weeks |
| 8. Submit to App Store / Play Store | Orases | 1-2 weeks |

**Steps 1-5 require zero code changes.** Step 6 is the only engineering work — integrating with the new utility's customer validation and plan management APIs.

---

## Instructions for Dev Team

Three non-negotiable requirements:

### 1. Every Database Table Must Have `tenant_id`

No exceptions. Even if we only have one tenant at launch. The column exists, the foreign key exists, the index exists.

### 2. Laravel Global Scopes Must Enforce Tenant Isolation

Every Eloquent model gets a `TenantScope` that auto-filters by the authenticated user's tenant. A developer should never have to manually add `WHERE tenant_id = X` — the framework does it. If a developer forgets, the scope catches it.

```php
// Applied to every model
class TenantScope implements Scope
{
    public function apply(Builder $builder, Model $model)
    {
        $builder->where('tenant_id', auth()->user()->tenant_id);
    }
}
```

### 3. Brand Config Is Data, Not Code

Logos, colors, app names, support phone numbers — all stored in the database, not hard-coded. Changing the branding for a new tenant should never require a code deploy. The app reads config from the API and renders dynamically.

---

## Risk If We Skip This

If the team builds without `tenant_id` and we need to add white-label support in Phase 2:

- **3-6 months of rework** — touching every table, query, endpoint, and screen
- **Data breach risk** — if one query is missed during migration, Tenant A sees Tenant B's data
- **Production downtime risk** — database migration on live data with 800K+ customers
- **Duke's white-label roadmap is delayed by 6+ months**
- **Proposal commitment is broken** — the proposal explicitly promised "multi-tenant platform design from Day 1"

---

*Source: Orases Proposal (Section B: White-Label Platform Foundation), Initial Solution Architecture (Principle #6, Section 13), SOW #1 V6*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
