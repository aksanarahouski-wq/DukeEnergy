# Statement of Work #1

CLIENT: 	Duke Energy Business Services LLC
This Statement of Work #1 (“SOW”) effective as of February X, 2026 (“Effective Date”), by and between Duke Energy Business Services LLC as agent for and on behalf of Duke Energy Florida, LLC, Duke Energy Progress, LLC, Duke Energy Carolinas, LLC, Duke Energy Kentucky, Inc., Duke Energy Ohio, Inc., Duke
Energy Indiana, LLC, and Duke Energy One, Inc.  (“CLIENT” or “Duke Energy”) with its principal offices located at 525 South Tryon St., Charlotte, NC 28202 and Orases Consulting Corporation (“Orases” or “Consultant”) with its principal offices located at 5728 Industry Lane, Frederick, MD 21704, shall serve as SOW to the Master Consulting Services Agreement by and between CLIENT and Orases effective as of February X, 2026 (“Agreement”). All terms that are defined in the Agreement will have the same meaning when used in this SOW. Duke Energy and Orases may sometimes hereinafter be referred to individually as a “Party” or collectively as “the Parties.”  In the event of any conflict between the terms of this SOW and those of the Agreement, the terms of this SOW will control.
This SOW identifies certain specific Services and Deliverables to be provided by Orases in connection with the following project (“Project”): Residential Solutions (RS) Home Services and Warranty Application

---

## 01 Executive Summary

The Duke Energy Residential Solutions Home Services Mobile App project encompasses the development of an integrated customer-facing mobile application and supporting administrative backend system to modernize Duke Energy's home protection plan (HPP) services and expand into new revenue-generating markets. This dual-platform solution will serve 800K+ existing Duke/Piedmont customers with home protection plans while simultaneously creating a marketplace to acquire non-native customers and grow ad-hoc service revenue
For Customers, the mobile app enables self-service to book both HPP-covered warranty services and ad-hoc services with transparent pricing, view real-time status updates on service requests from booking confirmation through completion, manage home inventories and HPP plan enrollments, receive intelligent maintenance reminders, and access complete service history documentation—transforming the current phone-only experience into an on-demand digital platform.
For Duke Operations, the administrative backend provides unified visibility and management capabilities across customer profiles, HPP plan enrollments and modifications, service request creation and contractor coordination, contractor network configuration, ad-hoc service catalog and pricing, home inventory data, maintenance reminders, exception handling, and comprehensive analytics—enabling cross-system data aggregation from Commerce CRM, Dynamics, and the app database with manual fallback workflows for business case validation and operational efficiency.

### 1.1 Project Scope

The following items shall be considered in or out of scope, respectively, and subject to change based on mutual agreement of both parties.

**In Scope:**

Features considered in scope of this statement of work shall include but not be limited to:
  - Home Protection Plan enrollment and management
  - Warranty and ad-hoc service scheduling
  - Duke Energy, Piedmont, and “Non-Native” customers
  - Home inventory management and maintenance reminders
  - Aggregation of data from multiple existing Duke Energy systems
  - Consumption of data sources provided by Duke Energy IT via API endpoint
  - Backend management and configuration to support Duke Energy administrative tasks related to the above
  - Reporting capabilities related to the above

**Out of Scope:**

Features considered out of the scope of this statement of work shall include but not be limited to:
  - Commercial property support
  - Landlord/Property management features
  - Unlicensed trades
  - Direct payments between Duke Energy and third-party contractors

---

## 02 Services and Deliverables

Orases shall provide the following Services and Deliverables as part of the Project. Parties acknowledge that the Services and Deliverables may include, but are not limited to, those described in this Section 02, depending on updates from discoveries made during the Project and subsequent CLIENT-approved priorities.

### 2.1 Project Kick-off and Project Plan

Following execution of this SOW, Orases will conduct a project kickoff to align the Parties on Project objectives, delivery approach, governance, roles, and initial priorities. The kickoff will establish communication protocols, decision-making authority, and coordination processes to support effective collaboration throughout the Project.
Following the kickoff, Orases will develop and maintain a Project Plan reflecting the Parties’ current understanding of priorities, sequencing, and estimated timelines. The Project Plan may include high-level milestones, dependencies, feature roadmap, and resource assumptions as appropriate. The Parties acknowledge that the Project Plan is a living artifact and may be updated as discovery progresses, requirements are refined, and CLIENT priorities evolve. Any material impacts to scope, timeline, or budget will be communicated to CLIENT and addressed in accordance with the change management provisions of this SOW.

### 2.2 Analysis Activities

During Analysis Activities under this SOW, Orases will conduct continuous discovery with CLIENT's project team and, utilizing the Sales Reference Documents and Project Plan, will validate feasibility, finalize project scope and define requirements. Throughout the project, Analysis Activities may include, but are not limited to:

**Technical Validation:**

Workshops with Duke, business, and technical project teams
API availability assessment (Customer Validation, HPP Plans, Service Request Creation, Enrollment)
Integration complexity analysis (Commerce CRM, Dynamics CRM, Duke Data Fabric)
Security requirements review and compliance assessment
Infrastructure constraints and deployment environment evaluation
Performance and scalability requirements validation

**Requirements Refinement:**

Validation of features
Identification of technical constraints, blockers, and dependencies
Assessment of alternative approaches where original assumptions prove invalid
Prioritization workshops with technical and business stakeholders
Development of user flows, wireframes, and/or user stories
Continuous refinement of scope, timeline, and cost estimates

**Architecture and Design:**

Technical architecture design (frontend, backend, infrastructure)
Database schema design
API specifications and integration patterns
Security architecture and compliance framework
Abstraction layer design to minimize future rework
DevOps and deployment strategy

**Activity Outcomes:**

Clickable prototypes to illustrate key workflows, proposed user experience, and system behavior
Technical architecture documentation
Updated scope, timeline, and cost estimate based on discovery findings
Development Backlog with refined requirements
Ongoing risk assessmentmitigation strategies
Validation sessions with CLIENT stakeholders

