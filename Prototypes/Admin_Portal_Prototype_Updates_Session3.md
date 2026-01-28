# Admin Portal Prototype Updates - Session 3 Contractor Discovery
## Duke Energy Residential Solutions

**Date Created:** November 22, 2025
**Purpose:** Clear specification of prototype changes needed based on Session 3 Contractor Discovery decisions
**Reference Documents:**
- `/Workshops/Admin Portal Scope/Admin_Portal_Preliminary_Scope.md`
- `/Workshops/Meetings/Session_3_Contractor_Discovery_meeting.md`
- `/Prototypes/Lovable_Build_Guide.md`

---

## Executive Summary

Based on Session 3 Contractor Discovery meeting, the following changes are required to the Admin Portal prototype:

### Critical Additions Needed:
1. **NEW SCREEN**: Contractor Configuration Management (Critical for MVP)
2. **NEW SCREEN**: Service Request Processing Queue (Manual workflow for MVP)
3. **UPDATE**: Operations Dashboard (add pending confirmation widget)
4. **UPDATE**: Service Request Detail (reflect manual status updates)

### Screens That Remain Unchanged:
✅ Customer Profile (no changes)
✅ Enrollment Queue (no changes)
✅ Customers Page (no changes)
✅ Service Catalog (no changes)
✅ Reminders (no changes)
✅ HPP Plans Management (no changes)

---

## Table of Contents

