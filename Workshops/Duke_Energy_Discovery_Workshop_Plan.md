# Duke Energy Residential Solutions - Discovery Workshop Plan

**Purpose:** 4-session workshop series to validate requirements, define MVP scope, and create wireframe prototypes
**Goal:** Demonstrate Orases understands the complexity and build mutual confidence to move forward with contract

---

## Overview

This workshop series enables Orases and Duke Energy to:

- **VALIDATE** foundational assumptions about users, personas, and business processes
- **DISCOVER** what data exists in current systems vs. what needs to be built
- **CLARIFY** technical integration requirements and Duke IT's role
- **DEFINE** MVP scope with clear IN vs Phase 2 decisions
- **CREATE** interactive wireframe prototypes showing app look and feel
- **BUILD** shared understanding and confidence for Statement of Work (SOW)

---

## Strategic Approach: User-Group-Focused Discovery

### **The Reality: We're Building an Ecosystem**

This isn't simply a customer mobile app. We're building an interconnected platform with **three distinct user groups**:

1. **Customers** - Native Duke/P&G customers with HPP plans + non-native customers seeking ad-hoc services
2. **Admins** - Content managers, product managers, operations team, analysts
3. **Contractors** - Duke's network of ~150 contractors receiving and completing jobs

### **Workshop Structure: Discovery First, Design Second**

**Sessions 1-3:** Discovery by user group (customer, admin, contractor)
- Focus on validating workflows and making scope decisions
- Identify integration requirements and data needs
- **Data-focused:** Each session includes critical data questions to define database schema and integration requirements
- Create rough wireframe sketches collaboratively

**Session 4:** Integration architecture + interactive wireframe presentation
- **CRITICAL:** Duke IT must attend to provide API specifications
- Present complete prototype (50+ screens across all 3 user groups)
- Finalize MVP scope and create go-forward plan

---

## 4-Session Workshop Series

### **Session 1: Customer Discovery**
**Focus:** Customer personas, service request workflows, MVP feature decisions

**Critical Decisions:**
- Who to design for FIRST? (native HPP customers, non-native, or both equally?)
- HPP coverage rules approach (real-time API check, self-determine, or hybrid?)
- Home inventory: mandatory, optional, or deferred to Phase 2?
- DIY content: Who creates? How much at launch?
- MVP features: What's IN vs Phase 2? (multi-property, warranty tracking, Spanish localization, etc.)

**Outputs:** Validated personas, service workflows, MVP scope decisions, customer wireframe sketches

**[Detailed Agenda: Session_1_Customer_Discovery.md]**

---

### **Session 2: Admin Discovery**
**Focus:** Admin roles, product catalog/pricing, content management, analytics

**🚨 Duke IT should attend**

**Critical Decisions:**
- CMS approach: Custom (Orases builds) or third-party?
- Pricing management: Who sets pricing? How often changes? Approval workflow?
- Content creation ownership: Duke team, Orases, contractors, third-party?
- Admin analytics scope: Basic dashboards or advanced BI?
- SSO for admin portal or separate login?

**Outputs:** Admin roles defined, CMS decision made, content strategy, admin wireframe sketches

**[Detailed Agenda: Session_2_Admin_Discovery.md]**

---

### **Session 3: Contractor Discovery**
**Focus:** Contractor workflows, matching algorithm, Phase 1 contractor portal scope

**🚨 Duke IT should attend**
**🚨 Invite 1-2 actual contractors if possible**

**Critical Decisions:**
- Contractor matching algorithm specification (geographic, specialization, availability, performance?)
- Phase 1 contractor portal scope:
  - Option A: Enhance existing portal (fastest, lowest cost)
  - Option B: Build new mobile app (modern UX, higher cost)
  - Option C: Hybrid approach
  - Option D: Minimal Phase 1, full rebuild Phase 2 (recommended)
- In-app messaging or phone/SMS sufficient?
- Payment collection approach confirmed

**Outputs:** Matching algorithm specified, Phase 1 scope decided, contractor wireframe sketches (if new build)

**[Detailed Agenda: Session_3_Contractor_Discovery.md]**

---

### **Session 4: Integration Architecture & Wireframe Presentation**
**Focus:** System architecture, API specifications, wireframe presentation, SOW foundation

**🚨 MOST CRITICAL SESSION - Duke IT MUST ATTEND**
- Leslie James (IT Manager)
- Clark Frederickson (Solution Architect)

