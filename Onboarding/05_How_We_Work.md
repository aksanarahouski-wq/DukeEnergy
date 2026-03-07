# How We Work — Sprint Process & Tools
### Team Onboarding | Step 5 of 5

---

## How We Work Together

This team operates on a foundation of **shared accountability and mutual support.** Every role has a clear owner — but ownership does not mean isolation. We back each other up, surface problems early, and make decisions together when they affect the whole team.

Clear accountability means everyone knows what they own. Collaborative culture means no one is left to figure it out alone. These two things are not in conflict — they are how good teams work.

Every feature follows this path before a developer writes a line of code:

```
PRD (WHAT + WHY) → TRD (HOW) → Backlog Ticket → Sprint Approval → Build → QA → UAT → Acceptance
```

We run **2-week sprints** using an iterative, agile approach tailored for a T&M client engagement. The process is designed around one core principle: **nothing gets built without a clear requirement, a technical plan, and written client approval.** This protects the team, ensures we deliver what Duke actually needs, and keeps the project on budget.

---

## The Three-Phase Requirements Framework

### Phase 1: Product Requirements Document (PRD)
**Owner: PM + BA (jointly)**

The PRD defines what we are building and why. It is the foundation for everything that follows. No TRD is written, no design begins, and no estimate is submitted to Duke until a PRD is approved.

