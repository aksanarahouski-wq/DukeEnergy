# Duke Energy Residential Solutions Home Services App
## MVP Scope & Assumptions - Executive Summary

**Document Purpose:** Comprehensive MVP scope definition for all three system components
**Date:** November 2025
**Project Timeline:** 44 weeks to MVP launch
**Target Go-Live:** Q2-Q3 2026

---

## EXECUTIVE OVERVIEW

The Duke Energy Residential Solutions Home Services App is a comprehensive three-component platform designed to transform home protection plan service delivery from a phone-only process to an "Uber of home services" digital experience. The platform consists of a Customer Mobile/Web App, Admin Backend Portal, and Contractor Management System.

### Business Objectives

**Revenue Goals:**
- Generate $25M in new ad-hoc service revenue within 12 months
- Acquire 250K non-native customers within 24 months
- Increase customer engagement (target: 70+ NPS score)

**Operational Efficiency Goals:**
- Reduce call center volume by 40%
- Automate scheduling to reduce coordination calls by 80%
- Reduce service request time from 15 minutes (phone) to <3 minutes (app)

**Customer Base:**
- 800K+ existing HPP customers (immediate user base)
- Existing Duke/P&G utility customers without HPPs (acquisition target)
- Non-native customers outside Duke territory (expansion market)

### Strategic Approach

The MVP prioritizes customer-facing features that drive revenue and engagement while accepting manual back-office processes where necessary. The approach balances serving existing warranty customers with building capabilities to acquire new customer segments through transparent, flat-rate pricing for ad-hoc services.

---

## CUSTOMER APP MVP SCOPE

### 1. Customer Segmentation & Support

**Three Primary Customer Types (All Supported in MVP):**

**Segment 1: Existing Duke/P&G Customers WITH Home Protection Plans**
- Current utility customers with active HPP subscriptions (average 1.7 plans per customer)
- Primary pain point: phone-only service request process
- MVP needs: Service booking for covered repairs, plan management, ad-hoc services, home inventory

**Segment 2: Existing Duke/P&G Customers WITHOUT Home Protection Plans**
- Utility customers interested in ad-hoc services or future plan enrollment
- Acquisition target for both HPPs and ad-hoc revenue
- MVP needs: Transparent pricing, easy enrollment, maintenance reminders

**Segment 3: Non-Native Customers (Outside Duke/P&G Territory)**
- Homeowners anywhere in U.S. who are not Duke/Piedmont utility customers
- Critical for business expansion and white-label platform viability
- MVP needs: All ad-hoc service booking, home inventory, transparent pricing
- Cannot access utility rebates/incentives (reserved for utility customers)

### 2. Core MVP Features

#### Registration & Onboarding ✅
- Profile creation required (separate from utility accounts)
- Guest access very limited (browsing only, no booking)
- Address entry minimum requirement (enables public data pre-fill)
- Profile validation API links Duke/P&G customers to existing HPP plans
- **Multi-property support**: Customers with multiple premises can manage all properties in single profile

#### Home Protection Plan Management ✅
- View all active HPPs linked to customer profile
- Enroll in new plans (full workflow with payment method selection)
- Upgrade/downgrade existing plans
- Self-service cancellation (compliance requirement)
- Display coverage terms, pricing, billing method
- Support for multiple plans per property

#### Home Inventory/Profile Building ✅
- Manual entry of appliances, systems, equipment (make, model, serial, age)
- Barcode scanning for auto-populate data
- Pre-fill home characteristics from address (square footage, year built, property type)
- Progressive profiling (build inventory over time)
- Gamification and loyalty rewards tied to profile completion
- **Contractor-enhanced data**: Technicians can add/update inventory during service visits
- Maintenance schedules auto-generated based on inventory
- Recall checking against CPSC database

#### Service Booking - HPP Covered Services ✅
- Symptom-based intake (customer describes issue, not technical diagnosis)
- Coverage check (app determines eligibility under existing plan)
- Inventory integration (pre-populate service request if item in profile)

**Contractor Assignment (Trade + Zip Code → Primary Contractor):**
- Automated matching based on trade + customer zip code
- Customer sees pre-assigned contractor: "Your contractor: ABC Plumbing"
- NO in-app contractor selection in MVP
- Request alternative via phone call to admin (not in-app feature)

