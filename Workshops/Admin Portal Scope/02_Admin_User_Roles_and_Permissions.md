# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---


## ADMIN USER ROLES & PERMISSIONS

### Role Matrix

| Role | Primary Function | Key Responsibilities | System Access |
|------|------------------|---------------------|---------------|
| **CSR (Enrollment Center)** | Customer acquisition | Handle enrollment inquiries, manually create accounts/business partners, process failed enrollments from review queue | CRM (Commerce), App Backend (view-only for loyalty/rewards) |
| **CSR (Shop/Support)** | Technical support | App account administration (password resets, unlock accounts), troubleshoot app issues | App Backend (full CRUD for customer profiles) |
| **Back Office Admin** | Operations & data management | Process enrollment queues, manage customer profiles, update inventory, configure services & pricing | App Backend (full CRUD), CRM (read/write) |
| **Product Manager** | Catalog management | Create/edit ad-hoc service catalog, set pricing, define service scope of work, manage reminders | App Backend (service catalog, pricing, reminders) |
| **Operations Manager** | Service oversight & contractor coordination | **MVP CRITICAL**: Manually process service requests (contact contractors within 1 hour, update app status based on responses), reassign contractors, handle exceptions, manage contractor availability overrides | App Backend (service request queue, contractor config, full CRUD), CRM (contractor assignments) |
| **Escalation Team** | Conflict resolution | Handle customer complaints, contractor disputes, service quality issues | CRM (full context), App Backend (create escalation tickets) |
| **Analyst/Reporting User** | Business intelligence | Access dashboards, export reports, track KPIs | App Backend (read-only analytics) |

### Permission Levels

**View Only:**
- Customer profile (basic info)
- Service request status
- Analytics dashboards

**Edit/Create:**
- Customer inventory (back office, support CSR)
- Service catalog & pricing (product managers)
- Reminders & content (product managers)
- Contractor configuration (operations)

**Admin/Super User:**
- User management
- System configuration
- Full CRUD across all entities

---

