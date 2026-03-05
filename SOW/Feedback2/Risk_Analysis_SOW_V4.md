# Risk Analysis: Duke-Orases SOW #1 - V4

**Date:** February 25, 2026
**Document:** DE-Orases SOW#1 - V4.docx
**Analyst:** Risk Assessment based on SOW review and internal communications context

---

## Executive Summary

Based on the context of Duke Energy's strict compliance requirements and documented willingness to use dispute resolution processes, this SOW presents **HIGH RISK** to Orases. The structure favors Duke Energy significantly through a combination of:

- Time & materials model with CLIENT-controlled prioritization BUT fixed milestone commitments
- Undefined security/compliance requirements with termination rights
- Support obligations that consume development capacity without milestone protection
- Multiple ambiguous clauses that favor the party with more leverage

**Critical Context from Internal Communications:**
> "They will exercise the dispute process in the MSA and SOW at any point that they need to. They have the upper hand to 'bully' us when needed, like other larger clients of ours...This is not an instance where we can write one thing and not do something unless its a problem, etc. Will need to be followed from the start."

---

## 🔴 **CRITICAL RISKS**

### 1. **Undefined Scope with Fixed Milestones (High Business Risk)**
**Referenced Sections: 2.3, 4.0**

**Risk Description:**
- Time & materials model with CLIENT-controlled prioritization BUT fixed Key Milestones:
  - MVP by 9/30/2026 (7 months from effective date)
  - Phase 1 by 12/31/2027 (23 months from effective date)

**The Problem:**
- CLIENT can re-prioritize work at any time (Section 2.3)
- Orases still contractually accountable to milestone dates
- Duke's documented position: will use dispute process when needed
- If milestones slip due to CLIENT reprioritization, Duke can claim breach

**Contractual Gap:**
Section 4 states: "Delays caused by CLIENT, its vendor or factors outside Orases reasonable control entitle Orases to a reasonable extension."

However:
- No definition of what constitutes a "CLIENT-caused delay"
- No process for how extensions are approved
- No formula for calculating "reasonable" extension
- Ambiguous whether CLIENT reprioritization counts as a delay they "caused"

**Potential Scenarios:**
1. Duke reprioritizes backlog multiple times, consuming analysis cycles
2. MVP date arrives with incomplete scope
3. Duke claims Orases failed to meet commitment; Orases claims CLIENT-caused delays
4. Dispute resolution with Duke "having the upper hand"

**Recommendation:**
Add explicit language that milestone dates automatically adjust when CLIENT reprioritization impacts critical path, with documented change approval process:

*"If CLIENT reprioritization decisions pursuant to Section 2.3 result in scope changes, new feature additions, or deferral of previously prioritized work, the Project Schedule and Key Milestones shall be adjusted by mutual written agreement to reflect the revised priorities. Orases shall provide written notice of projected milestone impacts within 5 business days of any material reprioritization, and CLIENT shall respond within 10 business days with acceptance or alternative approach."*

---

### 2. **"Substantial Conformance" Ambiguity (Legal/Payment Risk)**
**Referenced Sections: 2.7.1**

**Risk Description:**
Acceptance criteria includes a "Substantial Conformance Standard" that allows Orases to make "reasonable decisions consistent with industry best practices" when encountering scenarios not explicitly addressed in approved requirements.

**The Problem:**
Section 2.7.1 states:
> "Decisions made in good faith to address unspecified scenarios constitute substantial conformance with requirements. If CLIENT prefers a different approach after review, modifications will be treated as enhancements and added to the Backlog for prioritization per Section 2.3, not grounds for rejection or non-acceptance."

**Duke's Likely Position:**
- With strict compliance culture and documented willingness to dispute, Duke will likely challenge what constitutes "substantial conformance"
- Duke may argue that implementation decisions require advance approval
- Duke may reject deliverables as non-conforming, refuse payment, and demand modifications under original scope

**Payment Risk:**
- Orases delivers feature believing it substantially conforms
- Duke rejects as not meeting requirements
- Orases argues it was "good faith reasonable decision"
- Duke invokes dispute process
- Meanwhile, payment is withheld pending resolution

**Recommendation:**
This clause needs tighter definition and a decision-making process:

