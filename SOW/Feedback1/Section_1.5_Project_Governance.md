# Section 1.5 Project Governance

This section defines the operational framework, communication protocols, roles and responsibilities, and quality assurance processes that will govern the execution of this project.

---

## 1.5.1 Methodology

Orases will employ a **Hybrid Agile** approach combining structured requirements documentation with iterative development cycles, ensuring both rigorous planning and adaptive flexibility.

### Development Lifecycle

**Phase 1: Requirements Definition (PRD)**
- **Owner**: Product Manager/Business Analyst
- **Purpose**: Document the scope, business requirements, functional specifications, acceptance criteria, etc.
- **Deliverable**: Product Requirements Document (PRD) defining WHAT will be built and WHY
- **Client Involvement**: Review cycles with CLIENT Product Owner and stakeholders for validation and approval

**Phase 2: Technical Planning (TRD)**
- **Owner**: Development Team Lead
- **Purpose**: Validate technical feasibility, define architecture, identify constraints and dependencies
- **Deliverable**: Technical Requirements Document (TRD) defining HOW the feature will be built
- **Alignment Checkpoint**: Ensure PRD requirements are achievable; surface technical risks before commitment

**Phase 3: Backlog Creation & Prioritization**
- **Owner**: Product Manager and Development Team (collaborative)
- **Purpose**: Break approved PRD/TRD into actionable Epics and Jira tickets
- **Deliverable**: Prioritized Development Backlog with estimated work units
- **Client Involvement**: CLIENT Product Owner approves priorities

**Phase 4: Iterative Development**
- **Sprint Duration**: 2-week sprints
- **Sprint Activities**: Sprint planning, daily standups, development, testing, sprint status updates
- **Incremental Delivery**: Orases delivers working software for CLIENT review when features reach a demonstrable state. For larger features estimated across multiple sprints (e.g., a 3-sprint feature), sprint demos may not occur after each sprint. CLIENT receives written status updates after every sprint regardless of demo cadence.
- **Demo Cadence**: Sprint demos scheduled when meaningful functionality is complete and ready for CLIENT review, typically aligned with completion of Epics or significant milestones

### Agile Ceremonies

| Ceremony | Frequency | Duration | Participants | Purpose |
|----------|-----------|----------|--------------|---------|
| **Sprint Planning** | Every 2 weeks (start of sprint) | 2 hours | Orases PM, Dev Team | Review backlog, commit to sprint scope |
| **Daily Standup** | Daily | 15 minutes | Orases Team | Sync on progress, blockers, and next steps |
| **Sprint Demo** | As needed (when features reach demonstrable state) | 1 hour | Orases team, CLIENT Product Owner, Stakeholders | Demonstrate completed work, gather feedback |
| **Backlog Refinement** | Weekly | 1 hour | Orases Team | Clarify upcoming stories, refine estimates |

**Note**: Sprint Planning and Backlog Refinement are internal Orases activities focused on technical breakdown and sprint execution. CLIENT participates in separate prioritization and alignment meetings (see below).

### Client Prioritization and Alignment Meetings

**Purpose**: CLIENT participates in dedicated meetings separate from sprint ceremonies to prioritize high-level requirements and deliverables. These meetings focus on **what to build and in what order**, not the technical execution details.

**Scope of Prioritization**:
- High-level feature prioritization (which Epics or major deliverables to tackle next)
- Business value alignment and strategic sequencing
- Review of PRDs and approval of scope before development begins
- Alignment on deliverable priorities per Section 1.2

**After prioritization is established**, work flows into Orases' traditional development lifecycle:
1. PRD creation (Phase 1)
2. TRD creation (Phase 2)
3. Backlog breakdown (Phase 3)
4. Sprint execution (Phase 4)

**Cadence - Variable by Project Phase and Client Capacity**:

