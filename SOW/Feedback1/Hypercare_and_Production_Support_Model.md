# Hypercare and Production Support Model
## Addendum to Section 1.5 Project Governance

---

## Overview

This document addresses the critical intersection of **ongoing development work** and **production support** for live releases. As we follow an iterative delivery model (MVP → V1 → V2 → VX), there will be periods where:

1. **New features are in active development** (future versions)
2. **Production systems require support and maintenance** (current live version)

This addendum clarifies how Orases handles both workstreams concurrently, how production incidents impact development timelines, and how support effort is tracked and billed.

---

## 1. Concurrent Development and Production Support

### 1.1 Dual Workstream Model

Once the **MVP (or any subsequent version) is deployed to production**, Orases will operate in a dual workstream model:

| Workstream | Focus | Resource Allocation | Priority |
|------------|-------|---------------------|----------|
| **Production Support** | Maintaining live production environment, resolving defects, addressing incidents, applying security patches | Allocated as needed based on incident severity | **Critical/High defects take precedence over planned development** |
| **Active Development** | Building new features for next version (V1, V2, etc.), implementing enhancements, addressing Medium/Low backlog items | Primary team allocation per sprint plan | Planned work proceeds unless interrupted by production incidents |

### 1.2 Resource Flexibility and Impact on Development Velocity

**Key Principle**: Production stability takes precedence over new feature development.

**Operational Reality**:
- When Critical or High severity production defects occur, Orases will **pull developers from planned feature work** to troubleshoot, fix, test, and deploy resolutions
- This production support effort **directly impacts planned development velocity and timelines**
- Orases cannot deliver the same volume of new features if significant production support effort is required during the sprint

**Example Scenario**:
- **Planned Sprint**: Team commits to delivering Feature X (estimated 80 hours)
- **Production Incident**: Critical payment processing bug discovered (requires 40 hours to investigate, fix, test, and deploy)
- **Impact**: Feature X will either:
  - Slip to the next sprint, OR
  - Be partially delivered with remaining work carried forward
- **Communication**: Orases will notify CLIENT immediately when production incidents impact sprint commitments

---

## 2. Hypercare Period Definition

### 2.1 What is Hypercare?

**Hypercare** is an intensive support period immediately following a major production release (MVP, V1, V2, etc.) where Orases provides elevated support to ensure system stability and rapid issue resolution.

### 2.2 Hypercare Period Duration

| Release Type | Hypercare Duration | Rationale |
|--------------|-------------------|-----------|
| **MVP or Major Version Release** | **4 weeks post-production deployment** | Initial production release carries highest risk; user adoption patterns unknown; integration issues may surface under real load |
| **Minor Version Release** | **2 weeks post-production deployment** | Lower risk; existing production infrastructure proven; incremental changes |
| **Hotfix or Patch Release** | **1 week post-deployment** | Targeted fix with limited scope; minimal risk of cascading issues |

### 2.3 Hypercare Support Model

During Hypercare, Orases provides:

1. **Enhanced Monitoring**:
   - Daily review of application logs, error rates, and performance metrics
   - Proactive identification of anomalies or trends
   - Daily status updates to CLIENT Product Owner

2. **Accelerated Response Times**:
   - **Critical defects**: 1-hour response time (vs. standard 2-hour)
   - **High defects**: 2-hour response time (vs. standard 4-hour)
   - Extended support hours: Mon-Fri, 8am-7pm ET (vs. standard 9am-6pm)

3. **Dedicated Support Standby**:
   - At least one senior developer and one QA resource designated as "on-call" for rapid response
   - Technical Lead available for escalation and architectural decisions

4. **Frequent Check-Ins**:
   - Daily standup with CLIENT Product Owner (15 minutes) to review overnight incidents, defects, and user feedback
   - Weekly Hypercare Review meeting to assess stability trends and determine if early exit from Hypercare is appropriate

### 2.4 Impact of Hypercare on Development Velocity

