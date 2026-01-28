# Development Backlog Clarification - Proposal to Duke Energy

## Email Draft to Duke Energy

**Subject:** SOW #1 Clarification - Development Backlog Deliverable (Section 1.1)

---

Hi [Duke Contact Name],

Thank you for the feedback on SOW #1. We're reviewing the additions to the Deliverables Outcomes in Section 1.1, specifically:
- Feature Roadmap with expected timelines
- Development Backlog with refined requirements

We want to ensure we're aligned on expectations for the **"Development Backlog with refined requirements"** deliverable, as this can mean different things in different contexts and has significant implications for the Analysis phase scope and cost.

### Two Possible Interpretations:

**Option A: Strategic Feature Backlog (Recommended)**
- Prioritized list of all features/epics with high-level functional requirements
- Feature roadmap showing target delivery phases (e.g., "Payment Integration - Phase 1 Q2 2026")
- Dependencies, integration points, and technical constraints identified
- Business requirements and acceptance criteria for each feature area
- Sufficient detail to estimate effort and prioritize work
- **Detailed user stories created iteratively** as we approach each development phase (typically 1-2 work packages ahead, recognizing some features may span multiple sprints/phases)

**Option B: Comprehensive Development-Ready Backlog**
- Detailed user stories with acceptance criteria for the *entire project scope*
- Story point estimates for all features
- Task-level breakdowns ready for immediate development
- Full backlog created upfront during Analysis phase

### Our Recommendation: Option A

We recommend **Option A** for the following reasons:

1. **Aligns with the SOW's iterative approach**
   - Section 1.2 emphasizes ongoing prioritization and your ability to re-prioritize at any time, including mid-way through larger deliverables
   - Section 1.1 mentions "continuous refinement of scope, timeline, and cost estimates"
   - Creating detailed stories for 18+ months of work contradicts this flexibility

2. **Addresses technical unknowns**
   - Per Section 03, significant technical unknowns remain (API availability, integration complexity, security requirements)
   - Detailed user stories written before API validation may require significant rework
   - Better to detail stories *after* we validate technical feasibility

3. **Cost efficiency**
   - Creating a comprehensive development-ready backlog for the entire project = estimated 150-250 additional hours in Analysis phase (~$37,500-$62,500)
   - If priorities shift per Section 1.2 (even mid-way through a multi-sprint deliverable), detailed stories for deprioritized features represent wasted investment
   - Iterative backlog refinement allows us to focus Analysis hours on high-priority items

4. **Accommodates multi-phase deliverables**
   - Some features naturally span multiple sprints or development cycles (e.g., complex integrations may take 6-8 weeks across 3 sprint cycles)
   - Iterative refinement allows us to adjust scope and approach as we progress through multi-phase work
   - If reprioritization occurs mid-way through a larger deliverable, we can complete logical stopping points without wasting analysis effort on abandoned work

5. **Industry best practice**
   - Agile methodology recommends "just-in-time" backlog refinement (typically detailing work 1-2 work packages ahead)
   - Maintains flexibility while preventing analysis paralysis
   - Allows requirements to evolve based on stakeholder feedback and technical discoveries

### What You'll Get with Option A:

**During Analysis Activities (Section 1.1):**
- **Feature Roadmap**: All features mapped to delivery phases with target timelines, including multi-sprint/phase deliverables
- **Functional Requirements Document**: Business requirements, acceptance criteria, and success metrics for each feature area
- **Prioritized Feature Backlog**: Epic-level features with relative sizing (T-shirt sizes or story point ranges)
- **Initial Work Package Backlog**: Detailed user stories for the first 4-8 weeks of development work

**Throughout Development (Section 1.3):**
- **Ongoing Backlog Refinement**: User stories detailed 1-2 work packages ahead of development (acknowledging some features may span multiple work packages)
- **Sprint/Phase Planning**: Collaborative sessions where we review and refine upcoming stories
- **Backlog Updates**: Continuous updates based on your prioritization decisions (Section 1.2), including adjustments for multi-phase deliverables if reprioritization occurs mid-way
- **Progress Tracking**: Visibility into work in progress, including status of longer-duration deliverables

### Alternative: If You Prefer Option B

If Duke Energy requires a comprehensive development-ready backlog for the entire project scope upfront, we can accommodate this, but we'll need to:

1. **Adjust Analysis phase estimates**: Add 150-250 hours for comprehensive backlog creation
2. **Extend Analysis timeline**: Additional 3-4 weeks for backlog development and review
3. **Establish change management process**: Process for updating the backlog when priorities shift (including mid-way through multi-phase deliverables) or technical discoveries require changes
4. **Define refresh cadence**: How often do we revisit and update the detailed backlog as realities emerge?
5. **Handle work in progress**: Process for managing reprioritization that occurs mid-way through larger deliverables

