# Section 1.4 - CONCISE Versions (Options 1 & 4)

## OPTION 1: Balanced Approach (CONCISE)

### 1.4 Review Period, Acceptance

**Review Process:**

CLIENT shall have **fifteen (15) business days** after delivery (the "Review Period") to review and test Deliverables. CLIENT will provide written acceptance or rejection (email between project managers constitutes written notice).

**Acceptance Standard:**

Deliverables will be accepted if they **substantially conform** to requirements specified in the Development Backlog and Project Scope, meaning:
- Core functionality operates as specified
- Deliverable achieves its stated business objective
- Any defects are minor or can be remediated
- Deliverable is usable for its intended purpose

**Defect Classification:**

**Material Defects** (may block acceptance):
- Core functionality doesn't work as specified
- Critical security vulnerabilities
- Performance failures making deliverable unusable
- Data integrity issues
- Complete absence of specified functionality

**Minor Defects** (do not block acceptance):
- Cosmetic or UI issues
- Edge cases not specified in requirements
- Non-critical performance issues
- Secondary feature issues
- Documentation gaps

Minor defects will be documented in a punch list and addressed in subsequent sprints.

**Emerging Requirements:**

When Orases encounters scenarios not explicitly addressed in requirements, Orases will flag the issue to CLIENT's Product Owner and propose a reasonable approach. Decisions made in good faith to address unspecified scenarios will not be grounds for rejection, though CLIENT may request modifications in future sprints.

**Rejection Process:**

If CLIENT identifies **Material Defects**, CLIENT shall provide written notice within the Review Period including:
- Specific description of each defect
- Reference to requirement not met
- Steps to reproduce

Orases shall have **fifteen (15) Business Days** to remediate and re-deliver, or if issues stem from ambiguous requirements or technical constraints, provide a written proposal with timeline and budget implications. CLIENT then has **ten (10) Business Days** to review.

**Acceptance Trigger:**

Deliverables are accepted upon the earlier of:
1. CLIENT's written acceptance, OR
2. **Twenty (20) business days** after Orases notifies CLIENT the deliverable is ready for review, if CLIENT has not provided written rejection identifying specific material defects

If CLIENT requires additional review time, CLIENT shall provide written notice before expiration. Mutually agreed extensions suspend the acceptance trigger.

**Acceptance Criteria:**

- Substantially conforms to requirements as agreed at development commencement
- Free of material defects (minor defects acceptable)
- Meets security, compliance, and performance requirements as specified
- Passes applicable testing without critical defects
- Documented as specified

**Collaborative Resolution:**

Before formal rejection, CLIENT agrees to discuss concerns with Orases to explore remediation approaches. This does not extend the Review Period but promotes efficient resolution.

---

## OPTION 4: Payment/Acceptance Split (CONCISE)

### 1.4 Review Period, Acceptance, and Payment

**Two-Track Process:**

This SOW separates payment rights from production acceptance rights:

**Track 1 - Payment for Work Performed:**
- Orases invoices for hours invested per the time-and-materials terms in Section 05
- CLIENT pays for work performed regardless of acceptance status
- Payment is for good-faith effort, not perfection

**Track 2 - Acceptance for Production Use:**
- CLIENT accepts deliverables for production deployment only when they meet acceptance criteria
- Acceptance confirms readiness for production but is not required for payment

**Review Period:**

CLIENT has **fifteen (15) business days** after delivery to review and test Deliverables. CLIENT will provide written acceptance or rejection (email between project managers constitutes written notice).

**Acceptance Standard:**

Deliverables meet acceptance criteria when they:
- Substantially conform to requirements in Development Backlog
- Are free of **Critical** and **High-severity** defects
- Medium and Low defects do not block acceptance (added to backlog)
- Achieve core business objectives
- Are suitable for production use

**Defect Severity Levels:**

