# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

---

## 7. OPEN QUESTIONS & RISKS

### Unresolved Items from Meeting

#### Product & Scope Questions

**1. DIY Content Scope & Ownership**:
- **Question**: How extensive should DIY library be at MVP? Static articles vs. AI-powered assistant?
- **Decision Made**: Focus on maintenance reminders with basic DIY instructions, defer extensive library to Phase 2
- **Still Unclear**: Who creates DIY content? Duke internal team vs. contractor contributors vs. third-party content licensing?

**2. Contractor Ratings & Reviews**:
- **Question**: Should customers rate contractors in-app or continue external survey process?
- **Decision Made**: MVP uses external survey process, ratings fed back into app for display
- **Risk**: Delay in feedback loop if external survey process is slow

**3. Multi-Property UI/UX**:
- **Decision Made**: Multi-property support required in MVP
- **Still Unclear**: How do customers switch between properties in app? Property selector on every screen vs. "active property" toggle?

**4. Ad-Hoc Service Catalog Depth**:
- **Question**: How many ad-hoc services at MVP launch? 10? 50? 100?
- **Discussion**: Start with preventative maintenance (HVAC check, appliance tune-ups), expand to common repairs (toilet replacement, leaky faucet)
- **Risk**: Limited catalog = limited revenue potential and customer perception of "not much to offer"

**5. Loyalty Points Economics**:
- **Question**: What's the dollar value of 1 loyalty point? How many points for each action?
- **Discussion**: Points convert to dollar credits (e.g., 100 points = $10)
- **Still Unclear**: Duke needs to model the economics - how much are they willing to "give away" to drive engagement?

**6. Home Health Scorecard Algorithm**:
- **Question**: How is Home Health Score calculated? What triggers "Good" vs. "Fair" vs. "Poor"?
- **Discussion**: Based on appliance ages, maintenance history, known issues
- **Still Unclear**: Exact algorithm and whether it's built in-house or licensed from third-party (e.g., HomeAdvisor, Thumbtack models)

#### Technical & Integration Questions

**7. Customer Validation Edge Cases**:
- **Question**: What happens if customer swears they're a Duke customer but validation fails?
- **Options**: Manual review queue, customer uploads utility bill for verification, allow account creation anyway
- **Risk**: Fraudulent accounts or customer frustration if legitimate customers are blocked

**8. Payment Integration Timeline**:
- **Question**: Will payment gateway be fully integrated at MVP launch?
- **Decision Made**: Flexible - can launch without if needed, contractors collect payment directly
- **Still Unclear**: Target date for payment integration if not ready at launch? 1 month post-launch? 3 months?

**9. FSM Tool Selection & Procurement**:
- **Question**: Which FSM tool will Duke select? When will procurement be finalized?
- **Risk**: FSM is critical for automated scheduling, pizza tracker, contractor management. Delay in procurement = delay in these features.
- **Dependency**: Orases needs FSM API documentation to build integration. Can start with mock APIs but will need to refactor.

**10. Duke Enterprise API SLAs**:
- **Question**: What are Duke IT's commitments for API development timeline and uptime SLAs?
- **RFP Requirement**: API documentation and sandbox within 2 weeks of kickoff
- **Risk**: Duke IT has other priorities; delays in API delivery could block app development
- **Mitigation**: Orases can build with mock APIs initially, but real APIs needed for beta testing

**11. Data Privacy & Consent**:
- **Question**: For Duke/Piedmont customers, can app auto-link their utility account data, or does customer need to explicitly consent?
- **Discussion**: Customer should have choice to link utility account for rebates/incentives but NOT required
- **Still Unclear**: GDPR/CCPA compliance for non-native customers in states with strict privacy laws (California, Virginia, etc.)

**12. Contractor Payment Terms**:
- **Question**: For ad-hoc services, when does Duke pay contractors? Immediately after service completion? Net 30?
- **Impact**: If Duke pays contractors quickly but collects from customers later (or offers payment plans), Duke carries float
- **Still Unclear**: Payment reconciliation process between Duke and contractors

#### Business & Operational Questions

**13. Pilot Launch Strategy**:
- **Question**: Will MVP launch in all Duke/Piedmont territories at once, or phased rollout by region?
- **RFP Background**: Pilot program with ~25 contractors across 3 markets
- **Still Unclear**: Which 3 markets? How long is pilot before full rollout? Criteria for pilot success?

**14. Contractor Onboarding**:
- **Question**: How many contractors need to be onboarded to FSM/contractor portal before MVP launch?
- **Discussion**: At minimum, primary contractors for each trade in pilot markets
- **Risk**: Contractors resistant to adopting new technology, training burden, change management

**15. Customer Support Model**:
- **Question**: Who handles customer support for app issues? Orases during warranty? Duke call center? Separate app support team?
- **Still Unclear**: Escalation process for disputes between customers and contractors

**16. Non-Native Expansion Pace**:
- **Question**: How aggressively will Duke market to non-native customers in Year 1?
- **Discussion**: Non-native is in MVP scope, but marketing spend prioritization unclear
- **Risk**: If non-native growth is slower than expected, ad-hoc service revenue targets at risk