| Project Phase | Meeting Frequency | Rationale |
|---------------|-------------------|-----------|
| **Discovery & Analysis** | Weekly or bi-weekly | High frequency during requirements gathering, validation, and PRD reviews. CLIENT input critical for scope definition. |
| **Active Development** | Weekly or as needed | Lower frequency during heavy development cycles. Orases executes against approved backlog with periodic check-ins. |
| **Pre-Release & Testing** | Bi-weekly | Increased frequency for UAT coordination, acceptance testing, and launch preparation. |

**Important Note on Cadence**:
The actual meeting frequency will also depend on CLIENT capacity and operational realities, including:
- CLIENT availability and ability to schedule meetings with key stakeholders
- Speed at which CLIENT can deliver on their responsibilities (PRD reviews, approvals, SME input, requirements clarification)
- CLIENT's ability to assemble the right decision-makers and subject matter experts
- CLIENT's internal prioritization and competing business demands
- Time required for CLIENT to gather necessary information or make decisions

Parties acknowledge that meeting cadence is a collaborative effort requiring mutual availability and commitment. Orases will propose meeting schedules aligned with project phase needs, and CLIENT will work in good faith to accommodate prioritization discussions in a timely manner. If CLIENT capacity constraints impact the ability to maintain the proposed cadence, Parties will discuss timeline implications and adjust expectations accordingly.

**Meeting Format**:
- **Duration**: 1-2 hours
- **Participants**: Orases Team, CLIENT Product Owner, CLIENT Stakeholders/SMEs
- **Agenda**:
  - Review completed deliverables since last meeting
  - Review upcoming PRDs or feature proposals
  - Prioritize next set of high-level deliverables
  - Address risks, dependencies, or strategic changes
  - Confirm priorities for upcoming development cycles

**Flexibility**:
- Cadence may be adjusted by mutual agreement based on project needs
- Ad-hoc prioritization meetings may be scheduled for urgent business needs
- CLIENT may request re-prioritization at any time per Section 1.2

---

## 1.5.2 Communication Model and Cadence

### Regular Status Communications

| Communication | Frequency | Format | Owner | Recipients | Purpose |
|---------------|-----------|--------|-------|------------|---------|
| **Sprint Status Report** | Every 2 weeks (end of sprint) | Written (email/Confluence) | Orases PM | CLIENT Product Owner, Stakeholders | Progress update, completed work, upcoming work, risks, blockers |
| **Sprint Demo** | As needed (when features complete) | Meeting (1 hour) | Orases Team | CLIENT Product Owner, Stakeholders | Live demonstration of working features |
| **Monthly Stakeholder Review** | Monthly | Meeting (1 hour) | Orases Team | CLIENT Product Owner, Executive Sponsors, Orases Leadership | Strategic alignment, milestone progress, budget/timeline status, major decisions |
| **Ad-Hoc Technical Sync** | As needed | Meeting or Emails | Orases/CLIENT Team | CLIENT/Orases Team | Integration questions, technical blockers, architecture decisions |

### Escalation Path

**Level 1: Team-Level Issues**
- **Handler**: Orases Project Manager and CLIENT Product Owner
- **Response Time**: Within 1 business day
- **Examples**: Scope clarifications, minor blockers, resource scheduling

**Level 2: Project-Level Issues**
- **Handler**: Orases Product Manager and CLIENT Project Sponsor
- **Response Time**: Within 2 business days
- **Examples**: Significant scope changes, technical feasibility concerns, timeline impacts

**Level 3: Executive-Level Issues**
- **Handler**: Orases Leadership and CLIENT Executive Sponsor
- **Response Time**: Within 3 business days
- **Examples**: Budget overruns, critical path delays, contractual disputes, major risk materialization

### Communication Tools

- **Project Management**: Jira (Orases Team) and Trello (Client) (backlog, sprint tracking, defect management)
- **Documentation**: Confluence (requirements, technical specs, meeting notes, decisions)
- **Real-Time Communication**: Slack (dedicated project channel) or Microsoft Teams
- **Video Conferencing**: Google Meet or Microsoft Teams
- **Code Repository**: GitHub (version control, code reviews, CI/CD)

