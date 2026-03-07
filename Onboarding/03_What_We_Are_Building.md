# What We Are Building
### Team Onboarding | Step 3 of 5

---

## The Big Picture

We are building a **three-component platform** that transforms Duke Energy's home protection plan services from a phone-only operation into a fully digital, on-demand experience — the "Uber of home services." The three components work together but are built and operated separately:

```
┌─────────────────────────┐     ┌──────────────────────────┐     ┌─────────────────────────┐
│   CUSTOMER APP          │     │   ADMIN PORTAL           │     │   CONTRACTOR SYSTEM     │
│   iOS · Android · Web   │ ←→  │   Duke Internal Use      │ ←→  │   Existing CRM (MVP)    │
│   Self-service, booking │     │   Operations, config,    │     │   New portal Phase 2    │
│   home management       │     │   management, analytics  │     │                         │
└─────────────────────────┘     └──────────────────────────┘     └─────────────────────────┘
            ↕                               ↕
┌──────────────────────────────────────────────────────────────────┐
│   INTEGRATIONS: SAP Commerce · Microsoft Dynamics · App Database │
└──────────────────────────────────────────────────────────────────┘
```

**The MVP target date is September 30, 2026.** Everything below marked MVP is planned for that date.

---

## Component 1: Customer App

### Who Uses It
Three distinct customer types, all supported from Day 1:

| Customer Type | Who They Are | Key Difference |
|---|---|---|
| **HPP Customers** | Existing Duke/Piedmont utility customers with active home protection plans | Services are covered — $0 at time of service |
| **Utility Customers (No HPP)** | Duke/Piedmont utility customers without plans | Can buy ad-hoc services; target for HPP upsell |
| **Non-Native Customers** | Homeowners who are NOT Duke utility customers | Ad-hoc services only; no HPP access; pay directly |

### Core MVP Features

**Registration & Account**
- Profile creation separate from Duke utility accounts (new credentials)
- Address-based validation links Duke/P&G customers to their existing HPP plans
- Multi-property support — customers with multiple homes can manage all in one profile
- Guest access is extremely limited (browse only, no booking)

**Home Protection Plan Management**
- View all active HPP plans linked to profile
- Enroll in new plans, upgrade/downgrade, self-service cancellation
- Display coverage terms, pricing, billing method per plan
- Average customer has 1.7 plans — multi-plan display required

**Home Inventory & Profile**
- Manual entry of appliances and systems (make, model, serial number, age)
- Barcode scanning to auto-populate appliance data
- Address auto-fills home characteristics (square footage, year built, property type)
- Maintenance schedules auto-generated from inventory (e.g., "flush water heater annually")
- Gamification: loyalty points, profile completion score, badges — these are critical for driving inventory completion which unlocks the rest of the platform's value

**Service Booking — HPP Covered Services**
- Symptom-based intake (customer describes issue in plain language)
- Coverage check determines eligibility under existing plan
- Contractor auto-assigned by trade + zip code (no customer selection in MVP)
- Customer picks from available date/time windows based on trade-specific lead times:
  - HVAC/Water Heater: 1–2 business days
  - Appliance: 2–3 business days
  - Plumbing: 3–5 business days
  - Electrical (non-emergency): 5–6 business days
- Status starts as "Pending Confirmation" — admin manually contacts contractor
- Customer pays $0 (covered by subscription)

**Service Booking — Ad-Hoc Services**
- Browse service catalog with flat-rate or range pricing (e.g., "$99 HVAC tune-up")
- Available to all customer types including non-native
- Same contractor matching as HPP (primary by trade + zip code)
- MVP payment: contractor collects on-site. No in-app payment at launch.
- Service catalog starts with 5–10 services in 1–2 pilot markets

**Notifications & Communication**
- Push, SMS, email, in-app notification center
- Customer selects preferred channels
- MVP statuses (manual admin updates): Pending Confirmation → Confirmed → Completed
- No real-time tracking in MVP (no "pizza tracker" — that requires FSM tool, Phase 2)

**Maintenance Reminders**
- Auto-generated from home inventory
- Default reminder sets for new homeowners
- Custom user-created reminders
- Each reminder offers DIY path or "Book Service" button

**Service History**
- Full exportable log tied to appliances and systems
- Useful for home sales (buyers can see maintenance history)
- Invoice/receipt storage in app

**Emergency Handling — Phone Only**
- App asks triage questions to detect emergencies
- If emergency detected → routes customer to phone: "Call 1-800-XXX-XXXX immediately"
- Emergencies are NOT booked through the app (gas leaks, no heat in winter, active flooding, sparking electrical)

### What Is NOT in MVP (Phase 2+)
- In-app payment processing (Apple Pay, Google Pay, credit card)
- Real-time contractor GPS tracking ("pizza tracker")
- In-app contractor ratings and reviews
- Contractor marketplace (selecting from multiple contractors)
- In-app messaging between customer and contractor
- AI virtual assistant / conversational troubleshooting
- HPP enrollment for non-native customers

---

## Component 2: Admin Portal

### Who Uses It
Duke's internal operations team — not customers. Seven distinct roles:

