# Session 2: Admin Discovery

**Focus:** Define admin roles, understand product/content management needs, and decide CMS approach.

**🚨 CRITICAL:** Duke IT should attend this session for integration discussion.

---

## Critical Questions to Answer

### **1. Admin Roles & Responsibilities**

**Goal:** Understand who needs access to admin portal and what they need to do.

**Questions:**
- Who are the admin users? (content managers, product managers, operations, analysts?)
- How many total admin users? (5? 10? 50?)
- What systems do admins use today? (Commerce, Dynamics, contractor portal, others?)
- What are current pain points with managing operations?

**Why This Matters:** Defines admin portal complexity and user permissions model.

**Typical Roles We See:**
- Content Manager (DIY library)
- Product Catalog Manager (ad-hoc services & pricing)
- **HPP Plan Catalog Manager** (manages plan offerings, pricing, coverage)
- Service Operations Manager (service request oversight)
- Analytics/Reporting User (dashboards)
- Super Admin (user management, system config)

**HPP Plan Management Questions:**
- Who creates/manages HPP plan catalog? (product team, marketing, operations?)
- How often do plan details change? (rarely, quarterly, annually?)
- Do admins need to create new HPP plans in app? Or plans managed in Commerce/Dynamics only?
- Can admins enroll customers in HPP plans manually? (customer support use case)
- What reports do admins run on plan enrollment? (adoption rates, revenue, churn, etc.)

**DECISION:** Which roles needed for MVP vs Phase 2?

---

### **2. Product Catalog & Pricing Management - THE UNDEFINED PIECE**

**Goal:** Understand who manages ad-hoc services and how pricing works.

**From Meeting1:45:58:** "Ad-hoc service pricing still in development"

**CRITICAL Questions:**
- **Who sets pricing for ad-hoc services?** (product team proposes, operations approves, executive approves?)
- **How is pricing determined?** (fixed price per service, regional variations, quote-based?)
- **How often will pricing change?** (rarely, monthly, quarterly?)
- Can pricing vary by:
  - Region? (Charlotte vs Raleigh different prices?)
  - Season? (HVAC more expensive in summer?)
  - Contractor? (different contractors charge different rates?)

