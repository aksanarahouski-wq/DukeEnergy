# Discovery Strategy & Roadmap
### Duke Energy RS Home Services & Warranty Application
### Phase 1 / MVP Discovery Planning

**Author:** Aksana Rahouski, Product Manager (Orases)
**Created:** March 19, 2026
**Status:** Draft — Internal Planning Document

---

## Purpose

This document defines the discovery approach for the Duke Energy Residential Solutions Home Services App. It establishes:
- **Priority order** for feature discovery (what we tackle first, next, last)
- **Discovery session structure** for each deliverable
- **Dependencies and blockers** that must start moving immediately
- **What we do NOT need to discover upfront**

Discovery is not a single phase — it's a rolling process. We discover in waves, aligned to development readiness, so we stay ahead of the build team without doing months of upfront analysis that becomes stale.

**Each deliverable is a vertical slice** — not just a customer-facing feature. A deliverable covers: customer experience + admin experience + data model + data sync + business rules + integration points + design. Discovery produces PRDs as outputs; no PRDs exist prior to discovery.

---

## How the Three Workstreams Relate

We have three product surfaces — Customer App, Admin Portal, Contractor Portal — but they are not three separate discovery tracks.

**The contractor portal is minimal for MVP.** We are not rebuilding contractor-facing tools. Contractors continue using the existing Commerce CRM portal. Our admin backend manages contractor configuration (trades, zip codes, availability). Discovery for contractor concerns happens inside the admin workflow sessions, not as a standalone track.

**The admin portal is the manual engine that powers the customer app.** For every customer-facing feature, there is a corresponding admin workflow. When APIs don't exist or automation isn't ready, admins fill the gap manually. Discovery for admin and customer features happens together, not sequentially.

```
Customer App Feature          Admin Backend Counterpart
─────────────────────         ─────────────────────────
Registration & Onboarding  →  Manual enrollment processing (if API not ready)
HPP Service Booking        →  Manual contractor notification, status updates
Ad-Hoc Service Booking     →  Service catalog management tool
Home Inventory             →  Inventory admin views, contractor data entry
Notifications              →  Notification templates, bulk messaging
HPP Plan Management        →  Plan sync from Commerce/Dynamics
```

**Discovery sessions cover both sides of each feature** — what the customer sees AND what admin does behind the scenes.

---

## Priority Order: Waves

### Wave 1: Foundation (Discover First — Blocks Everything Else)

#### Deliverable #1: Customer Registration & Onboarding

**Why first:** Nothing works without it. Every other feature requires users to have accounts. This deliverable validates the Duke Enterprise API integration, defines the three customer types (Duke native, P&G native, non-native), and establishes the data model foundation.

**What's already known (from preliminary scope):**
- Three customer segments with different registration paths
- Duke/P&G customers validated against Commerce/Dynamics APIs
- Non-native customers register with email/password only (no Duke system validation)
- Multi-property support required from Day 1
- Guest access for browsing DIY content (limited, no account needed)
- Profile validation links app profile to Duke Business Partner ID

**What needs discovery:**
- Exact Duke Enterprise API specification (request/response format, error handling)
- Customer validation edge cases: spouse's name on bill, no active account, multiple customers at same address
- Multi-property UX: property selector approach (every screen vs. "active property" toggle)
- Password requirements, MFA approach, account recovery flow
- What data is collected at registration vs. progressive profiling later
- Guest access boundaries (what exactly can a guest see?)
- Admin workflow for manual enrollment when API is unavailable
- Data model: exact fields for user profile, property, customer type mapping

**Blocking dependencies (must be in motion before session):**
- Duke Enterprise API documentation and sandbox access
- Sample customer data for testing validation logic
- Duke brand guidelines for registration screens

**Admin counterpart:** Manual enrollment processing workflow, customer profile management for support calls, account unlock/password reset tools.

---

#### Deliverable #2: Service Booking — HPP Covered Services

**Why second:** Core value proposition for 800K existing customers. This is the feature that reduces call center volume by 40% and proves the app's value. It also defines the contractor matching algorithm and the admin manual workflow that powers ALL service types.