| Role | What They Do |
|---|---|
| **CSR — Enrollment** | Manually create accounts, process failed enrollments |
| **CSR — Support** | Password resets, account troubleshooting |
| **Back Office Admin** | Process enrollment queues, manage customer profiles, update inventory |
| **Product Manager (Duke)** | Create and edit ad-hoc service catalog, set pricing |
| **Operations Manager** | Process service requests — contact contractors within 1 hour, update app status |
| **Escalation Team** | Handle complaints, contractor disputes, service quality issues |
| **Analyst** | Dashboards, reports, KPI tracking |

### Why the Admin Portal Is Critical for MVP

The admin portal is not just a management tool — it is the **manual fallback layer** for MVP. Because several Duke IT APIs may not be ready at launch, human admin staff fill the gaps:

- Customer books service in app → Admin contacts contractor by phone/email within 1 hour
- Contractor responds → Admin manually updates status in the app
- Enrollment submitted → Admin manually processes in CRM if API not ready

This is intentional and planned. The admin portal must support this manual workflow reliably from Day 1.

### Core MVP Features

**Customer Management** — View, search, create, and edit customer profiles aggregated from Commerce (Duke), Dynamics (P&G), and the App DB (non-native). Includes review queue for failed enrollments.

**Service Request Management** — The most critical MVP admin feature. Dashboard showing all pending service requests, priority queue for unconfirmed requests, manual status updates, contractor reassignment, internal notes, 1-hour SLA tracker.

**Contractor Configuration** — Full CRUD on the contractor network: 125–140 contractors, trade assignments, zip code coverage (exact zip, not radius), primary/secondary designation, lead time buffers, availability windows.

**Ad-Hoc Service Catalog** — Entirely new — this does not exist in any Duke system today. Admin creates and manages services, pricing (flat, range, quote), geographic pricing, contractor associations.

**Maintenance Reminders Management** — Create and edit reminder templates, map to inventory categories, link to bookable services.

**Analytics Dashboard** — Instrumented from Day 1. Tracks customer acquisition, engagement, service request volume, call center volume reduction, contractor performance, revenue.

**Escalation Management** — Ticket creation, assignment, and resolution workflow for customer complaints.

### What Is NOT in the Admin Portal for MVP
- Document management for customer-uploaded files
- Automated FSM integration (all contractor status updates are manual)
- Advanced/predictive analytics
- Payment management and AR workflows

---

## Component 3: Contractor System

### The MVP Decision: No Contractor Portal Changes

This is counterintuitive but intentional. **Phase 1 builds zero new contractor-facing tools.**

Contractors continue using Duke's existing Commerce CRM portal exactly as they do today:
- Receive job assignments via email
- View service request details
- Schedule appointments with customers
- Update service status (accepted, completed, invoiced)
- Submit invoices

**Why this decision was made:**
1. The customer app drives the revenue — that is where we focus 100% of Phase 1
2. The existing contractor portal works and contractors know it
3. A proper contractor mobile app requires FSM tool integration (not procured yet)
4. Manual admin workflows are acceptable for MVP volume

**What we DO build for contractors in MVP** — all inside the Admin Portal:
- Contractor profile configuration (CRUD)
- Trade and zip code assignment management
- Primary/secondary designation per trade per zip code
- Availability and lead time configuration
- Performance metrics (admin view only)

**Phase 2 contractor features (future):**
- New contractor mobile app (iOS/Android)
- Real-time job acceptance via push notification
- GPS tracking for pizza tracker experience
- FSM tool integration
- In-app communication with customers

---

## The Integration Layer

This is where significant technical complexity lives. We are connecting to systems that were not designed to talk to each other.

### Systems We Integrate With

| System | Owner | What It Contains | Our Access |
|---|---|---|---|
| **SAP Commerce (Hybris)** | Duke IT | Duke electric customer profiles, HPP plans | Read via API |
| **Microsoft Dynamics** | Duke IT (P&G) | P&G gas customer profiles, service requests | Read/write via API |
| **App Database** | Orases (we build it) | Non-native customers, home inventory, ad-hoc catalog, reminders | Full control |
| **Duke Data Fabric** | Duke IT | Enterprise data integration layer | TBD |

### Data Ownership Map

| Data | Source of Truth | Notes |
|---|---|---|
| Duke customer profile | Commerce → App DB (synced) | Read-only sync |
| P&G customer profile | Dynamics → App DB (synced) | Read-only sync |
| Non-native customer profile | App DB | We own this entirely |
| HPP plan enrollments | Commerce/Dynamics → App DB | Real-time sync |
| Service requests (HPP) | Dynamics ↔ App DB | Bi-directional sync |
| Service requests (ad-hoc) | App DB → Dynamics | Pushed for invoicing |
| Home inventory | App DB | We own this entirely |
| Ad-hoc service catalog | App DB | We own this entirely |
| Contractor configuration | CRM/Dynamics → App DB (copy) | Manual sync for MVP |

### Critical API Dependencies

