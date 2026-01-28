# Product Requirements Document (PRD)
## Customer Registration & Onboarding

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
5. [User Stories](#user-stories)
6. [Scope](#scope)
7. [Functional Requirements](#functional-requirements)
8. [Technical Design](#technical-design)
9. [Testing Requirements](#testing-requirements)
10. [Dependencies and Risks](#dependencies-and-risks)
11. [Implementation Plan](#implementation-plan)
12. [Success Metrics](#success-metrics)
13. [Open Questions](#open-questions)

---

## Executive Summary

The Customer Registration & Onboarding feature establishes the foundation for the Duke Energy Residential Solutions Home Services Mobile App by enabling all prospective users to create accounts, validate their Duke Energy customer status, and set up their home profiles. This feature serves three distinct customer segments: existing Duke/Piedmont customers with Home Protection Plans (HPPs), existing Duke/Piedmont customers without HPPs, and non-native customers outside Duke's utility service areas.

### Key Features
- **Self-Service Account Creation**: Email/password-based registration with optional social login
- **Duke Enterprise Validation**: API integration to link app profiles to existing Duke utility accounts and HPP plans
- **Multi-Property Support**: Customers with multiple premises can manage all properties from single profile
- **Guided Onboarding Flow**: Progressive profiling that collects minimum required information upfront
- **Guest Access** (Limited): Browse DIY content without account creation

### Business Impact
- **Enables 800K+ existing HPP customers** to self-serve via mobile app (currently phone-only)
- **Acquisition channel for 250K non-native customers** within 24 months
- **Reduces call center volume by 40%** by shifting service requests from phone to app
- **Foundation for all downstream features**: service booking, home inventory, payments, notifications

---

## Background and Problem Statement

### Current State

**Existing Duke/Piedmont Customers:**
- 800K+ customers with active Home Protection Plans (HPPs)
- Average 1.7 plans per customer (HomeWire, Heating & Cooling, Appliance, Water Heater)
- Currently **phone-only** service request process (15-minute average call time)
- No self-service portal or mobile app
- Customer data exists in Duke Enterprise systems (Commerce/Dynamics/SAP)

**Non-Native Customers:**
- Potential market of millions outside Duke's utility service territories
- No existing relationship with Duke Energy
- Must discover Duke Residential Solutions via web search, ads, or referrals
- Seeking reliable, transparent home service providers

**Onboarding Friction:**
- Current process requires customers to call to schedule service
- No way to verify customer identity or link HPP plans without phone call
- Customers with multiple properties must manage each separately
- No digital home profile or service history

### Problems

**Problem 1: No Digital Identity for Customers**
- Duke Residential Solutions customers have no way to create digital profiles
- Existing HPP plans not accessible online
- Service history scattered across phone records and contractor notes
- Business impact: Cannot enable self-service features without digital identity

**Problem 2: Manual Customer Validation Process**
- Call center representatives manually validate customer information against Duke systems
- 5-10 minutes per call spent on identity verification
- Prone to errors (wrong address, misspelled names, duplicate accounts)
- Business impact: High operational costs, poor customer experience

**Problem 3: Multi-Property Customers Underserved**
- Customers with vacation homes or rental properties must call separately for each
- No unified view of all properties and HPP plans
- Business impact: Friction for 15-20% of customer base with multiple properties

**Problem 4: Non-Native Customer Acquisition Barrier**
- No digital entry point for customers outside Duke utility territories
- Must call to inquire about services (high-friction)
- Perceived as "Duke customers only" due to brand association
- Business impact: Missing $25M+ addressable market for ad-hoc services

### Impact if Not Addressed

- **Cannot launch self-service app** - all downstream features depend on registration
- **Lost revenue opportunity** - $25M in ad-hoc service revenue inaccessible
- **Call center overload** - 800K customers continue phone-based service requests
- **Competitive disadvantage** - Home service competitors already offer digital signup

---

## Goals and Objectives

### Primary Goals

1. **Enable Self-Service Account Creation**: All customer types can create profiles in < 3 minutes
2. **Automate Duke Customer Validation**: API integration reduces validation time from 5 minutes to < 5 seconds
3. **Support Multi-Property Management**: Single account can manage 2+ properties without friction
4. **Reduce Call Center Volume**: Shift 60% of account creation from phone to app within 6 months

### Success Criteria

- ✅ 95% of account creation attempts complete successfully without errors
- ✅ 90% of Duke/Piedmont customers successfully linked to existing HPP plans via API
- ✅ 80% of multi-property customers have all properties registered within first session
- ✅ Account creation time averages < 3 minutes (target: 2 minutes)
- ✅ 70% of new users complete onboarding without contacting support
- ✅ Non-native customers can create accounts with zero Duke Enterprise dependencies

### Non-Goals (Out of Scope)

- ❌ Social media login (Facebook, Google) - Phase 2 enhancement
- ❌ Biometric authentication (FaceID, TouchID) during registration - comes after account creation
- ❌ Multi-factor authentication (MFA) - Phase 2 security enhancement
- ❌ Landlord/property manager bulk account creation - commercial properties out of scope
- ❌ Account merging (combining duplicate accounts) - handled by Duke IT, not in-app

---

## Target Users

### Primary Users

**1. Established Eleanor (Existing Duke HPP Customer)**
- **Role**: 58-year-old homeowner with Duke/Piedmont utility service and 2 HPP plans
- **Need**: Digital access to existing plans and service history; self-service booking
- **Pain Point**: Must call for every service request; no visibility into service history
- **Benefit**: Create profile once, see all plans automatically linked; book services anytime

**2. Expanding Emma (New Duke Customer)**
- **Role**: 34-year-old first-time homeowner; Duke utility customer; no HPP yet
- **Need**: Easy signup to explore service options and preventative maintenance
- **Pain Point**: Unclear what services are available; hesitant to commit to plans without trying first
- **Benefit**: Try ad-hoc services before committing; transparent pricing; build trust

**3. Non-Native Nathan (Outside Duke Territory)**
- **Role**: 41-year-old homeowner in Florida (non-Duke territory); frustrated with unreliable contractors
- **Need**: Reliable home services with transparent pricing and vetted contractors
- **Pain Point**: Doesn't know Duke Residential Solutions exists; assumes "Duke customers only"
- **Benefit**: Access same vetted contractor network; clear pricing; no utility requirement

### Secondary Users

**4. Multi-Property Owner**
- **Role**: Customer with vacation home or rental property (15-20% of Duke customer base)
- **Need**: Manage service across multiple properties from one account
- **Pain Point**: Must call separately for each property; no unified view
- **Benefit**: Add multiple properties to single profile; switch between properties easily

---

## User Stories

**As an existing Duke HPP customer**, I want to create an app profile that automatically links my existing plans, so that I can book services without calling.

**As a new Duke utility customer**, I want to explore available services before committing to a plan, so that I can make informed decisions.

**As a non-native customer**, I want to sign up without being a Duke utility customer, so that I can access reliable home services in my area.

**As a customer with multiple properties**, I want to manage all my homes from one account, so that I don't have to juggle multiple logins.

**As a Duke customer**, I want the app to pre-fill my information from Duke systems, so that I don't have to manually enter data Duke already has.

---

## Scope

### In Scope

**User Account Creation**
- ✅ Email/password registration flow
- ✅ Password validation (8+ chars, uppercase, number, special char)
- ✅ Email verification via confirmation link
- ✅ Username uniqueness checking
- ✅ Terms of Service and Privacy Policy acceptance

**Duke Enterprise Validation**
- ✅ API integration to validate customer against Duke Commerce/Dynamics
- ✅ Automatic HPP plan linking for existing customers
- ✅ Address validation against Duke premise database
- ✅ Multi-premise detection and linking
- ✅ Non-native customer flag (no Duke utility account)

**Profile Setup**
- ✅ Minimum required fields: Name, Email, Phone, Home Address
- ✅ Optional fields: Date of Birth, Preferred Communication Channel
- ✅ Multi-property addition during onboarding
- ✅ Property type selection (single-family, condo, townhouse, mobile home)

**Onboarding Flow**
- ✅ Welcome screen with value proposition
- ✅ Guided address entry with autocomplete
- ✅ HPP plan display (if applicable)
- ✅ Home profile incentive messaging (gamification preview)
- ✅ Skip option for optional steps

**Guest Access**
- ✅ Browse DIY content library without login
- ✅ View service catalog pricing (limited)
- ✅ "Create Account to Book" prompts

### Out of Scope (Future Enhancements)

**Social Login**
- ❌ Sign up with Google/Apple/Facebook - Phase 2

**Advanced Security**
- ❌ Multi-factor authentication (SMS, authenticator app) - Phase 2
- ❌ Biometric login during registration - Phase 2

**Payment Information**
- ❌ Credit card entry during registration - collected at time of booking

**Commercial Accounts**
- ❌ Landlord/property manager bulk registration - separate commercial product

---

## Functional Requirements

### FR-1: Account Registration

**FR-1.1: Email/Password Registration**
- System shall provide registration form with fields: Email, Password, Confirm Password, First Name, Last Name, Phone Number, Home Address
- System shall validate email format (RFC 5322 standard)
- System shall validate password meets complexity requirements:
  - Minimum 8 characters
  - At least 1 uppercase letter
  - At least 1 number
  - At least 1 special character (!@#$%^&*)
- System shall check email uniqueness before account creation
- System shall display inline validation errors in real-time

**FR-1.2: Email Verification**
- System shall send verification email upon registration
- Email shall contain 6-digit verification code valid for 24 hours
- User can request new code if expired
- Account marked "unverified" until email confirmed
- Unverified accounts can log in but see banner prompting verification

**FR-1.3: Terms and Privacy Acceptance**
- System shall display Terms of Service and Privacy Policy links
- User must check "I agree to Terms and Privacy Policy" before submitting registration
- System shall record acceptance timestamp and ToS/Privacy version number

**FR-1.4: Address Entry with Autocomplete**
- System shall integrate Google Maps Autocomplete API for address entry
- User types address, sees dropdown with suggestions
- Selecting suggestion auto-fills: Street, City, State, Zip Code
- System shall validate zip code is 5 digits
- System shall allow manual entry if autocomplete doesn't find address

### FR-2: Duke Enterprise Validation

**FR-2.1: Customer Validation API Integration**
- System shall call Duke Enterprise API: `POST /customer/validate`
- Request payload: `{"firstName": "John", "lastName": "Doe", "address": "123 Main St", "zipCode": "28202"}`
- API response includes:
  - `customerExists`: true/false
  - `customerId`: Duke Enterprise customer ID
  - `accountType`: "Duke" | "Piedmont" | "None"
  - `premises`: array of addresses linked to customer
  - `activePlans`: array of HPP plans
- System shall handle API timeouts (5-second timeout, retry once)

**FR-2.2: HPP Plan Linking**
- If API returns `activePlans`, system shall display plans on confirmation screen:
  - "Great news! We found 2 plans linked to your account:"
  - HomeWire Protection Plan - Active
  - Heating & Cooling Plan - Active
- System shall store plan IDs in user profile for future reference
- Plans displayed in "My Account" section post-registration

**FR-2.3: Multi-Property Detection**
- If API returns multiple premises, system shall display:
  - "We found 2 properties associated with your account. Would you like to add both?"
  - Checkbox for each property
  - User can select which properties to link
- System shall create separate property records for each selected premise

**FR-2.4: Non-Native Customer Handling**
- If API returns `customerExists: false`, system shall flag account as "Non-Native"
- Non-native customers skip Duke validation step
- System shall display: "Welcome! You're all set. Start exploring services in your area."

### FR-3: Multi-Property Support

**FR-3.1: Property Addition During Onboarding**
- After primary address validated, system shall offer: "Do you have additional properties?"
- User can add vacation homes, rental properties, etc.
- System shall validate each additional address via Google Maps API
- System shall NOT validate additional properties against Duke Enterprise (may be out of territory)

**FR-3.2: Property Management**
- Each property record includes:
  - Nickname (optional): "Main House", "Beach House", "Rental Property"
  - Full address
  - Property type: Single-family / Condo / Townhouse / Mobile Home / Apartment
  - Primary property flag (default: first property added)
- User can switch between properties via dropdown in app header

**FR-3.3: Property-Level Plan Association**
- HPP plans linked to specific property (premise ID)
- Multi-property customers see which plans cover which properties
- Service requests tied to selected property

### FR-4: Onboarding Flow & Progressive Profiling

**FR-4.1: Welcome Screen**
- Display value proposition:
  - "Book home services in minutes"
  - "Track service history and warranties"
  - "Earn rewards for home maintenance"
- "Get Started" button proceeds to registration

**FR-4.2: Minimum Required Information**
- Step 1: Email, Password (account creation)
- Step 2: Name, Phone Number (contact info)
- Step 3: Home Address (service location)
- Optional: Date of Birth, Preferred Communication Channel

**FR-4.3: Duke Validation Feedback**
- If Duke customer found:
  - "We found your Duke Energy account! Your plans are linked."
  - Display linked HPP plans
- If not found:
  - "No problem! You can still use all our services."
  - Proceed to home profile incentive

**FR-4.4: Home Profile Incentive Messaging**
- Display after registration complete:
  - "Want to unlock the full experience?"
  - "Build your home profile and earn $10 credit toward first service"
  - "Start Now" or "Do This Later" buttons
- "Do This Later" proceeds to app home screen

**FR-4.5: Skip Options**
- Users can skip optional steps (Date of Birth, additional properties)
- Skipped steps can be completed later in "My Account" settings

### FR-5: Guest Access (Limited)

**FR-5.1: Guest Browsing**
- Users can browse DIY content library without logging in
- Users can view service categories and descriptions (no pricing)
- "Book Service" or "View Pricing" buttons prompt: "Create an account to continue"

**FR-5.2: Registration Prompts**
- System shall display "Create Account" prompts when guest attempts restricted actions:
  - Booking service
  - Viewing contractor details
  - Accessing loyalty rewards
  - Viewing full pricing
- Prompt includes value proposition and "Sign Up" button

### FR-6: Data Validation and Integrity

**FR-6.1: Input Validation**
- Email: Valid RFC 5322 format, max 255 characters
- Phone: 10 digits (US format), formatted as (XXX) XXX-XXXX
- Password: 8-128 characters, meets complexity rules
- Name fields: 2-50 characters, alphabetic with spaces/hyphens allowed
- Address: Validated via Google Maps API

**FR-6.2: Duplicate Account Prevention**
- System shall check email uniqueness before registration
- If email exists, display: "An account with this email already exists. Try logging in or reset your password."
- System shall check phone number uniqueness (warning, not blocking)
- If phone exists, display warning: "This phone number is associated with another account. Continue anyway?"

**FR-6.3: Error Handling**
- Duke API unavailable: Allow registration, defer validation
- Google Maps API unavailable: Fall back to manual address entry
- Email service unavailable: Allow registration, queue verification email for retry

---

## Technical Design

### High-Level Architecture

```
[Mobile App] <-> [API Gateway] <-> [Auth Service]
                                <-> [Duke Enterprise API]
                                <-> [Google Maps API]
                                <-> [Customer Profile Service]
                                <-> [Email Service]
```

**Components:**
1. **Auth Service**: Handles registration, login, password management
2. **Customer Profile Service**: Stores and manages user profiles and properties
3. **Duke Enterprise API**: Validates customers and retrieves HPP plans
4. **Google Maps API**: Address autocomplete and validation
5. **Email Service**: Sends verification emails and notifications

### Data Model Changes

```sql
-- User Accounts Table
CREATE TABLE users (
    user_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    phone VARCHAR(15) NOT NULL,
    date_of_birth DATE,
    email_verified BOOLEAN DEFAULT FALSE,
    email_verification_code VARCHAR(6),
    verification_code_expires_at TIMESTAMP,
    customer_type ENUM('Duke', 'Piedmont', 'Non-Native') DEFAULT 'Non-Native',
    duke_customer_id VARCHAR(50), -- Duke Enterprise customer ID
    preferred_communication ENUM('email', 'sms', 'push') DEFAULT 'push',
    terms_accepted_at TIMESTAMP NOT NULL,
    terms_version VARCHAR(10) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Properties Table (Multi-Property Support)
CREATE TABLE properties (
    property_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    user_id UUID NOT NULL REFERENCES users(user_id) ON DELETE CASCADE,
    duke_premise_id VARCHAR(50), -- Duke Enterprise premise ID (if applicable)
    nickname VARCHAR(50),
    street_address VARCHAR(255) NOT NULL,
    city VARCHAR(100) NOT NULL,
    state VARCHAR(2) NOT NULL,
    zip_code VARCHAR(10) NOT NULL,
    property_type ENUM('Single-Family', 'Condo', 'Townhouse', 'Mobile Home', 'Apartment'),
    is_primary BOOLEAN DEFAULT FALSE,
    latitude DECIMAL(10, 8),
    longitude DECIMAL(11, 8),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE(user_id, is_primary) WHERE is_primary = TRUE -- Only one primary property per user
);

-- HPP Plans Table (Linked to Properties)
CREATE TABLE hpp_plans (
    plan_id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    property_id UUID NOT NULL REFERENCES properties(property_id) ON DELETE CASCADE,
    duke_plan_id VARCHAR(50) NOT NULL, -- Duke Enterprise plan ID
    plan_type ENUM('HomeWire', 'Heating & Cooling', 'Appliance', 'Water Heater', 'Combo'),
    status ENUM('Active', 'Cancelled', 'Suspended') DEFAULT 'Active',
    start_date DATE,
    monthly_fee DECIMAL(10, 2),
    synced_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Integration Points

**Duke Enterprise API:**
- Endpoint: `POST /api/v1/customer/validate`
- Authentication: API key in header
- Timeout: 5 seconds
- Retry: Once on timeout
- Response: Customer ID, account type, premises, active plans

**Google Maps Autocomplete API:**
- Endpoint: `https://maps.googleapis.com/maps/api/place/autocomplete/json`
- Rate limit: 100,000 requests/day (free tier)
- Fallback: Manual address entry

**Email Service (SendGrid or AWS SES):**
- Verification email template
- Welcome email template
- Rate limit: 100 emails/hour per user (prevent abuse)

### Technical Constraints

- **Performance**: Account creation must complete in < 3 seconds (excluding API latency)
- **Scalability**: Support 10,000 concurrent registrations during launch period
- **Security**: Passwords hashed with bcrypt (cost factor 12)
- **Backwards Compatibility**: None required (new system)

---

## Testing Requirements

### Test Plan Overview

**Testing Phases:**
1. User Acceptance Testing (UAT) - Duke business stakeholders
2. Integration Testing - Duke Enterprise API validation
3. Load Testing - Concurrent registrations
4. Security Testing - Password encryption, API security

### Integration Test Cases

#### End-to-End Workflows

**Test Case IT-1: Existing Duke Customer Registration (Happy Path)**
1. User enters email, password, name, phone, Duke-validated address
2. System calls Duke API, returns customer with 2 HPP plans
3. System displays plans: "HomeWire, Heating & Cooling"
4. User confirms and completes registration
5. **Verify:** User profile created, plans linked, email verification sent

**Test Case IT-2: Non-Native Customer Registration**
1. User enters email, password, name, phone, non-Duke address (Florida)
2. System calls Duke API, returns `customerExists: false`
3. System displays: "Welcome! You're all set."
4. User completes registration
5. **Verify:** User profile created with `customer_type = 'Non-Native'`, no plans linked

**Test Case IT-3: Multi-Property Customer**
1. Duke customer with 2 premises registered with Duke
2. System calls Duke API, returns 2 premises
3. System asks: "Add both properties?"
4. User selects both, confirms
5. **Verify:** 2 property records created, 1 marked primary

**Test Case IT-4: Duke API Timeout**
1. User enters Duke-validated address
2. Duke API times out after 5 seconds
3. System retries once, still times out
4. System displays: "We couldn't validate your account right now. You can still register and we'll link your plans later."
5. User completes registration
6. **Verify:** User created, `duke_customer_id = NULL`, background job queued to retry validation

### User Acceptance Test Cases

#### UAT-1: Eleanor (Existing HPP Customer) Registration
**Persona:** 58-year-old existing Duke customer with 2 HPP plans
**Scenario:** Eleanor wants to create app profile to book HVAC service

**Steps:**
1. Download app, tap "Get Started"
2. Enter email, password, name, phone
3. Enter home address: 123 Main St, Charlotte, NC 28202
4. System displays: "We found your Duke account! HomeWire Plan, Heating & Cooling Plan"
5. Eleanor confirms plans, completes registration
6. Receives verification email, clicks link

**Success Criteria:**
- ✅ Registration completes in < 2 minutes
- ✅ Both HPP plans visible in "My Account"
- ✅ Eleanor can immediately book covered service
- ✅ No errors or unclear messaging

#### UAT-2: Nathan (Non-Native Customer) Registration
**Persona:** 41-year-old Florida homeowner, no Duke utility service
**Scenario:** Nathan finds app via Google search, wants to book plumbing service

**Steps:**
1. Download app from Google Play
2. Tap "Get Started"
3. Enter email, password, name, phone
4. Enter address: 456 Beach Ave, Tampa, FL 33609
5. System displays: "Welcome! Start exploring services."
6. Nathan completes registration

**Success Criteria:**
- ✅ No confusion about Duke utility requirement
- ✅ Registration completes without Duke validation
- ✅ Nathan can browse ad-hoc services immediately
- ✅ Clear pricing displayed for services

### Regression Test Cases

**Test Case RT-1: Email Uniqueness**
- **Verify:** Duplicate email registration blocked with clear error message
- **Verify:** User directed to login or password reset

**Test Case RT-2: Password Complexity**
- **Verify:** Weak passwords rejected (e.g., "password123")
- **Verify:** Strong passwords accepted (e.g., "Passw0rd!123")

---

## Dependencies and Risks

### Dependencies

**Internal Dependencies:**
1. **Duke Enterprise API Availability**
   - API must be available in development environment within 2 weeks of kickoff
   - Documentation and sandbox credentials required
   - **Mitigation:** Build registration without validation first, add integration later

2. **Customer Profile Service Backend**
   - Backend API endpoints for user creation, profile storage
   - Database schema deployed to dev/staging/prod
   - **Mitigation:** Backend development can proceed in parallel with mobile UI

3. **Email Service Configuration**
   - SendGrid or AWS SES account setup
   - Email templates approved by legal/marketing
   - **Mitigation:** Use placeholder emails in dev/staging, real emails in prod only

**External Dependencies:**
1. **Google Maps API**
   - API key and billing account setup
   - 100,000 requests/day limit (should be sufficient for MVP)
   - **Mitigation:** Manual address entry as fallback

2. **Duke IT Support**
   - Duke IT must provide API documentation and credentials
   - Duke SMEs must test UAT scenarios
   - **Mitigation:** Schedule API handoff meeting within first week

### Risks

#### HIGH RISK: Duke API Unavailability or Delays

**Description:** Duke Enterprise API not available by development milestone
**Impact:** High - Cannot validate Duke customers, delays HPP plan linking
**Probability:** Medium
**Mitigation:**
- Build registration flow without Duke validation first
- Allow non-native customers to register without validation
- Add Duke validation integration as separate sprint
- Background job can validate users post-registration if API delayed
- Communicate to users: "We'll link your plans within 24 hours"

#### MEDIUM RISK: Multi-Property Edge Cases

**Description:** Complex edge cases with multi-property customers (e.g., shared properties, rental properties)
**Impact:** Medium - May cause confusion or errors during onboarding
**Probability:** Medium
**Mitigation:**
- Test with actual Duke customer data (anonymized)
- UAT with multi-property customers
- Clear UI messaging: "Which properties would you like to add?"
- Allow users to add/remove properties later in settings

#### LOW RISK: Email Verification Deliverability

**Description:** Verification emails blocked by spam filters or not delivered
**Impact:** Low - Users can't verify accounts, must contact support
**Probability:** Low
**Mitigation:**
- Use reputable email service (SendGrid, AWS SES)
- SPF/DKIM/DMARC records configured
- Allow users to request new verification code
- Support can manually verify accounts if needed

---

## Implementation Plan

### Phase 1: Core Registration
- [ ] Backend: User account database schema
- [ ] Backend: Registration API endpoints (POST /register, POST /verify-email)
- [ ] Mobile: Registration UI screens (email/password, name/phone, address)
- [ ] Mobile: Form validation and error handling
- [ ] Integration: Google Maps Autocomplete API
- [ ] Integration: Email service (verification emails)

### Phase 2: Duke Validation Integration
- [ ] Backend: Duke Enterprise API client library
- [ ] Backend: Customer validation logic (call Duke API, parse response)
- [ ] Backend: HPP plan linking logic
- [ ] Mobile: Display linked HPP plans in onboarding flow
- [ ] Testing: Duke API integration tests with sandbox data

### Phase 3: Multi-Property Support
- [ ] Backend: Properties table and API endpoints
- [ ] Mobile: Multi-property selection UI during onboarding
- [ ] Mobile: Property switcher in app header
- [ ] Testing: Multi-property UAT scenarios

### Phase 4: Onboarding Enhancements
- [ ] Mobile: Welcome screen with value proposition
- [ ] Mobile: Progressive profiling (skip options)
- [ ] Mobile: Home profile incentive messaging
- [ ] Mobile: Guest access for DIY content browsing
- [ ] Testing: Full end-to-end onboarding flows

**Total Estimated Timeline:** To be determined during sprint planning

### Rollout Strategy

_How will this feature be deployed and released?_

- **Deployment Approach**: Phased rollout
  - Phase 1: Internal testing (Orases + Duke IT teams)
  - Phase 2: Beta testing (limited existing Duke customers)
  - Phase 3: Soft launch (single territory)
  - Phase 4: Full launch (all Duke/Piedmont territories)
- **User Communication**: Email campaign to existing HPP customers with app download link
- **Training Needed**: Duke call center staff trained to assist with registration issues
- **Rollback Plan**: Feature flag to disable registration, fall back to "Coming Soon" screen

---

## Success Metrics

### Key Performance Indicators (KPIs)

**Performance Metrics:**
- Registration completion rate: Baseline N/A → Target 95%
- Average registration time: Target < 3 minutes
- Duke API validation success rate: Target 90%
- Email verification completion rate: Target 80% within 24 hours

**User Adoption Metrics:**
- New registrations per day: Target 500+ (first month)
- Multi-property users: Target 15% of Duke customers
- Non-native registrations: Target 20% of total registrations

**Business Metrics:**
- Call center volume reduction: Baseline TBD → Target -20% within 3 months
- Self-service adoption: Target 60% of service requests via app (vs. phone)

### Measurement Plan

- **Measurement Period**: Post-launch monitoring period TBD
- **Review Cadence**: Regular reviews during initial rollout, ongoing monitoring thereafter
- **Success Threshold**: 90% registration completion rate + 80% Duke validation success

---

## Open Questions

### 1. Duke API Performance & Reliability
- **Question:** What is expected uptime and response time for Duke Enterprise API?
- **Options:**
  - **Option A**: API has 99.5% uptime, < 1 second response time → Build synchronous validation
  - **Option B**: API has 95% uptime, 2-5 second response time → Build async validation with background jobs
- **Decision Needed By**: Early in development phase
- **Decision Owner**: Duke IT + Orases Tech Lead

### 2. Password Complexity Requirements
- **Question:** Should we enforce Duke Energy's corporate password policy or use consumer-friendly policy?
- **Discussion Points:**
  - Duke corporate policy: 12+ chars, uppercase, lowercase, number, special char, no dictionary words
  - Consumer-friendly: 8+ chars, uppercase, number, special char
  - Trade-off: Security vs. user friction
- **Decision Needed By**: Before UAT
- **Decision Owner:** Duke Security Team + Product Owner

### 3. Social Login Support
- **Question:** Should we add Google/Apple sign-in for MVP or defer to Phase 2?
- **Options:**
  - **Option A**: MVP includes social login → Reduces friction, faster registration
  - **Option B**: Phase 2 only → Faster time to MVP, less complexity
- **Decision Needed By**: Sprint Planning for Phase 1
- **Decision Owner:** Duke Product Owner

---

## Next Steps

1. **Duke API Handoff Meeting** - Duke IT at project kickoff
2. **Database Schema Review** - Orases Backend Team early in development
3. **UAT Participant Recruitment** - Duke RS Team before testing phase
4. **Email Template Approval** - Duke Legal/Marketing during implementation
5. **Security Review** - Duke Security Team before deployment

---

## Document History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-01-27 | Aksana Rahouski | Initial PRD created |

---

**Document Status:** Draft for Review
**Next Review Date:** 2026-02-03
**Approvals Required:**
- [ ] Duke Product Manager (Kate Angina)
- [ ] Orases Engineering Lead
- [ ] Duke IT (API Integration)
- [ ] Duke Legal (Terms/Privacy)
- [ ] Duke Security (Password Policy)

---

END OF DOCUMENT
