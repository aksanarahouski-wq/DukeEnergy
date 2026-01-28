# Customer App Deliverable Prioritization Matrix

## Purpose

This document prioritizes the remaining MVP features for PRD creation based on dependencies, business value, technical complexity, and critical path analysis.

---

## Existing PRDs (Completed)

✅ **PRD #1: Customer Registration & Onboarding**
- Status: Complete
- Foundation: Required for all other features
- Key Dependencies: Duke Enterprise API validation

✅ **PRD #2: Service Booking - HPP Covered Services**
- Status: Complete
- Business Value: Core value proposition for 800K existing customers
- Revenue Impact: 40% call center reduction

✅ **PRD #3: Home Inventory & Profile Building**
- Status: Complete
- Strategic Value: Competitive moat, enables upselling (30% lift in plan enrollment)
- Engagement Driver: 80% profile completion target

---

## Candidate Deliverables for Next PRDs

### Prioritization Criteria

Each deliverable evaluated on:
- **Business Value**: Revenue impact, customer acquisition, operational efficiency
- **Dependencies**: Technical and functional prerequisites
- **Technical Complexity**: Integration requirements, API availability, third-party tools
- **MVP Critical Path**: Must-have for launch vs. nice-to-have
- **Risk Level**: Uncertainty in requirements, external dependencies

**Scoring**: 1-5 scale (5 = highest priority/value/complexity)

---

## Deliverable Evaluation Matrix

| # | Deliverable | Business Value | Dependencies | Technical Complexity | MVP Critical | Risk Level | **PRIORITY SCORE** |
|---|-------------|----------------|--------------|---------------------|--------------|------------|--------------------|
| **4** | **Home Protection Plan Management** | **5** | **2** | **3** | **5** | **2** | **🔥 17/25** |
| **5** | **Service Booking - Ad-Hoc Services** | **5** | **4** | **4** | **5** | **3** | **🔥 21/25** |
| **6** | **Communication & Notifications** | **4** | **3** | **3** | **5** | **2** | **🔥 17/25** |
| **7** | **Payment Processing** | **5** | **4** | **4** | **4** | **4** | **⚠️ 21/25** |
| 8 | Contractor Matching & Scheduling | 4 | 5 | 5 | 3 | 5 | ⚠️ 22/25 |
| 9 | DIY Content & Maintenance Reminders | 3 | 3 | 2 | 3 | 1 | ✓ 12/25 |
| 10 | Loyalty/Rewards/Gamification | 3 | 3 | 3 | 3 | 2 | ✓ 14/25 |
| 11 | Service History & Records | 3 | 4 | 2 | 4 | 1 | ✓ 14/25 |
| 12 | Emergency Service Handling | 2 | 2 | 2 | 3 | 2 | ✓ 11/25 |

---

## Detailed Analysis

### 🔥 TIER 1: CRITICAL - CREATE PRDs IMMEDIATELY

---

#### **Deliverable #4: Home Protection Plan Management**

**Why This Ranks #1 for Next PRD:**

**Business Value: 5/5**
- **Revenue Growth**: 100,000 new HPP enrollments target within 12 months
- **Upsell Opportunity**: 25% of ad-hoc customers convert to HPP plans
- **ARPU Increase**: Move from 1.7 to 2.0 plans per customer ($25-$40/month)
- **Customer Acquisition**: Enables Duke/Piedmont customers without plans to self-enroll
- **Quote from Goals**: "New HPP Enrollments: Duke/Piedmont customers without plans converting to plan holders"

**Dependencies: 2/5** (Low - relatively independent)
- ✅ Requires: PRD #1 (Customer Registration) - COMPLETE
- ✅ Requires: Duke HPP Plan APIs (enroll, cancel, modify) - documented in integrations
- ❌ Does NOT require: Service booking, payment integration (can launch with "Coming Soon" for enrollment if APIs delayed)

**Technical Complexity: 3/5** (Medium)
- Integration with SAP Commerce (Hybris) for plan catalog
- Duke HPP APIs for enrollment/cancellation workflows
- Plan comparison engine (feature matrix, pricing calculator)
- Payment method setup (can be phased)
- Self-service cancellation with retention flows

**MVP Critical: 5/5** (Must-have)
- Customers need to see their existing plans (display-only at minimum)
- Plan enrollment drives revenue and customer acquisition
- Plan comparison enables informed purchase decisions
- Cancellation self-service reduces call center volume
- **Quote from MVP Scope**: "Home Protection Plan Management ✅ MVP - Full enrollment workflow, plan comparison, self-service cancellation"

