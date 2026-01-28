# Meeting Analysis vs Workshop Plan - Strategic Assessment

**Date:** November 5, 2025
**Analyzed Meetings:** Orases Scoping Sessions (Meeting 1 & 2)
**Compared Against:** Duke Energy Discovery Workshop Plan

---

## Executive Summary

**Bottom Line:** Your 4-session workshop series is STILL CRITICAL despite two vendor scoping meetings. The scoping sessions were vendor-response focused (answering RFP questions), while your workshops need to be discovery-focused (validating requirements before final decisions).

**Key Finding:** Orases made many assumptions based on the RFP that Duke needs to validate, and Duke IT was notably absent from both scoping meetings.

---

## Coverage Analysis

### ✅ TOPICS WELL COVERED IN MEETINGS

#### 1. Business Context & Strategy
**Meeting 1 Coverage:** 13:35-20:55
- ✅ "Uber of home services" vision confirmed
- ✅ Non-regulated business model (separate from Duke utility)
- ✅ Native vs non-native customer strategy defined
- ✅ White-label potential for future utilities discussed
- ✅ Geographic coverage (7-8 states confirmed)

**Workshop Impact:** Session 1 can build on this foundation rather than starting from scratch

---

#### 2. Current State Systems & Data
**Meeting 1 Coverage:** 16:14-19:25, 36:34-37:49
- ✅ SAP Commerce (Duke customers) - confirmed
- ✅ Dynamics (P&G customers) - confirmed
- ✅ Contractor engagement portal exists
- ✅ **VALIDATED:** NO home inventory data exists
- ✅ **VALIDATED:** Ad-hoc service catalog doesn't exist
- ✅ **VALIDATED:** DIY content being created from scratch

**Workshop Impact:** Session 1 data discovery can focus on detailed field-level mapping

---

#### 3. Customer Base
**Meeting 1 Coverage:** 19:25-24:36
- ✅ 800K+ HPP customers (1.5M agreements total)
- ✅ Call center primary channel (no digital experience)
- ✅ 300K+ plans on water heater and home wiring
- ✅ Top service types: water heater, home wiring, HVAC

**Workshop Impact:** Can use this data as starting point for persona validation

---

#### 4. Contractor Network
**Meeting 1 Coverage:** 38:54-43:35
- ✅ 150 contractors across service areas
- ✅ Duke manages contractor network
- ✅ P&G contractors are internal employees
- ✅ Contractor engagement portal workflow described
- ✅ Automatic dispatch based on zip code

**Workshop Impact:** Session 2 can focus on detailed matching logic rather than explaining basics

---

#### 5. Payment Strategy
**Meeting 1 Coverage:** 43:56-48:19
- ✅ Phase 1: Contractor collects payment on-site
- ✅ Future state: Collect through app
- ✅ SpeedPay integration for non-native customers
- ✅ Pricing transparency goal (fixed pricing preferred)

**Workshop Impact:** Session 2 can focus on payment workflows and pricing rules

---

### ⚠️ TOPICS PARTIALLY COVERED (Need Deeper Validation)

#### 1. User Personas
**Meeting Coverage:** General discussion only
**What's Missing:**
- ❓ Are Eleanor, Emma, Nathan personas accurate?
- ❓ What percentage of customer base does each represent?
- ❓ Are there other major segments we're missing?
- ❓ What are ACTUAL pain points vs assumptions?

**Workshop Plan Reference:** Session 1, Part 1 (Lines 86-102)
**Why It Matters:** UI/UX design depends on validated personas
**Workshop Priority:** HIGH - Must validate in Session 1

---

#### 2. Service Request Process
**Meeting Coverage:** High-level workflow described (Meeting1:40:44-43:35)
**What's Missing:**
- ❓ Step-by-step reality vs understanding
- ❓ What data gets entered where?
- ❓ What decisions are made by whom vs automated?
- ❓ Exception handling processes

**Workshop Plan Reference:** Session 2, Part 1 (Lines 225-243)
**Why It Matters:** Backend logic depends on accurate process mapping
**Workshop Priority:** HIGH - Walk through real examples in Session 2

---

#### 3. Integration Architecture
**Meeting Coverage:** Mentioned but not detailed
**What's Missing:**
- ❓ Specific API endpoints that exist TODAY
- ❓ Authentication methods (OAuth 2.0, API keys, SSO?)
- ❓ Rate limits and throttling constraints
- ❓ Who at Duke IT owns each integration?

