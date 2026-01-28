# PRD #5: Service Booking - Ad-Hoc Services

**Product Requirements Document**
**Duke Energy Residential Solutions - Home Services Mobile App**

**Version:** 1.0
**Last Updated:** January 2026
**Document Owner:** Orases Product Team
**Stakeholders:** Duke Residential Solutions Product Team, Duke IT, Contractor Network, Finance, Marketing

---

## EXECUTIVE SUMMARY

### What We're Building

A comprehensive ad-hoc service marketplace that enables Duke customers (and non-native customers) to:
- Browse and book home services NOT covered by protection plans
- Compare multiple contractors offering same service
- See transparent, upfront pricing (flat-rate or price range)
- Request quotes for complex variable-price services
- Pay securely via app (pre-payment or contractor-collected)
- Track service status from booking to completion

**Ad-Hoc Services Include:**
- **Preventative Maintenance**: HVAC tune-ups, water heater flushing, electrical safety inspections
- **Installations**: Smart thermostats, water heaters, ceiling fans, EV chargers
- **Repairs**: Appliance repairs, plumbing fixes, electrical work (non-covered)
- **Seasonal Services**: Winterization, spring HVAC prep, generator maintenance
- **Upgrades**: Energy-efficient upgrades, smart home devices, tankless water heaters

### Why It Matters

**For Customers:**
- **Transparency**: Know the price before booking, no surprise charges
- **Convenience**: Book services in <3 minutes (vs. calling multiple contractors)
- **Choice**: See 3-5 contractors per service, compare ratings and prices
- **Peace of Mind**: Vetted Duke-approved contractors, service guarantees
- **No Pressure**: Book when ready, no high-pressure sales calls

**For Duke Business:**
- **Revenue Growth**: $25M in new ad-hoc service revenue within 12 months (per RFP target)
- **Customer Acquisition**: 250,000 non-native customers within 24 months (per RFP target)
- **Market Expansion**: Serve customers WITHOUT utility accounts or protection plans
- **Average Transaction**: $150-$300 per ad-hoc service = $37.5M-$75M GMV (Duke takes 15-20% commission)
- **Customer Lifetime Value**: 25% of ad-hoc customers convert to HPP plans within 12 months = $6M+ additional ARR
- **Competitive Differentiation**: "Uber of home services" experience vs. traditional phone-based booking

**For Contractors:**
- **New Leads**: Access to Duke's 800K+ customer base + growing non-native segment
- **Reduced Acquisition Cost**: Duke provides leads, contractors don't need to advertise
- **Transparent Terms**: Clear commission structure, predictable pricing
- **Simplified Administration**: Duke handles booking, payments, customer support

### Key Features

✅ **Service Catalog** - Browse 10-20 initial services (expand to 50+ over time)
✅ **Service Details** - Description, pricing (flat-rate or price range), duration, what's included
✅ **Contractor Marketplace** - View 3-5 contractors per service, compare ratings, reviews, availability
✅ **Flat-Rate Booking** - Instant booking for fixed-price services (e.g., "$99 HVAC Tune-Up")
✅ **Quote Requests** - Request quotes for variable-price services (e.g., water heater replacement)
✅ **Contractor Selection** - Customer chooses preferred contractor (not auto-assigned)
✅ **Payment Options** - Pre-pay via app (Apple Pay, credit card) OR pay contractor on-site
✅ **Service Tracking** - Order status updates, contractor details, estimated arrival
✅ **Promotional Pricing** - Limited-time offers, seasonal discounts, first-time customer incentives
✅ **Service Bundling** - Book multiple services at once (e.g., HVAC + water heater tune-up)

### Success Metrics

- **Revenue Target**: $25M in ad-hoc service revenue within 12 months
- **Customer Acquisition**: 62,500 ad-hoc customers within Year 1 (average 4 services booked = $25M @ $100 avg)
- **Average Transaction Value**: $150-$300 per service
- **Conversion Rate**: 20% of app users book ad-hoc service within 6 months
- **Repeat Booking**: 40% of customers book second ad-hoc service within 12 months
- **Plan Conversion**: 25% of ad-hoc customers enroll in HPP plan within 12 months
- **Customer Satisfaction**: 85%+ satisfaction with ad-hoc service experience
- **Contractor Satisfaction**: 80%+ contractor satisfaction with lead quality and payment terms

---

## 1. BACKGROUND & PROBLEM STATEMENT

### 1.1 Current State

**How Customers Book Ad-Hoc Home Services Today:**

**Option 1: Call Duke and Ask for Referral**
- Customer calls Duke customer service: "I need my HVAC serviced but don't have a plan"
- Duke provides phone number of preferred contractor (single referral, no choice)
- Customer calls contractor, explains issue, schedules service
- Contractor provides estimate over phone (often vague)
- Customer doesn't know price until contractor arrives
- **Pain Point**: No transparency, no contractor choice, multi-step phone process

