# Section 1.4 Review Period & Acceptance - Recommended Revision

## CURRENT DUKE LANGUAGE (PROBLEMATIC)

> "CLIENT shall have fifteen (15) business days after delivery of the applicable Deliverables (the "Review Period") to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection of applicable Deliverables in writing...
>
> If Orases fails to deliver the Deliverable and Duke Energy Provides notice of rejection to Orases per the terms above, Orases shall have fifteen (15) Business Days upon rejection from Duke Energy to address gaps or provide a proposal for a plan to remediate any Deliverable to Duke Energy. Re-delivery will occur within the agreed timeframe. Duke Energy shall have fifteen (15) Business Days to provide documented Acceptance or rejection.
>
> If additional time is needed by either Party, written notification shall be provided to the receiving Party prior to the conclusion of the response requirements indicated above. In order for extension to be granted, it must be mutually agreed upon by the Parties. **Deemed acceptance is prohibited.**"

---

## ISSUES THIS LANGUAGE CREATES

### Issue #1: No Payment Certainty ⚠️

**The Problem:**
"Deemed acceptance is prohibited" means if Duke doesn't respond, Orases is in indefinite limbo—working software delivered but unable to invoice.

**Real-World Impact:**
- Orases delivers MVP on 9/30/2026 (6 months of work)
- Duke starts reviewing but gets busy with other priorities
- Day 15 passes with no response
- Day 30... Day 60... Day 90... still no formal acceptance
- Orases: "Can we invoice for the MVP?" Duke: "We're still reviewing"
- **Result:** Orases has delivered working software but can't collect payment

**The Risk:** Cash flow crisis. You could have $200K+ of delivered work sitting in "review" with no payment trigger.

---

### Issue #2: No Material vs. Minor Defect Distinction ⚠️

**The Problem:**
Current language treats all defects equally—a typo has the same weight as a security breach.

**Real-World Impact:**
- Orases delivers entire appointment scheduling feature (80 hours, $20K)
- Core functionality works perfectly
- Duke finds a typo in a help text tooltip during UAT
- Under current language: Duke can reject the entire deliverable
- 15-day remediation cycle triggered for a 5-minute fix
- **Result:** $20K of completed work blocked by a typo

**The Risk:** Minor cosmetic issues trigger formal rejection/remediation cycles, delaying the project and creating adversarial dynamics.

---

### Issue #3: The "80% Scope Problem" ⚠️

**The Problem:**
In agile development, requirements written upfront only define ~80% of final scope. Edge cases and details emerge during implementation, but current language has no process for handling unspecified scenarios.

**Real-World Scenarios:**

#### Scenario A: The Race Condition

**Requirement in Backlog:**
"User can view available appointment slots and book an appointment"

**What Orases Delivers:**
- ✅ View slots feature works
- ✅ Booking feature works
- ✅ Confirmation email sent
- ✅ Appointment appears in dashboard
- ❌ Doesn't handle rare race condition where slot becomes unavailable while user is booking

**The Issue:**
- Was this specified in requirements? **NO** - edge case not anticipated
- Is it a problem? **YES** - should be fixed
- Is it a "failure to deliver"? **DEBATABLE** - we delivered what was specified

**Under Current Language:**
- Duke: "Rejected - users can book unavailable slots. This doesn't meet requirements."
- Orases: "That edge case wasn't in the requirements. It's a 15-hour enhancement."
- Duke: "It should have been obvious. Fix it for free within 15 days."
- **Result:** Dispute over whether unspecified edge case is a defect or enhancement

---

#### Scenario B: The API Limitation

**Requirement in Backlog:**
"Integrate with SpeedPay for non-native customer payments"

**What Orases Discovers During Integration:**
- SpeedPay API supports credit cards ✅
- SpeedPay API does NOT support ACH for non-native customers ❌
- This limitation wasn't documented; only discovered during actual integration

**What Orases Delivers:**
- Fully functional SpeedPay integration for credit card payments
- Clear documentation of ACH limitation

