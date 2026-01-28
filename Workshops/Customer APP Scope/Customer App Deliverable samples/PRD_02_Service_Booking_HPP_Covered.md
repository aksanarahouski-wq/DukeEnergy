# Product Requirements Document (PRD)
## Service Booking - HPP Covered Services

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

The Service Booking - HPP Covered Services feature enables 800K+ existing Duke Energy customers with Home Protection Plans to request service through the mobile app instead of calling. This feature represents the **core value proposition** of the Duke Residential Solutions app and directly addresses the #1 customer pain point: inability to self-service warranty claims.

### Key Features
- **Symptom-Based Service Request**: Customers describe issues in plain language (not technical diagnosis)
- **Coverage Eligibility Check**: App validates issue is likely covered under customer's active HPP
- **Automated Contractor Assignment**: Primary contractor assigned based on trade + zip code
- **Simplified Scheduling**: Customer selects date/time window based on contractor availability
- **$0 Customer Cost**: Covered services have no payment required at booking
- **Service Status Tracking**: Pending → Confirmed → Completed workflow

### Business Impact
- **Reduces service request time from 15 minutes (phone) to < 3 minutes (app)**
- **Reduces call center volume by 40%** by shifting 320K+ annual requests to self-service
- **Improves customer satisfaction**: 90% CSAT target for app-based service requests
- **Enables 24/7 booking**: Customers can request service anytime, not limited to call center hours

---

## Background and Problem Statement

### Current State

**Existing Process for HPP-Covered Service:**
1. Customer calls Duke Residential Solutions hotline (8am-8pm Mon-Fri)
2. Call center representative validates customer account and active HPP plans
3. CSR manually determines if issue is covered under plan
4. CSR looks up primary contractor for customer's trade + zip code
5. CSR calls contractor to schedule appointment
6. CSR calls customer back to confirm appointment (or emails)
7. **Total time: 15-20 minutes per service request**

**Current Pain Points:**
- **Phone-only service** - No digital self-service option
- **Business hours limitation** - Cannot request service evenings/weekends
- **Wait times** - 5-10 minute hold times during peak periods
- **Call-back delay** - 24-48 hours for appointment confirmation
- **No visibility** - Customers don't know which contractor is coming until callback

### Problems

**Problem 1: No Self-Service Option**
- 800K+ customers with HPP plans must call for every service request
- Average 1.2 service requests per customer per year = 960K annual calls
- Business impact: $20-30 per call in operational costs = $19-29M annually

**Problem 2: Business Hours Limitation**
- Call center operates 8am-8pm Mon-Fri (limited weekend hours)
- Customers discover issues evenings/weekends but must wait to call
- Business impact: Delayed service requests, customer frustration

**Problem 3: Lack of Transparency**
- Customers don't know which contractor will respond
- No visibility into contractor ratings or availability
- No confirmation until 24-48 hours later
- Business impact: 25% of callbacks result in reschedules (inconvenient times)

**Problem 4: Inefficient Resource Use**
- Manual contractor lookup and scheduling
- CSRs spend 60%+ of time on scheduling vs. complex issues
- Business impact: High operational costs, CSR burnout

### Impact if Not Addressed

- **Cannot justify app development** - 800K existing customers are primary user base
- **Continued high operational costs** - $19-29M annually in call center costs
- **Customer churn** - Competitors offer digital booking (Thumbtack, Angi, etc.)
- **Market perception** - "Duke is behind the times" compared to home service apps

---

## Goals and Objectives

### Primary Goals

1. **Enable Self-Service HPP Booking**: 80% of covered service requests submitted via app within 6 months
2. **Reduce Average Booking Time**: From 15 minutes (phone) to < 3 minutes (app)
3. **24/7 Availability**: Customers can book anytime, appointments confirmed within 24 hours
4. **Improve First-Time Resolution**: 90% of service requests require no customer support intervention

### Success Criteria

- ✅ 80% of app users successfully complete service booking without errors
- ✅ Average booking time < 3 minutes (target: 2 minutes)
- ✅ 90% of HPP-covered issues correctly identified as "likely covered" by app
- ✅ 95% of bookings confirmed within 24 hours (contractor acceptance)
- ✅ 90% customer satisfaction score for app-based bookings (vs. 75% phone baseline)
- ✅ Call center volume reduced by 40% within 3 months of launch

