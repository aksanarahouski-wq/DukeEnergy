# Your Role on This Project
### Team Onboarding | Step 4 of 5

---

## How We Work Together

This is a collaborative team. Every role has a clear owner, but ownership does not mean working in isolation. We surface problems early, support each other across disciplines, and make decisions together when they affect the whole project. No one is left to figure it out alone — and no one succeeds alone either.

The chain below describes accountability and sequencing, not hierarchy. Understanding where you sit — what you receive, what you produce, and what you hand off — is how we avoid gaps, rework, and missed deliverables.

## How the Team Is Structured

```
Client (Duke) ←→ Product Manager / Business Analyst
                         ↓
                  Project Manager
                (schedule, reporting, risk)
                         ↓
              Lead Developer + Designer
              (architecture, design, TRD)
                         ↓
                    Engineers
                 (build, test, ship)
```

No role operates in isolation. Every output becomes someone else's input.

---

## Product Manager — Aksana Rahouski

You are the primary point of contact with Duke Energy and the ultimate decision-maker on what the team builds and in what order. You sit at the intersection of client, business, and team.

**You own:**

- **Client relationship** — All substantive communication with Duke's Product Owner and stakeholders flows through you or with your awareness. You protect the team from conflicting direction.
- **Backlog prioritization** — You decide what gets built in what order, in close collaboration with Duke's Product Owner. Nothing enters a sprint without your sign-off.
- **Feature definition** — You own the product vision for each feature. You know not just what Duke asked for, but what they actually need and why.
- **Sprint approval flow** — You submit the written estimate to Duke before every sprint begins. No estimate submitted = no sprint starts. This is contractually required and non-negotiable.
- **UAT coordination** — You coordinate and facilitate User Acceptance Testing with Duke. You own the acceptance process from delivery through sign-off.
- **Budget awareness** — You track cumulative spend against the SOW estimate. You ensure the PM has the information needed to flag budget risks before they become problems.
- **Scope defense** — When Duke requests something outside the approved backlog, you are the one who says "that needs a Change Order" or "let's add it to the backlog." You do not absorb informal scope expansion.

**Shared with BA:**
- Workshop and discovery session facilitation
- Backlog grooming — reviewing, refining, and clarifying tickets before they reach development
- Ownership of priorities — BA supports you in keeping the backlog organized and well-defined

**Your rhythm:**
- Sprint planning meeting (internal) every 2 weeks
- Written estimate to Duke before each sprint begins
- Prioritization and alignment meeting with Duke (weekly during discovery, as-needed during development)
- UAT sessions when features are delivered to staging
- Monthly stakeholder meeting attendance

---

## Business Analyst

You are the bridge between what Duke describes and what the team can build. Your primary output is documentation — requirements that are precise enough for developers to implement and reviewable enough for Duke to approve.

**You own:**
- **PRD drafting** — You write the first draft of every Product Requirements Document. This covers what we're building, why, who uses it, functional requirements, scope boundaries, and test cases. The PM reviews and approves before it goes to Duke.
- **TRD support** — You work closely with the Lead Developer during TRD creation. You clarify requirements, answer questions, and ensure the technical plan maps back to business intent.
- **Discovery documentation** — During workshops and discovery sessions, you capture decisions, open questions, and requirements. You are the note-taker and follow-up owner.
- **Acceptance criteria** — You write clear, testable acceptance criteria for every Jira ticket. If QA or an engineer cannot determine whether a ticket is "done" from reading the acceptance criteria, it needs to be rewritten.

**Shared with PM:**
- Workshop and discovery session facilitation — you co-facilitate; PM leads the relationship and agenda, you run the documentation and structured questioning
- Backlog grooming — you are in the weeds on ticket quality, sequencing, and dependencies
- Priority management — you support the PM in keeping the backlog ordered and ready for the next sprint