---

## 1.5.3 Key Roles and Resource Allocations

### Orases Team Structure

**Product Manager**
- **Name**: [To be designated at kickoff]
- **Allocation**: Available as needed
- **Responsibilities**:
  - Own product strategy, and account strategy, and technical leadership
  - Manage CLIENT relationship, expectations, and approvals
  - Lead requirements elicitation from CLIENT stakeholders and SMEs
  - Produce clear documentation and materials
  - Guide risk management and approach decisions
  - Align business strategy and roadmap with delivery execution
  - Support development team through technical guidance and code review
  - Primary escalation point for CLIENT
  - Respond to CLIENT inquiries within 2 business days per Section 2.3

**Project Manager**
- **Name**: [To be designated at kickoff]
- **Allocation**: 15-20 hours/week (varies by project phase)
- **Responsibilities**:
  - Manage project budget, tracking spend and projections
  - Own resourcing and scheduling to meet milestones
  - Coordinate tasks, meetings, documentation, and internal systems
  - Partner with Product Manager on day-to-day CLIENT collaboration and advocacy
  - Deliver status reports and communications
  - Track risks, dependencies, and action items

**Business Analyst**
- **Name**: [To be designated at kickoff]
- **Allocation**: 15-20 hours/week (varies by project phase)
- **Responsibilities**:
  - Lead requirements elicitation from CLIENT stakeholders and SMEs
  - Ensure proposed solutions align with business needs
  - Produce clear documentation and materials
  - Define, prioritize, and refine scope and backlog items
  - Coordinate UAT and acceptance testing

**Note on PRD Creation**: The creation and maintenance of Product Requirements Documents (PRDs) and internal team alignment activities may be a shared responsibility between the Product Manager and Business Analyst, depending on skillset match and capacity. The role assignment will be determined based on project needs and team availability.

**Lead Developer / Technical Lead**
- **Name**: [To be designated at kickoff]
- **Allocation**: 40 hours/week
- **Responsibilities**:
  - Design the solution architecture
  - Create and maintain TRDs and technical documentation
  - Lead SDLC activities (backlog grooming, estimation, sprint planning, task assignments)
  - Contribute directly to development
  - Lead code reviews and ensure code quality
  - Create and maintain developer onboarding documentation
  - Hold leadership and management accountability for the development function
  - Collaborate with CLIENT IT on API integration and infrastructure
  - Validate technical feasibility of requirements

**Senior/Mid-Level Developers**
- **Team Size**: 2-4 developers (varies by project phase)
- **Allocation**: 40 hours/week per developer
- **Responsibilities**:
  - Implement features per sprint commitments
  - Write unit and integration tests
  - Participate in code reviews
  - Document technical implementation
  - Collaborate with QA on defect resolution

**QA Lead**
- **Team Size**: 1-2 QA resources (varies by project phase)
- **Allocation**: 20-40 hours/week (increases during testing phases)
- **Responsibilities**:
  - Create test plans from acceptance criteria
  - Validate that requirements are testable within scope and timeline
  - Execute testing throughout the SDLC
  - Log and track defects in Jira; monitor CLIENT-reported defects from Trello
  - Validate defect fixes and retest
  - Coordinate with CLIENT for UAT participation
  - Sign off on quality gates before release

**UX/UI Designer**
- **Allocation**: 10-20 hours/week (primarily during analysis and design phases)
- **Responsibilities**:
  - Ensure user experience aligns with business goals and user needs
  - Create flows, wireframes, and prototypes
  - Advocate for user needs through research and testing
  - Conduct usability validation with CLIENT stakeholders
  - Maintain design system and component library
  - Collaborate with developers on implementation fidelity


### Duke Energy Team (CLIENT Responsibilities)

**CLIENT Product Owner** (Required - per Section 2.2)
- **Responsibilities**:
  - Provide timely decisions and feedback on requirements
  - Review and approve PRDs before development begins
  - Prioritize Development Backlog per Section 1.2
  - Coordinate UAT and provide acceptance/rejection per Section 1.4
  - Serve as primary liaison to CLIENT stakeholders and SMEs

