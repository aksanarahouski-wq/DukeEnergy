# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 6. CONTRACTOR WORKFLOWS

### Workflow 1: HPP Covered Service Request (Warranty Work)

**Happy Path**:

1. **Customer Creates Service Request in App**
   - Describes problem (symptom-based, not technical diagnosis)
   - Confirms which appliance/system (adds to inventory if not already there)
   - Selects preferred date/time window from available options
   - Sees pre-assigned primary contractor: "ABC Plumbing will service your request"

2. **App Backend Matches Contractor**
   - Identifies trade (plumbing)
   - Customer zip code (28201)
   - Queries contractor table: primary contractor for plumbing + 28201
   - Returns: ABC Plumbing with availability windows (Tue/Thu 9-12, 1-4, 3-day buffer)
   - Customer selects: Thursday 9-12 (3 days from now)
   - Service request status: "Pending Confirmation"

3. **Admin Reviews Service Request**
   - Sees new request in admin dashboard
   - Reviews details: Customer info, problem, contractor, requested time
   - **MVP**: Admin manually communicates to contractor (email/phone)
   - "Hi ABC Plumbing, we have a service request for Thursday 9-12 at 123 Main St, customer Jane Doe, leaking faucet"

4. **Contractor Receives Assignment**
   - Checks schedule (in their own system)
   - Scenario A: Accepts Thursday 9-12 → Notifies Duke admin (email/portal update)
   - Scenario B: Proposes alternative → "Can't do Thursday 9-12, can do Friday 1-4"

5. **Admin Confirms with Contractor (Scenario A - Accept)**
   - Contractor accepts proposed time
   - Admin updates service request status in app: "Confirmed - ABC Plumbing - Thursday 9-12am"
   - App sends notification to customer: "Your service is confirmed! ABC Plumbing on Thursday 9-12am"

6. **Admin Negotiates Alternative (Scenario B - Counteroffer)**
   - Contractor proposes Friday 1-4
   - Admin evaluates:
     - Option 1: Accept alternative, update app, notify customer
     - Option 2: Call customer to confirm new time
     - Option 3: Try backup contractor for original time
   - **MVP**: Admin calls customer to confirm Friday 1-4
   - If customer accepts: Update app status: "Confirmed - ABC Plumbing - Friday 1-4pm"

7. **Contractor Calls Customer** (Current Process Continues)
   - Contractor directly calls customer to re-confirm appointment
   - Provides technician name, ETA, any prep instructions
   - Updates customer on any changes

8. **Service Day - Contractor Workflow** (No Change)
   - Contractor dispatches technician
   - Technician goes to customer home, performs service
   - Technician collects payment if over coverage limit (customer pays excess)
   - Contractor updates Commerce portal: "Completed - [date] - Services performed: [description]"

9. **Admin Updates App After Completion**
   - Admin sees contractor marked service as complete in Commerce
   - Admin updates app service request status: "Completed - [date]"
   - App displays in customer's service history
   - Duke sends customer survey via existing process (email)

**Timeline**:
- Customer books: Monday 2pm
- Admin processes: Monday 3pm (within 1 hour goal)
- Admin contacts contractor: Monday 3:15pm
- Contractor responds: Monday 5pm or Tuesday morning (within 24 hours)
- Admin confirms in app: Tuesday 10am
- Service window: Thursday 9-12am (3-day buffer from request)

**Quote from Kevin**: "For phase one, when we get the API built, it will supply that history of that contractor, that service order history back. It just probably wouldn't be an MVP. So we have to think about it maintaining."

### Workflow 2: Ad-Hoc Service Request (Cash-Pay Customer)

**Happy Path**:

1. **Customer Browses Ad-Hoc Service Catalog**
   - Non-native customer (or Duke customer wanting non-covered service)
   - Browses services: "HVAC Tune-Up - $99", "Ceiling Fan Installation - $120-190"
   - Selects: "HVAC Tune-Up - $99"
   - Enters zip code: 28201

2. **App Matches Contractors (Same Logic)**
   - System identifies: Primary HVAC contractor for 28201 = XYZ HVAC
   - Shows availability: "First available: Wednesday, 3-day lead time"
   - Customer selects: Wednesday 1-5pm window
   - Payment note: "Payment collected by contractor on-site (cash, check, credit card)"

3. **Admin Processing** (Same as Workflow 1)
   - Admin reviews ad-hoc service request
   - Contacts XYZ HVAC contractor: "Ad-hoc service, $99 HVAC tune-up, customer pays you directly"
   - Contractor accepts Wednesday 1-5pm
   - Admin updates app: "Confirmed - XYZ HVAC - Wednesday 1-5pm"

