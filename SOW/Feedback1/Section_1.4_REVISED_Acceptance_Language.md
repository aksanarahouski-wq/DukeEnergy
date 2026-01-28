# Section 1.4 - REVISED Acceptance Language Options

## OPTION 1: Balanced Agile-Friendly Approach (RECOMMENDED)

This option addresses all major concerns while remaining reasonable for Duke.

---

### 1.4 Review Period, Acceptance

Deliverables or Milestones established or outcomes received during the activities described in sections 1.1 and 1.3 shall be reviewed and either accepted or rejected in accordance with the following procedure:

**Review and Acceptance Process:**

CLIENT shall have **fifteen (15) business days** after delivery of applicable Deliverables (the "Review Period") to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection of applicable Deliverables in writing. For clarity, written acceptance includes e-mail confirmations between designated project managers.

**Acceptance Standards:**

Deliverables will be evaluated based on whether they substantially conform to the requirements specified in the Development Backlog and refined Project Scope as agreed at the time development began. "Substantial conformance" means:
- Core functionality operates as specified
- Deliverable achieves the stated business objective
- Any defects present are minor (as defined below) or can be remediated within the remediation period
- The deliverable is usable for its intended purpose in a production environment

**Defect Classification:**

For purposes of acceptance, defects are classified as:

**Material Defects** (may block acceptance):
- Core functionality does not work as specified
- Critical security vulnerabilities
- Performance failures that make the deliverable unusable
- Data integrity or loss issues
- Complete absence of specified functionality
- Defects that prevent the deliverable from achieving its primary business objective

**Minor Defects** (do not block acceptance):
- Cosmetic or UI issues that don't affect functionality
- Edge cases not explicitly addressed in requirements
- Non-critical performance issues
- Issues affecting optional or secondary features
- Documentation gaps or typos
- Issues that have reasonable workarounds

Minor defects will not prevent acceptance. They will be documented in a punch list and addressed in subsequent sprints as mutually agreed by the Parties.

**Handling Emerging Requirements:**

The Parties acknowledge that in iterative software development, some requirements emerge during implementation as edge cases, integration details, and user experience considerations become apparent. When Orases encounters scenarios not explicitly addressed in the agreed requirements, Orases will:
1. Flag the issue to CLIENT's Product Owner
2. Propose a reasonable approach consistent with industry best practices
3. Proceed with CLIENT's guidance or, if CLIENT is unavailable, use professional judgment

Decisions made in good faith to address unspecified scenarios will not be grounds for rejection, though CLIENT may request modifications which will be treated as enhancements and added to the backlog for future sprints.

**Rejection and Remediation:**

If CLIENT determines that any Services or Deliverables contain **Material Defects** that prevent substantial conformance with requirements, CLIENT shall provide written notice of such deficiencies within the Review Period, including:
- Specific description of each material defect
- Reference to the requirement that is not met
- Impact on functionality or business objective
- Evidence or steps to reproduce the issue

Upon receiving notice of rejection, Orases shall have **fifteen (15) Business Days** to either:
- Remediate the material defects and re-deliver, OR
- If material defects are due to ambiguous requirements, technical constraints discovered during integration, or other factors beyond Orases' control, provide a written proposal outlining: (a) root cause analysis, (b) proposed solution with effort estimate, (c) timeline for resolution, (d) any budget implications

If remediation is provided, CLIENT shall have **ten (10) Business Days** to review and either accept or provide detailed feedback on remaining issues.

**Acceptance or Payment Trigger:**

Deliverables will be considered accepted upon the earlier of:
1. CLIENT's written acceptance, OR
2. **Twenty (20) business days** after Orases notifies CLIENT that the deliverable is ready for review, if CLIENT has not provided written rejection with specific material defects identified

This provision ensures project momentum and allows Orases to invoice for completed work. If CLIENT requires additional review time beyond 20 business days, CLIENT shall provide written notice before expiration and Parties will mutually agree on an extension. During such mutually agreed extension, the above acceptance trigger will be suspended.

