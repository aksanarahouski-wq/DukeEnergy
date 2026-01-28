# Section 1.2 - REVISED Final Language Options

## Current Duke Language (PROBLEMATIC):

> "No work under section 1.3 will begin until Orases provide a written estimate and CLIENT issues written approval for the relevant work package or Sprint. CLIENT may re-prioritize the Backlog at any time; Orases will promptly provide written impact (timeline, scope, budget). Re-prioritization that remains within the approved scope and budget for the current Sprint/Phase will not require a Change Order and will not increase fees. In case not-to-exceed (NTE) sum will be determined for any Deliverable Orases will not exceed any approved NTE without CLIENT's prior written approval and will maintain a shared backlog with periodic status reports on progress and budget burn. Silence or inaction by CLIENT does not constitute approval."

**Problem:** The sentence "Re-prioritization that remains within the approved scope and budget for the current Sprint/Phase will not require a Change Order and will not increase fees" exposes Orases to unlimited free rework and sunk costs, especially problematic for multi-sprint features.

---

## OPTION 1: Balanced Protection (RECOMMENDED)

This option protects Orases while giving Duke flexibility. Works for both single-sprint and multi-sprint work packages.

### Replace Duke's paragraph with:

**1.2. Prioritization of Work**

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks identified throughout the Analysis Activities.

**Work Approval Process:**
- Throughout the project, work for Section 1.3 (Design, Development, and Implementation) will begin once CLIENT has reviewed, approved, and prioritized the proposed work
- CLIENT has final decision-making authority on priorities
- No work under section 1.3 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant Work Package
- Each Work Package may span multiple sprints (typically 1-3 sprints) depending on feature complexity
- In case a not-to-exceed (NTE) sum is determined for any Deliverable, Orases will not exceed any approved NTE without CLIENT's prior written approval
- Orases will maintain a shared backlog with periodic status reports on progress and budget burn at both work package and sprint levels
- Silence or inaction by CLIENT does not constitute approval

**CLIENT Re-prioritization Rights:**

CLIENT may re-prioritize the Backlog at any time to align with evolving business needs. Upon receiving a re-prioritization request, Orases will promptly provide a written impact analysis (typically within 2-3 business days) addressing timeline, scope, budget, technical dependencies, and risk implications.

The impact of re-prioritization depends on timing and nature of the change:

**Between Work Packages ("Clean Re-prioritization"):**
- CLIENT may reorder, add, or remove features from the backlog that have not yet been started
- If reprioritized features are of similar size/complexity, have no technical dependencies affecting in-progress or completed work, and require no architectural changes, no Change Order will be required and fees will not increase
- If re-prioritization affects dependencies, requires architectural adjustments, or impacts the timeline for Key Milestones (Section 04), Orases will document the impact and Parties will mutually agree on the approach, which may require a Change Order per Section 06

**During Active Development ("Mid-Development Re-prioritization"):**
- CLIENT may request re-prioritization of work in progress, subject to impact assessment
- For multi-sprint features (e.g., features spanning 2-3 sprints), reprioritization may occur mid-way through the development cycle
- Orases will provide impact analysis within 2 business days covering:
  - Hours already invested in deprioritized work (CLIENT remains obligated to pay for work completed to date)
  - Percentage completion of current work package
  - Recommended approach: complete to logical stopping point (e.g., finish current sprint within multi-sprint feature) vs. immediate halt
  - Timeline impact for current and subsequent work packages/sprints
  - Additional effort required for context switching, dependency adjustments, or rework
  - Technical debt implications from incomplete foundation work
- Parties will mutually agree on how to proceed based on the impact analysis

