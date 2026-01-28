# PRD #4: Home Protection Plan Management

**Product Requirements Document**
**Duke Energy Residential Solutions - Home Services Mobile App**

**Version:** 1.0
**Last Updated:** January 2026
**Document Owner:** Orases Product Team
**Stakeholders:** Duke Residential Solutions Product Team, Duke IT, Customer Experience, Marketing

---

## EXECUTIVE SUMMARY

### What We're Building

A comprehensive Home Protection Plan (HPP) management system that enables Duke Energy and Piedmont Natural Gas customers to:
- View their existing HPP plans with full coverage details
- Compare available plans side-by-side to make informed decisions
- Enroll in new plans directly through the app
- Manage multiple plans across multiple properties
- Upgrade, downgrade, or cancel plans through self-service workflows
- Update payment methods and billing preferences

### Why It Matters

**For Customers:**
- **Transparency**: See exactly what's covered under each plan, no more digging through paperwork
- **Convenience**: Enroll in new plans in <5 minutes (vs. 15+ minute phone call)
- **Control**: Self-service cancellation, upgrades, and payment management
- **Informed Decisions**: Side-by-side plan comparison shows exactly what you get for your money

**For Duke Business:**
- **Revenue Growth**: Target 100,000 new HPP enrollments within 12 months
- **Multi-Plan Upsell**: Increase average plans per customer from 1.7 to 2.0 ($25-$40/month combined)
- **Conversion**: 25% of ad-hoc service customers convert to HPP plans within 12 months
- **ARPU Increase**: Higher-value customers with multiple plans
- **Call Center Reduction**: Self-service plan management reduces support calls by ~30%
- **Customer Lifetime Value**: HPP customers have 3x higher LTV than ad-hoc-only customers

### Key Features

✅ **My Plans Dashboard** - See all active plans across all properties at a glance
✅ **Plan Details** - Coverage items, exclusions, deductibles, service limits, billing details
✅ **Plan Catalog** - Browse all available HPP plans with descriptions and pricing
✅ **Plan Comparison** - Side-by-side feature matrix for up to 3 plans
✅ **Enrollment Workflow** - Step-by-step plan enrollment with terms acceptance
✅ **Payment Method Setup** - Choose utility bill, credit card, or ACH for plan charges
✅ **Self-Service Cancellation** - Cancel plans with retention offers and confirmation
✅ **Upgrade/Downgrade** - Switch plans with prorated pricing calculation
✅ **Multi-Property Support** - Manage plans for multiple homes from single account

### Success Metrics

- **Enrollment Conversion Rate**: 15% of app users enroll in new plan within 6 months
- **Multi-Plan Adoption**: 30% of existing single-plan customers add second plan within 12 months
- **Plan Comparison Usage**: 60% of users compare plans before enrolling
- **Self-Service Cancellation Rate**: 70% of cancellations handled via app (vs. phone)
- **Retention Offer Effectiveness**: 20% of cancellation attempts retained via app offers
- **Time to Enroll**: Average <5 minutes from plan selection to confirmation
- **Customer Satisfaction**: 85% satisfaction with plan management experience (post-enrollment survey)

---

## 1. BACKGROUND & PROBLEM STATEMENT

### 1.1 Current State

**How Customers Manage HPP Plans Today:**

**View Existing Plans:**
- Option 1: Call customer service (15+ minute wait, 5-10 minute call)
- Option 2: Log into Duke Energy website (limited functionality, confusing navigation)
- Option 3: Review paper billing statements (no coverage details, just monthly charge)
- **Pain Point**: Customers don't know what their plans cover until they need service

**Enroll in New Plans:**
- **ONLY via phone call** - no self-service enrollment option exists
- Average call time: 15-20 minutes (IVR navigation, account verification, product explanation, terms review)
- Call center hours: Monday-Friday 8am-6pm EST (inconvenient for working customers)
- **Pain Point**: Long wait times during peak hours, inability to enroll evenings/weekends

**Compare Plans:**
- Marketing website shows plan features, but NOT personalized to customer's situation
- No side-by-side comparison tool
- Difficult to understand differences between similar plans (e.g., Electrical System vs. HomeWire)
- **Pain Point**: Customers can't make informed decisions without calling and asking multiple questions

**Cancel or Modify Plans:**
- **ONLY via phone call** - must speak to retention specialist
- Cancellation process intentionally friction-heavy to reduce churn
- No self-service option to upgrade, downgrade, or change billing method
- **Pain Point**: Customers feel "trapped" in plans due to cancellation difficulty

**Multi-Property Management:**
- Customers with multiple properties must manage each property separately
- No consolidated view of all plans across all properties
- Confusing when properties have different plans or billing methods
- **Pain Point**: Vacation home owners and rental property owners frustrated by complexity

### 1.2 Problems This Deliverable Solves

**Problem 1: Plan Enrollment Friction Limits Growth**
- **Impact**: Duke loses potential HPP customers due to phone-only enrollment
- **Data Point**: ~40% of customers who call to inquire about plans do NOT enroll (call abandon, decision paralysis)
- **Customer Quote**: *"I wanted to add the appliance plan but didn't have time to wait on hold for 30 minutes. I never called back."* - Customer survey feedback

**Problem 2: Low Multi-Plan Adoption Rate**
- **Impact**: Average 1.7 plans per customer, target is 2.0+ plans
- **Root Cause**: Customers don't know other plans exist or how to add them
- **Upsell Opportunity**: Customers who book HVAC service often don't have HVAC plan (upsell at point of booking)
- **Revenue Impact**: Each additional plan = $9-15/month = $108-$180/year per customer

**Problem 3: Hidden Coverage Creates Service Friction**
- **Impact**: Customers call to book service, unsure if it's covered
- **Call Center Burden**: 30% of service calls start with "Is this covered by my plan?"
- **Customer Frustration**: Customers pay for plans but don't know what they cover
- **Quote from Kevin Oppermann**: *"We need to make sure customers understand what they have and when to use it."*

**Problem 4: Cancellation Friction Damages Brand Reputation**
- **Impact**: Customers complain on social media about difficulty canceling
- **Regulatory Risk**: Some states require easy cancellation (California AB-390, others following)
- **Customer Trust**: Hidden cancellation processes erode trust in Duke brand
- **Competitive Disadvantage**: Competitors (Amazon Home Services, Best Buy) offer instant cancellation

**Problem 5: Missed Upsell Opportunities at Service Booking**
- **Impact**: Customer books HVAC service, has HomeWire plan but NOT HVAC plan
- **Current State**: No prompt to enroll in HVAC plan at point of need
- **Conversion Opportunity**: 40% of customers who encounter non-covered service would enroll if prompted
- **Revenue Impact**: Contextual enrollment converts 3-5x higher than cold marketing

### 1.3 Impact if Not Addressed

**Revenue Loss:**
- **100,000 enrollments missed**: Target 100K new enrollments Year 1, phone-only limits growth
- **Multi-plan upsell lost**: Missing $10M+ annual recurring revenue from multi-plan adoption
- **Ad-hoc conversion lost**: 25% of ad-hoc customers would convert to plans if prompted (62K customers = $9M ARR)

**Operational Costs:**
- **Call center burden**: Plan inquiries and enrollments require ~20 min per call = $25-30 cost per enrollment
- **Retention team costs**: Cancellation retention specialists = $50K+ per FTE, need 5+ FTEs for manual process

**Customer Experience:**
- **Low NPS**: Phone-only plan management = 40-50 NPS (vs. 70+ target)
- **Churn risk**: Customers cancel due to frustration with management process, not plan dissatisfaction
- **Brand damage**: Social media complaints about difficult cancellation process

**Competitive Risk:**
- **Market share loss**: Competitors offer transparent, self-service plan management
- **Non-native customer acquisition**: Non-utility customers expect Amazon-like UX, won't tolerate phone-only

---

## 2. GOALS & SUCCESS CRITERIA

### 2.1 Primary Goals