*"When Orases encounters scenarios not explicitly addressed in the approved PRD/TRD, Orases shall:*
1. *Notify CLIENT Product Owner in writing within 2 business days of identifying the scenario*
2. *Provide recommended approach with rationale*
3. *Obtain written approval from CLIENT Product Owner before implementation*
4. *If CLIENT does not respond within 5 business days, Orases may proceed with recommended approach, which shall constitute substantial conformance*

*Decisions requiring CLIENT approval include but are not limited to: user workflow changes, data model modifications, integration approach changes, security/compliance interpretations, and UI/UX patterns not specified in approved designs."*

---

### 3. **Unlimited Hypercare/Support Burden (Budget/Timeline Risk)**
**Referenced Sections: 2.5, 2.6, 2.8.9**

**Risk Description:**
Hypercare and Production Support are performed by the **same project team** doing feature development, with prioritized response targets but no capacity caps.

**The Problem:**

**Section 2.5 Hypercare:**
- 10 calendar days post-release stabilization period
- Response targets: Critical = 1 hour, High = 2 hours
- "CLIENT acknowledges that allocation of team capacity toward Hypercare activities may affect project timelines and velocity"

**Section 2.6 Production Support:**
- Ongoing for duration of SOW after Hypercare
- Same team, same acknowledgment about timeline impacts
- Time & materials billing at standard rates

**Section 2.8.9 SLAs:**
- Response time targets defined (1-4 hours depending on severity)
- Resolution depends on "issue complexity, CLIENT responsiveness, competing priorities"

**The Fatal Flaw:**
- CLIENT controls prioritization (Section 2.3) and doesn't have to agree to timeline extensions
- Monthly spend estimate ($80-105K) doesn't explicitly account for support overhead
- No cap on support hours that can be demanded

**Scenario:**
1. Major production issues consume 60% of team capacity for 3 weeks
2. Feature development stops or slows significantly
3. MVP milestone approaches
4. Orases notifies CLIENT of timeline impact
5. CLIENT refuses timeline extension, citing Section 2.8.9 statement that resolution depends on "competing priorities"
6. Duke argues Orases should have resourced appropriately; Orases argues CLIENT support demands caused delay
7. Dispute resolution with Duke having leverage

**Compounding Factor:**
Each release triggers a new 10-day Hypercare period. With continuous releases, team could be perpetually in Hypercare status.

**Recommendation:**
Add capacity protections:

*"Support Activities Capacity Management:*
- *Hypercare and Production Support activities shall not exceed 20% of total team capacity in any two-week sprint without triggering automatic milestone adjustment*
- *If support activities exceed 20% threshold for two consecutive sprints, the Parties shall meet within 5 business days to either: (a) add dedicated support resources at CLIENT expense, (b) adjust Key Milestones to reflect support burden, or (c) defer support requests to future sprints*
- *Monthly spend estimates in Section 5 assume support activities averaging 15% of team capacity; sustained support demands exceeding this threshold may result in revised monthly spend projections"*

---

### 4. **ISO/Security Requirements Undefined (Compliance/Cost Risk)**
**Referenced Sections: Appendix 2, Section 3.1, MSA Integration**

**Risk Description:**
SOW references compliance with Duke IT security protocols, Cybersecurity Assessment Questionnaire, and Remediation Plans, but doesn't define scope or allocate costs.

**The Problem:**

**From Internal Communications:**
> "Vlad you and DE IT are going to need to meet regarding the minimum requirements for ISO, etc...The way it is written is those are required, regardless of SOW request IF we are doing anything with areas that they would apply to (Confidential info, security, etc.). It is not optional based on business unit. Their attorney requested that you and Rick (DE IT) discuss for clarity. They were not OK with our redline there."

**From Appendix 2:**
> "Consultant may be required periodically to complete a Cybersecurity Assessment Questionnaire...Assessment reviews may identify material issues...Consultant shall develop a Duke Energy-approved Remediation Plan...In the event that Consultant does not meet its obligations of the Remediation Plan, Duke Energy reserves the right to terminate this SOW."

**Undefined Requirements:**
- ISO certification level (27001? 27017? 27018?)
- SOC 2 compliance expectations
- Penetration testing frequency and scope
- Infrastructure security requirements (encryption standards, key management, network segmentation)
- Personnel security (background checks, security training, access controls)
- Incident response requirements
- Disaster recovery/business continuity testing