**Extensions:**

If additional time is needed by either Party beyond the stated timelines, written notification shall be provided to the other Party prior to expiration of the applicable period. Extensions must be mutually agreed upon by the Parties and will be confirmed in writing.

**Acceptance Criteria for Deliverables and Milestones:**

Deliverables shall be expected to meet the following criteria:
- **Substantially conforms** to requirements specified in Development Backlog and refined Project Scope as agreed at commencement of development
- Free of **material defects** in functionality, code quality, and design quality (minor defects do not prevent acceptance)
- Meets security and compliance requirements established by Duke cybersecurity team, as applicable
- Meets performance expectations as defined in the requirements, tested on current-generation devices and browsers as specified
- Passes applicable testing (unit, integration, UAT) with no critical defects
- Documented in architecture, configuration, environment, or other artifacts as specified in the requirements

**Collaborative Resolution:**

Before formal rejection, CLIENT agrees to engage with Orases to discuss any concerns and explore remediation approaches. This collaborative discussion does not extend the Review Period but promotes efficient resolution. The Parties commit to good faith problem-solving when issues arise.

**Disputes:**

If the Parties disagree on whether a defect is material or whether a deliverable substantially conforms to requirements, the issue will be escalated to the Principal Representatives identified in Section 10 for resolution. Pending resolution, work will continue on other agreed priorities to maintain project momentum.

---

## OPTION 2: Softer Language, Keeps Some Duke Protections

This option is closer to Duke's language but softens the harsh elements.

---

### 1.4 Review Period, Acceptance

Deliverables or Milestones established or outcomes received during the activities described in sections 1.1 and 1.3 shall be reviewed and either accepted or rejected in accordance with the following procedure:

**Review Period:**

CLIENT shall have **fifteen (15) business days** after delivery of the applicable Deliverables (the "Review Period") to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection of applicable Deliverables in writing. For clarity, written acceptance includes e-mail confirmations between designated project managers.

**Acceptance or Rejection:**

If CLIENT determines that any Services or Deliverables **do not substantially conform** to the requirements of this SOW due to **material defects or omissions**, CLIENT shall provide written notice of such discrepancies within the Review Period, including specific details of the issues and the requirements they violate.

**Material vs. Minor Issues:**

- **Material issues:** Defects affecting core functionality, security, data integrity, or that prevent the deliverable from achieving its primary business purpose
- **Minor issues:** Cosmetic issues, edge cases, non-critical performance, secondary features, documentation gaps

Minor issues will not block acceptance and will be addressed via punch list in subsequent development cycles.

**Remediation Process:**

If Orases delivers a Deliverable that CLIENT determines contains material defects, Orases shall have **fifteen (15) Business Days** upon receipt of detailed rejection notice to:
1. **Remediate** the identified material defects and re-deliver, OR
2. **Provide a remediation plan** if the issues require more than 15 days or involve requirements ambiguity, including effort estimate, timeline, and any cost implications

Re-delivery will occur within the timeframe specified in the remediation plan, as mutually agreed by the Parties. CLIENT shall have **ten (10) Business Days** to review re-delivered work and provide acceptance or additional feedback.

**Invoicing and Payment:**

Orases may invoice for accepted deliverables. If CLIENT does not provide written acceptance or rejection within the Review Period, Orases will send a reminder notice. If CLIENT does not respond within **five (5) additional business days** after the reminder, the deliverable will be deemed accepted for invoicing purposes, though CLIENT retains the right to request remediation of material defects discovered during subsequent integration or production use.

**Mutual Extensions:**

If additional time is needed by either Party, written notification shall be provided to the other Party prior to expiration. Extensions require mutual written agreement between the Parties.

**Acceptance Criteria:**