### 2.3 Prioritization of Work

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks identified throughout the Analysis Activities.
Throughout the project, work for Section 2.4 (Design, Development, and Implementation) will begin once CLIENT has reviewed, approved, and prioritized the proposed work. CLIENT has final decision-making authority on priorities.
Priorities may be updated throughout the Project at CLIENT’s direction, and Orases will provide updated estimates regarding timeline, scope, or budget.
For prioritized work, Orases will provide good-faith estimates of effort based on information available at the time to support planning and prioritization in this time-and-materials engagement. Estimates are not guarantees and may evolve as discovery continues and requirements are further refined.
Orases will track actual effort against estimates and will provide ongoing visibility into progress, effort expended, and forecasted remaining work through regular project reporting. If Orases reasonably anticipates that actual effort for a prioritized work item, Epic, or Sprint will materially exceed the applicable estimate, Orases will notify CLIENT and provide context and options, which may include re-prioritization, scope adjustment, or continued execution at CLIENT’s direction.
No work under section 2.4 will begin until Orases provides a written estimate and CLIENT issues written approval for the relevant work package or Sprint. CLIENT may re-prioritize the Backlog at any time; Orases will promptly provide written impact (timeline, scope, budget).

### 2.4 Design, Development, and Implementation

Following CLIENT’s approval of priorities, Orases will proceed with design, development, testing, and implementation of the approved features. Activities may include, but are not limited to:
UX/UI design refining elements identified during the Analysis Phase
Front-end and back-end iterative development of features defined on Development Backlog
Integration with CLIENT systems or third-party services
System configuration and environment setup, including any hosting and configuration setup for third-party services Orases recommended and provided with this SOW.
QA testing, bug resolution, and deployment support
Documentation of system configuration, environment setup, deployment, and any other project processes established
Training for Duke project team on system configuration, environment setup, deployment, and any other project processes established
If hosting services are required, Orases and CLIENT will scope such services separately and execute one or more additional SOWs.

### 2.5 Hypercare (Post-Release Stabilization)

Following each Production Release, Parties shall plan for and Orases to provide a post-deployment stabilization period (“Hypercare”) to monitor performance, address defects, and ensure system stability.
Hypercare Period
- Hypercare shall begin upon Production deployment of each major Release.
- Hypercare shall continue for ten (10) calendar days unless otherwise agreed in writing by both Parties.
- Hypercare applies only to functionality included within the applicable Release scope.
Scope of Hypercare Services

**During Hypercare, Orases will:**

  - Monitor application health and deployment stability
  - Triage and remediate verified defects introduced in the applicable Release
  - Provide a prioritized response and resourced targets (Section 2.8.8 Service Hours and SLAs)
  - Participate in agreed-upon status checkpoints
Hypercare services will be performed by the same Orases project team assigned to the Services under this SOW. CLIENT acknowledges that allocation of team capacity toward Hypercare activities may affect project timelines and velocity, and all prioritization decisions and related timeline or budget impacts shall be governed by Section 2.3. Hypercare activities are part of the ongoing Services under this SOW and will be invoiced on a Time and Materials basis at the rates set forth herein. Following completion of the Hypercare Period, all ongoing services shall transition to Production Support as defined in Section 2.6.
identified during Hypercare, will address without additional cost to CLIENT. Billable Hypercare activities may include enhancements, configuration changes, monitoring, reporting, and other support tasks requested by CLIENT.

### 2.6 Production Support

Orases shall provide ongoing Production Support services for the duration of this SOW following the applicable Hypercare period. Production Support services will be performed by the same Orases project team assigned to the Services under this SOW. CLIENT acknowledges that allocation of team capacity toward support activities may affect project timelines and velocity, and all prioritization decisions and related timeline or budget impacts shall be governed by Section 2.3. All Production Support services are performed on a Time & Materials basis at the rates set forth in Section 4 of this SOW unless otherwise specified in a separate Support SOW.

### 2.7 Review Period, Acceptance

Deliverables received during the activities described in sections 2.2 and 2.4 shall be reviewed and either accepted or rejected in accordance with the following procedure: CLIENT shall have ten (10) business days after delivery of the applicable Deliverables (the “Review Period”) to review and test the Services and Deliverables. CLIENT will indicate acceptance or rejection of applicable Deliverables in writing. For clarity, mutual written acceptance includes e-mail confirmations between designated project managers.  Any Services or Deliverables not accepted or rejected in writing within the Review Period be deemed accepted
If Orases fails to deliver the Deliverable within the Acceptance Criteria and Duke Energy provides notice of rejection to Orases per the terms above, Orases shall have ten (10) Business Days upon rejection from Duke Energy to address gaps or provide a Response Plan to Duke Energy. Redelivery will occur within the agreed timeframe. Duke Energy shall have ten (10) Business Days to provide documented Acceptance or rejection.
If additional time is needed by either Party, written notification shall be provided to the receiving Party prior to the conclusion of the response requirements indicated above. In order for extension to be granted, it must be mutually agreed upon by the Parties.
If Orases materially fails to meet three (3) consecutive Sprints for reasons primarily attributable to Orases, CLIENT may, upon written notice, require one or more of the following at no additional cost (agreed to mutually):
(a) reallocation or augmentation of resources,
(b) revised delivery approach, or
(c) adjustment of billed sum/performance credit

#### 2.7.1 Acceptance Criteria for the Deliverables

Deliverables shall be evaluated for acceptance using the quality standards, defect severity definitions, and testing processes defined in Section 2.8 (Project Governance).

**Deliverables meet acceptance criteria when they:**