**Cost Impact:**
ISO certifications, security audits, infrastructure hardening, compliance personnel could add:
- $50K-150K for initial ISO 27001 certification
- $25K-50K annual maintenance
- $15K-40K per penetration test
- Infrastructure hardening costs (encryption, monitoring, SIEM tools)
- Dedicated security/compliance personnel time

**Termination Risk:**
Duke can terminate if Orases fails to implement security changes, even if those requirements weren't originally understood or budgeted.

**Current SOW Language:**
Section 3.3 states Consultant will "Deliver Services and Deliverables that meet acceptance criteria and quality standards defined in this SOW and mutually agreed upon."

But security requirements are incorporated by reference to Appendix 2, which references "security protocols set forth by Duke Energy" without specificity.

**Recommendation - URGENT ACTION REQUIRED:**

**Before Signing:**
1. Vlad MUST complete meeting with Duke IT (Rick) to obtain written documentation of ALL security/compliance requirements
2. Obtain specific list:
   - Required certifications (ISO 27001, SOC 2, etc.)
   - Infrastructure requirements (cloud provider, encryption standards, network architecture)
   - Personnel requirements (background checks, training, access controls)
   - Testing/audit requirements (penetration testing frequency, security audits)
   - Compliance documentation requirements
3. Review Third Party Risk Management Service Risk Profile Questionnaire referenced in CLAUDE.md

**Contractual Language to Add:**

*"Section 3.1 Security and Compliance Requirements:*

*Orases shall comply with the security and compliance requirements documented in Appendix 2A (Security Requirements Matrix), which shall be mutually agreed upon and executed as part of this SOW within 30 days of the Effective Date.*

*Appendix 2A shall specify:*
- *Required certifications and compliance frameworks*
- *Infrastructure and architecture security requirements*
- *Personnel security requirements*
- *Testing, audit, and assessment requirements*
- *Timeline for achieving compliance milestones*
- *Allocation of costs: [OPTION A: security compliance costs included in T&M rates up to $X annually] OR [OPTION B: security compliance costs billed separately as pass-through expenses]*

*If the Parties cannot reach mutual agreement on Appendix 2A within 30 days, either Party may terminate this SOW without penalty, and CLIENT shall pay for work performed through termination date."*

---

### 5. **API/Integration Dependency Acknowledged but Unprotected (Timeline Risk)**
**Referenced Sections: 3.1 Project Assumptions, 2.2 Analysis Activities**

**Risk Description:**
SOW explicitly acknowledges that technical feasibility is unknown and dependent on Duke systems, but provides inadequate contractual protection if Duke fails to deliver integration capabilities.

**Section 3.1 Project Assumptions:**
> "CLIENT acknowledges that preliminary sales-related discovery was completed WITHOUT Duke Energy's project team participation, and significant technical unknowns remain, including but not limited to:
> - API availability and integration capabilities
> - Technical feasibility of proposed features
> - Security and compliance requirements
> - Integration complexity with existing Duke systems
> - Production deployment constraints"

**From CLAUDE.md Critical Success Factors:**
> "API Integration: Duke IT must provide API documentation and sandbox access within 2 weeks of kickoff"

**The Problem:**
Section 4 states: "Delays caused by CLIENT, its vendor or factors outside Orases reasonable control entitle Orases to a reasonable extension."

**But:**
- No specific milestone dependencies tied to Duke deliverables
- No definition of what Duke must provide or when
- No contractual remedy if Duke systems aren't ready
- Duke could argue API delays are within Duke's control but not something Duke "caused" in the context of the SOW

**Required Duke System Integrations (from CLAUDE.md):**
1. **Commerce Platform** - Customer data and billing APIs
2. **Dynamics CRM** - Service order management and contractor coordination APIs
3. **Duke Energy Data Fabric** - Enterprise data integration layer
4. **Contractor Portals** - Real-time job assignment and status update APIs
5. **SpeedPay** - Payment processing integration for non-native customers

**Realistic Scenario:**
1. Week 2: Orases requests API documentation for Commerce Platform
2. Week 6: Duke IT provides partial documentation, notes some APIs not yet available
3. Week 10: Orases discovers integration complexity significantly higher than estimated
4. Week 16: Duke IT delays sandbox environment due to internal security review
5. Week 20: Architecture decisions blocked waiting for Duke system clarifications
6. Month 7: MVP deadline approaches, core features incomplete due to integration delays
7. Orases claims CLIENT-caused delays; Duke claims Orases should have planned for unknowns
8. Dispute

