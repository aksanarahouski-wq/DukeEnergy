# P&G Customer References - Duke Energy Residential Solutions

**Date Created:** November 6, 2025
**Purpose:** Comprehensive reference for P&G (Piedmont Natural Gas) customer distinctions, system differences, and workshop implications

---

## What is P&G?

**Piedmont Natural Gas (P&G)** - A Duke Energy acquisition that serves gas customers. P&G is now part of the Duke Energy parent company.

**Key Quote from Meeting1:15:35:**
> "Duke Energy is our parent company and they serve electric and gas customers under Piedmont. So PNG, you'll see those letters, that acronym as well."

---

## P&G Customer Base

### **Two Separate Native Customer Groups:**

1. **Duke customers** - Electric customers
2. **P&G customers** - Gas (Piedmont) customers

**From Meeting1:15:50 (Dana DeRemigis):**
> "We do have our own commerce SAP that handles and houses our customers that are on HPPs. So if they're already on a home protection plan with us, we do have a place for them. **Right now it's two places because we have some in a P&G world and some in the Duke world.**"

---

## System Differences: Duke vs P&G

### **Customer Data Storage:**

| Customer Type | System | Notes |
|---------------|--------|-------|
| **Duke customers** | SAP Commerce platform | Electric customers |
| **P&G customers** | Dynamics system | Gas customers |

**From Session 1 (line 174):**
> "Where is customer data stored TODAY? (Commerce for Duke, Dynamics for P&G?)"

**From Data Entities document (line 59):**
> "Native customers: Data exists in Commerce (Duke) or Dynamics (P&G)"

---

### **Contractor Differences - CRITICAL DISTINCTION:**

| Contractor Type | Duke | P&G |
|-----------------|------|-----|
| **Employment Model** | Third-party contractors (~150) | Internal employees |
| **Management** | Duke manages third-party network | P&G employees (on payroll) |
| **System** | Contractor portal | Different system? |

**From Meeting1:23 (Sun Gandara):**
> "We manage our contractor network. So **within Duke, it's third-party, but we manage them. Within P&G, those contractors are internal.**"

**From Data Entities document (lines 328, 360):**
> - Contractor type: Duke-managed contractor vs **P&G internal contractor (employee)**
> - **P&G contractors are internal employees** (different system?)

**Why This Matters:**
- Payment model differs (invoice third-party vs payroll internal employees)
- Availability tracking may differ (contractor schedules vs employee shifts)
- Performance management differs (ratings/contracts vs employee reviews)
- Job acceptance/decline process may differ

---

## Integration Implications

### **Service Territories:**

Contractors may serve:
- Duke territory only
- P&G territory only
- Both Duke and P&G territories

**From Data Entities document (line 315):**
> "Service area type (Duke territory, P&G territory, both)"

---

### **Billing Integration:**

| Customer Type | Billing Method | Integration |
|---------------|----------------|-------------|
| **Duke native customers** | Utility bill (electric) | SAP Commerce |
| **P&G native customers** | Utility bill (gas) | Dynamics |
| **Non-native customers** | Credit card/ACH | SpeedPay |

**From Meeting1:24:36:**
> "So I'm a due customer, I can sign up for this plan that 999 gets billed along with my regulated utility bill. So, if you are living in an area within where we have contractor network, **but you're not a Duke or P&G customer**, you should be able to sign up for these plans or these services without us having to charge it on your utility bill."

---

## Geographic Context

**From Meeting1:26:41:**
> "We are within jurisdictions where we operate along about **seven, eight states**. So that's where our contractor network is."

Both Duke and P&G operate across approximately 7-8 states in the Southeast/Mid-Atlantic region.

---

## Workshop Implications by Session

### **Session 1: Customer Discovery**

**Must Understand:**
- What percentage of customers are Duke vs P&G?
- Do P&G customers have same HPP plan options as Duke customers?
- Are there differences in coverage rules between Duke and P&G plans?

**Authentication Approach:**
- Duke customers: Authenticate via Commerce API
- P&G customers: Authenticate via Dynamics API
- Does authentication flow differ or unified experience?

**Data Sync Strategy:**
- Must account for two different source systems (Commerce + Dynamics)
- Real-time sync or batch from both systems?
- If conflicts, which system is master source?

---

### **Session 2: Admin Discovery**

**Admin Access:**
- Can admins view/edit both Duke AND P&G customer data?
- Single admin portal or separate systems?
- Different permissions for Duke vs P&G customers?

**Product Catalog:**
- Same ad-hoc service catalog for Duke and P&G territories?
- Different pricing by territory?

**Content Management:**
- Same DIY content for both customer bases?
- Territory-specific content needed?

---

### **Session 3: Contractor Discovery - MOST CRITICAL**

