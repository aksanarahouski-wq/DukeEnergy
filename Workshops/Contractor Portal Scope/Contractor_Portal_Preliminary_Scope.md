# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 1. EXECUTIVE SUMMARY

### Meeting Details
- **Date**: Session 3 Contractor Discovery Workshop
- **Participants**:
  - **Duke Energy Team**: Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap, Chris Murphy (Director, Contractor Network), Ed Carr (Field Operations)
  - **Orases Team**: Tom Witt, Vlad (Lead), Aksana Rahouski
- **Duration**: ~90 minutes
- **Format**: Virtual discovery session via video conference

### Purpose of Session
This contractor discovery session was designed to understand the current contractor ecosystem, define contractor matching algorithms, and determine Phase 1 contractor portal scope. The goal was to identify minimal viable contractor features needed to support the customer app MVP while deferring extensive contractor portal enhancements to Phase 2.

The team emphasized a pragmatic approach - understanding current contractor workflows and determining what must be built vs. what can be managed manually for MVP launch.

### Key Decisions Made

1. **Minimal Contractor Changes for MVP**: Phase 1 will NOT include new contractor portal or mobile app. Contractors will continue using existing Commerce CRM workflow. Admin backend will manage contractor configuration.

2. **Contractor Matching Algorithm**: Matching based on **Trade + Zip Code + Primary/Secondary designation**. System will recommend primary contractor with option for customer to request alternative (handled via phone call for MVP).

3. **Manual Status Updates for MVP**: Admin team will manually update service request statuses in app based on contractor communication (phone/email). No real-time FSM integration for Phase 1.

4. **Static Availability Windows**: Contractors will provide availability rules (lead time buffer, time windows, work days) that Duke maintains. Real-time contractor schedule visibility deferred to Phase 2 with FSM tool.

5. **Contractor Data Sync**: Contractor configuration data (trade, zip codes, lead time, availability windows) will be exported from CRM and maintained in app admin backend. Manual updates acceptable for MVP.

6. **FSM Tool Procurement Timeline**: Duke is evaluating Service Power and Service Bench as FSM solutions. NOT in scope for Phase 1. Phase 2+ will integrate FSM for:
   - Real-time contractor availability
   - GPS tracking ("pizza tracker")
   - Automated status updates
   - Mobile app for contractors

7. **Payment Collection - Phase 1**: Contractors collect payment on-site for ad-hoc services (cash, check, credit card via Square/Stripe). App-based payment processing deferred to Phase 2.

8. **Multi-Trade Contractors**: Contractors can serve multiple trades (plumbing, electrical, HVAC). Each trade may have different availability windows, lead times, and primary/secondary designations.

9. **Inventory Data Collection**: Contractors will be asked to capture appliance/system details during service visits to populate customer home inventory. Process and incentive structure TBD with contractor field coordinators.

10. **Communication Strategy**: Phase 1 uses phone/SMS for contractor-customer communication. In-app messaging deferred to Phase 2. Contractors continue providing lifecycle communications as they do today (~70% provide updates).

---

## 2. CONTRACTOR NETWORK OVERVIEW

### Current Contractor Base

**Total Contractors**: 125-140 contractors
- **Primary Contractors**: ~80% (100-112 contractors)
- **Backup Contractors**: ~20% (25-28 contractors)
- **Geographic Coverage**: 4-5 states (North Carolina, South Carolina, Florida, Ohio, Indiana)
- **Trades Covered**:
  - HVAC (Heating & Cooling)
  - Plumbing (interior lines)
  - Electrical (home wiring)
  - Water Heater
  - Appliance Repair

**Coverage Statistics**:
- **HVAC, Electrical, Plumbing, Water Heater**: 99-100% coverage in Duke/P&G territories
- **Appliance**: 95%+ coverage (some gaps filled by A&E nationwide contractor)
- **Rural Areas**: Some zip codes have only 1 contractor (no backup)
- **Urban Areas**: 2-3 contractors per trade per territory (primary + backups)

**Quote from Kevin**: "We have 125 contractors... across our four to five states that we primarily operate in... 80% are primary, maybe 20% are backup contractors."

### Contractor Types

#### Primary Contractors
- **Definition**: First assigned contractor for their designated trade + territory
- **Priority**: Receive job assignments first
- **SLA Contracts**: Negotiated response times, pricing, and territory commitments
- **Acceptance Rate**: Target 90-95% acceptance (contractors rarely decline)
- **Relationship**: Long-term partnerships, rarely change unless bought out or business model shifts
- **Revenue**: Duke warranty work provides steady revenue stream to fill schedule gaps

**Quote from Kevin**: "Our contractors, once they start doing our work, pretty much stay with our work unless they get bought out... It's very rare that we have contractors fall off our list once they're on it."

#### Backup/Secondary Contractors
- **Definition**: Assigned to territory but serve as overflow or replacement when primary unavailable
- **When Used**: Primary contractor at capacity, unavailable, or customer requests alternative
- **Challenge**: Limited work volume makes it hard to retain backup contractors
- **Work Distribution**: May only receive 5-10% of jobs in their backup territories

**Quote from Chris Murphy**: "One of the challenges with finding backup contractors is if you don't have enough work to support them as a backup, then they see no purpose in being a backup contractor."

#### Multi-Trade Contractors
- **Scope**: Most larger contractors offer 2-3 trades (plumbing, electrical, HVAC)
- **Appliance Exception**: Appliance repair often requires specialized contractors
- **Business Structure**: Contractors may operate trades as separate business units with different teams
- **Availability**: Each trade may have different availability windows, lead times, and buffers
- **Example**: Contractor may do plumbing on Tuesdays/Thursdays only, but HVAC Monday-Friday

**Quote from Ed Carr**: "When we talk about having windows for contractors, when they are multiple trades, they may have different windows depending upon the trade."

### Duke vs. Piedmont (P&G) Contractors

**Key Question**: Are Duke contractors third-party vendors while P&G uses internal employees?

**Current State**:
- **Duke**: ~125+ third-party independent contractors
- **P&G (Piedmont Natural Gas)**: Internal employees (count not specified in meeting)
- **Data Storage**: Duke contractor data in Commerce CRM, P&G in Dynamics
- **Phase 1 Scope**: Needs clarification if MVP must support both contractor types or Duke-only

**Critical for Phase 1**: Internal employees vs. independent contractors have different workflows:
- Payment models (salaried vs. per-job invoicing)
- Availability tracking (HR/PTO systems vs. contractor calendars)
- Portal access needs
- Compliance requirements

---

## 3. CONTRACTOR MATCHING ALGORITHM

### Current State Algorithm

**Matching Logic** (Existing in SAP/Commerce CRM):
1. **Customer Service Request** created (trade + zip code)
2. **System Auto-Assigns** to primary contractor for that trade + zip code
3. **Contractor Receives Assignment** via portal/email
4. **Contractor Calls Customer** within 48 hours to schedule
5. **Contractor Updates CRM** with scheduled date/time

**Quote from Kevin**: "Right now what exists is trade and zip code. So you will know if I need plumbing and my zip code is 12345, it will be assigned to this person."

### Phase 1 MVP Matching Requirements

**Matching Factors** (Priority Order):

1. **Trade/Specialization Match** (Required)
   - HVAC
   - Plumbing
   - Electrical
   - Water Heater
   - Appliance Repair
   - Multi-trade contractors match multiple services

2. **Geographic Match - Zip Code** (Required)
   - One-to-one zip code assignment
   - Does NOT use radius or county
   - Contractors assigned specific zip code lists
   - Some contractors serve non-contiguous areas (Charlotte AND Raleigh but not in between)

3. **Primary/Secondary Designation** (Required)
   - Primary contractor offered first
   - Customer sees "This is your contractor" with pre-selected assignment
   - Option to request different contractor (handled via phone call for MVP)
   - If primary unavailable/declines, offer to secondary contractor