**Workshop Plan Reference:** Session 4, Part 2 (Lines 509-541)
**Why It Matters:** Timeline depends on API availability
**Workshop Priority:** CRITICAL - Duke IT MUST attend Session 4

---

### ❌ TOPICS NOT DISCUSSED (Critical Gaps)

#### 1. HPP Coverage Determination Rules
**Meeting Coverage:** None
**Critical Questions Unanswered:**
- ❌ How is HPP eligibility determined?
- ❌ Who decides if service is covered?
- ❌ What happens if service is partially covered?
- ❌ Where do coverage rules live? (system, documentation, people?)
- ❌ Who has override authority?

**Workshop Plan Reference:** Session 2, Part 2 (Lines 245-260)
**Why It Matters:** Core app functionality - eligibility check is critical feature
**Workshop Priority:** HIGHEST - Must define in Session 2
**Business Impact:** Without rules, app can't determine coverage automatically

---

#### 2. Service Prioritization Criteria
**Meeting Coverage:** None
**Critical Questions Unanswered:**
- ❌ How are "emergency" vs "routine" services defined?
- ❌ What's the SLA for each priority level?
- ❌ Can customers request specific time windows?
- ❌ What happens if no contractors are available?

**Workshop Plan Reference:** Session 2, Part 2 (Lines 261-268)
**Why It Matters:** Affects scheduling logic and customer expectations
**Workshop Priority:** HIGH - Must define in Session 2
**Business Impact:** SLAs affect contractor assignments and customer satisfaction

---

#### 3. Contractor Matching Algorithm
**Meeting Coverage:** Mentioned "automatic dispatch" but no details
**Critical Questions Unanswered:**
- ❌ What factors determine which contractor gets assigned?
  - Geography/proximity?
  - Availability?
  - Specialization?
  - Performance rating?
  - Customer preference?
  - Contractor preference?
- ❌ Is matching automated, manual, or hybrid?
- ❌ How is contractor availability tracked?

**Workshop Plan Reference:** Session 2, Part 3 (Lines 269-295)
**Why It Matters:** Core app functionality - affects customer experience
**Workshop Priority:** HIGHEST - Must specify in Session 2
**Business Impact:** Matching algorithm affects contractor utilization and response time

---

#### 4. Pricing Structure & Approval Workflows
**Meeting Coverage:** Mentioned "in development" (Meeting1:45:58)
**Critical Questions Unanswered:**
- ❌ Who sets pricing for ad-hoc services?
- ❌ Who approves pricing changes?
- ❌ Can pricing vary by geographic region?
- ❌ Fixed price vs quote vs hourly rate - when each?
- ❌ How are estimates vs actual costs handled?

**Workshop Plan Reference:** Session 2, Part 4 (Lines 297-313)
**Why It Matters:** Revenue model depends on pricing transparency
**Workshop Priority:** HIGH - Must define in Session 2
**Business Impact:** Pricing model affects customer acquisition and revenue projections

---

#### 5. Home Inventory - MVP Scope Decision
**Meeting Coverage:** Discussed gamification ideas but scope unclear
**Critical Decisions Needed:**
- ❌ What data fields are REQUIRED vs optional?
- ❌ Is inventory entry mandatory or optional at MVP?
- ❌ What appliance types must be tracked for MVP?
- ❌ How much detail needed? (make/model/serial number?)

**Workshop Plan Reference:** Session 3, Part 1 (Lines 354-380)
**Why It Matters:** Affects MVP timeline and user onboarding flow
**Workshop Priority:** HIGH - Must decide in Session 3
**Business Impact:** Mandatory inventory could increase onboarding friction

---

#### 6. DIY Content Strategy
**Meeting Coverage:** Acknowledged content "in parallel development" but no details
**Critical Questions Unanswered:**
- ❌ How much content needed at launch? (10 articles? 50? 100?)
- ❌ Who creates content? (Duke team, Orases, contractors, third-party?)
- ❌ What content types for MVP? (articles, videos, step-by-step wizards?)
- ❌ Content approval process?
- ❌ How is content organized? (by appliance, by problem, by urgency?)

**Workshop Plan Reference:** Session 3, Part 2 (Lines 382-408)
**Why It Matters:** Content creation timeline affects launch date
**Workshop Priority:** HIGH - Must define in Session 3
**Business Impact:** Content volume affects CMS requirements and resource allocation

---