**Recommendation:**
Add explicit Duke deliverable schedule with milestone dependencies:

*"Section 3.4 Duke Energy System Integration Deliverables:*

*CLIENT shall provide the following integration capabilities and documentation according to the following schedule, measured from the Effective Date:*

| *Duke Deliverable* | *Target Date* | *Dependent SOW Milestone* |
|---|---|---|
| *API documentation for Customer Validation, HPP Plans, Service Request Creation APIs* | *Week 2* | *Architecture design (Week 8)* |
| *Sandbox environment access with test data* | *Week 4* | *Integration development start (Week 12)* |
| *Dynamics CRM integration specifications* | *Week 6* | *Service request workflow development (Week 14)* |
| *Commerce Platform integration testing support* | *Week 10* | *Alpha testing (Week 20)* |
| *Production deployment environment and procedures* | *Week 16* | *MVP release preparation (Week 24)* |

*If CLIENT fails to provide any deliverable within 2 weeks of the Target Date, the Dependent SOW Milestone and all subsequent Key Milestones shall be extended by the duration of the delay, plus reasonable time for Orases to adjust development activities (minimum 1-week extension for each delayed deliverable).*

*If any Duke system integration proves infeasible or requires materially different approach than documented in Sales Reference Documents (Appendix 1), the Parties shall meet within 5 business days to assess impact and agree upon either: (a) alternative technical approach with revised timeline and budget, (b) scope reduction, or (c) SOW amendment."*

---

## 🟡 **MODERATE RISKS**

### 6. **Resource Substitution Latitude (Quality Risk)**
**Referenced Sections: 2.8.5**

**Risk Description:**
Section 2.8.5 states:
> "Orases may substitute project resources as needed to support continuity of delivery, provided that replacement resources have comparable skills and experience. Key role substitutions will be communicated to CLIENT in advance when reasonably practicable. Non-key role substitutions may occur without prior communication."

**The Problem:**
- Duke's strict compliance culture (per internal communications) suggests they will scrutinize team continuity
- "Reasonably practicable" is subjective and could lead to disputes
- "Comparable skills and experience" is not objectively defined
- Risk of quality degradation or velocity reduction with frequent substitutions

**Potential Scenario:**
1. Orases substitutes 2 developers mid-sprint for business reasons
2. Sprint velocity drops as new developers ramp up
3. Duke notices reduced productivity in Sprint Status Reports
4. Duke challenges whether resources are truly "comparable"
5. Friction over resource quality and project progress

**Mitigation:**
Current language is reasonable for a T&M engagement, but Duke's culture suggests tighter controls may be expected.

**Recommendation:**
Consider tightening slightly:

*"Key role substitutions (Product Manager, Project Manager, Technical Lead) require 15 business days advance notice to CLIENT and written confirmation that replacement resource meets or exceeds the qualifications of the departing resource. Non-key role substitutions may occur without prior notice but shall be documented in Sprint Status Reports with justification if substitution materially impacts sprint velocity."*

---

### 7. **Auto-Acceptance After 10 Days (Process Risk)**
**Referenced Sections: 2.7**

**Risk Description:**
Section 2.7 states:
> "CLIENT shall have ten (10) business days after delivery of the applicable Deliverables (the 'Review Period') to review and test the Services and Deliverables...Any Services or Deliverables not accepted or rejected in writing within the Review Period shall be deemed accepted."

**The Problem:**
- Duke's attorney emphasized strict compliance and proper process adherence
- Unlikely Duke will miss review windows, but if they do, auto-acceptance could lead to disputes
- Duke might argue that auto-acceptance shouldn't apply to defective deliverables

**Potential Scenario:**
1. Orases delivers feature with Critical defect not discovered during Review Period
2. Feature auto-accepts after 10 business days
3. Defect discovered in production, causes customer impact
4. Duke demands immediate fix at no cost, argues defect existed at delivery
5. Orases points to auto-acceptance, argues issue is now Production Support
6. Dispute over whether auto-acceptance applies to latent defects

**Analysis:**
This is fairly standard language and generally protects Orases from indefinite review cycles. However, it should be paired with clear defect management language.

**Recommendation:**
Add clarification:

*"Auto-acceptance pursuant to this Section 2.7 does not waive CLIENT's rights to report defects discovered after acceptance. Defects discovered post-acceptance shall be addressed pursuant to Section 2.6 (Production Support) and prioritized pursuant to Section 2.3. However, defects that would have been discoverable through reasonable testing during the Review Period and that meet Critical or High severity definitions (Section 2.8.8) shall be remediated without additional charge to CLIENT if reported within 30 days of acceptance."*

---

### 8. **Governance Evolution Clause (Control Risk)**
**Referenced Sections: 2.8.11**

**Risk Description:**
Section 2.8.11 states:
> "The Parties acknowledge that governance practices may evolve over the course of the Project. Governance details, including cadence, roles, and tools, may be refined by mutual agreement to better align with project realities and CLIENT needs."

**The Problem:**
- "Mutual agreement" suggests equal footing, but internal communications indicate Duke has upper hand
- Duke could push for more rigid governance, more frequent meetings, more documentation
- No protection against Duke unilaterally demanding process changes
- "CLIENT needs" language suggests Duke-centric evolution

**Potential Scenario:**
1. Project encounters early challenges
2. Duke stakeholders demand daily status updates, mandatory attendance at weekly governance meetings
3. Orases team spends 20% of time in meetings/reporting instead of delivery
4. Orases objects that this wasn't contemplated in estimates
5. Duke cites Section 2.8.11 and "mutual agreement" requirement
6. Friction over governance overhead

**Analysis:**
This clause is reasonable and provides flexibility, but Duke's documented negotiating posture suggests they may use it to increase oversight if project faces challenges.

**Recommendation:**
Add boundaries:

*"Governance refinements shall be mutually agreed in writing and shall not materially increase reporting burden or meeting cadence beyond what is documented in Section 2.8.3 without corresponding adjustment to project capacity and budget estimates. If governance changes reduce team productivity by more than 10%, the Parties shall adjust either the governance model or the Project Schedule to maintain delivery momentum."*

---

### 9. **Estimated Monthly Spend Disclaimer (Budget Expectation Risk)**
**Referenced Sections: 5.0**

**Risk Description:**
Section 5.0 states:
> "Based on current staffing assumptions and projected scope, the anticipated monthly spend under this SOW is estimated to range between $80,000 and $105,000 per month. This estimate is provided for budgeting purposes only and does not constitute a minimum or maximum commitment."

**The Problem:**
- Estimate provides CLIENT budget expectation even though it's not contractually binding
- If actual spend consistently exceeds $105K/month, Duke may claim misrepresentation or poor estimating
- Internal communications emphasize Duke's willingness to dispute - budget overruns could trigger conflict
- No definition of what assumptions underlie the estimate

**Potential Scenario:**
1. Month 1-3: Actual spend is $115K/month due to discovery complexity
2. Month 4-6: Actual spend is $125K/month as development ramps up
3. Month 7: Duke finance team escalates budget overruns
4. Duke demands explanation and budget controls
5. Orases points to "not a commitment" language
6. Duke argues estimate was materially inaccurate and should have been updated
7. Tension over budget management

**Analysis:**
The disclaimer language protects Orases legally but not practically. Duke's culture suggests they track to estimates even when not binding.

**Recommendation:**
Add transparency requirements:

*"Orases shall provide monthly budget projections as part of the Monthly Stakeholder Meeting (Section 2.8.3), including:*
- *Actual spend vs. estimate for the prior month*
- *Forecasted spend for the next 3 months*
- *Explanation of any variance >15% from the stated estimate range*
- *Factors driving spend levels (scope, team size, support burden, etc.)*

*If forecasted spend is projected to exceed the estimated range for 3 consecutive months, the Parties shall meet to review scope priorities, team composition, and delivery approach to identify opportunities to manage spend while maintaining progress toward Key Milestones."*

---

## 🟢 **LOW/MANAGED RISKS**

### 10. **Change Order Process References MSA (Documented)**
**Referenced Sections: 6.0**

**Risk Description:**
Section 6.0 references Section 8 of the Agreement (MSA) for change order procedures.

**Analysis:**
Standard change order process. Should function appropriately if both parties act in good faith. However, Duke's documented "upper hand" position could result in slow approvals or disputes over what constitutes a change vs. original scope.

**Recommendation:**
Ensure Section 2.3 prioritization process is used for most scope adjustments to avoid triggering formal change order overhead. Reserve formal change orders for material impacts to Key Milestones or budget.

---

### 11. **30-Day Ramp-Down Notice (Staffing Protection)**
**Referenced Sections: 5.0**