- Requirements Conformance:
- Substantially conform to requirements specified in the approved PRD, and Development Backlog as defined at CLIENT approval
- Achieve the core business objectives and user outcomes specified in the PRD
- Quality Standards (2.8.8 Defect Severity Matrix):
- Are free of Critical defects
- Are free of High-Severity defects
- Subject to 2.8.8. aggregation standard, Medium and Low severity defects do not block acceptance and will be added to the Development Backlog for prioritization per Section 2.3
- Testing and Validation (Section 2.8.7 Quality Assurance):
- Pass Orases’ internal quality procedures
- Complete User Acceptance Testing (UAT) with CLIENT Product Owner and Subject Matter Experts
- Validated in staging environment prior to production deployment
- If UAT identifies defects, gaps, or issues that prevent the Deliverable from meeting the Acceptance Criteria, CLIENT may reject the Deliverable or extend the Review Period as reasonably necessary to complete testing and validation
The Review Period shall be extended during periods in which UAT cannot reasonably be completed due to unresolved defects, environmental issues, incomplete Deliverables, or dependencies outside CLIENT’s control.
- Technical Requirements:
- Meet security and compliance requirements as established in the approved PRD/TRD
- Meet performance requirements as specified in the approved PRD/TRD
- Suitable for deployment to production environment in the intended infrastructure
- Documentation:
- Include required documentation as specified in the PRD/TRD (architecture diagrams, configuration guides, deployment procedures, or other artifacts as applicable)
- Substantial Conformance Standard:
- The Parties acknowledge that in agile/iterative development, some implementation details, edge cases, and integration specifics emerge during development as requirements are translated into working software. When Orases encounters scenarios not explicitly addressed in the approved PRD/TRD, Orases will:
- Notify CLIENT Product Owner of the scenario and impacts to timeline, scope, budget
- Propose a recommended approach consistent with industry best practices and the spirit of the requirements
- Document the approach and rationale
- Obtain CLIENT’s written approval of the proposed approach prior to implementation, provided that CLIENT has a reasonable opportunity to review and approve such documentation. Notwithstanding the foregoing, if a scenario materially blocks development progress and CLIENT approval cannot be obtained in time despite reasonable efforts, Orases may proceed with a reasonable interim solution consistent with industry best practices, subject to subsequent CLIENT review and approval.
- Decisions made in good faith to address unspecified scenarios constitute substantial conformance with requirements. If CLIENT prefers a different approach after review, modifications will be treated as enhancements and added to the Backlog for prioritization per Section 2.3, not grounds for rejection or non-acceptance.

### 2.8 Project Governance

This section describes the governance framework that will guide delivery of the Services, including methodology, communication, roles, quality practices, and issue management. The governance model is intended to provide transparency and structure while remaining adaptable as project needs evolve.

#### 2.8.1 CLIENT Prioritization and Alignment Meetings

Every work engagement begins with prioritization and alignment. CLIENT participates in dedicated meetings to prioritize high-level requirements and deliverables. These meetings focus on what to build and in what order, establishing the foundation for all development work.
- Purpose and Scope:
- High-level feature prioritization (which Epics or major deliverables to tackle next)
- Business value alignment and strategic sequencing
- Review of requirements documents and approval of scope before development begins
- Alignment on priorities per Section 2.3
- Meeting Format:
- Duration: 1-2 hours
- Participants: Orases Team, CLIENT Product Owner, CLIENT Stakeholders/SMEs (as needed)
- Agenda:
- Review completed deliverables since last meeting
- Review upcoming requirements or feature proposals
- Prioritize next set of high-level deliverables
- Address risks, dependencies, or strategic changes
- Confirm priorities for upcoming development cycles
- Cadence - Variable by Project Phase and CLIENT Capacity:

| Project Phase | Meeting Frequency | Purpose |
| --- | --- | --- |
| Discovery & Analysis | Weekly or bi-weekly | High frequency during requirements gathering, validation, and documentation reviews. CLIENT input critical for scope definition. |
| Active Development | Weekly or as needed | Lower frequency during heavy development cycles. Orases executes against approved backlog with periodic check-ins. |
| Pre-Release & Testing | Bi-weekly | Increased frequency for UAT coordination, acceptance testing, and launch preparation. |

#### 2.8.2 Methodology

Orases will employ an iterative delivery approach appropriate for a time-and-materials engagement. Work will be planned and executed in incremental cycles, allowing priorities and scope to be refined based on CLIENT feedback, emerging requirements, and business needs.
Development Lifecycle
- Phase 1: Requirements Definition
- Purpose: Document the scope, business requirements, functional specifications, technical feasibility, architecture, and acceptance criteria
- Deliverables:
- Product Requirements Document (“PRD”) defining WHAT will be built and WHY
- Technical Requirements Document (“TRD”) defining HOW the feature will be built
- CLIENT Involvement: Review cycles with CLIENT Product Owner and stakeholders for validation and approval
- Alignment Checkpoint: Ensure requirements are achievable; surface technical risks before commitment, align scope, budget and timeline
- Phase 2: Backlog Creation & Prioritization
- Purpose: Transition approved requirements into actionable work packages (“Work Package(s)”)
- Deliverable: Prioritized Development Backlog with estimated efforts
- CLIENT Involvement: CLIENT Product Owner approves priorities
- Phase 3: Iterative Development
- Incremental Delivery: Orases delivers working software for CLIENT review when features reach a demonstrable state. For larger features estimated across multiple sprints, sprint demos may not occur after each sprint. CLIENT receives written status updates after every sprint regardless of demo cadence.
- Sprint Duration: 2-week sprints
- Sprint Activities: Sprint planning, daily standups, development, testing, sprint status updates
- Note: Sprint Planning and Backlog Refinement are internal Orases activities focused on technical breakdown and sprint execution. CLIENT participates in separate prioritization and alignment meetings (see Section 2.8.1).
- Demo Cadence: Demos scheduled when meaningful functionality is complete and ready for CLIENT review, typically aligned with completion of Epics or significant milestones
- Phase 4: Deployment
- Approval: Upon completion of testing and with CLIENT approval, Orases will coordinate deployment of the applicable Release to the final Production environment “Production”.
- Version Control: Orases utilizes industry-standard version control and branching methodologies to manage releases and maintain prior stable versions.
- Rollback: In the event of a critical production issue attributable to the Release, Orases may perform a rollback to the most recent stable version, where technically feasible.

#### 2.8.3 Communication Model and Cadence

Orases will provide regular project communications to ensure visibility into progress, upcoming work, risks, and decisions required. Expected communications may include:

| Communication | Frequency | Format | Recipients | Purpose |
| --- | --- | --- | --- | --- |
| Sprint Status Report | Every 2 weeks (end of sprint) | Written (Email/Confluence) | CLIENT Product Owner, Stakeholders | Progress update, completed work, upcoming work, risks, blockers |
| Demo | As needed (when features complete) | Meeting (1 hour) | CLIENT Product Owner, Stakeholders | Live demonstration of working features |
| Monthly Stakeholder Meeting | Monthly | Meeting (1 hour) | CLIENT Product Owner, Executive Sponsors | Strategic alignment, milestone progress, budget/timeline status, major decisions |
| Ad-Hoc Technical Sync | As needed | Meeting or Emails | CLIENT/Orases Team | Integration questions, technical blockers, architecture decisions |

The specific meeting cadence and formats may vary by project phase and CLIENT availability and may be adjusted by mutual agreement.

#### 2.8.4 Key Roles and Resource Allocation

Orases will assign resources appropriate to the scope and complexity of the Project. Anticipated roles may include:
- Consultant Product Manager “Product Manager” – overall delivery accountability, CLIENT coordination, prioritization support (Key role)
- Project Manager – schedule, budget tracking, reporting, and risk coordination (Key Role)
- Business Analyst - Elicits and documents requirements, supports backlog refinement and prioritization, and coordinates UAT and acceptance activities.
- Technical Lead – solution architecture, technical oversight, code quality (Key Role)
- Developers and QA Resources – implementation and testing activities
- Product Designer – Design activities (as needed)
Note: For critical roles, Orases may identify named resources at or following project kickoff. Resource allocation levels are estimates and may fluctuate over time based on project needs and CLIENT priorities.

#### 2.8.5 Resource Substitution and Replacement

Orases may substitute project resources as needed to support continuity of delivery, provided that replacement resources have comparable skills and experience. Key role substitutions will be communicated to CLIENT in advance when reasonably practicable. Non-key role substitutions may occur without prior communication and will be reflected in project reporting. Unplanned substitutions due to illness, attrition, or other circumstances will be communicated promptly.

#### 2.8.6 Risk Management

Orases will actively identify, monitor, and communicate project risks, including those related to scope clarity, dependencies, CLIENT availability, and technical complexity. Material risks impacting timeline, cost, or delivery expectations will be surfaced to CLIENT and discussed collaboratively. Mitigation strategies may include re-prioritization, scope adjustments, or changes to delivery approach.
If Orases materially fails to meet three (3) consecutive Sprints for reasons primarily attributable to Orases, CLIENT may, upon written notice, require one or more of the following at no additional cost (agreed to mutually):
(a) reallocation or augmentation of resources,
(b) revised delivery approach, or
(c) adjustment of billed sum/performance credit

#### 2.8.7 Quality Assurance

Orases employs a continuous testing approach integrated throughout the development lifecycle to ensure quality at every stage.
Testing and Quality Activities
- Development Phase:
- Developers write unit tests, where appropriate, for business logic and critical functionality
- Peer code reviews conducted before QA handoff
- QA Testing Phase:
- QA creates and executes test cases based on requirements
- Integration testing validates end-to-end workflows
- Regression testing ensures no unintended impacts to existing functionality
- User Acceptance Testing (UAT):
- CLIENT Product Owner and SMEs validate features in staging environment
- UAT test cases defined during requirements phase
- Orases facilitates UAT sessions and incorporates feedback
- CLIENT provides formal acceptance per Section 2.7
Defects identified during development, testing, or review will be logged, prioritized, and addressed as part of the ongoing time-and-materials engagement.
CLIENT reported Production Defects that are attributable to Orases’ failure to perform the Services in accordance with the requirements of this SOW, and approved specifications (“Orases‑At‑Fault Defects”) shall be corrected by Orases at no additional cost to CLIENT and shall not be billable as part of the time‑and‑materials engagement.
Defects resulting from (i) changes in scope or requirements, (ii) CLIENT‑provided materials, data, or instructions, (iii) third‑party systems or integrations not under Orases’ control, or (iv) issues outside the scope of the Services shall be addressed on a time‑and‑materials basis in accordance with this SOW.
For purposes of this SOW, a “Defect” includes any failure of a Deliverable to operate in accordance with approved requirements and documented workflows. Defects shall be deemed “Orases‑At‑Fault Defects” where the root cause is attributable to Orases’ implementation, configuration, integration logic, data handling, error handling, or performance tuning.
Where the Parties disagree on whether a Defect is an Orases‑At‑Fault Defect, Orases shall remediate the Defect without delay, and the Parties shall resolve cost responsibility thereafter. No remediation necessary to restore Production functionality shall be withheld pending such resolution.

#### 2.8.8 Defect Severity Matrix

Defects identified during development, testing, or review will be logged, prioritized, and addressed as part of the ongoing time-and-materials engagement in accordance with Section 2.8.7..
Defects will generally be categorized by severity to support prioritization. Resolution timelines are best-effort targets and are dependent on defect complexity, prioritization, and available capacity. This SOW does not establish fixed service-level guarantees.

| Severity | Definition | Examples |
| --- | --- | --- |
| Critical | System is unusable or major functionality is completely broken. Data loss or security vulnerability present. No workaround available. | Application crashes on launch - Payment processing failure - Security vulnerability exposing customer data |
| High | Major feature is broken or significantly impaired. Affects many users. Workaround is difficult or impractical. | Service booking fails for specific customer segment - Home inventory data not saving - Admin portal login issues |
| Medium | Feature is partially broken or behaves incorrectly. Affects some users. Reasonable workaround exists. | UI rendering issue on specific device - Validation error message unclear - Search returns incorrect results intermittently |
| Low | Minor issue with minimal impact. Cosmetic or edge case. Workaround is easy. | Typo in label or message - Minor UI alignment issue - Non-critical error in logs |

Medium Severity Defects shall not automatically block acceptance; however, acceptance may be withheld if the aggregate number, nature, or impact of such defects materially degrades functionality, usability,
performance, security posture, data integrity, or end‑user experience, as reasonably determined by CLIENT.
Medium Severity Defects that affect core customer journeys, administrative workflows, regulatory obligations, or production operability may, in the aggregate or individually, constitute grounds for rejection.

#### 2.8. Service Hours and SLAs

**Services are provided during the following hours:**

