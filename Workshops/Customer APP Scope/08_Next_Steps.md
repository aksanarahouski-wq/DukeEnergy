# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

---

## 8. NEXT STEPS

### Immediate Action Items (Before Session 2)

**Duke Team**:
1. **Product Catalog Prioritization**: Identify top 10-20 ad-hoc services for MVP with draft pricing (flat rate vs. variable)
2. **Duke IT Coordination**: Confirm API development timeline and prioritize customer validation + plan lookup APIs
3. **FSM Vendor Update**: Share current status of FSM tool procurement and estimated selection date
4. **Legal Review Kickoff**: Send draft terms of service and privacy policy to Duke legal team for initial review
5. **Payment Gateway**: Confirm preference (Stripe, Braintree, SpeedPay, other) and initiate vendor account setup
6. **Review Orases Prototype**: Team to review clickable prototype from RFP response and provide feedback

**Orases Team**:
1. **Finalize Customer Flows**: Clean up whiteboard diagrams from session and share with Duke team for review
2. **Technical Architecture**: Begin designing API integration layer and database schema for home inventory
3. **Wireframe Prep**: Start wireframing key screens (onboarding, service booking, home inventory) for Session 4 presentation
4. **Branding Assets**: Request Duke brand guidelines (logo, colors, typography, UI components if available)
5. **FSM Research**: Research API capabilities of ServicePower and Dispatch.me to understand integration options

**Quote from Dave McArdle (Orases)**: "That's what we're trying to capture today. So, again, this isn't full discovery by any stretch. But we're going to use this time wisely and we're going to build out agendas for each session to give us enough information so we can provide valuable information back to you."

### Session 2: Contractor Experience (Next Week)

**Agenda**:
- Contractor personas and workflow
- Contractor portal requirements
- Job acceptance/decline process
- In-field data collection (inventory updates, photos, notes)
- Payment collection (if contractor handles)
- Contractor ratings and performance management
- Training and onboarding requirements

**Expected Outcomes**:
- Contractor portal feature list
- Integration points between contractor systems and customer app
- Contractor engagement and incentive model

**Quote from Dave McArdle**: "I think there's even more opportunity. I'm super excited about the whole principle of incentivizing the customer to provide that data and rewarding them for it. I think in the next session, when we talk about the contractors, we can have really cool ideas about how to make the contractor the data provider for maybe some insights about the customer as well."

### Session 3: Internal Admin & Operations

**Agenda**:
- Admin portal/dashboard requirements
- Service catalog management (ad-hoc services, pricing, promotions)
- Content management (DIY articles, maintenance guides)
- Contractor management and performance monitoring
- Customer support tools and dispute resolution
- Reporting and analytics dashboards
- User roles and permissions

**Expected Outcomes**:
- Admin tool feature specifications
- Backend system architecture
- Operational workflow documentation

**Quote from Son**: "How can you help facilitate us setting up some of these ad hoc services or products without us having to go back to enterprise SAP? We want that flexibility... turn this offer on and this promotion off and this one on and this one off."

### Session 4: Wireframes & Prototype Review

**Agenda**:
- Walkthrough of updated wireframes/prototype
- Screen-by-screen design review
- Interaction patterns and navigation
- Branding application
- Accessibility considerations
- Feedback collection and iteration

**Expected Outcomes**:
- Approved design direction
- UI component library
- Clickable prototype for user testing

### Pre-Development Requirements

**Must Be Defined Before Development Starts** (Week 12 per RFP timeline):

1. **APIs**:
   - Customer validation API spec finalized
   - Plan lookup API spec finalized
   - Service order creation API spec finalized
   - Contractor assignment API spec finalized
   - Sandbox environment available for testing

2. **Product Catalog**:
   - HPP plan details and pricing confirmed
   - Initial ad-hoc service catalog (10-20 services minimum)
   - Pricing finalized (flat rate or ranges)
   - Service descriptions and photos

3. **Business Rules**:
   - Coverage eligibility logic (what's covered under each plan)
   - Cancellation policies (24-hour notice requirement, refunds, etc.)
   - Loyalty points earning and redemption rates
   - Contractor SLAs by trade and territory

4. **Legal**:
   - Terms of service approved
   - Privacy policy approved
   - Contractor agreements finalized (if new agreements needed)
   - State-specific compliance requirements documented

5. **Design**:
   - Wireframes approved
   - Brand guidelines applied
   - Clickable prototype tested with sample users
   - Key user flows validated

6. **Infrastructure**:
   - AWS environment provisioned (dev, staging, prod)
   - Payment gateway account approved and configured
   - Analytics tools selected (Google Analytics, Mixpanel, etc.)
   - Push notification service configured (Firebase, AWS SNS, etc.)

---

