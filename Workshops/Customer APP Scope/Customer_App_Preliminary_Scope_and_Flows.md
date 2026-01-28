# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

---

## 1. EXECUTIVE SUMMARY

### Meeting Details
- **Date**: Session 1 Customer Discovery Workshop
- **Participants**:
  - **Duke Energy Team**: Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap
  - **Orases Team**: Tom Witt, Dave McArdle, Devin Gaither, Aksana Rahouski
- **Duration**: 2 hours
- **Format**: Virtual discovery session via video conference

### Purpose of Session
This initial customer discovery session was designed to define the MVP scope, capture customer journeys, and identify key integrations needed for the Duke Energy Residential Solutions Home Services Mobile App. The goal was to move beyond the RFP requirements and collaboratively define what the app will "look and feel like" to inform wireframe development, timeline refinement, and budget estimation.

The team emphasized a "future-minded" approach - disconnecting from existing application workflows to dream about the ideal customer experience while remaining grounded in technical realities and dependencies.

### Key Decisions Made

1. **Customer Segmentation Strategy**: Three distinct customer types will be supported in Phase 1 MVP:
   - Existing Duke/Piedmont customers with home protection plans (HPP)
   - Existing Duke/Piedmont customers without HPPs
   - Non-native customers (outside Duke/Piedmont utility service areas)

2. **Balanced MVP Approach**: The team selected a hybrid strategy (Option 1) that balances serving existing warranty customers while simultaneously building features to acquire new customer segments, particularly through ad-hoc service offerings with transparent, flat-rate pricing.

3. **Home Inventory as Cornerstone**: Building comprehensive home profiles and appliance inventories is critical to MVP success, with gamification and loyalty rewards identified as key mechanisms to incentivize profile completion.

4. **Phased Payment Integration**: Payment processing for ad-hoc services and new plan enrollments is in scope for Phase 1, but launch may proceed without full integration if dependencies aren't ready. Contractors may initially collect payments directly with transition to app-based payment as integration becomes available.

5. **FSM Tool Dependency**: Field Service Management (FSM) software integration is essential for real-time contractor tracking ("pizza tracker"), automated status updates, and contractor mobile app. Current internal Duke FSM (SAP-based) is limited. **For MVP Phase 1**: FSM tool NOT in scope - manual admin processes acceptable. **Phase 2+**: Duke evaluating Service Power and Service Bench as FSM vendors.

6. **DIY Content Evolution**: Rather than extensive static DIY library, the focus shifted toward AI-assisted troubleshooting and intelligent, inventory-based maintenance reminders that can recommend both DIY solutions and professional service booking options.

7. **Multi-Property Support in MVP**: Despite being an outlier use case, customers with multiple properties (vacation homes, rental properties) must be supported from Day 1 since profile validation against Duke Enterprise systems will surface multiple premises for some customers.

8. **Contractor Portal Scope** (Session 3): **Phase 1 = Admin-Only Approach** - NO contractor portal rebuild or mobile app for MVP. Contractors continue using existing Commerce CRM portal. Admin backend manages contractor configuration (trade assignments, zip codes, availability windows). Manual status updates by admin acceptable for MVP. Contractor mobile app and FSM integration deferred to Phase 2.

9. **Contractor Matching Algorithm** (Session 3): Matching based on **Trade + Zip Code + Primary/Secondary designation**. Customer sees pre-assigned primary contractor with option to request alternative via phone call (not in-app selection). 125-140 contractors in network (80% primary, 20% backup). Target 90-95% acceptance rate. Static availability buffers for MVP (HVAC 1-2 days, Electrical 5-6 days, Plumbing 3-5 days).

10. **Emergency Services Handling** (Session 3): Emergency services NOT booked through app. App asks qualifying questions (no heat in winter, gas leak, sparking outlet, etc.). If emergency detected, routes customer to phone call. Safety warnings displayed for life-threatening situations (gas leaks).

---

## 2. CUSTOMER TYPES & SEGMENTATION

### Three Primary Customer Segments

#### Segment 1: Existing Duke/P&G Customers WITH Home Protection Plans
- **Profile**: Current utility customers already enrolled in one or more HPP (average 1.7 plans per customer)
- **Current Behavior**: Service requests handled entirely via phone call to Duke call center (no self-service option)
- **Priority**: HIGH - These customers represent the immediate pain point and largest existing user base
- **MVP Features Needed**:
  - Service booking for covered repairs
  - Plan viewing and management (upgrade/downgrade/cancel)
  - Ad-hoc service booking for non-covered items
  - Home inventory to improve service delivery
  - Communication and scheduling preferences

**Quote from Kevin**: "We won't be able to enhance the existing customer base, be able to book these services, be able to give them some more features that they don't currently have, show that we're trying to help them with reminders of what they should be doing inside the home."

#### Segment 2: Existing Duke/P&G Customers WITHOUT Home Protection Plans
- **Profile**: Utility customers who haven't enrolled in HPP but may be interested in ad-hoc services or future plan enrollment
- **Current Behavior**: May call for service quotes or not engage with Duke Residential Solutions at all
- **Priority**: HIGH - Key acquisition target for both HPPs and ad-hoc revenue
- **MVP Features Needed**:
  - Transparent pricing for flat-rate ad-hoc services (heating/cooling checks, preventative maintenance)
  - Easy plan enrollment with multiple payment options
  - Access to rebates and utility incentives unavailable elsewhere
  - DIY content and home maintenance reminders to build engagement

**Quote from Kevin**: "The second phase of it is really, really phase one, getting outside of MVP, is expand that to include ad hoc services that anyone would sign up for. If you are not on one of our plans, but want somebody to come out doing a heating and cooling check, you can still download this app, book those services, get discounted rates, get transparent pricing."

#### Segment 3: Non-Native Customers (Outside Duke/P&G Territory)
- **Profile**: Homeowners anywhere in the U.S. who are NOT Duke or Piedmont utility customers
- **Current Behavior**: Using competitor services or local contractors without trusted advisor
- **Priority**: HIGH for Phase 1 - Critical for business expansion and proving white-label platform viability
- **MVP Features Needed**:
  - All ad-hoc service booking capabilities
  - Home inventory and profile management
  - Transparent pricing and contractor ratings
  - Cannot access utility rebates/incentives (but could if white-labeled with other utilities in future)

**Quote from Kevin**: "The third is truly non-native. They may or may not know Duke, but it doesn't really matter to them. It's outside of Duke's footprint."

### Duke vs. Piedmont (P&G) Considerations

- **No Material Differences**: For app purposes, Duke Energy and Piedmont Natural Gas customers are treated identically
- **Unified Platform**: Single app serves both customer bases
- **Behind-the-Scenes Distinction**: Customer validation APIs will identify utility provider, but user experience is seamless
- **Billing Integration**: Both can add HPP charges to utility bills or choose credit card payment

**Quote from Son**: "You can say Duke and P&G anonymously. When we say non-native, these are customers that are not our utility customers that can access the app and get our services depending on where they live."

### Customer Volume & Priorities

- **Current HPP Customers**: 800K+ existing customers (99%+ have HPP charges on utility bills)
- **Target Distribution**: All three segments are "critical for the success of this app" per Son Gandara
- **Acquisition Goals**:
  - Generate $25M in new ad-hoc service revenue within 12 months
  - Acquire 250K non-native customers within 24 months (per RFP background)
  - Reduce call center volume by 40%

**Quote from Son**: "Everything within phase one is really, we are trying to target all the customer segments that we've just talked about... It's critical for us and the success of this app and for us to continue to invest in the app is to get those acquisitions and engagements across this customer segment."

---

## 3. MVP SCOPE DECISIONS

### Phase 1 MVP Features (IN SCOPE)

#### Customer Registration & Onboarding ✅ MVP
- **Profile Creation**: All users must create app profile (username, password, "My Account") separate from Duke/P&G utility accounts
- **Guest Access**: Very limited - perhaps some DIY content browsable, but profile creation required for core functionality
- **Address Entry**: Minimum requirement is home address (enables public data pre-fill of home characteristics)
- **Guided Onboarding**: Walk-through prompts to provide home information (zip code, address pulls in square footage, year built, property type, etc.)
- **Profile Validation**: For Duke/P&G customers, API checks address/name to link existing HPP plans to app profile
- **Multi-Property Support**: ✅ IN SCOPE for MVP - If customer has multiple premises, all must be accessible in single profile

**Quote from Son**: "Our assumption is there might be very little features, maybe some content, maybe some things with a guest profile. But what we do want is for the user to create a profile, user ID, password, my account."

**Quote from Son on Multi-Property**: "If you think about our phase one... if I create a profile, and you validate me against Duke Enterprise, and I have two premises, and I have two separate home protection plans, and I want to service it, I feel like we need to build that capability right up front."

#### Home Protection Plan Management ✅ MVP
- **View Existing Plans**: Display all active HPPs linked to customer's address/profile (average 1.7 plans per customer)
- **Enroll in New Plans**: Full enrollment workflow with plan selection, terms acceptance, payment method choice
- **Upgrade/Downgrade Plans**: Modify coverage levels or switch between plan tiers
- **Cancel Plans**: Self-service cancellation (compliance requirement: "If you can sign up for something online, you also have to be able to cancel it... just as easy" - Dana)
- **Plan Details**: Display coverage terms, what's included/excluded, pricing, billing method
- **Multiple Plans Per Property**: Support customers with multiple HPPs (e.g., HomeWire + Heating/Cooling + Water Heater)
- **Plan Comparison**: Show available plans customer could add to their portfolio

**Quote from Son**: "That is in the scope for phase one for us, that customers can sign up for new plans, upgrade plans, or unenrolled plans."

#### Home Inventory/Profile Building ✅ MVP
- **Manual Entry**: Customers can add appliances, systems, and equipment details (make, model, serial number, age)
- **Barcode Scanning**: Scan appliance labels to auto-populate make/model information
- **Pre-Fill from Public Data**: Auto-populate home characteristics from address (square footage, year built, property type)
- **Progressive Profiling**: Inventory can be built over time, not required all at once
- **Incentivized Completion**: Gamification and loyalty rewards tied to profile completion percentage
- **Contractor-Enhanced Data**: Technicians can add/update inventory during service visits **(NEW FROM SESSION 3)**
- **Recall Checking**: System checks CPSC database for recalls on registered appliances (future automation)
- **Maintenance Schedules**: Auto-generate recommended maintenance based on inventory (e.g., "flush water heater annually")

**✅ UPDATED FROM SESSION 3 - Contractor Inventory Capture**:
- **Opportunity**: Contractors capture appliance/system data during service visits (make, model, serial, manufacture date, photos)
- **Benefit**: High-quality inventory data without customer effort, improves future service delivery
- **MVP Implementation**: TBD - Options include:
  - **Option A**: Contractor takes photo, emails to admin, admin manually enters into customer profile
  - **Option B**: Simple form in existing contractor portal to submit data directly to app backend
  - **Option C**: Defer to Phase 2 contractor mobile app
- **Contractor Incentive**: TBD - May include small bonus per item captured, or positioned as creating future work pipeline
- **Process Owner**: Duke contractor field coordinators to communicate value proposition

**Quote from Son**: "We would try to walk them through of trying to create a home profile... because minimum, we need to know where they live, right? If they're going to potentially create a service request."

**Quote from Kevin**: "Building loyalty rewards... You build a profile, depending on the percentage of completion of your profile, we'll give you some loyalty points, which will be credited for future services."

**Quote from Kevin (Session 3)**: "How do we collect that information from the contractor to feed it back into the database... So we're saying, hey, if you're already at home, please collect this additional information... what that will do is provide us more information about the home. So we'll know what parts you need, et cetera. And they'll see the benefit of that."

#### Service Booking - HPP Covered Services ✅ MVP

**✅ UPDATED FROM SESSION 3:**

- **Symptom-Based Intake**: Customer describes issue (not technician-level diagnosis required)
- **Coverage Check**: App runs basic eligibility questions to determine if likely covered under existing plan
- **Inventory Integration**: If appliance/system already in profile, pre-populate service request
- **Inventory Building During Booking**: If not in profile, customer adds basic details during service request

**Contractor Assignment** (Trade + Zip Code → Primary Contractor):
- **Automated Matching**: System assigns primary contractor based on trade + zip code (no customer selection)
- **Customer Experience**: "Your contractor: ABC Plumbing" (pre-assigned, not "Select a contractor")
- **Contractor Details**: Company name, contact phone, brief description
- **Requesting Alternative**: Small link "Need a different contractor?" → triggers phone call to admin (NOT in-app contractor list)
- **Why Limited Choice**: Negotiated pricing, SLA contracts, prevent "contractor shopping" for coverage exceptions

**Date/Time Selection**:
- Customer chooses from available windows based on contractor's static availability buffer
- **Lead Times**:
  - HVAC/Water Heater: 1-2 business days (emergency-priority)
  - Plumbing: 3-5 business days
  - Electrical (non-emergency): 5-6 business days
  - Appliance: 2-3 business days
- **Time Windows**: Varies by contractor (8am-12pm, 1pm-5pm most common)
- Customer selects: "Thursday, March 15, 9am-12pm"

**Booking Confirmation**:
- Status: "Pending Confirmation"
- Notification: "We received your service request and are contacting your contractor"
- Admin manually contacts contractor within 1 hour (email/phone)

**Contractor Acceptance** (Behind the Scenes):
- Contractor responds within 24 hours (accepts or proposes alternative time)
- **If Accepted**: Admin updates app → Status: "Confirmed - ABC Plumbing - Thursday 9-12am"
- **If Alternative Proposed**: Admin calls customer to confirm new time OR tries backup contractor

**Confirmation & Communication**: Customer receives confirmation via preferred channel (push, SMS, email)

**Rescheduling**: Customer can reschedule within policy constraints (e.g., not within 24 hours)

**Cancellation**: Self-service cancellation with policy guardrails

**No Payment Required**: Covered services have $0 customer cost at time of booking

**Quote from Kevin**: "For if they're on a warranty plan, we will have our recommended contractor... hey, this is your contractor that's going to be out there."

**Quote from Kevin (Session 3)**: "I'd rather not give that transparent, hey, go select somebody else, because we have negotiated pricing, negotiated territories... as long as you display it, say, hey, here's who's coming out to your home... if you would like to change the contractor... it's like a little button that you can say, okay, I want to edit it."

#### Service Booking - Ad-Hoc (Non-Covered) Services ✅ MVP

**✅ UPDATED FROM SESSION 3:**

- **Service Catalog**: Browse/search available ad-hoc services with transparent, upfront pricing
- **Flat-Rate Pricing**: Preventative maintenance and common services priced clearly (e.g., "$99 HVAC cleaning check")
- **Variable Pricing**: Some services show price ranges (e.g., "$120-$190 ceiling fan installation")
- **No Plan Required**: Available to all customer types, including non-natives
- **Discounted Rates**: Duke may subsidize to drive engagement (charge customer $99, pay contractor $125)

**Contractor Assignment for MVP** (Same as Warranty):
- **Primary Contractor Assigned**: Ad-hoc services use same primary contractor assignment as warranty services for MVP
- **Customer Experience**: "Your contractor: ABC Plumbing - $99" (contractor pre-assigned based on trade + zip)
- **NO Contractor Marketplace in MVP**: Customer does NOT see 2-5 contractors to choose from
- **NO Ratings Displayed in MVP**: Contractor ratings NOT shown during booking

**Phase 2 - Contractor Marketplace** (Future State):
- **Multiple Contractor Options**: Show 2-5 contractors with pricing and ratings
- **Customer Selection**: Customer selects based on price, availability, ratings
- **Ratings Displayed**: "ABC Plumbing - 4.8 stars - 127 reviews"
- **Variable Pricing by Contractor**: Different contractors may charge different amounts for same service
- **Why Future**: Requires in-app ratings collection, contractor acceptance of marketplace model, complex matching logic

