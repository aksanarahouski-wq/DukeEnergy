# Section 1.4 Review Period & Acceptance - Risk Analysis & Recommendations

## Duke's Current Language (PROBLEMS HIGHLIGHTED)

> "CLIENT shall have fifteen (15) business days after delivery of the applicable Deliverables (the "Review Period") to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection of applicable Deliverables in writing. For clarity, mutual written acceptance includes e-mail confirmations between designated project managers. If CLIENT determines that any Services or Deliverables do not conform to the requirements of this SOW, Client shall provide written notice of such discrepancies, within the Review Period, in accordance with Section 4. Inspection and Acceptance provisions of the Agreement.
>
> If Orases fails to deliver the Deliverable and Duke Energy Provides notice of rejection to Orases per the terms above, Orases shall have fifteen (15) Business Days upon rejection from Duke Energy to address gaps or provide a proposal for a plan to remediate any Deliverable to Duke Energy. Re-delivery will occur within the agreed timeframe. Duke Energy shall have fifteen (15) Business Days to provide documented Acceptance or rejection.
>
> If additional time is needed by either Party, written notification shall be provided to the receiving Party prior to the conclusion of the response requirements indicated above. In order for extension to be granted, it must be mutually agreed upon by the Parties. **Deemed acceptance is prohibited**"

---

## Critical Issues with Current Language

### Issue #1: "Deemed Acceptance is Prohibited" ⚠️⚠️⚠️

**The Problem:**
- If Duke doesn't respond within 15 days, Orases is in limbo indefinitely
- Orases cannot invoice for completed work until Duke explicitly accepts
- Duke could sit on deliverables for months without formal acceptance
- Creates cash flow nightmare for Orases

**Real-World Scenario:**
- Orases delivers MVP on 9/30/2026
- Duke starts reviewing but gets busy with other priorities
- Day 15 passes, no response
- Day 30, Day 60, Day 90... still no formal acceptance
- Orases: "Can we invoice?" Duke: "We're still reviewing"
- Orases has delivered working software but can't get paid

**Industry Standard:**
Most software contracts say: "If Client doesn't respond within [X] days, deliverable is deemed accepted." This protects the vendor from indefinite limbo.

---

### Issue #2: "Fails to Deliver the Deliverable"

**The Problem:**
- Black-and-white language: either you delivered or you "failed"
- No recognition of degrees (95% complete? Material vs. minor defects?)
- Sounds adversarial, not collaborative

**Better Approach:**
- "If deliverable does not substantially conform to requirements"
- "If deliverable contains material defects"
- Distinguish between blocking issues and minor punch-list items

---

### Issue #3: No Distinction Between Material and Minor Defects

**The Problem:**
Current language treats all defects equally. Examples:

**Material Defect (Should Block Acceptance):**
- Payment processing doesn't work
- Critical security vulnerability
- Core feature completely missing
- App crashes on launch

**Minor Defect (Should NOT Block Acceptance):**
- Button is wrong shade of blue
- Typo in help text
- Minor UI alignment issue
- Edge case handling in a secondary feature

**Risk:**
Duke could reject entire deliverable because of a typo, forcing a 15-day remediation cycle.

**Industry Standard:**
"Minor defects do not prevent acceptance; they're added to the punch list and fixed in the next sprint."

---

### Issue #4: Conflicts with Agile/Iterative Approach

**The SOW says it's agile/iterative:**
- Section 1.1: "continuous discovery," "continuous refinement"
- Section 1.2: "iterative development"
- Section 1.3: "iterative development of features"

**But Section 1.4 imposes waterfall-style acceptance:**
- Must meet "requirements specified in Development Backlog"
- All-or-nothing acceptance
- 15-day formal review cycles

**The Conflict:**
In agile, you:
- Demo working software every sprint
- Get feedback and iterate
- Accept work incrementally
- Fix issues in the next sprint

Waterfall acceptance cycles contradict this approach.

---

### Issue #5: The "80% Scope Problem"

