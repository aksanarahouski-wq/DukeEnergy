# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---

## ADMIN WORKFLOWS

### Workflow 1: Manual Enrollment Processing (MVP Fallback)

**Trigger:** Customer submits HPP plan enrollment via app, but enrollment API doesn't exist yet.

**Steps:**
1. Customer completes enrollment flow in app
2. Enrollment request added to **Review Queue** in admin backend
3. Back office admin receives notification
4. Admin reviews enrollment details:
   - Customer info (name, address, email, phone)
   - Requested HPP plan(s)
   - Payment method (utility bill vs credit card)
5. Admin validates customer:
   - If Duke/P&G customer: Look up in CRM (Commerce/Dynamics) by account number, address, phone, or last name
   - If match found: Link app profile to existing customer record
   - If no match found: Admin manually creates business partner in CRM
6. Admin processes enrollment:
   - Creates enrollment in CRM (Commerce/Dynamics)
   - Enrollment syncs to billing system
   - App backend updated with enrollment confirmation
7. Customer receives confirmation notification
8. Admin marks queue item as "Processed"

**Timeline:** Within 24-48 hours of submission.

**Future State (Phase 2):** Direct API enrollment - no manual intervention.

---

### Workflow 2: Service Request Creation & Assignment

**Scenario A: Customer Books via App (HPP Covered Service)**

**Steps:**
1. Customer submits service request via app (e.g., "Water heater not working")
2. App validates HPP coverage (API call to Commerce/Dynamics)
3. Service request created in app backend
4. **For MVP:** App backend pushes service request to CRM (Commerce/Dynamics) via API or manual queue
5. CRM auto-assigns contractor based on trade + zip code
6. Admin can view service request in dashboard (status: "Assigned")
7. Admin monitors for exceptions (no contractor available, contractor declines, etc.)
8. If exception occurs, admin manually reassigns or contacts customer

**Scenario B: Customer Books via App (Ad-Hoc Service with Flat Rate Pricing)**

**Steps:**
1. Customer browses ad-hoc service catalog in app
2. Customer selects service (e.g., "HVAC Tune-Up - $99")
3. Customer selects date/time window based on contractor availability
4. Service request created in app backend
5. Service request pushed to CRM for contractor dispatch
6. Admin monitors service request dashboard
7. Admin can manually update status if FSM tool not integrated yet

**Scenario C: Customer Calls to Book Service (Phone Order)**

**Steps:**
1. Customer calls CSR
2. CSR looks up customer in app backend (to see inventory, HPP plans, loyalty rewards)
3. CSR creates service request manually in CRM (existing process)
4. CRM assigns contractor
5. Service request synced to app backend (so customer can track in app)

---

### Workflow 3: Ad-Hoc Service Catalog Creation

**Actor:** Product Manager

**Steps:**
1. Product manager logs into admin backend
2. Navigates to "Service Catalog Management"
3. Clicks "Create New Service"
4. Fills out service details:
   - Service name: "HVAC Tune-Up"
   - Category: HVAC
   - Description: "Annual HVAC maintenance to ensure optimal performance and efficiency"
   - Scope of work:
     - Replace air filter
     - Clean condenser coils
     - Check refrigerant levels
     - Inspect electrical connections
     - Test thermostat
     - Provide maintenance report
   - Exclusions: "Does not include repairs or replacement parts"
   - Customer must: "Provide clear access to HVAC unit"
5. Set pricing:
   - Pricing type: Fixed
   - Base price: $99
   - Regional overrides:
     - Orlando area: $99
     - Charlotte area: $109
     - Raleigh area: $105
6. Set geographic availability:
   - Available in: Orlando metro (zip codes: 32801-32899)
7. Associate contractors:
   - Select contractors who offer this service at negotiated rate
8. Set status: Active
9. Save service
10. Service now appears in customer app for booking

**Quote (Gandara, Sun, 55:35):**
> "What you will show on the front end to the customer could be whatever the ad hoc services are, when it maps back to our enterprise, you'll pass all the description or whatever that is, but from a back end, it will need to map to this ECN product."

---

### Workflow 4: Reminder Management

**Actor:** Product Manager / Content Manager

**Steps:**
1. Admin navigates to "Reminders Management"
2. Clicks "Create New Reminder"
3. Fills out reminder details:
   - Title: "Change HVAC Filter"
   - Description: "Replace your HVAC filter every 3 months to maintain air quality and system efficiency"
   - Frequency: Every 3 months
   - Asset category: HVAC
   - Seasonal trigger: None (year-round)
   - Optional service link: "Order filter replacement service ($29)"
4. Save reminder
5. Reminder automatically added to all customers with HVAC inventory
6. Customers receive notification based on frequency
7. Customers can adjust frequency or disable reminder

---

### Workflow 5: Customer Profile Management (Support Call)

**Actor:** CSR (Shop/Support)

**Scenario:** Customer calls saying they can't log into the app.

**Steps:**
1. Customer calls support: "I can't log into my account"
2. CSR asks for email or phone number
3. CSR searches for customer in admin backend
4. CSR views customer profile:
   - App account status: Active
   - Last login: 3 days ago
   - Email: verified
   - Phone: verified
5. CSR identifies issue: Customer forgot password
6. CSR sends password reset email to customer
7. Customer receives email, resets password
8. CSR confirms customer can log in
9. CSR updates ticket status: Resolved

**Alternative Scenario:** Customer account locked after multiple failed login attempts.

**Steps:**
1. CSR searches for customer
2. CSR sees account status: Locked
3. CSR unlocks account
4. CSR sends notification to customer
5. Customer can log in

---

### Workflow 6: Inventory Management (Contractor Update)

**Scenario:** Contractor completes service visit and updates inventory.

**Steps:**
1. Contractor visits customer home for water heater service
2. Contractor identifies water heater make/model/serial number
3. Contractor submits service completion report via contractor portal (or calls back to dispatch)
4. Service notes include: "Customer has Rheem tankless water heater, Model XYZ, Serial 123456, installed 2021"
5. **Admin action:** Back office admin reviews service completion notes
6. Admin navigates to customer profile in admin backend
7. Admin adds inventory item:
   - Item type: Water Heater
   - Category: Tankless
   - Make: Rheem
   - Model: XYZ
   - Serial: 123456
   - Installation date: 2021
   - Location: Garage
8. Save inventory
9. Customer now sees water heater in their app inventory
10. Customer receives reminder: "Annual tankless water heater flush recommended"

---

### Workflow 7: Analytics Review (Weekly Business Review)

**Actor:** Executive Team, Operations Manager

**Steps:**
1. Operations manager logs into admin backend
2. Navigates to "Executive Dashboard"
3. Reviews key metrics:
   - **This Week:**
     - New registrations: 1,250 (up 15% from last week)
     - Active users: 8,400 (70% engagement rate)
     - Service requests: 620 (480 HPP covered, 140 ad-hoc)
     - Ad-hoc revenue: $12,800
     - Call center volume: Down 32% (on track for 40% target)
     - Customer satisfaction: 4.6/5 stars average
4. Manager identifies issue: Ad-hoc service requests lower than expected
5. Manager drills into "Ad-Hoc Services" dashboard:
   - Most booked: HVAC Tune-Up (82 bookings)
   - Least booked: Toilet Install (3 bookings)
6. Manager hypothesis: Toilet install pricing too high or scope unclear
7. Manager tasks product manager: Review toilet install service, adjust pricing or scope
8. Manager exports report to share with executive team
9. Executive team reviews in weekly meeting, adjusts strategy

---