**CLIENT Technical Lead / Integration Liaison**
- **Responsibilities**:
  - Provide API documentation and integration specifications
  - Grant access to sandbox/development environments
  - Support troubleshooting of integration issues
  - Coordinate with CLIENT IT security and infrastructure teams

**Subject Matter Experts (SMEs)**
- **Roles**: Operations, Customer Service, Contractor Management, Billing, Legal/Compliance
- **Responsibilities**:
  - Validate business requirements and workflows
  - Provide domain expertise during requirements sessions
  - Participate in UAT for relevant features
  - Review and approve customer-facing content and communications

**Executive Sponsor / Project Sponsor**
- **Responsibilities**:
  - Attend monthly stakeholder reviews
  - Provide strategic direction and decision-making authority
  - Remove organizational blockers
  - Approve major scope or budget changes

---

## 1.5.4 Resource Substitution and Replacement Process

### Notification Requirements

**For Key Roles** (Product Manager, Project Manager, Technical Lead):
- Orases shall provide **written notice to CLIENT Product Owner and PROJECT Sponsor at least 7 calendar days in advance** of any planned resource change
- For unplanned changes (illness, emergency), Orases shall notify CLIENT within 1 business day

**For Non-Key Roles** (Developers, Designers, DevOps):
- Orases may substitute resources without prior approval, provided skill level and productivity are maintained
- Orases shall document substitutions in sprint status reports

---

## 1.5.5 Quality Assurance Process

Orases employs a **continuous testing approach** integrated throughout the development lifecycle to ensure quality at every stage.

### Testing and Quality Activities

**Development Phase**:
- Developers write unit tests for business logic and critical functionality
- Peer code reviews conducted before QA handoff

**QA Testing Phase**:
- QA creates and executes test cases based on PRD/TRD requirements
- Integration testing validates end-to-end workflows
- Regression testing ensures no unintended impacts to existing functionality

**User Acceptance Testing (UAT)**:
- CLIENT Product Owner and SMEs validate features in staging environment
- UAT test cases defined during PRD phase
- Orases facilitates UAT sessions and incorporates feedback
- CLIENT provides formal acceptance per Section 1.4

---

## 1.5.6 SLA Model and Defect Severity Matrix

### Defect Severity Definitions

Defects will be categorized by severity to prioritize resolution efforts and set response expectations.

| Severity | Definition | Examples | Impact |
|----------|------------|----------|--------|
| **Critical** | System is unusable or major functionality is completely broken. Data loss or security vulnerability present. Affects all users. No workaround available. | - Application crashes on launch<br>- Database corruption<br>- Payment processing failure<br>- Security vulnerability exposing customer data<br>- Critical API integration failure preventing service booking | Production blocker; immediate attention required |
| **High** | Major feature is broken or significantly impaired. Affects many users. Workaround is difficult or impractical. | - Service booking fails for specific customer segment<br>- Home inventory data not saving<br>- HPP enrollment process broken<br>- Admin portal login issues<br>- Contractor matching algorithm fails | Major user impact; high priority resolution |
| **Medium** | Feature is partially broken or behaves incorrectly. Affects some users. Reasonable workaround exists. | - UI rendering issue on specific device<br>- Validation error message unclear<br>- Search returns incorrect results intermittently<br>- Notification delays<br>- Minor data display errors | Moderate user impact; scheduled resolution |
| **Low** | Minor issue with minimal impact. Cosmetic or edge case. Workaround is easy. | - Typo in label or message<br>- Minor UI alignment issue<br>- Non-critical error in logs<br>- Edge case validation missing<br>- Feature enhancement or "nice to have" | Minimal impact; backlog for future sprint |

### Defect Response and Resolution SLAs

SLAs apply to defects discovered **in production environments or during UAT**. Defects found during development and QA testing are handled within normal sprint workflows.