**Your Concern:**
> "Sometimes when scope and functional requirements are written it only defines 80% of the final scope."

**Examples of Emerging Requirements:**

**Written Requirement:**
"User can schedule a service appointment"

**Reality During Development:**
- What if user's preferred slot becomes unavailable while they're booking?
- Should system auto-suggest alternative times?
- What if user's home has multiple properties - which one are they booking for?
- What if contractor cancels - how do we handle rescheduling?
- What about timezone handling for snowbirds with homes in different states?
- Should users get SMS confirmation in addition to email?

**None of these were in the original requirements, but they're necessary for a complete feature.**

**Risk with Current Language:**
Duke could say: "You delivered what was in the requirements, but it's not usable because you didn't handle [X, Y, Z that wasn't specified]."

Or flip side:
Orases could say: "We delivered exactly what was specified, here's your invoice," even though it's clearly incomplete.

Both scenarios create conflict.

---

### Issue #6: Undefined "Requirements Specified in Development Backlog"

**Acceptance Criteria says:**
> "Meets requirements specified in Development Backlog and refined Project Scope"

**But:**
- Section 1.2 allows CLIENT to re-prioritize at any time
- Backlog is described as iterative and evolving
- No process for "locking" requirements before development starts

**Risk:**
- Duke: "This doesn't meet the requirements"
- Orases: "Which requirements? The backlog changed 3 times during this sprint"
- Duke: "The requirements as we understand them now"
- Result: Acceptance dispute

---

### Issue #7: Remediation Timeline is Unrealistic

**Current Language:**
"Orases shall have fifteen (15) Business Days upon rejection from Duke Energy to address gaps or provide a proposal for a plan to remediate any Deliverable"

**Problems:**
- What if "gaps" are due to unclear requirements, not delivery failure?
- What if "gaps" would take 60 hours to fix and we're already over sprint budget?
- "Address gaps OR provide a proposal" - which is it?
- If we provide a proposal and Duke doesn't like it, then what?

**Scenario:**
- Orases delivers appointment scheduling feature
- Duke rejects: "Doesn't handle timezone for snowbirds"
- Orases: "That wasn't in the requirements. Here's a proposal: 40 hours to add timezone handling"
- Duke: "That should have been obvious. Fix it for free within 15 days"
- Now what?

---

## Root Cause: Missing "Definition of Done"

**The real problem:** The SOW doesn't define what "acceptance-ready" means.

**Missing Elements:**
1. **Requirements Baseline:** When are requirements "locked" for a given deliverable?
2. **UAT Process:** How does UAT happen before formal acceptance?
3. **Defect Classification:** What's material vs. minor?
4. **Scope Clarification:** Who decides if something is "in scope" vs. "additional"?
5. **Collaborative Process:** How do we resolve disputes about completeness?

---

## Comparison: Current vs. Industry Standard

| Element | Duke's Language | Industry Standard | Risk to Orases |
|---------|-----------------|-------------------|----------------|
| **Deemed acceptance** | Prohibited | Automatic after [X] days | HIGH - Indefinite limbo |
| **Defect classification** | Not defined | Material vs. Minor | MEDIUM - Trivial issues block acceptance |
| **Remediation** | "Fix it in 15 days" | "Fix material defects; minor go to backlog" | HIGH - Unrealistic for big gaps |
| **Emerging requirements** | Not addressed | "Substantial compliance" standard | HIGH - 80% scope problem |
| **Acceptance trigger** | CLIENT discretion only | Auto-accept or good faith standard | HIGH - CLIENT holds all cards |
| **Dispute resolution** | Not defined | Escalation process | MEDIUM - Could stall project |

---

## Impact on Project Dynamics

### Scenario A: Duke is Collaborative (Best Case)

Even with good faith on both sides, this language creates:
- **Invoicing delays:** Can't invoice until Duke formally accepts
- **Pressure to over-deliver:** Fear of rejection drives gold-plating
- **Risk aversion:** Orases reluctant to make judgment calls on edge cases
- **Documentation burden:** Everything must be over-documented to prove compliance

