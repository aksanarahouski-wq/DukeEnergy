# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---


## EXECUTIVE SUMMARY

**Session Focus:** Backend administration and operations - the people and systems that make the customer app experience work.

**Key Insight:** The admin portal serves as the "middle layer" aggregating data from multiple sources (Commerce CRM for Duke customers, Dynamics for P&G customers, app database for non-native customers and new data) into a unified administrative interface.

### Major Decisions Made:

1. **Build a dedicated admin backend** separate from existing CRM systems to support cross-system data aggregation
2. **Manual fallback processes for MVP** - When APIs don't exist, admin queues handle enrollment, service requests manually
3. **Multi-level admin access** - Different permission levels for CSR, back office, escalation team, analytics users
4. **Ad-hoc service catalog** - New product catalog management needed (doesn't exist today)
5. **Reminders over DIY content** - Focus on automated maintenance reminders rather than building static DIY content library
6. **Full instrumentation required** - Analytics and reporting critical from day 1 for business case validation
7. **Manual service request processing for MVP** (Session 3) - Admin manually contacts contractors (email/phone) within 1 hour of customer booking, updates app status based on contractor responses (within 24 hours)
8. **No contractor portal rebuild for MVP** (Session 3) - Contractors continue using existing Commerce CRM portal. Admin backend manages contractor configuration (trade, zip codes, availability). FSM integration and contractor mobile app deferred to Phase 2.
9. **Contractor configuration management in admin backend** (Session 3) - Admin backend houses contractor data (125-140 contractors, 80% primary/20% backup), manages matching algorithm configuration (trade + zip code + availability buffers)

---
