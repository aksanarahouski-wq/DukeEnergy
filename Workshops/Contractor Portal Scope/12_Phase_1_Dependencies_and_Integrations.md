# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 12. PHASE 1 DEPENDENCIES & INTEGRATIONS

### Critical Data Exports from Duke (Required for MVP)

**1. Contractor Master List**
- **Format**: CSV or JSON export
- **Frequency**: One-time initial load, then as-needed updates (rare)
- **Data Fields**:
  - Contractor ID
  - Contractor Name
  - Business Name
  - Contact Phone
  - Contact Email
  - Primary Contact Name
  - Status (Active/Inactive)

**2. Contractor Trade Assignments**
- **Format**: CSV or JSON
- **Frequency**: One-time initial, then manual updates
- **Data Fields**:
  - Contractor ID
  - Trade (HVAC, Plumbing, Electrical, Water Heater, Appliance)
  - Certification/License Numbers

**3. Contractor Zip Code Assignments**
- **Format**: CSV or JSON export (example provided in meeting)
- **Frequency**: One-time initial, then as-needed updates
- **Data Fields**:
  - Zip Code
  - Trade
  - Primary Contractor ID
  - Backup Contractor ID(s)

**Example from Ed Carr** (shown in meeting chat):
```
Zip Code: 28210
Trade: HomeWire
Primary: CNTR-001 (ABC Electric)
Backup: CNTR-045 (XYZ Electric)

Zip Code: 28210
Trade: HVAC
Primary: CNTR-012 (Cool Air Services)
Backup: CNTR-033 (Best HVAC)
```

**Quote from Ed Carr**: "What I put in the chat is actually an example of what the file is. And so you can see that's basically a zip code where I live. These are all those are the programs that are available. And then those are the contractors, including their IDs, including their backup contractors."

**4. Service Eligibility by Zip Code**
- **Format**: CSV or JSON
- **Data Fields**:
  - Zip Code
  - Plan Type (HomeWire, HVAC, Plumbing, Water Heater, Appliance)
  - Eligible (Yes/No)

**Purpose**: Show customer which plans available in their area

**Quote from Kevin**: "So we will give you the eligibility criteria. So then that way, you know, hey, for the zip code, these plans are available."

### Manual Admin Processes (MVP Acceptable)

**Service Request Handoff** (App → Contractor):
- **Current**: Admin manually emails/calls contractor with new service request
- **Data Required**: Service request details from app admin dashboard
- **Timeline**: Admin processes within 1 hour of customer booking
- **Acceptable for MVP**: Yes, 125 contractors with SLAs can handle this

**Status Updates** (Contractor → App):
- **Current**: Admin manually updates app when contractor confirms/completes
- **Data Source**: Contractor phone/email communication + Commerce portal updates
- **Frequency**: 2-3 updates per service request (confirmed, completed)
- **Acceptable for MVP**: Yes, manageable volume for back office team

**Quote from Kevin**: "For phase one, when we get the API built, it will supply that history of that contractor, that service order history back. It just probably wouldn't be an MVP."

### Phase 1 API Integrations (If Available - Not Required for MVP)

**Service Request Creation API** (App → Commerce CRM):
- **Endpoint**: POST /service-requests
- **Payload**: Customer ID, Service Type, Zip Code, Problem Description, Requested Time
- **Response**: Service Request ID, Assigned Contractor ID
- **Benefit**: Eliminates manual admin entry into CRM

**Service History API** (Commerce CRM → App):
- **Endpoint**: GET /customers/{id}/service-history
- **Response**: List of past service requests with dates, contractors, outcomes
- **Benefit**: Show customer complete service history in app
- **Not MVP**: Nice to have, not required for launch

**Quote from Kevin**: "So we will have all the service history for whether they called in or did the app. That will be part of the API as part of phase one. Not the MVP, but as part of phase one, that will be returned."