**Critical Questions for Duke IT:**
- Commerce API: Customer authentication, HPP validation - exists today or build?
- Dynamics API: Service request creation, status updates - exists today or build?
- Contractor system: Integration approach, data access
- Authentication: SSO or separate? MFA required?
- Sandbox access: When available? Process to request?
- **Timeline:** If APIs need to be built, when ready?

**Outputs:** Architecture validated, API dependency list with Duke IT owners/timelines, interactive wireframe prototype (50+ screens), MVP scope finalized, SOW-ready

**[Detailed Agenda: Session_4_Integration_Wireframes.md]**

---

## Critical Success Factors

### 🚨 **Duke IT Participation is Non-Negotiable**

**Required Attendance:**
- Session 2: Admin integrations and CMS discussion
- Session 3: Contractor portal integration
- Session 4: **MOST CRITICAL** - API specifications and architecture

**Why Critical:** From meetings analysis, Duke IT was NOT present in either Orases scoping meeting. Without Duke IT input, we cannot:
- Validate what APIs exist TODAY vs need to be built
- Get commitment on sandbox access timeline
- Understand authentication approach (SSO vs separate)
- Create realistic project timeline

---

## Key Blockers to Resolve

From scoping meeting analysis, these topics are **undefined and block development:**

| Topic | Session | Why Blocking | Impact if Unresolved |
|-------|---------|--------------|---------------------|
| **HPP coverage rules** | Session 1 | Can't build eligibility checking without rules | Core feature not functional |
| **Contractor matching algorithm** | Session 3 | Core app functionality | Can't automate contractor assignment |
| **Ad-hoc pricing structure** | Session 2 | Revenue model depends on it | Can't display pricing to customers |
| **API availability (Commerce + Dynamics)** | Session 4 | Project timeline depends on it | Massive timeline slippage |
| **CMS approach** | Session 2 | Affects architecture | Wrong technical decision |
| **P&G internal employees vs Duke contractors** | Session 3 | Different employment models may require different features | Phase 1 contractor portal can't support both |
| **Duke vs P&G API parity** | Session 4 | If one system not ready, delays half the customer base | Duke-only launch or delayed timeline |

---

## Expected Deliverables (End of Series)

### **Requirements Documentation:**
- Customer personas with actual percentages
- Service request workflows (HPP vs ad-hoc)
- HPP coverage determination approach
- Home inventory MVP scope and data model
- DIY content strategy and creation plan
- Admin roles and responsibilities
- Product catalog & pricing management workflow
- Contractor matching algorithm specification

### **Technical Specifications:**
- System architecture diagram
- Integration specification (high-level)
- API dependency list with Duke IT owners/timelines
- Data sync approach (real-time vs batch)
- Authentication and security requirements
- **Data model specifications** for each entity (customers, service requests, contractors, HPP plans, home inventory, DIY content, ad-hoc services, payments)
- **Role-based access (CRUD) matrices** for each data entity

### **Design Deliverables:**
- Interactive wireframe prototype (50+ screens)
  - Customer app (20-25 screens)
  - Admin portal (15-20 screens)
  - Contractor portal (10-15 screens, if new build)
- User journey maps for each user group

### **Project Planning:**
- Finalized MVP scope (IN vs Phase 2)
- Timeline validated (Q2-Q3 2026 realistic?)
- Open questions log with owners/due dates
- Go-forward plan with action items
- **Foundation for Statement of Work (SOW)**

---

## Workshop Logistics

### **Facilitation Approach:**
- Visual collaboration tools (Miro/FigJam) for real-time ideation
- Live wireframe updates in Figma during sessions
- "Show, Don't Tell" - walk through real examples, not hypotheticals
- Focus on decisions that affect scope/budget/timeline
- Park tangents for later - stay on critical path

### **Orases Team:**
- **Aksana (Product Manager):** Lead facilitation
- **Devin (Product Designer & Business Analyst):** Real-time wireframe creation
- **Vlad (CTO/Technical Lead):** Technical feasibility and integration discussion

### **Post-Session Activities:**
- Within 48 hours: Clean up wireframe sketches
- Within 1 week: Deliver session summary and updated wireframes
- Between sessions: Research open questions

---

## Risk Mitigation

### **Identified Risks:**