**Your rhythm:**
- Discovery sessions and workshops with Duke (active during analysis phase)
- PRD drafting and review cycles — continuous throughout the project
- Backlog grooming session every sprint
- TRD review with Lead Developer before each sprint
- UAT support — you help write UAT test cases and track outcomes

**Key rule:** PRD is approved by Duke before the Lead Developer writes the TRD. TRD is complete before any sprint begins. If you are writing a PRD and the Lead Developer is already starting architecture work, that sequencing is wrong — flag it.

---

## Project Manager

You keep the engine running. Your job is to make sure the team always knows what they are working on, the client always knows where the project stands, and risk is surfaced before it becomes a problem.

**You own:**
- **Schedule** — Maintain the project timeline, milestone tracking, and sprint calendar. You know at any given moment whether we are on track for MVP on September 30, 2026.
- **Sprint status reports** — Every 2 weeks, end of sprint, without exception. Written, sent to Duke's Product Owner. These are a contractual commitment.
- **Jira hygiene** — Tickets are up to date, sprints are organized, statuses reflect reality. If a ticket is "In Progress" and the engineer moved to something else, the ticket should reflect that.
- **Risk log** — You maintain a live list of project risks. When a risk materializes or escalates, you surface it to the PM with enough time to act on it.
- **Meeting coordination** — You schedule, track attendance, and follow up on action items for all recurring project meetings.
- **Trello (client-facing board)** — You maintain the client-visible board so Duke can see progress at a high level without needing Jira access.
- **Budget tracking support** — You track hours by sprint against the SOW estimate and flag to the PM when we are trending high.

**Your rhythm:**
- Sprint planning at the start of every sprint (internal)
- End-of-sprint status report to Duke
- Risk log review weekly (internal)
- Monthly stakeholder meeting prep with PM

**Key rule:** You do not make scope or prioritization decisions. When Duke asks for something or a change is needed, you surface it to the PM — you do not negotiate scope with the client.

---

## Lead Developer

You are the technical authority on this project. You validate that what the PM and BA define can actually be built, define how it gets built, and ensure the engineering team has the clarity they need to execute well.

**You own:**
- **Technical Requirements Documents (TRD)** — After the PM/BA finishes a PRD and Duke approves it, you write the TRD. This defines the architecture, data models, API design, implementation approach, and technical acceptance criteria. The TRD is your sign-off that a feature is technically feasible and the team knows how to build it.
- **Architecture decisions** — You make the call on technical architecture. When there are tradeoffs, you document them and communicate the decision and rationale.
- **Code quality** — You set the bar for code standards, review practices, and what "done" means technically.
- **Feasibility gating** — If a PRD describes something that cannot be built as written — due to technical constraints, integration limitations, or Duke IT dependencies — you raise it before the sprint begins. Never after.
- **Integration technical design** — You own the technical integration patterns for Commerce, Dynamics, and the App DB. You are the primary point of contact for Duke IT on technical questions.
- **Effort estimates** — You provide the effort estimates that the PM uses to write the sprint estimate submitted to Duke.

**Your rhythm:**
- PRD review with PM/BA after every PRD is drafted
- TRD writing before each sprint or work package
- Sprint planning (internal) at the start of every sprint
- Code review throughout development
- Architecture sync with PM as new features approach planning

**Key rule:** Do not start building before the TRD is written and the sprint is approved by Duke in writing. This is not about slowing you down — it is how we protect the team from rework when Duke's understanding of a feature evolves.

---

## Designer

You translate product requirements into user experience. You work from approved PRDs and produce designs that the development team can implement and that Duke can react to before any code is written.

**You own:**
- **UX/UI design** — Wireframes, flows, and high-fidelity mockups for all customer-facing and admin-facing screens. You produce designs based on approved PRDs.
- **Design system** — You establish and maintain the design language for the project (component library, patterns, spacing, typography) in alignment with Duke Energy brand standards.
- **Handoff to development** — Your designs are production-ready before they go to engineers. Specs, assets, and interaction notes are included. Engineers should not need to guess about any visual detail.
- **Prototype feedback** — Where applicable, you produce clickable prototypes for Duke review before development begins on complex flows.
- **Brand compliance** — Duke has documented brand standards and web standards. Every design must be validated against them.

