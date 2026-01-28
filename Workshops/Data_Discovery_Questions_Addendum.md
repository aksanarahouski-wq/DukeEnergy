# Data Discovery Questions - Workshop Addendum

**Purpose:** Supplement workshop sessions with data-focused questions to understand current data management processes and design database schema
**Created:** November 5, 2025
**Use:** Insert relevant sections into workshop session agendas

---

## For Session 1: Customer Discovery

### INSERT INTO "Part 1: Customer Types & Personas Validation"

#### **DATA DISCOVERY: Customer Entity**

**Current State Data Questions:**

1. **Where is customer data stored TODAY?**
   - Native Duke customers: Commerce platform?
   - Native P&G customers: Dynamics?
   - What fields exist in each system? (can we see sample export or screen recording?)
   - Are there other systems that store customer data?

2. **What customer data do you have TODAY?**
   - Customer ID/account number
   - Name (first, last, middle)
   - Contact info (email, phone, address)
   - HPP plan enrollments
   - Service history
   - Payment/billing information
   - What else?

3. **Customer data quality:**
   - How accurate is current customer data? (% of records with valid email, phone?)
   - How often is data updated?
   - What happens when customer moves or changes contact info?
   - Do customers update their own info or call center?

4. **Multi-property customers:**
   - **CRITICAL:** What percentage of customers have multiple properties?
   - How are multiple properties tracked today? (separate accounts, linked accounts, not tracked?)
   - Do customers have different HPP plans for different properties?
   - Is property address always same as mailing address?

5. **Customer identity & authentication:**
   - How do you verify customer identity when they call today?
     - Account number + last name?
     - Address + phone number?
     - Last 4 of SSN?
   - What should authentication look like for app?
     - For native customers: Login with account number? Email? Create username/password?
     - For non-native customers: Email + password? Social login (Google, Apple)?

6. **Non-native customers:**
   - Do you serve non-native customers TODAY in any capacity?
   - If yes, where is that data stored?
   - If no, what data needs to be collected for non-native customers?
     - No utility account number
     - How to verify identity?
     - How to link to property if not utility customer?

**Data Architecture Questions:**

7. **Master source of truth:**
   - If customer exists in both Commerce AND app database, which is master?
   - How do we keep data in sync?
   - What if customer updates email in Commerce but different email in app?

