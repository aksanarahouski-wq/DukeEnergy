# Session 1: Customer Discovery

**Focus:** Validate customer types, understand service request workflows, and define MVP scope for customer-facing features.

---

## Critical Questions to Answer

### **1. Customer Segments & Prioritization**

**Goal:** Understand who we're building for and prioritize MVP focus.

**Questions:**
- What percentage of your customer base is:
  - Native Duke/P&G customers with HPP plans?
  - Native customers without HPP plans?
  - Non-native customers (future market)?
- **What percentage of customers are Duke vs P&G?**
- What percentage have multiple properties?
- Do the three personas (Eleanor, Emma, Nathan) reflect your actual customers?
- **DECISION:** Who should we design for FIRST in MVP? (Native HPP customers, non-native, or both equally?)

**HPP Plan Understanding:**
- What percentage of customers have HPP plans? (vs no plan)
- **What percentage have MULTIPLE HPP plans?** (e.g., water heater + HVAC + plumbing)
- What's the average number of plans per customer?
- Can customers enroll in NEW HPP plans via app in MVP? Or just manage existing?
- Can customers upgrade/downgrade plans in MVP?
- Can customers cancel plans via app? (self-service or require call?)
- **Do customers understand what their plans cover?** (education opportunity)

**Duke vs P&G Customer Questions:**
- Do P&G customers have same HPP plan options as Duke customers?
- Can a customer be both Duke (electric) AND P&G (gas)? How is that handled?
- Are there geographic boundaries between Duke and P&G territories?

**Why This Matters:** Affects UI/UX design priorities, authentication approach, feature prioritization, and determines if Duke/P&G customers need different experiences.

---

### **2. Service Request Workflow - HPP Covered Services**

**Goal:** Understand current process to design app flow and identify integration points.

**Walk Through Real Example:** Native customer requests water heater service (HPP covered)

**Questions:**
- How does customer initiate request today? (call center process)
- How is HPP eligibility determined? (automated, manual, hybrid?)
- How is contractor assigned? (automatic dispatch by zip code mentioned - how does it really work?)
- What happens if no contractor available?
- What communication does customer receive throughout service?
- How long does the typical service request take from call to completion?

**Service Request Data Questions:**
- Where is service request data stored TODAY? (Dynamics primary? Commerce also?)
- Can we see a service request record in Dynamics? (screen share to understand fields)
- What statuses exist? (Requested, Assigned, En Route, On-Site, Completed, Cancelled - exact list?)
- Who can change status? (CSR, contractor, automated system?)
- Can customers reschedule or cancel requests today? How?
- How long is service history kept? (can you pull 5 years back?)
- Is customer rating/review collected today? Where stored?

**Why This Matters:** Defines core app functionality, Dynamics integration requirements, and data model design.

---

### **3. HPP Coverage Rules - THE BLOCKER**

**Goal:** Understand how coverage is determined so app can check eligibility.

**CRITICAL Questions:**
- Where are HPP coverage rules stored? (Commerce system, documentation, CSR knowledge?)
- Can we see coverage rules documentation? (structured data or Word docs/PDFs?)
- Can these rules be exposed via API for real-time eligibility check?
- Who decides edge cases or exceptions?
- How often do coverage rules change?

**Coverage Decision Tracking:**
- When service request is determined "covered" or "not covered," is that decision logged?
- Who made the decision? What was the reason?
- Can decision be appealed or overridden? Is override logged?

**Why This Matters:** **Without systematized coverage rules, app cannot function.** This is a potential project blocker if rules are not accessible via API or structured data.

**DECISION NEEDED:**
- Option A: Real-time API coverage check (requires rules in system)
- Option B: Customer self-determines based on plan info
- Option C: Submit request, CSR approves on backend

---

### **4. Service Request Workflow - Ad-Hoc Services (Non-Native)**

**Goal:** Understand how non-native customers will use platform for paid services.

**Questions:**
- Do you serve non-native customers today in any capacity?
- How should ad-hoc service booking work? (browse catalog → see price → book → pay?)
- **From Meeting1:** "Contractor collects payment on-site" for Phase 1 - confirm this approach?
- When does customer pay? (before service, after service, on-site?)
- What payment methods should be supported? (credit card, ACH, digital wallets?)

**Why This Matters:** Defines SpeedPay integration scope and payment processing requirements.

---

### **5. Home Inventory - MVP Scope Decision**

**Goal:** Decide if home inventory is mandatory, optional, or deferred to Phase 2.

**Questions:**
- What problem does home inventory solve for Duke? For customers?
- What's the incentive for customers to enter inventory?
- **DECISION:** Mandatory during onboarding, optional but incentivized, or deferred to Phase 2?
- If MVP: What's the minimum data needed? (just appliance type, or full details?)
- Should we support barcode scanning? Photo upload?

**Home Inventory Data Requirements:**
- **Minimum viable fields:**
  - Item type (HVAC, water heater, electrical, plumbing, appliance - dropdown?)
  - Specific category (e.g., central AC, heat pump, furnace, tankless water heater?)
  - Location in home (basement, garage, kitchen - dropdown or free-text?)
