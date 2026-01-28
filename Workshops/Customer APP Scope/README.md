# Customer App Scope Documents
## Duke Energy Residential Solutions Home Services Mobile App

---

## Overview

This folder contains the parsed sections from the **Customer App Preliminary Scope and Flows** workshop document. The original comprehensive document has been split into 9 focused documents for easier navigation and reference.

**Source Document**: `Customer_App_Preliminary_Scope_and_Flows.md`
**Workshop Date**: Session 1 Customer Discovery Workshop
**Participants**: Duke Energy Team (Kate Angina, Son Gandara, Kevin Oppermann, Dana DeRemigis, Joshua Gilstrap) & Orases Team (Tom Witt, Dave McArdle, Devin Gaither, Aksana Rahouski)

---

## Document Structure

### 01_Executive_Summary.md (3.1 KB)
High-level overview of the workshop, key decisions, and strategic direction.

**Contents:**
- Meeting details and participants
- Purpose of the discovery session
- 7 key decisions made during the workshop
- Strategic approach summary

**Key Decisions:**
- Customer segmentation strategy (3 customer types)
- Balanced MVP approach
- Home inventory as cornerstone feature
- Phased payment integration
- FSM tool dependency
- DIY content evolution
- Multi-property support

---

### 02_Customer_Types_and_Segmentation.md (4.3 KB)
Detailed breakdown of the three primary customer segments and their needs.

**Contents:**
- **Segment 1**: Existing Duke/P&G customers WITH Home Protection Plans (800K+ customers)
- **Segment 2**: Existing Duke/P&G customers WITHOUT HPPs
- **Segment 3**: Non-native customers (outside Duke/P&G territory)
- Duke vs. Piedmont considerations
- Customer volume and acquisition goals

**Target Goals:**
- Generate $25M in new ad-hoc service revenue within 12 months
- Acquire 250K non-native customers within 24 months
- Reduce call center volume by 40%

---

### 03_MVP_Scope_Decisions.md (18 KB)
Comprehensive list of features in and out of scope for Phase 1 MVP.

**Phase 1 MVP Features (IN SCOPE):**
- Customer registration & onboarding ✅
- Home Protection Plan management ✅
- Home inventory/profile building ✅
- Service booking (HPP covered services) ✅
- Service booking (ad-hoc services) ✅
- Contractor matching & scheduling ✅
- Communication & notifications ✅
- "Pizza tracker" real-time tracking ⚠️ (dependent on FSM)
- DIY content & maintenance reminders ✅
- Loyalty/rewards/gamification ✅
- Payment processing ⚠️ (phased implementation)
- Service history & records ✅
- Customer feedback/reviews ⚠️ (partially in scope)

**Phase 2+ Features (OUT OF SCOPE):**
- AI virtual assistant
- Advanced contractor portal
- White-label platform
- Expanded service categories
- Home sale transfer automation
- Energy efficiency integration
- Predictive maintenance

---

### 04_Customer_Flows.md (37 KB)
Detailed step-by-step user flows for 5 core customer journeys.

**Flow 1**: Existing Customer with HPP Plan - Books Covered Service
**Flow 2**: Existing Customer with HPP Plan - Books Ad-Hoc Service
**Flow 3**: New Customer Enrollment in HPP Plan
**Flow 4**: Non-Native Customer - Books Ad-Hoc Service
**Flow 5**: Home Inventory Building & Gamification

Each flow includes:
- Persona description
- Pre-conditions
- Detailed step-by-step actions
- System responses
- Edge cases and error handling
- Post-service follow-up

---

### 05_Key_Integrations_and_Dependencies.md (27 KB)
Technical integrations required and their dependencies.

**Critical Integrations:**
1. **Duke Enterprise APIs** (Customer validation, HPP lookup)
2. **Commerce Platform** (Service orders, billing)
3. **Dynamics CRM** (Customer data, service history)
4. **Field Service Management (FSM) Tool** (Contractor scheduling, GPS tracking)
5. **Payment Gateway** (SpeedPay, Apple Pay, Google Pay)
6. **Public Data Services** (Home characteristics pre-fill)
7. **CPSC Recall Database** (Product safety alerts)
8. **Market Research Platform** (Customer feedback surveys)