| Severity | Definition | Blocks Acceptance? |
|----------|------------|-------------------|
| **Critical** | System unusable, data loss, security breach, core feature broken | YES |
| **High** | Important functionality doesn't work, significant performance issues | YES (unless waived) |
| **Medium** | Secondary features impacted, moderate issues with workarounds | NO - backlog |
| **Low** | Minor bugs, cosmetic issues, edge cases, documentation gaps | NO - backlog |

**Rejection and Remediation:**

If CLIENT identifies Critical or High defects, CLIENT provides written notice within Review Period including defect descriptions, severity, steps to reproduce, and requirements not met.

Orases responds within **three (3) Business Days** with either:
- Agreement and remediation timeline, OR
- Alternative assessment if issues are not defects but new requirements or ambiguous specs

Parties collaboratively agree on path forward. Remediation of actual defects is covered by original sprint/phase budget. New requirements or enhancements require separate approval per Section 1.2.

**Acceptance Occurs When:**

Deliverables are accepted upon the earlier of:
1. CLIENT's written acceptance, OR
2. CLIENT's deployment to production (implies acceptance), OR
3. **Twenty (20) business days** after delivery without written rejection identifying Critical/High defects

If CLIENT needs more than 20 days, CLIENT requests extension in writing before expiration. Mutually agreed extensions suspend the acceptance trigger.

**Emerging Requirements:**

In agile development, some details emerge during implementation (edge cases, integration details, UX refinements, performance tuning). When Orases encounters such scenarios, Orases will:
- Make reasonable decisions consistent with industry best practices
- Document approach and rationale
- Notify CLIENT Product Owner for material decisions

Decisions made in good faith constitute substantial conformance. CLIENT may request different approaches, which are treated as enhancements for subsequent sprints.

**Acceptance Criteria:**

- Substantially conforms to requirements as defined at start of development
- Free of Critical defects; High defects resolved or waived
- Core functionality works as specified
- Meets security, compliance, and performance requirements
- Suitable for production deployment
- Documented as required

**Key Principle:**

Orases is compensated for good-faith effort (payment) while CLIENT retains quality standards for production deployment (acceptance). This aligns with time-and-materials pricing and supports agile iteration.

---

## SIDE-BY-SIDE COMPARISON

| Element | Option 1 (Balanced) | Option 4 (Split) |
|---------|---------------------|------------------|
| **Main Innovation** | Material vs. minor defects | Payment separate from acceptance |
| **Payment trigger** | After acceptance or 20 days | Regardless of acceptance |
| **Duke's control** | Can reject for material defects | Full control over production deployment |
| **Orases protection** | Deemed acceptance after 20 days | Gets paid for all work performed |
| **Defect levels** | Material vs. Minor (2 levels) | Critical/High/Medium/Low (4 levels) |
| **Best for** | Duke wants simplified approach | Duke wants maximum control |
| **Key benefit** | Balances both interests | Eliminates payment/acceptance conflict |
| **Handles 80% scope** | ✅ Via "substantial conformance" | ✅ Via "good faith decisions" |
| **Emerging requirements** | ✅ Covered explicitly | ✅ Covered explicitly |
| **Deemed acceptance** | ✅ After 20 days | ✅ After 20 days (for production use) |

---

## WHICH TO CHOOSE?

### Choose **Option 1** if:
- You want to keep it simple (2 defect levels vs. 4)
- Duke is willing to accept deemed acceptance concept
- You want traditional acceptance approach with improvements
- You prefer fewer changes from typical contracts

