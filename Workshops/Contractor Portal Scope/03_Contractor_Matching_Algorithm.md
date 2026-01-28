# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 3. CONTRACTOR MATCHING ALGORITHM

### Current State Algorithm

**Matching Logic** (Existing in SAP/Commerce CRM):
1. **Customer Service Request** created (trade + zip code)
2. **System Auto-Assigns** to primary contractor for that trade + zip code
3. **Contractor Receives Assignment** via portal/email
4. **Contractor Calls Customer** within 48 hours to schedule
5. **Contractor Updates CRM** with scheduled date/time

**Quote from Kevin**: "Right now what exists is trade and zip code. So you will know if I need plumbing and my zip code is 12345, it will be assigned to this person."

### Phase 1 MVP Matching Requirements

**Matching Factors** (Priority Order):

1. **Trade/Specialization Match** (Required)
   - HVAC
   - Plumbing
   - Electrical
   - Water Heater
   - Appliance Repair
   - Multi-trade contractors match multiple services

2. **Geographic Match - Zip Code** (Required)
   - One-to-one zip code assignment
   - Does NOT use radius or county
   - Contractors assigned specific zip code lists
   - Some contractors serve non-contiguous areas (Charlotte AND Raleigh but not in between)

3. **Primary/Secondary Designation** (Required)
   - Primary contractor offered first
   - Customer sees "This is your contractor" with pre-selected assignment
   - Option to request different contractor (handled via phone call for MVP)
   - If primary unavailable/declines, offer to secondary contractor

4. **Service Type** (HPP vs. Ad-Hoc)
   - **HPP Covered Services**: Duke assigns contractor, customer can request exception
   - **Ad-Hoc Services**: More marketplace model, may show contractor options in future
   - **MVP**: Both use primary contractor assignment

5. **Contractor Availability** (Lead Time/Buffer)
   - **HVAC/Water Heater**: 1-2 business days lead time (emergency-level priority)
   - **Electrical (non-emergency)**: 5-6 business days lead time (filler work)
   - **Plumbing**: 3-5 business days (varies)
   - **Appliance**: 2-3 business days
   - Contractors provide availability windows (time slots per day, days of week)

**Quote from Kevin**: "We will default based off our default logic. So we have a primary contractor that we will send out for HPP plan. That is what it's going to display in the app, so they know we have a contractor coming out there, who's going to be that person."

### Customer Preference & Contractor Selection

**MVP Approach**:
- Customer sees pre-selected primary contractor
- "Here's who's coming to your house" (not "select your contractor")
- Hidden option to request different contractor (small link/button)
- Requesting alternative triggers phone call to admin

**Quote from Kevin**: "I'd rather not give that transparent, hey, go select somebody else, because we have negotiated pricing, negotiated territories... I think that as long as you display it, say, hey, here's who's coming out to your home, and it's all on that summary page, and then you say, if you would like to change the contractor, blah blah, and it's like a little button that you can say, okay, I want to edit it."

**Why Limit Selection**:
1. **Negotiated Rates**: Duke has pre-negotiated pricing with primary contractors
2. **Prevent Gaming**: Customers may "contractor shop" to find one who will cover exclusions
3. **Territory Commitments**: Contractors have contractual territory obligations
4. **Operational Complexity**: Multiple contractors for same job creates backend coordination issues

**Quote from Chris Murphy**: "One of the challenges with that is customers become very strategic. So they get one contractor who knows their situation and knows that something's not covered because it's a code violation. Then they start going through the contractor list saying, well, I want someone else out here... until they try to find the right one who will cover something that should not be covered."

**Future State** (Phase 2+ with Ad-Hoc Services):
- For cash-pay ad-hoc services, may allow contractor selection
- Display multiple contractors with pricing and ratings
- Customer chooses based on availability, price, ratings
- No "gaming" risk since customer pays directly

### Exception Handling

**Scenario 1: Primary Contractor Unavailable**
- **Current**: Admin calls backup contractor, attempts to keep same time window
- **MVP**: Admin manually reassigns, updates app with new contractor/time
- **Customer Communication**: Admin calls/texts customer if time must change

**Scenario 2: Primary Contractor Declines**
- **Frequency**: Less than 5% of the time (rare due to SLA contracts)
- **Current**: Admin reassigns to backup contractor
- **MVP**: Same process, admin updates app
- **Goal**: 90-95% acceptance rate from primary contractors

**Scenario 3: No Contractors Available in Zip Code**
- **Current**: Rare - 99%+ coverage in served territories
- **MVP**: System should flag "service not available in your area" if no contractor match
- **Workaround**: Admin can manually reach out to contractors to expand coverage

**Scenario 4: All Contractors at Capacity**
- **Current**: Extend time window, offer later dates
- **MVP**: Show later availability windows to customer
- **Future**: Track contractor workload to close time slots when at capacity

**Scenario 5: Emergency/Hurricane Events**
- **Current**: Admin manually overrides assignments, extends buffers, communicates delays
- **MVP**: Admin can flag "service delays in your area" banner in app
- **Notification**: Proactive alerts to affected customers

**Quote from Ed Carr**: "Kevin, what are your thoughts about hurricanes and things like that, sometimes when a contractor has a zip code, but they're not available?"

**Quote from Kevin**: "We would just have to consider, do we override that inside the app that this contractor's buffer is changed or this is the primary contractor, which is maybe a secondary contractor normally for that territory."

---