**CRITICAL Questions for Duke/P&G Contractor Differences:**

1. **Since P&G contractors are internal employees, how does job assignment work differently?**
   - Do internal employees use the same contractor portal as Duke third-party contractors?
   - Or completely different system?

2. **Payment/Invoicing Differences:**
   - Duke contractors: Invoiced per job? Commission-based?
   - P&G employees: Salaried? Hourly? Tracked differently?
   - How does app handle these two different payment models?

3. **Availability Tracking:**
   - Duke contractors: Block out vacation, max jobs per day
   - P&G employees: Employee shift schedules? PTO system?
   - Can app access P&G employee scheduling system?

4. **Performance Management:**
   - Duke contractors: Customer ratings, acceptance rate, on-time %
   - P&G employees: Employee performance reviews (separate HR system?)
   - Should both show same performance metrics to customers?

5. **Can P&G internal contractors serve Duke customers and vice versa?**
   - Cross-territory assignments allowed?
   - Does matching algorithm consider this?

6. **Contractor Matching Algorithm:**
   - Does algorithm treat Duke third-party and P&G internal employees differently?
   - Priority rules: Duke contractor for Duke customer, P&G employee for P&G customer?
   - Or agnostic - just based on geography/specialization?

7. **Phase 1 Contractor Portal Scope:**
   - If building new contractor portal, must it support BOTH third-party contractors AND internal employees?
   - Different UX for each? (e.g., employees might need timesheet integration, PTO requests)
   - Or unified portal with different features enabled per contractor type?

---

### **Session 4: Integration Architecture & APIs - CRITICAL**

**Duke IT MUST Answer:**

**1. API Integration - Two Separate Paths:**
- **Commerce API (Duke customers):**
  - Customer authentication
  - HPP plan validation
  - Service request creation
  - Does this API exist TODAY or needs to be built?

- **Dynamics API (P&G customers):**
  - Customer authentication
  - HPP plan validation
  - Service request creation
  - Does this API exist TODAY or needs to be built?

**2. API Parity:**
- Do both Commerce and Dynamics have same API capabilities?
- Or is one more mature than the other?
- If P&G/Dynamics APIs are less developed, does that delay P&G customer support?

**3. Contractor System Integration:**
- Where is Duke contractor data stored? (Contractor Portal? Dynamics?)
- Where is P&G employee data stored? (HR system? Dynamics?)
- Can app access both via same API or different APIs?
- How does job assignment reach Duke contractors vs P&G employees?

**4. Service Request Flow:**
- When Duke customer books service, created in Commerce or Dynamics?
- When P&G customer books service, created in Commerce or Dynamics?
- Unified backend or separate flows?

**5. Data Sync Master Sources:**

| Data Entity | Duke Master Source | P&G Master Source | App Strategy |
|-------------|-------------------|-------------------|--------------|
| Customer profile | Commerce | Dynamics | Sync from both? |
| HPP plans | Commerce | Dynamics | Sync from both? |
| Service requests | Commerce/Dynamics | Dynamics | Unified in app DB? |
| Contractor/Employee data | Contractor Portal | HR system/Dynamics | Sync from both? |

---

## Key Questions for Workshops

### **High-Priority Questions to Add/Emphasize:**

**Customer Understanding:**
- [ ] What percentage of customers are Duke vs P&G?
- [ ] Do P&G customers have same HPP plan options as Duke customers?
- [ ] Are there geographic boundaries between Duke and P&G territories?
- [ ] Can a customer be both Duke (electric) AND P&G (gas)? How is that handled?

**Contractor/Employee Model:**
- [ ] How many Duke third-party contractors vs P&G internal employees?
- [ ] Do P&G employees use same contractor portal as Duke contractors?
- [ ] Can P&G employees serve Duke customers and vice versa?
- [ ] How does payment work for P&G employees? (salaried, hourly, per-job?)
- [ ] How is P&G employee availability tracked? (shift schedules, PTO system?)
- [ ] Do P&G employees want/need mobile app or web portal sufficient?

**System Integration:**
- [ ] Are Commerce (Duke) and Dynamics (P&G) APIs at same maturity level?
- [ ] Timeline for building APIs: Same for both systems or different?
- [ ] Can Duke IT provide sandbox access for BOTH Commerce and Dynamics?
- [ ] Who are Duke IT contacts for Commerce vs Dynamics integrations?

**Service Catalog & Pricing:**
- [ ] Same ad-hoc service catalog for Duke and P&G territories?
- [ ] Different pricing by Duke vs P&G territory?
- [ ] Do Duke and P&G contractors offer same services?

**Content & Communications:**
- [ ] Same DIY content library for Duke and P&G customers?
- [ ] Territory-specific content needed?
- [ ] Branded as "Duke Residential Solutions" for both? Or separate P&G branding?