4. **Service Type** (HPP vs. Ad-Hoc)
   - **HPP Covered Services**: Duke assigns contractor, customer can request exception
   - **Ad-Hoc Services**: More marketplace model, may show contractor options in future
   - **MVP**: Both use primary contractor assignment

5. **Contractor Availability** (Lead Time/Buffer)
   - **HVAC/Water Heater**: 1-2 business days lead time (emergency-level priority)
   - **Electrical (non-emergency)**: 5-6 business days lead time (filler work)
   - **Plumbing**: 3-5 business days (varies)
   - **Appliance**: 2-3 business days
   - Contractors provide availability windows (time slots per day, days of week)

**Quote from Kevin**: "We will default based off our default logic. So we have a primary contractor that we will send out for HPP plan. That is what it's going to display in the app, so they know we have a contractor coming out there, who's going to be that person."

### Customer Preference & Contractor Selection

**MVP Approach**:
- Customer sees pre-selected primary contractor
- "Here's who's coming to your house" (not "select your contractor")
- Hidden option to request different contractor (small link/button)
- Requesting alternative triggers phone call to admin

**Quote from Kevin**: "I'd rather not give that transparent, hey, go select somebody else, because we have negotiated pricing, negotiated territories... I think that as long as you display it, say, hey, here's who's coming out to your home, and it's all on that summary page, and then you say, if you would like to change the contractor, blah blah, and it's like a little button that you can say, okay, I want to edit it."

**Why Limit Selection**:
1. **Negotiated Rates**: Duke has pre-negotiated pricing with primary contractors
2. **Prevent Gaming**: Customers may "contractor shop" to find one who will cover exclusions
3. **Territory Commitments**: Contractors have contractual territory obligations
4. **Operational Complexity**: Multiple contractors for same job creates backend coordination issues

**Quote from Chris Murphy**: "One of the challenges with that is customers become very strategic. So they get one contractor who knows their situation and knows that something's not covered because it's a code violation. Then they start going through the contractor list saying, well, I want someone else out here... until they try to find the right one who will cover something that should not be covered."

**Future State** (Phase 2+ with Ad-Hoc Services):
- For cash-pay ad-hoc services, may allow contractor selection
- Display multiple contractors with pricing and ratings
- Customer chooses based on availability, price, ratings
- No "gaming" risk since customer pays directly

### Exception Handling

**Scenario 1: Primary Contractor Unavailable**
- **Current**: Admin calls backup contractor, attempts to keep same time window
- **MVP**: Admin manually reassigns, updates app with new contractor/time
- **Customer Communication**: Admin calls/texts customer if time must change

**Scenario 2: Primary Contractor Declines**
- **Frequency**: Less than 5% of the time (rare due to SLA contracts)
- **Current**: Admin reassigns to backup contractor
- **MVP**: Same process, admin updates app
- **Goal**: 90-95% acceptance rate from primary contractors

**Scenario 3: No Contractors Available in Zip Code**
- **Current**: Rare - 99%+ coverage in served territories
- **MVP**: System should flag "service not available in your area" if no contractor match
- **Workaround**: Admin can manually reach out to contractors to expand coverage

**Scenario 4: All Contractors at Capacity**
- **Current**: Extend time window, offer later dates
- **MVP**: Show later availability windows to customer
- **Future**: Track contractor workload to close time slots when at capacity

**Scenario 5: Emergency/Hurricane Events**
- **Current**: Admin manually overrides assignments, extends buffers, communicates delays
- **MVP**: Admin can flag "service delays in your area" banner in app
- **Notification**: Proactive alerts to affected customers

**Quote from Ed Carr**: "Kevin, what are your thoughts about hurricanes and things like that, sometimes when a contractor has a zip code, but they're not available?"

**Quote from Kevin**: "We would just have to consider, do we override that inside the app that this contractor's buffer is changed or this is the primary contractor, which is maybe a secondary contractor normally for that territory."

---

## 4. CONTRACTOR DATA & CONFIGURATION

### Contractor Data Model

**Core Contractor Fields** (Needed in App Backend):

| Field | Description | Example | Maintained By |
|-------|-------------|---------|---------------|
| Contractor ID | Unique identifier | CNTR-12345 | CRM |
| Contractor Name | Business name | ABC Plumbing & HVAC | CRM |
| Contact Info | Phone, email | (704) 555-1234 | CRM |
| Trade(s) | Services offered | Plumbing, HVAC, Electrical | Admin Backend |
| Service Areas | Zip codes served | 28201, 28202, 28203... | Admin Backend |
| Primary/Secondary | Per trade + zip | Primary HVAC in 28201, Secondary Plumbing | Admin Backend |
| Lead Time/Buffer | Days advance notice | HVAC: 2 days, Electrical: 6 days | Admin Backend |
| Availability Windows | Time slots | Mon-Fri 8-12, 1-5; Sat 9-1 | Admin Backend |
| Work Days | Days available | Plumbing: Tue/Thu only, HVAC: Mon-Fri | Admin Backend |
| Licensing | License numbers, expiration | NC-12345 exp 12/31/2025 | CRM |
| Insurance | Certificate, expiration | $2M liability, exp 6/30/2026 | CRM |
| Background Checks | Technician verification | All techs checked annually | CRM |
| Pricing | Negotiated rates per service | Water heater replace: $850 | CRM (not in app MVP) |

**Quote from Kevin**: "I would like to know exactly how much that contractor charges for each type of activity they would do for us and have that in a systematic database... That right now is not loaded. We do collect some of that information in our contract negotiations up front."

### Multi-Trade Contractor Configuration

**Challenge**: Contractor offers multiple trades with different availability per trade

**Example**: ABC Home Services
- **Trade 1: HVAC**
  - Primary contractor for zip codes: 28201, 28202, 28203
  - Lead time: 2 business days
  - Availability: Monday-Friday, 8am-5pm
  - Time windows: 8-12, 1-5
- **Trade 2: Plumbing**
  - Primary contractor for zip codes: 28201, 28202
  - Secondary contractor for zip codes: 28203, 28204
  - Lead time: 3 business days
  - Availability: Tuesday-Thursday only
  - Time windows: 9-12, 1-4
- **Trade 3: Electrical**
  - Secondary contractor for zip codes: 28201, 28202
  - Lead time: 6 business days
  - Availability: Monday, Wednesday, Friday only
  - Time windows: 8-12 only

**Data Model Requirement**: Separate configuration per contractor + trade combination

**Quote from Ed Carr**: "Many of those contractors handle those businesses as separate businesses. So it'd be almost like three separate businesses."

### Contractor Availability - How It Works

**Current State** (No Systematic Tracking):
- Contractors do not provide real-time availability calendar
- Duke does not have visibility into contractor's full schedule (they schedule non-Duke work too)
- Lead time/buffer is used as availability proxy (e.g., "HVAC contractor available starting 2 days from now")

**MVP Approach** (Static Availability Rules):

**Option 1: Static Buffer** (RECOMMENDED FOR MVP)
- Contractor provides: "Always available starting X days from request"
- System calculates: Today + buffer = first available date
- Shows customer: Windows starting on first available date
- **Pros**: Simple, no contractor input needed, 90%+ acceptance rate
- **Cons**: Not true real-time availability, may offer slots contractor can't fulfill

**Example**: HVAC contractor has 2-day buffer
- Customer requests service Monday 2pm
- System offers: Wednesday 8-12, Wednesday 1-5, Thursday 8-12, Thursday 1-5...
- Customer selects: Thursday 8-12
- Admin sends to contractor, contractor accepts/proposes alternative

**Option 2: Calendar-Based** (FUTURE - PHASE 2)
- Contractor provides: Available/blocked dates in calendar
- System checks: Contractor schedule before showing customer
- Requires: FSM tool with contractor mobile app
- **Pros**: True real-time availability
- **Cons**: Requires contractor to maintain calendar, high burden

**Quote from Kevin**: "We won't have their schedule. So we won't have the contractor scheduling because they can schedule for other work outside of our work with those technicians... We won't have that at all, even in an FSM scenario."