9:00am – 5:00pm Eastern Time, Monday through Friday, Excluding Orases Holidays
Orases Holidays: New Year’s Day, Martin Luther King Jr. Day, Presidents’ Day, Memorial Day, Juneteenth, Independence Day, Labor Day, Thanksgiving Day, the Friday following Thanksgiving, Christmas Day, the week between Christmas Day and New Year’s Day
For the above holidays, the date designated as the applicable federal holiday shall be used.
Support requests submitted outside of Support Hours will be deemed received at the start of the next Business Day unless otherwise agreed in writing.
Service Levels & Incident Response
Orases shall use commercially reasonable efforts to meet the following response resource targets:

| Severity Level | Response Time Target | Resourced Target |  |  |
| --- | --- | --- | --- | --- |
| Severity Level | Hypercare | Production Support | Hypercare | Production Support |
| Critical | Within 1 business hours | Within 2 business hours | Within 1 business hours | Within 2 business hours |
| High | Within 2 business hours | Within 4 business hours | Within 2 business hours | Scheduled based on CLIENT priority |
| Medium | N/A | Within 1 business day | Scheduled based on CLIENT priority | Scheduled based on CLIENT priority |
| Low | N/A | Within 3 business days | Scheduled based on CLIENT priority | Scheduled based on CLIENT priority |

Response Time means acknowledgement and triage — not full resolution.

**Resolution timelines depend on:**

- Issue complexity
- Reproducibility
- Third-party dependencies
- CLIENT responsiveness
- Competing priorities

#### 2.8.1 Tools and Tracking

- Orases will utilize industry-standard tools to manage delivery and communication, which may include:
- Project Management: Jira (Orases Team) and Trello (CLIENT) (backlog, sprint tracking, defect management)
- Documentation: Confluence (requirements, technical specs, meeting notes, decisions)
- Real-Time Communication: Slack (dedicated project channel) or Microsoft Teams
- Video Conferencing: Google Meet

#### 2.8.1 Governance Evolution

The Parties acknowledge that governance practices may evolve over the course of the Project. Governance details, including cadence, roles, and tools, may be refined by mutual agreement to better align with project realities and CLIENT needs.

---

## 03 Project Assumptions and CLIENT Responsibilities

Project Assumptions
Prior Discovery Context
Prior to executing this SOW, Orases conducted preliminary sales-related discovery activities with Duke Energy business stakeholders, resulting in two reference documents:
"Discovery Findings and Updated Project Scope" dated December 2025
"Duke Energy Residential Solution Scope" dated December 2025
These documents (collectively, "Sales Reference Documents") represent Orases' current understanding of the CLIENT’S objectives based on business stakeholder input and are incorporated herein for reference as Appendix 1. The purpose of these documents is to provide an initial understanding and are not meant to act as scope or Deliverables under this SOW. CLIENT acknowledges that preliminary sales-related discovery was completed WITHOUT Duke Energy's project team participation, and significant technical unknowns remain, including but not limited to:
API availability and integration capabilities
Technical feasibility of proposed features
Security and compliance requirements
Integration complexity with existing Duke systems
Production deployment constraints
Orases will decide on the project management, collaboration, and workflow tools to document requirements, manage work, and log defects and issues in collaboration with CLIENT and project needs. Orases shall provide appropriate tooling access to identified CLIENT Stakeholders.
Notwithstanding any other provision in the Agreement or this SOW, CLIENT shall provide documents, information, feedback, content, and other materials or inputs as reasonably needed or requested by Orases for Orases to provide the Services and Deliverables hereunder. Both Orases and CLIENT agree that material failure of CLIENT to provide support or cooperation as required hereunder may result in Orases’ delay or inability to provide the Services and/or Deliverables as contemplated hereunder. CLIENT shall remain obligated to pay for any work performed hereunder, even if the Deliverables are delayed or cannot be delivered as a result of CLIENT’S failure to cooperate as required hereunder.
CLIENT Responsibilities
CLIENT is responsible for ongoing UAT and timely acceptance of the Services and Deliverables, the cadence of which will be set together by the project team.
CLIENT is responsible for designating a single Product Owner who is accountable for:
Relaying decisions
Providing timely feedback on artifacts, deliverables, and questions
Acceptance of Services and Deliverables
Provide access to Subject Matter Experts
Attend scheduled meetings
Follow processes and workflows determined by Orases
Reading, reviewing, and approving requirements documentation
CLIENT is responsible for providing access to existing infrastructure and integration points.
CLIENT is responsible for notifying Orases in advance of significant business changes (for example, stakeholder changes, leave of absence, potential timeline bottlenecks, business case changes, etc.)
CLIENT is required to hold at least monthly Stakeholder meetings with their project sponsors and Orases. Project sponsors will be identified and documented in the Project Kickoff meeting.

### 3.3 Consultant Responsibilities:

- Provide clear, concise guidance and recommendations to Duke Energy for the CLIENT responsibilities listed within this SOW
- Deliver the scope of work in accordance with the timeline and project budget mutually agreed to by Duke Energy and Orases, recognizing that timeline and scope are subject to CLIENT prioritization and scope decisions, in accordance with Section 2.3.
- Deliver Services and Deliverables that meet the acceptance criteria and quality standards defined in this SOW and mutually agreed upon by the Parties.
- Orases shall use commercially reasonable efforts to mitigate the impact of any CLIENT‑related delays, including re‑sequencing work, adjusting staffing, or performing available tasks, before claiming schedule or cost relief.
- Maintain a qualified project team with appropriate roles and skill levels. Consultant will employ a sufficient number of resources with the appropriate level of skill and experience to successfully implement the Services described herein.
- Manage resource changes in accordance with the governance model: provide advance notice for key roles where practical, and document all resource substitutions to ensure continuity and skill level maintenance.
- Employ industry-standard quality assurance processes, including code reviews, testing, and defect management workflows.
- Consultant will remain free of conflicts of interest related to the Services at all times. In the event that the Consultant becomes aware of any issue or question concerning a possible conflict of interest, Consultant shall provide Duke Energy with written notice.
- Consultant shall comply with the Duke Energy Interface Requirements set forth in Appendix 2.
- Proactively identify and communicate risks, blockers, and issues that could impact project objectives, and work collaboratively with Duke Energy to develop appropriate remedies.
- Appoint and maintain a Consultant Product Manager for the Services under the SOW. The Consultant Product Manager shall have the following responsibilities:
- Facilitate periodic update meetings and communication
- Submit written status reports
- Respond to questions posed by the Duke Energy Principal Representative and project team in accordance with agreed-upon communication protocols
- Provide project information and be available to answer questions for the Duke Energy project team as needed
- Monitor quality of work and deliverables to ensure delivery consistent with the terms of this SOW and the Agreement

