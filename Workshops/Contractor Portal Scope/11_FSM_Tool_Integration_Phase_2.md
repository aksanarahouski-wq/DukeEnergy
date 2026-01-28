# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 11. FSM TOOL INTEGRATION (PHASE 2)

### Current FSM Limitations

**Today's FSM**:
- Internal SAP-based system
- Limited functionality
- No mobile contractor app
- No GPS tracking
- No real-time status updates
- No integration with contractor dispatch software

**Quote from Kevin**: "I would say that don't consider [FSM] as part of phase one."

### FSM Tools Under Consideration

**Vendors Being Evaluated**:
1. **Service Power** - Field service management platform
2. **Service Bench** - Contractor network management
3. **NOT Service Channel** - Ruled out

**Quote from Session 1**: "Future FSM tools: Service Power, Service Bench under consideration."

**FSM Tool Capabilities Needed**:
- Contractor mobile app (iOS/Android)
- Real-time job assignment and acceptance
- GPS tracking of technician location
- Automated status updates (dispatched, en route, on-site, completed)
- Integration with contractor dispatch software (Service Titan, Housecall Pro, etc.)
- Customer notifications based on technician location
- Two-way messaging between customer and contractor
- Digital completion forms (photos, parts used, customer signature)
- Automated invoicing

### Phase 2 Architecture (With FSM Tool)

**Data Flow**:

Customer App ↔ Duke App Backend ↔ **FSM Tool** ↔ Contractor Mobile App
                                    ↕
                              Commerce CRM

**Workflow Changes**:

1. **Customer Books Service in App**
   - Service request sent to app backend
   - App backend sends to FSM tool via API

2. **FSM Tool Assigns to Contractor**
   - FSM tool queries contractor availability (real-time calendar)
   - FSM tool sends push notification to contractor mobile app
   - Contractor sees job details in mobile app

3. **Contractor Accepts in Mobile App**
   - One-tap acceptance
   - FSM tool notifies Duke app backend
   - Duke app updates customer: "Confirmed!"

4. **Day of Service**:
   - Contractor marks "Dispatched" in mobile app
   - Customer sees: "Your technician is on the way"
   - GPS tracking enabled (pizza tracker)
   - Customer sees: "Technician is 15 minutes away"

5. **At Customer Home**:
   - Contractor marks "On-Site" in mobile app
   - Timer starts (for performance tracking)
   - Customer sees: "Technician has arrived"

6. **Service Completion**:
   - Contractor completes digital form in mobile app
   - Takes photos of completed work
   - Captures customer signature
   - Submits completion
   - FSM tool syncs to Commerce CRM for invoicing
   - Customer app immediately shows "Completed"
   - Customer prompted to rate contractor in-app

**Quote from Kevin**: "If we can get an FSM software that's integrated into their Service Titan or whatever they're using from their dispatching side, that's better because it'll make sure that we're better aligned with our contractors through their journey."

### Pizza Tracker Feature (Phase 2)

**Customer View**:
- Map showing technician location (like Uber)
- Estimated arrival time
- "John from ABC Plumbing is 12 minutes away"
- Auto-updates as technician moves

**Requirements**:
- FSM tool with GPS tracking
- Contractor mobile app running in background
- Real-time location sharing enabled
- Privacy controls (location only shared when dispatched to job)

**Quote from Aksana**: "In ideal world, you want kind of both of these entities have their own rooms in your house, right? Contractors have an app, customer has an app, and the data just bounce back and forth."

**Quote from Kevin**: "The FSM software that we looked at was they had tracking like that, so if it was all that for some software is on the technicians app or on their phone then it would actually track where they are and if they say they're dispatching it only releases that location whenever there it's been identified that they're dispatching to that customer."