**The Issue:**
- Did Orases "fail to deliver"? **NO** - delivered what the API supports
- Does it meet the business need? **PARTIALLY** - credit cards work, ACH doesn't
- Is this Orases' fault? **NO** - API limitation outside Orases' control

**Under Current Language:**
- Duke: "Rejected - we need ACH support, not just credit cards."
- Orases: "SpeedPay API doesn't support ACH for non-native customers. We delivered what's technically possible."
- Duke: "Find a different payment processor or extend SpeedPay to support it."
- Orases: "That's a major scope change - different integration, different vendor contracts, different timeline."
- **Result:** 15-day remediation period but problem can't be fixed in 15 days with current approach. Stalemate.

---

#### Scenario C: The Ambiguous Performance Requirement

**Requirement in Backlog:**
"Mobile app loads within 2 seconds on average device"

**What Orases Delivers:**
- iPhone 13 (2021): **1.6 seconds** ✅
- iPhone 12 (2020): **1.8 seconds** ✅
- Galaxy S21 (2021): **1.5 seconds** ✅
- Galaxy S20 (2020): **1.9 seconds** ✅
- iPhone 8 (2017): **2.3 seconds** ❌

**The Issue:**
- Does it meet requirements? **DEPENDS** - what's "average device"?
- Is 2017 device "average" in 2026? **DEBATABLE** - that's 9 years old
- Should we optimize for legacy devices? **TRADEOFF** - may degrade modern experience

**Under Current Language:**
- Duke: "Rejected - doesn't meet 2-second requirement on iPhone 8."
- Orases: "What's 'average device'? iPhone 8 is 9 years old. Optimizing for ancient hardware compromises modern experience."
- Duke: "The requirement says 2 seconds on average device. Fix it."
- Orases: "Define 'average' - what percentage of Duke customers have 9-year-old devices?"
- **Result:** Dispute over ambiguous requirement that should have been clarified upfront

---

### Issue #4: Waterfall Acceptance for Agile Project ⚠️

**The Problem:**
The SOW describes agile/iterative development:
- Section 1.1: "continuous discovery," "continuous refinement"
- Section 1.2: "iterative development"
- Section 1.3: "iterative development of features"

But Section 1.4 imposes waterfall-style acceptance:
- Detailed requirements must be complete upfront
- Single delivery with all-or-nothing acceptance
- 15-day formal review cycles
- No recognition of incremental delivery

**The Conflict:**
In **agile**, you demo working software every sprint, get feedback, iterate, and accept work incrementally.

**Waterfall** acceptance (deliver once, accept or reject) contradicts this approach.

**Real-World Impact:**
- Pressure to over-specify requirements upfront (reduces agility)
- Fear of rejection drives gold-plating and over-engineering
- Orases reluctant to make reasonable judgment calls on edge cases
- Every ambiguity becomes a potential rejection point

---

## OUR PROPOSED SOLUTION: PAYMENT/ACCEPTANCE SPLIT

### Core Concept

**Separate two distinct questions:**
1. **Did Orases do the work?** → Payment (based on hours invested)
2. **Is it ready for production?** → Acceptance (based on quality standards)

### How It Works

**Track 1 - Payment for Work Performed:**
- Orases invoices for hours invested per time-and-materials terms (Section 05)
- CLIENT pays for work performed in good faith, regardless of acceptance status
- Payment is for effort, not perfection

**Track 2 - Acceptance for Production Deployment:**
- CLIENT accepts deliverables for production use only when they meet quality standards
- CLIENT retains full control over what goes to production
- Acceptance confirms production-readiness but is not required for payment

### Proposed Language

---

### 1.4 Review Period, Acceptance, and Payment

**Two-Track Process:**

This SOW separates payment rights from production acceptance rights to align with time-and-materials pricing and agile development practices:

**Track 1 - Payment for Work Performed:**
- Orases invoices for hours invested per the time-and-materials terms in Section 05
- CLIENT pays for work performed in good faith regardless of acceptance status
- Payment compensates Orases for effort and expertise applied to deliverables

