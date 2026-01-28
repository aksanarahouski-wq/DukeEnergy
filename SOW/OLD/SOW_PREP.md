# Duke Energy Residential Solutions - SOW Preparation Analysis

**Date**: January 7, 2026
**Prepared By**: Orases
**Documents Reviewed**: Discovery Findings & Updated Project Scope, Duke Energy Residential Solution Scope (Detailed), Master Consulting Services Agreement

---

## Executive Summary

After comprehensive discovery, the Duke Energy Residential Solutions Home Services App project has **significantly expanded in scope** from the original RFP. The updated scope reflects operational realities, technical dependencies, and strategic decisions to launch 6-12 months earlier than waiting for full FSM/API integration.

### Key Scope Expansion Drivers

1. **User Role Complexity**: 7 distinct admin roles vs. 3 originally planned
2. **"Bridge Gap" Challenge**: $177,750 in temporary features needed because FSM/API integrations won't be available at launch
3. **New Features Added**: Ad-hoc customer separation, contractor database, gamification, enhanced analytics, maintenance reminders
4. **Enhanced Claims Management**: Dual pathways for members vs. one-time customers
5. **Advanced Home Inventory**: More sophisticated data capture and tracking

### Total Investment & ROI

| Component | Amount |
|-----------|--------|
| **Total Development** | **$788,600** |
| - CX Interface (36.1%) | $285,225 |
| - Backend Development (42.0%) | $332,083 |
| - DevOps & Security (21.7%) | $171,292 |
| **Bridge Functionality** | **$177,750** |
| - Temporary features | $152,250 |
| - Abstraction layers | $25,500 |
| **Expected Phase 2 Rework** | **$46,000** |
| **Business Case ROI** | **11.7x** |
| - Revenue during transition | $2M+ |
| - Cost of waiting | $2M+ lost revenue |

---

## Comprehensive Scope Analysis

### Discovery Document - Key Findings

#### Scope Changes Summary

**REMOVED ENTIRELY**:
- Contractor Marketplace (deferred to Phase 2)
- In-App Rating Display (moved out of MVP)
- Calendar Integration for contractors (eliminated)
- DIY Content Section (replaced with dynamic recommendations)

**SIMPLIFIED FEATURES**:
- Automation Workflows: Phase 1 relies on CSRs/schedulers with manual tools
- Contractor Matching: Streamlined algorithm (trade + zip code only)
- System Complexity: Reduced by leveraging existing Dynamics CRM and FSM2

**MODIFIED & ENHANCED**:

1. **Claims Management** (Net Increase)
   - Significantly enhanced with better workflow understanding
   - Added critical dimension: ad-hoc customers vs. existing customers (MAJOR addition)
   - Simpler workflow structure but more comprehensive feature set

2. **Home Inventory System** (Net Increase)
   - More advanced functionality with greater detail level and data capture
   - Comprehensive inventory tracking for homeowners

3. **Service Booking & Contractor Management** (Net Decrease)
   - Removed: Full contractor self-service portal
   - Added: CSR browse/lookup capabilities for account management
   - Rationale: Avoid CSRs juggling 4 different systems; phone-only for contractors

4. **DIY Content Replacement** (Net 0)
   - Removed: Static Do-It-Yourself content library
   - Added: Dynamic homeowner recommendations with automated notifications
   - Net Impact: Increase (notifications require backend infrastructure vs. static content)

**ENTIRELY NEW FEATURES ADDED**:

1. **Ad Hoc vs. Member Customer Separation**
   - Complete new workflow and user management system
   - Distinguishes one-time customers from membership holders
   - Requires dual pathways for claims, service booking, account management

2. **Contractor Database & Matrix**
   - New internal system managing contractors before FSM tool implementation
   - Tracks service areas, geographical coverage, preferred vs. backup status, availability
   - Critical bridge functionality

3. **Enhanced Analytics & Tracking**
   - Comprehensive interaction tracking across all touchpoints
   - Visibility into customer behavior, service patterns, operational efficiency metrics

4. **Gamification System**
   - "Home Score" rating system for homeowners
   - Encourages engagement and preventive maintenance
   - Includes point accumulation, achievement badges, progress tracking

5. **Maintenance Reminders**
   - Complete new feature set: scheduling, automated notifications, tracking, completion verification
   - Proactive homeowner engagement tool

6. **Expanded User Roles**
   - Original scope: ~3 user roles
   - Updated scope: ~7 different roles with distinct permissions, workflows, interface requirements
   - Significantly increased complexity

#### The "Bridge Gap" Challenge

**The Core Complexity Driver**:

Duke Energy needs a functional MVP now, but full third-party tools (FSM API, complete Dynamics CRM integration) won't be available until later phases. This timing gap creates the critical challenge.

**The Challenge**:
- Operations cannot wait for full third-party integrations
- Business needs immediate functionality to serve customers
- FSM/API availability: 6-12 months post-launch
- Cost of waiting: $2M+ in lost revenue

**Our Solution**:
- Build "stopgap" functionality: manual browse/management screens for CSRs
- Temporary contractor database
- Operational tools enabling work during transition
- Build abstraction layers ($25,500 investment) allowing backend swaps without UI changes
- Manual workflows with admin tools bridge the gap

**Cost Impact**:
- Bridge functionality adds $177,750 to Phase 1
  - $152,250 temporary features
  - $25,500 abstraction layers
- Expected rework when FSM arrives: $46K (reduced from $96K through smart architecture)

#### Risk of Obsolescence in Temporary Features

**Components That Will Be Replaced When FSM Tool Arrives**:

| Feature | Current Approach | When FSM Arrives | Obsolescence |
|---------|------------------|------------------|--------------|
| **Service Request Status Management** | Manual admin dashboard, simplified workflow, admin notifications | Automated, real-time sync, admin handles exceptions only | 70% waste |
| **Contractor Availability & Lead Time Logic** | Static availability, fixed buffers, manual capacity tracking | Real-time calendar sync, dynamic scheduling, instant confirmation | 75% waste |
| **Contractor Assignment Algorithm** | Simple trade + zip code matching, primary/secondary, manual override | Intelligent routing: proximity, ratings, capacity, real-time availability | 50% waste |
| **Appointment Confirmation Workflow** | Admin emails/calls contractors, manual response tracking, backup escalation | Instant confirmation via contractor app, automated escalation, real-time customer updates | 75% waste |
| **Service Request Tracking** | 5 basic statuses, limited visibility | Rich status updates (Dispatched, En Route, On-Site, In Progress), GPS tracking, "pizza tracker" | 50% waste |

**Average Obsolescence**: 67% across temporary features

**Mitigation Strategy**: Design for Abstraction

Without mitigation: 67% obsolescence, substantial waste, difficult FSM integration
With abstraction layers:
- Service Request Abstraction Layer: Reduce status management waste from 70% to 30%
- Contractor Data Service Interface: Reduce assignment waste from 50% to 20%
- Availability Provider Pattern: Reduce availability waste from 75% to 30%
- API Gateway Pattern: Reduce API fallback waste from 75% to 25%
- Event-Driven Architecture Prep: Enable easier FSM integration

**Mitigation Investment**: $25,500 additional architectural effort
**Net Benefit**: Significant reduction in future rework
**ROI**: Nearly 2x return on mitigation investment

---

### Detailed Scope Document - MVP Definition

#### Three-Tier System Architecture

**1. CUSTOMER APP (Mobile/Web)**

**Three Primary Customer Segments (All Supported in MVP)**:

**Segment 1: Existing Duke/P&G Customers WITH Home Protection Plans**
- 800K+ existing HPP customers (immediate user base)
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

**Core MVP Features**:

 **Registration & Onboarding**
- Profile creation required (separate from utility accounts)
- Guest access very limited (browsing only, no booking)
- Address entry minimum requirement (enables public data pre-fill)
- Profile validation API links Duke/P&G customers to existing HPP plans
- **Multi-property support**: Customers with multiple premises can manage all properties in single profile

 **Home Protection Plan Management**
- View all active HPPs linked to customer profile
- Enroll in new plans (full workflow with payment method selection)
- Upgrade/downgrade existing plans
- Self-service cancellation (compliance requirement)
- Display coverage terms, pricing, billing method
- Support for multiple plans per property

 **Home Inventory/Profile Building**
- Manual entry of appliances, systems, equipment (make, model, serial, age)
- Barcode scanning for auto-populate data
- Pre-fill home characteristics from address (square footage, year built, property type)
- Progressive profiling (build inventory over time)
- Gamification and loyalty rewards tied to profile completion
- **Contractor-enhanced data**: Technicians can add/update inventory during service visits
- Maintenance schedules auto-generated based on inventory
- Recall checking against CPSC database

 **Service Booking - HPP Covered Services**
- Symptom-based intake (customer describes issue, not technical diagnosis)
- Coverage check (app determines eligibility under existing plan)
- Inventory integration (pre-populate service request if item in profile)

**Contractor Assignment (Trade + Zip Code ’ Primary Contractor)**:
- Automated matching based on trade + customer zip code
- Customer sees pre-assigned contractor: "Your contractor: ABC Plumbing"
- **NO in-app contractor selection in MVP**
- Request alternative via phone call to admin (not in-app feature)

**Date/Time Selection**:
- Customer chooses from available windows based on static availability buffers
- Lead times vary by trade:
  - HVAC/Water Heater: 1-2 business days
  - Plumbing: 3-5 business days
  - Electrical (non-emergency): 5-6 business days
  - Appliance: 2-3 business days
- Time windows: Half-day slots (8am-12pm, 1pm-5pm most common)

**Booking Confirmation**:
- Status: "Pending Confirmation"
- Admin manually contacts contractor within 1 hour (email/phone)
- Contractor responds within 24 hours
- Admin updates app: "Confirmed - ABC Plumbing - Thursday 9-12am"
- No payment required (covered services $0 customer cost)

 **Service Booking - Ad-Hoc (Non-Covered) Services**
- Browse/search service catalog with transparent, upfront pricing
- Flat-rate pricing for preventative maintenance (e.g., "$99 HVAC cleaning check")
- Variable pricing for some services (e.g., "$120-$190 ceiling fan installation")
- Available to all customer types including non-natives
- Discounted rates (Duke may subsidize to drive engagement)

**Contractor Assignment for Ad-Hoc (Same as Warranty for MVP)**:
- Primary contractor assigned based on trade + zip code
- Customer experience: "Your contractor: ABC Plumbing - $99"
- **NO contractor marketplace in MVP** (no choosing from multiple options)
- **NO ratings displayed in MVP**

**Payment (Contractor Collects On-Site for MVP)**:
- Contractor collects payment at service completion
- Methods: Cash, check, credit card via contractor's reader
- App displays: "Total cost: $99. Payment collected by ABC Plumbing at service completion."
- **In-app payment processing deferred to Phase 2**

 **Communication & Notifications**
- Multi-channel delivery: Push notifications, SMS, email, in-app notification center
- Customer selects preferred communication channels

**MVP Service Request Status Flow (Manual Admin Updates)**:
1. **Booking Confirmation** (Immediate): "Pending Confirmation" status
2. **Appointment Confirmed** (Within 24-48 hours): "Confirmed - [Contractor] - [Date] [Time]"
3. **Appointment Changed** (If needed): Updated date/time with notification
4. **Service Completed** (After service): "Completed" status, external survey sent