1. [New Screen 1: Contractor Configuration Management](#new-screen-1-contractor-configuration-management)
2. [New Screen 2: Service Request Processing Queue](#new-screen-2-service-request-processing-queue)
3. [Update Existing: Operations Dashboard](#update-existing-operations-dashboard)
4. [Update Existing: Service Request Detail](#update-existing-service-request-detail)
5. [Navigation Updates](#navigation-updates)
6. [Implementation Order](#implementation-order)

---

## NEW SCREEN 1: Contractor Configuration Management

**Route:** `/contractors`
**Priority:** HIGH (MVP Critical)
**Complexity:** High
**Purpose:** Admin manages contractor data, trade assignments, zip codes, availability buffers for matching algorithm

### Why This Screen is Needed

Session 3 revealed that:
- 125-140 contractors need to be configured in admin backend
- Multi-trade contractors have different availability per trade
- Matching algorithm depends on admin-configured data (trade + zip + primary/secondary + lead time)
- No contractor portal rebuild for MVP, so admin manages all contractor configuration

### Screen Layout

```
Header:
├── Title: "Contractor Management"
├── Subtitle: "Configure contractor matching algorithm (trade, zip codes, availability)"
└── "Add New Contractor" button (primary blue)

Summary Stats (4 KPI cards):
├── Total Contractors: 127
├── Primary Contractors: 102 (80%)
├── Backup Contractors: 25 (20%)
└── Coverage: 99.5%

Filters Section:
├── Search (by name, company, contractor ID)
├── Trade Filter (All, HVAC, Plumbing, Electrical, Water Heater, Appliance)
├── Status Filter (All, Active, Inactive)
└── Territory Filter (NC, SC, FL, OH, IN)

Contractors Table:
├── Contractor ID
├── Contractor Name/Company
├── Trades (badges for multiple)
├── Service Areas (zip code count)
├── Primary/Secondary (badge)
├── Status (Active/Inactive toggle)
└── Actions (Edit, View Details, Deactivate)
```

### Lovable Build Prompts

#### Prompt 1: Contractor Management Page - Header & Stats
```
Create a new page called Contractor Management (/contractors):

HEADER SECTION:
- Title: "Contractor Management"
- Subtitle: "Configure contractor data for matching algorithm (trade, zip codes, availability buffers)"
- "Add New Contractor" button (primary #0066CC, plus icon)

SUMMARY STATS (4 KPI cards in grid):

Card 1 - Total Contractors:
- Number: 127
- Icon: Users (blue)
- Subtitle: "In network"
- Trend: "+2 this quarter" (green)
- Left border: 4px blue

Card 2 - Primary Contractors:
- Number: 102
- Icon: Star (gold)
- Subtitle: "80% primary, first assigned"
- Left border: 4px gold

Card 3 - Backup Contractors:
- Number: 25
- Icon: Shield (purple)
- Subtitle: "20% backup, overflow"
- Left border: 4px purple

Card 4 - Coverage:
- Number: 99.5%
- Icon: MapPin (green)
- Subtitle: "Service area coverage"
- Left border: 4px green

Use Duke Energy colors (#0066CC), Tailwind CSS, Lucide React icons.
Grid: grid-cols-4 gap-4.
```

#### Prompt 2: Contractor Management - Filters & Table
```
Continue Contractor Management page:

FILTERS SECTION (white card, grid-cols-4):

Column 1 - Search:
- Input with search icon
- Placeholder: "Search by name, company, or ID"

Column 2 - Trade Filter:
- Dropdown: "All Trades"
- Options: All Trades, HVAC, Plumbing, Electrical, Water Heater, Appliance

Column 3 - Status Filter:
- Dropdown: "All Status"
- Options: All Status, Active, Inactive, On Hold

Column 4 - Territory Filter:
- Dropdown: "All States"
- Options: All States, North Carolina, South Carolina, Florida, Ohio, Indiana

"Clear Filters" button if any filter active.

CONTRACTORS TABLE (white card):

Header:
- Title: "Contractors (127 total)"
- Right side:
  * "Export" button (file-download icon)
  * "Refresh" button (rotate icon)

Table columns:
1. Contractor ID (monospace, sortable)
2. Name / Company (bold name, gray company below)
3. Trades (multiple badges with icons)
4. Service Areas (count badge: "23 zip codes")
5. Primary / Backup (badge per trade)
6. Status (toggle switch: Active/Inactive)
7. Actions (3-dot menu)

Sample rows (10 contractors):

Row 1:
- ID: CNTR-001
- Name: Mike Thompson
- Company: Carolina Comfort Services
- Trades: 2 badges (HVAC blue, Plumbing teal)
- Service Areas: "32 zip codes" (gray badge)
- Primary: "Primary HVAC" (blue badge)
- Status: Active (toggle ON, green)
- Actions: Edit, View Config, Deactivate

Row 2:
- ID: CNTR-012
- Name: Sarah Johnson
- Company: Triangle Plumbing & Electric
- Trades: 3 badges (Plumbing teal, Electrical yellow, Water Heater red)
- Service Areas: "18 zip codes"
- Primary: "Primary Plumb" (teal badge), "Backup Elec" (yellow badge with "B")
- Status: Active
- Actions: (same)

Row 3:
- ID: CNTR-045
- Name: ABC Electric Services
- Company: ABC Electric Services LLC
- Trades: 1 badge (Electrical yellow)
- Service Areas: "45 zip codes"
- Primary: "Backup Elec" (yellow badge with "B")
- Status: Active
- Actions: (same)

Row 4:
- ID: CNTR-023
- Name: Best HVAC Solutions
- Company: Best HVAC Solutions Inc
- Trades: 1 badge (HVAC blue)
- Service Areas: "28 zip codes"
- Primary: "Primary HVAC" (blue badge)
- Status: Active
- Actions: (same)

Row 5:
- ID: CNTR-067
- Name: Quick Fix Appliance
- Company: Quick Fix Appliance Repair
- Trades: 1 badge (Appliance green)
- Service Areas: "15 zip codes"
- Primary: "Primary Appl" (green badge)
- Status: Inactive (toggle OFF, gray)
- Actions: Edit, View Config, Activate

(Add 5 more rows with varied data)

Actions menu:
- Edit Contractor (opens edit modal)
- View Configuration (expands row to show details)
- View Service Areas (opens zip code list)
- Change Status (activate/deactivate)

Table features:
- Sortable columns
- Hover state
- Click row: expands to show detailed configuration
- Status toggle: quick activate/deactivate
- Badge colors match trade types

Use alternating row colors, hover effects, responsive design.
```

#### Prompt 3: Contractor Management - Create/Edit Modal
```
Create modal for adding/editing contractors:

MODAL: "Add New Contractor" or "Edit Contractor"
- Large modal (900px max width)
- Multi-tab form (3 tabs with progress indicator)
- Scrollable content

TAB 1 - BASIC INFORMATION:

Section: Contractor Details
1. Contractor ID:
   - Input (auto-generated for new, read-only for edit)
   - Example: "CNTR-128"
   - Monospace font

2. Contractor Name:
   - Input (required)
   - Placeholder: "John Smith"

3. Business Name:
   - Input (required)
   - Placeholder: "Smith HVAC Services LLC"

4. Contact Phone:
   - Input with phone format
   - Placeholder: "(919) 555-0123"

5. Contact Email:
   - Input
   - Placeholder: "dispatch@smithhvac.com"

6. Primary Contact:
   - Input
   - Placeholder: "Name of main contact"

7. Status:
   - Radio buttons: Active, Inactive, On Hold
   - Default: Active

Section: Credentials & Insurance
8. Licensing Information:
   - Textarea
   - Placeholder: "License numbers and expiration dates"
   - Example: "NC HVAC License #12345, exp 12/31/2026"

9. Insurance:
   - Input: Certificate number
   - Date picker: Expiration date
   - Checkbox: "$2M liability minimum verified"

10. Background Checks:
    - Checkbox: "All technicians background checked"
    - Date: Last verification date

"Continue to Trades & Service Areas" button (blue, right arrow icon)

TAB 2 - TRADES & SERVICE AREAS:

For EACH Trade (can add multiple):

Trade Configuration Panel (expandable/collapsible):

Header: "Trade 1: HVAC" (dropdown to change trade type)
- Dropdown: Select Trade (HVAC, Plumbing, Electrical, Water Heater, Appliance)
- Delete button (x icon, red)

Fields per trade:
1. Primary/Secondary Designation:
   - Radio buttons PER ZIP CODE or GLOBAL
   - If GLOBAL: Radio buttons (Primary, Secondary)
   - If PER ZIP: Shows zip code list with P/S toggle per zip

2. Service Area (Zip Codes):
   - Multi-select tag input
   - Placeholder: "Enter zip codes (e.g., 28201, 28202)"
   - Tags appear as chips
   - Example: 28201, 28202, 28203, 28204, 28205
   - "Import from CSV" button

3. Lead Time Buffer:
   - Number input + dropdown (business days)
   - Example: "2 business days"
   - Helper text: "Minimum advance notice needed"

4. Availability:
   - Work Days: Checkboxes (Mon, Tue, Wed, Thu, Fri, Sat, Sun)
   - Time Windows: Multi-select
     * "8am-12pm", "1pm-5pm", "Full Day", "Custom"
   - If Custom: Time picker start/end

5. Max Jobs Per Day:
   - Number input
   - Example: "3"
   - Helper text: "Capacity limit per day"

"+ Add Another Trade" button (blue)

Examples:

Trade 1: HVAC
- Primary for: 28201, 28202, 28203
- Buffer: 2 days
- Days: Mon-Fri
- Windows: 8-12, 1-5
- Max jobs: 3

Trade 2: Plumbing
- Primary for: 28201, 28202
- Secondary for: 28203, 28204
- Buffer: 3 days
- Days: Tue, Thu only
- Windows: 9-12, 1-4
- Max jobs: 2

"Continue to Review" button

TAB 3 - REVIEW & SAVE:

Summary sections:

Section 1: Contractor Information
- Display all basic info in read-only format
- "Edit" link goes back to Tab 1

Section 2: Trade Configurations
- Display each trade with:
  * Trade name with icon
  * Primary/Secondary per zip list
  * Service areas (zip codes)
  * Lead time, availability, capacity
- "Edit" link goes back to Tab 2

Section 3: Quick Stats Preview:
- Total zip codes covered: 32
- Trades offered: 2
- Estimated weekly capacity: 30 jobs

MODAL FOOTER:
- "Cancel" button (left, secondary)
- "Save as Inactive" button (secondary)
- "Save & Activate" button (primary blue, check icon)

Validation:
- Required fields highlighted if missing
- Zip code format validation
- At least one trade required
- Primary/secondary must be set for all zip codes

After save:
- Close modal
- Refresh table
- Show success toast: "Contractor added successfully"
- If activated: "Contractor is now available for matching algorithm"

Use Duke colors, proper spacing, clear section dividers.
```

#### Prompt 4: Contractor Management - Expanded Row Details
```
When clicking a contractor row, expand it to show detailed configuration:

EXPANDED ROW (slides down below clicked row):

Background: Light gray (#F8F9FA)
Border: Blue left border (4px)

Layout: 3 columns

LEFT COLUMN - Contact & Status:
- Contact Information:
  * Phone: (919) 555-0987 (phone icon, blue link)
  * Email: dispatch@company.com (envelope icon, blue link)
  * Primary Contact: Mike Thompson
- Licensing:
  * NC HVAC #12345 (exp 12/31/2026)
  * NC Plumbing #67890 (exp 06/30/2027)
- Insurance: Verified, expires 12/31/2025
- Background Checks: Current (last checked 11/01/2025)

MIDDLE COLUMN - Trade Configurations:

Trade 1: HVAC (blue badge)
- Role: Primary Contractor
- Service Areas: 32 zip codes
  * Click "View all zip codes" → opens modal with full list
  * Preview: 28201, 28202, 28203, 28204, 28205 +27 more
- Lead Time: 2 business days
- Availability: Mon-Fri, 8am-12pm & 1pm-5pm
- Capacity: Max 3 jobs/day

Trade 2: Plumbing (teal badge)
- Role: Primary for 18 zips, Secondary for 14 zips
- Service Areas: 32 zip codes
  * Primary: 28201, 28202, 28203, +15 more
  * Secondary: 28204, 28205, 28206, +11 more
- Lead Time: 3 business days
- Availability: Tue, Thu only, 9am-12pm & 1pm-4pm
- Capacity: Max 2 jobs/day

RIGHT COLUMN - Performance & Actions:

Performance Stats (last 30 days):
- Jobs Completed: 45
- Acceptance Rate: 96% (43/45 accepted)
- On-Time Rate: 93%
- Avg Rating: 4.8/5.0

Quick Actions:
- "Edit Configuration" button (blue)
- "View Service History" button (white)
- "Override Availability" button (white)
  * Opens modal to block dates or extend buffer temporarily
- "Deactivate Contractor" button (red border)

CLOSE BUTTON:
- Top right: "Collapse" (chevron-up icon)
- Click: collapses row back to normal

Use proper spacing, icon colors match trade colors, responsive layout.
```

---

## NEW SCREEN 2: Service Request Processing Queue

**Route:** `/service-requests/queue`
**Priority:** HIGH (MVP Critical)
**Complexity:** High
**Purpose:** Admin manually processes service requests (contacts contractors, updates app status)

### Why This Screen is Needed

Session 3 revealed:
- Manual admin processing is the MVP approach (no FSM integration)
- Admin must contact contractors within 1 hour of customer booking
- Admin updates app status based on contractor responses (within 24 hours)
- Target 90-95% acceptance rate from contractors
- Need queue management interface for pending confirmations

### Screen Layout

```
Header:
├── Title: "Service Request Processing Queue"
├── Subtitle: "Manual contractor coordination for MVP (Target: Process within 1 hour)"
└── Real-time count: "8 Pending Confirmation" (red badge if any > 1 hour old)

Summary Stats:
├── Pending Confirmation: 8 (red, needs action)
├── Awaiting Contractor Response: 12 (yellow, waiting)
├── Confirmed Today: 15 (green, success)
└── Avg Processing Time: 45 minutes

Queue Table (Priority Order):
├── Time Submitted (oldest first, highlight if > 1 hour)
├── Request ID
├── Customer Name
├── Service Type
├── Assigned Contractor
├── Requested Date/Time
├── Status
└── Actions (Contact Contractor, Mark Confirmed, Reassign)
```

### Lovable Build Prompts

#### Prompt 1: Service Request Queue - Header & Stats
```
Create a new page called Service Request Processing Queue (/service-requests/queue):

HEADER SECTION:
- Title: "Service Request Processing Queue"
- Subtitle: "Manual contractor coordination for MVP (SLA: Process within 1 hour)"
- Real-time badge: "8 Pending Confirmation" (red if any > 1 hour, yellow if all < 1 hour)

SUMMARY STATS (4 KPI cards):

Card 1 - Pending Confirmation:
- Number: 8
- Icon: Clock (red)
- Subtitle: "ACTION REQUIRED"
- Badge: "2 over 1 hour" (red, pulsing)
- Left border: 4px red
- Clickable: filters table to pending only

Card 2 - Awaiting Contractor Response:
- Number: 12
- Icon: MessageCircle (yellow)
- Subtitle: "Contractor contacted, waiting"
- Left border: 4px yellow

Card 3 - Confirmed Today:
- Number: 15
- Icon: CheckCircle (green)
- Subtitle: "Successfully processed"
- Trend: "+3 vs yesterday" (green)
- Left border: 4px green

Card 4 - Avg Processing Time:
- Number: "45m"
- Icon: Hourglass (blue)
- Subtitle: "Per request (target: 60m)"
- Left border: 4px blue

Grid: grid-cols-4 gap-4. Duke colors. Responsive.
```

#### Prompt 2: Service Request Queue - Queue Table
```
Continue Service Request Queue page:

FILTERS (white card, grid-cols-3):

Column 1 - Status:
- Dropdown: "Pending Only" (default)
- Options: All, Pending Confirmation, Awaiting Response, Confirmed

Column 2 - Time Range:
- Dropdown: "Last 24 Hours" (default)
- Options: Last Hour, Last 6 Hours, Last 24 Hours, Last 7 Days

Column 3 - Search:
- Input: "Search by customer or request ID"

QUEUE TABLE (white card):

Header:
- Title: "Processing Queue (20 active requests)"
- Right side:
  * "Refresh" button (rotate icon, blue)
  * Auto-refresh toggle: "Auto-refresh: ON" (updates every 30 seconds)

Table columns:
1. Time Submitted (sortable, default: oldest first)
   - Shows: "15 min ago", "45 min ago", "1h 23m ago"
   - Red background if > 1 hour
   - Red badge: "OVERDUE" if > 2 hours

2. Request ID (monospace)

3. Customer (name + customer ID)

4. Service Type (icon + label)

5. Assigned Contractor (name + phone)

6. Requested Date/Time

7. Status (badge)

8. Time in Queue

9. Actions (buttons)

Sample rows (priority order: oldest first, overdue at top):

Row 1 - OVERDUE (red background):
- Time: 1h 47m ago
- ID: SR-2025-1201
- Customer: Robert Martinez (DKE-789012)
- Type: HVAC Maintenance (blue icon)
- Contractor: Carolina Comfort (919) 555-0987
- Requested: Nov 23, 9am-12pm
- Status: "Pending Confirmation" (yellow badge)
- Queue Time: 1h 47m (RED, bold)
- Actions:
  * "Contact Contractor" button (PRIMARY red)
  * "View Details" link

Row 2 - URGENT (yellow background):
- Time: 58 min ago
- ID: SR-2025-1199
- Customer: Lisa Wong (DKE-234567)
- Type: Water Heater Repair (red icon)
- Contractor: Triangle Plumbing (919) 555-1234
- Requested: Nov 24, 1pm-4pm
- Status: "Pending Confirmation" (yellow badge)
- Queue Time: 58m (ORANGE, bold)
- Actions:
  * "Contact Contractor" button (PRIMARY orange)
  * "View Details" link

Row 3 - Normal:
- Time: 23 min ago
- ID: SR-2025-1198
- Customer: Eleanor Mitchell (DKE-458923)
- Type: Plumbing Service (teal icon)
- Contractor: Quick Fix Plumbing (919) 555-4567
- Requested: Nov 23, 8am-11am
- Status: "Pending Confirmation" (yellow badge)
- Queue Time: 23m
- Actions:
  * "Contact Contractor" button (PRIMARY blue)
  * "View Details" link

Row 4 - Awaiting Response (gray background):
- Time: 2h 15m ago
- ID: SR-2025-1195
- Customer: Michael Chen (PG-345678)
- Type: Electrical Repair (yellow icon)
- Contractor: ABC Electric (919) 555-7890
- Requested: Nov 25, 10am-1pm
- Status: "Awaiting Response" (blue badge)
- Queue Time: 2h 15m (contractor contacted 15m ago)
- Actions:
  * "Follow Up" button (blue)
  * "Try Backup Contractor" button (white)
  * "View Details" link

Row 5 - Awaiting Response:
- Time: 1h 32m ago
- ID: SR-2025-1193
- Customer: Sarah Johnson (DKE-567890)
- Type: Appliance Repair (green icon)
- Contractor: Quick Fix Appliance (919) 555-2345
- Requested: Nov 24, 2pm-5pm
- Status: "Awaiting Response" (blue badge)
- Queue Time: 1h 32m (contractor contacted 32m ago)
- Actions:
  * "Follow Up" button (blue)
  * "Try Backup Contractor" button (white)

Row 6 - Confirmed (green background, collapsed by default):
- Time: 3h 12m ago
- ID: SR-2025-1190
- Customer: David Kim (PG-890123)
- Type: HVAC Tune-Up
- Contractor: Best HVAC (919) 555-6789
- Requested: Nov 22, 9am-12pm
- Status: "Confirmed" (green badge with check icon)
- Queue Time: Processed in 42m
- Actions:
  * "View Details" link

(Add 4 more rows with varied statuses)

Table features:
- Auto-refresh every 30 seconds (with toggle to disable)
- Priority sort: Overdue → Urgent → Normal → Awaiting → Confirmed
- Visual alerts: Red = overdue, Yellow = approaching 1 hour, Green = confirmed
- Click row: expands to show full details
- Actions always visible (not in 3-dot menu)

Use color-coded left borders, clear visual hierarchy, responsive design.
```

#### Prompt 3: Service Request Queue - Contact Contractor Modal
```
Create modal that opens when "Contact Contractor" button clicked:

MODAL: "Contact Contractor - SR-2025-1201"
- Medium modal (700px)
- Shows service request details + contact options

HEADER (blue background):
- Title: "Contact Contractor"
- Subtitle: "Carolina Comfort Services"
- Close X button

CONTENT SECTION 1 - Request Summary:
Display in gray box:
- Request ID: SR-2025-1201
- Customer: Robert Martinez
- Customer Phone: (919) 555-0234
- Service Type: HVAC Annual Maintenance
- Problem: "Annual preventive maintenance for HVAC system"
- Requested Date/Time: November 23, 9am-12pm
- Address: 1847 Elm Street, Durham, NC 27703

CONTENT SECTION 2 - Contractor Information:
Display in white box with blue border:
- Contractor: Carolina Comfort Services
- Contact: Mike Thompson
- Phone: (919) 555-0987 (large, clickable phone link)
- Email: dispatch@carolinacomfort.com (envelope icon, clickable)
- Role: Primary HVAC Contractor
- Typical Response Time: Within 2 hours

CONTENT SECTION 3 - Contact Method:
Radio buttons:
○ Call Contractor (recommended)
○ Email Contractor
○ SMS Contractor

IF "Call Contractor" selected:
- Large button: "Call (919) 555-0987" (phone icon)
- Click: triggers phone call (if supported) or copies number
- Checklist below:
  ☐ Confirmed customer details
  ☐ Confirmed requested date/time
  ☐ Contractor checked schedule
  ☐ Contractor accepted OR proposed alternative

IF "Email Contractor" selected:
- Email template (editable):
  Subject: "New Service Request SR-2025-1201 - Robert Martinez"
  Body:
  """
  Hi Mike,

  We have a new HVAC service request:

  Customer: Robert Martinez
  Phone: (919) 555-0234
  Address: 1847 Elm Street, Durham, NC 27703
  Service: HVAC Annual Maintenance
  Problem: Annual preventive maintenance
  Requested Date/Time: November 23, 9am-12pm

  Can you confirm availability for this time window?
  If not available, please provide alternative times.

  Please respond within 24 hours.

  Thank you,
  Duke Energy Admin Team
  """
- "Send Email" button (blue)

IF "SMS Contractor" selected:
- SMS template (editable, 160 char limit):
  "New service request SR-2025-1201 for Robert Martinez on Nov 23, 9-12pm. HVAC maintenance. Can you confirm? Reply Y/N or alternative time."
- Character count: "127/160"
- "Send SMS" button (blue)

CONTENT SECTION 4 - Next Steps:
After contacting contractor:

Button group (3 options):
1. "Mark as 'Awaiting Response'" (blue button)
   - Updates status to "Awaiting Response"
   - Sets timer (24 hour countdown)
   - Closes modal

2. "Contractor Accepted - Mark Confirmed" (green button)
   - If contractor accepted immediately on call
   - Opens confirmation mini-form:
     * Confirmed Date: [date picker]
     * Confirmed Time: [time picker]
     * Contractor Notes: [textarea]
   - "Save Confirmation" button
   - Updates app status to "Confirmed"
   - Sends notification to customer

3. "Contractor Declined - Try Backup" (red button)
   - If contractor declined
   - Opens backup contractor selector:
     * Dropdown: Select backup contractor
     * Reason for decline: [dropdown: At capacity, Unavailable, Other]
   - "Assign to Backup" button
   - Creates new queue item for backup contractor

MODAL FOOTER:
- "Cancel" button (left)
- "Mark as Contacted" button (right, secondary)

After action:
- Close modal
- Refresh table
- Show success toast: "Contractor contacted, marked as awaiting response"
- If confirmed: "Service request confirmed! Customer notification sent."

Use Duke colors, clear action buttons, proper spacing.
```

#### Prompt 4: Service Request Queue - Update Status Modal
```
Create modal for updating service request status after contractor response:

MODAL: "Update Status - SR-2025-1195"
- Opens when admin receives contractor response (email/call)
- Medium modal (700px)

HEADER:
- Title: "Update Service Request Status"
- Subtitle: SR-2025-1195 - Michael Chen
- Close X

CONTENT SECTION 1 - Current Status:
Display in gray box:
- Status: "Awaiting Contractor Response" (blue badge)
- Contractor Contacted: 15 minutes ago
- Time in Queue: 2h 15m
- Contractor: ABC Electric (Mike Johnson)

CONTENT SECTION 2 - Contractor Response:
Radio buttons (3 options):

OPTION 1: ○ Contractor Accepted (Confirm Original Time)
If selected, show:
- Confirmed Date: November 25, 2025 (read-only, green text)
- Confirmed Time: 10:00 AM - 1:00 PM (read-only, green text)
- Green checkmark icon
- Text: "Contractor confirmed original requested time"

Additional fields:
- Contractor Notes (optional):
  * Textarea
  * Placeholder: "Any special instructions or notes from contractor"
- Estimated Duration:
  * Dropdown: 1 hour, 2 hours, 3 hours, 4+ hours
- Technician Assigned:
  * Input: "Mike Johnson"

Action: "Confirm Booking" button (large, green)

OPTION 2: ○ Contractor Proposed Alternative Time
If selected, show:
- Original Requested: November 25, 10am-1pm (gray strikethrough)
- Contractor's Proposed Time:
  * Date picker: November 26, 2025
  * Time range:
    - Start: 1:00 PM
    - End: 4:00 PM
- Reason for change:
  * Textarea
  * Placeholder: "Why original time doesn't work"

Two sub-options:
Radio buttons:
○ Accept alternative and update customer
○ Try backup contractor for original time

If "Accept alternative":
- "Customer Notification" preview:
  "Your requested time (Nov 25, 10am-1pm) is not available.
   Contractor can service on Nov 26, 1pm-4pm instead.
   Does this work for you?"
- Action: "Send to Customer for Approval" button (blue)

If "Try backup contractor":
- Backup contractor dropdown
- Action: "Assign to Backup for Original Time" button (blue)

OPTION 3: ○ Contractor Declined
If selected, show:
- Decline Reason:
  * Dropdown: "At capacity", "Outside service area", "Contractor unavailable", "Other"
  * If "Other": Textarea for notes
- Acceptance Rate Alert:
  * Yellow warning box: "This contractor's acceptance rate: 87% (below 90% target)"
  * Link: "Flag for review"

Auto-suggests backup contractor:
- "Recommended Backup Contractor:"
  * Card showing: XYZ Electric (backup for this territory)
  * Phone: (919) 555-XXXX
  * "Assign to Backup" button (blue)

CONTENT SECTION 3 - Admin Notes:
- Internal Notes (optional):
  * Textarea
  * Placeholder: "Internal notes, not visible to customer"
  * Example: "Customer prefers morning appointments"

MODAL FOOTER:
- "Cancel" button (left)
- Action button (right, varies by selection):
  * "Confirm Booking" (green) - if accepted
  * "Send to Customer" (blue) - if alternative
  * "Assign to Backup" (blue) - if declined

After save:
- Close modal
- Update queue table
- Show toast notification
- If confirmed: "Request confirmed! Customer notification sent."
- If alternative: "Alternative time sent to customer for approval"
- If backup: "Assigned to backup contractor"

Timeline tracking:
- Record all status changes with timestamp
- Track: Submitted → Contacted → Response Received → Confirmed/Reassigned

Use clear visual states, proper validation, responsive design.
```

---

## UPDATE EXISTING: Operations Dashboard

**Route:** `/` or `/dashboard`
**Changes:** ADD pending confirmation widget

### What Needs to Change

Add a new "Pending Confirmation" queue widget to highlight admin action items.

### Lovable Update Prompts

#### Prompt: Add Pending Confirmation Widget to Dashboard
```
Update the Operations Dashboard (/) to add a new priority widget:

LOCATION: Below KPI cards, above Quick Actions (new top priority section)

NEW WIDGET: Pending Confirmation Queue
- White card with RED left border (4px)
- Header:
  * Title: "Pending Confirmation Queue"
  * Badge: "8 requests" (red, pulsing if any > 1 hour)
  * "View All →" link (right side) goes to /service-requests/queue

Content:
List of top 5 pending requests (sorted by oldest first):

Each item:
- Left: Request ID + Customer Name
- Middle: Time in queue (bold)
  * "58m ago" (orange if > 45 min)
  * "1h 23m ago" (RED if > 1 hour)
- Right: "Process Now" button (blue)

Item 1 (red background if > 1 hour):
- "SR-2025-1201"
- "Robert Martinez"
- "1h 47m ago" (RED, bold)
- "Process Now" button (red)
- HVAC icon (blue)

Item 2 (yellow background if 45m-1h):
- "SR-2025-1199"
- "Lisa Wong"
- "58m ago" (ORANGE, bold)
- "Process Now" button (orange)
- Water heater icon (red)

Item 3:
- "SR-2025-1198"
- "Eleanor Mitchell"
- "23m ago"
- "Process Now" button (blue)
- Plumbing icon (teal)

Item 4:
- "SR-2025-1197"
- "Michael Chen"
- "15m ago"
- "Process Now" button (blue)
- Electrical icon (yellow)

Item 5:
- "SR-2025-1196"
- "David Kim"
- "8m ago"
- "Process Now" button (blue)
- HVAC icon (blue)

If no pending items:
- Show: "✅ No pending confirmations" (green text)
- "All service requests processed!" (gray text)

Click "Process Now":
- Navigates to /service-requests/queue with that request highlighted

Visual priority:
- Red items at top
- Auto-refresh every 30 seconds
- Pulsing animation on red badge if overdue

Insert this widget ABOVE the existing "Quick Actions & Recent Activity" section.

Use Duke colors, clear visual hierarchy, responsive design.
```

---

## UPDATE EXISTING: Service Request Detail

**Route:** `/service-requests/:id`
**Changes:** Update status display and timeline to reflect manual MVP workflow

### What Needs to Change

1. Update possible statuses to MVP set (Pending → Confirmed → Completed)
2. Remove FSM-dependent statuses (En Route, On-Site, Dispatched)
3. Add admin contact log section
4. Update timeline to show manual processing steps

### Lovable Update Prompts

#### Prompt 1: Update Service Request Status Badge Options
```
Update the Service Request Detail page (/service-requests/:id):

CHANGE 1 - Status Badge (top of page):
Remove old statuses:
❌ "Dispatched" (no longer used in MVP)
❌ "En Route" (requires FSM tool, Phase 2)
❌ "On-Site" (requires FSM tool, Phase 2)
❌ "In Progress" (requires FSM tool, Phase 2)

Keep only MVP statuses:
✅ "Pending Confirmation" (yellow badge with clock icon)
✅ "Confirmed" (blue badge with check icon)
✅ "Completed" (green badge with check-circle icon)
✅ "Cancelled" (red badge with x-circle icon)
✅ "Rescheduled" (purple badge with calendar icon)

Update status badge component to only show these 5 statuses.

CHANGE 2 - Add "Admin Processing" section (right sidebar, below Schedule card):

NEW CARD: "Admin Processing"
- Title: "Admin Processing" (user-cog icon)
- Key-value pairs:

* Admin Assigned: Jessica Davis (avatar)
* Status: Confirmed (badge)
* Contractor Contacted: Nov 19, 2:15 PM
* Contractor Response: Nov 19, 3:30 PM (1h 15m)
* Confirmed By: Jessica Davis
* Processing Time: 1h 15m (green if < 2h, red if > 2h)

If status is "Pending Confirmation":
* Show: "⏰ Awaiting contractor response" (yellow text)
* Show: "Contacted 45 minutes ago"
* Show countdown: "Contractor should respond within 15 minutes"

Use consistent card styling, gray labels, bold values.
```

#### Prompt 2: Update Service Request Timeline
```
Update the Status History timeline (right sidebar) on Service Request Detail page:

CHANGE: Replace old automated timeline with manual MVP timeline

OLD TIMELINE (remove):
❌ En Route
❌ On-Site
❌ Dispatched

NEW MVP TIMELINE (5-6 events):

Event 1 (if completed):
- Green dot
- Title: "Completed"
- Time: Nov 19, 2025 at 3:45 PM
- Description: "Contractor marked service as complete. Customer notified."

Event 2 (if confirmed):
- Blue dot
- Title: "Confirmed"
- Time: Nov 19, 2025 at 3:30 PM
- Description: "Contractor accepted appointment. Confirmed for Thursday 9-12am with ABC Plumbing."
- Admin: Jessica Davis (avatar + name)

Event 3:
- Purple dot
- Title: "Contractor Responded"
- Time: Nov 19, 2025 at 3:30 PM
- Description: "ABC Plumbing confirmed availability for requested time window."

Event 4:
- Indigo dot
- Title: "Contractor Contacted"
- Time: Nov 19, 2025 at 2:15 PM
- Description: "Admin contacted ABC Plumbing via phone to confirm appointment."
- Admin: Jessica Davis

Event 5:
- Blue dot
- Title: "Contractor Assigned"
- Time: Nov 19, 2025 at 2:05 PM
- Description: "System assigned primary contractor: ABC Plumbing (Trade: Plumbing, Zip: 28201)"

Event 6 (last):
- Yellow dot
- Title: "Requested"
- Time: Nov 19, 2025 at 2:00 PM
- Description: "Service request created by customer via mobile app."
- No connecting line after this

IF status is "Pending Confirmation":
Add:
Event 4:
- Yellow dot (pulsing)
- Title: "Awaiting Contractor Response"
- Time: In progress (45 minutes)
- Description: "Admin contacted contractor at 2:15 PM. Waiting for response."
- Progress bar: 45m / 24h

Use colored dots matching event type, connecting lines between events.
Show admin name/avatar for manual actions.
```

#### Prompt 3: Add Admin Contact Log Section
```
Add new section to Service Request Detail page (main content area, below "Admin Notes"):

NEW SECTION: "Admin Contact Log"
- Title: "Admin Contact Log" (message-square icon)
- Shows history of all admin-contractor communications

Log Entry 1 (most recent, blue background):
- Header:
  * User icon + "Jessica Davis"
  * Phone icon + "Called contractor"
  * Timestamp: "Nov 19, 2025 at 3:30 PM"
- Content:
  "Called ABC Plumbing (Mike Thompson). Contractor confirmed availability for Thursday 9-12am. Will arrive between 9:00-9:15am. Technician assigned: Mike Thompson. Estimated duration: 2 hours."
- Footer:
  * "Response Time: 1h 15m" (green badge)
  * "Status: Confirmed" (green badge)

Log Entry 2 (gray background):
- Header:
  * User icon + "Jessica Davis"
  * Phone icon + "Called contractor"
  * Timestamp: "Nov 19, 2025 at 2:15 PM"
- Content:
  "Initial contact to ABC Plumbing. Left voicemail requesting callback to confirm Thursday 9-12am appointment for Robert Martinez at 1847 Elm Street."
- Footer:
  * "Method: Phone + Voicemail"

Log Entry 3 (gray background):
- Header:
  * System icon + "System"
  * Assignment icon
  * Timestamp: "Nov 19, 2025 at 2:05 PM"
- Content:
  "Service request auto-assigned to primary contractor: ABC Plumbing (Trade: Plumbing, Territory: 28201)"
- Footer:
  * "Assignment Type: Primary Contractor"

If no logs yet:
- Show: "No contact logs yet. Admin has not contacted contractor."
- If pending: Show warning: "⏰ Admin should contact contractor (SLA: within 1 hour)"

Use timeline-style layout, color-coded by action type, responsive design.
```

---

## NAVIGATION UPDATES

### Update Sidebar Navigation

The sidebar navigation needs to be updated to include the new Contractor Management screen.

#### Prompt: Add Contractor Management to Navigation
```
Update the BaseLayout component sidebar navigation:

CURRENT MENU (8 items):
1. Dashboard → "/" (Home icon)
2. Customers → "/customers" (Users icon)
3. Service Requests → "/service-requests" (ClipboardList icon)
4. Enrollments → "/enrollments" (UserPlus icon)
5. HPP Plans → "/hpp-plans" (Shield icon)
6. Service Catalog → "/catalog" (Wrench icon)
7. Reminders → "/reminders" (Bell icon)
8. Analytics → "/analytics" (BarChart3 icon)

ADD NEW ITEM (insert as #4, shift others down):
4. Contractors → "/contractors" (Users icon with hard-hat badge OR Briefcase icon)
   - Active state: blue background
   - Icon: Users icon OR HardHat icon (use lucide-react)

NEW MENU (9 items):
1. Dashboard → "/" (Home icon)
2. Customers → "/customers" (Users icon)
3. Service Requests → "/service-requests" (ClipboardList icon)
4. Contractors → "/contractors" (HardHat icon) ✨ NEW
5. Enrollments → "/enrollments" (UserPlus icon)
6. HPP Plans → "/hpp-plans" (Shield icon)
7. Service Catalog → "/catalog" (Wrench icon)
8. Reminders → "/reminders" (Bell icon)
9. Analytics → "/analytics" (BarChart3 icon)

Styling:
- Same NavLink component
- Active: bg-duke-blue (#0066CC), text-white
- Inactive: text-gray-700, hover:bg-gray-100
- Icon size: w-5 h-5
- Padding: px-4 py-3
- Border radius: rounded-lg

Also add route in App.tsx:
- /contractors → ContractorManagement page
- /service-requests/queue → ServiceRequestQueue page

Update breadcrumbs if needed.
```

---

## IMPLEMENTATION ORDER

### Priority 1: Critical MVP Features (Build First)
**Timeline: Week 1**

1. ✅ **DAY 1-2**: Contractor Management Page
   - Prompt 1: Header & Stats
   - Prompt 2: Filters & Table
   - Why first: Core matching algorithm depends on this data

2. ✅ **DAY 2-3**: Contractor Management Page (continued)
   - Prompt 3: Create/Edit Modal
   - Prompt 4: Expanded Row Details
   - Test: Create contractor with multiple trades, different zip codes

3. ✅ **DAY 3-4**: Service Request Processing Queue
   - Prompt 1: Header & Stats
   - Prompt 2: Queue Table
   - Why critical: Admin must process requests within 1 hour SLA

4. ✅ **DAY 4-5**: Service Request Processing Queue (continued)
   - Prompt 3: Contact Contractor Modal
   - Prompt 4: Update Status Modal
   - Test: Full workflow from pending → contacted → confirmed

### Priority 2: Dashboard & Detail Updates (Build Second)
**Timeline: Week 2**

5. ✅ **DAY 5**: Update Operations Dashboard
   - Add Pending Confirmation Widget
   - Test: Ensure links to queue work
   - Test: Auto-refresh works

6. ✅ **DAY 6**: Update Service Request Detail
   - Prompt 1: Update Status Badges
   - Prompt 2: Update Timeline
   - Prompt 3: Add Admin Contact Log
   - Test: View completed request with full manual timeline

7. ✅ **DAY 7**: Navigation Updates & Integration Testing
   - Add Contractors to sidebar navigation
   - Add routes in App.tsx
   - Test all navigation flows
   - Test end-to-end workflow

### Priority 3: Polish & Testing (Build Third)
**Timeline: Week 2**

8. ✅ **DAY 7**: Cross-Screen Integration
   - Test: Dashboard → Queue → Contractor Management
   - Test: Queue → Service Detail → Customer Profile
   - Ensure all links work correctly

9. ✅ **DAY 7**: Responsive Design Check
   - Test on mobile/tablet
   - Ensure modals work on small screens
   - Test table horizontal scroll

10. ✅ **DAY 7**: Final QA Pass
    - Test all new features
    - Verify Duke colors throughout
    - Check for console errors
    - Verify loading states
    - Test error handling

---

## TESTING CHECKLIST

### Contractor Management Page
- [ ] Can create new contractor
- [ ] Can add multiple trades to one contractor
- [ ] Can set different primary/secondary per trade
- [ ] Can add zip codes (multi-select tags work)
- [ ] Can set different lead times per trade
- [ ] Can set different availability windows per trade
- [ ] Status toggle works (Active/Inactive)
- [ ] Expanded row shows full configuration
- [ ] Edit modal loads existing data correctly
- [ ] Search/filters work
- [ ] Table is sortable
- [ ] Pagination works

### Service Request Processing Queue
- [ ] Pending requests show oldest first
- [ ] Overdue requests (> 1 hour) are highlighted red
- [ ] "Contact Contractor" opens modal with correct data
- [ ] Can mark as "Awaiting Response"
- [ ] Can mark as "Confirmed" with date/time
- [ ] Can assign to backup contractor
- [ ] Auto-refresh works (every 30 seconds)
- [ ] Queue count updates in real-time
- [ ] Status badges display correctly
- [ ] Time in queue calculates correctly
- [ ] Filters work (status, time range)

### Dashboard Updates
- [ ] Pending Confirmation widget shows correct count
- [ ] Overdue badge appears if requests > 1 hour
- [ ] "Process Now" button navigates to queue
- [ ] "View All →" link works
- [ ] Widget auto-refreshes
- [ ] Shows "No pending" when empty

### Service Request Detail Updates
- [ ] Only shows MVP statuses (5 statuses)
- [ ] Timeline shows manual processing steps
- [ ] Admin names appear in timeline
- [ ] Admin Contact Log shows communication history
- [ ] Admin Processing card shows processing time
- [ ] Processing time is green if < 2h, red if > 2h
- [ ] No FSM-dependent statuses appear

### Navigation
- [ ] Contractors menu item appears in sidebar
- [ ] Clicking Contractors navigates to /contractors
- [ ] Active state highlights correctly
- [ ] All other menu items still work
- [ ] Breadcrumbs update correctly

---

## DATA MODEL UPDATES

### Mock Data File Updates

Update `src/data/mockData.ts` with new data structures:

#### Add Contractors Array
```typescript
export interface Contractor {
  id: string;
  name: string;
  company: string;
  phone: string;
  email: string;
  status: 'active' | 'inactive' | 'on-hold';
  trades: ContractorTrade[];
}

export interface ContractorTrade {
  trade: 'hvac' | 'plumbing' | 'electrical' | 'water-heater' | 'appliance';
  role: 'primary' | 'secondary';
  serviceAreas: string[]; // zip codes
  leadTimeDays: number;
  availability: {
    days: string[]; // ['Monday', 'Tuesday', etc.]
    timeWindows: string[]; // ['8am-12pm', '1pm-5pm']
  };
  maxJobsPerDay: number;
}

export const contractors: Contractor[] = [
  {
    id: 'CNTR-001',
    name: 'Mike Thompson',
    company: 'Carolina Comfort Services',
    phone: '(919) 555-0987',
    email: 'dispatch@carolinacomfort.com',
    status: 'active',
    trades: [
      {
        trade: 'hvac',
        role: 'primary',
        serviceAreas: ['28201', '28202', '28203', '28204', '28205'],
        leadTimeDays: 2,
        availability: {
          days: ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'],
          timeWindows: ['8am-12pm', '1pm-5pm']
        },
        maxJobsPerDay: 3
      },
      {
        trade: 'plumbing',
        role: 'primary',
        serviceAreas: ['28201', '28202'],
        leadTimeDays: 3,
        availability: {
          days: ['Tuesday', 'Thursday'],
          timeWindows: ['9am-12pm', '1pm-4pm']
        },
        maxJobsPerDay: 2
      }
    ]
  },
  // Add 10 more contractors with varied configurations
];
```

#### Add Service Request Queue Array
```typescript
export interface ServiceRequestQueueItem {
  id: string;
  customerId: string;
  customerName: string;
  serviceType: string;
  assignedContractor: {
    id: string;
    name: string;
    phone: string;
  };
  requestedDateTime: {
    date: string;
    timeWindow: string;
  };
  status: 'pending-confirmation' | 'awaiting-response' | 'confirmed';
  submittedAt: string; // ISO timestamp
  contactedAt?: string; // ISO timestamp
  confirmedAt?: string; // ISO timestamp
  adminAssigned: string;
}

export const serviceRequestQueue: ServiceRequestQueueItem[] = [
  {
    id: 'SR-2025-1201',
    customerId: 'DKE-789012',
    customerName: 'Robert Martinez',
    serviceType: 'HVAC Maintenance',
    assignedContractor: {
      id: 'CNTR-001',
      name: 'Carolina Comfort',
      phone: '(919) 555-0987'
    },
    requestedDateTime: {
      date: '2025-11-23',
      timeWindow: '9:00 AM - 12:00 PM'
    },
    status: 'pending-confirmation',
    submittedAt: '2025-11-22T14:13:00Z', // 1h 47m ago
    adminAssigned: 'Jessica Davis'
  },
  // Add 15 more queue items with varied statuses
];
```

---

## SUMMARY OF CHANGES

### What's Being Added:
1. ✅ **Contractor Management Page** (NEW)
   - Full CRUD for contractors
   - Multi-trade configuration
   - Zip code assignments
   - Primary/secondary designation
   - Lead time and availability configuration

2. ✅ **Service Request Processing Queue** (NEW)
   - Manual admin workflow for MVP
   - Pending confirmation queue
   - Contact contractor interface
   - Status update workflow
   - SLA tracking (1 hour)

### What's Being Updated:
3. ✅ **Operations Dashboard**
   - Add pending confirmation widget
   - Priority action items

4. ✅ **Service Request Detail**
   - Update to MVP statuses only
   - Manual processing timeline
   - Admin contact log
   - Remove FSM-dependent features

5. ✅ **Navigation**
   - Add Contractors menu item
   - Update routes

### What's Staying the Same:
- ✅ Customer Profile (no changes)
- ✅ Enrollment Queue (no changes)
- ✅ Customers Page (no changes)
- ✅ Service Catalog (no changes)
- ✅ Reminders (no changes)
- ✅ HPP Plans Management (no changes)
- ✅ Base layout and design system

---

## BUILD ORDER SUMMARY

**Week 1:**
- Days 1-2: Contractor Management (Prompts 1-2)
- Days 2-3: Contractor Management (Prompts 3-4)
- Days 3-4: Service Request Queue (Prompts 1-2)
- Days 4-5: Service Request Queue (Prompts 3-4)

**Week 2:**
- Day 5: Dashboard Updates
- Day 6: Service Request Detail Updates
- Day 7: Navigation + Integration Testing + QA

**Total Effort:** ~7-10 days for complete prototype updates

---

## QUESTIONS TO CLARIFY

Before starting build, confirm:

1. **Data Source**: Where will contractor data come from initially?
   - Import from CSV?
   - Manual entry by admin?
   - API from Duke?

2. **Auto-Refresh**: Should queue auto-refresh?
   - Recommended: Yes, every 30 seconds
   - Toggle to disable?

3. **Notifications**: Should admin receive browser notifications for:
   - New pending confirmations?
   - Overdue requests (> 1 hour)?
   - Contractor responses?

4. **Access Control**: Do different admin roles see different features?
   - Operations Manager: Full access to contractor config + queue
   - CSR: View-only for contractors, can't edit
   - Back Office Admin: Full access

5. **Mobile Support**: Priority for contractor management on mobile?
   - Recommended: Desktop-first for MVP (complex forms)
   - Mobile: Read-only, queue processing only

---

**Document Version:** 1.0
**Created:** November 22, 2025
**Author:** Orases Product Team
**For:** Duke Energy Admin Portal Prototype Updates

**Next Steps:**
1. Review this document with development team
2. Clarify questions above
3. Begin implementation in priority order
4. Test each feature before moving to next
5. Final QA pass before handoff to Duke team

---

## NAVIGATION IMPROVEMENTS: Service Requests ↔ Queue Linking

**Date Added:** November 22, 2025
**Purpose:** Improve navigation and context switching between Service Requests page and Service Request Queue

### Overview

These prompts add better linking between:
- **Service Requests page** (`/service-requests`) - shows all service requests
- **Service Request Queue** (`/service-requests/queue`) - shows pending confirmation items only

The improvements provide multiple access points, context-aware navigation, and clear visual indicators for pending items that need admin action.

---

### Prompt 1: Add Queue Access Button to Service Requests Page

```
Update the Service Requests page (/service-requests):

Add a prominent "Processing Queue" button in the header section, next to the "Create Service Request" button:

HEADER SECTION (update):
- Title: "Service Requests"
- Subtitle: "Monitor and manage all service requests"
- Right side buttons:
  * "Processing Queue" button (amber/yellow background, Clock icon, LEFT position)
    - Badge showing pending count: "8 pending" (red badge if any > 1 hour)
    - Click: navigates to /service-requests/queue
    - If count is 0: gray background, "Queue Empty"
  * "Create Service Request" button (primary blue, RIGHT position)

Button styling for "Processing Queue":
- Background: #FFC107 (amber) if pending > 0, gray if 0
- Icon: Clock (lucide-react)
- Badge: Small red circle with number (top-right corner of button)
- Hover: slightly darker amber
- Font weight: 600 (semibold)

Also add a status filter chip row ABOVE the table that includes:
- "All Requests" (default, active)
- "Pending Confirmation" (yellow chip, click: filters to pending only + shows link "→ Go to Processing Queue")
- "Confirmed" (blue chip)
- "Completed" (green chip)
- "Cancelled" (red chip)

When "Pending Confirmation" chip is active:
- Show info banner above table: "Showing pending confirmation requests. View full Processing Queue →" (clickable link to /service-requests/queue)
- Info banner: light yellow background, Clock icon, blue link text
```

---

### Prompt 2: Add Breadcrumb Navigation to Queue Page

```
Update the Service Request Processing Queue page (/service-requests/queue):

Add breadcrumb navigation at the very top (above the title):

BREADCRUMB:
- Layout: flex items-center, small text (text-sm), gray color
- Path: Home → Service Requests → Processing Queue
- Format:
  * "Service Requests" (clickable link to /service-requests, blue on hover)
  * "/" separator (gray)
  * "Processing Queue" (current page, bold, dark gray)

Also add a "View All Service Requests" link button in the header:

HEADER (update):
- Title: "Service Request Processing Queue"
- Subtitle: "Manual contractor coordination for MVP (SLA: Process within 1 hour)"
- Right side: "View All Service Requests →" link button
  * Style: secondary button (white background, blue border, blue text)
  * Icon: List icon (lucide-react)
  * Click: navigates to /service-requests

Position breadcrumb 16px above the title, align left.
```

---

### Prompt 3: Add Context Switching in Service Request Detail

```
Update the Service Request Detail page (/service-requests/:id):

Add a context indicator and quick navigation at the top (below the back link):

CONTEXT BANNER (if request status is "Pending Confirmation"):
- Background: light yellow (#FFF9E6)
- Border: 1px solid #FFC107
- Padding: 12px 16px
- Border radius: 8px
- Content:
  * Left: Clock icon (amber), text "This request is in the Processing Queue"
  * Right: "Go to Queue →" button (amber background, white text)
    - Click: navigates to /service-requests/queue with this request highlighted
- Margin bottom: 16px

UPDATE BACK NAVIGATION:
Current: "← Back to Dashboard"
Change to: "← Back to Service Requests" (goes to /service-requests)

But if user came from Queue (track via URL param or state):
Show: "← Back to Processing Queue" (goes to /service-requests/queue)

Implementation:
- Check if URL has query param ?from=queue
- If yes: show "Back to Processing Queue" link
- If no: show "Back to Service Requests" link
```

---

### Prompt 4: Add Quick Access Widget on Dashboard

```
Update the Operations Dashboard (/) Pending Confirmation Widget:

Change the existing widget to have better navigation options:

PENDING CONFIRMATION WIDGET (update):
- Header row:
  * Title: "Pending Confirmation Queue"
  * Badge: "8 requests" (red, pulsing if any > 1 hour)
  * Two links on right:
    1. "View Queue →" (goes to /service-requests/queue)
    2. "All Requests →" (goes to /service-requests)
  * Make links distinct: "View Queue" is primary (blue, bold), "All Requests" is secondary (gray)

Each item in list:
- Click the entire row: navigates to /service-requests/:id?from=queue
  * This preserves context for back navigation
- "Process Now" button: navigates to /service-requests/queue with that request highlighted

Add bottom footer to widget:
- "View all 23 pending requests in queue →" (link to /service-requests/queue)
- Only show if there are more than 5 items (since widget shows top 5)
```

---

### Prompt 5: Add Quick Filter Toggle on Service Requests Page

```
Update the Service Requests page (/service-requests) to add a view toggle:

Add a VIEW TOGGLE section below the status overview cards, above the filters:

VIEW TOGGLE (pill tabs):
- Layout: inline-flex, rounded pill group
- 2 options:

  Tab 1: "All Requests" (List icon)
  - Default active
  - Shows main service requests table

  Tab 2: "Processing Queue Only" (Clock icon)
  - Shows pending confirmation items only
  - Adds badge with count: "8 pending"
  - When active:
    * Filters table to status="Pending Confirmation"
    * Changes sort to: oldest first (by time submitted)
    * Adds yellow background to header
    * Shows banner: "Processing Queue View - Showing pending confirmations only"
    * Adds "Switch to Full Queue →" button (goes to /service-requests/queue page)

Toggle styling:
- Active tab: blue background (#0066CC), white text, shadow
- Inactive tab: white background, gray text, border
- Hover: light blue background
- Border radius: 9999px (pill shape)
- Padding: 8px 16px
- Transition: smooth background/color change

This allows admins to see pending items without leaving the main Service Requests page, but also provides easy access to the full dedicated Queue page.
```

---

### Prompt 6: Add Empty State with Navigation

```
Update both pages to show helpful empty states with navigation:

SERVICE REQUESTS PAGE (/service-requests):
When filter results in 0 items:
- Show: Empty state illustration (Search icon, gray)
- Text: "No service requests found"
- Subtext: "Try adjusting your filters or check the Processing Queue for pending requests"
- Button: "View Processing Queue →" (navigates to /service-requests/queue)

SERVICE REQUEST QUEUE PAGE (/service-requests/queue):
When queue is empty (0 pending):
- Show: Empty state illustration (CheckCircle icon, green)
- Text: "✅ All caught up!"
- Subtext: "No pending confirmations. All service requests have been processed."
- Time indicator: "Last processed: 15 minutes ago"
- Button: "View All Service Requests →" (navigates to /service-requests)
- Small link below: "Refresh queue" (reloads data)

Use Duke Energy colors, proper spacing, centered layout for empty states.
```

---

## Navigation Improvements Summary

### What These Prompts Add:

1. **Multiple Access Points**
   - Dashboard widget with dual links (Queue + All Requests)
   - Service Requests page header button to Queue
   - Queue page header button to All Requests
   - Status filter chips with Queue access

2. **Context-Aware Navigation**
   - Back button changes based on where user came from
   - URL param tracking (?from=queue)
   - Context banner on detail page when item is in queue

3. **Visual Indicators**
   - Live count badges (red if overdue)
   - Status filter chips with colors
   - Empty states with helpful navigation
   - Breadcrumb showing page hierarchy

4. **Quick Filtering**
   - View toggle on Service Requests page
   - Filter to pending without leaving page
   - Easy switch to dedicated Queue page

5. **Improved UX**
   - Clear visual hierarchy
   - Multiple ways to access each view
   - Context preserved during navigation
   - Helpful empty states

### Implementation Order for Navigation Improvements:

**Priority 1 (Critical):**
1. Prompt 1 - Queue button on Service Requests page
2. Prompt 2 - Breadcrumbs on Queue page
3. Prompt 3 - Context-aware back navigation

**Priority 2 (Important):**
4. Prompt 4 - Dashboard widget updates
5. Prompt 5 - View toggle on Service Requests

**Priority 3 (Nice to Have):**
6. Prompt 6 - Empty states

### Testing Checklist for Navigation:

- [ ] Queue button shows correct pending count
- [ ] Queue button badge turns red if requests > 1 hour
- [ ] Breadcrumbs work on Queue page
- [ ] "Back" button changes based on referrer
- [ ] URL param ?from=queue is preserved
- [ ] Context banner appears for pending requests
- [ ] Dashboard widget has both navigation links
- [ ] View toggle filters correctly on Service Requests
- [ ] Status filter chips work
- [ ] Empty states show correct content
- [ ] All navigation links work correctly
- [ ] No broken links or 404 errors

---

**Navigation Improvements Version:** 1.0
**Added:** November 22, 2025
**Ready for Implementation:** Yes

---

## DATA CLEANUP: Remove Phase 2 Statuses from Service Requests Page

**Date Added:** November 23, 2025
**Purpose:** Clean up Service Requests page to only show MVP Phase 1 statuses (remove FSM-dependent statuses)

### Overview

The Service Requests page currently shows Phase 2 statuses that require FSM tool integration (En Route, On-Site, Dispatched, Assigned, In Progress). These need to be removed and replaced with only the 5 MVP Phase 1 statuses.

**MVP Phase 1 Statuses (Keep Only):**
- ✅ Pending Confirmation (yellow)
- ✅ Confirmed (blue)
- ✅ Completed (green)
- ✅ Cancelled (red)
- ✅ Rescheduled (purple)

**Phase 2 Statuses (Remove Completely):**
- ❌ Dispatched
- ❌ En Route
- ❌ On-Site
- ❌ In Progress
- ❌ Assigned

---

### Prompt: Clean Up Service Requests Page - Remove Phase 2 Statuses

```
Update the Service Requests page (/service-requests) to remove Phase 2 statuses and use only MVP Phase 1 statuses:

MVP PHASE 1 STATUSES (keep only these 5):
✅ Pending Confirmation (yellow)
✅ Confirmed (blue)
✅ Completed (green)
✅ Cancelled (red)
✅ Rescheduled (purple)

PHASE 2 STATUSES (remove completely):
❌ Dispatched
❌ En Route
❌ On-Site
❌ In Progress
❌ Assigned

---

CHANGE 1 - STATUS OVERVIEW CARDS (top of page):

REMOVE these cards:
❌ "En Route" card
❌ "On-Site" card
❌ "Assigned" card

KEEP/UPDATE these cards (4 cards total in grid-cols-4):

Card 1 - Pending Confirmation:
- Icon: Clock (yellow)
- Count: 18
- Trend: +3 from yesterday
- Subtitle: "Awaiting contractor response"
- Color: Yellow/amber (#FFC107)
- Click: filters table to "Pending Confirmation"

Card 2 - Confirmed:
- Icon: CheckCircle (blue)
- Count: 32
- Trend: +5 from yesterday
- Subtitle: "Contractor confirmed"
- Color: Blue (#0066CC)
- Click: filters table to "Confirmed"

Card 3 - In Progress Today:
- Icon: Wrench (blue)
- Count: 8
- Subtitle: "Scheduled for today"
- Color: Blue
- Click: filters table to today's date

Card 4 - Completed:
- Icon: CheckCircle (green)
- Count: 45 today
- Trend: +12% vs yesterday
- Subtitle: "Completed today"
- Color: Green (#28A745)
- Click: filters table to "Completed"

Update grid from 5 columns to 4 columns: grid-cols-4 gap-4

---

CHANGE 2 - STATUS FILTER DROPDOWN:

Update the "Status" filter dropdown options:

OLD OPTIONS (remove):
❌ Dispatched
❌ En Route
❌ On-Site
❌ In Progress
❌ Assigned

NEW OPTIONS (keep only):
- All Statuses (default)
- Pending Confirmation
- Confirmed
- Completed
- Cancelled
- Rescheduled

---

CHANGE 3 - SAMPLE DATA IN TABLE:

Update all 10 sample rows to use only MVP statuses:

Row 1:
- ID: SR-2025-1142
- Customer: Eleanor Mitchell (DKE-458923)
- Type: HVAC Maintenance (blue thermometer icon)
- Status: Completed (green badge, CheckCircle icon)
- Contractor: Carolina Comfort
- Date: Nov 15, 2025
- Priority: Normal
- Actions: View

Row 2:
- ID: SR-2025-1139
- Customer: Michael Chen (PG-345678)
- Type: Water Heater Repair (red flame icon)
- Status: Pending Confirmation (yellow badge, Clock icon)
- Contractor: Triangle Plumbing
- Date: Nov 19, 2025 (Today, bold)
- Priority: Urgent (red badge)
- Actions: View + Process

Row 3:
- ID: SR-2025-1138
- Customer: Sarah Johnson (DKE-567890)
- Type: Electrical Issue (yellow zap icon)
- Status: Confirmed (blue badge, CheckCircle icon)
- Contractor: Duke Electric
- Date: Nov 20, 2025
- Priority: Normal
- Actions: View

Row 4:
- ID: SR-2025-1137
- Customer: Robert Davis (DKE-234567)
- Type: Plumbing Emergency (teal droplet icon)
- Status: Confirmed (blue badge, CheckCircle icon)
- Contractor: Quick Fix Plumbing
- Date: Nov 19, 2025 (Today)
- Priority: Urgent (red badge)
- Actions: View

Row 5:
- ID: SR-2025-1136
- Customer: Jennifer Lee (NON-789012)
- Type: HVAC Installation (blue thermometer icon)
- Status: Pending Confirmation (yellow badge, Clock icon)
- Contractor: Best HVAC
- Date: Nov 21, 2025
- Priority: Normal
- Actions: View + Process

Row 6:
- ID: SR-2025-1135
- Customer: David Kim (PG-890123)
- Type: Appliance Repair (green package icon)
- Status: Confirmed (blue badge, CheckCircle icon)
- Contractor: Quick Fix Appliance
- Date: Nov 22, 2025
- Priority: Normal
- Actions: View

Row 7:
- ID: SR-2025-1134
- Customer: Lisa Wong (DKE-456789)
- Type: Water Heater Inspection (red flame icon)
- Status: Completed (green badge, CheckCircle icon)
- Contractor: Triangle Plumbing
- Date: Nov 18, 2025
- Priority: Normal
- Actions: View

Row 8:
- ID: SR-2025-1133
- Customer: Robert Martinez (DKE-789012)
- Type: Electrical Panel Upgrade (yellow zap icon)
- Status: Rescheduled (purple badge, Calendar icon)
- Contractor: ABC Electric
- Date: Nov 25, 2025 (was Nov 20)
- Priority: Normal
- Actions: View

Row 9:
- ID: SR-2025-1132
- Customer: Amanda Brown (DKE-345678)
- Type: Plumbing Leak (teal droplet icon)
- Status: Cancelled (red badge, XCircle icon)
- Contractor: (Unassigned)
- Date: Nov 19, 2025
- Priority: Low
- Actions: View

Row 10:
- ID: SR-2025-1131
- Customer: James Wilson (NON-901234)
- Type: HVAC Tune-Up (blue thermometer icon)
- Status: Pending Confirmation (yellow badge, Clock icon)
- Contractor: Carolina Comfort
- Date: Nov 24, 2025
- Priority: Normal
- Actions: View + Process

---

CHANGE 4 - STATUS BADGE COMPONENT:

Update the StatusBadge component to only render these 5 statuses:

interface StatusBadgeProps {
  status: 'pending-confirmation' | 'confirmed' | 'completed' | 'cancelled' | 'rescheduled';
  size?: 'sm' | 'md';
}

Status badge mapping:
- pending-confirmation: Yellow background (bg-yellow-100), yellow text (text-yellow-700), Clock icon
- confirmed: Blue background (bg-blue-100), blue text (text-blue-700), CheckCircle icon
- completed: Green background (bg-green-100), green text (text-green-700), CheckCircle icon
- cancelled: Red background (bg-red-100), red text (text-red-700), XCircle icon
- rescheduled: Purple background (bg-purple-100), purple text (text-purple-700), Calendar icon

---

CHANGE 5 - CHART DATA (if you have a chart):

If there's a "Service Requests by Status" chart, update it to show only MVP statuses:

Chart data:
const chartData = [
  { name: 'Pending Confirmation', value: 18, color: '#FFC107' },
  { name: 'Confirmed', value: 32, color: '#0066CC' },
  { name: 'Completed', value: 45, color: '#28A745' },
  { name: 'Cancelled', value: 5, color: '#DC3545' },
  { name: 'Rescheduled', value: 8, color: '#8B5CF6' },
];

Total: 108 requests

---

CHANGE 6 - MOCK DATA FILE (if using mockData.ts):

Update the serviceRequests array in mockData.ts to only use these 5 statuses.

Example:
export const serviceRequests = [
  {
    id: 'SR-2025-1142',
    customerId: 'DKE-458923',
    customerName: 'Eleanor Mitchell',
    type: 'hvac',
    category: 'HVAC Maintenance',
    status: 'completed',  // ✅ MVP status
    contractor: { name: 'Carolina Comfort', phone: '(919) 555-0987' },
    scheduledDate: '2025-11-15',
    // ... rest of fields
  },
  // ... more requests with only MVP statuses
];

---

VERIFICATION CHECKLIST:

After making changes, verify:
- [ ] Only 4 status overview cards appear (Pending, Confirmed, In Progress Today, Completed)
- [ ] Status filter dropdown has only 5 status options (+ "All")
- [ ] All table rows show only MVP statuses
- [ ] No "En Route", "On-Site", "Dispatched", "Assigned" appear anywhere
- [ ] StatusBadge component only handles 5 statuses
- [ ] Color coding is consistent (yellow=pending, blue=confirmed, green=completed, red=cancelled, purple=rescheduled)
- [ ] All icons are correct (Clock, CheckCircle, XCircle, Calendar)
- [ ] Chart (if present) shows only MVP statuses

Use Duke Energy colors (#0066CC for blue), Tailwind CSS, Lucide React icons.
```

---

## Data Cleanup Summary

### What This Prompt Does:

1. **Removes 5 Phase 2 Status Cards**
   - En Route
   - On-Site
   - Assigned
   - Dispatched
   - In Progress

2. **Updates to 4 MVP Status Cards**
   - Pending Confirmation (yellow)
   - Confirmed (blue)
   - In Progress Today (blue)
   - Completed (green)

3. **Cleans Up All Sample Data**
   - 10 sample rows updated
   - All use only MVP statuses
   - Realistic distribution across statuses

4. **Updates Status Badge Component**
   - Removes old status options
   - Only renders 5 MVP statuses
   - Correct colors and icons

5. **Updates Filters & Dropdowns**
   - Status filter dropdown cleaned up
   - Chart data (if present) updated
   - Mock data file aligned

### Benefits:

- ✅ Matches MVP Phase 1 scope exactly
- ✅ No confusion with Phase 2 features
- ✅ Consistent with Service Request Detail updates
- ✅ Aligns with manual admin workflow
- ✅ Removes FSM-dependent statuses

### Implementation Priority:

**Critical** - Should be implemented immediately to align prototype with Session 3 decisions.

### Testing:

Use the verification checklist in the prompt to ensure all Phase 2 statuses are removed and only MVP statuses remain.

---

**Data Cleanup Version:** 1.0
**Added:** November 23, 2025
**Ready for Implementation:** Yes

---

## Screen 8: Service Catalog Detail/View Page

### Purpose
Create individual service detail pages that display comprehensive information about each ad-hoc service offering. Currently, the Service Catalog only has a list view with inline create/edit modal. This adds dedicated detail pages accessible by clicking on any service from the catalog table.

### User Story
As an **Operations Manager**, I need to view complete details for any service in the catalog so I can verify pricing, availability, and service configurations before customers see them in the mobile app.

### Current State
- Service Catalog page exists at `/catalog` with services table
- Create/Edit functionality exists only as a modal overlay
- No individual service detail pages
- Clicking a service row does nothing

### New Feature: Service Detail Page
Create a dedicated service detail page at route `/catalog/:serviceId` that displays all service information in an organized, read-only format with navigation to edit mode.

---

### Prompt 1: Service Detail Page - Header & Navigation

**Copy this prompt into Lovable:**

```
Update the Service Catalog table to make service rows clickable and create a new Service Detail page.

PART 1: Make Service Rows Clickable

In the Service Catalog page (src/pages/Catalog.tsx or similar):
- Make each row in the services table clickable
- Add hover effect (bg-gray-50) on row hover
- Add cursor-pointer class to rows
- On row click, navigate to: /catalog/:serviceId
- Use react-router-dom's useNavigate hook

PART 2: Create Service Detail Page Route

Add new route to your router configuration:
- Route path: /catalog/:serviceId
- Component: ServiceDetailPage

PART 3: Create Service Detail Page - Header Section

Create new file: src/pages/ServiceDetailPage.tsx

Header section should include:
1. Back button (← Back to Catalog) linking to /catalog
2. Service name as page title (text-2xl font-bold text-gray-900)
3. Status badge (Active = green bg-green-100 text-green-800, Inactive = gray)
4. Action buttons in top-right:
   - Edit Service (primary blue button #0066CC)
   - Delete Service (secondary red button, outline only)

Layout:
- Use similar structure to Customer Profile page
- White background card with padding
- Header has flex justify-between for title/badge on left, actions on right

Duke Energy Design:
- Primary Blue: #0066CC
- Status Active: bg-green-100 text-green-800 border-green-200
- Status Inactive: bg-gray-100 text-gray-600 border-gray-300
- Use Lucide React icons: ArrowLeft, Edit, Trash2

Sample Data Structure:
Use serviceId from URL params to fetch/filter service data
Mock data should include:
- id, name, category, description
- basePrice, estimatedDuration
- availableInStates (array)
- isActive (boolean)
- createdDate, lastModifiedDate

Verification:
✅ Clicking service row navigates to detail page
✅ Back button returns to catalog list
✅ Service name and status display correctly
✅ Edit and Delete buttons are visible (non-functional for now)
```

---

### Prompt 2: Service Detail Page - Information Tabs

**Copy this prompt into Lovable:**

```
Add tabbed content sections to the Service Detail page to organize service information.

Create 3 tabs below the header:
1. Overview (default active)
2. Pricing & Duration
3. Availability & Settings

Tab Navigation:
- Use state to track active tab
- Horizontal tab buttons below header
- Active tab: blue border-b-2 border-blue-600, text-blue-600
- Inactive tabs: text-gray-600, hover:text-gray-900
- Use Lucide React icons for each tab

TAB 1: Overview
Display these fields in a 2-column grid:

Left Column:
- Service Name (read-only text)
- Category (read-only, with category badge)
- Description (read-only textarea/box, full width below columns)

Right Column:
- Status (Active/Inactive badge)
- Created Date (formatted: MM/DD/YYYY)
- Last Modified Date (formatted: MM/DD/YYYY)

TAB 2: Pricing & Duration
Display:
- Base Price (formatted as currency: $XXX.XX)
- Price Type (Fixed/Variable badge)
- Estimated Duration (e.g., "2-3 hours")
- Additional Cost Notes (if any)

Use info cards with icons:
- DollarSign icon for pricing section
- Clock icon for duration section

TAB 3: Availability & Settings
Display:
- Available in States (comma-separated list or chips)
- Service Window (e.g., "Same-day available" or "2-3 business days")
- Contractor Trades Required (e.g., "HVAC, Plumbing")
- Customer Visibility (Show in App: Yes/No)

Design Specs:
- Each tab content in white card with p-6 padding
- Field labels: text-sm font-medium text-gray-700
- Field values: text-base text-gray-900
- Use grid layout: grid-cols-1 md:grid-cols-2 gap-6
- Description field spans full width

Duke Energy Colors:
- Tab active: #0066CC
- Category badges: Different colors per category (blue, green, purple)
- Info cards: border-l-4 with colored accent

Sample Categories:
- HVAC (blue)
- Plumbing (green)
- Electrical (purple)
- Appliance (orange)

Verification:
✅ All 3 tabs are clickable and switch content
✅ Overview tab shows service name, category, description
✅ Pricing tab shows base price and duration
✅ Availability tab shows states and settings
✅ Layout is responsive (2 columns desktop, 1 column mobile)
```

---

### Prompt 3: Service Detail Page - Activity Log

**Copy this prompt into Lovable:**

```
Add an Activity Log section at the bottom of the Service Detail page to track service changes.

Below all tabs, add "Activity Log" section:

Header:
- "Activity Log" title (text-lg font-semibold)
- Shows last 10 changes to this service

Log Entry Format:
Each log entry displays:
1. User avatar/initials (small circle)
2. Action description (bold text)
   - "created this service"
   - "updated pricing from $150 to $175"
   - "changed status to Active"
   - "added North Carolina to available states"
3. User name (text-sm text-gray-600)
4. Timestamp (text-sm text-gray-500, relative time: "2 hours ago")

Layout:
- Vertical timeline on left with connecting lines
- Use border-l-2 border-gray-200 to create timeline
- Each entry has small dot (w-3 h-3 rounded-full bg-blue-600)
- Entry content in flex row with avatar, text, timestamp

Sample Activity Data:
[
  { user: "Sarah Johnson", action: "updated base price", oldValue: "$150", newValue: "$175", timestamp: "2 hours ago" },
  { user: "Mike Chen", action: "changed status to Active", timestamp: "1 day ago" },
  { user: "Sarah Johnson", action: "created this service", timestamp: "3 days ago" }
]

Design Specs:
- Activity section in separate card below tabs
- Max height: max-h-96 overflow-y-auto (scrollable if many entries)
- Empty state: "No activity recorded yet" with FileText icon

Icons:
- Use Lucide React: User, Clock, Edit icons

Verification:
✅ Activity log appears below all tabs
✅ Timeline connects all entries vertically
✅ Each entry shows user, action, and timestamp
✅ Empty state shows if no activity
✅ Log is scrollable if more than 5-6 entries
```

---

### Prompt 4: Service Detail Page - Edit Mode Navigation

**Copy this prompt into Lovable:**

```
Make the "Edit Service" button functional to navigate to edit mode.

Update the Edit Service button in the header:
1. On click, navigate to: /catalog/:serviceId/edit
2. Button should use primary blue styling (#0066CC)
3. Include Edit icon from Lucide React

Add confirmation for Delete button:
1. On Delete click, show confirmation dialog
2. Dialog: "Are you sure you want to delete this service? This action cannot be undone."
3. Cancel (gray) and Delete (red) buttons
4. On confirm delete:
   - Show success toast: "Service deleted successfully"
   - Navigate back to /catalog

Design Specs:
- Edit button: bg-blue-600 hover:bg-blue-700 text-white
- Delete button: border-red-600 text-red-600 hover:bg-red-50
- Use dialog/modal component (shadcn Dialog or custom modal)

Delete Dialog:
- Title: "Delete Service"
- Description: Warning text
- Two buttons: Cancel (left) and Delete (right, red)

Toast Notification:
- Use toast library or custom toast component
- Success toast: green background with checkmark icon
- Display for 3 seconds

Verification:
✅ Edit button navigates to edit page
✅ Delete button opens confirmation dialog
✅ Cancel in dialog closes without action
✅ Confirm delete removes service and shows toast
✅ After delete, user returns to catalog list
```

---

## Screen 9: Service Catalog Edit Page

### Purpose
Create a dedicated edit page for modifying existing services in the catalog. This provides a full-page editing experience (not modal-based) for comprehensive service configuration.

### User Story
As an **Operations Manager**, I need to edit service details, pricing, and availability so I can keep the service catalog accurate and up-to-date as business requirements change.

### New Feature: Full-Page Service Edit Interface
Create dedicated edit page at route `/catalog/:serviceId/edit` with form validation and save/cancel actions.

---

### Prompt 5: Service Edit Page - Route & Layout Structure

**Copy this prompt into Lovable:**

```
Create a new Service Edit page with full-page form layout.

PART 1: Add Route
Add new route to router configuration:
- Route path: /catalog/:serviceId/edit
- Component: ServiceEditPage

PART 2: Create ServiceEditPage.tsx

Page Structure:
1. Header Section:
   - Back button (← Back to Service Detail) linking to /catalog/:serviceId
   - Page title: "Edit Service"
   - Service status indicator (read-only badge)

2. Form Layout:
   - White card container with padding
   - Form sections divided by horizontal rules
   - Sticky footer with action buttons

3. Action Buttons (bottom of page, sticky):
   - Cancel (gray button, left side) - links back to detail page
   - Save Changes (blue button, right side) - submits form

Header Design:
- Flex container with back button + title on left
- Status badge on right
- Border-bottom separator
- mb-6 margin below header

Form Container:
- max-w-4xl mx-auto (centered, max width)
- bg-white rounded-lg shadow p-6
- Divide form into collapsible or clearly separated sections

Duke Energy Styling:
- Primary Blue: #0066CC for Save button
- Cancel button: border-gray-300 text-gray-700 hover:bg-gray-50

Verification:
✅ Route /catalog/:serviceId/edit is accessible
✅ Back button navigates to service detail page
✅ Page title shows "Edit Service"
✅ Cancel and Save buttons are visible at bottom
```

---

### Prompt 6: Service Edit Page - Basic Information Form

**Copy this prompt into Lovable:**

```
Add the first form section: Basic Information with validation.

Create form section titled "Basic Information" with these fields:

Fields:
1. Service Name (required)
   - Text input, max 100 characters
   - Label: "Service Name *"
   - Validation: Required, min 3 characters
   - Error message: "Service name must be at least 3 characters"

2. Category (required)
   - Dropdown select
   - Options: HVAC, Plumbing, Electrical, Appliance, General Home Repair
   - Label: "Category *"
   - Validation: Required

3. Description (required)
   - Textarea, 4 rows, max 500 characters
   - Label: "Service Description *"
   - Character counter: "450/500 characters"
   - Validation: Required, min 20 characters

4. Status (required)
   - Toggle switch (Active/Inactive)
   - Label: "Service Status"
   - Default: Active
   - Green when Active, Gray when Inactive

Form State Management:
- Use React Hook Form or similar form library
- Initialize with current service data
- Track dirty/touched state for each field

Validation Rules:
- Show error messages below fields (text-red-600 text-sm)
- Validate on blur for each field
- Prevent save if any required field is empty

Layout:
- Use 2-column grid for Name and Category (desktop)
- Description spans full width
- Status toggle on its own row

Design Specs:
- Field labels: text-sm font-medium text-gray-700
- Required fields marked with red asterisk
- Input borders: border-gray-300, focus:border-blue-500
- Section title: text-lg font-semibold text-gray-900 mb-4

Verification:
✅ All 4 fields render correctly
✅ Service Name validation works (required, min 3 chars)
✅ Category dropdown has 5 options
✅ Description has character counter
✅ Status toggle switches between Active/Inactive
✅ Error messages display on validation failure
```

---

### Prompt 7: Service Edit Page - Pricing & Duration Form

**Copy this prompt into Lovable:**

```
Add the second form section: Pricing & Duration.

Create form section titled "Pricing & Duration" with these fields:

Fields:
1. Base Price (required)
   - Number input with $ prefix
   - Label: "Base Price *"
   - Format: Currency (2 decimal places)
   - Validation: Required, min $25, max $5000
   - Error: "Price must be between $25 and $5000"

2. Price Type (required)
   - Radio buttons: Fixed Price / Variable Price
   - Label: "Pricing Type *"
   - Default: Fixed Price
   - Info icon with tooltip: "Fixed = exact price, Variable = estimate range"

3. Estimated Duration (required)
   - Two number inputs side-by-side: Min Hours and Max Hours
   - Label: "Estimated Duration (hours) *"
   - Format: "2 - 3 hours"
   - Validation: Min must be less than Max

4. Additional Cost Notes (optional)
   - Textarea, 2 rows
   - Label: "Additional Cost Notes"
   - Placeholder: "e.g., Parts not included, travel fees may apply"
   - Max 200 characters

Form Behavior:
- Base Price formats as currency on blur (e.g., 150 becomes $150.00)
- Duration displays as range: "2-3 hours"
- Price Type selection affects form behavior (Variable can show range)

Layout:
- Base Price and Price Type in same row (2 columns)
- Duration fields: two inputs side by side with hyphen between
- Additional Cost Notes spans full width

Design Specs:
- Currency input: pl-7 (padding for $ symbol)
- Radio buttons: flex gap-4, horizontal layout
- Duration inputs: w-20 each (small width)
- Info tooltip: Lucide Info icon with hover popover

Icons:
- DollarSign icon next to "Pricing & Duration" section title

Verification:
✅ Base Price formats as currency
✅ Price Type radio buttons work
✅ Duration validation ensures min < max
✅ Additional Cost Notes textarea is optional
✅ All validations trigger on blur/submit
```

---

### Prompt 8: Service Edit Page - Availability & Settings Form

**Copy this prompt into Lovable:**

```
Add the third form section: Availability & Settings.

Create form section titled "Availability & Settings" with these fields:

Fields:
1. Available in States (required)
   - Multi-select checkbox list
   - Label: "Service Available In *"
   - States: North Carolina, South Carolina, Florida, Indiana, Ohio
   - At least 1 state must be selected
   - Show selected count: "3 states selected"

2. Service Window (required)
   - Dropdown select
   - Label: "Typical Service Window *"
   - Options:
     - "Same Day (within 4-8 hours)"
     - "Next Business Day"
     - "2-3 Business Days"
     - "1 Week"
     - "Custom/Scheduled"

3. Required Contractor Trades (required)
   - Multi-select checkboxes
   - Label: "Contractor Trade Requirements *"
   - Options: HVAC, Plumbing, Electrical, Appliance Repair, General Contractor
   - At least 1 trade must be selected

4. Customer Visibility (required)
   - Toggle switch
   - Label: "Show in Customer App"
   - Default: ON (true)
   - Description below: "When enabled, customers can book this service in the mobile app"

Form Validation:
- States: At least 1 must be selected
- Service Window: Required selection
- Trades: At least 1 must be selected
- Customer Visibility: Always has value (toggle)

Layout:
- States: Grid of checkboxes (2 columns)
- Service Window: Full width dropdown
- Trades: Horizontal checkbox list
- Customer Visibility: Toggle with description text below

Design Specs:
- Checkboxes: Lucide Check icon when selected, blue border
- Selected count badge: bg-blue-100 text-blue-800 px-2 py-1 rounded
- Toggle: Same styling as Status toggle (green when ON)
- Description text: text-sm text-gray-600 mt-1

Icons:
- MapPin icon next to "Availability & Settings" section title

Verification:
✅ State checkboxes allow multiple selections
✅ Selected count updates dynamically
✅ Service Window dropdown works
✅ Trade checkboxes allow multiple selections
✅ Customer Visibility toggle works with description
✅ Validation requires at least 1 state and 1 trade
```

---

### Prompt 9: Service Edit Page - Save & Cancel Logic

**Copy this prompt into Lovable:**

```
Implement Save and Cancel functionality with validation and user feedback.

PART 1: Save Changes Button Logic

On "Save Changes" click:
1. Validate all form fields
2. If validation fails:
   - Scroll to first error field
   - Show error toast: "Please fix validation errors"
   - Highlight error fields in red
3. If validation passes:
   - Show loading state on button ("Saving...")
   - Simulate API call (setTimeout 1 second)
   - On success:
     - Show success toast: "Service updated successfully"
     - Navigate to detail page: /catalog/:serviceId
   - On error:
     - Show error toast: "Failed to save changes"
     - Keep user on edit page

PART 2: Cancel Button Logic

On "Cancel" click:
1. Check if form is dirty (has unsaved changes)
2. If dirty:
   - Show confirmation dialog: "You have unsaved changes. Are you sure you want to cancel?"
   - Cancel (stay) / Discard (leave) buttons
3. If not dirty:
   - Navigate directly to detail page: /catalog/:serviceId

PART 3: Browser Back Button Protection

Add unsaved changes warning:
- Use beforeunload event listener
- Prompt user if they try to leave page with unsaved changes
- Message: "You have unsaved changes. Are you sure you want to leave?"

Design Specs:

Save Button:
- bg-blue-600 hover:bg-blue-700 text-white
- Loading state: opacity-50 cursor-not-allowed
- Loading text: "Saving..." with spinner icon

Cancel Button:
- border-gray-300 text-gray-700 hover:bg-gray-50

Confirmation Dialog:
- Title: "Discard Changes?"
- Message: "You have unsaved changes that will be lost."
- Two buttons: "Stay on Page" (gray) / "Discard Changes" (red)

Toast Notifications:
- Success: bg-green-600 text-white, 3 seconds
- Error: bg-red-600 text-white, 5 seconds
- Info: bg-yellow-600 text-white, 3 seconds

Form Dirty Detection:
- Compare current form values to initial values
- Set isDirty flag to true when any field changes

Verification:
✅ Save validates form before submitting
✅ Success toast shows and navigates on successful save
✅ Cancel prompts if there are unsaved changes
✅ Cancel navigates immediately if no changes
✅ Browser back button prompts for unsaved changes
✅ Loading state shows during save operation
✅ Error toast shows if save fails
```

---

### Prompt 10: Service Edit Page - Audit Trail Display

**Copy this prompt into Lovable:**

```
Add a read-only "Edit History" section at the bottom of the edit page.

Below all form sections, add "Edit History" section:

Section Header:
- "Edit History" title (text-lg font-semibold)
- Collapsible section (collapsed by default)
- ChevronDown icon rotates when expanded

History Content (when expanded):
Display last 5 edits to this service:

Each entry shows:
1. User name and avatar
2. Fields changed (e.g., "Base Price, Service Window")
3. Old value → New value (for each field)
4. Timestamp (formatted: "MM/DD/YYYY at HH:MM AM/PM")

Example Entry:
---
Sarah Johnson
Changed: Base Price, Status
- Base Price: $150.00 → $175.00
- Status: Inactive → Active
11/23/2025 at 2:30 PM
---

Layout:
- Each entry in bordered card with p-4 padding
- Gray background for old values, green background for new values
- Timeline connector dots on left side (same as Activity Log)

Design Specs:
- Collapsible section: uses disclosure/accordion component
- History cards: border-l-4 border-blue-600
- Changed fields: text-sm font-medium text-gray-700
- Values: inline code style (bg-gray-100 px-2 py-1 rounded)
- Old value: text-red-600, New value: text-green-600

Sample History Data:
[
  {
    user: "Sarah Johnson",
    changes: [
      { field: "Base Price", oldValue: "$150.00", newValue: "$175.00" },
      { field: "Status", oldValue: "Inactive", newValue: "Active" }
    ],
    timestamp: "2025-11-23T14:30:00"
  },
  {
    user: "Mike Chen",
    changes: [
      { field: "Available States", oldValue: "NC, SC", newValue: "NC, SC, FL" }
    ],
    timestamp: "2025-11-22T10:15:00"
  }
]

Empty State:
- If no history: "No edit history available"
- Icon: Clock with slash-through

Verification:
✅ Edit History section is collapsible
✅ Expands to show last 5 edits
✅ Each entry shows user, changes, and timestamp
✅ Old/new values are color-coded (red/green)
✅ Empty state shows if no history
✅ Section stays collapsed by default
```

---

### Implementation Notes

**Navigation Flow:**
1. Service Catalog List (`/catalog`) → Click row → Service Detail (`/catalog/:serviceId`)
2. Service Detail → Click Edit → Service Edit (`/catalog/:serviceId/edit`)
3. Service Edit → Save → Back to Service Detail
4. Service Edit → Cancel → Back to Service Detail
5. Service Detail → Back → Service Catalog List

**Data Model Integration:**
These pages should integrate with the Service Catalog data model defined in Admin Portal Scope:
- `id`, `name`, `category`, `description`
- `basePrice`, `priceType`, `estimatedDuration`
- `availableStates[]`, `serviceWindow`, `requiredTrades[]`
- `isActive`, `showInCustomerApp`
- `createdDate`, `lastModifiedDate`, `lastModifiedBy`

**Duke Energy Design Consistency:**
- Primary Blue: #0066CC
- Success Green: #28A745
- Warning Yellow: #FFC107
- Danger Red: #DC3545
- All forms use consistent label/input styling
- Status badges match existing admin portal patterns
- Use Lucide React icons throughout

**Responsive Design:**
- Desktop: 2-column form layout where appropriate
- Tablet: Single column forms, full width
- Mobile: Stacked layout, full-width buttons

**Testing Checklist:**
- [ ] Service row clicks navigate to detail page
- [ ] All 3 tabs display correct information
- [ ] Edit button navigates to edit page
- [ ] Delete button shows confirmation dialog
- [ ] Form validation works for all required fields
- [ ] Save updates service and shows success toast
- [ ] Cancel prompts if unsaved changes exist
- [ ] Activity/Edit history displays correctly
- [ ] Navigation flow works: list → detail → edit → detail → list
- [ ] All Duke Energy colors are correct

---

**Version:** 1.0
**Added:** November 24, 2025
**Status:** Ready for Implementation
**Dependencies:** Existing Service Catalog list page (Screen 7)

---

## Screen 10: Reminder Detail/View Page

### Purpose
Create individual reminder detail pages that display comprehensive information about each maintenance reminder configuration. Currently, the Reminders page (Screen 8) only has a list view with inline create/edit modal. This adds dedicated detail pages accessible by clicking on any reminder from the reminders table.

### User Story
As an **Operations Manager**, I need to view complete details for any maintenance reminder so I can verify frequency settings, notification content, recipient targeting, and performance metrics before reminders are sent to customers.

### Current State
- Reminders page exists at `/reminders` with reminders table
- Create/Edit functionality exists only as a modal overlay
- No individual reminder detail pages
- Clicking a reminder row opens edit modal

### New Feature: Reminder Detail Page
Create a dedicated reminder detail page at route `/reminders/:reminderId` that displays all reminder information, performance analytics, and notification preview in an organized, read-only format.

---

### Prompt 1: Reminder Detail Page - Header & Navigation

**Copy this prompt into Lovable:**

```
Update the Reminders table to make reminder rows clickable and create a new Reminder Detail page.

PART 1: Make Reminder Rows Clickable

In the Reminders page (src/pages/Reminders.tsx or similar):
- Make each row in the reminders table clickable
- Add hover effect (bg-gray-50) on row hover
- Add cursor-pointer class to rows
- On row click, navigate to: /reminders/:reminderId
- Use react-router-dom's useNavigate hook

PART 2: Create Reminder Detail Page Route

Add new route to your router configuration:
- Route path: /reminders/:reminderId
- Component: ReminderDetailPage

PART 3: Create Reminder Detail Page - Header Section

Create new file: src/pages/ReminderDetailPage.tsx

Header section should include:
1. Back button (← Back to Reminders) linking to /reminders
2. Reminder title as page title (text-2xl font-bold text-gray-900)
3. Status badge (Active = green bg-green-100 text-green-800, Inactive = gray)
4. Asset category badge with icon (HVAC = blue, Plumbing = green, etc.)
5. Action buttons in top-right:
   - Edit Reminder (primary blue button #0066CC)
   - Duplicate Reminder (secondary gray button, outline)
   - Delete Reminder (secondary red button, outline only)

Layout:
- Use similar structure to Service Detail page
- White background card with padding
- Header has flex justify-between for title/badges on left, actions on right
- Show frequency badge below title: "Quarterly (4x/year)" or "Monthly (12x/year)"

Duke Energy Design:
- Primary Blue: #0066CC
- Status Active: bg-green-100 text-green-800 border-green-200
- Status Inactive: bg-gray-100 text-gray-600 border-gray-300
- Category badges:
  * HVAC: bg-blue-100 text-blue-800 (Thermometer icon)
  * Plumbing: bg-green-100 text-green-800 (Wrench icon)
  * Electrical: bg-purple-100 text-purple-800 (Zap icon)
  * Appliance: bg-orange-100 text-orange-800 (Package icon)
  * Water Heater: bg-red-100 text-red-800 (Flame icon)
  * General Home: bg-gray-100 text-gray-800 (Home icon)
- Use Lucide React icons: ArrowLeft, Edit, Copy, Trash2, Bell

Sample Data Structure:
Use reminderId from URL params to fetch/filter reminder data
Mock data should include:
- id, title, description
- frequency, assetCategory
- linkedService (optional), linkedHPPPlan (optional)
- status (active/inactive)
- notificationContent (title, body, cta)
- targetAudience, estimatedRecipients
- scheduleStartDate, scheduleEndDate
- createdDate, lastModifiedDate, lastSentDate

Verification:
✅ Clicking reminder row navigates to detail page
✅ Back button returns to reminders list
✅ Reminder title, status, and category badges display correctly
✅ Frequency badge shows below title
✅ Edit, Duplicate, and Delete buttons are visible (non-functional for now)
```

---

### Prompt 2: Reminder Detail Page - Information Tabs

**Copy this prompt into Lovable:**

```
Add tabbed content sections to the Reminder Detail page to organize reminder information.

Create 4 tabs below the header:
1. Overview (default active)
2. Notification Content
3. Frequency & Scheduling
4. Performance Analytics

Tab Navigation:
- Use state to track active tab
- Horizontal tab buttons below header
- Active tab: blue border-b-2 border-blue-600, text-blue-600
- Inactive tabs: text-gray-600, hover:text-gray-900
- Use Lucide React icons for each tab

TAB 1: Overview
Display these fields in a 2-column grid:

Left Column:
- Reminder Title (read-only text)
- Asset Category (badge with icon)
- Description (read-only textarea/box, full width below columns)
- Linked Service (if any): Shows service name as link, or "None"
- Linked HPP Plan (if any): Shows plan name as link, or "None"

Right Column:
- Status (Active/Inactive badge)
- Frequency (badge: "Quarterly", "Monthly", etc.)
- Target Audience (text: "All customers with HVAC", "HPP plan holders", etc.)
- Estimated Recipients (count: "~6,234 customers")
- Created Date (formatted: MM/DD/YYYY)
- Last Modified Date (formatted: MM/DD/YYYY)
- Last Sent Date (formatted: MM/DD/YYYY at HH:MM AM/PM)

TAB 2: Notification Content
Display notification preview in 2 sections:

Section 1: Content Details (left side)
- Notification Title (what appears in push notification)
- Message Body (full notification text)
- Variables used: Display list of variables (e.g., {customer_name}, {asset_name})
- Call-to-Action: Shows CTA button text and action (e.g., "Book Service", "Mark as Done")

Section 2: Preview (right side)
- Mobile phone mockup showing how notification appears
- Push notification preview at top
- In-app notification card preview
- Highlight CTA button in preview

Design for notification preview:
- Use phone frame mockup (375px width)
- Push notification: Small banner at top with title + snippet
- In-app card: Full content with CTA button
- Duke Energy blue for CTA button

TAB 3: Frequency & Scheduling
Display scheduling information:

Fields:
- Frequency Type (Monthly, Quarterly, Bi-annually, Annually, Seasonal, Custom)
- If Seasonal: Show which seasons (Spring, Summer, Fall, Winter) and months
- If Custom: Show list of specific dates
- Send Time: "9:00 AM in customer's local timezone"
- Days Before Event: "7 days before due date"
- Schedule Start Date: When reminders began sending
- Schedule End Date: When reminders stop (or "Ongoing")
- Next Scheduled Send: "December 1, 2025 at 9:00 AM"

Use calendar/schedule visualization:
- Timeline showing next 6 scheduled sends
- Calendar icon for each send date
- Highlight next send in blue

TAB 4: Performance Analytics
Display reminder performance metrics:

Metrics Cards (4 columns):
1. Total Sent
   - Count: 2,456 (last 90 days)
   - Icon: Send
   - Trend: +12% vs previous period

2. Open Rate
   - Percentage: 68%
   - Icon: Eye
   - Benchmark: "Above average (55%)"
   - Color: Green if above 60%, yellow if 40-60%, red if below 40%

3. Action Rate
   - Percentage: 32%
   - Icon: MousePointer
   - Actions: "Booked service" or "Marked as done"
   - Color: Green if above 25%, yellow if 15-25%, red if below 15%

4. Revenue Generated (if linked to service)
   - Amount: $15,678
   - Icon: DollarSign
   - From bookings made via this reminder

Charts Section:
1. Line Chart: "Sends Over Time" (last 6 months)
   - X-axis: Months
   - Y-axis: Number of sends
   - Show trend line

2. Bar Chart: "Performance by Month"
   - Compare open rate, action rate, dismissal rate
   - Last 6 months

Empty State (if reminder never sent):
- "No performance data yet"
- "This reminder hasn't been sent to customers"
- Icon: BarChart with slash-through

Design Specs:
- Each tab content in white card with p-6 padding
- Field labels: text-sm font-medium text-gray-700
- Field values: text-base text-gray-900
- Use grid layout: grid-cols-1 md:grid-cols-2 gap-6
- Description field spans full width
- Charts use Recharts library

Verification:
✅ All 4 tabs are clickable and switch content
✅ Overview tab shows all basic information
✅ Notification Content tab shows preview with phone mockup
✅ Frequency & Scheduling tab shows timeline and next send date
✅ Performance Analytics tab shows metrics and charts (or empty state)
✅ Layout is responsive (2 columns desktop, 1 column mobile)
```

---

### Prompt 3: Reminder Detail Page - Recipient List Modal

**Copy this prompt into Lovable:**

```
Add a clickable recipient count that opens a modal showing who will receive the reminder.

In the Overview tab, make the "Estimated Recipients" count clickable:
- Style as link (text-blue-600 hover:underline cursor-pointer)
- On click, open "Recipient List" modal

RECIPIENT LIST MODAL:

Modal Header:
- Title: "Reminder Recipients"
- Subtitle: "Change HVAC Filter" (reminder name)
- Close button (X)

Modal Content:

Section 1: Recipient Summary
Cards showing recipient breakdown:
1. Total Recipients: 6,234 customers
2. HPP Plan Holders: 4,890 (78%)
3. Non-HPP Customers: 1,344 (22%)
4. With Asset Registered: 6,234 (100%)

Section 2: Filters Applied
Display criteria used to target recipients:
- "Customers with HVAC asset type"
- "Active HPP Plan: Premium HVAC Protection"
- "Located in: NC, SC, FL"
- "Asset age: 1+ years"

Section 3: Sample Recipients Table
Show 10 sample customers who will receive this reminder:

Table columns:
1. Customer Name
2. Email
3. HPP Plan (badge or "None")
4. Asset Type (with icon)
5. Last Reminder Sent (date)

Sample rows:
- John Smith | john.smith@email.com | Premium HVAC | HVAC System | Oct 15, 2025
- Mary Johnson | mary.j@email.com | Basic | HVAC System | Oct 14, 2025
(8 more)

Table features:
- Pagination: "Showing 1-10 of 6,234"
- Search bar: "Search by name or email"
- Export button: "Export Full List (CSV)"

Section 4: Send Preview
Button at bottom of modal:
- "Send Test Notification" (secondary button)
- Opens small form to enter admin email
- Sends test notification to admin for preview

Design Specs:
- Modal size: Large (max-w-4xl)
- Scrollable content area
- Summary cards: grid-cols-4 gap-4
- Table: Striped rows, hover effect
- Duke Energy colors for badges

Icons:
- Users icon for Total Recipients
- Shield icon for HPP holders
- User icon for Non-HPP
- Home icon for Asset registered

Verification:
✅ Recipient count in Overview tab is clickable
✅ Modal opens showing recipient breakdown
✅ Filters applied section shows targeting criteria
✅ Sample recipients table displays 10 customers
✅ Export button is visible
✅ Send Test Notification button is functional
✅ Modal is scrollable if content is long
```

---

### Prompt 4: Reminder Detail Page - Edit, Duplicate, Delete Actions

**Copy this prompt into Lovable:**

```
Make the Edit, Duplicate, and Delete buttons functional.

PART 1: Edit Reminder Button

On "Edit Reminder" click:
1. Navigate to: /reminders/:reminderId/edit
2. Button styling: bg-blue-600 hover:bg-blue-700 text-white
3. Include Edit icon from Lucide React

PART 2: Duplicate Reminder Button

On "Duplicate" click:
1. Show confirmation dialog: "Duplicate this reminder?"
2. Dialog message: "This will create a copy of 'Change HVAC Filter' with all settings. The duplicate will be created as Inactive."
3. Buttons: Cancel (gray) / Duplicate (blue)
4. On confirm:
   - Show loading state (1 second)
   - Create duplicate with title: "[Original Title] (Copy)"
   - Set status to Inactive
   - Show success toast: "Reminder duplicated successfully"
   - Navigate to new reminder detail page: /reminders/:newReminderId

PART 3: Delete Reminder Button

On "Delete" click:
1. Show confirmation dialog: "Delete this reminder?"
2. Dialog message: "Are you sure you want to delete 'Change HVAC Filter'? This action cannot be undone."
3. Warning: "This reminder has been sent to 6,234 customers 24 times. Performance data will be archived."
4. Buttons: Cancel (gray) / Delete Permanently (red)
5. On confirm:
   - Show loading state
   - Delete reminder
   - Show success toast: "Reminder deleted successfully"
   - Navigate back to /reminders

Design Specs:

Edit Button:
- bg-blue-600 hover:bg-blue-700 text-white
- Icon: Edit (Lucide React)

Duplicate Button:
- border-gray-300 text-gray-700 hover:bg-gray-50
- Icon: Copy (Lucide React)

Delete Button:
- border-red-600 text-red-600 hover:bg-red-50
- Icon: Trash2 (Lucide React)

Confirmation Dialogs:
- Title: "Duplicate Reminder" or "Delete Reminder"
- Icon: AlertTriangle (yellow) for delete, Copy (blue) for duplicate
- Message text: text-gray-700
- Warning text (if applicable): text-red-600 text-sm

Toast Notifications:
- Success: bg-green-600 text-white, 3 seconds
- Error: bg-red-600 text-white, 5 seconds

Verification:
✅ Edit button navigates to edit page
✅ Duplicate button opens confirmation dialog
✅ Duplicate creates copy with "(Copy)" suffix and Inactive status
✅ Delete button opens confirmation dialog with warning
✅ Delete removes reminder and shows toast
✅ After delete, user returns to reminders list
✅ All buttons have correct styling and icons
```

---

## Screen 11: Reminder Edit Page

### Purpose
Create a dedicated edit page for modifying existing maintenance reminders. This provides a full-page editing experience (not modal-based) for comprehensive reminder configuration with real-time preview.

### User Story
As an **Operations Manager**, I need to edit reminder settings, notification content, frequency, and targeting so I can optimize reminder effectiveness and ensure customers receive timely, relevant maintenance notifications.

### New Feature: Full-Page Reminder Edit Interface
Create dedicated edit page at route `/reminders/:reminderId/edit` with multi-section form, real-time notification preview, and recipient targeting configuration.

---

### Prompt 5: Reminder Edit Page - Route & Layout Structure

**Copy this prompt into Lovable:**

```
Create a new Reminder Edit page with full-page form layout and side-by-side preview.

PART 1: Add Route
Add new route to router configuration:
- Route path: /reminders/:reminderId/edit
- Component: ReminderEditPage

PART 2: Create ReminderEditPage.tsx

Page Structure:
1. Header Section:
   - Back button (← Back to Reminder Detail) linking to /reminders/:reminderId
   - Page title: "Edit Reminder"
   - Reminder status indicator (read-only badge)

2. Layout: Split Screen (2 columns)
   - LEFT COLUMN (60% width): Form sections
   - RIGHT COLUMN (40% width): Live Preview (sticky)

3. Action Buttons (bottom of left column, sticky):
   - Cancel (gray button) - links back to detail page
   - Save as Draft (secondary button) - saves with Inactive status
   - Save & Activate (primary blue button) - saves with Active status

Header Design:
- Flex container with back button + title on left
- Status badge and category badge on right
- Border-bottom separator
- mb-6 margin below header

Form Container (Left Column):
- max-w-3xl width
- bg-white rounded-lg shadow p-6
- Divide form into clearly separated sections with borders

Preview Container (Right Column):
- Sticky positioning (top-24)
- bg-white rounded-lg shadow p-6
- Max height: calc(100vh - 200px)
- Overflow-y-auto if needed

Duke Energy Styling:
- Primary Blue: #0066CC for Save & Activate button
- Secondary: border-blue-600 text-blue-600 for Save as Draft
- Cancel button: border-gray-300 text-gray-700 hover:bg-gray-50

Verification:
✅ Route /reminders/:reminderId/edit is accessible
✅ Back button navigates to reminder detail page
✅ Page title shows "Edit Reminder"
✅ Layout splits into form (left) and preview (right)
✅ Preview section is sticky on scroll
✅ All 3 action buttons visible at bottom
```

---

### Prompt 6: Reminder Edit Page - Basic Information Form

**Copy this prompt into Lovable:**

```
Add the first form section: Basic Information with validation.

Create form section titled "Basic Information" with these fields:

Fields:
1. Reminder Title (required)
   - Text input, max 100 characters
   - Label: "Reminder Title *"
   - Placeholder: "e.g., Change HVAC Filter"
   - Validation: Required, min 3 characters
   - Error message: "Title must be at least 3 characters"

2. Description (required)
   - Textarea, 4 rows, max 500 characters
   - Label: "Description *"
   - Placeholder: "Explain what this reminder is about and why it's important..."
   - Character counter: "450/500 characters"
   - Validation: Required, min 20 characters
   - Help text: "This description is for admin reference only, not shown to customers"

3. Asset Category (required)
   - Dropdown select with icons
   - Label: "Asset Category *"
   - Options:
     * HVAC (Thermometer icon)
     * Plumbing (Wrench icon)
     * Electrical (Zap icon)
     * Appliance (Package icon)
     * Water Heater (Flame icon)
     * General Home Maintenance (Home icon)
   - Validation: Required

4. Status (required)
   - Toggle switch (Active/Inactive)
   - Label: "Reminder Status"
   - Default: Active
   - Green when Active, Gray when Inactive
   - Warning below toggle if Active: "Active reminders will automatically send to customers based on schedule"

Form State Management:
- Use React Hook Form or similar form library
- Initialize with current reminder data
- Track dirty/touched state for each field
- Update preview in right column on any change

Validation Rules:
- Show error messages below fields (text-red-600 text-sm)
- Validate on blur for each field
- Prevent save if any required field is empty

Layout:
- Title and Category in same row (2 columns desktop)
- Description spans full width
- Status toggle on its own row with warning text

Design Specs:
- Field labels: text-sm font-medium text-gray-700
- Required fields marked with red asterisk
- Input borders: border-gray-300, focus:border-blue-500
- Section title: text-lg font-semibold text-gray-900 mb-4
- Section has border-b pb-6 mb-6 separator

Verification:
✅ All 4 fields render correctly
✅ Title validation works (required, min 3 chars)
✅ Description has character counter
✅ Category dropdown shows icons for each option
✅ Status toggle switches between Active/Inactive
✅ Error messages display on validation failure
✅ Preview updates when title or category changes
```

---

### Prompt 7: Reminder Edit Page - Frequency & Scheduling Form

**Copy this prompt into Lovable:**

```
Add the second form section: Frequency & Scheduling Settings.

Create form section titled "Frequency & Scheduling" with these fields:

Fields:
1. Frequency Type (required)
   - Radio buttons (vertical layout)
   - Label: "How often should this reminder be sent? *"
   - Options:
     * Monthly (12 times/year)
     * Quarterly (4 times/year)
     * Bi-annually (2 times/year)
     * Annually (1 time/year)
     * Seasonal (specific seasons)
     * Custom (define specific dates)
   - Each option has description below in text-sm text-gray-600

2. IF Frequency = Seasonal:
   Show additional fields:
   - Checkboxes: Select seasons
     * Spring (March - May)
     * Summer (June - August)
     * Fall (September - November)
     * Winter (December - February)
   - For each selected season, show month dropdown
   - Example: Spring → Select month: March, April, or May
   - At least 1 season must be selected

3. IF Frequency = Custom:
   Show date picker interface:
   - Label: "Select reminder dates"
   - Date picker: Click to add dates
   - List of selected dates (sortable)
   - "Add Another Date" button
   - Delete icon next to each date
   - At least 1 date must be added

4. Send Time (required)
   - Time picker input
   - Label: "What time should reminders be sent? *"
   - Default: 09:00 AM
   - Format: HH:MM AM/PM
   - Help text: "Reminders are sent in customer's local timezone"

5. Days Before Event (required)
   - Number input (1-90 days)
   - Label: "Send reminder how many days before due date? *"
   - Default: 7
   - Suffix: "days"
   - Help text: "Gives customers time to book service"
   - Validation: Must be between 1 and 90

6. Schedule Start Date (required)
   - Date picker
   - Label: "When should reminders start? *"
   - Default: Today
   - Cannot be in the past

7. Schedule End Date (optional)
   - Date picker
   - Label: "When should reminders stop? (optional)"
   - Placeholder: "Ongoing (no end date)"
   - Must be after start date if provided

Form Behavior:
- Show/hide conditional fields based on Frequency Type selection
- Calculate and display "Next Send Date" based on all settings
- Show warning if end date is less than 30 days away

Layout:
- Frequency radio buttons: Vertical stack
- Conditional fields (Seasonal/Custom): Show with slide-down animation
- Send Time and Days Before in same row (2 columns)
- Start Date and End Date in same row (2 columns)
- "Next Send Date" displayed in info box (blue background) at bottom of section

Design Specs:
- Radio buttons: Large, clear labels with descriptions
- Seasonal checkboxes: Grid layout with season names
- Custom dates: List with hover/delete actions
- Time picker: Native or custom with AM/PM selector
- Info box for Next Send: bg-blue-50 border-l-4 border-blue-600 p-4

Icons:
- Calendar icon next to "Frequency & Scheduling" section title
- Clock icon next to Send Time field
- Calendar icon next to date pickers

Verification:
✅ All frequency options are selectable
✅ Seasonal fields appear when Seasonal is selected
✅ Custom dates interface appears when Custom is selected
✅ Time picker works with AM/PM format
✅ Days Before validation works (1-90)
✅ Date pickers prevent past dates
✅ Next Send Date calculates and displays correctly
✅ Preview updates with frequency information
```

---

### Prompt 8: Reminder Edit Page - Notification Content Form

**Copy this prompt into Lovable:**

```
Add the third form section: Notification Content with real-time preview.

Create form section titled "Notification Content" with these fields:

Fields:
1. Notification Title (required)
   - Text input, max 50 characters
   - Label: "Push Notification Title *"
   - Placeholder: "Time to change your HVAC filter"
   - Character counter: "45/50 characters"
   - Validation: Required, min 5 characters, max 50
   - Help text: "This appears as the notification headline"

2. Message Body (required)
   - Textarea, 6 rows, max 200 characters
   - Label: "Notification Message *"
   - Placeholder: "It's been 3 months since your last filter change..."
   - Character counter: "178/200 characters"
   - Validation: Required, min 20 characters, max 200

3. Variable Insertion
   - Below message body, show available variables:
   - Buttons to insert variables into message:
     * {customer_name} - Customer's first name
     * {asset_name} - Asset type (e.g., "HVAC system")
     * {due_date} - When maintenance is due
     * {service_price} - Price of linked service (if any)
   - Click button to insert variable at cursor position
   - Variables display in blue color in textarea

4. Call-to-Action (required)
   - Dropdown select
   - Label: "Call-to-Action Button *"
   - Options:
     * "Book Service" - Opens service booking flow
     * "Mark as Done" - Dismisses reminder
     * "Learn More" - Opens article/content
     * "View Details" - Opens reminder details
     * "No Action" - Notification only
   - Help text: "What should happen when customer taps the notification?"

5. CTA Button Text (conditional)
   - Text input, max 20 characters
   - Label: "Button Text"
   - Only show if CTA is NOT "No Action"
   - Default values:
     * Book Service → "Book Now"
     * Mark as Done → "Mark Done"
     * Learn More → "Learn More"
     * View Details → "View Details"
   - Customizable by admin

6. Link to Service (optional)
   - Dropdown select (searchable)
   - Label: "Link to Bookable Service (optional)"
   - Options: All active services from service catalog
   - Shows service name and price
   - If selected, "Book Service" CTA becomes more relevant
   - Help text: "Allow customers to book this service directly from the reminder"

7. Link to HPP Plan (optional)
   - Dropdown select
   - Label: "Link to HPP Plan (optional)"
   - Options: All active HPP plans
   - If selected, reminder only sent to customers with this plan
   - Help text: "Only customers with this plan will receive this reminder"

Form Behavior:
- Preview in right column updates in REAL-TIME as fields change
- Character counters update on keypress
- Variable buttons insert at cursor position
- CTA Button Text field shows/hides based on CTA selection
- If service is linked, show service badge in preview

Layout:
- Notification Title: Full width
- Message Body: Full width with variable buttons below
- Variables: Horizontal row of small buttons (bg-gray-100)
- CTA dropdown and Button Text in same row (2 columns)
- Link to Service and HPP Plan: Full width dropdowns

Design Specs:
- Character counters: text-sm text-gray-500 (turns red when over limit)
- Variable buttons: Small, gray, hover:bg-gray-200
- Variables in text: text-blue-600 font-semibold
- Field spacing: mb-4 between fields
- Section border-b pb-6 mb-6

Icons:
- Bell icon next to "Notification Content" section title
- Variables shown with curly braces { } icon

Verification:
✅ Notification title has character counter (max 50)
✅ Message body has character counter (max 200)
✅ Variable buttons insert text at cursor position
✅ Variables display in blue color in textarea
✅ CTA dropdown works
✅ CTA Button Text appears/hides based on selection
✅ Service and HPP Plan dropdowns are searchable
✅ Preview updates in real-time on right side
✅ Preview shows exactly what customer will see
```

---

### Prompt 9: Reminder Edit Page - Target Audience & Recipients

**Copy this prompt into Lovable:**

```
Add the fourth form section: Target Audience with recipient count calculator.

Create form section titled "Target Audience" with these fields:

Fields:
1. Recipient Selection (required)
   - Radio buttons (vertical layout)
   - Label: "Who should receive this reminder? *"
   - Options:
     * All customers with this asset type
       → Description: "Send to all customers who have [Asset Category] registered"
     * Only HPP plan holders
       → Description: "Send only to customers with an active home protection plan"
     * Only customers without HPP
       → Description: "Send to customers who might benefit from HPP enrollment"
     * Custom audience (Advanced)
       → Description: "Define custom filters for targeting"

2. IF "Custom audience" selected:
   Show advanced filters:

   a. Geographic Filter
      - Multi-select checkboxes: States
      - Options: North Carolina, South Carolina, Florida, Indiana, Ohio
      - Label: "Available in states"

   b. Asset Age Filter
      - Dropdown: "Asset age"
      - Options: Any age, 0-1 years, 1-3 years, 3-5 years, 5+ years
      - Label: "Asset registration age"

   c. HPP Plan Type (if HPP holders selected)
      - Multi-select checkboxes
      - Options: Basic, Standard, Premium, Elite
      - Label: "HPP plan tiers"

   d. Last Service Date
      - Dropdown: "Last service"
      - Options: Any time, Within 30 days, 30-90 days, 90+ days, Never
      - Label: "Time since last service"

3. Estimated Recipients (auto-calculated)
   - Display card (read-only)
   - Shows: "~6,234 customers will receive this reminder"
   - Icon: Users
   - Updates in real-time as filters change
   - Breakdown shown below:
     * HPP Holders: 4,890 (78%)
     * Non-HPP: 1,344 (22%)
     * Geographic distribution: NC (45%), SC (25%), FL (20%), IN (6%), OH (4%)

4. Preview Recipients
   - Button: "Preview Recipient List"
   - Opens modal showing sample recipients (see Prompt 3 pattern)
   - Shows 10 sample customers who match criteria

5. Test Notification
   - Text input: Admin email
   - Button: "Send Test to My Email"
   - Sends preview notification to admin
   - Shows toast: "Test notification sent to [email]"

Form Behavior:
- Recipient count updates automatically when any filter changes
- Show loading state (spinner) for 0.5 seconds when calculating count
- If count is 0, show warning: "No customers match these criteria"
- Geographic breakdown shown as mini bar chart

Layout:
- Recipient radio buttons: Vertical stack with descriptions
- Custom filters: Appear with slide-down animation
- Filters: 2-column grid on desktop
- Estimated Recipients card: Full width, highlighted (bg-blue-50 border)
- Test section: At bottom of section

Design Specs:
- Radio buttons: Large with clear descriptions
- Custom filters: Indented slightly (pl-6) to show hierarchy
- Recipients card:
  * bg-blue-50 border-l-4 border-blue-600 p-4
  * Large number (text-3xl font-bold text-blue-600)
  * Breakdown in smaller text below
- Loading spinner: Inline next to count
- Test section: bg-gray-50 p-4 rounded

Icons:
- Users icon next to "Target Audience" section title
- Filter icon next to "Custom audience" option
- MapPin icon for Geographic filter
- Calendar icon for Asset Age filter
- Shield icon for HPP Plan Type

Verification:
✅ All recipient options are selectable
✅ Custom filters appear when "Custom audience" selected
✅ Estimated recipients count updates in real-time
✅ Count shows loading state when recalculating
✅ Breakdown shows HPP vs Non-HPP percentages
✅ Preview Recipients button opens modal
✅ Test notification input and button work
✅ Warning shows if count is 0
```

---

### Prompt 10: Reminder Edit Page - Live Preview Panel

**Copy this prompt into Lovable:**

```
Create the live preview panel in the right column that updates in real-time as form fields change.

PREVIEW PANEL (Right Column, Sticky):

Header:
- Title: "Live Preview"
- Subtitle: "How customers will see this reminder"
- Tab switcher: Push Notification | In-App Card

TAB 1: Push Notification Preview

Show mobile phone mockup (375px width):
- Phone frame (rounded corners, bezels)
- Status bar at top (time, battery, signal)
- Notification banner:
  * App icon: Duke Energy logo
  * App name: "Duke Energy Home Services"
  * Time: "now"
  * Notification title: [From form field]
  * Message snippet: [First 50 chars from form]
  * Blue dot indicator (unread)

Design:
- Phone frame: bg-gray-900 rounded-3xl with notch
- Notification: bg-white shadow-lg rounded-lg p-3
- Title: text-sm font-semibold text-gray-900
- Message: text-xs text-gray-600
- Realistic iOS/Android notification styling

TAB 2: In-App Card Preview

Show full notification card as it appears in app:
- Card layout (bg-white shadow rounded-lg p-4)
- Asset category icon at top (large, colored)
- Notification title (text-lg font-bold)
- Full message body with variables replaced:
  * {customer_name} → "Sarah" (sample)
  * {asset_name} → [Selected category]
  * {due_date} → "December 15, 2025" (calculated)
- CTA button at bottom:
  * Button text: [From form field]
  * Button color: Duke Energy blue #0066CC
  * Full width button
- If service linked:
  * Show service badge above CTA
  * "HVAC Filter Replacement - $89"

Card Features:
- Dismiss icon (X) in top-right corner
- Frequency indicator: "Quarterly reminder"
- Next due date shown below message

Preview Updates:
Monitor these form fields for real-time updates:
1. Title → Updates notification title in both tabs
2. Message Body → Updates message text
3. CTA selection → Updates button text and appearance
4. Linked Service → Shows/hides service badge
5. Asset Category → Updates category icon and color
6. Frequency → Updates frequency badge

Empty States:
- If title empty: Show placeholder "Your notification title"
- If message empty: Show placeholder text
- If no CTA: Hide button in preview

Design Specs:
- Phone mockup: max-w-sm mx-auto
- Card preview: Full width of right column
- Tab switcher: border-b with active indicator
- Real-time: debounce updates by 300ms for smooth UX
- Variables in preview: Show with actual sample data

Icons:
- Category icons: Same as used throughout app (Thermometer, Wrench, etc.)
- Duke Energy logo in notification

Verification:
✅ Preview panel is sticky and scrolls with page
✅ Tab switcher works (Push vs In-App)
✅ Title updates in real-time
✅ Message body updates in real-time
✅ Variables are replaced with sample data in preview
✅ CTA button shows/hides based on form selection
✅ Service badge appears when service is linked
✅ Category icon and color update when category changes
✅ Preview shows realistic phone mockup
✅ Empty states show placeholders
```

---

### Prompt 11: Reminder Edit Page - Save, Cancel, and Validation Logic

**Copy this prompt into Lovable:**

```
Implement Save, Cancel, and form validation logic with user feedback.

PART 1: Save & Activate Button Logic

On "Save & Activate" click:
1. Validate all form sections
2. Required fields:
   - Reminder Title (min 3 chars)
   - Description (min 20 chars)
   - Asset Category
   - Frequency Type
   - Send Time
   - Days Before Event (1-90)
   - Schedule Start Date
   - Notification Title (5-50 chars)
   - Message Body (20-200 chars)
   - Call-to-Action
   - Target Audience selection

3. If validation fails:
   - Scroll to first error field
   - Show error toast: "Please fix all errors before saving"
   - Highlight error sections in red
   - Show error count: "3 errors found"

4. If validation passes:
   - Show confirmation dialog:
     * Title: "Activate This Reminder?"
     * Message: "This reminder will be sent to approximately 6,234 customers starting [Start Date]. Next send: [Calculated Date]"
     * Checkbox: "I confirm the notification content is accurate"
     * Buttons: Cancel / Activate Reminder

5. On confirm activate:
   - Show loading state on button ("Activating...")
   - Simulate API call (setTimeout 1.5 seconds)
   - On success:
     * Set status to Active
     * Show success toast: "Reminder activated successfully"
     * Sub-message: "First notification will send on [Date]"
     * Navigate to detail page: /reminders/:reminderId
   - On error:
     * Show error toast: "Failed to activate reminder"
     * Keep user on edit page

PART 2: Save as Draft Button Logic

On "Save as Draft" click:
1. Validate only basic required fields:
   - Title, Description, Asset Category
   - Less strict than Activate validation

2. If validation passes:
   - Show loading state ("Saving Draft...")
   - Set status to Inactive
   - Save changes
   - Show success toast: "Draft saved successfully"
   - Navigate to detail page: /reminders/:reminderId

3. Allows saving incomplete reminders for later editing

PART 3: Cancel Button Logic

On "Cancel" click:
1. Check if form is dirty (has unsaved changes)
2. If dirty:
   - Show confirmation dialog:
     * Title: "Discard Changes?"
     * Message: "You have unsaved changes. Are you sure you want to leave?"
     * Buttons: Stay on Page (gray) / Discard Changes (red)
3. If not dirty:
   - Navigate directly to detail page: /reminders/:reminderId

PART 4: Browser Navigation Protection

Add unsaved changes warning:
- Use beforeunload event listener
- Prompt user if they try to leave page with unsaved changes
- Message: "You have unsaved changes that will be lost."

PART 5: Field-Level Validation

Real-time validation as user types:
- Show error on blur if field is invalid
- Show green checkmark if field is valid
- Error messages below each field

Validation messages:
- Title: "Title must be 3-100 characters"
- Description: "Description must be 20-500 characters"
- Notification Title: "Title must be 5-50 characters"
- Message Body: "Message must be 20-200 characters"
- Days Before: "Must be between 1 and 90 days"
- Dates: "End date must be after start date"

Design Specs:

Save & Activate Button:
- bg-blue-600 hover:bg-blue-700 text-white
- Icon: CheckCircle
- Loading: opacity-50 cursor-not-allowed with Spinner

Save as Draft Button:
- border-blue-600 text-blue-600 hover:bg-blue-50
- Icon: Save
- Loading: Same as above

Cancel Button:
- border-gray-300 text-gray-700 hover:bg-gray-50
- Icon: X

Confirmation Dialog (Activate):
- Large modal with warning icon
- Checkbox required to enable Activate button
- Shows recipient count and next send date
- Blue "Activate" button only enabled when checkbox checked

Confirmation Dialog (Discard):
- Warning icon (AlertTriangle, yellow)
- Red "Discard Changes" button
- Gray "Stay on Page" button

Toast Notifications:
- Success: bg-green-600 text-white with CheckCircle icon, 4 seconds
- Error: bg-red-600 text-white with AlertCircle icon, 6 seconds
- Info: bg-blue-600 text-white with Info icon, 3 seconds

Error Summary (if validation fails):
- Show at top of form
- bg-red-50 border-l-4 border-red-600 p-4
- List of all errors with links to scroll to field
- "X errors found - please fix before saving"

Form Dirty Detection:
- Compare current form values to initial values
- Set isDirty flag when any field changes
- Show indicator in header: "Unsaved changes" (orange dot)

Verification:
✅ Save & Activate validates all required fields
✅ Activation confirmation shows with recipient count
✅ Success toast shows and navigates on successful activation
✅ Save as Draft saves with Inactive status
✅ Cancel prompts if there are unsaved changes
✅ Cancel navigates immediately if no changes
✅ Browser back button prompts for unsaved changes
✅ Field-level validation works on blur
✅ Error summary shows at top when validation fails
✅ All buttons have correct loading states
✅ Unsaved changes indicator shows in header
```

---

### Implementation Notes

**Navigation Flow:**
1. Reminders List (`/reminders`) → Click row → Reminder Detail (`/reminders/:reminderId`)
2. Reminder Detail → Click Edit → Reminder Edit (`/reminders/:reminderId/edit`)
3. Reminder Edit → Save → Back to Reminder Detail
4. Reminder Edit → Cancel → Back to Reminder Detail
5. Reminder Detail → Back → Reminders List
6. Duplicate creates new reminder → Navigates to new Reminder Detail

**Data Model Integration:**
These pages integrate with the Reminder data model:
- `reminder_id`, `title`, `description`
- `frequency`, `asset_category`
- `optional_service_link`, `optional_hpp_plan_link`
- `status` (active/inactive)
- `notification_content` (title, body, cta, variables)
- `target_audience`, `estimated_recipients`
- `schedule_start_date`, `schedule_end_date`
- `send_time`, `days_before_event`
- `created_by`, `created_date`, `last_modified_date`, `last_sent_date`
- Performance metrics: `total_sent`, `open_rate`, `action_rate`, `revenue_generated`

**Real-Time Preview Requirements:**
- Preview updates must debounce by 300ms for smooth UX
- Variables in preview should show realistic sample data:
  * {customer_name} → "Sarah"
  * {asset_name} → Selected category (e.g., "HVAC system")
  * {due_date} → Calculated based on frequency
  * {service_price} → Linked service price or "$XX"
- Preview should match actual customer experience exactly

**Duke Energy Design Consistency:**
- Primary Blue: #0066CC
- Success Green: #28A745
- Warning Yellow: #FFC107
- Danger Red: #DC3545
- Category colors:
  * HVAC: Blue (#0066CC)
  * Plumbing: Green (#28A745)
  * Electrical: Purple (#6F42C1)
  * Appliance: Orange (#FD7E14)
  * Water Heater: Red (#DC3545)
  * General Home: Gray (#6C757D)

**Responsive Design:**
- Desktop: Split layout (60% form, 40% preview)
- Tablet: Preview moves below form, full width
- Mobile: Single column, preview collapsible

**Testing Checklist:**
- [ ] Reminder row clicks navigate to detail page
- [ ] All 4 tabs display correct information
- [ ] Performance analytics show metrics and charts
- [ ] Recipient count modal opens and displays breakdown
- [ ] Edit button navigates to edit page
- [ ] Duplicate creates copy with "(Copy)" suffix and Inactive status
- [ ] Delete shows confirmation with warning about sent reminders
- [ ] Form layout splits into form (left) and preview (right)
- [ ] Preview is sticky and updates in real-time
- [ ] All form sections validate correctly
- [ ] Variables insert into message body at cursor
- [ ] Recipient count calculates automatically based on filters
- [ ] Save & Activate shows confirmation before activating
- [ ] Save as Draft saves with Inactive status
- [ ] Cancel prompts if unsaved changes exist
- [ ] Navigation flow works: list → detail → edit → detail → list
- [ ] All Duke Energy colors and category icons are correct
- [ ] Test notification sends to admin email

---

**Version:** 1.0
**Added:** November 24, 2025
**Status:** Ready for Implementation
**Dependencies:** Existing Reminders list page (Screen 8)