**90-95% Acceptance Target**:
- Goal: 90-95% of time slots offered to customers are accepted by contractors
- Achieved through: Conservative buffers (3-5 day minimums), contractor SLA contracts
- When contractor declines: Admin manually reschedules

### Contractor Data Sync Strategy

**Phase 1 MVP** (Manual Data Export/Import):

**Initial Setup**:
1. Duke exports contractor data from Commerce CRM
2. File includes: Contractor list, trade assignments, zip code assignments, primary/secondary designations
3. Orases imports into app backend database
4. Admin team configures additional fields (lead time, availability windows)

**Ongoing Maintenance**:
1. Contractor changes (new contractor, territory change, etc.) happen in CRM first
2. Admin team manually updates app backend to match
3. Frequency: As-needed (contractor changes are rare, ~1-2 per year)

**Quote from Kevin**: "We would have to do that today mainly anyway. And we do it today. We have to override the zip code eligibility, et cetera. Not frequently, it just happens that we have contractor that goes out, especially in the mom and pop areas that we have to get backup."

**Phase 2** (API Integration):
- Real-time API to read contractor data from CRM
- Nightly sync to keep app backend updated
- Potential FSM tool integration for availability

---

## 5. PHASE 1 CONTRACTOR PORTAL SCOPE

### The Big Decision: What to Build for Contractors in MVP?

**Options Evaluated**:

| Option | Description | Pros | Cons | Timeline | Cost | DECISION |
|--------|-------------|------|------|----------|------|----------|
| **Option A: Minimal Enhancements** | Keep existing portal, add integration hooks for app | Contractors keep familiar system, focus on customer app | Contractors don't see improvements, manual admin work | 44 weeks | Lowest | Possible |
| **Option B: New Mobile App** | Build contractor iOS/Android app with real-time updates | Modern UX, mobile-first, pizza tracker | Requires FSM tool, significant dev time, contractor adoption risk | 60+ weeks | Highest | **NO** - Phase 2 |
| **Option C: Hybrid** | Enhance portal + lightweight mobile for status updates | Contractors have options | Maintain two systems, still complex | 52 weeks | Medium-High | **NO** - Too complex |
| **Option D: Admin-Only** | No contractor changes, all managed via admin backend | Maximum customer app focus, learn from MVP first | Contractors use same old system, admin workload higher | 44 weeks | Lowest | **YES** ✅ |

**✅ DECISION: Option D - Admin-Only for Phase 1 MVP**

**Rationale**:
1. **Focus 100% on Customer App**: Customer app drives revenue ($25M ad-hoc services target)
2. **Contractor Portal is Functional**: Existing Commerce portal works, contractors are familiar
3. **Learn from MVP First**: Understand customer needs before investing in contractor features
4. **FSM Tool Dependency**: Robust contractor mobile app requires FSM integration (not ready for Phase 1)
5. **Manual Admin Updates Acceptable**: Back office can update statuses based on contractor communication for MVP
6. **Phase 2 Investment**: Build modern contractor mobile app after FSM tool selected and customer app proven

**Quote from Kevin**: "Consider that that's a gap right now for phase one. We need to fill... I would say that don't consider [FSM] as part of phase one."

**Quote from Son**: "For MVP, though, we're matching the same way, right? We're matching to a primary, no matter what service that is, and that's who they get."

### What Contractors Continue Using (No Changes)

**Existing Contractor Portal** (Direct Access to Commerce CRM):
- Receive job assignments
- View service request details (customer name, address, problem description)
- Schedule appointments with customers
- Update service request status (accepted, scheduled, dispatched, in-progress, completed, invoiced)
- Enter completion details (services performed, parts used, time spent)
- Submit invoices

**Communication Methods**:
- Email notification when new job assigned
- Phone calls to/from Duke back office
- Direct phone/SMS with customers (contractors have customer phone numbers)

**Their Own Systems**:
- Contractors use their own dispatch software (Service Titan, Housecall Pro, etc.)
- Contractors manage technician schedules internally
- Contractors send their own lifecycle communications (~70% provide en-route notifications, etc.)

**Quote from Kevin**: "The contractor is going through that entire lifecycle on their side, with some people with most of it being done by their admin, their back office is moving it through those respective stages."

### What Admin Backend Manages (New for App)

**Contractor Configuration** (Admin Portal Features):
- CRUD operations for contractors (Create, Read, Update, Delete)
- Assign trades to contractors (multi-select: HVAC, Plumbing, Electrical, etc.)
- Assign service areas (zip code list per contractor)
- Set primary/secondary designation per trade + zip code
- Configure lead time/buffer per contractor per trade
- Configure availability windows (time slots, days of week)
- View contractor performance metrics (once collected)
- Override assignments for exceptions (emergencies, capacity issues)

**Service Request Status Management** (Admin Portal):
- View pending service requests from customer app
- Manually send service request to contractor (email/phone for MVP)
- Update status when contractor confirms: "Confirmed - [Contractor Name] - [Date/Time]"
- Update status when contractor completes: "Completed - [Date]"
- Handle reschedules/cancellations (update app, notify customer)

**Quote from Kevin**: "The latter with the caveat, though... we will default based off our default logic. So we have a primary contractor that we will send out."

---

## 6. CONTRACTOR WORKFLOWS

### Workflow 1: HPP Covered Service Request (Warranty Work)

**Happy Path**:

1. **Customer Creates Service Request in App**
   - Describes problem (symptom-based, not technical diagnosis)
   - Confirms which appliance/system (adds to inventory if not already there)
   - Selects preferred date/time window from available options
   - Sees pre-assigned primary contractor: "ABC Plumbing will service your request"

2. **App Backend Matches Contractor**
   - Identifies trade (plumbing)
   - Customer zip code (28201)
   - Queries contractor table: primary contractor for plumbing + 28201
   - Returns: ABC Plumbing with availability windows (Tue/Thu 9-12, 1-4, 3-day buffer)
   - Customer selects: Thursday 9-12 (3 days from now)
   - Service request status: "Pending Confirmation"

3. **Admin Reviews Service Request**
   - Sees new request in admin dashboard
   - Reviews details: Customer info, problem, contractor, requested time
   - **MVP**: Admin manually communicates to contractor (email/phone)
   - "Hi ABC Plumbing, we have a service request for Thursday 9-12 at 123 Main St, customer Jane Doe, leaking faucet"

4. **Contractor Receives Assignment**
   - Checks schedule (in their own system)
   - Scenario A: Accepts Thursday 9-12 → Notifies Duke admin (email/portal update)
   - Scenario B: Proposes alternative → "Can't do Thursday 9-12, can do Friday 1-4"

5. **Admin Confirms with Contractor (Scenario A - Accept)**
   - Contractor accepts proposed time
   - Admin updates service request status in app: "Confirmed - ABC Plumbing - Thursday 9-12am"
   - App sends notification to customer: "Your service is confirmed! ABC Plumbing on Thursday 9-12am"

6. **Admin Negotiates Alternative (Scenario B - Counteroffer)**
   - Contractor proposes Friday 1-4
   - Admin evaluates:
     - Option 1: Accept alternative, update app, notify customer
     - Option 2: Call customer to confirm new time
     - Option 3: Try backup contractor for original time
   - **MVP**: Admin calls customer to confirm Friday 1-4
   - If customer accepts: Update app status: "Confirmed - ABC Plumbing - Friday 1-4pm"

7. **Contractor Calls Customer** (Current Process Continues)
   - Contractor directly calls customer to re-confirm appointment
   - Provides technician name, ETA, any prep instructions
   - Updates customer on any changes

8. **Service Day - Contractor Workflow** (No Change)
   - Contractor dispatches technician
   - Technician goes to customer home, performs service
   - Technician collects payment if over coverage limit (customer pays excess)
   - Contractor updates Commerce portal: "Completed - [date] - Services performed: [description]"

9. **Admin Updates App After Completion**
   - Admin sees contractor marked service as complete in Commerce
   - Admin updates app service request status: "Completed - [date]"
   - App displays in customer's service history
   - Duke sends customer survey via existing process (email)

