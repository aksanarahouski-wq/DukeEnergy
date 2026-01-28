# Data Entities & Workflow Analysis
## Duke Energy Residential Solutions Home Services App

**Date Created:** November 5, 2025
**Purpose:** Identify all data entities, their management workflows, and role-based access requirements
**Source:** RFP requirements, meeting analysis, and discovery workshop preparation

---

## Overview

This document maps out all data entities in the Duke Energy Home Services ecosystem, identifying:
- **What data** needs to be collected and managed
- **Where data** currently exists (if at all)
- **Who** creates, reads, updates, and deletes (CRUD) each data entity
- **Current processes** for managing this data
- **Expected workflows** for each role (Customer, Admin, Contractor)

---

## Critical Data Entities

### 1. **CUSTOMERS**

#### Data Points to Collect:
- **Identity:**
  - Customer ID (system-generated)
  - Name (first, last, middle initial)
  - Email address
  - Phone number (primary, secondary)
  - Authentication credentials

- **Customer Type:**
  - Native Duke customer (yes/no)
  - Native P&G customer (yes/no)
  - Non-native customer (yes/no)
  - Utility account number (if native)

- **Address/Property:**
  - Primary property address
  - Multiple properties (if applicable)
  - Property type (single-family, condo, townhome, etc.)
  - Years at property

- **HPP Plans:**
  - List of active HPP plans (water heater, HVAC, electrical, plumbing, appliance)
  - Plan start dates
  - Monthly fees
  - Coverage details
  - Plan status (active, cancelled, expired)

- **Preferences:**
  - Communication preferences (email, SMS, push notifications)
  - Language preference (English, Spanish)
  - Marketing opt-in/opt-out
  - Preferred contractors (if feature enabled)

#### Current State:
- **Native customers:** Data exists in Commerce (Duke) or Dynamics (P&G)
- **Non-native customers:** No system exists - need to build

#### Role-Based Access:

| Data Point | Customer (View/Edit) | Admin (View/Edit) | Contractor (View/Edit) |
|------------|---------------------|-------------------|----------------------|
| Identity info | View/Edit (limited) | View/Edit (full) | View only (name, address, phone) |
| Contact info | View/Edit | View/Edit | View only (masked?) |
| HPP plans | View only | View/Edit | View only (coverage details) |
| Preferences | View/Edit | View only | No access |
| Payment methods | View/Edit | View only | No access |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] What customer data exists in Commerce today? Can we see sample fields?
- [ ] What customer data exists in Dynamics? How does it differ from Commerce?
- [ ] How do customers update their contact information today?
- [ ] Can customers manage multiple properties today? How?
- [ ] What validation is required for new customer registration (non-native)?
- [ ] How do you verify a customer is who they say they are?

**Session 4 (Integration):**
- [ ] Can customer data be synced from Commerce/Dynamics via API?
- [ ] Real-time or batch sync?
- [ ] What's the master source of truth for customer data?
- [ ] What happens when customer data conflicts between systems?

---

### 2. **SERVICE REQUESTS / CLAIMS**

#### Data Points to Collect:

- **Request Identity:**
  - Service request ID (system-generated)
  - Created date/time
  - Status (requested, assigned, en route, on-site, in progress, completed, cancelled)
  - Priority (routine, urgent, emergency)

- **Customer Information:**
  - Customer ID (link to customer entity)
  - Property address (if different from customer primary)
  - Contact phone (for this service)

- **Service Details:**
  - Service type category (HVAC, plumbing, electrical, appliance, other)
  - Specific problem/issue (customer description)
  - Problem category (dropdown selection)
  - Photos uploaded by customer
  - Related appliance/system (link to home inventory, if available)

- **Coverage/Payment:**
  - Request type (HPP covered, ad-hoc service)
  - HPP plan ID (if covered)
  - Coverage status (covered, not covered, partially covered)
  - Coverage determination (who decided, when, why)
  - Service price (for ad-hoc services)
  - Payment status (pending, paid, refund)

- **Scheduling:**
  - Requested service date
  - Requested time window
  - Confirmed appointment date/time
  - Estimated service duration

- **Contractor Assignment:**
  - Contractor ID (link to contractor entity)
  - Assignment date/time
  - Assignment method (auto-match, manual override)
  - Contractor acceptance date/time
  - Contractor ETA