---

## 04 Estimated Timeline

Milestones will be agreed to throughout the project and reported on a pre-agreed cadence. The timeline of the project will be defined based on the Prioritization of Work (Section 2.3) agreed to by the CLIENT and Orases during the Iterative Development (Deliverable 2.2, 2.3 and 2.4.). Expected duration of project phases is listed below. These estimates are based on the project scope referenced in the Sales Reference Documents under Appendix 1, and are subject to change based on the aforementioned Prioritization of Work and Requirements Definition:
Both CLIENT and Orases agree to work together in good faith to drive towards the following target dates. These dates are subject to revision based on the above:

**Key Milestones:**

MVP target completion by 9/30/2026
Phase 1 target completion by 12/31/2027
Each Key Milestone shall be associated with a mutually agreed minimum set of Deliverables or functional outcomes, documented in writing prior to commencement of work toward that Milestone.
Orases and Duke Energy Project Teams will collaborate in good faith to establish and maintain a mutually agreeable Project Schedule. Except for the Key Milestones identified above, all dates are estimates and may be adjusted by mutual written agreement between the parties. For clarity, mutual written agreement includes e-mail confirmations between designated project managers. Any change that affects a Key Milestone by more than 10 business days, scope, fees, or acceptance criteria, will be reflected in a written Change Order executed by both parties. Delays caused by CLIENT, its vendor or factors outside Orases reasonable control entitle Orases to a reasonable extension.

---

## 05 Payment Schedule and Cost

CLIENT shall pay the fees to be calculated using the rate set forth below for the total number of hours worked by Orases, plus any and all Costs (as defined below) incurred by Orases during the applicable billing period.
The Services will be performed on a time and materials basis and will be invoiced at a blended rate of $250/hour, in addition to any and all third party costs incurred by Orases and/or any fixed fee configurable components used in providing the Services and/or Deliverables hereunder (collectively, “Costs”); invoices will be sent  a month, in accordance to the invoicing procedures set below (end of the month). Orases reserves the right to revise its rate schedule upon 90 days’ prior written notice to CLIENT, but no more often than once per year and not within the first year of the SOW.
Based on current staffing assumptions and projected scope, the anticipated monthly spend under this SOW is estimated to range between $80,000 and $105,000 per month. This estimate is provided for budgeting purposes only and does not constitute a minimum or maximum commitment. Actual monthly invoices will be based solely on the number of hours worked and Costs incurred during the applicable billing period at the rates set forth herein. Monthly spend may vary based on scope, prioritization decisions pursuant to Section 2.3, release cadence, support needs, and overall project velocity.
For budgeting and planning purposes only, and based on the scope, assumptions, and staffing model set forth in Orases’ RFP proposal dated  September 30, 2025, the parties acknowledge that the total fees and Costs anticipated to be incurred under this SOW during the completion of two Key Milestones are currently estimated not to exceed approximately $1,051,400 (the “Estimated SOW Amount”).
The Estimated SOW Amount is a non-binding estimate only and does not constitute a cap, minimum commitment, or fixed fee. Actual fees shall be based solely on the number of hours worked and Costs incurred in accordance with the time and materials rates set forth herein.
Orases shall track fees and Costs incurred against the Estimated SOW Amount and shall provide CLIENT with written notice when cumulative fees and Costs reach eighty‑five percent (85%) of the Estimated SOW Amount. Orases shall not materially exceed the Estimated SOW Amount unless and until the parties execute a written Change Order to this SOW addressing any applicable scope changes, milestone adjustments, or revised budget expectations. For purposes of this SOW, “materially exceed” shall mean exceeding the Estimated SOW Amount by more than ten percent (10%). If CLIENT does not approve continued work beyond the Estimated SOW Amount, Orases shall pause non‑critical work in an orderly manner until the Parties reach written agreement.
Orases will provide regular statements and updates regarding the fees incurred on the actual time spent for functionality delivered and the anticipated cost of functionality to be delivered based on the confidence level of scope at the time. Both Orases and CLIENT agree to work in good faith to make decisions and functionality choices that balance the spirit of the requirements and the overall budget.
CLIENT may request to expand or reduce the hours spent by Orases to provide the Services and/or create the Deliverables. Any request to expand the Services or Deliverables shall be subject to the procedures set forth in this Section 4 and the terms of Section 5 of this SOW.  After Orases establishes the initial number of hours and resources to be assigned for the work to be completed, if CLIENT wants Orases to change the number of hours or team size assigned to this SOW, it shall a submit to Orases a written request for such change(s) with no less than 30 days’ advanced written notice. Orases will notify CLIENT within 15 days after receiving any such notice, if CLIENT’S request is not feasible and will discuss alternative arrangements. Orases and CLIENT will cooperate in good faith and with due diligence to address any changes reasonably requested by CLIENT.
All Costs to be paid to Orases pursuant to this SOW shall be subject to Section 2 (Fees And Expenses) of the Agreement.
- INVOICING PROCEDURES:
Consultant shall invoice Duke Energy for the Fees pursuant to Section 2 of the Agreement and this SOW. Payment terms are  unless otherwise agreed upon within the Ariba Network. Payment terms are based on the date a correct invoice is received through the Ariba Network and not the date of the invoice. In the event of an incorrect invoice, Ariba will stop the submission of the invoice or it will be returned to the Consultant. An invoice is incorrect when sufficient information needed to begin processing is not included on the invoice.   The Consultant will need to send a corrected invoice with the requested information through Ariba.
All invoices for Services provided by Consultant must include a complete description of each Fee and Performance Credit (if applicable), and the Purchase Order number that applies to that invoice.  Invoices for Services shall be net of any Performance Credits. All invoices shall be submitted through the Ariba Network. All Fees for Services will be paid to an account designated by Consultant via Electronic Funds Transfer (EFT) or check payment.