- **Optional but valuable:**
  - Make/manufacturer, model number, serial number
  - Purchase/installation date
  - Warranty expiration date
  - Photos
- **Who can create/edit inventory?**
  - Customer: Create/edit own items
  - Admin: Create/edit on behalf (support use case)
  - Contractor: View during service? Add/update after service?

**Why This Matters:** Affects onboarding flow complexity, development timeline, and data model design. Home inventory does NOT exist in Duke systems today - need to build from scratch.

**Options:**
- **Mandatory:** Better data, but may cause customer drop-off during onboarding
- **Optional:** Less friction, but lower data collection rate
- **Progressive:** Prompt to add during service request (contextual)
- **Deferred:** Phase 2 feature

---

### **6. DIY Content Strategy**

**Goal:** Understand content creation plan and volume needed at launch.

**Questions:**
- Why DIY content? (reduce call volume, customer education, marketing?)
- What problems are customers trying to solve before calling?
- **CRITICAL:** Who will create DIY content? (Duke team, Orases, contractors, third-party?)
- How much content needed at launch? (10 articles? 50? 100?)
- Does any content exist today that can be migrated?
- What's the content approval process? (legal review, SME review?)

**Why This Matters:** Affects project timeline if content creation is on critical path. May need to adjust launch expectations if content not ready.

---

### **7. MVP Feature Prioritization**

**Goal:** Finalize what's IN vs Phase 2.

**DECISIONS NEEDED:**

| Feature | MVP or Phase 2? | Impact if Included |
|---------|----------------|-------------------|
| Multi-property management | ? | Adds UI complexity |
| Warranty tracking | ? | Adds data model complexity |
| Spanish localization | ? | Doubles content + UI work |
| Contractor ratings/reviews | ? | Standard for MVP |
| In-app messaging (customer ↔ contractor) | ? | Additional dev work |
| Real-time contractor GPS tracking | ? | Like Uber - complex |

**Questions:**
- If <10% of customers have multiple properties, defer to Phase 2?
- What % of customers are Spanish-speaking? Is localization critical for launch?
- Which features are "must-have" vs "nice-to-have"?

**Why This Matters:** Directly affects budget and timeline. Each deferred feature reduces MVP scope.

---

### **8. Data & System Integration Questions**

**Goal:** Understand where customer data lives and how app will integrate.

**Current State:**
- Where is customer data stored TODAY? (Commerce for Duke, Dynamics for P&G?)
- What customer data exists? (customer ID, name, contact, HPP plans, service history, billing?)
- Can we see sample fields or export? (understand data structure)
- **CRITICAL:** What % of customers have multiple properties?
- How are multiple properties tracked today? (separate accounts, linked accounts, not tracked?)

**Customer Identity & Authentication:**
- How do you verify customer identity when they call? (account number + name? address?)
- For app authentication:
  - Native customers: Login with account number? Email? Create username/password?
  - Non-native customers: Email + password? Social login?

**Data Sync & Master Source:**
- Can app access customer data via API? (name, address, HPP plans, service history?)
- Real-time API calls or batch sync?
- What's the master source of truth? (if customer data in both Commerce AND app, which wins?)
- If customer updates email in app, should it update Commerce?

**Data Access Permissions:**
- What customer data can customers edit? (email, phone, preferences? or all read-only?)
- Can contractors see customer contact info? (privacy concern - should it be masked?)

**Why This Matters:** Defines integration architecture, Duke IT involvement, and affects multi-property feature scope decision.

---

## Expected Outputs

By end of Session 1, we'll have:

✅ **Validated customer personas** with actual percentages
✅ **Service request workflows documented** (HPP vs ad-hoc) at high level
✅ **HPP coverage rules approach decided** (blocker resolved or escalated)
✅ **MVP feature scope finalized** (what's IN vs Phase 2)
✅ **Home inventory decision made** (mandatory, optional, or deferred)
✅ **DIY content strategy outlined** (who creates, how much, when)
✅ **Customer app wireframe sketches** (10-15 screens) based on decisions

---

## Key Risks to Surface

**Flag these if they emerge:**

🔴 **HIGH RISK:**
- HPP coverage rules not systematized or accessible via API
- Content creation ownership unclear or not resourced
- Duke IT not available for API discussions

🟡 **MEDIUM RISK:**
- Multi-property customers >10% but MVP doesn't support
- Spanish-speaking customers significant but no localization plan
- Payment processing timeline uncertain (SpeedPay setup)

---

## Pre-Session Preparation Needed

**Duke Team Should Prepare:**
- Customer data analysis (percentages by segment)
- 2-3 real service request examples (anonymized)
- HPP coverage rules documentation (if exists)
- Top 5-10 reasons customers call today

**Orases Team Will Prepare:**
- Rough wireframe concepts for discussion
- Question framework and facilitation plan
- CMS comparison (custom vs third-party) for Session 2 preview

---

**Session Facilitator:** Aksana (Orases Product Manager)
**Session Designer:** Devin (Orases Product Designer & Business Analyst)