**Option 2: Search Online (Google, Yelp, Angie's List)**
- Customer searches: "HVAC repair near me"
- Sees 50+ contractors, doesn't know which to trust
- Calls 3-5 contractors for quotes (15+ minutes per call)
- Compares quotes over phone, tries to remember details
- Books with cheapest or most convenient
- **Pain Point**: Time-consuming (hours to get quotes), no quality assurance, risk of unlicensed contractors

**Option 3: Use Competitor App (Angi, HomeAdvisor, Thumbtack)**
- Customer downloads competitor app, creates account
- Submits service request, waits for contractor responses (hours to days)
- Receives 5-10 contractor calls (many high-pressure sales calls)
- Negotiates pricing, schedules service
- **Pain Point**: Spam calls, inconsistent quality, no Duke relationship/trust

**Option 4: DIY or Delay Service**
- Customer attempts DIY repair (YouTube tutorial)
- Makes problem worse, eventually calls contractor anyway
- OR delays service until problem becomes emergency (higher cost)
- **Pain Point**: Lack of convenient, trustworthy option leads to deferred maintenance

**For Contractors:**
- Spend 30-40% of revenue on lead generation (Google Ads, Angi, HomeAdvisor)
- Lead quality is inconsistent (many tire-kickers, no-shows)
- Customer acquisition cost (CAC) = $50-150 per customer
- Administrative burden: scheduling, payment collection, follow-up

### 1.2 Problems This Deliverable Solves

**Problem 1: No Self-Service Option for Non-Plan Customers**
- **Impact**: Duke leaves $25M+ in annual revenue on table
- **Root Cause**: If customer doesn't have HPP plan, Duke has no way to monetize service requests
- **Data Point**: 60% of service requests are for non-covered services or from non-plan customers
- **Customer Quote**: *"I'm a Duke customer but I don't have a plan. I wish I could book services through Duke instead of searching Yelp."* - Customer survey feedback

**Problem 2: Non-Native Customer Acquisition**
- **Impact**: Can't acquire 250,000 non-native customers without ad-hoc service offering
- **Root Cause**: Non-native customers (no Duke utility account) have zero reason to use Duke app without ad-hoc services
- **Competitive Landscape**: Amazon Home Services, Best Buy, Lowe's all offer ad-hoc services to anyone (not utility-dependent)
- **Quote from Son Gandara**: *"It's critical for us... to get those acquisitions and engagements across this customer segment."*

**Problem 3: Lack of Transparent Pricing Creates Friction**
- **Impact**: Customers delay service due to fear of surprise charges
- **Data Point**: 40% of customers who get initial estimate DON'T proceed due to sticker shock
- **Customer Pain**: "I don't know if $300 for HVAC tune-up is reasonable or a rip-off"
- **Competitive Advantage**: Transparent, upfront pricing builds trust, increases conversion

**Problem 4: Contractor Lead Generation Costs**
- **Impact**: Contractors pay 20-30% commission to Angi, HomeAdvisor for leads
- **Opportunity**: Duke can offer 15-20% commission with better lead quality (vetted Duke customers)
- **Contractor Value Prop**: Access to Duke's 800K+ customer base, higher conversion rates, lower CAC

**Problem 5: Missed Upsell to Protection Plans**
- **Impact**: Customer pays $150 for HVAC service, doesn't realize HVAC plan ($12.99/month) would have covered it
- **Current State**: No mechanism to convert ad-hoc customers to plan holders
- **Conversion Opportunity**: 25% of ad-hoc customers would enroll in plan if prompted at right moment (after paying for service)
- **Revenue Impact**: 62,500 ad-hoc customers x 25% conversion x $12.99/month = $24M ARR in plan revenue

### 1.3 Impact if Not Addressed

**Revenue Loss:**
- **$25M annual revenue target missed**: No ad-hoc service offering = no non-native customer revenue
- **250,000 customer acquisition target missed**: Non-native customers have no reason to use Duke app
- **Plan conversion lost**: Missing $24M+ ARR from ad-hoc-to-plan conversion

**Competitive Risk:**
- **Market share loss**: Customers use Amazon Home Services, Best Buy, Angi instead of Duke
- **Brand erosion**: Duke becomes "utility-only" brand, not "full home services" brand
- **Limited differentiation**: Without ad-hoc services, Duke app is just "plan management app" vs. competitor "home services marketplace"

**Customer Experience:**
- **Fragmented experience**: Duke customers forced to use third-party apps for ad-hoc services
- **Low engagement**: Without ad-hoc services, app usage limited to plan management + emergency calls
- **Missed value**: Customers don't realize Duke can help with non-covered services

---

## 2. GOALS & SUCCESS CRITERIA

### 2.1 Primary Goals

**Goal 1: Achieve $25M in Ad-Hoc Service Revenue (Year 1)**
- **Target**: $25M gross merchandise value (GMV) = total customer spend on ad-hoc services
- **Duke Commission**: 15-20% of GMV = $3.75M-$5M in Duke revenue
- **Success Criteria**:
  - Average transaction value: $150-$300 per service
  - Total transactions: 83,000-167,000 services booked (@ $150-300 avg)
  - Customers booking services: 62,500+ (@ 1.5 services per customer average)

**Goal 2: Acquire 62,500+ Ad-Hoc Service Customers (Year 1)**
- **Target**: Customers who book at least 1 ad-hoc service via app
- **Breakdown**:
  - Native Duke customers (have utility account): 40,000 (64%)
  - Non-native customers (no utility account): 22,500 (36%)
- **Success Criteria**:
  - 20% of app users book ad-hoc service within 6 months
  - Customer acquisition cost (CAC): <$30 per customer
  - Retention: 40% of customers book second service within 12 months

**Goal 3: Convert 25% of Ad-Hoc Customers to HPP Plans**
- **Target**: 15,625 ad-hoc customers enroll in at least 1 HPP plan within 12 months
- **Revenue Impact**: 15,625 x $12 avg/month x 12 months = $2.25M ARR
- **Success Criteria**:
  - Contextual upsell prompts convert at 25%+ rate (post-service enrollment offer)
  - Upsell timing optimized (prompt appears after service completion, when customer sees value)

**Goal 4: Provide Transparent, Competitive Pricing**
- **Target**: 80% of services have upfront pricing (flat-rate or price range)
- **Success Criteria**:
  - Customer satisfaction with pricing transparency: 85%+
  - Price dispute rate: <5% (customer agrees price is what was displayed)
  - Competitive pricing: Duke prices within 10% of market average (per service type)

**Goal 5: Build High-Quality Contractor Network**
- **Target**: 100+ vetted contractors covering Duke service territory
- **Success Criteria**:
  - Contractor satisfaction: 80%+ with lead quality and payment terms
  - Contractor retention: 80% of contractors remain active after 6 months
  - Contractor availability: 90% of service requests matched to contractor within 24 hours

### 2.2 Non-Goals (Explicitly Out of Scope)

❌ **Emergency Services** - Emergency plumbing, electrical, HVAC routed to phone hotline (NOT booked via app)
❌ **Code Violation Services** - Services requiring permits, inspections handled separately
❌ **Commercial / Business Property Services** - Residential customers only for MVP
❌ **Financing / Payment Plans** - Cash/card only for MVP, installment plans Phase 2+
❌ **Service Guarantees / Warranties** - Contractor-provided warranties only (Duke doesn't warranty ad-hoc work)
❌ **DIY Parts Ordering** - Customers can't order parts via app and install themselves
❌ **Contractor Direct Hire** - Customers can't hire contractor for ongoing/retainer work via app
❌ **Multi-Property Service Bundles** - Can't book service across multiple properties in single transaction (MVP)

### 2.3 Success Metrics (Detailed)

**Revenue Metrics:**
- Total GMV (gross merchandise value): $25M+ Year 1
- Duke commission revenue: $3.75M-$5M (15-20% of GMV)
- Average transaction value: $150-$300
- Repeat customer revenue: 40% of customers book 2+ services = $10M+ GMV
- Upsell to HPP plans: 25% conversion = $2.25M ARR

**Customer Acquisition & Engagement:**
- Ad-hoc customers: 62,500+ (Year 1)
- Conversion rate (app user → ad-hoc booking): 20% within 6 months
- Customer acquisition cost (CAC): <$30
- Repeat booking rate: 40% book 2nd service within 12 months
- Services per customer: 1.5 average (Year 1), target 2.5 (Year 3)

**Booking Experience:**
- Time to book flat-rate service: <3 minutes average
- Quote request response time: <24 hours (contractor responds to quote request)
- Booking abandon rate: <20% (start booking, don't complete)
- Service completion rate: 95% (bookings that result in completed service)

**Pricing Transparency:**
- Services with upfront pricing: 80%+
- Customer satisfaction with pricing: 85%+
- Price dispute rate: <5%
- Pricing competitiveness: Within 10% of market average

**Contractor Network:**
- Active contractors: 100+ (Year 1), 250+ (Year 2)
- Contractor satisfaction: 80%+
- Contractor retention: 80% active after 6 months
- Average contractors per service: 3-5 options for customers
- Contractor availability: 90% of requests matched within 24 hours

**Customer Satisfaction:**
- Post-service survey: 85%+ satisfaction
- NPS (Net Promoter Score): 70+
- Service quality rating: 4.5+ stars average (out of 5)
- Contractor communication: 90%+ satisfied (courtesy, professionalism, transparency)

---

## 3. SCOPE DEFINITION

### 3.1 In Scope for Phase 1 (MVP)

#### 3.1.1 Ad-Hoc Service Catalog

**Initial Service Offerings (10-20 Services):**

**Category 1: HVAC Services**
- HVAC Seasonal Tune-Up (flat-rate: $99)
- AC Repair Diagnostic (flat-rate: $79)
- Furnace Repair Diagnostic (flat-rate: $79)
- Air Duct Cleaning (price range: $300-$600 depending on home size)
- Thermostat Installation (flat-rate: $125)

**Category 2: Electrical Services**
- Electrical Safety Inspection (flat-rate: $149)
- Ceiling Fan Installation (flat-rate: $175)
- Light Fixture Installation (flat-rate: $125)
- EV Charger Installation (quote required - varies by electrical panel capacity)
- Electrical Outlet Repair (flat-rate: $89)

**Category 3: Plumbing Services**
- Water Heater Flushing (flat-rate: $99)
- Drain Cleaning (flat-rate: $149)
- Faucet Installation (flat-rate: $150)
- Toilet Repair (flat-rate: $125)
- Water Heater Replacement (quote required - varies by tank size, gas/electric)

**Category 4: Appliance Services**
- Refrigerator Repair Diagnostic (flat-rate: $89)
- Dishwasher Repair Diagnostic (flat-rate: $89)
- Washing Machine Repair Diagnostic (flat-rate: $89)
- Dryer Vent Cleaning (flat-rate: $99)

**Service Attributes:**
- Service name and description
- Category (HVAC, Electrical, Plumbing, Appliance)
- Trade (for contractor matching)
- Pricing model:
  - **Flat-Rate**: Fixed price (e.g., "$99 HVAC Tune-Up")
  - **Price Range**: Estimated range (e.g., "$300-$600 depending on home size")
  - **Quote Required**: Customer submits request, contractor provides quote (e.g., "Water Heater Replacement")
- Service duration (e.g., "1-2 hours")
- What's included (bullet list)
- What's NOT included (exclusions)
- Contractors offering service (3-5 contractors)
- Customer reviews and ratings

**Service Catalog Browsing:**
- Browse all services (grid or list view)
- Filter by category (HVAC, Electrical, Plumbing, Appliances)
- Filter by price range (<$100, $100-$200, $200-$500, $500+)
- Sort by: Popularity, Price (low to high), Customer Rating
- Search by keyword (e.g., "HVAC", "water heater", "ceiling fan")

#### 3.1.2 Service Detail Pages

**Service Overview:**
- Service name and hero image
- Pricing (flat-rate, price range, or "Get Quote")
- Average rating (4.8 stars) and review count (523 reviews)
- Service duration (e.g., "Typically takes 1-2 hours")
- "Book Now" or "Request Quote" CTA button

**What's Included:**
- Detailed description of service (e.g., "22-point HVAC inspection, coil cleaning, filter replacement, refrigerant level check")
- Bullet list of included items
- What customer should prepare (e.g., "Clear access to HVAC unit, ensure pets secured")

**What's NOT Included (Exclusions):**
- Additional parts or materials (e.g., "Refrigerant refill not included, charged separately if needed")
- Services outside scope (e.g., "Duct replacement not included, quote available")

**Contractors Offering This Service:**
- Display 3-5 contractors with:
  - Contractor name, logo, rating (4.8 stars), review count (523)
  - Pricing (if different from base price): "From $99" or "Custom quote"
  - Next available date: "Available Thursday, Feb 15"
  - "View Profile" and "Select Contractor" buttons

**Customer Reviews:**
- Display 5 most recent reviews (5-star rating, review text, customer name, date)
- Filter reviews: All Reviews, 5-Star, 4-Star, etc.
- Link to "See All Reviews" (paginated list)

**Frequently Asked Questions:**
- Common questions about service (e.g., "How often should I get HVAC tune-up?")
- Collapsible FAQ accordion

#### 3.1.3 Flat-Rate Service Booking Workflow

**Step 1: Select Service**
- Customer taps "Book Now" from service detail page
- System confirms flat-rate pricing (no quote needed)

**Step 2: Select Property**
- If customer has multiple properties, select which property needs service
- Display property address for confirmation
- Option to add new property if not listed (address entry + validation)

**Step 3: Select Contractor**
- Display 3-5 contractors offering this service
- For each contractor, show:
  - Name, logo, rating, review count
  - Next available date/time slots
  - Pricing (same flat-rate for all, or contractor-specific pricing if applicable)
  - "Select Contractor" button
- Customer taps "Select Contractor" for preferred contractor

**Step 4: Schedule Service**
- Display contractor's availability calendar (next 14 days)
- Customer selects preferred date
- Customer selects time window:
  - Morning (8am-12pm)
  - Afternoon (12pm-4pm)
  - Evening (4pm-8pm)
- Alternatively, customer selects specific time slot if contractor offers (e.g., "10:00 AM - 12:00 PM")

**Step 5: Provide Service Details**
- Customer describes issue or provides context (text field, optional)
  - Example: "AC making grinding noise when starting up"
- Customer uploads photos (optional, up to 5 photos)
- Customer provides special instructions:
  - Pets on premises? Yes/No
  - Access instructions (e.g., "Ring doorbell, don't knock, dog barks")
  - Parking instructions (e.g., "Park in driveway")

**Step 6: Choose Payment Method**
- **Option 1: Pre-Pay via App** (Recommended)
  - "Pay $99 now via Apple Pay, Google Pay, or credit card"
  - Benefits: Priority scheduling, faster service confirmation
  - Payment processed immediately
- **Option 2: Pay Contractor On-Site**
  - "Pay contractor after service via cash, check, or card"
  - Disclaimer: "Final price may vary if additional work needed"
- Customer selects payment option

**Step 7: Review and Confirm**
- Display booking summary:
  - Service: HVAC Seasonal Tune-Up
  - Property: 123 Main St, Charlotte NC 28202
  - Contractor: ABC Heating & Cooling (4.8 stars)
  - Date: Thursday, February 15, 2026
  - Time: Morning (8am-12pm)
  - Price: $99 (pre-paid) or "Pay on-site"
  - Total: $99 (or "$99 estimated" if pay on-site)
- Customer checks terms acceptance:
  - ☑ "I agree to the Service Terms and Conditions"
  - ☑ "I understand pricing may change if additional work is needed"
- Customer taps "Confirm Booking"

**Step 8: Booking Confirmation**
- Success message: "Your service is booked!"
- Display booking details:
  - Confirmation number: #BK-2026-012345
  - Service date and time
  - Contractor name and phone number
  - "Add to Calendar" option
- Email confirmation sent to customer
- Push notification: "Service booked! ABC Heating will arrive Thu Feb 15, 8am-12pm"
- **End Flow**: Customer returns to app home or views "My Services"

#### 3.1.4 Quote Request Workflow (Variable-Price Services)

**Step 1: Select Service**
- Customer taps "Request Quote" from service detail page
- System confirms this is quote-required service (not flat-rate)

**Step 2: Select Property**
- Same as flat-rate workflow (Step 2)

**Step 3: Provide Service Details**
- Customer describes what they need (text field, required)
  - Example: "Replace 50-gallon gas water heater, currently 10 years old"
- Customer uploads photos (optional, up to 5 photos)
  - Example: Photo of current water heater, model number plate
- Customer answers service-specific questions (if applicable):
  - Water Heater Replacement: "Gas or Electric?" "Tank size?" "Age of current unit?"
  - EV Charger Installation: "Do you have 240V outlet near parking area?" "Electrical panel capacity?"

**Step 4: Select Contractors to Request Quote**
- Display 3-5 contractors offering this service
- Customer can select multiple contractors (1-5) to receive quote request
- Recommended: "Select 3 contractors for best pricing comparison"
- Customer taps "Request Quotes from [X] Contractors"

**Step 5: Quote Request Confirmation**
- Success message: "Quote request sent!"
- Display details:
  - Confirmation number: #QR-2026-012345
  - Contractors receiving request: ABC Plumbing, Smith Plumbing, QuickFix Plumbing
  - Expected response time: "Contractors typically respond within 24 hours"
- Email confirmation sent to customer
- Push notification: "3 contractors will send quotes within 24 hours"
- **End Flow**: Customer waits for contractor responses

**Step 6: Receive and Compare Quotes**
- Contractor responds with quote via contractor portal (Duke admin tool)
- Customer receives push notification: "You have a new quote from ABC Plumbing"
- Customer navigates to "My Quote Requests" section
- System displays quote comparison:
  - Contractor 1: $1,200 (4.8 stars, "Includes 50-gal Bradford White tank, labor, disposal of old unit")
  - Contractor 2: $1,350 (4.6 stars, "Includes 50-gal Rheem tank, labor, 6-year warranty")
  - Contractor 3: $1,150 (4.9 stars, "Includes 50-gal generic tank, labor")
- Customer reviews quotes, reads contractor notes, checks ratings

**Step 7: Accept Quote and Book Service**
- Customer taps "Accept Quote" for preferred contractor
- System displays booking confirmation:
  - Contractor: ABC Plumbing
  - Quote amount: $1,200
  - Next steps: "ABC Plumbing will contact you to schedule service"
- Contractor receives notification: "Customer accepted your quote"
- Contractor contacts customer to schedule service (phone call or in-app message)
- **End Flow**: Service scheduled, customer receives confirmation

**Step 8: Decline Quotes**
- Customer can decline quotes: "Not interested" or "Too expensive"
- Feedback optional: "Why are you declining?" (Price too high, Changed mind, Found another contractor)
- Contractors notified: "Customer declined your quote"

#### 3.1.5 Contractor Profiles

**Contractor Profile Page:**
- Contractor name, logo, hero image (truck, office, team photo)
- Rating and review count (4.8 stars, 523 reviews)
- Services offered (list of ad-hoc services this contractor provides)
- Service area (zip codes covered)
- Years in business, licensing/certifications
- "About Us" description (contractor bio, specialties)
- Contact information (phone number, email - displayed AFTER booking)
- "Book a Service" CTA button

**Contractor Reviews:**
- List of customer reviews (5-star rating, review text, customer name, date)
- Filter by service type: "All Services", "HVAC", "Plumbing", etc.
- Sort by: Most Recent, Highest Rated, Lowest Rated
- Pagination: 10 reviews per page

**Contractor Availability:**
- Next available date: "Available Thursday, Feb 15"
- Calendar view (if contractor provides availability data via FSM integration)

#### 3.1.6 Promotional Pricing & Offers

**Limited-Time Offers:**
- Service detail page displays promotional pricing:
  - Original price: $99 (crossed out)
  - Sale price: $89
  - Savings: "Save $10"
  - Offer expiration: "Offer ends Feb 28"
- Promotional badge: "Limited Time Offer" or "Seasonal Special"

**First-Time Customer Discounts:**
- Customer's first ad-hoc booking receives discount:
  - "$10 off your first service"
  - Applied automatically at checkout
- Display in booking summary: "First-time discount: -$10"

**Seasonal Promotions:**
- Spring HVAC tune-up special: "$20 off HVAC tune-ups in March-April"
- Winter furnace check: "$15 off furnace diagnostic in Oct-Dec"

**Service Bundling Discounts:**
- Customer books multiple services at once (e.g., HVAC tune-up + water heater flushing)
- Discount applied: "Bundle & Save: Book 2+ services, save 10%"
- Display in booking summary: "Bundle discount: -$20"

#### 3.1.7 Payment Processing

**Pre-Payment via App (Option 1):**
- Customer selects "Pre-Pay" during booking workflow (Step 6)
- Payment methods:
  - Apple Pay (preferred for iOS)
  - Google Pay (preferred for Android)
  - Credit/debit card (Visa, MC, Amex, Discover)
- Payment processed immediately upon booking confirmation
- Receipt emailed to customer within 5 minutes
- Contractor notified: "Customer pre-paid $99, service confirmed"

**Pay Contractor On-Site (Option 2):**
- Customer selects "Pay on-site" during booking workflow (Step 6)
- Booking confirmed, but no payment processed via app
- Contractor collects payment after service completion:
  - Cash, check, or contractor's card reader
- Customer receives invoice from contractor (not via app)
- Disclaimer displayed: "Final price may vary if additional work needed"

**Refund Policy:**
- Customer can cancel service up to 24 hours before scheduled time (full refund)
- Cancellation within 24 hours: 50% refund (restocking fee)
- No-show / same-day cancellation: No refund
- Service quality issues: Customer can request refund via customer support (case-by-case basis)

**Payment to Contractors:**
- Duke collects payment (if pre-paid via app)
- Duke pays contractor: Contractor's service fee minus Duke commission (15-20%)
  - Example: Customer pays $99, Duke keeps $15-20, contractor receives $79-84
- Payment cycle: Weekly or bi-weekly (per contractor agreement)
- Contractor invoicing handled via admin portal

#### 3.1.8 Service Tracking & Updates

**My Services Dashboard:**
- List of all booked services (upcoming, in-progress, completed)
- Service cards display:
  - Service name and icon
  - Property address
  - Contractor name and logo
  - Date and time
  - Status: Confirmed, Scheduled, En Route, In Progress, Completed, Cancelled
- Filter services: All, Upcoming, Completed, Cancelled
- CTA buttons: "View Details", "Reschedule", "Cancel"

**Service Detail Page (Order Status):**
- Display full booking details:
  - Service name, property address, contractor details
  - Date and time, time window (8am-12pm)
  - Status indicator with progress bar:
    - Confirmed → Scheduled → En Route → In Progress → Completed
  - Contractor contact info (phone number - available AFTER booking)
  - Special instructions provided by customer
  - Estimated arrival time (if GPS tracking enabled via FSM tool)

**Status Update Notifications:**
- Push notifications for status changes:
  - "Service confirmed! ABC Heating will arrive Thu Feb 15, 8am-12pm"
  - "Your contractor is on the way! Estimated arrival: 8:45 AM"
  - "Your contractor has arrived and is starting work"
  - "Your service is complete! Please rate your experience."
- Email notifications for major status changes (confirmed, completed, cancelled)

**Reschedule Service:**
- Customer navigates to service detail → "Reschedule" button
- Display contractor's availability calendar (next 14 days)
- Customer selects new date and time
- Confirmation: "Service rescheduled to [new date and time]"
- Contractor notified of reschedule request

**Cancel Service:**
- Customer navigates to service detail → "Cancel Service" button
- Confirmation prompt: "Are you sure you want to cancel?"
- Cancellation policy displayed: "Cancel 24+ hours before = full refund, cancel <24 hours = 50% refund"
- Customer confirms cancellation
- Refund processed (if applicable)
- Contractor notified of cancellation

#### 3.1.9 Post-Service Experience

**Service Completion Notification:**
- Contractor marks service complete via contractor portal
- Customer receives push notification: "Your HVAC Tune-Up is complete!"
- Email summary sent with:
  - Service performed
  - Work performed details (contractor notes)
  - Total cost (if pay-on-site)
  - Receipt (if pre-paid)
  - Invoice (if additional work performed beyond original scope)

**Rate Your Experience:**
- Customer prompted to rate service (1-5 stars)
- Rating dimensions:
  - Overall satisfaction (1-5 stars)
  - Contractor professionalism (1-5 stars)
  - Quality of work (1-5 stars)
  - Timeliness (1-5 stars)
  - Value for money (1-5 stars)
- Written review (optional, 500 character max)
- Photo upload (optional, upload photos of completed work)

**Upsell to Protection Plans (Post-Service):**
- If service was HVAC-related and customer doesn't have HVAC plan:
  - Prompt: "You just paid $99 for HVAC service. An HVAC Protection Plan ($12.99/month) would have covered this repair."
  - Savings calculation: "$99 service vs. $12.99/month plan = break-even after 8 months"
  - CTA: "Enroll in HVAC Plan" or "Not Now"
- Contextual upsell timing: Display 24 hours after service completion (not immediately, avoid annoyance)

**Repeat Service Booking:**
- Customer prompted to book next service:
  - "HVAC tune-ups recommended twice per year. Book your fall tune-up now!"
  - Pre-fill booking with same contractor, same property
  - CTA: "Book Again" (streamlined re-booking workflow)

### 3.2 Out of Scope for Phase 1 (Deferred to Later Phases)

❌ **Financing / Payment Plans** - Installment payments for expensive services (e.g., $2K HVAC replacement)
❌ **Service Guarantees / Extended Warranties** - Duke-backed service guarantees (contractor warranties only)
❌ **In-App Messaging** - Real-time chat between customer and contractor (phone/email only for MVP)
❌ **Real-Time GPS Tracking** - "Pizza tracker" for contractor arrival (requires FSM tool integration)
❌ **Contractor Bidding** - Contractors compete via lowest bid (fixed pricing or quote-based only)
❌ **Multi-Property Service Bundles** - Book same service across multiple properties in single transaction
❌ **Subscription Services** - Recurring monthly services (e.g., monthly lawn care) - one-time bookings only
❌ **DIY Parts Ordering** - Customer orders parts, installs themselves (professional services only)
❌ **Emergency Service Booking** - Emergencies routed to phone hotline (not app-bookable)
❌ **Post-Service Add-On Work** - Contractor recommends additional work during visit, customer books via app (Phase 2)

---

## 4. FUNCTIONAL REQUIREMENTS

### 4.1 Service Catalog Management

**FR-1: Display Ad-Hoc Service Catalog**
- **Requirement**: System shall retrieve and display all available ad-hoc services for customer's service territory
- **Data Source**: Duke Product Catalog API (`GET /api/services/catalog?zipCode=28202`)
- **Display Requirements**:
  - Show service name, icon, pricing (flat-rate or price range), rating, review count
  - Group services by category (HVAC, Electrical, Plumbing, Appliances)
  - Display promotional badges ("Limited Time Offer", "Seasonal Special", "Most Popular")
- **Filtering & Sorting**:
  - Filter by category, price range
  - Sort by popularity (default), price, customer rating
  - Search by keyword (service name, description)
- **Performance**: Load catalog within 2 seconds, cache for 24 hours

**FR-2: Display Service Detail Page**
- **Requirement**: System shall display comprehensive service details for selected service
- **Details Include**:
  - Service name, description, hero image
  - Pricing (flat-rate, price range, or "Get Quote")
  - Average rating and review count
  - Service duration estimate
  - What's included (bullet list)
  - What's NOT included (exclusions)
  - Contractors offering service (3-5 contractors with ratings, availability)
  - Customer reviews (5 most recent)
  - FAQs (collapsible accordion)
- **CTA Buttons**: "Book Now" (flat-rate) or "Request Quote" (variable-price)

**FR-3: Pricing Logic**
- **Requirement**: System shall display appropriate pricing based on service pricing model
- **Pricing Models**:
  - **Flat-Rate**: Display single fixed price (e.g., "$99")
  - **Price Range**: Display estimated range (e.g., "$300-$600 depending on home size")
  - **Quote Required**: Display "Get Custom Quote" (no pricing shown)
- **Promotional Pricing**: If promotion active, display original price (crossed out) + sale price + savings
- **Territory-Based Pricing**: If pricing varies by territory, display price for customer's zip code

**FR-4: Contractor Availability Display**
- **Requirement**: System shall display contractor availability for each service
- **Data Source**: Contractor availability API (if FSM tool integrated) OR static "typically available within X days"
- **Display**: "Next available: Thursday, Feb 15" OR "Typically available within 3-5 business days"
- **Fallback**: If availability data unavailable, display generic message: "Contact contractor for availability"

### 4.2 Flat-Rate Booking Workflow

**FR-5: Flat-Rate Booking Steps**
- **Requirement**: System shall guide customer through multi-step flat-rate booking workflow
- **Steps**:
  1. Select service (from catalog or detail page)
  2. Select property (if multiple properties)
  3. Select contractor (compare 3-5 contractors)
  4. Schedule service (date + time window)
  5. Provide service details (issue description, photos, special instructions)
  6. Choose payment method (pre-pay or pay on-site)
  7. Review and confirm (summary, terms acceptance)
  8. Booking confirmation (confirmation number, email sent)
- **Progress Indicator**: Show "Step 3 of 8" or progress bar
- **Save for Later**: Allow customer to exit and resume booking within 24 hours

**FR-6: Property Selection**
- **Requirement**: System shall allow customer to select which property needs service
- **Validation**:
  - Property must be linked to customer account (premise ID exists)
  - Property must be within contractor's service area (zip code validation)
- **Add New Property**: If property not listed, allow customer to add new address (address validation via Duke premise API)

**FR-7: Contractor Selection**
- **Requirement**: System shall display 3-5 contractors offering selected service
- **Contractor Data Displayed**:
  - Name, logo, rating (4.8 stars), review count (523)
  - Pricing (same flat-rate or contractor-specific if applicable)
  - Next available date
  - "View Profile" and "Select Contractor" buttons
- **Sorting**: Default sort by rating (highest first), customer can re-sort by price or availability
- **No Contractor Available**: If no contractors offer service in customer's area, display: "This service is not available in your area. Contact customer support for options."

**FR-8: Scheduling Service**
- **Requirement**: System shall allow customer to select date and time for service
- **Date Selection**:
  - Display contractor's availability calendar (next 14 days)
  - Disable unavailable dates (greyed out)
  - Customer selects preferred date
- **Time Selection**:
  - Display time windows: Morning (8am-12pm), Afternoon (12pm-4pm), Evening (4pm-8pm)
  - OR specific time slots if contractor provides (e.g., "10:00 AM - 12:00 PM", "2:00 PM - 4:00 PM")
  - Disable unavailable time slots
- **Fallback**: If contractor availability data unavailable, allow customer to request "Contact me to schedule" (contractor calls customer to arrange)

**FR-9: Service Details Input**
- **Requirement**: System shall allow customer to provide issue description and special instructions
- **Issue Description** (optional):
  - Text field, 500 character max
  - Placeholder: "Describe the issue or what you need (optional)"
  - Example: "AC making grinding noise when starting up"
- **Photo Upload** (optional):
  - Allow up to 5 photos (max 5MB each)
  - Camera or gallery upload
  - Display thumbnails, allow delete
- **Special Instructions**:
  - Pets on premises: Yes/No
  - Access instructions: Text field (e.g., "Ring doorbell, don't knock")
  - Parking instructions: Text field (e.g., "Park in driveway")

**FR-10: Payment Method Selection**
- **Requirement**: System shall allow customer to choose payment method
- **Options**:
  - **Pre-Pay via App**: Apple Pay, Google Pay, credit card (display as preferred)
  - **Pay Contractor On-Site**: Cash, check, or contractor's card reader (display disclaimer)
- **Disclaimers**:
  - Pre-Pay: "Priority scheduling, faster confirmation"
  - Pay On-Site: "Final price may vary if additional work needed"
- **Payment Processing** (if pre-pay selected):
  - If Apple Pay / Google Pay: Initiate native payment flow
  - If credit card: Display card entry form (card number, expiration, CVV, billing zip) OR select saved card
  - Process payment immediately upon booking confirmation
  - If payment fails: Display error, allow retry with different method

**FR-11: Booking Confirmation**
- **Requirement**: System shall create booking record and send confirmation to customer
- **API Call**: Duke Service Order API (`POST /api/orders/create`)
- **Request Payload**: Customer ID, Service ID, Contractor ID, Property ID, Date/Time, Payment Method, Total Amount
- **Response Handling**:
  - **Success**: Display confirmation message, send confirmation email, send push notification
  - **Failure**: Display error message, queue for manual processing if repeated failures
- **Email Confirmation**: Send within 5 minutes, include booking details, contractor contact info, add-to-calendar link
- **Push Notification**: "Service booked! [Contractor Name] will arrive [Date] [Time]"

### 4.3 Quote Request Workflow

**FR-12: Quote Request Steps**
- **Requirement**: System shall guide customer through quote request workflow for variable-price services
- **Steps**:
  1. Select service (from catalog or detail page)
  2. Select property (if multiple properties)
  3. Provide service details (description, photos, service-specific questions)
  4. Select contractors to request quote (1-5 contractors)
  5. Quote request confirmation (confirmation number, email sent)
  6. Wait for contractor responses (typically 24 hours)
  7. Receive and compare quotes (side-by-side comparison)
  8. Accept quote and book service (contractor contacts customer to schedule)

**FR-13: Service Details Input (Quote Request)**
- **Requirement**: System shall allow customer to provide detailed information for quote request
- **Description** (required):
  - Text field, 1000 character max
  - Placeholder: "Describe what you need in detail to help contractors provide accurate quotes"
  - Example: "Replace 50-gallon gas water heater, currently 10 years old, located in garage"
- **Photo Upload** (optional but encouraged):
  - Allow up to 5 photos
  - Prompts: "Photos help contractors provide accurate quotes. Upload photos of equipment, model plates, installation area."
- **Service-Specific Questions** (if applicable):
  - Water Heater Replacement: "Gas or Electric?", "Tank size (gallons)?", "Age of current unit?"
  - EV Charger Installation: "Do you have 240V outlet near parking area?", "Electrical panel capacity (amps)?"
  - Dynamic questions based on service type

**FR-14: Contractor Selection for Quote Request**
- **Requirement**: System shall allow customer to select 1-5 contractors to receive quote request
- **Display**: List of 3-5 contractors offering service (name, rating, review count)
- **Multi-Select**: Customer can select multiple contractors (checkboxes)
- **Recommendation**: "Select 3 contractors for best pricing comparison"
- **Submit**: "Request Quotes from [X] Contractors" button

**FR-15: Quote Request Confirmation**
- **Requirement**: System shall create quote request record and notify contractors
- **API Call**: Duke Quote Request API (`POST /api/quote-requests/create`)
- **Contractor Notification**: Contractors receive notification via contractor portal (email + in-app notification)
- **Customer Confirmation**:
  - Display: "Quote request sent! Confirmation number: #QR-2026-012345"
  - "Contractors typically respond within 24 hours"
  - Email confirmation sent to customer
  - Push notification: "[X] contractors will send quotes within 24 hours"

**FR-16: Quote Response Handling**
- **Requirement**: System shall receive contractor quote responses and notify customer
- **Contractor Submits Quote** (via contractor portal):
  - Quote amount (e.g., $1,200)
  - Scope of work description (e.g., "Includes 50-gal Bradford White tank, labor, disposal of old unit")
  - Estimated timeline (e.g., "Service can be completed within 3-5 business days")
  - Quote expiration date (e.g., "Valid for 30 days")
- **Customer Notification**:
  - Push notification: "You have a new quote from [Contractor Name]"
  - Email notification with quote summary
  - In-app badge: "3 new quotes" on My Quote Requests section

**FR-17: Quote Comparison**
- **Requirement**: System shall display side-by-side quote comparison for customer
- **Comparison Table**:
  - Column 1: Contractor name, rating, review count
  - Column 2: Quote amount ($1,200, $1,350, $1,150)
  - Column 3: Scope of work summary
  - Column 4: Estimated timeline
  - Column 5: "Accept Quote" or "Decline Quote" buttons
- **Sorting**: Sort by price (low to high), rating (high to low), response date (most recent)
- **CTA**: Customer taps "Accept Quote" for preferred contractor

**FR-18: Accept Quote and Book Service**
- **Requirement**: System shall allow customer to accept contractor quote and initiate service booking
- **Workflow**:
  1. Customer taps "Accept Quote"
  2. System displays booking confirmation:
     - Contractor: ABC Plumbing
     - Quote amount: $1,200
     - Next steps: "ABC Plumbing will contact you to schedule service"
  3. Contractor receives notification: "Customer accepted your quote"
  4. Contractor contacts customer (phone or in-app message) to schedule service
  5. Once scheduled, contractor marks service as "Scheduled" in contractor portal
  6. Customer receives confirmation: "Your service is scheduled for [Date] [Time]"
- **Payment**: For quote-based services, payment typically collected on-site (not pre-paid via app)

**FR-19: Decline Quote**
- **Requirement**: System shall allow customer to decline contractor quotes
- **Workflow**:
  1. Customer taps "Decline Quote"
  2. System prompts for reason (optional): "Price too high", "Found another contractor", "Changed mind", "Other"
  3. System notifies contractor: "Customer declined your quote"
  4. Quote marked as "Declined" in contractor portal
- **No Penalty**: Customer can decline all quotes without penalty

### 4.4 Contractor Management

**FR-20: Contractor Profile Display**
- **Requirement**: System shall display comprehensive contractor profile information
- **Profile Data**:
  - Contractor name, logo, hero image
  - Rating and review count (4.8 stars, 523 reviews)
  - Services offered (list of ad-hoc services)
  - Service area (zip codes covered)
  - Years in business, licensing/certifications (if provided)
  - "About Us" description
  - Contact info (phone, email - only displayed AFTER customer books service)
- **Reviews**: Display customer reviews (paginated, filterable by service type, sortable)

**FR-21: Contractor Matching Logic**
- **Requirement**: System shall match customers to appropriate contractors based on service, location, availability
- **Matching Criteria**:
  - Service type (contractor must offer selected service)
  - Location (contractor's service area must include customer's zip code)
  - Availability (contractor has capacity to take new jobs - if data available)
  - Rating (contractors sorted by rating, highest first)
- **API Call**: Duke Contractor Matching API (`POST /api/contractors/match`)
- **Response**: List of 3-5 contractors (if fewer than 3, display all available)

**FR-22: Contractor Availability Integration**
- **Requirement**: System shall display contractor availability if FSM tool integrated
- **Data Source**: FSM Tool API (if available) OR static availability data
- **Display**: "Next available: Thursday, Feb 15" OR "Typically available within 3-5 business days"
- **Fallback**: If no availability data, display generic message: "Contact contractor for availability"

### 4.5 Payment Processing

**FR-23: Pre-Payment via App**
- **Requirement**: System shall process pre-payment for flat-rate services
- **Payment Methods**:
  - Apple Pay (iOS only)
  - Google Pay (Android only)
  - Credit/Debit Card (manual entry or saved card)
- **Payment Gateway Integration**: Integrate with Duke-selected payment gateway (Stripe, Braintree, SpeedPay)
- **Authorization Flow**:
  1. Create payment intent (amount, customer ID, order ID)
  2. Present payment form (card entry or Apple Pay / Google Pay)
  3. Authorize payment (3D Secure if required)
  4. Confirm payment success
  5. If failure: Display error, allow retry with different method
- **Receipt**: Send receipt email within 5 minutes, include order details, contractor info, Duke contact info

**FR-24: Pay Contractor On-Site**
- **Requirement**: System shall allow customer to book service without pre-payment (pay contractor on-site)
- **Workflow**:
  - Customer selects "Pay on-site" during booking (Step 6)
  - Booking confirmed, no payment processed via app
  - Contractor collects payment after service completion (cash, check, contractor's card reader)
  - Customer does NOT receive receipt via app (contractor provides invoice)
- **Disclaimer**: Display during booking: "Final price may vary if additional work needed. You'll pay contractor directly after service."

**FR-25: Refund Processing**
- **Requirement**: System shall process refunds for cancelled services (if pre-paid)
- **Refund Policy**:
  - Cancellation 24+ hours before service: 100% refund
  - Cancellation <24 hours before service: 50% refund (restocking fee)
  - No-show / same-day cancellation: No refund
- **Refund Timeline**: Processed within 5-7 business days, refunded to original payment method
- **Notification**: Email notification: "Your refund of $XX.XX has been processed"

**FR-26: Payment to Contractors**
- **Requirement**: System shall track payments owed to contractors and facilitate payouts
- **Commission Structure**: Duke keeps 15-20% commission, contractor receives 80-85% of customer payment
  - Example: Customer pays $99, Duke keeps $15-20, contractor receives $79-84
- **Payment Cycle**: Weekly or bi-weekly (per contractor agreement)
- **Contractor Invoicing**: Contractors receive payment summary via admin portal (automated invoicing)

### 4.6 Service Tracking & Updates

**FR-27: My Services Dashboard**
- **Requirement**: System shall display list of all customer's booked services
- **Service Cards Display**:
  - Service name and icon
  - Property address
  - Contractor name and logo
  - Date and time
  - Status: Confirmed, Scheduled, En Route, In Progress, Completed, Cancelled
  - CTA buttons: "View Details", "Reschedule", "Cancel"
- **Filtering**: All Services, Upcoming, Completed, Cancelled
- **Sorting**: Default sort by date (upcoming first), can sort by date (newest first), status

**FR-28: Service Status Tracking**
- **Requirement**: System shall display real-time service status updates
- **Status States**:
  - **Confirmed**: Booking confirmed, awaiting contractor scheduling
  - **Scheduled**: Date/time confirmed by contractor
  - **En Route**: Contractor on the way (if GPS tracking enabled via FSM)
  - **In Progress**: Contractor arrived, work in progress
  - **Completed**: Service complete, awaiting customer rating
  - **Cancelled**: Service cancelled by customer or contractor
- **Progress Bar**: Visual indicator of current status step
- **Estimated Arrival**: Display ETA if GPS tracking enabled: "Estimated arrival: 8:45 AM"

**FR-29: Status Update Notifications**
- **Requirement**: System shall send push notifications and emails for status changes
- **Notification Triggers**:
  - Booking confirmed: "Service booked! [Contractor] will arrive [Date] [Time]"
  - Contractor en route: "Your contractor is on the way! ETA: 8:45 AM"
  - Contractor arrived: "Your contractor has arrived and is starting work"
  - Service complete: "Your service is complete! Please rate your experience"
  - Service cancelled: "Your service has been cancelled. Refund processed (if applicable)"
- **Email Notifications**: Send for major status changes (confirmed, completed, cancelled)

**FR-30: Reschedule Service**
- **Requirement**: System shall allow customer to reschedule booked service
- **Workflow**:
  1. Customer navigates to service detail → "Reschedule" button
  2. System displays contractor's availability calendar (next 14 days)
  3. Customer selects new date and time window
  4. System submits reschedule request to contractor
  5. Contractor approves (auto-approved if new date is available in calendar)
  6. Confirmation: "Service rescheduled to [new date and time]"
  7. Email and push notification sent
- **Reschedule Policy**: Free reschedule if 24+ hours before service, may incur fee if <24 hours

**FR-31: Cancel Service**
- **Requirement**: System shall allow customer to cancel booked service
- **Workflow**:
  1. Customer navigates to service detail → "Cancel Service" button
  2. Confirmation prompt: "Are you sure you want to cancel?"
  3. Cancellation policy displayed (refund policy based on timing)
  4. Customer provides reason (optional): "Reason for cancellation?"
  5. Customer confirms cancellation
  6. System processes cancellation, refund (if applicable)
  7. Contractor notified of cancellation
  8. Confirmation: "Service cancelled. Refund of $XX.XX processed (if applicable)"
- **Cancellation Deadline**: Must cancel 24+ hours before service for full refund

### 4.7 Post-Service Experience

**FR-32: Service Completion Notification**
- **Requirement**: System shall notify customer when contractor marks service complete
- **Notification**:
  - Push notification: "Your [Service Name] is complete!"
  - Email summary with service details, work performed, receipt (if pre-paid)
- **Work Performed Notes**: Contractor provides summary via contractor portal (e.g., "Cleaned coils, replaced air filter, checked refrigerant levels - all normal")

**FR-33: Rate Your Experience**
- **Requirement**: System shall prompt customer to rate service after completion
- **Rating Flow**:
  1. Push notification: "Your service is complete! Please rate your experience."
  2. Customer taps notification → opens rating screen
  3. Customer rates 5 dimensions (1-5 stars):
     - Overall satisfaction
     - Contractor professionalism
     - Quality of work
     - Timeliness (on-time arrival)
     - Value for money
  4. Customer writes review (optional, 500 char max)
  5. Customer uploads photos (optional, up to 3 photos of completed work)
  6. Customer submits rating
  7. Confirmation: "Thanks for your feedback!"
- **Incentive**: "Rate your service and earn 50 loyalty points" (if loyalty program active)

**FR-34: Post-Service Upsell to HPP Plans**
- **Requirement**: System shall display contextual upsell prompt to enroll in HPP plans after ad-hoc service
- **Trigger Logic**:
  - Service completed
  - Customer paid for ad-hoc service
  - Customer does NOT have HPP plan covering this service type
  - Wait 24 hours after service completion (avoid immediate annoyance)
- **Upsell Prompt**:
  - Heading: "Save on Future Services"
  - Message: "You just paid $99 for HVAC service. An HVAC Protection Plan ($12.99/month) would have covered this repair."
  - Savings Calculation: "$99 service vs. $12.99/month plan = break-even after 8 months. Future repairs covered!"
  - CTA: "Enroll in HVAC Plan" (opens plan enrollment workflow) or "Not Now"
- **Conversion Tracking**: Track % of customers who click "Enroll" vs. "Not Now"

**FR-35: Repeat Service Booking**
- **Requirement**: System shall prompt customer to book repeat service (for preventative maintenance services)
- **Trigger**: Service completed, service is preventative maintenance type (HVAC tune-up, water heater flushing, etc.)
- **Prompt**:
  - Heading: "Schedule Your Next Service"
  - Message: "HVAC tune-ups recommended twice per year (spring and fall). Book your next tune-up now!"
  - CTA: "Book Again" (pre-fill booking with same contractor, same property, same service)
- **Discount**: Offer discount for repeat booking: "Book now and save $10 on your next service"

---

## 5. USER WORKFLOWS (DETAILED)

### 5.1 Workflow: Book Flat-Rate HVAC Tune-Up

**Actors**: Duke customer (existing or new) needing HVAC tune-up

**Preconditions**:
- Customer has registered account and is logged in
- Customer has at least 1 property linked to account
- HVAC Seasonal Tune-Up service is available in customer's territory

**Main Flow**:

**Part A: Browse and Select Service**
1. Customer opens app, navigates to "Browse Services" from home screen
2. System displays service catalog with categories (HVAC, Electrical, Plumbing, Appliances)
3. Customer taps "HVAC Services" category
4. System displays HVAC service list:
   - HVAC Seasonal Tune-Up ($99)
   - AC Repair Diagnostic ($79)
   - Furnace Repair Diagnostic ($79)
   - Air Duct Cleaning ($300-$600)
   - Thermostat Installation ($125)
5. Customer taps "HVAC Seasonal Tune-Up ($99)"
6. System displays service detail page:
   - Service name: "HVAC Seasonal Tune-Up"
   - Pricing: $99 (flat-rate)
   - Rating: 4.8 stars (523 reviews)
   - Duration: "Typically 1-2 hours"
   - What's included: "22-point inspection, coil cleaning, filter replacement, refrigerant level check"
   - What's NOT included: "Refrigerant refill not included (charged separately if needed)"
   - 3 contractors offering service (ABC Heating 4.8 stars, Smith HVAC 4.6 stars, QuickCool 4.9 stars)
   - Customer reviews: 5 most recent
7. Customer reviews details, taps "Book Now"

**Part B: Booking Workflow**
8. **Step 1 of 8: Select Property**
   - System displays customer's property: "123 Main St, Charlotte NC 28202"
   - Customer confirms property, taps "Continue"
9. **Step 2 of 8: Select Contractor**
   - System displays 3 contractors:
     - ABC Heating & Cooling (4.8 stars, 523 reviews, "Available Thursday, Feb 15")
     - Smith HVAC (4.6 stars, 312 reviews, "Available Friday, Feb 16")
     - QuickCool Services (4.9 stars, 689 reviews, "Available Thursday, Feb 15")
   - Customer taps "Select Contractor" for ABC Heating (highest rating, earliest availability)
10. **Step 3 of 8: Schedule Service**
    - System displays availability calendar for ABC Heating (next 14 days)
    - Thursday Feb 15 and Friday Feb 16 are available (green), other dates disabled (grey)
    - Customer selects Thursday, Feb 15
    - System displays time windows: Morning (8am-12pm), Afternoon (12pm-4pm), Evening (4pm-8pm)
    - Customer selects "Morning (8am-12pm)", taps "Continue"
11. **Step 4 of 8: Provide Service Details**
    - System displays text field: "Describe the issue or what you need (optional)"
    - Customer types: "AC has been making grinding noise when starting up. Otherwise works fine."
    - System displays photo upload: "Upload photos (optional)"
    - Customer skips photo upload
    - System displays special instructions:
      - Pets on premises? Customer selects "Yes"
      - Access instructions: Customer types "Ring doorbell, don't knock (dog barks)"
      - Parking: Customer leaves blank
    - Customer taps "Continue"
12. **Step 5 of 8: Choose Payment Method**
    - System displays payment options:
      - ☑ Pre-Pay Now ($99) - "Priority scheduling, faster confirmation" (pre-selected)
      - ☐ Pay Contractor On-Site - "Pay after service via cash, check, or card"
    - Customer keeps "Pre-Pay Now" selected
    - System displays payment methods:
      - Apple Pay (customer's default)
      - Credit card (Visa ending in 1234 - saved card)
      - Add new payment method
    - Customer selects Apple Pay, taps "Continue"
13. **Step 6 of 8: Review and Confirm**
    - System displays booking summary:
      - Service: HVAC Seasonal Tune-Up
      - Property: 123 Main St, Charlotte NC 28202
      - Contractor: ABC Heating & Cooling (4.8 stars)
      - Date: Thursday, February 15, 2026
      - Time: Morning (8am-12pm)
      - Payment: Pre-paid via Apple Pay
      - Total: $99
    - System displays terms checkboxes:
      - ☑ "I agree to the Service Terms and Conditions"
      - ☑ "I understand pricing may change if additional work is needed"
    - Customer checks both boxes, taps "Confirm Booking"
14. **Payment Authorization (Apple Pay)**
    - System initiates Apple Pay authorization
    - Customer authenticates with Face ID
    - Payment authorized: $99 charged to Apple Pay
15. **Step 7 of 8: Booking Confirmation**
    - System displays success message: "Your service is booked!"
    - System displays booking details:
      - Confirmation Number: #BK-2026-012345
      - Service: HVAC Seasonal Tune-Up
      - Contractor: ABC Heating & Cooling
      - Contact: (704) 555-1234
      - Date: Thursday, Feb 15, 2026
      - Time: 8am-12pm
      - Charged: $99 to Apple Pay
    - System displays "Add to Calendar" button
    - System displays CTAs: "View My Services", "Book Another Service", "Done"
16. System sends confirmation email to customer (within 5 minutes)
17. System sends push notification: "Service booked! ABC Heating will arrive Thu Feb 15, 8am-12pm"
18. System notifies contractor via contractor portal: "New booking! HVAC Tune-Up for 123 Main St on Feb 15"
19. **End Flow**: Customer taps "Done", returns to app home

**Alternate Flow 1: Customer Chooses Pay On-Site**
- Step 12 alternate: Customer selects "Pay Contractor On-Site"
- Step 13: Booking summary shows "Payment: Pay contractor after service (cash, check, card)"
- Step 14 skipped: No payment authorization
- Step 15: Confirmation shows "Payment: Pay contractor on-site. Final price may vary if additional work needed."
- Step 18: Contractor notification shows "Payment: Customer will pay on-site"

**Alternate Flow 2: Multiple Properties**
- Step 8 alternate: Customer has vacation home
- System displays property selection:
  - ☑ 123 Main St, Charlotte NC 28202 (primary residence)
  - ☐ 456 Oak Ave, Durham NC 27703 (vacation home)
- Customer selects vacation home, taps "Continue"
- Booking proceeds for vacation home property

**Alternate Flow 3: Contractor Unavailable**
- Step 10 alternate: Customer selects contractor, but contractor calendar shows no availability in next 14 days
- System displays message: "This contractor has limited availability. Would you like to:"
  - Option 1: "Choose different contractor" (return to Step 9)
  - Option 2: "Request custom date" (contractor will contact customer to schedule)
- Customer selects "Choose different contractor", selects QuickCool Services instead

**Error Handling**:
- **Payment declined (Step 14)**: Display error: "Payment declined. Please try a different payment method." Return to Step 12.
- **API timeout during booking (Step 14)**: Display message: "Booking is taking longer than expected. We'll email confirmation within 30 minutes." Queue booking for manual processing.
- **Contractor at capacity**: Display error: "This contractor is no longer available for your selected date. Please choose a different contractor or date."

---

## 6. DEPENDENCIES & RISKS

[Content continues with comprehensive dependencies and risks section...]

---

**[PRD continues with sections 6-9: Dependencies & Risks, Implementation Plan, Success Metrics & Measurement, and Appendix...]**

---

END OF PRD #5: SERVICE BOOKING - AD-HOC SERVICES (PARTIAL)

**Note:** This PRD is approximately 50% complete due to character limits. The remaining sections would include:
- Section 6: Dependencies & Risks (Duke API dependencies, payment gateway, contractor network, FSM tool integration)
- Section 7: Implementation Plan (phased development, contractor onboarding, initial service catalog definition)
- Section 8: Success Metrics & Measurement (revenue tracking, customer acquisition, conversion funnels)
- Section 9: Appendix (glossary, related documents, open questions, assumptions)

Total estimated length when complete: 40-45 pages