8. **Customer preferences:**
   - Do you track customer communication preferences today? (email, SMS, do not call?)
   - Language preference? (Spanish-speaking customers - what %?)
   - Notification frequency preferences?
   - Where would this live? (new app database since doesn't exist?)

**Role-Based Access Questions:**

9. **Who can view/edit customer data?**
   - Can customers view/edit their own data in app? (which fields?)
   - Can admins view/edit customer data? (which admins, which fields?)
   - Can contractors see customer contact info? (privacy concern)
   - Should contact info be masked/proxied?

**Output:** Customer data model specification

---

### INSERT INTO "Part 2: Service Request Journey"

#### **DATA DISCOVERY: Service Request / Claims Entity**

**After walking through 3-5 real examples, ask these data questions:**

1. **Where is service request data stored TODAY?**
   - Dynamics primary system?
   - Commerce also stores something?
   - Contractor portal has its own records?
   - How do these systems sync?

2. **Service request lifecycle data:**
   - **When is service request created?**
     - When customer calls?
     - When CSR enters into system?
     - When contractor accepts?
   - **What statuses exist today?**
     - Can we see the exact status values? (Requested, Assigned, In Progress, etc.?)
     - How many statuses? (5? 10? 20?)
   - **Who can change status?**
     - CSR?
     - Contractor?
     - Automated system?

3. **Service request data fields:**
   - Can we see a service request record in Dynamics? (screen share)
   - What fields are **required**?
   - What fields are **optional**?
   - What fields are **auto-populated**? (created date, customer info, etc.)

4. **Problem description:**
   - Is it free-text entry? Or dropdown selection?
   - If dropdown, what are the options?
   - Can customer upload photos with problem description?
   - Do photos get stored in Dynamics or separate system?

5. **Priority/urgency:**
   - How is priority determined? (Customer declares? CSR determines? Rule-based?)
   - What priority levels exist? (Emergency, Urgent, Routine, Scheduled?)
   - Do different priorities have different SLAs?

6. **Service request ownership:**
   - Does a service request "belong" to a customer (many requests per customer)?
   - Can service request move between properties? (if customer has multiple?)
   - Can service request be transferred to different customer? (e.g., property sold?)

7. **Service history:**
   - How long is service request history kept?
   - Can you pull service history for a customer going back 5 years? 10 years?
   - Is old data archived or deleted?

8. **Data retention:**
   - Are there regulatory requirements for how long service request data must be kept?
   - PII retention policies?

**Coverage Determination Data:**

9. **HPP coverage data:**
   - Where are coverage rules stored? (Commerce, Dynamics, documents, people?)
   - Can we see coverage rules documentation?
   - Is it structured data (database) or unstructured (Word docs, PDFs)?
   - Who updates coverage rules when plans change?

10. **Coverage decision tracking:**
    - When service request is determined "covered" or "not covered," is that decision logged?
    - Who made the decision?
    - What was the reason?
    - Can decision be appealed or overridden?
    - Is override logged with reason?

**Contractor Assignment Data:**

11. **Assignment data:**
    - Is contractor assignment stored with service request?
    - Is assignment history tracked? (offered to Contractor A, declined, offered to Contractor B, accepted?)
    - Why is this important? (to improve matching algorithm over time)

12. **Reassignment:**
    - Can service request be reassigned to different contractor?
    - Who can reassign? (customer, admin, contractor?)
    - Is reassignment reason tracked?

**Service Completion Data:**

13. **Completion information:**
    - What does contractor enter when service is complete?
    - Free-text summary? Structured fields?
    - Parts used: free-text or selected from parts catalog?
    - Time spent: tracked? Required?

14. **Before/after photos:**
    - Do contractors take photos today?
    - Where are photos stored?
    - Can customer see photos?

15. **Customer feedback:**
    - Do customers rate/review service today?
    - Where is feedback stored?
    - Is it linked to service request record?
    - Is it linked to contractor record?

**Role-Based Access:**

16. **Who can see service requests?**
    - Customer: Own requests only?
    - Admin: All requests? Filtered by region/team?
    - Contractor: Assigned requests only?
    - Manager: Team's requests only or all?

17. **Who can edit service requests?**
    - Customer: Can edit before contractor assigned? Can cancel? Can reschedule?
    - Admin: Can edit any field at any time?
    - Contractor: Can edit completion fields only?

18. **Who can delete service requests?**
    - Can service requests be deleted? Or only cancelled?
    - Who has permission?
    - Is deletion audit-logged?

**Output:** Service request data model specification with full field list and CRUD matrix

---

### INSERT INTO "Part 4: Home Inventory Strategy"

#### **DATA DISCOVERY: Home Inventory Entity**

**After discussing MVP scope, ask these data questions:**

1. **Does home inventory data exist ANYWHERE today?**
   - Any customer database with appliance info?
   - Any warranty database?
   - Any home assessment data?
   - Answer: Likely NO - completely new database

2. **What data fields are needed for each inventory item?**

   **Required (minimum viable):**
   - [ ] Item type (HVAC, water heater, electrical, plumbing, appliance - dropdown?)
   - [ ] Specific category (e.g., if HVAC → central AC, heat pump, furnace, ductless mini-split?)
   - [ ] Location in home (basement, garage, attic, kitchen, etc. - dropdown or free-text?)

   **Optional but valuable:**
   - [ ] Make/manufacturer
   - [ ] Model number
   - [ ] Serial number
   - [ ] Purchase date (or "approximately how old?")
   - [ ] Installation date
   - [ ] Warranty expiration date
   - [ ] Warranty provider (manufacturer, Duke HPP, retailer, other)
   - [ ] Estimated replacement cost
   - [ ] Notes/comments (free-text)
   - [ ] Photos

   **Auto-populated (derived from service requests):**
   - [ ] Last service date
   - [ ] Service history (link to service requests)
   - [ ] Next maintenance due date

3. **Data entry complexity:**
   - For EACH field above, ask:
     - Is this dropdown selection or free-text entry?
     - If dropdown, what are the options?
     - How many options? (10? 50? 100s?)
   - Do you want to standardize make/model values? (prevent "LG" vs "LG Electronics" vs "LG Corp")

4. **Data validation:**
   - Should serial numbers be validated against format? (different manufacturers have different formats)
   - Should model numbers be validated?
   - Date validation? (can't be in future, can't be before 1900, etc.)

5. **Relationships:**
   - Can ONE appliance be related to MULTIPLE service requests? (yes - over time)
   - Can ONE service request be related to MULTIPLE appliances? (e.g., whole-house electrical inspection)
   - How to handle replacements? (water heater replaced - archive old record, create new? Or update same record?)

6. **Warranty tracking:**
   - If warranty tracking is MVP feature:
     - Where is warranty document stored? (PDF upload to AWS S3?)
     - File size limits? (max 5MB PDF?)
     - Can customer upload multiple warranty documents per item?
   - Warranty expiration reminders?
     - How far in advance? (30 days, 60 days?)
     - Send via email, push notification, both?

7. **Barcode scanning:**
   - If barcode scanning is MVP feature:
     - What database will we query to look up product info from barcode/serial number?
     - Does it exist? (Third-party service like Central, UPC database, manufacturer APIs?)
     - Cost per lookup?
     - Accuracy rate?
     - What if product not found in database? (fallback to manual entry)

8. **Home inventory completeness:**
   - How do you measure if home inventory is "complete"?
   - Is it percentage-based? ("You've added 5 of estimated 15 appliances")
   - How do you estimate how many appliances customer SHOULD have?
   - Do different property types have different expectations? (condo vs single-family home)

**Role-Based Access:**

9. **Who can create home inventory items?**
   - Customer: Create for own home
   - Admin: Create on behalf of customer (use case: phone support)
   - Contractor: Cannot create? Or can suggest items during service? (future feature)

10. **Who can view home inventory?**
    - Customer: Own inventory only
    - Admin: Any customer's inventory (for support purposes)
    - Contractor: Customer's inventory when assigned to service request (to help diagnose problem)

11. **Who can edit/delete home inventory?**
    - Customer: Edit/delete own items
    - Admin: Edit/delete any items (use case: customer calls to fix incorrect data)
    - Contractor: Cannot edit? Or can update after service? (e.g., "Replaced water heater, here's new model/serial")

**Privacy/Security:**

12. **Sensitive data:**
    - Is home inventory data PII? (reveals what's in someone's home)
    - Data encryption requirements?
    - Should contractor see ALL inventory or only relevant appliance?

**Output:** Home inventory data model specification with field list, validation rules, and CRUD matrix

---

### INSERT INTO "Part 6: Customer Account Management"

#### **DATA DISCOVERY: Payment Methods & Preferences**

1. **Payment data today:**
   - Native customers: How are HPP plans billed? (utility bill - stored in Commerce?)
   - Can we see sample of what payment data looks like?
   - Non-native customers: No payment data exists

2. **Payment method storage:**
   - For non-native customers using ad-hoc services:
     - Store credit card tokens (PCI-DSS compliant tokenization via SpeedPay/Stripe)
     - Store ACH info (tokenized)
     - Multiple payment methods per customer?
     - Default payment method?
   - Where stored? (new app database, but tokens only, not raw card numbers)

3. **Payment history:**
   - Should customers see payment history for ad-hoc services?
   - How far back? (1 year, all time?)
   - Where is payment history stored? (service request has payment link, or separate payment table?)

4. **Refunds:**
   - Can customers request refund via app?
   - Or must call customer service?
   - Refund status tracking? (requested, approved, processing, completed)

**Notification Preferences Data:**

5. **What notification preferences to track?**
   - By channel: Email (yes/no), SMS (yes/no), Push (yes/no)
   - By type: Transactional (yes/no), Promotional (yes/no), Maintenance reminders (yes/no)
   - Frequency: Real-time, daily digest, weekly digest

6. **Where stored?**
   - Customer preferences table in app database
   - Does Commerce/Dynamics have preferences? (if yes, which is master?)

**Language Preference:**

7. **Spanish localization:**
   - What % of customers are Spanish-speaking?
   - Is this MVP feature or Phase 2?
   - If MVP: Does entire app need Spanish or just customer-facing parts?
   - Content in Spanish: Is DIY content translated? Service request forms?

**Output:** Customer preferences data model specification

---

## For Session 2: Admin Discovery

### INSERT INTO "Part 2: Product Catalog & Pricing Management"

#### **DATA DISCOVERY: Ad-Hoc Service Catalog Entity**

**This is NEW data - does not exist today**

1. **Service catalog data fields:**

   **Required:**
   - [ ] Service ID (system-generated UUID)
   - [ ] Service name (e.g., "HVAC Tune-Up")
   - [ ] Service code/SKU (for reporting)
   - [ ] Category (HVAC, plumbing, electrical, appliance, other - dropdown)
   - [ ] Description (what's included - rich text or plain text?)
   - [ ] Price (fixed price, or price range, or "call for quote")
   - [ ] Active status (active, inactive, coming soon)

   **Optional:**
   - [ ] Sub-category (if nested categories needed)
   - [ ] Estimated duration (30 min, 1 hour, 2 hours, etc.)
   - [ ] Prerequisites (e.g., "Requires home assessment first")
   - [ ] Photos/images (service photo for marketing)
   - [ ] FAQ (common questions about this service)
   - [ ] Required contractor trade (HVAC specialist, plumber, electrician, general)
   - [ ] Required certifications (EPA certified, manufacturer certified, etc.)
   - [ ] Parts included (yes/no, or list of parts)
   - [ ] Geographic availability (all markets, specific states/zip codes)
   - [ ] Seasonal availability (e.g., "Snow removal - winter only")

2. **Pricing structure:**
   - Is price a single value? Or does it vary?
   - Regional pricing? (Charlotte price different from Raleigh?)
   - Seasonal pricing? (HVAC more expensive in summer?)
   - Dynamic pricing? (surge pricing during high demand?)
   - How is pricing stored? (single price field, or pricing table with region/season dimensions?)

3. **Pricing approval workflow:**
   - When admin creates new service with price, is approval needed?
   - Who approves? (operations manager, executive, automated if within range?)
   - Approval status field? (pending, approved, rejected)
   - Approval history tracked? (who approved, when, comments)

4. **Price change tracking:**
   - When price changes, is history kept?
   - Price history table? (service ID, price, effective date range, changed by user)
   - Why important: customers might book at old price, need to honor it

5. **Service catalog versioning:**
   - Can you have multiple versions of service catalog?
   - E.g., "HVAC Tune-Up v1" vs "HVAC Tune-Up v2" (expanded to include more)
   - Or just update in place?

6. **Service availability rules:**
   - How to track which services are available in which zip codes?
     - Separate table: ServiceAvailability (service ID, zip code) - millions of rows?
     - Or zip code ranges?
     - Or city/county/state level?
   - How to track seasonal availability?
     - Start date / end date fields?

**Role-Based Access:**

7. **Who can create/edit services?**
   - Product Manager: Create/edit services
   - Operations Manager: Edit pricing?
   - Marketing: Edit description/photos?
   - Or single "Product Catalog Manager" role does all?

8. **Who can view service catalog?**
   - Customers: View active services only (filtered by zip code)
   - Admins: View all services (including inactive/coming soon)
   - Contractors: View services (to know what they might be assigned)

**Output:** Ad-hoc service catalog data model specification

---

### INSERT INTO "Part 3: Content Management System"

#### **DATA DISCOVERY: DIY Content Entity**

**This is NEW data - does not exist today**

1. **Content types:**
   - Article (blog post format - rich text)
   - Video (embedded or hosted?)
   - PDF (downloadable document)
   - Step-by-step wizard (interactive troubleshooting)
   - FAQ (question + answer pairs)
   - Each type has different data model?

2. **Content data fields:**

   **Required (all content types):**
   - [ ] Content ID (UUID)
   - [ ] Content type (article, video, PDF, wizard, FAQ)
   - [ ] Title
   - [ ] Status (draft, published, archived)
   - [ ] Created date/time
   - [ ] Created by (user ID)
   - [ ] Published date/time (if published)
   - [ ] Last updated date/time
   - [ ] Updated by (user ID)

   **For Articles:**
   - [ ] Body content (rich text - HTML or Markdown?)
   - [ ] Featured image (URL to image in S3?)
   - [ ] Inline images (multiple images in body)
   - [ ] Reading time estimate (calculated from word count?)
   - [ ] Author name/bio

   **For Videos:**
   - [ ] Video URL (YouTube embed? Vimeo? Self-hosted on AWS?)
   - [ ] Video thumbnail (custom or auto-generated?)
   - [ ] Video duration
   - [ ] Video transcript (for accessibility and SEO)

   **For PDFs:**
   - [ ] PDF file (stored in S3)
   - [ ] File size
   - [ ] Number of pages

   **For Step-by-Step Wizards:**
   - [ ] Steps (JSON array of step objects?)
   - [ ] Each step: Question + Answer options + Next step logic

3. **Content organization:**

   **Categories/Tags:**
   - [ ] Primary category (HVAC, plumbing, electrical, appliances, general home maintenance)
   - [ ] Sub-category (troubleshooting, maintenance, safety, how-to, installation)
   - [ ] Tags (multiple tags per content - array or separate tags table?)
   - [ ] Related appliance types (e.g., "water heater" tag links to home inventory categories)
   - [ ] Difficulty level (beginner, intermediate, advanced - affects search/recommendations)

4. **SEO & Discoverability:**
   - [ ] SEO title (different from display title?)
   - [ ] SEO description (meta description)
   - [ ] SEO keywords
   - [ ] URL slug (for SEO-friendly URLs: /diy/how-to-fix-leaky-faucet)

5. **Content relationships:**
   - Can content be related to other content?
     - "Related articles" (many-to-many relationship)
     - "Next in series" (sequential content)
     - How stored? (separate ContentRelationships table?)

6. **Content versioning:**
   - When content is updated, keep old version?
   - Version history table? (content ID, version number, content snapshot, updated date)
   - Ability to revert to previous version?

7. **Content approval workflow:**
   - Status field: Draft → Pending Review → Approved → Published?
   - Or simpler: Draft → Published?
   - Who approved? (approved by user ID, approved date)
   - Approval comments/notes?

8. **Content scheduling:**
   - Publish on future date?
   - Publish date field (if in future, content not visible to customers yet)
   - Automated publishing job (cron job checks for content with publish date = today)

9. **Content expiration:**
   - Auto-archive after certain date?
   - Expiration date field?
   - Use case: seasonal content, outdated information

10. **Content analytics:**
    - View count (how many customers viewed this content?)
    - Time on page (average - requires analytics tracking)
    - Helpfulness ratings (thumbs up/down or 1-5 stars)
    - Number of ratings
    - Customer comments (separate Comments table? Or just ratings?)

**Multilingual Content:**

11. **Spanish translation:**
    - If Spanish localization is MVP:
      - Single content record with multiple language versions? (Content table has English + Spanish columns?)
      - Or separate content records per language? (Content table has language field, multiple records for same content)
    - Translation workflow? (English content → translate → review → publish Spanish version)
    - Translation status tracking?

**Media Storage:**

12. **Where are images/videos/PDFs stored?**
    - AWS S3?
    - CDN for faster delivery?
    - File naming convention?
    - Max file sizes?

**Role-Based Access:**

13. **Who can create content?**
    - Content Manager role: Create/edit/publish
    - Marketing role: Create/edit drafts, but cannot publish?
    - Or single role?

14. **Who can approve content?**
    - If approval workflow exists:
      - Content Manager can approve?
      - Or separate Content Approver role?
      - Legal team approval required for certain content?

15. **Who can delete/archive content?**
    - Content Manager: Archive content
    - Super Admin: Delete permanently
    - Audit log for deletions

**Output:** DIY content data model specification with field list, content types, and approval workflow

---

## For Session 3: Contractor Discovery

### INSERT INTO "Part 1: Current Contractor Experience"

#### **DATA DISCOVERY: Contractor Entity**

1. **Where is contractor data stored TODAY?**
   - Dynamics?
   - Contractor Engagement Portal (separate database)?
   - Both (synced)?

2. **Can we see contractor data fields?**
   - Screen share contractor portal or Dynamics
   - What fields exist today?
   - What's missing that we need?

3. **Contractor credentials data:**
   - License numbers: How stored? (single field or multiple if multi-trade?)
   - License expiration: Single date or multiple dates per license type?
   - Insurance: Certificate on file (PDF upload)? Expiration date tracked?
   - Background check: Status (pass/fail/pending)? Date performed? Expiration (annual renewal)?
   - Certifications: Free-text list or structured data?

4. **Contractor availability data:**
   - Is availability tracked today?
   - If yes: How? (calendar system, available hours per day, blocked dates?)
   - If no: How SHOULD it be tracked?
     - Work schedule: Monday-Friday 8am-5pm (standard hours)
     - Exceptions: Vacation days, holidays, sick days
     - Max capacity: Maximum jobs per day (e.g., 3 jobs/day)
     - Current load: How many active jobs (to avoid overloading contractor)

5. **Contractor performance data:**
   - Is performance tracked today?
   - What metrics? (jobs completed, on-time %, customer ratings, response time?)
   - Where stored? (Dynamics, contractor portal, not tracked?)

**Output:** Contractor data model specification

---

### INSERT INTO "Part 2: Contractor Matching Algorithm"

#### **DATA DISCOVERY: Contractor Specializations & Service Areas**

1. **Contractor specializations:**
   - How is specialization tracked today?
     - Single trade per contractor? (Contractor A = HVAC only)
     - Multiple trades per contractor? (Contractor B = HVAC + Plumbing)
   - If multiple trades, how stored?
     - Free-text field: "HVAC, Plumbing, Electrical" (hard to query)
     - Separate specializations table: ContractorSpecializations (contractor ID, trade type) (better)
   - Trade types: What are the options?
     - HVAC, Plumbing, Electrical, Appliance Repair, General Handyman, Other?
     - Standardized list?

2. **Service area data:**
   - How is service area defined?
     - List of zip codes? (ContractorServiceAreas table: contractor ID, zip code)
     - Radius from contractor location? (contractor address + 25 mile radius)
     - Cities? Counties? States?
   - Can contractor serve multiple non-contiguous areas?
     - E.g., Contractor serves Charlotte AND Raleigh but not cities in between?

3. **Contractor tier (primary/secondary):**
   - From Meeting1:43:35 - "primary contractor, secondary contractor"
   - How is tier tracked?
     - Per zip code? (Contractor A is primary for Charlotte, secondary for Raleigh?)
     - Or global tier? (Contractor A is always primary)
   - What determines tier?
     - Performance? Seniority? Contract terms? Duke decision?

**Matching Algorithm Data Requirements:**

4. **What data is needed to run matching algorithm?**
   - Customer's zip code (from service request)
   - Service type (from service request)
   - Contractor specializations (from contractor record)
   - Contractor service areas (from contractor record)
   - Contractor availability (from contractor record)
   - Contractor current workload (count of active jobs)
   - Contractor tier (primary/secondary)
   - Contractor performance rating (if considered in matching)
   - Customer preference (if customer can request specific contractor)

5. **Matching history:**
   - Should we track matching attempts?
     - Service Request ID + Contractor ID + Offered Date/Time + Accept/Decline + Decline Reason
   - Why important: To improve algorithm over time (which contractors decline which jobs and why)

**Output:** Contractor matching data requirements specification

---

## For Session 4: Integration Architecture & APIs

### INSERT INTO "Part 2: System Architecture Deep Dive"

#### **DATA DISCOVERY: Data Sync & Master Sources**

**For EACH entity, determine:**

1. **Where does data live?** (system of record)
2. **Where else is data copied?** (read replicas)
3. **How is data synced?** (real-time API, batch job, message queue)
4. **What's the master source of truth?** (if conflicts, which system wins)
5. **How often does data change?** (determines sync strategy)

### **Customer Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| Native customer profile | Commerce/Dynamics | App DB | ? | ? |
| Non-native customer profile | App DB | None | N/A | N/A |
| HPP plan enrollment | Commerce/Dynamics | App DB | ? | ? |
| Customer preferences (notifications) | App DB | None | N/A | N/A |
| Home inventory | App DB | None | N/A | N/A |

**Questions for Duke IT:**
- For native customers: Can app read customer data from Commerce via API?
- Real-time or daily batch sync?
- If customer updates email in Commerce, how long until app sees new email?
- If customer updates email in app, can it update Commerce?

### **Service Request Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| HPP service request | Dynamics | App DB | ? | ? |
| Ad-hoc service request | App DB | Dynamics (?) | ? | ? |
| Service status | Dynamics (?) | App DB | ? | Real-time? |
| Customer rating | App DB | Dynamics (?) | ? | ? |

**Questions for Duke IT:**
- When customer books service via app, where is service request created FIRST?
  - Option A: App DB → then synced to Dynamics
  - Option B: Directly in Dynamics via API
- When contractor updates status, where is it updated FIRST?
  - Option A: Contractor portal → Dynamics → App DB
  - Option B: Contractor portal → App DB → Dynamics
  - Option C: Both systems updated directly

### **Contractor Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| Contractor profile | Dynamics | App DB | ? | Daily batch? |
| Contractor availability | Contractor Portal (?) | App DB | ? | Real-time? |
| Contractor performance metrics | Dynamics | App DB | ? | Daily batch? |

**Questions for Duke IT:**
- Can app read contractor list via API? (needed for matching algorithm)
- Can app check contractor availability via API?
- Or does app need local copy of contractor data?

### **HPP Plan Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| HPP plan catalog | Commerce | App DB | API or batch | Weekly? |
| Customer plan enrollment | Commerce | App DB | API or batch | Real-time? |

**Questions for Duke IT:**
- Can app read HPP plan catalog via API?
- Can app check if customer enrolled in specific plan via API? (critical for coverage check)
- How often do HPP plans change? (rarely → batch sync acceptable)

### **Payment Data:**

| Data Point | Master Source | Synced To | Sync Method | Frequency |
|------------|---------------|-----------|-------------|-----------|
| HPP billing | Commerce | App DB (read-only) | API | ? |
| Ad-hoc payment | App DB (SpeedPay) | Accounting system? | ? | ? |

**Questions for Duke IT:**
- For ad-hoc payments: Does transaction data need to sync to Commerce/Dynamics for accounting?
- Or app keeps payment data only?

**Output:** Complete data sync specification with master sources, sync methods, and frequencies

---

## Summary: Critical Data Questions to Answer

### Across All Sessions:

1. **Where does each data entity live TODAY?** (if exists)
2. **What fields/attributes are needed for each entity?**
3. **What's required vs optional?**
4. **What are the relationships between entities?** (customer has many service requests, etc.)
5. **Who can CREATE each entity?** (customer, admin, contractor)
6. **Who can READ each entity?** (what data is visible to whom)
7. **Who can UPDATE each entity?** (edit permissions)
8. **Who can DELETE each entity?** (deletion policies)
9. **What are validation rules?** (required fields, format constraints, business rules)
10. **What are data retention policies?** (how long to keep data, archiving, deletion)
11. **What are data privacy requirements?** (PII encryption, data masking, GDPR/CCPA compliance)
12. **How does data sync between systems?** (if multiple systems have same data)
13. **What's the master source of truth?** (if conflicts, which system wins)

---

**How to Use This Document:**

During workshops, intersperse these data questions into the conversation naturally:
- After discussing a workflow, ask "What data is needed to support this?"
- After understanding a user need, ask "Where does this data live today?"
- After deciding on a feature, ask "Who can see this data? Who can edit it?"

The goal is to walk out of workshops with not just wireframes and workflows, but complete data models and integration specifications.

---

**Document Owner:** Orases Product Management & Technical Team
**Last Updated:** November 5, 2025
**Status:** Ready for workshop use
