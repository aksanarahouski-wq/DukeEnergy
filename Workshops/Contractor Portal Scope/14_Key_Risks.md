# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 14. KEY RISKS

### HIGH RISK 🔴

**1. Contractor Matching Algorithm Underdefined**
- **Risk**: Customer scheduling feature can't be built without complete matching specification
- **Impact**: Blocks customer app development
- **Mitigation**: Prioritize finalizing trade + zip + primary/secondary + availability rules in validation session

**2. Static Availability May Lead to Low Acceptance Rates**
- **Risk**: Showing customer time slots that contractors can't actually fulfill
- **Target**: 90-95% acceptance rate, but no real-time visibility into contractor schedules
- **Impact**: Customer frustration, admin rework, contractor complaints
- **Mitigation**: Conservative lead time buffers (3-5 days minimum), contractor SLA contracts

**3. Manual Admin Processes May Not Scale**
- **Risk**: Admin team manually processing all service requests (send to contractor, update status)
- **Volume**: If 1,000+ service requests/month, admin workload becomes unsustainable
- **Impact**: Delays in customer confirmations, poor customer experience
- **Mitigation**: Monitor admin workload closely, prioritize service request API for Phase 1 if possible

**4. No Service Request API to Commerce CRM**
- **Risk**: Service requests created in app have no automated path to contractor
- **Current Plan**: Admin manually creates in Commerce CRM OR emails contractor
- **Impact**: Dual data entry, risk of errors, admin burden
- **Mitigation**: Duke IT to assess if service request creation API can be built for Phase 1

**5. P&G Internal Employees vs. Duke Contractors Not Clarified**
- **Risk**: MVP may need to support both third-party contractors AND internal employees with different workflows
- **Impact**: Scope creep, different data models, separate admin features
- **Mitigation**: Get clarification ASAP - Is MVP Duke-only or must support P&G employees?

**6. Contractor Data Export Not Available**
- **Risk**: Cannot populate app admin backend with contractor configuration
- **Impact**: No contractor matching, no scheduling, MVP blocked
- **Mitigation**: Duke IT must provide contractor export within 2 weeks of project kickoff

### MEDIUM RISK 🟡

**7. Contractor Availability Rules Too Complex**
- **Risk**: Multi-trade contractors with different availability per trade is complex data model
- **Impact**: Admin difficulty configuring, potential bugs in matching algorithm
- **Mitigation**: Start with simple model (one availability per contractor), add complexity in Phase 2

**8. Contractor Reluctance to Capture Inventory Data**
- **Risk**: Contractors view data capture as extra work without benefit
- **Impact**: Inventory data remains incomplete, limits future features
- **Mitigation**: Communicate value proposition to contractors (future work pipeline), negotiate incentives

**9. Rural Areas with Single Contractor**
- **Risk**: No backup option if primary contractor unavailable or at capacity
- **Impact**: Customer cannot book service, poor experience
- **Mitigation**: Communicate limitations to customer ("limited availability in your area"), manual admin outreach to expand contractor network

**10. Commission Model for Ad-Hoc Services Undefined**
- **Risk**: Unclear how Duke captures revenue from ad-hoc services
- **Impact**: Pricing strategy unclear, contractor payment terms unclear
- **Mitigation**: Define commission model before MVP launch (can start with no commission, add later)

**11. FSM Tool Delayed Beyond Phase 2**
- **Risk**: No FSM tool selected or implemented, limiting contractor mobile app and pizza tracker
- **Impact**: Competitive disadvantage, customer experience gaps
- **Mitigation**: Duke to prioritize FSM procurement, include in Phase 2 scope

### LOW RISK 🟢 (Mitigated)

**12. Extensive Contractor Portal Build**
- **Risk**: MITIGATED - Phase 1 does NOT include contractor portal rebuild
- **Decision**: Admin-only approach, contractors use existing Commerce portal

**13. In-App Messaging Complexity**
- **Risk**: MITIGATED - Phase 1 uses phone/SMS, in-app messaging deferred to Phase 2

**14. Contractor Adoption of New Mobile App**
- **Risk**: MITIGATED - No contractor mobile app for Phase 1, deferred to Phase 2 with FSM tool