### Non-Goals (Out of Scope)

- ❌ Real-time contractor GPS tracking ("pizza tracker") - Phase 2 with FSM tool
- ❌ Customer selection of contractor (multiple options) - Phase 2 for ad-hoc services
- ❌ In-app messaging with contractor - Phase 2 enhancement
- ❌ Payment processing - Not needed for covered services ($0 customer cost)
- ❌ Emergency service booking - Emergency services routed to phone (safety)

---

## Target Users

### Primary Users

**1. Established Eleanor (Existing HPP Customer)**
- **Role**: 58-year-old homeowner with HomeWire + Heating & Cooling plans
- **Need**: Book HVAC repair quickly when system makes strange noise
- **Pain Point**: Must call during business hours, wait on hold, wait for callback
- **Benefit**: Book service in 2 minutes at 10pm when issue discovered

**2. Multi-Property Owner**
- **Role**: Customer with vacation home (also has HPP coverage)
- **Need**: Schedule water heater inspection at beach house from primary residence
- **Pain Point**: Must call separately for each property, explain which property each time
- **Benefit**: Switch property in app, book service instantly

### Secondary Users

**3. Duke Call Center Representatives**
- **Need**: Reduced call volume for routine service requests
- **Benefit**: Focus on complex issues, emergencies, and customer escalations

---

## Scope

### In Scope for MVP

**Service Request Intake**
- ✅ Trade/category selection (HVAC, Plumbing, Electrical, Appliance, Water Heater)
- ✅ Symptom-based issue description (dropdown + free text)
- ✅ Optional photo upload (up to 3 photos)
- ✅ Link to home inventory appliance (if already in profile)
- ✅ Emergency triage (route emergencies to phone, not in-app booking)

**Coverage Validation**
- ✅ Check customer's active HPP plans for selected property
- ✅ Match issue type to plan coverage (e.g., HVAC issue → H&C plan)
- ✅ Display coverage likelihood: "Likely Covered" or "May Not Be Covered"
- ✅ Caveat messaging: "Coverage determined by technician inspection"

**Contractor Assignment**
- ✅ Automated primary contractor lookup (trade + zip code)
- ✅ Display assigned contractor: company name, phone, description
- ✅ Small "Need different contractor?" link (routes to phone call, not in-app)

**Scheduling**
- ✅ Display available time windows based on trade-specific lead times:
  - HVAC: 1-2 business days
  - Plumbing: 3-5 business days
  - Electrical: 5-6 business days
  - Appliance: 2-3 business days
- ✅ Customer selects preferred date/time window (e.g., "Thursday 9am-12pm")
- ✅ Booking status: "Pending Confirmation" (admin contacts contractor)

**Communication & Status Updates**
- ✅ Booking confirmation notification (immediate)
- ✅ Appointment confirmed notification (within 24 hours)
- ✅ Service completed notification (after contractor marks complete)
- ✅ Multi-channel: Push, SMS, Email (per customer preference)

**Service History**
- ✅ Service record added to customer's history
- ✅ Details: Date, contractor, issue, status
- ✅ Exportable as PDF

### Out of Scope (Phase 2+)

**Advanced Features**
- ❌ Real-time contractor availability calendars - requires FSM tool
- ❌ GPS tracking and "pizza tracker" - requires FSM + contractor mobile app
- ❌ In-app messaging with contractor - Phase 2
- ❌ Customer contractor selection (multiple options) - Phase 2 for ad-hoc
- ❌ Contractor acceptance/rejection workflow - Phase 2 with FSM

**Payment Features**
- ❌ Payment processing - Not needed for covered services
- ❌ Excess charge collection - Contractor collects on-site if needed

---

## Functional Requirements

### FR-1: Service Request Initiation

**FR-1.1: Trade/Category Selection**
- User taps "Book Service" from app home screen
- System displays 5 service categories:
  - Heating & Cooling
  - Plumbing
  - Electrical
  - Appliances
  - Water Heater
- User selects category → Proceeds to issue description

