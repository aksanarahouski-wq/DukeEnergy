# Discovery Plan: Deliverable #1
## Customer Registration, Onboarding & Customer Management
### Duke Energy RS Home Services & Warranty Application

**Author:** Aksana Rahouski, Product Manager (Orases)
**Created:** March 19, 2026
**Status:** Draft — Internal Discovery Planning
**Produces:** PRD (post-discovery), Data Model, Admin Spec, Data Sync Decision Matrix

---

## How We Think About Deliverables

A deliverable is NOT a single feature on one screen. A deliverable is a **vertical slice** — the full stack of what must be defined, designed, and built to deliver one unit of value:

```
┌─────────────────────────────────────────────────────┐
│  DELIVERABLE = VERTICAL SLICE                       │
│                                                     │
│  Customer Experience  →  What does the user see/do? │
│  Admin Experience     →  What does admin see/do?    │
│  Data Model           →  What do we store and where?│
│  Data Sync            →  What moves between systems?│
│  Business Rules       →  What logic governs this?   │
│  Integration          →  What APIs are involved?    │
│  Design               →  What screens exist?        │
│                                                     │
│  Discovery defines ALL of these together.           │
│  The PRD is an OUTPUT of discovery, not an input.   │
└─────────────────────────────────────────────────────┘
```

The sample PRDs in the repository were earlier working drafts. They are reference material, not approved scope. Discovery produces the real PRDs.

---

## What This Deliverable Covers

Registration and onboarding is not just "user creates an account." It's the full **customer identity foundation** for the platform. This deliverable defines and builds:

1. **Registration** — How does a user create an account? What's different for Duke/P&G customers vs. non-native?
2. **Customer Profile** — What data do we store? What does the user see when they log in? What's visible Day 1 before they've done anything else?
3. **Customer Management (Admin)** — Every registered user appears in the admin tool. What can admins see, search, edit? What actions can they take?
4. **Data Sync Strategy** — Our database now holds customer data. What syncs to Duke? What syncs from Duke? Is it bi-directional? What happens when data changes on either side?

These four pieces are inseparable. You can't build registration without deciding what the admin sees. You can't build the admin view without deciding what data syncs where. Discovery covers all four in the same session.

---

## Part 1: Registration & Onboarding Experience

### What We Know From Preliminary Scope (Reference, Not Final)

Three registration paths exist based on customer type:

| Path | Who | What Happens |
|---|---|---|
| **Duke Native** | Has Duke electric utility account | Registers → API validates against Commerce → Business Partner ID linked → HPP plans cached → customer_type: duke_native |
| **P&G Native** | Has Piedmont Natural Gas account | Registers → API validates against Dynamics → Business Partner ID linked → HPP plans cached → customer_type: pg_native |
| **Non-Native** | No Duke/P&G utility account | Registers → API checks Commerce AND Dynamics → no match → customer_type: non_native → no plans, no external ID |

Edge case: some customers are BOTH Duke electric AND Piedmont gas at the same address. App must aggregate plans from both systems.

Multi-property support is required from Day 1. Guest access for browsing without an account was discussed.

### What Discovery Must Define

#### Registration Flow

| # | Question | Why It Matters | Who Answers |
|---|---|---|---|
| 1 | What exact fields does the Duke Enterprise validation API accept and return? | Determines what we can pre-fill and what we store | Duke IT |
| 2 | Can we validate by address alone, or do we need account number + name? | Account number = more accurate but higher friction. Address-only = easier but more false negatives. Changes the entire registration UX. | Duke IT + Product Owner |
| 3 | What happens if a customer enters an address that matches a Duke account but the name doesn't match? (Spouse, roommate, new owner) | Common scenario. Do we link? Ask for verification? Reject? | Duke Product Owner + IT |
| 4 | What happens if the Duke API is down during registration? | Fallback options: register without validation and queue for retry, or block registration entirely? | Orases Tech Lead + Duke IT |
| 5 | For P&G customers, is the Dynamics validation API the same contract as Commerce, or completely different? | If different, we need two separate integration implementations | Duke IT |
| 6 | What is the password policy? Duke corporate (12+ chars) or consumer-friendly (8+ chars)? | Security vs. conversion rate. A 12-char requirement will reduce registration completion. | Duke Security + Product Owner |
| 7 | Social login (Google/Apple) — in MVP or deferred? | Reduces friction significantly for non-native customers. But adds complexity. | Duke Product Owner |
| 8 | MFA — in MVP or deferred? | Security posture decision | Duke Security |
| 9 | What does the verification email look like? Duke-branded? What sender domain? | Requires marketing + legal input. Sender domain affects deliverability. | Duke Marketing + Legal |
| 10 | What minimum data is required at registration vs. collected later (progressive profiling)? | Fewer fields = higher completion rate. But we may need certain fields for downstream features. | Duke Product Owner + Orases PM |

