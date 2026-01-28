# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 5. PHASE 1 CONTRACTOR PORTAL SCOPE

### The Big Decision: What to Build for Contractors in MVP?

**Options Evaluated**:

| Option | Description | Pros | Cons | Timeline | Cost | DECISION |
|--------|-------------|------|------|----------|------|----------|
| **Option A: Minimal Enhancements** | Keep existing portal, add integration hooks for app | Contractors keep familiar system, focus on customer app | Contractors don't see improvements, manual admin work | 44 weeks | Lowest | Possible |
| **Option B: New Mobile App** | Build contractor iOS/Android app with real-time updates | Modern UX, mobile-first, pizza tracker | Requires FSM tool, significant dev time, contractor adoption risk | 60+ weeks | Highest | **NO** - Phase 2 |
| **Option C: Hybrid** | Enhance portal + lightweight mobile for status updates | Contractors have options | Maintain two systems, still complex | 52 weeks | Medium-High | **NO** - Too complex |
| **Option D: Admin-Only** | No contractor changes, all managed via admin backend | Maximum customer app focus, learn from MVP first | Contractors use same old system, admin workload higher | 44 weeks | Lowest | **YES** ✅ |

**✅ DECISION: Option D - Admin-Only for Phase 1 MVP**

**Rationale**:
1. **Focus 100% on Customer App**: Customer app drives revenue ($25M ad-hoc services target)
2. **Contractor Portal is Functional**: Existing Commerce portal works, contractors are familiar
3. **Learn from MVP First**: Understand customer needs before investing in contractor features
4. **FSM Tool Dependency**: Robust contractor mobile app requires FSM integration (not ready for Phase 1)
5. **Manual Admin Updates Acceptable**: Back office can update statuses based on contractor communication for MVP
6. **Phase 2 Investment**: Build modern contractor mobile app after FSM tool selected and customer app proven

**Quote from Kevin**: "Consider that that's a gap right now for phase one. We need to fill... I would say that don't consider [FSM] as part of phase one."

**Quote from Son**: "For MVP, though, we're matching the same way, right? We're matching to a primary, no matter what service that is, and that's who they get."

### What Contractors Continue Using (No Changes)

**Existing Contractor Portal** (Direct Access to Commerce CRM):
- Receive job assignments
- View service request details (customer name, address, problem description)
- Schedule appointments with customers
- Update service request status (accepted, scheduled, dispatched, in-progress, completed, invoiced)
- Enter completion details (services performed, parts used, time spent)
- Submit invoices

**Communication Methods**:
- Email notification when new job assigned
- Phone calls to/from Duke back office
- Direct phone/SMS with customers (contractors have customer phone numbers)

**Their Own Systems**:
- Contractors use their own dispatch software (Service Titan, Housecall Pro, etc.)
- Contractors manage technician schedules internally
- Contractors send their own lifecycle communications (~70% provide en-route notifications, etc.)

**Quote from Kevin**: "The contractor is going through that entire lifecycle on their side, with some people with most of it being done by their admin, their back office is moving it through those respective stages."

### What Admin Backend Manages (New for App)

**Contractor Configuration** (Admin Portal Features):
- CRUD operations for contractors (Create, Read, Update, Delete)
- Assign trades to contractors (multi-select: HVAC, Plumbing, Electrical, etc.)
- Assign service areas (zip code list per contractor)
- Set primary/secondary designation per trade + zip code
- Configure lead time/buffer per contractor per trade
- Configure availability windows (time slots, days of week)
- View contractor performance metrics (once collected)
- Override assignments for exceptions (emergencies, capacity issues)

**Service Request Status Management** (Admin Portal):
- View pending service requests from customer app
- Manually send service request to contractor (email/phone for MVP)
- Update status when contractor confirms: "Confirmed - [Contractor Name] - [Date/Time]"
- Update status when contractor completes: "Completed - [Date]"
- Handle reschedules/cancellations (update app, notify customer)

**Quote from Kevin**: "The latter with the caveat, though... we will default based off our default logic. So we have a primary contractor that we will send out."