**17. White-Label Timing**:
- **Question**: When will Duke pursue white-label partnerships with other utilities?
- **Discussion**: Architecture must support multi-tenancy from Day 1 (per RFP), but partnerships likely 18-24 months out
- **Impact**: Design decisions now affect white-label feasibility later

#### Compliance & Legal Questions

**18. Service Contract Compliance**:
- **Question**: State-by-state regulations for service contracts vary. Does app need to show different terms by state?
- **Risk**: Compliance violations if terms don't match state requirements (e.g., California requires different cancellation policies)

**19. Contractor Licensing Verification**:
- **Question**: How does Duke verify contractors are licensed and insured? Manual audit vs. API integration with state licensing boards?
- **Risk**: If unlicensed contractor booked via app, Duke liable for issues

**20. Data Retention Policies**:
- **Question**: How long does Duke retain customer service history, photos, contractor notes?
- **Discussion**: Important for home sale use case (customers want years of history) but privacy laws may require data deletion upon account closure

---

### Technical Dependencies & Risks

**High-Risk Dependencies**:

1. **Duke Enterprise APIs (CRITICAL PATH)**:
   - **Risk**: Delays in Duke IT delivering customer validation, plan lookup, and service order APIs
   - **Impact**: App cannot launch without these
   - **Mitigation**: Start with mock APIs, establish weekly checkpoint calls with Duke IT, escalate delays to executive sponsors
   - **Contingency**: If severe delays, launch with limited customer validation (non-native only) and expand to Duke customers later

2. **FSM Tool Procurement (HIGH IMPACT)**:
   - **Risk**: FSM vendor selection delayed or vendor delivers incomplete APIs
   - **Impact**: No automated scheduling, no pizza tracker, manual contractor assignment
   - **Mitigation**: Design app to work with simplified manual processes initially, use feature flags to enable FSM features when ready
   - **Contingency**: Continue call center contractor coordination for 3-6 months post-launch if needed

3. **Payment Gateway Integration (MEDIUM IMPACT)**:
   - **Risk**: Payment provider approval delayed (some require business reviews, compliance checks)
   - **Impact**: Cannot collect payment in-app for ad-hoc services
   - **Mitigation**: Contractor-collected payment model is acceptable fallback
   - **Contingency**: Launch without payment, add in Phase 1B (Month 3-4)

**Medium-Risk Dependencies**:

4. **Contractor Portal Adoption**:
   - **Risk**: Contractors slow to adopt new portal/FSM app, prefer phone calls
   - **Impact**: Manual processes continue, customer experience suffers
   - **Mitigation**: Contractor training program, incentives for portal usage, gradual rollout
   - **Contingency**: Duke staff act as intermediaries during transition period

5. **Product Catalog Definition**:
   - **Risk**: Duke team hasn't finalized ad-hoc service offerings and pricing by development start
   - **Impact**: Cannot build service catalog pages, booking flows incomplete
   - **Mitigation**: Start with 5-10 "no-brainer" services (preventative maintenance), add more iteratively
   - **Quote from RFP Background**: "Product Catalog Definition: Ad-hoc service pricing must be defined by Weeks 8-12"

6. **Content Creation (DIY, Maintenance Guides)**:
   - **Risk**: Duke doesn't have DIY content library ready
   - **Impact**: DIY section of app is empty or thin at launch
   - **Mitigation**: License content from third-party (e.g., HomeAdvisor, Angi), or defer DIY to Phase 1B

**Low-Risk Dependencies**:

7. **Legal Approvals**:
   - **Risk**: Duke legal review of customer-facing terms, privacy policy, contractor agreements takes longer than expected
   - **Impact**: Cannot publish app to app stores without legal approval
   - **Mitigation**: Start legal review early (Week 4-6), provide templates from similar apps
   - **Quote from RFP Background**: "Legal Approvals: Customer communications and privacy notices require Duke legal review"

---

### Timeline Concerns

**Aggressive 44-Week Schedule**:
- **RFP Commitment**: MVP launch in Week 40 (11 months from kickoff)
- **Parallel Workstreams**: Mobile app, APIs, backend systems, contractor portal, admin tools all being developed simultaneously
- **Risk**: Any one dependency delay cascades to launch date

**Critical Path Items** (Must be complete for launch):
1. Duke Enterprise APIs (customer validation, plan lookup, service order creation)
2. Core service booking workflow (mobile app)
3. Contractor assignment logic (even if manual)
4. Home inventory functionality
5. Payment integration (OR contractor-collected payment fallback)
6. Basic ad-hoc service catalog (10-20 services minimum)
7. Legal/compliance approval for terms, privacy policy
8. Contractor onboarding in pilot markets

**Nice-to-Have for Launch** (Can defer if needed):
- FSM integration and pizza tracker
- Full DIY content library
- Loyalty/rewards gamification
- Plan enrollment/cancellation self-service (vs. "call us")
- Extensive ad-hoc service catalog (50+ services)
- Contractor feedback in-app (vs. external survey)

**Quote from Tom (Orases)**: "It's also going to help us define what MVP is so we can get also more concrete around our estimate numbers, timeline, budget."

---

