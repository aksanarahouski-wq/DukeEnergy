# Duke Energy Service Offerings Overview
### Duke Energy RS Home Services & Warranty Application
### Architecture & Product Reference

**Purpose:** Quick reference for understanding the two service models, the Duke vs. P&G distinction, and what each customer segment can access
**Author:** Aksana Rahouski, Product Manager (Orases)

---

## Two Categories of Service

Duke Residential Solutions offers two fundamentally different things:

---

### 1. Home Protection Plans (HPPs) — Monthly Subscriptions

These are **$9.99/month service contracts** — think of them like a home warranty. The customer pays monthly, and when something breaks, Duke sends a contractor to fix it at **$0 cost** to the customer.

#### Available Plan Types

| Plan | What It Covers | Customer Base |
|---|---|---|
| **Water Heater Repair** | Water heater repairs and replacements | **300K+ plans** — #1 most popular |
| **Home Wiring / Electrical (HomeWire)** | Outlets, switches, breaker panel, interior wiring | **300K+ plans** — #2 most popular |
| **Heating & Cooling (HVAC)** | Central AC, heat pumps, furnaces | High incident rate, growing |
| **Plumbing** | Pipes, fixtures, plumbing systems | Growing |
| **Appliance Repair** | Major home appliances | Growing segment |
| **Utility Line Protection** | Service lines from the street to the house | Covers lines Duke doesn't maintain |

#### Key Facts

- Customers average **1.7 plans each** — many stack multiple plans (e.g., water heater + HVAC + electrical)
- **1.5 million total active agreements** across 800K+ customers
- Billed directly on the utility bill (electric or gas) — no separate payment
- Covers **repairs and replacements only** — NOT preventative maintenance
- No deductible, no per-visit fee — unlimited service calls
- HPP plans are NOT insurance and NOT manufacturer warranties — they are service contracts covering normal wear and tear

#### What's Included vs. What's Not

- Unlimited service calls (no per-visit fee)
- Labor costs
- Parts costs (within coverage limits)
- Repair or replacement (if repair not feasible)
- **NOT included:** Preventative maintenance, pre-existing conditions, issues outside plan scope, cosmetic damage, negligence

---

### 2. Ad-Hoc Services — Pay-Per-Service (NEW — Does Not Exist Yet)

These are **one-time, pay-as-you-go services** that anyone can book — no Duke utility account or HPP plan required. This is the new revenue line Duke is building.

#### Examples Discussed in Discovery Sessions

| Service | Estimated Price | Type |
|---|---|---|
| HVAC seasonal tune-up | ~$99 | Flat rate |
| Water heater flush | TBD | Flat rate |
| General plumber visit | TBD | Hourly or flat rate |
| Ceiling fan installation | $120-$190 | Variable (range) |
| Appliance installation | TBD | Quote required |
| Preventative maintenance checks | TBD | Flat rate |

#### Key Facts