**During Hypercare, development velocity for the next version will be reduced by approximately 25-40%** due to:
- Developer time allocated to monitoring, log review, and incident response
- QA time allocated to validating production defect fixes
- Context switching between support and development work

**CLIENT Expectations**:
- CLIENT should expect slower progress on new feature development during Hypercare windows
- Orases will clearly communicate Hypercare periods in advance and adjust sprint commitments accordingly
- If CLIENT requires sustained development velocity during Hypercare, additional developer resources may be required (change order)

### 2.5 Hypercare Exit Criteria

Hypercare period may be **shortened or extended** based on production stability:

**Early Exit** (before standard duration):
- Zero Critical or High defects reported for 5 consecutive business days
- Application performance metrics within acceptable thresholds
- User adoption proceeding smoothly with no major friction points
- Mutual agreement between Orases and CLIENT

**Extension** (beyond standard duration):
- Recurring Critical or High defects requiring multiple fixes
- Performance degradation or scalability issues under production load
- Integration instability with Duke Energy backend systems
- CLIENT requests extended Hypercare due to business risk

**Exit Decision**: Orases Product Manager and CLIENT Product Owner will jointly decide Hypercare exit based on objective stability metrics.

---

## 3. Production Support SLAs (Post-Hypercare)

### 3.1 Standard Production Support Hours

**Business Hours**: Monday-Friday, 9am-6pm ET

**After-Hours Support**:
- **Critical defects only**: On-call developer available for emergency response
- **Response Time**: Within 4 hours of notification (24/7)
- **Escalation**: CLIENT notifies Orases via designated emergency contact (phone + email)

**Holidays and Weekends**:
- No standard support coverage
- Critical defects may be addressed on best-effort basis with prior arrangement

### 3.2 Response and Resolution SLAs (Post-Hypercare)

*(Repeated from Section 1.5.7 for clarity; same SLAs apply)*

#### Response Time SLAs

**Response Time** = Time from defect reported until Orases acknowledges and begins investigation

| Severity | Response Time | Availability |
|----------|---------------|--------------|
| **Critical** | **2 hours** | Business hours: Mon-Fri, 9am-6pm ET<br>After-hours: 4 hours (emergency contact) |
| **High** | **4 business hours** | Business hours: Mon-Fri, 9am-6pm ET |
| **Medium** | **1 business day** | Business hours: Mon-Fri, 9am-6pm ET |
| **Low** | **3 business days** | Business hours: Mon-Fri, 9am-6pm ET |

#### Resolution Time Targets

**Resolution Time** = Time from defect reported until fix is deployed to production

| Severity | Resolution Target | Notes |
|----------|-------------------|-------|
| **Critical** | **24 hours** | Hotfix deployed immediately after validation. May require emergency deployment outside normal change windows. Orases will coordinate with CLIENT for emergency change approval. |
| **High** | **3-5 business days** | Prioritized in current sprint. If discovered late in sprint, may be completed in next sprint with CLIENT approval. |
| **Medium** | **1-2 weeks** | Scheduled in upcoming sprint based on priorities. |
| **Low** | **Next planned release** | Added to backlog and prioritized with other work. No specific timeline guaranteed. |

**Important**: Resolution targets are **best effort commitments**. Actual resolution time depends on:
- Root cause complexity and scope of required changes
- Availability of CLIENT for testing and approval
- Dependency on third-party systems (Duke Energy APIs, contractor portals, etc.)
- Availability of deployment windows per CLIENT change control policies

---

## 4. Production Support Effort: Tracking and Billing

### 4.1 Production Support Effort Classification

All production support work falls into one of three categories:

| Category | Definition | Examples | Billing Treatment |
|----------|------------|----------|-------------------|
| **Warranty Defects** | Defects in features delivered and accepted per Section 1.4 that do not meet acceptance criteria or introduce regressions | - Feature X fails to save data as specified in PRD<br>- Bug introduced by recent deployment<br>- Regression in previously working functionality | **Included in SOW** - No additional billing. Orases responsibility to fix at no charge per Section 1.4 warranty. |
| **Production Support** | Routine support tasks, minor enhancements, and defects outside warranty scope | - Performance tuning requests<br>- Content updates or configuration changes<br>- User training or troubleshooting<br>- Defects in features after warranty period expires | **Billable at T&M rates** - Charged separately from SOW deliverables. Requires CLIENT approval via change order. |
| **Enhancement Requests** | New features or functional changes beyond original acceptance criteria | - Add new data fields to home inventory<br>- Integrate with new third-party service<br>- Modify workflow per business process change | **Requires Change Order** - Treated as new scope per Section 1.2. Estimated, prioritized, and approved separately. |

### 4.2 How Production Support Impacts Development Capacity

**Scenario 1: Low Production Support Load** (< 10% of sprint capacity)
- **Impact**: Minimal impact to planned development
- **Example**: 1-2 Low/Medium defects per sprint, resolved within normal workflow
- **Billing**: Warranty defects = no charge; routine support = billed separately if CLIENT requests it

**Scenario 2: Moderate Production Support Load** (10-25% of sprint capacity)
- **Impact**: Noticeable reduction in new feature delivery
- **Example**: 1 High defect requiring 15-20 hours to resolve + several Medium defects
- **Orases Action**: Adjust sprint commitments to reflect reduced capacity; communicate timeline impact to CLIENT
- **Billing**: Warranty defects = no charge; additional support beyond warranty = billed separately

**Scenario 3: High Production Support Load** (> 25% of sprint capacity)
- **Impact**: Significant reduction in new feature delivery; may require dedicated support sprint
- **Example**: Critical production outage requiring 40+ hours of investigation and resolution + multiple High defects
- **Orases Action**:
  - Immediately notify CLIENT of capacity impact and timeline implications
  - Propose dedicated "stabilization sprint" with reduced new feature work
  - Recommend adding temporary support resources if sustained development velocity is required
- **Billing**: Warranty defects = no charge; CLIENT may opt to fund additional resources via change order to maintain development velocity

### 4.3 Production Support Time Tracking

**Orases Commitment**: All production support effort will be tracked separately from planned development work to provide transparency into capacity allocation.

**Tracking Mechanism**:
- Jira tickets tagged with "Production Support" label
- Time logged separately for:
  - Warranty defect resolution (no charge)
  - Non-warranty production support (billable if CLIENT approves)
  - Enhancement requests (change order)

**Reporting**:
- **Sprint Status Reports** (bi-weekly): Include production support effort summary:
  - Total hours spent on production support
  - Breakdown by severity and category (warranty vs. billable)
  - Impact on planned sprint commitments
- **Monthly Stakeholder Reviews**: Review production support trends and discuss capacity planning for upcoming months

### 4.4 Production Support Budget Planning

**Recommended Approach**:
- **Option 1: Dedicated Support Retainer**:
  - CLIENT pre-purchases a monthly block of production support hours (e.g., 40 hours/month)
  - Used for non-warranty support tasks, performance tuning, minor enhancements
  - Provides predictable monthly cost and guaranteed support capacity
  - Unused hours may roll over (up to 1 month) or be forfeited per agreement

- **Option 2: Ad-Hoc Support Billing**:
  - CLIENT is billed monthly for actual production support hours used
  - Requires approval for each support task via email or change request
  - More flexible but less predictable budgeting

**Discussion**: Parties will determine preferred approach during Project Kickoff or prior to MVP go-live.

---

## 5. Production Incident Response Workflow

### 5.1 Incident Notification

**CLIENT Reporting Channels**:
1. **Standard (Business Hours)**: Log defect in Trello with severity designation
2. **Urgent (Critical Defects)**:
   - Email: [Orases designated support email]
   - Phone: [Orases emergency contact - to be provided at kickoff]
   - Include: Severity, description, steps to reproduce, business impact, screenshots/logs