**Date/Time Selection:**
- Customer chooses from available windows based on static availability buffers
- Lead times vary by trade:
  - HVAC/Water Heater: 1-2 business days
  - Plumbing: 3-5 business days
  - Electrical (non-emergency): 5-6 business days
  - Appliance: 2-3 business days
- Time windows: Half-day slots (8am-12pm, 1pm-5pm most common)

**Booking Confirmation:**
- Status: "Pending Confirmation"
- Admin manually contacts contractor within 1 hour (email/phone)
- Contractor responds within 24 hours
- Admin updates app: "Confirmed - ABC Plumbing - Thursday 9-12am"
- No payment required (covered services $0 customer cost)

#### Service Booking - Ad-Hoc (Non-Covered) Services ✅
- Browse/search service catalog with transparent, upfront pricing
- Flat-rate pricing for preventative maintenance (e.g., "$99 HVAC cleaning check")
- Variable pricing for some services (e.g., "$120-$190 ceiling fan installation")
- Available to all customer types including non-natives
- Discounted rates (Duke may subsidize to drive engagement)

**Contractor Assignment for Ad-Hoc (Same as Warranty for MVP):**
- Primary contractor assigned based on trade + zip code
- Customer experience: "Your contractor: ABC Plumbing - $99"
- NO contractor marketplace in MVP (no choosing from multiple options)
- NO ratings displayed in MVP

**Payment (Contractor Collects On-Site for MVP):**
- Contractor collects payment at service completion
- Methods: Cash, check, credit card via contractor's reader
- App displays: "Total cost: $99. Payment collected by ABC Plumbing at service completion."
- In-app payment processing deferred to Phase 2

#### Communication & Notifications ✅
- Multi-channel delivery: Push notifications, SMS, email, in-app notification center
- Customer selects preferred communication channels

**MVP Service Request Status Flow (Manual Admin Updates):**
1. **Booking Confirmation** (Immediate): "Pending Confirmation" status
2. **Appointment Confirmed** (Within 24-48 hours): "Confirmed - [Contractor] - [Date] [Time]"
3. **Appointment Changed** (If needed): Updated date/time with notification
4. **Service Completed** (After service): "Completed" status, external survey sent

**MVP Status Limitations (No FSM Integration):**
- NO intermediate statuses: No "Dispatched", "En Route", "On-Site", "In Progress"
- Admin manually updates statuses based on contractor communication
- Contractors send their own "on my way" texts (~70% do this already)

#### Maintenance Reminders ✅
- Inventory-based reminders (auto-generate maintenance schedules)
- Default reminder sets for new homeowners
- Custom reminders (user-created)
- Reminder opt-out/snooze capability
- Each reminder offers "Book Service" button to schedule professional service
- Age-based recommendations for aging equipment
- Recall alerts from CPSC

#### Loyalty/Rewards/Gamification ✅
- Profile completion score (percentage indicator)
- Loyalty points for completing profile, scheduling maintenance, app engagement
- Point redemption for dollar credits on future services
- Home health scorecard (risk assessment based on appliance ages)
- Badge system (Fitbit-style achievements)
- Value tracking (cumulative savings display)

#### Service History & Records ✅
- Exportable service log (all services tied to appliances/systems)
- Service details: Date, contractor, technician, work performed, parts, cost
- Invoice/receipt storage (PDFs in app)
- Warranty tracking (manufacturer warranties)
- Home sale use case (export history for home buyers)

#### Customer Feedback/Reviews ⚠️ EXTERNAL PROCESS ONLY
- Survey sent after service completion via external vendor (email/SMS)
- Data collected but NOT displayed to customers in MVP
- NOT collected in-app for MVP
- Ratings used internally by Duke for contractor performance evaluation
- In-app ratings deferred to Phase 2

#### Emergency Service Handling 🚨 NOT IN APP - PHONE ONLY
- Emergency services NOT booked through app
- App asks qualifying questions to detect emergencies
- Emergency detected → Route to phone call: "Please call us immediately at 1-800-XXX-XXXX"
- Safety alerts for life-threatening situations (gas leaks, electrical sparking)
- CSR handles emergency coordination directly with contractors

**Examples of Emergencies:**
- No heat in winter (freezing temps)
- Gas leak smell
- Electrical sparking/smoking
- Active water flooding
- Sewage backup

### 3. Contractor Matching Algorithm