Deliverables shall be expected to substantially meet the following criteria:
- Conforms to requirements specified in Development Backlog and refined Project Scope
- Free of material defects in functionality, code quality, and design quality
- Meets security and compliance requirements established by Duke, as applicable
- Meets defined performance expectations, as applicable
- Passes applicable unit, integration, and UAT tests without critical defects
- Documented as specified in the requirements

**Emerging Requirements:**

For iterative development, the Parties acknowledge that some details emerge during implementation. When requirements are ambiguous or scenarios arise that were not explicitly specified, Orases will seek CLIENT guidance. Reasonable approaches taken in good faith will constitute substantial conformance, though CLIENT may request adjustments to be handled in subsequent sprints.

---

## OPTION 3: Most Agile-Friendly (Strongest Orases Protection)

This option fully embraces agile principles with sprint-based acceptance.

---

### 1.4 Review Period, Acceptance

Given the iterative and agile nature of this project, acceptance will occur on two levels: **Sprint-Level Acceptance** for incremental deliverables and **Milestone Acceptance** for major phases.

**Sprint-Level Acceptance (For Iterative Development):**

At the end of each sprint, Orases will demonstrate completed work to CLIENT in a Sprint Review session.

- **Sprint Demo:** CLIENT will attend Sprint Reviews where Orases demonstrates working software
- **Provisional Acceptance:** Work demonstrated in Sprint Reviews that CLIENT does not raise material concerns about is provisionally accepted
- **Feedback Integration:** Feedback from Sprint Reviews is incorporated in subsequent sprints
- **Invoicing:** Orases may invoice for sprint work based on hours invested, regardless of provisional acceptance status, per the time-and-materials terms in Section 05

**Milestone Acceptance (For Major Deliverables):**

For major milestones (e.g., MVP completion, Phase 1 completion, Analysis Phase deliverables):

CLIENT shall have **fifteen (15) business days** to review and test the milestone deliverable (the "Review Period"). CLIENT will indicate acceptance or rejection in writing.

**Acceptance Standards:**

Milestone deliverables will be accepted if they:
- Substantially conform to the agreed scope and functional requirements
- Are free of **Critical Defects** (defined below)
- Achieve the primary business objectives of the milestone
- Are suitable for production use or for the next project phase

**Defect Severity Levels:**

- **Critical:** Core functionality broken, security vulnerabilities, data loss, system unusable → Blocks milestone acceptance
- **Major:** Important features don't work as expected, significant performance issues → May block acceptance depending on impact
- **Minor:** Secondary features, edge cases, cosmetic issues, non-critical bugs → Do not block acceptance; addressed in backlog

**Rejection and Remediation:**

If CLIENT rejects a milestone deliverable due to Critical or Major defects, CLIENT shall provide written notice detailing:
- Specific defects and their severity
- Steps to reproduce
- Requirements not met
- Business impact

Orases will assess the rejection notice and within **five (5) Business Days** provide a response indicating:
- Agreement with assessment and remediation timeline, OR
- Alternative analysis (e.g., issue is not a defect but a new requirement, technical constraint, or ambiguity in original requirements) with proposed path forward

Parties will collaboratively agree on remediation approach, timeline, and any budget implications.

**Acceptance Trigger:**

Milestone deliverables will be considered accepted upon the earlier of:
1. CLIENT's written acceptance, OR
2. CLIENT's use of the deliverable in production, OR
3. **Thirty (30) calendar days** after delivery without written rejection identifying Critical defects

This ensures project momentum while protecting CLIENT's ability to reject deliverables with serious issues.

**Handling Ambiguity:**

When requirements are ambiguous or scenarios arise that were not specified:
- Orases will document assumptions and approach
- CLIENT will be notified and given opportunity to provide guidance
- Reasonable industry-standard approaches taken in good faith constitute conformance
- Adjustments can be made in subsequent sprints if CLIENT prefers different approach

**Acceptance Criteria:**

