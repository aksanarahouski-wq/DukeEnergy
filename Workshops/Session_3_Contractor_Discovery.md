# Session 3: Contractor Discovery

**Focus:** Understand contractor workflows, define matching algorithm, and decide Phase 1 contractor portal scope.

**🚨 CRITICAL:**
- Invite 1-2 actual contractors if possible (for authentic feedback)
- Duke IT should attend for integration discussion

---

## KEY DECISIONS & ASSUMPTIONS FROM SESSIONS 1 & 2

### What We Know So Far:

**Current Contractor Matching (Confirmed):**
- **Algorithm**: Trade + Zip Code → Automatic assignment in SAP/CRM
- **Primary/Secondary**: Contractors designated as primary or secondary per trade + zip code
- **Lead Time**: Varies by contractor and trade
  - HVAC/Water Heater: 1-2 days (faster)
  - Electrical (non-emergency): 5-6 business days
  - General buffer: 3-5 days minimum
- **Time Windows**: Varies per contractor (1-hour, 3-hour, or half-day slots)
- **SLA Contracts**: Contractors under contract with Duke, rarely decline jobs

**Current Contractor Workflow:**
1. Customer calls Duke → CSR creates service request in CRM (manual today)
2. CRM auto-assigns to contractor based on trade + zip code
3. Contractor calls customer back within 48 hours
4. Contractor schedules appointment with customer
5. **Piloting now**: Front-end scheduling during initial call (skip callback)

**Warranty vs Ad-Hoc Service Differences:**
- **Warranty (HPP Covered)**:
  - Duke assigns contractor (customer can request exception)
  - Negotiated rates with contractors
  - Contractor covers territory under contract
  - Duke pays contractor
- **Ad-Hoc Services**:
  - More marketplace model (customer may have choice)
  - Pricing varies by contractor/region
  - Phase 1: Contractor collects payment on-site
  - Future: App-based payment processing

**Contractor Data & Systems:**
- **Current Storage**: Commerce CRM (Duke) / Dynamics (P&G)
- **Current FSM**: Internal SAP-based system
- **Future FSM Tools Under Consideration**: Service Power, Service Bench (NOT Service Channel)
- **For MVP**: Copy contractor configuration to app backend (trade, zip code, lead time, primary/secondary)

**MVP Contractor Portal Scope (From Session 2):**
- **Minimal contractor portal changes for MVP**
- **Focus on backend admin configuration**: Manage contractor data in admin portal
- **No FSM integration Phase 1**: Manual status updates by admin
- **Contractor ratings**: External survey (current process), results fed back to app for display
- **Pizza tracker / GPS tracking**: Phase 2 (requires FSM tool with contractor mobile app)

**Communication & Status Updates:**
- **Today**: 70% of contractors provide some lifecycle communication (contractor-specific)
- **Future Vision**: Consistent communication across all contractors via FSM tool
- **MVP**: Duke provides confirmation, scheduled, completed notifications; contractors handle "en route" notifications

**What Still Needs Clarification (This Session):**
1. P&G internal employees vs Duke third-party contractors - how are they managed differently?
2. Contractor availability tracking - how should this work? (blocked dates, max jobs/day, vacation?)
3. Contractor specialization - multi-trade contractors or single-trade only?
4. Exception handling - what happens when no contractor available, contractor cancels, etc.?
5. Phase 1 contractor portal scope decision - Option A, B, C, or D?

---

## Critical Questions to Answer

### **1. Current Contractor Experience**

**Goal:** Understand what works and what doesn't in current contractor portal.

**✅ CONFIRMED from Sessions 1 & 2:**
- Contractors receive assignments via CRM (Commerce/Dynamics)
- Assignment is automatic based on trade + zip code
- Contractors call customers back within 48 hours to schedule
- ~150 Duke third-party contractors in network
- Contractor data stored in Commerce (Duke) and Dynamics (P&G)

**NEW Questions for This Session:**
- **Can we see the current contractor portal?** (screen share or demo)
- **What do contractors like about current portal?** What frustrates them?
- **What features do contractors want most?** (real-time job notifications, mobile app, scheduling calendar, etc.)
- **How do contractors currently manage their schedules?** (external calendar, paper, mental notes?)
- **Do contractors want a mobile app or is web portal sufficient?** (If mobile, iOS or Android or both?)

