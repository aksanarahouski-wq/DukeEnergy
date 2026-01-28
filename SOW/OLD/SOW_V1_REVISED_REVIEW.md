# SOW V1 - Revised Assessment: T&M with Appropriate Guardrails

**Date**: January 7, 2026
**Context**: Discovery completed WITHOUT Duke's tech team involvement; significant unknowns remain; Round 2 discovery needed with correct stakeholders; Detailed requirements discovery still required

---

## Executive Summary

Given the context that **discovery was conducted without Duke's technical team** and **significant unknowns remain**, the **Time & Materials approach is APPROPRIATE and PROTECTIVE for Orases**. However, the current SOW needs strategic additions to provide budget transparency, scope management, and risk mitigation while maintaining the flexibility required for this project.

### Updated Risk Assessment: **MEDIUM RISK (with recommended modifications)**

The T&M approach is correct for this situation. The SOW needs refinements to:
- ✅ Reference existing discovery as "current understanding subject to validation"
- ✅ Provide budget estimate for planning (not commitment)
- ✅ Add transparency mechanisms for scope and cost tracking
- ✅ Establish communication protocols for significant variances
- ✅ Protect both parties during technical validation phase

---

## Why T&M Is Appropriate Here

### 1. **Discovery Limitations Context**

**Reality**: Discovery was completed without Duke's tech team
- APIs may not exist as assumed
- Integration complexity unknown
- Technical constraints not yet validated
- Feasibility of certain features uncertain
- Security requirements may be more stringent than anticipated

**Risk of Fixed Price**: Orases would bear 100% of risk for unknowns
- If APIs don't exist → $177,750 bridge investment could balloon
- If security requirements more complex → DevOps costs could double
- If integration constraints discovered → rework could exceed budget
- Fixed price would require massive contingency (30-50%) making bid uncompetitive

**T&M Benefit**: Shares discovery risk appropriately
- Duke pays for actual effort as scope becomes clear
- Orases protected from catastrophic losses on unknowns
- Both parties incentivized to make good decisions as facts emerge
- Flexibility to pivot based on Round 2 discovery findings

### 2. **Round 2 Discovery Needed**

**What's Still Unknown**:
- Duke Enterprise API availability and capabilities (Service Request Creation, Enrollment)
- FSM tool selection timeline and integration requirements
- Actual contractor data structure in CRM systems
- Commerce vs Dynamics integration complexity
- Duke IT security requirements and approval processes
- Production deployment constraints
- Duke's internal approval cycles and decision-making processes

**T&M Enables**:
- Proper discovery with Duke's tech team before committing to detailed scope
- Flexibility to adjust approach based on technical validation
- Ability to address blockers as they're discovered
- Avoid premature commitments that create conflict later

### 3. **Business Case for T&M**

**For Orases**:
- Protects against catastrophic loss from unknowns
- Enables iterative refinement of scope based on facts
- Avoids need for massive contingency buffer (30-50%)
- Allows charging for actual effort rather than worst-case estimates

**For Duke**:
- Pays for actual work, not inflated contingency
- Flexibility to adjust priorities as scope becomes clear
- Avoid paying fixed price for features that become unnecessary
- Shared learning reduces overall project cost

---

## Current SOW Strengths

### ✅ **What's Working Well**

1. **Flexible Analysis Phase (Section 1.1)**
   - Acknowledges that scope may evolve during analysis
   - Lists comprehensive discovery activities
   - Includes validation sessions with stakeholders
   - Allows for technical feasibility assessments

2. **Prioritization Gate (Section 1.2)**
   - Requires CLIENT approval before development begins
   - Includes timeline and cost estimates for transparency
   - Allows CLIENT to make informed go/no-go decision
   - Protects both parties from premature commitment

3. **Good Faith Collaboration (Section 4)**
   - "Both Orases and CLIENT agree to work in good faith to make decisions and functionality choices that balance the spirit of the requirements and the overall budget"
   - This is excellent language for T&M projects
   - Establishes partnership mindset, not adversarial

4. **Change Management (Section 5)**
   - Clear process for handling scope changes
   - Three options: swap features, defer to Phase 2, or approve additional budget
   - Protects both parties from scope creep

5. **Team Flexibility (Section 4)**
   - Allows CLIENT to request changes to team size/hours with 30 days notice
   - Orases notifies if not feasible
   - Reasonable accommodation process

