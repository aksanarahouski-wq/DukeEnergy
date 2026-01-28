# HPP (Home Protection Plans) - Complete Reference

**Date Created:** November 6, 2025
**Purpose:** Comprehensive explanation of Duke Energy Home Protection Plans - how they work, pricing, coverage, and options

---

## What Are HPP (Home Protection Plans)?

**Home Protection Plans (HPPs)** are **monthly subscription-based service contracts** offered by Duke Energy Residential Solutions that cover repairs and replacements for home systems and appliances.

**Key Characteristics:**
- **Monthly fee-based:** Customers pay a flat monthly fee (typically **$9.99 per month**)
- **Billed on utility bill:** Native Duke/P&G customers have HPP fees added to their electric/gas utility bill
- **Service contracts:** Cover **repairs and replacements** (NOT maintenance)
- **Problem-based:** Customers only call when something breaks or malfunctions
- **No deductible/service call fee:** Monthly fee covers unlimited service calls

**From Meeting1:29 (Sun Gandara):**
> "Right now, if I were to say product offering, I'm talking about the home protection plans. **Those are $9.99 per month, goes on your bill, and you have up to so much coverage for your whatever you're covering, whether it's your HVAC, hot water heater, plumbing, etc.** So that's the current product offerings. And we have many, many plans."

---

## How HPP Plans Work

### **For Customers WITH HPP Plans:**

**From Meeting1:25 (Kevin Oppermann):**
> "So whether you're on our plan great if you're on our plan **we're going to go out there and do it for free basically because you're already paying a monthly subscription fee with us** you just go ahead and book it we'll go out there and do it."

**Current Process (Phone-Based):**
1. Customer's appliance/system breaks (e.g., water heater stops working)
2. Customer calls Duke Energy service number
3. Call center representative (CSR):
   - Verifies customer has HPP plan covering that item
   - Determines if issue is covered under plan rules
   - Creates service request in system (Dynamics)
   - Assigns contractor based on zip code
4. Contractor receives job assignment
5. Contractor visits home, repairs or replaces system
6. **Customer pays $0** (covered under monthly subscription fee)
7. After service, customer receives satisfaction survey (email-based)

**Future Process (App-Based - MVP Goal):**
1. Customer opens app
2. App shows customer's active HPP plans
3. Customer selects problem (e.g., "Water heater not working")
4. App checks coverage eligibility automatically (if rules systematized)
5. App matches and assigns contractor based on algorithm
6. Customer sees contractor info, ETA, real-time status updates
7. Service completed, customer rates contractor in app
8. **Customer still pays $0** (covered under subscription)

---

## Current Customer Base

### **Total Customers:**
- **800K+ current customers** with active HPP plans
- **1.5 million total agreements** (customers can have multiple plans)

**From Meeting1:25 (Kevin Oppermann):**
> "We don't have a digital experience for the customers to be able to do that today right so we won't be able to provide them that digital experience for our **1.5 million agreements** that we have."

**From CLAUDE.md:**
> "Duke Energy's home protection plan services, **serving 800K+ current customers** with plans to expand to non-native customers."

### **Customer Distribution:**
- Native Duke customers (electric) with HPP plans
- Native P&G customers (gas) with HPP plans
- **Goal:** Expand to non-native customers (not Duke/P&G utility customers)

---

## HPP Plan Options

### **Most Popular Plans:**

**From Meeting1:189 (Kevin Oppermann):**
> "They're calling about **water heater and home wiring. Those are the primary two.** They're the ones with the most amount of agreements as well. So we have **over 300,000 plans on each of those**."

### **Complete List of HPP Plan Categories:**

| HPP Plan Type | What It Covers | Customer Base | Notes |
|---------------|----------------|---------------|-------|
| **Water Heater Repair** | Water heater repairs/replacements | **300K+ plans** | #1 most popular - high call volume |
| **Home Wiring / Electrical** | Electrical issues, outlets, breakers | **300K+ plans** | #2 most popular - random issues (outlets not working, breakers tripping) |
| **HVAC (Heating & Cooling)** | Central AC, heat pumps, furnaces | High incident rate | High usage, growing plan base |
| **Plumbing** | Plumbing systems and fixtures | Growing | Part of core offerings |
| **Appliance Repair** | Major home appliances | High incident rate | Growing segment |
| **Utility Line Protection** | Service lines from street to home | Offered | Covers lines Duke doesn't maintain |