### Recommended SOW Language Change

To clarify this in the SOW, we propose revising the "Deliverables Outcomes" section to:

**Current:**
- Development Backlog with refined requirements

**Proposed Revision:**
- **Development Backlog**: Prioritized feature backlog with functional requirements for all features, including identification of multi-sprint/phase deliverables. Detailed user stories will be created for initial work packages (4-8 weeks) and refined iteratively throughout development, typically 1-2 work packages ahead of implementation, in collaboration with CLIENT stakeholders. This iterative approach allows for adjustments to multi-phase deliverables if reprioritization occurs mid-way through development.

### Next Steps

Could you please confirm which approach aligns with your expectations?

- [ ] **Option A (Recommended)**: Strategic feature backlog + iterative story refinement
- [ ] **Option B**: Comprehensive development-ready backlog for entire project (with scope/budget adjustment)
- [ ] **Option C**: Alternative approach - please describe

We're happy to schedule a brief call to discuss this if helpful.

Best regards,
[Your Name]
Orases

---

## Key Discussion Points if They Want a Call

### 1. Example Comparison

**Feature: Home Service Scheduling (Multi-Sprint Deliverable - 8 weeks)**

**Option A Deliverable (Analysis Phase):**
```
Epic: Home Service Scheduling
- User can view available appointment slots
- User can select preferred date/time
- User receives confirmation notification
- User can reschedule/cancel appointments
- Integration with Dynamics for contractor availability
- Real-time status updates during service window
- Estimated Size: X-Large (21-34 story points)
- Target: Phase 1, Q2 2026
- Duration: 6-8 weeks (spans 3-4 sprint cycles)
- Dependencies: API integration with Dynamics CRM
- Deliverable Structure:
  - Work Package 1 (Weeks 1-2): View/Select appointments
  - Work Package 2 (Weeks 3-4): Booking confirmation & integration
  - Work Package 3 (Weeks 5-6): Reschedule/Cancel functionality
  - Work Package 4 (Weeks 7-8): Real-time status updates
```

**Option B Deliverable (Analysis Phase):**
```
User Story 1: View Available Appointment Slots
As a homeowner
I want to view available appointment slots for my service request
So that I can choose a convenient time

Acceptance Criteria:
- System displays available slots for next 14 days
- Slots shown in 2-hour windows (8-10am, 10-12pm, etc.)
- Unavailable dates are grayed out
- System filters by contractor availability in my ZIP code
- Mobile responsive view

Technical Notes:
- API endpoint: /api/v1/appointments/availability
- Requires: customerID, serviceType, zipCode
- Response time: <2 seconds
- Cache availability data for 15 minutes

Story Points: 5
Dependencies: [STORY-123, STORY-124]
```

...multiply this by 200+ user stories covering 8 weeks of work

### 2. Risk Discussion - Multi-Phase Deliverable Scenario

**With Option B (Comprehensive Upfront Backlog):**
- **Scenario**: You're 4 weeks into an 8-week Home Scheduling feature
- **Mid-way discovery**: Duke's Dynamics API doesn't support real-time availability queries
- **Impact**: 15-20 user stories for weeks 5-8 need complete rewrite
- **Cost**: Already paid for detailed stories that must be redone
- **Additional risk**: If Duke reprioritizes mid-way (per Section 1.2), you've paid for detailed stories for work that may never be completed

**With Option A (Iterative Refinement):**
- **Scenario**: Same 8-week feature, same API discovery at week 4
- **Impact**: Adjust high-level approach before detailing weeks 5-8 stories
- **Cost**: Minimal rework, pivot before investing in detailed stories for remaining work packages
- **Reprioritization flexibility**: If Duke reprioritizes at week 4, only weeks 1-4 have detailed stories; no wasted analysis on abandoned future work

### 3. Multi-Phase Work & Reprioritization Example

**Scenario: Payment Integration Feature (Spans 3 Sprint Cycles - 6 weeks)**

**Week 1-2 (Work Package 1):** Basic credit card processing
- Detailed stories created before work begins
- Development completed

**Week 3-4 (Work Package 2):** ACH/Bank account payments
- Stories detailed at end of Week 1-2
- **MID-WAY REPRIORITIZATION**: Duke decides to deprioritize ACH and prioritize Apple Pay/Google Pay instead
- **With Option A**: Only 2 weeks of detailed stories exist; pivot is straightforward
- **With Option B**: All 6 weeks detailed upfront; ACH stories wasted, new Apple/Google Pay stories needed

**Week 5-6 (Work Package 3):** Now Apple Pay/Google Pay integration
- Stories detailed at end of Week 3-4 based on new priority
- Development proceeds with current priorities

### 4. Value Proposition

