Statement of Work #1
Client: 	Duke Energy Business Services LLC

This Statement of Work #1 ("SOW") effective as of January 5, 2026 ("Effective Date"), by and between Duke Energy Business Services LLC ("CLIENT") with its principal offices located at 525 South Tryon St., Charlotte, NC 28202 and Orases Consulting Corporation ("Orases") with its principal offices located at 5728 Industry Lane, Frederick, MD 21704, shall serve as SOW to the Master Service Agreement by and between CLIENT and Orases effective as of 02/28/2025 ("Agreement"). All terms that are defined in the Agreement will have the same meaning when used in this SOW. In the event of any conflict between the terms of this SOW and those of the Agreement, the terms of this SOW will control.

This SOW identifies certain specific Services and Deliverables to be provided by Orases in connection with the following project ("Project"): Residential Solutions (RS) Application

- - - - - - - - - - - - - - - - - - - -

## 01 Services and Deliverables

Orases shall provide the following Services and Deliverables as part of the Project. The activities listed below represent the anticipated scope of Services; however, the Parties acknowledge that the Services may include, but are not limited to, the activities described in this Section 01, depending on discoveries made during the Analysis and subsequent Client-approved priorities.

### 1.1 Analysis Activities

**Prior Discovery Context**

Prior to executing this SOW, Orases conducted preliminary discovery activities with Duke Energy business stakeholders, resulting in two reference documents:
- "Discovery Findings and Updated Project Scope" dated December 2025
- "Duke Energy Residential Solution Scope" dated December 2025

These documents (collectively, "Initial Discovery") represent Orases' current understanding of project requirements based on business stakeholder input and are incorporated herein by reference as Exhibit A. However, CLIENT acknowledges that Initial Discovery was completed WITHOUT Duke Energy's technical team participation, and significant technical unknowns remain including but not limited to:
- API availability and integration capabilities
- Technical feasibility of proposed features
- Security and compliance requirements
- Integration complexity with existing Duke systems
- Production deployment constraints

**Round 2 Discovery Activities**

During Analysis Activities under this SOW, Orases will conduct Round 2 discovery with CLIENT's technical team to validate feasibility and refine project scope. Activities may include, but are not limited to:

**Technical Validation**:
- Workshops with Duke IT, Security, Integration, and Infrastructure teams
- API availability assessment (Customer Validation, HPP Plans, Service Request Creation, Enrollment)
- Integration complexity analysis (Commerce CRM, Dynamics CRM, Duke Data Fabric)
- Security requirements review and compliance assessment
- Infrastructure constraints and deployment environment evaluation
- Performance and scalability requirements validation

**Requirements Refinement**:
- Validation of features identified in Initial Discovery
- Identification of technical constraints, blockers, and dependencies
- Assessment of alternative approaches where original assumptions prove invalid
- Prioritization workshops with technical and business stakeholders
- Development of user flows, wireframes, and/or user stories
- Refinement of scope, timeline, and cost estimates

**Architecture and Design**:
- Technical architecture design (frontend, backend, infrastructure)
- Database schema design
- API specifications and integration patterns
- Security architecture and compliance framework
- Abstraction layer design to minimize future rework
- DevOps and deployment strategy

**Deliverables**:
- Clickable prototype to illustrate key workflows, proposed user experience, and system behavior
- Technical architecture documentation
- Updated scope, timeline, and cost estimate based on Round 2 discovery findings
- Risk assessment and mitigation strategies
- Validation sessions with CLIENT stakeholders

**CLIENT Acknowledgment**

CLIENT understands that Round 2 discovery may reveal:
- APIs assumed to exist may not be available, requiring manual fallback workflows or alternative implementation approaches
- Integration complexity with Commerce/Dynamics CRM may exceed initial estimates
- Security and compliance requirements may require additional development effort
- Certain features identified in Initial Discovery may be technically infeasible or cost-prohibitive given business value
- Timeline and cost estimates provided in Initial Discovery may increase or decrease based on technical validation findings

Initial Discovery (Exhibit A) serves as a starting point for collaboration and planning, not a binding commitment of scope, timeline, or budget. Final scope will be determined through Analysis Activities and CLIENT-approved prioritization per Section 1.2.

### 1.2 Prioritization of Work

Following completion of Analysis Activities (Section 1.1), Orases will provide CLIENT with a comprehensive recommendation including:
- Refined scope based on technical validation with Duke's technical team
- Detailed feature list with acceptance criteria
- Timeline with milestones and dependencies
- Updated cost forecast with confidence level
- Risks, dependencies, and mitigation strategies
- Recommended approach for Phase 1 implementation

Orases and CLIENT will work collaboratively to establish the priority order for all features, enhancements, and tasks.

No work for Section 1.3 (Design, Development, and Implementation) will begin until CLIENT has reviewed, approved, and prioritized the proposed work.

CLIENT will review Orases' recommendation and may choose to:
(a) Approve proposed scope, timeline, and budget to proceed with Section 1.3
(b) Request modifications to scope, timeline, or budget
(c) Pause engagement to assess findings and options

If CLIENT chooses not to proceed with Section 1.3 after receiving Orases' recommendations, CLIENT will pay for all Analysis Activities performed through the date of such decision at the rates specified in Section 4. This SOW contemplates that both parties intend to proceed with Phase 1 implementation (Section 1.3) following successful completion of Analysis Activities, subject to mutual agreement on scope, timeline, and budget.

Priorities may be updated throughout the Project at CLIENT's direction, and Orases will provide updated estimates regarding timeline, scope, or budget per the Change Order Process (Section 5).

### 1.3 Design, Development, and Implementation

Following CLIENT's approval of priorities, Orases will proceed with design, development, testing, and implementation of the approved features. Activities may include, but are not limited to:

**Design Phase**:
- UX/UI design refining elements identified during the Analysis Phase
- Design system creation and style guide documentation
- Responsive design for mobile, tablet, and desktop viewports
- Accessibility compliance (WCAG 2.1 AA standards)
- CLIENT review and approval of designs

**Development Phase**:
- Front-end development (mobile applications and responsive web)
- Back-end development (APIs, business logic, data models)
- Integration with CLIENT systems and third-party services
- Database implementation and migration scripts
- Authentication and authorization implementation
- Multi-channel notification system (push, SMS, email)

**Quality Assurance**:
- Unit testing and integration testing
- Security testing (OWASP Top 10 compliance)
- Performance testing and optimization
- Browser and device compatibility testing
- Accessibility testing

**Infrastructure and DevOps**:
- System configuration and environment setup (development, staging, production)
- CI/CD pipeline implementation
- Monitoring and logging configuration
- Security hardening and compliance implementation
- Backup and disaster recovery setup

**Deployment Support**:
- Production deployment and cutover support
- App store submissions (iOS App Store, Google Play Store)
- Admin user training and documentation
- Go-live support and stabilization
- Bug resolution during warranty period

If ongoing support, maintenance, or hosting services are required beyond the warranty period, Orases and CLIENT will scope such services separately and execute one or more additional SOWs.

### 1.4 Deliverable Acceptance

Given the time-and-materials nature of this engagement, deliverable acceptance will occur incrementally throughout the project rather than at final delivery.

**Sprint-Level Progress Reviews**:
- Work will be organized in 2-week sprints with defined objectives agreed upon by both parties
- At the conclusion of each sprint, Orases will provide a progress demonstration to CLIENT stakeholders
- Formal acceptance is not required for every sprint, particularly when:
  - Features are in-progress and span multiple sprints (e.g., complex workflows requiring 4-6 weeks)
  - Work is foundational (architecture, infrastructure setup, database design) with no user-visible functionality to demonstrate
  - Sprint focused on technical debt, refactoring, performance optimization, or security hardening
  - Both parties agree that work-in-progress should continue without interruption
- **Formal sprint acceptance is required when**:
  - A complete user-facing feature or workflow is delivered and ready for CLIENT review
  - A significant milestone is completed (e.g., clickable prototype, API integration functional, major admin portal functionality complete)
  - CLIENT requests formal review and acceptance of sprint deliverables
- When formal acceptance is required, CLIENT will have 5 business days to review sprint deliverables and provide acceptance or rejection with specific defects noted
- Orases will address defects in subsequent sprint(s) at no additional cost if defects are due to Orases error or non-conformance with agreed specifications
- Sprint demos provide visibility and feedback opportunities without creating formal acceptance gates that slow progress

**Phase-Level Acceptance**:
- Major project phases (Analysis, Design, Development, Testing, Deployment) will have formal acceptance milestones
- CLIENT will have 15 business days to review and accept phase deliverables
- If CLIENT rejects phase deliverable, CLIENT will provide written rejection notice specifying defects or non-conformance with agreed specifications
- Orases will address defects and re-submit for acceptance within timeframe agreed by both parties

**Final Acceptance and Warranty Period**:
- Final acceptance occurs upon successful production deployment and CLIENT's written acceptance
- Warranty period begins upon final acceptance and extends for 90 days
- During warranty period, Orases will fix defects in workmanship at no additional cost
- Warranty coverage subject to Section II.D (Acceptance) of the Agreement and Section 10 (Warranty) of this SOW

**What CLIENT is Accepting**:

CLIENT acknowledges that in a time-and-materials engagement with evolving scope:
- Sprint demos provide ongoing visibility into progress; formal acceptance only required when complete features/milestones delivered
- Phase acceptance means deliverables meet acceptance criteria defined for that phase
- Final acceptance means system is ready for production use with features and limitations documented during Analysis Activities and approved by CLIENT

**What Constitutes a Defect**:
- Functionality does not perform as specified in agreed sprint objectives or acceptance criteria
- System does not meet security, performance, or availability requirements documented in acceptance criteria
- Code quality does not meet professional standards (e.g., contains OWASP Top 10 vulnerabilities, lacks proper error handling, or violates documented coding standards)
- Deliverable does not conform to approved designs or technical specifications

**What Does NOT Constitute a Defect**:
- Features not included in agreed sprint objectives, phase scope, or approved prioritization
- Changes to CLIENT requirements after formal acceptance of completed features or phases
- Work-in-progress during active development sprints (not yet submitted for formal acceptance)
- Issues caused by third-party systems, APIs, or services outside Orases control
- Performance issues caused by CLIENT infrastructure, configuration, or data volumes not specified in acceptance criteria
- Changes in CLIENT's business requirements, regulatory environment, or strategic direction

Deliverable Acceptance pursuant to this SOW shall be subject to Section II.D. (Acceptance) of the Agreement.

### 1.5 Phase 1 Anticipated Components

Based on Initial Discovery (Exhibit A), Phase 1 is anticipated to include the following high-level components, subject to technical validation during Analysis Activities (Section 1.1) and CLIENT approval during Prioritization (Section 1.2):

**Customer-Facing Applications**:
- Native mobile applications (iOS and Android)
- Responsive web application (Progressive Web App)
- User registration and authentication
- Multi-property support
- Home Protection Plan (HPP) management (view plans, enroll, upgrade/downgrade, self-service cancellation)
- Home inventory and profile building (manual entry, barcode scanning, warranty tracking, maintenance schedules)
- Service booking for HPP-covered services (symptom-based intake, coverage check, contractor assignment, date/time selection)
- Service booking for ad-hoc services (service catalog browsing, transparent pricing, booking flow)
- Communication preferences and notification center
- Multi-channel notifications (push, SMS, email, in-app)
- Maintenance reminders (inventory-based, seasonal, custom)
- Loyalty and gamification features (profile completion score, loyalty points, home health scorecard, badge system)
- Service history and records (exportable service log, invoice storage, warranty tracking)

**Admin Portal** (anticipated 7 user roles, subject to validation):
- Role-based access control (RBAC) for multiple administrative user types
- Customer profile management (view, edit, create customer records across Commerce, Dynamics, and App systems)
- Home inventory management (full CRUD on customer inventory)
- HPP plan management (view subscriptions, manual enrollment support)
- Service request management dashboard (view all requests, filter/search, priority queue)
- Manual service request processing workflow (contact contractors, update app status, manage exceptions)
- Contractor configuration management (CRUD operations, trade assignment, service areas, primary/secondary designation, availability)
- Ad-hoc service catalog management (create/edit services, set pricing, define scope of work, geographic availability)
- Analytics and reporting dashboard (customer acquisition, engagement, service requests, revenue, contractor performance, operational metrics)
- Communication and notification management (send email/SMS, bulk notifications, communication log)
- Review queue management (failed enrollments, exceptions, escalations)

**Backend Infrastructure**:
- RESTful API architecture (comprehensive API endpoints for all frontend operations)
- Database design and implementation (PostgreSQL or MySQL with proper normalization and indexing)
- Integration with Duke Enterprise APIs (Customer Validation, HPP Plan retrieval, Service Request Creation if available, Enrollment if available)
- Manual fallback workflows if Duke APIs not available (admin queue processing for enrollments and service requests)
- Data synchronization layer (Commerce CRM for Duke customers, Dynamics CRM for P&G customers, App Backend for non-native customers)
- Contractor matching algorithm (trade + zip code → primary contractor assignment)
- Multi-channel notification engine (push notification service integration, SMS integration, email service integration, notification template management)
- Authentication and authorization (JWT/OAuth, role-based access control, multi-factor authentication for admin users)
- File storage and management (customer photos, invoices, warranty documents)
- Integration with external services (CPSC recall database, barcode lookup APIs, SMS gateway, email service)

**DevOps, Security, and Compliance**:
- Cloud infrastructure setup (AWS: VPC, EC2/ECS, RDS, S3, CloudFront, load balancing, auto-scaling)
- Multi-environment deployment (development, staging, production with proper separation)
- CI/CD pipeline (automated testing, build automation, deployment automation, rollback procedures)
- Security implementation (data encryption at rest and in transit, security headers, API security with rate limiting, OWASP Top 10 compliance, penetration testing)
- Security compliance certification (SOC 2 Type 2 OR ISO 27001 at Orases expense)
- Monitoring and logging (application monitoring, log aggregation, error tracking, performance monitoring, uptime monitoring and alerting)
- Database backup and recovery (automated backups, disaster recovery procedures, data retention policies)
- Mobile app deployment (iOS App Store submission and review, Android Play Store submission and review, app signing certificate management, push notification certificate setup)

