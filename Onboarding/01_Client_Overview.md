# Client Overview — Duke Energy Residential Solutions
### Team Onboarding | Step 1 of 5

---

## Who Is Duke Energy?

Duke Energy is one of the largest electric power holding companies in the United States, headquartered in Charlotte, North Carolina. They are a Fortune 150 company with approximately 26,400 employees and annual revenues of $32+ billion. Duke Energy serves **8.7 million electric customers** across six states — North Carolina, South Carolina, Florida, Indiana, Ohio, and Kentucky — and an additional **1.8 million natural gas customers** through Piedmont Natural Gas (P&G), which Duke acquired and operates as a subsidiary.

Duke Energy is not a startup or a scrappy tech company. They are a heavily regulated, publicly traded utility with deep roots in the communities they serve. Their core business — generating and distributing electricity and natural gas — is mature and stable. What they are investing in now is **modernizing the customer experience** and expanding into adjacent services that leverage their massive, existing customer relationships. That is where we come in.

---

## What Is Duke Energy Residential Solutions?

Duke Energy Residential Solutions (RS) is a business unit within Duke Energy focused on home services — specifically, selling and administering **Home Protection Plans (HPPs)**. Think of it as Duke's version of a home warranty business, but with a built-in distribution advantage: they already have billing relationships with millions of homeowners through their utility accounts.

**Home Protection Plans** are monthly subscription contracts that cover the repair or replacement of key home systems and appliances — water heaters, HVAC systems, electrical wiring, plumbing, and appliances. Customers pay approximately $9.99 per month per plan, and that fee is simply added to their Duke utility bill. When something breaks, the customer calls, and Duke dispatches a vetted contractor from their managed network to fix or replace it — at no additional cost to the customer. No deductibles, no service fees, no surprise bills.

Currently, Residential Solutions manages:
- **800,000+ customers** with active HPP subscriptions
- **1.5 million total plan agreements** (customers often hold multiple plans)
- **125–140 contractors** across 4–5 states, covering HVAC, plumbing, electrical, water heater, and appliance trades
- **Top plans by volume:** Water heater (300K+ agreements) and home wiring/electrical (300K+ agreements)

The business also operates through **Piedmont Natural Gas** territory, which means there are two separate back-end CRM systems: SAP Commerce for Duke electric customers, and Microsoft Dynamics for P&G gas customers. This is an important technical reality our team needs to understand from Day 1 — we are integrating with two distinct enterprise systems, not one.

---

## The Problem We Are Solving

Today, if a Duke Residential Solutions customer's water heater breaks, their only option is to call a phone number, wait on hold, talk to a customer service rep, get a service request created manually, and wait to hear back about a contractor. There is no app, no self-service, no way to track what is happening, and no way to see when the contractor is coming. The average service request takes **15 minutes on the phone** to initiate.

This is entirely phone-driven in a world where customers book restaurants, order groceries, track deliveries, and request rides in under 60 seconds on their phone. Duke's customer satisfaction scores and call center volumes reflect the gap. They are losing customers who expect a modern experience, and they are leaving money on the table because they have a large contractor network with capacity that non-Duke-utility customers cannot currently access.

The vision Duke has articulated is to build the **"Uber of home services"** — a transparent, on-demand, digital-first platform where customers can book warranty service or pay-per-use home services, see exactly who is coming and when, and manage their entire home from one app.

---

## What Orases Is Building for Them

We are building a **three-component platform** under SOW #1:

### 1. Customer Mobile App (iOS, Android + Web PWA)
The primary customer-facing product. Customers use this to book home protection plan services, browse and book ad-hoc (pay-per-use) services, manage their home inventory, track service requests, set maintenance reminders, and manage their HPP subscriptions. The app supports three distinct customer types:

- **Existing HPP customers** — 800K+ Duke/P&G customers who already have active plans and currently can only call to use them
- **Existing Duke/P&G utility customers without HPPs** — potential plan enrollees and ad-hoc service buyers
- **Non-native customers** — homeowners outside Duke's utility territory who have no existing Duke relationship but can access the ad-hoc service marketplace

### 2. Admin Backend Portal
The operational backbone. Duke's internal back-office team (CSRs, operations managers, product managers, analysts) uses this portal to manage everything the customer app depends on: customer profiles, service requests, contractor assignments, the ad-hoc service catalog, maintenance reminders, and analytics. This portal is also critical for MVP because it serves as the **manual fallback layer** — where human admin staff fill gaps where automated API integrations don't yet exist.

### 3. Contractor Management System (Admin-Side, MVP)
For Phase 1, there is no new contractor-facing portal or mobile app. Contractors continue using Duke's existing Commerce CRM portal. However, we are building robust contractor configuration and management capabilities inside the Admin Portal — including contractor profiles, service area (zip code) assignments, trade designations, availability windows, and the matching algorithm that connects a customer's service request to the right contractor.

---

## High-Level Scope Summary