---

## Recommended Modifications

### Strategic Additions for T&M Success

The following modifications support T&M while adding necessary guardrails for transparency and trust:

---

### **MODIFICATION #1: Reference Discovery as Baseline (Not Commitment)**

**Section 1.1 - Add After Line 19**:

```markdown
1.1 Analysis Activities

Prior to executing this SOW, Orases conducted preliminary discovery activities with
Duke Energy business stakeholders, resulting in two reference documents:
- "Discovery Findings and Updated Project Scope" dated December 2025
- "Duke Energy Residential Solution Scope" dated December 2025

These documents (collectively, "Initial Discovery") represent Orases' current
understanding of project requirements based on business stakeholder input. However,
CLIENT acknowledges that Initial Discovery was completed WITHOUT Duke Energy's
technical team participation, and significant technical unknowns remain.

During Analysis Activities under this SOW, Orases will:
- Conduct Round 2 discovery with Duke's technical team (IT, Security, Integration)
- Validate feasibility of features identified in Initial Discovery
- Identify technical constraints, blockers, and dependencies
- Assess API availability and integration complexity
- Refine scope, timeline, and cost estimates based on technical validation
- Document findings and provide updated recommendations to CLIENT

CLIENT understands that Round 2 discovery may reveal:
- APIs assumed to exist may not be available (requiring alternative approaches)
- Integration complexity may exceed initial estimates
- Security requirements may require additional effort
- Certain features may be technically infeasible or cost-prohibitive
- Timeline and cost estimates may increase or decrease based on findings

Initial Discovery serves as a starting point for collaboration, not a binding
commitment of scope, timeline, or budget.
```

**Why This Helps**:
- ✅ Establishes Initial Discovery as reference, not contract
- ✅ Sets expectation that Round 2 discovery will refine scope
- ✅ Protects Orases from "you promised X" disputes later
- ✅ Transparent about unknowns and risks
- ✅ Duke understands scope may change based on technical validation

---

### **MODIFICATION #2: Budget Estimate with Flexibility**

**Section 4 - Add After Line 71 (before line about "regular statements")**:

```markdown
04 Payment Schedule and Cost

[Existing rate language...]

**Planning Budget Estimate**

Based on Initial Discovery (conducted without Duke's technical team), Orases
estimates the total project cost to be approximately **$788,600**, allocated as follows:

| Component | Estimated Amount | Percentage |
|-----------|------------------|------------|
| CX Interface Development | $285,225 | 36.1% |
| Backend Development | $332,083 | 42.0% |
| DevOps & Security | $171,292 | 21.7% |
| **Total Estimated** | **$788,600** | **100%** |

**Important Notes Regarding Budget Estimate**:

1. **This is a planning estimate, not a cap or commitment.** Actual costs will be
   based on time and materials at the rate specified above ($250/hour).

2. **Estimate is subject to refinement** after Round 2 discovery with Duke's
   technical team. Scope, timeline, and cost may increase or decrease based on:
   - API availability and capabilities (Service Request Creation, Enrollment)
   - Integration complexity with Duke's Commerce and Dynamics CRM systems
   - Security requirements and compliance obligations
   - Technical feasibility of features identified in Initial Discovery
   - Duke IT approval processes and deployment constraints

3. **Orases will provide updated estimates** after completing Analysis Activities
   (Section 1.1) and before beginning Design, Development, and Implementation
   (Section 1.3). Updated estimates will be provided as part of the prioritization
   process in Section 1.2.

4. **Transparency and Communication**: Orases will provide regular statements and
   updates regarding the fees incurred on the actual time spent for functionality
   delivered and the anticipated cost of functionality to be delivered based on the
   confidence level of scope at the time. [Existing language continues...]

5. **Variance Notification**: If at any point during the project Orases anticipates
   that total costs will exceed the planning estimate by more than 15% ($118,290),
   Orases will notify CLIENT in writing within 5 business days of such determination,
   providing:
   - Explanation of drivers for variance (scope changes, technical complexity, etc.)
   - Updated cost forecast with confidence level
   - Recommendations for cost mitigation (if applicable)
   - Options for CLIENT consideration (continue, adjust scope, pause for review)

6. **CLIENT retains full control**: CLIENT may at any time request a pause in work
   to review progress, costs, and priorities. Upon such request, Orases will provide
   a comprehensive status report within 5 business days.
```