**Handling Re-prioritization Costs:**
- **Sunk Costs:** Hours invested in work that is subsequently deprioritized will be billed to CLIENT as part of the applicable work package, even if the feature is incomplete
- **Multi-Sprint Features:** For work packages spanning multiple sprints, sunk costs include foundation work, architecture, infrastructure, and partially completed functionality
- **Rework and Dependencies:** If re-prioritization creates additional effort due to disrupted dependencies, architectural changes, incomplete infrastructure, or technical debt from halted work, Orases will document the additional effort in the impact analysis
- **Change Order Threshold:** Additional effort resulting from re-prioritization that exceeds **40 hours or $10,000** (cumulative per development phase) will require mutual written agreement and may require a Change Order per Section 06
- **Minor Adjustments:** Re-prioritization with minimal impact (< 40 hours additional effort) will be accommodated within the approved phase budget as goodwill, provided cumulative impact remains reasonable

**Process:**
- Orases will track and report re-prioritization impacts in regular status updates
- Both Orases and CLIENT agree to work in good faith to minimize disruption from re-prioritization
- CLIENT will endeavor to provide re-prioritization requests between work packages when feasible to minimize impact, particularly for multi-sprint features
- For work packages in progress, CLIENT and Orases will discuss optimal stopping points to minimize technical debt
- Priorities may be updated throughout the Project at CLIENT's direction; Orases will provide updated estimates regarding timeline, scope, or budget impact within 2-3 business days

---

## OPTION 2: More Duke-Friendly (Higher Risk to Orases)

This keeps more of Duke's language but adds minimum protections. Accommodates multi-sprint features.

### Replace Duke's paragraph with:

**1.2. Prioritization of Work**

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks identified throughout the Analysis Activities. Throughout the project, work for Section 1.3 (Design, Development, and Implementation) will begin once CLIENT has reviewed, approved, and prioritized the proposed work. CLIENT has final decision-making authority on priorities.

**Work Approval and Re-prioritization:**
- No work under section 1.3 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant Work Package
- Each Work Package may span multiple sprints (typically 1-3 sprints depending on feature complexity)
- CLIENT may re-prioritize the Backlog at any time; Orases will promptly provide written impact analysis (timeline, scope, budget, dependencies, technical risk) typically within 2-3 business days
- **Re-prioritization between work packages** that remains within the approved scope and budget for the phase and does not disrupt technical dependencies or in-progress work will not require a Change Order and will not increase fees
- **Re-prioritization during active development** (mid-development of work package) may result in:
  - Sunk costs for hours already invested in deprioritized work (CLIENT pays for work completed to date)
  - For multi-sprint features, sunk costs include foundation work completed in earlier sprints
  - Additional effort for context switching, rework, or dependency adjustments
  - Timeline adjustments for current and subsequent deliverables
  - Change Order if additional effort is material (exceeds 5% of work package budget or $10K, whichever is less)
- In case a not-to-exceed (NTE) sum is determined for any Deliverable, Orases will not exceed any approved NTE without CLIENT's prior written approval and will maintain a shared backlog with periodic status reports on progress and budget burn
- Silence or inaction by CLIENT does not constitute approval

---

## OPTION 3: Maximum Protection for Orases (May Face Pushback)

This option gives Orases the most protection for both small and large work packages.

### Replace Duke's paragraph with:

**1.2. Prioritization of Work**

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks identified throughout the Analysis Activities. Throughout the project, work for Section 1.3 (Design, Development, and Implementation) will begin once CLIENT has reviewed, approved, and prioritized the proposed work. CLIENT has final decision-making authority on priorities.

**Work Approval Process:**
- No work under section 1.3 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant Work Package
- Each Work Package represents a cohesive unit of development that may span 1-3 sprints depending on feature complexity
- Orases will maintain a shared backlog with periodic status reports on progress and budget burn, tracking both sprint-level and work package-level progress
- In case a not-to-exceed (NTE) sum is determined for any Deliverable, Orases will not exceed any approved NTE without CLIENT's prior written approval
- Silence or inaction by CLIENT does not constitute approval

**Re-prioritization Process:**

CLIENT may request re-prioritization of the Backlog to align with business needs. Orases will provide written impact analysis within 2-3 business days (or sooner for urgent requests) addressing:
- Timeline impact (current work package/sprint and downstream impacts)
- Budget impact (sunk costs, additional effort needed, rework)
- Technical impact (dependencies, architectural implications, technical debt)
- Completion status for multi-sprint features
- Risk assessment and recommended approach