### Scenario B: Duke is Difficult (Worst Case)

If Duke is adversarial or slow, this language enables:
- **Indefinite non-payment:** "Still reviewing" with no deemed acceptance
- **Moving goalposts:** "Doesn't meet requirements" for things not specified
- **Leverage in disputes:** Hold up acceptance to force scope concessions
- **Cash flow squeeze:** Orases delivers working software but can't collect

---

## The "80% Scope" Problem - How to Navigate

### Strategy 1: "Substantial Compliance" Standard

**Add to acceptance criteria:**
> "Deliverables shall be deemed to meet requirements if they substantially comply with the functional specifications, even if minor details or edge cases not explicitly specified in the requirements are handled differently than CLIENT might have preferred. Substantial compliance means the deliverable achieves the core business objective and is usable for its intended purpose, though minor refinements may be added to the backlog for future sprints."

### Strategy 2: "Definition of Ready" and "Definition of Done"

**Add a new section 1.4A:**
> "Before development begins on any feature, CLIENT and Orases will collaboratively establish:
> - **Definition of Ready:** Requirements are sufficiently detailed for development to begin
> - **Definition of Done:** Criteria for considering the feature complete
> - **Known Unknowns:** Edge cases or details that will be clarified during development
>
> If issues arise during development that were not addressed in the original requirements (edge cases, integration details, UX details), Orases will:
> 1. Flag the issue to CLIENT Product Owner
> 2. Propose a reasonable approach
> 3. Proceed with CLIENT's guidance or, if CLIENT is unavailable, use best judgment
>
> Such decisions made in good faith will not be grounds for rejection if CLIENT later disagrees with the approach, though modifications can be added to the backlog."

### Strategy 3: "Sprint Demo = Provisional Acceptance"

**Add to Section 1.4:**
> "For iterative development deliverables, CLIENT will participate in sprint demos where Orases demonstrates working software. Feedback provided during sprint demos will be incorporated in subsequent sprints. If CLIENT does not raise material concerns during a sprint demo, the demonstrated functionality is provisionally accepted, subject to final integration testing."

### Strategy 4: "Collaborative Completion"

**Add to acceptance criteria:**
> "Both Parties acknowledge that in agile/iterative development, some requirements emerge during implementation as edge cases and integration details become apparent. Orases commits to:
> - Proactively communicate when requirements are ambiguous or incomplete
> - Propose reasonable solutions for unspecified scenarios
> - Seek CLIENT input on material design decisions
>
> CLIENT commits to:
> - Provide timely feedback on questions and proposals
> - Participate in regular sprint demos and reviews
> - Distinguish between defects (didn't meet specified requirements) and enhancements (wasn't specified)
>
> Acceptance will be based on whether deliverables meet specified requirements and resolve unspecified scenarios in a reasonable, commercially acceptable manner."

---

## Real-World Examples - How This Language Would Play Out

### Example 1: Appointment Scheduling

**Requirements in Backlog:**
"User can view available appointment slots and book an appointment"

**What Orases Delivers:**
- User can view slots
- User can book appointment
- Confirmation email sent
- Appointment appears in user's dashboard
- **But:** Doesn't handle the case where a slot becomes unavailable while user is booking (race condition)

**Under Current Language:**
- Duke: "Rejected. Users can book slots that aren't actually available. This doesn't meet requirements."
- Orases: "The requirement didn't specify race condition handling. That's a 20-hour enhancement."
- Duke: "It's not usable without that. Fix it for free within 15 days."
- Result: Dispute

**Under Better Language (Substantial Compliance):**
- Orases: "Here's the core scheduling feature. We discovered a race condition edge case. It's rare but we should fix it. Add to backlog for next sprint?"
- Duke: "Agrees. Accept current delivery, add race condition fix to backlog."
- Result: Progress continues

---

### Example 2: Payment Integration