**Why This Helps**:
- ✅ Provides Duke with budget planning number ($788,600)
- ✅ Clearly states this is an estimate, not a cap
- ✅ Establishes 15% variance threshold for proactive notification
- ✅ Demonstrates transparency and good faith
- ✅ Duke retains control (can pause at any time)
- ✅ Protects Orases from "you estimated X" disputes
- ✅ Shows partnership approach, not adversarial

---

### **MODIFICATION #3: High-Level Scope Reference (Not Detailed Commitment)**

**Add New Section 1.5 - Phase 1 Anticipated Components**:

```markdown
1.5 Phase 1 Anticipated Components

Based on Initial Discovery, Phase 1 is anticipated to include the following
high-level components, subject to technical validation during Analysis Activities:

**Customer-Facing Applications**:
- Mobile applications (iOS and Android)
- Responsive web application (PWA)
- User registration and authentication
- Home Protection Plan (HPP) management
- Home inventory and profile building
- Service booking (HPP-covered and ad-hoc services)
- Maintenance reminders and notifications
- Communication preferences and notification center
- Service history and records
- Loyalty/gamification features

**Admin Portal**:
- Multi-role user management (anticipated 7 roles, subject to validation)
- Customer profile management
- Service request management and processing
- Contractor configuration and matching algorithm
- Ad-hoc service catalog management
- Analytics and reporting dashboard
- Communication and notification management

**Backend Infrastructure**:
- RESTful API architecture
- Database design and implementation
- Integration with Duke Enterprise APIs (customer validation, HPP plans)
- Contractor matching algorithm (trade + zip code)
- Multi-channel notification system (push, SMS, email)
- Authentication and authorization (role-based access control)

**DevOps and Security**:
- Cloud infrastructure setup (AWS or equivalent)
- CI/CD pipeline
- Security compliance (SOC 2 Type 2 OR ISO 27001)
- Monitoring and logging
- Multi-environment deployment (dev, staging, production)

**Phase 1 Anticipated Limitations** (subject to validation with Duke's tech team):
- Manual admin workflows for service request processing (no FSM integration)
- Contractors collect payment on-site (no in-app payment processing)
- Basic status updates (5 statuses, no real-time GPS tracking)
- Emergency services phone-only (not bookable in-app)
- No changes to existing contractor portal
- Limited ad-hoc service catalog (5-10 services, 1-2 pilot markets)
- Ratings collected via external survey (not displayed in-app)
- No contractor marketplace (primary contractor auto-assigned)

**Technical Dependencies** (to be validated during Analysis):
- Duke Enterprise API availability (Customer Validation, HPP Plans, Service Request
  Creation, Enrollment)
- Commerce CRM and Dynamics CRM integration capabilities
- Duke IT security requirements and approval processes
- Contractor data structure and export capabilities
- Production deployment constraints

CLIENT acknowledges that:
1. This is an anticipated scope based on business requirements, not technical validation
2. Round 2 discovery with Duke's technical team may reveal features that are:
   - Not technically feasible
   - More complex than anticipated
   - Dependent on systems/APIs that don't exist
   - Cost-prohibitive given business value
3. Final scope will be determined through Analysis Activities (Section 1.1) and
   Prioritization (Section 1.2) with CLIENT approval required before development begins
4. Out-of-scope items requiring Phase 2 or separate SOW: FSM tool integration,
   in-app payment processing, contractor mobile app, real-time GPS tracking,
   in-app ratings display, contractor marketplace, AI virtual assistant
```

**Why This Helps**:
- ✅ Provides Duke with understanding of anticipated deliverables
- ✅ References detailed Initial Discovery without making it binding
- ✅ Clearly states this is "anticipated" pending technical validation
- ✅ Lists limitations explicitly so Duke has realistic expectations
- ✅ Acknowledges dependencies and unknowns
- ✅ Protects Orases from scope disputes later
- ✅ Duke understands what's NOT included (Phase 2 items)

---

### **MODIFICATION #4: Communication and Transparency Protocols**

**Add New Section 09 - Project Governance and Transparency**:

