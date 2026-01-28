# Admin Portal - Preliminary Scope & Requirements

**Meeting Date:** Session 2 - Admin Discovery
**Document Created:** November 19, 2025
**Purpose:** Define admin portal functionality, workflows, and MVP scope based on Session 2 discovery workshop

---

## OPEN QUESTIONS & RISKS

### Unresolved Questions

#### **APIs & Integration:**
1. **Which APIs will exist by MVP launch?** - Need commitment from Duke IT on timeline
2. **Enrollment API timeline** - If doesn't exist for MVP, how long will manual fallback be needed?
3. **Service request creation API** - Can app create service requests directly in Dynamics? Or manual queue?
4. **FSM tool selection** - What's the timeline for Duke to select and implement FSM tool?
5. **SSO capabilities** - Can Duke IT provide SSO for admin portal? Timeline?

#### **Data & Permissions:**
6. **Admin access to CRM** - Will all admins have CRM access? Or some use app backend only?
7. **Data privacy** - What customer data can admins view? Are there restrictions (e.g., payment info)?
8. **Multi-level permissions** - How many permission levels needed? (3? 5? 10?)

#### **Ad-Hoc Services:**
9. **Initial service list** - Which 5-10 services to launch with? Pricing finalized?
10. **Pricing approval workflow** - Who approves pricing changes? Product manager alone or executive approval?
11. **Regional pricing strategy** - How different should pricing be across markets?
12. **Contractor negotiation** - Timeline for negotiating flat rate prices with contractors?

#### **Reminders:**
13. **Default reminder list** - What's the "starter set" of reminders? (10? 20? 50?)
14. **Reminder frequency** - How often should reminders trigger? (monthly, quarterly, annually?)
15. **Asset-to-reminder mapping** - Which reminders apply to which inventory categories?

#### **Analytics:**
16. **Analytics tool** - Build custom dashboards or integrate third-party BI tool (Tableau, Looker, etc.)?
17. **Data retention** - How long to keep historical data? (1 year? 5 years? Forever?)

---

### Risks

#### 🔴 **HIGH RISK:**

**1. Duke IT API Delays**
- **Risk:** APIs promised for MVP don't deliver on time
- **Impact:** Manual fallback processes required longer than anticipated, admin workload increases
- **Mitigation:** Build robust manual fallback processes, get written commitment from Duke IT on API timeline

**2. CRM System Constraints**
- **Risk:** CRM systems (Commerce, Dynamics) can't support app volume or real-time API calls
- **Impact:** Performance issues, data sync delays, poor customer experience
- **Mitigation:** Load testing, discuss with Duke IT infrastructure requirements

**3. Admin User Adoption**
- **Risk:** Admins resist using new backend system, prefer existing CRM
- **Impact:** Low adoption, data entry errors, poor data quality
- **Mitigation:** Admin training, make new system EASIER than existing process, gather admin feedback early

#### 🟡 **MEDIUM RISK:**

**4. Ad-Hoc Service Catalog Readiness**
- **Risk:** Pricing not finalized, scope of work undefined, contractor negotiations incomplete
- **Impact:** Launch with very limited ad-hoc services, miss revenue targets
- **Mitigation:** Prioritize 3-5 "hero services," launch in limited geography, expand gradually

**5. Data Quality Issues**
- **Risk:** Customer data in CRM is incomplete or inaccurate (missing addresses, wrong phone numbers)
- **Impact:** Service request failures, customer frustration, admin manual cleanup
- **Mitigation:** Data validation rules, admin can correct data in app backend

**6. Analytics Tool Selection Delay**
- **Risk:** Decision on analytics/BI tool delayed, can't build dashboards in time
- **Impact:** No visibility into app performance at launch
- **Mitigation:** Start with basic reporting (SQL queries, CSV exports), upgrade to dashboards in Phase 2

---