**Payment** (Contractor Collects On-Site for MVP):
- **MVP**: Contractor collects payment at service completion (cash, check, credit card via contractor's reader)
- **App Displays**: "Total cost: $99. Payment collected by ABC Plumbing at service completion."
- **Phase 2**: Customer pre-pays in app, Duke pays contractor net of commission

**Quote from Kevin**: "I do want to offer those ad hoc services early on, things that are flat rate, transparent pricing that we can provide up front... that's missing from the market today, that we really want to show that transparent pricing up front."

**Quote from Kevin (Session 3)**: "For MVP... we want to stay focused on the primary... especially when we start talking about ad hoc services, then showing different contractors won't be fine... But I would say that for this, you stick to what's the primary's contractor availability."

#### Contractor Matching & Scheduling ✅ MVP

**✅ UPDATED FROM SESSION 3:**

**Contractor Network**:
- **Total Contractors**: 125-140 contractors across 4-5 states (NC, SC, FL, OH, IN)
- **Primary Contractors**: ~80% (100-112 contractors) - first assigned, receive jobs first
- **Backup Contractors**: ~20% (25-28 contractors) - overflow when primary unavailable
- **Coverage**: 99-100% coverage for HVAC, Plumbing, Electrical, Water Heater; 95%+ for Appliance
- **Multi-Trade**: Most contractors offer 2-3 trades (e.g., Plumbing + HVAC + Electrical)

**Matching Algorithm** (Trade + Zip Code + Primary/Secondary):
1. **Trade Match**: System identifies correct trade (electrical, plumbing, HVAC, appliance, water heater)
2. **Zip Code Match**: Exact zip code assignment (NOT radius-based). Contractors assigned specific zip code lists.
3. **Primary Contractor**: System auto-assigns primary contractor for that trade + zip code
4. **Customer Experience**: Customer sees **pre-assigned contractor** - "This is your contractor: ABC Plumbing"
5. **Requesting Alternative**: Small link "Need a different contractor?" triggers **phone call to admin** (NOT in-app contractor selection)

**Availability & Lead Times** (Trade-Specific):
- **HVAC/Water Heater**: 1-2 business days (emergency-level priority)
- **Plumbing**: 3-5 business days (standard priority)
- **Electrical (non-emergency)**: 5-6 business days (filler work)
- **Appliance**: 2-3 business days
- **Static Buffer Approach**: Contractors provide availability rules (e.g., "Available Mon-Fri 8-5, 3-day buffer")
- **No Real-Time Calendars**: MVP does not check contractor's actual schedule (FSM tool required for that - Phase 2)

**Time Windows** (Contractor-Specific):
- **Half-Day**: 8am-12pm or 1pm-5pm (most common)
- **Full-Day**: 8am-5pm (rare, rural contractors only)
- **Varies by Trade**: Same contractor may have different windows for different trades
  - Example: Plumbing only Tue/Thu 9-12, HVAC Mon-Fri 8-5

**Customer Selection**:
- Customer chooses preferred **date/time window** from available options
- Customer does NOT choose contractor (pre-assigned)
- **Warranty Services (HPP)**: Primary contractor assigned, customer can request exception via phone
- **Ad-Hoc Services (MVP)**: Primary contractor assigned same as warranty
- **Future Ad-Hoc (Phase 2)**: May show 2-3 contractors with pricing/ratings for customer to select

**Contractor Acceptance**:
- **Target**: 90-95% acceptance rate (contractors rarely decline due to SLA contracts)
- **MVP Process**:
  1. Customer books service in app (status: "Pending Confirmation")
  2. Admin manually contacts contractor (email/phone) within 1 hour
  3. Contractor responds within 24 hours (accepts or proposes alternative time)
  4. Admin updates app: "Confirmed - ABC Plumbing - Thursday 9-12am"
  5. If contractor proposes alternative: Admin calls customer to confirm new time OR tries backup contractor
- **Phase 2 (With FSM)**: Contractor receives push notification in mobile app, one-tap acceptance

**Exception Handling**:
- **Primary Unavailable**: Admin tries backup contractor for same time window (priority: keep time > keep contractor)
- **All Contractors at Capacity**: Offer later time windows to customer
- **Rural Areas**: Some zip codes have only 1 contractor (no backup) - communicate limitations
- **Emergency Events** (hurricanes, etc.): Admin can override assignments, extend buffers, display service delay banner

**Current State**: Trade and zip code assignment exists in internal SAP-based system. Admin manually manages assignments today. MVP copies contractor configuration to app backend (manual data export/import).

**Quote from Kevin (Session 3)**: "We will default based off our default logic. So we have a primary contractor that we will send out for HPP plan. That is what it's going to display in the app, so they know we have a contractor coming out there, who's going to be that person."

**Quote from Chris Murphy (Session 3)**: "Many of our customers prefer a certain contractor. They are used to having that contractor come out and they also, the contractor gets familiar with that customer's home with the previous issues that they've had. So many customers are more than willing to reschedule when a contractor is not available so that they can have that same contractor come out."

#### Communication & Notifications ✅ MVP

**✅ UPDATED FROM SESSION 3:**

**Multi-Channel Delivery**: Push notifications, SMS, email, in-app notification center
**Customer Preferences**: User selects preferred communication channels

**MVP Service Request Status Flow** (Manual Admin Updates):
1. **Booking Confirmation** (Immediate):
   - Customer creates service request in app
   - Status: "Pending Confirmation"
   - Notification: "We received your service request and are contacting your contractor"

2. **Appointment Confirmed** (Within 24-48 hours):
   - Admin manually updates after contractor acceptance
   - Status: "Confirmed - [Contractor Name] - [Date] [Time]"
   - Notification: "Your appointment is confirmed! ABC Plumbing on Thursday 9-12am"
   - Contact info for contractor provided (phone number)

3. **Appointment Changed** (If needed):
   - If contractor proposes alternative time and customer accepts
   - Admin updates app with new time
   - Notification: "Your appointment time has changed to Friday 1-4pm"

4. **Service Completed** (After contractor completes):
   - Admin manually updates when contractor marks complete in Commerce CRM
   - Status: "Completed - [Date]"
   - Notification: "Your service has been completed"
   - Survey link sent via external process (email/SMS)

**MVP Status Limitations** (No FSM Integration):
- **NO intermediate statuses**: No "Dispatched", "En Route", "On-Site", "In Progress" for MVP
- **Data Sync Delays**: Customer may not see real-time updates if contractor reschedules with customer directly and doesn't update Duke systems
- **Manual Admin Updates**: Admin team updates statuses based on contractor communication (phone/email)
- **Contractor Provides En Route Updates**: ~70% of contractors send their own "on my way" texts to customers (not through app)

**Phase 2 (With FSM Tool)**:
- **Automated Status Updates**: Dispatched, En Route, On-Site, In Progress, Completed (real-time)
- **Pizza Tracker**: GPS tracking of contractor location with ETA
- **Contractor Mobile App**: Contractor updates status in their mobile app, syncs to customer app automatically

**Day-Before Reminders** (Optional for MVP):
- Risk: Reminder may conflict if contractor rescheduled with customer without updating Duke systems
- Safer approach: Let contractors handle reminders until FSM integration complete

**Two-Way Communication**:
- **MVP**: Customer can call contractor directly (phone number provided)
- **Phase 2**: In-app messaging between customer and contractor (like Uber chat)

**Rescheduling Notifications**: If contractor needs to change time, admin calls customer to confirm, then updates app

**Quote from Son**: "At a minimum, I would say all those things about like if I schedule, I want to know I'm confirmed someone's coming. If I want to reschedule and having that notification and whatever preference that I would want to be notified."

**Quote from Kevin (Session 3)**: "Once we've created that order, we handed off that customer communication to the contractor to do up until the point that they've completed it... the consistency of whether they update it is a challenge."

#### "Pizza Tracker" Real-Time Tracking ❌ NOT IN MVP - PHASE 2 ONLY

**✅ UPDATED FROM SESSION 3:**

**Phase 2 Feature** (Requires FSM Tool):
- **GPS Tracking**: See contractor's real-time location as they travel to appointment (like Uber/Lyft)
- **ETA Updates**: Dynamic arrival time estimates ("Technician is 15 minutes away")
- **Service Progress**: Real-time updates (Technician Arrived, Diagnosis Complete, Repair in Progress, etc.)
- **Map View**: Customer sees contractor location on map as they move
- **Completion Notification**: Alert when service is finished

**Why NOT in MVP**:
- **FSM Tool Dependency**: Requires FSM tool (Service Power or Service Bench) with contractor mobile app
- **Contractor Mobile App**: Contractors must use FSM mobile app with GPS tracking enabled
- **Location Sharing**: Privacy controls and contractor acceptance needed
- **Timeline**: FSM tool procurement and contractor onboarding takes 6-12 months

**MVP Workaround**:
- Contractors send "on my way" text/call to customers directly (~70% do this today)
- Customer can call contractor directly if ETA needed
- Confirmed appointment time window (9am-12pm) sets expectation

**Quote from Dana**: "Blue sky this, I want to know who's showing up at my door. And when they're showing up... I want pizza tracker all the way through."

**Quote from Son**: "From what we're seeing through the demos, it's really that FSM tool that enables that because the tool itself has a customer integration, customer experience and notifications back."

**Quote from Kevin (Session 3)**: "The FSM software that we looked at was they had tracking like that, so if it was all that for some software is on the technicians app or on their phone then it would actually track where they are."

#### DIY Content & Maintenance Reminders ✅ MVP
- **Inventory-Based Reminders**: Auto-generate maintenance schedules based on appliances in profile
  - Example: "Flush water heater annually" for tank water heaters
  - Example: "Change HVAC filter quarterly" based on system type
- **Default Reminder Sets**: New homeowners get standard home maintenance checklist
- **Custom Reminders**: Users can add their own reminders (pool maintenance, seasonal tasks)
- **Reminder Opt-Out**: Users can dismiss or snooze reminders they don't want
- **DIY + Service Options**: Each reminder offers two paths - instructions to DIY or "Book Service" button
- **Browsable Content Library**: General home maintenance tips searchable/browsable
- **Age-Based Recommendations**: "Your system is 15 years old, here's what to expect in next 5 years"
- **Recall Alerts**: Proactive notifications if CPSC issues recall for appliances in customer's inventory

**Evolution from Original Concept**: Team shifted from extensive static DIY library toward intelligent, actionable reminders with AI-assisted troubleshooting planned for future.

**Quote from Kevin**: "What would be valuable is more the reminders of saying, hey, based off this inventory you have, here's some considerations that you need to make sure you're doing to maintain your home and building that and maintaining that reminder schedule for them."

**Quote from Kevin on AI Future**: "The initial, especially where we're going with AI, AI is going to pretty much help people through anything. That's who's going to be a DIY content in the future."

#### Loyalty/Rewards/Gamification ✅ MVP
- **Profile Completion Score**: Visual indicator (percentage) of how complete home profile is
- **Loyalty Points**: Earn points for completing profile sections, scheduling maintenance, engaging with app
- **Point Redemption**: Points convert to dollar credits for future services
- **Home Health Scorecard**: Risk assessment based on appliance ages, maintenance history, known issues
  - Concept similar to credit score but for home asset health
  - "Your HVAC is 18 years old (avg lifespan 15) - start budgeting for replacement"
  - "You maintained this system beyond expected life - great job!"
- **Badge System**: Fitbit-style achievement badges for milestones (first service booked, 5 reminders completed, etc.)
- **Value Tracking**: Show customer cumulative savings (like Amazon Prime savings tracker)
- **Educational Framing**: Frame scores positively - celebrate wins, gently warn of upcoming needs

**Strategic Importance**: Gamification is essential to incentivize home inventory building, which unlocks upselling, preventative scheduling, and customer stickiness.

**Quote from Son**: "It's in the scope for phase one. We referenced it as like a home health scorecard... if you start filling out more information, if you have more engagement, if you create more service, it's basically you might get a score."

**Quote from Dana**: "I definitely think we need some way to keep the customer engaged. If I'm earning this fake badge... 5,000 steps, I got a badge, 10,000 steps, I got a badge."

#### Payment Processing ⚠️ MVP (Phased Implementation - Nice to Have, NOT Required)

**✅ UPDATED FROM SESSION 3:**

**MVP Approach: Contractor Collects Payment On-Site**

**Use Cases for Payment Integration**:
1. **Ad-Hoc Service Payment**: Customer pays for flat-rate or variable-priced non-covered services
2. **New HPP Enrollment**: Customer enrolls in new plan and chooses payment method
3. **Recurring HPP Charges**: Monthly subscription billing for plans NOT on utility bill

**Phase 1 MVP - Contractor On-Site Collection**:
- **Ad-Hoc Services**: Contractor collects payment directly at service completion
- **Payment Methods Contractors Accept**: Cash, check, credit card via contractor's Square/Stripe/Clover reader
- **Customer Experience**:
  - App displays: "Total cost: $99"
  - "Payment will be collected by ABC Plumbing at service completion"
  - "Accepted methods: Cash, check, credit card"
- **Backend**: Contractor reports payment collected to Duke (for commission tracking if applicable)
- **Pros**: Launch immediately without payment integration dependency
- **Cons**: Customer cannot pre-pay in app, may reduce conversion for non-native customers

**Phase 2 - App-Based Payment Integration**:
- **Customer Pre-Pays in App**: Credit card, Apple Pay, Google Pay at time of booking
- **Duke Collects Payment**: Duke charges customer's card, pays contractor net of commission
- **Benefits**: Customer convenience, Duke controls payment flow, eliminates on-site collection burden

**Payment Methods to Support** (Phase 2):
- **On Utility Bill**: For Duke/P&G customers only - easiest, lowest cost (prorated fee vs. credit card fees)
- **Apple Pay / Google Pay**: Preferred for customer convenience (no typing credit card numbers)
- **Credit/Debit Card**: Direct card entry as fallback
- **ACH**: For recurring charges (lower fees than credit cards)

**HPP Covered Services**:
- **No Payment Required**: Covered services have $0 customer cost at time of booking
- **Excess Charges**: If service exceeds coverage limit, contractor collects excess amount on-site from customer

**Commission Model** (TBD):
- **Question**: Does Duke take percentage of ad-hoc services?
- **Example**: Customer pays contractor $99, Duke takes $24 commission, contractor keeps $75?
- **Phase 1**: TBD - may start with no commission to incentivize contractor participation
- **Phase 2**: Define commission structure for app-based payments

**Quote from Son**: "We have payment integration as part of this. How we prioritize that as part of MVP and the iterations, that will be part of our phases, but that is in scope."

**Quote from Kevin (Session 3)**: "Phase 1 - contractor collects payment on-site... For the customers that are on bill, it's even easier because you just say, do you want to add this to your bill? They say yes."

#### Emergency Service Handling 🚨 NOT IN APP - PHONE ONLY

**✅ NEW FROM SESSION 3:**

**Emergency services are NOT booked through app** - customers routed to phone call for immediate assistance.

**App Triage Flow**:
1. **Customer Starts Service Request**: Selects issue type (HVAC not working, electrical problem, gas smell, etc.)
2. **App Asks Qualifying Questions**:
   - **HVAC**: "Is your home temperature below 60°F?" "Is it currently freezing outside?"
   - **Electrical**: "Is anything sparking or smoking?" "Do you smell burning?"
   - **Gas**: "Do you smell gas?" "Do you hear hissing sounds?"
   - **Water**: "Is there active flooding?" "Is water damage spreading?"
3. **Emergency Detected**:
   - App displays: "⚠️ This appears to be an emergency. Please call us immediately at 1-800-XXX-XXXX"
   - **For Safety Emergencies** (gas leaks): "🚨 SAFETY ALERT: If you smell gas, evacuate immediately and call your gas utility emergency line: 1-800-GAS-LEAK"
   - App does NOT create service request (routed to phone)
4. **CSR Handles Emergency**:
   - Customer calls Duke emergency line
   - CSR determines urgency, directly calls primary contractor
   - CSR negotiates soonest available time (2-4 hours for true emergencies)
   - CSR confirms with customer via phone
5. **Optional: Admin Adds to App** (Post-Call):
   - After phone resolution, admin can manually create service record in app
   - Customer sees service history: "Emergency HVAC Repair - [Date] - ABC HVAC"
   - Provides complete service history in one place

**Examples of Emergency Scenarios**:
- No heat in winter (freezing temps)
- No AC in extreme summer heat (vulnerable customer)
- Gas leak smell
- Electrical sparking/smoking
- Active water flooding
- Sewage backup

**Examples of NON-Emergency** (Can Book in App):
- One outlet not working (can work around it for a week)
- Light switch broken (non-essential)
- Toilet running constantly (annoying but not damaging)
- Refrigerator not cooling well (can save food temporarily)

**Why Route to Phone**:
- **Safety**: Some emergencies require evacuation or 911 call, not contractor
- **Speed**: CSR can coordinate immediate dispatch, confirm contractor availability in real-time
- **Triage**: CSR validates true emergency vs. customer perception of urgency
- **Contractor Availability**: Emergency slots require direct contractor negotiation

**Quote from Kevin (Session 3)**: "We will have those emergency questions. It won't be a clear cut, hey, is this an emergency for a customer? It will be based off those criteria that they filled in. We'll determine this emergency and hey, call in, go down a flow."

**Quote from Dana (Session 3)**: "Most customers would say everything's an emergency, but there's a handful of things that we can definitely help with that should feed through the app, no problem. And then there's a smaller set of things that should be call us for the emergency."

#### Service History & Records ✅ MVP
- **Exportable Service Log**: Complete record of all services performed, tied to appliances/systems
- **Service Details**: Date, contractor, technician name, work performed, parts used, cost (if applicable)
- **Tied to Inventory**: Each service linked to specific appliance/system in home profile
- **Home Sale Use Case**: Customer can export full service history to share with home buyers
- **Warranty Tracking**: Maintain records of equipment warranties, including manufacturer warranties
- **Invoice/Receipt Storage**: PDFs of invoices and receipts accessible in app
- **Maintenance Proof**: Documentation that preventative maintenance was performed on schedule

**Future Enhancement**: Auto-transfer home profile and service history to new homeowner when house sells.

**Quote from Dana**: "If I'm getting ready to package my home for sale and the new homeowners and I want to send them all the information, I could link them to PDFs or invoices and proof that I maintenance this, this and this."

#### Customer Feedback/Reviews ⚠️ MVP - External Process Only

**✅ UPDATED FROM SESSION 3:**

**MVP Approach - NO In-App Ratings or Display**:
- **Survey Delivery**: Sent after service completion via external market research vendor (email/SMS)
- **Data Collection**: Contractor name, technician name, service details auto-populated
- **Rating System**: Star ratings and written feedback via external survey
- **NOT Displayed to Customers in MVP**: Contractor ratings NOT shown during booking for MVP
- **NOT Collected In-App**: Customer does NOT rate contractor within app for MVP

**Why External Process for MVP**:
1. **Existing System**: External survey process already established and working
2. **Legal/Compliance**: In-app reviews require legal review, terms of service updates
3. **Contractor Relationships**: Avoiding "Yelp effect" where customers shop for highest-rated contractor
4. **Primary Assignment**: MVP uses primary contractor assignment (no selection), so ratings less relevant
5. **Small Contractor Network**: 125-140 contractors, don't want public ratings to create tension

**Backend Use of Ratings**:
- Ratings data used internally by Duke to evaluate contractor performance
- Aggregate ratings reported back to contractors (monthly/quarterly scorecards)
- Low-performing contractors may be replaced as primary contractor
- Ratings do NOT factor into customer-facing contractor assignment algorithm for MVP

**Phase 2 - In-App Ratings** (Future State):
- **For Ad-Hoc Marketplace**: When customers can select from multiple contractors
- **Display**: "ABC Plumbing - 4.8 stars - 127 reviews"
- **In-App Collection**: Customer rates immediately after service completion
- **Review Display**: Customer can read recent reviews before booking
- **Two-Way Rating**: Contractors rate customers (Uber model) to flag difficult customers

**Current Process**: Survey link sent via email/SMS after contractor marks job complete in Commerce CRM. Feedback flows to Duke's market research database, not directly into app.

**Quote from Kevin**: "It's collected outside of the app, and we will feed it back to the app through, hey, this is what we know about this contractor, here's the scores, etc."

**Quote from Kevin (Session 3)**: "It's the primary contractor. We'll consider it [ratings] in the fact that they'll be our primary contractor or not... And if we do end up with a situation, you know, on occasion, what we'll do is replace the contractor."

### Phase 2+ Features (EXPLICITLY OUT OF MVP SCOPE)

#### Phase 2 Features
- **AI Virtual Assistant**: Conversational AI to troubleshoot issues and recommend DIY vs. professional service
- **Advanced Contractor Portal**: Full two-way integration, contractor app for job acceptance, updates, inventory management
- **White-Label Platform**: Template app that other utilities can brand and deploy in their territories
- **Expanded Service Categories**: Beyond core trades (electrical, plumbing, HVAC, appliance) to include:
  - Pool service
  - Roof repairs/inspections
  - Window sealing/replacement
  - Insulation
  - General handyman services (2-3 years out)
- **Home Sale Transfer**: Automated transfer of home profile and service history to new homeowner
- **Energy Efficiency Integration**: Real-time energy monitoring tied to utility data
- **Predictive Maintenance**: Machine learning to predict failures before they occur
- **Referral Network**: "Binded Duke" integration for trades not under direct Duke contract

#### Deprioritized/Out of Scope
- **Commercial Properties**: Only residential properties supported (no landlords managing multiple units, no apartment buildings)
- **Unlicensed Trades**: No lawn care, painting, or other non-licensed services in near-term
- **In-App Messaging**: Two-way chat between customer and contractor (future enhancement)
- **Contractor Direct Payment**: Contractors paying Duke for job leads (current model is Duke pays contractors)

---

## 4. CUSTOMER FLOWS

### Flow 1: Existing Customer with HPP Plan - Books Covered Service

**Persona**: Eleanor, 58, existing Duke customer with HomeWire plan, existing app on phone, HVAC making strange noise

**Pre-Conditions**:
- Customer already downloaded app via welcome letter or service reminder prompt
- Profile created and linked to Duke Enterprise account
- Existing HPP plans visible in "My Account"

**Steps**:

1. **Open App & Navigate**
   - Customer opens app from home screen
   - Logs in with username/password (or FaceID/TouchID)
   - Lands on dashboard/home screen

2. **Initiate Service Request**
   - Taps "Book Service" or "Request Service" button
   - Selects affected area: "Heating & Cooling"

3. **Check Existing Inventory**
   - App checks if HVAC system already in home profile
   - **If YES**: Pre-populates system details (make, model, age)
   - **If NO**: Prompts customer to add basic info (or skip and have contractor collect later)

4. **Describe Issue**
   - Symptom checklist or free-text description
   - Example: "Strange grinding noise when AC turns on"
   - App asks 2-3 diagnostic questions to assess coverage likelihood

5. **Coverage Check**
   - App runs basic eligibility: "Do you have Heating & Cooling plan? YES"
   - Displays: "This service is likely covered under your H&C Protection Plan"
   - Shows $0 estimated cost (with caveat about non-covered scenarios)

6. **Contractor Assignment**
   - App queries FSM/Duke system: Trade=HVAC, ZipCode=12345
   - Returns primary contractor: "ABC Heating & Cooling"
   - Displays contractor card with:
     - Company name and logo
     - Star rating (4.8/5)
     - "Recommended Contractor" badge
     - Contact phone number
     - Small text: "Prefer different contractor? Tap here"

7. **Select Date & Time**
   - System shows available windows based on 1-day buffer for HVAC (emergency) or 3-day buffer (non-emergency)
   - Customer selects: "Tomorrow, 9am-12pm"
   - Confirmation: "ABC Heating will arrive between 9am-12pm on Tuesday, March 15"

8. **Review & Confirm**
   - Summary screen:
     - Service: Heating & Cooling Repair
     - System: Carrier HVAC Model ABC123 (if in inventory)
     - Contractor: ABC Heating & Cooling
     - Time: Tuesday 3/15, 9am-12pm
     - Cost: $0 (covered under plan)
   - "Confirm Booking" button

9. **Booking Confirmation**
   - Confirmation screen with booking reference number
   - "Add to Calendar" button
   - Immediate push notification
   - SMS/email confirmation sent (per customer preference)
   - Displays: "ABC Heating will call you within 2 hours to confirm" (current process) OR "Your appointment is confirmed" (future state with FSM)

10. **Pre-Service Communication**
    - Day before: Reminder notification "Your HVAC service is tomorrow 9am-12pm"
    - Morning of: "Your technician is on the way" (if FSM/GPS tracking enabled)
    - **If Pizza Tracker Enabled**: Real-time map showing technician location and ETA

11. **During Service**
    - **If FSM Enabled**: Status updates (Arrived, Diagnosing Issue, Ordering Parts, Repair Complete)
    - **Contractor Actions**: Technician updates HVAC inventory in their contractor portal (model, serial, photos)
    - Data syncs back to customer's home profile in app

12. **Service Completion**
    - Push notification: "Your service is complete!"
    - Service details added to customer's service history
    - **If Contractor Added Inventory**: Customer sees updated HVAC profile with photos, notes
    - **If Additional Costs**: "Additional work required outside coverage: $150. Paid directly to ABC Heating." (current process)

13. **Post-Service**
    - Survey link sent via email/SMS (not in-app for MVP)
    - Customer rates contractor and service quality
    - Service record exportable as PDF from "Service History" section
    - New maintenance reminders auto-generated: "Schedule annual HVAC checkup in 12 months"

**Alternate Paths**:
- **Service Not Covered**: At Step 5, app determines issue might not be covered → routes to ad-hoc service flow with pricing
- **Contractor Unavailable**: At Step 7, no windows available within desired timeframe → customer chooses later date or requests secondary contractor
- **Customer Reschedules**: Customer navigates to "My Appointments" → taps appointment → "Reschedule" (if >24 hours away)
- **Customer Cancels**: Customer navigates to "My Appointments" → taps appointment → "Cancel" (if >24 hours away)

---

### Flow 2: Existing Customer - Books Ad-Hoc Service (Preventative Maintenance)

**Persona**: Emma, 34, Duke customer without HPP, saw email promo for "$99 HVAC Cleaning & Check", wants to book before summer

**Pre-Conditions**:
- Customer downloaded app from email promo link
- Created profile (no HPP plans)
- Added home address only

**Steps**:

1. **Discover Service**
   - Opens app, browses "Preventative Maintenance" section
   - Sees "$99 HVAC Seasonal Cleaning & Check" tile with:
     - Clear price
     - Service description: "22-point inspection, filter replacement, coil cleaning"
     - 4.7-star average rating
     - "Book Now" button

2. **Initiate Booking**
   - Taps "Book Now"
   - App prompts: "Let's add some details about your HVAC system to help us serve you better"

3. **Quick Inventory Add**
   - Simple form:
     - System Type: Central AC / Heat Pump / Other
     - Age: <5 years / 5-10 years / 10-15 years / 15+ years
     - Known Issues: None / Makes noise / Not cooling well / Other
   - "Skip for Now" option (contractor will collect details)
   - Customer provides basic info: "Heat Pump, 8 years old, no issues"

4. **Contractor Selection** (Ad-Hoc Marketplace Model)
   - App shows 3 contractors offering this service in customer's zip code:
     - **ABC Heating** - 4.8 stars, $99, "Recommended"
     - **Smith HVAC** - 4.6 stars, $109
     - **QuickCool** - 4.5 stars, $99
   - Each card shows: Star rating, price, availability (e.g., "Available this week")
   - Customer selects: ABC Heating

5. **Select Date & Time**
   - Calendar shows available windows (3-day buffer for non-emergency)
   - Customer chooses: "Saturday, March 18, 9am-12pm"

6. **Payment Method Selection**
   - **IF Payment Integration Live**:
     - "How would you like to pay?"
     - Options: Apple Pay (default), Credit Card, Pay at Service Completion
     - Customer selects: Apple Pay
     - Prompted for FaceID to confirm $99 payment
   - **IF Payment Integration NOT Live**:
     - "Total cost: $99"
     - "Payment will be collected by ABC Heating at service completion"
     - "Accepted methods: Cash, check, credit card"

7. **Review & Confirm**
   - Summary:
     - Service: HVAC Seasonal Cleaning & Check
     - Contractor: ABC Heating & Cooling
     - Time: Saturday 3/18, 9am-12pm
     - Cost: $99 (paid via Apple Pay) OR (to be collected by contractor)
   - Terms checkbox: "I agree to terms and conditions"
   - "Confirm Booking" button

8. **Confirmation & Payment**
   - **IF Payment Integrated**:
     - Payment processed immediately
     - Receipt generated and emailed
     - "Payment Confirmed: $99" on confirmation screen
   - **IF Not Integrated**:
     - "Booking Confirmed - Payment due at completion"
   - Confirmation number displayed
   - SMS/Email confirmation sent

9. **Pre-Service Communication**
   - Same as Flow 1: Reminders, day-of notification, pizza tracker if available

10. **Service Delivered**
    - Technician performs 22-point inspection
    - Technician adds/updates HVAC inventory in contractor portal:
      - Model: Carrier Heat Pump Model XYZ
      - Serial Number: 123456
      - Photos of equipment
      - Notes: "Coils cleaned, filter replaced with MERV-11, refrigerant levels good, recommend check again in 6 months"
    - Data syncs to customer's home profile

11. **Payment at Completion** (If Not Pre-Paid)
    - Customer pays contractor directly via card reader
    - Contractor marks job complete in their system
    - Triggers completion notification to customer

12. **Post-Service**
    - Push notification: "Service complete! Your HVAC is in great shape."
    - Service added to history with full details and photos
    - New reminder set: "Schedule next HVAC checkup in 6 months"
    - Survey link sent
    - **Upsell Opportunity**: "Want to protect your HVAC year-round? Enroll in Heating & Cooling Protection Plan for $12.99/month"

**Alternate Paths**:
- **Variable Pricing Service** (e.g., ceiling fan installation): At Step 4, contractors show price ranges ($120-$190), customer sees detail page with "Request Quote" button, contractor confirms exact price before scheduling
- **Service Requires Quote**: Some services can't be flat-rate priced, app routes to "Contractor will assess and quote" flow
- **Payment Fails**: If pre-payment fails, customer prompted to try different payment method or pay at completion
- **Customer Refers Friend**: Post-service, "Love the service? Refer a friend and earn $25 credit" prompt

---

### Flow 3: Non-Native Customer - First Time User (Ad-Hoc Only)

**Persona**: Nathan, 41, lives in Florida (non-Duke territory), found app via Google search for "reliable plumber near me", needs toilet replacement

**Pre-Conditions**:
- No prior relationship with Duke Energy
- Downloaded app from app store or web link
- Never used app before

**Steps**:

1. **App Discovery & Download**
   - Google search: "Reliable plumber Tampa"
   - Duke Residential Solutions app appears in results (SEO/paid ads)
   - App Store listing emphasizes: "Transparent pricing, vetted contractors, no subscription required"
   - Downloads app

2. **Guest Browse (Optional)**
   - Opens app, sees home screen with service categories
   - May browse DIY content or service catalog without logging in
   - Taps "Book Service" → prompted to create account

3. **Account Creation**
   - "Create Your Profile"
   - Email address (used as username)
   - Password
   - First/Last Name
   - Home Address (with map pin to confirm)
   - Zip Code (auto-populated from address)
   - Phone Number
   - "Create Account" button
   - No credit card required at signup

4. **Welcome & Onboarding**
   - "Welcome to Duke Home Services!"
   - Optional tutorial: "Here's what we can help you with..."
   - "Tell Us About Your Home" prompt (incentivized):
     - "Build your home profile and earn $10 credit toward first service"
     - Option to "Do This Later" or "Start Now"
   - Nathan skips for now, wants to book service immediately

5. **Service Search**
   - Navigates to "Plumbing" category
   - Browses available services:
     - Toilet Installation/Replacement - $275-$450 (price varies)
     - Leaky Faucet Repair - $125 flat rate
     - Drain Cleaning - $150 flat rate
     - Emergency Plumbing - Call for pricing
   - Selects "Toilet Installation/Replacement"

6. **Service Details**
   - Detail page:
     - Service description: "Professional toilet removal and installation. Price includes labor and basic installation hardware. Toilet fixture purchased separately."
     - Average price range: $275-$450
     - Duration: 2-3 hours
     - "What's Included" and "What's Not Included" sections
   - "Get Quote" button

7. **Provide Service Details**
   - Form to help contractors quote accurately:
     - Current toilet: Standard 2-piece / Modern 1-piece / Other
     - Issue: Replacing old toilet / Cracked fixture / Upgrading
     - New toilet: Already purchased (Y/N)
     - Photos: Option to upload photos of current toilet and space
   - Nathan fills out form, uploads 2 photos

8. **Contractor Matching**
   - App queries zip code 33609 + service type
   - Returns 3 available plumbers:
     - **A+ Plumbing** - 4.9 stars, "Quote: $300" (based on form details), Next available: This week
     - **Tampa Plumbing Pros** - 4.7 stars, "Quote: $325", Next available: Tomorrow
     - **Quick Fix Plumbing** - 4.5 stars, "Quote: $275", Next available: Next week
   - Each contractor card shows reviews snippet: "Professional, on-time, cleaned up after job"

9. **Contractor Selection**
   - Nathan selects Tampa Plumbing Pros ($325, available tomorrow)
   - Detail page shows:
     - Full contractor profile
     - License # and insurance verification badge
     - 20 reviews (most recent displayed)
     - "Book with Tampa Plumbing Pros" button

10. **Scheduling**
    - Calendar shows available windows: Tomorrow, 1pm-4pm OR Next Day, 9am-12pm
    - Nathan chooses: Tomorrow, 1pm-4pm

11. **Payment & Checkout**
    - **IF Payment Integration Live**:
      - "Total: $325"
      - Payment method: Apple Pay / Credit Card / Pay After Service
      - Nathan selects: "Pay After Service" (doesn't want to pre-pay since he hasn't worked with this contractor before)
    - **IF Payment Integration NOT Live**:
      - "Total: $325 - Payment due at completion"
      - "Contractor accepts: Cash, check, credit card"

12. **Terms & Confirmation**
    - Terms checkbox: "I agree to terms of service and contractor policies"
    - "By booking, you agree that work warranty is provided by contractor, not Duke Residential Solutions"
    - "Confirm Booking" button
    - Confirmation screen with reference number
    - Email/SMS confirmation sent

13. **Pre-Service**
    - Email with contractor contact info: "Tampa Plumbing Pros will arrive between 1-4pm tomorrow"
    - Day-of reminder push notification
    - **IF Pizza Tracker Enabled**: Real-time tracking

14. **Service Delivered**
    - Technician arrives, installs toilet
    - Customer pays $325 directly to contractor via card reader (or via app if integrated)
    - Technician marks job complete

15. **Post-Service & Engagement**
    - Push notification: "Service complete!"
    - Prompt: "Add this toilet to your home profile for warranty tracking and maintenance reminders"
    - Nathan adds: Kohler Toilet Model ABC, installed March 2025
    - Survey link sent
    - **Engagement Prompt**: "You've earned $10 credit! Complete your home profile to earn $10 more."
    - **Loyalty Building**: "Love the service? Here's $25 off your next booking"
    - **Future Reminders**: App now sends Nathan general home maintenance tips for first-time users

16. **Long-Term Engagement (Subsequent Visits)**
    - Nathan returns to app for HVAC filter purchase recommendation
    - Browses DIY content on winterizing pipes
    - Eventually books annual HVAC checkup when app sends reminder
    - Over time, Nathan builds full home profile and becomes engaged user
    - **Future Upsell**: "Did you know we also operate in Georgia? Protect your vacation home with our services."

**Alternate Paths**:
- **Service Not Available in Area**: At Step 8, no contractors found → "We're expanding to your area soon! Join waitlist?"
- **Customer Abandons**: If Nathan drops off at any step, retargeting email: "Complete your booking and get $15 off first service"
- **Customer Has Issue**: Post-service, customer can report issue → Duke mediates between customer and contractor (protects brand reputation)

---

### Flow 4: Home Inventory Building (Incentivized)

**Persona**: All customer types, but especially focused on engaged customers who want to unlock rewards and better service

**Triggers**:
- First-time app login (onboarding prompt)
- Before booking first service (suggested)
- Proactive notification: "Complete your home profile and earn rewards!"
- Post-service: "Contractor added your HVAC details - review and earn points"
- Periodic reminders if profile <50% complete

**Steps**:

1. **Entry Point**
   - Customer taps "Home Profile" or "My Home" from navigation
   - Dashboard shows:
     - **Profile Completion Score**: "Your profile is 35% complete"
     - **Loyalty Points Earned**: "120 points ($12 toward services)"
     - **Home Health Score**: "Good" (based on limited data)
   - "Add Appliance or System" button prominently displayed

2. **Add Method Selection**
   - Three options presented:
     - **Scan Barcode**: Use camera to scan appliance label
     - **Manual Entry**: Type in details
     - **Import from Address**: Pre-fill basic home characteristics from public records
   - Customer selects "Scan Barcode"

3. **Barcode Scanning**
   - Camera opens with overlay guide: "Point at appliance label or manual"
   - Scans barcode on HVAC unit
   - App queries product database
   - Returns: "Carrier Heat Pump, Model 25HPA4, 18 SEER, Manufactured 2017"
   - "Is this correct?" confirmation
   - Customer taps "Yes"

4. **Additional Details**
   - Pre-filled form:
     - Category: Heating & Cooling (auto-detected)
     - Type: Heat Pump (auto-detected)
     - Make: Carrier (auto-detected)
     - Model: 25HPA4 (auto-detected)
     - Serial Number: [customer enters]
     - Install Date: 2017 (estimated) - customer can correct
     - Location: Indoor unit location? "Basement / Attic / Garage / Closet"
   - Optional fields:
     - Warranty expiration
     - Purchase price
     - Photos (upload or take photo)
   - "Save to Profile" button

5. **Confirmation & Reward**
   - Success animation: "Heat Pump Added!"
   - **Points Earned**: "+20 points for adding appliance"
   - **Profile Completion Updated**: "Your profile is now 45% complete"
   - **Maintenance Reminders Auto-Generated**:
     - "Change air filter every 3 months"
     - "Schedule seasonal checkup twice per year"
   - Prompt: "Add another appliance or system?"

6. **Bulk Import Option** (For Tech-Savvy Users)
   - "Import Home Details" button
   - Connects to public records API
   - Auto-populates:
     - Square footage: 2,400 sq ft
     - Year built: 1998
     - Property type: Single-family home
     - Bedrooms: 4
     - Bathrooms: 2.5
     - Estimated appliances: "Homes like yours typically have these systems:"
       - Central HVAC
       - Water heater
       - Electrical panel (200 amp)
       - Dishwasher
       - Range/oven
       - Washer/dryer
   - "Add these to your profile?" batch confirmation
   - Customer selects which to add, confirms

7. **Contractor-Enhanced Inventory** (Passive Addition)
   - Scenario: Contractor performs service visit
   - Contractor adds/updates details in contractor portal during visit:
     - Takes photo of water heater label
     - Scans or enters model/serial
     - Adds notes: "Tank water heater, 50 gallon, installed 2015, recommend replacement within 2 years"
   - Data syncs to customer's home profile
   - Customer receives push notification: "Your plumber added details about your water heater to your profile. Review now and earn +10 points."

8. **Review Contractor-Added Data**
   - Customer opens app, sees "New Item to Review" badge
   - Water heater profile page displays:
     - Make/Model/Serial (added by contractor)
     - Photo of water heater (added by contractor)
     - Contractor notes visible
     - "Is this information correct?" prompt
   - Customer confirms: "Yes, looks good"
   - **+10 Points Earned** for reviewing

9. **Gamification Milestones**
   - As customer adds more items, unlocks badges:
     - "First Appliance" badge
     - "Home Basics" badge (5 items)
     - "Home Expert" badge (10+ items)
     - "Complete Profile" badge (100% profile)
   - Milestone rewards:
     - 50% profile complete: $10 credit
     - 80% profile complete: $15 credit
     - 100% profile complete: $25 credit + "Priority Scheduling" perk

10. **Home Health Scorecard Integration**
    - As inventory grows, Home Health Score becomes more accurate
    - Dashboard shows:
      - **Overall Home Health**: 78/100 (Good)
      - **Appliances Needing Attention**: 2
        - Water heater (15 years old - nearing end of life)
        - HVAC filter (overdue for change)
      - **Upcoming Costs**: "Budget $1,500-$2,500 for water heater replacement within 2 years"
      - **Savings Opportunities**: "Your HVAC is 8 years old. Schedule preventative maintenance now to extend life by 3-5 years"
    - Educational tone, not fear-based

11. **Maintenance Reminder Workflow**
    - Based on inventory, app sends timely reminders:
      - "Time to change your HVAC filter" (quarterly)
      - "Schedule your bi-annual HVAC checkup" (spring/fall)
      - "Flush your water heater" (annually)
    - Each reminder includes:
      - DIY instructions: "Watch our 3-minute video on how to change your filter"
      - Service booking option: "Or book a pro to do it for $45"
    - Customer can:
      - Mark as "Done" (earns +5 points)
      - "Do This Later" (snooze for 1 week)
      - "Not Interested" (dismiss permanently)

12. **Exportable Home Report** (Future Use)
    - Customer preparing to sell home
    - Navigates to "Home Profile" → "Export Report"
    - Generates PDF:
      - Full inventory with photos
      - Service history for each appliance
      - Maintenance completed
      - Home Health Score
    - Shareable with real estate agent or buyer
    - "Download" or "Email to Realtor" options

**Success Metrics**:
- **Target**: 80% of active users have 5+ items in profile within 6 months
- **Target**: Average profile completion score >60%
- **Target**: 50% of service visits result in contractor adding/updating inventory data

---

### Flow 5: Contractor Assignment & Scheduling (Behind the Scenes)

**Overview**: This flow describes how the system matches customers to contractors and manages scheduling - the "backend" logic that powers the customer-facing flows above.

**Actors**:
- Customer (via mobile app)
- Duke Home Services System (app backend + APIs)
- Field Service Management (FSM) Tool (future procurement)
- Contractor Portal (existing + future enhancements)
- Duke Enterprise Systems (Commerce/Salesforce, Dynamics, SAP)

**Current State Limitations**:
- Manual contractor assignment via call center
- No real-time availability checking
- Customer must wait for contractor callback to schedule (48-hour window)
- No GPS tracking or automated status updates
- Contractor management via internal SAP-based system (trade + zip code only)

**Future State Vision** (Enabled by FSM Tool):
- Automated contractor matching
- Real-time availability calendars
- Customer selects date/time, contractor auto-accepts or proposes alternatives
- GPS tracking and pizza tracker
- Automated status update triggers

---

#### Sub-Flow 5A: Service Request Intake & Routing

**Steps**:

1. **Customer Initiates Request**
   - Customer completes service booking form in app (Flows 1-3 above)
   - Data captured:
     - Service type (trade: electrical, plumbing, HVAC, appliance, water heater)
     - Symptom/issue description
     - Appliance details (if in inventory or entered)
     - Photos (optional)
     - Customer address (premise ID)
     - Urgency (emergency vs. standard)

2. **Service Validation**
   - **IF HPP Customer**:
     - App queries Commerce/Dynamics API: `GET /customer/{id}/plans`
     - Returns active plans for customer's premise
     - App runs coverage logic:
       - Service type matches plan coverage? (e.g., HVAC issue + Heating & Cooling Plan)
       - Issue type typically covered? (normal wear vs. pre-existing condition)
     - Result: "Likely Covered" or "Not Covered - Ad-Hoc Pricing Applies"
   - **IF Non-HPP Customer**:
     - Skip validation, proceed as ad-hoc

3. **Service Order Creation**
   - App backend creates service order record:
     - Order ID: AUTO-GENERATED
     - Customer ID
     - Premise ID (address)
     - Service Type (trade)
     - Coverage Type (HPP-covered vs. ad-hoc)
     - Issue Description
     - Status: "Pending Contractor Assignment"
   - Order stored in Duke's commerce CRM (Salesforce eCommerce)

4. **Contractor Matching Query**
   - App queries contractor assignment system:
     - **Current State**: SAP-based lookup: `Trade={HVAC} + ZipCode={28202}`
     - **Future State**: FSM API call: `POST /contractor/match` with parameters:
       ```json
       {
         "trade": "HVAC",
         "zipCode": "28202",
         "urgency": "standard",
         "preferredDate": "2025-03-15",
         "customerHistory": "previousContractor_ABC_Heating",
         "serviceType": "covered"
       }
       ```
   - System returns contractor match(es)

---

#### Sub-Flow 5B: Contractor Matching Logic

**Matching Algorithm** (Simplified):

**For HPP-Covered Services** (Warranty Work):
1. **Primary Contractor Assignment**:
   - Lookup: Trade + Zip Code → Primary Contractor
   - Example: HVAC + 28202 → ABC Heating & Cooling (primary)
   - Check: Is primary contractor active and available?
   - **IF YES**: Assign ABC Heating
   - **IF NO**: Proceed to secondary

2. **Secondary Contractor Backup**:
   - Lookup: Trade + Zip Code → Secondary Contractors (list)
   - Example: HVAC + 28202 → [Smith HVAC, Cool Breeze, QuickCool]
   - Rank by:
     - Availability
     - Customer rating (if customer has rated them before)
     - Response time SLA compliance
     - Current workload
   - Assign highest-ranked available secondary

3. **Customer History Check** (Future Enhancement):
   - Query: Has customer worked with contractor before?
   - IF YES and rating >4 stars: Boost that contractor's rank
   - IF YES and customer flagged issue: De-prioritize or exclude

4. **Contractor Relationship Rules**:
   - All warranty work contractors are under contract with Duke
   - Negotiated rates already defined
   - SLA response times defined (e.g., 3 business days for non-emergency)
   - Contractors cannot decline warranty work (except extenuating circumstances)

**For Ad-Hoc Services** (Non-Covered Work):
1. **Contractor Pool Query**:
   - Lookup: Trade + Zip Code + Service Type → All contractors offering that service
   - Example: Plumbing + 33609 + "Toilet Installation" → [A+ Plumbing, Tampa Plumbing Pros, Quick Fix Plumbing, 5 others]

2. **Filtering**:
   - Active contractors only
   - Licensed and insured (verified)
   - Accepting new jobs (availability flag)
   - Serving that specific zip code

3. **Ranking Algorithm**:
   - **Star Rating**: 40% weight (4.5+ stars ranked higher)
   - **Price Competitiveness**: 30% weight (within $50 of average = neutral)
   - **Response Time**: 20% weight (average time to accept job)
   - **Completion Rate**: 10% weight (jobs accepted vs. jobs completed)
   - Result: Top 3-5 contractors shown to customer

4. **Pricing**:
   - **Flat Rate Services**: Price pre-negotiated with Duke, shown upfront
   - **Variable Services**: Contractor submits quote based on customer-provided details
   - **Market Rate Services**: Contractor sets own price, Duke takes commission (future model)

5. **Customer Selection**:
   - Customer sees top 3-5 ranked contractors
   - Can filter/sort by: Price, Rating, Availability
   - Selects preferred contractor
   - Selection sent to chosen contractor for acceptance

---

#### Sub-Flow 5C: Availability & Scheduling

**Current State** (Manual):
- Contractor receives job assignment via email or contractor portal
- Contractor calls customer within 48 hours
- Negotiates date/time over phone
- Contractor manually updates job status in their system

**Future State** (Automated via FSM):

1. **Contractor Availability Calendar**:
   - Each contractor maintains availability calendar in FSM tool
   - Blocks out:
     - Booked appointments
     - Lunch breaks
     - Holidays/PTO
     - Travel time between jobs
   - Defines availability windows per service type:
     - HVAC repair: 2-hour windows (9-11am, 11am-1pm, 1-3pm, 3-5pm)
     - Plumbing: 3-hour windows (9am-12pm, 12-3pm, 3-6pm)
     - Emergency: Same-day or next-day

2. **Real-Time Availability Check**:
   - When customer selects contractor, app queries FSM:
     - `GET /contractor/{id}/availability?date=2025-03-15&duration=2hrs&trade=HVAC`
   - FSM returns available windows:
     ```json
     {
       "availableSlots": [
         {"date": "2025-03-15", "start": "09:00", "end": "11:00"},
         {"date": "2025-03-15", "start": "13:00", "end": "15:00"},
         {"date": "2025-03-16", "start": "09:00", "end": "11:00"}
       ]
     }
     ```
   - Customer selects: March 15, 1-3pm

3. **Appointment Request**:
   - App sends appointment request to FSM:
     - `POST /appointment/create`
     - Payload: Order ID, Customer ID, Contractor ID, Requested Time
   - FSM creates tentative appointment
   - Status: "Pending Contractor Confirmation"

4. **Contractor Acceptance**:
   - **Auto-Accept Scenario** (Warranty Work with SLA):
     - If contractor has availability in FSM and it's within SLA window
     - FSM auto-accepts appointment
     - Contractor receives notification: "New job assigned for March 15, 1-3pm"
     - Customer receives immediate confirmation: "Your appointment is confirmed"

   - **Manual Accept Scenario** (Ad-Hoc or Close to Capacity):
     - Contractor receives push notification in contractor app: "New job request for March 15, 1-3pm - Accept?"
     - Contractor has 2-hour window to respond
     - **IF Accept**: Customer notified immediately
     - **IF Decline or Counter-Offer**: Customer notified with alternative times or routing to next contractor

5. **Appointment Confirmation**:
   - Appointment status updated: "Confirmed"
   - Customer receives:
     - Push notification
     - SMS with appointment details and contractor contact
     - Email confirmation
     - "Add to Calendar" .ics file
   - Contractor receives:
     - Job details (customer address, contact, issue description, appliance details if available)
     - Customer notes (e.g., "Prefer no calls before 10am", "Dog on premises")

---

#### Sub-Flow 5D: Pre-Service & Day-Of Updates

1. **Day Before Appointment**:
   - FSM triggers reminder:
     - **To Customer**: "Reminder: HVAC service tomorrow, 1-3pm with ABC Heating"
     - **To Contractor**: "Tomorrow's appointments: 3 jobs scheduled, first at 9am"
   - Customer can reschedule via app (if >24 hours out):
     - Taps appointment → "Reschedule"
     - Shown new available windows
     - Contractor notified of reschedule request

2. **Morning of Appointment**:
   - Contractor's FSM app shows route for the day:
     - Job 1: 9am - 123 Main St
     - Job 2: 1pm - 456 Oak Ave (Customer's appointment)
     - Job 3: 4pm - 789 Elm St
   - FSM calculates travel time between jobs

3. **Technician En Route** (Pizza Tracker):
   - **IF FSM/GPS Enabled**:
     - Contractor's app tracks GPS location
     - When technician completes previous job, FSM triggers: "Next job: 456 Oak Ave"
     - Customer receives push notification: "Your technician is on the way! ETA: 1:15pm"
     - Customer opens app, sees live map with technician location and ETA
     - Map updates every 30 seconds

   - **IF FSM Not Enabled** (MVP Fallback):
     - Contractor manually texts customer: "On my way, be there in 20 minutes"
     - OR Duke staff manually sends SMS based on contractor check-in

4. **Technician Arrival**:
   - Technician marks "Arrived" in contractor FSM app
   - Customer receives notification: "Your technician has arrived"
   - Service timer starts (for internal SLA tracking)

---

#### Sub-Flow 5E: During Service (Contractor Actions)

1. **Service Diagnosis**:
   - Technician assesses issue
   - Updates job status in FSM app: "Diagnosing"
   - Customer sees status update in app: "Technician is diagnosing the issue"

2. **Inventory Data Collection**:
   - Technician uses contractor portal/app:
     - Takes photos of appliance label
     - Scans barcode or manually enters model/serial number
     - Adds notes: "Compressor issue, covered under warranty"
   - Data submitted to Duke backend
   - Syncs to customer's home profile in customer app

3. **Parts/Additional Work Scenarios**:
   - **Scenario A - Part Needed**:
     - Technician: "Need to order compressor, will take 3-5 business days"
     - Technician updates FSM: Status = "Parts on Order"
     - Customer receives notification: "We need to order a part. We'll be back in 3-5 days to complete repair."
     - Follow-up appointment auto-scheduled when part arrives

   - **Scenario B - Non-Covered Work Found**:
     - Technician: "Your compressor is covered, but your ductwork has leaks (not covered)"
     - Technician creates ad-hoc quote in system: "Duct sealing: $450"
     - Customer receives in-app notification: "Your technician found additional work needed. View quote?"
     - Customer can approve or decline add-on work immediately in app
     - **IF Payment Integrated**: Customer pays for add-on in app
     - **IF Not Integrated**: Customer pays technician directly

4. **Service Completion**:
   - Technician completes repair
   - Updates FSM: Status = "Work Complete"
   - Technician collects customer signature (on contractor's tablet/app)
   - Signature sent to Duke backend

---

#### Sub-Flow 5F: Post-Service & Feedback Loop

1. **Completion Notification**:
   - FSM triggers completion:
     - `POST /order/{id}/complete`
   - Customer app receives webhook:
     - Updates appointment status to "Completed"
     - Sends push notification: "Your HVAC repair is complete!"
   - Service added to customer's service history

2. **Service Record Details**:
   - Customer views service record in app:
     - Date/Time
     - Contractor: ABC Heating & Cooling
     - Technician: John Smith
     - Service performed: Compressor replacement
     - Parts used: Carrier Compressor Model XYZ
     - Warranty: 1-year parts and labor
     - Photos: Before/after photos (if technician added)
     - Contractor notes: "Compressor failed due to age. Replaced. System tested, cooling properly. Recommend annual checkup."
     - Cost: $0 (covered under HPP) OR $450 (ad-hoc)
   - Exportable as PDF

3. **Customer Feedback Survey**:
   - **Current Process**:
     - Email sent by Duke's market research team
     - Link in email to external survey tool (Qualtrics, SurveyMonkey, etc.)
     - Survey includes contractor/technician details pre-populated
   - **MVP**: Continue current process, don't build survey in-app
   - **Future State**: In-app feedback prompt
     - "How was your service?" - 5-star rating
     - Optional comment field
     - "Would you request this contractor again?" Y/N

4. **Contractor Performance Data**:
   - Feedback data sent to Duke contractor management team
   - Updates contractor scorecard:
     - Average rating: 4.8/5 (was 4.7/5)
     - Jobs completed on time: 95%
     - Customer satisfaction: 92%
     - Inventory data completion: 78%
   - Low performers flagged for review
   - High performers eligible for bonuses or more job assignments

5. **Customer Loyalty Points**:
   - Service completion triggers loyalty calculation:
     - +50 points for booking service through app
     - +25 points for completing feedback survey
     - +10 points for reviewing contractor-added inventory data
   - Customer sees updated points balance: "You earned 85 points! ($8.50 credit)"

6. **Automated Maintenance Reminders**:
   - Service completion triggers new reminder schedule:
     - HVAC repair completed → "Schedule next annual checkup in 12 months"
     - Filter replaced → "Change filter again in 3 months"
   - Reminders added to customer's calendar

---

#### Sub-Flow 5G: Exception Handling

**Contractor Unavailable After Assignment**:
1. Contractor marks calendar unavailable or doesn't respond to job request within 2 hours
2. FSM auto-routes to secondary contractor
3. Customer notified: "We're finding you another contractor. You'll receive confirmation shortly."
4. New contractor assigned, repeat scheduling flow

**Customer No-Show**:
1. Contractor arrives, customer not home
2. Contractor marks "Customer Not Available" in FSM
3. Customer charged no-show fee (future policy)
4. Rescheduling required

**Contractor No-Show**:
1. Appointment window passes, contractor hasn't marked "Arrived" or "En Route"
2. System alerts Duke customer service team
3. Duke calls contractor and customer
4. Emergency re-routing to backup contractor if possible
5. Customer receives apology + credit for future service

**Service Dispute**:
1. Customer reports issue post-service: "Work not completed correctly"
2. Customer submits dispute in app: "Report an Issue" button on service record
3. Duke customer service team mediates
4. May dispatch different contractor for re-inspection
5. Resolution tracked in app; customer notified of outcome

**Contractor Cancellation/Reschedule**:
1. Contractor requests reschedule due to emergency (rare)
2. Contractor uses FSM app: "Request Reschedule" with reason
3. Duke approves or denies request
4. IF Approved: Customer notified with new time options
5. Customer can accept new time or choose different contractor

---

#### Key Dependencies for Automated Scheduling

1. **Field Service Management (FSM) Tool Procurement**:
   - Recommended vendors mentioned: ServicePower, Dispatch.me (ServiceChannel not recommended)
   - Features required:
     - Real-time contractor availability calendars
     - GPS tracking for technicians
     - Two-way API integration with customer app
     - Contractor mobile app for job management
     - Automated routing and travel time calculation
     - Customer notification triggers
   - **Timeline Impact**: If FSM not procured by launch, manual scheduling via contractor callbacks required (current process)

2. **Contractor Portal Enhancements**:
   - Contractors must adopt FSM tool/app
   - Training required for contractor technicians
   - Change management: shift from phone calls to app-based job acceptance
   - Incentives for contractors to maintain accurate availability calendars

3. **Duke Enterprise API Development**:
   - Customer validation API (links app profile to Duke/P&G accounts)
   - HPP plan lookup API (returns active plans for premise)
   - Service order creation API (creates order in Commerce/Dynamics)
   - Contractor assignment API (queries SAP-based system initially, FSM later)
   - Premise/property lookup API (validates addresses)
   - **Timeline**: APIs for customer validation and plan lookup are highest priority, must be ready within 2 weeks of vendor kickoff (per RFP background)

4. **Product Catalog & Pricing Management**:
   - Ad-hoc service catalog with flat-rate pricing
   - Dynamic pricing engine for variable services
   - Discount/promotion rules
   - Commission structure for non-warranty work
   - **See Section 5 below for detailed integration needs**

---

## 5. KEY INTEGRATIONS & DEPENDENCIES

### Critical Duke IT Dependencies

#### 5.1 Customer & Premise Validation APIs

**Purpose**: Link app profiles to existing Duke Energy / Piedmont customer accounts and retrieve premise information.

**API Requirements**:
- **Endpoint**: `GET /api/customer/validate`
- **Input Parameters**:
  - Address (street, city, state, zip)
  - Last name
  - Optional: Account number, phone number
- **Response**:
  - Customer match found: Y/N
  - Business Partner ID (Duke's master customer ID)
  - Premise ID(s) - list if customer has multiple properties
  - Utility provider: Duke / Piedmont / None
  - Active utility account: Y/N
- **Edge Cases to Handle**:
  - Multiple customers at same address (roommates, family members)
  - Premise exists but no active utility account (vacant property)
  - Customer has utility account but different name (spouse's name on bill)
  - Validation fails but customer insists they're a Duke customer (manual review queue)

**Timeline**: MUST be available within 2 weeks of vendor kickoff (blocking for MVP)

**Fallback**: If API not ready, allow all users to create profiles without validation. Reconcile accounts post-launch via batch process.

**Quote from Son**: "Duke SME Availability: Business SMEs need 10-15 hours/week for requirements validation... API Integration: Duke IT must provide API documentation and sandbox access within 2 weeks of kickoff." (from RFP background)

---

#### 5.2 Home Protection Plan APIs

**Purpose**: Retrieve customer's active HPP plans, coverage details, enrollment history, and enable plan management actions.

**API Endpoints Needed**:

**A. Get Customer Plans**:
- **Endpoint**: `GET /api/customer/{businessPartnerId}/plans`
- **Response**:
  ```json
  {
    "customerId": "BP123456",
    "premises": [
      {
        "premiseId": "PREM001",
        "address": "123 Main St, Charlotte NC 28202",
        "plans": [
          {
            "planId": "HPP-HOMEWIRE-001",
            "planName": "HomeWire Protection Plan",
            "status": "Active",
            "enrollmentDate": "2020-01-15",
            "renewalDate": "2025-01-15",
            "monthlyCharge": "$9.99",
            "billingMethod": "On Utility Bill",
            "coverageDetails": {
              "coveredItems": ["Electrical wiring", "Outlets", "Switches", "Breaker panel"],
              "exclusions": ["Pre-existing conditions", "Code violations"],
              "deductible": "$0",
              "serviceLimit": "Unlimited repairs"
            }
          },
          {
            "planId": "HPP-HVAC-002",
            "planName": "Heating & Cooling Plan",
            "status": "Active",
            "enrollmentDate": "2022-06-01",
            "renewalDate": "2025-06-01",
            "monthlyCharge": "$12.99",
            "billingMethod": "Credit Card",
            "coverageDetails": {...}
          }
        ]
      }
    ]
  }
  ```

**B. Enroll in New Plan**:
- **Endpoint**: `POST /api/customer/{businessPartnerId}/plans/enroll`
- **Input**:
  - Premise ID
  - Plan ID (from catalog)
  - Billing method: OnBill / CreditCard / ACH
  - Payment details (if not on bill)
  - Terms acceptance timestamp
- **Response**:
  - Enrollment confirmation
  - Effective date
  - First charge date

**C. Cancel Plan**:
- **Endpoint**: `POST /api/customer/{businessPartnerId}/plans/{planId}/cancel`
- **Input**:
  - Cancellation reason (optional)
  - Effective date: Immediate / End of billing cycle
- **Response**:
  - Cancellation confirmation
  - Refund amount (if applicable)
  - Final charge date

**D. Upgrade/Downgrade Plan**:
- **Endpoint**: `PUT /api/customer/{businessPartnerId}/plans/{planId}/modify`
- **Input**:
  - New plan ID
  - Effective date
- **Response**:
  - Modification confirmation
  - Price difference proration

**Timeline**: Customer plan lookup API critical for MVP (must validate coverage for service booking). Enrollment/cancellation APIs high priority but could launch with "Coming Soon" placeholders if delayed.

**Data Source**: Currently in SAP Commerce (Hybris) per Son Gandara. May require new API layer to expose to mobile app.

**Quote from Dana**: "The first set of APIs is customer validation slash premise and home protection plans, what they have. So we have we are developing all of these kind of use cases or permutations of what could happen."

---

#### 5.3 Service Order Management APIs

**Purpose**: Create, update, and track service orders throughout their lifecycle.

**API Endpoints Needed**:

**A. Create Service Order**:
- **Endpoint**: `POST /api/orders/create`
- **Input**:
  ```json
  {
    "customerId": "BP123456",
    "premiseId": "PREM001",
    "serviceType": "HVAC",
    "trade": "Heating & Cooling",
    "coverageType": "HPP-Covered" | "Ad-Hoc",
    "planId": "HPP-HVAC-002" (if covered),
    "issueDescription": "AC making grinding noise",
    "urgency": "Standard" | "Emergency",
    "customerNotes": "Dog on premises, please call before entering backyard",
    "applianceDetails": {
      "make": "Carrier",
      "model": "25HPA4",
      "serialNumber": "12345ABC",
      "age": 8
    },
    "photos": ["base64encodedimage1", "base64encodedimage2"],
    "preferredDates": ["2025-03-15", "2025-03-16"],
    "preferredTimeWindows": ["9-12", "1-4"]
  }
  ```
- **Response**:
  - Order ID
  - Order status: "Pending Assignment"
  - Estimated response time

**B. Get Order Status**:
- **Endpoint**: `GET /api/orders/{orderId}`
- **Response**:
  ```json
  {
    "orderId": "ORD-2025-00123",
    "status": "Assigned" | "Scheduled" | "Dispatched" | "In Progress" | "Parts Needed" | "Completed" | "Cancelled",
    "contractor": {
      "name": "ABC Heating & Cooling",
      "phone": "704-555-1234",
      "rating": 4.8
    },
    "technician": {
      "name": "John Smith",
      "photo": "url"
    },
    "scheduledDate": "2025-03-15",
    "scheduledWindow": "13:00-15:00",
    "estimatedArrival": "13:15" (if GPS enabled),
    "workPerformed": "Replaced compressor",
    "partsUsed": ["Carrier Compressor Model XYZ"],
    "cost": {
      "total": 0,
      "customerPaid": 0,
      "coveredByPlan": true
    },
    "completionDate": "2025-03-15T14:45:00Z"
  }
  ```

**C. Update Order (Reschedule/Cancel)**:
- **Endpoint**: `PUT /api/orders/{orderId}`
- **Input**:
  - Action: Reschedule / Cancel
  - New date/time (if reschedule)
  - Reason (optional)
- **Response**:
  - Updated order details
  - Confirmation

**D. Order History**:
- **Endpoint**: `GET /api/customer/{customerId}/orders/history`
- **Response**:
  - List of all past and current orders for customer
  - Filterable by premise, date range, status

**Timeline**: Service order creation API is MVP-critical (blocking for service booking). Order status/history APIs needed for MVP. Update APIs high priority.

**Data Source**: Duke Commerce CRM (Salesforce eCommerce) per Kevin Oppermann. Currently stores service order lifecycle.

**Quote from Kevin**: "They all exist inside of our commerce CRM system, SSF eCommerce. It goes through the lifecycle of the order's been placed, the order's been assigned, the order's been scheduled, dispatched, completed, etc."

---

#### 5.4 Contractor Assignment & Matching APIs

**Purpose**: Match service requests to appropriate contractors based on trade, location, availability, and business rules.

**Current State**:
- **System**: Internal SAP-based FSM tool
- **Logic**: Trade + Zip Code = Primary Contractor
- **Limitations**: No availability checking, no secondary ranking, manual assignment by call center

**Future State**:
- **System**: Third-party FSM tool (ServicePower, Dispatch.me, or similar)
- **Logic**: Multi-factor matching including availability, ratings, customer history, workload balancing

**API Endpoints Needed**:

**A. Get Contractor for Service**:
- **Endpoint**: `POST /api/contractors/match`
- **Input**:
  ```json
  {
    "serviceType": "HVAC",
    "trade": "Heating & Cooling",
    "zipCode": "28202",
    "urgency": "Standard",
    "coverageType": "HPP-Covered" | "Ad-Hoc",
    "preferredDate": "2025-03-15",
    "customerId": "BP123456" (optional, for history check)
  }
  ```
- **Response** (HPP-Covered):
  ```json
  {
    "primaryContractor": {
      "contractorId": "CON-ABC-001",
      "name": "ABC Heating & Cooling",
      "phone": "704-555-1234",
      "rating": 4.8,
      "reviewCount": 523,
      "serviceArea": "Charlotte Metro",
      "sla": "3 business days",
      "availability": "Available"
    },
    "secondaryContractors": [
      {"contractorId": "CON-SMITH-002", "name": "Smith HVAC", ...},
      {"contractorId": "CON-QUICK-003", "name": "QuickCool", ...}
    ]
  }
  ```
- **Response** (Ad-Hoc):
  ```json
  {
    "contractors": [
      {
        "contractorId": "CON-ABC-001",
        "name": "ABC Heating & Cooling",
        "rating": 4.8,
        "reviewCount": 523,
        "price": "$99" (if flat rate),
        "priceRange": "$200-$350" (if variable),
        "nextAvailable": "2025-03-14",
        "recommended": true
      },
      // 4 more contractors...
    ]
  }
  ```

**B. Get Contractor Availability**:
- **Endpoint**: `GET /api/contractors/{contractorId}/availability`
- **Input Query Params**: `?startDate=2025-03-15&endDate=2025-03-20&duration=2`
- **Response**:
  ```json
  {
    "contractorId": "CON-ABC-001",
    "availableSlots": [
      {"date": "2025-03-15", "start": "09:00", "end": "11:00"},
      {"date": "2025-03-15", "start": "13:00", "end": "15:00"},
      {"date": "2025-03-16", "start": "09:00", "end": "11:00"}
    ]
  }
  ```

**C. Assign Contractor to Order**:
- **Endpoint**: `POST /api/orders/{orderId}/assign`
- **Input**:
  - Contractor ID
  - Scheduled date/time
- **Response**:
  - Assignment confirmation
  - Contractor notified (webhook to contractor portal)

**Timeline**:
- **MVP Launch**: Can function with simplified current-state API (trade + zip code lookup from SAP system)
- **Enhanced Matching**: Requires FSM tool procurement and integration (3-6 months post-launch)

**Quote from Son**: "Right now what exists is trade and zip code. So you will know if I need plumbing and my zip code is 12345, it will be assigned to this person. Some of the additional things that we're talking about, they will be, we will have to build out those additional configurations."

---

#### 5.5 Field Service Management (FSM) Tool

**Purpose**: Contractor scheduling, dispatching, GPS tracking, availability management, and real-time status updates.

**Decision**: Duke Residential Solutions needs to procure third-party FSM tool (does not exist in robust form currently).

**Key FSM Features Required**:
1. **Contractor Calendar Management**: Each contractor maintains availability, blocks out booked time
2. **Job Dispatching**: Automated or semi-automated job assignment to contractors
3. **Mobile Contractor App**: Technicians use app to receive jobs, navigate, update status, collect payments
4. **GPS Tracking**: Real-time technician location for pizza tracker feature
5. **Two-Way Integration**: APIs for customer app to query availability and receive status updates
6. **Customer Communication Triggers**: Auto-send notifications when job status changes
7. **Inventory Management**: Technicians can update home appliance details during visit
8. **Routing Optimization**: Calculate travel time between jobs, optimize daily routes
9. **Reporting & Analytics**: Contractor performance metrics, SLA compliance tracking

**FSM Vendor Options Discussed**:
- **ServicePower**: Mentioned as vendor Duke is evaluating
- **Dispatch.me**: Another option being considered
- **Service Bench**: Kevin is familiar with this one
- **ServiceChannel**: Orases mentioned integration experience, but does NOT recommend (Kevin: "Good to know")

**Integration Approach**:
- FSM tool will have its own API layer
- Duke app backend will integrate with FSM APIs
- Customer app does not directly call FSM (calls Duke backend, which calls FSM)
- Contractor portal may be FSM's native contractor app or custom-built Duke portal that integrates with FSM

**Timeline Impact**:
- **If FSM not procured by MVP launch**:
  - Manual contractor assignment (current call center process)
  - No real-time availability checking
  - No pizza tracker / GPS tracking
  - Limited automated status updates (manual workarounds acceptable)
- **If FSM procured within 6 months post-launch**:
  - Gradual rollout of automated features
  - Contractor onboarding and training period
  - Feature flags to enable pizza tracker, automated matching, etc. as FSM comes online

**Quote from Son**: "A lot of that usually comes from an FSM tool. So ideally any app would be able to, depending on the service or create the service, be able to call APIs to pull in this information that gives you the configuration, the logic to say for this service, for this zip code, it would be this person and they have this kind of three day buffer."

**Quote from Dave McArdle (Orases)**: "We do have a lot of experience of like actually building that, as well as integrating with like other FSM, like service channel or something like that, where you can manage that part."

---

#### 5.6 Product Catalog & Pricing Management

**Purpose**: Maintain ad-hoc service offerings, flat-rate pricing, promotions, and dynamic pricing rules.

**Current State**:
- **HPP Plans**: Stored in SAP Commerce (Hybris) product catalog
- **Ad-Hoc Services**: Do NOT exist in structured catalog form currently
- **Pricing**: Negotiated contractor rates exist for warranty work; ad-hoc pricing being defined
- **Limitations**: Changes to product catalog require Duke Enterprise SAP team involvement (slow, rigid)

**Future State Vision**:
- **App-Managed Product Catalog**: Ad-hoc services managed in admin tool by Duke Residential Solutions team (not Enterprise SAP)
- **Flexibility**: Quick turnaround to add new services, modify pricing, create promotions
- **Territory-Specific Pricing**: Same service may have different price in different zip codes (contractor rate variance)
- **Promotional Pricing**: Limited-time offers, seasonal discounts, first-time customer incentives

**Data Model Needed**:

**Service Catalog Structure**:
```json
{
  "serviceId": "SVC-HVAC-CLEAN-001",
  "serviceName": "HVAC Seasonal Cleaning & Check",
  "serviceCategory": "Preventative Maintenance",
  "trade": "Heating & Cooling",
  "description": "22-point inspection, coil cleaning, filter replacement, refrigerant level check",
  "duration": "1-2 hours",
  "pricingType": "FlatRate" | "Variable" | "QuoteRequired",
  "basePrice": "$99",
  "territoryPricing": [
    {"zipCodeRange": "28200-28299", "price": "$99"},
    {"zipCodeRange": "33600-33699", "price": "$109"}
  ],
  "promotions": [
    {
      "promoId": "PROMO-SPRING-2025",
      "discountAmount": "$10",
      "validFrom": "2025-03-01",
      "validTo": "2025-05-31",
      "eligibility": "All customers"
    }
  ],
  "contractorsOffering": ["CON-ABC-001", "CON-SMITH-002"],
  "availability": "Active" | "Inactive"
}
```

**Admin Tool Features Required** (See Session 2 for full details):
- Service CRUD: Create, read, update, delete ad-hoc services
- Pricing management: Set flat rates, price ranges, territory-specific pricing
- Promotion builder: Create time-limited discounts, customer segment targeting
- Contractor assignment: Define which contractors offer which services
- Content management: Service descriptions, images, DIY instructions
- Analytics: Track which services are most popular, conversion rates

**API Endpoints Needed**:

**A. Get Service Catalog**:
- **Endpoint**: `GET /api/services/catalog`
- **Query Params**: `?zipCode=28202&category=Preventative&trade=HVAC`
- **Response**: List of available services with pricing for that location

**B. Get Service Details**:
- **Endpoint**: `GET /api/services/{serviceId}`
- **Response**: Full service details, pricing, contractors offering, reviews

**C. Admin APIs** (for admin tool):
- `POST /api/admin/services/create` - Create new service
- `PUT /api/admin/services/{serviceId}` - Update service
- `DELETE /api/admin/services/{serviceId}` - Deactivate service
- `POST /api/admin/promotions/create` - Create promotion

**Timeline**:
- **MVP**: Basic service catalog with ~10-20 pre-defined ad-hoc services (preventative maintenance focus)
- **Post-MVP**: Full admin tool with self-service product management (Phase 1 / Month 6-9)

**Quote from Son**: "We don't have a way to maintain that product level today so that's also something that we need to think about is where do we maintain that product level for those services... how can you help facilitate us setting up some of these ad hoc services or products without us having to go back to enterprise SAP?"

**Quote from Son**: "We want that flexibility... turn this offer on and this promotion off and this one on and this one off. We want that flexibility, too."

---

#### 5.7 Payment Integration

**Purpose**: Process payments for ad-hoc services, new HPP enrollments, and recurring plan charges (for customers not on utility bill).

**Payment Use Cases**:
1. **Ad-Hoc Service Pre-Payment**: Customer books $99 HVAC check, pays at checkout
2. **Ad-Hoc Service Post-Payment**: Customer pays after service completion (less common)
3. **New HPP Enrollment**: Customer enrolls in new plan, first month's charge processed immediately
4. **Recurring HPP Charges**: Monthly billing for customers choosing credit card vs. utility bill
5. **Add-On Work During Service**: Technician finds additional non-covered work, customer approves and pays

**Payment Methods**:
- **Apple Pay** (preferred for iOS)
- **Google Pay** (preferred for Android)
- **Credit/Debit Card** (Visa, MC, Amex, Discover)
- **ACH/Bank Account** (for recurring charges only)
- **On Utility Bill** (for Duke/Piedmont customers only, existing process)

**Payment Gateway Options**:
- **Stripe**: Modern, developer-friendly, supports Apple/Google Pay, strong fraud prevention
- **Braintree** (PayPal): Similar to Stripe, good mobile SDK
- **Authorize.net**: Older but reliable, may already be used by Duke
- **SpeedPay**: Mentioned in RFP background for non-native customers (Duke may have existing relationship)

**Integration Requirements**:
- **PCI Compliance**: Payment gateway handles card tokenization, Duke never stores full card numbers
- **Recurring Billing**: Support for subscription management (HPP monthly charges)
- **Refunds**: Ability to issue refunds if service cancelled or issue reported
- **Reporting**: Transaction reports for reconciliation with contractor payouts
- **Fraud Prevention**: Address verification, CVV checking, velocity limits

**API Endpoints** (will vary by gateway, example using Stripe-like model):

**A. Create Payment Intent**:
- **Endpoint**: `POST /api/payments/intent`
- **Input**:
  ```json
  {
    "amount": 9900 (cents),
    "currency": "USD",
    "customerId": "BP123456",
    "orderId": "ORD-2025-00123",
    "paymentMethod": "ApplePay" | "CreditCard"
  }
  ```
- **Response**:
  ```json
  {
    "paymentIntentId": "pi_abc123",
    "clientSecret": "pi_abc123_secret_xyz",
    "status": "requires_payment_method"
  }
  ```

**B. Confirm Payment**:
- **Endpoint**: `POST /api/payments/{paymentIntentId}/confirm`
- **Input**: Payment method token (from Apple Pay or card form)
- **Response**:
  ```json
  {
    "paymentIntentId": "pi_abc123",
    "status": "succeeded",
    "receiptUrl": "https://...",
    "chargeId": "ch_xyz789"
  }
  ```

**C. Create Subscription** (for recurring HPP charges):
- **Endpoint**: `POST /api/subscriptions/create`
- **Input**:
  - Customer ID
  - Plan ID
  - Payment method token
  - Billing frequency: Monthly / Annual
- **Response**: Subscription ID, next charge date

**D. Refund Payment**:
- **Endpoint**: `POST /api/payments/{chargeId}/refund`
- **Input**: Refund amount (full or partial), reason
- **Response**: Refund confirmation, refund ID

**Phased Implementation Plan**:

**Phase 1 (MVP Launch - If Ready)**:
- Ad-hoc service payment at checkout (one-time payments only)
- Apple Pay and Google Pay supported
- Credit card as fallback
- Basic fraud prevention

**Phase 1 (MVP Launch - If NOT Ready)**:
- Display service prices in app
- Customer books service, payment collected by contractor at completion
- App shows: "Pay contractor directly via cash, check, or card"
- Backend invoicing between Duke and contractor

**Phase 2 (3-6 Months Post-Launch)**:
- Recurring billing for HPP enrollments
- Post-service payment option (pay after service, not at booking)
- ACH/bank account payments for lower fees on recurring charges
- Refund workflows

**Phase 3 (6-12 Months Post-Launch)**:
- In-service payment (contractor triggers charge for add-on work via app)
- Split payments (part covered by loyalty points, part charged to card)
- Payment plans for expensive services

**Timeline Dependency**:
- Payment integration is IN SCOPE for Phase 1 but has flexible launch timeline
- If payment APIs not ready at MVP launch, app can still launch with contractor-collected payment model
- Goal is to have payment integration live within 3-4 months of launch maximum

**Quote from Son**: "We have payment integration as part of this. So whether it's ongoing monthly charges or if it's for the ad hoc services. Now, how we prioritize that as part of MVP and the iterations, that will be part of our phases, but that is in scope."

**Quote from Son (on phased approach)**: "If we don't have payment integration right out of the door, but we want to offer these ad hoc services to create some acquisitions and learnings... then we will work with our contractors to collect that payment."

---

#### 5.8 Duke Energy Existing App Convergence

**Purpose**: Seamless experience for Duke/Piedmont customers who use both Duke Energy utility app and new Home Services app.

**Current State**:
- **Duke Energy App**: Existing utility app for bill payment, outage reporting, energy usage tracking (utility-focused)
- **New Home Services App**: Being built by this project (home services, HPP management, contractor booking)
- **Overlap**: Some Duke customers will use both apps

**Convergence Requirements**:

**Visual/Brand Continuity**:
- Consistent color scheme (Duke blues and greens per Dana)
- Similar navigation patterns and UI components
- Recognizable Duke Energy branding elements
- "Powered by Duke Energy" or co-branding

**Data Sharing** (Future State):
- **Single Sign-On (SSO)**: Customer logged into Duke Energy app can seamlessly access Home Services features without re-login
- **Unified Profile**: Customer profile data synced between apps (name, address, contact preferences)
- **Utility Data Sharing**: With customer permission, utility app shares:
  - Energy usage data (for predictive maintenance recommendations)
  - Rebate eligibility info (appliance efficiency programs)
  - Billing history (for adding HPP charges to utility bill)
  - Property details (square footage, service panel amperage, gas/electric heating)

**Navigation Links**:
- Duke Energy utility app could have link: "Manage Home Services" → deep link to Home Services app
- Home Services app could have link: "View My Utility Account" → deep link to utility app
- Cross-promotion banners

**Divergence Strategy** (Separate Apps):
- Two distinct apps in app stores, NOT merged into one
- Reason: Different user bases (all Duke utility customers vs. subset with HPPs + non-native expansion)
- Allows Home Services app to be white-labeled for other utilities in future

**Quote from Son**: "We do have an experience for our Duke customers through our Duke native app, as well as the Duke website. It doesn't include a lot of the functionalities that we're wanting to invest into this app, but there will be a convergence where we need to make sure that if it's a Duke customer, how do we make sure that these two separate apps, that there's some continuity and a seamless kind of experience between them."

**Quote from Dave McArdle (Orases)**: "As we're walking through the workflow, when you can point when you kind of know that there's overlap, the existing functionality already exists, if you can just point that out so that we can flag it and we can look at that and figure out what's the most efficient way we can actually build it forward."

**Timeline**:
- **MVP**: Visual continuity and branding alignment (no technical integration)
- **Phase 2**: Explore SSO and data sharing via Duke IT APIs (6-12 months post-launch)

---

#### 5.9 Utility Rebate & Incentive APIs (Future)

**Purpose**: Automatically check customer eligibility for Duke Energy rebate programs and recommend energy-efficient upgrades.

**Use Cases**:
- Customer's 20-year-old HVAC fails → App suggests: "Replace with 18 SEER unit and receive $1,000 Duke Energy rebate"
- Customer schedules water heater replacement → App checks: "You qualify for $300 rebate for tankless water heater upgrade"
- Customer links utility account → App analyzes energy usage: "Your HVAC is working overtime. Schedule maintenance to improve efficiency."

**Data Needed**:
- Current rebate programs (by territory, equipment type, efficiency ratings)
- Customer eligibility criteria (account status, property type, income level for some programs)
- Appliance efficiency ratings (SEER for HVAC, EF for water heaters, etc.)

**Integration Approach**:
- Duke Energy Rebate API (if exists) OR
- Web scraping + manual updates of rebate catalog OR
- Partner with rebate aggregator service (e.g., Energy Incentives website)

**API Endpoints** (hypothetical):
- `GET /api/rebates/eligible?zipCode=28202&applianceType=HVAC&seer=18`
- Response: List of applicable rebates with amounts, requirements, application links

**Timeline**: Phase 2+ feature (12+ months post-launch). Requires utility side API development or partnership.

**Quote from Kevin**: "Since you're a utility customer, insight into rebates and incentives that they wouldn't necessarily get anywhere else if they went directly to an electrician or a plumber, that we'd be able to tell them, hey, you can get these R&G savings from using our app or rebates."

---

#### 5.10 CPSC Recall Database Integration (Future)

**Purpose**: Automatically check customer's registered appliances against Consumer Product Safety Commission (CPSC) recall database and proactively alert customers.

**Use Cases**:
- Customer adds Samsung dryer to home inventory → App checks CPSC database → "RECALL ALERT: Your dryer model has a fire hazard recall. Schedule free repair."
- Weekly batch job scans all customer inventories for new recalls → Push notifications sent automatically

**Data Source**: CPSC public API (https://www.cpsc.gov/Recalls)

**Integration**:
- Background job queries CPSC API with make/model of appliances in customer inventories
- Matches recalls to customer appliances
- Triggers notification workflow

**Timeline**: Phase 2 feature (post-launch). Low complexity, high customer value.

---

### Summary of Integration Priorities

**CRITICAL for MVP (Blocking)**:
1. Customer validation API (link app profiles to Duke accounts)
2. HPP plan lookup API (show customer's existing plans)
3. Service order creation API (book services)
4. Contractor assignment API (match customers to contractors)

**HIGH Priority for MVP (Workarounds Available)**:
5. Payment integration (can launch with contractor-collected payments if needed)
6. Plan enrollment/cancellation APIs (can launch with "Coming Soon" feature flags)
7. Service order status updates (manual workarounds acceptable initially)

**MEDIUM Priority (Enhanced UX, Not Blocking)**:
8. FSM tool integration (enables pizza tracker, automated scheduling)
9. Product catalog admin tool (for ad-hoc service management)
10. Customer feedback survey integration (currently external process)

**LOW Priority / Future Phases**:
11. Duke Energy app SSO and data sharing
12. Utility rebate APIs
13. CPSC recall database integration
14. Predictive maintenance / energy monitoring

---

## 6. BUSINESS GOALS & SUCCESS METRICS

### Customer Acquisition Targets

**New Customer Acquisition**:
- **Non-Native Customers**: 250,000 within 24 months of launch (per RFP background)
- **New HPP Enrollments**: Duke/Piedmont customers without plans converting to plan holders
- **Ad-Hoc Service Users**: Customers who don't want plans but use app for one-time services

**App Download Goals**:
- **Year 1**: 400,000+ downloads (50% of existing 800K HPP customers + new customers)
- **App Store Rating**: Maintain 4.5+ stars
- **Organic Growth**: Referral program driving 20% of new downloads by Year 2

### Engagement Metrics

**App Usage**:
- **Monthly Active Users (MAU)**: Target 60% of downloads (240K MAU by end of Year 1)
- **Session Frequency**: Average 2-3 sessions per month (maintenance reminders, service bookings)
- **Feature Adoption**:
  - Home inventory: 80% of users have 5+ items within 6 months
  - Service booking: 70% of service requests come through app (vs. phone) by Year 1
  - DIY content engagement: Average 1.5 pages viewed per session

**Customer Satisfaction**:
- **Net Promoter Score (NPS)**: 70+ (RFP target per background)
- **Contractor Communication Satisfaction**: 90% of customers satisfied with updates and transparency (RFP target)
- **Service Booking Time**: <3 minutes average (vs. 15 minutes via phone - RFP target)

**Quote from Son**: "It's critical for us and the success of this app and for us to continue to invest in the app is to get those acquisitions and engagements across this customer segment."

### Retention Goals

**HPP Plan Retention**:
- **Churn Reduction**: Reduce annual HPP cancellation rate by 15% (engaged app users less likely to cancel)
- **Multi-Plan Adoption**: Increase average plans per customer from 1.7 to 2.0 within 18 months

**Repeat Service Booking**:
- **Ad-Hoc Services**: 40% of ad-hoc customers book second service within 12 months
- **Preventative Maintenance**: 60% of customers who book preventative service schedule follow-up within 6 months

**App Stickiness**:
- **90-Day Retention**: 50% of users active 90 days after first service booking
- **Loyalty Program Participation**: 70% of active users enrolled in loyalty/rewards program

### Profile Completion Targets

**Home Inventory Metrics**:
- **Target**: 80% of active users have at least 5 appliances/systems in profile (RFP target - "80% inventory completion")
- **Average Items Per User**: 8-10 items (HVAC, water heater, appliances, electrical panel, plumbing)
- **Contractor-Enhanced Data**: 50% of inventory items added or updated by contractors during service visits

**Gamification Success**:
- **Profile Completion Rates**:
  - 50% completion: 80% of users achieve within 3 months
  - 100% completion: 40% of users achieve within 12 months
- **Loyalty Points Redemption**: 60% of earned points redeemed within 12 months (indicates value perception)

**Quote from RFP Background**: "Improve data collection through app-based home inventory (80% inventory completion goal)."

### Revenue Growth Goals

**Ad-Hoc Service Revenue**:
- **Year 1 Target**: $25M in new ad-hoc service revenue (per RFP background)
- **Average Transaction Size**: $150-$300 per ad-hoc service
- **Services per Customer**: Average 1.5 ad-hoc services booked per year by active users

**HPP Plan Revenue**:
- **New Enrollments**: Add 100,000 new HPP subscriptions within 12 months
- **Average Revenue Per User (ARPU)**: Increase from 1.7 plans per customer to 2.0+ ($25-$40/month combined)
- **Upsell Rate**: 25% of ad-hoc customers convert to HPP plan within 12 months

**Customer Lifetime Value (LTV)**:
- **HPP Customers**: Increase LTV by 20% through reduced churn and multi-plan adoption
- **Ad-Hoc Customers**: Establish baseline LTV in Year 1 for non-plan users

### Operational Efficiency Goals

**Call Center Reduction**:
- **Target**: Reduce inbound service request calls by 40% (per RFP background)
- **Cost Savings**: $X per call avoided (Duke to calculate based on call center staffing costs)
- **Call Deflection Rate**: 70% of app users book services via app, not phone

**Scheduling Efficiency**:
- **Automated Scheduling**: 80% of service appointments scheduled without human coordination (once FSM integrated)
- **First-Time Resolution**: Reduce repeat visits by 15% through better inventory data and customer issue descriptions
- **Contractor Utilization**: Increase contractor job bookings by 20% through better demand visibility

**Quote from RFP Background**: "Reduce call center volume by 40%... Automate scheduling to reduce coordination calls by 80%."

### Data & Insights Goals

**Home Profile Intelligence**:
- **Predictive Maintenance**: By Year 2, app accurately predicts 60% of equipment failures 3-6 months in advance
- **Appliance Age Distribution**: Build database of appliance ages to inform Duke's maintenance and replacement service offerings
- **Regional Trends**: Identify zip codes with aging infrastructure to target marketing for preventative services

**Customer Segmentation**:
- **Behavioral Segments**: Identify "DIY Enthusiasts" vs. "Full-Service Customers" vs. "Emergency-Only Customers"
- **Targeted Offers**: 50% improvement in conversion rates through personalized service recommendations

**Contractor Performance**:
- **Quality Benchmarking**: Rank contractors by customer satisfaction, on-time arrival, inventory data completion
- **Network Optimization**: Identify underserved territories and recruit contractors to fill gaps

### Success Metrics Dashboard (MVP Features)

**Customer App Metrics**:
- Total downloads
- Active users (daily, weekly, monthly)
- Service bookings (HPP-covered vs. ad-hoc)
- Home inventory: Average items per user, % of users with 5+ items
- Loyalty points: Earned vs. redeemed
- App rating and reviews

**Business Metrics**:
- New HPP enrollments via app
- Ad-hoc service revenue
- Average transaction value
- Customer acquisition cost (CAC)
- Customer lifetime value (LTV)

**Operational Metrics**:
- Service request volume (app vs. phone)
- Contractor assignment time (manual vs. automated)
- Average service booking time
- First-time resolution rate
- Customer satisfaction (NPS, survey scores)

**Contractor Metrics**:
- Jobs completed per contractor
- Average contractor rating
- On-time arrival %
- Inventory data contribution rate

---

## 7. OPEN QUESTIONS & RISKS

### Unresolved Items from Meeting

#### Product & Scope Questions

**1. DIY Content Scope & Ownership**:
- **Question**: How extensive should DIY library be at MVP? Static articles vs. AI-powered assistant?
- **Decision Made**: Focus on maintenance reminders with basic DIY instructions, defer extensive library to Phase 2
- **Still Unclear**: Who creates DIY content? Duke internal team vs. contractor contributors vs. third-party content licensing?

**2. Contractor Ratings & Reviews**:
- **Question**: Should customers rate contractors in-app or continue external survey process?
- **Decision Made**: MVP uses external survey process, ratings fed back into app for display
- **Risk**: Delay in feedback loop if external survey process is slow

**3. Multi-Property UI/UX**:
- **Decision Made**: Multi-property support required in MVP
- **Still Unclear**: How do customers switch between properties in app? Property selector on every screen vs. "active property" toggle?

**4. Ad-Hoc Service Catalog Depth**:
- **Question**: How many ad-hoc services at MVP launch? 10? 50? 100?
- **Discussion**: Start with preventative maintenance (HVAC check, appliance tune-ups), expand to common repairs (toilet replacement, leaky faucet)
- **Risk**: Limited catalog = limited revenue potential and customer perception of "not much to offer"

**5. Loyalty Points Economics**:
- **Question**: What's the dollar value of 1 loyalty point? How many points for each action?
- **Discussion**: Points convert to dollar credits (e.g., 100 points = $10)
- **Still Unclear**: Duke needs to model the economics - how much are they willing to "give away" to drive engagement?

**6. Home Health Scorecard Algorithm**:
- **Question**: How is Home Health Score calculated? What triggers "Good" vs. "Fair" vs. "Poor"?
- **Discussion**: Based on appliance ages, maintenance history, known issues
- **Still Unclear**: Exact algorithm and whether it's built in-house or licensed from third-party (e.g., HomeAdvisor, Thumbtack models)

#### Technical & Integration Questions

**7. Customer Validation Edge Cases**:
- **Question**: What happens if customer swears they're a Duke customer but validation fails?
- **Options**: Manual review queue, customer uploads utility bill for verification, allow account creation anyway
- **Risk**: Fraudulent accounts or customer frustration if legitimate customers are blocked

**8. Payment Integration Timeline**:
- **Question**: Will payment gateway be fully integrated at MVP launch?
- **Decision Made**: Flexible - can launch without if needed, contractors collect payment directly
- **Still Unclear**: Target date for payment integration if not ready at launch? 1 month post-launch? 3 months?

**9. FSM Tool Selection & Procurement**:
- **Question**: Which FSM tool will Duke select? When will procurement be finalized?
- **Risk**: FSM is critical for automated scheduling, pizza tracker, contractor management. Delay in procurement = delay in these features.
- **Dependency**: Orases needs FSM API documentation to build integration. Can start with mock APIs but will need to refactor.

**10. Duke Enterprise API SLAs**:
- **Question**: What are Duke IT's commitments for API development timeline and uptime SLAs?
- **RFP Requirement**: API documentation and sandbox within 2 weeks of kickoff
- **Risk**: Duke IT has other priorities; delays in API delivery could block app development
- **Mitigation**: Orases can build with mock APIs initially, but real APIs needed for beta testing

**11. Data Privacy & Consent**:
- **Question**: For Duke/Piedmont customers, can app auto-link their utility account data, or does customer need to explicitly consent?
- **Discussion**: Customer should have choice to link utility account for rebates/incentives but NOT required
- **Still Unclear**: GDPR/CCPA compliance for non-native customers in states with strict privacy laws (California, Virginia, etc.)

**12. Contractor Payment Terms**:
- **Question**: For ad-hoc services, when does Duke pay contractors? Immediately after service completion? Net 30?
- **Impact**: If Duke pays contractors quickly but collects from customers later (or offers payment plans), Duke carries float
- **Still Unclear**: Payment reconciliation process between Duke and contractors

#### Business & Operational Questions

**13. Pilot Launch Strategy**:
- **Question**: Will MVP launch in all Duke/Piedmont territories at once, or phased rollout by region?
- **RFP Background**: Pilot program with ~25 contractors across 3 markets
- **Still Unclear**: Which 3 markets? How long is pilot before full rollout? Criteria for pilot success?

**14. Contractor Onboarding**:
- **Question**: How many contractors need to be onboarded to FSM/contractor portal before MVP launch?
- **Discussion**: At minimum, primary contractors for each trade in pilot markets
- **Risk**: Contractors resistant to adopting new technology, training burden, change management

**15. Customer Support Model**:
- **Question**: Who handles customer support for app issues? Orases during warranty? Duke call center? Separate app support team?
- **Still Unclear**: Escalation process for disputes between customers and contractors

**16. Non-Native Expansion Pace**:
- **Question**: How aggressively will Duke market to non-native customers in Year 1?
- **Discussion**: Non-native is in MVP scope, but marketing spend prioritization unclear
- **Risk**: If non-native growth is slower than expected, ad-hoc service revenue targets at risk

**17. White-Label Timing**:
- **Question**: When will Duke pursue white-label partnerships with other utilities?
- **Discussion**: Architecture must support multi-tenancy from Day 1 (per RFP), but partnerships likely 18-24 months out
- **Impact**: Design decisions now affect white-label feasibility later

#### Compliance & Legal Questions

**18. Service Contract Compliance**:
- **Question**: State-by-state regulations for service contracts vary. Does app need to show different terms by state?
- **Risk**: Compliance violations if terms don't match state requirements (e.g., California requires different cancellation policies)

**19. Contractor Licensing Verification**:
- **Question**: How does Duke verify contractors are licensed and insured? Manual audit vs. API integration with state licensing boards?
- **Risk**: If unlicensed contractor booked via app, Duke liable for issues

**20. Data Retention Policies**:
- **Question**: How long does Duke retain customer service history, photos, contractor notes?
- **Discussion**: Important for home sale use case (customers want years of history) but privacy laws may require data deletion upon account closure

---

### Technical Dependencies & Risks

**High-Risk Dependencies**:

1. **Duke Enterprise APIs (CRITICAL PATH)**:
   - **Risk**: Delays in Duke IT delivering customer validation, plan lookup, and service order APIs
   - **Impact**: App cannot launch without these
   - **Mitigation**: Start with mock APIs, establish weekly checkpoint calls with Duke IT, escalate delays to executive sponsors
   - **Contingency**: If severe delays, launch with limited customer validation (non-native only) and expand to Duke customers later

2. **FSM Tool Procurement (HIGH IMPACT)**:
   - **Risk**: FSM vendor selection delayed or vendor delivers incomplete APIs
   - **Impact**: No automated scheduling, no pizza tracker, manual contractor assignment
   - **Mitigation**: Design app to work with simplified manual processes initially, use feature flags to enable FSM features when ready
   - **Contingency**: Continue call center contractor coordination for 3-6 months post-launch if needed

3. **Payment Gateway Integration (MEDIUM IMPACT)**:
   - **Risk**: Payment provider approval delayed (some require business reviews, compliance checks)
   - **Impact**: Cannot collect payment in-app for ad-hoc services
   - **Mitigation**: Contractor-collected payment model is acceptable fallback
   - **Contingency**: Launch without payment, add in Phase 1B (Month 3-4)

**Medium-Risk Dependencies**:

4. **Contractor Portal Adoption**:
   - **Risk**: Contractors slow to adopt new portal/FSM app, prefer phone calls
   - **Impact**: Manual processes continue, customer experience suffers
   - **Mitigation**: Contractor training program, incentives for portal usage, gradual rollout
   - **Contingency**: Duke staff act as intermediaries during transition period

5. **Product Catalog Definition**:
   - **Risk**: Duke team hasn't finalized ad-hoc service offerings and pricing by development start
   - **Impact**: Cannot build service catalog pages, booking flows incomplete
   - **Mitigation**: Start with 5-10 "no-brainer" services (preventative maintenance), add more iteratively
   - **Quote from RFP Background**: "Product Catalog Definition: Ad-hoc service pricing must be defined by Weeks 8-12"

6. **Content Creation (DIY, Maintenance Guides)**:
   - **Risk**: Duke doesn't have DIY content library ready
   - **Impact**: DIY section of app is empty or thin at launch
   - **Mitigation**: License content from third-party (e.g., HomeAdvisor, Angi), or defer DIY to Phase 1B

**Low-Risk Dependencies**:

7. **Legal Approvals**:
   - **Risk**: Duke legal review of customer-facing terms, privacy policy, contractor agreements takes longer than expected
   - **Impact**: Cannot publish app to app stores without legal approval
   - **Mitigation**: Start legal review early (Week 4-6), provide templates from similar apps
   - **Quote from RFP Background**: "Legal Approvals: Customer communications and privacy notices require Duke legal review"

---

### Timeline Concerns

**Aggressive 44-Week Schedule**:
- **RFP Commitment**: MVP launch in Week 40 (11 months from kickoff)
- **Parallel Workstreams**: Mobile app, APIs, backend systems, contractor portal, admin tools all being developed simultaneously
- **Risk**: Any one dependency delay cascades to launch date

**Critical Path Items** (Must be complete for launch):
1. Duke Enterprise APIs (customer validation, plan lookup, service order creation)
2. Core service booking workflow (mobile app)
3. Contractor assignment logic (even if manual)
4. Home inventory functionality
5. Payment integration (OR contractor-collected payment fallback)
6. Basic ad-hoc service catalog (10-20 services minimum)
7. Legal/compliance approval for terms, privacy policy
8. Contractor onboarding in pilot markets

**Nice-to-Have for Launch** (Can defer if needed):
- FSM integration and pizza tracker
- Full DIY content library
- Loyalty/rewards gamification
- Plan enrollment/cancellation self-service (vs. "call us")
- Extensive ad-hoc service catalog (50+ services)
- Contractor feedback in-app (vs. external survey)

**Quote from Tom (Orases)**: "It's also going to help us define what MVP is so we can get also more concrete around our estimate numbers, timeline, budget."

---

## 8. NEXT STEPS

### Immediate Action Items (Before Session 2)

**Duke Team**:
1. **Product Catalog Prioritization**: Identify top 10-20 ad-hoc services for MVP with draft pricing (flat rate vs. variable)
2. **Duke IT Coordination**: Confirm API development timeline and prioritize customer validation + plan lookup APIs
3. **FSM Vendor Update**: Share current status of FSM tool procurement and estimated selection date
4. **Legal Review Kickoff**: Send draft terms of service and privacy policy to Duke legal team for initial review
5. **Payment Gateway**: Confirm preference (Stripe, Braintree, SpeedPay, other) and initiate vendor account setup
6. **Review Orases Prototype**: Team to review clickable prototype from RFP response and provide feedback

**Orases Team**:
1. **Finalize Customer Flows**: Clean up whiteboard diagrams from session and share with Duke team for review
2. **Technical Architecture**: Begin designing API integration layer and database schema for home inventory
3. **Wireframe Prep**: Start wireframing key screens (onboarding, service booking, home inventory) for Session 4 presentation
4. **Branding Assets**: Request Duke brand guidelines (logo, colors, typography, UI components if available)
5. **FSM Research**: Research API capabilities of ServicePower and Dispatch.me to understand integration options

**Quote from Dave McArdle (Orases)**: "That's what we're trying to capture today. So, again, this isn't full discovery by any stretch. But we're going to use this time wisely and we're going to build out agendas for each session to give us enough information so we can provide valuable information back to you."

### Session 2: Contractor Experience (Next Week)

**Agenda**:
- Contractor personas and workflow
- Contractor portal requirements
- Job acceptance/decline process
- In-field data collection (inventory updates, photos, notes)
- Payment collection (if contractor handles)
- Contractor ratings and performance management
- Training and onboarding requirements

**Expected Outcomes**:
- Contractor portal feature list
- Integration points between contractor systems and customer app
- Contractor engagement and incentive model

**Quote from Dave McArdle**: "I think there's even more opportunity. I'm super excited about the whole principle of incentivizing the customer to provide that data and rewarding them for it. I think in the next session, when we talk about the contractors, we can have really cool ideas about how to make the contractor the data provider for maybe some insights about the customer as well."

### Session 3: Internal Admin & Operations

**Agenda**:
- Admin portal/dashboard requirements
- Service catalog management (ad-hoc services, pricing, promotions)
- Content management (DIY articles, maintenance guides)
- Contractor management and performance monitoring
- Customer support tools and dispute resolution
- Reporting and analytics dashboards
- User roles and permissions

**Expected Outcomes**:
- Admin tool feature specifications
- Backend system architecture
- Operational workflow documentation

**Quote from Son**: "How can you help facilitate us setting up some of these ad hoc services or products without us having to go back to enterprise SAP? We want that flexibility... turn this offer on and this promotion off and this one on and this one off."

### Session 4: Wireframes & Prototype Review

**Agenda**:
- Walkthrough of updated wireframes/prototype
- Screen-by-screen design review
- Interaction patterns and navigation
- Branding application
- Accessibility considerations
- Feedback collection and iteration

**Expected Outcomes**:
- Approved design direction
- UI component library
- Clickable prototype for user testing

### Pre-Development Requirements

**Must Be Defined Before Development Starts** (Week 12 per RFP timeline):

1. **APIs**:
   - Customer validation API spec finalized
   - Plan lookup API spec finalized
   - Service order creation API spec finalized
   - Contractor assignment API spec finalized
   - Sandbox environment available for testing

2. **Product Catalog**:
   - HPP plan details and pricing confirmed
   - Initial ad-hoc service catalog (10-20 services minimum)
   - Pricing finalized (flat rate or ranges)
   - Service descriptions and photos

3. **Business Rules**:
   - Coverage eligibility logic (what's covered under each plan)
   - Cancellation policies (24-hour notice requirement, refunds, etc.)
   - Loyalty points earning and redemption rates
   - Contractor SLAs by trade and territory

4. **Legal**:
   - Terms of service approved
   - Privacy policy approved
   - Contractor agreements finalized (if new agreements needed)
   - State-specific compliance requirements documented

5. **Design**:
   - Wireframes approved
   - Brand guidelines applied
   - Clickable prototype tested with sample users
   - Key user flows validated

6. **Infrastructure**:
   - AWS environment provisioned (dev, staging, prod)
   - Payment gateway account approved and configured
   - Analytics tools selected (Google Analytics, Mixpanel, etc.)
   - Push notification service configured (Firebase, AWS SNS, etc.)

---

## APPENDIX: Participant Quotes & Context

### On Customer Segmentation

**Kevin Oppermann**: "I was thinking three customer types. One being the Duke or Piedmont existing warranty customers that have our service. Another would be Duke Piedmont customers that don't currently have our warranty services, but could use these repairs. And the third is truly non-native. They may or may not know Duke, but it doesn't really matter to them."

**Son Gandara**: "For MVP phase one, we are envisioning our current Duke customers as well as what you consider non-native customers."

### On Business Goals

**Kevin Oppermann**: "Make sure we have an experience for [existing customers] to be able to book these services, navigate and maintain home inventory. We're getting them recall information, things that they'll see as value add... But the second phase of it is really expanding to include ad hoc services that anyone would sign up for... And then you get into where you start expanding to non-native."

**Son Gandara**: "Everything within phase one is really, we are trying to target all the customer segments... It's critical for us and the success of this app and for us to continue to invest in the app is to get those acquisitions and engagements across this customer segment."

### On Home Inventory & Gamification

**Kevin Oppermann**: "You hit what we have talked about internally... building loyalty rewards. You build a profile, depending on the percentage of completion of your profile, we'll give you some loyalty points, which will be credited for future services."

**Dana DeRemigis**: "The more we know about their home, the more we can help them with all these things that just make homeownership really just, oh, I hate this. So there really is a benefit and an added value to all of that."

**Kevin Oppermann**: "Being able to add a reminders list externally from a contractor or W-2 employee... would be valuable and having default reminders. A lot of new homeowners don't know what all they should be doing to maintain their systems, flushing their water heater every year."

### On Transparent Pricing

**Kevin Oppermann**: "Things that show that transparent pricing, I think that's missing from the market today, that we really want to show that transparent pricing up front, and it's a clear statement of work of what can be done inside their home."

### On Payment Integration

**Son Gandara**: "We have payment integration as part of this. So whether it's ongoing monthly charges or if it's for the ad hoc services. How we prioritize that as part of MVP and the iterations, that will be part of our phases, but that is in scope."

**Kevin Oppermann**: "I personally would go with like Apple Pay, Google Pay type of transaction where you can sign up with that. So you don't have to type in credit card information into a third party app."

**Son Gandara**: "If they want it on the bill, if they're Duke P&G customers, we can put it on the bill. They'd rather, even if they're Duke P&G customers, if they want it on credit card, let them put it on the credit card. We want them to make the choice and have the options available to them."

### On Contractor Matching & Scheduling

**Kevin Oppermann**: "For if they're on a warranty plan, we will have our recommended contractor... they can always ask for a new contractor. But we would tell them pretty much, hey, this is your contractor that's going to be out there."

**Son Gandara**: "Right now what exists is trade and zip code. So you will know if I need plumbing and my zip code is 12345, it will be assigned to this person. Some of the additional things that we're talking about, we will have to build out those additional configurations."

### On Pizza Tracker & Real-Time Updates

**Dana DeRemigis**: "Blue sky this, I want to know who's showing up at my door. And when they're showing up... I want pizza tracker all the way through. I want to be able to see that."

**Son Gandara**: "From what we're seeing through the demos, it's really that FSM tool that enables that because the tool itself has a customer integration, customer experience and notifications back."

### On Product Catalog Flexibility

**Son Gandara**: "How can you help facilitate us setting up some of these ad hoc services or products without us having to go back to enterprise SAP? We want to be creative in being able to offer a discount for a limited time or turn this offer on and this promotion off and this one on and this one off. We want that flexibility."

### On Duke App Convergence

**Son Gandara**: "We do have an experience for our Duke customers through our Duke native app, as well as the Duke website. It doesn't include a lot of the functionalities that we're wanting to invest into this app, but there will be a convergence where we need to make sure that if it's a Duke customer, how do we make sure that these two separate apps, that there's some continuity and a seamless kind of experience between them."

### On Dependencies & Constraints

**Son Gandara**: "Everything that we just talked about... we want to convey kind of our constraints and timelines and dependencies that we have so that everyone, not only you, but the other vendor partners, are aware if that impacts timeline, the cost, staffing."

**Son Gandara**: "Some of the APIs that are being built... if we want to acquire new customers to sign up for our home protection plan, those APIs might not be delivered up front. So we can share that kind of information that'll help inform what are the features and functions that we should deliver MVP, and then what's the second round of features."

### Orases Team Observations

**Dave McArdle**: "I think the decision to go and try to pick a field service management software to enhance kind of the data set is something that we didn't know before. But I think that's a great choice if we can find one and like enhance the data, plug that into the app."

**Dave McArdle**: "I'm super excited about the whole principle of kind of incentivizing the customer to provide that data and rewarding them for it. I think in the next session, when we talk about the contractors, we can have really cool ideas about how to make the contractor the data provider for maybe some insights about the customer as well."

**Tom Witt**: "We're going to use these four sessions to look at and capture some information from sort of the different users groups... to answer the ask, which was, what is this going to look and feel like, build out some wireframes... It's also going to help us define what MVP is so we can get more concrete around our estimate numbers, timeline, budget."

---

## Document Control

**Document Title**: Customer App Preliminary Scope and Flows
**Version**: 1.0
**Date**: Based on Session 1 Customer Discovery Meeting
**Prepared By**: Orases Team (compiled from meeting transcript)
**Prepared For**: Duke Energy Residential Solutions
**Purpose**: Inform wireframe development, scope refinement, and timeline/budget estimation
**Next Review**: After Session 2 (Contractor Experience)

**Distribution**:
- Duke Energy Team: Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap
- Orases Team: Tom Witt, Dave McArdle, Devin Gaither, Aksana Rahouski
- Project stakeholders as appropriate

---

**END OF DOCUMENT**