**Types of Re-prioritization:**

1. **Backlog Re-sequencing (Between Work Packages):** Reordering features that have not yet been started. Generally does not require Change Order unless it:
   - Disrupts technical dependencies or architectural sequence
   - Impacts Key Milestone dates (Section 04)
   - Requires significant rework of completed features

2. **Mid-Development Re-prioritization:** Changing priorities during active development of a work package. Will result in:
   - CLIENT obligation to pay for all hours invested to date in deprioritized work
   - For multi-sprint features, all foundation work completed in prior sprints is billable
   - Assessment of impact on work package deliverables and timeline
   - Evaluation of optimal stopping point to minimize technical debt
   - Potential Change Order if additional effort or timeline impact is material (exceeds 30 hours or 5% of work package budget, whichever is less)

3. **Major Re-scoping:** Adding, removing, or significantly changing features. Handled via Change Order per Section 06.

**Re-prioritization Impact Management:**

- Orases will track cumulative impact of re-prioritization requests at both sprint and work package levels
- Minor re-prioritization impacts (< 30 hours per work package or < 80 hours per phase) will be accommodated within approved budgets as goodwill
- Material impacts exceeding these thresholds will require Change Order
- For multi-sprint features, CLIENT and Orases will discuss optimal pause points (e.g., completing current sprint before switching priorities)
- CLIENT and Orases will work collaboratively to minimize disruption by:
  - Timing re-prioritization requests between work packages when feasible
  - Completing in-progress work to logical stopping points before changing direction
  - Considering technical dependencies when re-sequencing features
  - Recognizing that multi-sprint features have higher sunk costs if deprioritized mid-stream

Both Orases and CLIENT agree to work in good faith to balance business agility with project efficiency.

---

## OPTION 4: Compromise with "Re-prioritization Budget Buffer"

This creative option gives Duke flexibility while protecting Orases with a built-in buffer. Scales appropriately for larger work packages.

### Replace Duke's paragraph with:

**1.2. Prioritization of Work**

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks identified throughout the Analysis Activities. Throughout the project, work for Section 1.3 (Design, Development, and Implementation) will begin once CLIENT has reviewed, approved, and prioritized the proposed work. CLIENT has final decision-making authority on priorities.

**Work Approval and Budget Management:**
- No work under section 1.3 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant Work Package
- Each Work Package may span 1-3 sprints depending on feature complexity (e.g., simple features = 1 sprint, complex features = 3 sprints)
- Each work package budget will include:
  - **Primary Development Budget:** [90-95%] for planned feature development
  - **Agile Flexibility Reserve:** [5-10%] to accommodate re-prioritization impacts, minor scope adjustments, and technical discoveries
  - For larger multi-sprint work packages, a 10% reserve is recommended to account for greater re-prioritization risk
- In case a not-to-exceed (NTE) sum is determined for any Deliverable, Orases will not exceed any approved NTE without CLIENT's prior written approval
- Orases will maintain a shared backlog with periodic status reports showing progress, budget burn, and Flexibility Reserve utilization at both sprint and work package levels
- Silence or inaction by CLIENT does not constitute approval

**CLIENT Re-prioritization:**

CLIENT may re-prioritize the Backlog at any time. Orases will promptly provide written impact analysis (timeline, scope, budget, dependencies, risk) typically within 2-3 business days.

**Using the Agile Flexibility Reserve:**

The Flexibility Reserve may be used for:
- Sunk costs when work in progress is deprioritized
- Foundation work completed in early sprints of multi-sprint features that are subsequently deprioritized
- Additional effort for context switching and dependency adjustments
- Minor rework resulting from re-prioritization
- Completing deprioritized work to logical stopping points (e.g., finishing current sprint to minimize technical debt)
- Maintaining architectural coherence when multi-sprint features are halted mid-development

**When Re-prioritization Requires Change Order:**

