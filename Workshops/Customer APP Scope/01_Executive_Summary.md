# Customer App Preliminary Scope and Flows
## Duke Energy Residential Solutions Home Services Mobile App

---

## 1. EXECUTIVE SUMMARY

### Meeting Details
- **Date**: Session 1 Customer Discovery Workshop
- **Participants**:
  - **Duke Energy Team**: Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap
  - **Orases Team**: Tom Witt, Dave McArdle, Devin Gaither, Aksana Rahouski
- **Duration**: 2 hours
- **Format**: Virtual discovery session via video conference

### Purpose of Session
This initial customer discovery session was designed to define the MVP scope, capture customer journeys, and identify key integrations needed for the Duke Energy Residential Solutions Home Services Mobile App. The goal was to move beyond the RFP requirements and collaboratively define what the app will "look and feel like" to inform wireframe development, timeline refinement, and budget estimation.

The team emphasized a "future-minded" approach - disconnecting from existing application workflows to dream about the ideal customer experience while remaining grounded in technical realities and dependencies.

### Key Decisions Made

1. **Customer Segmentation Strategy**: Three distinct customer types will be supported in Phase 1 MVP:
   - Existing Duke/Piedmont customers with home protection plans (HPP)
   - Existing Duke/Piedmont customers without HPPs
   - Non-native customers (outside Duke/Piedmont utility service areas)

2. **Balanced MVP Approach**: The team selected a hybrid strategy (Option 1) that balances serving existing warranty customers while simultaneously building features to acquire new customer segments, particularly through ad-hoc service offerings with transparent, flat-rate pricing.

3. **Home Inventory as Cornerstone**: Building comprehensive home profiles and appliance inventories is critical to MVP success, with gamification and loyalty rewards identified as key mechanisms to incentivize profile completion.

4. **Phased Payment Integration**: Payment processing for ad-hoc services and new plan enrollments is in scope for Phase 1, but launch may proceed without full integration if dependencies aren't ready. Contractors may initially collect payments directly with transition to app-based payment as integration becomes available.

5. **FSM Tool Dependency**: Field Service Management (FSM) software integration is essential for real-time contractor tracking ("pizza tracker"), automated status updates, and contractor mobile app. Current internal Duke FSM (SAP-based) is limited. **For MVP Phase 1**: FSM tool NOT in scope - manual admin processes acceptable. **Phase 2+**: Duke evaluating Service Power and Service Bench as FSM vendors.

6. **DIY Content Evolution**: Rather than extensive static DIY library, the focus shifted toward AI-assisted troubleshooting and intelligent, inventory-based maintenance reminders that can recommend both DIY solutions and professional service booking options.

7. **Multi-Property Support in MVP**: Despite being an outlier use case, customers with multiple properties (vacation homes, rental properties) must be supported from Day 1 since profile validation against Duke Enterprise systems will surface multiple premises for some customers.

8. **Contractor Portal Scope** (Session 3): **Phase 1 = Admin-Only Approach** - NO contractor portal rebuild or mobile app for MVP. Contractors continue using existing Commerce CRM portal. Admin backend manages contractor configuration (trade assignments, zip codes, availability windows). Manual status updates by admin acceptable for MVP. Contractor mobile app and FSM integration deferred to Phase 2.

9. **Contractor Matching Algorithm** (Session 3): Matching based on **Trade + Zip Code + Primary/Secondary designation**. Customer sees pre-assigned primary contractor with option to request alternative via phone call (not in-app selection). 125-140 contractors in network (80% primary, 20% backup). Target 90-95% acceptance rate. Static availability buffers for MVP (HVAC 1-2 days, Electrical 5-6 days, Plumbing 3-5 days).

10. **Emergency Services Handling** (Session 3): Emergency services NOT booked through app. App asks qualifying questions (no heat in winter, gas leak, sparking outlet, etc.). If emergency detected, routes customer to phone call. Safety warnings displayed for life-threatening situations (gas leaks).