### Choose **Option 4** if:
- Duke is resistant to deemed acceptance
- You want to eliminate payment/acceptance conflicts entirely
- Duke wants maximum control (they keep it with this option)
- You want the most innovative/creative solution
- Time-and-materials pricing makes this natural (they're paying for hours anyway)

---

## EMAIL TEMPLATE (CONCISE VERSION)

**Subject:** SOW #1 Section 1.4 - Proposed Revisions for Acceptance Process

Hi [Duke Contact],

We've reviewed the acceptance language in Section 1.4 and would like to propose revisions to better align with agile/iterative development while maintaining your quality standards.

**Three Key Issues with Current Language:**

1. **"Deemed acceptance is prohibited"** - If you don't respond, when can we invoice? We need payment certainty.

2. **No material vs. minor defect distinction** - Should a typo block acceptance of an entire milestone?

3. **"80% scope problem"** - In agile development, edge cases and details emerge during implementation. How do we handle scenarios not explicitly specified in requirements?

**Our Recommendations:**

We've drafted two concise options (attached):

**Option 1 - Balanced Approach:**
- Distinguishes material defects (block acceptance) from minor issues (punch list)
- "Substantial conformance" standard for emerging requirements
- Deemed acceptance after 20 days if no response
- Collaborative resolution process

**Option 4 - Payment/Acceptance Split:** (innovative approach)
- You pay for hours worked (it's time-and-materials anyway)
- You accept for production use only when quality standards are met
- Gives you maximum control while ensuring our cash flow
- Eliminates payment/acceptance conflicts

Both options:
✅ Keep your 15-day review period
✅ Give you strong quality control
✅ Address emerging requirements in agile development
✅ Support iterative approach described in the SOW

**Concrete Example:**

We deliver appointment scheduling. It works as specified but doesn't handle a rare race condition (slot becomes unavailable while user is booking - wasn't in requirements).

- **Current language:** You could reject the entire feature; we have 15 days to fix
- **Our language:** It's a minor defect → goes to punch list, we fix in next sprint; feature is accepted

This keeps the project moving while ensuring quality.

**Next Steps:**

Can we schedule 30 minutes to discuss? We're flexible on specifics (timelines, exact wording) but want to ensure we align on the principles.

Best regards,
[Your Name]

**Attachments:**
- Option 1 - Balanced Approach (1 page)
- Option 4 - Payment/Acceptance Split (1 page)

---

## KEY TALKING POINTS (QUICK REFERENCE)

### If Duke asks: "Why can't we keep our language?"

**"Your language is waterfall-style (all-or-nothing acceptance) but the SOW describes agile development (iterative, continuous discovery). We need acceptance criteria that match the development approach. Otherwise we'll have constant disputes about whether edge cases not specified in requirements constitute 'defects.'"**

### If Duke asks: "What if we need more than 20 days?"

**"No problem! Just let us know before day 20 and we'll extend. The 20-day trigger only prevents indefinite silence where we've delivered working software but can't invoice. As long as we're communicating, we're flexible on timeline."**

### If Duke asks: "Why should minor defects not block acceptance?"

**"If we deliver a $50K milestone and there's a typo in help text, should that really block acceptance and prevent us from invoicing for 6 months of work? Industry standard: material defects block acceptance, minor issues go to a punch list. We're happy to define severity levels together."**

### If Duke asks: "What about the payment split in Option 4?"

**"You're paying time-and-materials anyway, so you're paying for our hours regardless of acceptance. Option 4 just clarifies: you pay for work performed, but you only 'accept for production' when quality standards are met. This way you keep full production control while we have cash flow certainty. It's a win-win."**

---

## SUMMARY

Both options address your concerns:

**The "Too Strict" Problem:**
- ✅ Material vs. minor defect distinction (not all-or-nothing)
- ✅ "Substantial conformance" standard (not perfection)
- ✅ Collaborative resolution (not adversarial)

**The "80% Scope" Problem:**
- ✅ Process for handling unspecified scenarios
- ✅ Good faith decisions covered
- ✅ Emerging requirements explicitly addressed

**The "Deemed Acceptance Prohibited" Problem:**
- ✅ Option 1: Acceptance after 20 days
- ✅ Option 4: Payment separate from acceptance (even better)

**Recommendation:** Lead with **Option 4** - it's the most innovative and gives Duke maximum control while protecting your cash flow.