#### Response Time SLAs

**Response Time** = Time from defect reported until Orases acknowledges and begins investigation

| Severity | Response Time | Availability |
|----------|---------------|--------------|
| **Critical** | **2 hours** | Business hours: Mon-Fri, 9am-6pm ET |
| **High** | **4 business hours** | Business hours: Mon-Fri, 9am-6pm ET |
| **Medium** | **1 business day** | Business hours: Mon-Fri, 9am-6pm ET |
| **Low** | **3 business days** | Business hours: Mon-Fri, 9am-6pm ET |

#### Resolution Time Targets

**Resolution Time** = Time from defect reported until fix is deployed to production (or ready for deployment per CLIENT approval)

| Severity | Resolution Target | Notes |
|----------|-------------------|-------|
| **Critical** | **24 hours** | Hotfix deployed immediately after validation. May require emergency deployment outside normal change windows. |
| **High** | **3-5 business days** | Prioritized in current sprint. If discovered late in sprint, may be completed in next sprint with CLIENT approval. |
| **Medium** | **1-2 weeks** | Scheduled in upcoming sprint based on priorities. |
| **Low** | **Next planned release** | Added to backlog and prioritized with other work. No specific timeline guaranteed. |

**Note**: Resolution targets are **best effort commitments** based on typical defect complexity. Actual resolution time depends on defect root cause, availability of resources, and CLIENT approval for changes. Orases will provide regular updates on resolution progress for High and Critical defects.

### Defect Workflow

1. **Defect Reported**:
   - **Orases Team** (QA, developers): Defects logged in **Jira** with severity, steps to reproduce, expected vs. actual behavior, screenshots/logs
   - **CLIENT**: Defects logged in **Trello** with same information
   - **Note**: Jira is used for internal backlog management; Trello is used for CLIENT alignment and communication
2. **Triage**: Orases PM and Tech Lead review and confirm severity classification within SLA response time. CLIENT-reported defects from Trello are reviewed and corresponding Jira tickets created for internal tracking.
3. **Assignment**: Developer assigned based on severity and availability
4. **Investigation**: Root cause identified and fix approach determined
5. **Fix Development**: Code changes implemented, unit tested, and peer reviewed
6. **QA Validation**: QA verifies fix and runs regression tests
7. **CLIENT Validation** (for High/Critical defects): CLIENT validates fix in staging before production deployment
8. **Deployment**: Fix deployed to production per deployment process
9. **Verification**: Defect marked Closed in both Jira (internal) and Trello (CLIENT visibility) after production verification
10. **Post-Mortem** (for Critical defects): Orases conducts post-mortem to identify prevention measures

### Production Support Model

**During Active Development** (Sections 1.1-1.3):
- Orases provides defect support as described above for features delivered and accepted per Section 1.4
- Production support hours: **Business hours (Mon-Fri, 9am-6pm ET)** with on-call coverage for Critical defects

**Post-Go-Live Warranty Period**:
- If CLIENT requires extended warranty support beyond Section 1.4 acceptance, terms will be defined separately
- Ongoing maintenance and support beyond project completion require a separate SOW per Section 1.3

---

## 1.5.7 Governance Review and Adaptation

This governance model will be reviewed and refined during the **Project Kickoff** to ensure alignment with CLIENT preferences and organizational culture.

**Areas for Refinement During Kickoff**:
- Confirmation of named key resources (Section 1.5.3)
- Communication preferences and meeting schedules (Section 1.5.2)
- Customization of defect severity definitions for CLIENT context (Section 1.5.6)
- Integration with CLIENT's existing project governance frameworks

**Ongoing Governance Improvement**:
- Sprint Retrospectives will include process improvement discussions
- Quarterly governance review with CLIENT Project Sponsor to assess effectiveness and identify adjustments
- Governance model is a living framework; parties agree to adapt collaboratively as project needs evolve

---

**End of Section 1.5 Project Governance**