- **Service Execution:**
  - Contractor arrival time (actual)
  - Service start time
  - Service completion time
  - Services performed (contractor description)
  - Parts used
  - Before/after photos (contractor upload)
  - Additional work recommended

- **Completion:**
  - Completion notes
  - Customer signature (if required)
  - Customer rating (1-5 stars)
  - Customer review/comments
  - Issue resolved (yes/no)
  - Follow-up required (yes/no)

- **Communication Log:**
  - All messages between customer and contractor
  - All messages between customer and admin
  - All status change notifications
  - Timestamps for each communication

#### Current State:
- **Native customers:** Service requests exist in Dynamics (and maybe Commerce for billing)
- **Non-native customers:** No system exists - need to build
- **Process:** Call center creates service requests manually today

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **CREATE** service request | ✅ Create (own requests) | ✅ Create (on behalf of customer) | ❌ Cannot create |
| **READ** request details | View own requests only | View all requests | View assigned requests only |
| Problem description/photos | View/Edit (before assigned) | View all | View (after assigned) |
| Status | View only | View/Edit (can change status) | View/Edit (update status during service) |
| Contractor assignment | View only | View/Edit (can reassign) | View (can decline) |
| Appointment time | View/Edit (can reschedule) | View/Edit | View/Edit (if customer requests change) |
| Service completion details | View only | View all | Create/Edit (fill out completion form) |
| Customer rating/review | Create (after completion) | View all | View (for own services) |
| **UPDATE** request | Limited (reschedule, cancel) | Full edit capability | Limited (status, completion) |
| **DELETE**/Cancel request | Can cancel (before assigned) | Can cancel anytime | Cannot delete |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] Walk through 3-5 real service requests step-by-step (anonymized)
- [ ] What fields does call center collect today when customer calls?
- [ ] How is service request created in system? (Dynamics, Commerce, both?)
- [ ] Can customers reschedule or cancel requests today? How?
- [ ] What happens to service request data after completion? Archived? How long stored?
- [ ] Can customers see their service history? How far back?

**Session 2 (Admin Discovery):**
- [ ] What visibility do admins need into active service requests?
- [ ] Can admins edit customer-created service requests?
- [ ] What actions can admins take? (reassign contractor, change priority, cancel?)
- [ ] What triggers admin intervention? (no contractor accepts, customer complaint, etc.)
- [ ] What reports do admins run on service requests? (volume, completion rate, etc.)

**Session 3 (Contractor Discovery):**
- [ ] How does contractor receive service request today?
- [ ] What information does contractor see about service request?
- [ ] Can contractor edit service request details? (problem description, photos?)
- [ ] What completion information is contractor required to enter?
- [ ] How long does contractor have access to service request data after completion?

**Session 4 (Integration):**
- [ ] Where is service request data stored today? (Dynamics primary?)
- [ ] If customer books via app, does it create record in Dynamics?
- [ ] Real-time creation or batch sync?
- [ ] What's the data flow from app → backend → Dynamics → Contractor Portal?

---

### 3. **HOME INVENTORY**

#### Data Points to Collect:

- **Inventory Item Identity:**
  - Item ID (system-generated)
  - Customer ID (link to customer)
  - Property address (if customer has multiple)

- **Appliance/System Information:**
  - Item type (HVAC, water heater, electrical panel, plumbing system, appliance)
  - Specific category (central AC, heat pump, tankless water heater, etc.)
  - Location in home (basement, garage, attic, kitchen, etc.)

- **Product Details:**
  - Make/manufacturer
  - Model number
  - Serial number
  - Purchase date
  - Installation date (if different)
  - Age (calculated or entered)

- **Warranty Information:**
  - Warranty provider (manufacturer, retailer, Duke HPP, other)
  - Warranty type (parts, labor, both)
  - Warranty expiration date
  - Warranty document (PDF upload)
  - Extended warranty (yes/no)

- **Maintenance:**
  - Last service date
  - Maintenance schedule (recommended frequency)
  - Next maintenance due date
  - Maintenance reminders (enabled/disabled)

- **Additional Info:**
  - Energy Star certified (yes/no)
  - Estimated replacement cost
  - Photos of item
  - Notes/comments
  - Recall status (if database integration available)

