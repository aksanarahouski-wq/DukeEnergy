# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---

## EXECUTIVE SUMMARY

**Session Focus:** Backend administration and operations - the people and systems that make the customer app experience work.

**Key Insight:** The admin portal serves as the "middle layer" aggregating data from multiple sources (Commerce CRM for Duke customers, Dynamics for P&G customers, app database for non-native customers and new data) into a unified administrative interface.

### Major Decisions Made:

1. **Build a dedicated admin backend** separate from existing CRM systems to support cross-system data aggregation
2. **Manual fallback processes for MVP** - When APIs don't exist, admin queues handle enrollment, service requests manually
3. **Multi-level admin access** - Different permission levels for CSR, back office, escalation team, analytics users
4. **Ad-hoc service catalog** - New product catalog management needed (doesn't exist today)
5. **Reminders over DIY content** - Focus on automated maintenance reminders rather than building static DIY content library
6. **Full instrumentation required** - Analytics and reporting critical from day 1 for business case validation
7. **Manual service request processing for MVP** (Session 3) - Admin manually contacts contractors (email/phone) within 1 hour of customer booking, updates app status based on contractor responses (within 24 hours)
8. **No contractor portal rebuild for MVP** (Session 3) - Contractors continue using existing Commerce CRM portal. Admin backend manages contractor configuration (trade, zip codes, availability). FSM integration and contractor mobile app deferred to Phase 2.
9. **Contractor configuration management in admin backend** (Session 3) - Admin backend houses contractor data (125-140 contractors, 80% primary/20% backup), manages matching algorithm configuration (trade + zip code + availability buffers)

---

## ADMIN USER ROLES & PERMISSIONS

### Role Matrix

| Role | Primary Function | Key Responsibilities | System Access |
|------|------------------|---------------------|---------------|
| **CSR (Enrollment Center)** | Customer acquisition | Handle enrollment inquiries, manually create accounts/business partners, process failed enrollments from review queue | CRM (Commerce), App Backend (view-only for loyalty/rewards) |
| **CSR (Shop/Support)** | Technical support | App account administration (password resets, unlock accounts), troubleshoot app issues | App Backend (full CRUD for customer profiles) |
| **Back Office Admin** | Operations & data management | Process enrollment queues, manage customer profiles, update inventory, configure services & pricing | App Backend (full CRUD), CRM (read/write) |
| **Product Manager** | Catalog management | Create/edit ad-hoc service catalog, set pricing, define service scope of work, manage reminders | App Backend (service catalog, pricing, reminders) |
| **Operations Manager** | Service oversight & contractor coordination | **MVP CRITICAL**: Manually process service requests (contact contractors within 1 hour, update app status based on responses), reassign contractors, handle exceptions, manage contractor availability overrides | App Backend (service request queue, contractor config, full CRUD), CRM (contractor assignments) |
| **Escalation Team** | Conflict resolution | Handle customer complaints, contractor disputes, service quality issues | CRM (full context), App Backend (create escalation tickets) |
| **Analyst/Reporting User** | Business intelligence | Access dashboards, export reports, track KPIs | App Backend (read-only analytics) |

### Permission Levels

**View Only:**
- Customer profile (basic info)
- Service request status
- Analytics dashboards

**Edit/Create:**
- Customer inventory (back office, support CSR)
- Service catalog & pricing (product managers)
- Reminders & content (product managers)
- Contractor configuration (operations)

**Admin/Super User:**
- User management
- System configuration
- Full CRUD across all entities

---

## MVP SCOPE DECISIONS

### ✅ IN SCOPE - MVP (Phase 1)

#### **1. Customer Management**
- **Customer Profile CRUD** - View, edit, create customer records
- **Cross-system aggregation** - Pull data from Commerce (Duke), Dynamics (P&G), App DB (non-native)
- **Review queue for failed enrollments** - When automatic matching fails, admin manually processes
- **Account administration** - Password resets, unlock accounts, update preferences
- **Manual enrollment processing** - For MVP, when API doesn't exist, admin creates enrollment manually in CRM

**Quote (Kevin Oppermann, 22:18):**
> "For MVP, it doesn't mean that we don't allow them to go ahead and think that we're processing that enrollment. It just means that there may be a manual intervention on the back end to actually do it. So from the customer perspective, they still think there's processing."

#### **2. Home Inventory Management**
- **Full CRUD on customer inventory** - Admin can view, create, edit, delete inventory items
- **Multi-source inventory data**:
  - Customer-entered during onboarding
  - Admin-added during support calls
  - Contractor-added after service visit
- **Inventory fields**: Item type, brand, model, serial number, age, location in home, purchase date, warranty expiration
- **Use case**: Customer calls support → Admin needs to look up inventory to help troubleshoot or add missing details

**Quote (Gilstrap, Joshua, 1:12:46):**
> "CRUD functions on inventory, and then it's just a matter of making sure the fields we have are correct. So, like, brand, age was a good one, model number."

#### **3. HPP Plan (Subscription) Management**
- **View customer subscriptions** - See all HPP plans customer is enrolled in
- **Subscription status** - Active, suspended (delinquent payment), cancelled
- **Manual enrollment support** - For MVP, admins may manually process enrollments submitted via app
- **Sync with CRM** - Plans live in Commerce/Dynamics, app backend mirrors for aggregation

**Current State:** Enrollment APIs will exist by MVP for validating existing subscriptions, but NEW enrollment API may not exist, requiring manual fallback.

#### **4. Service Request Management**

**✅ UPDATED FROM SESSION 3:**

**Service Request Dashboard:**
- View all service requests (HPP covered + ad-hoc)
- Filter by status, date, customer, contractor, type
- **Priority Queue**: "Pending Confirmation" requests needing immediate admin action
- Search by customer name, service request ID
- Drill into service request details

**Service Request Statuses** (MVP - Manual Updates):
1. **Pending Confirmation** - Customer booked, admin needs to contact contractor (ACTION REQUIRED)
2. **Confirmed** - Contractor accepted, appointment scheduled with contractor + date/time
3. **Rescheduled** - Time/date changed after initial confirmation
4. **Completed** - Service finished
5. **Cancelled** - Service cancelled by customer or contractor

**NO FSM Integration for MVP**: No automated statuses like "Dispatched", "En Route", "On-Site", "In Progress"

**Service Request Details View:**
- Customer info (name, phone, address, HPP plans)
- Service type (HPP covered vs ad-hoc)
- Service category/trade (HVAC, plumbing, electrical, water heater, appliance)
- Problem description (customer-entered)
- Related inventory item (if applicable)
- **Assigned contractor** (primary contractor based on trade + zip code)
- **Requested date/time window** (customer-selected)
- **Confirmed date/time** (contractor-accepted, may differ from requested)
- Status history (timestamp + who updated)
- Contractor notes (entered after acceptance/completion)
- Payment status (for ad-hoc services)
- **Time since submission** (to track SLA: admin should process within 1 hour)

**MVP Admin Workflow - Manual Service Request Processing** (CRITICAL):

**Step 1: Customer Books Service in App**
- Customer creates service request
- Status auto-set to: "Pending Confirmation"
- Request appears in admin "Pending Confirmation Queue"
- Admin receives notification (email/dashboard alert)

**Step 2: Admin Contacts Contractor (Within 1 Hour SLA)**
- Admin opens service request from queue
- Reviews customer details, service type, requested time window
- Identifies primary contractor (auto-matched by system: trade + zip code)
- Admin contacts contractor via:
  - **Email**: service request details sent to contractor email
  - **Phone**: admin calls contractor directly if urgent
  - **Future**: Push notification to contractor mobile app (Phase 2 with FSM)
- Admin includes:
  - Customer name, address, phone
  - Service type, problem description
  - Requested date/time window (e.g., "Thursday 9-12am")
  - Payment type (warranty covered $0, or ad-hoc $99)

**Step 3: Contractor Responds (Within 24 Hours)**
- Contractor checks their schedule
- Responds to admin:
  - **Option A: Accept** - "Yes, Thursday 9-12am works"
  - **Option B: Propose Alternative** - "Can't do Thursday 9-12am, can do Friday 1-4pm"
  - **Option C: Decline** - "At capacity, cannot service" (rare, <5% due to SLA contracts)

**Step 4: Admin Updates App Based on Contractor Response**

**If Contractor Accepts:**
- Admin updates service request status: "Confirmed"
- Admin enters: Contractor name, confirmed date/time
- App displays to customer: "Your appointment is confirmed! ABC Plumbing on Thursday 9-12am"
- Customer receives push notification + SMS/email

**If Contractor Proposes Alternative Time:**
- Admin evaluates options:
  - **Option 1**: Accept contractor's alternative, call customer to confirm new time
  - **Option 2**: Try backup contractor for original time (priority: keep time > keep contractor)
- If customer accepts new time:
  - Admin updates status: "Confirmed" with new date/time
  - Notification sent to customer
- If backup contractor accepts original time:
  - Admin updates status: "Confirmed" with backup contractor + original time
  - Notification sent to customer

**If Contractor Declines:**
- Admin immediately contacts backup contractor
- Repeats Step 2 with backup contractor
- Goal: 90-95% acceptance rate from primary contractors

**Step 5: Service Day - Admin Monitors**
- Admin does NOT receive real-time updates (no FSM integration)
- Contractor performs service, updates Commerce CRM when complete
- Admin checks CRM daily for completed services
- Admin updates app status: "Completed"
- Customer receives completion notification
- External survey sent to customer (not in-app)

**Admin Actions:**
- **Manual service request creation** - Create on behalf of customer (phone orders)
- **Manual status updates** - Update based on contractor communication
- **Reassign contractor** - Override automatic assignment, assign backup contractor
- **Add internal notes** - Notes visible to admins only (e.g., "Customer prefers morning appointments")
- **Cancel/reschedule** - Modify appointments if customer or contractor requests
- **Handle exceptions**:
  - No contractor available in zip code
  - All contractors at capacity
  - Contractor emergency (needs to reschedule)
  - Customer requests different contractor (phone call required)
  - Emergency events (hurricanes, etc.) - bulk reassignments

**For MVP:** Admin backend creates local copy of service requests for visibility. Service requests also pushed to CRM (Commerce/Dynamics) for contractor dispatch and invoicing.

**Target SLAs:**
- Admin processes service request: **Within 1 hour** of customer submission
- Contractor responds to admin: **Within 24 hours**
- Admin updates app with confirmation: **Within 1 hour** of contractor response
- Total time to confirmation: **24-48 hours**

**Quote (Gilstrap, Joshua, 52:15):**
> "A service request is made in commerce manually by a human today when they call in."

**Quote from Session 3:**
> "Admin manually contacts contractor (email/phone) within 1 hour. Contractor responds within 24 hours (accepts or proposes alternative time). Admin updates app: 'Confirmed - ABC Plumbing - Thursday 9-12am'."

#### **5. Ad-Hoc Service Catalog Management**

**CRITICAL:** Ad-hoc service catalog does NOT exist today. Must be built.

**Service Catalog Admin Functions:**
- **Create new ad-hoc services** - Define service name, category, description, scope of work
- **Set pricing** - Fixed price, price range, or "quote required"
- **Geographic pricing** - Different prices by region/market (e.g., Orlando vs Charlotte)
- **Scope of work definition** - What's included, exclusions, parameters
- **Service availability** - Which zip codes/regions service is offered
- **Contractor association** - Which contractors offer this service at negotiated rate
- **HPP plan association** - Map ad-hoc services to HPP plans (for customers already on plan, service may be covered)

**Pricing Workflow:**
1. Product manager creates service
2. Defines scope of work (e.g., "HVAC tune-up: includes filter replacement, coil cleaning, refrigerant check")
3. Negotiates pricing with contractors per region
4. Sets flat rate price for customers (e.g., $99 for HVAC tune-up in Orlando area)
5. Service goes live in app for booking

**Quote (Oppermann, Kevin, 56:10):**
> "For the ad hoc services, it will depend. So like you need just, hey, something's wrong with my water heater, I don't know what it is. That's just like a request for us... Versus if we are saying there's a defined scope of work, like a water heater flush or an HVAC maintenance... we can give them a flat rate pricing and transparent pricing, that will have come, that will come with a defined scope of work."

**MVP Ad-Hoc Services (Limited Set):**
- Start with 5-10 well-defined services with flat rate pricing
- Examples: HVAC tune-up ($99), water heater flush, air filter change, toilet install (customer-supplied)
- Launch in 1-2 pilot markets (e.g., Orlando area)

**Service Fields:**
- Service name
- Service code/SKU (for reporting)
- Category (HVAC, plumbing, electrical, appliance, other)
- Description (customer-facing)
- Scope of work (detailed, customer agrees to before booking)
- Pricing type (fixed, variable, quote-based)
- Base price (if fixed)
- Regional price overrides (optional)
- Geographic availability (zip codes, cities, or regions)
- Contractor availability (which contractors offer this service)
- Status (draft, active, inactive)

#### **6. Contractor Configuration Management**

**✅ MAJOR EXPANSION FROM SESSION 3:**

**Quote (Gandara, Sun, 53:07):**
> "I can see where from an administration on the back end, we would probably want some type of admin access to for the contractor configuration... in the future, we should have APIs that call that, but in the short term, we might need to house a copy somewhere on the back end."

**Contractor Network Overview:**
- **Total Contractors**: 125-140 contractors across 4-5 states (NC, SC, FL, OH, IN)
- **Primary Contractors**: ~80% (100-112 contractors) - First assigned, receive jobs first
- **Backup Contractors**: ~20% (25-28 contractors) - Overflow when primary unavailable
- **Coverage**: 99-100% for HVAC, Plumbing, Electrical, Water Heater; 95%+ for Appliance
- **Multi-Trade**: Most contractors offer 2-3 trades (e.g., Plumbing + HVAC + Electrical)

**Contractor Data Model - Admin Backend:**

**Basic Contractor Information:**
- Contractor ID (unique identifier)
- Contractor Name (individual or company name)
- Business Name
- Contact Phone
- Contact Email
- Primary Contact Name
- Status (Active, Inactive, On Hold)
- Licensing Information (license numbers, expiration dates)
- Insurance Information (certificate, expiration)
- Background Check Status (required for all technicians)

**Service Area Configuration** (Critical for Matching Algorithm):
- **Zip Code List**: Exact zip codes contractor serves (e.g., 28201, 28202, 28203)
- **NOT Radius-Based**: Assignment is zip code specific, not distance-based
- **Non-Contiguous Areas**: Contractor may serve Charlotte (28xxx) AND Raleigh (27xxx) but not cities in between
- **Geographic Coverage Notes**: Admin can add notes (e.g., "Only serves north side of city")

**Trade/Specialization Configuration** (Multi-Trade Support):

Each contractor can have multiple trade configurations:

**Trade 1: HVAC**
- Primary contractor for zip codes: 28201, 28202, 28203
- Lead time buffer: 2 business days
- Availability: Monday-Friday, 8am-5pm
- Time windows: 8-12, 1-5
- Status: Active

**Trade 2: Plumbing**
- Primary contractor for zip codes: 28201, 28202
- Secondary contractor for zip codes: 28203, 28204
- Lead time buffer: 3 business days
- Availability: Tuesday-Thursday only
- Time windows: 9-12, 1-4
- Status: Active

**Trade 3: Electrical**
- Secondary contractor for zip codes: 28201, 28202
- Lead time buffer: 6 business days
- Availability: Monday, Wednesday, Friday only
- Time windows: 8-12 only
- Status: Active

**Quote from Session 3 (Ed Carr):**
> "When we talk about having windows for contractors, when they are multiple trades, they may have different windows depending upon the trade."

**Primary/Secondary Designation** (Per Trade + Zip Code):
- **Primary**: First assigned, receives job first, SLA commitment to accept 90-95% of jobs
- **Secondary/Backup**: Assigned when primary unavailable or at capacity
- **Designation can vary**: Contractor may be primary for HVAC in 28201 but secondary for Plumbing in 28203
- **What Determines Tier**: Negotiated contracts, capacity, pricing, performance, not dynamic ratings

**Lead Time & Availability Configuration**:

**Lead Time Buffers** (Trade-Specific):
- **HVAC/Water Heater**: 1-2 business days (emergency-priority)
- **Plumbing**: 3-5 business days
- **Electrical (non-emergency)**: 5-6 business days
- **Appliance**: 2-3 business days

**Static Availability Rules** (MVP Approach):
- **Work Days**: Which days contractor is available (e.g., Mon-Fri, Tue/Thu only, Weekends)
- **Time Windows**: Available time slots (e.g., 8am-12pm, 1pm-5pm)
- **Time Window Duration**: Half-day (4 hours), Quarter-day (2 hours), Full-day (8 hours)
- **Blocked Dates**: Vacation, holidays, already booked (admin manually updates)
- **Max Jobs Per Day**: Capacity limit (e.g., "Max 3 HVAC jobs per day")

**NOT Real-Time Calendars for MVP**: Contractors do NOT provide live availability. System uses static rules + buffer.

**Admin CRUD Operations:**

**Create New Contractor:**
1. Admin navigates to "Contractor Management"
2. Clicks "Add New Contractor"
3. Enters basic info (name, company, contact, licensing, insurance)
4. Adds trade(s) with configuration:
   - Trade type (HVAC, Plumbing, Electrical, etc.)
   - Service area (zip code list)
   - Primary/secondary designation per zip code
   - Lead time buffer
   - Availability windows
   - Work days
5. Sets status: Active
6. Saves contractor
7. Contractor now available for matching algorithm

**Edit Contractor:**
- Update contact info, licensing, insurance
- Add/remove service areas (zip codes)
- Change primary/secondary designation
- Adjust lead time buffers
- Update availability windows
- Add blocked dates (vacation, maintenance)
- Change status (Active → Inactive if contractor leaves network)

**Override/Exception Handling:**
- **Emergency Override**: Admin can manually assign contractor outside normal rules (hurricanes, disasters)
- **Blocked Date Override**: Admin can extend buffer (e.g., "All electrical contractors need 10 days lead time this week due to storm repairs")
- **Capacity Override**: Admin can close contractor to new jobs ("At capacity, no new assignments")

**Contractor Data Sync Strategy (MVP):**

**Initial Setup:**
1. Duke exports contractor data from Commerce CRM (CSV/JSON file)
2. Export includes: Contractor list, trade assignments, zip code assignments, primary/secondary designations
3. Orases imports into app backend database
4. Admin team manually configures additional fields (lead time, availability windows)

**Ongoing Maintenance:**
1. Contractor changes happen in CRM first (source of truth)
2. Admin manually updates app backend to match
3. Frequency: As-needed (contractor changes rare, ~1-2 per year)

**Phase 2 (Future):**
- Real-time API to read contractor data from CRM
- Nightly sync to keep app backend updated
- FSM tool integration for real-time contractor availability

**Contractor Performance Tracking** (Admin View Only):
- Jobs completed (total, per month)
- Acceptance rate (% of jobs accepted vs. declined)
- On-time arrival rate
- Customer satisfaction ratings (from external surveys)
- Average job completion time
- Revenue generated

**Performance does NOT factor into MVP matching algorithm** - Primary/secondary designation is based on contracts, not real-time ratings.

**Quote from Session 3 (Kevin Oppermann):**
> "We would have to do that today mainly anyway. And we do it today. We have to override the zip code eligibility, et cetera. Not frequently, it just happens that we have contractor that goes out, especially in the mom and pop areas that we have to get backup."

**Current State:** Contractor data lives in Commerce CRM (Duke) and Dynamics (P&G). For MVP, app backend houses copy for matching algorithm configuration.

**Critical for MVP:** Admin backend MUST have full CRUD on contractor configuration to drive customer scheduling calendar.

#### **7. Reminders & Content Management**

**DECISION:** Focus on **reminders** (automated maintenance calendar) NOT static DIY content.

**Reminders System:**

**Reminder Categories:**
- **Global reminders** - Default for all homeowners (e.g., "Change HVAC filter every 3 months")
- **Asset-based reminders** - Triggered by inventory items (e.g., "Annual HVAC tune-up" if customer has HVAC)
- **Seasonal reminders** - Spring/summer/fall/winter maintenance (e.g., "Prep HVAC before summer heat")
- **Customer-created reminders** - Customers can add their own (e.g., "Grease garage door wheels quarterly")

**Admin Functions:**
- **Create/edit reminder templates** - Define reminder text, frequency, asset category association
- **Asset category mapping** - Tie reminders to inventory categories (HVAC, water heater, appliance, etc.)
- **Seasonal configuration** - Set reminders to trigger in specific seasons
- **Service linkage** - Optionally link reminder to bookable service (e.g., "Annual HVAC tune-up" → book $99 service)

**Reminder Fields:**
- Title (e.g., "Change HVAC Filter")
- Description/instructions (what to do, why it matters)
- Frequency (monthly, quarterly, bi-annually, annually, seasonal)
- Asset category (which inventory items trigger this reminder)
- Optional: Link to ad-hoc service (if customer wants to book instead of DIY)
- Optional: Link to HPP plan (if reminder is covered under plan, prompt to book covered service)
- Status (active, inactive)

**Customer Experience:**
- Customer sees default reminders based on their inventory
- Customer can enable/disable individual reminders
- Customer can adjust frequency (e.g., change from monthly to every 6 months)
- Customer can assign reminder to family member (e.g., "Husband's job")
- Reminder notifications sent via push, email, or SMS (based on customer preference)

**Quote (Oppermann, Kevin, 1:29:02):**
> "There is a default that, hey, if you have a heating and cooling system, here's reminders we should be sending out. If you have a water heater, here's the reminders that should be sent out... And the homeowner then can select or deselect which ones they're interested in continuously being reminded of."

#### **8. Analytics & Reporting Dashboard**

**CRITICAL:** Full instrumentation required from MVP launch.

**Quote (Gandara, Sun, 1:24:49):**
> "I would like the whole app instrumented. Yeah, we would. I want it all. We want to see where customers are falling off from the app, being able to capture their click throughs through the different components within the app."

**Key Metrics to Track:**

**Customer Acquisition:**
- New app registrations (total, by customer type: Duke, P&G, non-native)
- Customer source (existing utility customer vs new acquisition)
- Registration conversion rate (downloads → completed profiles)
- Inventory completion rate (% of customers with home inventory)

**Engagement:**
- Active users (daily, weekly, monthly)
- Session duration
- Feature usage (service booking, inventory, DIY/reminders, HPP management)
- Customer drop-off points (where in flow do customers abandon?)

**Service Requests:**
- Total service requests (HPP covered vs ad-hoc)
- Service request volume by type (HVAC, plumbing, electrical, etc.)
- Service request volume by region
- Time to complete service request
- Customer satisfaction ratings

**Revenue:**
- Ad-hoc service revenue
- New HPP enrollments via app
- Cancellations/churn

**Contractor Performance:**
- Jobs completed
- On-time percentage
- Customer ratings
- Utilization rate

**Operational:**
- Call center volume reduction (target: 40%)
- Automated scheduling rate (target: 80%)
- Manual intervention rate (queue processing)

**Dashboard Views:**
- **Operations Dashboard** - Real-time service request tracking, contractor status
- **Executive Dashboard** - High-level KPIs, trends, business case validation
- **Marketing Dashboard** - Customer acquisition, engagement, feature usage
- **Product Dashboard** - Feature adoption, drop-off points, A/B test results

**Export Capabilities:**
- Export reports to CSV, Excel, PDF
- Scheduled reports (daily, weekly, monthly)

#### **9. Communication & Notifications**

**Admin-to-Customer Communication:**
- Send email or SMS to customers
- Bulk notifications (e.g., "New service available in your area")
- Customer communication preferences (email, SMS, push, in-app)
- Communication log/history per customer

**Quote (Gandara, Sun, 1:46:16):**
> "Depending on customer preference, whether it's email or SMS... there's like a communication portal part of it."

#### **10. Escalation Management**

**Escalation Workflow:**
1. Customer initiates escalation via app (submits ticket with issue details)
2. Ticket created in admin backend
3. Escalation team receives notification
4. Escalation team reviews ticket, calls customer back
5. Escalation team resolves issue, updates ticket status

**Escalation Ticket Fields:**
- Customer info
- Service request ID (if applicable)
- Issue category (service quality, contractor dispute, billing, technical issue)
- Issue description
- Priority (low, medium, high, urgent)
- Status (open, in progress, resolved, closed)
- Assigned to (escalation team member)
- Resolution notes

**Quote (Oppermann, Kevin, 1:38:55):**
> "We may be able to let them like enter a ticket saying, hey, I have an issue. Can you call me back? Blah, blah. So that way they feel like they can put that out there. It's, you know, past hours that they can call in, but they still want this order, you know, that escalation to be identified."

---

### ❌ OUT OF SCOPE - MVP (Deferred to Phase 2 or Future)

#### **Phase 2 Features:**
- **CRM data entry** - MVP: Admins still use CRM for certain functions. Phase 2: Move more operations into app backend
- **Advanced FSM integration** - MVP: Manual status updates. Phase 2: Automated contractor tracking, GPS, pizza tracker
- **Advanced analytics** - MVP: Basic dashboards. Phase 2: Predictive analytics, AI-driven insights, custom reports
- **Static DIY content library** - Replaced by AI-powered troubleshooting (ChatGPT-style) in future
- **Payment management** - MVP: Limited visibility. Phase 2: Full AR/invoicing for ad-hoc services
- **Contractor portal admin** - Session 3 will define scope. Likely Phase 2.

---

## ADMIN WORKFLOWS

### Workflow 1: Manual Enrollment Processing (MVP Fallback)

**Trigger:** Customer submits HPP plan enrollment via app, but enrollment API doesn't exist yet.

**Steps:**
1. Customer completes enrollment flow in app
2. Enrollment request added to **Review Queue** in admin backend
3. Back office admin receives notification
4. Admin reviews enrollment details:
   - Customer info (name, address, email, phone)
   - Requested HPP plan(s)
   - Payment method (utility bill vs credit card)
5. Admin validates customer:
   - If Duke/P&G customer: Look up in CRM (Commerce/Dynamics) by account number, address, phone, or last name
   - If match found: Link app profile to existing customer record
   - If no match found: Admin manually creates business partner in CRM
6. Admin processes enrollment:
   - Creates enrollment in CRM (Commerce/Dynamics)
   - Enrollment syncs to billing system
   - App backend updated with enrollment confirmation
7. Customer receives confirmation notification
8. Admin marks queue item as "Processed"

**Timeline:** Within 24-48 hours of submission.

**Future State (Phase 2):** Direct API enrollment - no manual intervention.

---

### Workflow 2: Service Request Creation & Assignment

**Scenario A: Customer Books via App (HPP Covered Service)**

**Steps:**
1. Customer submits service request via app (e.g., "Water heater not working")
2. App validates HPP coverage (API call to Commerce/Dynamics)
3. Service request created in app backend
4. **For MVP:** App backend pushes service request to CRM (Commerce/Dynamics) via API or manual queue
5. CRM auto-assigns contractor based on trade + zip code
6. Admin can view service request in dashboard (status: "Assigned")
7. Admin monitors for exceptions (no contractor available, contractor declines, etc.)
8. If exception occurs, admin manually reassigns or contacts customer

**Scenario B: Customer Books via App (Ad-Hoc Service with Flat Rate Pricing)**

**Steps:**
1. Customer browses ad-hoc service catalog in app
2. Customer selects service (e.g., "HVAC Tune-Up - $99")
3. Customer selects date/time window based on contractor availability
4. Service request created in app backend
5. Service request pushed to CRM for contractor dispatch
6. Admin monitors service request dashboard
7. Admin can manually update status if FSM tool not integrated yet

**Scenario C: Customer Calls to Book Service (Phone Order)**

**Steps:**
1. Customer calls CSR
2. CSR looks up customer in app backend (to see inventory, HPP plans, loyalty rewards)
3. CSR creates service request manually in CRM (existing process)
4. CRM assigns contractor
5. Service request synced to app backend (so customer can track in app)

---

### Workflow 3: Ad-Hoc Service Catalog Creation

**Actor:** Product Manager

**Steps:**
1. Product manager logs into admin backend
2. Navigates to "Service Catalog Management"
3. Clicks "Create New Service"
4. Fills out service details:
   - Service name: "HVAC Tune-Up"
   - Category: HVAC
   - Description: "Annual HVAC maintenance to ensure optimal performance and efficiency"
   - Scope of work:
     - Replace air filter
     - Clean condenser coils
     - Check refrigerant levels
     - Inspect electrical connections
     - Test thermostat
     - Provide maintenance report
   - Exclusions: "Does not include repairs or replacement parts"
   - Customer must: "Provide clear access to HVAC unit"
5. Set pricing:
   - Pricing type: Fixed
   - Base price: $99
   - Regional overrides:
     - Orlando area: $99
     - Charlotte area: $109
     - Raleigh area: $105
6. Set geographic availability:
   - Available in: Orlando metro (zip codes: 32801-32899)
7. Associate contractors:
   - Select contractors who offer this service at negotiated rate
8. Set status: Active
9. Save service
10. Service now appears in customer app for booking

**Quote (Gandara, Sun, 55:35):**
> "What you will show on the front end to the customer could be whatever the ad hoc services are, when it maps back to our enterprise, you'll pass all the description or whatever that is, but from a back end, it will need to map to this ECN product."

---

### Workflow 4: Reminder Management

**Actor:** Product Manager / Content Manager

**Steps:**
1. Admin navigates to "Reminders Management"
2. Clicks "Create New Reminder"
3. Fills out reminder details:
   - Title: "Change HVAC Filter"
   - Description: "Replace your HVAC filter every 3 months to maintain air quality and system efficiency"
   - Frequency: Every 3 months
   - Asset category: HVAC
   - Seasonal trigger: None (year-round)
   - Optional service link: "Order filter replacement service ($29)"
4. Save reminder
5. Reminder automatically added to all customers with HVAC inventory
6. Customers receive notification based on frequency
7. Customers can adjust frequency or disable reminder

---

### Workflow 5: Customer Profile Management (Support Call)

**Actor:** CSR (Shop/Support)

**Scenario:** Customer calls saying they can't log into the app.

**Steps:**
1. Customer calls support: "I can't log into my account"
2. CSR asks for email or phone number
3. CSR searches for customer in admin backend
4. CSR views customer profile:
   - App account status: Active
   - Last login: 3 days ago
   - Email: verified
   - Phone: verified
5. CSR identifies issue: Customer forgot password
6. CSR sends password reset email to customer
7. Customer receives email, resets password
8. CSR confirms customer can log in
9. CSR updates ticket status: Resolved

**Alternative Scenario:** Customer account locked after multiple failed login attempts.

**Steps:**
1. CSR searches for customer
2. CSR sees account status: Locked
3. CSR unlocks account
4. CSR sends notification to customer
5. Customer can log in

---

### Workflow 6: Inventory Management (Contractor Update)

**Scenario:** Contractor completes service visit and updates inventory.

**Steps:**
1. Contractor visits customer home for water heater service
2. Contractor identifies water heater make/model/serial number
3. Contractor submits service completion report via contractor portal (or calls back to dispatch)
4. Service notes include: "Customer has Rheem tankless water heater, Model XYZ, Serial 123456, installed 2021"
5. **Admin action:** Back office admin reviews service completion notes
6. Admin navigates to customer profile in admin backend
7. Admin adds inventory item:
   - Item type: Water Heater
   - Category: Tankless
   - Make: Rheem
   - Model: XYZ
   - Serial: 123456
   - Installation date: 2021
   - Location: Garage
8. Save inventory
9. Customer now sees water heater in their app inventory
10. Customer receives reminder: "Annual tankless water heater flush recommended"

---

### Workflow 7: Analytics Review (Weekly Business Review)

**Actor:** Executive Team, Operations Manager

**Steps:**
1. Operations manager logs into admin backend
2. Navigates to "Executive Dashboard"
3. Reviews key metrics:
   - **This Week:**
     - New registrations: 1,250 (up 15% from last week)
     - Active users: 8,400 (70% engagement rate)
     - Service requests: 620 (480 HPP covered, 140 ad-hoc)
     - Ad-hoc revenue: $12,800
     - Call center volume: Down 32% (on track for 40% target)
     - Customer satisfaction: 4.6/5 stars average
4. Manager identifies issue: Ad-hoc service requests lower than expected
5. Manager drills into "Ad-Hoc Services" dashboard:
   - Most booked: HVAC Tune-Up (82 bookings)
   - Least booked: Toilet Install (3 bookings)
6. Manager hypothesis: Toilet install pricing too high or scope unclear
7. Manager tasks product manager: Review toilet install service, adjust pricing or scope
8. Manager exports report to share with executive team
9. Executive team reviews in weekly meeting, adjusts strategy

---

## KEY INTEGRATIONS & DEPENDENCIES

### Integration Architecture

**Admin Portal as "Middle Layer":**

```
[Duke CRM - Commerce]  ←→  [Admin Portal Backend]  ←→  [Customer App]
[P&G CRM - Dynamics]   ←→                           ←→  [Contractor Portal]
[App Database]         ←→                           ←→  [Analytics Tools]
```

**Admin portal aggregates data from:**
- Commerce (Duke customer data, HPP plans)
- Dynamics (P&G customer data, service requests)
- App Database (non-native customers, home inventory, ad-hoc services, reminders)

---

### 1. Customer Validation & HPP Plan APIs

**Status:** WILL EXIST by MVP launch (confirmed by Duke team)

**APIs Needed:**
- Validate if customer is Duke/P&G utility customer
- Retrieve customer HPP plan subscriptions
- Check subscription status (active, suspended, cancelled)

**Usage:**
- Customer logs into app → API validates against Commerce/Dynamics
- Customer views "My Plans" → API retrieves active HPP plans
- Customer books service → API checks if service covered under plan

---

### 2. Service Request Creation API

**Status:** MAY NOT EXIST for MVP - Manual fallback required

**API Needed:**
- Create service request in Dynamics (CRM)
- Pass all service request details: customer, service type, problem description, inventory details, date/time preference

**MVP Fallback:**
- Service request created in app backend
- Admin manually enters into CRM, OR
- Automated email/queue sent to operations team to manually process

---

### 3. Contractor Data & Assignment

**Status:** Exists in CRM but may need local copy for scheduling logic

**Current State:**
- Contractor data in CRM/Dynamics: trade, zip code coverage, primary/secondary designation
- Automatic assignment: Trade + Zip Code → Contractor

**For MVP:**
- Admin backend may need local copy of contractor configuration to drive scheduling calendar
- Configuration includes: lead time (e.g., "3-5 days"), scheduling buffer

**Session 3 will define:** Detailed contractor integration requirements

---

### 4. FSM (Field Service Management) Tool Integration

**Status:** Future - NOT for MVP

**Current State:**
- Duke exploring FSM tools (Service Power, Service Bench, others mentioned)
- No FSM tool today

**For MVP:**
- Admin manually updates service request status (assigned, en route, on-site, completed)
- Customer sees status in app based on manual admin updates

**Future State (Phase 2):**
- FSM tool provides real-time contractor GPS tracking
- Automated status updates (contractor en route, on-site, completed)
- "Pizza tracker" experience for customers

**Quote (Gandara, Sun, 1:23:28):**
> "From what we're seeing through the demos, I'll say it's really that FSM tool that enables that because the tool itself, you know, has a customer integration, customer experience and notifications back. But that tool itself is what the contractors use."

---

### 5. SSO (Single Sign-On) for Admin Portal

**Status:** TBD - Depends on Duke IT capabilities

**Options:**
- SSO with Duke corporate IT (SAML, Okta, Azure AD)
- Separate login (username/password)

**For MVP:** May start with separate login, migrate to SSO in Phase 2

---

### 6. Data Sync Strategy

**Master Sources of Truth:**

| Data Entity | Master Source | Synced To | Sync Method | Frequency |
|-------------|---------------|-----------|-------------|-----------|
| **Duke customer profile** | Commerce | App Backend | API (read) | Real-time or daily |
| **P&G customer profile** | Dynamics | App Backend | API (read) | Real-time or daily |
| **Non-native customer profile** | App Backend | None | N/A | N/A |
| **HPP plan enrollment (Duke)** | Commerce | App Backend | API (read) | Real-time |
| **HPP plan enrollment (P&G)** | Dynamics | App Backend | API (read) | Real-time |
| **Service requests (HPP)** | Dynamics | App Backend | API (create/read/update) | Real-time |
| **Service requests (ad-hoc)** | App Backend | Dynamics | API (create) or manual | Batch or manual |
| **Home inventory** | App Backend | None | N/A | N/A |
| **Ad-hoc service catalog** | App Backend | None | N/A | N/A |
| **Reminders** | App Backend | None | N/A | N/A |
| **Contractor configuration** | CRM/Dynamics | App Backend (copy) | Manual or API | Daily or on-demand |

**Key Principle:**
- For MVP, admin backend mirrors data from CRM systems (read-only sync)
- New data (inventory, ad-hoc services, reminders) lives primarily in app backend
- Over time, migrate more "source of truth" functions from CRM to app backend

**Quote (Gilstrap, Joshua, 1:44:32):**
> "We need mostly full visibility, but with the understanding that a lot of the stuff lives in CRM and that's the source of truth. Over time, in the future, we'd like to eventually kind of move the source of truth function for a lot of these things out of the CRM, but right now it's going to be in there."

---

## BUSINESS GOALS & SUCCESS METRICS

### Why Admin Portal Matters

**Quote (Gandara, Sun, 1:24:49):**
> "We want to see where customers are falling off from the app, being able to capture their click throughs... definitely reporting metrics, you know, how many customers signed up, how many service requests, how many new enrollments, how many new ad hocs, how much cancellation. So it's going to be really important for us to have this metrics as we are deploying this app. And, you know, because at the end of the day, we still have a business case to prove and we will continue to have to do that."

### Success Criteria

**Operational Efficiency:**
- **Manual intervention rate** - Target: <10% of transactions require manual admin action
- **Queue processing time** - Target: <24 hours for enrollment queue, <1 hour for support tickets
- **Admin user satisfaction** - Admins can find customer data quickly, perform tasks efficiently

**Data Quality:**
- **Inventory completion rate** - Target: 80% of active customers have at least 1 inventory item
- **Profile completion rate** - Target: 90% of customers have complete profile (name, address, email, phone)

**Business Case Validation:**
- **Real-time visibility** into app performance, customer behavior, revenue
- **Data-driven decisions** on which features to build, which markets to expand, which services to offer
- **ROI tracking** - Cost of app development vs revenue generated, call center savings

---

## OPEN QUESTIONS & RISKS

### Unresolved Questions

#### **APIs & Integration:**
1. **Which APIs will exist by MVP launch?** - Need commitment from Duke IT on timeline
2. **Enrollment API timeline** - If doesn't exist for MVP, how long will manual fallback be needed?
3. **Service request creation API** - Can app create service requests directly in Dynamics? Or manual queue?
4. **FSM tool selection** - What's the timeline for Duke to select and implement FSM tool?
5. **SSO capabilities** - Can Duke IT provide SSO for admin portal? Timeline?

#### **Data & Permissions:**
6. **Admin access to CRM** - Will all admins have CRM access? Or some use app backend only?
7. **Data privacy** - What customer data can admins view? Are there restrictions (e.g., payment info)?
8. **Multi-level permissions** - How many permission levels needed? (3? 5? 10?)

#### **Ad-Hoc Services:**
9. **Initial service list** - Which 5-10 services to launch with? Pricing finalized?
10. **Pricing approval workflow** - Who approves pricing changes? Product manager alone or executive approval?
11. **Regional pricing strategy** - How different should pricing be across markets?
12. **Contractor negotiation** - Timeline for negotiating flat rate prices with contractors?

#### **Reminders:**
13. **Default reminder list** - What's the "starter set" of reminders? (10? 20? 50?)
14. **Reminder frequency** - How often should reminders trigger? (monthly, quarterly, annually?)
15. **Asset-to-reminder mapping** - Which reminders apply to which inventory categories?

#### **Analytics:**
16. **Analytics tool** - Build custom dashboards or integrate third-party BI tool (Tableau, Looker, etc.)?
17. **Data retention** - How long to keep historical data? (1 year? 5 years? Forever?)

---

### Risks

#### 🔴 **HIGH RISK:**

**1. Duke IT API Delays**
- **Risk:** APIs promised for MVP don't deliver on time
- **Impact:** Manual fallback processes required longer than anticipated, admin workload increases
- **Mitigation:** Build robust manual fallback processes, get written commitment from Duke IT on API timeline

**2. CRM System Constraints**
- **Risk:** CRM systems (Commerce, Dynamics) can't support app volume or real-time API calls
- **Impact:** Performance issues, data sync delays, poor customer experience
- **Mitigation:** Load testing, discuss with Duke IT infrastructure requirements

**3. Admin User Adoption**
- **Risk:** Admins resist using new backend system, prefer existing CRM
- **Impact:** Low adoption, data entry errors, poor data quality
- **Mitigation:** Admin training, make new system EASIER than existing process, gather admin feedback early

#### 🟡 **MEDIUM RISK:**

**4. Ad-Hoc Service Catalog Readiness**
- **Risk:** Pricing not finalized, scope of work undefined, contractor negotiations incomplete
- **Impact:** Launch with very limited ad-hoc services, miss revenue targets
- **Mitigation:** Prioritize 3-5 "hero services," launch in limited geography, expand gradually

**5. Data Quality Issues**
- **Risk:** Customer data in CRM is incomplete or inaccurate (missing addresses, wrong phone numbers)
- **Impact:** Service request failures, customer frustration, admin manual cleanup
- **Mitigation:** Data validation rules, admin can correct data in app backend

**6. Analytics Tool Selection Delay**
- **Risk:** Decision on analytics/BI tool delayed, can't build dashboards in time
- **Impact:** No visibility into app performance at launch
- **Mitigation:** Start with basic reporting (SQL queries, CSV exports), upgrade to dashboards in Phase 2

---

## NEXT STEPS

### Before Session 3 (Contractor Discovery):

**Duke Team:**
- [ ] Identify which APIs will exist by MVP (get commitment from Duke IT)
- [ ] Define initial ad-hoc service list (5-10 services to launch with)
- [ ] Provide admin role definitions (who does what, how many users)
- [ ] Share CRM screenshots or demo access (so Orases understands current admin workflow)

**Orases Team:**
- [ ] Create admin portal wireframe concepts (dashboard, customer profile, service catalog management)
- [ ] Draft API specification for Duke IT (what data app needs from Commerce/Dynamics)
- [ ] Create data model for admin backend (entities, relationships, fields)

---

### After Session 3 (Contractor Discovery):

**Combined Deliverables:**
- Complete entity relationship diagram (customers, services, contractors, inventory, reminders)
- Admin portal wireframes (15-20 screens)
- API integration specification
- Manual fallback process documentation
- Analytics dashboard mockups

---

## ADMIN PORTAL WIREFRAMES NEEDED

### Dashboard Screens (5 screens):
1. **Operations Dashboard** - Service request overview, active jobs, exceptions
2. **Customer Management Dashboard** - New registrations, queue items, search
3. **Analytics Dashboard** - KPIs, trends, charts
4. **Executive Dashboard** - High-level business metrics
5. **Notifications Center** - Admin alerts, tasks, escalations

### Customer Management (4 screens):
6. **Customer Profile View** - All customer data in one place (profile, inventory, subscriptions, service history, loyalty)
7. **Customer Search** - Search by name, email, phone, account number
8. **Enrollment Queue** - Process failed enrollments
9. **Customer Inventory Management** - Add/edit inventory items

### Service Management (4 screens):
10. **Service Request Dashboard** - All service requests, filter, search
11. **Service Request Detail** - Drill into individual service request, edit status, reassign contractor
12. **Manual Service Request Creation** - Create service request on behalf of customer
13. **Escalation Ticket Management** - View/assign/resolve escalation tickets

### Catalog Management (5 screens):
14. **Ad-Hoc Service Catalog** - List of all services, filter, search
15. **Create/Edit Service** - Define service details, pricing, scope, availability
16. **Reminders Management** - List of all reminders, create/edit
17. **Asset Category Management** - Define inventory categories, tie to reminders
18. **Contractor Configuration** - View/edit contractor data, service area, lead time

### Analytics & Reporting (2 screens):
19. **Reports Library** - Saved reports, export options
20. **Custom Report Builder** - Ad-hoc queries, filters, export

---

## DATA MODEL SUMMARY

### Core Admin Entities:

**1. AdminUser**
- admin_user_id (PK)
- username
- email
- role (CSR, BackOffice, ProductManager, OperationsManager, Analyst, SuperAdmin)
- permissions (JSON or role-based)
- created_date
- last_login

**2. Customer (Aggregated from CRM + App)**
- customer_id (PK)
- customer_type (duke_native, pg_native, non_native)
- source_system (commerce, dynamics, app)
- utility_account_number (null if non-native)
- first_name, last_name
- email, phone
- address (street, city, state, zip)
- loyalty_points
- profile_completion_percentage
- created_date, last_login

**3. HomeInventory**
- inventory_id (PK)
- customer_id (FK)
- item_type (HVAC, WaterHeater, Appliance, etc.)
- category (tankless, tanked, central_ac, heat_pump, etc.)
- make, model, serial_number
- installation_date, age
- warranty_expiration
- location_in_home
- added_by (customer, admin, contractor)
- created_date, updated_date

**4. ServiceRequest**
- service_request_id (PK)
- customer_id (FK)
- service_type (hpp_covered, ad_hoc)
- service_category (HVAC, plumbing, electrical, etc.)
- problem_description
- inventory_item_id (FK, optional)
- contractor_id (FK)
- scheduled_date, scheduled_time_window
- status (requested, assigned, en_route, on_site, completed, cancelled)
- payment_status
- customer_rating
- source_system (app, phone, crm)
- created_date, updated_date

**5. AdHocService**
- service_id (PK)
- service_name
- service_code_sku
- category
- description
- scope_of_work (text)
- pricing_type (fixed, variable, quote)
- base_price
- regional_price_overrides (JSON)
- geographic_availability (zip_codes or regions)
- status (draft, active, inactive)
- created_by (admin_user_id)
- created_date, updated_date

**6. Reminder**
- reminder_id (PK)
- title
- description
- frequency (monthly, quarterly, biannually, annually, seasonal)
- asset_category (FK)
- optional_service_link (FK to AdHocService)
- optional_hpp_plan_link (FK)
- status (active, inactive)
- created_by (admin_user_id)
- created_date, updated_date

**7. EnrollmentQueue**
- queue_item_id (PK)
- customer_id (FK)
- enrollment_details (JSON)
- status (pending, in_progress, processed, failed)
- assigned_to (admin_user_id)
- created_date, processed_date

**8. EscalationTicket**
- ticket_id (PK)
- customer_id (FK)
- service_request_id (FK, optional)
- issue_category
- issue_description
- priority (low, medium, high, urgent)
- status (open, in_progress, resolved, closed)
- assigned_to (admin_user_id)
- resolution_notes
- created_date, resolved_date

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 19, 2025
**Status:** Ready for wireframe creation

---

**Related Documents:**
- [Customer App Preliminary Scope & Flows](Customer_App_Preliminary_Scope_and_Flows.md)
- [Session 1: Customer Discovery](Session_1_Customer_Discovery.md)
- [Session 2: Admin Discovery](Session_2_Admin_Discovery.md)
- [Session 3: Contractor Discovery](Session_3_Contractor_Discovery.md) - TO BE COMPLETED
- [HPP Plans Explained](HPP_Plans_Explained.md)
- [P&G Customer References](P&G_Customer_References.md)