**What's already known (from preliminary scope):**
- Symptom-based intake (not technician-level diagnosis)
- Coverage eligibility check at booking (against cached HPP plans)
- Contractor auto-assignment by Trade + Zip Code (primary contractor only for MVP)
- Customer sees pre-assigned contractor with option to request alternative via phone call (NOT in-app selection)
- Static availability buffers: HVAC 1-2 days, Electrical 5-6 days, Plumbing 3-5 days, Appliance 2-3 days
- No FSM integration for MVP — all status updates are manual via admin
- Status flow: Pending Confirmation → Confirmed → Completed (no intermediate statuses)
- $0 cost to customer (covered by HPP subscription)
- Emergency services route to phone, not app

**What needs discovery:**
- Symptom intake: exact categories, questions, branching logic per trade
- Coverage check logic: what rules determine if a service request is covered? (This is a CRITICAL business rules session — Duke must define)
- Contractor matching: confirm the Trade + Zip Code + Primary/Secondary lookup. Get the actual data (contractor master list, trade assignments, zip code mappings)
- Service request creation: does an API exist to write to Dynamics/Commerce, or is this fully manual for MVP?
- Scheduling UX: how does customer select date/time? Calendar picker with available windows? Or just "next available"?
- Cancellation/reschedule flow: customer-initiated vs. admin-initiated, policies, notice requirements
- Emergency triage: exact qualifying questions and routing logic
- Admin SLAs: 1-hour processing target, 24-hour contractor response — confirm these with Duke ops team
- What information does the contractor receive? (customer name, address, problem description, inventory data?)

**Blocking dependencies:**
- Contractor data export from Duke (CSV: contractor ID, name, trades, zip codes, primary/secondary)
- Service order API specification (or confirmation that MVP is fully manual)
- Coverage rules documentation from Duke business team

**Admin counterpart:** Service request dashboard, manual contractor notification workflow, status update workflow, exception handling (no contractor available, contractor declines), manual service request creation for phone orders.

---

### Wave 2: Core Product (Discover Next — Revenue + Engagement)

Wave 2 discovery starts while Wave 1 is in early development. These features have fewer Duke API dependencies and can be designed in parallel.

#### Deliverable #3: Home Inventory & Profile Building

**Why next:** Strategic competitive moat. Drives engagement (80% inventory completion target). Enables maintenance reminders and upselling (30% lift in plan enrollment). No Duke API dependency — this is 100% our data stored in our database. Can be developed in parallel with Wave 1 backend work.

**What's already known:**
- Manual entry with barcode scanning for appliances
- Pre-fill from public data sources (address → square footage, year built, property type)
- Progressive profiling (not required all at once)
- Contractor-enhanced data collection during service visits
- Gamification incentives for completion (points, badges, profile score)
- Home Health Scorecard (risk assessment based on appliance ages, maintenance history)

**What needs discovery:**
- Item categories and fields: exact list of what we track per appliance type (HVAC, water heater, electrical panel, plumbing, appliances)
- Barcode scanning: which barcode database/API to use for product lookup
- Public data pre-fill: which data source for property data (Zillow API, county records, other)
- Warranty tracking: what information, how entered (manual vs. photo/scan of warranty card)
- Maintenance schedule generation: rules per appliance type (e.g., HVAC filter every 90 days, water heater flush annually)
- Home Health Score algorithm: exact calculation method (Duke decision or we propose?)
- Contractor data capture: what form do contractors fill out post-service? How does it flow to customer's inventory?
- Photo storage: requirements, limits, S3 architecture
- Data model: inventory item fields, relationship to property, relationship to service history

**Blocking dependencies:**
- Barcode/product database selection
- Public property data source selection
- Duke decision on Home Health Score approach

**Admin counterpart:** Inventory admin views (support agents can see/edit customer inventory), contractor inventory data entry workflow.

---

#### Deliverable #4: Home Protection Plan Management