**Dependencies & Risks:**
- FSM tool procurement critical path
- API documentation delivery timeline
- Payment integration phasing
- Duke IT resource availability

---

### 06_Business_Goals_and_Success_Metrics.md (6.3 KB)
Quantifiable goals and KPIs to measure app success.

**Primary Goals:**
- **Revenue Growth**: $25M in ad-hoc service revenue within 12 months
- **Customer Acquisition**: 250K non-native customers within 24 months
- **Operational Efficiency**: 40% reduction in call center volume
- **Customer Satisfaction**: 70+ NPS score, 90% satisfaction with contractor communication
- **Engagement**: 80% home inventory completion rate

**Success Metrics:**
- App download rate
- Profile completion percentage
- Service booking conversion rate
- Repeat service rate
- Customer lifetime value (CLV)
- Ad-hoc service attachment rate
- HPP enrollment growth
- Contractor acceptance rate (90% target)

---

### 07_Open_Questions_and_Risks.md (11 KB)
Unresolved questions and identified risks that require follow-up.

**Open Questions:**
- FSM tool selection and procurement timeline
- Ad-hoc service catalog definition and pricing
- Contractor compensation models
- Non-native customer service area boundaries
- Profile data retention after home sale
- Legal/compliance review timelines

**Risks:**
- FSM tool not available at launch (fallback: manual workarounds)
- Payment integration delays (fallback: contractor collects)
- API documentation delays from Duke IT
- Contractor onboarding challenges
- Pilot market selection constraints
- Competitive pressure from established players

**Mitigation Strategies:**
- Phased feature rollout approach
- Manual workarounds for critical features
- Parallel development tracks
- Early contractor engagement

---

### 08_Next_Steps.md (5.1 KB)
Action items and deliverables following the workshop.

**Immediate Next Steps:**
1. Orases wireframe development (2 weeks)
2. Duke IT API documentation delivery
3. FSM tool procurement evaluation
4. Ad-hoc service catalog definition
5. Legal/compliance review initiation
6. Contractor pilot program planning

**Phase 2 Workshop Topics:**
- Detailed wireframe review
- Technical architecture deep dive
- Integration sequence and dependencies
- Testing strategy and pilot market selection
- Go-to-market planning

---

### 09_Appendix.md (7.3 KB)
Supporting materials including participant quotes and document control.

**Contents:**
- Key participant quotes with full context
- Decision rationale documentation
- Terminology and acronym definitions
- Document version control
- Meeting attendee roles

---

## How to Use These Documents

### For Product Team:
- Start with **01_Executive_Summary** for high-level context
- Reference **03_MVP_Scope_Decisions** for feature prioritization
- Use **04_Customer_Flows** for wireframe and UX design
- Review **06_Business_Goals** for success criteria

### For Development Team:
- Focus on **03_MVP_Scope_Decisions** for feature specifications
- Review **05_Key_Integrations** for technical dependencies
- Reference **04_Customer_Flows** for user interaction patterns

### For Project Management:
- Use **08_Next_Steps** for action item tracking
- Monitor **07_Open_Questions_and_Risks** for blockers
- Track dependencies in **05_Key_Integrations**

### For Stakeholders:
- Read **01_Executive_Summary** for strategic decisions
- Review **06_Business_Goals** for ROI projections
- Reference **02_Customer_Types** for market opportunity

---

## Document Metadata

**Created**: November 21, 2025
**Source**: Customer_App_Preliminary_Scope_and_Flows.md
**Total Documents**: 9 files
**Total Size**: ~120 KB
**Format**: Markdown (.md)

**Folder Location**: `/Users/aksana/Documents/Duke_residential_solutions/Workshops/Customer APP Scope/`

---

## Related Documents

- **Original Source**: `../Customer_App_Preliminary_Scope_and_Flows.md`
- **Admin Portal Scope**: `../Admin_Portal_Prototype_Plan.md`
- **Workshop Diagrams**: `../Admin_Workflow_Diagrams.md`
- **Proposal Documents**: `../../ProposalDocuments/`

---

**Note**: These documents are working artifacts from discovery workshops and should be updated as decisions evolve and additional detail is gathered in subsequent sessions.