**Contractor Data - Current State:**
- **Can we review actual contractor data fields?** (screen share CRM)
- **What fields exist today?**
  - Trade/specialization
  - Service area (zip codes)
  - Primary/secondary designation
  - Contact info
  - Lead time/buffer
  - Time window preferences
- **What fields are MISSING that we need?**
- **Contractor credentials tracking:**
  - License numbers (single or multiple if multi-trade?)
  - License expiration dates tracked?
  - Insurance certificates on file? Expiration dates?
  - Background check status/dates?
- **Contractor availability tracking:**
  - **NOT tracked systematically today** - How SHOULD it be tracked for app?
  - Blocked dates (vacation, holidays)?
  - Max jobs per day capacity?
  - Work schedule (Monday-Friday 8-5? Weekends available?)?
  - Real-time availability calendar or static buffer (3-5 days)?
- **Contractor performance tracking:**
  - Is performance tracked? What metrics? (jobs completed, on-time %, customer ratings?)
  - Where stored? (CRM or external survey system?)
  - Does performance inform primary/secondary designation?

**🚨 CRITICAL: Duke vs P&G Contractor Model Differences:**
- **How many P&G internal employees?** (Duke = ~150 third-party contractors, P&G = ?)
- **Do P&G employees use same portal as Duke contractors?** Or completely different system?
- **Can P&G employees serve Duke customers and vice versa?** Cross-territory assignments allowed?
- **How does payment work for P&G employees?** (salaried, hourly, per-job?) vs Duke contractors (invoiced per job?)
- **How is P&G employee availability tracked?** (shift schedules, PTO system, HR system?) vs Duke contractors
- **Do P&G employees need mobile app or existing system sufficient?**
- **Phase 1 contractor portal: Must it support BOTH third-party contractors AND internal employees?** Or Duke-only for MVP?

**Why This Matters:** **P&G internal employees vs Duke third-party contractors is COMPLETELY different employment model.** Informs Phase 1 scope decision (build new vs enhance existing), defines data integration requirements, and may require different features for employees vs contractors.

---

### **2. Contractor Matching Algorithm - THE BLOCKER**

**Goal:** Define how contractors are matched to service requests.

**✅ CONFIRMED from Sessions 1 & 2:**
- **Current Algorithm**: Trade + Zip Code → Automatic assignment in CRM
- **Primary/Secondary Logic**: Primary contractor gets first opportunity, secondary is backup
- **Geographic Coverage**: Contractors cover specific zip codes (some rural areas have only 1 contractor)
- **Warranty Services**: Duke assigns contractor (customer can request exception)
- **Ad-Hoc Services**: More marketplace model (customer may have choice, depending on pricing)
- **Contractor Acceptance**: Target 90%+ acceptance rate (contractors rarely decline due to SLA contracts)

**CRITICAL Questions - Need Specification:**

**Matching Factors - What's the Priority Order?**
1. **Geographic Match**: How is service area defined?
   - Exact zip code match only?
   - Radius from contractor location (e.g., 25 miles)?
   - Can contractor serve non-contiguous areas (Charlotte AND Raleigh but not between)?
2. **Trade/Specialization Match**:
   - Are contractors single-trade or multi-trade?
   - If contractor is multi-trade (HVAC + Plumbing), which services can they accept?
3. **Availability**:
   - Does app check contractor availability BEFORE assigning?
   - Or assign to primary, if declined then offer to secondary?
   - How do we handle lead time (HVAC = 1-2 days, Electrical = 5-6 days)?
4. **Performance/Rating**:
   - Are high-performing contractors prioritized?
   - Does customer rating affect future assignments?
5. **Customer Preference**:
   - Can customer request specific contractor?
   - Can customer request "same tech as last time"?
   - How to handle preferred contractor unavailable?

**Primary/Secondary Contractor Logic - Need Details:**
- **What determines tier?** (performance, seniority, contract terms, pricing?)
- **Is tier per geography or global?** (Primary for Charlotte, secondary for Raleigh? Or always primary?)
- **How long to wait for primary before offering to secondary?**
  - Immediate fallback if primary declines?
  - Wait 24 hours for primary to accept?
  - Offer to multiple contractors simultaneously?
- **Can secondary become primary?** (based on performance, ratings, availability?)

**Edge Cases & Exception Handling:**
- **No contractor available in zip code**:
  - Expand radius search?
  - Offer to contractors in neighboring zip codes?
  - Manual admin intervention?