#### 7. Warranty Tracking - MVP or Phase 2?
**Meeting Coverage:** Mentioned but not prioritized
**Critical Decision Needed:**
- ❌ Is warranty tracking MVP or Phase 2?
- ❌ If MVP: What warranty information needs to be captured?
- ❌ Manual entry vs photo upload vs barcode scan?

**Workshop Plan Reference:** Session 3, Part 3 (Lines 409-426)
**Why It Matters:** Affects MVP scope and timeline
**Workshop Priority:** MEDIUM - Must decide in Session 3
**Business Impact:** Adding warranty tracking to MVP adds development time

---

#### 8. Multi-Property Management - MVP or Phase 2?
**Meeting Coverage:** Mentioned as feature but scope unclear
**Critical Questions Unanswered:**
- ❌ What percentage of customers have multiple properties?
- ❌ If <10%, should this be Phase 2?
- ❌ If MVP: What's minimum needed?

**Workshop Plan Reference:** Session 3, Part 4 (Lines 429-436)
**Why It Matters:** Affects MVP complexity and UI design
**Workshop Priority:** MEDIUM - Must decide in Session 3
**Business Impact:** Multi-property adds significant UI/data complexity

---

#### 9. Admin Interface Requirements
**Meeting 2 Coverage:** CMS admin discussed only
**Critical Questions Unanswered:**
- ❌ What other admin functions needed beyond CMS?
- ❌ Who manages product catalog?
- ❌ What approval workflows exist?
- ❌ What analytics/reporting needed?
- ❌ User management interface?

**Workshop Plan Reference:** Session 4, Part 3 (Lines 542-556)
**Why It Matters:** Admin portal affects development scope
**Workshop Priority:** MEDIUM - Must define in Session 4
**Business Impact:** Comprehensive admin portal may require additional development time

---

#### 10. Integration Specifications - Duke IT Requirements
**Meeting Coverage:** None - **Duke IT was NOT present**
**Critical Questions Unanswered:**
- ❌ What specific API endpoints exist TODAY?
- ❌ When will API documentation be available?
- ❌ When will sandbox/test environments be ready?
- ❌ What authentication methods? (OAuth 2.0, API keys, SSO?)
- ❌ What rate limits and throttling constraints exist?
- ❌ Who at Duke IT owns each system integration?
- ❌ What APIs need to be built by Duke IT?
- ❌ What's the timeline for Duke IT to build new APIs?

**Workshop Plan Reference:** Session 4, Part 2 (Lines 509-541)
**Why It Matters:** **CRITICAL** - Project timeline depends on API availability
**Workshop Priority:** **HIGHEST** - Duke IT MUST attend Session 4
**Business Impact:** If APIs don't exist, timeline slips significantly

---

#### 11. Security & Compliance Requirements
**Meeting Coverage:** None
**Critical Questions Unanswered:**
- ❌ Authentication method: SSO with Duke systems or separate login?
- ❌ Data encryption requirements (at rest, in transit)?
- ❌ Audit logging requirements?
- ❌ Penetration testing requirements before launch?
- ❌ Who conducts security review? (Duke team, third-party?)
- ❌ What security standards must be met? (SOC 2, ISO 27001?)

**Workshop Plan Reference:** Session 4, Part 4 (Lines 567-574)
**Why It Matters:** Security requirements affect architecture decisions
**Workshop Priority:** HIGH - Must define in Session 4
**Business Impact:** Security compliance could delay launch if not addressed early

---

#### 12. Go-Live Planning & Rollout Strategy
**Meeting Coverage:** None
**Critical Questions Unanswered:**
- ❌ Soft launch vs full launch?
- ❌ Phased rollout by user segment or geography?
- ❌ Pilot program with subset of contractors?
- ❌ Q2-Q3 2026 timeline still realistic after scoping?

**Workshop Plan Reference:** Session 4, Part 4 (Lines 580-587)
**Why It Matters:** Launch strategy affects testing and training timelines
**Workshop Priority:** MEDIUM - Must plan in Session 4
**Business Impact:** Phased rollout reduces risk but extends timeline

---

## Why Scoping Meetings ≠ Discovery Workshops

### What Scoping Meetings Accomplished:
- ✅ Vendor understood RFP requirements
- ✅ Vendor proposed technical approach
- ✅ High-level alignment on scope
- ✅ Identified major unknowns
- ✅ Vendor submitted proposal