**A PRD must include:**
- Executive summary (what it is, why it's needed, business impact)
- Goals, success criteria, and explicit non-goals (what's out of scope)
- Target users and their pain points
- Functional requirements — specific, unambiguous descriptions of what the system must do
- Test cases — UAT scenarios and integration test cases written before development starts
- Dependencies and risks

**PRD process:**
1. PM + BA draft based on discovery sessions, workshops, and Duke stakeholder input
2. Lead Developer reviews the draft — not to write it, but to flag technical risks, dependency blockers, or feasibility concerns before the document is finalized
3. PM reviews and approves the draft before it leaves the team
4. Duke's Product Owner reviews and provides feedback
5. PM + BA incorporate feedback and resolve open questions
6. Duke approves in writing — this is the gate that unlocks design and TRD work

The Lead Developer's early involvement in PRD review is intentional. It prevents scope from being defined in a vacuum and allows technical risks to be surfaced and addressed before they become sprint problems.

**Key rule:** The PRD is a business document. Keep it jargon-free and implementation-agnostic. If a PRD starts describing database schemas or API patterns, that belongs in the TRD.

---

### Phase 2: Technical Requirements Document (TRD)
**Owner: Lead Developer (with BA support)**

The TRD defines how we will build what the PRD describes, and confirms it is technically feasible. The Lead Developer cannot write a TRD without first reading the PRD and asking questions of the PM/BA.

**A TRD must include:**
- Technical architecture — system design, components, data models
- Implementation approach — how each functional requirement gets built
- API design — endpoints, inputs, outputs, error handling
- Integration patterns — how this feature connects to Commerce, Dynamics, App DB, or Duke IT APIs
- Technical constraints and dependencies — what must exist before this can be built
- Effort breakdown — task-level breakdown used to generate the sprint estimate
- Technical testing requirements — unit test coverage expectations, integration test scenarios

**TRD process:**
1. Lead Developer reviews the approved PRD
2. Q&A session with PM/BA to resolve technical ambiguities
3. Lead Developer writes TRD
4. PM reviews to confirm technical approach aligns with business intent
5. If TRD reveals a constraint that changes scope or timeline, PM communicates to Duke before sprint begins
6. Lead Developer and PM align — TRD is the green light for backlog ticket creation

**Key rule:** If something in the PRD is not technically feasible as written, the Lead Developer raises it during TRD — not after the sprint has started. Raising it late costs everyone time and money.

---

### Phase 3: Backlog Creation & Sprint Execution
**Owner: PM + BA (tickets), full team (execution)**

Once PRD and TRD are aligned, work is broken into executable units.

**Epics:** Logical groupings of related features (e.g., "Service Booking — HPP Covered Services"). One PRD may produce one or more epics.

**Jira Tickets:** Atomic units of work, sized to be completable within a few days. Each ticket must contain:
- Clear description of the work
- Functional requirements from the PRD (what the system must do)
- Technical guidance from the TRD (how to implement)
- Acceptance criteria — specific, testable conditions that define "done"
- Dependencies on other tickets
- Links to PRD and TRD

**BA writes the tickets.** Engineers should be able to pick up a ticket cold and understand what to build, why it matters, and how to know when it is complete.

---

## The Sprint Cycle

### Sprint Length: 2 Weeks

```
WEEK 1, DAY 1 — Sprint Planning
WEEK 1, DAYS 2-5 — Development
WEEK 2, DAYS 1-4 — Development + QA
WEEK 2, DAY 5 — Sprint Review + Status Report
(→ repeat)
```

### Before the Sprint Starts

**Sprint approval gate** — the most important step in the entire process:

1. PM reviews the proposed sprint scope with the Lead Developer (effort estimates from TRD)
2. PM drafts a written sprint estimate and submits to Duke's Product Owner
3. Duke Product Owner approves in writing (email is sufficient)
4. Sprint begins

**No written approval = sprint does not start.** This is contractually required and protects us from disputes about what was authorized.

---

### Sprint Planning (Internal — Day 1)

Attendees: Full team
Duration: 1–2 hours

Agenda:
1. Review sprint goal — what are we delivering this sprint and why
2. Walk through tickets in order of priority — BA presents each ticket, engineer asks questions
3. Engineers confirm understanding of acceptance criteria
4. Lead Developer surfaces any technical concerns before work starts
5. Assign tickets — engineers pull from the top of the prioritized queue
6. Confirm definition of done for the sprint

**Output:** Every team member knows exactly what they are building this sprint, has no unresolved questions about their tickets, and agrees the sprint goal is achievable.

---

### During the Sprint

**Daily Standup** — async or sync, 15 minutes max. Format:
- What did I complete yesterday?
- What am I working on today?
- Do I have any blockers?

**Blocker rule:** If you are blocked, raise it in standup the same day — not at the end of the week. A blocker that sits for 3 days kills the sprint. The PM or Lead Developer resolves blockers same-day where possible.

**In-progress discipline:**
- Update your Jira ticket status as you move through work (To Do → In Progress → In Review → Done)
- When a ticket is ready for QA, move it and tag the QA owner
- Do not mark a ticket Done until QA has validated it against acceptance criteria in staging

---

### End of Sprint

**Sprint Review / Demo**

We do not demo every sprint. We demo when meaningful, demonstrable functionality is complete — typically aligned with an epic completion or a significant milestone. A half-built feature that does not work end-to-end is not demo-ready.

When we do demo:
- Attendees: Full Orases team + Duke Product Owner and stakeholders
- The demo is led by whoever is best suited to present the work — PM or BA, depending on the feature and the audience. This will be decided per demo, not set as a standing rule.
- Team members present their own features where appropriate
- Duke provides feedback — PM captures it and turns it into backlog items or acceptance decisions

**Sprint Status Report (every sprint, no exceptions)**

Within 24 hours of sprint end, PM or Project Manager delivers a written status report to Duke. Format:

```
Sprint [#] Status Report — [Date Range]

Sprint Goal: [One sentence]

Completed This Sprint:
- [Feature/ticket] — [brief description]
- [Feature/ticket] — [brief description]

In Progress / Carrying Over:
- [Feature/ticket] — [reason, expected completion]

Next Sprint Preview:
- [High-level what's planned]

Risks / Blockers:
- [Any active risks or dependencies needing Duke action]

Budget: [Hours used this sprint] / [Sprint estimate]
```

This report is our primary transparency mechanism with Duke. It also documents our delivery record. Never skip it.

---

## The Requirement Flow for a Single Feature

Here is how a single feature moves from idea to production:

| Step | Who | Output | Gate |
|---|---|---|---|
| Duke describes need | Duke + PM | Workshop notes, requirements brief | — |
| Discovery / workshops | PM + BA + Duke SMEs | Validated requirements, open questions resolved | — |
| PRD draft | BA (PM reviews; Lead Dev flags risks) | Draft PRD | PM approves |
| PRD review with Duke | PM + Duke PO | Feedback, revisions | Duke approves in writing |
| UX/UI design | Designer | Wireframes, mockups, prototype | PM reviews; Duke reviews |
| PRD → TRD handoff | BA briefs Lead Dev | — | — |
| TRD | Lead Developer | TRD document | PM reviews |
| Backlog tickets | BA | Jira tickets with acceptance criteria | Lead Dev reviews |
| Sprint estimate | PM | Written estimate to Duke | Duke approves in writing |
| Development | Engineers | Code in feature branch | Peer review |
| QA | QA / Engineers | Test pass/fail against acceptance criteria | All criteria pass |
| Demo (if applicable) | Team | Live demo in staging | Duke provides feedback |
| UAT | PM + Duke team | UAT sign-off | Duke accepts in writing |
| Deployment | Lead Dev + PM | Feature in production | — |

---

## Handling Scope Requests Mid-Sprint

Duke will occasionally ask for changes, additions, or "quick" adjustments. How to handle:

1. **Never say no directly** — say "let me take a look at the impact and get back to you"
2. PM assesses: Is this within the approved PRD scope? Is it small enough to absorb?
3. If yes to both: PM adds it to the current sprint if capacity allows, or queues it next sprint
4. If it changes scope, timeline, or budget: PM informs Duke in writing with the impact and options before proceeding
5. Material changes require a Change Order

**The golden rule:** Every informal ask that gets executed without documented approval is a risk we absorb. Document first, build second.

---

## Defect Handling

Defects found during QA or UAT are categorized by severity:

| Severity | Definition | Blocks Acceptance? |
|---|---|---|
| **Critical** | System unusable, data loss, security vulnerability, no workaround | Yes |
| **High** | Major feature broken, significant user impact, workaround impractical | Yes |
| **Medium** | Feature partially broken, workaround exists | Not automatically — but can block if core flows are impaired |
| **Low** | Cosmetic, edge case, easy workaround | No — added to backlog |

All defects are fixed regardless of origin. Defect resolution is billed as usual under T&M.

---

## Tools

| Tool | Used By | Purpose |
|---|---|---|
| **Jira** | Full Orases team | Sprint tracking, backlog, ticket management, defect logging |
| **Trello** | PM + Duke team | Client-visible progress board (high-level, no implementation detail) |
| **Confluence** | PM, BA, Lead Dev | PRDs, TRDs, architecture docs, meeting notes, decisions log |
| **Email** | Full team + Duke | Primary async communication channel for client-facing updates, approvals, and delivery records |
| **Google Meet** | Full team + Duke | Scheduled meetings, sprint reviews, discovery sessions; ad-hoc meetings scheduled as needed |
| **Slack / Teams** | Orases team (internal) | Internal team coordination only — not used for client communication |
| **Design Tool** | Designer + Lead Dev | UX/UI design, component library, design handoff — tool TBD |
| **GitHub** | Engineering | Version control, branching, pull requests, CI/CD |
| **AWS** | Infrastructure | Hosting and environment infrastructure — environment structure TBD |

### Environment Strategy

**TBD — to be defined with Duke input.** The environment names, ownership, and access model will be confirmed during kickoff and early discovery. At minimum, we expect separate environments for development, testing/UAT, and production — but the exact structure, naming, and Duke's involvement in each must be agreed upon before development begins.

---

## Communication Norms

**With Duke:**
- All substantive communication goes through the PM
- If Duke contacts you directly with a scope request or timeline question, loop in the PM before responding
- Written record of everything — follow up verbal conversations with a brief email confirming what was discussed

**Within the team:**
- Blockers raised the same day they are discovered
- Decisions that affect timeline, scope, or approach are surfaced to PM same-day
- If something in a ticket is ambiguous, ask before building — do not interpret and proceed
- No one works on something that is not in the approved sprint without PM sign-off

---

## Definition of Done

A feature is done when all of the following are true:

- [ ] Code is written and peer-reviewed
- [ ] Unit tests written and passing (where applicable)
- [ ] Feature works end-to-end in staging against all acceptance criteria
- [ ] QA has tested and signed off
- [ ] No Critical or High defects open against this feature
- [ ] PM has been notified and delivery has been documented in writing to Duke
- [ ] Jira ticket status is updated to Done

If any checkbox is unchecked, the feature is not done.

---

*You have completed onboarding. Welcome to the team.*

*Source: SOW #1 V6, Development Framework Overview, PRD/TRD Templates, Team delivery process*

---

## Glossary of Abbreviations

| Abbreviation | Full Term |
|---|---|
| **API** | Application Programming Interface — a connection point that allows two software systems to talk to each other |
| **AWS** | Amazon Web Services — the cloud infrastructure platform we use for hosting |
| **BA** | Business Analyst |
| **CI/CD** | Continuous Integration / Continuous Deployment — automated pipeline for building, testing, and releasing code |
| **HPP** | Home Protection Plan — Duke's monthly subscription product that covers repair/replacement of home systems and appliances |
| **MVP** | Minimum Viable Product — the core version of the app, targeting September 30, 2026 |
| **PM** | Product Manager (Aksana Rahouski, Orases) — unless context specifies "Project Manager" |
| **PO** | Product Owner — Duke's designated decision-maker; must approve sprint estimates and accept deliverables in writing |
| **PRD** | Product Requirements Document — defines what we are building and why; the BA writes the first draft, the PM approves, Duke approves before any development begins |
| **QA** | Quality Assurance — the process of testing features to ensure they meet acceptance criteria before delivery |
| **SLA** | Service Level Agreement — a committed response or resolution time |
| **SME** | Subject Matter Expert — a Duke stakeholder with deep knowledge of a specific domain (operations, IT, legal, etc.) |
| **SOW** | Statement of Work — the contract between Orases and Duke Energy governing this engagement |
| **T&M** | Time and Materials — the billing model; we bill for actual hours worked at $250/hour blended rate |
| **TRD** | Technical Requirements Document — defines how we will build what the PRD describes; written by the Lead Developer |
| **UAT** | User Acceptance Testing — formal testing conducted by Duke to verify delivered features meet requirements before acceptance |
| **UX/UI** | User Experience / User Interface — the design discipline covering how the product looks and how users interact with it |