#### Current State:
- **Does NOT exist** anywhere in Duke systems
- **Need to build** completely new database

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **CREATE** inventory item | ✅ Create (own inventory) | ✅ Create (on behalf of customer) | ❌ Cannot create (future: contractor could suggest items) |
| **READ** inventory | View own inventory only | View any customer's inventory | View customer inventory (when assigned service) |
| Item details | View/Edit all fields | View all | View (to help diagnose problem) |
| Warranty info | View/Edit | View | View (to know if under warranty) |
| Service history | View (auto-populated from service requests) | View all | View (past services on this item) |
| Photos | View/Upload | View all | View/Upload (during service) |
| **UPDATE** inventory | Edit own items | Edit any customer's items | ❌ Cannot edit (future: update after service) |
| **DELETE** inventory item | Delete own items | Delete any items | ❌ Cannot delete |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] **CRITICAL:** Is home inventory mandatory or optional in MVP?
- [ ] If mandatory, what's minimum required? (just appliance type, or full details?)
- [ ] How do customers collect this information today? (manually look at appliances?)
- [ ] What's the incentive for customers to enter inventory? (gamification, service benefits?)
- [ ] Do customers know their appliance make/model/serial number without looking?
- [ ] What data entry methods should we support? (manual, barcode scan, photo + AI, import from manufacturer?)
- [ ] Should we integrate with appliance recall databases? (CPSC, manufacturer APIs?)

**Session 2 (Admin Discovery):**
- [ ] Do admins need to manage customer home inventory?
- [ ] What use cases require admin to view/edit inventory?
- [ ] Should admins be able to bulk import inventory? (e.g., new construction, partnerships with builders?)

**Session 3 (Contractor Discovery):**
- [ ] Should contractors see customer's home inventory before/during service?
- [ ] Can contractors add items to inventory during service? (e.g., "I noticed you have a water heater I didn't see in your inventory")
- [ ] Should contractors update inventory after service? (new parts installed, system replaced?)

**Session 4 (Integration):**
- [ ] Integration with manufacturer warranty databases (if available)?
- [ ] Integration with recall databases (CPSC)?
- [ ] Integration with IoT/smart home devices (future)?

---

### 4. **CONTRACTORS**

#### Data Points to Collect:

- **Contractor Identity:**
  - Contractor ID (system-generated)
  - Company name
  - Business license number
  - Tax ID (for invoicing/payments)

- **Contact Information:**
  - Primary contact name
  - Email address
  - Phone number (office, mobile)
  - Address (business location)

- **Service Details:**
  - Trade specializations (HVAC, plumbing, electrical, appliance, multi-trade)
  - Specific services offered (list)
  - Service area (zip codes, cities, or radius from location)
  - Service area type (Duke territory, P&G territory, both)

- **Credentials & Compliance:**
  - License numbers (by trade type)
  - License expiration dates
  - Insurance certificate (liability, workers comp)
  - Insurance expiration dates
  - Background check status
  - Background check date
  - Certifications (EPA, manufacturer, etc.)

- **Contractor Type:**
  - Duke-managed contractor
  - P&G internal contractor (employee)
  - Contractor tier (primary, secondary, tertiary)

- **Availability:**
  - Work schedule (days/hours available)
  - Blocked-out dates (vacation, holidays)
  - Maximum jobs per day
  - Current workload (active jobs)

- **Performance Metrics:**
  - Total jobs completed
  - Jobs completed on-time (%)
  - Average customer rating (calculated from customer reviews)
  - Number of reviews
  - Acceptance rate (% of assigned jobs accepted)
  - Cancellation rate (% of accepted jobs cancelled)
  - Response time (average time to accept/decline job)

- **Pricing (if applicable):**
  - Hourly rate
  - Service-specific rates
  - Travel fee
  - Emergency service multiplier

- **Payment:**
  - Payment method (Duke pays contractor)
  - Payment schedule (weekly, bi-weekly, monthly)
  - Outstanding invoices

