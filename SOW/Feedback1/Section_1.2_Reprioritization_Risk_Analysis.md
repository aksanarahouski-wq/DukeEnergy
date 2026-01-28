# Section 1.2 Reprioritization Language - Risk Analysis & Recommendation

## The Problem Statement

### Duke's Added Language:
> "CLIENT may re-prioritize the Backlog at any time; Orases will promptly provide written impact (timeline, scope, budget). Re-prioritization that remains within the approved scope and budget for the current Sprint/Phase will not require a Change Order and will not increase fees."

### Why This Is Risky for Orases:

This language assumes re-prioritization is "free" if it stays within the work package budget, but **ignores the real costs** of mid-flight changes:

1. **Sunk Costs**: Work already started on deprioritized features
2. **Dependencies**: Features often have technical dependencies that make sequence matter
3. **Rework**: Architecture decisions made for Feature A may need revision for Feature B
4. **Context Switching**: Developers lose productivity when switching between features
5. **Technical Debt**: Rushed deprioritization can leave incomplete code/infrastructure
6. **Integration Risk**: Some features must be built in a specific order for system coherence

## Real-World Scenarios That Would Hurt Orases

### Scenario 1: Mid-Development Deprioritization of Large Feature
**Work Package:** "Home Service Scheduling" - 3-sprint feature (estimated 240 hours, $60K)

**Sprint 1-2 (Weeks 1-4):**
- Orases completes database schema design, API architecture, core booking engine
- 120 hours invested, foundation laid for subsequent work

**Week 5 (Mid-way through the work package):** Duke says "deprioritize scheduling, start building payment integration instead"

**Impact:**
- 120 hours invested in scheduling with no completed deliverable
- Foundation work (database schema, APIs) must be shelved (technical debt)
- Payment integration requires different architectural approach
- **Who pays for the 120 hours?** Current language suggests Orases absorbs it
- Lost momentum and context on the scheduling feature

### Scenario 2: Dependency Disruption Across Phases
**Planned Sequence:**
1. Build customer authentication (Work Package 1, 2 sprints)
2. Build customer profile management (Work Package 2, 1 sprint) - depends on auth
3. Build appointment scheduling (Work Package 3, 3 sprints) - depends on profile

**Duke re-prioritizes after completing Work Package 1:** "Skip profile management, start scheduling in Work Package 2"

**Impact:**
- Scheduling needs profile data (dependencies)
- Orases must build temporary workarounds or stub data across 3 sprints
- When profile is built later, scheduling needs refactoring across all 3 sprints of work
- **Extra work created by re-prioritization**, but within "approved scope"

### Scenario 3: Architecture Rework Mid-Development
**Work Packages 1-2 (6 weeks):** Build features assuming API integration pattern A
**Week 7 (during Work Package 3):** Duke says "deprioritize remaining API features, build offline-first features instead"

**Impact:**
- Architecture decisions made for API-first approach may not suit offline-first
- Work completed in WP1 and WP2 may need refactoring
- Offline features in WP3 may take longer without proper foundation
- **Timeline impact** even though scope hasn't changed
- Potential rework of already-accepted deliverables

### Scenario 4: Budget Burn Without Deliverables Across Multiple Sprints
**Approved Work Package Budget:** $120,000 for 3-sprint feature (480 hours)

**Sprint 1 (Weeks 1-2):** Start Feature A (80 hours invested - foundation work)
**Sprint 2 (Weeks 3-4):** "Stop Feature A, do Feature B instead" (80 hours invested in Feature A, now 80 hours into Feature B)
**Sprint 3 (Weeks 5-6):** "Actually, go back to Feature A" (160 hours in Feature A, 80 hours in Feature B)

**Result:**
- 320 hours spent across 6 weeks
- Neither feature complete
- Client: "We're within work package budget, no change order needed"
- Orases: absorbed thrashing costs across multiple sprints
- No complete deliverable after 3 full sprints

## The Core Issue

The phrase **"remains within the approved scope and budget for the current Sprint/Phase"** is ambiguous when features span multiple sprints:

### What Duke Thinks It Means:
"If we change our mind about which features to build during a work package, as long as the total hours don't increase, it's free"

### What It Actually Costs:
- Abandoned work (sunk costs) - potentially across multiple sprints
- Rework of dependencies that span work packages
- Context switching inefficiency - losing momentum on partially complete features
- Technical debt creation - incomplete foundations
- Timeline delays due to disrupted sequencing across phases
- Lost learning and optimization that occurs during multi-sprint development

---

## RECOMMENDED APPROACH

### Proposed Section 1.2 Language

**1.2. Prioritization of Work**

[...existing intro language...]

**CLIENT Re-prioritization Rights:**

CLIENT may re-prioritize the Backlog to align with evolving business needs. The process and impact will depend on the timing and nature of the re-prioritization:

**Between Work Packages (Clean Re-prioritization):**
- CLIENT may reorder, add, or remove features from the backlog that have not yet been started
- Orases will provide written impact analysis within **three (3) business days** addressing timeline, technical dependencies, and any budget implications
- If reprioritized features are of similar size/complexity, have no technical dependencies, and require no architectural changes, no Change Order will be required
- If re-prioritization creates dependency disruption or requires architectural adjustments, Orases will document the impact and Parties will mutually agree on approach

**During Active Development (Mid-Development Re-prioritization):**
- CLIENT may request re-prioritization of work in progress, subject to impact assessment
- For multi-sprint features, reprioritization may occur mid-way through the development cycle
- Orases will provide impact analysis within **two (2) business days** covering:
  - Sunk costs for work in progress (CLIENT remains obligated to pay for hours invested to date)
  - Percentage completion of the current work package
  - Recommended stopping point for in-progress work to minimize technical debt
  - Timeline impact for current and subsequent work packages
  - Additional costs for context switching, rework, or dependency adjustments
- Parties will mutually agree on how to proceed
- CLIENT may choose to: (a) complete in-progress work to logical stopping point (e.g., finish current sprint within multi-sprint feature), (b) immediate halt and accept technical debt, or (c) defer the re-prioritization to the next work package

**Sunk Cost and Rework Policy:**
- All hours invested in work that is subsequently deprioritized will be billed to CLIENT
- For multi-sprint features, sunk costs include foundation work, architecture, infrastructure, and partially completed functionality
- If deprioritization creates rework for related features (due to dependencies, architecture changes, or incomplete infrastructure), the additional effort will be documented in the impact analysis
- Rework costs that exceed **40 hours or $10,000** (cumulative per development phase) will require mutual agreement or Change Order per Section 06

**Change Order Threshold:**

Re-prioritization will not require a Change Order if:
1. It occurs between work packages (not during active development), AND
2. No material dependencies are disrupted, AND
3. No significant rework or architectural changes are required, AND
4. Overall approved scope and timeline targets (per Section 04) are not materially affected

If any of these conditions are not met, Orases' impact analysis will form the basis for discussion and potential Change Order.

**Approval Process:**
- No work under Section 1.3 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant Work Package
- Each Work Package may span multiple sprints (typically 1-3 sprints depending on feature complexity)
- Orases will maintain a shared backlog with periodic status reports showing progress and budget burn at both work package and sprint levels
- In case a not-to-exceed (NTE) sum is determined for any Deliverable, Orases will not exceed the approved NTE without CLIENT's prior written approval
- Silence or inaction by CLIENT does not constitute approval

---

## FALLBACK OPTION: If Duke Pushes Back Hard

If Duke insists on broad re-prioritization rights without Change Orders, propose a **"Re-prioritization Budget Reserve"**:

### Proposed Compromise Language:

> "CLIENT may re-prioritize at any time. Orases will accommodate re-prioritization requests to the extent possible within the approved work package budget.
>
> To account for potential costs associated with re-prioritization (context switching, sunk costs, dependency rework), the Parties agree to allocate **[5-10%]** of each work package budget as a Re-prioritization Reserve. This reserve may be used for:
> - Completing in-progress work to logical stopping points when deprioritized
> - Addressing technical debt or rework caused by re-prioritization
> - Context switching and efficiency loss, particularly for multi-sprint features
> - Maintaining architectural coherence when features are deprioritized mid-development
>
> If re-prioritization costs exceed the allocated reserve, Orases will provide written notice and impact analysis. Additional costs beyond the reserve will require mutual agreement or Change Order."

**Why This Works:**
- Gives Duke the flexibility they want
- Provides Orases a buffer (5-10% = $3K-$6K per $60K work package) for real costs
- Makes costs visible and manageable
- Particularly important for multi-sprint features where mid-development changes have larger impact
- Avoids disputes over what's "within scope"

**Example:** For a 3-sprint scheduling feature ($60K budget), a 10% reserve = $6K to cover reprioritization impacts

---

## Bottom Line

**The current language is too risky for Orases.** You need protection for:
1. Sunk costs on deprioritized work (especially critical for multi-sprint features)
2. Rework caused by dependency disruption across work packages
3. Timeline impacts from out-of-sequence development
4. Context switching inefficiency and lost momentum on partially-complete features

**Recommended Strategy:**
1. **First Position:** Push for the Recommended Approach (Clean vs. Disruptive reprioritization with clear sunk cost and rework policies)
2. **Fallback Position:** If Duke resists, propose the 5-10% Re-prioritization Budget Reserve (higher percentage for longer work packages)
3. **Bottom Line:** Never accept language where mid-development reprioritization is "free" with no compensation for sunk costs, especially on multi-sprint features

The risk is amplified when features span multiple sprints - reprioritization mid-way through a 3-sprint feature can result in $30K+ of sunk costs with no deliverable.
