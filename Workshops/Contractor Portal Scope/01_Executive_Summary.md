# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 1. EXECUTIVE SUMMARY

### Meeting Details
- **Date**: Session 3 Contractor Discovery Workshop
- **Participants**:
  - **Duke Energy Team**: Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap, Chris Murphy (Director, Contractor Network), Ed Carr (Field Operations)
  - **Orases Team**: Tom Witt, Vlad (Lead), Aksana Rahouski
- **Duration**: ~90 minutes
- **Format**: Virtual discovery session via video conference

### Purpose of Session
This contractor discovery session was designed to understand the current contractor ecosystem, define contractor matching algorithms, and determine Phase 1 contractor portal scope. The goal was to identify minimal viable contractor features needed to support the customer app MVP while deferring extensive contractor portal enhancements to Phase 2.

The team emphasized a pragmatic approach - understanding current contractor workflows and determining what must be built vs. what can be managed manually for MVP launch.

### Key Decisions Made

1. **Minimal Contractor Changes for MVP**: Phase 1 will NOT include new contractor portal or mobile app. Contractors will continue using existing Commerce CRM workflow. Admin backend will manage contractor configuration.

2. **Contractor Matching Algorithm**: Matching based on **Trade + Zip Code + Primary/Secondary designation**. System will recommend primary contractor with option for customer to request alternative (handled via phone call for MVP).

3. **Manual Status Updates for MVP**: Admin team will manually update service request statuses in app based on contractor communication (phone/email). No real-time FSM integration for Phase 1.

4. **Static Availability Windows**: Contractors will provide availability rules (lead time buffer, time windows, work days) that Duke maintains. Real-time contractor schedule visibility deferred to Phase 2 with FSM tool.

5. **Contractor Data Sync**: Contractor configuration data (trade, zip codes, lead time, availability windows) will be exported from CRM and maintained in app admin backend. Manual updates acceptable for MVP.

6. **FSM Tool Procurement Timeline**: Duke is evaluating Service Power and Service Bench as FSM solutions. NOT in scope for Phase 1. Phase 2+ will integrate FSM for:
   - Real-time contractor availability
   - GPS tracking ("pizza tracker")
   - Automated status updates
   - Mobile app for contractors

7. **Payment Collection - Phase 1**: Contractors collect payment on-site for ad-hoc services (cash, check, credit card via Square/Stripe). App-based payment processing deferred to Phase 2.

8. **Multi-Trade Contractors**: Contractors can serve multiple trades (plumbing, electrical, HVAC). Each trade may have different availability windows, lead times, and primary/secondary designations.

9. **Inventory Data Collection**: Contractors will be asked to capture appliance/system details during service visits to populate customer home inventory. Process and incentive structure TBD with contractor field coordinators.

10. **Communication Strategy**: Phase 1 uses phone/SMS for contractor-customer communication. In-app messaging deferred to Phase 2. Contractors continue providing lifecycle communications as they do today (~70% provide updates).

---