**FR-1.2: Emergency Triage Questions**
- After trade selection, system asks qualifying questions:
  - **HVAC**: "Is your home below 60°F with freezing temps outside?" OR "Is it above 85°F indoors with extreme heat?"
  - **Electrical**: "Is anything sparking or smoking?" OR "Do you smell burning?"
  - **Gas/Water Heater**: "Do you smell gas?" OR "Do you hear hissing sounds?"
  - **Plumbing**: "Is there active flooding?" OR "Is water damage spreading?"
- **If YES to any**: Display emergency alert:
  - "⚠️ This appears to be an emergency. Please call us immediately at 1-800-XXX-XXXX"
  - **If gas-related**: "🚨 SAFETY ALERT: If you smell gas, evacuate immediately and call 1-800-GAS-LEAK"
  - App does NOT create service request
- **If NO**: Proceed to non-emergency booking flow

**FR-1.3: Symptom-Based Issue Description**
- System displays common symptoms for selected trade:
  - **HVAC**: Not cooling/heating, strange noise, not turning on, bad smell, high energy bills
  - **Plumbing**: Leaky faucet, clogged drain, running toilet, low water pressure, water heater issue
  - **Electrical**: Outlet not working, light switch broken, circuit breaker tripping, flickering lights
  - **Appliance**: Dishwasher not draining, refrigerator not cooling, oven not heating, washer not spinning
  - **Water Heater**: No hot water, lukewarm water, water heater leaking, strange noise
- User selects symptom from list OR selects "Other" to enter free text (255 char max)
- System stores issue description for contractor reference

**FR-1.4: Link to Home Inventory (Optional)**
- System checks if appliances/systems in home profile match selected trade
- **If YES**: Display "Select Appliance" dropdown with existing inventory
  - Example: "Which HVAC system?" → "Carrier Heat Pump (Main Floor)" | "Add New System"
- **If NO**: Prompt "Add basic details to help contractor (optional)"
- User can skip, contractor will collect details during visit

**FR-1.5: Photo Upload (Optional)**
- User can upload up to 3 photos of issue
- Photos help contractor understand problem before arrival
- Formats: JPG, PNG; Max 5MB per photo
- System displays photo thumbnails with "Remove" option

### FR-2: Coverage Eligibility Check

**FR-2.1: HPP Plan Lookup**
- System queries database for customer's active HPP plans for selected property
- Query: `SELECT * FROM hpp_plans WHERE property_id = ? AND status = 'Active'`
- Returns: List of active plans (HomeWire, Heating & Cooling, Appliance, Water Heater)

**FR-2.2: Coverage Matching Logic**
- System matches issue category to plan coverage:
  - **HVAC issue** + **Heating & Cooling Plan** = Likely Covered
  - **Plumbing issue** + **HomeWire Plan** = Likely Covered
  - **Electrical issue** + **HomeWire Plan** = Likely Covered
  - **Appliance issue** + **Appliance Plan** = Likely Covered
  - **Water Heater issue** + **Water Heater Plan** = Likely Covered
- **If NO matching plan**: Display "This service may not be covered. View ad-hoc pricing?"

**FR-2.3: Coverage Display**
- **If Likely Covered**:
  - Green checkmark icon
  - "This service is likely covered under your [Plan Name]"
  - "Estimated cost: $0"
  - Caveat: "Final coverage determined by technician inspection"
- **If NOT Covered**:
  - Yellow warning icon
  - "This service may not be covered by your current plans"
  - "Would you like to see ad-hoc pricing?"
  - Button: "View Pricing" (routes to ad-hoc service flow)

**FR-2.4: Coverage Edge Cases**
- **Pre-existing conditions**: Display disclaimer: "Services for pre-existing conditions may not be covered. Your technician will assess."
- **Plan limits**: If plan has claim limits (e.g., 2 per year), display: "You have 1 remaining service available this year"
- **Plan exclusions**: Link to full plan terms: "View what's covered"

### FR-3: Contractor Assignment

**FR-3.1: Primary Contractor Lookup**
- System queries contractor assignment database:
  - Input: `{trade: "HVAC", zipCode: "28202"}`
  - Query: `SELECT * FROM contractor_assignments WHERE trade = ? AND zip_code = ? AND designation = 'Primary'`
  - Returns: Primary contractor for trade + zip