If re-prioritization impacts exceed the available Flexibility Reserve, or if re-prioritization affects Key Milestones (Section 04) or approved NTE limits, Orases will notify CLIENT and provide:
- Documentation of Flexibility Reserve utilization to date
- Estimated additional effort beyond the Reserve
- For multi-sprint features, breakdown of completed vs. incomplete work
- Recommended path forward

Parties will mutually agree on how to proceed, which may include:
- Reallocating reserve from future work packages
- Executing a Change Order for additional budget
- Adjusting timeline expectations
- Modifying scope to stay within budget

**Best Practices:**

Both Parties commit to:
- Timing re-prioritization requests between work packages when feasible
- For multi-sprint features, considering natural breakpoints (e.g., completing current sprint) before reprioritizing
- Considering technical dependencies when re-sequencing work
- Completing in-progress features to logical stopping points before shifting priorities
- Transparent communication about Reserve utilization and remaining capacity

---

## Side-by-Side Comparison

| Aspect | Duke's Language | Option 1 (Balanced) | Option 2 (Duke-Friendly) | Option 3 (Orases Protection) | Option 4 (Buffer) |
|--------|-----------------|---------------------|--------------------------|------------------------------|-------------------|
| **Multi-sprint support** | Not addressed | Explicit | Explicit | Explicit | Explicit |
| **Duke flexibility** | Unlimited | High | High | Medium | High |
| **Orases protection** | None | Good | Fair | Strong | Good |
| **Sunk costs covered** | No | Yes | Yes | Yes | Yes (from buffer) |
| **Rework covered** | No | Yes (if >$10K) | Yes (if >5% or $10K) | Yes (if >30hrs/5%) | Yes (from buffer) |
| **Change order threshold** | None defined | $10K or 40hrs/phase | 5% or $10K/WP | 30hrs or 5%/WP | When buffer exhausted |
| **Multi-sprint cost recognition** | No | Yes | Yes | Yes | Yes (scaled reserve) |
| **Clarity** | Vague | Very clear | Clear | Very clear | Clear |
| **Likely Duke acceptance** | N/A (their draft) | Good | Very Good | Pushback likely | Good |

---

## RECOMMENDED STRATEGY

### 1. Lead with Option 1 (Balanced Protection)
- Fair to both parties
- Clear thresholds appropriate for multi-sprint features
- Protects against major risks
- Explicitly addresses larger work packages
- Still gives Duke significant flexibility

### 2. Have Option 4 (Buffer) as Backup
- Creative approach Duke might like
- Scales appropriately (10% reserve for larger features)
- Builds in cost protection via "Flexibility Reserve"
- Feels less restrictive than explicit thresholds

### 3. Fall back to Option 2 if Necessary
- Keeps more of Duke's language
- Minimum viable protection
- Still addresses multi-sprint scenarios
- Only if Duke strongly pushes back

### 4. Avoid accepting Duke's current language as-is
- Too much risk for multi-sprint features
- Ambiguous about who pays for what
- Could cost Orases $50K+ in absorbed rework on large features
- No recognition that larger features have greater reprioritization risk

---

## INTERNAL SUMMARY FOR ALIGNMENT

**Core Issue:**
Duke's language assumes reprioritization is "free" within approved budget, but doesn't account for:
- Multi-sprint features being deprioritized mid-development
- Sunk costs including foundation work from earlier sprints
- Context switching costs amplified across longer development cycles
- Technical debt from incomplete multi-sprint features

**Key Talking Points:**
- A 3-sprint feature ($60K, 240 hours) deprioritized mid-way = $30K+ sunk costs
- Foundation work in Sprint 1 has value even if feature isn't completed
- Larger features need larger buffers or clearer thresholds
- "Work Package" terminology accommodates both small (1 sprint) and large (3+ sprint) features

**Recommended Approach:**
Option 1 with higher thresholds (40 hours/$10K) to account for multi-sprint feature risks

**Bottom Line:**
Multi-sprint features amplify reprioritization risk. Never accept language where mid-development reprioritization is "free" - especially critical for features spanning multiple sprints.
