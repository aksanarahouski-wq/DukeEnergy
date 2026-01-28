# Duke Customer App - Deliverable Samples

## Purpose of These Documents

These Product Requirements Documents (PRDs) demonstrate **how Orases and Duke can achieve scope and timeline alignment at the requirements document level WITHOUT diving into Jira ticket-level detail** for every feature. This approach enables:

✅ **Clear deliverable boundaries** - Each PRD is a "Work Package" with defined scope and estimated effort
✅ **Effort estimation at PRD level** - Teams can estimate work packages without creating 100+ Jira tickets first
✅ **Dependency identification** - PRDs show dependencies between deliverables
✅ **Business alignment** - Stakeholders understand WHAT is being built and WHY
✅ **Risk visibility** - Risks surfaced early, before detailed task breakdown
✅ **Change management** - Re-prioritization discussions happen at PRD level, not ticket level

## Why These 3 Deliverables Were Selected

Based on the Customer App scope workshops, these **3 deliverables represent the critical path for Phase 1 MVP** and should be prioritized first:

### 1. Customer Registration & Onboarding
**Why First:**
- **Foundational requirement** - Nothing else works without it
- **800K+ existing Duke customers** need digital identities
- **Non-native customer acquisition** depends on frictionless signup
- **API integration risk** - Duke Enterprise API must be validated early

**Estimated Timeline:** To be determined during planning
**Estimated Effort:** To be estimated after technical review

**Dependencies:**
- Duke Enterprise API (customer validation, HPP plan linking)
- Email service setup
- Database schema approval

### 2. Service Booking - HPP Covered Services
**Why Second:**
- **Core value proposition** for 800K existing customers with HPPs
- **Highest business impact** - Reduces call center volume by 40%
- **Customer pain point #1** - Phone-only service booking (15 min avg)
- **Revenue protection** - Customers with self-service have 2x retention

**Estimated Timeline:** To be determined during planning
**Estimated Effort:** To be estimated after technical review

**Dependencies:**
- Deliverable #1 complete (customers must have accounts)
- Duke Commerce/Dynamics API (order creation, contractor lookup)
- Admin portal for manual confirmation

### 3. Home Inventory & Profile Building
**Why Third:**
- **Strategic competitive moat** - Proprietary customer data
- **Enables upselling** - 30% lift in plan enrollment
- **Drives engagement** - Users with 80%+ profile have 3x higher LTV
- **Predictive maintenance** - Proactive reminders drive preventative bookings

**Estimated Timeline:** To be determined during planning
**Estimated Effort:** To be estimated after technical review

**Dependencies:**
- Deliverable #1 complete (customers must have accounts)
- Barcode API (optional but recommended)
- Contractor portal enhancements (for contractor-captured data)

---

## How These PRDs Enable Work Package-Level Scope Alignment

### Traditional Approach (Jira-First)
1. Duke says: "We want service booking"
2. Orases creates 100+ Jira tickets for service booking
3. Duke reviews tickets: "Wait, we meant something different"
4. Re-work: Delete 50 tickets, create 50 new ones
5. **Result:** Misalignment discovered late, after detailed planning

### Orases Approach (PRD-First)
1. Duke says: "We want service booking"
2. Orases writes PRD: 20 pages covering goals, requirements, dependencies, risks
3. Duke reviews PRD: "This looks right, except we need emergency triage"
4. Orases updates PRD (1 section changed, 30 minutes of work)
5. PRD approved → NOW create Jira tickets for implementation
6. **Result:** Alignment achieved before detailed planning, minimal rework

---

## What Each PRD Contains

### 1. Executive Summary
- **What:** 2-3 paragraph overview of the deliverable
- **Why it matters:** Business impact, user value
- **Key features:** 3-5 bullet points
- **Enables:** Duke stakeholders to understand deliverable in 2 minutes

### 2. Background & Problem Statement
- **Current state:** How things work today
- **Problems:** 3-4 specific pain points with business impact
- **Impact if not addressed:** What happens if we don't build this
- **Enables:** Justification for prioritization decisions

### 3. Goals & Success Criteria
- **Primary goals:** What we're trying to achieve (measurable)
- **Success criteria:** How we know we succeeded
- **Non-goals:** What's explicitly out of scope
- **Enables:** Clear boundaries, prevents scope creep

### 4. Scope (In/Out)
- **In scope:** Specific features/functionality for THIS deliverable
- **Out of scope:** Features deferred to Phase 2+
- **Enables:** Work package estimation without creating Jira tickets

### 5. Functional Requirements
- **What the system must do:** Detailed but not implementation-specific
- **Example:** "System shall validate password complexity" (NOT "Add regex validator to UserController.ts line 42")
- **Enables:** Duke business stakeholders can review without technical knowledge

### 6. Dependencies & Risks
- **Dependencies:** What must be ready before work starts
- **Risks:** What could go wrong, mitigation strategies
- **Enables:** Project planning, dependency sequencing

### 7. Implementation Plan
- **Phases:** High-level breakdown (Phase 1: Core, Phase 2: Enhancements, etc.)
- **Estimated timeline:** High-level effort estimate (NOT "473 story points across 47 tickets")
- **Rollout strategy:** How will this be deployed
- **Enables:** Timeline discussion at work package level

### 8. Success Metrics
- **KPIs:** How we measure success post-launch
- **Measurement plan:** When and how to review metrics
- **Enables:** Alignment on business outcomes, not just feature delivery

---

## How Orases Uses PRDs for Work Package Estimation

### Step 1: PRD Review & Scoping
- Product team writes PRD
- Engineering reviews PRD, identifies technical unknowns
- Team estimates effort at **PRD level**: "This is a large/medium/small effort"
- **No Jira tickets created yet**

