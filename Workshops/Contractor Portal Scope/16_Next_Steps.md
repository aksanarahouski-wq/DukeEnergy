# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 16. NEXT STEPS

### Immediate Actions (Post-Session 3)

**Duke Team**:
1. **Clarify P&G vs. Duke Contractor Model**: Are P&G employees in MVP scope? Different workflows needed?
2. **Provide Contractor Data Exports**: Contractor list, trade assignments, zip code assignments
3. **Define Contractor Availability Rules**: Confirm lead time buffers, work days, time windows per contractor
4. **Assess Service Request API Feasibility**: Can Duke IT build API for Phase 1 or manual process acceptable?
5. **Define Ad-Hoc Commission Model**: Percentage, collection method, contractor payment terms

**Orases Team**:
1. **Finalize Contractor Matching Algorithm Spec**: Document complete matching logic with edge cases
2. **Design Admin Backend Contractor Configuration**: Wireframes for admin managing contractors
3. **Design Service Request Workflow**: Admin processing service requests, updating statuses
4. **Prototype Contractor-Related Customer Flows**: Booking with contractor assignment, rescheduling

### Phase 1 Contractor Portal Deliverables

**Admin Backend Features**:
- Contractor CRUD (Create, Read, Update, Delete)
- Trade assignment (multi-select)
- Zip code assignment (list entry)
- Primary/secondary designation per trade + zip
- Lead time/buffer configuration per trade
- Availability windows configuration (time slots, days of week)
- Service request queue management
- Status update interface (confirm, reschedule, complete)
- Exception handling (reassign contractor, extend time window)

**Customer App Features**:
- View assigned contractor details (name, contact, photo?)
- See confirmed appointment date/time/contractor
- Reschedule/cancel service request (within policy)
- View service history (contractor name, date, outcome)
- Contact contractor (phone/SMS link)

**No Contractor Portal Changes**:
- Contractors continue using existing Commerce portal
- No contractor mobile app for Phase 1
- No contractor-facing features in app MVP