- **If NO primary contractor found**: Fall back to secondary contractors

**FR-3.2: Contractor Display**
- System displays contractor card:
  - Company name: "ABC Heating & Cooling"
  - Company logo (if available)
  - Phone number: "(555) 123-4567"
  - Brief description: "Serving Charlotte since 2005. HVAC specialists."
  - Badge: "Your Recommended Contractor"
- **Note**: NO star ratings displayed in MVP (ratings collected externally)

**FR-3.3: Alternative Contractor Request**
- Small link below contractor card: "Need a different contractor?"
- Tapping link displays modal:
  - "We've pre-assigned the best contractor for your area."
  - "If you'd prefer someone else, please call us at 1-800-XXX-XXXX"
  - Button: "Call Now" (initiates phone call)
- **Why limited**: Negotiated pricing, SLA contracts, coverage exceptions

### FR-4: Scheduling

**FR-4.1: Availability Window Calculation**
- System calculates available windows based on trade-specific lead times:
  - **HVAC/Water Heater**: Starting 1 business day out (emergency priority)
  - **Plumbing**: Starting 3 business days out
  - **Electrical**: Starting 5 business days out
  - **Appliance**: Starting 2 business days out
- System generates date options for next 14 days
- Time windows: Morning (8am-12pm), Afternoon (1pm-5pm)

**FR-4.2: Calendar Display**
- System displays calendar view with available dates highlighted
- User taps date → Time window options display
- Example: "Thursday, March 15"
  - 8am-12pm (available)
  - 1pm-5pm (available)
- User selects: "Thursday 9am-12pm"

**FR-4.3: Scheduling Constraints**
- System does NOT check real-time contractor availability (no FSM tool in MVP)
- Static availability buffers used
- Contractor may propose alternative time after manual review

**FR-4.4: Confirmation Display**
- Summary screen:
  - Service: Heating & Cooling Repair
  - Issue: "Strange grinding noise when AC turns on"
  - Contractor: ABC Heating & Cooling
  - Date/Time: Thursday, March 15, 9am-12pm
  - Cost: $0 (covered under plan)
  - Photos: 2 photos attached
- Button: "Confirm Booking"

### FR-5: Booking Confirmation & Status Updates

**FR-5.1: Booking Creation**
- User taps "Confirm Booking"
- System creates service order record:
  - Order ID: AUTO-GENERATED
  - Customer ID, Property ID
  - Trade, Issue Description
  - Selected Contractor ID
  - Requested Date/Time
  - Coverage Type: "HPP-Covered"
  - Status: "Pending Confirmation"
- System sends order to Duke Commerce/Dynamics API: `POST /orders/create`

**FR-5.2: Immediate Confirmation**
- System displays confirmation screen:
  - Order number: #12345678
  - "Your service request has been received!"
  - "ABC Heating will contact you within 24 hours to confirm your appointment"
  - Button: "Add to Calendar"
  - Button: "View Service Details"
- System sends push notification: "Service request received! We'll confirm your appointment soon."
- System sends SMS/email confirmation (per customer preference)

**FR-5.3: Admin Manual Confirmation Process** (MVP)
- Duke admin team receives notification of new booking
- Admin manually contacts contractor (email/phone) within 1 hour
- Contractor responds within 24 hours (accepts or proposes alternative time)
- Admin updates order status in system

**FR-5.4: Appointment Confirmed Notification**
- Admin updates order status: "Confirmed"
- System sends notification to customer:
  - Push: "Your appointment is confirmed! ABC Heating on Thursday 9am-12pm"
  - SMS: "Confirmed: ABC Heating, March 15, 9-12am. Call them at (555) 123-4567"
  - Email: Full appointment details with calendar invite
- Customer can view appointment details in "My Appointments" section

**FR-5.5: Service Completed Notification**
- After contractor marks job complete in Commerce CRM:
- Admin updates order status: "Completed"
- System sends notification: "Your service has been completed!"
- Service record added to customer's service history
- Survey link sent via external process (email/SMS)