**Risk Level: 2/5** (Low-Medium)
- Duke HPP APIs may not be ready at launch (can display existing plans, add enrollment later)
- Legal review required for enrollment terms and cancellation policies
- Payment integration dependency (but can be phased)

**Recommended Scope for PRD #4:**

**Phase 1 (MVP Launch):**
- Display customer's existing HPP plans with coverage details
- Plan catalog browsing (view all available plans)
- Plan comparison tool (side-by-side feature/pricing comparison)
- Enrollment workflow with terms acceptance (if API ready)
- Payment method setup (if payment integration ready)
- Self-service cancellation request (may route to call center confirmation)

**Phase 2 (Post-Launch):**
- Instant enrollment confirmation (no manual review)
- Upgrade/downgrade plan workflows
- Multi-property plan management
- Plan renewal notifications and reminders
- Cancellation retention offers

**Dependencies to Address in PRD:**
- Duke HPP Plan APIs (Section 5.2 of integrations doc)
- Payment integration (can be phased)
- Legal approval for enrollment terms

---

#### **Deliverable #5: Service Booking - Ad-Hoc Services**

**Why This Ranks #2 for Next PRD:**

**Business Value: 5/5**
- **Revenue Target**: $25M in new ad-hoc service revenue (Year 1 per RFP)
- **Customer Acquisition**: 250,000 non-native customers within 24 months
- **Market Expansion**: Serves customers without utility accounts or HPP plans
- **Average Transaction**: $150-$300 per ad-hoc service
- **Quote from Goals**: "Ad-Hoc Service Revenue: Year 1 Target: $25M in new ad-hoc service revenue"

