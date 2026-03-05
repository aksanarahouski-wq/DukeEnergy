# Defect Severity Matrix
**Duke Energy Residential Solutions Home Services App**

---

## Overview

Defects will generally be categorized by severity to support prioritization. Resolution timelines are best-effort targets and are dependent on defect complexity, prioritization, and available capacity. This SOW does not establish fixed service-level guarantees.

---

## Severity Definitions and Examples

| Severity | Definition | Examples |
|----------|------------|----------|
| **Critical** | System is unusable or major functionality is completely broken. Data loss or security vulnerability present. No workaround available. | • Application crashes on launch<br>• Payment processing failure<br>• Security vulnerability exposing customer data<br>• Unable to create service requests (core function completely broken)<br>• Database connection failure preventing all operations<br>• Authentication system down - no users can log in<br>• HPP coverage data displaying incorrectly causing wrong service pricing<br>• Customer PII exposed in API responses<br>• Service requests being sent to wrong contractors system-wide |
| **High** | Major feature is broken or significantly impaired. Affects many users. Workaround is difficult or impractical. | • Service booking fails for specific customer segment<br>• Home inventory data not saving<br>• Admin portal login issues<br>• Push notifications not being sent for service updates<br>• Contractor assignment logic failing for entire service territory<br>• HPP plan details not loading (customers can't verify coverage)<br>• Search functionality completely non-functional<br>• Service history showing incorrect or missing data<br>• Photo upload failing for all home inventory items<br>• SpeedPay integration broken for non-native customers<br>• Email confirmations not sending after service booking |
| **Medium** | Feature is partially broken or behaves incorrectly. Affects some users. Reasonable workaround exists. | • UI rendering issue on specific device<br>• Validation error message unclear<br>• Search returns incorrect results intermittently<br>• Barcode scanner fails on certain device models (manual entry available)<br>• Maintenance reminder notifications delayed by several hours<br>• Service request status updates not refreshing until app restart<br>• Filter options in service history not working correctly<br>• Warranty expiration dates off by one day due to timezone handling<br>• DIY tutorial videos not loading on iOS (work on Android)<br>• Address autocomplete suggests incorrect city names<br>• Service appointment time slots showing in wrong timezone |
| **Low** | Minor issue with minimal impact. Cosmetic or edge case. Workaround is easy. | • Typo in label or message<br>• Minor UI alignment issue<br>• Non-critical error in logs<br>• Icon not centered in button<br>• Inconsistent font size in footer text<br>• Missing period at end of help text<br>• Color slightly off-brand in one screen<br>• Tooltip appears too quickly on hover<br>• Loading spinner animation slightly choppy<br>• Date format inconsistent between screens (MM/DD vs DD/MM)<br>• Extra whitespace in text field<br>• Sort order default not ideal but all options work |

---

## Prioritization Guidelines

### Critical Defects
- **Impact:** Complete system failure or security breach
- **User Impact:** All or most users unable to complete core workflows
- **Business Impact:** Revenue loss, data breach, regulatory risk, reputation damage
- **Response Expectation:** Immediate response required
- **Acceptance Criteria:** Must be resolved before release/acceptance

### High Defects
- **Impact:** Major feature broken or severely degraded
- **User Impact:** Large subset of users significantly impaired
- **Business Impact:** Customer satisfaction impact, support burden increase
- **Response Expectation:** Prioritized resolution
- **Acceptance Criteria:** Must be resolved before release/acceptance

### Medium Defects
- **Impact:** Feature partially working or inconsistent behavior
- **User Impact:** Some users affected, workaround available
- **Business Impact:** Minor customer dissatisfaction, increased support calls
- **Response Expectation:** Scheduled based on priority and capacity
- **Acceptance Criteria:** Does NOT block acceptance; added to backlog for prioritization

### Low Defects
- **Impact:** Minor issue, cosmetic, or edge case
- **User Impact:** Minimal or no impact on user workflow
- **Business Impact:** Negligible
- **Response Expectation:** Scheduled based on priority and capacity
- **Acceptance Criteria:** Does NOT block acceptance; added to backlog for prioritization

---

## Defect Escalation Process

### When to Escalate

**Critical Defects:**
1. Discovered in production → Immediate escalation to Product Manager and CLIENT Product Owner
2. Discovered during testing → Block release, escalate to Technical Lead and Product Manager
3. Security vulnerabilities → Immediate escalation regardless of environment

**High Defects:**
1. Discovered within 48 hours of planned release → Escalate to Product Manager for go/no-go decision
2. Multiple High defects in same area → Escalate to Technical Lead for architectural review
3. Recurring High defects after fixes → Escalate for root cause analysis

**Medium/Low Defects:**
1. Standard prioritization process through backlog refinement
2. Escalate only if pattern indicates underlying systemic issue

### Escalation Contacts

**Orases Team:**
- Critical/High defects → Product Manager + Technical Lead
- Production Critical defects → Product Manager + CLIENT Product Owner (immediate)

**CLIENT Team:**
- All production defects → CLIENT Product Owner
- Critical defects → CLIENT Product Owner + Executive Sponsors

---

## Defect Lifecycle

```
1. Defect Identified
   ↓
2. Severity Assigned (using matrix above)
   ↓
3. Impact Assessment
   ↓
4. Prioritization Decision
   ↓
5. Resolution (or defer to backlog)
   ↓
6. Testing/Validation
   ↓
7. Deployment
   ↓
8. Verification in Production
   ↓
9. Closure
```

---

## Special Considerations

### Security Vulnerabilities
- **ALL security vulnerabilities are treated as Critical** regardless of likelihood of exploitation
- Must be patched before production deployment
- Require security review and sign-off
- May require immediate production hotfix depending on exposure risk

### Data Integrity Issues
- Defects causing **data loss, corruption, or incorrect data storage** are elevated to Critical
- Defects causing **data display issues** (but data stored correctly) may be High or Medium depending on business impact

### Integration Failures
- Commerce CRM integration failures → Critical (blocks service request flow)
- Dynamics integration failures → Critical (blocks contractor coordination)
- SpeedPay integration failures → High (only impacts non-native customers, manual payment alternative exists)
- Analytics integration failures → Medium (does not block core workflows)

### Cross-Platform Issues
- Defect affecting **both iOS and Android** → Severity as defined in matrix
- Defect affecting **only one platform** → Reduce severity by one level if workaround exists (use other platform)
- Exception: If defect affects majority platform (e.g., 70% of users on iOS) → Keep original severity

### Performance Degradation
- Response time >10 seconds for core functions → Critical
- Response time 5-10 seconds → High
- Response time 2-5 seconds → Medium
- Response time <2 seconds → Low (if noticeable lag but still responsive)

---

## Examples by Feature Area

### Service Request Booking (Core Function)
- **Critical:** Cannot create service request at all
- **High:** Service request created but contractor not assigned
- **Medium:** Service request created but confirmation email delayed
- **Low:** Service request form field labels slightly misaligned

### Home Protection Plan (HPP) Management
- **Critical:** HPP coverage data incorrect (wrong plan details displayed)
- **High:** Cannot view HPP plan details at all
- **Medium:** HPP renewal date shown in wrong format
- **Low:** HPP plan description text truncated on small screens

### Home Inventory
- **Critical:** Home inventory data being deleted or corrupted
- **High:** Cannot add items to home inventory (photos upload fails consistently)
- **Medium:** Barcode scanner doesn't work on some devices (manual entry available)
- **Low:** Item categories not sorted alphabetically

### Contractor Coordination (Admin Backend)
- **Critical:** Service requests routed to wrong contractors
- **High:** Contractor availability not updating (all appear unavailable)
- **Medium:** Contractor assignment algorithm not optimal (manual reassignment works)
- **Low:** Contractor profile photos not displaying correctly

### Payment Processing
- **Critical:** Payment processing fails with error (money not charged, service not confirmed)
- **High:** Payment succeeds but confirmation not recorded (creates billing disputes)
- **Medium:** Payment form validation prevents valid card formats
- **Low:** Payment success message displays with typo

---

## Version History

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0 | 2026-02-27 | Initial defect severity matrix with comprehensive examples | Risk Analysis Team |

---

**Reference:** This matrix supports Section 2.8.8 (Defect Severity Matrix) of SOW #1 between Duke Energy and Orases.