**The invoice shall include, but not limited to:**

- The name, address, and telephone number(s) of the Duke Energy Principal Representative,
- A valid Purchase Order (“PO”) number located in the invoice or any credit invoice,
- A valid Duke Energy “Bill To” address,
- A valid “Remit to” address,
- Invoice date,
- Itemized Fees, including Time or Performance Credits where needed;
- Total amount of the invoice
All invoices and supporting documentation shall be submitted to the Duke Energy Principal Representative, unless otherwise directed by Duke Energy. At no time will Duke Energy accept invoices without supporting documentation.
- - - - - - - - - - - - - - - - - - -

## 06 Change Order Process

Any Change Orders shall be subject to the terms and procedures outlined in Section 8 (Changes in Service) in the Agreement. Consultant shall use commercially reasonable efforts to resolve matters that could reasonably be calculated to disrupt the Services and/or to negatively impact the defined Project Objectives and the Deliverables. Consultant shall make every attempt to notify Duke Energy prior to any process changes and quality control changes.
Where advanced notice is not reasonably possible and on rare occasions where prior notice is not possible due to the necessity of an expedited change, Duke Energy should be notified within one (1) business day of any personnel, process, scheduling or quality control changes.

---

## 07 Travel

Any travel expenses for travel to/from CLIENT ofﬁces in Charlotte, NC or St. Petersburg, FL by any Orases employee shall be subject to the terms and procedures set forth in Exhibit B (Guidelines for Consultant Expense Reimbursement) in the Agreement.
Orases estimates 1 trip to CLIENT Office and does not anticipate any additional travel at this time.  All travel requests must be mutually agreed to by all Parties. Travel Expenses are not included in the solution pricing and are billed as incurred. Travel arrangements, including flights, hotels, meals, etc. will be booked by Orases to optimize on-site productivity while being cost conscious and staying within the guidelines provided by Duke Energy.
Both Parties agree to provide the other Party with reasonable facilities when representatives come to the Party’s Premises, e.g., desk, office equipment, phone, during face-to-face visits.

---

## 08 Term

The term of this SOW shall commence as of the Effective Date and shall continue in effect until December 31, 2027, unless earlier terminated or extended in accordance with the provisions of Agreement or if extended upon the mutual agreement of the Parties (by providing written notice to the other party delivered at least thirty (30) days prior to the then-scheduled expiration date, may extend the initial term of this SOW for up to two (2) additional 1-year terms.

---

## 09 Termination Assistance

Duke Energy may terminate or suspend this SOW in accordance with the provisions set forth in Section 9 of the Agreement. Upon termination of this SOW, and within thirty (30) days of notice, Consultant shall furnish to Duke Energy all information collected from Duke Energy, its subcontractors, partners, customers, trade allies, distributors, etc. Consultant shall follow a mutually agreed upon transition plan and promptly furnish Duke Energy all information collected, recorded and/or retained by Consultant, in electronic format, in the manner reasonably requested by Duke Energy, and return to Duke Energy all Deliverables in Consultant’s possession.
Within thirty (30) days of the expiration or earlier termination of the Agreement, or such earlier time as Duke Energy requests, Consultant shall return to Duke Energy or its designee, or at Duke Energy’s request, securely destroy or render unreadable or undecipherable if return is not reasonably feasible or desirable to Duke Energy (which decision shall be based solely on Duke Energy’s written instructions), each and every original and copy in all media of all Confidential Information in Consultant’s possession, custody or control.
Consultant shall reasonably cooperate with Duke Energy to transition work from Duke Energy’s existing suppliers of the Services, if any, to Consultant. Further, upon request of Duke Energy and at the termination of this SOW, Consultant shall provide reasonable assistance to Duke Energy to transition any Duke Energy owned or retained aspects of the Services or Deliverables to a new supplier.

---

## 10 Communications and Notices

The contact information for CLIENT’S PRODUCT OWNER for purposes of this SOW is as follows:
Name
Address
Phone
Email
Such representative has complete authority to make decisions on behalf of CLIENT with respect to this SOW including, without limitation, the approval of any element of the Deliverables and all issues regarding any Response Plans or Change Orders.  ANY TELEPHONE OR VIDEO CALLS BETWEEN CLIENT AND ORASES REGARDING THE SERVICES MAY BE RECORDED AND USED FOR QUALITY ASSURANCE AND TRAINING PURPOSES BY ORASES.   CLIENT MUST NOTIFY ORASES IF IT OBJECTS TO ANY SUCH RECORDINGS.
The Principal Representatives for both Parties, in accordance with Section 22 Notices in the Agreement, are as follows:
ORASES
Amy Damoulakis
5728 Industry Lane, Frederick MD, 21702
240-409-6152
amy@orases.com
CLIENT
Name
Address
Phone
Email

---

Once received and signed by both parties, this SOW shall constitute a binding contractual agreement between Orases and CLIENT. THE PARTIES ACKNOWLEDGE THAT THEY HAVE READ THE STATEMENT OF WORK, UNDERSTAND IT, AND AGREE TO BE BOUND BY ITS TERMS AND CONDITIONS. FURTHER, THE PARTIES AGREE THAT THE COMPLETE AND EXCLUSIVE STATEMENT OF THE AGREEMENT BETWEEN THE PARTIES RELATING TO THIS SUBJECT SHALL CONSIST OF 1) THIS STATEMENT OF WORK, 2) ITS SCHEDULES, AND 3) THE AGREEMENT (INCLUDING THE EXHIBITS THERETO), INCLUDING THOSE AMENDMENTS MADE EFFECTIVE BY THE PARTIES IN THE FUTURE. THIS STATEMENT OF WORK BETWEEN THE PARTIES SUPERSEDES ALL PROPOSALS OR OTHER PRIOR AGREEMENTS, ORAL OR WRITTEN, AND ALL OTHER COMMUNICATIONS BETWEEN THE PARTIES RELATING TO THE SUBJECT DESCRIBED HEREIN.
Orases Consulting Corporation
Signature: _______________________________________
Printed Name: __________________________________
Title: ______________________________
Date: __________________
Duke Energy Business Services, LLC
Signature: _______________________________________
Printed Name: ___________________________________
Title: ______________________________
Date: _________________