**Dependencies: 4/5** (High)
- ✅ Requires: PRD #1 (Customer Registration) - COMPLETE
- ✅ Requires: PRD #2 (Service Booking - HPP) - COMPLETE (reuse workflows)
- ⚠️ Requires: Product Catalog & Pricing Management (ad-hoc service catalog doesn't exist yet)
- ⚠️ Requires: Payment Integration (customers must pay at checkout or after service)
- ⚠️ Requires: Contractor matching for ad-hoc services (different logic than HPP)
- **Quote from Integrations**: "Ad-Hoc Services: Do NOT exist in structured catalog form currently"

**Technical Complexity: 4/5** (Medium-High)
- Product catalog system (admin tool to manage ad-hoc services)
- Dynamic pricing by territory and contractor
- Payment integration (Apple Pay, Google Pay, credit card)
- Contractor marketplace (multiple contractors per service, customer choice)
- Quote/estimate workflows for variable-price services
- Promotional pricing and discounts
- **Quote from Son**: "We don't have a way to maintain that product level today so that's also something that we need to think about"

**MVP Critical: 5/5** (Must-have)
- Core business model for non-native customer acquisition
- $25M revenue target depends on this feature
- Differentiates Duke from competitors (Uber-like service marketplace)
- **Quote from MVP Scope**: "Service Booking - Ad-Hoc Services ✅ MVP - Non-covered services with flat-rate pricing"

**Risk Level: 3/5** (Medium)
- Product catalog doesn't exist (Duke must define ~10-20 initial ad-hoc services)
- Pricing strategy unclear (flat rate vs. quote required vs. price ranges)
- Contractor participation (need contractors willing to offer ad-hoc services at defined prices)
- Payment integration dependency (can launch with contractor-collected payment as fallback)
- Legal review for service terms, warranties, liability

**Recommended Scope for PRD #5:**

**Phase 1 (MVP Launch):**
- Ad-hoc service catalog browsing (preventative maintenance focus)
- Service detail pages (description, pricing, contractors offering, reviews)
- Booking workflow for flat-rate services
- Contractor selection (show 3-5 contractors, customer chooses)
- Pre-payment or contractor-collected payment (based on integration readiness)
- Order confirmation and status tracking

**Phase 2 (Post-Launch):**
- Quote-required services (variable pricing, customer submits request)
- Promotional pricing and limited-time offers
- Territory-specific pricing
- Service bundling (book multiple services at once)
- Financing options for expensive services

**Dependencies to Address in PRD:**
- Product catalog admin tool (may need to build this first)
- Payment integration (Section 5.7 of integrations doc)
- Contractor matching for ad-hoc (Section 5.4)
- Initial service catalog definition (Duke to provide ~10-20 services)

---

#### **Deliverable #6: Communication & Notifications**

**Why This Ranks #3 for Next PRD:**

**Business Value: 4/5**
- **Customer Satisfaction**: 90% satisfaction with contractor communication target
- **Engagement**: Drives app opens, reduces call center inquiries ("Where's my contractor?")
- **Retention**: Timely notifications improve perceived service quality
- **Multi-Channel**: Push, SMS, email ensures customers don't miss updates
- **Quote from Goals**: "Contractor Communication Satisfaction: 90% of customers satisfied with updates and transparency"

**Dependencies: 3/5** (Medium)
- ✅ Requires: PRD #1 (Customer Registration) - COMPLETE (need customer contact preferences)
- ✅ Requires: PRD #2 (Service Booking) - COMPLETE (notifications tied to order status)
- ⚠️ Requires: Service order status API integration (triggers for notifications)
- ⚠️ Requires: FSM tool integration for real-time updates (nice-to-have, not blocking)

**Technical Complexity: 3/5** (Medium)
- Push notification service (Firebase Cloud Messaging for iOS/Android)
- SMS gateway integration (Twilio, AWS SNS)
- Email service (SendGrid, Mailgun, AWS SES)
- Notification preferences management (customer controls channels and frequency)
- Event-driven architecture (order status changes trigger notifications)
- Template management (different messages for different events)
- Rate limiting and delivery tracking

**MVP Critical: 5/5** (Must-have)
- Core part of "Uber-like" experience (transparent communication)
- Reduces "where's my contractor?" calls to call center
- Drives app engagement (customers open app when they get notification)
- **Quote from MVP Scope**: "Communication & Notifications ✅ MVP - Multi-channel delivery (push, SMS, email)"

**Risk Level: 2/5** (Low)
- Well-understood technology (push, SMS, email are standard)
- Multiple vendor options for each channel
- Can launch with subset of notifications and expand over time
- Limited external dependencies (mostly internal event triggers)

**Recommended Scope for PRD #6:**

**Phase 1 (MVP Launch):**
- Push notifications (order confirmations, contractor assigned, en route, completed)
- SMS notifications (same events as push, fallback if app not open)
- Email notifications (order summaries, receipts, service history)
- Notification preferences (customer chooses channels and frequency)
- In-app notification center (history of all notifications)
- Critical alerts (emergency service routing, recall alerts)

**Phase 2 (Post-Launch):**
- Maintenance reminders based on home inventory (proactive notifications)
- Promotional offers and upsell campaigns
- Loyalty program updates (points earned, rewards available)
- Two-way communication (customer can reply to contractor messages)
- Rich notifications (images, action buttons, deep links)

**Dependencies to Address in PRD:**
- Push notification service setup (Firebase)
- SMS gateway selection and setup
- Email service selection and setup
- Notification event triggers from service order API

---

#### **Deliverable #7: Payment Processing**

**Why This Is Important But Ranks Lower:**

**Business Value: 5/5**
- **Revenue Enablement**: Required to collect payment for ad-hoc services
- **Customer Convenience**: Apple Pay, Google Pay for frictionless checkout
- **Recurring Revenue**: Supports HPP monthly charges (for non-utility-billed customers)
- **Transaction Volume**: $25M ad-hoc revenue target = ~$100K+ in payment processing

**Dependencies: 4/5** (High)
- ⚠️ Requires: PRD #5 (Ad-Hoc Service Booking) - NOT YET CREATED
- ⚠️ Requires: PRD #4 (HPP Management) - NOT YET CREATED (for plan enrollment payments)
- ⚠️ Requires: Payment gateway procurement and contract (Stripe, Braintree, SpeedPay)
- ⚠️ Requires: PCI compliance audit and certification

**Technical Complexity: 4/5** (Medium-High)
- Payment gateway integration (Stripe, Braintree, etc.)
- Apple Pay and Google Pay SDKs
- PCI compliance (tokenization, secure card storage)
- Recurring billing for HPP subscriptions
- Refund workflows
- Payment method management (save cards, update expired cards)
- Fraud prevention (address verification, CVV, velocity limits)

**MVP Critical: 4/5** (High priority but can be phased)
- **Critical for ad-hoc service revenue target**
- BUT: Can launch with contractor-collected payment as fallback
- **Quote from Son**: "If we don't have payment integration right out of the door, but we want to offer these ad hoc services... then we will work with our contractors to collect that payment."
- Allows MVP launch without blocking on payment gateway procurement

**Risk Level: 4/5** (Medium-High)
- Payment gateway procurement may take months (RFP, contract, legal review)
- PCI compliance audit required before processing payments
- Refund policy and dispute resolution processes needed
- Contractor payout reconciliation (Duke pays contractors for completed work)
- **External dependency on Duke payment gateway selection**

**Recommended Approach:**

**DO NOT CREATE PRD #7 YET - Wait until:**
1. PRD #5 (Ad-Hoc Services) is complete (defines what needs to be paid for)
2. PRD #4 (HPP Management) is complete (defines enrollment payment flows)
3. Duke selects payment gateway vendor
4. PCI compliance requirements are clarified

**When ready, PRD #7 scope should include:**
- Payment method collection (Apple Pay, Google Pay, credit card, ACH)
- One-time payment for ad-hoc services
- Recurring billing for HPP monthly charges
- Payment method management (save, update, delete cards)
- Receipt generation and delivery
- Refund workflows
- Fraud prevention and security

---

### ⚠️ TIER 2: IMPORTANT - CREATE AFTER TIER 1

---

#### Deliverable #8: Contractor Matching & Scheduling

**Priority Score: 22/25** (High but complex)

**Why This Ranks Lower Despite High Score:**

**Complex External Dependency:**
- Requires Duke to procure third-party FSM tool (ServicePower, Dispatch.me, Service Bench)
- FSM tool doesn't exist yet in robust form
- **Quote from Integrations**: "Duke Residential Solutions needs to procure third-party FSM tool (does not exist in robust form currently)"

**Can Launch MVP Without Advanced Matching:**
- Current state: Trade + Zip Code = Primary Contractor (simple lookup from SAP)
- MVP can use simplified matching logic (manual assignment by call center if needed)
- Advanced features (availability checking, GPS tracking, automated assignment) come later

**Recommended Approach:**
- **Phase 1 (MVP)**: Simple contractor assignment (trade + zip code lookup)
- **Phase 2 (Post-Launch)**: Advanced matching once FSM tool procured
- Consider creating TWO PRDs:
  - **PRD #8A**: Basic Contractor Assignment (MVP)
  - **PRD #8B**: Advanced Matching & Scheduling (Phase 2, dependent on FSM procurement)

---

#### Deliverable #9: DIY Content & Maintenance Reminders

**Priority Score: 12/25** (Medium priority)

**Why This Can Wait:**
- Engagement feature, not revenue-critical
- Requires home inventory to be populated (depends on PRD #3 adoption)
- Content creation effort (Duke must write/curate DIY guides and videos)
- **Quote from MVP Scope**: "DIY Content & Maintenance Reminders ✅ MVP - Inventory-based reminders, recall alerts"

**Recommended Approach:**
- Create PRD after Tier 1 deliverables complete
- Can launch with basic content library and manual reminders
- CPSC recall integration is low complexity, high value (Phase 1 candidate)

---

#### Deliverable #10: Loyalty/Rewards/Gamification

**Priority Score: 14/25** (Medium priority)

**Why This Can Wait:**
- Engagement feature, not core business value
- Depends on profile completion (PRD #3) and service booking (PRD #2)
- Requires loyalty program rules definition (Duke business decision)
- **Quote from MVP Scope**: "Loyalty/Rewards/Gamification ✅ MVP - Profile completion score, home health scorecard"

**Recommended Approach:**
- Create PRD after Tier 1 deliverables and DIY Content
- Phase 1: Simple points for profile completion
- Phase 2: Points for service bookings, referrals, rewards redemption

---

#### Deliverable #11: Service History & Records

**Priority Score: 14/25** (Medium priority)

**Why This Is Important But Not Urgent:**
- Functionality largely covered by PRD #2 (Service Booking includes order history)
- May not need standalone PRD - could be enhancement to PRD #2
- Exportable service logs are nice-to-have, not MVP-critical

**Recommended Approach:**
- Evaluate if this warrants standalone PRD or is just an enhancement to PRD #2
- If standalone PRD created, do after Tier 1 deliverables

---

#### Deliverable #12: Emergency Service Handling

**Priority Score: 11/25** (Lower priority)

**Why This Ranks Lowest:**
- Emergency services explicitly routed to PHONE ONLY (not app)
- App just needs triage flow: "Is this an emergency?" → "Call this number"
- **Quote from MVP Scope**: "Emergency Service Handling 🚨 NOT IN APP - PHONE ONLY - Triage flow with escalation"

**Recommended Approach:**
- Simple triage flow can be built into PRD #2 (Service Booking)
- May not need standalone PRD
- Emergency hotline integration is minimal (just display phone number and call button)

---

## RECOMMENDED PRD ROADMAP

### Next PRDs to Create (Priority Order)

**🔥 Immediate (Create Next 3-4 PRDs):**

1. **PRD #4: Home Protection Plan Management**
   - **Timeline**: Create PRD now, ready for development sprint planning
   - **Business Impact**: 100K new enrollments, multi-plan upsell
   - **Dependencies**: Duke HPP APIs (documented), payment integration (can be phased)
   - **Estimated PRD Size**: Large (similar to PRD #1 or #2) - 25-30 pages

2. **PRD #5: Service Booking - Ad-Hoc Services**
   - **Timeline**: Create PRD now, parallel to PRD #4
   - **Business Impact**: $25M revenue target, 250K new customers
   - **Dependencies**: Product catalog definition (Duke), payment integration
   - **Estimated PRD Size**: Very Large - 30-35 pages (most complex)

3. **PRD #6: Communication & Notifications**
   - **Timeline**: Create PRD now
   - **Business Impact**: 90% satisfaction target, reduces call center inquiries
   - **Dependencies**: Service order APIs (documented), push/SMS/email services
   - **Estimated PRD Size**: Medium - 20-25 pages

4. **PRD #7: Payment Processing** ⚠️
   - **Timeline**: Create AFTER PRD #4 and #5 are complete
   - **Business Impact**: Enables ad-hoc revenue and HPP enrollments
   - **Dependencies**: Payment gateway procurement, PCI compliance
   - **Estimated PRD Size**: Large - 25-30 pages

---

**✓ Secondary (Create After Initial 3-4):**

5. **PRD #8: Contractor Assignment - Basic (MVP)**
   - Simplified trade + zip code matching
   - Manual assignment workflows
   - Contractor profile display

6. **PRD #9: DIY Content & Maintenance Reminders**
   - Content library browsing
   - Inventory-based maintenance reminders
   - CPSC recall alerts

7. **PRD #10: Loyalty/Rewards/Gamification**
   - Profile completion scoring
   - Points earning rules
   - Rewards catalog

---

**Later Phases:**

8. **PRD #8B: Contractor Matching - Advanced (Phase 2)**
   - FSM tool integration
   - Automated availability checking
   - GPS tracking / pizza tracker
   - Multi-factor matching algorithm

9. **PRD #11: Service History & Records** (or enhancement to PRD #2)
10. **PRD #12: Emergency Service Triage** (or enhancement to PRD #2)

---

## Summary: Create These 3 PRDs Immediately

### 1. PRD #4: Home Protection Plan Management
- **Why**: High revenue impact, low dependencies, MVP-critical
- **Value**: 100K new enrollments, multi-plan upsell
- **Ready**: Duke HPP APIs documented, can phase payment integration

### 2. PRD #5: Service Booking - Ad-Hoc Services
- **Why**: $25M revenue target, non-native customer acquisition
- **Value**: Core business model expansion
- **Risk**: Product catalog doesn't exist yet (Duke must define services)

### 3. PRD #6: Communication & Notifications
- **Why**: Foundational for all service flows, 90% satisfaction target
- **Value**: Reduces call center volume, drives engagement
- **Ready**: Well-understood technology, minimal external dependencies

### HOLD: PRD #7 (Payment Processing)
- **Why Hold**: Depends on PRD #4 and #5, payment gateway not selected yet
- **Create After**: PRD #4 and #5 complete, Duke selects gateway

---

## Next Steps

1. ✅ **Review this prioritization** with Duke Product Owner
2. ✅ **Confirm top 3 PRDs** align with Duke priorities and API readiness
3. ✅ **Begin PRD #4** (Home Protection Plan Management)
4. ✅ **Begin PRD #5** (Service Booking - Ad-Hoc Services)
5. ✅ **Begin PRD #6** (Communication & Notifications)
6. ⏳ **Schedule PRD #7** (Payment Processing) after gateway selection

---

END OF DOCUMENT