**Timeline**:
- Customer books: Monday 2pm
- Admin processes: Monday 3pm (within 1 hour goal)
- Admin contacts contractor: Monday 3:15pm
- Contractor responds: Monday 5pm or Tuesday morning (within 24 hours)
- Admin confirms in app: Tuesday 10am
- Service window: Thursday 9-12am (3-day buffer from request)

**Quote from Kevin**: "For phase one, when we get the API built, it will supply that history of that contractor, that service order history back. It just probably wouldn't be an MVP. So we have to think about it maintaining."

### Workflow 2: Ad-Hoc Service Request (Cash-Pay Customer)

**Happy Path**:

1. **Customer Browses Ad-Hoc Service Catalog**
   - Non-native customer (or Duke customer wanting non-covered service)
   - Browses services: "HVAC Tune-Up - $99", "Ceiling Fan Installation - $120-190"
   - Selects: "HVAC Tune-Up - $99"
   - Enters zip code: 28201

2. **App Matches Contractors (Same Logic)**
   - System identifies: Primary HVAC contractor for 28201 = XYZ HVAC
   - Shows availability: "First available: Wednesday, 3-day lead time"
   - Customer selects: Wednesday 1-5pm window
   - Payment note: "Payment collected by contractor on-site (cash, check, credit card)"

3. **Admin Processing** (Same as Workflow 1)
   - Admin reviews ad-hoc service request
   - Contacts XYZ HVAC contractor: "Ad-hoc service, $99 HVAC tune-up, customer pays you directly"
   - Contractor accepts Wednesday 1-5pm
   - Admin updates app: "Confirmed - XYZ HVAC - Wednesday 1-5pm"