---

## Risks & Considerations

### 🔴 **HIGH RISK:**

1. **Two Separate Systems = Double Integration Complexity**
   - Commerce (Duke) + Dynamics (P&G) APIs both need to exist and be stable
   - If one system's APIs not ready, delays HALF the customer base

2. **P&G Internal Employees vs Duke Third-Party Contractors**
   - Completely different employment models may require different features
   - Phase 1 contractor portal must support both or pick one?
   - If Phase 1 only supports Duke contractors, P&G employees have NO digital experience

3. **Data Sync Conflicts**
   - If Duke customer data in Commerce conflicts with P&G customer data in Dynamics, how resolved?
   - Master source of truth must be clearly defined

### 🟡 **MEDIUM RISK:**

4. **Cross-Territory Service**
   - If Duke contractor can serve P&G customer, which system records service request?
   - Payment routing: Who pays whom? (Duke pays contractor? P&G pays contractor? Unified?)

5. **API Availability Timeline**
   - If Commerce APIs ready but Dynamics APIs not ready, do we launch Duke-only then add P&G?
   - Or wait for both to be ready?

6. **P&G Employee Feature Needs**
   - Internal employees may need different features (timesheet integration, PTO requests, employee shift schedules)
   - Is this MVP or Phase 2?

---

## Decision Framework

### **Phased Approach Options:**

**Option A: Launch Both Duke & P&G Simultaneously (Ideal)**
- Requires both Commerce and Dynamics APIs ready
- Requires contractor portal to support both third-party and internal employees
- Higher complexity, longer timeline

**Option B: Launch Duke First, P&G Phase 2**
- Focus MVP on Duke customers (Commerce API) and Duke contractors
- Add P&G customers and employees in Phase 2 once Dynamics APIs ready
- Lower complexity, faster MVP, but delays value for P&G customers

**Option C: Launch Customer App for Both, Contractor Portal Duke-Only**
- Customer app supports both Duke and P&G customers (via Commerce + Dynamics APIs)
- Contractor portal Phase 1 only for Duke third-party contractors
- P&G employees keep existing system, integrate in Phase 2
- Balanced approach - delivers value to all customers, defers contractor employee complexity

**DECISION NEEDED in Session 4:** Which phased approach based on API availability and business priorities?

---

## Data Model Implications

### **Customer Entity Must Support:**
```
Customer {
  customer_id: UUID
  customer_type: ENUM ['duke_native', 'pg_native', 'non_native']
  utility_account_number: STRING (null if non-native)
  source_system: ENUM ['commerce', 'dynamics', 'app'] (where customer data came from)
  // ... other fields
}
```

### **Contractor/Employee Entity Must Support:**
```
Contractor {
  contractor_id: UUID
  contractor_type: ENUM ['duke_third_party', 'pg_internal_employee', 'non_native']
  employment_model: ENUM ['third_party', 'internal_employee']
  service_territories: ARRAY ['duke', 'pg', 'both']
  // ... different fields based on contractor_type
}
```

### **Service Request Entity Must Track:**
```
ServiceRequest {
  service_request_id: UUID
  customer_id: UUID -> Customer
  customer_type: ENUM ['duke_native', 'pg_native', 'non_native']
  contractor_id: UUID -> Contractor
  contractor_type: ENUM ['duke_third_party', 'pg_internal_employee']
  source_system: ENUM ['commerce', 'dynamics', 'app']
  synced_to_systems: ARRAY ['commerce', 'dynamics'] (where it's been synced)
  // ... other fields
}
```

---

## Bottom Line

**P&G represents a separate customer base with different systems (Commerce vs Dynamics) and different contractor models (third-party vs internal employees), but same business goals.**

**The app must support BOTH Duke and P&G customers seamlessly despite backend system differences.**

**Critical Discovery Needed:**
- API availability timeline for Commerce vs Dynamics
- Contractor portal requirements for internal employees vs third-party contractors
- Phased approach decision (launch both vs Duke-first)

---

**Document Owner:** Orases Product Management Team
**Last Updated:** November 6, 2025
**Status:** Reference document for workshop facilitation

---

**Related Documents:**
- [Duke Energy Discovery Workshop Plan](Duke_Energy_Discovery_Workshop_Plan.md)
- [Session 1: Customer Discovery](Session_1_Customer_Discovery.md)
- [Session 3: Contractor Discovery](Session_3_Contractor_Discovery.md)
- [Session 4: Integration Architecture & Wireframe Presentation](Session_4_Integration_Wireframes.md)
- [Data Entities & Workflows Analysis](Data_Entities_and_Workflows_Analysis.md)
- [Meeting 1 Transcript](../Meetings/Meeting1.md)