- Substantially meets functional requirements as defined at start of development
- Free of Critical defects; Major defects either resolved or waived by CLIENT
- Achieves stated business objectives
- Suitable for intended use (production, next phase, etc.)
- Meets specified security, compliance, and performance standards
- Documented as required

---

## OPTION 4: Compromise - Payment vs. Acceptance Split

This creative option separates payment rights from acceptance rights.

---

### 1.4 Review Period, Acceptance, and Payment

**Review and Acceptance Process:**

CLIENT shall have **fifteen (15) business days** after delivery of applicable Deliverables (the "Review Period") to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection in writing (including email between project managers).

**Two-Track Process:**

**Track 1: Payment for Work Performed**
- Orases may invoice for hours invested in deliverable development per the time-and-materials terms in Section 05
- CLIENT pays for work performed regardless of acceptance status
- This ensures Orases is compensated for work done in good faith

**Track 2: Acceptance for Production Use**
- CLIENT accepts deliverables for production use only when they meet acceptance criteria
- Acceptance is not required for payment but is required for production deployment
- This ensures CLIENT doesn't deploy incomplete work

**Acceptance Standards:**

Deliverables meet acceptance criteria when they:
- Substantially conform to requirements specified in Development Backlog
- Are free of **Critical** and **High-severity** defects
- Medium and Low defects do not block acceptance; they are added to backlog
- Achieve core business objectives
- Are suitable for production use

**Defect Classification:**

| Severity | Definition | Blocks Acceptance? |
|----------|------------|-------------------|
| **Critical** | System unusable, data loss, security breach, core feature completely broken | YES |
| **High** | Important functionality doesn't work, significant performance issues | YES (unless CLIENT waives) |
| **Medium** | Secondary features don't work, moderate issues with workarounds | NO - Goes to backlog |
| **Low** | Minor bugs, cosmetic issues, edge cases, documentation gaps | NO - Goes to backlog |

**Rejection and Remediation:**

If CLIENT determines a deliverable contains Critical or High defects, CLIENT shall provide written notice within the Review Period, including:
- Defect descriptions and severity assessments
- Steps to reproduce
- Requirements not met

Orases will respond within **three (3) Business Days** with either:
- Agreement and remediation plan with timeline, OR
- Alternative assessment if Orases believes issues are not defects (e.g., new requirements, ambiguous specs, technical constraints)

Parties will collaboratively resolve the path forward. Remediation of actual defects is covered by the original sprint/phase budget. Enhancements or new requirements require separate approval per Section 1.2.

**When Acceptance Occurs:**

Deliverables are accepted upon the earlier of:
1. CLIENT's written acceptance
2. CLIENT's deployment to production (implies acceptance)
3. **Twenty (20) business days** after delivery if no written rejection with identified Critical/High defects

If CLIENT needs more than 20 days for review, CLIENT shall request extension in writing before expiration. Mutually agreed extensions suspend the acceptance trigger.

**Emerging Requirements During Development:**

The Parties acknowledge that in agile development, some details emerge during implementation:
- Unspecified edge cases
- Integration details not apparent until APIs are connected
- UX details not captured in written requirements
- Performance tuning needed for production conditions

When Orases encounters such scenarios, Orases will:
- Make reasonable decisions consistent with industry best practices
- Document approach and rationale
- Notify CLIENT Product Owner for material decisions

Such decisions made in good faith constitute substantial conformance. CLIENT may request different approaches, which will be treated as enhancements for subsequent sprints.

**Acceptance Criteria:**

- Substantially conforms to requirements as defined at start of development
- Free of Critical defects; High defects resolved or waived
- Core functionality works as specified
- Meets security, compliance, and performance requirements
- Suitable for production deployment
- Documented as required

**Key Principle:**

This approach separates "did Orases do the work?" (payment) from "is it ready for production?" (acceptance). Orases is paid for good-faith effort regardless of acceptance status, while CLIENT retains quality standards for production deployment.

---

## COMPARISON TABLE