### What Discovery Workshops Will Accomplish:
- 🎯 Duke validates requirements with REAL data
- 🎯 Business rules documented formally
- 🎯 Duke IT provides integration specifications
- 🎯 Scope decisions made (MVP vs Phase 2)
- 🎯 Wireframes created collaboratively
- 🎯 Assumptions validated before development
- 🎯 Shared understanding across Duke teams

### The Critical Difference:

| **Scoping Meetings** | **Discovery Workshops** |
|----------------------|-------------------------|
| Vendor asking questions | Duke documenting answers |
| Solution-first approach | Discovery-first approach |
| RFP compliance focus | Requirements validation focus |
| Business team only | **Duke IT must participate** |
| High-level discussion | Detailed specifications |
| Vendor proposing | Duke deciding |

---

## Key Vendor Assumptions That Need Validation

### Orases Made These Assumptions (Need Duke Confirmation):

1. **Orchestration Layer** (Meeting2:42:15-44:36)
   - **Assumption:** Orases will build middleware to orchestrate between Commerce/Dynamics
   - **Needs Validation:** Is Duke IT comfortable with vendor-built orchestration?

2. **Custom CMS** (Meeting2:10:23-11:46)
   - **Assumption:** Custom CMS better than third-party
   - **Needs Validation:** Does Duke want custom or off-the-shelf?

3. **Service Catalog Database** (Meeting1:39:12-40:44)
   - **Assumption:** Ad-hoc service catalog doesn't exist anywhere
   - **Needs Validation:** Confirm no existing product database

4. **Non-Native Customer Database** (Meeting1:24:36-26:41)
   - **Assumption:** Need to build new customer database for non-natives
   - **Needs Validation:** Can any existing Duke systems be leveraged?

5. **Contractor Availability** (Meeting1:43:35)
   - **Assumption:** Contractors provide availability windows
   - **Needs Validation:** Do contractors have scheduling systems today?

**WORKSHOP ACTION:** Session 1 must validate these assumptions with Duke IT present

---

## Strategic Recommendations

### 🚨 KEEP ALL 4 WORKSHOP SESSIONS

**Why:** The scoping meetings were vendor-response sessions, not discovery sessions. Workshops are needed to validate requirements before final vendor selection and development kickoff.

---

### SESSION 1 UPDATED STRATEGY
**Status:** 60% covered in meetings, but needs Duke IT validation
**New Focus:**

1. **Invite Duke IT Team**
   - Leslie James (IT Manager) MUST attend
   - Clark Frederickson (Solution Architect) MUST attend
   - They were absent from scoping meetings

2. **Validate Vendor Assumptions**
   - Confirm orchestration layer approach
   - Validate system architecture proposed
   - Review CMS strategy

3. **Document API Status**
   - What endpoints exist TODAY (not "will exist")
   - Sandbox access timeline
   - Duke IT owners for each integration

4. **Persona Validation with Data**
   - Pull actual customer data to validate personas
   - Get percentages for each segment
   - Confirm pain points with customer research

**Pre-Session 1 Homework Still Critical:**
- ✅ List of all systems that store customer data
- ✅ Sample data exports from Commerce/Dynamics
- ✅ API documentation (what exists today)
- ✅ Duke IT attendance confirmed

---

### SESSION 2 UPDATED STRATEGY
**Status:** 20% covered in meetings - HIGHEST PRIORITY SESSION
**New Focus:**

1. **Walk Through REAL Service Requests**
   - **CRITICAL:** Pull 3-5 real (anonymized) examples
   - Show actual data in systems
   - Document exception scenarios

2. **Define HPP Coverage Rules**
   - **MUST HAVE:** How is eligibility determined?
   - **MUST HAVE:** Who decides coverage?
   - **MUST HAVE:** Where do rules live?

3. **Specify Contractor Matching Algorithm**
   - **MUST HAVE:** What factors drive assignment?
   - **MUST HAVE:** Automated vs manual decisions
   - **MUST HAVE:** Availability tracking method

4. **Document Pricing Structure**
   - **MUST HAVE:** Who sets ad-hoc pricing?
   - **MUST HAVE:** Approval workflows
   - **MUST HAVE:** Regional variation rules

**Pre-Session 2 Homework Critical:**
- ✅ 3-5 real service request examples (anonymized)
- ✅ Screen recordings of current process
- ✅ HPP coverage rules documentation
- ✅ Contractor assignment process documentation

---

### SESSION 3 UPDATED STRATEGY
**Status:** 30% covered in meetings - SCOPE DECISIONS NEEDED
**New Focus:**