**Your rhythm:**
- Design begins after PRD is approved by Duke — not before
- Design review with PM before presenting to Duke
- Design handoff to Lead Developer before TRD is finalized (so architecture accounts for UI needs)
- Feedback incorporation cycles with Duke during UAT

**Key rule:** You design for what is in the approved PRD. If Duke asks for design changes during a review that go beyond the approved scope, flag it to the PM before incorporating — it may require a backlog item or Change Order.

---

## Engineer(s)

You build the product. Your job is to implement tickets correctly, completely, and in a way that the team can maintain and extend. You are the last line of defense before a feature reaches QA.

**You own:**
- **Implementation** — Build features according to the accepted criteria in the Jira ticket, the functional requirements in the PRD, and the technical guidance in the TRD. All three documents are your source of truth.
- **Unit testing** — Where appropriate, write unit tests for business logic and critical paths. QA tests the feature end-to-end; you test the code.
- **Surfacing blockers early** — If you hit something unexpected — an API that doesn't behave as documented, a requirement that is ambiguous, a dependency that isn't ready — you raise it the same day. Not at the end of the sprint.
- **Definition of done** — A ticket is done when: code is written and peer-reviewed, unit tests pass, the feature works against the acceptance criteria in staging, and QA has signed off.

**Your rhythm:**
- Sprint planning at the start of every sprint
- Daily standup (async or sync, PM and Project Manager will define format)
- Code review before merging
- Demo participation when features are ready for client review

**Key rule:** "Done" means working in staging and validated by QA. A feature is not done because code was written. Do not move a ticket to "Done" until it passes acceptance criteria.

---

## How We All Connect — The Handoff Chain

```
Duke describes need
        ↓
PM + BA run discovery / workshop
        ↓
BA drafts PRD → PM reviews → Duke approves
        ↓
Designer creates UX/UI → PM reviews → Duke reviews
        ↓
Lead Dev reads PRD → Q&A with BA → writes TRD
        ↓
PM submits sprint estimate → Duke approves in writing
        ↓
BA writes Jira tickets with acceptance criteria
        ↓
Engineers build → peer review → staging
        ↓
QA tests against PRD/TRD acceptance criteria
        ↓
PM coordinates UAT with Duke
        ↓
Duke accepts in writing
        ↓
PM / Project Manager deliver sprint status report
```

If any step in this chain is skipped, the next step will produce something wrong. The chain exists to prevent rework, not to create bureaucracy.

---

*Next: Step 5 — How We Work (Sprint Process & Tools)*

*Source: SOW #1 V6, Development Framework Overview, Team structure as defined by PM*

---

## Glossary of Abbreviations

| Abbreviation | Full Term |
|---|---|
| **BA** | Business Analyst |
| **MVP** | Minimum Viable Product — the core version of the app, targeting September 30, 2026 |
| **PM** | Product Manager (Aksana Rahouski, Orases) — unless context specifies "Project Manager" |
| **PRD** | Product Requirements Document — defines what we are building and why; the BA writes the first draft, the PM approves, Duke approves before any development begins |
| **QA** | Quality Assurance — the process of testing features to ensure they meet acceptance criteria before delivery |
| **SOW** | Statement of Work — the contract between Orases and Duke Energy governing this engagement |
| **TRD** | Technical Requirements Document — defines how we will build what the PRD describes; written by the Lead Developer |
| **UAT** | User Acceptance Testing — formal testing conducted by Duke to verify delivered features meet requirements |
| **UX/UI** | User Experience / User Interface — the design discipline covering how the product looks and how users interact with it |