**Phase 1 Anticipated Limitations** (subject to validation with Duke's technical team):

CLIENT acknowledges that Phase 1 MVP is anticipated to include the following limitations, with enhanced functionality deferred to Phase 2 or future releases:

- **Manual Admin Workflows**: Service request processing requires manual admin intervention. Operations Manager contacts contractors via email/phone within 1-hour SLA and manually updates customer app status. Automated contractor assignment and real-time status updates require FSM tool integration (Phase 2 scope).

- **Payment Processing**: Contractors collect payment on-site at service completion via cash, check, or credit card (contractor's own payment terminal). Customer app displays service cost and payment instructions. In-app payment integration (Apple Pay, Google Pay, credit card processing, utility bill payment) is Phase 2 scope requiring separate SOW.

- **Limited Status Visibility**: Service request status workflow includes 5 statuses: Pending Confirmation, Confirmed, Rescheduled, Completed, Cancelled. Real-time statuses (Dispatched, En Route, On-Site, In Progress) and GPS tracking ("pizza tracker" experience) require FSM tool integration (Phase 2 scope).

- **Emergency Services Phone-Only**: Emergency services are NOT bookable through the customer app. App includes emergency detection logic via qualifying questions. When emergency detected, app routes customer to phone call. CSR handles emergency coordination with contractors via existing phone-based workflow.

- **No Contractor Portal Changes**: Phase 1 includes NO changes to existing contractor portal. Contractors continue using Commerce CRM portal for job assignment, status updates, scheduling, and invoicing. Admin backend portal provides contractor configuration management (CRUD, trade assignment, service areas, availability) to support customer app matching algorithm. Modern contractor mobile app with real-time job acceptance and GPS tracking is Phase 2 scope.

- **Limited Ad-Hoc Service Catalog**: Phase 1 ad-hoc service catalog limited to 5-10 services with flat-rate or variable pricing, launched in 1-2 pilot markets (to be determined by Duke Energy). Service catalog includes: service name, description, scope of work, pricing, geographic availability, contractor association. Catalog expansion and additional markets require Phase 2 scope adjustment or Change Order.

- **Ratings Collection Only (Not Display)**: Phase 1 customer ratings and reviews collected via external survey vendor (email/SMS) post-service completion. Ratings used internally by Duke Energy for contractor performance evaluation. In-app ratings collection and display to customers during booking flow is Phase 2 scope.

- **No Contractor Marketplace**: Phase 1 contractor assignment uses automated matching algorithm: Trade + Zip Code → Primary Contractor. Customer sees pre-assigned contractor with no in-app option to select alternative contractor. Request for alternative contractor requires phone call to admin Operations Manager who manually reassigns. Contractor marketplace (customer selects from multiple contractors with pricing/ratings) is Phase 2 scope.

**Technical Dependencies** (to be validated during Analysis Activities):

The following technical dependencies will be validated during Analysis Activities. If dependencies are not met, Orases will implement alternative approaches or manual fallback workflows:

- **Duke Enterprise APIs**: Customer Validation API and HPP Plan API anticipated to be available by Week 12. If Service Request Creation API or Enrollment API are not available by MVP launch, Orases will implement manual admin queue processing workflows at no additional cost.

- **CRM System Access**: Integration capabilities with Commerce CRM (Duke customers) and Dynamics CRM (P&G customers) including data schema, API documentation, sandbox environment access, and test accounts.

- **Contractor Data**: Contractor data export from Duke CRM systems (contractor name, contact info, trades, service areas/zip codes, primary/secondary designation, availability rules, lead times) provided by CLIENT by Week 4.

- **Duke IT Infrastructure**: VPN access to Duke network (if required), sandbox environments for integration testing, production deployment procedures and constraints, security approval processes and timelines.

**Out of Scope - Phase 2 or Future Releases** (require separate SOW):

The following features are explicitly out of scope for Phase 1 and require separate SOW:

- FSM tool integration and associated rework ($46,000 estimated based on Initial Discovery)
- In-app payment processing and payment gateway integration
- Contractor mobile app with real-time job acceptance, GPS tracking, and customer communication
- Real-time GPS tracking for customers ("pizza tracker" experience)
- In-app ratings and reviews display during booking flow
- Contractor marketplace (customer selection from multiple contractors)
- AI virtual assistant for troubleshooting and service recommendations
- Predictive maintenance recommendations using machine learning
- IoT integration for smart home devices
- Real-time energy monitoring through utility integration
- White-label platform customization for other utilities
- Commercial properties (Phase 1 supports residential properties only)

CLIENT acknowledges that:
1. This is an anticipated scope based on business requirements from Initial Discovery, not technical validation
2. Round 2 discovery with Duke's technical team may reveal features that are: not technically feasible, more complex than anticipated, dependent on systems/APIs that don't exist, or cost-prohibitive given business value
3. Final scope will be determined through Analysis Activities (Section 1.1) and Prioritization (Section 1.2) with CLIENT approval required before development begins (Section 1.3)

- - - - - - - - - - - - - - - - - - - -

## 02 Project Assumptions and Client Responsibilities

### Project Assumptions

Orases will decide on the project management, collaboration, and workflow tools to document requirements, manage work, and log defects and issues.

Notwithstanding any other provision in the Agreement or this SOW, CLIENT shall provide documents, information, feedback, content and other materials or inputs as reasonably needed or requested by Orases for Orases to provide the Services and Deliverables hereunder. Both Orases and CLIENT agree that any failure of CLIENT to provide support or cooperation as required hereunder may result in Orases' delay or inability to provide the Services and/or deliverables as contemplated hereunder. CLIENT shall remain obligated to pay for any work performed hereunder even if the Deliverables are delayed or cannot be delivered as a result of CLIENT's failure to cooperate as required hereunder.

### Client Responsibilities

CLIENT is responsible for the following activities and commitments to enable Orases to successfully deliver the Services and Deliverables:

**Technical Team Participation**:
- Provide access to Duke IT, Security, Integration, and Infrastructure teams during Analysis Activities (Section 1.1)
- Allocate 10-15 hours per week of technical SME time during Weeks 1-8 for Round 2 discovery activities
- Provide API documentation and sandbox access within 2 weeks of Effective Date
- Provide contractor data export (CSV/JSON format) by Week 4
- Provide test accounts for Commerce CRM and Dynamics CRM integration testing by Week 12

**Business Stakeholder Participation**:
- Designate a single Product Owner who is accountable for: relaying decisions, providing timely feedback on artifacts, deliverables, and questions, acceptance of deliverables, and prioritization decisions
- Provide access to Subject Matter Experts as needed for requirements validation and UAT
- Attend scheduled meetings (bi-weekly sprint demos, milestone reviews, stakeholder updates)
- Follow processes and workflows determined by Orases
- Reading, reviewing, and approving requirements documentation

**Review and Approval Cycles**:
- CLIENT responsible for ongoing UAT and timely acceptance of the Deliverables, the cadence of which will be set by the project team
- Provide design approval within 2 weeks of submission (target: Week 16)
- Provide feedback on sprint deliverables within 5 business days
- Provide feedback on phase deliverables within 15 business days
- Legal review of customer communications (privacy notices, terms of service) within 1 week
- Marketing content review within 3 business days

**Infrastructure and Environment**:
- Provide access to existing infrastructure and integration points (Commerce CRM, Dynamics CRM, Duke Data Fabric)
- Provide or approve cloud infrastructure (AWS) for development, staging, and production environments
- Provide app store developer accounts (iOS, Android) by Week 32
- Security team review and approval of architecture by Week 8
- Security team penetration testing approval by Week 32
- Production infrastructure and deployment approval by Week 36

**Ongoing Responsibilities**:
- Notify Orases in advance of significant business changes (stakeholder changes, leave of absence, potential timeline bottlenecks, business case changes, etc.)
- Hold at least monthly Stakeholder meetings with project sponsors and Orases
- Define initial 5-10 ad-hoc services (service name, description, scope of work, pricing) by Week 8
- Ensure minimum 25 contractors participate in Phase 1 pilot program across pilot markets
- Provide ongoing hosting costs ($800/month estimated for AWS infrastructure)

- - - - - - - - - - - - - - - - - - - -

## 03 Estimated Timeline

Based on Initial Discovery (Exhibit A) conducted without Duke's technical team, Orases anticipates the project will follow a **phased delivery approach** with an estimated total duration of approximately **11 months** from the Effective Date.

**IMPORTANT**: Specific timeline and milestones will be established after Analysis Activities (Section 1.1) when Round 2 discovery with Duke's technical team is complete and scope is validated.

### Phase-Based Delivery Approach

The project will be delivered in the following sequential phases. Duration of each phase will be determined after Analysis Activities based on validated scope and technical complexity:

| Phase | Key Activities | Key Deliverables | Phase Complete When |
|-------|----------------|------------------|---------------------|
| **Phase 0: Analysis & Planning** | Round 2 discovery with Duke's tech team, requirements validation, technical feasibility assessment, architecture design, UI/UX wireframes, cost/timeline refinement | Technical architecture documentation, clickable prototype, validated scope document, detailed timeline with milestones, updated budget estimate, risk assessment | CLIENT approves validated scope, timeline, and budget; authorizes proceeding to Phase 1 |
| **Phase 1: Design & Foundation** | UI/UX design finalization, design system creation, technical specifications, database schema design, API specifications, infrastructure setup, CI/CD pipeline | UI/UX designs approved by CLIENT, technical specifications approved, acceptance criteria defined, development environment operational, foundational architecture in place | CLIENT approves designs and specifications; development team ready to begin feature implementation |
| **Phase 2: Core Development** | Sprint-based iterative development of prioritized features, customer app (iOS/Android/web), admin portal, backend APIs, contractor matching algorithm, Duke API integrations | Working software increments delivered every 2 weeks, functional features available for CLIENT review and feedback | Agreed-upon MVP feature set is functionally complete (per prioritized backlog from Phase 0) |
| **Phase 3: Integration & Refinement** | System integration testing, Duke CRM integration validation, third-party service integration, admin portal completion (all 7 roles), notification system, bug fixes from CLIENT feedback | Integrated system with all components working together, all MVP features complete and refined based on CLIENT feedback, Alpha release candidate | CLIENT validates integrated system meets acceptance criteria; ready for formal testing |
| **Phase 4: Testing & Security** | UAT with CLIENT team, security testing, penetration testing, performance testing, compliance review, bug fixes, SOC 2/ISO 27001 certification | Security testing complete, penetration test report with all HIGH/CRITICAL issues remediated, performance benchmarks met, SOC 2 Type 2 or ISO 27001 certificate, Beta release candidate | CLIENT UAT complete with acceptance; security compliance certified; performance validated |
| **Phase 5: Deployment & Launch** | Production environment setup, app store submissions and approvals, admin training, go-live preparation, production deployment, launch support | App store approvals (iOS/Android), admin users trained, production environment live, monitoring configured, system in production serving customers | System successfully deployed to production; CLIENT declares go-live complete |
| **Phase 6: Warranty & Stabilization** | Post-launch support, bug fixes, stabilization, performance optimization, warranty period (90 days from launch) | Stable production system, warranty period complete, production support documentation | 90-day warranty period complete; system stable and ready for ongoing support handoff (if CLIENT opts for post-warranty support per Section 10) |

### Critical Path Milestones

The following milestones represent critical decision points and dependencies. Specific timing will be established after Phase 0 (Analysis & Planning) is complete:

**Phase 0 Completion Gate**:
- Analysis Activities complete with validated scope, timeline, and budget
- CLIENT reviews and approves recommendation to proceed with Phase 1
- **This is the primary decision gate** - all subsequent timeline depends on validated plan from Phase 0

**Early Dependencies** (required for Phase 0):
- API documentation and sandbox access provided by CLIENT (target: within 2 weeks of kickoff)
- Contractor data export provided by CLIENT (target: within 4 weeks of kickoff)
- Duke technical team available for Round 2 discovery (target: 10-15 hours/week during Phase 0)

**Design Approval Gate** (between Phase 1 and Phase 2):
- UI/UX designs and technical specifications approved by CLIENT
- Acceptance criteria agreed upon
- Development team authorized to begin feature implementation

**Alpha Release Gate** (between Phase 2 and Phase 3):
- Core MVP features functionally complete
- CLIENT reviews Alpha release and provides feedback
- Decision to proceed with integration and refinement

**Beta Release Gate** (between Phase 3 and Phase 4):
- Integrated system with all MVP features complete
- CLIENT validates Beta release meets requirements
- Authorization to proceed with formal testing and security certification

**Production Readiness Gate** (between Phase 4 and Phase 5):
- UAT complete with CLIENT acceptance
- Security compliance certified (SOC 2 Type 2 OR ISO 27001)
- App store approvals obtained
- CLIENT authorizes production deployment

**Launch Complete** (between Phase 5 and Phase 6):
- Production deployment successful
- System serving customers
- Monitoring operational
- Warranty period begins

### Estimated Phase Durations

Based on Initial Discovery, the following phase durations are **rough estimates only** and will be refined after Phase 0 completes:

| Phase | Estimated Duration | Notes |
|-------|-------------------|-------|
| **Phase 0: Analysis & Planning** | 8-12 weeks | Duration depends on Duke tech team availability and complexity discovered |
| **Phase 1: Design & Foundation** | 4-6 weeks | Duration depends on CLIENT review/approval cycles |
| **Phase 2: Core Development** | 12-20 weeks | Duration depends on validated scope complexity and prioritization |
| **Phase 3: Integration & Refinement** | 6-10 weeks | Duration depends on integration complexity and feedback volume |
| **Phase 4: Testing & Security** | 6-10 weeks | Duration depends on UAT findings, security compliance timeline, app store review times |
| **Phase 5: Deployment & Launch** | 2-4 weeks | Duration depends on Duke IT approval processes |
| **Phase 6: Warranty & Stabilization** | 12+ weeks | 90-day warranty period from production launch |
| **Total Estimated** | **40-60 weeks** (~**11 months** average) | Range reflects uncertainty; will be refined after Phase 0 |

**IMPORTANT**: These duration estimates are based on Initial Discovery conducted without Duke's technical team and carry significant uncertainty. After Phase 0 (Analysis & Planning) completes, Orases will provide a detailed timeline with specific milestones, dependencies, and confidence levels for CLIENT approval before proceeding to Phase 1.

### Timeline Dependencies and Assumptions

Project timeline depends on the following critical dependencies:

**CLIENT Dependencies**:
- Duke technical team available for Round 2 discovery during Phase 0 (estimated 10-15 hours/week)
- API documentation and sandbox access provided during Phase 0 (target: within 2 weeks of kickoff)
- Contractor data export provided during Phase 0 (target: within 4 weeks of kickoff)
- Duke Enterprise APIs available by end of Phase 0 (Customer Validation, HPP Plans at minimum)
- CLIENT design approval within agreed timeframe (target: 2 weeks from submission)
- CLIENT UAT participation during Phase 4 with timely feedback
- Duke IT security reviews and approvals at each gate (architecture, penetration test, production)
- App store developer accounts provided during Phase 4 (before app store submissions)
- No major scope changes after Design Approval Gate (between Phase 1 and Phase 2)

**Technical Dependencies**:
- No major technical blockers discovered during Phase 0 that invalidate Initial Discovery assumptions
- Commerce CRM and Dynamics CRM integration feasible as anticipated (or acceptable alternatives identified)
- Duke IT infrastructure supports planned architecture (or constraints identified and accommodated in Phase 0)
- Third-party services (CPSC, barcode APIs, SMS, email, push notifications) available and stable
- Security compliance (SOC 2 Type 2 OR ISO 27001) certification process completed during Phase 4

**Orases Commitments**:
- Orases team resources available as planned
- No significant turnover of key Orases personnel
- Technology stack performs as anticipated (React Native, Vue.js, Laravel, AWS)

### Timeline Risk Factors

Timeline may extend beyond estimated 11 months if:
- **Phase 0 Findings**: Round 2 discovery reveals significantly higher complexity than Initial Discovery anticipated (integration complexity, security requirements, API limitations, technical constraints)
- **API Availability**: Duke APIs not available as anticipated, requiring development of more complex manual fallback workflows or alternative approaches
- **Integration Complexity**: Commerce/Dynamics CRM integration significantly more complex than Initial Discovery estimated
- **Review Cycles**: CLIENT review and approval cycles exceed targets (design approval >2 weeks, phase gate approvals delayed, UAT feedback cycles extended)
- **Scope Changes**: Major scope changes requested by CLIENT after Design Approval Gate
- **Infrastructure Constraints**: Production deployment constraints or CLIENT IT infrastructure limitations requiring rework
- **Third-Party Dependencies**: External service integrations (CPSC, barcode APIs, SMS, email) require more effort than anticipated
- **Security/Compliance**: Security compliance certification or penetration testing reveals issues requiring significant remediation
- **App Store Delays**: iOS or Android app store review processes encounter rejections or extended review times

### Timeline Communication and Variance Management

**Timeline Updates**:
- After Phase 0 completes: Detailed timeline with specific milestones provided to CLIENT for approval
- At each phase gate: Updated timeline forecast with any adjustments based on actual progress
- Monthly: Timeline status included in monthly financial reports per Section 9.2
- When variance anticipated: Proactive notification per Section 9.3 if timeline will extend significantly

**Variance Notification Threshold**:
- If timeline extends beyond **13 months (56 weeks)** from Effective Date, Orases will notify CLIENT per Section 9.3 (Variance Management) and provide:
  - Root cause analysis of timeline variance
  - Updated timeline forecast with revised phase durations
  - Options for CLIENT consideration (continue as planned, adjust scope to accelerate, add resources, etc.)

**CLIENT Options Upon Variance**:
- Continue as planned and accept extended timeline
- Adjust scope to reduce timeline (descope lower-priority features)
- Request feasibility assessment for timeline acceleration (may require additional cost)
- Pause project for comprehensive review and replanning

Timeline will be tracked and reported via bi-weekly status reports per Section 9.2 (Budget and Progress Reporting). Specific milestones and deliverable dates will be agreed upon after Phase 0 completes and throughout the project per Section 9 (Project Governance and Transparency).

- - - - - - - - - - - - - - - - - - - -

## 04 Payment Schedule and Cost

CLIENT shall pay the fees to be calculated using the rate set forth below for the total number of hours worked by Orases, plus any and all Costs (as defined below) incurred by Orases during the applicable billing period.

### Time and Materials Rate

The Services will be performed on a time and materials basis and will be invoiced at a blended rate of **$250/hour**, in addition to any and all third party costs incurred by Orases and/or any fixed fee configurable components used in providing the Services and/or Deliverables hereunder (collectively, "Costs"); invoices will be sent once a month (at the end of the month). Orases reserves the right to revise its rate schedule upon 90 days' prior written notice to CLIENT, but no more often than once per year.

### Planning Budget Estimate

Based on Initial Discovery (Exhibit A) conducted without Duke's technical team, Orases estimates the total project cost to be approximately **$788,600**, allocated as follows:

| Component | Estimated Amount | Percentage | Description |
|-----------|------------------|------------|-------------|
| **CX Interface Development** | $285,225 | 36.1% | Customer mobile apps (iOS/Android), responsive web app, UI/UX design, frontend development |
| **Backend Development** | $332,083 | 42.0% | APIs, business logic, database, integrations, contractor matching algorithm, notification system |
| **DevOps & Security** | $171,292 | 21.7% | Cloud infrastructure, CI/CD, security implementation, monitoring, SOC 2/ISO 27001 certification |
| **Total Estimated** | **$788,600** | **100%** | Total anticipated cost for Phase 1 |

**Note on Bridge Functionality**: The budget estimate above includes approximately $177,750 for "bridge functionality" - temporary features and abstraction layers to enable MVP launch before FSM tool and certain Duke APIs are available. This includes:
- Manual admin workflows and service request processing tools ($152,250 estimated)
- Abstraction layer architecture to minimize future rework ($25,500 estimated)
- When FSM tool and Duke APIs become available (estimated 6-12 months post-launch), Phase 2 rework of approximately $46,000 will be required (separate SOW)

### Important Notes Regarding Budget Estimate

1. **This is a planning estimate, not a cap or commitment.** Actual costs will be based on time and materials at the rate specified above ($250/hour). The estimate is provided to enable CLIENT budget planning and internal approvals.

2. **Estimate is subject to refinement** after Round 2 discovery with Duke's technical team (Analysis Activities, Section 1.1). Scope, timeline, and cost may increase or decrease based on:
   - API availability and capabilities (Service Request Creation API, Enrollment API)
   - Integration complexity with Duke's Commerce and Dynamics CRM systems
   - Security and compliance requirements and implementation effort
   - Technical feasibility of features identified in Initial Discovery
   - Duke IT infrastructure constraints, approval processes, and deployment procedures
   - Discovery of technical blockers or dependencies not identified in Initial Discovery

3. **Orases will provide updated estimates** after completing Analysis Activities (Section 1.1) and before beginning Design, Development, and Implementation (Section 1.3). Updated estimates will include:
   - Refined scope based on technical validation
   - Updated timeline with dependencies and risks
   - Updated cost forecast with confidence level (low/medium/high)
   - Risk assessment and mitigation strategies

4. **Transparency and Communication**: Orases will provide regular statements and updates regarding the fees incurred on the actual time spent for functionality delivered and the anticipated cost of functionality to be delivered based on the confidence level of scope at the time. Both Orases and CLIENT agree to work in good faith to make decisions and functionality choices that balance the spirit of the requirements and the overall budget.

5. **Variance Notification**: If at any point during the project Orases anticipates that total costs will exceed the planning estimate by more than **15% ($118,290 variance threshold)**, Orases will notify CLIENT in writing within 5 business days of such determination, providing:
   - Explanation of drivers for variance (scope changes discovered during development, technical complexity greater than anticipated, integration challenges, CLIENT-requested changes, etc.)
   - Updated cost forecast with confidence level
   - Recommendations for cost mitigation (if applicable), such as descoping lower-priority features, adjusting implementation approach, or phasing delivery
   - Options for CLIENT consideration (continue as planned and accept variance, adjust scope to stay closer to original estimate, pause for comprehensive review, or proceed with modified approach)

6. **CLIENT retains full control**: CLIENT may at any time:
   - Request a pause in work (no more than 2 weeks) to review progress, costs, and priorities
   - Request comprehensive status report and financial review
   - Request detailed timesheets for any billing period
   - Request scope adjustments to manage budget
   - Upon such request, Orases will provide requested documentation within 5 business days

### Team Size and Resource Adjustments

CLIENT may request to expand or reduce the hours spent by Orases to provide the Services and/or create the Deliverables. Any request to expand the Services or Deliverables shall be subject to the procedures set forth in this Section 4 and the terms of Section 5 of this SOW (Change Order Process).

After Orases establishes the initial number of hours and resources to be assigned for the work to be completed, if CLIENT wants Orases to change the number of hours or team size assigned to this SOW, it shall submit to Orases a written request for such change(s) with no less than 30 days' advanced written notice. Orases will notify CLIENT within 15 days after receiving any such notice, if CLIENT's request is not feasible and will discuss alternative arrangements. Orases and CLIENT will cooperate in good faith and with due diligence to address any changes reasonably requested by CLIENT.

### Payment Terms

All Costs to be paid to Orases pursuant to this SOW shall be subject to Section II.A. (Consideration, Payment, Finance Charge and Expenses) of the Agreement.

Invoices will include:
- Detailed breakdown of hours worked by role/activity
- Description of work performed during billing period
- Third-party costs with supporting documentation
- Cumulative hours and costs to date
- Progress against planning budget estimate

Payment terms: Net 90 days from receipt of correct and undisputed invoice.

### Additional Costs (Not Included in Project Budget)

The following costs are not included in the $788,600 planning budget estimate:

| Item | Estimated Amount | Responsible Party | Frequency | Notes |
|------|------------------|-------------------|-----------|-------|
| **SOC 2 Type 2 Audit OR ISO 27001 Certification** | $20,000 - $40,000 | Orases | Annual | Required by Master Services Agreement Section 10.2, at Orases expense |
| **Hosting Infrastructure (AWS)** | $800/month | CLIENT | Monthly | Development, staging, and production environments; scales with user growth |
| **Support & Maintenance (Optional)** | $6,500/month | CLIENT | Monthly | Post-warranty support (see Section 10); optional, requires separate agreement |
| **Phase 2 Rework (FSM Integration)** | $46,000 estimated | CLIENT | One-time | When FSM tool available (6-12 months post-launch); requires separate SOW |

- - - - - - - - - - - - - - - - - - - -

## 05 Change Order Process

If during the Term of this SOW CLIENT requests a change to any Deliverables that is beyond the scope or budget of the applicable SOW, Orases shall provide in writing to CLIENT a written estimate of required hours to execute CLIENT's new request, whereupon CLIENT may choose in writing to:

(1) **Swap Features**: Remove another feature of comparable effort from the subject Deliverables that is yet to be developed, and substitute the new, higher priority feature in its place; OR

(2) **Defer to Future Phase**: Have the new feature scheduled to be completed as a separate mini-project, post-launch, subject to the negotiation and execution of a new SOW; OR

(3) **Approve Additional Budget**: Approve and sign a formal "change request estimate" and have the additional estimated hours added to the project budget and timeline under this SOW.

### Change Order Documentation

Each Change Order will include:
- Change Order ID and date submitted
- Description of requested change
- Rationale/business justification
- Scope impact (features added/removed/modified)
- Timeline impact (weeks delay or acceleration)
- Budget impact (additional hours and cost)
- Risks and dependencies
- Approvals (CLIENT signature, Orases signature)

### Scope Clarifications (No Change Order Required)

Minor clarifications that do not materially impact scope, timeline, or budget do not require formal Change Order and may be documented via email or sprint notes. Examples include:
- Wording changes to user interface text
- Minor UI adjustments within approved design system
- Field label or validation message changes
- Bug fixes or defect corrections

### Emergency Changes

CLIENT may issue written change directive for emergency situations requiring immediate action. Orases will proceed with work immediately and provide impact assessment within 2 business days after emergency resolved. Change Order will be executed retroactively.

- - - - - - - - - - - - - - - - - - - -

## 06 Travel

Any travel expenses for travel, including to CLIENT offices in Charlotte, NC by any Orases employee shall be subject to the terms and procedures set forth in the Agreement and the following additional terms as set forth in this SOW.

Any time spent by Orases traveling including to/from the CLIENT's offices shall be billed at the hourly rate set forth in Section 4 ($250/hour).

Orases will submit approved expenses (and applicable receipts) on an invoice payable by CLIENT as follows:
- Auto mileage: Current standard IRS reimbursement rates apply
- Airfare: Actual cost (economy class)
- Hotel: Actual cost (standard business hotel rates)
- Per Diem: GSA applicable rate for Charlotte, NC
- Car Rental: Actual cost (standard rental vehicle)

Orases estimates 1 trip to CLIENT Headquarters and does not anticipate any additional travel at this time. Any additional travel beyond 1 trip will be pre-approved by CLIENT before booking.

All approved expenses to be paid to Orases shall be subject to Section II.A. (Consideration, Payment, Finance Charge and Expenses) of the Agreement.

- - - - - - - - - - - - - - - - - - - -

## 07 Term

The term of this SOW shall commence as of the Effective Date (January 5, 2026) and shall continue in effect until **December 31, 2026**, unless extended upon the mutual agreement of the parties (for which email shall suffice).

In the event the Agreement is terminated at an earlier date pursuant to the Agreement, this SOW shall automatically terminate as of the termination date of the Agreement.

Either party may terminate this SOW:
- For convenience with 30 days' written notice
- For cause if the other party materially breaches this SOW and fails to cure within 30 days of written notice
- Immediately if the other party becomes insolvent, files for bankruptcy, or ceases business operations

Upon termination:
- CLIENT shall pay for all work performed through the date of termination at the rates specified in Section 4
- Orases shall deliver all work product completed through the date of termination
- Orases shall return or destroy all CLIENT confidential information per the Agreement
- All intellectual property rights in deliverables completed through termination date shall transfer to CLIENT per Section 11 (Intellectual Property Rights)

- - - - - - - - - - - - - - - - - - - -

## 08 Communications

The contact information for CLIENT's initial representative for purposes of this SOW is as follows:

**Name**: [To be completed by CLIENT]
**Title**: [To be completed by CLIENT]
**Address**: 525 South Tryon St., Charlotte, NC 28202
**Phone**: [To be completed by CLIENT]
**Email**: [To be completed by CLIENT]

Such representative has complete authority to make decisions on behalf of CLIENT with respect to this SOW including, without limitation, the approval of any element of the Deliverables and all issues regarding any Rejection Notice or Change Request.

**ANY TELEPHONE OR VIDEO CALLS BETWEEN CLIENT AND ORASES REGARDING THE SERVICES MAY BE RECORDED AND USED FOR QUALITY ASSURANCE AND TRAINING PURPOSES BY ORASES. CLIENT MUST NOTIFY ORASES IF IT OBJECTS TO ANY SUCH RECORDINGS.**

PROJECT-LEVEL CONTACTS:

**Orases Project Manager**: [To be assigned at project kickoff]
**Duke Product Owner**: [To be designated by CLIENT]
**Duke Technical Lead**: [To be designated by CLIENT]

- - - - - - - - - - - - - - - - - - - -

## 09 Project Governance and Transparency

To ensure effective collaboration and mutual understanding throughout this time-and-materials engagement, the parties agree to the following governance protocols:

### 9.1 Sprint-Based Progress Tracking

- Work will be organized in **2-week sprints**
- Each sprint will have defined objectives agreed upon by both parties at sprint planning
- Sprint demos will be conducted bi-weekly with CLIENT stakeholders to demonstrate completed work
- Sprint retrospectives will identify lessons learned and process improvements
- Sprint objectives locked at sprint start; new requests deferred to subsequent sprints unless both parties agree otherwise

### 9.2 Budget and Progress Reporting

Orases will provide CLIENT with the following reports to maintain transparency and enable informed decision-making:

**Bi-Weekly Status Reports** including:
- Hours worked by role/activity for the sprint (e.g., Frontend Development: 80 hours, Backend Development: 60 hours, DevOps: 20 hours)
- Cumulative hours and costs to date
- Progress against current phase objectives (percentage complete, features delivered)
- Risks, issues, and blockers with mitigation strategies
- Upcoming sprint objectives and planned deliverables
- Any anticipated variances from plan

**Monthly Financial Reports** including:
- Total costs incurred month-to-date and project-to-date
- Comparison to planning budget estimate ($788,600) with variance analysis
- Forecast of costs to complete remaining anticipated scope (burn rate analysis and projection)
- Confidence level of forecast (low/medium/high based on scope certainty)
- Explanation of any significant variances (>10% from previous forecast)
- Breakdown of costs by component (CX Interface, Backend, DevOps)

**Milestone Reviews** at key decision points:
- **Week 12** (End of Analysis Activities): Comprehensive review including refined scope, detailed timeline with milestones, updated cost forecast with confidence level, risk assessment, recommendation to proceed or adjust
- **25% Budget Consumed**: Progress review, validate forecast, assess risks, confirm approach
- **50% Budget Consumed**: Comprehensive mid-project review, validate remaining scope and budget, adjust plan if needed
- **75% Budget Consumed**: Final scope validation, completion forecast, prepare for deployment and warranty
- **Week 40** (Production Launch): Go-live review, warranty period kickoff, lessons learned

### 9.3 Variance Management

If Orases determines that any of the following conditions exist, Orases will proactively notify CLIENT:

**Variance Triggers**:
- Total costs will exceed planning estimate by **>15% ($118,290 variance threshold)**, OR
- Timeline will extend beyond anticipated duration by **>4 weeks (48 weeks total)**, OR
- Significant technical blockers discovered that require material scope changes, OR
- Integration with CLIENT systems significantly more complex than anticipated, OR
- CLIENT dependencies (API availability, approvals, data access) delayed beyond assumptions

**Variance Notification Process**:

Within **5 business days** of determining variance trigger met, Orases will provide CLIENT with written notification including:
- Root cause analysis of variance (what changed, why, when discovered)
- Impact assessment (scope impact, timeline impact, budget impact)
- Recommended corrective actions or alternatives (descope features, adjust approach, extend timeline, add resources)
- Updated forecast with revised assumptions
- Request for CLIENT direction on path forward

CLIENT will respond within **10 business days** with direction to:
- **Continue as planned**: Accept variance and proceed with current approach
- **Adjust scope**: Descope lower-priority features to stay within budget/timeline
- **Pause for review**: Pause work (up to 2 weeks) for comprehensive review and replanning
- **Modify approach**: Approve alternative implementation approach recommended by Orases
- **Terminate**: Terminate engagement per Section 7 (Term)

### 9.4 CLIENT Review Rights

CLIENT may at any time exercise the following review rights:

- Request detailed timesheets for any billing period (including employee name, role, hours worked, activities performed)
- Request comprehensive project status review meeting (to be scheduled within 5 business days)
- Request pause in work (no more than 2 weeks) to assess progress, costs, and deliverables
- Request independent review of deliverables, code quality, security posture, or technical approach
- Request access to source code repository for inspection
- Request demonstration of any completed features or work in progress

Upon such request, Orases will cooperate fully and provide requested documentation or access within **5 business days**.

### 9.5 Decision Log

Both parties will maintain a **shared decision log** documenting all major project decisions. Decision log will be maintained in Orases' project management system with CLIENT access.

Decision log will document:
- Date of decision
- Decision description and context
- Options considered and trade-off analysis
- Selected approach and rationale
- Technical constraints or dependencies that influenced decision
- Budget/timeline impact of decision
- Approvers (CLIENT Product Owner, Orases Project Manager, others as applicable)
- Link to supporting documentation

**Examples of decisions requiring documentation**:
- Technology stack selections (if deviating from anticipated approach)
- Major architecture decisions (e.g., abstraction layer design, API integration patterns)
- Scope adjustments (features added, removed, or modified)
- Trade-off decisions (e.g., manual workflow vs. automated, temporary solution vs. waiting for API)
- Security or compliance approach decisions
- Deployment strategy decisions

Decision log will be reviewed at each milestone review (Section 9.2) to ensure alignment and shared understanding.

### 9.6 Escalation Path

For issues requiring executive attention beyond project team resolution:

**Escalation Triggers**:
- Budget variance >20% ($157,720) with no clear path to mitigation
- Timeline slip >6 weeks (50 weeks total) with no clear path to acceleration
- Technical feasibility concerns that threaten project viability
- Scope disagreements that cannot be resolved at project team level
- CLIENT dependency delays threatening project timeline
- Quality concerns or repeated deliverable rejections

**Escalation Process**:
- Either party may escalate to executive sponsors via written notification
- Escalation notification must include: issue description, impact, options considered, recommended resolution, urgency level
- Executive sponsors will meet within **5 business days** to review and resolve
- Executive sponsors: [CLIENT VP/Director to be designated], [Orases Executive to be designated]
- If executive sponsors cannot resolve, issue escalates to Agreement governance per Master Services Agreement

### 9.7 Agile Ceremonies and Cadence

The following recurring meetings will be scheduled to maintain alignment and transparency:

| Meeting | Frequency | Duration | Attendees | Purpose |
|---------|-----------|----------|-----------|---------|
| **Sprint Planning** | Every 2 weeks | 2 hours | Product Owner, Project Manager, Tech Lead | Define sprint objectives and commit to deliverables |
| **Daily Standup** | Daily | 15 min | Orases development team | Internal sync on progress, blockers (CLIENT optional) |
| **Sprint Demo** | Every 2 weeks | 1 hour | Product Owner, stakeholders, project team | Demonstrate completed work, gather feedback |
| **Sprint Retrospective** | Every 2 weeks | 1 hour | Product Owner, project team | Lessons learned, process improvements |
| **Stakeholder Update** | Monthly | 1 hour | Executives, sponsors, product owner | High-level progress, budget, risks, decisions needed |
| **Milestone Review** | Per Section 9.2 | 2 hours | Executives, sponsors, project team | Comprehensive review at key milestones |

- - - - - - - - - - - - - - - - - - - -

## 10 Warranty and Support

### 10.1 Warranty Period

**Warranty period: 90 days** from production launch (final acceptance per Section 1.4).

During the warranty period, Orases will provide bug fixes and defect corrections at no additional cost to CLIENT.

### 10.2 Warranty Coverage

Per Master Services Agreement Section 5, Orases warrants that:

1. **Professional Standards**: Services performed with high level of accepted professional standards by qualified personnel

2. **Conformance to Specifications**: Services and deliverables conform to SOW specifications and are free from errors and defects in workmanship and materials

3. **No Malicious Code**: Software does not contain trojan horses, viruses, disabling code, timers, clocks, counters, or other limiting routines

4. **No Infringement**: Software does not infringe upon patent, copyright, or other legal rights of any third party

5. **Authority to Contract**: Orases has authority to enter into this SOW and performance is not prohibited by any other agreement

### 10.3 Warranty Remedies

Orases shall, at CLIENT's option, either **re-perform** or **refund** applicable fees for services/deliverables that fail to meet warranty.

Orases is liable for all damages incurred by CLIENT from warranty breach (not limited to re-perform/refund), subject to limitations in the Master Services Agreement.

If Orases fails to commence corrective action within reasonable timeframe specified by CLIENT, CLIENT may fix defects itself or hire third party and back-charge Orases for reasonable costs incurred.

### 10.4 Warranty Exclusions

Warranty does not cover:
- Defects caused by CLIENT modifications to deliverables after acceptance
- Defects caused by third-party software, hardware, or services outside Orases control
- Issues caused by CLIENT's failure to implement Orases recommendations
- Issues caused by CLIENT's IT environment, infrastructure, or configuration (if outside Orases control and not specified in acceptance criteria)
- Changes in CLIENT's business requirements after acceptance
- Force majeure events (natural disasters, pandemics, wars, etc.)

### 10.5 Post-Warranty Support (Optional)

After 90-day warranty period, CLIENT may opt for ongoing support and maintenance. Post-warranty support requires separate agreement and is not included in this SOW.

**Anticipated Support & Maintenance Plan**: $6,500/month (optional)

Anticipated to include:
- Bug fixes for defects discovered after warranty period
- Security patches and updates
- Performance optimization and tuning
- 8x5 support (business hours: Monday-Friday 8am-5pm ET)
- Email and phone support with 4-hour response time (business hours)
- Monthly status reports
- Quarterly product roadmap reviews

**NOT Included in Anticipated Support Plan**:
- New feature development (requires separate SOW or Change Order)
- Hosting infrastructure costs (CLIENT pays AWS directly)
- Third-party API changes requiring significant rework
- Phase 2 rework when FSM tool and Duke APIs available (requires separate SOW)
- Major version upgrades of underlying technology stack
- Scope expansion or significant functionality changes

- - - - - - - - - - - - - - - - - - - -

## 11 Intellectual Property Rights

Per Master Services Agreement Section 6:

### 11.1 CLIENT Owns All Deliverables

CLIENT owns all rights, title, and interests in deliverables and intellectual property created under this SOW, including:
- Trademark rights
- Patent rights
- Copyrights
- Trade secret rights
- All other intellectual property rights

Deliverables are deemed "works made for hire" under U.S. Copyright Law. Orases assigns all rights to CLIENT upon creation of each deliverable, including all United States and international rights.

### 11.2 Deliverables Provided to CLIENT

Orases will provide to CLIENT:
- Full and complete source code for all software deliverables
- All data, graphics, files, assets used to create deliverables
- All files necessary for proper operation, modification, and maintenance of deliverables
- Documentation of any pre-existing third-party software, libraries, or frameworks incorporated into deliverables
- Technical documentation, architecture diagrams, data models, API specifications
- Admin user guides and training materials

### 11.3 Pre-Existing Third-Party Software

Orases may incorporate pre-existing works (open-source libraries, frameworks, third-party components) into deliverables ONLY IF Orases causes CLIENT to obtain **perpetual, irrevocable, nonexclusive, worldwide, royalty-free, fully paid-up license** to:
- Use, copy, execute, reproduce, display, perform, and distribute
- Create derivative works and modifications
- Sublicense to others (including for white-label use with other utilities)

**Pre-Existing Third-Party Software Anticipated to be Used**:
- Laravel framework (open-source, MIT license)
- React Native (open-source, MIT license)
- Vue.js (open-source, MIT license)
- PostgreSQL or MySQL (open-source licenses)
- Redis (open-source, BSD license)
- Various npm packages and composer packages (licenses to be documented in deliverables)

Orases will maintain a **Software Bill of Materials (SBOM)** documenting all third-party components, their licenses, and version numbers. SBOM will be provided to CLIENT with final deliverables.

### 11.4 Orases Proprietary Code or Frameworks

If Orases incorporates any proprietary code, frameworks, or tools owned by Orases into deliverables, Orases grants CLIENT perpetual, royalty-free, worldwide license to:
- Use for this project and future projects
- Modify and create derivative works
- Sublicense to others as needed for CLIENT's business purposes (including white-label platform for other utilities)

CLIENT may not resell Orases proprietary code/frameworks as standalone products, but may use them as part of CLIENT's integrated solutions.

### 11.5 CLIENT Data Remains CLIENT Property

All customer data, HPP plans, contractor data, service requests, and other data provided by CLIENT or collected through the application remains CLIENT property. Orases has no rights to CLIENT data.

Upon project completion or termination, Orases will return or destroy all CLIENT data per Master Services Agreement Section 10.1.I.

- - - - - - - - - - - - - - - - - - - -

## 12 Security and Compliance

### 12.1 Security Requirements

Per Master Services Agreement Section 10.2, Orases will implement security controls meeting or exceeding industry standards:

**Data Protection**:
- Encryption at rest and in transit (NIST standards: AES-256 for data at rest, TLS 1.2+ for data in transit)
- Role-based access control (RBAC) for admin portal with principle of least privilege
- Multi-factor authentication (MFA) for all admin users
- Secure password storage using industry-standard hashing (bcrypt or better)
- API security with JWT authentication, rate limiting, and input validation

**Application Security**:
- OWASP Top 10 compliance (protect against injection, broken authentication, sensitive data exposure, XXE, broken access control, security misconfiguration, XSS, insecure deserialization, components with known vulnerabilities, insufficient logging)
- Security headers (Content Security Policy, HTTP Strict Transport Security, X-Frame-Options, X-Content-Type-Options)
- Input validation and output encoding to prevent injection attacks
- Secure session management
- Protection against CSRF attacks

**Infrastructure Security**:
- VPC with private subnets for databases and internal services
- Security groups and network ACLs limiting access
- Web Application Firewall (WAF) for production environment
- Intrusion detection and prevention
- Regular security patching of operating systems and dependencies

**Monitoring and Incident Response**:
- Comprehensive logging of authentication, authorization, and data access events
- Real-time monitoring and alerting for security events
- Incident response plan and procedures
- 24-hour breach notification to CLIENT (30 minutes for critical cyber systems) per Master Services Agreement Section 10.2.A

### 12.2 Compliance Certification

Per Master Services Agreement Section 10.2, Orases will obtain one of the following compliance certifications at Orases expense:

**Option A: SOC 2 Type 2 Audit** (estimated $20,000-$30,000 annually)
- Service Organization Control 2 Type 2 report
- Trust Service Criteria: Security, Availability, Processing Integrity, Confidentiality, Privacy
- Annual recertification required

**Option B: ISO 27001 Certification** (estimated $30,000-$40,000 annually)
- International Organization for Standardization 27001 Information Security Management System certification
- Comprehensive security management framework
- Annual recertification required

CLIENT will specify preferred certification (SOC 2 Type 2 OR ISO 27001) by Week 4. Certification process will begin by Week 20 to ensure completion by Week 32.

### 12.3 Security Testing

Security testing will be conducted prior to production launch:

**Penetration Testing** (Week 32):
- External penetration test by qualified third-party firm
- Test scope: web applications, APIs, mobile apps, infrastructure
- All HIGH and CRITICAL vulnerabilities remediated before production launch
- Penetration test report provided to CLIENT

**Security Code Review**:
- Automated static code analysis during development (integrated into CI/CD pipeline)
- Manual code review of authentication, authorization, and data handling code
- Dependency vulnerability scanning (npm audit, composer audit)

**Compliance Review**:
- OWASP Top 10 compliance validation
- Security checklist review (encryption, access control, logging, etc.)
- Privacy and data protection compliance (GDPR, CCPA principles as applicable)

### 12.4 Breach Notification and Liability

Per Master Services Agreement Section 10.2.A, if Orases experiences a security breach involving CLIENT data:

**Notification Timeline**:
- Within 24 hours for general security incidents
- Within 30 minutes for critical cyber system incidents

**Orases Responsibilities**:
- Immediate investigation and containment
- Root cause analysis and remediation
- Forensic investigation at Orases expense
- Notification to affected individuals at Orases expense
- Credit monitoring services for affected individuals at Orases expense
- Legal fees and costs associated with breach response at Orases expense

**Unlimited Liability**: Orases has unlimited liability for security breaches per Master Services Agreement. Orases maintains cybersecurity insurance to cover breach-related costs.

- - - - - - - - - - - - - - - - - - - -

## 13 Risk Allocation

### 13.1 Orases Responsibilities and Risks

Orases is responsible for and bears the risk of:

**Development and Quality**:
- Software development per agreed specifications (sprint objectives, acceptance criteria)
- Quality assurance and testing (unit tests, integration tests, security tests, performance tests)
- Bug fixes and defect corrections during development and warranty period (90 days)
- Code quality meeting professional standards (OWASP Top 10 compliance, secure coding practices)
- Source code delivery with complete documentation

**Security and Compliance**:
- Security implementation per Section 12 (Security and Compliance)
- Security compliance certification (SOC 2 Type 2 OR ISO 27001) at Orases expense ($20K-$40K annually)
- Security breach notification costs, forensic investigation, credit monitoring, legal fees (unlimited liability per Master Services Agreement)
- Annual recertification of security compliance at Orases expense

**Architecture and Design**:
- Abstraction layer architecture to minimize Phase 2 rework when FSM tool and Duke APIs become available
- Scalable architecture supporting anticipated user growth (200K to 2M users over 3 years)
- Technical architecture meeting performance, availability, and scalability requirements

**Fallback Solutions**:
- Manual fallback workflows if Duke APIs not available at launch (Service Request Creation API, Enrollment API) at no additional cost
- Alternative implementation approaches if anticipated integrations prove infeasible

### 13.2 CLIENT Responsibilities and Risks

CLIENT is responsible for and bears the risk of:

**Duke Enterprise Systems and APIs**:
- Duke Enterprise API availability and functionality (Customer Validation, HPP Plans, Service Request Creation, Enrollment)
- API documentation and sandbox access within 2 weeks of Effective Date
- CRM system access (Commerce for Duke customers, Dynamics for P&G customers) including test accounts, data schemas, integration documentation
- Contractor data export from Duke CRM systems by Week 4

**Infrastructure and Environment**:
- Ongoing hosting costs ($800/month estimated for AWS infrastructure, scales with user growth)
- Production infrastructure approval and deployment permissions
- Duke IT security approvals (architecture review Week 8, penetration test approval Week 32, production launch approval Week 36)
- App store developer accounts (iOS, Android) by Week 32

**Stakeholder Participation**:
- Duke technical team availability for Round 2 discovery (10-15 hours/week, Weeks 1-8)
- Business SME availability for requirements validation and UAT
- Timely review and approval cycles (design approval 2 weeks, sprint feedback 5 days, phase acceptance 15 days)
- Single designated Product Owner with decision-making authority

**Business Decisions**:
- Ad-hoc service catalog definition (5-10 initial services with pricing) by Week 8
- Contractor participation in pilot program (minimum 25 contractors across pilot markets)
- Revenue targets ($25M ad-hoc service revenue, 250K non-native customers) are CLIENT's business risk, not Orases technical risk

**Scope and Priority Decisions**:
- Prioritization of features and trade-off decisions
- Approval to proceed with Section 1.3 (Design, Development, and Implementation) after Analysis Activities complete
- Change Order approvals for scope changes beyond agreed plan

### 13.3 Shared Risks (Acknowledged by Both Parties)

Both parties acknowledge the following shared risks:

**API Availability Uncertainty**:
- Service Request Creation API and Enrollment API may not exist by MVP launch
- If APIs not available: Orases implements manual fallback workflows at no additional cost (included in planning budget estimate)
- Manual fallbacks are operationally less efficient but functionally acceptable for MVP

**FSM Tool Integration Timing**:
- Duke has not selected FSM tool as of SOW execution date
- FSM tool selection and integration anticipated 6-12 months post-launch
- Phase 2 rework estimated at $46,000 when FSM tool available (separate SOW required)
- Earlier or later FSM availability will adjust Phase 2 timing accordingly

**Third-Party Dependencies**:
- External services (CPSC recall database, barcode lookup APIs, SMS gateway, email service, push notification services) may experience outages, API changes, or service disruptions
- Orases not liable for third-party service failures outside Orases control
- Orases will implement error handling and graceful degradation for third-party service outages

**Technical Complexity Uncertainty**:
- Round 2 discovery may reveal integration complexity with Commerce/Dynamics CRM exceeds Initial Discovery estimates
- Security and compliance requirements may require more effort than anticipated
- Certain features may prove cost-prohibitive or technically infeasible
- If complexity significantly exceeds estimates, variance notification per Section 9.3 with options for CLIENT

**Contractor Network Risk**:
- CLIENT responsible for ensuring contractor participation in pilot program
- If contractors do not participate or use system as expected, customer experience may be impacted
- Orases not liable for contractor adoption rates or contractor behavior

**Revenue Target Risk**:
- $25M ad-hoc service revenue and 250K non-native customer acquisition targets are Duke business goals based on market assumptions
- Orases not liable if targets not met, as achievement depends on factors outside Orases control including: pricing strategy, marketing spend, contractor availability and quality, customer demand, competitive landscape, economic conditions, MVP limitations (no in-app payment, no ratings display, no contractor marketplace)

### 13.4 Limitation of Liability

Subject to the Master Services Agreement:

**Unlimited Liability For**:
- Security breaches (Orases pays all notification costs, credit monitoring, forensic investigations, legal fees, customer claims per Section 12.4)
- Intellectual property infringement (Orases warrants no third-party infringement per Section 11)
- Gross negligence or willful misconduct

**Limited or No Liability For**:
- Third-party service failures (CPSC, barcode APIs, SMS, email, push notifications) outside Orases control
- Duke IT infrastructure issues, outages, or constraints outside Orases control
- CLIENT dependency delays (API availability, approvals, data access, stakeholder participation)
- Contractor non-participation or poor contractor performance
- Revenue targets not met due to market factors or business decisions
- Force majeure events (natural disasters, pandemics, wars, government actions)

- - - - - - - - - - - - - - - - - - - -

## 14 Assumptions and Dependencies

### 14.1 Critical Assumptions

This SOW is based on the following assumptions. If assumptions prove incorrect, scope, timeline, and budget may require adjustment:

**Technical Assumptions**:
- Duke Enterprise APIs for Customer Validation and HPP Plan retrieval will be available by Week 12 with adequate documentation and sandbox access
- Commerce CRM (Duke customers) and Dynamics CRM (P&G customers) support anticipated integration approaches
- Duke IT infrastructure and security policies allow for planned cloud architecture on AWS
- Planned technology stack (React Native, Vue.js, Laravel, PostgreSQL/MySQL, Redis, AWS) is acceptable to CLIENT and performs as expected
- Third-party services (CPSC, barcode APIs, SMS gateway, email service, push notifications) remain available and stable

**Data Assumptions**:
- Contractor data can be exported from Duke CRM systems in usable format (CSV or JSON) with required fields: contractor name, contact info, trades, service areas/zip codes, primary/secondary designation, availability rules, lead times
- Customer data quality in Commerce/Dynamics CRM is sufficient for integration (no major data cleansing required)
- No bulk data migration from Duke CRM systems to app backend required for Phase 1 (customers create new profiles in app, linked to existing HPP plans via API lookup)

**Resource Assumptions**:
- Duke technical team available for Round 2 discovery at estimated 10-15 hours/week during Weeks 1-8
- CLIENT Product Owner available for bi-weekly sprint demos and timely feedback (5 business days for sprint acceptance, 15 business days for phase acceptance)
- CLIENT design approval within 2 weeks of submission (target Week 16)
- Orases team resources available as planned with no significant turnover of key personnel

**Timeline Assumptions**:
- No major scope changes after design approval (Week 16)
- CLIENT review and approval cycles meet assumed timelines
- Duke IT security approvals on schedule (Weeks 8, 32, 36)
- App store review and approval processes complete within standard timeframes (2-4 weeks)
- No extended holidays, CLIENT shutdowns, or other calendar disruptions beyond normal business holidays

**Scope Assumptions**:
- Phase 1 scope aligned with Initial Discovery (Exhibit A) subject to refinement during Analysis Activities
- MVP limitations documented in Section 1.5 are acceptable to CLIENT
- Phase 2 work (FSM integration, in-app payment, contractor portal, etc.) will be scoped separately and is not included in this SOW

### 14.2 Critical Dependencies

Project success depends on the following dependencies being met. Delays or failures of dependencies may impact timeline and budget:

| Dependency | Owner | Required By | Impact if Not Met | Mitigation |
|------------|-------|-------------|-------------------|------------|
| **API Documentation & Sandbox Access** | CLIENT | Week 2 | 2-week delay in integration development | Orases proceeds with mock data and API simulation |
| **Duke Tech Team Availability** | CLIENT | Weeks 1-8 | Analysis Activities incomplete, assumptions unvalidated, risk of rework | Extend Analysis Activities phase, adjust timeline |
| **Contractor Data Export** | CLIENT | Week 4 | Cannot configure contractor matching algorithm | 2-week delay, Orases proceeds with sample data for development |
| **Customer Validation & HPP Plan APIs** | CLIENT | Week 12 | Implement manual fallback workflows (included in budget) | Admin portal with manual lookup/entry queue |
| **CLIENT Design Approval** | CLIENT | Week 16 | 1:1 slip for each week of delay (1 week delay = 1 week project delay) | Escalate per Section 9.6, executive review |
| **Duke IT Security Approvals** | CLIENT | Weeks 8, 32, 36 | Delay in development start, testing, or production launch; potential rework if architecture changes required | Early engagement with Duke Security, incremental approvals, architecture preview |
| **Test Accounts for Commerce/Dynamics** | CLIENT | Week 12 | Cannot test integrations, blocks Alpha release | Delay testing phase, use production-like sandbox environment |
| **App Store Developer Accounts** | CLIENT | Week 32 | Cannot submit apps for review, blocks production launch | Orases can use temporary accounts for testing, but CLIENT accounts required for production |
| **UAT Participation** | CLIENT | Weeks 28-36 | Cannot validate functionality, risk of production issues | Extend testing phase, Orases performs additional QA, client acceptance risk |
| **Production Infrastructure Approval** | CLIENT | Week 36 | Cannot deploy to production, blocks launch | Parallel path: stage in pre-production, production cutover upon approval |

### 14.3 Out of Scope Assumptions

The following are explicitly assumed to be OUT OF SCOPE for Phase 1:

**Phase 2 or Future Work** (require separate SOW):
- FSM tool integration and associated rework ($46,000 estimated)
- In-app payment processing and payment gateway integration (PCI DSS compliance, payment flows, contractor payout, escrow management)
- Contractor mobile app with real-time job acceptance, GPS tracking, photo upload, customer communication
- Real-time GPS tracking for customers ("pizza tracker" experience)
- In-app ratings and reviews display during booking flow
- Contractor marketplace (customer selection from multiple contractors with pricing comparison)
- AI virtual assistant, predictive maintenance, IoT integration, real-time energy monitoring

**Explicitly Not Included**:
- Commercial properties (Phase 1 supports residential properties only)
- Unlicensed trades (no lawn care, painting, pest control, or other non-licensed services)
- Landlord/property management features (managing multiple rental units, tenant management, rent collection)
- International expansion (U.S. only: English language, U.S. phone numbers, U.S. payment methods)
- White-label customization for other utilities (architecture designed for white-label, but customization is Phase 2)
- Data migration from existing Duke CRM systems (customers create new profiles; existing Duke/P&G customers linked via API)
- Integration with Duke billing systems for utility bill payment method (Phase 2)
- Custom mobile apps beyond iOS and Android (no Windows Phone, Blackberry, etc.)

- - - - - - - - - - - - - - - - - - - -

## 15 Exhibits

### Exhibit A: Initial Discovery Documents

The following documents are incorporated by reference as Exhibit A and represent Orases' understanding of project requirements based on business stakeholder input prior to technical validation:

1. **"Discovery Findings and Updated Project Scope"** dated December 2025
   - Scope expansion from original RFP
   - Bridge Gap Challenge and ROI analysis
   - Budget breakdown: $788,600 estimated ($285K CX, $332K Backend, $171K DevOps)
   - Risk of obsolescence and mitigation strategies

2. **"Duke Energy Residential Solution Scope"** dated December 2025
   - Detailed MVP feature specifications
   - Three-tier architecture (Customer App, Admin Portal, Backend)
   - MVP limitations and Phase 2 scope
   - Three customer segments and workflows
   - Contractor matching algorithm specification
   - Admin portal roles and responsibilities

**Important Note**: These documents were developed based on business stakeholder input WITHOUT Duke Energy's technical team participation. Scope, timeline, and budget estimates in these documents are subject to validation and refinement during Analysis Activities (Section 1.1) with Duke's technical team.

- - - - - - - - - - - - - - - - - - - -

## Signatures

Once received and signed by both parties, this SOW shall constitute a binding contractual agreement between Orases and CLIENT.

**Orases Consulting Corporation**

Signature: _______________________________________

Printed Name: _______________________________________

Title: _______________________________________

Date: __________________


**Duke Energy Business Services, LLC**

Signature: _______________________________________

Printed Name: _______________________________________

Title: _______________________________________

Date: __________________