1. **Make MVP Scope Decisions**
   - **DECIDE:** Warranty tracking MVP or Phase 2?
   - **DECIDE:** Multi-property MVP or Phase 2?
   - **DECIDE:** Home inventory mandatory or optional?

2. **Define DIY Content Requirements**
   - **SPECIFY:** Content volume at launch (how many articles/videos?)
   - **SPECIFY:** Who creates content?
   - **SPECIFY:** Content approval process

3. **Home Inventory Data Model**
   - **SPECIFY:** Required fields vs optional
   - **SPECIFY:** Appliance types to track
   - **SPECIFY:** Data entry methods (manual, barcode, photo)

4. **Finalize CMS Approach**
   - **DECIDE:** Custom CMS (Orases proposal) or third-party?
   - **SPECIFY:** Admin user roles and permissions

**Pre-Session 3 Homework Critical:**
- ✅ Customer data: How many have multiple properties?
- ✅ DIY content examples or existing resources
- ✅ Who will create/maintain content?
- ✅ Multi-property customer analysis

---

### SESSION 4 UPDATED STRATEGY
**Status:** 10% covered in meetings - DUKE IT MUST ATTEND
**New Focus:**

1. **Integration Specifications with Duke IT**
   - **DUKE IT REQUIRED:** Leslie James & Clark Frederickson
   - **SPECIFY:** Exact API endpoints available today
   - **SPECIFY:** Authentication methods
   - **SPECIFY:** Rate limits and constraints
   - **TIMELINE:** When will sandbox be available?

2. **API Dependency List**
   - **DOCUMENT:** What APIs Duke IT needs to build
   - **ASSIGN:** Duke IT owner for each
   - **TIMELINE:** When will each be ready?

3. **Security & Compliance**
   - **DECIDE:** SSO or separate login?
   - **SPECIFY:** Data encryption requirements
   - **SPECIFY:** Audit logging requirements
   - **PLAN:** Security review process

4. **Go-Live Strategy**
   - **DECIDE:** Soft launch or full launch?
   - **PLAN:** Phased rollout approach
   - **SPECIFY:** Pilot contractor program

**Pre-Session 4 Homework CRITICAL:**
- ✅ Duke IT attendance CONFIRMED
- ✅ API documentation status update
- ✅ Security requirements documentation
- ✅ Infrastructure preferences/constraints

---

## Immediate Action Items (Before Session 1)

### 1. **Ensure Duke IT Participation**
- [ ] Confirm Leslie James (IT Manager) attendance
- [ ] Confirm Clark Frederickson (Solution Architect) attendance
- [ ] Brief them on scoping meetings (share transcripts)

### 2. **Gather Data for Validation**
- [ ] Pull customer data to validate persona percentages
- [ ] Determine multi-property customer percentage
- [ ] Analyze Spanish-speaking customer base (for localization decision)
- [ ] Pull service request volume by type

### 3. **Document Current State**
- [ ] List all systems storing customer data
- [ ] Document API availability status
- [ ] Gather sample data exports from Commerce/Dynamics
- [ ] Screen record current service request process

### 4. **Prepare Real Examples**
- [ ] 3-5 anonymized service request examples:
  - HPP covered service (routine)
  - HPP covered service (emergency)
  - Ad-hoc service request
  - Service that was denied/not covered

### 5. **Clarify Ownership**
- [ ] Who creates DIY content? (Internal, vendor, contractors?)
- [ ] Who manages product catalog?
- [ ] Who approves pricing changes?

---

## Key Questions to Answer Before Workshops

### Business Questions:
1. What percentage of customers have multiple properties?
2. What percentage of customers speak Spanish (localization priority)?
3. How many customers are expected to download app in Year 1?
4. What's the target adoption rate? (30% used in cost analysis)

### Technical Questions:
1. What APIs exist TODAY vs need to be built by Duke IT?
2. When will API sandbox access be available?
3. Is SSO with Duke systems required or optional?
4. What security standards must be met?

### Content Questions:
1. Who will create DIY content?
2. How much content needed at launch?
3. Is there existing content to migrate?
4. What's the content approval process?

### Scope Questions:
1. Is warranty tracking MVP or Phase 2?
2. Is multi-property support MVP or Phase 2?
3. Is Spanish localization MVP or Phase 2?
4. What's the minimum viable home inventory?

---

## Risk Assessment

### 🔴 HIGH RISK - Requires Immediate Attention

1. **Duke IT Not Involved Yet**
   - **Risk:** API availability unknown, timeline at risk
   - **Mitigation:** Ensure Duke IT attends Session 1 & 4
   - **Impact if Not Addressed:** Project timeline could slip significantly

