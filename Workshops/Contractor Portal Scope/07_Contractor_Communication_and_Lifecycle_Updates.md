# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 7. CONTRACTOR COMMUNICATION & LIFECYCLE UPDATES

### Current Contractor Communication

**Today's Process**:
- **Assignment**: Email notification to contractor when job assigned
- **Scheduling**: Contractor calls customer within 48 hours to schedule
- **Confirmation**: Contractor confirms time in Commerce portal (hit or miss)
- **Day-Before**: ~70% of contractors send reminder text/call to customer
- **En Route**: ~70% of contractors send "on my way" text to customer
- **Completion**: Contractor updates Commerce portal when job completed
- **Survey**: Duke sends customer survey after completion (external process)

**Quote from Kevin**: "Once we've created that order, we handed off that customer communication to the contractor to do up until the point that they've completed it... Now we have some of that transparency in the database as long as they're updating it, but the consistency of whether they update it is a challenge."

### MVP Communication Strategy

**Communication Touchpoints Provided by App/Admin**:

1. **Booking Confirmation** (Customer App → Customer)
   - "We received your service request"
   - Pending confirmation from contractor

2. **Contractor Assignment** (Customer App → Customer)
   - "Your contractor has been assigned: ABC Plumbing"
   - Contact info provided

3. **Appointment Confirmation** (Admin → Customer App → Customer)
   - "Your appointment is confirmed: Thursday 9-12am with ABC Plumbing"
   - SMS + push notification + email (per customer preference)

4. **Day-Before Reminder** (App → Customer) - OPTIONAL FOR MVP
   - "Reminder: ABC Plumbing coming tomorrow 9-12am"
   - May conflict with contractor's own reminders

5. **Reschedule Notification** (Admin → Customer App → Customer)
   - "Your appointment time has changed"
   - New date/time displayed

6. **Completion Notification** (Admin → Customer App → Customer)
   - "Your service has been completed"
   - Survey link (existing external process continues)

**Communication Provided by Contractor** (No Change):
- Day-before reminder call/text
- "On my way" text
- "Running 15 minutes late" text
- Post-service follow-up

**Quote from Kevin**: "Most of our contractors already have in their system a process doing that. So they already are sending notifications that are coming out there, text notification, all that stuff."

### Challenge: Data Sync Between Contractor & App

**Problem**: Contractor may reschedule with customer without updating Duke systems

**Example**:
- App shows: "Thursday 9-12am appointment confirmed"
- Contractor calls customer Tuesday: "Can we move to Friday 1-4pm instead?"
- Customer agrees
- Contractor updates their own system (Service Titan, etc.)
- Contractor does NOT immediately update Duke Commerce portal
- App still shows Thursday 9-12am (out of sync)

**MVP Solution**:
- Accept that data may be temporarily out of sync
- Contractor updates Commerce when completing job (source of truth)
- For MVP, don't send automated reminders that could conflict
- Admin manually updates app if they're informed of changes

**Phase 2 Solution** (FSM Tool):
- FSM tool integrated with contractor's dispatch software
- Real-time sync between contractor system ↔ FSM tool ↔ Duke app
- Automated status updates
- GPS tracking

**Quote from Chris Murphy**: "One of the challenges would be if a contractor changes an appointment with the customer for some reason and doesn't go into our system and change it immediately and the customer starts getting notifications that, hey, we're coming in 24 hours when the contractor has made other arrangements with the customer."

### In-App Messaging (NOT in MVP)

**Future Consideration** (Phase 2):
- Customer ↔ Contractor in-app chat (like Uber)
- Keeps communication within app
- Privacy protection (no phone numbers exposed)
- Message history tracked

**MVP**: Continue using phone/SMS for direct communication

**Quote from Aksana**: "MVP: Phone/SMS communication continues (no in-app messaging Phase 1)"