4. **Payment at Completion**
   - Contractor performs service
   - **MVP**: Contractor collects $99 from customer (cash, check, or contractor's credit card reader)
   - Contractor reports payment to Duke (for commission tracking if applicable)

5. **Future State** (Phase 2 with Payment API):
   - Customer pre-pays $99 in app (credit card, Apple Pay)
   - Duke collects $99, pays contractor $75 (net of $24 commission)
   - Customer pays nothing on-site

**Quote from Kevin**: "Phase 1 - contractor collects payment on-site... The ad hoc services, where the customer is going to pay the contractor directly... if you want some X, Y, Z, because it's not going to be like what Chris was saying, where they're trying to get some exception made or they have a back-end deal with the contractor, it doesn't matter because they're a cash customer versus a warranty customer."

### Workflow 3: Emergency Service Request (NOT in App - Phone Only)

**Scenario**: Customer has no heat in winter, or smells gas, or has sparking outlet

**App Triage Flow**:

1. **Customer Starts Service Request**
   - Selects: "HVAC not working"
   - App asks qualifying questions:
     - "Is your home temperature below 60°F?"
     - "Is it currently below freezing outside?"
     - "Do you smell gas?"
     - "Is anything sparking or smoking?"

2. **Emergency Detected**
   - Based on answers, app determines: Emergency
   - App displays: "⚠️ This appears to be an emergency. Please call us immediately at 1-800-XXX-XXXX"
   - For gas leaks: "⚠️ SAFETY ALERT: If you smell gas, evacuate immediately and call your gas utility emergency line: 1-800-XXX-XXXX"
   - App does NOT create service request (routed to phone)

3. **CSR Handles Emergency**
   - Customer calls Duke emergency line
   - CSR collects details, determines urgency
   - CSR directly calls primary contractor: "Emergency - need immediate dispatch"
   - CSR negotiates soonest available time (2-4 hours for true emergencies)
   - CSR confirms with customer

4. **Optional: Admin Adds to App for Tracking**
   - After phone resolution, admin can manually create service record in app
   - Customer sees service history: "Emergency HVAC Repair - [Date] - XYZ HVAC"
   - Helps track all customer interactions in one place

**Quote from Kevin**: "We will have those emergency questions. It won't be a clear cut, hey, is this an emergency for a customer? It will be based off those criteria that they filled in. We'll determine this emergency and hey, call in, go down a flow."

**Quote from Dana**: "Most customers would say everything's an emergency, but there's a handful of things that we can definitely help with that should feed through the app, no problem. And then there's a smaller set of things that should be call us for the emergency."

### Workflow 4: Contractor Declines or Reschedules

**Scenario**: Primary contractor cannot fulfill requested time

**Path 1: Contractor Declines Before Confirmation**
1. Admin sends request to primary contractor
2. Primary contractor responds: "Cannot service Thursday 9-12, can do Friday 1-4"
3. Admin evaluates options:
   - **Option A**: Accept contractor's alternative time
   - **Option B**: Try backup contractor for original Thursday 9-12 time
4. **MVP Decision**: Prioritize keeping original time window if possible
5. If backup contractor available for Thursday 9-12:
   - Admin assigns to backup
   - Updates app: "Confirmed - Backup Plumbing LLC - Thursday 9-12"
   - Customer may not even know primary contractor wasn't available
6. If no one available for Thursday 9-12:
   - Admin calls/texts customer: "Original time not available, contractor can do Friday 1-4. Does this work?"
   - Customer accepts or requests different time
   - Admin updates app with final confirmed time

**Quote from Kevin**: "That's a fantastic question. I will say that we don't necessarily know by default what should happen next... Most likely the person in the back office that is maintaining that order that identifies, hey, the contractor rejected this time, should look to see and call the backup contractor and say, hey, can you service this time so we can try to keep that window as much as possible?"

**Path 2: Contractor Needs to Reschedule After Confirmation**
1. Service already confirmed: "Thursday 9-12am - ABC Plumbing"
2. Contractor has emergency (e.g., family issue, truck breakdown)
3. Contractor calls Duke admin: "Need to reschedule Thursday appointment"
4. Admin immediately notifies customer:
   - Push notification + SMS: "Your Thursday appointment needs to be rescheduled"
   - Admin calls customer to apologize and offer alternatives
5. Admin reassigns to backup contractor OR reschedules with same contractor
6. Admin updates app with new confirmed time
7. App shows updated appointment

**Frequency**: Rare (less than 5% of appointments)

**Quote from Ed Carr**: "The only time it happens is really when we have brush orders and the primary contractor is not available. I would say probably less than 5% of the time."

### Workflow 5: Customer Requests Different Contractor

**Scenario**: Customer doesn't want assigned contractor (past bad experience)

**MVP Approach**:

1. **Customer Sees Assignment**
   - App shows: "Your service will be provided by ABC Plumbing"
   - Small link: "Need a different contractor?"

2. **Customer Clicks Link**
   - App displays: "Please call us at 1-800-XXX-XXXX to request an alternative contractor"
   - Or: "Text REQUEST CHANGE to 12345 with your service request number"
   - **MVP does NOT show list of alternative contractors in app**

3. **Admin Handles Request**
   - Customer calls/texts
   - Admin asks reason (to track patterns)
   - Admin checks if backup contractor available
   - Admin confirms new contractor with customer
   - Admin updates app: "Confirmed - Backup Plumbing LLC - Thursday 9-12"

4. **Edge Case: Customer Keeps Requesting Different Contractors**
   - Admin notes account for potential "contractor shopping"
   - May require manager approval for multiple changes
   - Protects against customers gaming system to find contractor who will cover exclusions

**Quote from Chris Murphy**: "One of the challenges with that is customers become very strategic. So they get one contractor who knows their situation and knows that something's not covered because it's a code violation. Then they start going through the contractor list and saying, well, I want someone else out here... until they try to find the right one who will cover something that should not be covered."

**Future State** (Phase 2 with Ad-Hoc Marketplace):
- For cash-pay ad-hoc services, customer may see 2-3 contractor options
- Customer selects based on price, availability, ratings
- No "gaming" risk since customer pays directly

---

## 7. CONTRACTOR COMMUNICATION & LIFECYCLE UPDATES

### Current Contractor Communication

**Today's Process**:
- **Assignment**: Email notification to contractor when job assigned
- **Scheduling**: Contractor calls customer within 48 hours to schedule
- **Confirmation**: Contractor confirms time in Commerce portal (hit or miss)
- **Day-Before**: ~70% of contractors send reminder text/call to customer
- **En Route**: ~70% of contractors send "on my way" text to customer
- **Completion**: Contractor updates Commerce portal when job completed
- **Survey**: Duke sends customer survey after completion (external process)

**Quote from Kevin**: "Once we've created that order, we handed off that customer communication to the contractor to do up until the point that they've completed it... Now we have some of that transparency in the database as long as they're updating it, but the consistency of whether they update it is a challenge."

### MVP Communication Strategy

**Communication Touchpoints Provided by App/Admin**:

1. **Booking Confirmation** (Customer App → Customer)
   - "We received your service request"
   - Pending confirmation from contractor

2. **Contractor Assignment** (Customer App → Customer)
   - "Your contractor has been assigned: ABC Plumbing"
   - Contact info provided

3. **Appointment Confirmation** (Admin → Customer App → Customer)
   - "Your appointment is confirmed: Thursday 9-12am with ABC Plumbing"
   - SMS + push notification + email (per customer preference)

4. **Day-Before Reminder** (App → Customer) - OPTIONAL FOR MVP
   - "Reminder: ABC Plumbing coming tomorrow 9-12am"
   - May conflict with contractor's own reminders

5. **Reschedule Notification** (Admin → Customer App → Customer)
   - "Your appointment time has changed"
   - New date/time displayed

6. **Completion Notification** (Admin → Customer App → Customer)
   - "Your service has been completed"
   - Survey link (existing external process continues)

**Communication Provided by Contractor** (No Change):
- Day-before reminder call/text
- "On my way" text
- "Running 15 minutes late" text
- Post-service follow-up

**Quote from Kevin**: "Most of our contractors already have in their system a process doing that. So they already are sending notifications that are coming out there, text notification, all that stuff."

### Challenge: Data Sync Between Contractor & App

**Problem**: Contractor may reschedule with customer without updating Duke systems

**Example**:
- App shows: "Thursday 9-12am appointment confirmed"
- Contractor calls customer Tuesday: "Can we move to Friday 1-4pm instead?"
- Customer agrees
- Contractor updates their own system (Service Titan, etc.)
- Contractor does NOT immediately update Duke Commerce portal
- App still shows Thursday 9-12am (out of sync)

**MVP Solution**:
- Accept that data may be temporarily out of sync
- Contractor updates Commerce when completing job (source of truth)
- For MVP, don't send automated reminders that could conflict
- Admin manually updates app if they're informed of changes

**Phase 2 Solution** (FSM Tool):
- FSM tool integrated with contractor's dispatch software
- Real-time sync between contractor system ↔ FSM tool ↔ Duke app
- Automated status updates
- GPS tracking

**Quote from Chris Murphy**: "One of the challenges would be if a contractor changes an appointment with the customer for some reason and doesn't go into our system and change it immediately and the customer starts getting notifications that, hey, we're coming in 24 hours when the contractor has made other arrangements with the customer."

### In-App Messaging (NOT in MVP)

**Future Consideration** (Phase 2):
- Customer ↔ Contractor in-app chat (like Uber)
- Keeps communication within app
- Privacy protection (no phone numbers exposed)
- Message history tracked

**MVP**: Continue using phone/SMS for direct communication

**Quote from Aksana**: "MVP: Phone/SMS communication continues (no in-app messaging Phase 1)"

---

## 8. PAYMENT & INVOICING

### HPP Covered Service Payment (No Customer Payment)

**Current Process**:
1. Contractor performs covered service at no charge to customer
2. Contractor invoices Duke for negotiated rate
3. Duke pays contractor (e.g., $500 for covered repair)
4. Customer pays $0 out-of-pocket

**If Service Exceeds Coverage**:
1. Contractor identifies issue exceeds coverage limits (e.g., code violation, additional parts needed)
2. Contractor provides quote for excess work to customer
3. Customer pays contractor directly for excess amount (cash, check, contractor's credit card reader)
4. Contractor invoices Duke for covered portion
5. Example: Service requires $800 repair, plan covers $500, customer pays contractor $300

**Quote from Kevin**: "Warranty covered: Duke pays contractor. Excess/over coverage: Customer pays contractor directly."

### Ad-Hoc Service Payment

**Phase 1 MVP - Contractor Collects On-Site**:

1. **At Booking**:
   - App displays service price: "HVAC Tune-Up - $99"
   - Payment note: "Payment collected by contractor on-site (cash, check, credit card)"
   - Customer books service

2. **At Service Completion**:
   - Contractor performs service
   - Contractor collects $99 from customer using their own payment method:
     - Cash
     - Check
     - Credit card via contractor's Square/Stripe/Clover reader
   - Contractor provides receipt to customer

3. **Contractor Reporting to Duke**:
   - Contractor updates Commerce portal: Service completed
   - Contractor reports payment collected (for Duke's ad-hoc service tracking)
   - If Duke takes commission: Contractor invoices Duke for their net amount
   - Example: Customer pays contractor $99, Duke takes $24 commission, contractor keeps $75 and invoices Duke for $24? (commission model TBD)

**Quote from Kevin**: "Phase 1 - contractor collects payment on-site."

**Commission Model (TBD)**:
- Does Duke take a percentage of ad-hoc services?
- If yes: How much? (e.g., 20% = $20 on $99 service)
- How is commission collected? Deducted from contractor payment? Invoiced separately?
- How does contractor report cash payments?

**Phase 2 - App-Based Payment**:

1. **At Booking**:
   - Customer enters credit card, Apple Pay, Google Pay
   - Customer pre-pays $99 in app
   - Duke collects $99

2. **After Service**:
   - Duke pays contractor their portion (e.g., $75 if 20% commission)
   - Contractor paid via direct deposit or check
   - Customer already paid, no on-site payment collection needed

3. **Benefits**:
   - Customer convenience
   - Payment tracking in app
   - Reduces contractor burden
   - Duke captures commission automatically

**Quote from Kevin**: "Future: Customer pays Duke via app → Duke pays contractor."

### Contractor Invoicing to Duke

**Current Process** (Continues for MVP):
1. Contractor completes service
2. Contractor updates Commerce portal with completion details:
   - Services performed
   - Parts used
   - Labor hours
   - Total cost
3. Contractor invoice created in Commerce
4. Duke back office reviews and approves
5. Contractor paid via check or direct deposit (Net 30 terms typically)

**For App MVP**:
- No changes to contractor invoicing process
- Contractor continues using Commerce portal for invoicing
- Admin updates app service request status to "Completed" after contractor invoices

---

## 9. CONTRACTOR PERFORMANCE & RATINGS

### Current Contractor Performance Tracking

**Customer Surveys** (Existing Process):
- After service completion, Duke sends email survey to customer
- Survey managed by external market research vendor
- Questions include:
  - Overall satisfaction (1-5 stars)
  - Contractor professionalism
  - Timeliness
  - Work quality
  - Would you recommend?

**Duke Uses Survey Data For**:
- Aggregate reporting to contractor (monthly/quarterly scorecards)
- Identifying low-performing contractors for improvement plans
- Deciding whether to renew contractor agreements
- Does NOT currently factor into contractor assignment algorithm

**Quote from Kevin**: "It ends up in our market research database, so we get that information report out on it internally and report it back out to the contractors, sometimes at an aggregate level."

### MVP Approach - No Change to Ratings Collection

**Phase 1**:
- Continue external survey process
- Ratings NOT collected in-app for MVP
- Ratings NOT displayed in-app for MVP
- Contractor assignment based solely on primary/secondary designation, NOT ratings

**Why Defer In-App Ratings**:
- External survey process already established
- Legal/compliance review needed for in-app reviews
- Want to avoid "Yelp effect" where customers shop for highest-rated contractor
- Maintaining contractor relationships (small network, don't want to create tension)

**Quote from Kevin**: "No. It's the primary contractor. We'll consider it in the fact that they'll be our primary contractor or not... most of those are going to be fine. And if we do end up with a situation which we've had rarely, you know, on occasion, what we'll do is replace the contractor."

### Future State - In-App Ratings (Phase 2+)

**For Ad-Hoc Marketplace Services**:
- Display contractor ratings and reviews in app
- Customer can see: "ABC Plumbing - 4.8 stars - 127 reviews"
- Customer reads recent reviews before booking
- Customer submits rating immediately after service (in-app)
- Ratings factor into contractor recommendations

**Quote from Joshua Gilstrap**: "Kevin, is there a possibility that in the future we would want to collect that rating or survey through the app and maybe show that rating on a contractor profile for those ad hoc services?"

**Quote from Kevin**: "Yes."

**Benefits**:
- Customer confidence in contractor selection
- Incentivizes contractor performance
- Competitive marketplace dynamic
- Real-time feedback vs. delayed survey

**Risks**:
- Low-rated contractors may lose work
- Small contractor network (may not have alternatives)
- Contractors may push back on public ratings
- Need process for disputing unfair reviews

---

## 10. INVENTORY DATA COLLECTION FROM CONTRACTORS

### The Opportunity

**Problem**: Customers don't know what appliances/systems they have
- Make/model/serial numbers not readily accessible
- Age of equipment unknown
- Customer-entered data often incomplete or inaccurate

**Solution**: Contractors capture inventory during service visits
- Technician is already at appliance/system
- Can easily read data plate (make, model, serial, manufacture date)
- Photos of data plate uploaded to app
- Customer profile automatically updated with accurate data

**Benefits**:
- **For Customer**: Automated home inventory, no effort required
- **For Duke**: Better service delivery with accurate equipment data
- **For Contractor**: More targeted future work (know when equipment end-of-life approaching)

**Quote from Aksana**: "One thing we'll have to solve for new data like inventory, right? Because right now, we're kind of assuming that we're dealing with the same data that already exists... we want contractors to provide after the service has been served, perhaps they can add feedback comments as far as this is the model, this is the year, so we can upgrade that customer profile for the future improvements."

### MVP Scope Question: How to Implement?

**Challenge**: Contractor portal not being rebuilt for MVP

**Options**:

**Option 1: Manual Process - Admin Enters Data**
- Contractor takes photo of data plate during service
- Contractor emails/texts photo to Duke admin
- Admin manually enters data into customer profile in app admin backend
- **Pros**: No contractor system changes needed
- **Cons**: High admin burden, slow data entry

**Option 2: Contractor Portal Simple Form**
- Add lightweight form to existing Commerce portal
- Contractor enters: Make, Model, Serial Number, Manufacture Date
- Form submits data to app backend API
- **Pros**: Direct data flow, faster entry
- **Cons**: Requires minor contractor portal enhancement (may violate "no contractor changes" decision)

**Option 3: Defer to Phase 2**
- No inventory collection from contractors for MVP
- Rely on customer-entered data only
- Phase 2: Build into contractor mobile app
- **Pros**: Simplest for MVP
- **Cons**: Missed opportunity to build high-quality inventory data

**Recommendation**: Option 2 if feasible, otherwise Option 3

**Quote from Kevin**: "Yes, 100%. That's a great call out. How do we collect that information from the contractor to feed it back into the database that will probably not exist inside of Commerce to be able to communicate it back through the Commerce database. Now, we may have to think about that in the future, Joshua, of, you know, do we have a place for them to update the order itself so that it feeds back over? And then we feed that back over to the app, etc."

### Contractor Incentive Model (TBD)

**Question**: How do we incentivize contractors to capture inventory data?

**Options**:
1. **No Additional Payment**: Part of service expectations, tied to SLA
2. **Small Per-Item Bonus**: $5-10 per appliance/system documented
3. **Gamification**: Contractor leaderboard, recognition for most data captured
4. **Future Work Pipeline**: "You capture data now, you know when equipment needs replacement, you get the replacement job"

**Requires Discussion With**:
- Contractor field coordinators
- Chris Murphy's contractor network team
- Contract negotiation team

**Quote from Kevin**: "Correct. And so stuff like that would be stuff we would have to ask them to do outside. And I think that that's a different ask that we can do. We definitely would want to do and ask for them to do... what that will do is provide us more information about the home. So we'll know what parts you need, et cetera. And they'll see the benefit of that."

---

## 11. FSM TOOL INTEGRATION (PHASE 2)

### Current FSM Limitations

**Today's FSM**:
- Internal SAP-based system
- Limited functionality
- No mobile contractor app
- No GPS tracking
- No real-time status updates
- No integration with contractor dispatch software

**Quote from Kevin**: "I would say that don't consider [FSM] as part of phase one."

### FSM Tools Under Consideration

**Vendors Being Evaluated**:
1. **Service Power** - Field service management platform
2. **Service Bench** - Contractor network management
3. **NOT Service Channel** - Ruled out

**Quote from Session 1**: "Future FSM tools: Service Power, Service Bench under consideration."

**FSM Tool Capabilities Needed**:
- Contractor mobile app (iOS/Android)
- Real-time job assignment and acceptance
- GPS tracking of technician location
- Automated status updates (dispatched, en route, on-site, completed)
- Integration with contractor dispatch software (Service Titan, Housecall Pro, etc.)
- Customer notifications based on technician location
- Two-way messaging between customer and contractor
- Digital completion forms (photos, parts used, customer signature)
- Automated invoicing

### Phase 2 Architecture (With FSM Tool)

**Data Flow**:

Customer App ↔ Duke App Backend ↔ **FSM Tool** ↔ Contractor Mobile App
                                    ↕
                              Commerce CRM

**Workflow Changes**:

1. **Customer Books Service in App**
   - Service request sent to app backend
   - App backend sends to FSM tool via API

2. **FSM Tool Assigns to Contractor**
   - FSM tool queries contractor availability (real-time calendar)
   - FSM tool sends push notification to contractor mobile app
   - Contractor sees job details in mobile app

3. **Contractor Accepts in Mobile App**
   - One-tap acceptance
   - FSM tool notifies Duke app backend
   - Duke app updates customer: "Confirmed!"

4. **Day of Service**:
   - Contractor marks "Dispatched" in mobile app
   - Customer sees: "Your technician is on the way"
   - GPS tracking enabled (pizza tracker)
   - Customer sees: "Technician is 15 minutes away"

5. **At Customer Home**:
   - Contractor marks "On-Site" in mobile app
   - Timer starts (for performance tracking)
   - Customer sees: "Technician has arrived"

6. **Service Completion**:
   - Contractor completes digital form in mobile app
   - Takes photos of completed work
   - Captures customer signature
   - Submits completion
   - FSM tool syncs to Commerce CRM for invoicing
   - Customer app immediately shows "Completed"
   - Customer prompted to rate contractor in-app

**Quote from Kevin**: "If we can get an FSM software that's integrated into their Service Titan or whatever they're using from their dispatching side, that's better because it'll make sure that we're better aligned with our contractors through their journey."

### Pizza Tracker Feature (Phase 2)

**Customer View**:
- Map showing technician location (like Uber)
- Estimated arrival time
- "John from ABC Plumbing is 12 minutes away"
- Auto-updates as technician moves

**Requirements**:
- FSM tool with GPS tracking
- Contractor mobile app running in background
- Real-time location sharing enabled
- Privacy controls (location only shared when dispatched to job)

**Quote from Aksana**: "In ideal world, you want kind of both of these entities have their own rooms in your house, right? Contractors have an app, customer has an app, and the data just bounce back and forth."

**Quote from Kevin**: "The FSM software that we looked at was they had tracking like that, so if it was all that for some software is on the technicians app or on their phone then it would actually track where they are and if they say they're dispatching it only releases that location whenever there it's been identified that they're dispatching to that customer."

---

## 12. PHASE 1 DEPENDENCIES & INTEGRATIONS

### Critical Data Exports from Duke (Required for MVP)

**1. Contractor Master List**
- **Format**: CSV or JSON export
- **Frequency**: One-time initial load, then as-needed updates (rare)
- **Data Fields**:
  - Contractor ID
  - Contractor Name
  - Business Name
  - Contact Phone
  - Contact Email
  - Primary Contact Name
  - Status (Active/Inactive)

**2. Contractor Trade Assignments**
- **Format**: CSV or JSON
- **Frequency**: One-time initial, then manual updates
- **Data Fields**:
  - Contractor ID
  - Trade (HVAC, Plumbing, Electrical, Water Heater, Appliance)
  - Certification/License Numbers

**3. Contractor Zip Code Assignments**
- **Format**: CSV or JSON export (example provided in meeting)
- **Frequency**: One-time initial, then as-needed updates
- **Data Fields**:
  - Zip Code
  - Trade
  - Primary Contractor ID
  - Backup Contractor ID(s)

**Example from Ed Carr** (shown in meeting chat):
```
Zip Code: 28210
Trade: HomeWire
Primary: CNTR-001 (ABC Electric)
Backup: CNTR-045 (XYZ Electric)

Zip Code: 28210
Trade: HVAC
Primary: CNTR-012 (Cool Air Services)
Backup: CNTR-033 (Best HVAC)
```

**Quote from Ed Carr**: "What I put in the chat is actually an example of what the file is. And so you can see that's basically a zip code where I live. These are all those are the programs that are available. And then those are the contractors, including their IDs, including their backup contractors."

**4. Service Eligibility by Zip Code**
- **Format**: CSV or JSON
- **Data Fields**:
  - Zip Code
  - Plan Type (HomeWire, HVAC, Plumbing, Water Heater, Appliance)
  - Eligible (Yes/No)

**Purpose**: Show customer which plans available in their area

**Quote from Kevin**: "So we will give you the eligibility criteria. So then that way, you know, hey, for the zip code, these plans are available."

### Manual Admin Processes (MVP Acceptable)

**Service Request Handoff** (App → Contractor):
- **Current**: Admin manually emails/calls contractor with new service request
- **Data Required**: Service request details from app admin dashboard
- **Timeline**: Admin processes within 1 hour of customer booking
- **Acceptable for MVP**: Yes, 125 contractors with SLAs can handle this

**Status Updates** (Contractor → App):
- **Current**: Admin manually updates app when contractor confirms/completes
- **Data Source**: Contractor phone/email communication + Commerce portal updates
- **Frequency**: 2-3 updates per service request (confirmed, completed)
- **Acceptable for MVP**: Yes, manageable volume for back office team

**Quote from Kevin**: "For phase one, when we get the API built, it will supply that history of that contractor, that service order history back. It just probably wouldn't be an MVP."

### Phase 1 API Integrations (If Available - Not Required for MVP)

**Service Request Creation API** (App → Commerce CRM):
- **Endpoint**: POST /service-requests
- **Payload**: Customer ID, Service Type, Zip Code, Problem Description, Requested Time
- **Response**: Service Request ID, Assigned Contractor ID
- **Benefit**: Eliminates manual admin entry into CRM

**Service History API** (Commerce CRM → App):
- **Endpoint**: GET /customers/{id}/service-history
- **Response**: List of past service requests with dates, contractors, outcomes
- **Benefit**: Show customer complete service history in app
- **Not MVP**: Nice to have, not required for launch

**Quote from Kevin**: "So we will have all the service history for whether they called in or did the app. That will be part of the API as part of phase one. Not the MVP, but as part of phase one, that will be returned."

---

## 13. OPEN QUESTIONS & RISKS

### Unresolved Items from Meeting

#### Contractor Network Questions

**1. P&G Internal Employees vs. Duke Third-Party Contractors**:
- **Question**: How many P&G internal employees? Do they use same portal as Duke contractors?
- **Decision Made**: TBD - Need clarification from Duke team
- **Risk**: Internal employees may have completely different workflow, data model, and portal needs
- **Impact**: Could require separate features or workflows for employee vs. contractor

**2. Contractor Availability Tracking**:
- **Decision Made**: Use static buffer (e.g., 3-day lead time) for MVP
- **Still Unclear**: How do contractors communicate vacation/unavailability? Who updates app backend?
- **Risk**: Customer books time that contractor cannot fulfill

**3. Contractor Specialization - Multi-Trade Details**:
- **Decision Made**: Contractors can serve multiple trades
- **Still Unclear**: Data model for trade-specific availability (does each trade get separate config record?)
- **Risk**: Complex data model, difficult for admin to configure

**4. Primary/Secondary Tier Determination**:
- **Question**: What makes a contractor "primary" vs. "secondary"? Performance? Pricing? Territory size?
- **Discussion**: Negotiated contracts, not dynamic based on ratings
- **Still Unclear**: Can secondary be promoted to primary? What's the criteria?

**5. Exception Handling - All Contractors at Capacity**:
- **Question**: What happens if primary and all backups decline?
- **Discussion**: Rare scenario (90%+ acceptance rate)
- **Still Unclear**: Does system automatically extend time windows? Or admin manually intervenes?

#### Payment & Invoicing Questions

**6. Ad-Hoc Service Commission Model**:
- **Question**: Does Duke take a percentage of ad-hoc services? If yes, how much?
- **Discussion**: Customer pays $99, contractor keeps portion, Duke keeps portion?
- **Still Unclear**: Exact commission structure, how collected, how reported

**7. Contractor Invoicing for Ad-Hoc Services**:
- **Question**: How does contractor report cash payments collected on-site?
- **Discussion**: Contractor updates Commerce portal with payment collected
- **Still Unclear**: Does contractor invoice Duke for commission? Or Duke invoices contractor?

**8. SpeedPay Integration for Non-Native Customers**:
- **Question**: When does SpeedPay integration come online?
- **Discussion**: Non-native customers need third-party payment since they can't add to utility bill
- **Risk**: If SpeedPay not ready at launch, contractors collect cash on-site (may reduce non-native bookings)

#### Inventory Data Collection Questions

**9. Contractor Inventory Capture Process**:
- **Question**: How do contractors submit inventory data to app?
- **Options**: Manual admin entry vs. simple portal form vs. defer to Phase 2
- **Decision Made**: TBD - Needs technical feasibility assessment
- **Risk**: If deferred, miss opportunity to build high-quality inventory data early

**10. Contractor Incentive for Data Capture**:
- **Question**: What motivates contractors to capture appliance data?
- **Discussion**: Future work pipeline, small bonus, part of SLA expectations?
- **Still Unclear**: Duke needs to negotiate with contractors via field coordinators

#### FSM Tool Questions

**11. FSM Tool Selection Timeline**:
- **Question**: When will Duke select FSM vendor (Service Power vs. Service Bench)?
- **Discussion**: NOT in scope for Phase 1 MVP
- **Risk**: If delayed beyond Phase 2, limits contractor mobile app and pizza tracker features

**12. FSM Tool API Documentation**:
- **Question**: Do Service Power and Service Bench have APIs? What's the integration complexity?
- **Still Unclear**: Need to review vendor documentation during Phase 2 planning

---

## 14. KEY RISKS

### HIGH RISK 🔴

**1. Contractor Matching Algorithm Underdefined**
- **Risk**: Customer scheduling feature can't be built without complete matching specification
- **Impact**: Blocks customer app development
- **Mitigation**: Prioritize finalizing trade + zip + primary/secondary + availability rules in validation session

**2. Static Availability May Lead to Low Acceptance Rates**
- **Risk**: Showing customer time slots that contractors can't actually fulfill
- **Target**: 90-95% acceptance rate, but no real-time visibility into contractor schedules
- **Impact**: Customer frustration, admin rework, contractor complaints
- **Mitigation**: Conservative lead time buffers (3-5 days minimum), contractor SLA contracts

**3. Manual Admin Processes May Not Scale**
- **Risk**: Admin team manually processing all service requests (send to contractor, update status)
- **Volume**: If 1,000+ service requests/month, admin workload becomes unsustainable
- **Impact**: Delays in customer confirmations, poor customer experience
- **Mitigation**: Monitor admin workload closely, prioritize service request API for Phase 1 if possible

**4. No Service Request API to Commerce CRM**
- **Risk**: Service requests created in app have no automated path to contractor
- **Current Plan**: Admin manually creates in Commerce CRM OR emails contractor
- **Impact**: Dual data entry, risk of errors, admin burden
- **Mitigation**: Duke IT to assess if service request creation API can be built for Phase 1

**5. P&G Internal Employees vs. Duke Contractors Not Clarified**
- **Risk**: MVP may need to support both third-party contractors AND internal employees with different workflows
- **Impact**: Scope creep, different data models, separate admin features
- **Mitigation**: Get clarification ASAP - Is MVP Duke-only or must support P&G employees?

**6. Contractor Data Export Not Available**
- **Risk**: Cannot populate app admin backend with contractor configuration
- **Impact**: No contractor matching, no scheduling, MVP blocked
- **Mitigation**: Duke IT must provide contractor export within 2 weeks of project kickoff

### MEDIUM RISK 🟡

**7. Contractor Availability Rules Too Complex**
- **Risk**: Multi-trade contractors with different availability per trade is complex data model
- **Impact**: Admin difficulty configuring, potential bugs in matching algorithm
- **Mitigation**: Start with simple model (one availability per contractor), add complexity in Phase 2

**8. Contractor Reluctance to Capture Inventory Data**
- **Risk**: Contractors view data capture as extra work without benefit
- **Impact**: Inventory data remains incomplete, limits future features
- **Mitigation**: Communicate value proposition to contractors (future work pipeline), negotiate incentives

**9. Rural Areas with Single Contractor**
- **Risk**: No backup option if primary contractor unavailable or at capacity
- **Impact**: Customer cannot book service, poor experience
- **Mitigation**: Communicate limitations to customer ("limited availability in your area"), manual admin outreach to expand contractor network

**10. Commission Model for Ad-Hoc Services Undefined**
- **Risk**: Unclear how Duke captures revenue from ad-hoc services
- **Impact**: Pricing strategy unclear, contractor payment terms unclear
- **Mitigation**: Define commission model before MVP launch (can start with no commission, add later)

**11. FSM Tool Delayed Beyond Phase 2**
- **Risk**: No FSM tool selected or implemented, limiting contractor mobile app and pizza tracker
- **Impact**: Competitive disadvantage, customer experience gaps
- **Mitigation**: Duke to prioritize FSM procurement, include in Phase 2 scope

### LOW RISK 🟢 (Mitigated)

**12. Extensive Contractor Portal Build**
- **Risk**: MITIGATED - Phase 1 does NOT include contractor portal rebuild
- **Decision**: Admin-only approach, contractors use existing Commerce portal

**13. In-App Messaging Complexity**
- **Risk**: MITIGATED - Phase 1 uses phone/SMS, in-app messaging deferred to Phase 2

**14. Contractor Adoption of New Mobile App**
- **Risk**: MITIGATED - No contractor mobile app for Phase 1, deferred to Phase 2 with FSM tool

---

## 15. SUCCESS METRICS

### Contractor-Related KPIs for MVP

**Contractor Performance**:
- **Acceptance Rate**: 90-95% of service requests accepted by contractors
- **On-Time Arrival**: 85%+ of appointments started within scheduled window
- **Completion Rate**: 95%+ of accepted jobs completed (not cancelled)
- **Average Response Time**: Contractors confirm/decline within 24 hours
- **Customer Satisfaction with Contractor**: 80%+ satisfied or very satisfied (from survey)

**Admin Operational Efficiency**:
- **Service Request Processing Time**: Admin processes customer booking and contacts contractor within 1 hour
- **Status Update Accuracy**: 95%+ of service statuses in app match actual contractor status
- **Exception Handling**: Rescheduled appointments resolved within 4 hours

**System Reliability**:
- **Contractor Matching Success**: 99%+ of service requests successfully matched to contractor
- **Data Sync Errors**: Less than 1% of contractor data out of sync

---

## 16. NEXT STEPS

### Immediate Actions (Post-Session 3)

**Duke Team**:
1. **Clarify P&G vs. Duke Contractor Model**: Are P&G employees in MVP scope? Different workflows needed?
2. **Provide Contractor Data Exports**: Contractor list, trade assignments, zip code assignments
3. **Define Contractor Availability Rules**: Confirm lead time buffers, work days, time windows per contractor
4. **Assess Service Request API Feasibility**: Can Duke IT build API for Phase 1 or manual process acceptable?
5. **Define Ad-Hoc Commission Model**: Percentage, collection method, contractor payment terms

**Orases Team**:
1. **Finalize Contractor Matching Algorithm Spec**: Document complete matching logic with edge cases
2. **Design Admin Backend Contractor Configuration**: Wireframes for admin managing contractors
3. **Design Service Request Workflow**: Admin processing service requests, updating statuses
4. **Prototype Contractor-Related Customer Flows**: Booking with contractor assignment, rescheduling

### Phase 1 Contractor Portal Deliverables

**Admin Backend Features**:
- Contractor CRUD (Create, Read, Update, Delete)
- Trade assignment (multi-select)
- Zip code assignment (list entry)
- Primary/secondary designation per trade + zip
- Lead time/buffer configuration per trade
- Availability windows configuration (time slots, days of week)
- Service request queue management
- Status update interface (confirm, reschedule, complete)
- Exception handling (reassign contractor, extend time window)

**Customer App Features**:
- View assigned contractor details (name, contact, photo?)
- See confirmed appointment date/time/contractor
- Reschedule/cancel service request (within policy)
- View service history (contractor name, date, outcome)
- Contact contractor (phone/SMS link)

**No Contractor Portal Changes**:
- Contractors continue using existing Commerce portal
- No contractor mobile app for Phase 1
- No contractor-facing features in app MVP

---

## 17. APPENDIX

### Contractor Network Size by State (Estimated)

| State | Estimated Contractors | Primary/Backup Split | Notes |
|-------|----------------------|----------------------|-------|
| North Carolina | 40-45 | 30-35 primary / 10-12 backup | Largest coverage area |
| South Carolina | 25-30 | 20-25 primary / 5-8 backup | Good coverage |
| Florida | 30-35 | 24-28 primary / 6-10 backup | Growing market |
| Ohio | 15-20 | 12-16 primary / 3-6 backup | Established market |
| Indiana | 10-15 | 8-12 primary / 2-5 backup | Smaller market |

**Total**: 125-140 contractors

### Contractor Trade Coverage by Trade (Estimated)

| Trade | Coverage | Average Lead Time | Notes |
|-------|----------|-------------------|-------|
| HVAC | 99-100% | 1-2 business days | Emergency-level priority |
| Water Heater | 99-100% | 1-2 business days | Emergency-level priority |
| Plumbing | 99-100% | 3-5 business days | Standard priority |
| Electrical | 99-100% | 5-6 business days | Filler work, non-emergency |
| Appliance | 95%+ | 2-3 business days | Some gaps filled by A&E |

### Common Service Time Windows

**Full-Day Windows**: 8am-5pm (8-hour window) - Rare, only rural contractors
**Half-Day Windows**: 8am-12pm or 1pm-5pm (4-hour windows) - Common
**Quarter-Day Windows**: 8am-10am, 10am-12pm, 1pm-3pm, 3pm-5pm (2-hour windows) - Less common
**Precision Windows**: Specific arrival time ± 30 minutes - Future state with FSM tool

**Quote from Kevin**: "It could vary. So that's why I said you may, we need it to be flexible enough that it could be an 8 to 12 window or it could be an 8 to 10 window, you know, depending on the contractor."

---

**Document Version**: 1.0
**Date**: November 2025
**Prepared By**: Orases Team (Vlad, Aksana Rahouski, Tom Witt)
**Next Update**: Post-Validation Session (Session 4)