**Goal 1: Enable Self-Service Plan Enrollment**
- **Target**: 70% of new enrollments happen via app (vs. phone) within 6 months of launch
- **Success Criteria**:
  - Enrollment workflow completes in <5 minutes average
  - <10% enrollment abandon rate (start enrollment, don't complete)
  - 90% first-time success rate (no errors requiring customer service escalation)

**Goal 2: Increase Multi-Plan Adoption**
- **Target**: Increase average plans per customer from 1.7 to 2.0 within 12 months
- **Success Criteria**:
  - 30% of existing single-plan customers add second plan within 12 months
  - Contextual upsell prompts (at service booking) convert at 15%+ rate
  - Plan comparison tool used by 60% of users before enrolling

**Goal 3: Improve Plan Transparency and Utilization**
- **Target**: 80% of app users view plan details within first 30 days of app use
- **Success Criteria**:
  - Customers booking services correctly identify if service is covered (95% accuracy)
  - Reduction in "Is this covered?" calls to call center (30% reduction)
  - Customer satisfaction with plan transparency: 85%+ (post-enrollment survey)

**Goal 4: Reduce Call Center Burden**
- **Target**: 70% of plan management actions self-service via app (vs. phone)
- **Success Criteria**:
  - Enrollments via app: 70%
  - Cancellations via app: 70%
  - Payment method updates via app: 80%
  - Plan upgrades/downgrades via app: 60%

**Goal 5: Maintain or Improve Plan Retention**
- **Target**: Reduce HPP cancellation rate by 10% (engaged app users less likely to cancel)
- **Success Criteria**:
  - Retention offers in app prevent 20% of cancellation attempts
  - App users have 15% lower churn rate than non-app users
  - Multi-plan customers have 25% lower churn rate (tracked via app)

### 2.2 Non-Goals (Explicitly Out of Scope)

❌ **White-Label Plan Management for Other Utilities** - Phase 1 is Duke/Piedmont only
❌ **Group/Family Plan Enrollments** - Individual plans per property only
❌ **Gifting Plans to Others** - Customer can only enroll their own properties
❌ **Third-Party Plan Integration** - Duke HPP plans only, no HomeServe or competitors
❌ **Plan Customization/Build-Your-Own** - Pre-defined plan packages only
❌ **Contractor-Initiated Enrollment** - Customers self-enroll only (not contractor upsell)
❌ **Corporate/Business Property Plans** - Residential customers only for MVP

### 2.3 Success Metrics (Detailed)

**Enrollment Metrics:**
- New enrollments via app: 70% of total (vs. 30% phone)
- Enrollment conversion rate: 15% of app users enroll within 6 months
- Average time to enroll: <5 minutes
- Enrollment abandon rate: <10%
- Plan comparison usage before enrollment: 60%

**Multi-Plan Adoption:**
- Average plans per customer: 1.7 → 2.0 within 12 months
- Single-plan customers adding second plan: 30% within 12 months
- Contextual upsell conversion (at service booking): 15%+
- Three-plan customers (power users): 10% of customer base

**Transparency & Utilization:**
- Customers viewing plan details: 80% within 30 days
- "Is this covered?" call volume: -30%
- Customers correctly identifying coverage: 95% accuracy
- Satisfaction with plan transparency: 85%+

**Self-Service Adoption:**
- Enrollments via app: 70%
- Cancellations via app: 70%
- Payment method updates via app: 80%
- Plan upgrades/downgrades via app: 60%

**Retention & Churn:**
- Retention offer acceptance rate: 20% of cancellation attempts
- App user churn rate: -15% vs. non-app users
- Multi-plan customer churn rate: -25% vs. single-plan customers
- Overall HPP cancellation rate: -10%

**Revenue Impact:**
- New enrollment revenue: $9-15/month per enrollment x 100K = $10.8M-$18M ARR
- Multi-plan upsell revenue: 30% of 800K customers add plan = 240K additional plans x $12 avg = $34.5M ARR
- Total revenue impact Year 1: $45M+ ARR

---

## 3. SCOPE DEFINITION

### 3.1 In Scope for Phase 1 (MVP)

#### 3.1.1 My Plans Dashboard

**Display Customer's Existing Plans:**
- List all active HPP plans across all customer properties
- Show plan name, property address, monthly charge, billing method
- Status indicators: Active, Pending Cancellation, Expired
- Quick links: View Details, Manage Payment, Cancel Plan
- Multi-property filtering: View all plans or filter by property

**Plan Summary Cards:**
- Plan icon/logo (branded per plan type)
- Plan name (e.g., "HomeWire Protection Plan")
- Property address (if multiple properties)
- Monthly charge amount
- Billing method (On Utility Bill, Credit Card, ACH)
- Enrollment date and renewal date
- Coverage summary (e.g., "Covers: Electrical wiring, outlets, switches")
- Action buttons: View Details, Manage

**Empty State (No Plans):**
- Customer has no active plans
- Prompt: "Protect your home with Duke Protection Plans"
- CTA: "Browse Plans" (links to plan catalog)

#### 3.1.2 Plan Details View

**Full Plan Information:**
- Plan name and description
- Property address (which home this plan covers)
- Enrollment date and renewal date
- Monthly charge and billing frequency (monthly, annual prepay)
- Billing method (Utility Bill, Credit Card xxxx-1234, ACH Bank xxx-5678)

**Coverage Details:**
- **Covered Items**: List of systems/appliances covered (e.g., "Electrical wiring up to 500 feet, outlets, switches, breaker panel")
- **Exclusions**: What's NOT covered (e.g., "Pre-existing conditions, code violations, outdoor wiring")
- **Deductible**: Service call fee (e.g., "$0 deductible" or "$50 per service call")
- **Service Limits**: Coverage caps (e.g., "Unlimited repairs" or "Up to $5,000 per year")
- **Service Area**: Geographic coverage (e.g., "Within Duke Energy service territory")

**Terms & Conditions:**
- Link to full Terms of Service PDF
- Cancellation policy summary
- Warranty information

**Plan Documents:**
- Download plan brochure (PDF)
- Download enrollment agreement (PDF)
- Download billing statements (if available)

**Action Buttons:**
- "Upgrade Plan" (upgrade to higher-tier plan)
- "Update Payment Method" (change billing)
- "Cancel Plan" (self-service cancellation)

#### 3.1.3 Plan Catalog (Browse Plans)

**Plan Listing:**
- Display all available HPP plans for customer's service territory
- Plans organized by category:
  - **Utility Line Protection**: HomeWire (electrical), HomePlumb (plumbing), HomeServe (gas lines)
  - **HVAC Plans**: Heating & Cooling, Heat Pump, AC-Only
  - **Appliance Plans**: Major Appliances, Kitchen Appliances, Water Heater
  - **Bundled Plans**: Whole Home Protection (multiple systems)

**Plan Cards:**
- Plan icon/logo
- Plan name
- Tagline (e.g., "Peace of mind for your home's electrical system")
- Monthly price (e.g., "$9.99/month")
- Coverage summary (e.g., "Covers: Wiring, outlets, switches, breaker panel")
- Rating/popularity indicator (e.g., "Most Popular Plan" badge)
- CTA button: "Learn More" or "Compare Plans"

**Filtering & Sorting:**
- Filter by category (Electrical, HVAC, Appliances, etc.)
- Filter by price range ($5-10/month, $10-15/month, $15+/month)
- Sort by: Popularity, Price (low to high), Price (high to low), Name

**Search:**
- Search plans by keyword (e.g., "HVAC", "water heater", "electrical")
- Autocomplete suggestions

**Personalized Recommendations:**
- "Recommended for You" section based on:
  - Home inventory data (customer has 15-year-old HVAC → recommend HVAC plan)
  - Service booking history (booked plumbing service → recommend HomePlumb plan)
  - Existing plans (has HomeWire, doesn't have HVAC → recommend HVAC plan)
- Algorithm prioritizes contextual relevance

#### 3.1.4 Plan Comparison Tool

**Side-by-Side Comparison:**
- Compare up to 3 plans at once
- Comparison table showing:
  - Monthly price
  - Covered items (checkmarks for yes, X for no)
  - Exclusions
  - Deductible
  - Service limits
  - Additional benefits (e.g., "24/7 emergency hotline")

**Comparison Features:**
- Add/remove plans from comparison
- Sticky header (plan names and prices stay visible when scrolling)
- Highlight differences (visual emphasis on what's unique to each plan)
- "Best Value" or "Most Comprehensive" badges

**Comparison Use Cases:**
- Customer comparing HomeWire vs. HomeWire Plus (basic vs. enhanced)
- Customer comparing HVAC plan vs. bundled Whole Home plan
- Customer comparing monthly vs. annual prepay pricing

**CTA from Comparison:**
- "Enroll in [Plan Name]" button for each plan
- "Save Comparison" (email or bookmark for later)

#### 3.1.5 Plan Enrollment Workflow

**Step 1: Select Plan**
- Customer clicks "Enroll" from plan details or comparison tool
- Confirm plan selection and pricing

**Step 2: Select Property**
- If customer has multiple properties, select which property this plan covers
- Display property address for confirmation
- Option to add new property if not listed (validates via Duke premise API)

**Step 3: Review Coverage**
- Display full coverage details (covered items, exclusions, deductibles)
- Prompt customer to confirm understanding: "I understand what is and isn't covered"

**Step 4: Choose Billing Method**
- **Option 1: Add to Utility Bill** (Duke/Piedmont customers only)
  - "Charge $9.99/month to my Duke Energy utility bill"
  - Confirm utility account number auto-populated (from registration)
- **Option 2: Credit Card**
  - Enter card details or select saved payment method
  - Supports Apple Pay, Google Pay, manual card entry
- **Option 3: ACH / Bank Account** (for recurring charges)
  - Enter routing and account number
  - Verify account ownership (micro-deposits or instant verification)

**Step 5: Review and Accept Terms**
- Display enrollment summary:
  - Plan name, property address, monthly charge, billing method
  - Effective date (typically next billing cycle)
  - First charge date
- Terms acceptance checkboxes:
  - ☑ "I agree to the Plan Terms and Conditions" (link to T&C)
  - ☑ "I authorize Duke to charge me $X.XX per month via [billing method]"
  - ☑ "I understand I can cancel at any time with 30 days notice"
- Legal disclosures (as required by Duke legal team)

**Step 6: Enrollment Confirmation**
- Success message: "You're enrolled! [Plan Name] is now protecting [Property Address]"
- Display enrollment details:
  - Effective date
  - First charge date (if not on utility bill)
  - Plan ID / confirmation number
- Next steps:
  - "View My Plans" (return to dashboard)
  - "Book a Service" (now that coverage exists)
  - "Add Another Plan" (multi-plan upsell)

**Email Confirmation:**
- Send confirmation email with:
  - Plan details and coverage summary
  - Terms and Conditions PDF attached
  - Customer service contact info

**Error Handling:**
- Payment declined: Show friendly error, allow retry with different payment method
- Premise validation failed: Prompt to verify address or contact customer service
- API timeout: Queue enrollment for manual processing, notify customer within 24 hours

#### 3.1.6 Self-Service Cancellation Workflow

**Step 1: Initiate Cancellation**
- Customer navigates to Plan Details → "Cancel Plan" button
- Confirmation prompt: "Are you sure you want to cancel [Plan Name]?"
- Reason selection (optional but encouraged):
  - Moving out of service area
  - No longer need coverage
  - Too expensive
  - Switching to competitor
  - Other (free text)

**Step 2: Retention Offer (If Applicable)**
- **Scenario 1: Customer selects "Too expensive"**
  - Offer: "Save 10% - Get 2 months at $8.99/month instead of $9.99"
  - CTA: "Keep Plan with Discount" or "Continue Cancellation"
- **Scenario 2: Customer has multiple service bookings history**
  - Reminder: "You've booked 3 services in the past year, saving $X in service call fees"
  - CTA: "Keep Plan" or "Continue Cancellation"
- **Scenario 3: Customer has multi-plan discount**
  - Warning: "Canceling this plan will remove your multi-plan discount ($3/month savings)"
  - CTA: "Keep Plan" or "Continue Cancellation"

**Step 3: Confirm Cancellation**
- Display cancellation details:
  - Effective date (typically end of current billing cycle)
  - Final charge amount (prorated if mid-cycle)
  - What happens next: "You'll lose coverage on [date], your final bill will be $X.XX"
- Final confirmation: "Cancel [Plan Name]" button (requires second confirmation)

**Step 4: Cancellation Confirmation**
- Success message: "[Plan Name] has been cancelled"
- Display details:
  - Coverage ends: [Date]
  - Final charge: $X.XX on [Date]
  - Confirmation number: #12345
- Next steps:
  - "View Remaining Plans" (if customer has other plans)
  - "Re-enroll Anytime" (link to plan catalog)
  - "Provide Feedback" (optional survey)

**Email Confirmation:**
- Send cancellation confirmation email with:
  - Cancellation details (effective date, final charge)
  - Reminder of coverage end date
  - Re-enrollment instructions (if customer changes mind)

**Cancellation Hold Period:**
- Customer can reverse cancellation up to 48 hours before effective date
- "Undo Cancellation" option in My Plans dashboard if still in hold period

**Manual Review Queue (Edge Cases):**
- Customer has active service order tied to plan → route to manual review
- Customer has outstanding balance → require balance payment before cancellation
- Cancellation within 30 days of enrollment → potential early termination fee (per T&C)

#### 3.1.7 Plan Upgrade/Downgrade Workflows

**Upgrade Plan:**
- Customer navigates to Plan Details → "Upgrade Plan"
- Display available upgrade options:
  - Example: HomeWire → HomeWire Plus (adds coverage for surge protection, smart home devices)
  - Example: HVAC Basic → HVAC Premium (adds refrigerant coverage, 24/7 emergency service)
- Show price difference: "+$3/month" or "+15%"
- Show what additional coverage includes
- Effective date: Immediate or next billing cycle (customer choice)
- Prorated pricing: Calculate credit for remaining days on current plan, charge difference

**Downgrade Plan:**
- Customer navigates to Plan Details → "Change Plan" → select lower-tier plan
- Warning: "You'll lose coverage for: [list of items]"
- Show price savings: "-$3/month" or "Save $36/year"
- Effective date: End of current billing cycle (no mid-cycle downgrades)
- Confirmation required: "I understand I'm losing coverage for [items]"

**Switch Plan (Different Category):**
- Example: Customer has HomeWire, wants to switch to HVAC instead (cancel one, enroll in another)
- Process as cancellation + enrollment
- Offer to keep both plans: "Most customers have 2-3 plans for comprehensive protection"
- Multi-plan discount applied if keeping both

#### 3.1.8 Payment Method Management

**View Saved Payment Methods:**
- Display all saved payment methods on file
- Card: Visa xxxx-1234 (Expires: 05/2027)
- Bank Account: Checking xxx-5678 (Bank of America)
- Utility Bill: Duke Energy Account #987654321

**Add Payment Method:**
- Add credit/debit card (manual entry or Apple Pay / Google Pay)
- Add bank account (routing + account number, verify with micro-deposits)
- Link to utility bill (for Duke/Piedmont customers)

**Update Payment Method for Plan:**
- Customer navigates to Plan Details → "Update Payment Method"
- Select new payment method from saved methods or add new one
- Effective date: Next billing cycle
- Confirmation: "Your [Plan Name] billing will switch to [new payment method] on [date]"

**Delete Payment Method:**
- Can only delete if NOT assigned to any active plan
- Warning: "This card is used for [Plan Name]. Update plan billing first before removing card."

**Failed Payment Handling:**
- If payment fails (card declined, insufficient funds):
  - In-app notification: "Payment Failed for [Plan Name]"
  - Email notification with instructions to update payment method
  - Grace period: 15 days to update payment before plan suspension
  - Suspended plan: Coverage inactive until payment resolved

#### 3.1.9 Multi-Property Plan Management

**Property Selection:**
- Customer with multiple properties sees property switcher at top of screen
- "Showing plans for: 123 Main St" with dropdown to switch properties
- Option to "View All Properties" (consolidated view)

**Consolidated Dashboard:**
- View all plans across all properties in single list
- Group by property: "123 Main St" section, "456 Oak Ave" section
- Summary: "You have 5 active plans protecting 2 properties"

**Property-Specific Enrollment:**
- When enrolling in new plan, always prompt: "Which property does this plan cover?"
- Validate property is within Duke service territory
- Prevent duplicate plans (can't enroll in HomeWire twice for same property)

**Transfer Plan Between Properties:**
- Out of scope for MVP (requires cancellation + re-enrollment)
- Future enhancement for Phase 2

#### 3.1.10 Contextual Upsell Prompts

**At Service Booking (Non-Covered Service):**
- Scenario: Customer books HVAC service, has HomeWire plan but NOT HVAC plan
- Prompt: "This service isn't covered by your current plans. Did you know you could save with an HVAC Protection Plan?"
- Display: HVAC plan details (covers this type of service, $12.99/month, no deductible)
- CTA: "Add HVAC Plan Now" or "Continue Without Plan"
- Conversion tracking: Measure % who enroll vs. decline

**In Home Inventory (Appliance Age Trigger):**
- Scenario: Customer adds 15-year-old water heater to home inventory
- Prompt: "Water heaters typically last 10-15 years. Protect yours with a Water Heater Plan for $6.99/month"
- CTA: "Learn More" or "Dismiss"

**After Service Completion:**
- Scenario: Customer books ad-hoc HVAC service, pays $150
- Prompt (in service completion notification): "You just paid $150 for HVAC service. An HVAC Plan ($12.99/month) would have covered this repair."
- CTA: "Enroll in HVAC Plan" or "Not Now"

**Anniversary Reminder:**
- Scenario: Customer enrolled 1 year ago, used plan 3 times, saved $X
- Notification: "Your HomeWire Plan saved you $450 this year! Add more coverage to save even more."
- CTA: "Browse Plans"

### 3.2 Out of Scope for Phase 1 (Deferred to Later Phases)

❌ **Business/Commercial Property Plans** - MVP is residential only
❌ **Plan Gifting** - Customer cannot gift plan enrollment to another person
❌ **Group Plans** - No family plans or multi-customer plans
❌ **Custom Plan Builder** - Customers cannot customize coverage, must choose pre-defined plans
❌ **Plan Transfer Between Customers** - If home is sold, new owner must enroll separately
❌ **Trial Periods / Money-Back Guarantees** - All enrollments are commitment (per T&C)
❌ **Agent-Assisted Enrollment** - Customer self-service only (no in-app chat with enrollment specialist)
❌ **Contractor-Initiated Enrollment** - Contractors cannot enroll customers on their behalf
❌ **Third-Party Plan Integration** - Only Duke HPP plans, no HomeServe, AHS, or other providers
❌ **Plan Pausing / Temporary Suspension** - Plans are always active or cancelled, no pause option
❌ **Historical Plan Comparison** - Cannot view past plans or enrollment history beyond current active plans
❌ **Plan Referral Program** - No "Refer a Friend" functionality (general app referral covers this)

---

## 4. FUNCTIONAL REQUIREMENTS

### 4.1 Plan Data Management

**FR-1: Display Customer's Active Plans**
- **Requirement**: System shall retrieve and display all active HPP plans for authenticated customer
- **Data Source**: Duke HPP Plan API (`GET /api/customer/{businessPartnerId}/plans`)
- **Display Requirements**:
  - Show plan name, property address, monthly charge, billing method, enrollment date
  - Group plans by property if customer has multiple properties
  - Update plan status in real-time (active, pending cancellation, expired)
- **Performance**: Load plan data within 2 seconds of navigating to My Plans dashboard
- **Error Handling**: If API fails, display cached plan data with "Last updated: [timestamp]" indicator

**FR-2: Display Detailed Plan Information**
- **Requirement**: System shall display full coverage details for selected plan
- **Details Include**:
  - Covered items (list with checkmarks)
  - Exclusions (list with X marks)
  - Deductible amount
  - Service limits (dollar caps, frequency limits)
  - Terms and Conditions (downloadable PDF link)
- **Data Source**: Duke HPP Plan API with expanded coverage details
- **UI Requirements**: Collapsible sections for Covered Items, Exclusions, Terms (reduce scroll)

**FR-3: Display Plan Catalog**
- **Requirement**: System shall display all available HPP plans for customer's service territory
- **Data Source**: Duke HPP Plan Catalog API (`GET /api/plans/catalog?zipCode=28202`)
- **Filtering Logic**:
  - Territory-based: Only show plans available in customer's zip code
  - Eligibility-based: Hide plans customer already has enrolled (show "Enrolled" badge instead of "Enroll" button)
- **Sorting Options**: Popularity (default), Price (low to high), Price (high to low), Name (A-Z)
- **Refresh Frequency**: Cache catalog for 24 hours, refresh daily (plan offerings change infrequently)

**FR-4: Plan Comparison Logic**
- **Requirement**: System shall allow customers to compare up to 3 plans side-by-side
- **Comparison Table Columns**: Plan Name, Monthly Price, Covered Items, Exclusions, Deductible, Service Limits, Additional Benefits
- **Comparison Features**:
  - Highlight differences (visual emphasis on unique features)
  - Sticky header (plan names visible when scrolling)
  - Add/remove plans from comparison dynamically
- **Shareable Comparison**: Generate shareable link or email comparison (for household decision-making)

### 4.2 Plan Enrollment

**FR-5: Enrollment Workflow Steps**
- **Requirement**: System shall guide customer through multi-step enrollment process
- **Steps**:
  1. Select plan (from catalog or comparison tool)
  2. Select property (if multiple properties)
  3. Review coverage (confirm understanding)
  4. Choose billing method (utility bill, credit card, ACH)
  5. Accept terms (checkboxes, legal disclosures)
  6. Confirm enrollment (show success message, send confirmation email)
- **Progress Indicator**: Show "Step 2 of 6" or progress bar throughout workflow
- **Save for Later**: Allow customer to exit enrollment and resume later (save progress for 24 hours)

**FR-6: Property Validation**
- **Requirement**: System shall validate that selected property is eligible for plan enrollment
- **Validation Checks**:
  - Property is within Duke Energy or Piedmont service territory
  - Property is linked to customer's account (premise ID exists)
  - Property does not already have this plan enrolled (prevent duplicates)
- **API Call**: Duke Customer Validation API (`GET /api/customer/{businessPartnerId}/premises`)
- **Error Handling**: If property ineligible, display friendly error: "This plan is not available for [address]. Browse other plans."

**FR-7: Payment Method Selection**
- **Requirement**: System shall allow customer to select billing method for plan charges
- **Options**:
  - **Utility Bill** (Duke/Piedmont customers only): Auto-select if customer has active utility account, charge appears on monthly utility bill
  - **Credit Card**: Manual entry (card number, expiration, CVV, billing zip) OR Apple Pay / Google Pay OR select saved card
  - **ACH / Bank Account**: Manual entry (routing number, account number) with instant verification or micro-deposit verification
- **Saved Payment Methods**: Display previously saved payment methods with "Use this card" option
- **Security**: Tokenize all payment data (do not store full card numbers, use PCI-compliant gateway)

**FR-8: Terms Acceptance**
- **Requirement**: System shall require customer to accept plan terms before enrollment confirmation
- **Required Checkboxes**:
  - ☑ "I agree to the Plan Terms and Conditions" (link to T&C PDF)
  - ☑ "I authorize Duke to charge me $X.XX per month via [billing method]"
  - ☑ "I understand I can cancel at any time with 30 days notice"
- **Legal Disclosures**: Display Duke-approved legal text (provided by Duke legal team)
- **Audit Trail**: Log terms acceptance with timestamp, IP address, device info for compliance

**FR-9: Enrollment Confirmation**
- **Requirement**: System shall create enrollment record and send confirmation to customer
- **API Call**: Duke HPP Enrollment API (`POST /api/customer/{businessPartnerId}/plans/enroll`)
- **Request Payload**: Customer ID, Plan ID, Premise ID, Billing Method, Terms Acceptance Timestamp
- **Response Handling**:
  - **Success**: Display confirmation message, send confirmation email, redirect to My Plans dashboard
  - **Failure**: Display error message, allow retry, queue for manual processing if multiple failures
- **Email Confirmation**: Send within 5 minutes of enrollment, include plan details, T&C PDF attachment, confirmation number

**FR-10: Enrollment Effective Date**
- **Requirement**: System shall calculate and display enrollment effective date
- **Logic**:
  - **Utility Bill Customers**: Effective first day of next billing cycle (to align with utility bill)
  - **Credit Card / ACH Customers**: Effective immediately upon payment authorization
- **Display**: Show effective date during enrollment review step: "Coverage begins: [Date]"

**FR-11: Payment Processing (If Immediate Charge)**
- **Requirement**: If customer chooses credit card or ACH, process first charge immediately (for immediate coverage)
- **Amount**: Pro-rated charge for remainder of current month + first full month (if enrollment mid-cycle)
- **Payment Gateway**: Integrate with Duke-selected payment gateway (Stripe, Braintree, SpeedPay, or other)
- **Authorization Flow**:
  1. Create payment intent (amount, customer ID, plan ID)
  2. Present payment form (card entry or Apple Pay / Google Pay)
  3. Authorize payment (3D Secure if required)
  4. Confirm payment success
  5. If failure: Display error, allow retry with different payment method

### 4.3 Plan Cancellation

**FR-12: Cancellation Initiation**
- **Requirement**: System shall allow customer to initiate plan cancellation via self-service workflow
- **Entry Point**: Plan Details page → "Cancel Plan" button
- **Confirmation Prompt**: Display confirmation dialog: "Are you sure you want to cancel [Plan Name]?"
- **Cancellation Reason**: Prompt customer to select reason (optional but encouraged for analytics)

**FR-13: Retention Offer Logic**
- **Requirement**: System shall display retention offer based on cancellation reason
- **Retention Scenarios**:
  - **Reason: "Too expensive"** → Offer 10% discount for 3 months
  - **Reason: "No longer need coverage"** + Customer has service history → Remind of past savings: "You've saved $X with this plan"
  - **Reason: "Switching to competitor"** → Offer to match competitor pricing (if customer provides proof)
  - **Multi-plan customer** → Warn that multi-plan discount will be lost
- **Offer Acceptance**: If customer accepts retention offer, apply discount, cancel cancellation request
- **Offer Decline**: If customer declines, proceed with cancellation

**FR-14: Cancellation Effective Date**
- **Requirement**: System shall calculate cancellation effective date per plan terms
- **Logic**:
  - **Standard**: End of current billing cycle (customer receives full month of coverage they paid for)
  - **Immediate Cancellation**: Optional for customer, but no refund for unused days
  - **Early Termination Fee**: If plan T&C require 30-day notice or early termination fee, calculate and display
- **Display**: Show effective date and final charge: "Coverage ends: [Date], Final charge: $X.XX on [Date]"

**FR-15: Cancellation Confirmation**
- **Requirement**: System shall process cancellation and send confirmation
- **API Call**: Duke HPP Cancellation API (`POST /api/customer/{businessPartnerId}/plans/{planId}/cancel`)
- **Request Payload**: Plan ID, Cancellation Reason, Effective Date
- **Response Handling**:
  - **Success**: Display confirmation, send email confirmation, update plan status to "Pending Cancellation"
  - **Failure**: Display error, route to manual cancellation queue, notify customer service team
- **Email Confirmation**: Send within 5 minutes, include effective date, final charge, re-enrollment instructions

**FR-16: Undo Cancellation (Hold Period)**
- **Requirement**: System shall allow customer to reverse cancellation within 48-hour hold period
- **Undo Option**: Display "Undo Cancellation" button in My Plans dashboard if still within hold period
- **API Call**: Duke HPP Cancel Cancellation API (`DELETE /api/customer/{businessPartnerId}/plans/{planId}/cancellation`)
- **Confirmation**: "Your [Plan Name] cancellation has been reversed. Coverage continues."

### 4.4 Plan Upgrade/Downgrade

**FR-17: Plan Upgrade Workflow**
- **Requirement**: System shall allow customer to upgrade to higher-tier plan within same category
- **Upgrade Logic**:
  - Display available upgrade options (e.g., HomeWire → HomeWire Plus)
  - Show price difference ("+$3/month")
  - Show additional coverage included (list of new items covered)
  - Calculate prorated charge (credit for unused portion of current plan, charge difference for upgraded plan)
- **Effective Date**: Immediate (customer chooses) or next billing cycle
- **API Call**: Duke HPP Upgrade API (`PUT /api/customer/{businessPartnerId}/plans/{planId}/upgrade`)

**FR-18: Plan Downgrade Workflow**
- **Requirement**: System shall allow customer to downgrade to lower-tier plan
- **Downgrade Warning**: Display warning of coverage loss: "You'll lose coverage for: [list of items]"
- **Price Savings**: Show monthly savings ("-$3/month" or "Save $36/year")
- **Effective Date**: End of current billing cycle (no mid-cycle downgrades to prevent gaming)
- **Confirmation Required**: Customer must confirm understanding of coverage loss
- **API Call**: Duke HPP Downgrade API (`PUT /api/customer/{businessPartnerId}/plans/{planId}/downgrade`)

**FR-19: Plan Switching (Different Category)**
- **Requirement**: System shall allow customer to switch from one plan category to another (e.g., cancel HomeWire, enroll in HVAC)
- **Process**: Cancellation of Plan A + Enrollment in Plan B (two separate workflows)
- **Upsell Prompt**: "Most customers have 2-3 plans. Keep [Plan A] and add [Plan B] for comprehensive protection?"
- **Multi-Plan Discount**: If customer keeps both plans, apply multi-plan discount automatically

### 4.5 Payment Method Management

**FR-20: View Saved Payment Methods**
- **Requirement**: System shall display all saved payment methods on customer account
- **Display**: Card type + last 4 digits + expiration date, Bank account type + last 4 digits
- **Indicators**: Show which payment method is assigned to which plan

**FR-21: Add Payment Method**
- **Requirement**: System shall allow customer to add new payment method
- **Methods Supported**: Credit/debit card (manual entry or Apple Pay / Google Pay), ACH / bank account
- **Tokenization**: Use payment gateway tokenization (never store full card numbers)
- **Validation**: Verify card is valid (Luhn algorithm, expiration date future, CVV 3-4 digits)

**FR-22: Update Plan Payment Method**
- **Requirement**: System shall allow customer to change billing method for existing plan
- **Workflow**: Plan Details → "Update Payment Method" → Select new method → Confirm
- **Effective Date**: Next billing cycle
- **API Call**: Duke HPP Update Payment API (`PUT /api/customer/{businessPartnerId}/plans/{planId}/payment`)

**FR-23: Delete Payment Method**
- **Requirement**: System shall allow customer to delete saved payment method if not in use
- **Validation**: Cannot delete payment method assigned to active plan
- **Warning**: "This card is used for [Plan Name]. Update plan billing first before removing card."

**FR-24: Failed Payment Handling**
- **Requirement**: System shall notify customer of payment failures and provide grace period
- **Notifications**: In-app notification + email notification within 24 hours of failed payment
- **Grace Period**: 15 days to update payment method before plan suspension
- **Plan Suspension**: If payment not resolved within grace period, suspend coverage (no service bookings allowed)
- **Reactivation**: Once payment method updated and charge successful, reactivate plan immediately

### 4.6 Multi-Property Management

**FR-25: Property Switcher**
- **Requirement**: System shall allow customer to view plans for specific property or all properties
- **UI**: Dropdown at top of My Plans dashboard: "Showing plans for: [Property Address]" with "All Properties" option
- **Filtering**: When property selected, show only plans for that property

**FR-26: Consolidated View**
- **Requirement**: System shall display all plans across all properties in single view
- **Grouping**: Group plans by property with property address headers
- **Summary**: "You have X active plans protecting Y properties"

**FR-27: Property-Specific Enrollment**
- **Requirement**: System shall always require property selection during enrollment
- **Validation**: Prevent duplicate plans (same plan cannot be enrolled twice for same property)
- **Error**: "You already have [Plan Name] for this property. Consider adding a different plan."

### 4.7 Contextual Upsell

**FR-28: Service Booking Upsell Prompt**
- **Requirement**: System shall detect when customer books non-covered service and display plan enrollment prompt
- **Trigger**: Customer selects service type (e.g., HVAC), system checks if customer has plan covering this service type
- **Logic**: If no plan covers service → display upsell prompt
- **Prompt**: "This service isn't covered. Enroll in [Relevant Plan] to save on future services."
- **CTA**: "Add Plan Now" (opens enrollment workflow) or "Continue Without Plan"

**FR-29: Home Inventory Upsell Prompt**
- **Requirement**: System shall detect when customer adds aging appliance to inventory and display plan enrollment prompt
- **Trigger**: Customer adds appliance with age > expected lifespan (e.g., 15-year-old water heater, typical lifespan 10-15 years)
- **Prompt**: "[Appliance] typically lasts X years. Protect yours with [Plan Name] for $Y/month."
- **CTA**: "Learn More" (opens plan details) or "Dismiss"

**FR-30: Post-Service Upsell Prompt**
- **Requirement**: System shall display plan enrollment prompt after customer completes ad-hoc service
- **Trigger**: Service marked complete, customer paid $X
- **Prompt**: "You just paid $X for [Service Type]. A [Plan Name] ($Y/month) would have covered this."
- **CTA**: "Enroll Now" or "Not Now"
- **Timing**: Display in service completion notification + follow-up email 24 hours later

### 4.8 Notifications & Communications

**FR-31: Enrollment Confirmation Email**
- **Requirement**: System shall send enrollment confirmation email within 5 minutes of successful enrollment
- **Content**: Plan name, property address, monthly charge, effective date, billing method, confirmation number, Terms PDF attachment
- **Template**: Duke-approved email template with branding

**FR-32: Cancellation Confirmation Email**
- **Requirement**: System shall send cancellation confirmation email within 5 minutes of successful cancellation
- **Content**: Plan name, cancellation effective date, final charge amount, re-enrollment instructions

**FR-33: Payment Failure Notification**
- **Requirement**: System shall send payment failure notification within 24 hours of failed charge
- **Content**: Plan name, failure reason, instructions to update payment method, grace period expiration date, link to app

**FR-34: Plan Renewal Reminder**
- **Requirement**: System shall send renewal reminder 30 days before annual plan renewal
- **Content**: Plan name, renewal date, renewal charge amount, option to cancel if desired

**FR-35: Retention Offer Email**
- **Requirement**: System shall send retention offer email if customer declines in-app retention offer
- **Content**: Re-state retention offer (e.g., "We'd hate to see you go. Here's 10% off for 3 months"), CTA to accept offer via app

---

## 5. USER WORKFLOWS (DETAILED)

### 5.1 Workflow: View Existing Plans

**Actors**: Existing Duke customer with 1+ active HPP plans

**Preconditions**:
- Customer has registered account and is logged in
- Customer has at least 1 active HPP plan linked to account

**Main Flow**:
1. Customer taps "My Plans" from app home screen or navigation menu
2. System retrieves active plans from Duke HPP API (GET /api/customer/{customerId}/plans)
3. System displays My Plans dashboard with plan cards
4. Customer sees:
   - Plan icon, plan name, property address, monthly charge, billing method
   - Status indicator: "Active"
   - Action buttons: "View Details", "Manage"
5. Customer taps "View Details" on specific plan
6. System displays Plan Details screen with:
   - Full coverage details (covered items, exclusions, deductibles, limits)
   - Enrollment date and renewal date
   - Billing method and next charge date
   - Terms & Conditions link
   - Action buttons: "Upgrade Plan", "Update Payment", "Cancel Plan"
7. Customer reviews coverage details
8. **End Flow**: Customer exits or navigates to other action

**Alternate Flow 1: No Plans Exist**
- Step 3 alternate: If customer has no active plans, display empty state
- Empty state shows: "Protect your home with Duke Protection Plans"
- CTA: "Browse Plans" (navigates to plan catalog)

**Alternate Flow 2: Multiple Properties**
- Step 3 alternate: If customer has multiple properties, display property switcher at top
- Customer can filter plans by property: "Showing plans for: 123 Main St" (dropdown)
- Customer can select "All Properties" to see consolidated view grouped by property

**Alternate Flow 3: Plan Pending Cancellation**
- Step 4 alternate: If plan has pending cancellation, display status: "Cancels on [Date]"
- Display "Undo Cancellation" button if still within 48-hour hold period

**Error Handling**:
- If API fails to retrieve plans, display cached plan data with "Last updated: [timestamp]" warning
- If no cached data available, display error: "Unable to load plans. Check connection and try again."

---

### 5.2 Workflow: Compare and Enroll in New Plan

**Actors**: Duke customer (existing or new) considering enrolling in HPP plan

**Preconditions**:
- Customer has registered account and is logged in
- Customer has at least 1 property linked to account (premise validation completed)

**Main Flow**:

**Part A: Browse and Compare Plans**
1. Customer navigates to "Browse Plans" from app home or My Plans dashboard
2. System retrieves plan catalog for customer's service territory (GET /api/plans/catalog?zipCode={zip})
3. System displays plan catalog with plan cards (icon, name, price, coverage summary, "Learn More" CTA)
4. Customer filters or searches:
   - Option 1: Filter by category (HVAC, Electrical, Appliances, etc.)
   - Option 2: Search by keyword ("HVAC", "water heater")
5. Customer taps "Learn More" on HomeWire Protection Plan
6. System displays Plan Details page with full coverage information
7. Customer taps "Add to Compare"
8. System adds HomeWire to comparison sidebar (shows "1 plan selected")
9. Customer returns to catalog, selects HomeWire Plus and HVAC plan for comparison
10. Customer taps "Compare Plans" button
11. System displays side-by-side comparison table:
    - Row 1: Monthly Price ($9.99, $12.99, $12.99)
    - Row 2: Covered Items (checkmarks and X for each item)
    - Row 3: Deductibles ($0, $0, $50)
    - Row 4: Service Limits (Unlimited, Unlimited, Up to $5K/year)
12. Customer reviews comparison, decides on HomeWire Plus

**Part B: Enroll in Selected Plan**
13. Customer taps "Enroll in HomeWire Plus" from comparison table
14. System displays enrollment workflow (Step 1 of 6: Confirm Plan Selection)
15. Customer confirms plan selection, taps "Continue"
16. **Step 2 of 6: Select Property**
    - System displays customer's linked properties: "123 Main St, Charlotte NC" (primary residence)
    - Customer confirms property, taps "Continue"
17. **Step 3 of 6: Review Coverage**
    - System displays full coverage details (covered items, exclusions, deductibles)
    - Customer reviews, checks box: "I understand what is and isn't covered"
    - Customer taps "Continue"
18. **Step 4 of 6: Choose Billing Method**
    - System displays billing options:
      - ☑ Add to Duke Energy utility bill (pre-selected, customer is Duke utility customer)
      - ☐ Credit card
      - ☐ ACH / Bank account
    - Customer keeps "Add to utility bill" selected, taps "Continue"
19. **Step 5 of 6: Review and Accept Terms**
    - System displays enrollment summary:
      - Plan: HomeWire Plus Protection Plan
      - Property: 123 Main St, Charlotte NC 28202
      - Monthly Charge: $12.99
      - Billing Method: Duke Energy Utility Bill (Account #987654321)
      - Effective Date: February 1, 2026 (first day of next billing cycle)
      - First Charge: $12.99 on February 15, 2026 (with utility bill)
    - Customer checks required boxes:
      - ☑ "I agree to the Plan Terms and Conditions" (link to T&C)
      - ☑ "I authorize Duke to charge me $12.99 per month via my utility bill"
      - ☑ "I understand I can cancel at any time with 30 days notice"
    - Customer taps "Confirm Enrollment"
20. System submits enrollment request to Duke HPP API (POST /api/customer/{id}/plans/enroll)
21. System displays loading indicator: "Processing your enrollment..."
22. **Step 6 of 6: Enrollment Confirmation**
    - System displays success message: "You're enrolled! HomeWire Plus is now protecting your home."
    - System displays enrollment details:
      - Confirmation Number: #EN-2026-012345
      - Effective Date: February 1, 2026
      - First Charge: $12.99 on February 15, 2026
    - System displays next steps:
      - "View My Plans" button
      - "Add Another Plan" button (multi-plan upsell)
      - "Book a Service" button (now that coverage exists)
23. System sends enrollment confirmation email to customer (within 5 minutes)
24. **End Flow**: Customer taps "View My Plans" and sees newly enrolled plan listed

**Alternate Flow 1: Customer Chooses Credit Card Billing**
- Step 18 alternate: Customer selects "Credit card" option
- System displays payment form:
  - Option A: Apple Pay / Google Pay (quick checkout)
  - Option B: Manual card entry (card number, expiration, CVV, billing zip)
  - Option C: Select saved card (if customer has saved cards on file)
- Customer selects Apple Pay
- System initiates Apple Pay authorization flow
- Customer authenticates with Face ID / Touch ID
- System tokenizes payment method
- Step 19: Enrollment summary shows "Billing Method: Apple Pay xxxx-1234"
- Step 20: System processes immediate first charge ($12.99) since not on utility bill
- Step 22: Confirmation shows "Charged: $12.99 to Apple Pay xxxx-1234" and "Coverage effective: Immediately"

**Alternate Flow 2: Multiple Properties**
- Step 16 alternate: If customer has multiple properties, system displays property selection list
- Customer selects: "456 Oak Ave, Durham NC" (vacation home)
- System validates property is in Duke service territory
- Enrollment proceeds for selected property

**Alternate Flow 3: Customer Already Has This Plan**
- Step 15 alternate: System detects customer already has HomeWire Plus for selected property
- System displays error: "You already have HomeWire Plus for this property. Browse other plans?"
- Customer returns to catalog or comparison

**Error Handling**:
- **API timeout during enrollment**: Display error: "Enrollment is taking longer than expected. We'll email confirmation within 24 hours." Queue for manual processing.
- **Payment declined (credit card)**: Display error: "Payment declined. Please try a different payment method." Return to Step 18.
- **Property validation failed**: Display error: "This plan is not available for [address]. Please verify address or browse other plans."

---

### 5.3 Workflow: Cancel Plan with Retention Offer

**Actors**: Existing Duke customer with active HPP plan considering cancellation

**Preconditions**:
- Customer has registered account and is logged in
- Customer has at least 1 active HPP plan

**Main Flow**:
1. Customer navigates to My Plans → selects plan → taps "View Details"
2. System displays Plan Details page
3. Customer taps "Cancel Plan" button
4. System displays confirmation dialog: "Are you sure you want to cancel HomeWire Plus?"
5. Customer taps "Yes, Cancel Plan"
6. System displays cancellation reason selection screen:
   - ☐ Moving out of service area
   - ☐ No longer need coverage
   - ☑ Too expensive
   - ☐ Switching to competitor
   - ☐ Other (free text)
7. Customer selects "Too expensive", taps "Continue"
8. **Retention Offer Display**:
   - System detects "Too expensive" reason
   - System displays retention offer:
     - Heading: "Before You Cancel - Special Offer"
     - Message: "We'd hate to see you go! Save 10% on your next 3 months: $11.69/month instead of $12.99"
     - Savings calculation: "You'll save $3.90 over 3 months"
     - CTA: "Keep Plan with Discount" or "Continue Cancellation"
9. Customer evaluates offer, decides to accept
10. Customer taps "Keep Plan with Discount"
11. System applies discount to plan (updates billing to $11.69/month for next 3 billing cycles)
12. System displays confirmation: "Your discount has been applied! HomeWire Plus now $11.69/month for 3 months."
13. System sends retention offer acceptance email
14. **End Flow**: Cancellation prevented, customer remains enrolled at discounted rate

**Alternate Flow 1: Customer Declines Retention Offer**
- Step 9 alternate: Customer taps "Continue Cancellation"
- System displays cancellation details screen:
  - Heading: "Cancellation Summary"
  - Coverage ends: End of current billing cycle (January 31, 2026)
  - Final charge: $12.99 on January 15, 2026 (full month since mid-cycle)
  - What you'll lose: "You'll lose coverage for: [list of covered items]"
  - Confirmation prompt: "Are you sure you want to cancel?"
  - CTA: "Cancel Plan" (requires second confirmation) or "Go Back"
- Customer taps "Cancel Plan"
- System submits cancellation request to Duke API (POST /api/plans/{planId}/cancel)
- System displays cancellation confirmation:
  - "HomeWire Plus has been cancelled"
  - Confirmation Number: #CAN-2026-012345
  - Coverage ends: January 31, 2026
  - Final charge: $12.99 on January 15, 2026
  - Re-enrollment instructions: "Changed your mind? Re-enroll anytime from Browse Plans."
- System sends cancellation confirmation email
- **End Flow**: Plan cancelled, customer loses coverage on effective date

**Alternate Flow 2: Customer Has Service Booking History**
- Step 8 alternate: System detects customer selected "No longer need coverage" but has booked 3 services in past year
- System displays different retention offer:
  - Heading: "Your Plan Has Saved You Money"
  - Message: "You've booked 3 services this year. Your plan covered $450 in repairs. Without the plan, you would have paid $500+."
  - Savings calculation: "You've saved: $450 - ($12.99/month x 12 months) = $294 net savings"
  - CTA: "Keep Plan" or "Continue Cancellation"
- Customer reviews savings history, decides to keep plan
- Customer taps "Keep Plan"
- System cancels cancellation request, plan remains active
- System displays: "We're glad you're staying! Your HomeWire Plus plan continues to protect your home."
- **End Flow**: Cancellation prevented

**Alternate Flow 3: Multi-Plan Customer Cancelling One Plan**
- Step 8 alternate: System detects customer has multiple plans with multi-plan discount
- System displays warning:
  - Heading: "Multi-Plan Discount Warning"
  - Message: "You currently have 2 plans and receive a $3/month multi-plan discount. Cancelling HomeWire Plus will remove this discount from your HVAC plan."
  - Impact: "Your HVAC plan will increase from $9.99/month to $12.99/month"
  - CTA: "Keep Both Plans" or "Continue Cancellation"
- Customer reviews, decides to keep both plans to preserve discount
- Customer taps "Keep Both Plans"
- System cancels cancellation request
- **End Flow**: Cancellation prevented

**Alternate Flow 4: Cancellation Within 48-Hour Hold Period**
- After Step 14 (Alt Flow 1 - cancellation confirmed):
- Customer changes mind, returns to My Plans dashboard within 24 hours
- System displays plan card with status: "Cancels on January 31, 2026"
- System displays "Undo Cancellation" button (available for 48 hours)
- Customer taps "Undo Cancellation"
- System displays confirmation: "Are you sure you want to undo this cancellation and keep HomeWire Plus?"
- Customer taps "Yes, Keep My Plan"
- System submits undo request to Duke API (DELETE /api/plans/{planId}/cancellation)
- System displays: "Your cancellation has been reversed. HomeWire Plus continues to protect your home."
- System sends undo confirmation email
- **End Flow**: Cancellation reversed, plan remains active

**Error Handling**:
- **API timeout during cancellation**: Display error: "Cancellation request is processing. We'll email confirmation within 24 hours." Queue for manual processing.
- **Active service order exists**: Display error: "You have an active service order tied to this plan. Please complete or cancel the service order before cancelling your plan." Block cancellation.
- **Outstanding balance**: Display error: "You have an outstanding balance of $XX.XX. Please resolve payment before cancelling." Link to payment resolution workflow.

---

## 6. DEPENDENCIES & RISKS

### 6.1 Technical Dependencies

**Dependency 1: Duke HPP Plan APIs**
- **Description**: Suite of APIs for plan data retrieval, enrollment, cancellation, modification
- **Required APIs**:
  - `GET /api/customer/{id}/plans` - Retrieve customer's active plans
  - `GET /api/plans/catalog` - Retrieve available plans for territory
  - `POST /api/customer/{id}/plans/enroll` - Enroll customer in new plan
  - `POST /api/plans/{id}/cancel` - Cancel existing plan
  - `PUT /api/plans/{id}/modify` - Upgrade/downgrade plan
  - `PUT /api/plans/{id}/payment` - Update payment method
- **Timeline Requirement**: APIs must be available within 2 weeks of development kickoff (per SOW Section 5.2)
- **Risk**: Duke IT may not deliver APIs on time
- **Mitigation**:
  - **Phase 1 (MVP)**: Display-only plan data (no enrollment/cancellation) if APIs delayed
  - **Phase 2**: Add enrollment/cancellation when APIs ready
  - Fallback: Use mock API responses for development, connect to real APIs during UAT

**Dependency 2: Payment Integration**
- **Description**: Payment gateway for credit card, ACH, Apple Pay, Google Pay processing
- **Required for**: Non-utility-bill customers to pay for plan charges
- **Duke Decision Required**: Select payment gateway vendor (Stripe, Braintree, SpeedPay, other)
- **Timeline Risk**: Payment gateway procurement may take 3-6 months (RFP, contract, PCI compliance)
- **Mitigation**:
  - **Phase 1 (MVP Launch)**: Support utility bill payment only (covers Duke/Piedmont customers)
  - Display message for non-utility customers: "Payment processing coming soon. Call to enroll: 1-800-XXX-XXXX"
  - **Phase 2 (3-4 months post-launch)**: Add credit card / ACH payment once gateway procured
  - This allows MVP launch without blocking on payment integration

**Dependency 3: Duke SAP Commerce (Hybris) Integration**
- **Description**: Plan catalog data stored in SAP Commerce (Hybris)
- **Required for**: Plan catalog retrieval, plan details, pricing, coverage definitions
- **Data Source**: Current system of record for HPP plan data
- **Risk**: SAP Commerce API layer may not exist yet (currently admin-only system)
- **Mitigation**:
  - Duke IT must create API layer to expose plan catalog to mobile app backend
  - Alternatively, cache plan catalog in app backend database (refreshed nightly)
  - Fallback: Manual JSON file with plan definitions if API delayed (not ideal, but unblocks development)

**Dependency 4: Duke Enterprise Customer Validation API**
- **Description**: Validate that customer can enroll in plans (has Duke/Piedmont utility account)
- **Already Identified**: Documented in Section 5.1 of integrations doc
- **Status**: High priority, should be available for MVP (customer registration depends on this)
- **Risk**: Low (already identified as critical MVP dependency)

**Dependency 5: Multi-Property Support (Premise API)**
- **Description**: Retrieve customer's multiple properties (vacation homes, rental properties)
- **Required for**: Customers enrolling plans for non-primary-residence properties
- **Risk**: Premise API may only return primary residence initially
- **Mitigation**:
  - **Phase 1 (MVP)**: Support single property (primary residence) only
  - **Phase 2**: Add multi-property support once premise API enhanced

### 6.2 Business Dependencies

**Dependency 1: Plan Catalog Definition**
- **Description**: Duke must define which HPP plans are available via app
- **Decision Required**: Which plans to offer (all existing plans? subset? new app-exclusive plans?)
- **Timeline**: Must be finalized during Analysis phase (weeks 1-12)
- **Impact**: Cannot build plan catalog UI without knowing plan offerings
- **Owner**: Duke Product Owner + Duke marketing team

**Dependency 2: Legal Approval for Terms & Conditions**
- **Description**: Plan enrollment requires customer acceptance of legal terms
- **Decision Required**:
  - Enrollment agreement language (what customer agrees to)
  - Cancellation policy (30-day notice? early termination fees?)
  - Auto-renewal terms (annual plans auto-renew?)
  - Dispute resolution and arbitration clauses
- **Timeline**: Must be finalized before enrollment workflow can launch (legal review = 4-8 weeks)
- **Owner**: Duke legal team
- **Risk**: Legal review delays are common, can extend timeline by weeks/months
- **Mitigation**: Start legal review early (during design phase), use existing Duke T&C as starting point

**Dependency 3: Retention Offer Rules**
- **Description**: Define retention offers for customers attempting to cancel
- **Decision Required**:
  - Which cancellation reasons trigger retention offers?
  - Offer details: 10% discount for 3 months? Free month? Gift card?
  - Budget for retention offers (discounts reduce revenue)
  - Approval workflow (automatic or requires manager approval?)
- **Timeline**: Can be defined post-MVP (start with no retention offers, add later)
- **Owner**: Duke customer retention team + finance

**Dependency 4: Pricing Strategy for Ad-Hoc Customers**
- **Description**: How are plans priced for non-Duke utility customers?
- **Decision Required**:
  - Same pricing as utility customers? Premium pricing?
  - Territory-based pricing variations?
  - Promotional pricing for first-time enrollments?
- **Timeline**: Must be defined before non-native customer enrollment launches
- **Owner**: Duke pricing team + finance

**Dependency 5: Multi-Plan Discount Rules**
- **Description**: Customers with 2+ plans receive discount
- **Decision Required**:
  - Discount amount ($3/month? 10%?)
  - Discount applies to all plans or specific plans?
  - Discount eligibility (all customers or certain plans only?)
- **Timeline**: Can be defined post-MVP (start with no discounts, add later)
- **Owner**: Duke finance + pricing team

### 6.3 Risks

**Risk 1: API Delivery Delays**
- **Description**: Duke IT does not deliver HPP APIs on time (2-week deadline)
- **Probability**: Medium-High (enterprise IT projects often delayed)
- **Impact**: High (blocks enrollment/cancellation features)
- **Mitigation**:
  - **Plan A**: Launch MVP with display-only plan data (no enrollment), add enrollment in Phase 2
  - **Plan B**: Use mock APIs for development, connect real APIs during UAT
  - **Plan C**: Build admin tool to manually process enrollments from app (temporary workaround)
- **Owner**: Duke IT + Orases project manager

**Risk 2: Payment Gateway Procurement Delays**
- **Description**: Duke takes 6+ months to procure and contract payment gateway
- **Probability**: High (RFP, legal review, PCI compliance audit = long process)
- **Impact**: Medium (blocks non-utility customer enrollment, limits ad-hoc customer acquisition)
- **Mitigation**:
  - Launch MVP with utility-bill-only payment (covers 800K existing customers)
  - Add credit card / ACH payment in Phase 2 once gateway procured
  - This unblocks MVP launch without sacrificing Duke customer experience
- **Owner**: Duke procurement + finance

**Risk 3: Legal Review Delays**
- **Description**: Duke legal team takes 8+ weeks to review and approve enrollment T&C
- **Probability**: Medium (legal reviews often take longer than expected)
- **Impact**: Medium (blocks enrollment workflow launch)
- **Mitigation**:
  - Start legal review early (during design phase, not development phase)
  - Use existing Duke T&C as starting point (faster approval)
  - Prepare fallback: soft launch enrollment with "Call to complete enrollment" if T&C not approved
- **Owner**: Duke legal team + Orases project manager

**Risk 4: Customer Confusion (What Plans Cover)**
- **Description**: Customers don't understand plan coverage, leading to low enrollment or high cancellation
- **Probability**: Medium (plan coverage can be complex)
- **Impact**: Medium (reduces enrollment conversion, increases support calls)
- **Mitigation**:
  - Clear, simple coverage descriptions (avoid jargon)
  - Visual coverage indicators (checkmarks, icons)
  - FAQs and tooltips throughout enrollment workflow
  - Pre-enrollment quiz: "What do you want coverage for?" → recommend plan
- **Owner**: Orases UX team + Duke content team

**Risk 5: Retention Offer Abuse**
- **Description**: Customers repeatedly cancel and re-enroll to get retention discounts
- **Probability**: Low (requires intentional gaming of system)
- **Impact**: Low (revenue loss from discounts)
- **Mitigation**:
  - Limit retention offers: 1 per customer per 12 months
  - Track retention offer history, flag repeat offenders
  - Require 90-day enrollment before cancellation eligible for retention offer
- **Owner**: Duke finance + fraud prevention team

**Risk 6: Multi-Property Complexity**
- **Description**: Customers with vacation homes or rental properties have complex plan management needs
- **Probability**: Medium (rental property owners are significant customer segment)
- **Impact**: Low (only affects subset of customers)
- **Mitigation**:
  - **Phase 1 (MVP)**: Support single property only (simplify for majority of customers)
  - **Phase 2**: Add multi-property support once core functionality validated
  - Provide phone support for complex multi-property scenarios
- **Owner**: Orases product team + Duke product owner

---

## 7. IMPLEMENTATION PLAN

### 7.1 Development Phases

**Phase 1: Foundation (Weeks 1-4)**
- Set up plan management module architecture
- Integrate with Duke HPP Plan APIs (mock APIs if real APIs delayed)
- Build My Plans dashboard (display-only)
- Build Plan Details view (read-only)
- UAT: Duke SMEs validate plan data display accuracy

**Phase 2: Plan Catalog & Comparison (Weeks 5-8)**
- Build plan catalog browsing UI
- Implement filtering, sorting, search
- Build plan comparison tool (side-by-side)
- Implement personalized plan recommendations
- UAT: Duke marketing team validates plan catalog content

**Phase 3: Enrollment Workflow (Weeks 9-14)**
- Build multi-step enrollment workflow (6 steps)
- Integrate with payment gateway (utility bill + credit card options)
- Implement property validation logic
- Implement terms acceptance and legal compliance
- Build enrollment confirmation and email notifications
- UAT: Duke legal team validates terms acceptance, Duke finance validates billing integration

**Phase 4: Cancellation & Retention (Weeks 15-18)**
- Build self-service cancellation workflow
- Implement retention offer logic and display
- Build cancellation confirmation and email notifications
- Implement 48-hour undo cancellation hold period
- UAT: Duke retention team validates retention offer rules

**Phase 5: Plan Management (Weeks 19-22)**
- Build plan upgrade/downgrade workflows
- Build payment method management (add, update, delete)
- Implement failed payment handling and grace period
- Build multi-property support (if premise API ready)
- UAT: Duke SMEs test full plan lifecycle (enroll, modify, cancel)

**Phase 6: Contextual Upsell (Weeks 23-24)**
- Implement service booking upsell prompts
- Implement home inventory upsell prompts
- Implement post-service upsell notifications
- UAT: Duke marketing team validates upsell messaging and conversion tracking

**Phase 7: Testing & Refinement (Weeks 25-28)**
- End-to-end testing (enrollment to cancellation)
- Performance testing (load testing for API calls)
- Security testing (PCI compliance for payment data)
- Accessibility testing (WCAG 2.1 AA compliance)
- Bug fixes and refinements based on UAT feedback

**Phase 8: Launch Preparation (Weeks 29-30)**
- Duke legal final approval for enrollment T&C
- Duke finance approval for billing integration
- Production API integration (switch from mock to real APIs)
- Soft launch to pilot group (100 customers)
- Monitor metrics, address issues
- Full launch to all customers

### 7.2 Key Milestones

| Milestone | Target Week | Deliverable | Stakeholder Approval |
|-----------|-------------|-------------|---------------------|
| **M1: Foundation Complete** | Week 4 | My Plans dashboard, Plan Details view | Duke Product Owner |
| **M2: Catalog & Comparison Complete** | Week 8 | Plan catalog, comparison tool | Duke Marketing |
| **M3: Enrollment Workflow Complete** | Week 14 | Full enrollment workflow, payment integration | Duke Finance + Legal |
| **M4: Cancellation Workflow Complete** | Week 18 | Self-service cancellation, retention offers | Duke Retention Team |
| **M5: Plan Management Complete** | Week 22 | Upgrade, downgrade, payment management | Duke Product Owner |
| **M6: Contextual Upsell Complete** | Week 24 | Service booking upsell, inventory upsell | Duke Marketing |
| **M7: Testing Complete** | Week 28 | All testing passed, bugs resolved | Duke QA + Orases QA |
| **M8: Production Launch** | Week 30 | Live to all customers | Duke Executive Sponsor |

### 7.3 Rollout Strategy

**Soft Launch (Week 29 - 100 Pilot Customers)**
- Select 100 Duke customers with existing plans (high engagement, active app users)
- Enable plan management features for pilot group only
- Monitor metrics:
  - Plan enrollment conversion rate
  - Enrollment abandon rate
  - Time to enroll average
  - Cancellation rate
  - Customer satisfaction (post-enrollment survey)
- Gather feedback via in-app survey and customer interviews
- Address critical bugs and UX issues before full launch

**Full Launch (Week 30 - All Customers)**
- Enable plan management features for all customers
- Push notification to all app users: "New Feature: Manage Your Protection Plans in the App"
- Email campaign to Duke email list (800K customers): "Enroll in Plans via App, No Phone Call Needed"
- Monitor metrics daily for first 2 weeks, weekly thereafter
- Customer support team trained on plan management workflows (handle escalations)

**Post-Launch Optimization (Weeks 31-40)**
- Analyze enrollment funnel: Identify drop-off points, optimize UI/UX
- A/B test retention offers: Test different discount amounts, messaging
- Refine contextual upsell prompts: Test timing, messaging, conversion rates
- Add enhancements based on customer feedback:
  - Gifting plans
  - Plan pausing (if legal/business approved)
  - Family plans (if product strategy approved)

### 7.4 Success Criteria for Launch

**Launch Readiness Checklist:**
- ✅ All APIs integrated and tested (enrollment, cancellation, payment)
- ✅ Duke legal approval for enrollment T&C
- ✅ Duke finance approval for billing integration
- ✅ Payment gateway live (at minimum utility bill payment, credit card nice-to-have)
- ✅ Email notifications configured and tested (enrollment, cancellation confirmations)
- ✅ Customer support team trained (handle escalations, answer plan questions)
- ✅ Metrics tracking configured (enrollment conversion, abandon rate, time to enroll)
- ✅ Soft launch successful (pilot group metrics meet targets, no critical bugs)

**Post-Launch Success Metrics (First 3 Months):**
- New enrollments via app: 5,000+ (average 55/day)
- Enrollment conversion rate: 10%+ (exceeds target of 15% within 6 months)
- Enrollment abandon rate: <15% (target <10%)
- Average time to enroll: <7 minutes (target <5 minutes, allow ramp-up period)
- Self-service cancellation rate: 50%+ (target 70% within 6 months)
- Customer satisfaction: 80%+ (target 85%, allow ramp-up period)
- Critical bugs: 0 (no bugs affecting payment processing, enrollment confirmation)

---

## 8. SUCCESS METRICS & MEASUREMENT

### 8.1 Key Performance Indicators (KPIs)

**Enrollment Metrics:**
- **New enrollments via app**: 100,000 within 12 months (Year 1 target)
- **Enrollment conversion rate**: 15% of app users enroll within 6 months
- **Enrollment funnel metrics**:
  - Browse catalog → View plan details: 60% proceed
  - View plan details → Start enrollment: 40% proceed
  - Start enrollment → Complete enrollment: 85% complete (15% abandon)
- **Average time to enroll**: <5 minutes
- **Enrollment channel split**: 70% app, 30% phone (target)

**Multi-Plan Adoption Metrics:**
- **Average plans per customer**: 1.7 → 2.0 within 12 months
- **Single-plan customers adding second plan**: 30% within 12 months (240K customers)
- **Three-plan adoption**: 10% of customer base (80K customers)
- **Contextual upsell conversion**:
  - Service booking upsell: 15% conversion
  - Home inventory upsell: 10% conversion
  - Post-service upsell: 20% conversion

**Transparency & Utilization Metrics:**
- **Customers viewing plan details**: 80% within 30 days of app use
- **Plan comparison usage**: 60% of users compare plans before enrolling
- **"Is this covered?" call volume**: -30% reduction
- **Customers correctly identifying coverage**: 95% accuracy (measured via service bookings)

**Self-Service Adoption Metrics:**
- **Enrollments via app**: 70% (vs. 30% phone)
- **Cancellations via app**: 70% (vs. 30% phone)
- **Payment method updates via app**: 80% (vs. 20% phone)
- **Plan upgrades/downgrades via app**: 60% (vs. 40% phone)

**Retention & Churn Metrics:**
- **Retention offer acceptance**: 20% of cancellation attempts
- **App user churn rate**: -15% vs. non-app users (app users more engaged, less likely to cancel)
- **Multi-plan customer churn rate**: -25% vs. single-plan customers (multi-plan customers more invested)
- **Overall HPP cancellation rate**: -10% (from baseline)

**Revenue Impact Metrics:**
- **New enrollment revenue**: 100K enrollments x $12 avg/month = $14.4M ARR
- **Multi-plan upsell revenue**: 240K additional plans x $12 avg/month = $34.5M ARR
- **Total revenue impact**: $48.9M ARR (Year 1)
- **Revenue per app user**: $150/year (average across enrollments, upsells, retention)

**Customer Satisfaction Metrics:**
- **Post-enrollment survey**: 85%+ satisfaction
- **NPS for plan management**: 70+ (app users vs. phone-only customers)
- **App store reviews mentioning plans**: 4.5+ stars
- **Customer support escalations**: <5% of enrollments require support

### 8.2 Measurement Plan

**Data Sources:**
- **App analytics** (Mixpanel, Amplitude): User behavior, funnel conversion, feature usage
- **Backend database**: Enrollment records, cancellation records, plan modifications
- **Duke HPP APIs**: Plan enrollment data, cancellation data (source of truth)
- **Payment gateway**: Payment success/failure rates, payment method distribution
- **Customer surveys**: Post-enrollment satisfaction, post-cancellation feedback
- **Call center data**: Call volume (enrollments, cancellations, plan inquiries)

**Dashboards:**
- **Enrollment Dashboard**: New enrollments (daily, weekly, monthly), conversion funnel, time to enroll, abandon rate
- **Revenue Dashboard**: ARR from app enrollments, multi-plan upsell revenue, retention offer cost
- **Self-Service Dashboard**: % of enrollments via app vs. phone, % of cancellations via app vs. phone
- **Retention Dashboard**: Cancellation attempts, retention offer acceptance rate, churn rate by segment

**Review Cadence:**
- **Daily**: Enrollment volume, critical bugs, payment failures (first 2 weeks post-launch)
- **Weekly**: Enrollment conversion rate, funnel drop-offs, customer feedback (first 3 months)
- **Monthly**: Revenue impact, multi-plan adoption, retention metrics, customer satisfaction (ongoing)
- **Quarterly**: Overall business impact, ROI, strategic adjustments

**Optimization Triggers:**
- **If enrollment conversion rate <10%**: Investigate funnel drop-offs, A/B test enrollment UI
- **If abandon rate >20%**: Simplify enrollment steps, reduce friction
- **If time to enroll >7 minutes**: Streamline workflow, pre-populate more data
- **If retention offer acceptance <15%**: Test different discount amounts, messaging
- **If self-service rate <50%**: Investigate why customers still calling, improve UX

---

## 9. APPENDIX

### 9.1 Glossary

- **HPP**: Home Protection Plan (Duke's warranty/service plan products)
- **Duke Energy**: Utility provider (electricity) in North Carolina, South Carolina, Florida, Indiana, Ohio, Kentucky
- **Piedmont Natural Gas**: Natural gas utility provider (Duke Energy subsidiary)
- **Native Customer**: Customer with Duke Energy or Piedmont utility account
- **Non-Native Customer**: Customer without Duke/Piedmont utility account (expansion target)
- **Plan Enrollment**: Customer signing up for new HPP plan
- **Plan Cancellation**: Customer terminating HPP plan
- **Retention Offer**: Discount or incentive to prevent customer from canceling plan
- **Multi-Plan Discount**: Discount applied when customer has 2+ plans
- **Contextual Upsell**: Enrollment prompt shown at relevant moment (e.g., when booking non-covered service)
- **Self-Service**: Customer completes action via app without calling customer support

### 9.2 Related Documents

- **RFP Background**: Original Duke Energy RFP for Home Services Mobile App
- **PRD #1**: Customer Registration & Onboarding (prerequisite for plan management)
- **PRD #2**: Service Booking - HPP Covered Services (plans determine coverage)
- **PRD #3**: Home Inventory & Profile Building (drives contextual upsell)
- **PRD #5** (Future): Service Booking - Ad-Hoc Services (upsell to plans)
- **PRD #7** (Future): Payment Processing (enables non-utility customer enrollment)
- **Integration Documentation**: Section 5.2 - Home Protection Plan APIs
- **Business Goals**: Section 6 - Business Goals & Success Metrics

### 9.3 Open Questions

**For Duke Product Team:**
1. Which HPP plans should be available via app? All existing plans or subset?
2. Should we create app-exclusive plans (e.g., discounted digital-only enrollment)?
3. Multi-plan discount rules: $3/month flat or % discount? Applies to all plans or specific plans?
4. Retention offer budget: What's the maximum discount we can offer to retain customers?
5. Annual plans: Do they auto-renew or require manual renewal?

**For Duke Legal Team:**
6. Enrollment T&C language: Use existing Duke T&C or create app-specific version?
7. Cancellation policy: 30-day notice required or instant cancellation allowed?
8. Early termination fees: Do any plans have early termination fees (e.g., cancel within 90 days)?
9. Dispute resolution: Arbitration clause required?

**For Duke IT:**
10. HPP Plan APIs: What's the realistic timeline for API delivery? Can mock APIs be provided for development?
11. SAP Commerce integration: Is API layer being built or should we cache plan catalog?
12. Payment gateway: Which vendor is Duke selecting? What's the procurement timeline?

**For Duke Finance:**
13. Ad-hoc customer pricing: Same pricing as utility customers or premium pricing?
14. Billing integration: Can we add plan charges to utility bills programmatically or requires manual process?
15. Refund policy: If customer cancels mid-cycle, prorated refund or no refund?

### 9.4 Assumptions

- Duke HPP APIs will be available within 4 weeks of development kickoff (allowing 2-week buffer)
- Duke legal team will approve enrollment T&C within 8 weeks of submission
- Payment gateway will support utility bill charging for Duke/Piedmont customers
- Multi-plan discount will be automated (no manual approval required)
- Retention offers will be automated (no manager approval for standard offers)
- Customers can cancel at any time with 30-day notice (no early termination fees)
- Annual plans auto-renew unless customer cancels
- Plan pricing is fixed (no dynamic pricing based on customer risk profile)

---

END OF PRD #4: HOME PROTECTION PLAN MANAGEMENT