**From CLAUDE.md:**
> "Duke Energy Residential Solutions administers home protection plans (HPPs) covering **utility lines, electrical, heating & cooling, and appliances**"

**From Data Entities document:**
> "List of active HPP plans (water heater, HVAC, electrical, plumbing, appliance)"

---

## HPP Plan Pricing

### **Standard Pricing:**
- **$9.99 per month** per plan
- Billed on utility bill (for native Duke/P&G customers)
- Customer can have **multiple plans** (e.g., water heater + HVAC + plumbing)

**From Meeting1:29 (Sun Gandara):**
> "Those are **$9.99 per month, goes on your bill**, and you have up to so much coverage for your whatever you're covering, whether it's your HVAC, hot water heater, plumbing, etc."

### **Coverage Limits:**
- **"Up to so much coverage"** - Coverage limits exist per plan (exact amounts TBD during workshops)
- Covers **repairs and replacements** within coverage limits
- Some exclusions apply (coverage rules need to be documented)

### **What's Included:**
- ✅ Unlimited service calls (no per-visit fee)
- ✅ Labor costs
- ✅ Parts costs (within coverage limits)
- ✅ Repair or replacement (if repair not feasible)
- ❌ Preventative maintenance (NOT covered - repairs only)
- ❌ Pre-existing conditions or issues outside plan scope

---

## How Customers Enroll in HPP Plans

### **Current Enrollment Methods:**
1. **Phone enrollment:** Call Duke Energy customer service
2. **Online enrollment:** Limited digital capabilities (Duke website)
3. **Call center channels:** Various acquisition channels

**From Meeting1:23 (Sun Gandara):**
> "The enrollment process or the acquisition process of the customer, there is a digital portion as well as an acquisition through our call center channels and various other channels. So for now, **the scope of this app will not include at MVP the acquisition** [enrollment], but that is fast follow."

### **MVP Scope:**
- **NOT in MVP:** Enrolling NEW customers in HPP plans via app (Phase 2 feature)
- **IN MVP:** Managing EXISTING HPP plans (view plans, book services, track status)

### **Future State (Phase 2):**
- Customers can enroll in HPP plans directly in app
- Non-native customers can sign up (with credit card/ACH payment via SpeedPay)
- Upgrade/downgrade plans
- Add additional properties

---

## HPP Coverage Determination - THE BLOCKER

### **Current State:**

**Critical Gap:** How coverage eligibility is determined is **UNDEFINED and not systematized**.

**From Meetings Analysis:**
> "**HPP Coverage Rules** - ❌ Not discussed - Where are coverage rules stored? - How is HPP eligibility determined? - **CRITICAL gap**"

### **Questions That MUST Be Answered in Workshops:**

1. **Where are HPP coverage rules stored?**
   - In Commerce/Dynamics database (structured data)?
   - In documentation (Word docs, PDFs)?
   - In CSR knowledge (tribal knowledge)?

2. **How is coverage determined today?**
   - CSR manually checks plan details and makes decision?
   - Automated system checks eligibility?
   - Manager approval required for edge cases?

3. **Can coverage rules be exposed via API?**
   - Can app check eligibility in real-time?
   - Or must customer self-determine based on plan info?
   - Or submit request → CSR approves on backend?

4. **What are the coverage rules?**
   - Age of appliance/system (e.g., must be <15 years old)?
   - Specific failure types covered vs not covered?
   - Coverage limits per year (e.g., max $2000 per claim)?
   - Exclusions (e.g., cosmetic damage, negligence)?

5. **Who decides edge cases?**
   - CSR has authority?
   - Manager approval?
   - Customer can appeal?

### **Why This Is a Blocker:**

**From Workshop Plan:**
> "**HPP coverage rules** - Can't build eligibility checking without rules - Core feature not functional"

**Without systematized coverage rules, the app cannot:**
- Auto-determine if customer's issue is covered
- Show customers what's covered under their plans
- Route service requests correctly (HPP-covered vs ad-hoc)
- Prevent customers from booking services not covered under plan

### **Options for MVP:**

