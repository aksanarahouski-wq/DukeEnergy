# SOW Quick Reference — Duke Energy RS Home Services App
### Orases Delivery Team

**SOW #1 | Orases x Duke Energy | Effective: February 2026 | Last updated: March 6, 2026**

---

## 1. What We're Building and Why It Matters

**Project:** Residential Solutions (RS) Home Services and Warranty Application for Duke Energy.

Two interconnected systems:
- **Customer-facing app** (iOS, Android, web/PWA) — self-service booking for home protection plan (HPP) warranty services and ad-hoc services, home inventory, maintenance reminders, real-time service tracking
- **Admin backend** — Duke operations portal for managing customers, contractors, service orders, catalog pricing, and cross-system data

**Serving:** 800K+ existing Duke/Piedmont HPP customers + new non-native (non-Duke utility) customers.

**Key business outcome Duke cares about:** Reduce service request time from 15 minutes (phone) to under 3 minutes. Every feature decision should be measured against that.

---

## 2. Our Two Key Milestone Dates

| Milestone | Target Date | What It Means |
|---|---|---|
| MVP | September 30, 2026 | Core customer booking + HPP management live in production |
| Phase 1 Complete | December 31, 2027 | Full scope delivered |

These are **Key Milestones**. Any slip of more than 10 business days requires a signed Change Order — the client can initiate that based on scope decisions, but it needs to be proactively communicated and aligned with both parties. We plan backward from September 30, 2026 on Day 1.

---

## 3. How Work Gets Authorized — Follow This Religiously

This is a **Time & Materials engagement**. The contract has a strict gate:

> "No work under section 2.4 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant work package or Sprint."

Our flow every sprint:
1. We provide a written estimate for the next sprint/work package
2. Duke's Product Owner approves in writing (email counts)
3. Work begins
4. We deliver written sprint status at end of every sprint — regardless of whether there's a demo

**No work begins without written approval.** This protects the team and the engagement — if Duke changes priorities mid-sprint without a Change Order, we can reference the approved work package. It also ensures Duke is always aligned with what we're delivering before we deliver it.

---

## 4. Budget — Know the Numbers, Protect the Burn Rate

| Item | Number |
|---|---|
| Blended hourly rate | $250/hour |
| Estimated monthly spend | $80K–$105K |
| Total SOW estimate | ~$1,051,400 |
| 85% alert obligation | ~$893,690 — we must notify Duke in writing |
| Hard stop threshold | ~$1,156,540 (110% of estimate — needs Change Order) |

**We proactively track cumulative spend against the $1,051,400 estimate.** When we hit ~$893K, we are contractually required to send written notice to Duke.

If the project is trending over, we surface it early with options (scope reduction, re-prioritization, Change Order). We never silently exceed the estimate — that's a contract breach.

Rate increases: we can raise rates once per year with 90 days notice, but **not in Year 1**.

---

## 5. The Estimate Is Not a Cap — But Treat It Like One

The $1,051,400 is non-binding, but exceeding it by more than 10% without a Change Order is a breach. Practically:
- Track actuals against estimates every sprint
- Flag overruns at the work-package level before they compound
- If a feature is taking significantly more effort than estimated, notify Duke immediately with written context and options — do not absorb the cost silently

The contract explicitly says: "If Orases reasonably anticipates that actual effort will materially exceed the applicable estimate, Orases will notify CLIENT and provide context and options."

---

## 6. Deliverable Acceptance — Run a Tight Process

When we deliver a sprint or milestone:
- Duke has **10 business days** to accept or reject in writing
- Silence at 10 days = deemed accepted (this protects us)
- If rejected: we have **10 business days** to fix or provide a Response Plan
- Duke then has another **10 business days** to accept or reject again

**Practical tips:**
- Deliver to the Product Owner via written communication (email/Confluence), not just in a meeting
- Document the delivery date clearly — the clock starts there
- If Duke goes quiet, send a reminder at day 7
- If we need more time to fix something, communicate before our 10-day window closes

---

## 7. Acceptance Criteria — What We Must Ship

Deliverables are accepted when they:
- Conform to the approved PRD and Development Backlog
- Are **free of Critical and High defects** at delivery
- Pass our internal QA and complete UAT with Duke's team in staging
- Meet security/performance requirements from the approved PRD/TRD
- Include required documentation

| Defect Severity | Our Obligation at Delivery |
|---|---|
| Critical | Must be resolved — blocks acceptance |
| High | Must be resolved — blocks acceptance |
| Medium | Does not auto-block, but can if core journeys are broken |
| Low | Add to backlog |

**Important:** Medium defects on core customer journeys (booking, payments, scheduling) can collectively justify rejection even if no single one is Critical. We do not ship broken happy paths and call them Medium.

---

## 8. Defects — How We Handle Them

All defects are fixed regardless of origin — whether found by our team, Duke, or end users. Defect resolution is billed as usual under T&M.

If there's a dispute about root cause: **fix it first, discuss later.** We never withhold remediation pending cost resolution. We do not let a billing question become a production incident.

---

## 9. SLA Commitments During Hypercare and Support

**Hypercare** = 10 calendar days post each production release. Same team, T&M billed.

| Severity | Hypercare Response | Prod Support Response |
|---|---|---|
| Critical | Within 1 business hour | Within 2 business hours |
| High | Within 2 business hours | Within 4 business hours |
| Medium | N/A | Within 1 business day |
| Low | N/A | Within 3 business days |

