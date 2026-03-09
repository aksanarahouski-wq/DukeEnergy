# Initial Solution Architecture
### Duke Energy Residential Solutions — Home Services & Warranty Application
### Draft v1.0 — March 2026

**Status:** Pre-development draft — subject to refinement during requirements definition and Duke IT technical sessions
**Author:** Aksana Rahouski, Product Manager (Orases)
**Audience:** Orases technical team, Duke Product Owner, Duke IT stakeholders

---

## Table of Contents

1. [Architecture Principles](#1-architecture-principles)
2. [System Context — The Big Picture](#2-system-context)
3. [Application Architecture](#3-application-architecture)
4. [Data Architecture — What We Own vs. What Duke Owns](#4-data-architecture)
5. [API Layer Design](#5-api-layer-design)
6. [Frontend Architecture — Customer App + Web](#6-frontend-architecture)
7. [Admin Portal Architecture](#7-admin-portal-architecture)
8. [Integration Architecture — Duke Systems](#8-integration-architecture)
9. [Push Notification Architecture](#9-push-notification-architecture)
10. [Security Architecture](#10-security-architecture)
11. [Infrastructure & Deployment](#11-infrastructure-and-deployment)
12. [Data Flow Diagrams — Key Workflows](#12-data-flow-diagrams)
13. [Phase 2 Architecture Considerations](#13-phase-2-considerations)
14. [Open Questions & Decisions Needed](#14-open-questions)

---

## 1. Architecture Principles

These principles guide every technical decision. When trade-offs arise, use these to resolve them.

1. **Duke systems are never exposed to the client.** All external system communication goes through our Laravel API. The mobile app and web app never call Commerce, Dynamics, or any Duke API directly.

2. **Our database is the app's source of truth for app-owned data.** Home inventory, ad-hoc service catalog, reminders, non-native customer profiles, loyalty points, and notification preferences live in our PostgreSQL database. Duke CRM remains source of truth for Duke/P&G customer identity, HPP plans, and contractor master records.

3. **Build for three customer types from Day 1.** The architecture must handle native Duke customers, native P&G customers, and non-native customers with different data sources, different validation paths, and different payment flows. No shortcuts.

4. **Design for offline-first where it matters.** Cached HPP plans, cached home inventory, cached service history, and cached DIY content should be available without a network connection. Booking and payment require connectivity.

5. **One API serves all clients.** The React Native app (iOS + Android), the Vue.js web app, and the admin portal all consume the same Laravel REST API. No separate backend per frontend.

6. **White-label ready from Day 1.** Multi-tenant data isolation, configurable branding, and tenant-scoped API responses must be part of the core design — not retrofitted later. This is a SOW and proposal requirement.

7. **Manual fallback is a feature, not a bug.** MVP relies on admin manual processes for service request handoff, enrollment processing, and status updates. The architecture must support these graceful degradation paths with queues, notification triggers, and admin dashboards.

8. **Instrument everything.** Analytics events, API response times, error rates, and business metrics (booking funnel completion, inventory adoption, call center deflection) must be tracked from the first sprint. Duke's business case depends on measurable outcomes.

---

## 2. System Context — The Big Picture

### Level 0: System Context Diagram

```
                                    ┌─────────────────────────────┐
                                    │      DUKE ENERGY SYSTEMS     │
                                    │                              │
                                    │  ┌────────────────────────┐  │
                                    │  │  SAP Commerce (Hybris)  │  │
                                    │  │  Duke Electric Customers │  │
                                    │  │  HPP Plans & Enrollment  │  │
                                    │  └────────────────────────┘  │
                                    │                              │
                                    │  ┌────────────────────────┐  │
                                    │  │  Microsoft Dynamics     │  │
                                    │  │  P&G Gas Customers      │  │
                                    │  │  Service Orders         │  │
                                    │  └────────────────────────┘  │
                                    │                              │
                                    │  ┌────────────────────────┐  │
                                    │  │  Duke Data Fabric       │  │
                                    │  │  Enterprise Integration  │  │
                                    │  └────────────────────────┘  │
                                    └──────────────┬──────────────┘
                                                   │
                                          VPN / Secure API
                                                   │
┌──────────────┐   ┌──────────────┐   ┌────────────▼─────────────────────────┐
│  iOS App     │   │  Android App │   │                                       │
│  (React      │   │  (React      │   │     ORASES PLATFORM (AWS)             │
│   Native)    │   │   Native)    │   │                                       │
└──────┬───────┘   └──────┬───────┘   │  ┌─────────────────────────────────┐  │
       │                  │           │  │  Laravel API                     │  │
       │     HTTPS        │           │  │  (Business Logic, Auth,          │  │
       ├──────────────────┤           │  │   Integration Gateway)           │  │
       │                  │           │  └─────────────────────────────────┘  │
       │                  │           │                                       │
┌──────┴───────┐          │           │  ┌──────────┐ ┌───────┐ ┌─────────┐  │
│  Web App     │          │           │  │PostgreSQL│ │ Redis │ │   S3    │  │
│  (Vue.js     ├──────────┘           │  │ Database │ │ Cache │ │ Storage │  │
│   PWA)       │                      │  └──────────┘ └───────┘ └─────────┘  │
└──────────────┘                      │                                       │
                                      └───────────────────────────────────────┘
┌──────────────┐
│  Admin Portal│──── HTTPS ──── Same Laravel API
│  (Vue.js)    │
└──────────────┘

┌──────────────────────────┐
│  External Services       │
│  • APNs (iOS push)       │
│  • FCM (Android push)    │
│  • Twilio/SNS (SMS)      │
│  • SendGrid (Email)      │
│  • Stripe (Payments Ph2) │
│  • CPSC API (Recalls Ph2)│
└──────────────────────────┘
```

### Key Actors

| Actor | Interface | Authentication |
|---|---|---|
| HPP Customer (Duke) | iOS App, Android App, Web App | Email/password + address-based validation against Commerce |
| HPP Customer (P&G) | iOS App, Android App, Web App | Email/password + address-based validation against Dynamics |
| Non-Native Customer | iOS App, Android App, Web App | Email/password only (no Duke/P&G validation) |
| Duke Admin (CSR) | Admin Portal (Vue.js) | SSO or email/password |
| Duke Admin (Ops Manager) | Admin Portal (Vue.js) | SSO or email/password |
| Duke Admin (Product Manager) | Admin Portal (Vue.js) | SSO or email/password |
| Contractor | Existing Commerce CRM Portal (MVP) | Existing credentials (unchanged) |

---

## 3. Application Architecture

### Level 1: Container Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                           AWS VPC                                        │
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                        PUBLIC SUBNET                             │    │
│  │                                                                  │    │
│  │  ┌──────────────┐    ┌──────────────┐    ┌──────────────────┐  │    │
│  │  │  CloudFront   │    │    AWS WAF    │    │  ALB (Load       │  │    │
│  │  │  CDN          │    │  (Firewall)   │    │  Balancer)       │  │    │
│  │  │  Static assets│    │  Rate limiting│    │  SSL termination │  │    │
│  │  │  Web app      │    │  IP filtering │    │  Health checks   │  │    │
│  │  └──────────────┘    └──────────────┘    └────────┬─────────┘  │    │
│  │                                                    │            │    │
│  └────────────────────────────────────────────────────┼────────────┘    │
│                                                       │                  │
│  ┌────────────────────────────────────────────────────┼────────────┐    │
│  │                        PRIVATE SUBNET               │            │    │
│  │                                                     │            │    │
│  │  ┌─────────────────────────────────────────────────▼──────┐    │    │
│  │  │                   LARAVEL API CLUSTER                    │    │    │
│  │  │                                                         │    │    │
│  │  │  ┌───────────────┐  ┌───────────────┐  ┌────────────┐ │    │    │
│  │  │  │ Authentication │  │ Business Logic│  │ Integration│ │    │    │
│  │  │  │ & Authorization│  │ Service Booking│ │ Gateway    │ │    │    │
│  │  │  │ JWT tokens     │  │ Coverage Check │ │ Commerce   │ │    │    │
│  │  │  │ Role-based     │  │ Contractor     │ │ Dynamics   │ │    │    │
│  │  │  │ access control │  │ Matching       │ │ Data Fabric│ │    │    │
│  │  │  └───────────────┘  │ Inventory Mgmt │ └────────────┘ │    │    │
│  │  │                     │ Catalog Mgmt   │                  │    │    │
│  │  │  ┌───────────────┐  │ Notification   │  ┌────────────┐ │    │    │
│  │  │  │ Queue Worker   │  │ Dispatch       │  │ Scheduled  │ │    │    │
│  │  │  │ (Laravel       │  └───────────────┘  │ Jobs       │ │    │    │
│  │  │  │  Horizon)      │                      │ Reminders  │ │    │    │
│  │  │  │ Async jobs:    │                      │ Data sync  │ │    │    │
│  │  │  │ • Notifications│                      │ Cache warm │ │    │    │
│  │  │  │ • Email sends  │                      │ Analytics  │ │    │    │
│  │  │  │ • Data sync    │                      └────────────┘ │    │    │
│  │  │  │ • Report gen   │                                      │    │    │
│  │  │  └───────────────┘                                       │    │    │
│  │  └──────────────────────────────────────────────────────────┘    │    │
│  │                                                                  │    │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  │    │
│  │  │  PostgreSQL   │  │    Redis     │  │   Amazon S3          │  │    │
│  │  │  (RDS)        │  │  (ElastiCache│  │   File storage       │  │    │
│  │  │               │  │   )          │  │   • Customer photos  │  │    │
│  │  │  Primary +    │  │  • Session   │  │   • Inventory images  │  │    │
│  │  │  Read replica │  │    store     │  │   • Service reports   │  │    │
│  │  │  Auto backup  │  │  • API cache │  │   • DIY content media │  │    │
│  │  │               │  │  • Queue     │  │   • Invoices/receipts │  │    │
│  │  │               │  │    backend   │  │                       │  │    │
│  │  └──────────────┘  └──────────────┘  └──────────────────────┘  │    │
│  │                                                                  │    │
│  └──────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Component Responsibilities

| Component | Responsibility | Technology |
|---|---|---|
| **Laravel API** | All business logic, authentication, authorization, data validation, external system integration | PHP 8.3+ / Laravel 11 |
| **PostgreSQL** | Persistent storage for all app-owned data | PostgreSQL 16 (AWS RDS) |
| **Redis** | Session storage, API response caching, queue backend, rate limiting | Redis 7 (AWS ElastiCache) |
| **Amazon S3** | File storage for all uploaded media | S3 with CloudFront CDN |
| **Laravel Horizon** | Async job processing — notifications, emails, data sync, report generation | Runs on same EC2/ECS cluster |
| **CloudFront** | CDN for static assets (web app, images, media files) | AWS CloudFront |
| **ALB** | Load balancing, SSL termination, health checks | AWS Application Load Balancer |
| **WAF** | Firewall, rate limiting, IP filtering, bot protection | AWS WAF |

---

## 4. Data Architecture — What We Own vs. What Duke Owns

This is the most important section. The core architectural challenge is that data lives in multiple systems with different owners, and new data entities (inventory, ad-hoc catalog, loyalty) don't exist anywhere in Duke's systems today.

### Data Ownership Map

```
┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│   DUKE-OWNED DATA (Source of Truth = Duke CRM)                          │
│   We READ from Duke. We do NOT write to Duke for these.                 │
│                                                                          │
│   ┌─────────────────────────┐    ┌─────────────────────────┐           │
│   │  SAP Commerce (Hybris)   │    │  Microsoft Dynamics      │           │
│   │                          │    │                          │           │
│   │  • Duke Electric         │    │  • P&G Gas customer      │           │
│   │    customer identity     │    │    identity               │           │
│   │  • Business Partner ID   │    │  • Customer ID            │           │
│   │  • Premise addresses     │    │  • Premise addresses      │           │
│   │  • HPP plan catalog      │    │  • HPP plan catalog       │           │
│   │  • HPP enrollments       │    │  • HPP enrollments        │           │
│   │  • Billing info          │    │  • Service order history   │           │
│   │  • Contractor master     │    │  • Contractor assignments  │           │
│   │    records               │    │                          │           │
│   └─────────────────────────┘    └─────────────────────────┘           │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│   APP-OWNED DATA (Source of Truth = Our PostgreSQL)                      │
│   We own this entirely. Duke reads from us if needed.                   │
│                                                                          │
│   ┌───────────────────┐  ┌───────────────────┐  ┌──────────────────┐   │
│   │  App User Profiles │  │  Home Inventory    │  │  Ad-Hoc Service  │   │
│   │                    │  │                    │  │  Catalog         │   │
│   │  • App credentials │  │  • Appliances      │  │                  │   │
│   │  • Auth tokens     │  │  • Systems         │  │  • Services      │   │
│   │  • Preferences     │  │  • Make/model/     │  │  • Flat-rate     │   │
│   │  • Communication   │  │    serial          │  │    pricing       │   │
│   │    settings        │  │  • Warranty info   │  │  • Variable      │   │
│   │  • Notification    │  │  • Photos          │  │    pricing       │   │
│   │    opt-in/out      │  │  • Maintenance     │  │  • Territory     │   │
│   │  • Multi-property  │  │    schedules       │  │    availability  │   │
│   │    links           │  │  • Barcode data    │  │  • Promotions    │   │
│   └───────────────────┘  └───────────────────┘  └──────────────────┘   │
│                                                                          │
│   ┌───────────────────┐  ┌───────────────────┐  ┌──────────────────┐   │
│   │  Non-Native        │  │  Loyalty &         │  │  Reminders       │   │
│   │  Customer Profiles │  │  Gamification      │  │                  │   │
│   │                    │  │                    │  │  • Templates     │   │
│   │  • Full identity   │  │  • Points balance  │  │  • Frequencies   │   │
│   │  • No Duke/P&G     │  │  • Badges earned   │  │  • Asset-linked  │   │
│   │    link            │  │  • Profile score   │  │  • Custom user   │   │
│   │  • Address         │  │  • Home health     │  │    reminders     │   │
│   │  • Payment methods │  │    scorecard       │  │  • Service links │   │
│   └───────────────────┘  └───────────────────┘  └──────────────────┘   │
│                                                                          │
│   ┌───────────────────┐  ┌───────────────────┐  ┌──────────────────┐   │
│   │  Notifications     │  │  DIY Content       │  │  Analytics       │   │
│   │                    │  │                    │  │  Events          │   │
│   │  • Push/SMS/Email  │  │  • Articles        │  │                  │   │
│   │    records         │  │  • Videos          │  │  • User actions  │   │
│   │  • Delivery status │  │  • Guides          │  │  • Funnel data   │   │
│   │  • User prefs      │  │  • Categories      │  │  • Performance   │   │
│   └───────────────────┘  └───────────────────┘  └──────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────┐
│                                                                          │
│   SHARED DATA (Written by us, synced to/from Duke)                      │
│   Requires bi-directional sync or dual-write strategy                   │
│                                                                          │
│   ┌───────────────────────────────────────────────────────────────┐     │
│   │  Service Requests                                              │     │
│   │                                                                │     │
│   │  • Created in our app → must sync to Dynamics for contractor   │     │
│   │    dispatch and invoicing                                      │     │
│   │  • Status updates from Duke/contractor → must sync back to     │     │
│   │    our app for customer visibility                              │     │
│   │  • MVP: Manual admin sync (admin updates both systems)         │     │
│   │  • Phase 1+: API-based bi-directional sync                     │     │
│   └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│   ┌───────────────────────────────────────────────────────────────┐     │
│   │  HPP Enrollments (New / Changes / Cancellations)               │     │
│   │                                                                │     │
│   │  • Customer enrolls/cancels in app → must push to Commerce     │     │
│   │    or Dynamics for billing system activation                    │     │
│   │  • MVP: Enrollment queue → admin manually processes in CRM     │     │
│   │  • Phase 1+: Enrollment API writes directly to Commerce        │     │
│   └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
│   ┌───────────────────────────────────────────────────────────────┐     │
│   │  Contractor Configuration (Local Copy)                         │     │
│   │                                                                │     │
│   │  • Master data lives in CRM (contractor identity, licensing)   │     │
│   │  • We maintain local copy with extended fields:                 │     │
│   │    trade assignments, zip codes, lead times, availability      │     │
│   │  • MVP: Manual CSV import, then admin maintains in our system  │     │
│   │  • Phase 2: Nightly API sync from CRM                          │     │
│   └───────────────────────────────────────────────────────────────┘     │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

### Database Schema — Core Entities

```
┌──────────────────────────────────────────────────────────────────────┐
│  TENANTS (White-Label Foundation)                                     │
│  tenant_id PK | name | brand_config (JSON) | domain | active        │
└──────────────────────────────────────────────────────────────────────┘
        │
        │ Every table below scoped by tenant_id
        ▼
┌──────────────────────────────────────────────────────────────────────┐
│  USERS (App Customers)                                                │
│  user_id PK | tenant_id FK | email | password_hash                   │
│  first_name | last_name | phone                                       │
│  customer_type ENUM(duke_native, pg_native, non_native)              │
│  external_customer_id (Business Partner ID from Commerce/Dynamics)    │
│  email_verified_at | phone_verified_at                                │
│  communication_preferences (JSON)                                     │
│  loyalty_points INT | profile_completion_pct INT                     │
│  created_at | updated_at | last_login_at                             │
└───────────────────────────────┬──────────────────────────────────────┘
                                │
            ┌───────────────────┼───────────────────────┐
            │                   │                       │
            ▼                   ▼                       ▼
┌─────────────────┐  ┌──────────────────┐  ┌───────────────────────┐
│  PROPERTIES      │  │  HPP_ENROLLMENTS  │  │  PAYMENT_METHODS      │
│                  │  │  (Cached from     │  │  (App-owned for       │
│  property_id PK  │  │   Commerce/       │  │   non-native and      │
│  user_id FK      │  │   Dynamics)       │  │   credit card payers) │
│  address_line_1  │  │                   │  │                       │
│  address_line_2  │  │  enrollment_id PK │  │  payment_method_id PK │
│  city | state    │  │  user_id FK       │  │  user_id FK           │
│  zip_code        │  │  property_id FK   │  │  type ENUM(card,      │
│  property_type   │  │  external_plan_id │  │   ach, apple_pay)     │
│  sq_footage      │  │  plan_name        │  │  token (from gateway) │
│  year_built      │  │  status           │  │  last_four            │
│  premise_id      │  │  monthly_charge   │  │  is_default           │
│  (Duke/P&G ref)  │  │  billing_method   │  │  created_at           │
│  is_primary BOOL │  │  coverage (JSON)  │  └───────────────────────┘
│  created_at      │  │  synced_at        │
└────────┬─────────┘  └──────────────────┘
         │
         ▼
┌──────────────────────────────────────────────────────────────────────┐
│  HOME_INVENTORY                                                       │
│  inventory_id PK | property_id FK | user_id FK                       │
│  item_type ENUM(hvac, water_heater, electrical, plumbing, appliance) │
│  category (central_ac, heat_pump, tankless, etc.)                    │
│  make | model | serial_number                                         │
│  installation_date | age_years (calculated)                           │
│  warranty_provider | warranty_expiration                               │
│  location_in_home | energy_star BOOL                                  │
│  barcode_data | photos (S3 paths, JSON array)                        │
│  added_by ENUM(customer, admin, contractor)                           │
│  recall_status | recall_checked_at                                    │
│  created_at | updated_at                                              │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  CONTRACTORS (Local Copy + Extended Config)                           │
│  contractor_id PK | tenant_id FK                                     │
│  external_contractor_id (CRM reference)                              │
│  business_name | contact_name | phone | email                        │
│  status ENUM(active, inactive, suspended)                            │
│  license_numbers (JSON) | insurance_expiration                       │
│  created_at | updated_at | synced_from_crm_at                        │
└───────────────────────────────┬──────────────────────────────────────┘
                                │
                                ▼
┌──────────────────────────────────────────────────────────────────────┐
│  CONTRACTOR_TRADE_ASSIGNMENTS                                         │
│  assignment_id PK | contractor_id FK                                 │
│  trade ENUM(hvac, plumbing, electrical, water_heater, appliance)     │
│  zip_code VARCHAR(10)                                                 │
│  designation ENUM(primary, secondary)                                 │
│  lead_time_days INT                                                   │
│  availability_windows (JSON: [{day, start, end}])                    │
│  work_days (JSON: ["Mon","Tue","Wed"...])                            │
│  active BOOL                                                          │
│  created_at | updated_at                                              │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  SERVICE_REQUESTS                                                     │
│  service_request_id PK | tenant_id FK | user_id FK | property_id FK │
│  external_order_id (Dynamics/Commerce reference)                     │
│  request_type ENUM(hpp_covered, ad_hoc)                              │
│  trade ENUM(hvac, plumbing, electrical, water_heater, appliance)     │
│  problem_description TEXT | photos (JSON array of S3 paths)          │
│  inventory_item_id FK (nullable)                                     │
│  coverage_status ENUM(covered, not_covered, pending_review)          │
│  hpp_enrollment_id FK (nullable)                                     │
│  adhoc_service_id FK (nullable)                                      │
│  contractor_id FK (nullable)                                         │
│  scheduled_date | scheduled_window ENUM(morning, afternoon, full_day)│
│  status ENUM(pending_confirmation, confirmed, in_progress,           │
│              parts_ordered, completed, cancelled, disputed)           │
│  price_cents INT (0 for HPP-covered)                                 │
│  payment_status ENUM(not_required, pending, collected, refunded)     │
│  source ENUM(app, phone, admin)                                      │
│  admin_notes TEXT                                                     │
│  contractor_notes TEXT                                                │
│  completed_at | cancelled_at | created_at | updated_at               │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  ADHOC_SERVICES (Product Catalog)                                     │
│  service_id PK | tenant_id FK                                        │
│  service_name | service_sku                                           │
│  category | trade                                                     │
│  description TEXT | scope_of_work TEXT | exclusions TEXT              │
│  pricing_type ENUM(fixed, variable, quote_required)                  │
│  base_price_cents INT                                                 │
│  territory_pricing (JSON: [{zip_range, price_cents}])                │
│  duration_estimate VARCHAR                                            │
│  geographic_availability (JSON: [zip_codes or regions])              │
│  status ENUM(draft, active, inactive)                                │
│  created_by FK (admin_user) | created_at | updated_at                │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  REMINDERS                                                            │
│  reminder_id PK | tenant_id FK                                       │
│  type ENUM(system_template, user_custom)                             │
│  title | description                                                  │
│  frequency ENUM(monthly, quarterly, biannually, annually, seasonal)  │
│  asset_category (maps to inventory item_type)                        │
│  linked_service_id FK (nullable — "Book this service" CTA)           │
│  created_by FK (admin or user) | status ENUM(active, inactive)       │
└────────────────────┬─────────────────────────────────────────────────┘
                     ▼
┌──────────────────────────────────────────────────────────────────────┐
│  USER_REMINDERS (Instance per user)                                   │
│  user_reminder_id PK | user_id FK | reminder_id FK                   │
│  inventory_item_id FK (nullable)                                     │
│  next_due_date | last_completed_at                                    │
│  status ENUM(active, snoozed, dismissed, completed)                  │
│  snooze_until                                                         │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  LOYALTY_EVENTS                                                       │
│  event_id PK | user_id FK                                            │
│  event_type ENUM(profile_complete, inventory_add, service_booked,    │
│              survey_completed, inventory_reviewed, badge_earned)      │
│  points_earned INT | badge_id FK (nullable)                          │
│  created_at                                                           │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  ENROLLMENT_QUEUE (MVP Manual Fallback)                               │
│  queue_id PK | user_id FK | property_id FK                          │
│  plan_name | plan_details (JSON) | billing_method                    │
│  status ENUM(pending, in_progress, processed, failed)                │
│  assigned_to FK (admin_user) | processed_at | admin_notes TEXT       │
│  created_at                                                           │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  ADMIN_USERS                                                          │
│  admin_user_id PK | tenant_id FK                                     │
│  name | email | password_hash                                         │
│  role ENUM(csr_enrollment, csr_support, back_office, product_mgr,    │
│       ops_manager, escalation, analyst, super_admin)                  │
│  permissions (JSON) | last_login_at | created_at                     │
└──────────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────────┐
│  ESCALATION_TICKETS                                                   │
│  ticket_id PK | service_request_id FK (nullable)                     │
│  user_id FK | assigned_to FK (admin_user)                            │
│  category | description TEXT | priority ENUM(low, med, high, urgent) │
│  status ENUM(open, in_progress, resolved, closed)                    │
│  resolution_notes TEXT | created_at | resolved_at                    │
└──────────────────────────────────────────────────────────────────────┘
```

### Entity Relationship Summary

```
TENANT ──< USER ──< PROPERTY ──< HOME_INVENTORY
                 ──< HPP_ENROLLMENT
                 ──< SERVICE_REQUEST >── CONTRACTOR
                 ──< USER_REMINDER >── REMINDER
                 ──< LOYALTY_EVENT
                 ──< PAYMENT_METHOD

SERVICE_REQUEST >── ADHOC_SERVICE (if ad-hoc)
SERVICE_REQUEST >── HPP_ENROLLMENT (if covered)
SERVICE_REQUEST >── HOME_INVENTORY (optional link)

CONTRACTOR ──< CONTRACTOR_TRADE_ASSIGNMENT

ADHOC_SERVICE (standalone catalog, no user FK)
REMINDER (templates, linked to services)
ADMIN_USER ──< ENROLLMENT_QUEUE
ADMIN_USER ──< ESCALATION_TICKET
```

---

## 5. API Layer Design

### API Structure

All clients (iOS, Android, web, admin) consume the same REST API. Authentication determines what data is returned.

```
Base URL: https://api.dukehomeservices.com/v1

Authentication:
  POST   /auth/register
  POST   /auth/login
  POST   /auth/forgot-password
  POST   /auth/reset-password
  POST   /auth/refresh-token
  DELETE /auth/logout

Customer Profile:
  GET    /me                              → current user profile
  PUT    /me                              → update profile
  PUT    /me/preferences                  → update communication prefs
  GET    /me/loyalty                      → points, badges, score

Properties:
  GET    /properties                      → list user's properties
  POST   /properties                      → add property
  PUT    /properties/{id}                 → update property
  DELETE /properties/{id}                 → remove property

Customer Validation (Duke/P&G):
  POST   /validate/customer               → check address against Commerce/Dynamics
                                            returns: match status, Business Partner ID,
                                            premise IDs, HPP plans

HPP Plans:
  GET    /properties/{id}/plans           → plans for a property (cached from CRM)
  POST   /plans/enroll                    → enroll in new plan (→ queue if API unavailable)
  POST   /plans/{id}/cancel               → cancel plan (→ queue if API unavailable)
  PUT    /plans/{id}/modify               → upgrade/downgrade

Home Inventory:
  GET    /properties/{id}/inventory       → all items for property
  POST   /properties/{id}/inventory       → add item (manual or barcode)
  PUT    /inventory/{id}                  → update item
  DELETE /inventory/{id}                  → remove item
  POST   /inventory/barcode-lookup        → scan barcode → return product data

Service Requests:
  POST   /service-requests                → create booking
  GET    /service-requests                → list user's requests (filterable)
  GET    /service-requests/{id}           → request detail + status
  PUT    /service-requests/{id}/reschedule → reschedule
  PUT    /service-requests/{id}/cancel    → cancel

Contractor Matching:
  POST   /contractors/match               → trade + zip → primary contractor + availability
  GET    /contractors/{id}/availability   → available time windows

Ad-Hoc Service Catalog:
  GET    /services                         → browse catalog (filtered by zip, category)
  GET    /services/{id}                    → service detail + pricing for user's zip

Reminders:
  GET    /reminders                        → user's active reminders
  PUT    /reminders/{id}/complete          → mark done
  PUT    /reminders/{id}/snooze            → snooze
  PUT    /reminders/{id}/dismiss           → dismiss
  POST   /reminders                        → create custom reminder

DIY Content:
  GET    /content                           → browse/search articles
  GET    /content/{id}                      → article detail

Notifications:
  GET    /notifications                     → notification center
  PUT    /notifications/{id}/read           → mark as read
  POST   /devices                           → register device for push (APNs/FCM token)
  DELETE /devices/{token}                   → unregister device

Service History:
  GET    /service-history                   → all past services (filterable)
  GET    /service-history/{id}/export       → PDF export

--- ADMIN ENDPOINTS (requires admin role) ---

Admin:
  GET    /admin/dashboard                   → KPI metrics
  GET    /admin/customers                   → search/list customers
  GET    /admin/customers/{id}              → full customer profile (aggregated)
  PUT    /admin/customers/{id}              → edit customer

  GET    /admin/service-requests            → all requests (filterable, sortable)
  PUT    /admin/service-requests/{id}       → update status, reassign contractor, add notes

  GET    /admin/enrollment-queue            → pending enrollments
  PUT    /admin/enrollment-queue/{id}       → process enrollment

  CRUD   /admin/services                    → manage ad-hoc catalog
  CRUD   /admin/reminders                   → manage reminder templates
  CRUD   /admin/contractors                 → manage contractor config
  CRUD   /admin/contractor-assignments      → manage trade/zip assignments

  GET    /admin/escalations                 → escalation tickets
  POST   /admin/escalations                 → create ticket
  PUT    /admin/escalations/{id}            → update/resolve

  GET    /admin/analytics/*                 → various reporting endpoints
```

### API Versioning Strategy

- URL-based versioning: `/v1/`, `/v2/`
- Mobile apps ship with a specific API version. Old versions must remain supported until force-update threshold
- Admin portal always uses latest API version (it's a web app, always up to date)

### Caching Strategy

| Data | Cache Duration | Cache Location | Invalidation |
|---|---|---|---|
| HPP plan details | 1 hour | Redis | On enrollment change event |
| Ad-hoc service catalog | 15 minutes | Redis | On admin catalog update |
| Contractor assignments | 1 hour | Redis | On admin config change |
| Customer profile | 5 minutes | Redis | On profile update |
| DIY content | 1 hour | Redis + CDN | On content publish |
| Home inventory | No cache (real-time) | — | — |
| Service request status | No cache (real-time) | — | — |
| Dashboard analytics | 5 minutes | Redis | Time-based expiry |

---

## 6. Frontend Architecture — Customer App + Web

### React Native App Architecture (iOS + Android)

```
┌─────────────────────────────────────────────────────────────────┐
│  React Native Application                                        │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  NAVIGATION (React Navigation)                            │   │
│  │                                                           │   │
│  │  Tab Navigator                                            │   │
│  │  ├── Home (Dashboard)                                     │   │
│  │  ├── Services (Browse catalog + Book)                     │   │
│  │  ├── My Home (Inventory + Reminders + Health Score)       │   │
│  │  ├── Activity (Service history + Notifications)           │   │
│  │  └── Account (Profile + Plans + Settings)                 │   │
│  │                                                           │   │
│  │  Stack Navigators (per tab for drill-down screens)        │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  STATE MANAGEMENT                                         │   │
│  │                                                           │   │
│  │  React Query (TanStack Query)                             │   │
│  │  ├── Server state: API data (plans, inventory, requests)  │   │
│  │  ├── Auto-caching, background refresh, stale-while-       │   │
│  │  │   revalidate                                           │   │
│  │  └── Offline persistence (AsyncStorage adapter)           │   │
│  │                                                           │   │
│  │  Zustand (or React Context)                               │   │
│  │  ├── Client state: auth tokens, selected property,        │   │
│  │  │   navigation state, form drafts                        │   │
│  │  └── Minimal — most state is server state via React Query │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  NATIVE MODULES                                           │   │
│  │                                                           │   │
│  │  Camera / Barcode Scanner                                 │   │
│  │  ├── react-native-camera or expo-camera                   │   │
│  │  └── Barcode library (ML Kit or ZXing)                    │   │
│  │                                                           │   │
│  │  Push Notifications                                       │   │
│  │  ├── @react-native-firebase/messaging (FCM for Android)   │   │
│  │  └── @react-native-community/push-notification-ios (APNs) │   │
│  │                                                           │   │
│  │  Secure Storage                                           │   │
│  │  └── react-native-keychain (auth tokens, NOT AsyncStorage)│   │
│  │                                                           │   │
│  │  Biometrics                                               │   │
│  │  └── react-native-biometrics (Face ID / Touch ID /        │   │
│  │      fingerprint)                                          │   │
│  │                                                           │   │
│  │  Deep Linking                                             │   │
│  │  └── react-navigation deep links (push notification →     │   │
│  │      service request detail screen)                        │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  API CLIENT                                               │   │
│  │                                                           │   │
│  │  Axios (HTTP client)                                      │   │
│  │  ├── Base URL per environment (dev/staging/prod)          │   │
│  │  ├── JWT token auto-attach via interceptor                │   │
│  │  ├── Token refresh on 401 response                        │   │
│  │  ├── Request/response logging (dev only)                  │   │
│  │  └── Retry logic for network failures                     │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  OFFLINE SUPPORT                                          │   │
│  │                                                           │   │
│  │  React Query Persister (AsyncStorage)                     │   │
│  │  ├── Cached: HPP plans, inventory, service history,       │   │
│  │  │          DIY content, reminder list                     │   │
│  │  ├── NOT cached: active service request status (must be   │   │
│  │  │   real-time), booking flow, payment                    │   │
│  │  └── Stale data indicator when offline                    │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  ANALYTICS & CRASH REPORTING                              │   │
│  │                                                           │   │
│  │  Sentry (crash reporting + performance monitoring)        │   │
│  │  Firebase Analytics (user behavior + funnel tracking)     │   │
│  │  Google Tag Manager (Duke brand requirement — all Duke-   │   │
│  │    branded pages must include GTM)                         │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

### Vue.js Web App Architecture

The web app provides the same features as the mobile app, accessible via browser. It is a separate codebase (Vue.js, not React Native Web) but consumes the same API.

```
Vue.js SPA (Single Page Application) with PWA capabilities
├── Vue Router (client-side routing, mirrors mobile app navigation)
├── Pinia (state management — equivalent to Zustand on mobile)
├── Axios (same API client config as mobile)
├── PWA Service Worker
│   ├── Offline caching for static assets and content
│   ├── Push notification support (where browser supports)
│   └── Add-to-homescreen prompt
├── Responsive design (desktop → tablet → mobile breakpoints)
├── Google Tag Manager integration (Duke brand requirement)
└── Hosted on CloudFront (CDN, S3 static hosting)
```

### Code Sharing Strategy Between Mobile and Web

**These are NOT shared codebases.** React Native (mobile) and Vue.js (web) are separate projects. What they share:

| Shared | How |
|---|---|
| API contract | Both call the same Laravel API with the same request/response format |
| Business rules | Enforced server-side in Laravel — never duplicated on client |
| Design system | Shared design tokens (colors, typography, spacing) in a shared Figma library, implemented natively in each framework |
| Feature parity | Same features, same screens, same flows — but native implementation per platform |

**Why not React Native Web?** React Native Web exists but produces mediocre web experiences for data-heavy applications. A dedicated Vue.js web app delivers better SEO, faster load times, and a more natural desktop experience. The proposal specifies Vue.js for web — this is the correct choice.

---

## 7. Admin Portal Architecture

```
Vue.js Admin SPA
├── Authentication (SSO via Duke corporate identity OR local auth)
├── Role-based access control (7 roles defined in scope)
├── Dashboard framework (charts, metrics, real-time counters)
├── Data tables (customer search, service request queue, contractor list)
├── Form builders (service catalog CRUD, contractor config, reminders)
├── Notification center (admin alerts for new service requests, escalations)
├── Reporting / export (PDF, CSV export for analytics)
└── Same Laravel API (admin-scoped endpoints)
```

The admin portal is a web-only application — no mobile admin app. Duke operations staff access it from desktop browsers. It shares the same Vue.js framework as the customer web app for consistency but is a separate application with its own routing, authentication, and role-based views.

---

## 8. Integration Architecture — Duke Systems

### Integration Gateway Pattern

The Laravel API acts as an **Integration Gateway** — a single point of contact between our platform and all Duke systems. No client application ever calls Duke directly.

```
┌──────────────────────┐
│  Customer App / Web   │
│  Admin Portal         │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────────────────────────────────────────────┐
│  LARAVEL INTEGRATION GATEWAY                                  │
│                                                               │
│  ┌───────────────────────────────────────────────────────┐   │
│  │  Integration Service Layer                             │   │
│  │                                                        │   │
│  │  CommerceApiService.php                                │   │
│  │  ├── validateCustomer(address, lastName)                │   │
│  │  ├── getCustomerPlans(businessPartnerId)                │   │
│  │  ├── enrollInPlan(businessPartnerId, planId, billing)   │   │
│  │  └── cancelPlan(businessPartnerId, planId)              │   │
│  │                                                        │   │
│  │  DynamicsApiService.php                                │   │
│  │  ├── validateCustomer(address, lastName)                │   │
│  │  ├── getCustomerPlans(customerId)                       │   │
│  │  ├── createServiceOrder(orderDetails)                   │   │
│  │  ├── getServiceOrderStatus(orderId)                     │   │
│  │  └── getServiceHistory(customerId)                      │   │
│  │                                                        │   │
│  │  UnifiedCustomerService.php                            │   │
│  │  ├── validate(address, lastName)                        │   │
│  │  │   → tries Commerce first, then Dynamics              │   │
│  │  │   → returns unified CustomerProfile                  │   │
│  │  ├── getPlans(userId)                                   │   │
│  │  │   → merges Commerce + Dynamics plans                 │   │
│  │  └── syncCustomerData(userId)                           │   │
│  │      → pulls latest from CRM, updates local cache       │   │
│  │                                                        │   │
│  │  ContractorMatchingService.php                         │   │
│  │  ├── findContractor(trade, zipCode)                     │   │
│  │  │   → queries local contractor_trade_assignments       │   │
│  │  ├── getAvailability(contractorId, trade, dateRange)    │   │
│  │  │   → calculates from static buffers (MVP)             │   │
│  │  │   → queries FSM API (Phase 2)                        │   │
│  │  └── assignContractor(serviceRequestId, contractorId)   │   │
│  └───────────────────────────────────────────────────────┘   │
│                                                               │
│  ┌───────────────────────────────────────────────────────┐   │
│  │  Circuit Breaker + Fallback Pattern                    │   │
│  │                                                        │   │
│  │  When Commerce/Dynamics API is down or slow:           │   │
│  │  1. Circuit breaker opens after 3 consecutive failures  │   │
│  │  2. Requests served from Redis cache (stale data OK)   │   │
│  │  3. Write operations queued for retry                   │   │
│  │  4. Admin notified of integration failure               │   │
│  │  5. Circuit breaker retries every 30 seconds            │   │
│  │  6. When API recovers, queued operations processed      │   │
│  └───────────────────────────────────────────────────────┘   │
│                                                               │
│  ┌───────────────────────────────────────────────────────┐   │
│  │  Data Sync Jobs (Laravel Scheduled Tasks)              │   │
│  │                                                        │   │
│  │  Every 1 hour:  Sync HPP plan changes for active users │   │
│  │  Every 6 hours: Sync contractor status from CRM        │   │
│  │  Every 24 hours: Full contractor data reconciliation    │   │
│  │  Every 24 hours: Service request status sync from CRM  │   │
│  │  On demand: Customer validation on login/registration   │   │
│  └───────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘
```

### MVP vs. Phase 1 vs. Phase 2 Integration Approach

| Integration | MVP | Phase 1 (post-MVP) | Phase 2 |
|---|---|---|---|
| **Customer validation** | API call to Commerce/Dynamics | Same | Same + SSO with Duke utility app |
| **HPP plan lookup** | API call to Commerce/Dynamics | Same | Same |
| **HPP enrollment/cancel** | Enrollment queue → admin manually processes in CRM | Direct API write to Commerce/Dynamics | Same |
| **Service order creation** | Created in our DB + admin manually enters in CRM | API write to Dynamics | Same |
| **Service order status** | Admin manually updates our DB when contractor reports back | Webhook/polling from Dynamics | FSM real-time status |
| **Contractor matching** | Local DB query (trade + zip code) | Same | FSM API with real-time availability |
| **Contractor data** | One-time CSV import + admin maintains | Nightly API sync from CRM | Real-time API + FSM |
| **Payment** | Contractor collects on-site | Stripe/payment gateway for ad-hoc | Full in-app payments |
| **FSM integration** | N/A | N/A | ServicePower or similar — GPS, calendar, auto-dispatch |

---

## 9. Push Notification Architecture

Push notifications are business-critical. The entire "real-time updates" value proposition depends on them.

```
┌─────────────────────────────────────────────────────────────────┐
│  NOTIFICATION DISPATCH FLOW                                      │
│                                                                  │
│  Trigger Event                                                   │
│  (service request status change, reminder due, admin action)     │
│       │                                                          │
│       ▼                                                          │
│  ┌──────────────────────────────────┐                           │
│  │  NotificationService.php          │                           │
│  │                                   │                           │
│  │  1. Look up user preferences      │                           │
│  │     (push, SMS, email, in-app)    │                           │
│  │  2. Create notification record    │                           │
│  │  3. Dispatch to selected channels │                           │
│  └──────────┬────────┬──────┬───────┘                           │
│             │        │      │                                    │
│        ┌────▼───┐ ┌──▼──┐ ┌▼──────┐ ┌──────────┐              │
│        │  Push  │ │ SMS │ │ Email │ │ In-App   │              │
│        │Notif.  │ │     │ │       │ │Notif.    │              │
│        │Job     │ │Job  │ │Job    │ │Center    │              │
│        └───┬────┘ └──┬──┘ └┬──────┘ └──────────┘              │
│            │         │     │                                    │
│       ┌────▼────┐  ┌─▼──┐ ┌▼────────┐                         │
│       │ APNs    │  │SNS │ │SendGrid │                         │
│       │ (iOS)   │  │or  │ │or SES   │                         │
│       │ FCM     │  │Twi │ │         │                         │
│       │(Android)│  │lio │ │         │                         │
│       └─────────┘  └────┘ └─────────┘                         │
└─────────────────────────────────────────────────────────────────┘
```

### Notification Types for MVP

| Event | Push | SMS | Email | In-App |
|---|---|---|---|---|
| Service request submitted | Yes | Yes | Yes | Yes |
| Service request confirmed | Yes | Yes | Yes | Yes |
| Appointment changed | Yes | Yes | Yes | Yes |
| Service completed | Yes | Yes | Yes | Yes |
| Maintenance reminder due | Yes | No | Yes | Yes |
| Inventory item added by contractor | Yes | No | No | Yes |
| Loyalty points earned | Yes | No | No | Yes |
| HPP plan enrollment confirmed | Yes | Yes | Yes | Yes |
| Admin broadcast (service area alert) | Yes | Yes | Yes | Yes |

### Device Token Management

```
User installs app → registers device token (APNs or FCM)
  → POST /devices { platform: "ios", token: "abc123" }
  → stored in devices table, linked to user_id

User has multiple devices → all receive push notifications
User logs out → token deregistered
Token refresh (Apple/Google rotate tokens) → app auto-updates
```

---

## 10. Security Architecture

### Authentication Flow

```
Customer Registration:
  1. User submits: email, password, name, phone, address
  2. Server validates, creates user record
  3. If Duke/P&G address detected → calls Commerce/Dynamics validation API
  4. If match found → links external_customer_id, loads HPP plans
  5. If no match → user created as non-native
  6. Email verification sent
  7. JWT access token (15min) + refresh token (30 days) returned

Customer Login:
  1. User submits: email, password
  2. Server validates credentials
  3. Optional: biometric (Face ID / Touch ID) using stored refresh token
  4. JWT access token + refresh token returned
  5. Background: sync latest data from Commerce/Dynamics if stale

Admin Login:
  1. MVP: email/password with MFA (TOTP)
  2. Phase 2: SSO via Duke corporate identity (SAML/OAuth2 with Azure AD)
```

### Security Layers

| Layer | Implementation |
|---|---|
| **Transport** | TLS 1.3 everywhere. No HTTP — only HTTPS. HSTS headers. |
| **API Authentication** | JWT tokens (short-lived access + long-lived refresh). Tokens stored in Keychain (iOS) / EncryptedSharedPreferences (Android). NEVER in AsyncStorage. |
| **Authorization** | Role-based access control (RBAC). Admin roles enforce permission checks on every endpoint. Customer can only access own data. |
| **Input Validation** | Laravel Form Request validation on every endpoint. Sanitize all inputs. Parameterized queries (no raw SQL). |
| **Rate Limiting** | Per-user rate limits on auth endpoints (prevent brute force). Per-IP rate limits on public endpoints. Redis-backed. |
| **Data Encryption** | AES-256 encryption for sensitive fields at rest (PII). PostgreSQL connection encrypted. S3 server-side encryption. |
| **Secrets Management** | AWS Secrets Manager for API keys, database credentials, Duke API credentials. Never in code or environment files. |
| **Audit Logging** | Every admin action logged (who did what, when, from where). Customer data access logged. Retained per Duke compliance requirements. |
| **Network** | VPC with public/private subnets. API servers in private subnet. Database in private subnet, no public access. Security groups restrict traffic. |
| **WAF** | AWS WAF rules: SQL injection protection, XSS protection, rate limiting, geographic restrictions if required. |
| **GDPR/CCPA** | Data export endpoint (customer can request their data). Data deletion endpoint (right to be forgotten). Consent tracking for marketing. |
| **Duke VPN** | Secure VPN tunnel between our AWS VPC and Duke's network for Commerce/Dynamics API access. |

---

## 11. Infrastructure & Deployment

### Environment Strategy

| Environment | Purpose | URL Pattern | Duke Access |
|---|---|---|---|
| **Local** | Developer machines | localhost | No |
| **Development** | Shared dev, latest code | dev-api.dukehomeservices.com | No |
| **Staging** | Pre-production mirror, UAT | staging-api.dukehomeservices.com | Yes (Duke PM + QA) |
| **Production** | Live users | api.dukehomeservices.com | Yes (all) |

### CI/CD Pipeline

```
Developer pushes code to GitHub
    │
    ▼
GitHub Actions runs:
    ├── PHPUnit tests (Laravel backend)
    ├── Jest tests (React Native)
    ├── ESLint + code quality checks
    ├── Security vulnerability scan (Snyk or similar)
    │
    ▼ (if all pass)
    ├── Build Laravel Docker image → push to ECR
    ├── Build React Native iOS → upload to TestFlight (via Fastlane)
    ├── Build React Native Android → upload to Play Console Internal Testing
    ├── Build Vue.js web app → deploy to S3/CloudFront (staging)
    ├── Build Vue.js admin portal → deploy to S3/CloudFront (staging)
    │
    ▼ (manual approval for production)
    ├── Deploy Laravel to production ECS cluster (blue/green)
    ├── Submit iOS to App Store (manual trigger)
    ├── Submit Android to Play Store (manual trigger)
    ├── Deploy web app to production CDN
    └── Deploy admin portal to production CDN
```

### Infrastructure Sizing (MVP Estimate)

| Component | Sizing | Notes |
|---|---|---|
| **API Servers (ECS)** | 2x t3.medium (2 vCPU, 4GB) | Auto-scale to 4 at peak |
| **Queue Workers** | 1x t3.small (dedicated) | Horizon for async jobs |
| **PostgreSQL (RDS)** | db.t3.medium (2 vCPU, 4GB) | Multi-AZ, automated backups |
| **Redis (ElastiCache)** | cache.t3.small | Single node sufficient for MVP |
| **S3** | Standard storage | Pay per use |
| **CloudFront** | Standard distribution | Web app + static assets |
| **Estimated monthly cost** | $800-$1,200/month | Scales with traffic |

---

## 12. Data Flow Diagrams — Key Workflows

### Flow 1: Duke Customer Registration & Validation

```
Customer                    App (React Native)         Laravel API              Commerce/Dynamics
   │                              │                        │                          │
   │  Enter email, password,      │                        │                          │
   │  name, phone, address        │                        │                          │
   │ ─────────────────────────▶   │                        │                          │
   │                              │  POST /auth/register   │                          │
   │                              │ ───────────────────▶   │                          │
   │                              │                        │  POST /validate          │
   │                              │                        │  {address, lastName}     │
   │                              │                        │ ──────────────────────▶  │
   │                              │                        │                          │
   │                              │                        │  ◀─ { match: true,       │
   │                              │                        │       bpId: "BP123",     │
   │                              │                        │       premiseIds: [...], │
   │                              │                        │       plans: [...] }     │
   │                              │                        │                          │
   │                              │                        │  Create user record      │
   │                              │                        │  (customer_type:         │
   │                              │                        │   duke_native)           │
   │                              │                        │  Cache HPP plans         │
   │                              │                        │  Create property records │
   │                              │                        │                          │
   │                              │  ◀─ { user, token,     │                          │
   │                              │       plans, props }   │                          │
   │  ◀────── Welcome screen ───  │                        │                          │
   │  "You have 2 HPP plans"      │                        │                          │
   │  "2 properties linked"       │                        │                          │
```

### Flow 2: Non-Native Customer Registration

```
Customer                    App (React Native)         Laravel API              Commerce/Dynamics
   │                              │                        │                          │
   │  Enter email, password,      │                        │                          │
   │  name, phone, address        │                        │                          │
   │ ─────────────────────────▶   │                        │                          │
   │                              │  POST /auth/register   │                          │
   │                              │ ───────────────────▶   │                          │
   │                              │                        │  POST /validate          │
   │                              │                        │  {address, lastName}     │
   │                              │                        │ ──────────────────────▶  │
   │                              │                        │                          │
   │                              │                        │  ◀─ { match: false }     │
   │                              │                        │                          │
   │                              │                        │  Create user record      │
   │                              │                        │  (customer_type:         │
   │                              │                        │   non_native)            │
   │                              │                        │  Create property record  │
   │                              │                        │  No HPP plans            │
   │                              │                        │                          │
   │                              │  ◀─ { user, token }    │                          │
   │  ◀── Welcome screen ───────  │                        │                          │
   │  "Browse services in your    │                        │                          │
   │   area" + "Build your home   │                        │                          │
   │   profile for $10 credit"    │                        │                          │
```

### Flow 3: HPP Service Booking (MVP — Manual Fallback)

```
Customer          App            Laravel API        PostgreSQL       Admin Portal    Contractor
   │               │                  │                 │                 │              │
   │ Book Service  │                  │                 │                 │              │
   │ ─────────▶    │                  │                 │                 │              │
   │               │ POST /service-   │                 │                 │              │
   │               │ requests         │                 │                 │              │
   │               │ ────────────▶    │                 │                 │              │
   │               │                  │ Check coverage  │                 │              │
   │               │                  │ (cached HPP)    │                 │              │
   │               │                  │ ──────────▶     │                 │              │
   │               │                  │ ◀──────────     │                 │              │
   │               │                  │                 │                 │              │
   │               │                  │ Match contractor│                 │              │
   │               │                  │ (trade + zip)   │                 │              │
   │               │                  │ ──────────▶     │                 │              │
   │               │                  │ ◀── ABC HVAC    │                 │              │
   │               │                  │                 │                 │              │
   │               │                  │ Create service  │                 │              │
   │               │                  │ request record  │                 │              │
   │               │                  │ status: pending │                 │              │
   │               │                  │ ──────────▶     │                 │              │
   │               │                  │                 │                 │              │
   │               │                  │ Dispatch push   │                 │              │
   │               │                  │ notification    │                 │              │
   │               │                  │ to admin ───────┼────────────▶    │              │
   │               │                  │                 │   "New request  │              │
   │               │                  │                 │    from Eleanor"│              │
   │               │                  │                 │                 │              │
   │               │ ◀── 201 Created  │                 │                 │              │
   │ ◀── "Request  │   {requestId,    │                 │                 │              │
   │  submitted,   │    status:       │                 │                 │              │
   │  contractor   │    pending,      │                 │                 │              │
   │  ABC HVAC     │    contractor}   │                 │                 │              │
   │  assigned"    │                  │                 │                 │              │
   │               │                  │                 │                 │              │
   │               │                  │                 │    Admin calls  │              │
   │               │                  │                 │    contractor   │              │
   │               │                  │                 │    within 1hr   │──────────▶   │
   │               │                  │                 │                 │              │
   │               │                  │                 │                 │ ◀── Accepted │
   │               │                  │                 │    Admin updates│   Thu 9-12   │
   │               │                  │                 │    status ──────┤              │
   │               │                  │                 │                 │              │
   │               │                  │ ◀── status:     │                 │              │
   │               │                  │     confirmed   │                 │              │
   │               │                  │                 │                 │              │
   │               │                  │ Push to customer│                 │              │
   │ ◀── "Your     │ ◀───────────     │                 │                 │              │
   │  appointment  │                  │                 │                 │              │
   │  is confirmed!│                  │                 │                 │              │
   │  ABC HVAC     │                  │                 │                 │              │
   │  Thu 9-12am"  │                  │                 │                 │              │
```

---

## 13. Phase 2 Architecture Considerations

These features are NOT in MVP or Phase 1 but the architecture must not block them.

### FSM Integration (Phase 2)

```
Current (MVP):
  App → Laravel → PostgreSQL → Admin manually contacts contractor

Phase 2:
  App → Laravel → FSM API (ServicePower/etc.) → Contractor Mobile App
                                               → Real-time GPS tracking
                                               → Auto-status updates
                                               → Calendar availability

Architecture prep:
  • ContractorMatchingService already abstracts matching logic
  • Add FsmApiService implementing same interface
  • Feature flag: use_fsm_integration = true/false
  • Webhook endpoint for FSM status callbacks
```

### In-App Payment (Phase 2)

```
Architecture prep:
  • payment_methods table already exists
  • PaymentService interface defined (strategy pattern)
  • MVP implementation: NullPaymentService (contractor collects)
  • Phase 2 implementation: StripePaymentService
  • payment_status field on service_requests ready for payment states
```

### White-Label / Multi-Tenant (Phase 2+)

```
Architecture prep (built from Day 1):
  • tenant_id on every table
  • Brand config (JSON) per tenant: colors, logos, names, feature flags
  • API responses scoped by tenant
  • Separate app store listings per tenant (future)
  • Data isolation: queries always filtered by tenant_id

Why Day 1: Retrofitting multi-tenancy is one of the most expensive
architectural changes. Duke's roadmap explicitly includes white-labeling
for other utilities. Building it in from the start costs <5% more;
retrofitting later costs 3-6 months of rework.
```

### AI Virtual Assistant (Phase 2+)

```
Architecture prep:
  • Troubleshooting flow data (symptom → diagnosis → resolution) tracked
  • Content tagged with appliance types and symptom keywords
  • Service request history provides training data
  • API endpoint for conversational interface: POST /assistant/chat
  • Can integrate Claude or similar LLM for troubleshooting guidance
```

---

## 14. Open Questions & Decisions Needed

These must be resolved before or during the first 4 weeks of development.

### Blocking (Must resolve before Sprint 1)

| # | Question | Decision Owner | Impact |
|---|---|---|---|
| 1 | **Customer app platform confirmed as native?** | Duke + Orases | Gates all frontend work. See Platform Decision document. |
| 2 | **Apple Developer Account (Organization) — who initiates?** | Duke IT | Requires D-U-N-S number. Can take 2 weeks. |
| 3 | **Commerce API documentation and sandbox access** | Duke IT | Blocking for customer validation and HPP plan integration. Per RFP: within 2 weeks of kickoff. |
| 4 | **Dynamics API documentation and sandbox access** | Duke IT | Same — blocking for P&G customers and service orders. |
| 5 | **VPN setup between AWS and Duke network** | Duke IT + Orases | Blocking for any real API integration testing. |

### High Priority (Resolve by Week 4)

| # | Question | Decision Owner | Impact |
|---|---|---|---|
| 6 | **HPP coverage rules — where do they live?** | Duke Business | Core to coverage check logic. Not systematized today. Orases needs structured data to implement. |
| 7 | **Contractor data export format and timeline** | Duke IT/Ops | Need CSV/JSON of 125-140 contractors to seed contractor_trade_assignments table. |
| 8 | **Admin portal SSO or separate auth?** | Duke IT | Determines authentication architecture for admin users. |
| 9 | **Payment gateway selection (Phase 1+)** | Duke + Orases | Stripe recommended. Duke may have existing relationships. Affects PaymentService implementation. |
| 10 | **Google Tag Manager container ID** | Duke Marketing | Required on all Duke-branded pages (SOW requirement). |

### Medium Priority (Resolve by Week 8)

| # | Question | Decision Owner | Impact |
|---|---|---|---|
| 11 | **Ad-hoc service catalog — initial 5-10 services defined?** | Duke Business | Needed to build catalog screens and test booking flows. |
| 12 | **Pilot market(s) for ad-hoc services** | Duke Business | Determines geographic filtering logic and test contractor availability. |
| 13 | **Duke Data Fabric — will it be the integration layer?** | Duke IT | Affects whether we call Commerce/Dynamics directly or go through Data Fabric. |
| 14 | **Non-native customer — does inventory data ever flow to Duke?** | Duke Business | Determines if we need to build a data export/sync for non-native data. |
| 15 | **Loyalty point values and redemption rules** | Duke Business | Needed to implement LoyaltyService logic. |

---

*This document is a living artifact. It will be refined as Duke IT provides API documentation, as PRDs are approved, and as technical decisions are validated during Sprint 0 and Sprint 1.*

*Source documents: Customer App Scope (9 docs), Admin Portal Scope (12 docs), Contractor Portal Scope (17 docs), Data Entities & Workflows Analysis, SOW #1 V6, Proposal*

*Prepared by: Aksana Rahouski, Product Manager (Orases)*