**Risk Description:**
Section 5.0 states:
> "If CLIENT wants Orases to change the number of hours or team size assigned to this SOW, it shall submit to Orases a written request for such change(s) with no less than 30 days' advanced written notice."

**Analysis:**
Reasonable protection for both parties. Gives Orases time to adjust staffing plans if CLIENT wants to ramp down or ramp up.

**Low Risk Assessment:**
This clause protects Orases from sudden team size changes and associated resource management challenges.

---

### 12. **Rate Increase Provisions (Cost Management)**
**Referenced Sections: 5.0**

**Risk Description:**
Section 5.0 states:
> "Orases reserves the right to revise its rate schedule upon 90 days' prior written notice to CLIENT, but no more often than once per year and not within the first year of the SOW."

**Analysis:**
- Fair protection for Orases against inflation and market rate changes
- Cannot increase rates in Year 1 (through Feb 2027)
- Can increase once per year thereafter with 90 days notice
- Standard and reasonable terms

**Low Risk Assessment:**
Appropriate cost protection for long-term T&M engagement.

---

## 🎯 **KEY RISK MITIGATION ACTIONS**

### **BEFORE SIGNING - BLOCKING ITEMS:**

#### 1. **Security/Compliance Requirements Definition (CRITICAL)**
**Owner:** Vlad + Duke IT (Rick)
**Action:** Complete security requirements meeting and obtain written documentation
**Deliverable:** Appendix 2A - Security Requirements Matrix including:
- Required certifications (ISO 27001, SOC 2, etc.)
- Infrastructure requirements
- Personnel requirements (background checks, training)
- Testing/audit requirements
- Cost allocation model

**Why Critical:** Duke rejected Orases' redline attempting to limit these requirements. Undefined compliance costs could exceed $100K+ annually and failure to meet requirements gives Duke termination rights.

---

#### 2. **Milestone Adjustment Language (HIGH PRIORITY)**
**Owner:** Contract negotiation team
**Action:** Add explicit language that Key Milestones adjust when CLIENT reprioritization impacts critical path
**Proposed Language:** See Section 1 recommendations above

**Why Critical:** Current SOW holds Orases accountable to fixed dates but gives CLIENT unlimited reprioritization rights. Duke's documented dispute willingness makes this a high-risk gap.

---

#### 3. **Support Capacity Caps (HIGH PRIORITY)**
**Owner:** Contract negotiation team
**Action:** Add capacity management language limiting support burden without milestone adjustment
**Proposed Language:** See Section 3 recommendations above

**Why Critical:** Same team doing support and development with no capacity limits. Production issues could consume all capacity while milestones remain fixed.

---

#### 4. **Duke System Integration Dependencies (MEDIUM-HIGH PRIORITY)**
**Owner:** Contract negotiation team + Duke IT
**Action:** Add Duke deliverables schedule with milestone dependencies
**Proposed Language:** See Section 5 recommendations above

**Why Critical:** SOW acknowledges "significant technical unknowns" including API availability, but doesn't protect Orases if Duke systems aren't ready. Integration delays are the most common cause of custom development project failures.

---

### **AFTER SIGNING - OPERATIONAL CONTROLS:**

#### 5. **Documentation Discipline**
**Action Items:**
- Document EVERY CLIENT decision in writing (email confirmations count per SOW)
- Document EVERY reprioritization with impact assessment to milestones
- Document EVERY delay caused by waiting for CLIENT feedback, SME availability, or Duke system access
- Weekly written status reports showing:
  - Support hours vs. development hours
  - CLIENT-caused delays
  - Risks to milestone dates
  - Budget burn rate vs. estimate

**Why Critical:** Internal message says "This is not an instance where we can write one thing and not do something unless its a problem." Duke will hold Orases to strict compliance. Documentation is the only defense in disputes.

---

#### 6. **Proactive Escalation**
**Action Items:**
- Don't wait until milestone deadline to escalate risks
- Monthly Stakeholder Meetings should include explicit milestone health assessment
- Any risk to Key Milestones should trigger immediate escalation to Duke Product Owner and executive sponsors
- Request written acknowledgment of risks and decisions to proceed/adjust

**Why Critical:** Duke's culture of strict compliance means surprises will be poorly received. Early, transparent escalation is critical to maintaining trust and getting milestone adjustments before deadlines pass.