- **Contractor accepts but cancels later** (e.g., contractor's husband in hospital):
  - Auto-reassign to secondary?
  - Notify customer immediately?
  - Admin manually reassigns?
- **All contractors in area at capacity**:
  - Waitlist customer?
  - Offer later time slots?
  - Expand geographic search?
- **Customer requests specific contractor who's unavailable**:
  - Offer next available date for that contractor?
  - Suggest alternative contractor?
  - Let customer wait for preferred contractor?
- **Service request outside any contractor's coverage area**:
  - Inform customer service not available in their area?
  - Manual outreach to contractors to expand coverage?

**Contractor Availability - How Does This Work?**
- **Does contractor provide availability proactively?** (e.g., "I'm available Mon-Fri 9-5, max 3 jobs/day")
- **Or does system assign, then contractor accepts/declines?**
- **How does lead time/buffer factor in?** (3-5 days minimum, varies by trade)
- **Can contractor block dates?** (vacation, holidays, already booked)

**Why This Matters:** **This algorithm is core to app functionality.** Customer sees available time slots based on contractor availability. Can't build scheduling calendar without detailed specification.

**DECISION NEEDED:** Define matching factors, priority order, and edge case handling.

---

### **3. Contractor Data & Availability**

**Goal:** Define contractor data structure and how availability will be tracked.

**✅ CONFIRMED from Sessions 1 & 2:**
- Contractor data exists in CRM: Trade, Zip Code, Primary/Secondary designation
- **For MVP**: Copy to app backend for configuration management
- Admin backend will manage contractor configuration (trade, zip, lead time, buffer)
- **Availability is NOT systematically tracked today** - need to define how it should work

**CRITICAL Data Model Questions:**

**Contractor Specializations:**
- **Single trade or multi-trade per contractor?**
  - Contractor A = HVAC only?
  - Contractor B = HVAC + Plumbing + Electrical?
- **If multi-trade, how is this stored?** (separate records per trade, or multi-select field?)
- **Trade types list - Are these correct?**
  - HVAC
  - Plumbing (interior)
  - Electrical (home wiring)
  - Water Heater
  - Appliance Repair
  - General Handyman
  - Other?

**Service Area Definition:**
- **How is service area defined?**
  - List of zip codes? (Contractor serves zip: 28201, 28202, 28203...)
  - Radius from contractor location? (address + 25 mile radius)
  - Cities or counties?
- **Can contractor serve non-contiguous areas?** (e.g., Charlotte AND Raleigh but not cities in between?)
- **Do service areas ever change?** How often? Who updates?

**Contractor Tier (Primary/Secondary):**
- **Is tier per zip code or global?**
  - Example 1: Contractor A is primary for Charlotte (28xxx), secondary for Raleigh (27xxx)
  - Example 2: Contractor A is always primary across all their service areas
- **What determines tier?** (performance, pricing, capacity, seniority, contract terms?)
- **Can tier change over time?** (e.g., secondary promoted to primary based on performance?)

**Contractor Availability - NEW SYSTEM NEEDED:**
- **How should contractors indicate availability?**
  - Option A: Static buffer (e.g., "Always available starting 3 days from now")
  - Option B: Calendar system (contractor blocks dates, marks availability)
  - Option C: Capacity-based (e.g., "Max 3 jobs/day, show available slots")
  - Option D: Accept/decline model (system assigns, contractor accepts or declines within X hours)
- **What availability data do we need?**
  - Work schedule (Mon-Fri 8-5? Weekends? Evenings?)
  - Time window preferences (1-hour slots, 3-hour slots, half-day?)
  - Max jobs per day
  - Blocked dates (vacation, holidays, already booked)
  - Lead time/buffer (3 days? 5 days? Varies by trade?)
- **Who manages contractor availability?**
  - Contractor self-service (contractor updates own availability)?
  - Admin managed (back office updates based on contractor communication)?
  - Hybrid (contractor requests changes, admin approves)?

**Data Model for Matching:**
- **Confirm these are the data points needed for matching:**
  - Customer zip code
  - Service type (trade)
  - Contractor trade(s)
  - Contractor service areas (zip codes)
  - Contractor availability (dates/times)
  - Contractor lead time/buffer
  - Contractor tier (primary/secondary)
  - Contractor current workload (active jobs count)
  - Contractor performance rating (optional)
- **Should we track matching history?** (Service Request + Contractor Offered + Accept/Decline + Reason)
  - **Why**: Improve algorithm over time, identify bottlenecks

**Why This Matters:** **Data model must support matching algorithm.** Can't show customer "available time slots" without contractor availability data. This is MVP blocker.

---

### **4. Job Assignment & Status Updates**

**Goal:** Understand contractor workflow from assignment to completion.

**✅ CONFIRMED from Sessions 1 & 2:**
- **Current**: Contractors receive assignment in CRM, call customer within 48 hours
- **Piloting**: Front-end scheduling during initial call (no callback delay)
- **MVP Approach**: Manual status updates by admin (no FSM integration Phase 1)
- **Future**: FSM tool provides automated status updates (en route, on-site, completed)
- Contractors rarely decline (SLA contracts), but can request reassignment (emergencies, capacity issues)

**Questions for This Session:**

**Contractor Notification & Job Details:**
- **How does contractor receive job assignment today?** (email, SMS, portal login, phone call?)
- **What information does contractor see?**
  - Customer name, address, phone
  - Service type, problem description
  - Preferred date/time window
  - Payment type (warranty covered, ad-hoc cash, over-coverage amount)
  - Customer inventory details (make, model, serial number)?
  - Coverage limits (for warranty services)?
- **How quickly must contractor respond?** (accept/decline within X hours?)

**Contractor Workflow:**
- **Current workflow - confirm sequence:**
  1. Contractor receives assignment in CRM
  2. Contractor calls customer to schedule
  3. Contractor performs service
  4. Contractor updates CRM: completed, services performed, parts used
  5. Duke sends customer survey (external)
- **Future workflow - for app:**
  1. Contractor receives notification (email/SMS/push)
  2. Contractor accepts/declines in portal (or auto-assigned if SLA)
  3. Customer sees confirmation in app
  4. Contractor provides status updates (en route, on-site, in progress, completed) - **Phase 2 with FSM**
  5. Customer rates contractor in app - **Phase 2**

**Status Updates - MVP vs Future:**
- **MVP (No FSM integration)**:
  - Which statuses are critical? (assigned, scheduled, completed minimum?)
  - How does admin know when to update status? (contractor calls/emails operations?)
  - Can contractor update status themselves in current portal?
- **Future (FSM tool integrated)**:
  - Automated GPS tracking (pizza tracker)
  - Real-time status updates from contractor mobile app
  - Customer notifications based on contractor location

**Service Completion:**
- **What does contractor enter at completion?**
  - Services performed (dropdown list or free text?)
  - Parts used, quantities, costs?
  - Photos of completed work?
  - Customer signature (collected today? Required for MVP?)?
  - Time spent (for invoicing)?
- **Where is completion data entered?** (CRM only? Or also in contractor portal?)

**Why This Matters:** Defines contractor portal/app requirements for MVP vs Phase 2. Manual admin updates acceptable for MVP, but need to know current contractor communication process.

---

### **5. Contractor-Customer Communication**

**Goal:** Understand how contractors and customers communicate.

**✅ CONFIRMED from Sessions 1 & 2:**
- **Today**: Contractor calls customer after assignment (within 48 hours)
- **70% of contractors** provide some lifecycle communication (contractor-specific)
- **MVP**: Phone/SMS communication continues (no in-app messaging Phase 1)
- **Future Vision**: Consistent communication via FSM tool (SMS, push notifications)

**Questions for This Session:**
- **How do contractor and customer communicate today?**
  - Direct phone calls?
  - SMS text messages?
  - Through Duke dispatch (3-way calling)?
- **Do contractors have customer's phone number directly?** Or is it masked/routed through Duke?
- **Privacy/Safety concerns:**
  - Should contractor see customer's full phone number?
  - Should customer see contractor's personal cell phone or business line?
- **In-app messaging:**
  - **MVP**: Not needed (phone/SMS sufficient)
  - **Phase 2**: Should app support in-app chat? (like Uber messaging)
  - Pros: Keeps communication within app, privacy protection
  - Cons: Development complexity, contractor adoption challenge

**Why This Matters:** In-app messaging adds significant complexity. Confirming phone/SMS is acceptable for MVP simplifies scope.

---

### **6. Payment Collection - Phase 1 Approach**

**Goal:** Confirm Phase 1 payment approach for ad-hoc services.

**✅ CONFIRMED from Sessions 1 & 2:**
- **Warranty (HPP Covered) Services**:
  - Duke pays contractor (negotiated rates)
  - Customer pays $0 for covered services
  - If over coverage limit: Customer pays excess to contractor on-site
- **Ad-Hoc Services**:
  - **Phase 1**: Contractor collects payment on-site (cash, check, credit card via Square/Stripe)
  - **Future**: Customer pays via app → Duke pays contractor

**Questions for This Session:**
- **What payment methods can contractors accept today?**
  - Cash?
  - Check?
  - Credit card via Square/Stripe/Clover?
  - All contractors have card readers?
- **How does contractor report payment to Duke?**
  - Enter in CRM after service completion?
  - Invoice Duke for ad-hoc services?
  - Weekly/monthly reconciliation?
- **Does Duke take commission on ad-hoc services?**
  - If yes: How much? (% of service cost or flat fee?)
  - How is commission collected? (deducted from contractor payment?)
- **Contractor invoicing:**
  - How does contractor invoice Duke for warranty work?
  - How does contractor invoice Duke for their portion of ad-hoc work (if commission model)?
  - Weekly batch? Per-job? Net 30?
- **Future state payment flow:**
  - Customer pays Duke via app (credit card, Apple Pay, Google Pay)
  - Duke pays contractor (net commission)
  - Timeline for Phase 2? (Year 2? Phase 3?)

**Why This Matters:** Phase 1 payment scope is simpler (on-site collection), but need to understand invoicing/reconciliation process for admin portal. Future app-based payment is Phase 2+.

---

### **7. Phase 1 Contractor Portal Scope - THE BIG DECISION**

**Goal:** Decide what to build for contractors in Phase 1.

**✅ STRONG SIGNAL from Sessions 1 & 2:**
- **Focus MVP on customer app** (highest business value)
- **Minimal contractor portal changes for Phase 1**
- **Admin backend** will manage contractor configuration (copy data from CRM)
- **Manual status updates** by admin acceptable for MVP (no FSM integration Phase 1)
- **Pizza tracker/GPS = Phase 2** (requires FSM tool selection and contractor mobile app)

**Options for Phase 1:**

| Option | Description | Pros | Cons | Timeline | Cost | Likelihood Based on Sessions 1 & 2 |
|--------|-------------|------|------|----------|------|-------------------------------------|
| **A: Minimal Enhancements** | Keep existing portal, integrate backend only, admin manages contractor config | Contractors keep familiar system, focus on customer app, fastest to market | Contractors don't see improvements, manual admin updates required | 44 weeks | Lowest | **HIGH - This aligns with Session 2 decisions** |
| **B: New Mobile App** | Build new contractor iOS/Android app with job notifications, status updates, scheduling | Modern UX, mobile-first, pizza tracker possible | Contractors must adopt new tool, significant dev time, FSM tool needed | 60+ weeks | Highest | LOW - Deferred to Phase 2 |
| **C: Hybrid Approach** | Enhance existing portal + lightweight mobile companion for status updates only | Contractors have choice, partial mobility | Maintain two systems, still significant scope | 52 weeks | Medium-High | LOW - Too complex for MVP |
| **D: Admin-Only (No Contractor Changes)** | No contractor portal changes, all managed via admin backend, contractors use CRM as today | Maximum focus on customer app, learn from MVP before contractor investment | Contractors use same old system, admin workload higher | 44 weeks (no contractor scope) | Lowest | **VERY HIGH - Most aligned with sessions** |

**Questions for This Session:**
- **What do contractors need MOST from app?**
  - Real-time job notifications (email/SMS)?
  - Mobile access to job details?
  - Ability to update status on-the-go?
  - Scheduling calendar?
- **What frustrates contractors most about current system?**
  - Too many phone calls?
  - Hard to manage schedule?
  - Lack of customer information?
  - Payment reconciliation issues?
- **Business priority for Phase 1:**
  - Customer acquisition (highest priority)?
  - Contractor satisfaction (secondary)?
  - Operational efficiency (admin/back office)?
- **Timeline pressure:**
  - Must launch by Q2-Q3 2026?
  - Can we defer contractor improvements to Phase 2?
- **Contractor feedback:**
  - **If contractors are in the meeting**: What do you want most in a new system?
  - Would you use a mobile app if we built one?
  - Or is web portal sufficient?

**Why This Matters:** **Directly impacts Phase 1 budget and timeline.** Building new contractor mobile app adds 3-4 months and significant cost. Based on Sessions 1 & 2, **Option D (Admin-Only)** seems most aligned with Duke's priorities.

**Orases Recommendation:** **Option D for MVP** ✅
- **Focus 100% of Phase 1 on customer app** (highest business value for $25M ad-hoc revenue goal)
- **Admin backend manages contractor configuration** (data copied from CRM)
- **Manual status updates** by admin acceptable for MVP (contractors call/email operations)
- **Contractors keep existing CRM workflow** (functional, familiar)
- **Phase 2: Build modern contractor mobile app** after FSM tool selected and after learning from customer app MVP
- **Rationale**: Customer app drives revenue ($25M target), contractor app improves operations but doesn't directly generate revenue

**DECISION NEEDED:** Confirm Phase 1 contractor portal scope (Option A or D recommended)

---

### **8. Contractor System Integration**

**Goal:** Understand where contractor data lives and how to integrate.

**✅ CONFIRMED from Sessions 1 & 2:**
- **Contractor data storage**: Commerce CRM (Duke contractors), Dynamics (P&G)
- **Current FSM**: Internal SAP-based system
- **MVP approach**: Copy contractor data to app backend (no real-time API for MVP)
- **Future FSM tools**: Service Power, Service Bench under consideration
- **Admin backend will house contractor configuration** (trade, zip, lead time, buffer, availability)

**Questions for Duke IT:**

**Data Integration:**
- **Can we get a data export of contractor information?**
  - Contractor list (name, company, contact info)
  - Trade specializations
  - Service areas (zip codes)
  - Primary/secondary designation
  - Lead time/buffer
  - Pricing (negotiated rates for warranty services)
  - Performance metrics (if tracked)
- **How often does contractor data change?**
  - Daily? Weekly? Monthly?
  - Do we need nightly sync or manual updates acceptable?
- **Can we get API access in future?** (Phase 2)
  - Read contractor list
  - Read contractor availability
  - Read/write service request status

**Service Request Flow:**
- **If app creates service request, how does it get to contractor?**
  - Option A: App creates record in app DB → Manual export to CRM → CRM assigns contractor
  - Option B: App creates record in app DB → API call to CRM (if API exists) → CRM assigns contractor
  - Option C: App creates record in app DB → Email/queue to operations → Operations manually creates in CRM
- **Which option is most realistic for MVP?**
- **What data must be passed to CRM for service request?**
  - Customer ID (utility account number or app profile ID?)
  - Service type (trade)
  - Problem description
  - Customer address
  - Preferred date/time
  - Customer inventory details (make, model, serial)
  - HPP plan info (if covered service)

**Status Updates - How Do They Flow Back?**
- **If contractor updates status in CRM, does app need to know?**
  - Real-time API callback? (unlikely for MVP)
  - Batch sync nightly? (possible)
  - Admin manually updates app DB? (most realistic for MVP)
- **Which statuses must sync to app?**
  - Assigned
  - Scheduled (date/time confirmed)
  - Completed
  - Cancelled
  - Other?

**FSM Tool Selection Timeline:**
- **When will Duke select FSM tool?** (Q1 2026? Q2 2026? Later?)
- **Will FSM tool have APIs?** (Service Power and Service Bench do)
- **Phase 2 integration:** App ↔ FSM tool ↔ Contractor mobile app
- **Should we design for future FSM integration now?** (hooks, placeholders, API architecture?)

**Why This Matters:** Defines integration architecture for MVP. Manual data sync acceptable for Phase 1 if APIs don't exist. Must understand service request flow (app → CRM → contractor) and status update flow (contractor → CRM → app).

---

## Expected Outputs

By end of Session 3, we'll have:

✅ **Contractor matching algorithm fully specified** (factors, priority order, edge cases, availability handling)
✅ **Contractor data model defined** (trade specializations, service areas, tier system, availability tracking)
✅ **Current contractor portal assessment** (what works, pain points, contractor feedback if available)
✅ **Phase 1 contractor scope decided** (Likely Option D: Admin-only, no contractor portal changes)
✅ **Job assignment workflow documented** (app → CRM → contractor flow)
✅ **Status update process confirmed** (MVP: manual admin updates; Future: FSM tool automation)
✅ **Contractor communication strategy** defined (phone/SMS for MVP, in-app messaging Phase 2)
✅ **Payment collection approach** confirmed (on-site collection MVP, app-based payment Phase 2+)
✅ **Integration plan** (data exports, service request creation, status sync)
✅ **P&G vs Duke contractor differences** clarified (internal employees vs third-party contractors)

---

## Key Risks to Surface

**Flag these if they emerge:**

🔴 **HIGH RISK:**
- **Contractor matching algorithm not fully specified** (blocks customer scheduling calendar development)
- **Contractor availability not systematically tracked** (how does customer see "available time slots"?)
- **Service request API doesn't exist** (how does app-created service request get to contractor?)
- **P&G internal employees vs Duke contractors** have different workflows (scope creep if must support both in MVP)
- **No contractor availability data** (can't show customer "this contractor available Mon 9-12, Wed 1-4")
- **Contractor data export not available** (can't populate admin backend contractor configuration)

🟡 **MEDIUM RISK:**
- **Manual admin status updates required** (admin workload high, potential for delays/errors)
- **Contractor resistance to changes** (if we change their workflow even minimally)
- **Commission structure for ad-hoc services undefined** (how is contractor paid? How does Duke take cut?)
- **Rural areas with only 1 contractor** (no backup if contractor unavailable, system breaks down)
- **FSM tool selection delayed** (Phase 2 pizza tracker dependent on FSM tool APIs)
- **Multi-trade contractors** (data model complexity if contractors can serve multiple trades)

🟢 **LOW RISK (Mitigated):**
- **Phase 1 contractor scope too ambitious** - MITIGATED by Option D (admin-only, no contractor portal changes)
- **Contractor adoption of new app** - MITIGATED by keeping existing CRM workflow for MVP
- **In-app messaging complexity** - MITIGATED by using phone/SMS for MVP

---

## Key Decisions This Session

| Decision | Options | Impact | Likely Outcome Based on Sessions 1 & 2 |
|----------|---------|--------|----------------------------------------|
| **Contractor Matching Algorithm** | Define factors (geographic, trade, availability, performance) & priority order | CRITICAL - Blocks customer scheduling development | Needs full specification this session |
| **Availability Tracking Method** | Static buffer vs calendar vs capacity vs accept/decline | Determines customer UX (available slots) | Likely static buffer for MVP (e.g., 3-5 days) |
| **Phase 1 Contractor Scope** | Option A (minimal enhancements), Option D (admin-only), Option B/C (new app) | Budget, timeline, contractor satisfaction | **Option D most likely** (no contractor changes) |
| **Contractor Data Model** | Single-trade vs multi-trade, zip list vs radius, tier per zip vs global | Data structure for matching algorithm | Needs definition this session |
| **Service Request Integration** | API vs manual queue vs email | App → CRM → Contractor flow | Likely manual/queue for MVP (no API) |
| **P&G Employee Support** | MVP supports both Duke & P&G, or Duke-only | Scope complexity | Needs clarification |

---

## Pre-Session Preparation Needed

**Duke Team Should Prepare:**
- **🚨 CRITICAL**: Invite 1-2 contractors to participate (for authentic feedback on pain points and needs)
- **Contractor portal demo**: Screen share current contractor portal (show workflow from assignment to completion)
- **Contractor data export**: Sample export showing contractor fields (trade, zip codes, primary/secondary, lead time, etc.)
- **Contractor matching process**: Document how primary/secondary selection works today
- **Contractor network data**:
  - Total # Duke contractors (confirmed ~150?)
  - Total # P&G employees
  - Breakdown by trade (HVAC, Plumbing, Electrical, etc.)
  - Geographic distribution (which markets have good coverage, which are thin?)
- **Performance data**: How is contractor performance tracked today? (surveys, ratings, on-time %, complaints?)

**Duke IT Should Prepare:**
- **Contractor data system architecture**: Where does data live? (Commerce, Dynamics, contractor portal DB?)
- **Data export feasibility**: Can we get CSV/JSON export of contractor data for admin backend?
- **API timeline**: Which APIs will exist by MVP? Service request creation? Status updates?
- **Service request workflow**: How does CRM assign contractor today? (SAP rules, manual override?)

**Orases Team Will Prepare:**
- **Matching algorithm specification template** (factors, priority, edge cases)
- **Contractor data model proposal** (entities, fields, relationships)
- **Phase 1 scope recommendation** (Option D: Admin-only approach with cost/timeline analysis)
- **Integration architecture diagrams** (app → CRM → contractor flows)

---

**Session Facilitator:** Aksana (Orases Product Manager)
**Session Designer:** Devin (Orases Product Designer & Business Analyst)
**Technical Lead:** Vlad (Orases CTO) - for integration discussion