```markdown
09 Project Governance and Transparency

To ensure effective collaboration and mutual understanding throughout this
time-and-materials engagement, the parties agree to the following governance protocols:

**9.1 Sprint-Based Progress Tracking**

- Work will be organized in 2-week sprints
- Each sprint will have defined objectives agreed upon by both parties
- Sprint demos will be conducted bi-weekly with CLIENT stakeholders
- Sprint retrospectives will identify lessons learned and process improvements

**9.2 Budget and Progress Reporting**

Orases will provide CLIENT with:

1. **Bi-Weekly Status Reports** including:
   - Hours worked by role/activity for the sprint
   - Cumulative hours and costs to date
   - Progress against current phase objectives
   - Risks, issues, and blockers
   - Upcoming sprint objectives

2. **Monthly Financial Reports** including:
   - Total costs incurred month-to-date and project-to-date
   - Comparison to planning budget estimate ($788,600)
   - Forecast of costs to complete remaining anticipated scope
   - Confidence level of forecast (low/medium/high)
   - Explanation of any significant variances

3. **Milestone Reviews** at key decision points:
   - End of Analysis Activities (Section 1.1): Scope, timeline, cost recommendations
   - 25% budget consumed: Progress review and forecast validation
   - 50% budget consumed: Comprehensive mid-project review
   - 75% budget consumed: Final scope validation and completion forecast

**9.3 Variance Management**

If Orases determines that:
- Total costs will exceed planning estimate by >15% ($118,290), OR
- Timeline will extend beyond anticipated duration by >4 weeks, OR
- Significant technical blockers require scope changes

Orases will notify CLIENT in writing within 5 business days, providing:
- Root cause analysis of variance
- Impact assessment (scope, timeline, budget)
- Recommended corrective actions or alternatives
- Request for CLIENT direction

CLIENT will respond within 10 business days with direction to:
- Continue as planned (accept variance)
- Adjust scope to stay within budget
- Pause for comprehensive review
- Terminate engagement per Section 7 (Term)

**9.4 CLIENT Review Rights**

CLIENT may at any time:
- Request detailed timesheets for any billing period
- Request comprehensive project status review meeting
- Request pause in work (no more than 2 weeks) to assess progress and costs
- Request independent review of deliverables, code quality, or technical approach

Upon such request, Orases will cooperate fully and provide requested documentation
within 5 business days.

**9.5 Decision Log**

Both parties will maintain a shared decision log documenting:
- Major scope decisions and rationale
- Trade-off discussions and selected approach
- Technical constraints discovered
- Budget/timeline impact of decisions
- Approvals and sign-offs

Decision log will be reviewed at each milestone review to ensure alignment.

**9.6 Escalation Path**

For issues requiring executive attention:
- Either party may escalate to executive sponsors
- Escalation triggers: budget variance >20%, timeline slip >6 weeks, technical
  feasibility concerns, scope disagreements
- Executive sponsors will meet within 5 business days to resolve
```

**Why This Helps**:
- ✅ Establishes clear communication cadence (bi-weekly, monthly, milestones)
- ✅ 15% variance threshold provides early warning system
- ✅ CLIENT has visibility and control throughout project
- ✅ Decision log prevents "he said/she said" disputes
- ✅ Demonstrates good faith partnership approach
- ✅ Protects both parties through transparency
- ✅ Duke sees Orases is committed to proactive communication

---

### **MODIFICATION #5: Remove "Analysis Only" Exit Clause**

**Section 1.2 - Modify Line 24**:

❌ **REMOVE**:
> "CLIENT is under no obligation to prioritize or authorize any subsequent work for
> Section 1.3 and may choose to limit the Project to the Analysis Activities only,
> in its sole discretion."

✅ **REPLACE WITH**:
> "Following completion of Analysis Activities (Section 1.1), Orases will provide
> CLIENT with a comprehensive recommendation including:
> - Refined scope based on technical validation with Duke's team
> - Detailed timeline with milestones
> - Updated cost forecast with confidence level
> - Risks, dependencies, and mitigation strategies
> - Recommended approach for Phase 1 implementation
>
> CLIENT will review Orases' recommendation and may choose to:
> (a) Approve proposed scope, timeline, and budget to proceed with Section 1.3
> (b) Request modifications to scope, timeline, or budget
> (c) Pause engagement to assess findings and options
>
> If CLIENT chooses not to proceed with Section 1.3 after receiving Orases'
> recommendations, CLIENT will pay for all Analysis Activities performed through
> the date of such decision at the rates specified in Section 4. This SOW
> contemplates that both parties intend to proceed with Phase 1 implementation
> (Section 1.3) following successful completion of Analysis Activities, subject
> to mutual agreement on scope, timeline, and budget."