---

#### 7. **Budget Transparency**
**Action Items:**
- Provide monthly spend projections as recommended in Section 9 above
- If spend exceeds $105K/month estimate for 2 consecutive months, proactively schedule budget review meeting
- Track and communicate support burden impact on development velocity
- Connect budget to scope priorities - make trade-offs explicit

**Why Critical:** Even though monthly estimate is "not a commitment," Duke finance will track to it. Proactive budget management prevents surprise escalations.

---

#### 8. **Security/Compliance Project Tracking**
**Action Items:**
- Create separate project plan for security/compliance work
- Track costs separately from feature development
- Provide quarterly compliance status reports to Duke
- Get written acceptance of Remediation Plans before starting work

**Why Critical:** Security requirements are grounds for termination if not met. Treating compliance as separate workstream ensures visibility and accountability.

---

## 📊 **RISK SCORING MATRIX**

| Risk # | Risk Name | Probability | Impact | Risk Score | Status |
|--------|-----------|-------------|--------|------------|---------|
| 1 | Undefined Scope + Fixed Milestones | High | Critical | **RED** | Needs contract fix |
| 2 | "Substantial Conformance" Ambiguity | Medium | High | **RED** | Needs contract fix |
| 3 | Unlimited Support Burden | High | High | **RED** | Needs contract fix |
| 4 | ISO/Security Requirements Undefined | High | Critical | **RED** | Blocking - needs immediate action |
| 5 | API/Integration Dependencies | High | High | **RED** | Needs contract fix |
| 6 | Resource Substitution | Low | Medium | **YELLOW** | Consider tightening |
| 7 | Auto-Acceptance | Low | Medium | **YELLOW** | Consider clarification |
| 8 | Governance Evolution | Medium | Medium | **YELLOW** | Consider boundaries |
| 9 | Budget Expectation Mismatch | Medium | Medium | **YELLOW** | Operational controls |
| 10 | Change Order Process | Low | Low | **GREEN** | Standard process |
| 11 | Rate Increases | Low | Low | **GREEN** | Adequate protection |

**Overall Project Risk Rating: 🔴 HIGH**

---

## 💬 **OVERALL ASSESSMENT & RECOMMENDATION**

### **The Bottom Line:**

**This SOW structure significantly favors Duke Energy.** Combined with the internal communications context about Duke's negotiating posture, this creates a **high-risk engagement** where Orases has limited contractual protection in key areas.

### **✅ Positive Aspects:**
1. **Time & Materials model** protects against fixed-price overruns
2. **CLIENT prioritization** acknowledges that scope will evolve
3. **Iterative delivery approach** allows for continuous discovery and adjustment
4. **Clear governance framework** provides structure for collaboration
5. **Reasonable payment terms** (NET 30, twice-monthly invoicing)

### **❌ High-Risk Aspects:**
1. **Fixed milestones with undefined scope** - Duke controls prioritization but Orases owns dates
2. **Support obligations eating development capacity** - no caps, no automatic milestone adjustments
3. **Unspecified compliance costs** - ISO/security requirements undefined but mandatory and grounds for termination
4. **Duke system integration dependencies** - acknowledged but unprotected
5. **Multiple ambiguous standards** - "substantial conformance," "reasonable," "material" - all favor party with more leverage
6. **Duke's documented negotiating posture** - willing to "bully," will use disputes, rejected Orases redlines

### **Critical Warning from Internal Communications:**
> "We need to be 100% comfortable performing under strict guidelines that we are agreeing to. This is not an instance where we can write one thing and not do something unless its a problem, etc. Will need to be followed from the start."

**This assessment is accurate.** The SOW must be followed exactly as written, and the ambiguous areas create significant exposure where Duke can dispute Orases' performance.

---

### **RECOMMENDATION:**

**DO NOT SIGN without addressing blocking items #1-4 above, particularly:**
- ✋ **BLOCKING:** Complete security requirements definition (Vlad meeting with Duke IT)
- 🔴 **HIGH PRIORITY:** Add milestone adjustment language tied to CLIENT reprioritization
- 🔴 **HIGH PRIORITY:** Add support capacity caps or automatic milestone adjustments
- 🟡 **MEDIUM PRIORITY:** Add Duke deliverables schedule with dependencies