| Area | MVP (Phase 1 — by Sept 30, 2026) | Phase 2+ (Future) |
|---|---|---|
| Customer App | Service booking (HPP + ad-hoc), home inventory, maintenance reminders, service history, notifications, loyalty/gamification | In-app payments, contractor GPS tracking, AI troubleshooting, in-app ratings, contractor marketplace |
| Admin Portal | Customer management, service request queue, contractor config, ad-hoc catalog, reminders, analytics | Document management, advanced FSM integration, predictive analytics |
| Contractor Portal | No changes — contractors use existing portal | New contractor mobile app, real-time job acceptance, FSM integration |
| Integrations | Commerce API (Duke customer data + HPP plans), Dynamics (P&G + service requests), App DB (non-native customers, inventory, catalog) | FSM tool (Service Power or Service Bench), in-app payment processing |
| Payment | Contractor collects on-site for ad-hoc services | Pre-pay in app (Apple Pay, Google Pay, credit card, utility bill) |
| Service catalog | 5–10 ad-hoc services, 1–2 pilot markets | Full catalog, expanded markets, bundled services |

**Out of scope entirely:** Commercial properties, landlord/property management, unlicensed trades (lawn care, painting), direct contractor payment flows.

---

## Key Facts for Your First Week

**Client contacts you will work with:**
- Kate Angina — Primary Duke contact and project lead
- Sun Gandara — Business stakeholder, product/operations
- Kevin Oppermann — Business stakeholder
- Dana DeRemigis — Technical/integration stakeholder
- Joshua Gilstrap — Technical stakeholder

**Contract structure:**
- SOW #1 runs through December 31, 2027
- Time and Materials at $250/hour blended rate
- Estimated total engagement: ~$1,051,400
- MVP target date: September 30, 2026

**Tech stack we are building on:**
- Frontend: React Native (mobile), Vue.js (web), PWA
- Backend: Laravel (PHP), RESTful APIs
- Database: PostgreSQL or MySQL with Redis caching
- Infrastructure: AWS
- Integrations: SAP Commerce, Microsoft Dynamics, Duke Data Fabric

**The most important things to understand about this client:**
1. They are a large enterprise with two separate back-end CRM systems (Commerce + Dynamics) that do not speak to each other — and we are building the layer that bridges them
2. The ad-hoc service catalog does not exist today — it is entirely new and must be defined collaboratively with Duke during the early weeks of the project
3. HPP coverage rules are currently not systematized or accessible via API — resolving this is a critical dependency for core app functionality
4. Contractors are not being disrupted in Phase 1 — the manual admin process is intentional to keep MVP scope focused on the customer experience
5. Duke's real measure of success is call center volume reduction (target: 40%) and new ad-hoc revenue ($25M in 12 months) — keep those numbers in mind when making scope and priority decisions

---

*Next: Step 2 — Project Governance and How We Work*

*Sources: SOW #1 V6 (Feb 2026), MVP Scope Executive Summary, Customer/Admin/Contractor Workshop Findings, HPP Plans Reference, Duke Energy 2025 Annual Results*

---

## Glossary of Abbreviations

| Abbreviation | Full Term |
|---|---|
| **AI** | Artificial Intelligence |
| **API** | Application Programming Interface — a connection point that allows two software systems to talk to each other |
| **AWS** | Amazon Web Services — the cloud infrastructure platform we use for hosting |
| **CRM** | Customer Relationship Management — the software Duke uses to manage customer accounts (SAP Commerce for Duke electric customers, Microsoft Dynamics for P&G gas customers) |
| **CSR** | Customer Service Representative |
| **DIY** | Do It Yourself |
| **FSM** | Field Service Management — software used to coordinate and track contractor field work; not in Phase 1 scope |
| **GPS** | Global Positioning System — used for real-time contractor location tracking (Phase 2 feature) |
| **HPP** | Home Protection Plan — Duke's monthly subscription product that covers repair/replacement of home systems and appliances |
| **HVAC** | Heating, Ventilation, and Air Conditioning |
| **iOS** | iPhone Operating System — Apple's mobile operating system |
| **MVP** | Minimum Viable Product — the core version of the app, targeting September 30, 2026 |
| **NPS** | Net Promoter Score — a customer satisfaction metric (target: 70+) |
| **P&G** | Piedmont Natural Gas — Duke Energy's natural gas subsidiary |
| **PHP** | Hypertext Preprocessor — the programming language used by Laravel (our backend framework) |
| **PRD** | Product Requirements Document — defines what we are building and why; must be approved before development begins |
| **PWA** | Progressive Web App — a web application that behaves like a native mobile app |
| **RS** | Residential Solutions — the Duke Energy business unit we are building for |
| **SAP** | Systems, Applications & Products — the enterprise software platform used by Duke for electric customer data (SAP Commerce/Hybris) |
| **SMS** | Short Message Service — text messaging |
| **SOW** | Statement of Work — the contract between Orases and Duke Energy governing this engagement |
| **SSO** | Single Sign-On — allows users to log in once and access multiple systems |
| **T&M** | Time and Materials — the billing model for this engagement; we bill for actual hours worked |
| **TRD** | Technical Requirements Document — defines how we will build what the PRD describes; written by the Lead Developer |
