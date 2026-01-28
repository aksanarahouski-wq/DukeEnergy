# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

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