**Why This Helps**:
- ✅ Removes language that allows Duke to use discovery and walk away
- ✅ Establishes expectation that both parties intend to continue
- ✅ Still allows Duke flexibility to request changes or pause
- ✅ Clarifies that Analysis is not "free discovery for competitors"
- ✅ Protects Orases investment in discovery work
- ✅ Maintains partnership tone, not adversarial

---

### **MODIFICATION #6: Acceptance Process for T&M**

**Section 1.4 - Expand Deliverable Acceptance**:

```markdown
1.4 Deliverable Acceptance

Given the time-and-materials nature of this engagement, deliverable acceptance
will occur incrementally throughout the project rather than at final delivery.

**Sprint-Level Acceptance**:
- At the conclusion of each 2-week sprint, Orases will demonstrate completed work
- CLIENT will have 5 business days to review sprint deliverables
- CLIENT will provide feedback and acceptance or rejection with specific defects noted
- Orases will address defects in subsequent sprint(s) at no additional cost if defects
  are due to Orases error or non-conformance with agreed specifications

**Phase-Level Acceptance**:
- Major project phases (Analysis, Design, Development, Testing, Deployment) will
  have formal acceptance milestones
- CLIENT will have 15 business days to review and accept phase deliverables
- If CLIENT rejects phase deliverable, CLIENT will provide written rejection notice
  specifying defects or non-conformance
- Orases will address defects and re-submit for acceptance

**Final Acceptance and Warranty Period**:
- Final acceptance occurs upon successful production deployment
- Warranty period begins upon final acceptance and extends for 90 days
- During warranty period, Orases will fix defects in workmanship at no additional cost
- Warranty coverage subject to Section II.D (Acceptance) of the Agreement

**What CLIENT is Accepting**:
CLIENT acknowledges that in a time-and-materials engagement with evolving scope:
- Sprint acceptance means work completed conforms to specifications agreed for that sprint
- Phase acceptance means deliverables meet acceptance criteria defined for that phase
- Final acceptance means system is ready for production use with anticipated features
  (subject to any limitations documented during Analysis Activities)

**What Constitutes a Defect**:
- Functionality does not perform as specified in agreed sprint objectives
- System does not meet security, performance, or availability requirements documented
  in acceptance criteria
- Code quality does not meet professional standards (e.g., OWASP Top 10 vulnerabilities)

**What Does NOT Constitute a Defect**:
- Features not included in agreed sprint objectives or phase scope
- Changes to CLIENT requirements after sprint/phase acceptance
- Issues caused by third-party systems or APIs outside Orases control
- Performance issues caused by CLIENT infrastructure or configuration
```

**Why This Helps**:
- ✅ Establishes incremental acceptance process appropriate for Agile/T&M
- ✅ Clarifies what CLIENT is accepting at each stage
- ✅ Defines "defect" vs "new requirement"
- ✅ Protects Orases from unlimited rework for scope changes
- ✅ Aligns with Master Agreement's 90-day inspection period
- ✅ Still provides Duke with quality assurance

---

### **MODIFICATION #7: Timeline with Flexibility**

**Section 3 - Expand Estimated Timeline**:

```markdown
03 Estimated Timeline

Based on Initial Discovery (conducted without Duke's technical team), Orases
anticipates the project duration to be approximately **44 weeks (11 months)** from
the Effective Date, subject to refinement after Analysis Activities.

**Anticipated Timeline** (subject to change based on Round 2 discovery findings):

| Phase | Weeks | Key Activities | Dependencies |
|-------|-------|----------------|--------------|
| **Analysis Activities** | 1-12 | Round 2 discovery with Duke's tech team, requirements validation, technical feasibility, architecture design, UI/UX wireframes, cost/timeline refinement | Duke tech team availability, API documentation, CRM access |
| **Design Approval** | 12-16 | UI/UX design finalization, technical specs approval, CLIENT review and approval | CLIENT 2-week review cycle |
| **Development** | 16-32 | Iterative development in 2-week sprints, customer app, admin portal, backend APIs, contractor matching | Duke API availability, sprint approvals |
| **Testing & QA** | 28-36 | UAT, security testing, performance testing, penetration testing, bug fixes | Duke UAT participation, test environments |
| **Deployment** | 36-40 | Production setup, app store submissions, go-live preparation, admin training | Duke IT approvals, app store reviews |
| **Warranty** | 40-44+ | Post-launch support, bug fixes, stabilization | Production access |

**Key Milestones** (anticipated, subject to refinement):
- **Week 12**: Analysis Activities complete, updated scope/timeline/budget provided
- **Week 16**: Design approval, development kickoff
- **Week 24**: Alpha release (functional testing)
- **Week 28**: Beta release (UAT)
- **Week 32**: Security testing complete
- **Week 36**: App store approvals
- **Week 40**: Production launch
- **Week 44+**: Warranty period (90 days from launch)

**Timeline Dependencies and Risks**:

The timeline assumes:
1. Duke tech team available for Round 2 discovery (10-15 hours/week, Weeks 1-8)
2. Duke Enterprise APIs available by Week 12 (Customer Validation, HPP Plans)
3. API documentation and sandbox access provided by Week 2
4. Contractor data export provided by Week 4
5. CLIENT design approval within 2 weeks (Week 16)
6. CLIENT UAT participation during Testing phase (Weeks 28-36)
7. Duke IT security and production approvals (Weeks 32-36)
8. No major scope changes after Week 16 (design lock)

**Timeline may extend if**:
- Round 2 discovery reveals significantly higher complexity than anticipated
- Duke APIs not available, requiring alternative implementation approaches
- Integration complexity with Commerce/Dynamics exceeds estimates
- Security requirements require additional development effort
- CLIENT review/approval cycles exceed 2 weeks
- Production deployment constraints require additional work

**Timeline Updates**:
- Orases will provide updated timeline forecast at each milestone review
- If timeline extends beyond 44 weeks + 4 weeks (48 weeks total), Orases will
  notify CLIENT per Section 9.3 (Variance Management) and provide revised forecast
- CLIENT may request schedule acceleration (subject to feasibility and additional cost)

**Milestones for deliverables will be agreed to throughout the project and reported
on a pre-agreed cadence per Section 9.2 (Budget and Progress Reporting).**
```

**Why This Helps**:
- ✅ Provides Duke with planning timeline (44 weeks)
- ✅ Clearly states timeline is subject to validation
- ✅ Lists dependencies and risks that could extend timeline
- ✅ Establishes 48-week threshold for proactive notification
- ✅ Demonstrates realistic planning, not overpromising
- ✅ Protects Orases from "you promised 44 weeks" disputes

---

## What's Intentionally NOT Changed

These elements should remain as-is in the SOW:

### ✅ **Keep T&M Rate Structure** (Section 4)
- $250/hour blended rate is reasonable
- Monthly invoicing is standard
- Rate revision with 90 days notice (max once/year) is fair
- No changes needed here

### ✅ **Keep Team Flexibility** (Section 4, lines 72-73)
- CLIENT can request team size changes with 30 days notice
- Orases responds within 15 days if not feasible
- This is good balance of flexibility and stability

### ✅ **Keep Change Order Process** (Section 5)
- Three options (swap, defer, approve) are clear and fair
- Protects both parties from scope creep
- No changes needed

### ✅ **Keep Travel Section** (Section 6)
- 1 trip estimated, actual costs reimbursed
- Travel time billed at hourly rate
- Standard and fair

### ✅ **Keep Term Through Dec 31, 2026** (Section 7)
- Provides 12 months from Effective Date (Jan 5, 2026)
- Can be extended by mutual agreement (email suffices)
- Reasonable given unknowns

### ✅ **Keep Communications Section** (Section 8)
- Standard contact information and authority
- Recording disclosure is fine
- No changes needed

---

## Comparison: Before and After Modifications

### **BEFORE**: What Made SOW "High Risk"

❌ **No Discovery Reference**: Zero mention of $788,600 discovery work
❌ **No Budget Guidance**: Unlimited T&M with no planning number
❌ **"Analysis Only" Exit**: Duke could walk away after discovery
❌ **No Scope Clarity**: Vague "design, development, testing" language
❌ **No Transparency Mechanisms**: Monthly invoicing only

### **AFTER**: T&M with Appropriate Guardrails

