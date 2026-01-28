# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the Duke Energy Residential Solutions Home Services Mobile App project - a comprehensive RFP response and proposal documentation repository. The project involves developing a native mobile application (iOS/Android) and web version for Duke Energy's home protection plan services, serving 800K+ current customers with plans to expand to non-native customers.

**Key Business Context:**
- Duke Energy Residential Solutions administers home protection plans (HPPs) covering utility lines, electrical, heating & cooling, and appliances
- Current state: customers can only call to request service (no self-service option)
- Goal: Create an "Uber of home services" experience with transparent pricing and real-time updates
- Target go-live: Q2-Q3 2026

## Repository Structure

```
Duke_residential_solutions/
├── Bid_Package/              # Original RFP documents from Duke Energy
│   ├── RFP_Instruction_Home_Services_App.pdf
│   ├── Home_App_Requirements.xlsx
│   ├── Technical_Questionnaire_RFP_Home_App.xlsx
│   ├── Pricing_Template_CX_Mobile_App.xlsx
│   ├── Third_Party_Risk_Management_Services_Risk_Profile.xlsx
│   ├── 2025_Duke_Energy_Master_Consulting_Services_Agreement.docx
│   ├── Duke_Energy_Code_of_Business_Ethics.pdf
│   └── Duke_Energy_Supplier_Code_of_Conduct.pdf
└── ProposalDocuments/        # Orases response documents
    ├── Duke_RS_Proposal.pdf
    ├── Y1__Detailed_Project_Approach_Timeline_and_Implementation_Strategy.pdf
    ├── Final_Technical_Questionnaire_RFP_Home_App.xlsx
    └── Final_Pricing_Template_CX_Mobile_App.xlsx
```

## Key Technical Requirements

### Phase 1 Core Features (MVP - 44 weeks)
- **Native Mobile Apps**: iOS and Android with offline capabilities
- **Mobile Web Version**: Responsive PWA with feature parity
- **Home Service Scheduling**: Appointment management, contractor matching, real-time status
- **Home Profile & Inventory**: Barcode scanning, warranty tracking, maintenance reminders
- **My Account**: Multi-property support, payment preferences, order history
- **DIY Library**: Educational content and tutorials
- **Payment Processing**: SpeedPay integration for non-native customers

### Technology Stack (Proposed)
- **Frontend**: React Native (mobile), Vue.js (web), PWA capabilities
- **Backend**: Laravel framework with RESTful APIs
- **Database**: PostgreSQL or MySQL with Redis caching
- **Hosting**: AWS cloud infrastructure
- **Integration**: Duke Energy Commerce & Dynamics systems via custom APIs

### Key System Integrations
1. **Commerce Platform**: Customer data and billing
2. **Dynamics**: Service order management and contractor coordination
3. **Contractor Portals**: Real-time job assignment and status updates
4. **SpeedPay**: Payment processing for non-native customers
5. **Duke Energy Data Fabric**: Enterprise data integration layer

## Project Timeline

- **Total Duration**: 44 weeks (11 months) from contract execution
- **Planning & Analysis**: Weeks 1-12
- **Design & Architecture**: Weeks 8-16
- **Development MVP**: Weeks 12-20
- **Alpha/Beta Development**: Weeks 20-28
- **Testing & QA**: Weeks 24-36
- **Deployment**: Weeks 36-40
- **Warranty Support**: Weeks 40-44

**Key Milestones:**
- Week 20: MVP Release
- Week 24: Functional Alpha
- Week 28: Beta Version
- Week 32: Release Candidate
- Week 40: Production Launch

## Important Business Requirements

### Customer Experience Goals
- Reduce service request time from 15 minutes (phone) to <3 minutes (app)
- Achieve 90% customer satisfaction with contractor communication
- Enable contractor availability and job status dashboard visibility
- Provide real-time updates and communication throughout service lifecycle

### Operational Efficiency Goals
- Reduce call center volume by 40%
- Automate scheduling to reduce coordination calls by 80%
- Improve data collection through app-based home inventory (80% inventory completion)

### Revenue Growth Goals
- Generate $25M in new ad-hoc service revenue within 12 months
- Acquire 250K non-native customers within 24 months
- Increase customer engagement with 70+ NPS score

## Security & Compliance

- **Data Encryption**: End-to-end encryption for sensitive data
- **Access Control**: Role-based permissions with MFA
- **Compliance**: GDPR, CCPA, and state-specific privacy regulations
- **Audit Logging**: Comprehensive activity tracking
- **Infrastructure**: VPC, WAF, security groups on AWS

## Development Approach

**Methodology**: Hybrid Agile
- 2-week sprints with bi-weekly demos
- AI-assisted development (31% efficiency improvement using Claude Code)
- Parallel workstreams: mobile app, APIs, backend systems
- Continuous integration/continuous deployment (CI/CD)
- Phased deployment: Development → Staging → Production

## Key Personas

1. **"Established Eleanor"** - 58, existing Duke customer with HPP, frustrated with phone-only service
2. **"Expanding Emma"** - 34, first-time homeowner, new Duke customer, wants proactive home management
3. **"Non-Native Nathan"** - 41, not a Duke utility customer, seeks reliable home services platform

## Phase 2/3 Future Features

- AI virtual assistant for troubleshooting
- Predictive maintenance recommendations
- Real-time energy monitoring through utility integration
- IoT integration for smart home devices
- White-label platform for other utilities
- Advanced analytics and BI dashboards

## Critical Success Factors

1. **API Integration**: Duke IT must provide API documentation and sandbox access within 2 weeks of kickoff
2. **Duke SME Availability**: Business SMEs need 10-15 hours/week for requirements validation
3. **Contractor Participation**: Pilot program requires ~25 contractors across 3 markets
4. **Product Catalog Definition**: Ad-hoc service pricing must be defined by Weeks 8-12
5. **Legal Approvals**: Customer communications and privacy notices require Duke legal review

## Working with Documents

### Viewing RFP Requirements
```bash
# RFP instructions are in PDF format
open Bid_Package/RFP_Instruction_Home_Services_App.pdf
```

### Technical Requirements Spreadsheet
```bash
# Detailed requirements matrix
open Bid_Package/Home_App_Requirements.xlsx
```

### Proposal Documents
```bash
# Main proposal document
open ProposalDocuments/Duke_RS_Proposal.pdf

# Detailed timeline and implementation
open ProposalDocuments/Y1__Detailed_Project_Approach_Timeline_and_Implementation_Strategy.pdf
```

## Contact Information

**Primary Contact**: Kate Angina (kate.angina@duke-energy.com)
**Vendor**: Orases (orases.com)
**Vendor Contact**: Tom Witt (tom@orases.com, 703.585.7499)
**RFP Reference**: #236724
**Response Deadline**: September 30, 2025

## Notes for Future Development

- This is currently a proposal/RFP response repository with no code yet
- When development begins, follow the hybrid agile methodology outlined in the proposal
- Architecture must support white-label functionality from Day 1 (multi-tenant design)
- All customer data must remain segregated per Duke Energy compliance requirements
- Payment processing must support multiple flows: utility billing, credit cards, contractor collection
