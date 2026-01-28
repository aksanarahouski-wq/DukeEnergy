# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 10. INVENTORY DATA COLLECTION FROM CONTRACTORS

### The Opportunity

**Problem**: Customers don't know what appliances/systems they have
- Make/model/serial numbers not readily accessible
- Age of equipment unknown
- Customer-entered data often incomplete or inaccurate

**Solution**: Contractors capture inventory during service visits
- Technician is already at appliance/system
- Can easily read data plate (make, model, serial, manufacture date)
- Photos of data plate uploaded to app
- Customer profile automatically updated with accurate data

**Benefits**:
- **For Customer**: Automated home inventory, no effort required
- **For Duke**: Better service delivery with accurate equipment data
- **For Contractor**: More targeted future work (know when equipment end-of-life approaching)

**Quote from Aksana**: "One thing we'll have to solve for new data like inventory, right? Because right now, we're kind of assuming that we're dealing with the same data that already exists... we want contractors to provide after the service has been served, perhaps they can add feedback comments as far as this is the model, this is the year, so we can upgrade that customer profile for the future improvements."

### MVP Scope Question: How to Implement?

**Challenge**: Contractor portal not being rebuilt for MVP

**Options**:

**Option 1: Manual Process - Admin Enters Data**
- Contractor takes photo of data plate during service
- Contractor emails/texts photo to Duke admin
- Admin manually enters data into customer profile in app admin backend
- **Pros**: No contractor system changes needed
- **Cons**: High admin burden, slow data entry

**Option 2: Contractor Portal Simple Form**
- Add lightweight form to existing Commerce portal
- Contractor enters: Make, Model, Serial Number, Manufacture Date
- Form submits data to app backend API
- **Pros**: Direct data flow, faster entry
- **Cons**: Requires minor contractor portal enhancement (may violate "no contractor changes" decision)

**Option 3: Defer to Phase 2**
- No inventory collection from contractors for MVP
- Rely on customer-entered data only
- Phase 2: Build into contractor mobile app
- **Pros**: Simplest for MVP
- **Cons**: Missed opportunity to build high-quality inventory data

**Recommendation**: Option 2 if feasible, otherwise Option 3

**Quote from Kevin**: "Yes, 100%. That's a great call out. How do we collect that information from the contractor to feed it back into the database that will probably not exist inside of Commerce to be able to communicate it back through the Commerce database. Now, we may have to think about that in the future, Joshua, of, you know, do we have a place for them to update the order itself so that it feeds back over? And then we feed that back over to the app, etc."

### Contractor Incentive Model (TBD)

**Question**: How do we incentivize contractors to capture inventory data?

**Options**:
1. **No Additional Payment**: Part of service expectations, tied to SLA
2. **Small Per-Item Bonus**: $5-10 per appliance/system documented
3. **Gamification**: Contractor leaderboard, recognition for most data captured
4. **Future Work Pipeline**: "You capture data now, you know when equipment needs replacement, you get the replacement job"

**Requires Discussion With**:
- Contractor field coordinators
- Chris Murphy's contractor network team
- Contract negotiation team

**Quote from Kevin**: "Correct. And so stuff like that would be stuff we would have to ask them to do outside. And I think that that's a different ask that we can do. We definitely would want to do and ask for them to do... what that will do is provide us more information about the home. So we'll know what parts you need, et cetera. And they'll see the benefit of that."