✅ **Discovery Referenced**: Initial Discovery as "current understanding, subject to validation"
✅ **Budget Estimate Provided**: $788,600 planning estimate with 15% variance threshold
✅ **Partnership Language**: "Both parties intend to proceed" after Analysis
✅ **High-Level Scope**: Anticipated components listed (not binding, subject to validation)
✅ **Transparency Protocols**: Bi-weekly reports, monthly financials, milestone reviews, variance notification
✅ **Incremental Acceptance**: Sprint-level and phase-level acceptance for Agile/T&M
✅ **Timeline with Flexibility**: 44-week estimate with dependencies and risks documented

---

## Why This Approach Works

### **For Orases (Protective)**:

✅ **Risk Protection**:
- Not locked into fixed price with massive unknowns
- Can charge for actual effort as scope becomes clear
- Protected from catastrophic losses if complexity exceeds estimates
- 15% variance threshold provides early warning before major overruns

✅ **Flexibility**:
- Can adjust approach based on Round 2 discovery findings
- Can pivot if APIs don't exist or integration more complex than expected
- Can recommend scope adjustments based on technical realities
- Not forced to deliver features that become cost-prohibitive

✅ **Fair Compensation**:
- Paid for actual work, not worst-case contingency estimates
- Overhead recovery through blended rate ($250/hour)
- Travel time compensated (not unpaid)
- Discovery work valued and compensated

### **For Duke (Transparent & Controlled)**:

✅ **Budget Planning**:
- Has planning estimate ($788,600) for internal approval and budgeting
- Understands estimate may change based on technical validation
- 15% variance threshold provides predictability
- Monthly financial reports provide ongoing visibility

✅ **Control and Oversight**:
- Can pause at any time to review progress and costs
- Milestone reviews at 25%, 50%, 75% budget consumed
- Bi-weekly sprint demos show tangible progress
- Can request detailed timesheets or independent review

✅ **Scope Flexibility**:
- Can adjust priorities based on business needs
- Can descope features that become cost-prohibitive
- Can add features that become critical
- Not locked into rigid fixed-price scope

✅ **Risk Mitigation**:
- Shares discovery risk with Orases
- Pays for actual effort, not inflated contingency
- Round 2 discovery validates feasibility before major commitment
- Incremental acceptance catches issues early (not 90-day bomb at end)

---

## Recommended Next Steps

### **1. Update SOW with Modifications**

Incorporate the 7 modifications above:
1. ✅ Section 1.1: Add discovery reference and Round 2 discovery description
2. ✅ Section 4: Add budget estimate with flexibility and variance notification
3. ✅ Section 1.5 (NEW): Add high-level anticipated scope
4. ✅ Section 9 (NEW): Add project governance and transparency protocols
5. ✅ Section 1.2: Remove "analysis only" exit, replace with partnership language
6. ✅ Section 1.4: Expand acceptance process for incremental/T&M approach
7. ✅ Section 3: Expand timeline with dependencies and flexibility

### **2. Add Exhibit A: Initial Discovery Reference**

Create Exhibit A attached to SOW:
- Include links or copies of two discovery documents
- State: "Exhibit A provides reference materials representing Orases' understanding of business requirements as of December 2025, prior to technical validation with Duke's team."

### **3. Legal Review with T&M Context**

Have Orases legal counsel review modified SOW with context:
- Emphasis: This is T&M with unknowns, not fixed price
- Key protections: Budget estimate is not cap, variance notification at 15%, Duke can pause/review
- Partnership language: Both parties intend to proceed after Analysis
- Acceptance process: Incremental, not 90-day bomb

### **4. Prep for Negotiation**

**Duke may push back on**:
- "We want a cap" → Response: "Given unknowns from limited discovery, cap would require 40-50% contingency. Better to do Round 2 discovery, then discuss cap for implementation phase."
- "We want deliverables list" → Response: "Section 1.5 provides anticipated components. Final deliverables determined after Analysis Activities with your approval (Section 1.2)."
- "We want milestones" → Response: "Section 3 provides anticipated milestones. We'll refine after Round 2 discovery and track via bi-weekly reports (Section 9)."

**Orases should be willing to**:
- Lower variance threshold from 15% to 10% if Duke wants tighter control
- Add more frequent financial reporting (weekly vs bi-weekly) if Duke wants more visibility
- Add executive review at 50% budget consumed for mid-project assessment
- Clarify that Duke can request pause at any time (already in Section 9.4)

### **5. Presentation to Duke**