**Ad-Hoc Service Catalog Data Requirements:**
- **Required fields:**
  - Service name (e.g., "HVAC Tune-Up")
  - Service code/SKU (for reporting)
  - Category (HVAC, plumbing, electrical, appliance, other)
  - Description (what's included)
  - Price (fixed price, price range, or "call for quote")
  - Active status (active, inactive, coming soon)
- **Optional fields:**
  - Estimated duration, photos, required contractor trade, geographic availability
- **Pricing structure:**
  - Single price or varies by region/season?
  - How is pricing stored? (single field or pricing table with dimensions?)
- **Price change tracking:**
  - When price changes, is history kept? (important: customers might book at old price)
  - Price history table needed?
- **Service availability:**
  - How to track which services available in which zip codes?
  - How to track seasonal availability? (e.g., snow removal winter only)

**Who can create/edit services:**
- Product Manager: Create/edit services
- Operations Manager: Edit pricing?
- Or single "Product Catalog Manager" role?

**Duke vs P&G Territory Questions:**
- **Same ad-hoc service catalog for Duke and P&G territories?** Or separate catalogs?
- **Different pricing by Duke vs P&G territory?** (e.g., Charlotte Duke vs Charlotte P&G)
- Do Duke and P&G contractors offer same services?

**Why This Matters:** **Pricing structure is not defined and affects revenue model.** Ad-hoc service catalog does NOT exist today - need to build from scratch. If pricing changes frequently, need robust admin tools. If Duke/P&G have different catalogs, doubles complexity.

**DECISION:** Approval workflow needed or can authorized admin change pricing directly?

---

### **3. Content Management System (CMS) - ARCHITECTURE DECISION**

**Goal:** Decide between custom CMS (Orases proposal) or third-party.

**From Meeting2:10:23-11:46:** Orases proposed **custom CMS** built into admin portal
- **Pros:** Seamless integration, tailored to needs, no third-party costs
- **Cons:** Duke depends on Orases for updates, may be less feature-rich initially

**Alternative:** Third-party CMS (WordPress, Contentful, Strapi, etc.)
- **Pros:** Mature feature set, Duke can manage independently
- **Cons:** Additional licensing costs, requires integration, separate system to learn

**Questions:**
- Does Duke team have CMS experience/preference?
- How important is independence from vendor for content management?
- What's expected content volume? (10s? 100s? 1000s of articles?)
- Are advanced CMS features needed? (A/B testing, personalization, SEO tools?)

**Why This Matters:** Affects architecture, cost model, and Duke's long-term platform independence.

**DECISION:** Custom CMS (Orases builds) or third-party CMS (integrate existing)?

---

### **4. DIY Content Creation - OWNERSHIP & TIMELINE**

**Goal:** Clarify who creates content and when it needs to be ready.

**CRITICAL Questions:**
- **WHO creates DIY content?** (Duke internal team, Orases, contractors, third-party partner?)
- **HOW MUCH content at launch?** (10 articles minimum? 50? 100?)
- Does any content exist today? (website, call center scripts, email templates?)
- What's the approval workflow? (legal review required? SME review? How long?)
- **WHEN will content be created?** (in parallel with dev, or before launch?)

**DIY Content Data Requirements:**
- **Content types to support:**
  - Article (rich text with images)
  - Video (embedded or hosted - YouTube/Vimeo/self-hosted?)
  - PDF (downloadable documents)
  - Step-by-step wizard (interactive troubleshooting)?
  - FAQ (question + answer pairs)
- **Required fields (all content types):**
  - Title, content type, body/video URL/PDF file, status (draft/published/archived)
  - Primary category (HVAC, plumbing, electrical, appliances, general)
  - Tags (for search)
  - Created by, created date, published date, last updated
- **Content organization:**
  - How to categorize? (single category or nested sub-categories?)
  - Tag-based search or category-based browse?
  - Related content linking needed?
- **Content approval workflow:**
  - Status flow: Draft → Pending Review → Approved → Published? Or simpler?
  - Who approves? (content manager, legal team, SME?)
  - Approval tracking needed? (who approved, when, comments)
- **Content analytics:**
  - View count, time on page, helpfulness ratings (thumbs up/down or 1-5 stars)?
  - Customer comments/feedback?

**Media storage:**
- Where are images/videos/PDFs stored? (AWS S3? CDN?)
- Max file sizes?

**Who can create/publish content:**
- Content Manager: Create/edit/publish
- Marketing: Create/edit drafts only?
- Legal: Approval role only?

**Duke vs P&G Content Questions:**
- **Same DIY content library for Duke and P&G customers?** Or territory-specific content?
- Branded as "Duke Residential Solutions" for both? Or separate P&G branding?
- Do Duke and P&G territories have different regulations requiring different content? (e.g., electrical codes)

**Why This Matters:** **If content creation is on critical path and not resourced, it will delay launch.** DIY content does NOT exist today - need to create from scratch. If Duke/P&G need separate content libraries, doubles content creation effort. Need to set realistic expectations.

**Content Types for MVP:**
- Articles/troubleshooting guides (text + images)
- Videos (how-to demonstrations)
- FAQs
- Step-by-step wizards (interactive)? - higher complexity

---

### **5. Service Operations Oversight**

**Goal:** Understand what visibility operations team needs into active service requests.

**Questions:**
- What visibility do operations managers need? (all active requests, by status, by contractor, by region?)
- What actions can operations managers take? (reassign contractor, escalate, cancel?)
- What triggers manual intervention? (no contractor accepts, customer complaint, contractor no-show?)
- Can operations managers communicate with customers or contractors via admin portal?

**Why This Matters:** Defines service operations dashboard scope.

---

### **6. Analytics & Reporting Needs**

**Goal:** Understand what metrics matter and who needs dashboards.

**Questions:**
- What metrics are most important to track?
  - Customer acquisition (registrations, active users)
  - Service request volume (by type, by region, trends)
  - Revenue (ad-hoc services)
  - Contractor performance (ratings, on-time %, utilization)
  - Customer satisfaction (NPS, CSAT, ratings)
- Who needs dashboards? (operations daily, executives monthly, marketing for campaigns?)
- Real-time data or daily refresh acceptable?
- Need to export reports? (to Excel, PDF?)

**Why This Matters:** Determines analytics complexity. Real-time dashboards are more complex than daily batch reports.

**DECISION:** MVP analytics scope (basic dashboards vs advanced BI)?

---

### **7. System Integration - Admin Perspective**

**Goal:** Understand admin-side integrations with Duke IT.

**🚨 Duke IT Should Answer:**

**Authentication:**
- SSO with Duke corporate IT for admin portal? (SAML, Okta, Azure AD?)
- Or separate login?

**Data Access:**
- Can admins view customer data from Commerce/Dynamics via admin portal?
- Or must they log into separate systems?
- If admin edits customer info, where does it update? (Commerce, app database, both?)

**Service Request Management:**
- If admin creates service request on behalf of customer, where is it created? (Dynamics, app database, both?)
- Can admin see service requests from BOTH app AND legacy call center? (unified view?)

**Why This Matters:** Defines integration architecture and Duke IT's role.

---

## Expected Outputs

By end of Session 2, we'll have:

✅ **Admin roles defined** (types, quantities, permissions)
✅ **Pricing management workflow** documented
✅ **CMS decision made** (custom vs third-party)
✅ **Content creation ownership** assigned
✅ **Service operations requirements** understood
✅ **Analytics scope** defined for MVP
✅ **Admin portal wireframe sketches** (10-15 screens)

---

## Key Risks to Surface

**Flag these if they emerge:**

🔴 **HIGH RISK:**
- Pricing structure not defined (blocks ad-hoc service feature)
- Content creation ownership unclear or not resourced (delays launch)
- Duke IT not available for SSO/integration discussion

🟡 **MEDIUM RISK:**
- Content approval process lengthy (legal review bottleneck)
- Admin users not identified or too many stakeholders
- CMS decision delayed (affects architecture)

---

## Key Decisions This Session

| Decision | Options | Impact |
|----------|---------|--------|
| **CMS Approach** | Custom vs Third-party | Architecture, cost model, Duke independence |
| **Pricing Management** | Simple (rarely changes) vs Complex (frequent changes, approvals) | Admin tool complexity |
| **Content Creation** | Duke team, Orases, Contractors, Third-party | Timeline, cost, quality |
| **Admin Analytics** | Basic dashboards vs Advanced BI | Development scope |
| **SSO for Admin** | Duke SSO vs Separate login | Integration with Duke IT |

---

## Pre-Session Preparation Needed

**Duke Team Should Prepare:**
- List of admin users and their roles
- Current content examples (if any exist)
- Pricing philosophy for ad-hoc services (if defined)
- Analytics/reporting examples (what reports run today?)

**Duke IT Should Prepare:**
- SSO capabilities (what systems support SSO?)
- Data access policies (can admin portal read from Commerce/Dynamics?)
- Integration preferences

**Orases Team Will Prepare:**
- CMS comparison document (custom vs third-party pros/cons)
- Admin portal wireframe concepts
- Pricing management workflow examples from similar projects

---

**Session Facilitator:** Aksana (Orases Product Manager)
**Session Designer:** Devin (Orases Product Designer & Business Analyst)
**Technical Lead:** Vlad (Orases CTO) - for integration discussion