**FR-5.6: Status Tracking in App**
- Customer can view service status in "My Appointments":
  - **Pending Confirmation**: "We're contacting your contractor"
  - **Confirmed**: "Scheduled - ABC Heating - March 15, 9-12am"
  - **Completed**: "Service completed on March 15"
- Limited status updates in MVP (no "Dispatched", "En Route", "On-Site" without FSM)

### FR-6: Rescheduling & Cancellation

**FR-6.1: Customer-Initiated Reschedule**
- Customer taps appointment in "My Appointments" → "Reschedule" button
- **If >24 hours before appointment**:
  - Display same calendar/time selection flow
  - User selects new date/time
  - System updates order, notifies admin
  - Admin contacts contractor to confirm new time
- **If <24 hours before appointment**:
  - Display: "Please call us to reschedule within 24 hours: 1-800-XXX-XXXX"

**FR-6.2: Customer-Initiated Cancellation**
- Customer taps appointment → "Cancel Service" button
- **If >24 hours before appointment**:
  - Confirmation modal: "Are you sure you want to cancel?"
  - User confirms → Order status: "Cancelled by Customer"
  - System notifies admin, admin notifies contractor
- **If <24 hours before appointment**:
  - Display: "Please call us to cancel within 24 hours: 1-800-XXX-XXXX"
  - No-show policy displayed (future: may charge fee)

**FR-6.3: Contractor-Initiated Reschedule** (Rare)
- Admin receives reschedule request from contractor
- Admin calls customer to propose new time
- **If customer accepts**: Admin updates order with new time
- **If customer declines**: Admin tries backup contractor
- System sends notification: "Your appointment has been rescheduled to Friday 1-4pm"

### FR-7: Service History

**FR-7.1: Service Record Details**
- After service completion, record added to "Service History":
  - Date: March 15, 2026
  - Contractor: ABC Heating & Cooling
  - Service Type: Heating & Cooling Repair
  - Issue: Strange grinding noise
  - Status: Completed
  - Cost: $0 (covered under plan)
  - Photos: 2 photos (if uploaded)
- Linked to HVAC appliance in home inventory (if applicable)

**FR-7.2: Exportable History**
- User can tap service record → "Export as PDF"
- PDF includes all service details
- Use case: Home sale documentation

---

## Dependencies and Risks

### Dependencies

**Internal Dependencies:**
1. **Customer Registration & Onboarding**
   - Users must have accounts and linked HPP plans
   - **Mitigation:** Registration is Deliverable #1, must be complete first

2. **Duke Commerce/Dynamics API**
   - Order creation API: `POST /orders/create`
   - Contractor lookup API: `GET /contractors?trade={}&zip={}`
   - **Mitigation:** Mock APIs for development, real integration in staging

3. **Admin Portal for Manual Confirmation**
   - Duke admin team needs interface to view pending bookings, update statuses
   - **Mitigation:** Build simple admin dashboard in parallel

**External Dependencies:**
1. **Contractor Participation**
   - Contractors must respond to appointment requests within 24 hours (95% acceptance target)
   - **Mitigation:** SLA contracts with contractors, penalties for non-response

2. **Duke Call Center Support**
   - Call center must handle exceptions (reschedules, contractor alternatives, emergencies)
   - **Mitigation:** Train CSRs on app flow, provide scripts

### Risks

#### HIGH RISK: Contractor Non-Acceptance

**Description:** Contractor doesn't accept appointment within 24 hours (system assumes acceptance)
**Impact:** High - Customer expects confirmation, contractor doesn't show
**Probability:** Medium (target 95% acceptance, but 5% edge cases)
**Mitigation:**
- Admin team monitors pending bookings, follows up with contractors
- Backup contractor assignment if primary doesn't respond
- Customer notification if rescheduling needed
- Escalation process for non-responsive contractors (SLA violation)

#### MEDIUM RISK: Coverage Miscategorization

**Description:** App says "Likely Covered" but technician determines not covered on-site
**Impact:** Medium - Customer expectation mismatch, potential conflict
**Probability:** Low-Medium (10-15% of cases may have coverage ambiguity)
**Mitigation:**
- Clear caveat messaging: "Final coverage determined by technician"
- Train technicians to explain coverage politely
- Customer can dispute via customer service if disagreement
- Track miscategorization rate, refine logic over time

