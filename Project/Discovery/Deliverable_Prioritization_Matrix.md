# Deliverable Prioritization Matrix
### Duke Energy RS Home Services & Warranty Application
### Phase 1 / MVP

**Author:** Aksana Rahouski, Product Manager (Orases)
**Created:** March 19, 2026
**Status:** Draft — Internal Planning Document

---

## How to Read This Matrix

Each deliverable is a **vertical slice** — not just a customer-facing feature. A deliverable includes:

| Layer | What It Covers |
|---|---|
| **Customer Experience** | What the user sees and does in the app |
| **Admin Experience** | What admins do behind the scenes to support the feature |
| **Data Model** | Entities, fields, relationships, source of truth per field |
| **Data Sync** | How data flows between our DB, Commerce, Dynamics — and who owns what |
| **Business Rules** | Coverage logic, eligibility, matching, pricing rules that Duke must define |
| **Integration Points** | APIs needed from Duke, fallback plans if APIs aren't ready |
| **Design** | Customer and admin screens, flows, content |

PRDs are produced as an **output of discovery** for each deliverable. Discovery defines scope → PRD documents it → dev builds it.

---

## Prioritization Criteria

| Criterion | Description | Weight |
|---|---|---|
| **Foundational** | Does it block other deliverables? Must exist before others can work. | Critical |
| **Revenue Impact** | Direct tie to revenue targets ($25M ad-hoc, 100K enrollments) | High |
| **Duke API Dependency** | How much relies on Duke providing APIs/data we don't control | Risk factor |
| **Business Rules Clarity** | Do rules exist today, or must Duke define them from scratch? | Risk factor |
| **Technical Complexity** | Integration difficulty, number of systems touched, unknowns | Effort factor |
| **MVP Critical** | Required for launch, or can ship after? | Gate |

---

## The Matrix

