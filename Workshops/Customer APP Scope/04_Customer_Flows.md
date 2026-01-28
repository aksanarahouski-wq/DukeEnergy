# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

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

