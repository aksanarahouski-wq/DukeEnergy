# Contractor Portal - Preliminary Scope & Requirements
## Duke Energy Residential Solutions Home Services App

---

## 8. PAYMENT & INVOICING

### HPP Covered Service Payment (No Customer Payment)

**Current Process**:
1. Contractor performs covered service at no charge to customer
2. Contractor invoices Duke for negotiated rate
3. Duke pays contractor (e.g., $500 for covered repair)
4. Customer pays $0 out-of-pocket

**If Service Exceeds Coverage**:
1. Contractor identifies issue exceeds coverage limits (e.g., code violation, additional parts needed)
2. Contractor provides quote for excess work to customer
3. Customer pays contractor directly for excess amount (cash, check, contractor's credit card reader)
4. Contractor invoices Duke for covered portion
5. Example: Service requires $800 repair, plan covers $500, customer pays contractor $300

**Quote from Kevin**: "Warranty covered: Duke pays contractor. Excess/over coverage: Customer pays contractor directly."

### Ad-Hoc Service Payment

**Phase 1 MVP - Contractor Collects On-Site**:

1. **At Booking**:
   - App displays service price: "HVAC Tune-Up - $99"
   - Payment note: "Payment collected by contractor on-site (cash, check, credit card)"
   - Customer books service

2. **At Service Completion**:
   - Contractor performs service
   - Contractor collects $99 from customer using their own payment method:
     - Cash
     - Check
     - Credit card via contractor's Square/Stripe/Clover reader
   - Contractor provides receipt to customer

3. **Contractor Reporting to Duke**:
   - Contractor updates Commerce portal: Service completed
   - Contractor reports payment collected (for Duke's ad-hoc service tracking)
   - If Duke takes commission: Contractor invoices Duke for their net amount
   - Example: Customer pays contractor $99, Duke takes $24 commission, contractor keeps $75 and invoices Duke for $24? (commission model TBD)

**Quote from Kevin**: "Phase 1 - contractor collects payment on-site."

**Commission Model (TBD)**:
- Does Duke take a percentage of ad-hoc services?
- If yes: How much? (e.g., 20% = $20 on $99 service)
- How is commission collected? Deducted from contractor payment? Invoiced separately?
- How does contractor report cash payments?

**Phase 2 - App-Based Payment**:

1. **At Booking**:
   - Customer enters credit card, Apple Pay, Google Pay
   - Customer pre-pays $99 in app
   - Duke collects $99

2. **After Service**:
   - Duke pays contractor their portion (e.g., $75 if 20% commission)
   - Contractor paid via direct deposit or check
   - Customer already paid, no on-site payment collection needed

3. **Benefits**:
   - Customer convenience
   - Payment tracking in app
   - Reduces contractor burden
   - Duke captures commission automatically

**Quote from Kevin**: "Future: Customer pays Duke via app → Duke pays contractor."

### Contractor Invoicing to Duke

**Current Process** (Continues for MVP):
1. Contractor completes service
2. Contractor updates Commerce portal with completion details:
   - Services performed
   - Parts used
   - Labor hours
   - Total cost
3. Contractor invoice created in Commerce
4. Duke back office reviews and approves
5. Contractor paid via check or direct deposit (Net 30 terms typically)

**For App MVP**:
- No changes to contractor invoicing process
- Contractor continues using Commerce portal for invoicing
- Admin updates app service request status to "Completed" after contractor invoices