**Option A: Real-time API Coverage Check**
- Requires coverage rules in system (Commerce/Dynamics)
- App calls API: "Customer X, Plan Y, Issue Z - covered?"
- API returns: Yes/No + coverage amount
- **Ideal but requires Duke IT to build API**

**Option B: Customer Self-Determines**
- App displays plan coverage details
- Customer reads and decides if issue is covered
- Customer proceeds with booking
- Risk: Customer misunderstands, books service not covered
- **Simpler but less user-friendly**

**Option C: Submit Request → CSR Approves**
- Customer submits service request via app
- CSR reviews and approves/denies coverage
- Customer gets notification
- **Works but defeats purpose of self-service**

**DECISION NEEDED in Session 1:** Which approach based on coverage rules availability?

---

## HPP Plans vs Ad-Hoc Services

### **Two Customer Service Models:**

| Aspect | **HPP Plans** | **Ad-Hoc Services** |
|--------|--------------|-------------------|
| **Customer Type** | Native Duke/P&G customers with active plans | Non-native customers OR native customers without plan |
| **Pricing Model** | $9.99/month subscription (billed on utility bill) | Pay-per-service (quote or fixed price) |
| **Service Trigger** | Problem/repair needed | Maintenance, repair, or installation needed |
| **Customer Pays** | $0 at time of service (covered by subscription) | Pay upfront or after service |
| **Payment Method** | Utility bill | Credit card, ACH, cash/check (contractor collects Phase 1) |
| **Coverage Limits** | Yes (per plan rules) | No limits (customer pays full amount) |
| **Scope** | Repairs & replacements only | Any service (maintenance, repair, replacement, tune-up) |
| **MVP Status** | ✅ Core MVP feature | ✅ Core MVP feature (expand customer base) |

**From Meeting1:29 (Sun Gandara):**
> "What we also want to do is offer those **ad hoc services**, maybe subscription services, as it pertains to these types of things around your home. **HVAC, I want to get my HVAC tuned before the summer peak season for $99.99. Or I need to get my hot water flushed. Or I just need a plumber**, right? And maybe there is a price range, or we do have a set price or at an hourly rate or something to that effect. **We don't offer those right now**, but we have a contractor network that can support all those services."

### **Ad-Hoc Service Examples (NEW - Not HPP Plans):**
- HVAC tune-up before summer ($99.99)
- Water heater flush ($XX)
- General plumber service (hourly rate or fixed price)
- Appliance installation
- Preventative maintenance
- Emergency repairs (for non-plan customers)

**Ad-Hoc Pricing Status:** **STILL IN DEVELOPMENT** (from Meeting1:45:58)

---

## What Customers Can Do With HPP Plans

### **Current Capabilities (Phone-Based):**
- ✅ Call to report problem
- ✅ Schedule service appointment
- ✅ Receive contractor assignment
- ✅ Receive email confirmation/reminders
- ✅ Provide feedback after service (NPS/CSAT survey)
- ❌ NO self-service digital experience
- ❌ NO real-time status updates
- ❌ NO contractor visibility
- ❌ NO service history access
- ❌ NO ability to reschedule/cancel online

### **MVP App Capabilities (Goal):**
- ✅ View active HPP plans
- ✅ Book service for covered issue
- ✅ Check coverage eligibility (if rules accessible)
- ✅ See contractor info, photo, ratings
- ✅ Real-time status updates (assigned, en route, on-site, completed)
- ✅ In-app messaging with contractor (if MVP feature)
- ✅ View service history
- ✅ Rate and review contractor
- ✅ Reschedule or cancel appointment
- ✅ Track contractor GPS location (like Uber) - if MVP
- ❌ Enroll in NEW HPP plans (Phase 2)
- ❌ Upgrade/downgrade plans (Phase 2)

---

## Data Storage: Where HPP Plan Information Lives Today

### **Current Systems:**

| Data Entity | Duke Customers | P&G Customers | Integration |
|-------------|----------------|---------------|-------------|
| **Customer Profile** | SAP Commerce | Dynamics | App must sync from BOTH |
| **HPP Plan Enrollment** | Commerce | Dynamics | App must sync from BOTH |
| **HPP Plan Catalog** | Commerce | Dynamics | App must sync from BOTH |
| **Service Requests** | Dynamics | Dynamics | Primary system |
| **Coverage Rules** | ❓ Unknown | ❓ Unknown | **BLOCKER** |

