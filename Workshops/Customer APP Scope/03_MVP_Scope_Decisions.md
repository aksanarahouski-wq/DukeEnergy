# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

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