**MVP Status Limitations (No FSM Integration)**:
- **NO intermediate statuses**: No "Dispatched", "En Route", "On-Site", "In Progress"
- Admin manually updates statuses based on contractor communication
- Contractors send their own "on my way" texts (~70% do this already)

 **Maintenance Reminders**
- Inventory-based reminders (auto-generate maintenance schedules)
- Default reminder sets for new homeowners
- Custom reminders (user-created)
- Reminder opt-out/snooze capability
- Each reminder offers "Book Service" button to schedule professional service
- Age-based recommendations for aging equipment
- Recall alerts from CPSC

 **Loyalty/Rewards/Gamification**
- Profile completion score (percentage indicator)
- Loyalty points for completing profile, scheduling maintenance, app engagement
- Point redemption for dollar credits on future services
- Home health scorecard (risk assessment based on appliance ages)
- Badge system (Fitbit-style achievements)
- Value tracking (cumulative savings display)

 **Service History & Records**
- Exportable service log (all services tied to appliances/systems)
- Service details: Date, contractor, technician, work performed, parts, cost
- Invoice/receipt storage (PDFs in app)
- Warranty tracking (manufacturer warranties)
- Home sale use case (export history for home buyers)

  **Customer Feedback/Reviews - EXTERNAL PROCESS ONLY**
- Survey sent after service completion via external vendor (email/SMS)
- Data collected but **NOT displayed to customers in MVP**
- **NOT collected in-app for MVP**
- Ratings used internally by Duke for contractor performance evaluation
- **In-app ratings deferred to Phase 2**

=¨ **Emergency Service Handling - NOT IN APP - PHONE ONLY**
- Emergency services **NOT booked through app**
- App asks qualifying questions to detect emergencies
- Emergency detected ’ Route to phone call: "Please call us immediately at 1-800-XXX-XXXX"
- Safety alerts for life-threatening situations (gas leaks, electrical sparking)
- CSR handles emergency coordination directly with contractors

**Examples of Emergencies**:
- No heat in winter (freezing temps)
- Gas leak smell
- Electrical sparking/smoking
- Active water flooding
- Sewage backup

**Contractor Matching Algorithm**:

**Network Overview**:
- 125-140 contractors across 4-5 states (NC, SC, FL, OH, IN)
- 80% primary contractors (first assigned, receive jobs first)
- 20% backup contractors (overflow when primary unavailable)
- 99-100% coverage for HVAC, Plumbing, Electrical, Water Heater
- Most contractors offer 2-3 trades (multi-trade support)

**Matching Logic (Trade + Zip Code + Primary/Secondary)**:
1. System identifies trade needed (HVAC, plumbing, electrical, appliance, water heater)
2. Exact zip code match (NOT radius-based)
3. Primary contractor auto-assigned for that trade + zip code
4. Customer sees pre-assigned contractor
5. Request alternative triggers phone call to admin

**Availability & Lead Times (Static Buffer Approach)**:
- Contractors provide availability rules (e.g., "Mon-Fri 8-5, 3-day buffer")
- No real-time calendar checking (FSM tool required - Phase 2)
- Lead times trade-specific (HVAC 1-2 days, Electrical 5-6 days, etc.)

**Contractor Acceptance Process**:
- Target: 90-95% acceptance rate (SLA contracts)
- Customer books ’ Admin contacts contractor within 1 hour
- Contractor responds within 24 hours
- If primary unavailable: Admin tries backup contractor
- Priority: Keep customer's requested time > keep specific contractor

---

**2. ADMIN PORTAL (7 User Roles)**

**Purpose**: The admin portal serves as the "middle layer" aggregating data from multiple sources (Commerce CRM for Duke customers, Dynamics for P&G customers, app database for non-native customers) into a unified administrative interface. Enables back-office operations to support customer app experience while managing manual fallback processes for MVP.

**Seven Distinct Roles**:

1. **CSR (Enrollment Center)**: Handle enrollment inquiries, manually create accounts/business partners, process failed enrollments from review queue

2. **CSR (Shop/Support)**: App account administration (password resets, unlock accounts), troubleshoot app issues

3. **Back Office Admin**: Process enrollment queues, manage customer profiles, update inventory, configure services & pricing

4. **Product Manager**: Create/edit ad-hoc service catalog, set pricing, define service scope of work, manage reminders

5. **Operations Manager (MVP CRITICAL)**: Manually process service requests (contact contractors within 1 hour, update app status based on responses), reassign contractors, handle exceptions

6. **Escalation Team**: Handle customer complaints, contractor disputes, service quality issues

7. **Analyst/Reporting User**: Access dashboards, export reports, track KPIs

**Permission Levels**:
- **View Only**: Customer profile basic info, service request status, analytics dashboards
- **Edit/Create**: Customer inventory, service catalog & pricing, reminders & content, contractor configuration
- **Admin/Super User**: User management, system configuration, full CRUD across all entities

**Core MVP Features**:

 **1. Customer Management**