**If Duke Energy refuses to address these gaps:**
- Proceed only with executive-level risk acceptance
- Implement rigorous operational controls (documentation, escalation, budget tracking)
- Consider this a "strategic client" engagement where relationship value outweighs contractual risk
- Build strong relationship with Joshua (Digital & Technology Lead) and Product Owner as primary risk mitigation

**The relationship will be "AWESOME" (per internal message) only if:**
1. Duke provides APIs and system access on time
2. Duke Product Owner makes clear, consistent prioritization decisions
3. Duke accepts that T&M model means scope evolution requires milestone flexibility
4. Both parties act in good faith to balance requirements and budget

**But given Duke's documented posture**, Orases should **plan for disputes and be prepared to defend every decision with written documentation.**

---

## 📎 **APPENDIX: RECOMMENDED REDLINES**

### **Add New Section 3.4: Duke Energy System Integration Deliverables**

*"CLIENT shall provide the following integration capabilities and documentation according to the following schedule, measured from the Effective Date:*

| *Duke Deliverable* | *Target Date* | *Dependent SOW Milestone* |
|---|---|---|
| *API documentation for Customer Validation, HPP Plans, Service Request Creation APIs* | *Week 2* | *Architecture design (Week 8)* |
| *Sandbox environment access with test data* | *Week 4* | *Integration development start (Week 12)* |
| *Dynamics CRM integration specifications* | *Week 6* | *Service request workflow development (Week 14)* |
| *Commerce Platform integration testing support* | *Week 10* | *Alpha testing (Week 20)* |
| *Production deployment environment and procedures* | *Week 16* | *MVP release preparation (Week 24)* |

*If CLIENT fails to provide any deliverable within 2 weeks of the Target Date, the Dependent SOW Milestone and all subsequent Key Milestones shall be extended by the duration of the delay, plus reasonable time for Orases to adjust development activities (minimum 1-week extension for each delayed deliverable)."*

---

### **Revise Section 2.3: Prioritization of Work - Add Paragraph:**

*"If CLIENT reprioritization decisions pursuant to this Section 2.3 result in scope changes, new feature additions, or deferral of previously prioritized work, the Project Schedule and Key Milestones shall be adjusted by mutual written agreement to reflect the revised priorities. Orases shall provide written notice of projected milestone impacts within 5 business days of any material reprioritization, and CLIENT shall respond within 10 business days with acceptance or alternative approach."*

---

### **Revise Section 2.5: Hypercare - Add Paragraph:**

*"Hypercare and Production Support activities shall not exceed 20% of total team capacity in any two-week sprint without triggering automatic milestone adjustment. If support activities exceed 20% threshold for two consecutive sprints, the Parties shall meet within 5 business days to either: (a) add dedicated support resources at CLIENT expense, (b) adjust Key Milestones to reflect support burden, or (c) defer support requests to future sprints."*

---

### **Add New Section 3.1: Security and Compliance Requirements**

*"Orases shall comply with the security and compliance requirements documented in Appendix 2A (Security Requirements Matrix), which shall be mutually agreed upon and executed as an amendment to this SOW within 30 days of the Effective Date.*

*Appendix 2A shall specify:*
- *Required certifications and compliance frameworks*
- *Infrastructure and architecture security requirements*
- *Personnel security requirements*
- *Testing, audit, and assessment requirements*
- *Timeline for achieving compliance milestones*
- *Allocation of costs: [OPTION A: security compliance costs included in T&M rates up to $X annually] OR [OPTION B: security compliance costs billed separately as pass-through expenses]*

*If the Parties cannot reach mutual agreement on Appendix 2A within 30 days, either Party may terminate this SOW without penalty, and CLIENT shall pay for work performed through termination date."*

---

### **Revise Section 2.7.1: Substantial Conformance Standard - Replace Paragraph:**

*"When Orases encounters scenarios not explicitly addressed in the approved PRD/TRD, Orases shall:*
1. *Notify CLIENT Product Owner in writing within 2 business days of identifying the scenario*
2. *Provide recommended approach with rationale*
3. *Obtain written approval from CLIENT Product Owner before implementation*
4. *If CLIENT does not respond within 5 business days, Orases may proceed with recommended approach, which shall constitute substantial conformance*

*Decisions requiring CLIENT approval include but are not limited to: user workflow changes, data model modifications, integration approach changes, security/compliance interpretations, and UI/UX patterns not specified in approved designs."*

---

**END OF RISK ANALYSIS**