**Requirements in Backlog:**
"Integrate with SpeedPay for non-native customer payments"

**What Orases Delivers:**
- SpeedPay integration working for credit cards
- Integration testing completed
- **But:** Orases discovers SpeedPay doesn't support ACH for non-native customers (Duke assumed it did, but API doesn't support it)

**Under Current Language:**
- Duke: "Rejected. We need ACH support, not just credit cards."
- Orases: "SpeedPay API doesn't support ACH for non-native customers. We delivered what's possible with the API."
- Duke: "Find a different payment processor or extend SpeedPay to support it."
- Orases: "That's major scope change - different integration, different vendor contracts."
- Result: 15-day remediation period starts, but problem can't be fixed in 15 days with current approach

**Under Better Language (Technical Constraint Handling):**
- Orases: "During integration, we discovered SpeedPay API limitation. Here are options: (1) Credit card only for MVP, add ACH later if SpeedPay adds support, (2) Integrate second payment processor for ACH, (3) Different approach"
- Duke: "Thanks for flagging. Let's do option 1 for now."
- Orases: "Great, we'll document the limitation and accept current delivery."
- Result: Pragmatic resolution

---

### Example 3: Mobile App Performance

**Requirements in Backlog:**
"Mobile app loads within 2 seconds on average device"

**What Orases Delivers:**
- App loads in 1.8 seconds on iPhone 12
- App loads in 2.3 seconds on iPhone 8 (older device)
- App loads in 1.5 seconds on Samsung Galaxy S21

**Under Current Language:**
- Duke: "Rejected. Doesn't meet 2-second requirement on iPhone 8."
- Orases: "What's 'average device'? iPhone 8 is 6 years old. If we optimize for 6-year-old devices, we're compromising modern experience."
- Duke: "The requirement says 2 seconds. Fix it."
- Result: Dispute over ambiguous requirement

**Under Better Language (Collaborative Resolution):**
- Orases: "We're hitting 2 seconds on current-gen devices but not on 6-year-old hardware. What percentage of Duke's users have devices that old?"
- Duke: "<5%"
- Orases: "Recommend we accept current performance and optimize for legacy devices in Phase 2 if analytics show it's needed."
- Duke: "Makes sense. Accepted."
- Result: Data-driven decision

---

## Recommended Solutions

I'll provide multiple options in the next document, but the key principles should be:

1. **Deemed acceptance after reasonable period** (or alternative payment trigger)
2. **Material vs. minor defect distinction**
3. **Substantial compliance standard** for agile work
4. **Process for handling emerging requirements**
5. **Collaborative resolution** before formal rejection
6. **Clear remediation triggers** (only for material defects)

---

## Questions for Duke Energy

Before revising, you may want to ask Duke:

1. **On deemed acceptance:** "If we deliver working software and you don't respond within the review period, when can we invoice? We need some certainty for cash flow planning."

2. **On minor defects:** "Should a typo in help text block acceptance of an entire feature, or should we handle minor issues via punch list?"

3. **On emerging requirements:** "In agile development, edge cases emerge during implementation. How should we handle scenarios that weren't explicitly specified in requirements?"

4. **On remediation:** "The 15-day remediation period assumes the issue is a defect. What if rejection is due to ambiguous requirements or technical constraints discovered during integration? How do we handle those?"

5. **On UAT:** "Should there be a UAT/review process during development (before formal acceptance) to catch issues early?"

---

## Bottom Line

**Current language is too strict for agile development.** It's designed for waterfall (detailed specs upfront, single delivery, accept or reject).

**Your project is iterative.** You need language that supports:
- Incremental delivery
- Emerging requirements
- Collaborative problem-solving
- Reasonable handling of edge cases

**Without changes, you risk:**
- Endless acceptance disputes
- Cash flow problems (can't invoice without acceptance, no deemed acceptance)
- Pressure to over-deliver beyond specified requirements
- Adversarial relationship instead of collaborative partnership

I'll create detailed revised language options in the next document.