- Customer profile CRUD (view, edit, create customer records)
- Cross-system data aggregation from Commerce, Dynamics, and App DB
- Review queue for failed enrollments
- Account administration (password resets, unlock accounts)
- Manual enrollment processing (when API doesn't exist)

 **2. Home Inventory Management**
- Full CRUD on customer inventory
- Multi-source data: Customer-entered, admin-added, contractor-added
- Inventory fields: Item type, brand, model, serial number, age, location, purchase date, warranty expiration
- Use case: Admin looks up inventory during support calls to troubleshoot

 **3. HPP Plan (Subscription) Management**
- View customer subscriptions (all HPP plans)
- Subscription status: Active, suspended, cancelled
- Manual enrollment support for MVP
- Sync with CRM (plans live in Commerce/Dynamics, app backend mirrors)

 **4. Service Request Management (MAJOR MVP COMPONENT)**

**Service Request Dashboard**:
- View all service requests (HPP covered + ad-hoc)
- Filter by status, date, customer, contractor, type
- Priority queue: "Pending Confirmation" requests needing immediate action
- Search by customer name, service request ID

**Service Request Statuses (MVP - Manual Updates)**:
1. Pending Confirmation (customer booked, admin needs to contact contractor)
2. Confirmed (contractor accepted, appointment scheduled)
3. Rescheduled (time/date changed)
4. Completed (service finished)
5. Cancelled (cancelled by customer or contractor)

**NO FSM Integration for MVP**: No automated statuses like "Dispatched", "En Route", "On-Site", "In Progress"

**Service Request Details View**:
- Customer info, service type, service category/trade
- Problem description, related inventory item
- Assigned contractor (primary based on trade + zip code)
- Requested date/time window (customer-selected)
- Confirmed date/time (contractor-accepted, may differ)
- Status history, contractor notes, payment status
- Time since submission (SLA tracker: process within 1 hour)

**MVP Admin Workflow - Manual Service Request Processing**:

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

**Admin Actions**:
- Manual service request creation (phone orders)
- Manual status updates based on contractor communication
- Reassign contractor (override automatic assignment)
- Add internal notes
- Cancel/reschedule appointments
- Handle exceptions (no contractor available, all at capacity, emergencies)

**Target SLAs**:
- Admin processes service request: Within 1 hour of customer submission
- Contractor responds to admin: Within 24 hours
- Admin updates app with confirmation: Within 1 hour of contractor response
- Total time to confirmation: 24-48 hours

 **5. Ad-Hoc Service Catalog Management**

**CRITICAL: Ad-hoc service catalog does NOT exist today. Must be built.**

**Service Catalog Admin Functions**:
- Create new ad-hoc services (define name, category, description, scope of work)
- Set pricing (fixed price, price range, or "quote required")
- Geographic pricing (different prices by region/market)
- Scope of work definition (what's included, exclusions)
- Service availability (which zip codes/regions)
- Contractor association (which contractors offer service at negotiated rate)
- HPP plan association (map services to plans)

**MVP Ad-Hoc Services (Limited Set)**:
- Start with 5-10 well-defined services with flat rate pricing
- Examples: HVAC tune-up ($99), water heater flush, air filter change
- Launch in 1-2 pilot markets (e.g., Orlando area)

**Service Fields**:
- Service name, service code/SKU, category
- Description, scope of work
- Pricing type (fixed, variable, quote-based)
- Base price, regional price overrides
- Geographic availability, contractor availability
- Status (draft, active, inactive)

 **6. Contractor Configuration Management (MAJOR MVP COMPONENT)**

**Contractor Network Overview**:
- 125-140 contractors across 4-5 states
- Primary contractors (~80%): First assigned, receive jobs first
- Backup contractors (~20%): Overflow when primary unavailable
- Multi-trade: Most contractors offer 2-3 trades with different configs per trade

**Contractor Data Model - Admin Backend**:

**Basic Information**:
- Contractor ID, name, business name
- Contact phone, email, primary contact
- Status (Active, Inactive, On Hold)
- Licensing information, insurance information
- Background check status

**Service Area Configuration (Critical for Matching Algorithm)**:
- Zip code list (exact zip codes contractor serves)
- NOT radius-based (zip code specific assignment)
- Non-contiguous areas supported (Charlotte + Raleigh but not cities in between)
- Geographic coverage notes

**Trade/Specialization Configuration (Multi-Trade Support)**:

Each contractor can have multiple trade configurations:
- Trade 1: HVAC - Primary for zips 28201, 28202, 28203 - Lead time 2 days - Mon-Fri 8-5
- Trade 2: Plumbing - Secondary for zips 28203, 28204 - Lead time 3 days - Tue-Thu only
- Trade 3: Electrical - Secondary for zips 28201, 28202 - Lead time 6 days - Mon/Wed/Fri only

**Primary/Secondary Designation (Per Trade + Zip Code)**:
- Primary: First assigned, SLA commitment to accept 90-95% of jobs
- Secondary/Backup: Assigned when primary unavailable
- Designation can vary (primary for HVAC in one zip, secondary for Plumbing in another)
- Determined by: Negotiated contracts, capacity, pricing, performance

**Lead Time & Availability Configuration**:
- Trade-specific lead time buffers
- Static availability rules (work days, time windows, blocked dates)
- Max jobs per day (capacity limits)
- NOT real-time calendars for MVP

**Admin CRUD Operations**:
- Create new contractor (add basic info, configure trades, service areas, availability)
- Edit contractor (update info, add/remove service areas, adjust lead times, blocked dates)
- Override/exception handling (emergency override, blocked date override, capacity override)

**Contractor Data Sync Strategy (MVP)**:
- Initial setup: Duke exports contractor data from CRM (CSV/JSON), Orases imports into app backend
- Ongoing maintenance: Contractor changes in CRM first, admin manually updates app backend
- Frequency: As-needed (contractor changes rare, ~1-2 per year)

**Contractor Performance Tracking (Admin View Only)**:
- Jobs completed, acceptance rate, on-time arrival rate
- Customer satisfaction ratings (from external surveys)
- Average job completion time, revenue generated
- Performance does NOT factor into MVP matching algorithm

 **7. Reminders Management**

Focus on reminders (automated maintenance calendar).

**Reminder Categories**:
- Global reminders (default for all homeowners)
- Asset-based reminders (triggered by inventory items)
- Seasonal reminders (spring/summer/fall/winter maintenance)
- Customer-created reminders

**Admin Functions**:
- Create/edit reminder templates
- Asset category mapping (tie reminders to inventory categories)
- Seasonal configuration
- Service linkage (link reminder to bookable service)

**Reminder Fields**:
- Title, description/instructions
- Frequency (monthly, quarterly, bi-annually, annually, seasonal)
- Asset category, optional service link, optional HPP plan link
- Status (active, inactive)

 **8. Analytics & Reporting Dashboard**

**CRITICAL: Full instrumentation required from MVP launch.**

**Key Metrics to Track**:

**Customer Acquisition**:
- New app registrations (by customer type)
- Registration conversion rate
- Inventory completion rate

**Engagement**:
- Active users (DAU, WAU, MAU)
- Session duration, feature usage
- Customer drop-off points

**Service Requests**:
- Total service requests (HPP vs ad-hoc)
- Volume by type, region
- Time to complete service request
- Customer satisfaction ratings

**Revenue**:
- Ad-hoc service revenue
- New HPP enrollments via app
- Cancellations/churn

**Contractor Performance**:
- Jobs completed, on-time percentage
- Customer ratings, utilization rate

**Operational**:
- Call center volume reduction (target: 40%)
- Automated scheduling rate (target: 80%)
- Manual intervention rate

**Dashboard Views**:
- Operations Dashboard: Real-time service request tracking
- Executive Dashboard: High-level KPIs, trends
- Marketing Dashboard: Customer acquisition, engagement
- Product Dashboard: Feature adoption, drop-off points

**Export Capabilities**:
- Export reports to CSV, Excel, PDF
- Scheduled reports (daily, weekly, monthly)

 **9. Communication & Notifications**
- Send email or SMS to customers
- Bulk notifications
- Customer communication preferences management
- Communication log/history per customer

---

**3. CONTRACTOR PORTAL - NO CHANGES FOR MVP**

**The Big Decision: Admin-Only Approach for Phase 1**

**MVP Decision**: No Contractor Portal Changes

Contractors will continue using existing Commerce CRM portal for Phase 1 MVP. All contractor-related functionality will be managed through the admin backend portal.

**Rationale**:
1. Focus 100% on customer app (drives revenue: $25M ad-hoc services target)
2. Existing Commerce portal is functional, contractors are familiar
3. Learn from MVP first before investing in contractor features
4. FSM tool dependency: Robust contractor mobile app requires FSM integration (not ready for Phase 1)
5. Manual admin updates acceptable for MVP
6. Phase 2 investment: Build modern contractor mobile app after FSM tool selected and customer app proven

**What Contractors Continue Using (No Changes)**:

**Existing Contractor Portal (Direct Access to Commerce CRM)**:
- Receive job assignments
- View service request details (customer name, address, problem description)
- Schedule appointments with customers
- Update service request status (accepted, scheduled, dispatched, in-progress, completed, invoiced)
- Enter completion details (services performed, parts used, time spent)
- Submit invoices

**Communication Methods**:
- Email notification when new job assigned
- Phone calls to/from Duke back office
- Direct phone/SMS with customers (contractors have customer phone numbers)

**Their Own Systems**:
- Contractors use their own dispatch software (Service Titan, Housecall Pro, etc.)
- Contractors manage technician schedules internally
- Contractors send their own lifecycle communications (~70% provide en-route notifications)

**What Admin Backend Manages (New for App)**:

**Contractor Configuration (Admin Portal Features)**:
- CRUD operations for contractors
- Assign trades to contractors (multi-select: HVAC, Plumbing, Electrical, etc.)
- Assign service areas (zip code list per contractor)
- Set primary/secondary designation per trade + zip code
- Configure lead time/buffer per contractor per trade
- Configure availability windows (time slots, days of week)
- View contractor performance metrics
- Override assignments for exceptions (emergencies, capacity issues)

**Service Request Status Management (Admin Portal)**:
- View pending service requests from customer app
- Manually send service request to contractor (email/phone for MVP)
- Update status when contractor confirms: "Confirmed - [Contractor Name] - [Date/Time]"
- Update status when contractor completes: "Completed - [Date]"
- Handle reschedules/cancellations (update app, notify customer)

---

## KEY ASSUMPTIONS & DEPENDENCIES

### Technical Dependencies

**1. Duke Enterprise APIs**

 **Customer Validation & HPP Plan APIs**: WILL EXIST by MVP launch (confirmed)
- Validate if customer is Duke/P&G utility customer
- Retrieve customer HPP plan subscriptions
- Check subscription status (active, suspended, cancelled)

  **Service Request Creation API**: MAY NOT EXIST for MVP - Manual fallback required
- If API unavailable: Service request created in app backend, admin manually enters into CRM or processes via automated queue

  **Enrollment API**: May not exist for MVP
- If unavailable: Admin manually processes enrollments submitted via app
- Manual fallback: Admin creates enrollment in CRM, syncs to billing, updates app backend

**2. FSM (Field Service Management) Tool Integration**

L **Status**: Future - NOT for MVP
- Current State: Duke exploring FSM tools (Service Power, Service Bench)
- For MVP: Admin manually updates service request status
- Future State (Phase 2): FSM tool provides real-time contractor GPS tracking, automated status updates, "pizza tracker" experience

**3. Payment Processing Integration**

  **MVP Approach**: Contractor collects payment on-site (cash, check, credit card via contractor's reader)

**Phase 2**: App-based payment integration
- Customer pre-pays in app
- Duke charges customer's card
- Pays contractor net of commission
- Payment Methods: On utility bill (Duke/P&G only), Apple Pay, Google Pay, credit/debit card, ACH

**4. Data Sync Strategy**

**Master Sources of Truth**:
- Duke customer profile: **Commerce (master)** ’ App Backend (synced)
- P&G customer profile: **Dynamics (master)** ’ App Backend (synced)
- Non-native customer profile: **App Backend (master)**
- HPP plan enrollments: **Commerce/Dynamics (master)** ’ App Backend (synced)
- Service requests (HPP): **Dynamics (master)** ” App Backend (bi-directional sync)
- Service requests (ad-hoc): **App Backend (master)** ’ Dynamics (pushed for invoicing)
- Home inventory: **App Backend (master)**
- Ad-hoc service catalog: **App Backend (master)**
- Reminders: **App Backend (master)**
- Contractor configuration: **CRM/Dynamics (source of truth)** ’ App Backend (copy for matching algorithm)

**Sync Approach**:
- For MVP: Admin backend mirrors data from CRM systems (read-only sync)
- New data (inventory, ad-hoc services, reminders) lives primarily in app backend
- Over time: Migrate more "source of truth" functions from CRM to app backend

### MVP Constraints & Limitations

L **No FSM Integration**:
- No real-time contractor tracking ("pizza tracker")
- No automated status updates from contractor
- No "En Route", "On-Site", "In Progress" statuses
- Manual admin status updates required

L **No In-App Payment**:
- Contractors collect payment on-site for ad-hoc services
- Customer cannot pre-pay in app for MVP
- May reduce conversion for non-native customers

L **No In-App Ratings**:
- Customer ratings collected via external survey (email/SMS)
- Ratings NOT displayed to customers during booking
- Customers cannot read reviews of contractors
- Prevents "contractor shopping" behavior

  **Limited Ad-Hoc Service Catalog**:
- Start with 5-10 services (not comprehensive)
- Launch in 1-2 pilot markets only
- Expand gradually based on MVP learnings

=¨ **Emergency Services Phone-Only**:
- Emergency services NOT booked through app
- App triage routes to phone call
- Prevents customers from selecting inappropriate service times for emergencies

---

## Budget Breakdown

### Total Development Investment: $788,600

| Component | Amount | Percentage |
|-----------|--------|------------|
| **CX Interface Development** | $285,225 | 36.1% |
| Mobile Responsive + Native Apps (iOS/Android) | | |
| **Backend Development** | $332,083 | 42.0% |
| Laravel + API Infrastructure | | |
| **DevOps & Security** | $171,292 | 21.7% |
| Deployment, Infrastructure & Compliance | | |

### Bridge Functionality Investment

| Item | Cost |
|------|------|
| Temporary features (manual workflows) | $152,250 |
| Abstraction layers (mitigation) | $25,500 |
| **Total Bridge Investment** | **$177,750** |
| Expected rework (with mitigation) | $46,000 |

### Business Case ROI

| Metric | Value |
|--------|-------|
| Temporary investment | $177,750 |
| Expected waste | $46,112 (6% of project with mitigation) |
| Revenue during transition | $2M+ in Ad Hoc revenue |
| **Net ROI** | **11.7x return** |

**Business Case**: The $177,750 investment in temporary features and abstraction layers enables launch 6-12 months earlier, generating $2M+ in revenue during the transition period. Even accounting for $46K in eventual rework, this represents an 11.7x return on investment. Waiting for full FSM/API availability would cost $2M+ in lost revenue and competitive positioning.

### Ongoing Costs

- **Hosting**: $800/month (includes beta + production environments, scales with user growth)
- **Support & Maintenance**: $6,500/month (optional but recommended)

**Key Notes**: Budget reflects comprehensive discovery findings including bridge functionality, enhanced claims workflows, dual service pathways (HPP + ad-hoc), and 7-role admin architecture. Hosting costs will scale with user growth from 200K to 2M users over 3 years.

### Highest Investment Areas

1. **Claims Management System** (+$70K from enhanced workflows)
   - ~$70K impact from comprehensive workflow improvements and ad hoc customer support
   - Includes dual pathways for members vs. one-time customers

2. **Contractor Management & Matching** (includes temporary assignment logic)

3. **Bridge/Stopgap Functionality** ($152,250 temporary features)

4. **User Role Management** (7 roles vs. 3 originally planned)

5. **Analytics & Tracking Infrastructure**

6. **Notifications & Recommendations Engine**

7. **Abstraction Layer Architecture** ($25,500 mitigation investment)

---

## CX Interface Development Breakdown

**Customer-Facing Application Components ($285,225)**

### Authentication & User Management
- User registration & onboarding flow
- Multi-property support
- Profile creation separate from utility accounts
- Session management & guest browsing

### Customer Profile & Dashboard
- Multi-property management interface
- Profile management (personal info, preferences)
- Communication preferences
- Property selection/switching

### Home Protection Plan (HPP) Management
- View active HPP plans linked to profile
- New plan enrollment workflow
- Upgrade/downgrade existing plans
- Self-service cancellation flow
- Integration with Duke API for plan validation

### Home Inventory/Profile Building
- Manual appliance/system entry
- Barcode scanning for auto-populate
- Pre-fill home characteristics from address
- Photo upload for inventory items
- Warranty tracking & maintenance schedule generation
- Recall checking integration (CPSC database)

### Service Booking - HPP Covered Services
- Symptom-based intake form
- Coverage check logic
- Contractor assignment display
- Date/time selection with static availability buffers
- Booking confirmation flow
- Emergency detection logic

### Service Booking - Ad-Hoc Services
- Browse/search service catalog
- Service detail pages with transparent pricing
- Flat-rate & variable pricing display
- Payment collection messaging
- Price display by region

### Mobile Native App Development
- iOS native app (Swift/SwiftUI or React Native)
- Android native app (Kotlin or React Native)
- App store deployment setup
- Push notification configuration
- Camera integration for barcode scanning
- Deep linking & offline capability

### Communication & Notifications
- Push notification setup (iOS/Android)
- SMS & email notification integration
- In-app notification center
- Multi-channel delivery logic

### Maintenance Reminders & Gamification
- Inventory-based reminders display
- Profile completion score indicator
- Loyalty points tracking system
- Home health scorecard display
- Badge system (achievements)

**Includes**: Responsive web interface, mobile-first design, accessibility compliance (WCAG 2.1), and complete UI/UX design system implementation.

---

## Backend Development Breakdown

**API & Business Logic Infrastructure ($332,083)**

### Core Backend Architecture
- Laravel application setup
- Database schema design & implementation
- RESTful API architecture
- Authentication & authorization (JWT/OAuth)
- Multi-tenant architecture support
- API documentation (Swagger/OpenAPI)

### HPP Plan Management Backend
- HPP plan data model
- Duke Enterprise API integration (customer validation & HPP plans)
- Plan enrollment processing
- Plan upgrade/downgrade logic
- Subscription status sync (Commerce/Dynamics)
- Multi-plan support per property

### Home Inventory Management
- Inventory data model & CRUD API endpoints
- Barcode lookup API integration
- Public data pre-fill API (address ’ home characteristics)
- Photo upload & storage (S3/cloud)
- Maintenance schedule generation logic
- CPSC recall checking integration
- Warranty tracking logic

### Contractor Matching Algorithm
- Contractor data model (complex multi-trade support)
- Trade + Zip code matching logic
- Primary/secondary designation handling
- Service area configuration (zip code lists)
- Lead time calculation logic
- Availability buffer implementation
- Override/exception handling

### Service Request Management - HPP
- Service request data model
- Coverage check logic (HPP eligibility)
- Contractor assignment automation
- Status management workflow
- Manual status update capability for admin
- Duke CRM API integration (if available)
- Manual fallback queue processing
- Emergency detection logic

### Ad-Hoc Service Catalog Management
- Ad-hoc service catalog data model (NEW - doesn't exist)
- Service CRUD APIs
- Pricing management (flat-rate, variable, quote)
- Geographic pricing support
- Scope of work definition
- Service availability by region
- Contractor-service association

### Communication & Notification System
- Multi-channel notification engine
- Push notification service integration (FCM, APNs)
- SMS integration (Twilio/similar)
- Email service integration (SendGrid/similar)
- Notification template management
- Communication log/history

### Admin Portal Backend APIs
- Admin user management
- RBAC for 7 distinct admin roles
- Customer management APIs
- Service request management APIs (admin operations)
- Contractor configuration APIs
- Manual processing queues
- Failed enrollment queue
- Override/exception handling APIs

### Data Sync & Integration Layer
- Commerce CRM integration (Duke customers)
- Dynamics integration (P&G customers)
- Customer profile sync logic
- HPP plan sync
- Service request bi-directional sync
- Contractor data sync from CRM
- Sync error handling & retry logic

### Analytics & Reporting Backend
- Analytics instrumentation
- Event tracking system
- KPI calculation logic
- Dashboard data aggregation APIs
- Report generation & export functionality

**Backend represents 42% of development investment** due to complex contractor matching, dual service flows (HPP + ad-hoc), multi-system data sync, and comprehensive admin capabilities.

---

## DevOps, Deployment & Security Breakdown

**Infrastructure, Compliance & Operations ($171,292)**

### Infrastructure Setup & Configuration
- Cloud infrastructure setup (AWS/Azure/GCP)
- Environment provisioning (dev, staging, production)
- Load balancing & auto-scaling configuration
- CDN configuration
- DNS management
- SSL/TLS certificate management
- Backup strategy implementation

### CI/CD Pipeline
- Git repository setup & branching strategy
- CI/CD pipeline configuration (GitHub Actions/GitLab CI/Jenkins)
- Automated testing integration
- Build & deployment automation
- Environment-specific configuration management
- Rollback procedures

### Database & Storage
- Database provisioning (MySQL/PostgreSQL)
- Database replication setup
- Backup & recovery automation
- S3/cloud storage setup (images, PDFs, documents)
- Database migration strategy
- Data retention policies
- Database performance optimization

### Security Implementation
- Duke Energy cybersecurity requirements compliance
- Role-based access control implementation
- Multi-factor authentication (MFA)
- API security (rate limiting, JWT validation)
- Data encryption at rest & in transit
- Security headers configuration
- OWASP Top 10 vulnerability mitigation
- Penetration testing preparation
- Security audit documentation
- PCI compliance prep (for future payment integration)

### Monitoring & Logging
- Application monitoring setup (New Relic/Datadog/CloudWatch)
- Log aggregation (ELK stack/CloudWatch Logs)
- Error tracking (Sentry/Rollbar)
- Performance monitoring
- Uptime monitoring & alerting
- Dashboard creation for DevOps metrics
- Alert configuration & on-call setup

### API Gateway & Management
- API gateway setup
- API versioning strategy
- API documentation hosting
- API rate limiting & throttling
- API key management
- API analytics

### Container & Orchestration
- Docker containerization
- Kubernetes/ECS orchestration setup
- Container registry setup
- Service mesh configuration (if needed)
- Container security scanning

### Network & VPN Configuration
- VPC setup
- Security group configuration
- Network ACLs
- VPN setup for Duke Enterprise API access
- Private subnet configuration for databases

### Compliance & Documentation
- Compliance documentation (Duke Energy requirements)
- Architecture documentation
- Runbook creation
- Disaster recovery planning
- Data privacy controls documentation
- Security policy documentation

### Mobile App Deployment
- iOS App Store submission & review
- Android Play Store submission & review
- App signing certificate management
- App update strategy
- Push notification certificate setup
- Mobile analytics configuration

**DevOps represents 21.7% of investment**, critical for Duke Energy cybersecurity compliance, enterprise-grade security standards, and multi-environment infrastructure supporting 200K-2M users.

---

## Integration Timeline & Transition Plan

**Approach to Minimize Disruption**

### Phase 1: MVP LAUNCH (Months 0-6)

**Months 1-2**: Build core features with abstraction layers

**Months 3-4**: Implement temporary solutions (manual workflows)

**Months 5-6**: Test, launch, begin revenue generation

**Status**: Manual workflows operational, admin team trained

### Phase 2: API INTEGRATION (Months 7-9)

**Month 7**: Duke APIs become available

**Month 8**: Replace API fallback logic, test integration

**Month 9**: Cutover to real-time sync, decommission manual queues

**Decommissioned**: Manual enrollment processes, data sync workarounds

**Retained**: Admin portal for exceptions, core data models

### Phase 3: FSM INTEGRATION (Months 10-15)

**Months 10-11**: FSM tool selected and configured

**Months 12-13**: Replace status management, availability, assignment logic

**Month 14**: Gradual cutover from manual to automated

**Month 15**: Full automation live, decommission admin workflows

**Decommissioned**:
- Manual status UI
- Static availability calculator
- Pending confirmation queue
- Admin-to-contractor workflow

**Retained**:
- Admin portal (exceptions)
- Notification infrastructure
- Contractor data model
- Customer-facing UI (enhanced)

**Rework investment required across transition phases**
**Significant revenue generation during transition period**

---

## Phase 2 & Beyond

### Phase 2+ Features

**Customer App**:
- In-app payment processing (pre-pay for ad-hoc services, Apple Pay, Google Pay, credit card)
- In-app ratings and reviews (collection and display during booking flow)
- FSM tool integration (GPS tracking, automated status updates)
- Contractor marketplace (select from multiple contractors with pricing/ratings)
- Preferred Service Providers (customer ability to save/designate favorite contractors per inventory item or trade)
- Real-time job acceptance and contractor calendar sync (push notifications, one-tap accept/decline)
- Pizza tracker (real-time contractor GPS tracking)
- Contractor inventory capture tool (photo upload, barcode scanning, data entry on mobile)
- In-app communication with Contractor (chat, send photos)
- In-app messaging (two-way chat between customer and contractor)
- AI virtual assistant (conversational troubleshooting)

### Out of Scope (Not Planned)

- Commercial properties (only residential properties supported)
- Unlicensed trades (no lawn care, painting, or other non-licensed services)
- Landlord/property management features (managing multiple units)
- Contractor direct payment (contractors paying Duke for job leads)

---

## Critical Scope Items for SOW

### MUST BE EXPLICITLY STATED IN SOW

#### 1. Manual Admin Workflows Acceptable
- Service request confirmation: Admin contacts contractors within 1 hour, updates app manually
- No FSM integration in Phase 1
- Status updates are manual, not automated
- **SOW Language**: "Phase 1 service request workflow requires manual admin intervention within 1-hour SLA. Admin portal provides Operations Manager role with tools to contact contractors via email/phone, track responses, and manually update customer app status. Automated contractor assignment and real-time status updates require FSM integration (Phase 2 scope)."

#### 2. Payment Processing Deferred
- Contractors collect payment on-site
- In-app payment is Phase 2
- **SOW Language**: "Phase 1 payment processing: Contractors collect payment on-site at service completion via cash, check, or credit card (contractor's own payment terminal). Customer app displays service cost and payment instructions. In-app payment integration (Apple Pay, Google Pay, credit card processing) is Phase 2 scope requiring separate SOW."

#### 3. Limited Status Visibility
- 5 basic statuses only
- No real-time tracking, no GPS "pizza tracker"
- Contractors send their own "on my way" texts (~70% already do this)
- **SOW Language**: "Phase 1 service request status workflow includes 5 statuses: Pending Confirmation, Confirmed, Rescheduled, Completed, Cancelled. Real-time statuses (Dispatched, En Route, On-Site, In Progress) and GPS tracking ('pizza tracker' experience) require FSM tool integration (Phase 2 scope). Admin manually updates app status based on contractor communication."

#### 4. Emergency Services Phone-Only
- App detects emergencies and routes to phone call
- NOT bookable through app
- **SOW Language**: "Emergency services are NOT bookable through the customer app. App includes emergency detection logic via qualifying questions. When emergency detected, app routes customer to phone call: 'Please call us immediately at 1-800-XXX-XXXX.' CSR handles emergency coordination with contractors via existing phone-based workflow."

#### 5. No Contractor Portal Changes
- Contractors continue using existing Commerce CRM
- Admin backend manages contractor configuration
- **SOW Language**: "Phase 1 includes NO changes to existing contractor portal. Contractors continue using Commerce CRM portal for job assignment, status updates, scheduling, and invoicing. Admin backend portal provides contractor configuration management (CRUD, trade assignment, service areas, availability) to support customer app matching algorithm. Modern contractor mobile app with real-time job acceptance and GPS tracking is Phase 2 scope."

#### 6. Limited Ad-Hoc Service Catalog
- Start with 5-10 services
- Launch in 1-2 pilot markets
- Flat-rate pricing only (e.g., "$99 HVAC tune-up")
- **SOW Language**: "Phase 1 ad-hoc service catalog limited to 5-10 services with flat-rate or variable pricing, launched in 1-2 pilot markets (to be determined by Duke Energy). Service catalog includes: service name, description, scope of work, pricing, geographic availability, contractor association. Catalog expansion and additional markets require Phase 2 scope adjustment."

#### 7. No In-App Ratings Display
- Ratings collected via external survey (email/SMS)
- Used internally by Duke for contractor performance
- NOT shown to customers during booking
- **SOW Language**: "Phase 1 customer ratings and reviews collected via external survey vendor (email/SMS) post-service completion. Ratings used internally by Duke Energy for contractor performance evaluation. In-app ratings collection and display to customers during booking flow is Phase 2 scope."

#### 8. No Contractor Marketplace
- System auto-assigns primary contractor
- Customer sees pre-assigned contractor only
- Request alternative = phone call to admin
- **SOW Language**: "Phase 1 contractor assignment uses automated matching algorithm: Trade + Zip Code ’ Primary Contractor. Customer sees pre-assigned contractor with no in-app option to select alternative contractor. Request for alternative contractor requires phone call to admin Operations Manager who manually reassigns. Contractor marketplace (customer selects from multiple contractors with pricing/ratings) is Phase 2 scope."

#### 9. API Dependencies
- **Customer Validation & HPP Plan APIs**: Will exist by launch (confirmed)
- **Service Request Creation API**: May NOT exist - manual fallback required
- **Enrollment API**: May NOT exist - manual fallback required
- **SOW Language**: "Phase 1 assumes Duke Enterprise APIs for Customer Validation and HPP Plan retrieval will be available by Week 12 of project. If Service Request Creation API or Enrollment API are not available by MVP launch, Orases will implement manual fallback workflows in admin portal at no additional cost. Manual fallbacks include: (1) Admin queue for failed enrollments requiring manual processing in CRM, and (2) Service requests created in app backend with admin manually entering into Duke CRM or processing via automated queue."

#### 10. $46K Rework Budget
- When FSM/APIs arrive (6-12 months post-launch)
- Replace temporary features with automated workflows
- **SOW Language**: "Phase 1 budget includes $25,500 for abstraction layer architecture to minimize future rework when FSM tool and Duke APIs become available (estimated 6-12 months post-launch). Phase 2 rework budget of $46,000 covers replacement of temporary features (manual status management, static availability logic, simplified assignment algorithm) with automated workflows integrated with FSM tool. Phase 2 work requires separate SOW upon FSM tool selection."

---

## Alignment with Master Services Agreement

### Deliverables (Section 3)
- Must define specific deliverables per SOW
- **Include**: Customer app (iOS/Android/Web), Admin portal (7 roles), API infrastructure, contractor matching algorithm, database schema, cloud infrastructure, source code repository, technical documentation, admin user guides, security compliance documentation
- Source code, documentation provided with full rights transfer to Duke

### Intellectual Property (Section 6)
- Duke owns ALL deliverables (work for hire)
- Must provide source code with each deliverable
- Pre-existing tools (Laravel, React Native, Vue.js, etc.) come with perpetual, royalty-free licenses for Duke
- **Critical**: Any pre-existing Orases code/frameworks must grant Duke perpetual license

### Inspection & Acceptance (Section 4)
- Duke has **90 days** to review/test after delivery
- **Critical**: Must define acceptance criteria per phase/sprint to avoid surprises
- If rejected: 30 days to fix at Orases expense
- If not fixed in 30 days: Duke can fix themselves and back-charge OR terminate and get full refund

### Warranties (Section 5)
- Professional standards warranty
- Conform to SOW specifications
- Free from defects in workmanship
- NO trojans, viruses, disabling code
- Software does not infringe third-party rights
- Must re-perform or refund if warranty breach
- **Liable for all damages** from warranty breach (not just re-perform/refund)

### Security Requirements (Section 10.2)
- **SOC 2 Type 2** audit OR ISO 27001 certification (**annual, at Orases expense: $20K-40K**)
- Multi-factor authentication required for all systems with Duke data
- Encryption at rest and in transit (NIST standards)
- **24-hour breach notification** (30 minutes for critical cyber systems)
- Duke can terminate network connection immediately if security risks found
- **Orases pays for ALL breach costs**: notification, credit monitoring, forensic investigation, legal fees

### Audit Rights (Section 2F)
- Duke can audit Orases records during and after project
- For 3 years after final payment
- Must provide records within 7-14 days
- If overcharge found ’ immediate refund

### Payment Terms (Section 2)
- **Net 90 days** - Duke pays invoices 90 days after receipt
- Must reference PO/Contract number on every invoice
- Time-and-materials work requires detailed timesheets
- Final invoice due within 60 days of project completion

---

## Key Risks & Recommendations

### HIGH RISK ITEMS

#### 1. API Availability Uncertainty

**Risk**: Service Request Creation API and Enrollment API may not exist at launch

**Your Commitment**: Manual fallback workflows in admin portal

**SOW Language Recommendation**:
> "If Duke Enterprise APIs (Service Request Creation API, Enrollment API) are not available by MVP launch date [specify date], Orases will implement manual admin queue processing workflows at no additional cost to Duke Energy. Manual workflows include: (1) Admin portal 'Failed Enrollment Queue' where CSRs manually create customer accounts in Commerce/Dynamics CRM and sync to app backend, and (2) Service Request Queue where Operations Manager manually contacts contractors and updates app status. API integration will be completed within 30 days of Duke providing API documentation and sandbox access under separate Change Order."

#### 2. Temporary Feature Obsolescence ($46K)

**Risk**: When FSM/APIs arrive, $152K of work becomes 67% obsolete

**Your Mitigation**: $25.5K abstraction layers reduce waste to $46K

**SOW Language Recommendation**:
> "Phase 1 includes $177,750 investment in bridge functionality: $152,250 for temporary features (manual workflows, static availability, simplified contractor assignment) and $25,500 for abstraction layer architecture. Bridge functionality enables MVP launch 6-12 months earlier than waiting for FSM tool selection and API availability, generating estimated $2M+ in ad-hoc service revenue during transition period. Phase 2 rework budget of $46,000 (reduced from $96,000 through abstraction layers) covers replacement of temporary features when FSM tool and Duke APIs become available. Phase 2 work requires separate SOW and is not included in Phase 1 contract value."

#### 3. Manual Admin Workflows

**Risk**: Duke expects more automation than MVP delivers

**Reality**: Operations Manager manually processes all service requests (1-hour SLA)

**SOW Language Recommendation**:
> "Phase 1 Operations Manager role requires manual service request processing with 1-hour SLA: (1) Admin receives notification when customer books service, (2) Admin contacts primary contractor via email/phone within 1 hour, (3) Contractor responds within 24 hours with acceptance or alternative time, (4) Admin updates customer app status: 'Confirmed - [Contractor] - [Date/Time]', (5) Admin monitors service completion and updates app status: 'Completed'. Total time to confirmation: 24-48 hours. Automated contractor assignment (push notification, one-tap acceptance) and real-time status updates require FSM tool integration (Phase 2 scope)."

#### 4. No In-App Payment

**Risk**: Reduces conversion for non-native customers

**Impact**: May affect $25M ad-hoc revenue target

**SOW Language Recommendation**:
> "Phase 1 ad-hoc service payment processing: Contractors collect payment on-site at service completion. Customer app displays service cost and payment instructions: 'Total cost: $99. Payment collected by [Contractor Name] at service completion via cash, check, or credit card.' In-app payment processing (Apple Pay, Google Pay, credit card, ACH, utility bill payment for Duke/P&G customers) requires Phase 2 scope including payment gateway integration, PCI compliance certification, contractor payout workflows, and escrow account management. Phase 2 payment processing is not included in Phase 1 contract value."

### MEDIUM RISK ITEMS

#### 1. Limited Ad-Hoc Service Catalog
- Starting with only 5-10 services in 1-2 pilot markets
- SOW should specify phased rollout with Duke approval required for market expansion

#### 2. No Contractor Portal Changes
- Contractors continue using existing portal
- May create friction if contractors expect new tools
- **Mitigation**: Clearly communicate to contractors that Phase 1 has no changes to their workflow

#### 3. 90-Day Inspection Period
- Duke has 90 days to reject deliverables
- You must fix at your expense
- **Mitigation**: Define very clear acceptance criteria per sprint with bi-weekly demos to catch issues early

#### 4. SOC 2 / ISO 27001 Annual Certification
- **Cost**: $20K-40K annually at Orases expense
- **Risk**: Recurring cost not in project budget
- **Mitigation**: Budget separately for annual security compliance

#### 5. Security Event Liability
- Orases liable for ALL breach costs with no cap
- Includes: notification costs, credit monitoring, forensic investigation, legal fees, customer claims
- **Mitigation**: Ensure comprehensive cybersecurity insurance coverage

---

## SOW Drafting Recommendations

### Section 1: Scope of Work

**Must Include**:
- Detailed feature list with MVP limitations clearly stated
- 3-component architecture: Customer App, Admin Portal, NO Contractor Portal changes
- Manual admin workflows (service request processing, contractor coordination)
- API dependencies with manual fallbacks
- Limited ad-hoc service catalog (5-10 services, 1-2 markets)
- Payment processing: On-site collection only (Phase 1)
- Status updates: Manual admin updates (5 statuses only)
- Emergency services: Phone-only (not in-app)
- Bridge functionality with abstraction layers ($177,750)
- Phase 2 rework budget ($46,000 when FSM/APIs available)

### Section 2: Technical Specifications

**Frontend**:
- React Native (mobile apps - iOS/Android)
- Vue.js (web app - responsive PWA)
- Mobile-first design, WCAG 2.1 accessibility compliance
- Offline capability for key features

**Backend**:
- Laravel framework
- RESTful API architecture
- PostgreSQL or MySQL database
- Redis caching layer
- JWT/OAuth authentication

**Hosting**:
- AWS cloud infrastructure
- Multi-environment: Dev, Staging, Production
- Auto-scaling, load balancing
- CDN for static assets

**Security**:
- SOC 2 Type 2 OR ISO 27001 certification (annual, Orases expense)
- Multi-factor authentication (MFA)
- Encryption at rest and in transit (NIST standards)
- OWASP Top 10 compliance
- Role-based access control (RBAC) for 7 admin roles

**Integrations**:
- Duke Enterprise APIs (customer validation, HPP plans)
- CPSC recall database
- Barcode lookup APIs (UPC database)
- SMS gateway (Twilio or similar)
- Email service (SendGrid or similar)
- Push notifications (FCM for Android, APNs for iOS)

### Section 3: Deliverables

**Phase 1 Deliverables**:
1. Customer Mobile App (iOS native app - Swift/SwiftUI or React Native)
2. Customer Mobile App (Android native app - Kotlin or React Native)
3. Customer Web App (responsive PWA - Vue.js)
4. Admin Portal (7 user roles, RBAC, manual workflows)
5. Backend API infrastructure (Laravel, RESTful APIs)
6. Contractor matching algorithm (trade + zip code, primary/secondary)
7. Database schema & migrations (PostgreSQL/MySQL)
8. Cloud infrastructure (AWS: VPC, EC2/ECS, RDS, S3, CloudFront)
9. CI/CD pipeline (automated testing, deployment)
10. Source code repository (Git, full history, documentation)
11. Technical documentation (API docs, architecture diagrams, data models)
12. Admin user guides (role-specific training materials)
13. Security compliance documentation (SOC 2 Type 2 OR ISO 27001 certificate)
14. DevOps runbooks (deployment procedures, monitoring, incident response)

**Phase 2 Deliverables (Future SOW - NOT included in Phase 1 contract)**:
- FSM tool integration ($46K rework)
- In-app payment processing
- Contractor mobile app (real-time job acceptance, GPS tracking)
- Real-time GPS tracking ("pizza tracker")
- In-app ratings & reviews display
- Contractor marketplace
- AI virtual assistant

### Section 4: Timeline & Milestones

Based on Discovery document (44 weeks / 11 months):

| Phase | Weeks | Deliverables | Payment Milestone |
|-------|-------|--------------|-------------------|
| **Planning & Analysis** | 1-12 | Requirements finalization, architecture design, UI/UX wireframes, technical specs | 20% upon contract execution |
| **Design & Architecture** | 8-16 | UI/UX design approval, database schema, API specs, abstraction layer design | 20% upon design approval (Week 16) |
| **Development MVP** | 12-20 | Core features, customer app (iOS/Android/Web), admin portal (7 roles), contractor matching algorithm | - |
| **Alpha/Beta Development** | 20-28 | Alpha release (functional testing), Beta release (user acceptance testing), bug fixes | 30% upon Alpha release (Week 24) |
| **Testing & QA** | 24-36 | UAT, security testing, penetration testing, Duke compliance review, performance testing | 20% upon Beta release (Week 28) |
| **Deployment** | 36-40 | Production launch, app store submissions, monitoring setup, admin training | 10% upon production launch (Week 40) |
| **Warranty Support** | 40-44 | Bug fixes, stabilization, warranty support (90-day inspection period) | - |

**Key Milestones**:
- **Week 12**: Requirements sign-off, Duke APIs available (customer validation, HPP plans)
- **Week 16**: UI/UX design approval (Duke 2-week review cycle)
- **Week 20**: MVP Alpha release (functional testing begins)
- **Week 24**: Alpha approved, Beta release (UAT with Duke team)
- **Week 28**: Beta approved, Release Candidate ready
- **Week 32**: Security testing complete (SOC 2 Type 2 OR ISO 27001)
- **Week 36**: App store approvals (iOS App Store, Google Play Store)
- **Week 40**: Production launch, go-live
- **Week 44**: Warranty period ends (90-day inspection period from launch)

**Total Duration**: 44 weeks (11 months from contract execution)

### Section 5: Acceptance Criteria

**Must Define Sprint-Level Acceptance Criteria**:

**Sprint Acceptance (Bi-Weekly)**:
- Features functional per sprint scope
- Unit tests passing (>80% code coverage)
- No critical bugs (P0/P1)
- Code review completed
- Demo to Duke stakeholders with approval

**Alpha Release Acceptance (Week 24)**:
- All MVP features functional per spec
- Customer app: Registration, HPP management, home inventory, service booking (HPP + ad-hoc), notifications, maintenance reminders, gamification, service history
- Admin portal: All 7 user roles operational, manual service request processing workflow, contractor configuration, ad-hoc service catalog, analytics dashboard
- Contractor matching algorithm: 95%+ successful auto-assignment rate (trade + zip code)
- APIs functional: Duke Enterprise API integration (customer validation, HPP plans)
- Performance: <2 sec page load times, <200ms API response times
- Security: No critical vulnerabilities (OWASP Top 10)

**Beta Release Acceptance (Week 28)**:
- All Alpha criteria met
- User acceptance testing complete (Duke team testing with real data)
- Bug fixes from Alpha testing complete
- Integration testing complete (Duke Enterprise APIs, external services)
- Performance testing: Load testing (1,000 concurrent users), stress testing
- Security testing: Penetration testing complete, vulnerabilities remediated

**Production Launch Acceptance (Week 40)**:
- All Beta criteria met
- App store approvals: iOS App Store approved, Google Play Store approved
- Production infrastructure deployed: AWS production environment live, monitoring configured, backups operational
- Admin training complete: All 7 admin roles trained on portal usage
- Documentation delivered: Technical docs, API docs, admin user guides, runbooks
- Security compliance: SOC 2 Type 2 report OR ISO 27001 certificate provided
- Go-live checklist complete: Data migration validated (if applicable), integrations tested in production, incident response plan documented

**Warranty Period (Weeks 40-44 / 90 days from launch)**:
- Bug fixes for defects found during 90-day inspection period
- No additional feature development
- Performance optimization for production load
- Monitoring and incident response

**Performance Benchmarks**:
- Page load times: <2 seconds (mobile app), <3 seconds (web app)
- API response times: <200ms average, <500ms 95th percentile
- Uptime: 99.5% availability during business hours (6am-10pm ET)
- Concurrent users: Support 1,000 concurrent users without degradation
- Database queries: <100ms for 95% of queries

**Security Checklist**:
- OWASP Top 10 compliance
- Data encryption at rest and in transit
- Multi-factor authentication (MFA) functional for admin users
- Role-based access control (RBAC) enforced for 7 admin roles
- Secure API authentication (JWT tokens)
- Security headers configured (CSP, HSTS, X-Frame-Options)
- Vulnerability scan clean (no critical/high vulnerabilities)
- Penetration testing report with all findings remediated
- SOC 2 Type 2 OR ISO 27001 certification provided

### Section 6: Assumptions & Dependencies

**Critical Assumptions**:

1. **Duke Enterprise APIs available by Week 12**:
   - Customer Validation API (utility customer verification)
   - HPP Plan API (retrieve active subscriptions, plan details, coverage)
   - API documentation and sandbox access provided within 2 weeks of kickoff
   - If APIs not available: Manual fallback workflows implemented at no additional cost

2. **Service Request Creation API may NOT be available**:
   - If unavailable: Service requests created in app backend, admin manually processes via queue or CRM entry
   - Manual fallback acceptable for MVP

3. **Enrollment API may NOT be available**:
   - If unavailable: Admin manually processes enrollments (create in CRM, sync to billing, update app backend)
   - Manual fallback acceptable for MVP

4. **FSM tool integration deferred to Phase 2**:
   - Duke has not selected FSM tool (Service Power, Service Bench under evaluation)
   - Timeline: 6-12 months post-launch
   - Phase 2 rework: $46,000 (separate SOW required)

5. **Contractor portal changes deferred to Phase 2**:
   - Contractors continue using Commerce CRM portal (no changes)
   - Admin backend manages contractor configuration for app
   - Modern contractor mobile app is Phase 2 scope

6. **Duke provides contractor data export**:
   - Initial setup: Duke exports contractor data from CRM (CSV/JSON format)
   - Fields required: Contractor name, contact info, trades, service areas (zip codes), primary/secondary designation, availability rules, lead times
   - Provided by Week 4 of project

7. **Duke SMEs available for requirements validation**:
   - 10-15 hours/week for bi-weekly sprint reviews and demos
   - Key SMEs: Product Owner, Operations Manager, IT Lead, Business Analyst
   - 2-week turnaround for design approvals

8. **Duke IT provides sandbox access**:
   - Development environment access to Commerce CRM (for Duke customers)
   - Development environment access to Dynamics CRM (for P&G customers)
   - Test accounts for integration testing
   - VPN access to Duke network (if required)

9. **Duke legal review timelines**:
   - Customer communications (privacy notices, terms of service): 1-week turnaround
   - Marketing content (ad-hoc service descriptions): 3-business-day turnaround

10. **Duke security team approvals**:
    - Infrastructure architecture review: Week 8
    - Penetration testing approval: Week 32
    - Production launch approval: Week 36

**Dependencies (Risk if Not Met)**:

| Dependency | Owner | Required By | Risk if Not Met |
|------------|-------|-------------|-----------------|
| Duke Enterprise APIs available | Duke IT | Week 12 | Manual fallback workflows required (included in scope) |
| API documentation & sandbox access | Duke IT | Week 2 | Delays integration development (2-week slip) |
| Contractor data export (CSV/JSON) | Duke Ops | Week 4 | Cannot configure contractor matching algorithm (2-week slip) |
| UI/UX design approval | Duke Product | Week 16 | Delays development start (1:1 slip for each week of delay) |
| Duke SME availability for sprint reviews | Duke Team | Bi-weekly | Rework risk if requirements misunderstood |
| Test accounts for Commerce/Dynamics | Duke IT | Week 12 | Cannot test integrations (blocks Alpha release) |
| Duke legal review of customer comms | Duke Legal | Week 20 | Cannot launch without privacy notices (blocks launch) |
| Duke security approval of architecture | Duke Security | Week 8 | Rework risk if architecture changes required |
| App store developer accounts | Duke | Week 32 | Cannot submit apps for review (blocks launch) |
| Production infrastructure approval | Duke IT/Security | Week 36 | Cannot deploy to production (blocks launch) |

**Assumptions - Project Management**:
- Hybrid Agile methodology with 2-week sprints
- Bi-weekly sprint demos with Duke stakeholders
- Sprint retrospectives and planning sessions
- Change requests submitted via written Change Order (both parties sign)
- No scope changes during active sprint (defer to next sprint)

**Assumptions - Hosting & Operations**:
- Duke responsible for ongoing hosting costs: $800/month (includes beta + production environments)
- Duke responsible for optional support & maintenance: $6,500/month
- Orases responsible for SOC 2 Type 2 OR ISO 27001 annual certification: $20K-40K/year
- Hosting costs scale with user growth (200K to 2M users over 3 years)

### Section 7: Out of Scope (Explicitly State)

**Phase 1 Out of Scope (Require Separate SOW)**:

L **FSM Tool Integration**:
- Real-time contractor GPS tracking ("pizza tracker")
- Automated status updates from contractor
- Intermediate statuses: Dispatched, En Route, On-Site, In Progress
- Contractor mobile app with real-time job acceptance
- Dynamic contractor calendar sync

L **In-App Payment Processing**:
- Apple Pay, Google Pay, credit card processing
- Utility bill payment (Duke/P&G customers)
- ACH payment
- Contractor payout workflows
- Escrow account management
- PCI DSS compliance certification

L **Contractor Portal Rebuild**:
- New contractor mobile app
- Real-time job assignment notifications
- One-tap job acceptance/decline
- GPS tracking and check-in functionality
- In-app customer communication (chat)
- Photo upload for service completion

L **In-App Ratings & Reviews Display**:
- Customer ratings collection in-app
- Contractor ratings/reviews display during booking
- Star rating system
- Review moderation and flagging

L **Contractor Marketplace**:
- Customer ability to select from multiple contractors
- Contractor comparison (pricing, ratings, availability)
- Contractor profiles with photos, bio, specialties
- "Request quote" from multiple contractors

L **AI Virtual Assistant**:
- Conversational troubleshooting chatbot
- Natural language processing (NLP)
- AI-powered service recommendations

L **Advanced Analytics**:
- Predictive maintenance recommendations (machine learning)
- Customer lifetime value (CLV) modeling
- Churn prediction models
- A/B testing framework

L **IoT Integration**:
- Smart home device integration
- Real-time energy monitoring
- Automated alerts from connected devices

L **Phase 2 Rework ($46K)**:
- Replacement of temporary features when FSM/APIs available
- Requires separate SOW after FSM tool selection

**Permanently Out of Scope (Not Planned)**:

L **Commercial Properties**: Only residential properties supported

L **Unlicensed Trades**: No lawn care, painting, pest control, or other non-licensed services

L **Landlord/Property Management**: No bulk property management features, tenant management, or rent collection

L **Contractor Lead Generation**: No contractor marketplace where contractors pay Duke for job leads

L **White-Label Customization (Phase 1)**: Platform designed for white-label but customization for other utilities is Phase 2 scope

L **International Expansion**: U.S. only (English language, U.S. phone numbers, U.S. payment methods)

### Section 8: Change Management

**Change Order Process**:

1. **Change Request Submission**:
   - Either party submits written Change Order request
   - Include: Description of change, rationale, impact to scope/timeline/budget
   - Submit via email to designated project manager

2. **Impact Assessment**:
   - Orases provides written impact assessment within 5 business days
   - Include: Scope impact, timeline impact (weeks), budget impact (dollars), risks

3. **Approval**:
   - Duke reviews and approves/rejects Change Order
   - Both parties sign written Change Order
   - No work begins until Change Order executed

4. **Integration**:
   - Approved changes integrated into project plan
   - Sprint schedule adjusted if needed
   - Budget and timeline baseline updated

**Change Order Template**:
- Change Order ID
- Date submitted
- Submitted by (Duke or Orases)
- Description of change
- Rationale/business justification
- Scope impact (features added/removed/modified)
- Timeline impact (weeks delay or acceleration)
- Budget impact (additional cost or credit)
- Risks and dependencies
- Approvals (Duke signature, Orases signature)

**Emergency Changes**:
- Duke may issue written change directive for emergencies
- Orases must proceed with work immediately
- Impact assessment provided within 2 business days after emergency resolved
- Change Order executed retroactively

**Scope Clarifications (No Change Order Required)**:
- Minor clarifications that do not impact scope, timeline, or budget
- Documented via email or sprint notes
- Examples: Wording changes, UI tweaks, minor field additions

**Bridge Functionality Rework**:
- $46K Phase 2 rework budget already included in Phase 1 scope
- Triggered when FSM tool and Duke APIs become available (estimated 6-12 months post-launch)
- Requires separate Phase 2 SOW defining specific rework scope
- No Change Order required if rework stays within $46K budget

### Section 9: Payment Terms

**Total Project Cost: $788,600**

**Payment Schedule (Milestone-Based)**:

| Milestone | Deliverable | Amount | Percentage |
|-----------|-------------|--------|------------|
| Contract Execution | Signed SOW, project kickoff | $157,720 | 20% |
| Design Approval | UI/UX designs approved, technical specs finalized | $157,720 | 20% |
| Alpha Release | Functional Alpha release (Week 24) | $236,580 | 30% |
| Beta Release | Beta release with UAT complete (Week 28) | $157,720 | 20% |
| Production Launch | Production go-live (Week 40) | $78,860 | 10% |

**Additional Costs**:

| Item | Amount | Responsible Party | Frequency |
|------|--------|-------------------|-----------|
| **SOC 2 Type 2 Audit** | $20,000 - $40,000 | Orases | Annual |
| **ISO 27001 Certification** | $20,000 - $40,000 | Orases | Annual (alternative to SOC 2) |
| **Hosting (AWS)** | $800/month | Duke Energy | Monthly |
| **Support & Maintenance** | $6,500/month | Duke Energy | Monthly (optional) |

**Invoice Requirements**:
- Must reference Duke PO/Contract number
- Submitted upon milestone completion with supporting documentation
- Duke pays Net 90 days from receipt of correct invoice
- Final invoice due within 60 days of production launch (Week 40)

**Payment Terms from Master Services Agreement**:
- Net 90 days (calendar days from invoice receipt)
- Duke may withhold payment for disputed amounts
- Duke may offset from payment if Orases non-compliant with contract terms
- Time-and-materials work (if any) requires detailed timesheets with employee name, classification, hours worked, rate

**Expense Reimbursement**:
- Orases responsible for all project expenses unless otherwise agreed
- Travel expenses for on-site meetings (if required): Pre-approved by Duke, reimbursed per Duke Guidelines (Exhibit C)
- No expense reimbursement without prior written approval

**Late Payment**:
- No late payment fees or interest charges (per Master Services Agreement Section 2B)

**Tax Responsibility**:
- Orases responsible for all corporate and individual taxes
- Sales tax (if applicable) billed as separate line item on invoices
- Orases responsible for sales tax on materials/supplies/equipment purchased for project

### Section 10: Warranty & Support

**Warranty Period**: 90 days from production launch (Week 40-44 / through Week 52)

**Warranty Coverage (Per Master Services Agreement Section 5)**:

Orases warrants that:

1. **Professional Standards**: Services performed with high level of accepted professional standards by qualified personnel

2. **Conformance to Specifications**: Services and deliverables conform to SOW specifications and are free from errors and defects in workmanship and materials

3. **No Malicious Code**: Software does not contain trojan horses, viruses, disabling code, timers, clocks, counters, or other limiting routines

4. **No Infringement**: Software does not infringe upon patent, copyright, or other legal rights of any third party

5. **Authority to Contract**: Orases has authority to enter into SOW and performance is not prohibited by any other agreement

**Warranty Remedies**:
- Orases shall, at Duke's option, either **re-perform** or **refund** applicable fees for services/deliverables that fail to meet warranty
- Orases liable for **all damages** incurred by Duke from warranty breach (not limited to re-perform/refund)
- If Orases fails to commence corrective action: Duke may fix defects itself or hire third party and **back-charge Orases**

**Warranty Exclusions**:
- Defects caused by Duke modifications to deliverables
- Defects caused by third-party software/hardware
- Issues caused by Duke's failure to implement Orases recommendations
- Issues caused by Duke's IT environment (if outside Orases control)

**Post-Warranty Support (Optional)**:

After 90-day warranty period, Duke may opt for ongoing support:

**Support & Maintenance Plan**: $6,500/month (optional)

Includes:
- Bug fixes for defects discovered after warranty period
- Security patches and updates
- Performance optimization
- 8x5 support (business hours: Mon-Fri 8am-5pm ET)
- Email/phone support with 4-hour response time (business hours)
- Monthly status reports
- Quarterly product roadmap reviews

**NOT Included in Support Plan**:
- New feature development (requires separate SOW)
- Hosting infrastructure costs (Duke pays AWS directly: $800/month)
- Third-party API changes requiring rework
- Phase 2 rework when FSM/APIs available ($46K separate SOW)

### Section 11: Risk Allocation & Limitations

**Orases Responsibilities**:

 Orases responsible for:
- Software development per SOW specifications
- Quality assurance and testing
- Bug fixes during warranty period (90 days)
- Security compliance (SOC 2 Type 2 OR ISO 27001 annual certification at Orases expense)
- Source code delivery with full documentation
- Abstraction layer architecture to minimize Phase 2 rework
- Manual fallback workflows if Duke APIs not available
- Security breach notification costs (unlimited liability per Master Services Agreement)

**Duke Energy Responsibilities**:

 Duke responsible for:
- Duke Enterprise API availability (customer validation, HPP plans)
- API documentation and sandbox access within 2 weeks of kickoff
- Contractor data export (CSV/JSON) by Week 4
- SME availability for sprint reviews (10-15 hours/week)
- Design approval within 2 weeks
- Legal review of customer communications within 1 week
- Test accounts for Commerce/Dynamics integration testing
- App store developer accounts (iOS, Android)
- Production infrastructure approval
- Ongoing hosting costs ($800/month)
- Contractor participation in pilot program (~25 contractors)

**Shared Risks**:

  Both parties acknowledge:
- **API Availability Uncertainty**: Service Request Creation API and Enrollment API may not exist by MVP launch. Manual fallback acceptable (Orases implements at no additional cost).
- **FSM Tool Timing**: Duke has not selected FSM tool. Timeline: 6-12 months post-launch. Phase 2 rework ($46K) required when FSM available (separate SOW).
- **Third-Party Dependencies**: External services (CPSC recall database, barcode lookup APIs, SMS gateway, email service, push notification services) may experience outages. Orases not liable for third-party service failures.
- **Contractor Participation Risk**: Duke responsible for ensuring contractor participation in pilot program. If contractors do not use system, Orases not liable for low adoption.
- **Revenue Target Risk**: $25M ad-hoc service revenue and 250K non-native customer targets are Duke business goals. Orases not liable if targets not met (dependent on pricing, marketing, contractor availability, customer demand).

**Liability Limitations (Per Master Services Agreement)**:

  **Unlimited Liability for**:
- Security breaches (Orases pays ALL notification costs, credit monitoring, forensic investigations, legal fees, customer claims)
- IP infringement (Orases warrants no third-party infringement)
- Warranty breaches (Orases liable for all damages from defects)

 **Limited Liability for**:
- Third-party service failures (CPSC, barcode APIs, SMS, email, push notifications)
- Duke IT infrastructure issues (if outside Orases control)
- Contractor non-participation in pilot program
- Revenue targets not met (Duke's business risk)

### Section 12: Intellectual Property Rights

**Per Master Services Agreement Section 6**:

 **Duke Owns ALL Deliverables**:
- All rights, title, and interests in deliverables and intellectual property
- Includes: trademark rights, patent rights, copyrights, trade secret rights
- Deliverables deemed "works made for hire"
- Orases assigns all rights to Duke upon creation of each deliverable
- Includes all United States and international rights

**Orases Must Provide**:
- Full and complete source code for all deliverables
- All data, graphics, files used to create deliverables
- All files necessary for proper operation of deliverables
- Documentation of any pre-existing third-party software/libraries

**Pre-Existing Third-Party Software**:

Orases may incorporate pre-existing works (open-source libraries, frameworks) ONLY IF:
- Orases causes Duke to obtain **perpetual, irrevocable, nonexclusive, worldwide, royalty-free, fully paid-up license**
- Duke can use, copy, execute, reproduce, display, perform, distribute, create derivative works
- Duke can sublicense to others

**Pre-Existing Third-Party Software Likely Used**:
- Laravel framework (open-source, MIT license) 
- React Native (open-source, MIT license) 
- Vue.js (open-source, MIT license) 
- PostgreSQL or MySQL (open-source licenses) 
- Redis (open-source, BSD license) 
- Various npm packages and composer packages (verify licenses)  

**Orases Proprietary Code**:

If Orases uses any proprietary code/frameworks owned by Orases:
- Must grant Duke perpetual, royalty-free license
- Duke can use for this project and future projects
- Duke can modify and create derivative works
- Duke can sublicense to others (e.g., white-label to other utilities)

  **Risk**: Ensure ALL proprietary Orases code/frameworks have appropriate licenses granted to Duke

**Duke Data Remains Duke Property**:
- All customer data, HPP plans, contractor data, service requests remain Duke property
- Orases has no rights to Duke data
- Orases must return or destroy all Duke data upon project completion (per Section 10.1.I)

---

## Key Questions to Resolve Before Signing SOW

### 1. API Availability Timeline

**Question**: When will Duke have Service Request Creation API and Enrollment API ready?

**Why It Matters**:
- If APIs not available by launch, manual fallback required (included in scope)
- Manual fallbacks reduce operational efficiency (admin must manually process requests)
- Duke should confirm APIs will exist OR accept manual fallbacks for MVP

**Recommendation**: Include in SOW: "If Service Request Creation API or Enrollment API are not available by MVP launch (Week 40), Orases will implement manual admin queue processing workflows at no additional cost."

### 2. FSM Tool Selection

**Question**: What's Duke's timeline for selecting FSM tool (Service Power, Service Bench, other)?

**Why It Matters**:
- Drives Phase 2 timing and $46K rework scope
- Affects when temporary features can be replaced with automated workflows
- Contractor mobile app depends on FSM tool integration

**Recommendation**: Include in SOW: "FSM tool integration is Phase 2 scope. Orases will provide $46K rework proposal within 30 days of Duke notifying Orases of FSM tool selection."

### 3. Ad-Hoc Service Catalog Definition

**Question**: Who defines the initial 5-10 services and pricing for ad-hoc catalog?

**Options**:
- A) Duke defines services and pricing (Orases implements)
- B) Orases recommends services/pricing (Duke approves)
- C) Joint collaboration workshop

**Why It Matters**:
- Affects project timeline (if Duke defines, need time for internal approvals)
- Pricing strategy affects revenue targets ($25M ad-hoc services)
- Service scope of work definitions affect contractor participation

**Recommendation**: Include in SOW: "Duke Energy will define initial 5-10 ad-hoc services (service name, description, scope of work, pricing) by Week 8. Orases will provide service catalog template and recommendations for Duke's consideration."

### 4. Acceptance Criteria Details

**Question**: What are specific success metrics for MVP launch?

**Examples to Discuss**:
- 90% service request auto-assignment success rate?
- <3 min average booking time?
- 95% contractor acceptance rate?
- <2 sec page load time?
- 99.5% API uptime?

**Why It Matters**:
- Defines "done" for production launch milestone
- Avoids disputes during 90-day inspection period
- Clear targets for performance testing

**Recommendation**: Include detailed acceptance criteria table in SOW (see Section 5 above)

### 5. SOC 2 vs. ISO 27001

**Question**: Which security certification does Duke prefer?

**Options**:
- **SOC 2 Type 2**: More common for SaaS, U.S.-focused, ~$20K-30K annually
- **ISO 27001**: More global, internationally recognized, ~$30K-40K annually

**Why It Matters**:
- Orases pays for annual certification (Section 10.2 of Master Services Agreement)
- Affects Orases ongoing costs (not in project budget)
- Certification process takes 3-6 months (must start by Week 20 to have by Week 32)

**Recommendation**: Confirm Duke preference and include in SOW: "Orases will obtain [SOC 2 Type 2 OR ISO 27001] certification by Week 32, at Orases expense (~$20K-40K). Annual recertification required at Orases expense."

### 6. Phase 2 Commitment

**Question**: Is Duke committed to Phase 2 ($46K rework + in-app payment + contractor portal + FSM integration)?

**Why It Matters**:
- Affects Orases willingness to invest in abstraction layers ($25.5K)
- If Duke may not proceed with Phase 2, Orases has $152K in potentially wasted temporary features
- Business case ROI (11.7x) assumes Phase 2 proceeds

**Recommendation**: Get Duke commitment (even if non-binding) that Phase 2 is planned. Include in SOW: "Phase 1 bridge functionality investment of $177,750 assumes Duke Energy will proceed with Phase 2 FSM integration and temporary feature replacement within 12 months of Phase 1 launch. Phase 2 requires separate SOW."

### 7. Revenue Targets Are Aspirational

**Question**: Are $25M ad-hoc revenue and 250K non-native customer targets firm commitments or aspirational goals?

**Why It Matters**:
- Affects risk if MVP limitations (no in-app payment, no ratings, no contractor marketplace) impact conversion
- Orases should NOT be liable if revenue targets not met (Duke's business risk, not technical risk)

**Recommendation**: Include in SOW: "$25M ad-hoc service revenue and 250K non-native customer acquisition targets are Duke Energy business goals. Orases is not liable if targets not met, as achievement depends on factors outside Orases control (pricing strategy, marketing spend, contractor availability, customer demand, competitive landscape)."

### 8. Contractor Participation Commitment

**Question**: Will Duke ensure ~25 contractors participate in pilot program?

**Why It Matters**:
- MVP success depends on contractor network
- If contractors don't use system, customer experience suffers
- Orases cannot force contractor participation

**Recommendation**: Include in SOW: "Duke Energy is responsible for ensuring minimum 25 contractors participate in Phase 1 pilot program across 2 pilot markets. Orases will provide contractor onboarding materials and training but is not responsible for contractor adoption rates."

### 9. Third-Party Service Availability

**Question**: Does Duke accept risk of third-party service outages (CPSC, barcode APIs, SMS, email, push notifications)?

**Why It Matters**:
- Orases integrates with external services but doesn't control their uptime
- If CPSC recall database is down, recall checking feature unavailable
- If SMS gateway is down, text notifications fail

**Recommendation**: Include in SOW: "Third-party service integrations (CPSC recall database, barcode lookup APIs, SMS gateway, email service, push notification services) are outside Orases control. Orases will implement error handling and graceful degradation but is not liable for third-party service outages or API changes."

### 10. Data Migration Scope

**Question**: Is there existing customer data to migrate from Duke CRM systems to app backend?

**If Yes**:
- How many customer records?
- What data fields need to be migrated?
- Who is responsible for data cleansing?
- What is data quality (missing fields, duplicates, format inconsistencies)?

**Why It Matters**:
- Data migration not explicitly included in scope documents
- Can add significant effort (2-4 weeks) depending on data volume and quality
- Risk of project delay if data migration underestimated

**Recommendation**: Clarify data migration requirements. If data migration required, include in SOW with separate line item or exclude from Phase 1: "Phase 1 assumes no data migration from existing Duke CRM systems. Customers will create new profiles in app. Existing Duke/P&G customers will be linked to HPP plans via API lookup. If bulk data migration required, separate Change Order will be issued."

---

## Final Recommendations

### Before SOW Signing - Action Items

 **Schedule SOW Review Meeting with Duke**:
- Review this analysis document together
- Discuss 10 key questions above
- Align on acceptance criteria
- Confirm API availability timeline
- Clarify roles and responsibilities

 **Draft SOW Using This Analysis**:
- Use Section 1-12 recommendations above
- Include detailed acceptance criteria table
- Explicitly state MVP limitations (manual workflows, no FSM, no in-app payment, etc.)
- Include out-of-scope section
- Define Phase 2 rework trigger and budget

 **Legal Review**:
- Have Orases legal counsel review SOW
- Ensure alignment with Master Services Agreement terms
- Verify IP rights are clear (Duke owns all, Orases provides perpetual licenses for pre-existing code)
- Confirm unlimited liability for security breaches is acceptable (or negotiate cyber insurance requirement)
- Review warranty terms (re-perform or refund, but also liable for ALL damages)

 **Insurance Review**:
- Verify Orases has adequate cybersecurity insurance (covers breach notification costs, forensic investigations, legal fees)
- Verify Orases has adequate errors & omissions insurance
- Verify Orases has adequate general liability insurance
- Master Services Agreement likely requires specific coverage amounts (check Section 15 - not provided in this analysis)

 **Budget for Ongoing Costs**:
- SOC 2 Type 2 OR ISO 27001: $20K-40K annually (Orases pays)
- Annual recertification: $15K-25K (Orases pays)
- Not included in $788,600 project budget

 **Prepare for 90-Day Inspection Period**:
- Define very clear acceptance criteria per sprint to avoid surprises
- Plan for bi-weekly demos with Duke stakeholders to catch issues early
- Document all decisions and approvals in writing
- If Duke finds defects during 90-day period, you must fix at your expense

 **Phase 2 Commitment**:
- Get Duke commitment (even if non-binding) that Phase 2 is planned
- Without Phase 2, the $177,750 bridge investment has lower ROI
- Business case assumes $2M+ revenue during transition + Phase 2 rework proceeds

---

## Summary: What You're Committing To

### Deliverables
- Customer mobile app (iOS + Android native apps)
- Customer web app (responsive PWA)
- Admin portal (7 user roles, manual workflows)
- Backend API infrastructure (Laravel)
- Contractor matching algorithm (trade + zip code)
- Cloud infrastructure (AWS)
- Source code with full documentation
- Security compliance (SOC 2 Type 2 OR ISO 27001)

### What's Included
- Manual admin workflows (service request processing within 1-hour SLA)
- Manual API fallbacks (if Duke APIs not available)
- Bridge functionality ($177,750: $152K temporary features + $25.5K abstraction layers)
- Limited ad-hoc service catalog (5-10 services, 1-2 pilot markets)
- Basic contractor matching (trade + zip code, no marketplace)
- 5 basic statuses (no real-time tracking)
- Ratings collected (not displayed to customers)
- Emergency services phone-only (not in-app)

### What's NOT Included (Requires Phase 2 SOW)
- FSM tool integration ($46K rework when FSM available)
- In-app payment processing
- Contractor mobile app with real-time job acceptance
- Real-time GPS tracking ("pizza tracker")
- In-app ratings & reviews display
- Contractor marketplace (customer selects contractor)
- AI virtual assistant

### Risks You're Accepting
- **Unlimited liability for security breaches** (notification costs, credit monitoring, forensic investigations, legal fees, customer claims)
- **$46K rework** when FSM/APIs available (6-12 months post-launch)
- **67% obsolescence** of temporary features (reduced to $46K through abstraction layers)
- **Annual security compliance costs**: $20K-40K (SOC 2/ISO 27001 at Orases expense)
- **90-day inspection period**: Duke can reject deliverables, you must fix at your expense
- **Warranty liability**: Re-perform or refund PLUS liable for ALL damages from defects

### Risks Duke Is Accepting
- **Manual admin workflows** may reduce operational efficiency (target: 40% call center reduction may not be fully achieved)
- **No in-app payment** may reduce non-native customer conversion (affects $25M revenue target)
- **No contractor marketplace** may reduce customer satisfaction (no choice of contractor)
- **Limited ad-hoc service catalog** (5-10 services only at launch)
- **API availability uncertainty** (if APIs not available, manual fallbacks less efficient)
- **Contractor participation risk** (if contractors don't participate, customer experience suffers)

---

## Bottom Line

This is a **well-scoped, realistic MVP** with a clear path to Phase 2. The $788,600 budget is reasonable given the complexity (3-tier architecture, 7 admin roles, dual customer workflows, contractor matching algorithm, bridge functionality).

**The $177,750 bridge investment is justified** by $2M+ revenue during transition period (11.7x ROI).

**Your biggest risks**:
1. Unclear acceptance criteria ’ Duke rejects deliverables during 90-day inspection
2. Duke expects more automation than MVP delivers ’ Reputational risk
3. Unlimited security breach liability ’ Ensure adequate cyber insurance
4. Annual SOC 2/ISO 27001 costs ($20K-40K) ’ Not in project budget
5. $46K rework if Duke doesn't proceed with Phase 2 ’ Get commitment

**Recommended Next Steps**:
1. Schedule SOW review meeting with Duke
2. Resolve 10 key questions above
3. Draft SOW using this analysis (Sections 1-12)
4. Have Orases legal counsel review SOW
5. Verify insurance coverage (cyber, E&O, general liability)
6. Get Duke commitment on Phase 2 (even if non-binding)
7. Budget for annual security compliance ($20K-40K not in project budget)

**Success Factors**:
- Very clear acceptance criteria per sprint (avoid surprises)
- Bi-weekly demos with Duke stakeholders (catch issues early)
- Document ALL decisions and approvals in writing
- Proactive communication about manual workflows and MVP limitations
- Set realistic expectations (this is MVP, not full-featured system)

Good luck with the SOW negotiation! This is a complex project with significant scope, but the analysis shows you've thought through the risks and mitigation strategies. The key is making sure Duke understands and accepts the MVP limitations before you commit.