"We want to invest your Analysis budget in:
- ✅ Validating technical feasibility
- ✅ Designing solid architecture
- ✅ Creating detailed stories for immediate work (next 4-8 weeks)
- ✅ Identifying which features span multiple work packages
- ❌ NOT in writing detailed stories for features 6-12 months out that may change
- ❌ NOT in detailing week 5-6 of work when week 3-4 might reveal the need to pivot"

---

## Questions to Anticipate from Duke

### Q: "How will we know what we're getting if you don't detail everything upfront?"

**A:** "You'll have:
- Complete feature list with functional requirements
- Roadmap showing when each feature will be built, including multi-sprint/phase deliverables
- Effort estimates for each feature (epic sizing)
- Breakdown of which features span multiple work packages
- Detailed stories for upcoming work (next 4-8 weeks)

The difference is *timing* - we detail stories just before building them, when we have the most information, rather than guessing details 6-12 months in advance. For larger features spanning multiple sprints, we detail each work package as we approach it, allowing us to adjust based on learnings from earlier work packages."

### Q: "What happens if we need to reprioritize mid-way through a large feature?"

**A:** "This is exactly why iterative refinement is beneficial:
- We detail work 1-2 work packages ahead
- If you reprioritize during a multi-phase feature, we complete the current work package to a logical stopping point
- Only the immediate work package has detailed stories, so minimal analysis effort is wasted
- We can pivot to the new priority without throwing away weeks of detailed planning
- Section 1.2 already allows reprioritization; our approach makes it less costly when you exercise that right"

### Q: "We need to budget and plan our UAT resources. How can we do that without a detailed backlog?"

**A:** "The Feature Roadmap and epic-level estimates provide what you need for:
- Budget planning (we'll have effort ranges for all features)
- UAT planning (you'll know which features release when, including multi-phase deliverables)
- Resource planning (you'll see the phases and duration for larger features)

We'll provide detailed UAT test cases as we detail each user story or work package, aligned with your UAT schedule. For multi-sprint deliverables, you'll see UAT test cases emerge incrementally as each work package is detailed."

### Q: "Our internal stakeholders need to see the full scope to approve the project."

**A:** "Completely understandable. The Functional Requirements Document will show:
- Every feature you're getting
- What each feature does (business requirements)
- How success will be measured
- When it will be delivered
- Which features span multiple work packages/phases

This is typically MORE useful for stakeholder approval than user stories, which are developer-focused. We can also create a visual prototype (already included in deliverables) to make it tangible."

### Q: "We've had vendors under-deliver because they didn't commit to specific scope upfront."

**A:** "That's a valid concern. Here's how we address it:
- Section 1.4 defines clear acceptance criteria
- All features in the roadmap are committed scope
- You have written approval authority before we build anything (Section 1.2)
- The only difference is we don't detail stories for all work packages until we validate they're technically feasible
- For multi-phase deliverables, completing earlier work packages validates the approach for later work packages

You have MORE control this way because you can see progress and re-prioritize based on actual working software, not just paper commitments. If a 6-week feature isn't delivering value at week 3, you can pivot rather than being locked into a plan created months ago."

---

## Internal Orases Discussion Notes

### If Duke Insists on Option B

**Negotiate these terms:**

1. **Additional Budget**: 150-250 hours for comprehensive backlog creation
2. **Backlog Refresh Process**: Define how/when backlog updates happen when priorities shift, including mid-way through multi-phase deliverables
3. **Change Order Threshold**: Clarify that backlog changes due to technical discoveries or mid-course adjustments don't automatically trigger change orders
4. **Acceptance Criteria**: Backlog is accepted based on completeness, not accuracy of future predictions
5. **Timeline Buffer**: Add 3-4 weeks to Analysis phase
6. **Work-in-Progress Policy**: Define how reprioritization mid-way through multi-sprint deliverables affects billing and deliverables

**Risks to Document:**
- Backlog will require significant updates as technical realities emerge, especially for multi-phase deliverables
- CLIENT re-prioritization (allowed in Section 1.2), including mid-way through larger features, will create backlog maintenance overhead
- Detailed stories may become stale/irrelevant before implementation
- Detailed planning for weeks 5-6 of a 6-week feature may be wasted if technical discoveries in weeks 1-2 require approach changes

### Compromise Option

**Phased Detailed Backlog:**
- Full comprehensive backlog for MVP Phase (target 9/30/2026), broken into work packages
- Identify which MVP features span multiple work packages (with high-level breakdown)
- Epic-level for Phase 1 beyond MVP
- Detail Phase 1 stories during MVP development
- For multi-sprint MVP deliverables, detail first work package fully, subsequent work packages at high level until we approach them

This gives Duke the comfort of seeing MVP scope fully mapped while maintaining flexibility for:
- Mid-course adjustments within multi-phase deliverables
- Later phases
- Reprioritization decisions based on actual MVP delivery experience