**Orases Monitoring**:
- Proactive monitoring of application error logs and performance metrics
- Orases may identify and report incidents before CLIENT notification

### 5.2 Incident Triage and Classification

**Orases Response** (within SLA response time):
1. Acknowledge receipt of incident report
2. Confirm severity classification (or escalate/de-escalate based on investigation)
3. Assign to appropriate developer based on severity and expertise
4. Provide initial assessment and estimated resolution timeline

**Severity Validation**:
- If Orases assesses severity differently than CLIENT, Orases will explain rationale and seek CLIENT agreement
- In case of disagreement, Orases will treat incident at the **higher severity level** until resolution

### 5.3 Incident Investigation and Resolution

**Investigation Phase**:
- Developer reproduces issue in staging/development environment
- Identifies root cause and scope of impact
- Determines fix approach and estimates effort required

**Fix Development**:
- Code changes implemented with focus on minimal risk
- Unit tests added to prevent regression
- Peer code review completed

**QA Validation**:
- QA verifies fix in staging environment
- Regression testing to ensure no unintended side effects
- For Critical/High defects: CLIENT UAT in staging before production deployment

**Deployment**:
- Hotfix deployed to production per deployment process
- For Critical defects: Emergency deployment may occur outside normal change windows with CLIENT approval
- Deployment communication sent to CLIENT with release notes

**Post-Deployment Verification**:
- Orases monitors production logs and error rates post-deployment
- CLIENT verifies issue resolution from user perspective
- Defect marked Closed after mutual confirmation

### 5.4 Incident Communication Cadence

| Severity | Update Frequency | Format |
|----------|------------------|--------|
| **Critical** | Every 4 hours until resolved | Email or Slack to CLIENT Product Owner + Stakeholders |
| **High** | Daily | Email to CLIENT Product Owner |
| **Medium** | Every 2-3 days | Included in sprint status report or ad-hoc email |
| **Low** | Weekly | Included in sprint status report |

**Escalation**: If resolution is delayed beyond SLA target, Orases PM will escalate to CLIENT Product Owner with revised timeline and explanation.

---

## 6. Post-Incident Review (Critical Defects Only)

### 6.1 Post-Mortem Process

For **Critical defects**, Orases will conduct a **post-incident review** (post-mortem) within 5 business days of resolution.

**Post-Mortem Objectives**:
1. Document root cause and contributing factors
2. Identify prevention measures to avoid recurrence
3. Assess response effectiveness and identify process improvements
4. Update monitoring, testing, or documentation as needed

**Post-Mortem Deliverable**:
- Written summary shared with CLIENT Product Owner
- Includes:
  - Incident timeline and impact summary
  - Root cause analysis
  - Immediate fix implemented
  - Long-term prevention measures (if applicable)
  - Process improvements identified

**CLIENT Participation**:
- Optional but encouraged for high-impact incidents
- Provides opportunity for feedback on incident response and communication

---

## 7. Production Support Transition Planning

### 7.1 Knowledge Transfer and Documentation

**Prior to MVP Go-Live**, Orases will deliver:

1. **Production Support Runbook**:
   - Common issues and troubleshooting steps
   - Deployment procedures and rollback process
   - Monitoring and alerting configuration
   - Emergency contact information and escalation paths

2. **Technical Documentation**:
   - System architecture diagrams
   - API integration specifications
   - Database schema and data flow documentation
   - Security and access control configuration

3. **Training Sessions**:
   - Live walkthrough of support processes with CLIENT IT team (if CLIENT plans to take over support)
   - Q&A session to address operational questions

### 7.2 Long-Term Support Options

**Post-Project Completion** (after all deliverables in Sections 1.1-1.3 are complete):

- **Option 1: Ongoing Orases Support**:
  - Separate SOW for ongoing maintenance, support, and enhancements
  - Typically structured as monthly retainer or dedicated support team
  - Ensures continuity and institutional knowledge retention