**Network Overview:**
- 125-140 contractors across 4-5 states (NC, SC, FL, OH, IN)
- 80% primary contractors (first assigned, receive jobs first)
- 20% backup contractors (overflow when primary unavailable)
- 99-100% coverage for HVAC, Plumbing, Electrical, Water Heater
- Most contractors offer 2-3 trades (multi-trade support)

**Matching Logic (Trade + Zip Code + Primary/Secondary):**
1. System identifies trade needed (HVAC, plumbing, electrical, appliance, water heater)
2. Exact zip code match (NOT radius-based)
3. Primary contractor auto-assigned for that trade + zip code
4. Customer sees pre-assigned contractor
5. Request alternative triggers phone call to admin

**Availability & Lead Times (Static Buffer Approach):**
- Contractors provide availability rules (e.g., "Mon-Fri 8-5, 3-day buffer")
- No real-time calendar checking (FSM tool required for that - Phase 2)
- Lead times trade-specific (HVAC 1-2 days, Electrical 5-6 days, etc.)

**Contractor Acceptance Process:**
- Target: 90-95% acceptance rate (SLA contracts)
- Customer books → Admin contacts contractor within 1 hour
- Contractor responds within 24 hours
- If primary unavailable: Admin tries backup contractor
- Priority: Keep customer's requested time > keep specific contractor

---

## ADMIN PORTAL MVP SCOPE

### Purpose

The admin portal serves as the "middle layer" aggregating data from multiple sources (Commerce CRM for Duke customers, Dynamics for P&G customers, app database for non-native customers) into a unified administrative interface. The portal enables back-office operations to support the customer app experience while managing manual fallback processes for MVP.

### Admin User Roles

**Seven Distinct Roles:**

1. **CSR (Enrollment Center)**: Handle enrollment inquiries, manually create accounts/business partners, process failed enrollments from review queue
2. **CSR (Shop/Support)**: App account administration (password resets, unlock accounts), troubleshoot app issues
3. **Back Office Admin**: Process enrollment queues, manage customer profiles, update inventory, configure services & pricing
4. **Product Manager**: Create/edit ad-hoc service catalog, set pricing, define service scope of work, manage reminders
5. **Operations Manager** (MVP CRITICAL): Manually process service requests (contact contractors within 1 hour, update app status based on responses), reassign contractors, handle exceptions
6. **Escalation Team**: Handle customer complaints, contractor disputes, service quality issues
7. **Analyst/Reporting User**: Access dashboards, export reports, track KPIs

**Permission Levels:**
- View Only: Customer profile basic info, service request status, analytics dashboards
- Edit/Create: Customer inventory, service catalog & pricing, reminders & content, contractor configuration
- Admin/Super User: User management, system configuration, full CRUD across all entities

### Core MVP Features