**Track 2 - Acceptance for Production Use:**
- CLIENT accepts deliverables for production deployment when they meet acceptance criteria below
- Acceptance confirms deliverables are suitable for production use
- Acceptance is not required for payment but is required for production deployment

**Review Period:**

CLIENT has **fifteen (15) business days** after delivery to review and test Deliverables. CLIENT will provide written acceptance or rejection (email between designated project managers constitutes written notice).

**Acceptance Standard:**

Deliverables meet acceptance criteria when they:
- Substantially conform to requirements specified in Development Backlog as agreed at commencement of development
- Are free of **Critical** and **High-severity** defects (as defined below)
- Medium and Low severity defects do not block acceptance and are added to backlog for future sprints
- Achieve core business objectives
- Are suitable for production use

**Defect Severity Levels:**

| Severity | Definition | Blocks Acceptance? |
|----------|------------|-------------------|
| **Critical** | System unusable, data loss, security breach, core feature completely broken | YES |
| **High** | Important functionality doesn't work as specified, significant performance issues | YES (unless CLIENT waives) |
| **Medium** | Secondary features impacted, moderate issues with reasonable workarounds | NO - Added to backlog |
| **Low** | Minor bugs, cosmetic issues, edge cases, documentation gaps | NO - Added to backlog |

**Rejection and Remediation:**

If CLIENT identifies **Critical or High-severity defects**, CLIENT provides written notice within the Review Period including:
- Specific description of each defect with severity assessment
- Steps to reproduce the issue
- Reference to requirement not met
- Business impact

Orases responds within **three (3) Business Days** with either:
- **Agreement and remediation plan** with timeline, OR
- **Alternative assessment** if issues are not defects but rather new requirements, ambiguous specifications, or technical constraints discovered during integration, along with proposed path forward

