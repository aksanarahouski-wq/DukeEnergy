# Discovery Planning

This folder contains the discovery planning documents for the Duke Energy RS Home Services & Warranty Application (Phase 1 / MVP).

## How These Documents Work Together

```
Deliverable Prioritization Matrix     "What do we build, in what order, and why?"
              ↓
Discovery Strategy & Roadmap          "How do we discover each one? Timeline, sessions, dependencies."
              ↓
Wave1_Deliverable1_*                  "The actual prep for discovery session #1."
Wave1_Deliverable2_*                  (created as we get to each session)
Wave2_Deliverable3_*                  ...
```

The Matrix sets the order. The Roadmap sets the process. The deliverable docs are the execution — one per session.

---

## Document Descriptions

### Deliverable_Prioritization_Matrix.md

Ranks all 9 MVP deliverables and justifies the sequencing. Each deliverable is a **vertical slice** — not just a customer feature, but the full stack: customer UX, admin UX, data model, data sync, business rules, integration points, and design.

Scores deliverables against: foundational importance, revenue impact, Duke API dependency, business rules clarity, technical complexity, and MVP criticality. Groups them into 3 waves.

Also documents what is NOT a standalone deliverable (payment processing, contractor matching, emergency handling) and where those concerns live instead.

**Use when:** Justifying priority order, explaining scope to stakeholders, or answering "why are we doing X before Y?"

### Discovery_Strategy_and_Roadmap.md

The operational plan for how discovery runs. Covers:

- **Rolling wave approach** — discovery stays 2-3 weeks ahead of dev, not a waterfall phase
- **Per-deliverable summaries** — what's known, what needs discovery, blocking dependencies
- **Session format** — 6-block template (2-3 hours), who attends, what comes out
- **Week-by-week timeline** — mapping discovery → design → dev starts
- **Critical path items** — 7 things to push Duke on immediately at kickoff (API access, contractor data, legal, brand guidelines, etc.)
- **Risk register** — project-level risks with mitigations

**Use when:** Planning weekly work, prepping for sessions, tracking Duke dependencies, or onboarding someone to the discovery process.

### Wave1_Deliverable1_Registration_Onboarding.md

Deep-dive discovery prep for the first deliverable: Customer Registration, Onboarding & Customer Management.

Breaks the deliverable into 4 inseparable parts:
1. **Registration flow** — 3 customer types, validation logic, edge cases
2. **Customer profile** — the "Day 1" empty-state problem
3. **Admin customer management** — search, view, edit, manual enrollment queue
4. **Data sync strategy** — 5 scenarios with option tables and tradeoffs

Contains 29 numbered discovery questions (with "why it matters" and "who answers"), a source-of-truth-per-field matrix, definition of "done," a 3-hour session plan, and pre-session checklists for both Orases and Duke.

**Use when:** Preparing for or running the Deliverable #1 discovery session. The questions are the agenda.

---

## Key Concepts

**Vertical slice:** Every deliverable covers the full stack — customer experience + admin experience + data model + data sync + business rules + integration + design. Not just a screen or a feature.

**Discovery produces PRDs:** No PRDs exist before discovery. Discovery defines scope, the PRD documents it, dev builds it.

**Rolling waves:** We don't discover everything upfront. Wave 1 discovery feeds Wave 1 dev while Wave 2 discovery runs in parallel.

## Adding New Documents

As discovery progresses, add new deliverable documents following the naming pattern:

```
Wave1_Deliverable2_HPP_Service_Booking.md
Wave2_Deliverable3_Home_Inventory.md
Wave2_Deliverable4_HPP_Plan_Management.md
...
```

Each document should follow the same structure as Deliverable #1: what's known, what needs discovery (numbered questions), data sync implications, definition of done, session plan, and prep checklists.
