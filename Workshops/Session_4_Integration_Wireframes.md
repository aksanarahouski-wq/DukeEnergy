# Session 4: Integration Architecture & Wireframe Presentation

**Focus:** System architecture, API specifications, wireframe presentation, and MVP scope finalization.

**🚨 MOST CRITICAL SESSION - Duke IT MUST ATTEND**
- Leslie James (IT Manager)
- Clark Frederickson (Solution Architect)
- **Without Duke IT, cannot finalize integration approach or create SOW**

---

## Session Agenda

### **Part 1: Recap Sessions 1-3 Decisions** (Quick Review)

**Customer Discovery (Session 1):**
- Customer personas validated
- HPP coverage approach decided
- MVP features finalized (what's IN vs Phase 2)
- Home inventory scope decided

**Admin Discovery (Session 2):**
- CMS approach decided (custom vs third-party)
- Content creation ownership assigned
- Pricing management workflow defined
- Admin roles clarified

**Contractor Discovery (Session 3):**
- Contractor matching algorithm specified
- Phase 1 contractor portal scope decided
- Payment collection approach confirmed

---

### **Part 2: System Architecture & Integration - DUKE IT FOCUS**

**Goal:** Define how app integrates with Duke systems and what Duke IT must provide.

#### **High-Level Architecture:**

```
[Customer App] → [Orases Backend/Orchestration] → [Commerce] (Duke IT)
                                                 → [Dynamics] (Duke IT)
                                                 → [Contractor Portal] (Duke IT)
                                                 → [App Database] (Orases AWS)
```

**Components:**
- **Customer apps:** iOS, Android, Mobile Web (PWA) - all call same backend APIs
- **Orases orchestration layer:** Business logic, contractor matching, integration layer
- **Duke IT systems:** Commerce (customer data), Dynamics (service requests), Contractor Portal
- **App database:** Non-native customers, home inventory, DIY content, ad-hoc services

---

#### **Critical API Questions for Duke IT:**

**🚨 These questions MUST be answered to create SOW:**

**1. Commerce Platform (Customer Data - DUKE CUSTOMERS):**
- **Question:** Can app authenticate Duke customers via Commerce API?
- **Question:** Can app retrieve Duke customer HPP plans and coverage via API?
- **Question:** Can app check HPP eligibility in real-time for Duke customers?
- **Question:** Does this API exist TODAY or need to be built by Duke IT?
- **Question:** If needs to be built, what's the timeline? Who owns it?

**1b. Dynamics Platform (Customer Data - P&G CUSTOMERS):**
- **Question:** Can app authenticate P&G customers via Dynamics API?
- **Question:** Can app retrieve P&G customer HPP plans and coverage via API?
- **Question:** Can app check HPP eligibility in real-time for P&G customers?
- **Question:** Does this API exist TODAY or need to be built by Duke IT?
- **Question:** If needs to be built, what's the timeline? Who owns it?
- **🚨 CRITICAL:** Are Commerce (Duke) and Dynamics (P&G) APIs at same maturity level?
- **🚨 CRITICAL:** Timeline for building APIs: Same for both systems or different?
- **🚨 CRITICAL:** Who are Duke IT contacts for Commerce vs Dynamics integrations?

**2. Dynamics (Service Requests):**
- **Question:** Can app create service requests in Dynamics via API?
- **Question:** Can app retrieve service request status in real-time?
- **Question:** Can app retrieve customer service history?
- **Question:** Does this API exist TODAY or need to be built by Duke IT?
- **Question:** If needs to be built, what's the timeline? Who owns it?

**3. Contractor Portal / System:**
- **Question:** Where is contractor data stored? (Dynamics, separate portal database?)
- **Question:** Can app access contractor list for matching algorithm?
- **Question:** When app assigns job to contractor, how does it reach contractor?
- **Question:** Integration via API or different approach?

**4. Authentication & Security:**
- **Question:** SSO for admin portal? (SAML, Okta, Azure AD?)
- **Question:** For customer app: Authenticate against Commerce or separate?
- **Question:** MFA required?
- **Question:** Data encryption requirements?

**5. Sandbox & Testing:**
- **Question:** When can Orases get sandbox/test environment access?
- **Question:** What's the process to request access?
- **Question:** Timeline: 2 weeks? 1 month? 3 months?

**Why This Matters:** **These answers determine project timeline.** If APIs don't exist and Duke IT can't build them quickly, timeline slips.

---

### **Part 3: Data Sync & Master Sources**

**Goal:** Clarify where data lives and how it syncs. For EACH entity, determine: (1) Where does data live? (2) Where else is data copied? (3) How is data synced? (4) What's the master source of truth? (5) How often does data change?

**Customer Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| **Native customer profile** | Commerce/Dynamics | App DB (read-only?) | API? Batch? | ? |
| **Non-native customer profile** | App DB | None | N/A | N/A |
| **HPP plan enrollment** | Commerce/Dynamics | App DB | ? | ? |
| **Customer preferences (notifications)** | App DB | None | N/A | N/A |
| **Home inventory** | App DB | None | N/A | N/A |

**Questions for Duke IT:**
- For native customers: Can app read customer data from Commerce/Dynamics via API?
- Real-time or daily batch sync?
- If customer updates email in Commerce, how long until app sees new email?
- If customer updates email in app, can it update Commerce? Should it?
- What's the master source of truth for customer data? (if conflicts, which system wins?)

---

**Service Request Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| **HPP service request** | Dynamics | App DB | ? | ? |
| **Ad-hoc service request** | App DB | Dynamics (?) | ? | ? |
| **Service status** | Dynamics (?) | App DB | ? | Real-time? |
| **Customer rating** | App DB | Dynamics (?) | ? | ? |

**Questions for Duke IT:**
- When customer books service via app, where is service request created FIRST?
  - Option A: App DB → then synced to Dynamics
  - Option B: Directly in Dynamics via API
- When contractor updates status, where is it updated FIRST?
  - Option A: Contractor portal → Dynamics → App DB
  - Option B: Contractor portal → App DB → Dynamics
  - Option C: Both systems updated directly

---

**Contractor Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| **Contractor profile** | Dynamics | App DB | ? | Daily batch? |
| **Contractor availability** | Contractor Portal (?) | App DB | ? | Real-time? |
| **Contractor performance metrics** | Dynamics | App DB | ? | Daily batch? |

**Questions for Duke IT:**
- Can app read contractor list via API? (needed for matching algorithm)
- Can app check contractor availability via API?
- Or does app need local copy of contractor data?

---

**HPP Plan Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| **HPP plan catalog (Duke)** | Commerce | App DB | API or batch | Weekly? |
| **HPP plan catalog (P&G)** | Dynamics | App DB | API or batch | Weekly? |
| **Customer plan enrollment (Duke)** | Commerce | App DB | API or batch | Real-time? |
| **Customer plan enrollment (P&G)** | Dynamics | App DB | API or batch | Real-time? |

**Questions for Duke IT:**
- Can app read HPP plan catalog via API from BOTH Commerce (Duke) and Dynamics (P&G)?
- Can app check if customer enrolled in specific plan via API? (critical for coverage check)
- How often do HPP plans change? (rarely → batch sync acceptable)
- **Can app create NEW enrollments via API?** (if Phase 2 enrollment feature enabled)
- **Can app update enrollments (upgrade/downgrade plans) via API?**
- **Can app cancel enrollments via API?** (if self-service cancellation enabled)
- Do Duke and P&G have same HPP plan offerings? Or different catalogs?
- **🚨 Can Duke IT provide sandbox access for BOTH Commerce and Dynamics?**

---

**Payment Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| **HPP billing** | Commerce | App DB (read-only) | API | ? |
| **Ad-hoc payment** | App DB (SpeedPay) | Accounting system? | ? | ? |

**Questions for Duke IT:**
- For ad-hoc payments: Does transaction data need to sync to Commerce/Dynamics for accounting?
- Or app keeps payment data only?

---

**Data Entities Owned by App Only:**
- **Home inventory** (App DB - does NOT exist in Duke systems)
- **DIY content** (App DB - does NOT exist in Duke systems)
- **Ad-hoc service catalog** (App DB - does NOT exist in Duke systems)
- **Non-native customer profiles** (App DB - does NOT exist in Duke systems)

---

### **Part 4: Wireframe Presentation** (Interactive Prototype)

**Goal:** Show Duke team what the app will look like.

**Orases Will Present:**

**Customer App Wireframes** (~20 screens):
- Onboarding & login flow
- Dashboard
- Service request booking (HPP vs ad-hoc)
- Home inventory management
- DIY content library
- Service tracking
- Account settings

**Admin Portal Wireframes** (~15 screens):
- Product catalog management
- Content management (CMS)
- Service operations dashboard
- Analytics/reporting
- User management

**Contractor Portal Wireframes** (if new build):
- Job list & job details
- Status updates
- Customer communication

**Format:** Interactive, clickable prototype (Figma or similar)

---

### **Part 5: MVP Scope Finalization**

**Goal:** Confirm final scope for Statement of Work (SOW).

**MVP Features CONFIRMED IN:**

**Customer App:**
- ✅ Login/registration (native + non-native)
- ✅ Service request booking
- ✅ HPP coverage check (approach decided in Session 1)
- ✅ Home inventory (scope decided in Session 1)
- ✅ DIY content library
- ✅ Service tracking
- ✅ Contractor ratings/reviews
- ✅ Account management
- ✅/❌ Multi-property (IF >10% customers)
- ✅/❌ Warranty tracking (IF decided MVP)
- ✅/❌ Spanish localization (IF customer base justifies)

**Admin Portal:**
- ✅ Product catalog & pricing management
- ✅ CMS (custom or third-party - decided in Session 2)
- ✅ Service operations dashboard
- ✅ Analytics & reporting (scope decided in Session 2)
- ✅ Admin user management

**Contractor:**
- ✅ Phase 1 scope (Option A, B, C, or D - decided in Session 3)

**Integrations:**
- ✅ Commerce (customer auth, HPP validation)
- ✅ Dynamics (service requests)
- ✅ Contractor Portal (job assignments)
- ✅ SpeedPay (non-native payments)

**Timeline:** 44 weeks (11 months) - Q2-Q3 2026 launch
- **Question:** Still realistic based on discoveries?

---

### **Part 6: Key Risks & Dependencies**

**Project Blockers Identified:**

🔴 **CRITICAL (Project Cannot Proceed Without):**
1. **Duke IT API availability**
   - What APIs exist vs need to be built
   - Timeline for API development by Duke IT
   - Sandbox access timeline

2. **HPP coverage rules** (if not systematized or accessible)
   - Approach decided in Session 1
   - If rules not in system, need workaround

3. **Ad-hoc pricing structure** (if not defined)
   - Decided in Session 2 or deferred to Phase 2

🟡 **HIGH RISK (Affects Timeline/Quality):**
4. **Content creation** (if ownership unclear or not resourced)
5. **Contractor data access** (if APIs don't exist)
6. **Duke IT availability** (for integration support during development)

**Dependencies on Duke:**
- [ ] Duke IT builds required APIs (timeline: ?)
- [ ] Duke IT provides sandbox access (timeline: ?)
- [ ] Duke creates DIY content (timeline: ?)
- [ ] Duke defines ad-hoc pricing (timeline: ?)
- [ ] Duke identifies pilot contractors (timeline: ?)

---

### **Part 7: Go-Forward Plan**

**Immediate Next Steps:**

**Within 1 Week:**
- [ ] Orases: Deliver workshop summary and wireframe prototype
- [ ] Orases: Draft Statement of Work (SOW)
- [ ] Duke IT: Provide API documentation (what exists today)
- [ ] Duke: Answer open questions from workshops

**Within 2-4 Weeks:**
- [ ] Duke IT: Commit to API availability timeline
- [ ] Duke IT: Provide sandbox access (if APIs exist)
- [ ] Duke & Orases: Review and negotiate SOW
- [ ] Duke: Finalize content creation plan

**Within 6-8 Weeks:**
- [ ] SOW signed
- [ ] Kickoff meeting
- [ ] Development begins

**Development Approach:**
- Agile/iterative with 2-week sprints
- Bi-weekly demos to Duke team
- Parallel workstreams: Backend, Customer App, Admin Portal, Contractor integration
- Continuous feedback loop

---

## Expected Outputs

By end of Session 4, we'll have:

✅ **System architecture diagram** validated by Duke IT
✅ **API dependency list** with Duke IT owners and timelines
✅ **Integration specification** (high-level)
✅ **Interactive wireframe prototype** (50+ screens)
✅ **MVP scope finalized** (no major unknowns)
✅ **Timeline validated** (Q2-Q3 2026 realistic or adjusted)
✅ **Go-forward plan** with action items and owners
✅ **Foundation for SOW** (can be drafted immediately)

---

## Key Decisions This Session

| Decision | Options | Impact |
|----------|---------|--------|
| **API Availability** | Exist today vs Duke IT builds | Project timeline |
| **Sandbox Access** | Immediate, 1 month, 3 months | Development start date |
| **Authentication Approach** | SSO vs Separate login | Architecture complexity |
| **Data Sync Strategy** | Real-time vs Batch | Performance, complexity |
| **Timeline Validation** | Q2-Q3 2026 realistic? | Contract terms, expectations |

---

## Pre-Session Preparation Needed

**🚨 Duke IT MUST Prepare:**
- API documentation (what exists TODAY - not "will exist")
- List of APIs that need to be built (with estimates)
- Sandbox access timeline
- Security requirements
- Infrastructure constraints/preferences

**Duke Business Team Should Prepare:**
- Final questions or concerns
- Decision-makers present for final scope approval
- Budget/timeline constraints to discuss

**Orases Team Will Prepare:**
- Interactive wireframe prototype (all 3 user groups)
- System architecture diagrams
- Integration specification draft
- SOW outline

---

**Session Facilitator:** Aksana (Orases Product Manager)
**Session Designer:** Devin (Orases Product Designer & Business Analyst)
**Technical Lead:** Vlad (Orases CTO) - **MUST ATTEND for Duke IT discussion**

---

## Success Criteria

**Session 4 is successful if:**

✅ Duke IT attended and answered all critical API questions
✅ API availability timeline established (or escalated if blocked)
✅ Wireframes approved by stakeholders
✅ MVP scope finalized with no major surprises
✅ Timeline validated or adjusted based on realities
✅ Go-forward plan clear with owners and dates
✅ Duke team confident Orases understands the complexity
✅ Orases can draft SOW immediately after session

**This session should result in mutual confidence to move forward with contract.**