**Must exist at MVP launch (blocking):**
- Customer validation API — links app profiles to Duke/P&G accounts
- HPP plan lookup API — shows customer's active plans
- Service order creation API — creates bookings in Dynamics

**May need manual fallback at launch:**
- HPP enrollment/cancellation API — can launch with manual processing if not ready
- Service order status update API — admin manually updates if API not ready

**Phase 2 (not blocking MVP):**
- FSM tool integration — enables real-time tracking and automated status updates
- In-app payment processing
- CPSC recall database integration
- Duke Energy utility app SSO

### Duke IT Expectations

Duke IT must provide:
- API documentation and sandbox access **within 2 weeks of project kickoff**
- Commerce API (Duke customer data and HPP plans)
- Dynamics API (P&G customers and service requests)
- Ongoing IT SME availability for integration questions

If API access is delayed, it directly impacts our MVP timeline. Flag any Duke IT delays to the PM immediately.

---

## Interactive Prototypes

Early prototypes have been built to visualize the product before development begins. These are reference tools for the team — use them to understand the intended user experience, screen flows, and feature scope. They are not final designs and will evolve based on Duke feedback and discovery.

| Prototype | URL | What It Covers |
|---|---|---|
| **Customer App** | https://duke-home-guardian.lovable.app/ | Customer-facing experience: service booking, home inventory, HPP management, maintenance reminders |
| **Admin Portal** | https://duke-portal-nexus.lovable.app/ | Duke operations interface: service request queue, contractor management, customer profiles, catalog |

These prototypes are attached to the onboarding deck and serve as a visual starting point for team alignment and Duke stakeholder conversations.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Mobile App | React Native (iOS + Android) |
| Web App | Vue.js, PWA |
| Backend | Laravel (PHP), RESTful APIs |
| Database | PostgreSQL or MySQL |
| Caching | Redis |
| Infrastructure | AWS (VPC, WAF, security groups) |
| Project Management | Jira (internal), Trello (client-facing) |
| Documentation | Confluence |
| Communication | Email (client-facing); Slack or Teams (internal) |

---

## Success Metrics Duke Cares About

These are the numbers Duke will judge us by. Keep them in mind when making scope and priority decisions:

| Metric | Target |
|---|---|
| Service request time | Phone: 15 min → App: under 3 min |
| Call center volume reduction | 40% reduction |
| Scheduling automation | 80% reduction in coordination calls |
| Customer satisfaction | 70+ NPS score |
| Ad-hoc service revenue | $25M within 12 months of launch |
| Non-native customer acquisition | 250K within 24 months |
| App adoption (HPP customers) | 30–40% using app within 12 months |
| Home inventory completion | 80% of customers with at least 1 item |

---

*Next: Step 4 — Your Role on This Project*

*Source: MVP Scope Executive Summary, Customer/Admin/Contractor Workshop Findings, SOW #1 V6, Integration Dependencies Analysis*

---

## Glossary of Abbreviations

| Abbreviation | Full Term |
|---|---|
| **AI** | Artificial Intelligence |
| **API** | Application Programming Interface — a connection point that allows two software systems to talk to each other |
| **AR** | Accounts Receivable — financial tracking of money owed; not in MVP scope |
| **AWS** | Amazon Web Services — the cloud infrastructure platform we use for hosting |
| **CPSC** | Consumer Product Safety Commission — U.S. government agency that maintains a database of recalled products; integration planned for Phase 2 |
| **CRM** | Customer Relationship Management — the software Duke uses to manage customer accounts |
| **CRUD** | Create, Read, Update, Delete — the four basic operations for managing data records |
| **CSR** | Customer Service Representative |
| **DIY** | Do It Yourself |
| **FSM** | Field Service Management — software used to coordinate and track contractor field work; not in Phase 1 scope |
| **GPS** | Global Positioning System — used for real-time contractor location tracking (Phase 2 feature) |
| **HPP** | Home Protection Plan — Duke's monthly subscription product that covers repair/replacement of home systems and appliances |
| **HVAC** | Heating, Ventilation, and Air Conditioning |
| **iOS** | iPhone Operating System — Apple's mobile operating system |
| **MVP** | Minimum Viable Product — the core version of the app, targeting September 30, 2026 |
| **NPS** | Net Promoter Score — a customer satisfaction metric scored 0–100 (target: 70+) |
| **P&G** | Piedmont Natural Gas — Duke Energy's natural gas subsidiary |
| **PWA** | Progressive Web App — a web application that behaves like a native mobile app |
| **SAP** | Systems, Applications & Products — the enterprise software platform used by Duke for electric customer data (SAP Commerce/Hybris) |
| **SLA** | Service Level Agreement — a committed response or resolution time; e.g., admin must contact contractor within 1 hour of booking |
| **SMS** | Short Message Service — text messaging |
| **SOW** | Statement of Work — the contract between Orases and Duke Energy governing this engagement |
| **SSO** | Single Sign-On — allows users to log in once and access multiple systems |
| **TBD** | To Be Determined |
| **VPC** | Virtual Private Cloud — an isolated network environment within AWS for security |
| **WAF** | Web Application Firewall — a security layer that filters malicious web traffic |