| Element | Duke's Original | Option 1 (Balanced) | Option 2 (Softer Duke) | Option 3 (Agile) | Option 4 (Split) |
|---------|----------------|---------------------|----------------------|------------------|------------------|
| **Deemed acceptance** | PROHIBITED | 20 days | 5 days after reminder | 30 days | 20 days |
| **Defect classification** | Not defined | Material vs. Minor | Material vs. Minor | Critical/Major/Minor | Critical/High/Medium/Low |
| **Minor defects block?** | Unclear (yes?) | NO | NO | NO | NO |
| **Emerging requirements** | Not addressed | Covered | Covered | Covered | Covered |
| **Payment trigger** | After acceptance | After acceptance or 20 days | After acceptance or reminder+5 | Sprint invoicing | Regardless of acceptance |
| **Agile-friendly?** | NO | YES | SOMEWHAT | VERY | YES |
| **Orases protection** | LOW | GOOD | FAIR | VERY GOOD | VERY GOOD |
| **Duke control** | ABSOLUTE | BALANCED | HIGH | MODERATE | HIGH (for production) |

---

## RECOMMENDED APPROACH

### Step 1: Lead with Option 1 (Balanced)
- Addresses all major issues
- Fair to both parties
- Clear processes
- Softer than Duke's language but protects both sides

### Step 2: Have Option 4 (Split Payment/Acceptance) as Alternative
- Creative approach Duke might appreciate
- They keep quality control (acceptance for production)
- Orases gets paid regardless (time and materials anyway)
- Solves the cash flow problem

### Step 3: Fall back to Option 2 if Necessary
- Closer to Duke's language
- Minimum viable changes
- Still addresses key issues

### Step 4: Use Option 3 if Duke is Open to True Agile
- Best for iterative development
- Sprint-based acceptance
- Only if Duke embraces agile fully

---

## INTERNAL SUMMARY FOR ALIGNMENT

**Four Critical Issues with Duke's Current Language:**
1. **No payment certainty** - "Deemed acceptance prohibited" creates indefinite limbo for invoicing
2. **No defect classification** - Typos can block entire milestones (no material vs. minor distinction)
3. **80% scope problem** - No process for handling emerging requirements during agile development
4. **Waterfall acceptance** - Conflicts with iterative/agile approach described throughout SOW

**Recommended Strategy:**

**Primary Position: Option 1 (Balanced Agile-Friendly)**
- Addresses all four issues while remaining reasonable for Duke
- 20-day deemed acceptance with extension option
- Material vs. Minor defect classification (only material blocks acceptance)
- Explicit "Handling Emerging Requirements" process
- Maintains Duke's quality control while protecting Orases cash flow

**Alternative Position: Option 4 (Payment/Acceptance Split)**
- Creative compromise: separate payment from production acceptance
- Payment track: Invoice for T&M hours worked regardless of acceptance
- Acceptance track: Duke controls production deployment based on quality standards
- Critical/High/Medium/Low severity framework
- Most protective for Orases while giving Duke maximum control

**Fallback Positions:**
- Option 2: Softer version closer to Duke's language (minimum viable changes)
- Option 3: True agile with sprint-based acceptance (only if Duke fully embraces agile)

**Key Talking Points:**
- Appointment scheduling race condition example (edge case not in requirements)
- Payment vs. acceptance split aligns with T&M pricing model Duke chose
- Material vs. minor defects prevents project delays over cosmetic issues
- Emerging requirements are inevitable in agile - need collaborative process

**Non-Negotiables:**
- Some form of payment certainty (deemed acceptance OR payment/acceptance split)
- Defect classification (material vs. minor at minimum)
- Process for handling ambiguous/unspecified scenarios
- Language that supports agile methodology, not waterfall

**Bottom Line:**
Duke's current Section 1.4 language creates unacceptable risk for Orases in a T&M agile engagement. Option 1 or Option 4 must be implemented to protect both parties and align with how modern software development actually works.