#### Current State:
- **Contractor data exists** in Dynamics and/or Contractor Engagement Portal
- **150 contractors** across Duke service area (from Meeting1)
- **P&G contractors are internal employees** (different system?)

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **CREATE** contractor | ❌ No access | ✅ Create new contractor | ❌ Cannot create (self-register future feature?) |
| **READ** contractor list | View limited info (when booking service or viewing assigned contractor) | View all contractors | View own profile only |
| Contractor profile | View: name, photo, rating, reviews | View: all fields | View/Edit: own profile |
| Specializations | View (to choose contractor if feature enabled) | View/Edit | View/Edit (own specializations) |
| Service area | View (to see if contractor serves their zip code) | View/Edit | View/Edit (own service area) |
| Availability | View (if customer can choose time window) | View/Edit | View/Edit (own availability) |
| Performance metrics | View: rating, # reviews | View: all metrics | View: own metrics |
| Credentials | ❌ No access | View/Edit (required for compliance) | View only (upload docs) |
| Pricing | ❌ No access (future: might see in ad-hoc booking) | View/Edit | View only (set by Duke) |
| **UPDATE** contractor | ❌ No access | Edit all fields | Edit limited fields (contact, availability) |
| **DELETE** contractor | ❌ No access | Deactivate contractor | ❌ Cannot delete |

#### Discovery Questions for Workshops:

**Session 2 (Admin Discovery):**
- [ ] Who manages contractor records today? (Operations team, specific role?)
- [ ] How often does contractor information change? (new contractors, updated licenses, etc.)
- [ ] What's the onboarding process for new contractors?
- [ ] What compliance checks are required before contractor can start working?
- [ ] How do admins track contractor performance? (manual reports, automated dashboards?)
- [ ] Can admins remove/deactivate contractors? What triggers that?

**Session 3 (Contractor Discovery):**
- [ ] Can contractors update their own profile? (contact info, availability, specializations?)
- [ ] How do contractors communicate availability today?
- [ ] Do contractors block out vacation days in a system?
- [ ] Can contractors see their performance metrics? (ratings, acceptance rate, etc.)
- [ ] Do contractors want to see their own analytics? (jobs completed, revenue, etc.)

**Session 4 (Integration):**
- [ ] Where is contractor data stored today? (Dynamics? Contractor Portal? Both?)
- [ ] How does contractor data sync between systems?
- [ ] Can we retrieve contractor list via API for matching algorithm?
- [ ] Real-time availability check or assume availability based on schedule?

---

### 5. **HPP PLANS (Home Protection Plans)**

#### Data Points to Collect:

- **Plan Identity:**
  - Plan ID (system-generated)
  - Plan name (e.g., "Water Heater Repair Plan")
  - Plan code/SKU

