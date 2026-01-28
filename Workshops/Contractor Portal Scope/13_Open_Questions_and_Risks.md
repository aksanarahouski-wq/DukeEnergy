# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 13. OPEN QUESTIONS & RISKS

### Unresolved Items from Meeting

#### Contractor Network Questions

**1. P&G Internal Employees vs. Duke Third-Party Contractors**:
- **Question**: How many P&G internal employees? Do they use same portal as Duke contractors?
- **Decision Made**: TBD - Need clarification from Duke team
- **Risk**: Internal employees may have completely different workflow, data model, and portal needs
- **Impact**: Could require separate features or workflows for employee vs. contractor

**2. Contractor Availability Tracking**:
- **Decision Made**: Use static buffer (e.g., 3-day lead time) for MVP
- **Still Unclear**: How do contractors communicate vacation/unavailability? Who updates app backend?
- **Risk**: Customer books time that contractor cannot fulfill

**3. Contractor Specialization - Multi-Trade Details**:
- **Decision Made**: Contractors can serve multiple trades
- **Still Unclear**: Data model for trade-specific availability (does each trade get separate config record?)
- **Risk**: Complex data model, difficult for admin to configure

**4. Primary/Secondary Tier Determination**:
- **Question**: What makes a contractor "primary" vs. "secondary"? Performance? Pricing? Territory size?
- **Discussion**: Negotiated contracts, not dynamic based on ratings
- **Still Unclear**: Can secondary be promoted to primary? What's the criteria?

**5. Exception Handling - All Contractors at Capacity**:
- **Question**: What happens if primary and all backups decline?
- **Discussion**: Rare scenario (90%+ acceptance rate)
- **Still Unclear**: Does system automatically extend time windows? Or admin manually intervenes?

#### Payment & Invoicing Questions

**6. Ad-Hoc Service Commission Model**:
- **Question**: Does Duke take a percentage of ad-hoc services? If yes, how much?
- **Discussion**: Customer pays $99, contractor keeps portion, Duke keeps portion?
- **Still Unclear**: Exact commission structure, how collected, how reported

**7. Contractor Invoicing for Ad-Hoc Services**:
- **Question**: How does contractor report cash payments collected on-site?
- **Discussion**: Contractor updates Commerce portal with payment collected
- **Still Unclear**: Does contractor invoice Duke for commission? Or Duke invoices contractor?

**8. SpeedPay Integration for Non-Native Customers**:
- **Question**: When does SpeedPay integration come online?
- **Discussion**: Non-native customers need third-party payment since they can't add to utility bill
- **Risk**: If SpeedPay not ready at launch, contractors collect cash on-site (may reduce non-native bookings)

#### Inventory Data Collection Questions

**9. Contractor Inventory Capture Process**:
- **Question**: How do contractors submit inventory data to app?
- **Options**: Manual admin entry vs. simple portal form vs. defer to Phase 2
- **Decision Made**: TBD - Needs technical feasibility assessment
- **Risk**: If deferred, miss opportunity to build high-quality inventory data early

**10. Contractor Incentive for Data Capture**:
- **Question**: What motivates contractors to capture appliance data?
- **Discussion**: Future work pipeline, small bonus, part of SLA expectations?
- **Still Unclear**: Duke needs to negotiate with contractors via field coordinators

#### FSM Tool Questions

**11. FSM Tool Selection Timeline**:
- **Question**: When will Duke select FSM vendor (Service Power vs. Service Bench)?
- **Discussion**: NOT in scope for Phase 1 MVP
- **Risk**: If delayed beyond Phase 2, limits contractor mobile app and pizza tracker features

**12. FSM Tool API Documentation**:
- **Question**: Do Service Power and Service Bench have APIs? What's the integration complexity?
- **Still Unclear**: Need to review vendor documentation during Phase 2 planning