Create 1-page summary for Duke explaining:
- **Why T&M**: Discovery without tech team means unknowns; fixed price would require massive contingency
- **Budget Estimate**: $788,600 based on current understanding; may increase/decrease after Round 2 discovery
- **Transparency**: Bi-weekly reports, monthly financials, 15% variance notification
- **Control**: Duke can pause anytime, adjust scope, milestone reviews at 25%/50%/75%
- **Partnership**: Both parties committed to good faith collaboration and cost-effective decisions

---

## Final Assessment: Medium Risk with Strong Upside

### **Risk Level**: ⚠️ **MEDIUM RISK** (improved from EXTREMELY HIGH)

With the 7 modifications above, this SOW becomes:
- ✅ Appropriate for a T&M engagement with significant unknowns
- ✅ Transparent about budget, scope, and timeline
- ✅ Protective of both parties through clear communication protocols
- ✅ Flexible enough to accommodate Round 2 discovery findings
- ✅ Controlled through variance thresholds and milestone reviews

### **Remaining Risks** (Inherent to T&M with Unknowns)

⚠️ **Medium Risks**:
1. **Scope Creep**: Even with good controls, scope can expand if Duke requests features during sprints
   - **Mitigation**: Change Order process (Section 5), decision log (Section 9.5), sprint-locked objectives
2. **Timeline Extension**: If Round 2 discovery reveals major complexity, timeline could extend significantly
   - **Mitigation**: 48-week threshold for notification (Section 3), milestone reviews, CLIENT can pause
3. **Budget Overrun Beyond 15%**: If APIs don't exist or integration extremely complex, could exceed variance threshold multiple times
   - **Mitigation**: Monthly financials, variance notifications, CLIENT approval required for major changes
4. **Duke Pauses/Terminates Mid-Project**: Duke could pause after 50% budget consumed, leaving Orases with partial engagement
   - **Mitigation**: Partnership language (Section 1.2), good faith clause (Section 4), but this risk cannot be eliminated in T&M

⚠️ **Low Risks** (Well Mitigated):
- ❇️ Duke claims "you promised $788K": Mitigated by "planning estimate" language and variance notification
- ❇️ Duke disputes scope: Mitigated by anticipated scope (Section 1.5) and decision log (Section 9.5)
- ❇️ Duke rejects at end: Mitigated by incremental acceptance (Section 1.4) and bi-weekly demos
- ❇️ Surprises in monthly invoices: Mitigated by bi-weekly status reports and monthly financials (Section 9.2)

### **Success Factors**

For this SOW to succeed:
1. **Trust and Communication**: Both parties must embrace partnership mindset, not adversarial
2. **Proactive Transparency**: Orases must provide bi-weekly reports and monthly financials religiously
3. **Early Issue Escalation**: Don't wait for 15% variance—flag issues early for collaborative problem-solving
4. **Documented Decisions**: Maintain decision log to prevent "he said/she said" disputes
5. **Round 2 Discovery Thoroughness**: Invest properly in Analysis Activities to reduce unknowns before development starts

---

## Bottom Line: This SOW Can Work

**The T&M approach is RIGHT for this situation.** Discovery without Duke's tech team means:
- ✅ APIs may not exist as assumed → T&M allows pivoting to alternatives
- ✅ Integration complexity unknown → T&M avoids catastrophic fixed-price loss
- ✅ Security requirements may be more stringent → T&M accommodates additional effort
- ✅ Feasibility of features uncertain → T&M allows descoping cost-prohibitive features

**With the 7 modifications above**, this SOW:
- ✅ Provides Duke with budget planning guidance ($788,600)
- ✅ Establishes transparency through regular reporting and variance notifications
- ✅ Protects both parties through milestone reviews and pause/review rights
- ✅ Maintains flexibility to adapt to Round 2 discovery findings
- ✅ Demonstrates good faith partnership approach

**This is a MUCH BETTER approach** than forcing a fixed-price SOW with:
- ❌ 40-50% contingency buffer making bid uncompetitive
- ❌ Orases bearing 100% of discovery risk
- ❌ Rigid scope that becomes wrong after Round 2 discovery
- ❌ Conflict when Orases can't deliver within fixed price

**Recommendation**: Proceed with modified SOW. The T&M approach with appropriate guardrails is the right balance of flexibility and control for this project's current stage.

Good luck! 🚀
