# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 4. CONTRACTOR DATA & CONFIGURATION

### Contractor Data Model

**Core Contractor Fields** (Needed in App Backend):

| Field | Description | Example | Maintained By |
|-------|-------------|---------|---------------|
| Contractor ID | Unique identifier | CNTR-12345 | CRM |
| Contractor Name | Business name | ABC Plumbing & HVAC | CRM |
| Contact Info | Phone, email | (704) 555-1234 | CRM |
| Trade(s) | Services offered | Plumbing, HVAC, Electrical | Admin Backend |
| Service Areas | Zip codes served | 28201, 28202, 28203... | Admin Backend |
| Primary/Secondary | Per trade + zip | Primary HVAC in 28201, Secondary Plumbing | Admin Backend |
| Lead Time/Buffer | Days advance notice | HVAC: 2 days, Electrical: 6 days | Admin Backend |
| Availability Windows | Time slots | Mon-Fri 8-12, 1-5; Sat 9-1 | Admin Backend |
| Work Days | Days available | Plumbing: Tue/Thu only, HVAC: Mon-Fri | Admin Backend |
| Licensing | License numbers, expiration | NC-12345 exp 12/31/2025 | CRM |
| Insurance | Certificate, expiration | $2M liability, exp 6/30/2026 | CRM |
| Background Checks | Technician verification | All techs checked annually | CRM |
| Pricing | Negotiated rates per service | Water heater replace: $850 | CRM (not in app MVP) |

**Quote from Kevin**: "I would like to know exactly how much that contractor charges for each type of activity they would do for us and have that in a systematic database... That right now is not loaded. We do collect some of that information in our contract negotiations up front."

### Multi-Trade Contractor Configuration

**Challenge**: Contractor offers multiple trades with different availability per trade

**Example**: ABC Home Services
- **Trade 1: HVAC**
  - Primary contractor for zip codes: 28201, 28202, 28203
  - Lead time: 2 business days
  - Availability: Monday-Friday, 8am-5pm
  - Time windows: 8-12, 1-5
- **Trade 2: Plumbing**
  - Primary contractor for zip codes: 28201, 28202
  - Secondary contractor for zip codes: 28203, 28204
  - Lead time: 3 business days
  - Availability: Tuesday-Thursday only
  - Time windows: 9-12, 1-4
- **Trade 3: Electrical**
  - Secondary contractor for zip codes: 28201, 28202
  - Lead time: 6 business days
  - Availability: Monday, Wednesday, Friday only
  - Time windows: 8-12 only

**Data Model Requirement**: Separate configuration per contractor + trade combination

**Quote from Ed Carr**: "Many of those contractors handle those businesses as separate businesses. So it'd be almost like three separate businesses."

### Contractor Availability - How It Works

**Current State** (No Systematic Tracking):
- Contractors do not provide real-time availability calendar
- Duke does not have visibility into contractor's full schedule (they schedule non-Duke work too)
- Lead time/buffer is used as availability proxy (e.g., "HVAC contractor available starting 2 days from now")

**MVP Approach** (Static Availability Rules):

**Option 1: Static Buffer** (RECOMMENDED FOR MVP)
- Contractor provides: "Always available starting X days from request"
- System calculates: Today + buffer = first available date
- Shows customer: Windows starting on first available date
- **Pros**: Simple, no contractor input needed, 90%+ acceptance rate
- **Cons**: Not true real-time availability, may offer slots contractor can't fulfill

**Example**: HVAC contractor has 2-day buffer
- Customer requests service Monday 2pm
- System offers: Wednesday 8-12, Wednesday 1-5, Thursday 8-12, Thursday 1-5...
- Customer selects: Thursday 8-12
- Admin sends to contractor, contractor accepts/proposes alternative

**Option 2: Calendar-Based** (FUTURE - PHASE 2)
- Contractor provides: Available/blocked dates in calendar
- System checks: Contractor schedule before showing customer
- Requires: FSM tool with contractor mobile app
- **Pros**: True real-time availability
- **Cons**: Requires contractor to maintain calendar, high burden

**Quote from Kevin**: "We won't have their schedule. So we won't have the contractor scheduling because they can schedule for other work outside of our work with those technicians... We won't have that at all, even in an FSM scenario."

**90-95% Acceptance Target**:
- Goal: 90-95% of time slots offered to customers are accepted by contractors
- Achieved through: Conservative buffers (3-5 day minimums), contractor SLA contracts
- When contractor declines: Admin manually reschedules

### Contractor Data Sync Strategy

**Phase 1 MVP** (Manual Data Export/Import):

**Initial Setup**:
1. Duke exports contractor data from Commerce CRM
2. File includes: Contractor list, trade assignments, zip code assignments, primary/secondary designations
3. Orases imports into app backend database
4. Admin team configures additional fields (lead time, availability windows)

**Ongoing Maintenance**:
1. Contractor changes (new contractor, territory change, etc.) happen in CRM first
2. Admin team manually updates app backend to match
3. Frequency: As-needed (contractor changes are rare, ~1-2 per year)

**Quote from Kevin**: "We would have to do that today mainly anyway. And we do it today. We have to override the zip code eligibility, et cetera. Not frequently, it just happens that we have contractor that goes out, especially in the mom and pop areas that we have to get backup."

**Phase 2** (API Integration):
- Real-time API to read contractor data from CRM
- Nightly sync to keep app backend updated
- Potential FSM tool integration for availability