🔴 **HIGH RISK:**
1. **Duke IT Not Engaged** → Confirm attendance for Sessions 2, 3, 4
2. **Business Rules Undefined** → Document formally in workshops
3. **MVP Scope Not Finalized** → Make scope decisions, don't defer

🟡 **MEDIUM RISK:**
4. **Content Strategy Unclear** → Assign ownership in Session 2
5. **Scope Creep During Workshops** → Maintain "MVP vs Phase 2" parking lot
6. **Too Many Stakeholders** → Define decision-makers upfront

---

## Success Metrics

### **Workshops are successful if:**

✅ **Alignment Achieved:**
- Duke and Orases have shared understanding of MVP scope
- All critical blockers resolved or assigned owners
- Business rules documented (not just discussed)
- Wireframes approved by stakeholders

✅ **Technical Clarity:**
- Duke IT commits to API availability timeline
- Integration approach validated
- Security requirements understood
- No major unknowns blocking SOW creation

✅ **Design Validation:**
- Wireframes reflect actual business workflows
- All three user groups represented
- Ready for development handoff

✅ **Project Readiness:**
- MVP scope finalized with no major surprises
- Timeline validated (Q2-Q3 2026 still realistic?)
- Orases can draft SOW immediately after Session 4
- Mutual confidence to move forward with contract

---

## Quick Reference

| Session | Focus | Key Attendees | Critical Outputs |
|---------|-------|---------------|-----------------|
| **1: Customer** | Personas, service workflows, MVP features, **Duke vs P&G customers**, **HPP plans** | Business team, CSR rep | Personas validated, MVP scope, HPP coverage approach, Duke/P&G percentages |
| **2: Admin** | Roles, catalog, CMS, analytics, **HPP plan management**, **Duke/P&G territories** | Business team, **Duke IT** | CMS decision, pricing workflow, content strategy, HPP catalog ownership |
| **3: Contractor** | Matching, workflows, Phase 1 scope, **🚨 P&G employees vs Duke contractors** | Business team, **1-2 Contractors**, **Duke IT** | Matching algorithm, Phase 1 scope decision, **P&G employee approach** |
| **4: Integration** | Architecture, APIs, wireframes, SOW, **Commerce + Dynamics APIs** | All stakeholders + **Duke IT Team** | API specs, wireframe prototype, MVP finalized, **Duke/P&G API timelines** |

---

## Next Steps

1. **Schedule all 4 workshop sessions** (ideally within 3-4 week period)
2. **Confirm Duke IT attendance** for Sessions 2, 3, 4
3. **Review individual session agendas** (linked above)
4. **Complete pre-session preparation** (outlined in each session document)
5. **Invite contractors** to participate in Session 3

---

## Individual Session Documents

For detailed agendas and questions:

- **[Session 1: Customer Discovery](Session_1_Customer_Discovery.md)**
- **[Session 2: Admin Discovery](Session_2_Admin_Discovery.md)**
- **[Session 3: Contractor Discovery](Session_3_Contractor_Discovery.md)**
- **[Session 4: Integration Architecture & Wireframe Presentation](Session_4_Integration_Wireframes.md)**

---

## Supporting Documents

**Data Analysis:**
- **[Data Entities & Workflows Analysis](Data_Entities_and_Workflows_Analysis.md)** - 10 critical data entities with CRUD matrices (master reference)
- **[Data Discovery Questions Addendum](Data_Discovery_Questions_Addendum.md)** - Detailed data questions organized by session (supplemental reference)
- **Note:** Most critical data discovery questions have been integrated directly into individual session documents for easier facilitation
- **[Meetings vs Workshops Analysis](Meetings_vs_Workshops_Analysis.md)** - What was covered in scoping meetings vs what's missing

**Critical Reference Documents:**
- **[HPP Plans Explained](HPP_Plans_Explained.md)** - Complete reference on Home Protection Plans: how they work, pricing ($9.99/month), coverage rules (BLOCKER), customer base (800K+), and plan options
- **[P&G Customer References](P&G_Customer_References.md)** - Critical distinctions between Duke (electric, Commerce, third-party contractors) vs P&G (gas, Dynamics, internal employees) and integration implications

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 5, 2025
**Status:** Ready for Duke review and session scheduling

---

**The Goal:** Walk out of these 4 sessions with Duke team saying, "Orases clearly understands what we're building. We're confident moving forward with them as our partner."