## Appendix 1 Sales Reference Documents

"Discovery Findings and Updated Project Scope" dated December 2025
"Duke Energy Residential Solution Scope" dated December 2025

## Appendix 2 Duke Energy Interface Requirements

Duke Energy retains all rights and full discretion to determine the access rights to its IT systems and processes and may deny Consultant’s access to its IT systems and processes at any time. Duke Energy will provide to the Consultant IT contacts that enable the Consultant to understand the Duke Energy IT systems and requirement and participate in testing of the IT systems and processes related to the Programs.
Duke Energy will provide to Consultant detailed information and formats relating to reporting needs. Duke Energy may also request Consultant to provide a format for Duke Energy approval. Any requests made by Duke will follow the processes set forth in this SOW, specifically Section 2.
Consultant shall cause its subcontractor to maintain a business continuity and disaster recovery plan reasonably acceptable to Duke Energy.  Duke Energy shall have the right to audit Consultant’s subcontractors’ compliance with the business continuity and disaster recovery plan.

### Customer Information and Personally Identifiable Information

Consultant shall, and shall require its subcontractors to, adhere to and perform the Services in accordance with the security protocols set forth by Duke Energy and as indicated in the Agreement.

### Third Party Risk Management Service Risk Profile Questionnaire

Consultant may be required periodically to complete a Cybersecurity Assessment Questionnaire for review by Duke Energy and at Duke Energy’s expense.  Assessment reviews may identify material issues that will be shared by Duke Energy with the Consultant.  The Consultant shall review each material issue and determine, to the extent possible, its ability to reasonably mitigate or resolve the material issue identified, shall develop a Duke Energy-approved Remediation Plan to mitigate or resolve the material issues identified and implement the mutually agreed upon security changes or enhancements according to the Remediation Plan.  In the event that Consultant does not meet its obligations of the Remediation Plan, Duke Energy reserves the right to terminate this SOW in accordance with Section 9 of the Agreement.
Throughout the performance of its obligations under the Agreement or this SOW, Consultant shall provide Duke Energy with prompt notice of any planned material change in security controls and processes that would negatively impact the security of the Services being provided by the Consultant and materially modify answers provided in the Cybersecurity Assessment Questionnaire.

### Record Retention

Consultant shall retain, by state, in electronic form or as otherwise directed by Duke Energy, all records, documents and data required to be maintained for such periods required by law and in accordance with the Agreement.

### Data Gathering and Reporting

Duke Energy shall have access to all data collected for the purposes of fulfilling the Services.
Consultant shall to the best of its ability cooperate with Duke Energy in preparing regulatory filings or audits related to the Services and shall provide such information and assistance as Duke Energy reasonably deems necessary at Duke Energy expense.

### Vendor Hosted Sites and Marketing Activities

#### Google Tag Manager

Consultant will agree to affix Duke Energy-supplied Google Tag Manager coding (GTM) to the following:
•         all externally hosted web pages carrying a Duke Energy subdomain
•         and/or all web pages that serve as a continuation path from the Duke Energy domain (http://duke-energy.com)
•         and/or all web pages containing a digitally-based enrollment to the respective program or service; including, but not limited to web-based forms, app-based forms, and any i-frame pages.
If any of the aforementioned span multiple jurisdictions, Consultant will ensure that GTM codes are included on each individual web page. In addition, Consultant will implement the relevant linker plugin for the proper implementation of bi-directional cross-domain tracking.  For security reasons, Consultant will not receive access to Duke Energy’s instance of Google Tag Manager.
Custom coding, data layer pushes, and/or virtual pages (as defined by the Web Analytics group) may need to be implemented on the site to properly track customer interactions. After implementing analytics tags, Consultant will work with Duke Energy’s Marketing Operations team and/or Web Analytics group to confirm that all tags are properly functioning and no PII data is being passed prior to the initiation of any marketing campaigns. Duke Energy will perform testing and sign-off on “properly functioning” analytics tags once completed by Consultant. Additionally, Consultant will agree to make any necessary tagging updates to revised web pages or newly developed web pages made on behalf of the program or service. If possible, Duke Energy would like to obtain ‘read-access’ to the portion of the Consultant’s Google Analytics property that tracks activity on Duke Energy branded web pages.

#### Paid Media

All paid media should be fulfilled through the Duke Energy’s sole Media Agency of Record (MAoR) including but not limited to broadcast, digital, search engine marketing, out-of-home, print and social media. The MAoR should be informed of any planned campaigns for consultation and recommendation in advance of execution.

#### Brand Standards

Adherence to Duke Energy’s brand standards, including logo use, graphic guidelines, writing tone and AP Style standards, etc. to ensure proper representation of the Duke Energy brand if requested by the Project Team for certain areas or Deliverables. The Brand Standards document https://www.duke-energy.com/_/media/pdfs/legal/duke-energy-brand-standards.pdf is available online and updated regularly. Any questions arising during asset development that are not addressed within the comprehensive guide can be addressed by the Corporate Communications organization. The Duke Energy Principal Representative will direct Consultant to the appropriate individual(s) for assistance if needed.

#### Web Standards

Duke Energy has documented standards for vendor integration that address topics such as the proper use of the Duke Energy’s logo, color palette, typography styles, user interface (UI) elements, imagery and icon guidelines, form styles, responsive design requirements, coding and accessibility standards, and website implementation approaches. These standards are available for review at https://share.goabstract.com/47fc3466-4fb5-46ce-80d8-e6a3f99b7f0d?collectionLayerId&mode. Consultant agrees to adhere to these visual design and content standards and any other design or content direction provided by the Project team where needed, along with User Experience (UX) and Content managers reporting to Duke Energy’s Director of Digital Strategy & Execution. In case the Project Team request this, Consultant agrees to take design and content direction solely from that Director’s team, and no other Duke Energy representatives.