- **Plan Details:**
  - Category (HVAC, water heater, electrical, plumbing, appliance, bundled)
  - Description (what's covered)
  - Coverage details (repair, replacement, both)
  - Coverage limits ($, # service calls per year)
  - Exclusions (what's NOT covered)

- **Pricing:**
  - Monthly fee
  - One-time enrollment fee (if any)
  - Regional pricing variations (if any)

- **Availability:**
  - Available to native customers only or also non-native?
  - Geographic availability (states, territories)
  - Active status (active, discontinued, coming soon)

- **Customer Enrollment:**
  - Customer ID (link)
  - Plan ID (link)
  - Enrollment date
  - Plan status (active, cancelled, expired)
  - Renewal date
  - Cancellation date (if cancelled)
  - Cancellation reason

#### Current State:
- **HPP plans exist** in Commerce (Duke) and Dynamics (P&G)
- **300K+ plans** for water heater and home wiring alone (from Meeting1)
- **Customer enrollment data** exists in same systems

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **READ** plan list | View all available plans | View all plans (including inactive) | View plan details (when assigned service to determine coverage) |
| Plan details | View: description, coverage, price | View/Edit all fields | View: coverage details only |
| Customer's active plans | View own enrolled plans | View any customer's plans | View customer's plans (when assigned service) |
| **ENROLL** in plan | ✅ Enroll in available plans (future feature) | Enroll customer in plan (on behalf of) | ❌ No access |
| **UPDATE** enrollment | Limited (maybe can cancel via app) | Edit/cancel customer enrollment | ❌ No access |
| **CREATE** new plan | ❌ No access | ✅ Create new plan (product team) | ❌ No access |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] Can customers enroll in HPP plans via app in MVP? Or just manage existing?
- [ ] What information do customers need to see about their plans?
- [ ] Can customers upgrade/downgrade plans?
- [ ] Can customers cancel plans? (self-service or require call?)
- [ ] Do customers understand what their plans cover? (education opportunity)

**Session 2 (Admin Discovery):**
- [ ] Who creates/manages HPP plan catalog? (product team, marketing?)
- [ ] How often do plan details change? (rarely, quarterly, annually?)
- [ ] Do admins need to create new plans in app? Or plans managed in Commerce/Dynamics?
- [ ] Can admins enroll customers in plans manually?
- [ ] What reports do admins run on plan enrollment? (adoption rates, revenue, etc.)

**Session 4 (Integration):**
- [ ] Where is HPP plan data stored? (Commerce, Dynamics, both?)
- [ ] Can we retrieve plan catalog via API?
- [ ] Can we check if customer is enrolled in specific plan via API? (critical for coverage check)
- [ ] Read-only or can app create new enrollments?

---

### 6. **AD-HOC SERVICES (Product Catalog)**

#### Data Points to Collect:

- **Service Identity:**
  - Service ID (system-generated)
  - Service name (e.g., "HVAC Tune-Up")
  - Service code/SKU

- **Service Details:**
  - Category (HVAC, plumbing, electrical, appliance, other)
  - Description (what's included)
  - Estimated duration
  - Prerequisites (e.g., requires home assessment first)

- **Pricing:**
  - Price type (fixed, quote-based, hourly)
  - Base price
  - Regional price variations (if any)
  - Seasonal pricing (if any)

- **Availability:**
  - Available to (native customers, non-native, both)
  - Geographic availability (zip codes, cities, states)
  - Seasonal availability (e.g., snow removal winter only)
  - Active status (active, inactive, coming soon)

- **Service Requirements:**
  - Required trade (HVAC specialist, plumber, electrician, etc.)
  - Required contractor certifications (if any)
  - Parts/materials included or additional?

#### Current State:
- **Does NOT exist** - ad-hoc service catalog needs to be built
- **Pricing "still in development"** (from Meeting1:45:58)

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **READ** service catalog | View all available services (filtered by zip code) | View all services (including inactive) | View services (to know what they're assigned) |
| Service details | View: name, description, price | View/Edit all fields | View: service description, what's expected |
| **BOOK** service | ✅ Book available services | Book service on behalf of customer | ❌ Cannot book (receives assignment) |
| **CREATE** new service | ❌ No access | ✅ Create new service (product team) | ❌ No access (future: might suggest new services) |
| **UPDATE** service | ❌ No access | Edit service details, pricing | ❌ No access |
| **DELETE** service | ❌ No access | Deactivate service | ❌ No access |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] How do customers browse/search for ad-hoc services?
- [ ] Do customers understand the difference between HPP covered vs ad-hoc?
- [ ] What information do customers need to see before booking ad-hoc service? (price, duration, what's included?)
- [ ] Can customers get quotes for custom services? Or only fixed-price services in catalog?

**Session 2 (Admin Discovery):**
- [ ] **CRITICAL:** Who sets pricing for ad-hoc services?
- [ ] Who approves new services being added to catalog?
- [ ] How often will catalog be updated? (weekly, monthly, quarterly?)
- [ ] What reports do admins need on ad-hoc services? (bookings, revenue, popular services?)
- [ ] Can admins create promotional pricing? (discounts, bundles?)

**Session 3 (Contractor Discovery):**
- [ ] Do different contractors charge different prices for same service?
- [ ] Or is pricing standardized across all contractors?
- [ ] Can contractors see ad-hoc service pricing?
- [ ] Do contractors need to accept pricing before accepting job?

**Session 4 (Integration):**
- [ ] Where will ad-hoc service catalog be stored? (new app database)
- [ ] Does it need to sync with any Duke systems?
- [ ] How is pricing managed? (in app admin portal or external system?)

---

### 7. **DIY CONTENT (Knowledge Base)**

#### Data Points to Collect:

- **Content Identity:**
  - Content ID (system-generated)
  - Title
  - Content type (article, video, PDF, step-by-step wizard, FAQ)

- **Content Details:**
  - Body/content (rich text, HTML, markdown)
  - Video URL (if video)
  - PDF file (if document)
  - Duration (for videos)
  - Reading time estimate (for articles)

- **Organization:**
  - Primary category (HVAC, plumbing, electrical, appliances, general home maintenance)
  - Sub-category (troubleshooting, maintenance, safety, how-to)
  - Tags (keywords for search)
  - Related appliance types (link to home inventory categories)

- **Publishing:**
  - Author (who created)
  - Created date
  - Published date
  - Last updated date
  - Status (draft, published, archived)

- **Media:**
  - Featured image
  - Inline images
  - Video embeds
  - Downloadable files (PDFs, checklists)

- **Metadata:**
  - SEO title/description (if public-facing)
  - Search keywords
  - Difficulty level (beginner, intermediate, advanced)
  - Safety warning (yes/no)
  - When to call professional (guidance)

- **Analytics:**
  - View count
  - Average time on page
  - Helpfulness ratings (thumbs up/down or 1-5 stars)
  - Number of ratings
  - Customer comments/feedback

#### Current State:
- **Does NOT exist** - DIY content needs to be created
- **Content creation "in parallel"** (from Meeting1:48:28)

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **READ** content | View all published content | View all content (including drafts) | View published content (might share with customers) |
| Content details | View: title, body, media | View/Edit all fields | View only |
| Search content | Full-text search | Full-text search + filters | Limited search |
| Rate/review content | ✅ Rate helpful/not helpful, leave feedback | View ratings/feedback | ❌ Cannot rate (future: might contribute content) |
| Bookmark content | Save favorites | ❌ No bookmarking | ❌ No bookmarking |
| **CREATE** content | ❌ No access | ✅ Create new content (content team) | ❌ No access (future: might contribute SME content) |
| **UPDATE** content | ❌ No access | Edit/update content | ❌ No access |
| **DELETE** content | ❌ No access | Archive content | ❌ No access |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] What problems do customers try to solve before calling for service?
- [ ] What content would prevent unnecessary service calls?
- [ ] How do customers prefer to consume content? (articles, videos, both?)
- [ ] Do customers want interactive troubleshooting wizards? ("Answer these questions to diagnose...")

**Session 2 (Admin Discovery):**
- [ ] **CRITICAL:** Who creates DIY content? (internal marketing, customer service, contractors, third-party?)
- [ ] What's the content approval workflow? (legal review, SME review, both?)
- [ ] How much content needs to exist at launch? (10 articles, 50, 100?)
- [ ] What's the priority content? (top 10 customer problems)
- [ ] How is content effectiveness measured? (views, reduced service calls, CSAT?)
- [ ] Who maintains/updates content? (same team or different?)

**Session 4 (Integration):**
- [ ] CMS decision (custom vs third-party) made in Session 2
- [ ] Where is content stored? (app database, separate CMS, CDN?)
- [ ] Content versioning needed?
- [ ] Multilingual content? (Spanish translation workflow?)

---

### 8. **PAYMENTS & INVOICES**

#### Data Points to Collect:

- **Payment Identity:**
  - Payment ID (system-generated)
  - Transaction ID (from payment processor)

- **Payment Details:**
  - Service request ID (link to what was paid for)
  - Customer ID (link)
  - Amount
  - Currency (USD)
  - Payment date/time

- **Payment Method:**
  - Payment type (utility bill, credit card, ACH, cash, check)
  - Payment processor (SpeedPay, Stripe, etc.)
  - For credit card: last 4 digits, expiration date
  - For ACH: account type, last 4 digits

- **Payment Status:**
  - Status (pending, authorized, captured, failed, refunded, disputed)
  - Authorization code
  - Failure reason (if failed)

- **Invoice Information:**
  - Invoice number
  - Invoice date
  - Due date
  - Line items (services performed, parts used, labor)
  - Subtotal, tax, total
  - Payment status (unpaid, partial, paid in full)

- **For HPP Services:**
  - Plan ID (covered under HPP)
  - No payment required from customer (billed via monthly plan fee)

- **For Ad-Hoc Services:**
  - Service price
  - Payment timing (before service, after service, on-site)

#### Current State:
- **Native customers:** Payments via utility bill (existing process in Commerce)
- **Non-native customers:** Need payment processing (SpeedPay integration proposed)
- **Phase 1:** Contractor collects payment on-site for ad-hoc services (from Meeting1:44:26)

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **READ** payment history | View own payments/invoices | View all customer payments | View payments for own services |
| Payment methods | View/Edit saved payment methods | View customer payment methods | ❌ No access (Phase 1: collects on-site) |
| Invoices | View/download own invoices | View/generate invoices for any customer | View invoice for own completed work |
| **MAKE** payment | ✅ Pay for ad-hoc services | Process payment on behalf of customer | Collect payment on-site (Phase 1) |
| **REFUND** payment | Request refund | Process refund | ❌ Cannot refund |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] For native customers: Do they see HPP plan fees on utility bill? Itemized?
- [ ] For non-native customers: What payment methods should be supported? (credit card, ACH, Apple Pay, Google Pay?)
- [ ] When do customers pay for ad-hoc services? (book → pay → service, or service → pay?)
- [ ] Do customers want to save payment methods for future use?
- [ ] Can customers see payment history? (for ad-hoc services)

**Session 2 (Admin Discovery):**
- [ ] Who manages invoicing and payments?
- [ ] What happens with failed payments?
- [ ] What's the refund process? (who approves, timeline?)
- [ ] What payment reports do admins need? (revenue by service type, by region, etc.)

**Session 3 (Contractor Discovery):**
- [ ] **Phase 1:** What payment methods can contractors accept on-site? (cash, credit card via Square, check?)
- [ ] How does contractor report payment to Duke?
- [ ] Does Duke take commission on ad-hoc services? (if yes, how calculated?)
- [ ] **Future state:** How should app-based payment work? (customer pays Duke, Duke pays contractor?)

**Session 4 (Integration):**
- [ ] SpeedPay integration: what APIs are available?
- [ ] PCI-DSS compliance requirements?
- [ ] Tokenization for saved payment methods?
- [ ] Payment processing timeline (setup, testing)?

---

### 9. **NOTIFICATIONS & COMMUNICATIONS**

#### Data Points to Collect:

- **Notification Identity:**
  - Notification ID (system-generated)
  - Customer ID (recipient)
  - Created date/time

- **Notification Details:**
  - Type (transactional, promotional, system alert)
  - Category (service update, appointment reminder, marketing, account)
  - Title/subject
  - Message body
  - Priority (low, normal, high, urgent)

- **Delivery:**
  - Channels (push notification, email, SMS, in-app)
  - Sent date/time
  - Delivery status (sent, delivered, failed, bounced)
  - Read status (read, unread)
  - Read date/time

- **Related Entity:**
  - Service request ID (if related to service)
  - Content ID (if related to DIY content)
  - Link/CTA (call-to-action button)

- **Customer Preferences:**
  - Notification preferences by category
  - Preferred channels (email, SMS, push, all, none)
  - Frequency preferences (real-time, daily digest, weekly)
  - Opt-in/opt-out status

#### Current State:
- **Native customers:** Likely receive email confirmations today (from Commerce/Dynamics?)
- **Notification system:** May not exist in unified way - need to build

#### Role-Based Access:

| Data Point | Customer (CRUD) | Admin (CRUD) | Contractor (CRUD) |
|------------|----------------|--------------|------------------|
| **READ** notifications | View own notifications | View all notifications sent | View own notifications |
| Notification history | View past notifications | View all sent notifications + analytics | View own notification history |
| Notification preferences | View/Edit own preferences | View customer preferences | View/Edit own preferences |
| **SEND** notification | ❌ Cannot send (receives only) | Send notifications to customers (announcements, alerts) | Send notifications to customers (in context of service) |

#### Discovery Questions for Workshops:

**Session 1 (Customer Discovery):**
- [ ] What notifications do customers want to receive?
  - Service request confirmed
  - Contractor assigned
  - Contractor en route
  - Service completed
  - Maintenance reminders
  - New content published
  - Promotional offers
- [ ] What channels do customers prefer? (push, email, SMS, in-app?)
- [ ] How much control do customers want over notifications? (all or nothing, or granular by type?)

**Session 2 (Admin Discovery):**
- [ ] Can admins send announcements to customers? (all customers, filtered by geography, by plan type?)
- [ ] What notification templates need to exist?
- [ ] What notification analytics do admins need? (open rates, click rates, opt-out rates?)

**Session 3 (Contractor Discovery):**
- [ ] What notifications do contractors need?
  - New job assignment
  - Job accepted by another contractor (if multi-contractor offer)
  - Customer cancelled appointment
  - Customer messages
- [ ] What channels do contractors prefer? (push, email, SMS?)

---

### 10. **ANALYTICS & REPORTING DATA**

#### Data Points to Collect:

- **User Activity:**
  - Login events
  - Page views
  - Feature usage (which features are used most)
  - Session duration
  - User flow (navigation patterns)

- **Service Metrics:**
  - Service request volume (by day, week, month)
  - Service request by type (HPP vs ad-hoc)
  - Service request by category (HVAC, plumbing, etc.)
  - Service request by region
  - Average time to contractor assignment
  - Average time to service completion
  - Service completion rate
  - Service cancellation rate

- **Customer Metrics:**
  - New registrations (native vs non-native)
  - Active users (DAU, MAU)
  - User retention rate
  - Churn rate
  - Home inventory adoption rate
  - DIY content engagement

- **Contractor Metrics:**
  - Contractor utilization (jobs per contractor)
  - Contractor acceptance rate
  - Contractor cancellation rate
  - Contractor performance (on-time rate, ratings)

- **Revenue Metrics:**
  - Ad-hoc service revenue
  - Revenue by service type
  - Revenue by region
  - Average transaction value

- **Customer Satisfaction:**
  - NPS score
  - CSAT score
  - Customer ratings distribution
  - Customer reviews (sentiment analysis?)

#### Discovery Questions for Workshops:

**Session 2 (Admin Discovery):**
- [ ] What metrics are most important to track?
- [ ] Who needs access to analytics? (operations, executives, marketing, product?)
- [ ] Real-time dashboards or daily reports?
- [ ] What decisions will be made based on analytics data?
- [ ] Are there regulatory reporting requirements?

---

## Data Entity Relationship Map

```
CUSTOMER
  ├─ has many → SERVICE REQUESTS
  ├─ has many → HOME INVENTORY ITEMS
  ├─ enrolled in many → HPP PLANS
  ├─ has many → PAYMENT METHODS
  ├─ has many → NOTIFICATIONS
  └─ rates/reviews → CONTRACTORS

SERVICE REQUEST
  ├─ belongs to → CUSTOMER
  ├─ assigned to → CONTRACTOR
  ├─ related to → HOME INVENTORY ITEM (optional)
  ├─ covered by → HPP PLAN (if applicable)
  ├─ related to → AD-HOC SERVICE (if applicable)
  ├─ has → PAYMENT/INVOICE (if ad-hoc)
  └─ generates → NOTIFICATIONS

CONTRACTOR
  ├─ assigned to many → SERVICE REQUESTS
  ├─ has many → PERFORMANCE METRICS
  └─ receives → NOTIFICATIONS

HPP PLAN
  ├─ has many → CUSTOMERS enrolled
  └─ covers → SERVICE REQUEST TYPES

AD-HOC SERVICE
  ├─ can be booked as → SERVICE REQUEST
  └─ has → PRICING

HOME INVENTORY ITEM
  ├─ belongs to → CUSTOMER
  ├─ related to many → SERVICE REQUESTS
  └─ may link to → WARRANTY DATA

DIY CONTENT
  ├─ viewed by → CUSTOMERS
  └─ may be related to → HOME INVENTORY CATEGORIES

PAYMENT/INVOICE
  ├─ belongs to → CUSTOMER
  ├─ related to → SERVICE REQUEST
  └─ processed by → PAYMENT PROCESSOR

NOTIFICATION
  ├─ sent to → CUSTOMER or CONTRACTOR or ADMIN
  └─ may relate to → SERVICE REQUEST or other entities
```

---

## Workshop Integration

This document should be used during workshops to:

1. **Validate data points:** For each entity, ask "Is this data point needed? Is it accurate?"
2. **Discover current processes:** "How is this data managed today?"
3. **Define workflows:** "Who creates/reads/updates/deletes this data?"
4. **Identify integrations:** "Where does this data live in existing systems?"
5. **Design data models:** "What's the database schema for this entity?"
6. **Create wireframes:** "How is this data displayed to each user role?"

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 5, 2025
**Status:** Ready for workshop use