4. **Payment at Completion**
   - Contractor performs service
   - **MVP**: Contractor collects $99 from customer (cash, check, or contractor's credit card reader)
   - Contractor reports payment to Duke (for commission tracking if applicable)

5. **Future State** (Phase 2 with Payment API):
   - Customer pre-pays $99 in app (credit card, Apple Pay)
   - Duke collects $99, pays contractor $75 (net of $24 commission)
   - Customer pays nothing on-site

**Quote from Kevin**: "Phase 1 - contractor collects payment on-site... The ad hoc services, where the customer is going to pay the contractor directly... if you want some X, Y, Z, because it's not going to be like what Chris was saying, where they're trying to get some exception made or they have a back-end deal with the contractor, it doesn't matter because they're a cash customer versus a warranty customer."

### Workflow 3: Emergency Service Request (NOT in App - Phone Only)

**Scenario**: Customer has no heat in winter, or smells gas, or has sparking outlet

**App Triage Flow**:

1. **Customer Starts Service Request**
   - Selects: "HVAC not working"
   - App asks qualifying questions:
     - "Is your home temperature below 60°F?"
     - "Is it currently below freezing outside?"
     - "Do you smell gas?"
     - "Is anything sparking or smoking?"

2. **Emergency Detected**
   - Based on answers, app determines: Emergency
   - App displays: "⚠️ This appears to be an emergency. Please call us immediately at 1-800-XXX-XXXX"
   - For gas leaks: "⚠️ SAFETY ALERT: If you smell gas, evacuate immediately and call your gas utility emergency line: 1-800-XXX-XXXX"
   - App does NOT create service request (routed to phone)

3. **CSR Handles Emergency**
   - Customer calls Duke emergency line
   - CSR collects details, determines urgency
   - CSR directly calls primary contractor: "Emergency - need immediate dispatch"
   - CSR negotiates soonest available time (2-4 hours for true emergencies)
   - CSR confirms with customer

4. **Optional: Admin Adds to App for Tracking**
   - After phone resolution, admin can manually create service record in app
   - Customer sees service history: "Emergency HVAC Repair - [Date] - XYZ HVAC"
   - Helps track all customer interactions in one place

**Quote from Kevin**: "We will have those emergency questions. It won't be a clear cut, hey, is this an emergency for a customer? It will be based off those criteria that they filled in. We'll determine this emergency and hey, call in, go down a flow."

**Quote from Dana**: "Most customers would say everything's an emergency, but there's a handful of things that we can definitely help with that should feed through the app, no problem. And then there's a smaller set of things that should be call us for the emergency."

### Workflow 4: Contractor Declines or Reschedules

**Scenario**: Primary contractor cannot fulfill requested time

**Path 1: Contractor Declines Before Confirmation**
1. Admin sends request to primary contractor
2. Primary contractor responds: "Cannot service Thursday 9-12, can do Friday 1-4"
3. Admin evaluates options:
   - **Option A**: Accept contractor's alternative time
   - **Option B**: Try backup contractor for original Thursday 9-12 time
4. **MVP Decision**: Prioritize keeping original time window if possible
5. If backup contractor available for Thursday 9-12:
   - Admin assigns to backup
   - Updates app: "Confirmed - Backup Plumbing LLC - Thursday 9-12"
   - Customer may not even know primary contractor wasn't available
6. If no one available for Thursday 9-12:
   - Admin calls/texts customer: "Original time not available, contractor can do Friday 1-4. Does this work?"
   - Customer accepts or requests different time
   - Admin updates app with final confirmed time

**Quote from Kevin**: "That's a fantastic question. I will say that we don't necessarily know by default what should happen next... Most likely the person in the back office that is maintaining that order that identifies, hey, the contractor rejected this time, should look to see and call the backup contractor and say, hey, can you service this time so we can try to keep that window as much as possible?"

**Path 2: Contractor Needs to Reschedule After Confirmation**
1. Service already confirmed: "Thursday 9-12am - ABC Plumbing"
2. Contractor has emergency (e.g., family issue, truck breakdown)
3. Contractor calls Duke admin: "Need to reschedule Thursday appointment"
4. Admin immediately notifies customer:
   - Push notification + SMS: "Your Thursday appointment needs to be rescheduled"
   - Admin calls customer to apologize and offer alternatives
5. Admin reassigns to backup contractor OR reschedules with same contractor
6. Admin updates app with new confirmed time
7. App shows updated appointment

**Frequency**: Rare (less than 5% of appointments)

**Quote from Ed Carr**: "The only time it happens is really when we have brush orders and the primary contractor is not available. I would say probably less than 5% of the time."

### Workflow 5: Customer Requests Different Contractor

**Scenario**: Customer doesn't want assigned contractor (past bad experience)

**MVP Approach**:

1. **Customer Sees Assignment**
   - App shows: "Your service will be provided by ABC Plumbing"
   - Small link: "Need a different contractor?"

2. **Customer Clicks Link**
   - App displays: "Please call us at 1-800-XXX-XXXX to request an alternative contractor"
   - Or: "Text REQUEST CHANGE to 12345 with your service request number"
   - **MVP does NOT show list of alternative contractors in app**

3. **Admin Handles Request**
   - Customer calls/texts
   - Admin asks reason (to track patterns)
   - Admin checks if backup contractor available
   - Admin confirms new contractor with customer
   - Admin updates app: "Confirmed - Backup Plumbing LLC - Thursday 9-12"

4. **Edge Case: Customer Keeps Requesting Different Contractors**
   - Admin notes account for potential "contractor shopping"
   - May require manager approval for multiple changes
   - Protects against customers gaming system to find contractor who will cover exclusions

**Quote from Chris Murphy**: "One of the challenges with that is customers become very strategic. So they get one contractor who knows their situation and knows that something's not covered because it's a code violation. Then they start going through the contractor list and saying, well, I want someone else out here... until they try to find the right one who will cover something that should not be covered."

**Future State** (Phase 2 with Ad-Hoc Marketplace):
- For cash-pay ad-hoc services, customer may see 2-3 contractor options
- Customer selects based on price, availability, ratings
- No "gaming" risk since customer pays directly