**From Data Entities document:**
> "**HPP plans exist** in Commerce (Duke) and Dynamics (P&G)"

**From Meeting1:19 (Dana DeRemigis):**
> "We do have our own commerce SAP that handles and houses our customers that are on HPPs. So if they're already on a home protection plan with us, we do have a place for them. **Right now it's two places because we have some in a P&G world and some in the Duke world.**"

### **Integration Requirements:**

**Duke IT MUST Provide:**
- Commerce API to retrieve Duke customer HPP plans
- Dynamics API to retrieve P&G customer HPP plans
- Coverage validation API (if rules are systematized)
- Service request creation API

**App Database Will Store:**
- Cached copy of customer HPP plans (synced from Commerce/Dynamics)
- Service request status (synced with Dynamics)
- Customer preferences (notifications, favorites)

---

## Business Goals for HPP Plans

### **Customer Experience Goals:**

**From CLAUDE.md - Customer Experience Goals:**
- **Reduce service request time** from 15 minutes (phone) to <3 minutes (app)
- **90% customer satisfaction** with contractor communication
- Enable contractor availability and job status **dashboard visibility**
- Provide **real-time updates** and communication throughout service lifecycle

### **Operational Efficiency Goals:**

**From CLAUDE.md - Operational Efficiency Goals:**
- **Reduce call center volume by 40%**
- Automate scheduling to **reduce coordination calls by 80%**
- Improve data collection through app-based home inventory (**80% inventory completion**)

### **Adoption Goals:**

**From Executive Summary Proposal:**
> "**30–40% of Home Protection Plan (HPP) customers using mobile/web within first 12 months**"

That means:
- Year 1 target: 240K-320K of 800K customers using app (30-40%)
- Reduce phone call volume significantly
- Increase customer engagement and satisfaction

### **Retention Goals:**

**From Executive Summary Proposal:**
> "**15–20% increase in HPP renewal/retention rates**"

Why retention matters:
- Monthly recurring revenue model
- Customer lifetime value increases with retention
- App provides better experience → customers less likely to cancel plans

---

## HPP Plans vs Warranty vs Insurance

### **What HPP Plans Are NOT:**

| NOT This | Actually This |
|----------|--------------|
| ❌ **Manufacturer warranty** | ✅ **Service contract / Home warranty** |
| ❌ **Homeowners insurance** | ✅ **Subscription-based repair coverage** |
| ❌ **Preventative maintenance plan** | ✅ **Repair & replacement plan** |
| ❌ **One-time warranty purchase** | ✅ **Monthly subscription ($9.99/month)** |
| ❌ **Covers accidental damage** | ✅ **Covers normal wear & tear failures** |

### **Similar Products in Market:**
- American Home Shield (home warranties)
- Choice Home Warranty
- First American Home Warranty
- Select Home Warranty

**Duke Energy's Differentiator:**
- Leverages existing customer relationship (utility customers)
- Billed on utility bill (no separate payment)
- Managed contractor network (trusted, vetted contractors)
- Goal: "Uber of home services" experience

---

## Open Questions for Workshops

### **Session 1 - Customer Discovery:**

**HPP Plan Questions:**
- [ ] What percentage of customers have HPP plans?
- [ ] What percentage have MULTIPLE HPP plans?
- [ ] What's the average number of plans per customer?
- [ ] Can customers enroll in HPP plans via app in MVP? Or just manage existing?
- [ ] Can customers upgrade/downgrade plans in MVP?
- [ ] Can customers cancel plans via app? (self-service or require call?)
- [ ] Do customers understand what their plans cover? (education opportunity)

**Coverage Rules Questions (CRITICAL):**
- [ ] Where are HPP coverage rules stored? (Commerce, documentation, CSR knowledge?)
- [ ] Can we see coverage rules documentation?
- [ ] Can coverage rules be exposed via API for real-time eligibility check?
- [ ] How often do coverage rules change?
- [ ] Who decides edge cases or exceptions?
- [ ] Is coverage decision logged? (who decided, reason, timestamp)

**Multi-Property Questions:**
- [ ] Do customers have different HPP plans for different properties?
- [ ] If customer has vacation home, can they have separate plans?

