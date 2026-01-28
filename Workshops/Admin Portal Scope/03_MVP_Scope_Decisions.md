# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

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

