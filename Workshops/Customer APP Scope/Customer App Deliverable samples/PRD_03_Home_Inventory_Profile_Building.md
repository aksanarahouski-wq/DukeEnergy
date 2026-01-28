# Product Requirements Document (PRD)
## Home Inventory & Profile Building

**Document Version:** 1.0
**Date:** January 27, 2026
**Author:** Orases Product Team
**Status:** Draft for Review
**Related Tickets:** TBD
**Document Owner:** Aksana Rahouski

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Background and Problem Statement](#background-and-problem-statement)
3. [Goals and Objectives](#goals-and-objectives)
4. [Target Users](#target-users)
5. [Scope](#scope)
6. [Functional Requirements](#functional-requirements)
7. [Dependencies and Risks](#dependencies-and-risks)
8. [Implementation Plan](#implementation-plan)
9. [Success Metrics](#success-metrics)
10. [Open Questions](#open-questions)

---

## Executive Summary

The Home Inventory & Profile Building feature transforms the Duke Residential Solutions app from a transactional service booking tool into a **comprehensive home management platform**. By incentivizing customers to build detailed profiles of their homes' appliances and systems, Duke unlocks strategic value: predictive maintenance, targeted upselling, customer stickiness, and a defensible competitive moat.

### Key Features
- **Barcode Scanning**: Auto-populate appliance details by scanning product labels
- **Manual Entry**: Add appliances/systems with make, model, age, purchase date, warranty info
- **Pre-Fill from Public Data**: Auto-populate home characteristics (sq ft, year built) from address
- **Contractor-Enhanced Data**: Technicians capture inventory during service visits (photos, model #s)
- **Gamification & Rewards**: Loyalty points for completing profile, badges for milestones
- **Maintenance Reminders**: Auto-generate maintenance schedules based on inventory
- **Home Health Scorecard**: Risk assessment showing appliance ages, upcoming replacement needs

### Business Impact
- **Increases customer lifetime value (LTV)**: Engaged users spend 3x more on services
- **Drives upselling**: Inventory enables targeted plan enrollment ("Your HVAC is 15 years old - protect it")
- **Reduces churn**: Customers with 80%+ profile completion have 2x retention rate
- **Creates data moat**: Proprietary home data not available to competitors
- **Enables predictive maintenance**: "Your water heater is 12 years old - book inspection now"
- **Improves service quality**: Contractors arrive prepared with right parts/tools

---

## Background and Problem Statement

### Current State

**Customer Home Knowledge Gap:**
- Customers don't know make/model/age of most appliances
- Service history scattered (paper invoices, email receipts, contractor notes)
- No centralized record of warranties, purchase dates, maintenance performed
- Customers reactive (call when broken) vs. proactive (maintain before failure)

**Duke's Knowledge Gap:**
- Duke only knows customer address, active HPP plans
- No data on what appliances/systems customer owns
- Cannot proactively recommend maintenance or replacement
- Cannot target upselling effectively (e.g., "You need appliance plan" but customer has no major appliances)

**Contractor Inefficiency:**
- Technicians arrive without knowing equipment details
- Must spend time identifying make/model on-site
- May not bring correct parts or tools
- Results in return trips, lower first-time fix rate

### Problems

**Problem 1: No Incentive for Customers to Provide Home Data**
- Customers don't see value in manually entering appliance details
- Time-consuming to gather serial numbers, model numbers, purchase dates
- Business impact: Customer profiles remain empty, no data for Duke to leverage

**Problem 2: Missed Upselling Opportunities**
- Duke can't target relevant services without knowing customer's home inventory
- Example: Sending HVAC plan promotions to customer with no HVAC system
- Business impact: Low conversion on marketing campaigns, wasted spend

**Problem 3: Reactive vs. Proactive Service Model**
- Customers only engage when something breaks (crisis mode)
- No preventative maintenance reminders
- Business impact: Lost revenue from preventative services, higher-cost emergency repairs

**Problem 4: Poor First-Time Fix Rate**
- Technicians don't know equipment details before arrival
- May bring wrong parts or need to order parts on-site
- Business impact: Lower customer satisfaction, higher operational costs

### Impact if Not Addressed

- **Transactional app only** - Customers use app only when booking service (low engagement)
- **No competitive differentiation** - Booking feature easily replicated by competitors
- **Cannot deliver on vision** - "Uber of home services" requires proactive, personalized experience
- **Missed $25M+ revenue opportunity** - Cannot upsell or drive preventative maintenance without data

---

## Goals and Objectives

### Primary Goals

1. **Achieve 80% Profile Completion**: 80% of active users have 5+ appliances/systems in profile within 6 months
2. **Enable Predictive Maintenance**: Auto-generate maintenance reminders for 90% of inventory items
3. **Drive Upselling**: Increase plan enrollment by 30% via targeted inventory-based recommendations
4. **Improve Service Quality**: 70% first-time fix rate improvement when technicians have inventory data

### Success Criteria

- ✅ 80% of users add at least 1 appliance within first 30 days
- ✅ Average profile completion score >60%
- ✅ 50% of service visits result in contractor adding/updating inventory data
- ✅ 70% of customers engage with at least 1 maintenance reminder within 6 months
- ✅ 30% increase in preventative maintenance service bookings
- ✅ 20% increase in HPP plan enrollments driven by inventory-based recommendations

### Non-Goals (Out of Scope)

- ❌ IoT device integration (smart thermostats, leak sensors) - Phase 2
- ❌ AI-powered photo recognition (auto-identify appliances from photos) - Phase 2
- ❌ Home sale transfer (transfer inventory to new homeowner) - Phase 2
- ❌ Energy efficiency tracking (correlate inventory with utility usage) - Phase 2+
- ❌ Predictive failure modeling (machine learning to predict failures) - Phase 3

---

## Target Users

### Primary Users

**1. Expanding Emma (Proactive Homeowner)**
- **Role**: 34-year-old first-time homeowner, wants to manage home proactively
- **Need**: Centralized record of appliances, maintenance schedules, warranty tracking
- **Pain Point**: Doesn't know what maintenance is needed or when
- **Benefit**: App tells her what to maintain and when; peace of mind

**2. Established Eleanor (Existing HPP Customer)**
- **Role**: 58-year-old homeowner, wants to maximize HPP plan value
- **Need**: Track service history, know what's covered, avoid surprises
- **Pain Point**: Doesn't remember when HVAC was last serviced or what work was done
- **Benefit**: Complete service history in one place; proof of maintenance for home sale

### Secondary Users

**3. Multi-Property Owner**
- **Role**: Customer with vacation home or rental property
- **Need**: Manage inventory for each property separately
- **Benefit**: Switch between properties, see which need maintenance

**4. Home Sellers**
- **Role**: Customer preparing to sell home
- **Need**: Export complete home profile and service history for buyer
- **Benefit**: Increases home value, speeds up sale

**5. Duke Residential Solutions (Business Stakeholder)**
- **Need:** Rich customer data to enable upselling, preventative maintenance, customer retention
- **Benefit:** Higher LTV, lower churn, targeted marketing

**6. Contractors (Secondary Beneficiary)**
- **Need:** Know equipment details before arrival (make, model, age)
- **Benefit:** Bring correct parts, improve first-time fix rate, faster service delivery

---

## Scope

### In Scope for MVP

**Inventory Addition Methods**
- ✅ Barcode scanning (camera-based, queries product database)
- ✅ Manual entry (form with make, model, serial, age, purchase date)
- ✅ Pre-fill from public data (address → sq ft, year built, property type)
- ✅ Contractor-enhanced data (technician adds/updates during service visit)

**Inventory Data Fields**
- ✅ Category: HVAC, Plumbing, Electrical, Appliances, Water Heater, Other
- ✅ Type: Specific appliance/system type (e.g., Central AC, Dishwasher, Electrical Panel)
- ✅ Make/Manufacturer
- ✅ Model Number
- ✅ Serial Number
- ✅ Manufacture Date / Age
- ✅ Purchase Date
- ✅ Warranty Info (expiration date, type)
- ✅ Location in Home (e.g., "Kitchen", "Basement", "Attic")
- ✅ Photos (up to 5 photos per item)
- ✅ Notes (free text, 500 char max)

**Gamification & Incentives**
- ✅ Profile Completion Score (percentage, visual progress bar)
- ✅ Loyalty Points for actions:
  - +20 points per appliance added manually
  - +10 points per appliance added via barcode scan
  - +10 points for reviewing contractor-added data
  - +50 points for 50% profile completion
  - +100 points for 100% profile completion
- ✅ Badges/Achievements (Fitbit-style):
  - "First Appliance" badge
  - "Home Basics" badge (5 items)
  - "Home Expert" badge (10+ items)
  - "Complete Profile" badge (100%)
- ✅ Dollar credit conversion: 100 points = $10 credit

**Maintenance Reminders**
- ✅ Auto-generate maintenance schedules based on inventory:
  - HVAC filter change (quarterly)
  - HVAC seasonal checkup (bi-annual)
  - Water heater flush (annual)
  - Appliance maintenance (per manufacturer recommendations)
- ✅ Custom reminders (user-created)
- ✅ Reminder notifications (push, email, SMS)
- ✅ Reminder actions: "Mark as Done" (earn +5 points) | "Book Service" | "Dismiss"

**Home Health Scorecard**
- ✅ Overall Home Health Score (0-100)
- ✅ Risk assessment by category:
  - "Your HVAC is 15 years old (avg lifespan 12-15 years) - consider replacement soon"
  - "Your water heater is 8 years old (avg lifespan 10-12 years) - still good"
- ✅ Appliances needing attention (overdue maintenance, nearing end of life)
- ✅ Estimated upcoming costs (e.g., "Budget $3,000-$5,000 for HVAC replacement")
- ✅ Positive messaging: "You've maintained this system well - great job!"

**Contractor Inventory Capture**
- ✅ Technician can add/update inventory during service visit
- ✅ **MVP Implementation Options:**
  - **Option A**: Technician takes photo, emails to admin, admin manually enters
  - **Option B**: Simple form in existing contractor portal to submit data
  - **Option C**: Defer to Phase 2 contractor mobile app
- ✅ Customer receives notification: "Your technician added details about your water heater"
- ✅ Customer reviews and confirms data (+10 points)

### Out of Scope (Phase 2+)

**Advanced Features**
- ❌ AI photo recognition (auto-identify appliances from photos)
- ❌ IoT integration (sync data from smart thermostats, leak sensors)
- ❌ Predictive failure modeling (ML to predict when appliances will fail)
- ❌ Energy efficiency tracking (correlate inventory with utility usage)
- ❌ Home sale transfer (auto-transfer inventory to new homeowner)

**Recall Automation**
- ❌ Automated CPSC recall checking (check inventory against recall database)
- ❌ Proactive recall notifications (alert customer if appliance has recall)

---

## Functional Requirements

### FR-1: Inventory Addition Methods

**FR-1.1: Barcode Scanning**
- User taps "Add Appliance" → "Scan Barcode"
- Camera opens with overlay guide: "Point at appliance label or manual"
- System uses OCR to extract barcode (UPC, EAN, QR code)
- System queries product database API (e.g., UPCitemdb, Barcode Lookup)
- **If match found**: Pre-fill make, model, type, category
- **If no match**: Display "Product not found. Enter details manually"
- User confirms or edits pre-filled data
- Success: "+10 points for scanning!"

**FR-1.2: Manual Entry**
- User taps "Add Appliance" → "Enter Manually"
- Form with fields:
  - Category: Dropdown (HVAC, Plumbing, Electrical, Appliances, Water Heater, Other)
  - Type: Dropdown (changes based on category)
  - Make/Manufacturer: Text input (autocomplete from common brands)
  - Model Number: Text input
  - Serial Number: Text input (optional)
  - Manufacture/Install Date: Date picker OR "Age" dropdown (< 5 years, 5-10, 10-15, 15+)
  - Purchase Date: Date picker (optional)
  - Warranty Expiration: Date picker (optional)
  - Location in Home: Dropdown (Kitchen, Bathroom, Basement, Attic, Garage, Outdoor, Other)
  - Photos: Upload/take photo (up to 5)
  - Notes: Free text (500 char max)
- "Save to Profile" button
- Success: "+20 points for adding appliance!"

**FR-1.3: Pre-Fill from Public Data (Bulk Import)**
- User taps "Import Home Details"
- System queries public records API (e.g., Zillow, Realtor.com) with address
- Returns: Square footage, Year built, Property type, Bedrooms, Bathrooms
- System displays pre-filled home characteristics for confirmation
- System suggests likely appliances based on property type:
  - "Homes like yours typically have:"
  - Central HVAC ✓
  - Water Heater ✓
  - Electrical Panel (200 amp) ✓
  - Dishwasher ✓
  - Range/Oven ✓
  - Washer/Dryer ✓
- User selects which to add (checkboxes)
- "Add Selected Items" button
- Items added with estimated data (user can edit details later)

**FR-1.4: Contractor-Enhanced Inventory**
- **Contractor Workflow** (MVP - Option B: Contractor Portal Form):
  1. Contractor completes service visit
  2. Contractor logs into existing Duke contractor portal
  3. Portal displays: "Capture appliance details for [Customer Name]"
  4. Simple form:
     - Category: HVAC / Plumbing / Electrical / Appliance / Water Heater
     - Make/Model/Serial: Text inputs
     - Manufacture Date: Text input or "Unknown"
     - Photos: Upload up to 3 photos
     - Notes: "Recommend replacement within 2 years" (500 char)
  5. Contractor submits → Data syncs to customer profile
- **Customer Experience**:
  - Push notification: "Your technician added details about your water heater. Review now!"
  - Customer opens app, sees "New Item to Review" badge in Home Profile
  - Customer views water heater details, photos, technician notes
  - Prompt: "Is this information correct?"
  - Customer taps "Looks Good" → +10 points earned
  - OR Customer taps "Edit" to make corrections

### FR-2: Inventory Management

**FR-2.1: Inventory List View**
- User navigates to "Home Profile" or "My Home"
- Dashboard displays:
  - Profile Completion Score: "Your profile is 65% complete" (progress bar)
  - Loyalty Points Balance: "240 points ($24 credit)"
  - Home Health Score: "78/100 - Good"
- "Add Appliance" button prominently displayed
- List of appliances grouped by category:
  - **Heating & Cooling** (2 items)
    - Carrier Heat Pump (Main Floor) - 8 years old
    - HVAC Filter (Main Floor) - Changed 2 months ago
  - **Plumbing** (1 item)
    - Rheem Water Heater (Garage) - 12 years old ⚠️
  - **Appliances** (3 items)
    - Whirlpool Dishwasher (Kitchen) - 5 years old
    - GE Refrigerator (Kitchen) - 3 years old
    - Samsung Washing Machine (Laundry) - 6 years old

**FR-2.2: Appliance Detail View**
- User taps appliance → Detail screen displays:
  - Make/Model/Serial
  - Age / Install Date
  - Photos (swipeable gallery)
  - Location in Home
  - Warranty Status: "Warranty expired 2 years ago" or "Under warranty until Dec 2026"
  - Service History: List of services performed on this appliance
  - Maintenance Reminders: "Next checkup due in 4 months"
  - Contractor Notes: "System operating normally. Recommend annual checkup."
- Edit button (pencil icon) → Edit form
- Delete button → Confirmation modal

**FR-2.3: Edit & Delete**
- User taps "Edit" → Same form as manual entry, pre-filled
- User updates fields, taps "Save Changes"
- User taps "Delete" → Confirmation: "Are you sure? Service history will be preserved."
- **Soft delete**: Appliance marked inactive, not permanently deleted (service history retained)

### FR-3: Gamification & Loyalty Rewards

**FR-3.1: Profile Completion Score**
- Calculation:
  - Base home info (address, property type, sq ft, year built): 20%
  - Each appliance/system added: +8% (up to 10 items = 80%)
  - Total possible: 100%
- Visual: Circular progress bar with percentage
- Display on Home Profile dashboard
- Milestone rewards at 50%, 80%, 100%

**FR-3.2: Loyalty Points System**
- Points earned for:
  - **Appliance added manually**: +20 points
  - **Appliance added via barcode scan**: +10 points (faster, so fewer points)
  - **Review contractor-added data**: +10 points
  - **Complete maintenance reminder**: +5 points (tap "Mark as Done")
  - **Milestone: 50% profile completion**: +50 bonus points
  - **Milestone: 80% profile completion**: +75 bonus points
  - **Milestone: 100% profile completion**: +100 bonus points
- Points balance displayed prominently
- Conversion: 100 points = $10 credit toward services
- Credits applied automatically at checkout

**FR-3.3: Badges & Achievements**
- Badges earned at milestones:
  - "First Appliance" badge (1 item added)
  - "Home Basics" badge (5 items)
  - "Home Expert" badge (10 items)
  - "Complete Profile" badge (100% completion)
  - "Maintenance Master" badge (10 maintenance tasks completed)
- Badges displayed on profile screen (visual icons)
- Shareable to social media (optional): "I just earned the Home Expert badge!"
- Leaderboard (optional for Phase 2): "You're in the top 10% of users!"

**FR-3.4: In-App Messaging for Incentives**
- After registration: "Build your home profile and earn $10 credit!"
- At 25% completion: "You're off to a great start! Add 3 more items to earn 50 bonus points."
- At 75% completion: "Almost there! Complete your profile to unlock $25 credit."
- After first service: "Your technician added water heater details. Review now and earn 10 points!"

### FR-4: Maintenance Reminders

**FR-4.1: Auto-Generated Reminders**
- System generates reminders based on appliance type and age:
  - **HVAC**:
    - "Change air filter" (quarterly, based on last change date)
    - "Schedule seasonal checkup" (bi-annual: spring and fall)
  - **Water Heater**:
    - "Flush water heater" (annual)
    - "Check anode rod" (every 3 years)
  - **Appliances**:
    - "Clean refrigerator coils" (bi-annual)
    - "Clean dryer vent" (annual)
  - **Electrical**:
    - "Test GFCI outlets" (monthly)
    - "Inspect electrical panel" (annual)
- Reminders added to customer's calendar automatically when appliance added

**FR-4.2: Reminder Notifications**
- Push notification: "Time to change your HVAC filter!"
- Email/SMS (per customer preference)
- In-app notification center (red badge on bell icon)
- Timing: 1 week before due date, day of due date, 1 week overdue

**FR-4.3: Reminder Actions**
- User taps reminder → Detail screen:
  - Appliance: Carrier Heat Pump (Main Floor)
  - Task: Change air filter
  - Due Date: March 15, 2026
  - Instructions: "3-minute video: How to change your HVAC filter" (DIY)
  - **Actions:**
    - "Mark as Done" → +5 points, reminder dismissed
    - "Book Service" → Navigate to service booking flow (pre-filled with appliance)
    - "Snooze 1 Week" → Reminder reappears in 7 days
    - "Dismiss" → Reminder permanently removed
- User can also create custom reminders: "Pool opening" (seasonal), "Gutter cleaning" (bi-annual)

**FR-4.4: Maintenance History Tracking**
- When user marks reminder as "Done", system logs:
  - Date completed
  - Task: "Changed HVAC filter"
  - Completed by: Customer (DIY) or Contractor (if booked service)
- Maintenance history displayed on appliance detail page
- Use case: Proof of maintenance for warranty claims, home sale

### FR-5: Home Health Scorecard

**FR-5.1: Overall Home Health Score Calculation**
- Algorithm considers:
  - **Age of appliances** (30% weight): Older appliances lower score
  - **Maintenance up-to-date** (30% weight): Overdue maintenance lowers score
  - **Known issues** (20% weight): Customer-reported issues lower score
  - **Warranty coverage** (10% weight): Items under warranty increase score
  - **Service history** (10% weight): Regular service increases score
- Score: 0-100 (color-coded: 0-50 = Red "Needs Attention", 51-75 = Yellow "Fair", 76-100 = Green "Good")

**FR-5.2: Home Health Dashboard**
- Display on Home Profile screen:
  - **Overall Score**: "78/100 - Good" (large number with color)
  - **Appliances Needing Attention**: 2 (red badge)
    - Water Heater (12 years old - nearing end of life) ⚠️
    - HVAC filter (overdue for change) ⚠️
  - **Upcoming Costs**: "Budget $1,500-$2,500 for water heater replacement within 2 years"
  - **Positive Messaging**: "Your HVAC is well-maintained - great job!"

**FR-5.3: Risk Assessment & Recommendations**
- System analyzes each appliance:
  - **Water Heater (12 years old)**:
    - "Average lifespan: 10-12 years. Your water heater is nearing end of life."
    - "Recommendation: Schedule inspection now to assess condition."
    - "Estimated replacement cost: $1,500-$2,500"
    - **Action Buttons**:
      - "Book Inspection" → Service booking flow
      - "Learn More" → Article on water heater replacement
      - "Dismiss" → Hide recommendation
  - **HVAC (8 years old)**:
    - "Average lifespan: 12-15 years. Your HVAC is in mid-life."
    - "Recommendation: Schedule bi-annual checkup to extend lifespan."
    - "Savings: Regular maintenance can extend life by 3-5 years."
    - **Action Buttons**:
      - "Book Checkup" → Service booking flow
      - "Set Reminder" → Add to maintenance reminders

**FR-5.4: Upselling Integration**
- System identifies upselling opportunities:
  - **Appliance without warranty**: "Protect your 5-year-old water heater with our Water Heater Plan ($8.99/month)"
  - **High-value appliance nearing end of life**: "Your HVAC is 15 years old. Protect against costly replacement with our H&C Plan."
  - **Multiple appliances without coverage**: "You have 3 appliances without protection. Save 20% with our Combo Plan."
- Upsell prompts displayed on Home Health dashboard
- Track conversion rate: How many customers enroll in plans after inventory-based recommendations

### FR-6: Contractor Inventory Capture (Behind the Scenes)

**FR-6.1: Contractor Portal Enhancement (MVP - Option B)**
- After contractor marks job complete in existing portal:
- Portal displays: "Optional: Add appliance details to customer's profile"
- Form with fields: Category, Make, Model, Serial, Manufacture Date, Photos (up to 3), Notes
- Contractor submits → Data sent to Duke backend API: `POST /inventory/contractor-add`
- API validates data, links to customer profile and service order
- Customer receives notification

**FR-6.2: Data Quality Control**
- System flags incomplete or suspicious data:
  - Missing make/model → Prompt contractor to complete
  - Mismatched appliance type (e.g., contractor says "HVAC" but service order was for plumbing) → Admin review
- Admin dashboard shows flagged entries for manual review
- Customer can edit or reject contractor-added data

**FR-6.3: Contractor Incentives (TBD)**
- **Option A**: Small bonus per item captured ($2-5 per appliance)
- **Option B**: Leaderboard/recognition for contractors who capture most data
- **Option C**: Positioned as creating future work pipeline (contractor who maintains system gets repeat business)
- **Decision Owner**: Duke Contractor Relations Team

---

## Dependencies and Risks

### Dependencies

**Internal Dependencies:**
1. **Customer Registration & Onboarding**
   - Users must have accounts before building inventory
   - **Mitigation:** Registration is Deliverable #1, prerequisite

2. **Loyalty Points System Backend**
   - Points calculation engine, balance tracking, credit conversion
   - **Mitigation:** Build simple points ledger table, can enhance later

3. **Contractor Portal Access**
   - Contractors need login to existing portal to add inventory data
   - **Mitigation:** Use existing contractor portal, add new form/API endpoint

**External Dependencies:**
1. **Product Database API (for Barcode Scanning)**
   - APIs: UPCitemdb, Barcode Lookup, or similar
   - **Mitigation:** Fallback to manual entry if API unavailable

2. **Public Records API (for Home Pre-Fill)**
   - APIs: Zillow, Realtor.com, or similar
   - **Mitigation:** Optional feature, can skip if API unavailable/expensive

3. **Contractor Participation**
   - Contractors must capture inventory data during visits
   - **Mitigation:** Start with opt-in pilot (25 contractors), expand based on success

### Risks

#### MEDIUM RISK: Low User Adoption (Inventory Building Friction)

**Description:** Customers don't see value in building inventory, profiles remain empty
**Impact:** High - Cannot deliver on strategic vision if no data collected
**Probability:** Medium (depends on incentive effectiveness)
**Mitigation:**
- Strong gamification (points, badges, tangible rewards)
- Immediate value: "Add your water heater to track warranty expiration"
- Contractor-enhanced data (passive inventory building)
- Targeted nudges: "Complete profile to unlock $25 credit"
- Track adoption rate weekly, iterate incentives

#### MEDIUM RISK: Barcode Scanning Accuracy

**Description:** Barcode API returns incorrect product data or no match
**Impact:** Medium - User frustration, lower adoption of scanning feature
**Probability:** Medium (product databases incomplete, especially for older appliances)
**Mitigation:**
- Allow user to edit pre-filled data before saving
- Fallback to manual entry always available
- Collect feedback: "Was this information correct?" → Improve database over time
- Consider multiple barcode APIs to increase match rate

#### LOW RISK: Contractor Data Quality

**Description:** Contractors submit incomplete or inaccurate inventory data
**Impact:** Low - Customer can edit/reject, but reduces value of contractor-enhanced feature
**Probability:** Low-Medium
**Mitigation:**
- Make key fields required (make, model at minimum)
- Admin review of flagged entries
- Customer confirms data ("Is this correct?") before adding to profile
- Track data quality metrics, provide feedback to contractors

---

## Implementation Plan

### Phase 1: Core Inventory Building
- [ ] Backend: Inventory database schema (appliances, maintenance reminders, points ledger)
- [ ] Backend: Inventory CRUD APIs (`POST /inventory/add`, `GET /inventory/list`, `PUT /inventory/update`, `DELETE /inventory/delete`)
- [ ] Mobile: "Add Appliance" manual entry form
- [ ] Mobile: Inventory list view (Home Profile dashboard)
- [ ] Mobile: Appliance detail view with edit/delete
- [ ] Mobile: Profile completion score calculation and display

### Phase 2: Barcode Scanning & Public Data Import
- [ ] Mobile: Camera integration for barcode scanning
- [ ] Integration: Barcode API (UPCitemdb or similar)
- [ ] Mobile: Pre-fill from barcode data
- [ ] Integration: Public records API (Zillow, Realtor.com)
- [ ] Mobile: Bulk import flow ("Import Home Details")

### Phase 3: Gamification & Loyalty Rewards
- [ ] Backend: Loyalty points calculation engine
- [ ] Backend: Points ledger (track points earned, points spent)
- [ ] Mobile: Points balance display
- [ ] Mobile: Badges/achievements (icons, unlock conditions)
- [ ] Mobile: In-app messaging for incentives
- [ ] Backend: Credit conversion logic (100 points = $10 credit at checkout)

### Phase 4: Maintenance Reminders
- [ ] Backend: Maintenance reminder generation logic (based on appliance type)
- [ ] Backend: Reminder notification system (push, SMS, email)
- [ ] Mobile: Reminder list view (notification center)
- [ ] Mobile: Reminder detail view with actions (Mark as Done, Book Service, Snooze, Dismiss)
- [ ] Backend: Maintenance history tracking

### Phase 5: Home Health Scorecard
- [ ] Backend: Home Health Score calculation algorithm
- [ ] Backend: Risk assessment logic (age-based, maintenance-based)
- [ ] Mobile: Home Health dashboard (score, appliances needing attention, recommendations)
- [ ] Mobile: Upselling integration (link to plan enrollment flow)

### Phase 6: Contractor Inventory Capture
- [ ] Backend: Contractor API endpoint (`POST /inventory/contractor-add`)
- [ ] Contractor Portal: Simple form to capture inventory data
- [ ] Mobile: "New Item to Review" notification and review flow
- [ ] Admin Portal: Data quality review dashboard

**Total Estimated Timeline:** To be determined during sprint planning

---

## Success Metrics

### Key Performance Indicators (KPIs)

**User Adoption Metrics:**
- Inventory adoption rate: Target 80% of users add 1+ appliance within 30 days
- Average profile completion: Target >60%
- Appliances per user: Target 5+ appliances
- Barcode scan usage: Target 40% of appliances added via barcode scan

**Engagement Metrics:**
- Maintenance reminder engagement: Target 70% of reminders result in action (Mark as Done or Book Service)
- Points earned per user: Target 200+ points per user (average)
- Badge unlock rate: Target 50% of users earn "Home Basics" badge

**Business Impact Metrics:**
- Plan enrollment lift: Baseline TBD → Target +30% driven by inventory-based recommendations
- Preventative service bookings: Target +30% increase
- Customer retention: Target 2x retention rate for users with 80%+ profile completion
- First-time fix rate: Target +70% improvement when contractors have inventory data

**Contractor Participation Metrics:**
- Contractor data capture rate: Target 50% of service visits result in inventory data added
- Data quality score: Target 90% of contractor-added data confirmed accurate by customers

### Measurement Plan

- **Measurement Period:** Post-launch monitoring period TBD
- **Review Cadence:** Regular reviews during initial rollout, ongoing monitoring thereafter
- **Success Threshold:** 80% adoption + 60% avg profile completion + 30% upsell lift

---

## Open Questions

### 1. Barcode API Selection & Cost
- **Question:** Which barcode API should we use? What is cost per lookup?
- **Options:**
  - **Option A**: UPCitemdb (free tier: 100 requests/day, paid: $0.01 per lookup)
  - **Option B**: Barcode Lookup (free tier: 100 requests/month, paid: $10/month for 10K lookups)
  - **Option C**: Build custom database (higher upfront cost, no per-lookup fees)
- **Decision Needed By:** Phase 2 planning
- **Decision Owner:** Orases Tech Lead + Duke Product Owner

### 2. Contractor Incentive Model
- **Question:** Should we pay contractors to capture inventory data?
- **Options:**
  - **Option A**: No payment → Rely on value proposition (future work pipeline)
  - **Option B**: Small bonus ($2-5 per appliance) → Drives adoption, costs $10-25K/year
  - **Option C**: Leaderboard/recognition only → Low cost, may not drive adoption
- **Decision Needed By:** Before contractor portal enhancement
- **Decision Owner:** Duke Contractor Relations Team

### 3. Loyalty Points Expiration Policy
- **Question:** Do loyalty points expire? If so, when?
- **Discussion Points:**
  - No expiration: Simpler, customer-friendly
  - 12-month expiration: Encourages active use, reduces liability
  - Expiration on account closure: Fair, minimizes disputes
- **Decision Needed By:** Before points system launch
- **Decision Owner:** Duke Legal + Product Owner

---

END OF DOCUMENT
