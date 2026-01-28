# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---

## KEY INTEGRATIONS & DEPENDENCIES

### Integration Architecture

**Admin Portal as "Middle Layer":**

```
[Duke CRM - Commerce]  ←→  [Admin Portal Backend]  ←→  [Customer App]
[P&G CRM - Dynamics]   ←→                           ←→  [Contractor Portal]
[App Database]         ←→                           ←→  [Analytics Tools]
```

**Admin portal aggregates data from:**
- Commerce (Duke customer data, HPP plans)
- Dynamics (P&G customer data, service requests)
- App Database (non-native customers, home inventory, ad-hoc services, reminders)

---

### 1. Customer Validation & HPP Plan APIs

**Status:** WILL EXIST by MVP launch (confirmed by Duke team)

**APIs Needed:**
- Validate if customer is Duke/P&G utility customer
- Retrieve customer HPP plan subscriptions
- Check subscription status (active, suspended, cancelled)

**Usage:**
- Customer logs into app → API validates against Commerce/Dynamics
- Customer views "My Plans" → API retrieves active HPP plans
- Customer books service → API checks if service covered under plan

---

### 2. Service Request Creation API

**Status:** MAY NOT EXIST for MVP - Manual fallback required

**API Needed:**
- Create service request in Dynamics (CRM)
- Pass all service request details: customer, service type, problem description, inventory details, date/time preference

**MVP Fallback:**
- Service request created in app backend
- Admin manually enters into CRM, OR
- Automated email/queue sent to operations team to manually process

---

### 3. Contractor Data & Assignment

**Status:** Exists in CRM but may need local copy for scheduling logic

**Current State:**
- Contractor data in CRM/Dynamics: trade, zip code coverage, primary/secondary designation
- Automatic assignment: Trade + Zip Code → Contractor

**For MVP:**
- Admin backend may need local copy of contractor configuration to drive scheduling calendar
- Configuration includes: lead time (e.g., "3-5 days"), scheduling buffer

**Session 3 will define:** Detailed contractor integration requirements

---

### 4. FSM (Field Service Management) Tool Integration

**Status:** Future - NOT for MVP

**Current State:**
- Duke exploring FSM tools (Service Power, Service Bench, others mentioned)
- No FSM tool today

**For MVP:**
- Admin manually updates service request status (assigned, en route, on-site, completed)
- Customer sees status in app based on manual admin updates

**Future State (Phase 2):**
- FSM tool provides real-time contractor GPS tracking
- Automated status updates (contractor en route, on-site, completed)
- "Pizza tracker" experience for customers

**Quote (Gandara, Sun, 1:23:28):**
> "From what we're seeing through the demos, I'll say it's really that FSM tool that enables that because the tool itself, you know, has a customer integration, customer experience and notifications back. But that tool itself is what the contractors use."

---

### 5. SSO (Single Sign-On) for Admin Portal

**Status:** TBD - Depends on Duke IT capabilities

**Options:**
- SSO with Duke corporate IT (SAML, Okta, Azure AD)
- Separate login (username/password)

**For MVP:** May start with separate login, migrate to SSO in Phase 2

---

### 6. Data Sync Strategy

**Master Sources of Truth:**

| Data Entity | Master Source | Synced To | Sync Method | Frequency |
|-------------|---------------|-----------|-------------|-----------|
| **Duke customer profile** | Commerce | App Backend | API (read) | Real-time or daily |
| **P&G customer profile** | Dynamics | App Backend | API (read) | Real-time or daily |
| **Non-native customer profile** | App Backend | None | N/A | N/A |
| **HPP plan enrollment (Duke)** | Commerce | App Backend | API (read) | Real-time |
| **HPP plan enrollment (P&G)** | Dynamics | App Backend | API (read) | Real-time |
| **Service requests (HPP)** | Dynamics | App Backend | API (create/read/update) | Real-time |
| **Service requests (ad-hoc)** | App Backend | Dynamics | API (create) or manual | Batch or manual |
| **Home inventory** | App Backend | None | N/A | N/A |
| **Ad-hoc service catalog** | App Backend | None | N/A | N/A |
| **Reminders** | App Backend | None | N/A | N/A |
| **Contractor configuration** | CRM/Dynamics | App Backend (copy) | Manual or API | Daily or on-demand |

**Key Principle:**
- For MVP, admin backend mirrors data from CRM systems (read-only sync)
- New data (inventory, ad-hoc services, reminders) lives primarily in app backend
- Over time, migrate more "source of truth" functions from CRM to app backend

**Quote (Gilstrap, Joshua, 1:44:32):**
> "We need mostly full visibility, but with the understanding that a lot of the stuff lives in CRM and that's the source of truth. Over time, in the future, we'd like to eventually kind of move the source of truth function for a lot of these things out of the CRM, but right now it's going to be in there."

---