| Wave | # | Deliverable (Vertical Slice) | Foundational | Revenue | API Dependency | Rules Clarity | Complexity | MVP Critical | **Priority** |
|---|---|---|---|---|---|---|---|---|---|
| **1** | **1** | **Registration, Onboarding & Customer Management** | Blocks everything | — | High (Commerce + Dynamics validation) | Medium (edge cases) | High (3 customer types, dual CRM) | Must-have | **#1** |
| **1** | **2** | **Service Booking — HPP Covered Services** | Blocks ad-hoc, notifications | High (40% call reduction) | High (service order API TBD) | High (coverage rules from Duke) | High (contractor matching, manual workflow) | Must-have | **#2** |
| **2** | **3** | **Home Inventory & Profile Building** | Enables reminders, health score | Medium (30% plan upsell) | Low (our data, our DB) | Low (we define) | Medium (barcode scanning, public data) | Must-have | **#3** |
| **2** | **4** | **HPP Plan Management** | — | High (100K enrollments) | High (plan catalog + enrollment APIs) | Medium (plan rules exist internally) | Medium (enrollment/cancellation flows) | Must-have | **#4** |
| **2** | **5** | **Service Booking — Ad-Hoc Services** | — | Very High ($25M target) | Medium (less Duke API, more our catalog) | Low (catalog doesn't exist yet) | High (pricing, catalog CRUD, payment) | Must-have | **#5** |
| **3** | **6** | **Communication & Notifications** | — | Medium (90% satisfaction) | Low (our infrastructure) | Low (we propose event map) | Low-Medium (standard push/SMS/email) | Must-have | **#6** |
| **3** | **7** | **Loyalty / Gamification / Home Health Score** | — | Low (engagement) | None | Low (Duke defines economics) | Low | Nice-to-have | **#7** |
| **3** | **8** | **DIY Content & Maintenance Reminders** | — | Low (engagement) | None | Low (Duke provides content) | Low | Nice-to-have | **#8** |
| **3** | **9** | **Service History & Records** | — | Low | Low (falls out of #2) | High (rules already defined by #2) | Low | Enhancement to #2 | **#9** |

---

## Wave 1: Foundation — Discover First

### Deliverable #1: Registration, Onboarding & Customer Management

**The vertical slice:**
- **Customer UX:** Registration flows for 3 customer types (Duke native, P&G native, non-native), profile creation, multi-property support, "Day 1" empty-state experience
- **Admin UX:** Manual enrollment processing, customer profile management, account support tools (unlock, reset, merge)
- **Data Model:** Users, properties, customer types, tenant mapping; source-of-truth per field
- **Data Sync:** App ↔ Commerce (Duke electric), App ↔ Dynamics (P&G gas), non-native data ownership (our DB only), conversion scenario (non-native → native)
- **Business Rules:** Validation logic per customer type, what fields are editable vs. read-only, sync conflict resolution
- **Integration:** Commerce validation API, Dynamics validation API, fallback for when APIs are down
- **Design:** Registration screens (3 paths), profile screens, admin customer management screens

**Why #1:** Everything depends on users having accounts. Validates the Duke API integration pattern that every other deliverable reuses. Establishes the data model foundation and the three-customer-type architecture.

**Key risks:**
- Duke Enterprise APIs delayed → build against mocks, but blocks real testing
- Dual-CRM complexity (Commerce vs. Dynamics) is the highest technical risk in the project
- Edge cases in customer validation (spouse name, inactive account, multi-address) need Duke SME input

**Discovery document:** `Wave1_Deliverable1_Registration_Onboarding.md`

---

### Deliverable #2: Service Booking — HPP Covered Services

**The vertical slice:**
- **Customer UX:** Symptom-based intake, coverage eligibility check, contractor assignment display, appointment scheduling, status tracking, cancellation/reschedule
- **Admin UX:** Service request dashboard, manual contractor notification, status update workflow, exception handling (no contractor available, contractor declines), manual service request creation for phone orders
- **Data Model:** Service requests, contractor assignments, status history, trade/zip mappings
- **Data Sync:** Service orders to/from Dynamics/Commerce, contractor status updates (manual for MVP)
- **Business Rules:** Coverage check logic per HPP plan type, contractor matching (Trade + Zip + Primary/Secondary), static availability buffers per trade, emergency triage routing, admin SLAs
- **Integration:** Service order API (TBD if exists), contractor data from Commerce, coverage rules engine
- **Design:** Booking flow screens, status tracker, admin dashboard, contractor notification templates

**Why #2:** Core value proposition. This is the feature that proves the app works — turning a 15-minute phone call into a 3-minute booking. Defines the contractor matching pattern and admin manual workflow that Deliverable #5 (ad-hoc) reuses.

**Key risks:**
- Service order API may not exist for MVP → entire workflow is manual through admin
- Coverage rules are complex and Duke must define them (not something we can guess)
- Contractor data export from Duke has historically been slow to obtain

**Discovery document:** TBD (Wave 1, Session 2)

---

## Wave 2: Core Product — Discover Next

### Deliverable #3: Home Inventory & Profile Building

**The vertical slice:**
- **Customer UX:** Manual item entry, barcode scanning, property data pre-fill, progressive profiling, warranty tracking, maintenance schedule view, Home Health Score
- **Admin UX:** Inventory admin views (support agents see/edit), contractor inventory data entry workflow post-service
- **Data Model:** Inventory items (per property), appliance details, warranty records, maintenance schedules
- **Data Sync:** Minimal — this is 100% our data in our database. No Duke CRM sync needed.
- **Business Rules:** Maintenance schedule rules per appliance type, Home Health Score algorithm, gamification incentives
- **Integration:** Barcode/product lookup API, public property data source (Zillow/county records)
- **Design:** Inventory screens, barcode scanner, profile completion progress, contractor data entry form

**Why #3:** Strategic competitive moat with 80% completion target. Zero Duke API dependency — can be built in parallel with Wave 1 backend work. Enables maintenance reminders (Deliverable #8) and upselling (30% lift in plan enrollment).

**Key risks:** Low. Mostly our own data and our own decisions. Barcode database selection is the biggest open question.

---

### Deliverable #4: HPP Plan Management

**The vertical slice:**
- **Customer UX:** View existing plans with coverage details, browse plan catalog, compare plans side-by-side, enroll in new plan, cancel plan (self-service)
- **Admin UX:** Enrollment queue management, manual enrollment processing in CRM, plan sync monitoring, cancellation processing
- **Data Model:** Plans, plan types, coverage rules, enrollment records, cancellation records
- **Data Sync:** Plan data from Commerce/Dynamics → our DB (read-only for display); enrollment/cancellation requests from our DB → Commerce/Dynamics
- **Business Rules:** Plan eligibility per customer type, enrollment terms, cancellation policy (immediate vs. end-of-cycle), retention offers, state-specific variations
- **Integration:** HPP plan catalog API, enrollment API, cancellation API — all from Commerce/Dynamics
- **Design:** Plan catalog, comparison tool, enrollment flow, cancellation flow, admin enrollment queue

**Why #4:** Revenue driver (100K new enrollments target). "Display existing plans" is a quick win that can ship with registration. Full enrollment/cancellation workflow is the high-value piece.

**Key risks:**
- HPP plan APIs may not be ready → can display cached plan data, defer enrollment to phone
- Legal review required for enrollment terms (long lead time)
- Plan rules may differ by state — complexity multiplier

---

### Deliverable #5: Service Booking — Ad-Hoc Services

**The vertical slice:**
- **Customer UX:** Browse service catalog with transparent pricing, service detail pages, booking flow (similar to HPP but with price), contractor assignment, payment (contractor-collected for MVP)
- **Admin UX:** Service catalog CRUD tool (add/edit/disable services and pricing), geographic availability configuration, revenue reporting, promotional pricing management
- **Data Model:** Service catalog (services, pricing, descriptions, availability), ad-hoc bookings, payment records
- **Data Sync:** Minimal Duke sync — catalog is our data. Booking records may sync to Dynamics for contractor coordination.
- **Business Rules:** Pricing model per service (flat rate vs. range vs. quote), geographic availability, contractor participation rules, promotional discount rules
- **Integration:** Reuses contractor matching from Deliverable #2. Payment integration deferred (contractor-collected for MVP).
- **Design:** Service catalog browsing, service detail pages, booking flow, admin catalog management tool

**Why #5:** $25M revenue target and 250K non-native customer acquisition. But the service catalog doesn't exist today — Duke must define what services to offer at what price before we can build anything. This is as much a business workshop as a technical discovery.

**Key risks:**
- Product catalog doesn't exist (Duke business decision, not a tech problem)
- Pricing strategy undefined (flat rate vs. variable — fundamentally changes the UX)
- Contractor willingness to participate at defined prices is unknown
- Payment integration deferred to post-MVP means contractor-collected payment reconciliation is manual

---

## Wave 3: Experience Layer — Discover Last

### Deliverable #6: Communication & Notifications

**The vertical slice:**
- **Customer UX:** Push/SMS/email notifications for service status changes, in-app notification center, notification preferences
- **Admin UX:** Notification template management, bulk messaging tool, notification delivery monitoring
- **Data Model:** Notification events, templates, customer preferences, delivery logs
- **Data Sync:** Event-driven — triggered by status changes in service bookings, plan updates, etc.
- **Business Rules:** Which events trigger which channels, frequency limits, opt-in/opt-out rules
- **Integration:** Firebase (push), SMS gateway (Twilio/SNS), email service (SES/SendGrid)
- **Design:** Notification center, preferences screen, admin template editor

**Why #6:** Foundational for the "Uber-like" experience but technically well-understood. Discovery is mostly about defining the notification event map with Duke, not solving technical unknowns.

**Key risks:** Low. Standard technology, multiple vendor options. Main risk is Duke marketing team being slow to approve notification copy.

---

### Deliverable #7: Loyalty / Gamification / Home Health Score

**The vertical slice:**
- **Customer UX:** Points display, badges, profile completion score, Home Health Score dashboard, rewards redemption
- **Admin UX:** Points/rewards configuration, badge management, leaderboard monitoring
- **Data Model:** Points ledger, badges, rewards catalog, redemption records
- **Data Sync:** None — fully our data
- **Business Rules:** Points earning rules, point-to-dollar conversion, redemption options, Home Health Score algorithm
- **Integration:** None
- **Design:** Gamification dashboard, rewards catalog, badges gallery

**Why #7:** Engagement feature that enhances everything else but doesn't block anything. Duke must define the loyalty program economics (business decision) before we can design it.

**Key risks:** Low technical risk. Main risk is Duke not prioritizing the business decisions needed.

---

### Deliverable #8: DIY Content & Maintenance Reminders

**The vertical slice:**
- **Customer UX:** Content library browsing, search, video playback, maintenance reminder notifications, CPSC recall alerts
- **Admin UX:** Content management (CRUD), reminder rule configuration, recall alert management
- **Data Model:** Content items (articles, videos), content categories, reminder rules, recall records
- **Data Sync:** CPSC recall feed integration
- **Business Rules:** Reminder frequency per appliance type, content categorization taxonomy
- **Integration:** CPSC recall API
- **Design:** Content library, article/video views, reminder notification templates

**Why #8:** Content must be created or sourced by Duke — that's the long-lead-time item, not the tech. Reminders depend on inventory data (Deliverable #3) existing first.

---

### Deliverable #9: Service History & Records

**Likely an enhancement to Deliverable #2, not a standalone deliverable.** Service history is a natural output of service bookings. Discovery may confirm this doesn't need its own slice.

**Open questions:**
- Does Duke want to import historical service data into the app, or start fresh?
- Export format requirements (PDF, CSV)?
- Home sale use case: can customers share/export full history?

---

## What Is NOT a Deliverable

These items from the old matrix are **not standalone deliverables** — they are layers within other vertical slices or deferred to Phase 2:

| Item | Where It Lives |
|---|---|
| **Payment Processing** | Part of Deliverable #5 (ad-hoc services) for MVP. Contractor-collected payment for MVP; in-app payment is Phase 2 or added when Duke selects a payment gateway. |
| **Contractor Matching & Scheduling** | Part of Deliverable #2 (HPP service booking). Simple Trade + Zip lookup for MVP. Advanced matching (FSM tool) is Phase 2. |
| **Emergency Service Handling** | Part of Deliverable #2. Simple triage flow: "Is this an emergency?" → "Call this number." Not app-based for MVP. |

---

## Cross-Cutting Concerns (Not Deliverables — Addressed Across All Slices)

These are architectural decisions and patterns that apply to every deliverable, not standalone discovery sessions:

| Concern | How Addressed |
|---|---|
| **Multi-tenancy** | Architecture decision already made: tenant_id on every table, Laravel global scopes. Applied from Deliverable #1 onward. |
| **Authentication & security** | Defined in Deliverable #1 (registration). Applied to all subsequent deliverables. |
| **Data sync patterns** | Defined in Deliverable #1 (the three customer types establish the sync pattern). Reused in all deliverables that touch Duke data. |
| **Admin role-based access** | Base RBAC defined in Deliverable #1's admin slice. Permissions extended per deliverable. |
| **Offline capability** | Architecture decision (service workers, local storage strategy). Defined during Deliverable #1-2, applied everywhere. |
| **Brand guidelines & design system** | Established during Deliverable #1 design phase. Component library reused across all deliverables. |

---

## Discovery → Build Flow

```
Wave 1 Discovery (Weeks 2-3)     →  Wave 1 PRDs produced (Week 5-6)  →  Wave 1 Dev (Weeks 5-6+)
         ↓                                                                      ↓
Wave 2 Discovery (Weeks 4-5)     →  Wave 2 PRDs produced (Week 7-8)  →  Wave 2 Dev (Weeks 8+)
         ↓                                                                      ↓
Wave 3 Discovery (Weeks 7-8)     →  Wave 3 PRDs produced (Week 9-10) →  Wave 3 Dev (Weeks 10+)
```

Discovery stays 2-3 weeks ahead of development. No waterfall. PRDs are outputs of discovery, not inputs.

---

*Source: Customer App Scope, Admin Portal Scope, Contractor Portal Scope, SOW #1 V6, Discovery Strategy & Roadmap*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