#### Onboarding Flow (Post-Registration)

| # | Question | Why It Matters | Who Answers |
|---|---|---|---|
| 11 | After registration, what does the user see? Empty home screen? Guided setup? Something else? | Defines the "first 60 seconds" experience — critical for retention. The app is mostly empty at this point. | Duke Product Owner + Orases UX |
| 12 | For a Duke customer with HPP plans, do we show the linked plans immediately? | Seeing linked plans builds trust ("it worked!"). But where? Same screen? Separate tab? | Orases UX + Duke Product Owner |
| 13 | For a non-native customer, what's the first call-to-action? | Non-native users have nothing linked — we need to drive them somewhere valuable or they'll leave. | Duke Product Owner |
| 14 | Multi-property: how does the user switch between properties? | Dropdown in header? Separate tab? Setting? This decision affects every screen in the app. | Orases UX |
| 15 | Do we prompt for home inventory during onboarding, or is that a separate entry point? | If yes, onboarding gets longer but engagement increases. If no, user needs to find inventory on their own. | Duke Product Owner |

---

## Part 2: Customer Profile — What the User Sees

### The "Day 1" Problem

When a user registers and logs in for the first time, they haven't done anything yet. No service bookings. No inventory. No loyalty points. The profile is mostly empty.

**Available at registration (all types):**
- Name, email, phone
- Home address(es)
- Property type (if entered)
- Customer type (Duke/P&G/Non-Native — but we probably don't show this label)
- Account creation date

**Additional data for Duke/P&G customers (from API):**
- Active HPP plans (plan name, status, coverage details)
- Utility account linkage confirmation

**NOT available Day 1 (comes from other deliverables):**
- Home inventory, service history, loyalty points, payment methods, maintenance reminders

### What Discovery Must Define

| # | Question | Why It Matters | Who Answers |
|---|---|---|---|
| 16 | What does the profile/account screen look like at Day 1? | Designing a screen that's mostly empty for new users — needs to feel complete, not broken | Orases UX + Duke Product Owner |
| 17 | For Duke/P&G customers, do we show utility account details (account number, service address per plan) or just the plan names? | Privacy consideration — some customers may not want account numbers visible | Duke Product Owner + Security |
| 18 | Can users edit their own profile data (name, phone, email, address)? | If yes, what happens on the backend? Does the change need to push back to Duke? (See Part 4) | Duke Product Owner |
| 19 | What happens when a user changes their address? | Major implications: new address may match a different Duke account, plans are address-specific, contractor zip code matching changes | Duke Product Owner + Orases Tech Lead |
| 20 | Can users delete their account? | GDPR/CCPA compliance. If yes, what happens to their data in Duke's systems? Do we hard-delete or soft-delete? | Duke Legal + IT |
| 21 | Profile completion percentage — do we show this from Day 1 as an incentive to build out their profile (inventory, etc.)? | Gamification hook — but needs to be designed into the profile from the start | Duke Product Owner |

---

## Part 3: Customer Management — Admin Tool

### Why This Is Part of Deliverable #1

The moment registration goes live, the admin tool must be ready. Support agents need to:
- Look up customers who call with problems ("I can't log in," "My plans didn't link")
- See what the customer sees (their profile, plans, properties)
- Take actions on their behalf (reset password, unlock account, manually link plans)
- Handle the manual enrollment queue (registrations where Duke API was unavailable)

If we build registration without admin, there's no way to support the customer base on Day 1.

### What the Admin Needs to Do with Customer Data

**Search and find customers:**
- By email, phone, name, address, Duke Business Partner ID
- Filter by customer type, verification status, registration date

**View customer profiles:**
- Everything the customer sees on their own profile
- Plus internal fields: customer_type, external_customer_id, premise_id(s), sync status, last login, email verification status
- Plus activity log: when they registered, verified email, edited profile, logged in

**Take actions:**

| Action | Description | Sync Question |
|---|---|---|
| Reset password | Send password reset email | No sync — our auth system only |
| Unlock account | Unlock after too many failed login attempts | No sync |
| Edit profile (name, phone) | Update customer record in our database | **Does this push to Duke?** |
| Edit address | Update property record | **Does this trigger re-validation? Change contractor matching?** |
| Manually link Duke account | Set duke_customer_id, pull HPP plans | Writes to our DB only |
| Change customer type | e.g., non_native → duke_native (conversion) | **Does Duke need to know?** |
| Process enrollment queue | Validate customer in CRM when API was down during their registration, then link in our system | Admin works in both CRM + our backend |
| Deactivate account | Customer can't log in | **Delete our data? Notify Duke? GDPR?** |
| Create account for caller | Phone registration — agent creates account on behalf of customer calling in | Common call center scenario |

### What Discovery Must Define

| # | Question | Why It Matters | Who Answers |
|---|---|---|---|
| 22 | Which admin roles need access to customer management? | Determines permission model. Not everyone should edit profiles. | Duke Ops Team |
| 23 | Can admins edit a customer's name or contact info? If yes, does it push back to Duke? | If we change a phone number but Duke CRM still has the old one, data diverges | Duke Product Owner + IT |
| 24 | Can an admin create a customer account on behalf of a phone caller? | Call center agents currently handle everything by phone. Do they keep doing registration by phone, or do they create app accounts? | Duke Ops Team |
| 25 | What internal fields should admins see that customers should NOT see? | Business Partner ID, premise ID, customer_type flag, sync timestamps — these are operational | Duke Product Owner |
| 26 | What does the manual enrollment queue workflow look like? How often does the Duke API go down? How many queued registrations do we expect? | Sizes the admin workload. If it's 5/day, it's manual. If it's 500/day, we need automation. | Duke Ops + IT |
| 27 | Does Duke want registration analytics from Day 1? (New accounts/day, by type, by region) | If yes, needs to be in the admin dashboard alongside customer management | Duke Product Owner |
| 28 | How does Duke's call center currently handle account/registration issues? | Understanding the current workflow helps us design the admin tool to match or improve it | Duke Ops Team |
| 29 | What is the expected admin user count? 5 admins? 50? 500? | Affects admin tool design (simple list vs. advanced search + roles) | Duke Ops Team |

---

## Part 4: Data Sync Strategy

### The Core Problem

Once we store customer data, multiple systems know about the same customer:

```
Duke/P&G Customer:
  Commerce (Duke electric) ← Source of truth for utility identity + HPP plans
  Dynamics (P&G gas)       ← Source of truth for gas identity + HPP plans
  Our Database             ← Source of truth for app profile, preferences, inventory, loyalty

Non-Native Customer:
  Our Database             ← ONLY source of truth. Duke systems have no record.
```

### Sync Scenarios — Each Needs a Decision

#### Scenario 1: Customer Updates Profile in Our App

Customer changes their phone number in the app.

| Option | Description | Tradeoff |
|---|---|---|
| **A: No sync** | Phone changes in our DB only. Duke CRM keeps old number. | Simple. But if customer calls Duke, call center sees old data. |
| **B: Push to Duke** | We update our DB AND push to Commerce/Dynamics via API. | Consistent. But requires Duke to have a write API we can call. |
| **C: Notify Duke** | We update our DB. Send notification/report to Duke: "These customers changed data." Duke updates CRM manually. | Middle ground. Duke controls their CRM. But manual process. |

**Key question:** Does Duke have (or plan to have) an API that accepts customer profile updates from external systems?

#### Scenario 2: Customer Updates Profile at Duke (Calls Duke, Updates in CRM)

Customer calls Duke and changes their address. Duke CRM has the new address. Our database still has the old one.

| Option | Description | Tradeoff |
|---|---|---|
| **A: No sync** | Our DB keeps old address until customer manually updates in app. | Simple. But customer sees stale data. |
| **B: Nightly sync** | Batch job pulls latest customer data from Duke API daily. | Eventually consistent (up to 24 hours stale). Requires Duke "get customer updates" API. |
| **C: Sync on login** | When customer opens app, we refresh their profile from Duke API. | Fresh data every session. Adds latency. Requires reliable API. |
| **D: Event-driven** | Duke pushes webhook when data changes. We update immediately. | Best UX. Most complex. Unlikely for MVP. |

**Key question:** Does Duke expect their CRM to remain the source of truth for customer identity data?

#### Scenario 3: Non-Native Customer Data — Does Duke Ever Get It?

Non-native customers exist only in our database. Commerce and Dynamics have no record.

| Option | Description | Tradeoff |
|---|---|---|
| **A: Never sync** | Our DB is sole source of truth. Duke gets aggregate dashboards only. | Simplest. But Duke can't reach these customers through their CRM. |
| **B: Push to Duke CRM** | Create a customer record in Dynamics on registration. | Duke has complete view. But CRM may not support records without utility accounts. |
| **C: Sync on first booking** | Don't sync at registration. Push to Duke only when customer books a service (Duke needs it for invoicing/revenue). | Pragmatic. Only syncs revenue-generating customers. But partial data. |

**Key question:** Already raised in the Non-Native Customer Data Ownership doc. Decision needed by Week 4 of development.

#### Scenario 4: Non-Native Customer Becomes a Duke Customer

Nathan (non-native) moves to Duke territory and gets a utility account.

**What should happen:**
1. Nathan's address changes (in app or Duke detects him)
2. Re-validation finds a Commerce match
3. customer_type → duke_native, Business Partner ID linked
4. HPP plans linked
5. All existing app data (inventory, history, loyalty) carries over

**Key question:** Is this automatic (re-validate on address change) or manual (customer contacts support)? Does Duke notify us when non-native customers enter their territory?

#### Scenario 5: Source of Truth Per Data Field

| Data Field | Source of Truth | Sync Direction | Discovery Decision Needed |
|---|---|---|---|
| Name | Duke CRM (native) / Our DB (non-native) | TBD | If customer changes name in app, does it go to Duke? |
| Email | Our DB (app login credential) | None | Our email may differ from Duke's email on file. Is that OK? |
| Phone | TBD | TBD | Which system is authoritative? |
| Home address | Duke CRM (native) / Our DB (non-native) | TBD | Address changes affect contractor matching + plan eligibility |
| Customer type | Our DB (derived from validation) | None outbound | We determine type; Duke doesn't consume this |
| Business Partner ID | Duke CRM | Duke → Us (read-only) | We never write this back |
| Premise ID | Duke CRM | Duke → Us (read-only) | We never write this back |
| HPP Plans | Duke CRM | Duke → Us (periodic refresh) | How often do we refresh cached plans? On login? Nightly? |
| Communication preferences | Our DB | None | App-only setting |
| Home inventory | Our DB | None (MVP) | New entity. Does not exist in Duke systems. |
| Loyalty points | Our DB | None | App-only feature |

---

## Part 5: What "Done" Looks Like

### For the Customer

After this deliverable ships, a customer can:
- Download the app and create an account (< 3 minutes)
- See their linked HPP plans if they're a Duke/P&G customer
- See a welcome experience if they're non-native
- Add multiple properties to their profile
- View and edit their profile
- Log in, log out, reset password, verify email
- See a home screen with navigation to features not yet built (behind feature flags or "coming soon")

**What they CANNOT do yet** (requires later deliverables):
- Book a service
- Add home inventory
- Enroll in or manage HPP plans
- Browse ad-hoc services
- Earn loyalty points

The app after Deliverable #1 is intentionally limited. Registration creates the user identity foundation. Everything else builds on it.

### For the Admin

After this deliverable ships, an admin can:
- Search for any registered customer
- View full customer profile (app data + Duke-linked data + internal fields)
- Filter and sort the customer list
- Reset passwords, unlock accounts
- Edit customer profiles (scope TBD — depends on sync decisions)
- Process the manual enrollment queue
- Create accounts on behalf of phone callers (if confirmed)
- View registration analytics

### Data Model Established

These core tables exist and are populated:
- **users** — All registered customers with customer_type, external IDs
- **properties** — Customer properties with Duke premise mapping
- **hpp_plans** — Cached HPP plan data from Duke (for native customers)
- **admin_users** — Admin accounts with roles and permissions
- **activity_log** — Customer and admin action tracking

### What Gets Produced After Discovery

Discovery for Deliverable #1 produces:
1. **PRD** — The real PRD, written from confirmed discovery decisions (not a sample)
2. **Data Model** — Finalized table definitions, field types, relationships
3. **Data Sync Decision Matrix** — Confirmed sync direction per field, with justification and fallback
4. **Admin Customer Management Spec** — Search, view, edit, actions, permissions, workflows
5. **Registration Flow Diagrams** — All paths with confirmed steps, decision points, error handling
6. **API Dependency Document** — What we need from Duke IT, status, fallbacks
7. **Design Brief** — Screen inventory, key interactions, content needs for wireframes
8. **Open Questions & Action Items** — With owners and deadlines

---

## Discovery Session Plan

### Session Structure (Estimated 3 Hours)

| Block | Time | Topic | Focus |
|---|---|---|---|
| **1. Registration Flow** | 45 min | Walk through all 3 registration paths. Confirm steps, fields, edge cases. Decide account number vs. address-only validation. Discuss progressive profiling. | Questions 1-15 |
| **2. Duke API Deep Dive** | 30 min | API spec review: request format, response fields, error codes, SLAs, sandbox access. Commerce vs. Dynamics differences. Timeout and fallback handling. | Questions 1-5 (technical depth) |
| **3. Customer Profile & Day 1 Experience** | 30 min | What does the user see after registration? Profile screen content. Multi-property UX. What's editable. What's visible vs. hidden. | Questions 16-21 |
| **4. Admin Customer Management** | 30 min | Admin search, view, edit capabilities. Manual enrollment queue. Role permissions. Phone registration workflow. Current call center process. | Questions 22-29 |
| **5. Data Sync Strategy** | 30 min | Walk through 5 sync scenarios. Get decisions on direction per data field. Non-native data ownership. Source-of-truth matrix. | Scenarios 1-5 |
| **6. Open Questions & Actions** | 15 min | Capture remaining unknowns. Assign owners. Set deadlines. | All remaining |

### Who Attends

| Role | Organization | Why They're Needed |
|---|---|---|
| Product Manager (Aksana) | Orases | Facilitates, captures decisions |
| Technical Lead | Orases | Validates feasibility, API questions, data model |
| UX Designer | Orases | Captures UX requirements, asks flow questions |
| Product Owner | Duke | Confirms scope, makes business decisions |
| Subject Matter Expert(s) | Duke | Business rules: coverage logic, call center process, customer operations |
| Duke IT Representative | Duke | API availability, data formats, integration constraints |
| Duke Ops (Call Center/Support) | Duke | Current support workflows, admin tool requirements |

### Pre-Session Prep

**Orases:**
- [ ] Prepare registration flow diagrams (3 paths) for walkthrough — rough, not polished
- [ ] Prepare data sync scenario diagrams (the 5 scenarios above) for discussion
- [ ] Prepare rough admin customer view wireframe (even whiteboard level)
- [ ] Send Duke IT the API questions (1-5) at least 3 days before session
- [ ] Review preliminary scope docs to identify any gaps or contradictions

**Duke:**
- [ ] Duke IT: Bring API documentation (or draft spec) for customer validation endpoints
- [ ] Duke IT: Confirm sandbox availability and timeline
- [ ] Duke Ops: Be prepared to describe current call center process for registration and account issues
- [ ] Duke Product Owner: Think through data sync preferences (who owns what)
- [ ] Duke Legal: Provide status on Terms of Service and Privacy Policy drafts

---

## Risks Specific to This Deliverable

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| Duke API not available for development | Cannot validate Duke customers. Must mock and retrofit. | Medium-High | Build registration without validation first. Add API integration as separate phase. Background retry for failed validations. |
| Dual-CRM complexity (Commerce + Dynamics) | Two APIs, two data formats, edge cases with customers in both systems | Medium | Design unified validation service that calls both and merges. Test with anonymized real data. |
| Data sync direction not decided | Blocks profile editing. Risk of data divergence. | Medium | Force decision in discovery session. Default to "no sync outbound" for MVP if Duke can't commit. |
| Non-native data ownership unclear | Blocks non-native experience design | Medium | Present 3 options, push for decision. Default to Option A (our DB only, dashboards for Duke). |
| Legal review delays (ToS, Privacy Policy) | Cannot submit to App Store without live privacy policy URL | Medium | Start legal review at kickoff regardless. Privacy policy is first priority. |
| Admin tool deprioritized | No way to support customers when registration goes live | High | Frame admin as inseparable from registration. Same deliverable, same sprint. |

---

*Source: Customer App Scope (preliminary), Admin Portal Scope (preliminary), Non-Native Customer Data Ownership architecture doc, Initial Solution Architecture*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