Response = acknowledgement and triage, not full resolution. The team must be reachable during support hours: **9am–5pm ET, Mon–Fri**, excluding Orases holidays.

---

## 10. The Biggest Risks We Own

| Risk | What to Do |
|---|---|
| Duke IT delayed on API access | Flag at kickoff. APIs for Commerce CRM, Dynamics, and Data Fabric are explicit unknowns. We need sandbox access within 2 weeks of kickoff — escalate if delayed. |
| Duke's Product Owner is slow to approve | We do not start work without approval. Document every request for approval and the date sent. |
| Scope creep via informal requests | Every ask outside an approved work package = a Change Order or backlog item. We do not absorb verbal scope changes. |
| Team estimating low on integrations | Integration complexity with Duke systems is unproven. Pad estimates until APIs are documented and tested. |
| 3 consecutive sprint misses | This triggers client rights to demand resource changes or performance credits. Track sprint velocity from Sprint 1. |
| Key resource loss (PM, Tech Lead) | We must notify Duke in advance for key role substitutions. Have a succession plan. |

---

## 11. What Duke Owes Us — Hold Them Accountable

The SOW explicitly lists CLIENT responsibilities. We use this list when delays are on their side:

- Designate and maintain a single empowered Product Owner
- Attend all scheduled meetings
- Provide timely feedback and written approvals
- Give access to existing systems, APIs, and infrastructure
- Provide access to SMEs for requirements validation
- Complete UAT and provide formal written acceptance
- Hold monthly stakeholder meetings with their executive sponsors
- Notify us in advance of stakeholder changes, leave, or business case changes

If Duke fails on any of these and it causes delay, document it in writing immediately. The SOW states: "Material failure of CLIENT to provide support or cooperation may result in Orases' delay or inability to provide the Services." That language protects our team's schedule and budget position.

---

## 12. Our Governance Responsibilities

**We maintain:**
- Written sprint status reports every 2 weeks (every sprint, no exceptions)
- A living Project Plan with milestones, dependencies, and resource assumptions
- A Development Backlog with prioritized, estimated work packages
- PRD and TRD for every feature before development begins
- Risk register — proactively surface risks in writing before they become issues
- Jira for our team, Trello visibility for Duke, Confluence for all documentation

**Sprint demos:** Only when meaningful functionality is complete — not every sprint. But written status goes out every sprint regardless.

**Monthly stakeholder meeting:** Required by contract. Duke runs it with their executives — we attend and provide project status.

---

## 13. Change Orders — When We Need One

Get a Change Order (signed by both parties) before proceeding when:
- Duke requests features or work outside the approved backlog
- A Key Milestone will slip more than 10 business days
- Total fees will exceed ~$1.15M (110% of estimate)
- Duke's priorities change in a way that materially impacts scope, timeline, or budget

For smaller changes: we provide written impact (timeline, scope, budget) promptly and get written approval before executing. Every "quick add" that isn't documented is a risk we're absorbing.

---

## 14. The Sales Docs Are a Starting Point, Not Our Scope

Orases' December 2025 discovery documents are **reference only** (Appendix 1). They were created without Duke's IT team. Significant unknowns remain:

- API availability and integration capabilities
- Security and compliance requirements
- Integration complexity with Commerce CRM, Dynamics, Duke Data Fabric
- Production deployment constraints

Our first 4–8 weeks (Analysis Activities) are where the real scope gets defined. We run those workshops rigorously. The PRDs and TRDs we produce in that phase become the contract for every feature we build. **Get them approved in writing before a single line of code is written.**

---

*Source: DE-Orases SOW #1 V6, February 2026 | Last updated: March 6, 2026*

---

## Glossary of Abbreviations

| Abbreviation | Full Term |
|---|---|
| **BA** | Business Analyst |
| **CRM** | Customer Relationship Management — the software Duke uses to manage customer accounts (SAP Commerce for Duke electric customers, Microsoft Dynamics for P&G gas customers) |
| **HPP** | Home Protection Plan — Duke's monthly subscription product that covers repair/replacement of home systems and appliances |
| **iOS** | iPhone Operating System — Apple's mobile operating system |
| **MVP** | Minimum Viable Product — the core version of the app, targeting September 30, 2026 |
| **P&G** | Piedmont Natural Gas — Duke Energy's natural gas subsidiary |
| **PM** | Product Manager (Aksana Rahouski, Orases) — unless context specifies "Project Manager" |
| **PRD** | Product Requirements Document — defines what we are building and why; approved by Duke before any development begins |
| **PWA** | Progressive Web App — a web application that behaves like a native mobile app |
| **QA** | Quality Assurance — the process of testing features to ensure they meet acceptance criteria before delivery |
| **RS** | Residential Solutions — the Duke Energy business unit we are building for |
| **SLA** | Service Level Agreement — a committed response or resolution time; e.g., Critical defects must be acknowledged within 1 business hour during Hypercare |
| **SME** | Subject Matter Expert — a Duke stakeholder with deep knowledge of a specific domain (operations, IT, legal, etc.) |
| **SOW** | Statement of Work — the contract between Orases and Duke Energy governing this engagement |
| **T&M** | Time and Materials — the billing model; we bill for actual hours worked at $250/hour blended rate |
| **TRD** | Technical Requirements Document — defines how we will build what the PRD describes; written by the Lead Developer |
| **UAT** | User Acceptance Testing — formal testing conducted by Duke to verify delivered features meet requirements before acceptance |
