# Non-Native Customer Data Ownership & Sync Strategy
### Duke Energy RS Home Services & Warranty Application
### Architecture Decision Reference

**Status:** Open — requires Duke decision on CRM sync strategy
**Related:** Initial Solution Architecture (Open Question #14)
**Author:** Aksana Rahouski, Product Manager (Orases)

---

## Context

When a non-native customer registers (someone who is NOT a Duke or P&G utility customer), **our platform owns 100% of their data.** There is no Duke system that knows they exist. Commerce and Dynamics have no matching record. This document defines what we store, what we don't sync, and what decisions Duke needs to make.

---

## What We Store for Non-Native Customers

### User Profile (USERS table)
- Email, password hash, name, phone
- `customer_type: non_native`
- `external_customer_id: NULL` — no Business Partner ID exists in Commerce or Dynamics
- Communication preferences (push, SMS, email opt-in/out)
- Loyalty points balance, profile completion percentage
- Last login, account creation date

### Property (PROPERTIES table)
- Home address — this is how we determine zip code for contractor matching
- Property type, square footage, year built (from public records pre-fill)
- `premise_id: NULL` — no Duke premise, they are not a utility customer
- Can have multiple properties

### Home Inventory (HOME_INVENTORY table)
- Every appliance they add: make, model, serial number, age, photos
- Warranty information, barcode scan data
- Maintenance schedules auto-generated from inventory
- **This is entirely new data that does not exist anywhere in Duke's systems**

### Service Requests (SERVICE_REQUESTS table)
- Every ad-hoc booking they make
- `request_type: ad_hoc` — non-native customers cannot book HPP-covered services (they have no plans)
- `hpp_enrollment_id: NULL`
- Contractor assigned, scheduled date/time, status, price
- Completion notes, contractor notes

### Loyalty & Engagement
- Points earned, badges, profile completion score
- Home health scorecard data
- All gamification state

### Payment Methods (Phase 2)
- Tokenized credit card or Apple Pay / Google Pay references stored with payment gateway (Stripe)
- Non-native customers cannot pay via utility bill — they have no utility account

---

## What Does NOT Sync to Duke (MVP and Likely Phase 1)

| Data | Why Not |
|---|---|
| Non-native user profile | No matching record in Commerce or Dynamics. Duke CRM has no concept of these customers. |
| Home inventory | This entity does not exist in any Duke system. We created it. |
| Loyalty points / badges | App-only feature, no Duke CRM equivalent. |
| Payment methods | Stored with our payment gateway, not Duke. |
| Communication preferences | App-only setting. |

**Our platform IS the system of record for all non-native customer data.**

---

## What MAY Need to Sync to Duke

| Data | When | Why |
|---|---|---|
| **Ad-hoc service requests** | Phase 1+ | Duke needs visibility into all service orders for contractor invoicing, revenue tracking, and operational reporting. If a non-native customer books a $99 HVAC tune-up, that service order likely needs to flow into Dynamics so Duke can track revenue and pay the contractor. |
| **Customer count / analytics** | Phase 1 | Duke's business case depends on the 250K non-native acquisition target within 24 months. They need aggregate data — how many non-natives registered, where, what they booked. This can be reporting/dashboard data rather than a CRM sync. |

---

## Three Scenarios — Requires Duke Decision

### Scenario A: Duke Never Gets Non-Native Raw Data
- We provide Duke dashboards and reports (aggregate numbers)
- Duke trusts our system as source of truth for non-native customers
- Service request data flows to Dynamics only for contractor invoicing
- **Simplest technically. Lowest integration cost.**

### Scenario B: Duke Wants Non-Native Customers in Their CRM
- When a non-native customer registers, we push a customer record to Dynamics
- This creates a "Business Partner" in Duke's world for someone who is not a utility customer
- **More complex** — Duke CRM may not support customer records without a utility account. Requires Duke IT confirmation.
- Adds integration scope and timeline.

### Scenario C: Non-Native Customer Converts to Duke Utility Customer
- Example: Nathan moves to Duke's service territory and gets a Duke utility account
- Now he IS a native customer
- We need to link his existing app profile (with all his inventory, service history, loyalty points) to his new Duke Business Partner ID
- **The architecture already handles this:** `customer_type` changes from `non_native` to `duke_native`, and `external_customer_id` gets populated with the Business Partner ID from Commerce validation
- All existing data (inventory, service history, loyalty) carries over seamlessly

---

## How Native vs. Non-Native Differ in the Architecture

| Aspect | Duke/P&G Native Customer | Non-Native Customer |
|---|---|---|
| **Registration** | Email/password + address validated against Commerce/Dynamics API | Email/password + address only (no validation against Duke systems) |
| **external_customer_id** | Populated (Business Partner ID) | NULL |
| **premise_id** | Populated (Duke premise reference) | NULL |
| **HPP Plans** | Cached from Commerce/Dynamics, displayed in app | None — cannot enroll in HPP (MVP). Future: TBD |
| **Service booking — HPP** | Available. Coverage check runs against cached plans. | Not available. No plans = no covered services. |
| **Service booking — Ad-hoc** | Available. Same flow as non-native. | Available. This is their primary use case. |
| **Contractor matching** | Same algorithm (trade + zip code) | Same algorithm (trade + zip code) |
| **Payment (MVP)** | Contractor collects on-site. HPP services = $0. | Contractor collects on-site. |
| **Payment (Phase 2)** | Credit card, Apple Pay, or add to utility bill | Credit card or Apple Pay only. No utility bill option. |
| **Data source of truth** | Commerce/Dynamics for identity + plans. Our DB for inventory, preferences, loyalty. | Our DB for everything. Duke systems have no record. |
| **Home inventory** | Stored in our DB (new entity, not in Duke systems) | Stored in our DB (identical) |
| **Loyalty / gamification** | Stored in our DB | Stored in our DB (identical) |

---

## Question for Duke

> "For non-native customers, our platform is the system of record. Commerce and Dynamics don't know these people exist. We store everything — their profile, their home inventory, their service history, their engagement data. The question for you is: do you need that data flowing into your CRM, or are you comfortable with our platform being the source of truth for non-native customers, with reporting and dashboards giving you visibility?"

### Why This Matters

- If Duke wants CRM sync for non-native customers, that is additional API work — and Duke IT needs to confirm their CRM can accept customer records not tied to a utility account
- If Duke is comfortable with dashboard-only visibility, we can deliver faster and keep integration scope focused on the Duke/P&G customer paths that have clear CRM mappings
- The architecture supports both approaches — the question is scope and timeline, not technical feasibility

### Decision Needed By: Week 4 of Development

This decision affects:
- Integration scope for service request sync to Dynamics
- Whether we need a "create non-native customer in CRM" API from Duke IT
- Reporting and analytics architecture (do we push data to Duke's BI tools, or do they consume our dashboards?)

---

*Source: Initial Solution Architecture, Customer App Scope (Section 2: Customer Types & Segmentation, Section 5: Key Integrations), Admin Portal Scope (Section 5: Data Sync Strategy)*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