### Step 2: Duke Stakeholder Review
- Duke Product Owner reviews PRD
- Duke SMEs review functional requirements
- Duke IT reviews dependencies
- Feedback incorporated, PRD approved
- **Still no Jira tickets created**

### Step 3: Sprint Planning (Just-In-Time Jira Ticket Creation)
- **Only when ready to start work**: Engineering breaks PRD into Jira tickets
- Tickets created for next 1-2 sprints only (not entire PRD)
- As work progresses, more tickets created as needed
- **Why:** Requirements may evolve during development; creating all tickets upfront leads to rework

### Step 4: Agile Execution
- Teams work in 2-week sprints
- PRD remains source of truth for "what" and "why"
- Jira tickets are "how" (implementation tasks)
- If priorities change, discuss at PRD level first

---

## Example: Re-prioritization Discussion at PRD Level

### Scenario: Duke Wants to Re-prioritize

**Without PRDs (Jira-Level Discussion):**
- Duke: "Can we deprioritize tickets CUST-234 through CUST-289?"
- Orases: "Um, let me look those up... CUST-234 is barcode scanning... CUST-235 is barcode API integration... CUST-236 is..."
- Duke: "Wait, what's barcode scanning for again?"
- Orases: "It's part of home inventory... or was it onboarding? Let me check the epic..."
- **Result:** 30-minute meeting to understand 55 tickets, still unclear on business impact

**With PRDs (Work Package Discussion):**
- Duke: "Can we deprioritize Home Inventory & Profile Building?"
- Orases: "Let's look at PRD #3. It's a large effort, enables upselling and customer retention. Depends on Registration being complete. Risks if deprioritized: can't deliver on gamification, no predictive maintenance."
- Duke: "What if we keep just the core inventory features and cut gamification?"
- Orases: "That's Phase 1 in the PRD. We can defer Phases 2-4 (gamification, rewards, home health scorecard) to later."
- **Result:** 10-minute discussion, clear business trade-offs understood

---

## How These PRDs Map to Project Planning

### Project Phases
- **Planning & Analysis:** Initial discovery and requirements gathering
- **Design & Architecture:** System design and technical architecture
- **Development MVP:** Core feature implementation
- **Alpha/Beta Development:** Feature enhancements and iteration
- **Testing & QA:** Quality assurance and user acceptance testing
- **Deployment:** Production rollout

### Orases Work Package Approach (Based on PRDs)

#### Deliverable #1: Registration & Onboarding
- **Phase 1:** Planning, Duke API integration, database schema
- **Phase 2:** Core registration flow, email verification
- **Phase 3:** Multi-property support, onboarding enhancements
- **Deliverable:** Customers can create accounts, validate against Duke Enterprise, link HPP plans

#### Deliverable #2: Service Booking - HPP
- **Phase 1:** Core booking flow, coverage check
- **Phase 2:** Contractor assignment, scheduling
- **Phase 3:** Status tracking, notifications
- **Phase 4:** Service history, admin tools
- **Deliverable:** Customers can book covered services, receive confirmations, track status

#### Deliverable #3: Home Inventory
- **Phase 1:** Core inventory building (manual entry, list view)
- **Phase 2:** Barcode scanning, public data import
- **Phase 3:** Gamification & loyalty rewards
- **Phase 4:** Maintenance reminders
- **Phase 5:** Home health scorecard, contractor capture
- **Deliverable:** Customers build home profiles, earn rewards, receive maintenance reminders

**Note:** Work packages can be executed in parallel workstreams. Team A can build Service Booking while Team B starts Home Inventory.

---

## Key Takeaways for Duke

### 1. PRDs Enable Scope Discussions Without Jira Tickets
- **Each PRD = 1 Work Package** (with high-level effort estimate)
- Duke can review, approve, or request changes at PRD level
- Detailed Jira tickets created just-in-time during development cycles
- **Benefit:** Faster alignment, less rework

### 2. PRDs Show Business Impact, Not Just Features
- Each PRD explains: **Problem → Solution → Business Value**
- Duke stakeholders can prioritize based on ROI, not technical complexity
- **Benefit:** Better prioritization decisions

### 3. PRDs Surface Dependencies & Risks Early
- Dependencies identified BEFORE detailed planning
- Risks with mitigation strategies
- **Benefit:** Duke can address API readiness, contractor participation, etc. upfront

### 4. PRDs Support Agile Re-prioritization
- Re-prioritization discussions happen at Work Package level
- Example: "Deprioritize PRD #3 (Home Inventory) to Phase 2"
- Clear business trade-offs: What do we lose? What dependencies are affected?
- **Benefit:** Informed re-prioritization decisions without Jira ticket-level detail

### 5. PRDs Align with Project Timeline
- Each PRD maps to specific project phases
- Duke can see: "Service Booking = Work Package 2"
- **Benefit:** High-level sequencing and dependency alignment without 200-page Gantt chart

---

## Next Steps

1. **Review PRDs:** Duke Product Owner + SMEs review PRDs #1, #2, #3
2. **Feedback Session:** Meeting to discuss each PRD and align on scope
3. **Approval:** Duke approves PRDs or requests revisions
4. **Detailed Planning:** Once approved, Orases creates detailed task breakdown for implementation
5. **Kickoff:** Development begins on Deliverable #1 (Registration & Onboarding)

---

## Contact

**Questions about these PRDs?**
- Aksana Rahouski (Orases Product Lead)
- Tom Witt (Orases CEO)

**Want to create more PRDs?**
- Candidates: Service Booking - Ad-Hoc, Payment Integration, DIY Content, Contractor Portal, etc.
- Process: PRD writing, stakeholder review, approval, detailed planning

---

END OF DOCUMENT