**Why next:** Revenue driver — 100K new HPP enrollments target within 12 months. Increases average plans per customer from 1.7 to 2.0. Depends on HPP plan APIs but "display existing plans" can ship with registration. Self-service enrollment and cancellation reduce call center volume.

**What's already known:**
- Display customer's existing HPP plans with coverage details
- Plan catalog browsing (view all available plans)
- Plan comparison tool (side-by-side feature/pricing comparison)
- Enrollment workflow with terms acceptance
- Self-service cancellation (compliance requirement)
- 6 plan types: Water Heater, HomeWire/Electrical, HVAC, Plumbing, Appliance, Utility Line
- $9.99/month per plan, billed on utility bill

**What needs discovery:**
- HPP plan APIs: exact endpoints for plan catalog, enrollment, cancellation, upgrade/downgrade
- Plan details: coverage rules per plan type (what's covered, what's excluded, dollar limits)
- Enrollment flow: instant confirmation or manual admin review? Payment method setup at enrollment?
- Cancellation flow: immediate or end-of-billing-cycle? Retention offers? Reason capture?
- Upgrade/downgrade: can customers change plans mid-cycle? Pro-rated billing?
- Plan comparison: what attributes to compare? (coverage items, price, deductible, limits)
- Legal: terms of service per plan, state-specific variations
- Admin workflow for manual enrollment processing (if enrollment API isn't ready)

**Blocking dependencies:**
- HPP plan API documentation (plan catalog, enrollment, cancellation endpoints)
- Plan coverage rules documentation from Duke business team
- Legal review of enrollment terms

**Admin counterpart:** Enrollment queue management, manual enrollment processing in CRM, plan sync monitoring.

---

#### Deliverable #5: Service Booking — Ad-Hoc Services

**Why next:** $25M revenue target within 12 months. 250K non-native customer acquisition within 24 months. This is Duke's growth play beyond their utility customer base.

**Critical caveat:** The ad-hoc service catalog does NOT exist today. This discovery is as much a business workshop with Duke as it is a technical session. Duke must define what services to offer and at what price before we can design anything.

**What's already known:**
- Browse/search with transparent, flat-rate pricing
- Pre-assigned contractor (same Trade + Zip Code logic as HPP)
- No contractor marketplace in MVP (Phase 2)
- Contractor collects payment on-site for MVP (cash, check, credit card via contractor's reader)
- Starts with 5-10 services in 1-2 pilot markets
- Examples discussed: HVAC tune-up (~$99), water heater flush, ceiling fan installation ($120-$190)

**What needs discovery:**
- Service catalog: which 10-20 services at launch? (Duke business decision — we facilitate)
- Pricing model per service: flat rate, price range, or quote required?
- Geographic availability: which markets at launch? All Duke territories or pilot only?
- Service descriptions: scope of work, what's included, what's excluded, estimated duration
- Contractor participation: which contractors offer ad-hoc services? Same network or subset?
- Contractor pricing: are contractor rates the same as customer price? Does Duke take margin?
- Payment collection: exact process for contractor-collected payment. How is it reported/reconciled?
- Booking flow differences from HPP: customer sees price, selects service, sees contractor — what else?
- Catalog admin tool: how does Duke's product team add/edit/disable services and pricing?
- Promotional pricing: discount codes, seasonal offers, first-time customer deals?

**Blocking dependencies:**
- Duke business team must define initial service catalog and pricing (target: Weeks 8-12 per RFP)
- Contractor negotiation for ad-hoc service rates
- Decision on pilot market geography

**Admin counterpart:** Ad-hoc service catalog CRUD tool, pricing management, geographic availability configuration, revenue reporting.

---

### Wave 3: Experience Layer (Discover Last — Enhances Everything Else)

Wave 3 features enhance the core product but don't block it. Discovery can happen incrementally through lighter sessions as Waves 1 and 2 are being built. No big upfront workshops needed — more like refinement sessions during development.

#### Deliverable #6: Communication & Notifications

**Why it can wait:** Technically well-understood (push/SMS/email are standard). The discovery is mostly about: which events trigger which notifications, message templates, and customer preference management. Can be defined late and built incrementally.

**What needs discovery:**
- Notification event map: every status change and action that triggers a notification
- Channel rules: which events go to push vs. SMS vs. email vs. all three
- Customer preference management: opt-in/out per channel, frequency controls
- Template content: message copy for each notification type (Duke marketing team input)
- Admin bulk messaging: use cases, approval workflow, targeting rules
- In-app notification center: design, read/unread, deep linking to relevant screen

**No blocking dependencies.** Can be discovered in Week 6-8 and built iteratively.

---

#### Deliverable #7: Loyalty / Gamification / Home Health Score

**Why it can wait:** Engagement feature, not revenue-critical. Depends on inventory (Wave 2) and service bookings (Wave 1) existing first. Duke needs to define the point economics.

**What needs discovery:**
- Points earning rules: how many points per action (profile completion, service booking, inventory item added, referral)
- Point-to-dollar conversion: what is 1 point worth?
- Redemption catalog: what can customers redeem points for? (service credits, plan discounts, merchandise)
- Badge definitions: what milestones earn badges? Visual design.
- Home Health Score: algorithm, display, recommendations based on score
- Profile completion score: which fields count, weighting

**Dependency:** Duke must define the loyalty program economics (business decision, not technical).

---

#### Deliverable #8: DIY Content & Maintenance Reminders

**Why it can wait:** Content must be created or sourced. Reminders depend on inventory data existing. Low technical risk.

**What needs discovery:**
- Content sourcing: who creates DIY content? Duke internal, third-party licensing, contractor contributors?
- Content categories and taxonomy
- Reminder rules: which appliance types get which reminders at what frequency
- CPSC recall integration: API access, notification flow
- Seasonal content calendar
- Content admin tool requirements

**Dependency:** Content creation is a Duke responsibility. Discovery is fast; content production is slow.

---

#### Deliverable #9: Service History & Records

**Why it can wait:** Largely falls out of service booking (Wave 1). May not need standalone discovery — likely an enhancement to Deliverable #2.

**What needs discovery:**
- Historical data: does Duke want to import past service history into the app, or start fresh?
- Export format: PDF, CSV, or both?
- What fields appear in service history records?
- Home sale use case: can customers share/export full history?

---

## Discovery Session Format

For each deliverable in Waves 1 and 2, run a structured discovery session:

### Session Template (2-3 Hours Per Deliverable)

| Block | Duration | Focus | Output |
|---|---|---|---|
| **1. Scope Alignment** | 30 min | Walk through preliminary scope research. Confirm what's in/out for MVP. Get client sign-off on boundaries. | Confirmed scope boundaries document |
| **2. User Flows & Business Rules** | 45 min | Walk through each user flow step by step. Identify decision points, edge cases, error states. Document business rules. | Validated flow diagrams + business rules matrix |
| **3. Data Model & Integration** | 30 min | What data do we need? Where does it come from (Duke API, our DB, manual)? Define fields and sources of truth. | Data model draft + API dependency list |
| **4. Admin Workflow** | 30 min | For every customer action, define what admin does behind the scenes. Define the manual fallback process. Define SLAs. | Admin workflow documentation |
| **5. Open Questions & Risks** | 15 min | Surface blockers. Assign owners. Set deadlines for answers. | Action items with owners and due dates |
| **6. Design Input** | 15-30 min | Key screens, interaction patterns, content needs. Enough for design to start wireframes. | Design brief with screen inventory |

### Who Attends

| Role | Organization | Why |
|---|---|---|
| Product Manager (Aksana) | Orases | Facilitates session, captures requirements |
| Technical Lead | Orases | Validates feasibility, identifies technical risks |
| UX Designer | Orases | Captures design requirements, asks UX questions |
| Product Owner | Duke | Confirms scope, makes business decisions |
| Subject Matter Expert(s) | Duke | Answers business rules questions (coverage logic, pricing, operations) |
| Duke IT Representative | Duke | Confirms API availability, answers integration questions |

### Session Outputs (Per Vertical Slice)

Each deliverable is a **vertical slice** — it covers the full stack from customer experience through admin workflows through data model and integrations. After each discovery session, Orases produces:

1. **PRD (Product Requirements Document)** — Created from discovery findings. Covers: customer UX, admin UX, data model, data sync, business rules, integration points, and design requirements. PRDs are an OUTPUT of discovery, not an input.
2. **Data Model** — Entity fields, relationships, sources of truth per field, sync direction
3. **API Dependency List** — What we need from Duke, status (available/not available/TBD), fallback plan
4. **Admin Workflow Documentation** — Step-by-step manual process for each customer action, including sync implications
5. **Design Brief** — Screen inventory for both customer and admin surfaces, key interactions, content needs for wireframe production
6. **Open Questions & Action Items** — With owners and deadlines

---

## What We Do NOT Need to Discover Upfront

| Topic | Why Not Now | When |
|---|---|---|
| **Contractor portal rebuild** | Not building one for MVP. Contractors stay on Commerce CRM. | Phase 2 discovery |
| **Payment gateway integration** | MVP uses contractor-collected payment. Duke hasn't selected a vendor yet. | After discovery for Deliverables #4 and #5 is complete and Duke selects gateway |
| **FSM tool integration** | Not MVP. Duke hasn't selected a tool (evaluating ServicePower, Service Bench). | Phase 2 discovery, after Duke procurement |
| **White-label multi-tenant configuration** | Architecture decision already made (tenant_id from Day 1). No config UI needed for MVP. | Phase 2 when second tenant onboards |
| **AI assistant / predictive maintenance** | Phase 2/3 feature. No discovery needed now. | Future phase |
| **IoT / smart home integration** | Phase 2/3 feature. | Future phase |
| **Contractor marketplace** | Phase 2. MVP uses pre-assigned primary contractor. | After MVP launch, based on customer feedback |
| **Advanced analytics / BI dashboards** | MVP starts with basic reporting. Full BI tool selection can wait. | Post-launch based on data needs |

---

## Suggested Timeline

| Week | Activity | Details |
|---|---|---|
| **Week 1** | Internal team kickoff | Review onboarding docs. Prep Wave 1 discovery materials. Assign session facilitators. |
| **Week 2** | **Wave 1 Discovery: Session 1** | Registration & Onboarding — scope, flows, data model, admin workflow |
| **Week 2-3** | **Wave 1 Discovery: Session 2** | HPP Service Booking — scope, flows, contractor matching, admin manual workflow |
| **Week 3** | Wave 1 design starts | Wireframes for registration and service booking flows |
| **Week 3-4** | Dev starts technical foundation | Auth system, API client, CI/CD pipeline, database schema, app shell |
| **Week 4** | **Wave 2 Discovery: Session 3** | Home Inventory — scope, data model, barcode scanning, public data pre-fill |
| **Week 4-5** | **Wave 2 Discovery: Session 4** | HPP Plan Management — plan APIs, enrollment/cancellation flows, coverage rules |
| **Week 5** | **Wave 2 Discovery: Session 5** | Ad-Hoc Services — catalog workshop with Duke business team, pricing, pilot markets |
| **Week 5-6** | Wave 1 PRDs produced | PRDs created from discovery findings — client review and approval of Registration + HPP Service Booking |
| **Week 5-6** | Wave 1 development begins | Registration and service booking feature development |
| **Week 6-8** | Wave 2 design starts | Wireframes for inventory, plan management, ad-hoc catalog |
| **Week 7-8** | **Wave 3 Discovery: Session 6** | Notifications + Loyalty + DIY Content (lighter session, combined) |
| **Week 8+** | Ongoing refinement | Discovery sessions as-needed when development surfaces questions |

---

## Critical Path Items — Push Duke on These Immediately

These dependencies have long lead times. They must start moving at the kickoff meeting regardless of discovery wave timing.

### 1. Duke Enterprise API Access
- **Need:** API documentation, sandbox environment, test credentials
- **Why urgent:** Blocks Wave 1 development (registration, plan lookup, service order creation)
- **RFP commitment:** API documentation and sandbox within 2 weeks of vendor kickoff
- **Action:** Confirm commitment at kickoff. Get named Duke IT contact. Set weekly checkpoint.

### 2. Contractor Data Export
- **Need:** CSV/JSON of all contractors with: contractor ID, name, trades, zip codes, primary/secondary designation
- **Why urgent:** Required to build contractor matching logic and populate admin backend
- **Action:** Request at kickoff. Target delivery by Week 3.

### 3. Ad-Hoc Service Catalog Definition
- **Need:** Duke business team to define 10-20 initial services with pricing
- **Why urgent:** Product catalog doesn't exist today. Must be defined by Weeks 8-12 per RFP timeline.
- **Action:** Raise at kickoff. Schedule dedicated business workshop by Week 5.

### 4. Legal Review
- **Need:** Terms of service, privacy policy, HPP enrollment terms, state-specific compliance
- **Why urgent:** Long lead time through Duke legal. Must be live before App Store submission.
- **Action:** Request Duke legal kickoff at Week 1. Privacy policy must be ready by Week 20 (MVP).

### 5. Apple Developer Account (If Native Decision Confirmed)
- **Need:** Organization developer account under Duke Energy (requires D-U-N-S number)
- **Why urgent:** D-U-N-S verification takes 5-14 business days. Account approval takes 1-5 days after that.
- **Action:** Confirm platform decision at kickoff. Start account process same week.

### 6. Coverage Rules Documentation
- **Need:** Business rules for what's covered under each HPP plan type
- **Why urgent:** Blocks service booking coverage check logic
- **Action:** Request from Duke business team by Week 3. This is a document that likely exists internally — just needs to be shared.

### 7. Duke Brand Guidelines
- **Need:** Logo files, color palette, typography, UI component standards
- **Why urgent:** Design cannot start without brand assets
- **Action:** Request at kickoff. Target delivery by Week 2.

---

## Risk Register

| Risk | Impact | Likelihood | Mitigation |
|---|---|---|---|
| Duke Enterprise APIs delayed beyond Week 4 | Blocks registration and service booking development | Medium-High | Build against mock APIs. Design API contract collaboratively. Escalate to Duke exec sponsor if delayed. |
| Ad-hoc product catalog not defined by Week 8 | Cannot build catalog browsing or ad-hoc booking | Medium | Start with 5 "hero services" Duke can define quickly. Expand iteratively. |
| Contractor data export delayed | Cannot build matching algorithm or admin contractor config | Medium | Build matching logic against sample data. Import real data when available. |
| Coverage rules not documented | Cannot build coverage check in service booking | Medium | Build with configurable rules engine. Populate rules when Duke provides documentation. |
| Duke IT resources unavailable for discovery sessions | Incomplete API understanding, rework during development | Medium | Get Duke IT commitment at kickoff. Identify named contacts per API domain. |
| Legal review takes longer than 12 weeks | Blocks App Store submission | Low-Medium | Start legal review in Week 1. Privacy policy is highest priority — push first. |

---

## Summary: The Three-Wave Approach

**Wave 1 (Weeks 2-3):** Registration + HPP Service Booking
- Foundation features that everything else depends on
- Validates Duke API integration
- Defines the admin manual workflow pattern
- **2 discovery sessions**

**Wave 2 (Weeks 4-5):** Home Inventory + HPP Plans + Ad-Hoc Services
- Revenue and engagement features
- Less Duke API dependency (inventory is our data)
- Ad-hoc requires Duke business decisions on catalog/pricing
- **3 discovery sessions**

**Wave 3 (Weeks 7-8):** Notifications + Loyalty + DIY Content
- Experience layer that enhances core features
- Lower risk, well-understood technology
- Can be discovered incrementally during Wave 1-2 development
- **1-2 lighter sessions**

**Total:** 7-8 discovery sessions over 6-8 weeks, running ahead of development. Not a waterfall "discover everything first" approach — a rolling discovery that stays 2-3 weeks ahead of the build team.

---

*Source: Customer App Scope, Admin Portal Scope, Contractor Portal Scope, SOW #1 V6*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