---

### **Session 2 - Admin Discovery:**

**HPP Plan Catalog Management:**
- [ ] Who creates/manages HPP plan catalog? (product team, marketing?)
- [ ] How often do plan details change? (rarely, quarterly, annually?)
- [ ] Do admins need to create new plans in app? Or plans managed in Commerce/Dynamics?
- [ ] Can admins enroll customers in plans manually?
- [ ] What reports do admins run on plan enrollment? (adoption rates, revenue, etc.)

---

### **Session 4 - Integration & Architecture:**

**HPP Plan Data Sync:**
- [ ] Where is HPP plan data stored? (Commerce, Dynamics, both?)
- [ ] Can we retrieve plan catalog via API?
- [ ] Can we check if customer is enrolled in specific plan via API? (critical for coverage check)
- [ ] Read-only or can app create new enrollments?
- [ ] Real-time sync or batch acceptable? (plans don't change often)

---

## Key Personas Using HPP Plans

### **"Established Eleanor"** - Existing HPP Customer

**From CLAUDE.md:**
> "**'Established Eleanor'** - 58, existing Duke customer with HPP, frustrated with phone-only service"

**Profile:**
- Age: 58
- Customer Type: Native Duke customer
- HPP Plans: Has water heater + HVAC plan
- Tech Savvy: Moderate
- Pain Points:
  - Can only call during business hours
  - No visibility into contractor arrival time
  - Can't track service status
  - Doesn't know which contractor is coming
- Goals:
  - Book service at midnight when water heater breaks
  - See real-time status updates
  - Rate contractor experience
  - Access service history

### **"Expanding Emma"** - New Duke Customer

**From CLAUDE.md:**
> "**'Expanding Emma'** - 34, first-time homeowner, new Duke customer, wants proactive home management"

**Profile:**
- Age: 34
- Customer Type: Native Duke customer (new)
- HPP Plans: Considering enrolling
- Tech Savvy: High
- Pain Points:
  - Doesn't know what HPP plans are
  - Unsure if she needs them
  - Wants proactive home management tools
- Goals:
  - Learn about HPP plan options
  - Enroll in plans via app (Phase 2)
  - Track home inventory
  - Preventative maintenance reminders

### **"Non-Native Nathan"** - Not a Utility Customer

**From CLAUDE.md:**
> "**'Non-Native Nathan'** - 41, not a Duke utility customer, seeks reliable home services platform"

**Profile:**
- Age: 41
- Customer Type: Non-native (not Duke/P&G utility customer)
- HPP Plans: Not eligible (but will be in future)
- Tech Savvy: High
- Pain Points:
  - Can't enroll in HPP plans (not utility customer)
  - Wants reliable contractors
  - Needs transparent pricing
- Goals:
  - Book ad-hoc services (HVAC tune-up, plumber, etc.)
  - Pay via credit card
  - Rate contractors
  - Eventually enroll in HPP plans if Duke opens to non-native

---

## Bottom Line: HPP Plans Summary

**What:** Monthly subscription service contracts ($9.99/month) covering home system repairs and replacements

**Who:** 800K+ native Duke/P&G utility customers with 1.5M total active plan agreements

**Top Plans:** Water heater (300K+), home wiring (300K+), HVAC, plumbing, appliance

**Current Experience:** Phone-only, no digital self-service, no real-time updates

**MVP Goal:** Enable app-based service booking, contractor visibility, real-time tracking for existing HPP customers

**Critical Blocker:** HPP coverage rules not systematized or accessible via API - MUST be resolved in Session 1

**Future State:** Expand to non-native customers (not utility customers), ad-hoc service marketplace, proactive home management platform

**The Vision:** "Uber of home services" - transparent, self-service, real-time, contractor-rated platform

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 6, 2025
**Status:** Reference document for workshop facilitation

---

**Related Documents:**
- [Duke Energy Discovery Workshop Plan](Duke_Energy_Discovery_Workshop_Plan.md)
- [Session 1: Customer Discovery](Session_1_Customer_Discovery.md)
- [P&G Customer References](P&G_Customer_References.md)
- [Data Entities & Workflows Analysis](Data_Entities_and_Workflows_Analysis.md)
- [Meeting 1 Transcript](../Meetings/Meeting1.md)