#### MEDIUM RISK: Scheduling Conflicts (No Real-Time Calendar)

**Description:** Customer books time slot, but contractor actually unavailable
**Impact:** Medium - Requires rescheduling, customer frustration
**Probability:** Medium (20-30% of bookings may need time adjustment)
**Mitigation:**
- Set customer expectation: "Pending Confirmation" status
- Admin confirms actual availability before customer notification
- Offer alternative times quickly if conflict
- Phase 2: FSM tool provides real-time calendars

---

## Implementation Plan

### Phase 1: Core Booking Flow
- [ ] Backend: Service order database schema
- [ ] Backend: Order creation API (`POST /orders/create`)
- [ ] Mobile: Service category selection UI
- [ ] Mobile: Issue description form (symptoms, photos)
- [ ] Mobile: Coverage check display
- [ ] Integration: Duke Commerce API (order creation)

### Phase 2: Contractor Assignment & Scheduling
- [ ] Backend: Contractor assignment logic (trade + zip lookup)
- [ ] Backend: Availability window calculation (trade-specific lead times)
- [ ] Mobile: Contractor display card
- [ ] Mobile: Calendar and time selection UI
- [ ] Mobile: Booking confirmation screen

### Phase 3: Status Tracking & Notifications
- [ ] Backend: Notification service (push, SMS, email)
- [ ] Backend: Order status update API
- [ ] Mobile: "My Appointments" list view
- [ ] Mobile: Appointment details view with reschedule/cancel buttons
- [ ] Integration: Email service (SendGrid/AWS SES)

### Phase 4: Service History & Admin Tools
- [ ] Backend: Service history API
- [ ] Mobile: Service history list view
- [ ] Mobile: Service record detail view
- [ ] Mobile: Export PDF functionality
- [ ] Admin Portal: Pending bookings dashboard (simple web app)

**Total Estimated Timeline:** To be determined during sprint planning

---

## Success Metrics

### Key Performance Indicators (KPIs)

**Performance Metrics:**
- Booking completion rate: Target 80%+
- Average booking time: Target < 3 minutes
- Contractor acceptance rate: Target 95%+
- Time to appointment confirmation: Target < 24 hours (90% of bookings)

**User Adoption Metrics:**
- App-based bookings: Target 60% of total service requests within 3 months
- Call center volume reduction: Target 40% within 3 months
- Repeat booking rate: Target 70% (customers book again via app)

**Business Metrics:**
- Customer satisfaction: Baseline 75% (phone) → Target 90% (app)
- Operational cost per booking: Baseline $20-30 (phone) → Target $5-10 (app)

### Measurement Plan

- **Measurement Period:** Post-launch monitoring period TBD
- **Review Cadence:** Regular reviews during initial rollout, ongoing monitoring thereafter
- **Success Threshold:** 60% adoption + 90% CSAT + 40% call center reduction

---

## Open Questions

### 1. Emergency Service Threshold
- **Question:** Where is the line between "urgent" (can book in app) vs. "emergency" (must call)?
- **Options:**
  - **Option A**: Strict emergency definition (safety only) → Most services bookable in app
  - **Option B**: Broad emergency definition (customer discomfort) → More routed to phone
- **Decision Needed By**: UAT phase
- **Decision Owner**: Duke Customer Service Lead

### 2. Contractor Alternative Request Process
- **Question:** Should we allow in-app contractor selection for MVP or always route to phone?
- **Options:**
  - **Option A**: Always route to phone → Simpler MVP, consistent with negotiated contracts
  - **Option B**: Show 2-3 contractor options in app → Better UX, more complex logic
- **Decision Needed By:** Design review
- **Decision Owner:** Duke Product Owner

### 3. Coverage Disclaimer Placement
- **Question:** How prominently should we display coverage disclaimers?
- **Discussion Points:**
  - Too prominent: May scare customers away from booking
  - Too subtle: Customers surprised when technician says not covered
- **Decision Needed By:** Legal review
- **Decision Owner:** Duke Legal + UX Lead

---

END OF DOCUMENT