2. **Business Rules Undefined**
   - **Risk:** Can't build eligibility checking without rules
   - **Mitigation:** Document rules formally in Session 2
   - **Impact if Not Addressed:** App can't determine HPP coverage automatically

3. **MVP Scope Not Finalized**
   - **Risk:** Vendor proposals may not reflect actual MVP
   - **Mitigation:** Make scope decisions in Session 3
   - **Impact if Not Addressed:** Budget and timeline estimates inaccurate

### 🟡 MEDIUM RISK - Needs Clarification

1. **Content Creation Strategy Unclear**
   - **Risk:** Content may not be ready at launch
   - **Mitigation:** Define content strategy and ownership in Session 3
   - **Impact if Not Addressed:** Launch delayed or app launches without DIY content

2. **Pricing Structure Still in Development**
   - **Risk:** Can't build pricing logic without structure
   - **Mitigation:** Define pricing model in Session 2
   - **Impact if Not Addressed:** Ad-hoc service revenue model unclear

3. **Security Requirements Undefined**
   - **Risk:** Architecture decisions may not meet security needs
   - **Mitigation:** Document security requirements in Session 4
   - **Impact if Not Addressed:** Security review could force rework

---

## Conclusion

### Your Workshop Series is CRITICAL Because:

1. **Scoping meetings were vendor-focused** → Workshops need to be Duke-focused validation
2. **Duke IT wasn't involved** → Must participate in workshops to provide integration specs
3. **Vendor made assumptions** → Duke needs to validate before development
4. **Business rules undefined** → Must document formally in workshops
5. **Scope decisions pending** → MVP vs Phase 2 must be decided
6. **Real examples not reviewed** → Need to walk through actual service requests
7. **Integration specs missing** → Need specific endpoints, not just "we'll integrate"

### The workshops will transform:
- ❌ Vendor assumptions → ✅ Duke-validated requirements
- ❌ High-level discussions → ✅ Detailed specifications
- ❌ RFP responses → ✅ Wireframes and user flows
- ❌ "We think it works this way" → ✅ "Here's exactly how it works"

### Next Steps:
1. **Schedule all 4 workshop sessions** (don't skip any)
2. **Ensure Duke IT attends** Session 1 & Session 4
3. **Complete pre-session homework** for Session 1
4. **Pull real customer data** to validate personas
5. **Document current processes** with screenshots/recordings

---

## Appendix: Coverage Matrix

| Workshop Topic | Meeting Coverage | Gap Analysis | Priority |
|---------------|------------------|--------------|----------|
| User Personas | 🟡 Discussed generally | Need percentages & validation | HIGH |
| Current Systems | 🟢 Well covered | Need Duke IT validation | HIGH |
| Data to Build | 🟢 Confirmed | Ready for detailed specs | MEDIUM |
| Service Process | 🟡 High-level only | Need real examples | HIGHEST |
| HPP Coverage Rules | 🔴 Not discussed | CRITICAL gap | HIGHEST |
| Contractor Matching | 🟡 Mentioned only | Need detailed algorithm | HIGHEST |
| Pricing Structure | 🟡 In development | Need to finalize | HIGH |
| Payment Strategy | 🟢 Well covered | Ready for workflows | MEDIUM |
| Home Inventory | 🟡 Discussed scope | Need data model decision | HIGH |
| DIY Content | 🟡 Acknowledged | Need strategy & volume | HIGH |
| Warranty Tracking | 🔴 Not decided | MVP vs Phase 2? | MEDIUM |
| Multi-Property | 🟡 Mentioned | MVP vs Phase 2? | MEDIUM |
| CMS Approach | 🟢 Discussed | Need to decide custom vs third-party | MEDIUM |
| Admin Interface | 🟡 CMS only | Need full requirements | MEDIUM |
| API Specifications | 🔴 Duke IT absent | CRITICAL gap | HIGHEST |
| Security & Compliance | 🔴 Not discussed | Need requirements | HIGH |
| Go-Live Planning | 🔴 Not discussed | Need rollout strategy | MEDIUM |

**Legend:**
🟢 Well Covered (70-100%)
🟡 Partially Covered (30-70%)
🔴 Not Covered (0-30%)

---

**Document Prepared By:** Claude Code
**Next Review:** After Session 1 completion
**Distribution:** Duke RS Product Team, Duke IT, Workshop Facilitators