Parties will collaboratively agree on remediation approach. Remediation of actual defects (work that doesn't meet specified requirements) is covered by the original sprint/phase budget. Enhancements or new requirements identified during review require separate approval per Section 1.2 Prioritization of Work.

**Acceptance Occurs When:**

Deliverables are accepted for production use upon the earlier of:
1. CLIENT's written acceptance, OR
2. CLIENT's deployment of deliverable to production (implies acceptance), OR
3. **Twenty (20) business days** after delivery without written rejection identifying specific Critical or High-severity defects

If CLIENT requires additional review time beyond 20 business days, CLIENT shall request extension in writing before expiration. Mutually agreed extensions suspend the acceptance trigger.

**Handling Emerging Requirements:**

The Parties acknowledge that in agile/iterative software development, some requirements emerge during implementation as edge cases, integration details, user experience considerations, and performance optimization needs become apparent. When Orases encounters scenarios not explicitly addressed in the agreed requirements, Orases will:

1. Flag the issue to CLIENT's Product Owner
2. Make reasonable decisions consistent with industry best practices and the spirit of the requirements
3. Document approach and rationale
4. Notify CLIENT Product Owner for material design decisions

Decisions made in good faith to address unspecified scenarios constitute substantial conformance with requirements. If CLIENT prefers a different approach, modifications will be treated as enhancements and added to the backlog for subsequent sprints, not grounds for rejection or non-payment.

**Acceptance Criteria:**

Deliverables shall meet the following criteria for production acceptance:
- Substantially conforms to requirements specified in Development Backlog and refined Project Scope as defined at commencement of development
- Free of Critical defects; High-severity defects either resolved or waived by CLIENT
- Core functionality operates as specified
- Meets security, compliance, and performance requirements as specified
- Suitable for production deployment in intended environment
- Documented as required (architecture, configuration, environment, or other artifacts as applicable)

**Collaborative Resolution:**

Before formal rejection, CLIENT and Orases agree to discuss concerns collaboratively to explore remediation approaches and clarify whether issues constitute defects (work doesn't meet specified requirements) or enhancements (new requirements emerging from use). This collaborative discussion does not extend the Review Period but promotes efficient resolution and maintains project partnership.

**Key Principle:**

This two-track approach aligns with the time-and-materials pricing structure in Section 05. Orases is compensated for good-faith effort applied to deliverables (payment track) while CLIENT retains full quality control over production deployment decisions (acceptance track). This supports agile iteration, protects both parties, and eliminates payment/acceptance conflicts.

---

## HOW THIS PROPOSED APPROACH SOLVES EACH ISSUE

### ✅ Solves Issue #1: No Payment Certainty

**Before (Duke's Language):**
- No deemed acceptance allowed
- Can't invoice until Duke formally accepts
- Duke could delay acceptance indefinitely while "still reviewing"
- Orases stuck in limbo with delivered work but no payment

**After (Our Proposed Approach):**
- Payment is based on hours worked (T&M pricing)
- Orases invoices for work performed regardless of acceptance status
- Acceptance is for production deployment, not payment
- **Result:** Cash flow certainty. Orases gets paid for work done in good faith, even if Duke needs more time to evaluate for production use.

**Why This Works:**
Duke is paying time-and-materials anyway, so they're paying for Orases' hours regardless. Our proposed approach clarifies: you pay for the work performed, but you control when it goes to production. This aligns payment with the actual pricing model (T&M) rather than forcing a deliverable-based payment structure.

---

### ✅ Solves Issue #2: No Material vs. Minor Defect Distinction

**Before (Duke's Language):**
- All defects treated equally
- Typo can block entire milestone
- Triggers 15-day remediation cycle for 5-minute fixes

**After (Our Proposed Approach):**
- Four severity levels: Critical, High, Medium, Low
- Only Critical and High defects block production acceptance
- Medium and Low defects go to backlog for next sprint
- **Result:** Minor issues don't derail the project. Typos and edge cases are fixed in normal sprint work.

**Example Application:**
Orases delivers appointment scheduling ($20K, 80 hours). Duke finds:
- Critical: Payment processing fails → Blocks acceptance ✓ Appropriate
- High: Can't reschedule appointments → Blocks acceptance ✓ Appropriate
- Medium: Edge case with timezone handling → Goes to backlog ✓ Reasonable
- Low: Typo in confirmation email → Goes to backlog ✓ Reasonable

Duke still gets quality control (can block for serious issues) but project keeps moving on minor issues.

---

### ✅ Solves Issue #3: The "80% Scope Problem"

**Before (Duke's Language):**
- No process for handling unspecified scenarios
- Ambiguous whether edge cases are "defects" or "enhancements"
- Disputes over what "should have been obvious"

**After (Our Proposed Approach):**
- Explicit "Handling Emerging Requirements" section
- Orases flags unspecified scenarios and proposes reasonable approaches
- Good-faith decisions constitute substantial conformance
- Different approaches are enhancements (added to backlog), not defects
- **Result:** Clear process prevents disputes. Both parties understand how to handle the inevitable ambiguities.

**Example Applications:**

**Scenario A - Race Condition:**
- Orases delivers scheduling feature
- Discovers rare race condition (not in requirements)
- Makes reasonable decision: optimistic locking with error recovery
- Documents approach and notifies Product Owner
- Duke: "Accepted. Good solution. Let's monitor in production."
- **NO DISPUTE.** Work continues.

**Scenario B - API Limitation:**
- During SpeedPay integration, discovers ACH not supported for non-native customers
- Orases notifies Duke immediately with options:
  1. Credit cards only for MVP (fast, limited)
  2. Integrate second processor for ACH (slower, complete)
  3. Different approach
- Duke: "Option 1 for MVP. We'll evaluate Option 2 for Phase 2."
- Orases delivers credit card integration
- Duke accepts for production use
- **NO DISPUTE.** Pragmatic resolution based on technical reality.

**Scenario C - Performance Ambiguity:**
- Requirement: "loads in 2 seconds on average device"
- Orases achieves 2 seconds on current-gen devices (2020+)
- Misses 2 seconds on 9-year-old devices
- Orases asks Duke: "What percentage of users have 2017 devices?"
- Duke: "Less than 3%"
- Duke and Orases agree: Accept current performance, monitor analytics, optimize for legacy if needed
- **NO DISPUTE.** Data-driven decision.

---

### ✅ Solves Issue #4: Waterfall Acceptance for Agile Project

**Before (Duke's Language):**
- All-or-nothing acceptance
- Formal review cycles
- Pressure to over-specify requirements upfront
- Fear of rejection drives conservative decisions

**After (Our Proposed Approach):**
- Payment based on sprint work (T&M)
- Production acceptance based on quality
- "Substantial conformance" standard (not perfection)
- Collaborative problem-solving for ambiguities
- **Result:** True agile approach. Iterate, learn, adapt, deliver incrementally.

**How It Enables Agile:**
- **Sprint demos:** Show working software, get feedback, iterate
- **Continuous payment:** Invoice for sprint work regardless of production deployment
- **Incremental acceptance:** Accept features for production as they're ready
- **Learn and adapt:** Discoveries during development inform next sprint, not trigger rejections

---

## WHY THIS APPROACH IS BEST FOR BOTH PARTIES

### For Duke Energy:

✅ **Maximum Control:** You decide what goes to production and when

✅ **Quality Standards:** You can still reject deliverables with Critical/High defects

✅ **No Surprises:** Clear severity definitions, collaborative resolution, documented approach

✅ **Aligns with T&M:** You're paying for hours anyway; this just clarifies when

✅ **Agile Benefits:** Supports iterative delivery, continuous improvement, faster time-to-market

✅ **Partnership Approach:** Collaborative problem-solving, not adversarial rejection cycles

### For Orases:

✅ **Payment Certainty:** Invoice for work performed, not stuck waiting for acceptance

✅ **Fair Treatment:** Compensated for good-faith effort even if requirements were ambiguous

✅ **Clear Standards:** Know exactly what blocks acceptance (Critical/High) vs. what doesn't (Medium/Low)

✅ **Professional Judgment:** Reasonable decisions on edge cases are covered

✅ **Reduced Risk:** Won't absorb costs for technical constraints or emerging requirements outside control

✅ **True Agile:** Can deliver incrementally without fear that minor issues block payment

---

## SUMMARY TABLE

| Issue | Duke's Current Language | Impact on Project | Our Proposed Solution |
|-------|------------------------|-------------------|-------------------|
| **No payment certainty** | "Deemed acceptance prohibited" | Cash flow crisis if Duke delays response | Payment based on hours worked (T&M) |
| **Minor defects block acceptance** | All defects treated equally | Typo blocks $20K milestone | Only Critical/High defects block |
| **80% scope problem** | No process for unspecified scenarios | Disputes over edge cases | Explicit emerging requirements process |
| **Waterfall for agile** | All-or-nothing acceptance | Fear of rejection, over-engineering | True agile with incremental acceptance |

---

## INTERNAL SUMMARY FOR ALIGNMENT

**Core Position:**
Section 1.4's current language creates four critical issues for Orases in an agile T&M engagement:
1. No payment certainty (deemed acceptance prohibited)
2. All defects treated equally (typos block milestones)
3. No process for emerging requirements (80% scope problem)
4. Waterfall acceptance contradicts agile methodology

**Recommended Approach:**
Implement a payment/acceptance split that:
- **Payment Track:** Invoice for hours worked (T&M) regardless of acceptance status
- **Acceptance Track:** Duke controls production deployment based on quality standards (Critical/High defects block acceptance; Medium/Low go to backlog)
- **Emerging Requirements Process:** Good-faith decisions on unspecified scenarios constitute substantial conformance

**Key Talking Points:**
- This gives Duke **more control** (production decisions) while eliminating payment disputes
- Aligns with the T&M pricing model already in the SOW
- Supports true agile/iterative development
- Clear severity framework prevents minor issues from blocking progress
- Collaborative approach for handling ambiguities and technical constraints

**Bottom Line:**
Duke pays for hours worked (which they're doing anyway) but retains full control over when deliverables go to production. We avoid cash flow issues and rejection disputes over edge cases that emerge during development.