#### 1. Customer Management ✅
- Customer profile CRUD (view, edit, create customer records)
- Cross-system data aggregation from Commerce, Dynamics, and App DB
- Review queue for failed enrollments
- Account administration (password resets, unlock accounts)
- Manual enrollment processing (when API doesn't exist)

#### 2. Home Inventory Management ✅
- Full CRUD on customer inventory
- Multi-source data: Customer-entered, admin-added, contractor-added
- Inventory fields: Item type, brand, model, serial number, age, location, purchase date, warranty expiration
- Use case: Admin looks up inventory during support calls to troubleshoot

#### 3. HPP Plan (Subscription) Management ✅
- View customer subscriptions (all HPP plans)
- Subscription status: Active, suspended, cancelled
- Manual enrollment support for MVP
- Sync with CRM (plans live in Commerce/Dynamics, app backend mirrors)

#### 4. Service Request Management ✅ (MAJOR MVP COMPONENT)

**Service Request Dashboard:**
- View all service requests (HPP covered + ad-hoc)
- Filter by status, date, customer, contractor, type
- Priority queue: "Pending Confirmation" requests needing immediate action
- Search by customer name, service request ID

**Service Request Statuses (MVP - Manual Updates):**
1. Pending Confirmation (customer booked, admin needs to contact contractor)
2. Confirmed (contractor accepted, appointment scheduled)
3. Rescheduled (time/date changed)
4. Completed (service finished)
5. Cancelled (cancelled by customer or contractor)

**NO FSM Integration for MVP**: No automated statuses like "Dispatched", "En Route", "On-Site", "In Progress"

**Service Request Details View:**
- Customer info, service type, service category/trade
- Problem description, related inventory item
- Assigned contractor (primary based on trade + zip code)
- Requested date/time window (customer-selected)
- Confirmed date/time (contractor-accepted, may differ)
- Status history, contractor notes, payment status
- Time since submission (SLA tracker: process within 1 hour)

**MVP Admin Workflow - Manual Service Request Processing:**

**Step 1: Customer Books Service**
- Service request created in app
- Status: "Pending Confirmation"
- Appears in admin "Pending Confirmation Queue"
- Admin receives notification

**Step 2: Admin Contacts Contractor (Within 1 Hour SLA)**
- Admin opens service request from queue
- Reviews details
- Identifies primary contractor (auto-matched by system)
- Contacts contractor via email or phone
- Provides: Customer info, service details, requested time window, payment type

**Step 3: Contractor Responds (Within 24 Hours)**
- Option A: Accept requested time
- Option B: Propose alternative time
- Option C: Decline (rare, <5% due to SLA contracts)

**Step 4: Admin Updates App Based on Response**
- If accepted: Status = "Confirmed", customer notified
- If alternative proposed: Admin calls customer to confirm OR tries backup contractor
- If declined: Admin immediately contacts backup contractor

**Step 5: Service Day - Admin Monitors**
- No real-time updates (no FSM integration)
- Admin checks CRM daily for completed services
- Admin updates app status: "Completed"
- Customer receives completion notification

**Admin Actions:**
- Manual service request creation (phone orders)
- Manual status updates based on contractor communication
- Reassign contractor (override automatic assignment)
- Add internal notes
- Cancel/reschedule appointments
- Handle exceptions (no contractor available, all at capacity, emergencies)

**Target SLAs:**
- Admin processes service request: Within 1 hour of customer submission
- Contractor responds to admin: Within 24 hours
- Admin updates app with confirmation: Within 1 hour of contractor response
- Total time to confirmation: 24-48 hours

#### 5. Ad-Hoc Service Catalog Management ✅

**CRITICAL**: Ad-hoc service catalog does NOT exist today. Must be built.

**Service Catalog Admin Functions:**
- Create new ad-hoc services (define name, category, description, scope of work)
- Set pricing (fixed price, price range, or "quote required")
- Geographic pricing (different prices by region/market)
- Scope of work definition (what's included, exclusions)
- Service availability (which zip codes/regions)
- Contractor association (which contractors offer service at negotiated rate)
- HPP plan association (map services to plans)

**MVP Ad-Hoc Services (Limited Set):**
- Start with 5-10 well-defined services with flat rate pricing
- Examples: HVAC tune-up ($99), water heater flush, air filter change
- Launch in 1-2 pilot markets (e.g., Orlando area)

**Service Fields:**
- Service name, service code/SKU, category
- Description, scope of work
- Pricing type (fixed, variable, quote-based)
- Base price, regional price overrides
- Geographic availability, contractor availability
- Status (draft, active, inactive)

#### 6. Contractor Configuration Management ✅ (MAJOR MVP COMPONENT)

**Contractor Network Overview:**
- 125-140 contractors across 4-5 states
- Primary contractors (~80%): First assigned, receive jobs first
- Backup contractors (~20%): Overflow when primary unavailable
- Multi-trade: Most contractors offer 2-3 trades with different configs per trade

**Contractor Data Model - Admin Backend:**

**Basic Information:**
- Contractor ID, name, business name
- Contact phone, email, primary contact
- Status (Active, Inactive, On Hold)
- Licensing information, insurance information
- Background check status

**Service Area Configuration (Critical for Matching Algorithm):**
- Zip code list (exact zip codes contractor serves)
- NOT radius-based (zip code specific assignment)
- Non-contiguous areas supported (Charlotte + Raleigh but not cities in between)
- Geographic coverage notes

**Trade/Specialization Configuration (Multi-Trade Support):**
Each contractor can have multiple trade configurations:
- Trade 1: HVAC - Primary for zips 28201, 28202, 28203 - Lead time 2 days - Mon-Fri 8-5
- Trade 2: Plumbing - Secondary for zips 28203, 28204 - Lead time 3 days - Tue-Thu only
- Trade 3: Electrical - Secondary for zips 28201, 28202 - Lead time 6 days - Mon/Wed/Fri only

**Primary/Secondary Designation (Per Trade + Zip Code):**
- Primary: First assigned, SLA commitment to accept 90-95% of jobs
- Secondary/Backup: Assigned when primary unavailable
- Designation can vary (primary for HVAC in one zip, secondary for Plumbing in another)
- Determined by: Negotiated contracts, capacity, pricing, performance

**Lead Time & Availability Configuration:**
- Trade-specific lead time buffers
- Static availability rules (work days, time windows, blocked dates)
- Max jobs per day (capacity limits)
- NOT real-time calendars for MVP

**Admin CRUD Operations:**
- Create new contractor (add basic info, configure trades, service areas, availability)
- Edit contractor (update info, add/remove service areas, adjust lead times, blocked dates)
- Override/exception handling (emergency override, blocked date override, capacity override)

**Contractor Data Sync Strategy (MVP):**
- Initial setup: Duke exports contractor data from CRM (CSV/JSON), Orases imports into app backend
- Ongoing maintenance: Contractor changes in CRM first, admin manually updates app backend
- Frequency: As-needed (contractor changes rare, ~1-2 per year)

**Contractor Performance Tracking (Admin View Only):**
- Jobs completed, acceptance rate, on-time arrival rate
- Customer satisfaction ratings (from external surveys)
- Average job completion time, revenue generated
- Performance does NOT factor into MVP matching algorithm

#### 7. Reminders Management ✅

**Focus on reminders** (automated maintenance calendar).

**Reminder Categories:**
- Global reminders (default for all homeowners)
- Asset-based reminders (triggered by inventory items)
- Seasonal reminders (spring/summer/fall/winter maintenance)
- Customer-created reminders

**Admin Functions:**
- Create/edit reminder templates
- Asset category mapping (tie reminders to inventory categories)
- Seasonal configuration
- Service linkage (link reminder to bookable service)

**Reminder Fields:**
- Title, description/instructions
- Frequency (monthly, quarterly, bi-annually, annually, seasonal)
- Asset category, optional service link, optional HPP plan link
- Status (active, inactive)

#### 8. Analytics & Reporting Dashboard ✅

**CRITICAL**: Full instrumentation required from MVP launch.

**Key Metrics to Track:**

**Customer Acquisition:**
- New app registrations (by customer type)
- Registration conversion rate
- Inventory completion rate

**Engagement:**
- Active users (DAU, WAU, MAU)
- Session duration, feature usage
- Customer drop-off points

**Service Requests:**
- Total service requests (HPP vs ad-hoc)
- Volume by type, region
- Time to complete service request
- Customer satisfaction ratings

**Revenue:**
- Ad-hoc service revenue
- New HPP enrollments via app
- Cancellations/churn

**Contractor Performance:**
- Jobs completed, on-time percentage
- Customer ratings, utilization rate

**Operational:**
- Call center volume reduction (target: 40%)
- Automated scheduling rate (target: 80%)
- Manual intervention rate

**Dashboard Views:**
- Operations Dashboard: Real-time service request tracking
- Executive Dashboard: High-level KPIs, trends
- Marketing Dashboard: Customer acquisition, engagement
- Product Dashboard: Feature adoption, drop-off points

**Export Capabilities:**
- Export reports to CSV, Excel, PDF
- Scheduled reports (daily, weekly, monthly)

#### 9. Communication & Notifications ✅
- Send email or SMS to customers
- Bulk notifications
- Customer communication preferences management
- Communication log/history per customer

#### 10. Escalation Management ✅
- Customer initiates escalation via app
- Ticket created in admin backend
- Escalation team receives notification, reviews ticket, calls customer back
- Escalation ticket fields: Customer info, service request ID, issue category, description, priority, status, assigned to, resolution notes

### Admin Portal Key Decisions

1. **Build a dedicated admin backend** separate from existing CRM systems to support cross-system data aggregation
2. **Manual fallback processes for MVP**: When APIs don't exist, admin queues handle enrollment and service requests manually
3. **Multi-level admin access**: Different permission levels for CSR, back office, escalation team, analytics users
4. **Ad-hoc service catalog**: New product catalog management needed (doesn't exist today)
5. **Automated maintenance reminders**: Focus on inventory-based maintenance reminders to drive engagement and service bookings
6. **Full instrumentation required**: Analytics and reporting critical from day 1 for business case validation
7. **Manual service request processing for MVP**: Admin manually contacts contractors within 1 hour, updates app status based on responses
8. **No contractor portal rebuild for MVP**: Contractors continue using existing Commerce CRM portal
9. **Contractor configuration management in admin backend**: Admin backend houses contractor data, manages matching algorithm configuration

---

## CONTRACTOR PORTAL MVP SCOPE

### The Big Decision: Admin-Only Approach for Phase 1

**MVP Decision: No Contractor Portal Changes**

Contractors will continue using existing Commerce CRM portal for Phase 1 MVP. All contractor-related functionality will be managed through the admin backend portal.

**Rationale:**
1. Focus 100% on customer app (drives revenue: $25M ad-hoc services target)
2. Existing Commerce portal is functional, contractors are familiar
3. Learn from MVP first before investing in contractor features
4. FSM tool dependency: Robust contractor mobile app requires FSM integration (not ready for Phase 1)
5. Manual admin updates acceptable for MVP
6. Phase 2 investment: Build modern contractor mobile app after FSM tool selected and customer app proven

### What Contractors Continue Using (No Changes)

**Existing Contractor Portal (Direct Access to Commerce CRM):**
- Receive job assignments
- View service request details (customer name, address, problem description)
- Schedule appointments with customers
- Update service request status (accepted, scheduled, dispatched, in-progress, completed, invoiced)
- Enter completion details (services performed, parts used, time spent)
- Submit invoices

**Communication Methods:**
- Email notification when new job assigned
- Phone calls to/from Duke back office
- Direct phone/SMS with customers (contractors have customer phone numbers)

**Their Own Systems:**
- Contractors use their own dispatch software (Service Titan, Housecall Pro, etc.)
- Contractors manage technician schedules internally
- Contractors send their own lifecycle communications (~70% provide en-route notifications)

### What Admin Backend Manages (New for App)

**Contractor Configuration (Admin Portal Features):**
- CRUD operations for contractors
- Assign trades to contractors (multi-select: HVAC, Plumbing, Electrical, etc.)
- Assign service areas (zip code list per contractor)
- Set primary/secondary designation per trade + zip code
- Configure lead time/buffer per contractor per trade
- Configure availability windows (time slots, days of week)
- View contractor performance metrics
- Override assignments for exceptions (emergencies, capacity issues)

**Service Request Status Management (Admin Portal):**
- View pending service requests from customer app
- Manually send service request to contractor (email/phone for MVP)
- Update status when contractor confirms: "Confirmed - [Contractor Name] - [Date/Time]"
- Update status when contractor completes: "Completed - [Date]"
- Handle reschedules/cancellations (update app, notify customer)

---

## KEY ASSUMPTIONS & DEPENDENCIES

### Technical Dependencies

**1. Duke Enterprise APIs**
- **Customer Validation & HPP Plan APIs**: WILL EXIST by MVP launch (confirmed)
  - Validate if customer is Duke/P&G utility customer
  - Retrieve customer HPP plan subscriptions
  - Check subscription status (active, suspended, cancelled)

- **Service Request Creation API**: MAY NOT EXIST for MVP - Manual fallback required
  - If API unavailable: Service request created in app backend, admin manually enters into CRM or processes via automated queue

- **Enrollment API**: May not exist for MVP
  - If unavailable: Admin manually processes enrollments submitted via app
  - Manual fallback: Admin creates enrollment in CRM, syncs to billing, updates app backend

**2. FSM (Field Service Management) Tool Integration**
- **Status**: Future - NOT for MVP
- **Current State**: Duke exploring FSM tools (Service Power, Service Bench)
- **For MVP**: Admin manually updates service request status
- **Future State (Phase 2)**: FSM tool provides real-time contractor GPS tracking, automated status updates, "pizza tracker" experience

**3. Payment Processing Integration**
- **MVP Approach**: Contractor collects payment on-site (cash, check, credit card via contractor's reader)
- **Phase 2**: App-based payment integration (customer pre-pays in app, Duke charges customer's card, pays contractor net of commission)
- **Payment Methods (Phase 2)**: On utility bill (Duke/P&G only), Apple Pay, Google Pay, credit/debit card, ACH

**4. Data Sync Strategy**

**Master Sources of Truth:**
- Duke customer profile: Commerce (master) → App Backend (synced)
- P&G customer profile: Dynamics (master) → App Backend (synced)
- Non-native customer profile: App Backend (master)
- HPP plan enrollments: Commerce/Dynamics (master) → App Backend (synced)
- Service requests (HPP): Dynamics (master) ↔ App Backend (bi-directional sync)
- Service requests (ad-hoc): App Backend (master) → Dynamics (pushed for invoicing)
- Home inventory: App Backend (master)
- Ad-hoc service catalog: App Backend (master)
- Reminders: App Backend (master)
- Contractor configuration: CRM/Dynamics (source of truth) → App Backend (copy for matching algorithm)

**Sync Approach:**
- For MVP: Admin backend mirrors data from CRM systems (read-only sync)
- New data (inventory, ad-hoc services, reminders) lives primarily in app backend
- Over time: Migrate more "source of truth" functions from CRM to app backend

### Business Dependencies

**1. Ad-Hoc Service Catalog Definition**
- Initial service list must be defined (5-10 services with flat rate pricing)
- Pricing must be negotiated with contractors per region
- Scope of work must be defined for each service
- Timeline: Weeks 8-12 of project

**2. Contractor Network Readiness**
- 125-140 contractors across 4-5 states
- Primary/secondary designations confirmed
- Zip code assignments validated
- Lead time buffers configured
- Contractors briefed on new app workflow

**3. Duke SME Availability**
- Business SMEs need 10-15 hours/week for requirements validation
- Product catalog definition and pricing approval
- Legal approvals for customer communications and privacy notices

**4. Multi-Property Support Requirement**
- Despite being outlier use case, multi-property support required from Day 1
- Profile validation against Duke Enterprise systems will surface multiple premises for some customers
- Cannot deprioritize as it will break validation flow

### MVP Constraints & Limitations

**No FSM Integration:**
- No real-time contractor tracking ("pizza tracker")
- No automated status updates from contractor
- No "En Route", "On-Site", "In Progress" statuses
- Manual admin status updates required

**No In-App Payment:**
- Contractors collect payment on-site for ad-hoc services
- Customer cannot pre-pay in app for MVP
- May reduce conversion for non-native customers

**No Contractor Mobile App:**
- Contractors use existing portal (not mobile-optimized)
- No one-tap job acceptance
- No in-app communication with customers
- No contractor inventory capture tool (photo upload, data entry)

**No In-App Ratings:**
- Customer ratings collected via external survey (email/SMS)
- Ratings NOT displayed to customers during booking
- Customers cannot read reviews of contractors
- Prevents "contractor shopping" behavior

**Limited Ad-Hoc Service Catalog:**
- Start with 5-10 services (not comprehensive)
- Launch in 1-2 pilot markets only
- Expand gradually based on MVP learnings

**Emergency Services Phone-Only:**
- Emergency services NOT booked through app
- App triage routes to phone call
- Prevents customers from selecting inappropriate service times for emergencies

---

## OUT OF SCOPE - PHASE 2 & BEYOND

### Phase 2 Features (Explicitly Deferred)

**Customer App:**

**Service Features:**
- AI virtual assistant (conversational troubleshooting)
- Pizza tracker (real-time contractor GPS tracking)
- In-app payment processing (pre-pay for ad-hoc services, Apple Pay, Google Pay, credit card)
- In-app ratings and reviews (collection and display during booking flow)
- Contractor marketplace (select from multiple contractors with pricing/ratings)
- In-app messaging (two-way chat between customer and contractor)
- Enhanced decision trees (comprehensive troubleshooting guides, service eligibility assessment)
- Coverage limit display (show remaining annual limits per plan: "$500 of $2,000 used this year")
- Service bundling (book multiple services in single workflow - e.g., "HVAC tune-up + filter change")

**Home Inventory & Profile:**
- Document Library (central storage for home documents, manuals, warranties, permits, receipts - upload, organize, search)
- Enhanced DIY content library (professionally created how-to video guides, step-by-step repair tutorials, integration with product manual databases)
- Home sale transfer (automated profile transfer to new homeowner with service history export)

**Contractor Features:**
- Preferred Service Providers (customer ability to save/designate favorite contractors per inventory item or trade)
- Enhanced contractor profiles (display certifications, licenses, insurance info, years in business, verification badges)
- Transaction history & invoices (downloadable receipts/invoices for all ad-hoc services with search/filter capabilities)

**Admin Portal:**
- Document management (view customer-uploaded documents, assist with document organization)
- Advanced FSM integration (automated contractor tracking, GPS)
- Advanced analytics (predictive analytics, AI-driven insights, custom reports)
- Payment management (full AR/invoicing for ad-hoc services, revenue reporting)
- Enhanced service catalog management (bundled services, dynamic pricing, promotional offers)
- Customer preferred contractor management (view/edit customer contractor preferences)
- Move more "source of truth" functions from CRM to app backend

**Contractor Portal:**
- New contractor mobile app (iOS/Android)
- Real-time job acceptance (push notifications, one-tap accept/decline)
- FSM tool integration (GPS tracking, automated status updates)
- Contractor inventory capture tool (photo upload, barcode scanning, data entry on mobile)
- In-app communication with customers (chat, send photos)
- Performance dashboards for contractors (jobs completed, ratings, revenue)

### Phase 3+ Features (Long-Term Vision)

- White-label platform (template app for other utilities)
- Expanded service categories (pool service, roof repairs, window replacement, insulation)
- Energy efficiency integration (real-time energy monitoring tied to utility data)
- Predictive maintenance (machine learning to predict failures)
- Referral network (Binded Duke integration for trades not under direct Duke contract)
- IoT integration for smart home devices
- Advanced BI dashboards

### Out of Scope (Not Planned)

- Commercial properties (only residential properties supported)
- Unlicensed trades (no lawn care, painting, or other non-licensed services)
- Landlord/property management features (managing multiple units)
- Contractor direct payment (contractors paying Duke for job leads)

---

## SUCCESS METRICS

### Customer Experience KPIs
- Reduce service request time from 15 minutes (phone) to <3 minutes (app)
- Achieve 90% customer satisfaction with contractor communication
- 70+ NPS score
- 80% inventory completion rate (customers with at least 1 inventory item)

### Operational Efficiency KPIs
- Reduce call center volume by 40%
- Automate scheduling to reduce coordination calls by 80%
- Manual intervention rate: <10% of transactions
- Admin queue processing time: <24 hours for enrollment, <1 hour for support tickets

### Business Growth KPIs
- Generate $25M in new ad-hoc service revenue within 12 months
- Acquire 250K non-native customers within 24 months
- New HPP enrollments via app
- Profile completion rate: 90% of customers have complete profile

### Contractor Performance KPIs
- 90-95% contractor acceptance rate (primary contractors)
- On-time arrival rate
- Jobs completed per contractor
- Customer satisfaction ratings per contractor

---

## IMPLEMENTATION APPROACH

### Development Methodology
- Hybrid Agile with 2-week sprints
- AI-assisted development (31% efficiency improvement estimated)
- Parallel workstreams: Mobile app, APIs, backend systems
- Continuous integration/continuous deployment (CI/CD)
- Phased deployment: Development → Staging → Production

### Timeline
- Total Duration: 44 weeks (11 months) from contract execution
- Planning & Analysis: Weeks 1-12
- Design & Architecture: Weeks 8-16
- Development MVP: Weeks 12-20
- Alpha/Beta Development: Weeks 20-28
- Testing & QA: Weeks 24-36
- Deployment: Weeks 36-40
- Warranty Support: Weeks 40-44

### Key Milestones
- Week 20: MVP Release
- Week 24: Functional Alpha
- Week 28: Beta Version
- Week 32: Release Candidate
- Week 40: Production Launch

### Platform
- Native Mobile Apps: iOS and Android with offline capabilities
- Mobile Web Version: Responsive PWA with feature parity
- Backend: Laravel framework with RESTful APIs
- Database: PostgreSQL or MySQL with Redis caching
- Hosting: AWS cloud infrastructure

---

**Document Status:** Final for MVP Planning
**Last Updated:** November 2025
**Next Review:** After Session 3 Contractor Discovery (if additional updates)

---

**Related Documents:**
- Customer App Preliminary Scope & Flows (Detailed)
- Admin Portal Preliminary Scope & Requirements (Detailed)
- Contractor Portal Preliminary Scope & Requirements (Detailed)
- Session 1: Customer Discovery Workshop Notes
- Session 2: Admin Discovery Workshop Notes
- Session 3: Contractor Discovery Workshop Notes