- This catalog **does not exist today** — it must be built from scratch
- Pricing is still being defined by Duke's business team
- Available to ALL customer types (Duke electric, P&G gas, and non-native)
- MVP payment: contractor collects on-site (cash, check, credit card via contractor's reader)
- Phase 2 payment: customer pre-pays in app (Stripe, Apple Pay, Google Pay)
- Starts with 5-10 services in 1-2 pilot markets
- Target: **$25M in new ad-hoc revenue within 12 months** of launch
- Target: **250K non-native customers within 24 months**

#### HPP Plans vs. Ad-Hoc Services Side by Side

| Aspect | HPP Plans | Ad-Hoc Services |
|---|---|---|
| **Customer type** | Native Duke/P&G customers with active plans | Any customer — Duke, P&G, or non-native |
| **Pricing model** | $9.99/month subscription (billed on utility bill) | Pay-per-service (flat rate, range, or quote) |
| **Service trigger** | Something breaks — problem/repair needed | Any need — maintenance, repair, installation |
| **Customer pays at service** | $0 (covered by subscription) | Full price |
| **Payment method** | Utility bill (monthly subscription) | Credit card, cash, check (MVP: contractor collects) |
| **Coverage limits** | Yes (per plan rules) | No limits — customer pays full amount |
| **Scope** | Repairs and replacements only | Any service (maintenance, repair, replacement, tune-up) |
| **Exists today** | Yes — 1.5M active agreements | No — must be built from scratch |
| **MVP status** | Core MVP feature | Core MVP feature |

---

## Duke Electric Customers vs. P&G Gas Customers

Behind the scenes these are **two different CRM systems**, but from the customer's perspective there is no difference.

| | Duke Electric Customers | Piedmont Natural Gas (P&G) Customers |
|---|---|---|
| **Utility service** | Electricity | Natural gas |
| **CRM system** | SAP Commerce (Hybris) | Microsoft Dynamics |
| **HPP plans available** | All plan types | All plan types |
| **Plan pricing** | Same ($9.99/month) | Same ($9.99/month) |
| **Billing** | Added to electric bill | Added to gas bill |
| **Contractor network** | Same shared network | Same shared network |
| **App experience** | Identical | Identical |
| **Customer validation API** | Commerce API | Dynamics API |
| **Service order system** | Dynamics | Dynamics |

As Son Gandara stated in the discovery sessions: *"You can say Duke and P&G anonymously."* The distinction is purely a backend integration concern — our API checks Commerce for Duke electric customers and Dynamics for P&G gas customers, but the customer never sees this difference.

**Important edge case:** Some customers are **both** — they have Duke electricity AND Piedmont gas at the same address, with HPP plans through both systems. The app must aggregate plans from both Commerce and Dynamics into a single unified view per property.

---

## The Three Customer Segments and What's Available to Each

| | HPP Customer (Duke or P&G) | Utility Customer Without HPP | Non-Native Customer |
|---|---|---|---|
| **Who they are** | Have electric/gas utility account AND at least one HPP plan | Have electric/gas utility account but NO HPP plans | Not a Duke or P&G utility customer at all |
| **Estimated size** | 800K+ customers, 1.5M agreements | Millions of Duke/P&G utility customers | Unlimited — any U.S. homeowner |
| **HPP covered services** | Yes — $0 at time of service | No — they have no plans | No — not eligible |
| **Ad-hoc services** | Yes — can also book pay-per-service | Yes — this is their primary path | Yes — this is their only path |
| **HPP enrollment** | Can manage existing plans, add more | Can enroll in plans (Phase 1+) | Cannot enroll (MVP). Future: TBD |
| **Payment for HPP** | Already paying via utility bill | Utility bill upon enrollment | N/A |
| **Payment for ad-hoc (MVP)** | Contractor collects on-site | Contractor collects on-site | Contractor collects on-site |
| **Payment for ad-hoc (Phase 2)** | Credit card, Apple Pay, or add to utility bill | Credit card, Apple Pay, or add to utility bill | Credit card or Apple Pay only. No utility bill option. |
| **Home inventory** | Yes | Yes | Yes |
| **Maintenance reminders** | Yes | Yes | Yes |
| **DIY content** | Yes | Yes | Yes |
| **Loyalty / gamification** | Yes | Yes | Yes |
| **Data source of truth** | Commerce/Dynamics for identity + plans. Our DB for inventory, preferences, loyalty. | Commerce/Dynamics for identity. Our DB for everything else. | Our DB for everything. Duke systems have no record. |
| **Persona** | "Established Eleanor" — 58, has water heater + HVAC plans, frustrated with phone-only service | "Expanding Emma" — 34, first-time homeowner, considering HPP enrollment | "Non-Native Nathan" — 41, not a Duke customer, found app via Google, wants reliable plumber |

---

## How This Maps to the Architecture

### Registration Flow Differs by Customer Type

**Duke/P&G customer registers:**
1. Enters email, password, name, address
2. Our API calls Commerce validation API (Duke electric) AND Dynamics validation API (P&G gas)
3. Match found → `customer_type: duke_native` or `pg_native`
4. `external_customer_id` populated with Business Partner ID
5. HPP plans cached from CRM into our database
6. Customer sees: "Welcome! You have 2 HPP plans linked to your account."

**Non-native customer registers:**
1. Enters email, password, name, address
2. Our API calls Commerce AND Dynamics — no match found
3. `customer_type: non_native`
4. `external_customer_id: NULL`
5. No HPP plans to display
6. Customer sees: "Welcome! Browse available services in your area."

### Service Booking Flow Differs by Service Type

**HPP-covered booking:**
1. Customer selects issue → coverage check against cached HPP plans
2. Covered → contractor auto-assigned (trade + zip code), $0 price
3. Service request created in our DB + synced to Dynamics (or admin manually enters)

**Ad-hoc booking:**
1. Customer browses catalog → selects service → sees flat-rate price
2. Contractor auto-assigned (same algorithm: trade + zip code)
3. Price displayed: "$99 — payment collected by contractor at service completion"
4. Service request created in our DB

### Data Storage Differs by Customer Type

| Data | HPP Customer | Utility Customer (No HPP) | Non-Native |
|---|---|---|---|
| Identity | Commerce/Dynamics (source of truth) + cached in our DB | Commerce/Dynamics + cached in our DB | Our DB only (we are source of truth) |
| HPP plans | Commerce/Dynamics → cached in our DB | None | None |
| Home inventory | Our DB (new entity, not in Duke systems) | Our DB | Our DB |
| Service requests | Our DB + synced to Dynamics | Our DB + synced to Dynamics | Our DB (sync to Dynamics TBD — see Non-Native Data Ownership doc) |
| Loyalty / gamification | Our DB | Our DB | Our DB |

---

## The Bottom Line

**HPP plans are the existing business** — 800K customers paying $9.99/month, 1.5M active agreements, recurring revenue that funds the platform.

**Ad-hoc services are the growth play** — $25M revenue target, 250K new non-native customers, proving the platform works beyond Duke's utility footprint and enabling white-label licensing to other utilities.

**The app must serve both from Day 1.** Every architectural decision, every screen, every API endpoint must account for the fact that some users have HPP plans and pay $0, while others are browsing a service catalog and paying per visit. The customer type determines what they see, what they can do, and how data flows through the system.

---

*Source: HPP Plans Explained, Customer App Scope (Sections 1-5), Admin Portal Scope (Section 4: Workflows), Discovery Session transcripts (Kevin Oppermann, Son Gandara, Dana DeRemigis quotes)*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