- **Option 2: CLIENT In-House Support**:
  - Orases provides knowledge transfer and documentation
  - CLIENT IT team assumes responsibility for production support
  - Orases available for consulting or escalation on as-needed basis

- **Option 3: Hybrid Model**:
  - CLIENT handles Tier 1 support (user questions, minor issues)
  - Orases handles Tier 2/3 support (complex defects, enhancements, architecture changes)
  - Structured as support retainer with defined SLAs

**Discussion**: Long-term support model will be determined collaboratively as MVP go-live approaches.

---

## 8. Key Takeaways and Summary

### 8.1 Core Principles

1. **Production Stability is Priority 1**: Critical and High production defects take precedence over planned feature development
2. **Transparency in Capacity Impact**: Orases will clearly communicate when production support reduces development velocity
3. **Warranty vs. Billable Support**: Defects within warranty are covered; routine support and enhancements outside warranty scope are billed separately
4. **Hypercare Provides Safety Net**: Intensive support immediately post-release ensures smooth production transition
5. **Proactive Communication**: Frequent updates during incidents and transparent reporting of support effort

### 8.2 CLIENT Expectations

**What CLIENT Can Expect from Orases**:
- Rapid response to production incidents per SLA
- Transparent communication about capacity impact and timeline implications
- Detailed tracking and reporting of production support effort
- Proactive monitoring and issue identification during Hypercare
- Post-incident analysis and prevention measures for Critical defects

**What Orases Needs from CLIENT**:
- Clear severity designation when reporting defects
- Timely availability for UAT validation of Critical/High defect fixes
- Reasonable expectations about development velocity during high support periods
- Collaborative discussion about capacity planning and support budgeting
- Approval for emergency deployments when required

### 8.3 Open Questions for Discussion

The following topics should be addressed during **Project Kickoff** or prior to **MVP go-live**:

1. **Production Support Budget**: Does CLIENT prefer dedicated retainer model or ad-hoc billing?
2. **After-Hours Support**: Does CLIENT require 24/7 coverage for Critical defects, or is 4-hour response sufficient?
3. **Change Control Process**: What is Duke Energy's process for approving emergency production deployments?
4. **Monitoring and Alerting**: What production monitoring tools does Duke Energy use? Should Orases integrate with existing tools?
5. **Long-Term Support Strategy**: What is CLIENT's preference for post-project support (Orases, in-house, or hybrid)?
6. **Hypercare Staffing**: Should Orases plan for dedicated Hypercare resources (at additional cost) or absorb Hypercare within existing team capacity?

---

## 9. Integration with Existing SOW Sections

This Hypercare and Production Support Model supplements existing SOW sections:

- **Section 1.2 (Change Request Process)**: Production enhancements and non-warranty support follow change request workflow
- **Section 1.4 (Acceptance Criteria and Warranty)**: Defines warranty scope; production defects within warranty are Orases responsibility
- **Section 1.5.6 (SLA Model and Defect Severity Matrix)**: Provides detailed SLA definitions; this document expands on operational context
- **Section 2.2 (Client Responsibilities)**: CLIENT must provide timely defect reports and UAT participation
- **Section 2.3 (Consultant Responsibilities)**: Orases provides production support per SLAs and communicates capacity impact

---

**End of Hypercare and Production Support Model Document**

---

## Proposed Next Steps

1. **Review and Discuss**: CLIENT reviews this document and provides feedback on approach and open questions
2. **Refine During Kickoff**: Finalize production support model, Hypercare staffing, and budget approach during Project Kickoff
3. **Integrate into SOW**: Incorporate approved sections into final SOW Section 1.5
4. **Define Support Contacts**: Designate emergency contacts and communication channels prior to MVP go-live
5. **Develop Support Runbook**: Create detailed production support runbook as part of pre-launch deliverables
