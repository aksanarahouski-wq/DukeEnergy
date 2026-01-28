# Admin Portal - Lovable Build Guide
## Duke Energy Residential Solutions

**Created:** November 20, 2025
**Purpose:** Step-by-step guide for building admin portal prototypes in Lovable.dev
**Reference:** Based on HTML prototypes in `/Prototypes/` folder

---

## Admin Portal Overview

This guide provides complete instructions for building a 9-screen Duke Energy Residential Solutions Admin Portal prototype in Lovable.dev.

**Core Screens (4):**
1. **Operations Dashboard** - Homepage with KPIs, charts, and recent activity
2. **Customer Profile View** - Detailed customer information with tabs (Overview, Inventory, HPP Plans, Service History)
3. **Service Request Detail** - Full service request workflow tracking
4. **Enrollment Queue** - Manual HPP enrollment processing (MVP fallback)

**Supporting Screens (5):**
5. **Customers Page** - Searchable customer directory
6. **Service Requests Page** - Filterable list of all service requests
7. **Service Catalog Page** - Manage ad-hoc service offerings
8. **Reminders Page** - Automated maintenance reminder management
9. **HPP Plans Management** - Manage Home Protection Plan products, pricing, and analytics

**Navigation:** All screens accessible via left sidebar with 8 menu items.

---

## Table of Contents
1. [Duke Energy Design System](#duke-energy-design-system)
2. [Project Setup](#project-setup)
3. [Screen 1: Operations Dashboard](#screen-1-operations-dashboard)
4. [Screen 2: Customer Profile View](#screen-2-customer-profile-view)
5. [Screen 3: Service Request Detail](#screen-3-service-request-detail)
6. [Screen 4: Enrollment Queue](#screen-4-enrollment-queue)
7. [Screen 5: Customers Page](#screen-5-customers-page)
8. [Screen 6: Service Requests Page](#screen-6-service-requests-page)
9. [Screen 7: Service Catalog Page](#screen-7-service-catalog-page)
10. [Screen 8: Reminders Page](#screen-8-reminders-page)
11. [Screen 9: HPP Plans Management](#screen-9-hpp-plans-management)
12. [Reusable Components](#reusable-components)
13. [Sample Data](#sample-data)
14. [Integration Points](#integration-points)

---

## Duke Energy Design System

### Color Palette
Based on Duke Energy branding and the HTML prototypes:

```css
/* Primary Colors */
--duke-blue: #0066CC (Primary brand color)
--duke-blue-dark: #0052A3 (Hover states)
--duke-blue-light: #E6F2FF (Backgrounds)

/* Status Colors */
--success: #28A745 (Completed, Active)
--warning: #FFC107 (Pending, Caution)
--danger: #DC3545 (Urgent, Error)
--info: #17A2B8 (Information)

/* Neutral Colors */
--gray-50: #F8F9FA (Light backgrounds)
--gray-100: #E9ECEF
--gray-200: #DEE2E6
--gray-300: #CED4DA
--gray-400: #ADB5BD
--gray-500: #6C757D
--gray-600: #495057
--gray-700: #343A40
--gray-800: #212529
--white: #FFFFFF
```

### Typography
```css
/* Font Family */
--font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif

/* Font Sizes */
--text-xs: 0.75rem (12px)
--text-sm: 0.875rem (14px)
--text-base: 1rem (16px)
--text-lg: 1.125rem (18px)
--text-xl: 1.25rem (20px)
--text-2xl: 1.5rem (24px)
--text-3xl: 1.875rem (30px)

/* Font Weights */
--font-normal: 400
--font-medium: 500
--font-semibold: 600
--font-bold: 700
```

### Component Styles

**Cards:**
- Background: White
- Border: 1px solid #DEE2E6
- Border Radius: 8px
- Shadow: 0 1px 3px rgba(0,0,0,0.1)
- Padding: 24px

**Buttons:**
- Primary: Blue background, white text
- Secondary: White background, gray border
- Border Radius: 6px
- Padding: 8px 16px
- Font Weight: 500

**Badges:**
- Border Radius: 9999px (pill shape)
- Padding: 4px 12px
- Font Size: 12px
- Font Weight: 600

**Sidebar Navigation:**
- Width: 256px (16rem)
- Background: White
- Active Item: Blue background (#0066CC)
- Hover: Light gray background (#F3F4F6)

---

## Project Setup

### Step 1: Initialize Lovable Project

**Prompt for Lovable:**
```
Create a new React admin dashboard application called "Duke Energy Admin Portal".
Set up the following:
- React Router for navigation between screens
- Tailwind CSS for styling
- Lucide React for icons
- Recharts for data visualization

Configure Tailwind with the Duke Energy color palette:
- Primary blue: #0066CC
- Success green: #28A745
- Warning amber: #FFC107
- Danger red: #DC3545
- Gray scale: 50-800

Use Inter font family for all typography.
```

### Step 2: Create Base Layout Component

**Prompt for Lovable:**
```
Create a BaseLayout component with:
1. Left sidebar (256px wide, white background):
   - Duke Energy logo at top with blue bolt icon
   - Title "Duke Energy" and subtitle "Admin Portal"
   - Navigation menu with 8 items:
     * Dashboard (home icon)
     * Customers (users icon)
     * Service Requests (clipboard icon)
     * Enrollments (user-plus icon)
     * HPP Plans (shield icon)
     * Service Catalog (wrench icon)
     * Reminders (bell icon)
     * Analytics (chart-bar icon)
   - Active item highlighted with blue background
   - User profile section at bottom showing "Jessica Davis, Back Office Admin"

2. Main content area:
   - White header with back navigation
   - Notification bell icon with red dot badge
   - Scrollable content area with gray background (#F8F9FA)

Use React Router NavLink for navigation items.
```

---

## Screen 1: Operations Dashboard

**Purpose:** Homepage showing all key metrics and active work
**Route:** `/` or `/dashboard`
**Complexity:** Medium

### Build Prompts

#### Prompt 1: Page Structure & KPI Cards
```
Create the Operations Dashboard page (/dashboard) with:

1. Header section:
   - Title: "Operations Dashboard"
   - Subtitle: "Welcome back, Jessica"

2. Four KPI cards in a grid (4 columns):

   Card 1 - Active Service Requests:
   - Icon: clipboard-list (blue)
   - Value: 127
   - Trend: +8.2% (green, up arrow)
   - Subtitle: "vs last week"
   - Left border: 4px blue

   Card 2 - Pending Enrollments:
   - Icon: user-plus (blue)
   - Value: 12
   - Trend: -15% (red, down arrow)
   - Subtitle: "in review queue"
   - Left border: 4px blue

   Card 3 - Open Tickets:
   - Icon: alert-circle (amber)
   - Value: 8
   - Badge: "3 urgent" (red)
   - Subtitle: "requires attention"
   - Left border: 4px amber

   Card 4 - Today's Completions:
   - Icon: check-circle (green)
   - Value: 45
   - Trend: +12% (green, up arrow)
   - Subtitle: "great progress!"
   - Left border: 4px green

Use Tailwind CSS for styling. Make cards responsive with hover effects (shadow increase).
```

#### Prompt 2: Quick Actions Panel
```
Add a Quick Actions section below KPI cards:

Create a white card with title "Quick Actions" and 4 action buttons in a 2x2 grid:

1. Create Service Request (blue background, wrench icon)
2. Process Enrollment (green background, user-check icon)
3. View Escalations (red background, alert-triangle icon)
4. Generate Report (gray background, file-text icon)

Each button should have:
- Icon on left
- Action text
- Hover effect (slight scale up)
- Rounded corners
- White text for colored buttons

Make buttons clickable and navigate to respective routes.
```

#### Prompt 3: Recent Activity Feed
```
Add a Recent Activity feed next to Quick Actions (2-column layout):

White card with title "Recent Activity" showing 5 activities:

1. "Service request SR-2025-1142 completed"
   - Time: "5 minutes ago"
   - Icon: green check circle

2. "New enrollment submitted by Robert Martinez"
   - Time: "12 minutes ago"
   - Icon: blue user-plus

3. "Contractor assigned to SR-2025-1139"
   - Time: "28 minutes ago"
   - Icon: purple user-hard-hat

4. "Eleanor Mitchell updated payment method"
   - Time: "1 hour ago"
   - Icon: blue credit-card

5. "Escalation ticket #EI-2947 resolved"
   - Time: "2 hours ago"
   - Icon: green check-circle

Each activity should have colored icon, message, and timestamp.
Add "View All Activity" link at bottom.
```

#### Prompt 4: Service Requests Chart
```
Below the 2-column section, add a Service Requests Distribution chart:

Create a white card with:
- Title: "Service Requests by Status"
- Subtitle: "Last 30 days"

Use Recharts to create a Doughnut/Pie chart showing:
- Requested: 18 (amber #FFC107)
- Assigned: 32 (indigo #6366F1)
- En Route: 24 (blue #3B82F6)
- On-Site: 8 (purple #8B5CF6)
- Completed: 45 (green #28A745)

Add legend below chart.
Include total count in center of doughnut: "127 Total"
```

#### Prompt 5: Recent Service Requests Table
```
Add a Recent Service Requests table at the bottom:

White card with title "Recent Service Requests" and table showing:

Columns:
- Request ID (monospace font)
- Customer Name
- Service Type
- Status (colored badge)
- Contractor
- Scheduled Date
- Actions (view link)

5 sample rows:
1. SR-2025-1142, Eleanor Mitchell, HVAC Maintenance, Completed (green), Carolina Comfort, Nov 15
2. SR-2025-1139, Michael Chen, Water Heater Repair, En Route (blue), Triangle Plumbing, Nov 19
3. SR-2025-1138, Sarah Johnson, Electrical Issue, Assigned (purple), Duke Electric, Nov 20
4. SR-2025-1137, Robert Davis, Plumbing Emergency, On-Site (blue), Quick Fix Plumbing, Nov 19
5. SR-2025-1136, Jennifer Lee, HVAC Installation, Requested (amber), Unassigned, Nov 21

Make table rows clickable to navigate to service request detail page.
Add "View All Requests" button at bottom.
```

---

## Screen 2: Customer Profile View

**Purpose:** Most frequently accessed screen showing customer details
**Route:** `/customers/:id`
**Complexity:** High (5 tabs with different content)

### Build Prompts

#### Prompt 1: Customer Header
```
Create the Customer Profile page (/customers/:id) with a customer header card:

Header includes:
1. Avatar circle with initials "EM" (blue background)
2. Customer name: "Eleanor Mitchell" (large, bold)
3. Two badges next to name:
   - "Duke Native" (blue badge)
   - "Active" (green badge with check icon)
4. Customer details in 2-column grid below name:
   - Customer ID: DKE-458923 (with id-card icon, monospace)
   - Email: eleanor.mitchell@email.com (with envelope icon)
   - Phone: (919) 555-0142 (with phone icon)
   - Address: 2847 Oak Street, Durham, NC 27705 (with home icon)
   - Member Since: March 2019 (with calendar icon)
   - Last Login: November 18, 2025 at 3:42 PM (with clock icon)

5. Action buttons on right side:
   - "Edit Profile" (primary blue button)
   - "Send Message" (secondary white button)
   - More menu (3 dots icon button)

Use gray text for labels, dark text for values, small icons before each field.
```

#### Prompt 2: Tabs Navigation
```
Below the customer header, add a tab navigation bar:

5 tabs:
1. Overview (info-circle icon) - active by default
2. Inventory (boxes icon)
3. HPP Plans (shield icon)
4. Service History (history icon)
5. Loyalty (star icon)

Active tab should have:
- Blue text color
- Blue bottom border (3px)
- Bold font weight

Inactive tabs:
- Gray text
- Hover effect (lighter blue text)

Tabs should be clickable and switch content below.
Use React state to manage active tab.
```

#### Prompt 3: Overview Tab Content
```
Create the Overview tab content with 3-column layout at top:

Quick Stats Cards (3 columns):
1. Active HPP Plans:
   - Icon: shield (blue)
   - Value: 2
   - Description: "Water Heater + HVAC"
   - Gradient blue background

2. Service Requests:
   - Icon: wrench (green)
   - Value: 6
   - Description: "All completed"
   - Gradient green background

3. Loyalty Points:
   - Icon: star (purple)
   - Value: 850
   - Description: "$8.50 value"
   - Gradient purple background

Below, create 2-column layout:

Left Column - Account Information:
- Title with user-circle icon
- Key-value pairs in bordered list:
  * Duke Utility Account: 3456789012
  * Property Type: Single Family Home
  * Home Size: 2,400 sq ft
  * Year Built: 1998
  * Payment Method: Visa •••• 4829 (credit-card icon)
  * Auto-Pay: Enabled (green badge with check)

Then Recent Service Requests section:
- 2 service request cards
- Each with title, status badge, request ID, date
- "View All Service History" link

Right Column - Recent Activity:
- Timeline showing 5 activities with colored dots and connecting lines
- Each activity has title, timestamp
- Varied icon colors (blue, green, purple)

Then Admin Notes section:
- 2 note cards with yellow and blue backgrounds
- Each note has title, content, date, author
- "Add Note" button at bottom
```

#### Prompt 4: Inventory Tab Content
```
Create the Inventory tab showing home inventory items:

Header:
- Title: "Home Inventory"
- "Add Item" button (blue, plus icon)

Grid of inventory item cards (2 columns):

Card 1 - Water Heater:
- Icon: fire/flame (blue circle background)
- Badge: "Covered" (green)
- Title: Water Heater
- Model: Rheem ProTech 50-Gallon Electric
- Details:
  * Install Date: March 2019
  * Warranty: 10 years (expires March 2029)
  * Last Service: September 2025
- Hover effect for entire card

Card 2 - HVAC System:
- Icon: wind (blue circle background)
- Badge: "Covered" (green)
- Title: HVAC System
- Model: Carrier Infinity 3-Ton Heat Pump
- Details:
  * Install Date: June 2020
  * Warranty: 15 years (expires June 2035)
  * Last Service: November 2025

Card 3 - Dishwasher:
- Icon: kitchen appliance (gray circle background)
- Badge: "Not Covered" (gray)
- Title: Dishwasher
- Model: Bosch 800 Series
- Details:
  * Install Date: January 2022
  * Warranty: 2 years (expired January 2024)
  * Last Service: None

Card 4 - Refrigerator:
- Icon: refrigerator (gray circle background)
- Badge: "Not Covered" (gray)
- Title: Refrigerator
- Model: Samsung French Door 28 cu ft
- Details similar to Card 3

Use smaller text for details, borders around cards, hover shadow effect.
```

#### Prompt 5: HPP Plans Tab Content
```
Create the HPP Plans tab showing active protection plans:

Header:
- Title: "Active HPP Plans"
- Subtitle: "Eleanor has 2 active Home Protection Plans"

Plan cards (full width, stacked):

Plan Card 1 - Water Heater Protection:
- Light blue background border
- Icon: fire/water-drop in blue circle (large)
- Title: Water Heater Protection Plan
- Plan Code: WH-STD (gray text)
- Active badge (green pill)

3-column info grid:
- Monthly Price: $9.99 (large, bold)
- Enrolled Since: March 2019
- Claims Filed: 2 claims

Coverage Details box (white nested card):
- "Coverage Details:" header
- 4 bullet points with green check icons:
  * Repairs to water heater tank and components
  * Labor and service calls included
  * No deductible or trip charges
  * Covers up to 50-gallon electric or gas units

Two buttons:
- "View Plan Details" (primary blue)
- "Manage" (secondary white)

Plan Card 2 - HVAC Protection:
Similar structure but:
- Icon: wind/air
- Title: HVAC Protection Plan
- Plan Code: HVAC-PLUS
- Monthly Price: $14.99
- Enrolled Since: June 2020
- Claims Filed: 4 claims
- 5 coverage bullet points (including annual maintenance)

Bottom summary card (gray background):
- Info icon
- "Total Monthly HPP Investment"
- $24.98 per month (large, bold)
- "Billed through Duke Energy utility statement" (small text)
```

#### Prompt 6: Service History & Loyalty Tabs
```
Create Service History tab:
- Title: "Service Request History"
- Subtitle: "6 total service requests"
- List of 6 service request cards (full width, stacked)
- Each card has:
  * Request ID (monospace)
  * Status badge (completed - green)
  * Title (bold)
  * Description (2 lines)
  * Footer row with 3 icons:
    - HPP Covered badge (blue shield icon)
    - Contractor name (hard-hat icon)
    - Star rating (yellow star, 5.0 or 4.5)
- Cards are clickable links to service request detail
- Hover effect

Create Loyalty tab:
- Top featured card (purple gradient):
  * Large star icon (white)
  * 850 Points (large, bold)
  * "$8.50 in rewards" subtitle
  * Progress bar showing 850/1,500 for Gold status
  * "650 more points to unlock Gold benefits"

2-column grid:
- Left: How to Earn Points (gift icon, 4 bullet points)
- Right: Membership Tiers (trophy icon, 3 tiers with point ranges)

Points History section:
- Timeline of 4 transactions
- Green cards for earned points (plus icon)
- Red card for redeemed points (minus icon)
- Each with description, date, and point value
```

---

## Screen 3: Service Request Detail

**Purpose:** Shows complete service request context for admin actions
**Route:** `/service-requests/:id`
**Complexity:** High (multiple sections, timeline)

### Build Prompts

#### Prompt 1: Service Request Header
```
Create Service Request Detail page (/service-requests/:id) with header card:

Header includes:
1. Request ID: SR-2025-1142 (large, bold, monospace)
2. Two badges next to ID:
   - Status: "Completed" (green badge with check icon)
   - Coverage: "HPP Covered" (blue badge with shield icon)
3. Info row below:
   - Created: Nov 10, 2025 (calendar icon)
   - Completed: Nov 15, 2025 (clock icon)
   - Resolution Time: 5 days (hourglass icon)
   - Gray text, small icons
4. Action buttons on right:
   - "Escalate" button (red, alert icon)
   - "Actions" button (blue, edit icon)

Add back navigation link at very top: "← Back to Dashboard"
White card background, padding, shadow.
```

#### Prompt 2: Main Layout & Customer Section
```
Create 3-column layout (2/3 main content, 1/3 sidebar):

MAIN CONTENT AREA (left 2/3):

Customer Information Card:
- Title: "Customer Information" (user icon)
- Customer avatar: "EM" initials in blue circle
- Name: Eleanor Mitchell (large)
- Badge: "Duke Native" (blue)
- 2-column details grid:
  * ID: DKE-458923 (id-card icon, monospace)
  * Email: eleanor.mitchell@email.com (envelope icon)
  * Phone: (919) 555-0142 (phone icon)
  * Address: 2847 Oak Street, Durham, NC 27705 (home icon)
- Link: "View Full Profile →" (blue, clickable)

Service Details Card (below customer):
- Title: "Service Details" (clipboard icon)
- Service Type: HPP - Annual Maintenance (bold)
- Category: HVAC (with wind icon, blue)
- Problem Description (gray box):
  "Annual preventive maintenance for HVAC system as part of HVAC Protection Plan. Customer scheduled routine service appointment."
- Related Inventory Item (blue box with icon):
  * Icon: wind symbol
  * Name: HVAC System
  * Model: Carrier Infinity 3-Ton Heat Pump
  * "View Details →" link
- HPP Plan Coverage (green box):
  * Plan name: HVAC Protection Plan
  * Status: Active (green badge)
  * Note: "Annual maintenance included. No charge to customer."

Make sections clearly separated with good spacing.
```

#### Prompt 3: Contractor Notes & Admin Notes
```
Continue main content area:

Contractor Work Notes Card:
- Title: "Contractor Work Notes" (comment-dots icon)
- Two note entries:

Note 1 (larger, gray background):
- Header: hard-hat icon, "Mike Thompson, Carolina Comfort Services"
- Timestamp: Nov 15, 2025 at 10:45 AM (right side)
- Content: "Completed annual preventive maintenance on Carrier Infinity heat pump system. Work performed:"
- Bullet list (7 items):
  * Cleaned condenser coils
  * Checked refrigerant levels (R-410A) - within normal range
  * Inspected electrical connections - all secure
  * Replaced air filter (16x25x1 MERV 11)
  * Tested thermostat operation - working properly
  * Checked blower motor and belt - no issues
  * Verified proper airflow throughout system
- Footer: "System is operating efficiently. No immediate repairs needed. Recommend next maintenance in 12 months."

Note 2 (smaller, blue background):
- Same contractor, earlier timestamp (8:15 AM)
- Content: "Arrived on-site. Customer very friendly. Starting annual maintenance inspection."

Admin Notes Card (below contractor notes):
- Title: "Admin Notes" with "Add Note" button (blue)
- One note card (yellow background):
  * Title: "Preferred morning appointments"
  * Date: Nov 10, 2025
  * Content: "Customer requested all future appointments be scheduled between 8-11 AM due to work schedule."
  * Author: "— Jessica Davis"
```

#### Prompt 4: Sidebar - Contractor & Schedule
```
SIDEBAR (right 1/3):

Contractor Information Card:
- Title: "Contractor" (hard-hat icon)
- Centered layout:
  * Large icon: building symbol in blue circle
  * Company: Carolina Comfort Services (bold)
  * Type: Primary HVAC Contractor (small, gray)
  * 5 gold stars + 5.0 rating
- Contact details (left-aligned with icons):
  * Technician: Mike Thompson (user icon)
  * Phone: (919) 555-0987 (phone icon)
  * Email: dispatch@carolinacomfort.com (envelope icon, small font)
  * Service Area: Durham, Raleigh, Chapel Hill (map-marker icon)
- "Reassign Contractor" button (white with blue border, full width)

Schedule Card (below contractor):
- Title: "Schedule" (calendar icon)
- Key-value pairs (label in gray, value in bold):
  * Scheduled Date: Friday, November 15, 2025
  * Time Window: 8:00 AM - 11:00 AM
  * Actual Arrival: 8:15 AM
  * Completion Time: 10:45 AM
  * Duration: 2 hours 30 minutes

Use consistent spacing, clear labels, good visual hierarchy.
```

#### Prompt 5: Status Timeline & Quick Actions
```
Continue sidebar:

Status History Card:
- Title: "Status History" (history icon)
- Vertical timeline with 5 events:

Event 1 (most recent):
- Green dot (large)
- Title: Completed (bold)
- Time: Nov 15, 2025 at 10:45 AM
- Description: "Service completed successfully. Customer satisfaction rating: 5/5"
- Connecting line to next event

Event 2:
- Blue dot
- Title: On-Site
- Time: Nov 15, 2025 at 8:15 AM
- Description: "Contractor arrived at property"

Event 3:
- Purple dot
- Title: En Route
- Time: Nov 15, 2025 at 7:50 AM
- Description: "Contractor en route to customer location"

Event 4:
- Indigo dot
- Title: Assigned
- Time: Nov 11, 2025 at 9:30 AM
- Description: "Assigned to Carolina Comfort Services"

Event 5 (oldest):
- Yellow dot
- Title: Requested
- Time: Nov 10, 2025 at 2:15 PM
- Description: "Service request created by customer via mobile app"
- No connecting line after this

Quick Actions Card (at bottom):
- Title: "Quick Actions" (bolt icon)
- 4 stacked buttons (full width):
  * "Update Status" (primary blue, sync icon)
  * "Export Details" (white, download icon)
  * "Email Customer" (white, envelope icon)
  * "Cancel Request" (white with red border, x-circle icon)

Each button should have icon on left, centered text.
```

---

## Screen 4: Enrollment Queue

**Purpose:** Manual HPP enrollment processing (MVP fallback)
**Route:** `/enrollments`
**Complexity:** High (table with filters, multi-step modal)

### Build Prompts

#### Prompt 1: Page Header & Summary Cards
```
Create Enrollment Queue page (/enrollments) with:

Page Header:
- Title: "HPP Enrollment Queue" (large, bold)
- Subtitle: "Manual processing for customer enrollments (MVP fallback)" (gray)

Summary Cards (4 columns):

Card 1 - Pending:
- Icon: clock (yellow)
- Value: 8 (large)
- Subtitle: "Awaiting review"
- Left border: 4px yellow

Card 2 - In Progress:
- Icon: spinner (blue)
- Value: 4
- Subtitle: "Being processed"
- Left border: 4px blue

Card 3 - Processed Today:
- Icon: check-circle (green)
- Value: 15
- Subtitle: "↑ 25% vs yesterday"
- Left border: 4px green

Card 4 - Avg Process Time:
- Icon: hourglass (gray)
- Value: 12m
- Subtitle: "Per enrollment"
- Left border: 4px gray

All cards have white background, shadow, hover effect.
```

#### Prompt 2: Filters & Search Bar
```
Below summary cards, add Filters section (white card):

4-column grid with filters:

Column 1 - Status:
- Label: "Status"
- Dropdown select with options:
  * All Statuses
  * Pending
  * In Progress
  * Processed

Column 2 - Date Range:
- Label: "Date Range"
- Dropdown select:
  * Today
  * Last 7 Days
  * Last 30 Days
  * Custom

Column 3 - Assigned To:
- Label: "Assigned To"
- Dropdown select:
  * All Admins
  * Jessica Davis (Me)
  * Mark Thompson
  * Sarah Chen
  * Unassigned

Column 4 - Search:
- Label: "Search"
- Text input with search icon
- Placeholder: "Name, email, or phone"

All inputs should have:
- Border styling
- Focus state (blue border)
- Proper spacing and padding
```

#### Prompt 3: Enrollment Queue Table
```
Create enrollment queue table card:

Header row:
- Title: "Queue (12 items)"
- Right side buttons:
  * "Export" (secondary, file-export icon)
  * "Refresh" (blue border, redo icon)

Table with columns:
1. Customer (name + avatar + type badge)
2. Contact (email + phone)
3. Requested Plans (blue badges)
4. Submitted (date + time)
5. Status (colored badge)
6. Assigned To (avatar + name or "Unassigned")
7. Actions (buttons)

5 Sample Rows:

Row 1 - Pending:
- Avatar: "RM" (purple)
- Name: Robert Martinez
- Type: New Customer (gray text)
- Email: robert.martinez@email.com
- Phone: (919) 555-0234
- Plans: 2 badges (Water Heater, HVAC)
- Submitted: Nov 19, 2025, 9:15 AM
- Status: Pending (yellow badge)
- Assigned: Unassigned
- Actions: "Process" (blue) + "Assign to Me" (white) buttons

Row 2 - Pending:
- Avatar: "LW" (green)
- Name: Lisa Wong
- Type: Duke Customer
- Email: lisa.wong@email.com
- Phone: (919) 555-0456
- Plans: 1 badge (Plumbing)
- Submitted: Nov 19, 2025, 8:42 AM
- Status: Pending (yellow badge)
- Assigned: Unassigned
- Actions: Same as Row 1

Row 3 - In Progress (blue background):
- Avatar: "DK" (blue)
- Name: David Kim
- Type: P&G Customer
- Email: david.kim@email.com
- Phone: (919) 555-0789
- Plans: 1 badge (Water Heater)
- Submitted: Nov 19, 2025, 7:23 AM
- Status: In Progress (blue badge)
- Assigned: Jessica Davis (with avatar)
- Actions: "Continue" (blue) + "View" (white)

Row 4 - In Progress (blue background):
- Similar to Row 3, different customer
- Assigned to: Mark Thompson

Row 5 - Processed (green background):
- Avatar: "MP" (teal)
- Name: Michael Patel
- Status: Processed (green badge with check)
- Assigned: Sarah Chen
- Actions: "View" button only

Add pagination at bottom:
- "Showing 1-5 of 12 enrollments"
- Page buttons: Previous (disabled), 1 (active), 2, 3, Next
```

#### Prompt 4: Process Enrollment Modal - Step 1
```
Create a modal component for processing enrollments with 3 steps:

Modal structure:
- Overlay: semi-transparent black background
- Content: white centered box (800px max width)
- Header: blue background
  * Title: "Process Enrollment" (white text)
  * Close button (X icon, white)

STEP 1 - Search CRM:
- Info banner (blue background):
  * "Customer: [Name]" (bold)
  * "Step 1 of 3: Search for existing customer in CRM"

- Search input:
  * Label: "Search CRM"
  * Input with search icon
  * Placeholder: "Search by account #, email, phone, or address"

- Search Results section (gray background):
  * Label: "Search Results:"
  * 2 customer result cards:

  Result 1:
  - Name: Robert Martinez (bold)
  - Account: Duke Account: 3456789123 • robert.martinez@email.com
  - Address: 1847 Elm Street, Durham, NC 27703
  - "Select" button (blue, right side)

  Result 2:
  - Name: Robert J. Martinez
  - Account: P&G Account: 9876543210 • robertjm@email.com
  - Address: 542 Pine Avenue, Raleigh, NC 27601
  - "Select" button

- Footer buttons:
  * Left: "Create New Customer" (white, user-plus icon)
  * Right: "Cancel" (white)

Clicking "Select" should advance to Step 2.
```

#### Prompt 5: Modal Steps 2 & 3
```
STEP 2 - Select Plans (replaces Step 1 content):
- Info banner: "Step 2 of 3: Select HPP Plans"
  * Subtitle: "Customer requested: Water Heater, HVAC"

- Two plan selection cards (checkboxes checked):

  Plan 1:
  - Checkbox: checked
  - Title: Water Heater Protection Plan (bold)
  - Code: WH-STD • $9.99/month (gray)
  - Blue border when selected

  Plan 2:
  - Checkbox: checked
  - Title: HVAC Protection Plan (bold)
  - Code: HVAC-PLUS • $14.99/month (gray)
  - Blue border when selected

- Total price box (gray background):
  * "Total Monthly Price:" label
  * "$24.98" (large, blue, bold)

- Footer buttons:
  * Left: "Back" (white, left-arrow icon)
  * Right: "Next: Review" (blue, right-arrow icon)

STEP 3 - Review & Submit:
- Info banner: "Step 3 of 3: Review & Submit"
  * Subtitle: "Verify enrollment details before submitting"

- Customer Information card (white with border):
  * Title: "Customer Information"
  * 2-column key-value pairs:
    - Name: Robert Martinez
    - Account: 3456789123 (monospace)
    - Email: robert.martinez@email.com
    - Phone: (919) 555-0234

- Selected Plans card:
  * Title: "Selected Plans"
  * List with prices:
    - Water Heater Protection Plan: $9.99/mo
    - HVAC Protection Plan: $14.99/mo
    - Total (border top): $24.98/mo (large, blue)

- Footer buttons:
  * Left: "Back" (white)
  * Right: "Submit Enrollment" (green, check icon)

Clicking Submit should show success message and close modal.
Use React state to track current step (1, 2, or 3).
```

---

## Reusable Components

### Component Library to Build

Create these reusable components first, then use throughout the app:

#### 1. StatusBadge Component
```typescript
interface StatusBadgeProps {
  status: 'pending' | 'in-progress' | 'assigned' | 'en-route' | 'on-site' | 'completed' | 'cancelled';
  size?: 'sm' | 'md' | 'lg';
}

// Colors:
// pending: yellow
// in-progress: blue
// assigned: purple
// en-route: blue
// on-site: blue
// completed: green
// cancelled: red
```

#### 2. KPICard Component
```typescript
interface KPICardProps {
  icon: LucideIcon;
  title: string;
  value: string | number;
  trend?: {
    value: string;
    direction: 'up' | 'down';
  };
  subtitle: string;
  borderColor: string;
}
```

#### 3. DataTable Component
```typescript
interface Column {
  key: string;
  label: string;
  width?: string;
  render?: (value: any, row: any) => ReactNode;
}

interface DataTableProps {
  columns: Column[];
  data: any[];
  onRowClick?: (row: any) => void;
  rowClassName?: (row: any) => string;
}
```

#### 4. Avatar Component
```typescript
interface AvatarProps {
  initials: string;
  size?: 'sm' | 'md' | 'lg';
  color?: string;
  image?: string;
}
```

#### 5. TimelineItem Component
```typescript
interface TimelineItemProps {
  icon: LucideIcon;
  iconColor: string;
  title: string;
  timestamp: string;
  description?: string;
  isLast?: boolean;
}
```

---

## Sample Data

### Create a Mock Data File

**Prompt for Lovable:**
```
Create a file called mockData.ts with sample data for:

1. Customer object (Eleanor Mitchell):
   - id: "DKE-458923"
   - name: "Eleanor Mitchell"
   - type: "duke-native"
   - status: "active"
   - email: "eleanor.mitchell@email.com"
   - phone: "(919) 555-0142"
   - address: "2847 Oak Street, Durham, NC 27705"
   - utilityAccount: "3456789012"
   - memberSince: "2019-03-15"
   - lastLogin: "2025-11-18T15:42:00"
   - hppPlans: [
       { id: "WH-STD", name: "Water Heater Protection", price: 9.99, enrolled: "2019-03" },
       { id: "HVAC-PLUS", name: "HVAC Protection", price: 14.99, enrolled: "2020-06" }
     ]
   - loyaltyPoints: 850

2. Service Requests array (5 items):
   - Each with: id, customerId, type, category, status, contractor, scheduledDate, description

3. Enrollment Queue array (12 items):
   - Each with: id, customerName, email, phone, requestedPlans, submittedDate, status, assignedTo

4. Inventory Items array (4 items):
   - Each with: id, type, brand, model, installDate, warranty, lastService, covered

5. Dashboard KPIs object:
   - activeServiceRequests: 127
   - pendingEnrollments: 12
   - openTickets: 8
   - todayCompletions: 45

Export all as named exports.
```

---

## Build Order Recommendation

### Phase 1: Foundation (Day 1)
1. ✅ Initialize Lovable project with dependencies
2. ✅ Set up Duke Energy design tokens in Tailwind config
3. ✅ Create BaseLayout component with sidebar
4. ✅ Create reusable components (StatusBadge, KPICard, Avatar, DataTable, TimelineItem)
5. ✅ Create mockData.ts file

### Phase 2: Operations Dashboard (Day 1-2)
1. ✅ Build KPI cards section
2. ✅ Build Quick Actions + Recent Activity (2-column)
3. ✅ Add Service Requests chart
4. ✅ Add Recent Service Requests table
5. ✅ Test navigation and responsiveness

### Phase 3: Customer Profile (Day 2-3)
1. ✅ Build customer header
2. ✅ Build tabs navigation
3. ✅ Build Overview tab (complex, do first)
4. ✅ Build Inventory tab
5. ✅ Build HPP Plans tab
6. ✅ Build Service History tab
7. ✅ Build Loyalty tab
8. ✅ Test tab switching

### Phase 4: Service Request Detail (Day 3-4)
1. ✅ Build header and back navigation
2. ✅ Build 3-column layout structure
3. ✅ Build customer and service details (main area)
4. ✅ Build contractor notes section
5. ✅ Build admin notes section
6. ✅ Build sidebar (contractor, schedule, timeline, actions)
7. ✅ Test layout responsiveness

### Phase 5: Enrollment Queue (Day 4-5)
1. ✅ Build page header and summary cards
2. ✅ Build filters section
3. ✅ Build enrollment table
4. ✅ Build pagination
5. ✅ Build modal structure
6. ✅ Build Step 1 (Search CRM)
7. ✅ Build Step 2 (Select Plans)
8. ✅ Build Step 3 (Review & Submit)
9. ✅ Add state management for modal steps
10. ✅ Test modal flow

### Phase 6: Polish & Testing (Day 5)
1. ✅ Test all navigation flows
2. ✅ Verify responsive design on mobile/tablet
3. ✅ Add loading states where needed
4. ✅ Verify color consistency
5. ✅ Test all interactive elements
6. ✅ Add hover/focus states
7. ✅ Final QA pass

---

## Tips for Using Lovable

### Best Practices

1. **Start with Layout First**
   - Build the shell/structure before adding details
   - Use placeholder content initially
   - Verify responsive behavior early

2. **Component Reuse**
   - Identify patterns (badges, cards, buttons)
   - Build reusable components first
   - Import and use throughout app

3. **Incremental Prompts**
   - Don't try to build entire screen in one prompt
   - Break into logical sections
   - Test each section before moving on

4. **State Management**
   - Use React useState for simple interactions
   - Use React Router for navigation
   - Consider Zustand for complex state if needed

5. **Data Mocking**
   - Create comprehensive mock data file
   - Use TypeScript interfaces for type safety
   - Export data as named exports

6. **Styling Consistency**
   - Reference Duke Energy design tokens
   - Use Tailwind utility classes
   - Create custom classes for repeated patterns

### Common Pitfalls to Avoid

1. ❌ **Don't build everything at once** - Break into smaller pieces
2. ❌ **Don't skip the reusable components** - You'll regret it later
3. ❌ **Don't hardcode colors** - Use design tokens
4. ❌ **Don't forget responsive design** - Test on different screen sizes
5. ❌ **Don't overcomplicate state** - Keep it simple initially
6. ❌ **Don't skip mock data** - You need realistic data to see issues

---

## Next Steps After Build

1. **User Testing**
   - Share with Duke team for feedback
   - Identify confusing workflows
   - Gather improvement suggestions

2. **Iteration**
   - Incorporate feedback
   - Refine UI based on real usage
   - Add missing features

3. **Documentation**
   - Document component APIs
   - Create style guide
   - Write usage instructions

4. **Handoff to Development**
   - Export component specs
   - Document data requirements
   - Create API contract definitions

---

## ADDITIONAL SCREENS

The following prompts build supporting screens that complete the admin portal:
- Customers page (list/search all customers)
- Service Requests page (list/filter all service requests)
- Service Catalog page (manage ad-hoc services)
- Reminders page (manage maintenance reminders)
- HPP Plans Management (manage all Home Protection Plan offerings and analytics)

---

## Screen 5: Customers Page

**Purpose:** Search and browse all customers
**Route:** `/customers`
**Complexity:** Medium

### Build Prompts

#### Prompt 1: Customers Page - Header & Filters
```
Create the Customers page (/customers) with search and filtering capabilities:

HEADER SECTION:
- Title: "Customers"
- Subtitle: "Search and manage customer accounts"
- "Export" button (file-download icon, secondary)

SEARCH & FILTERS SECTION (white card):
Grid layout (4 columns):

Column 1 - Search:
- Large search input
- Icon: Search (left side)
- Placeholder: "Search by name, email, phone, or customer ID"
- Real-time search (debounced)

Column 2 - Customer Type Filter:
- Label: "Customer Type"
- Dropdown select:
  * All Customers
  * Duke Native
  * P&G Customer
  * Non-Native

Column 3 - HPP Status:
- Label: "HPP Plans"
- Dropdown select:
  * All Customers
  * Has Active Plans
  * No Plans

Column 4 - Account Status:
- Label: "Status"
- Dropdown select:
  * All Statuses
  * Active
  * Inactive
  * Suspended

Add "Clear Filters" button if any filter is active.

SUMMARY STATS (below filters):
Small stat cards (4 columns, compact):
1. Total Customers: 12,458 (with trend)
2. Duke Native: 8,234
3. With HPP Plans: 6,890
4. New This Month: 127 (green)

Use proper spacing, focus states on inputs.
```

#### Prompt 2: Customers Table
```
Continue Customers page, add customer table:

CUSTOMERS TABLE CARD:
Header row:
- Title: "Customers (342 results)"
- Right side:
  * "Columns" button (toggle visible columns)
  * "Export Results" button

Table columns:
1. Customer ID (sortable, monospace)
2. Name (sortable, bold with avatar/initials)
3. Customer Type (badge: blue=Duke, green=P&G, gray=Non-Native)
4. Contact (email icon + email)
5. Account Status (badge: green=Active, gray=Inactive)
6. HPP Plans (count badge + "View" link)
7. Last Activity (date, sortable)
8. Actions (view icon button)

Sample rows (10 customers):

Row 1:
- ID: DKE-458923
- Name: Eleanor Mitchell (EM avatar)
- Type: Duke Native (blue badge)
- Email: eleanor.mitchell@email.com
- Status: Active (green)
- Plans: 2 plans (blue badge)
- Last Activity: Nov 18, 2025
- Actions: View button

Row 2:
- ID: PG-234567
- Name: Michael Chen (MC avatar)
- Type: P&G Customer (green badge)
- Email: m.chen@email.com
- Status: Active
- Plans: 1 plan
- Last Activity: Nov 19, 2025

Row 3:
- ID: NON-789012
- Name: Sarah Johnson (SJ avatar)
- Type: Non-Native (gray badge)
- Email: sarah.j@email.com
- Status: Active
- Plans: 0 plans
- Last Activity: Nov 17, 2025

(Add 7 more varied customers with different types, statuses, plan counts)

Table styling:
- Alternating row colors
- Hover: light gray background
- Click row: navigate to customer profile (/customers/:id)
- Sortable columns: arrows in header
- Sticky header on scroll

PAGINATION (bottom):
- "Showing 1-10 of 342 customers"
- Page buttons: Previous, 1, 2, 3, ..., 35, Next
- "Per page" dropdown: 10, 25, 50, 100

Make table responsive, horizontal scroll on smaller screens.
Add loading skeleton while fetching data.
```

#### Prompt 3: Customers - Recent Searches & Quick Actions
```
Continue Customers page, add sidebar section:

LAYOUT:
Change to 2-column layout:
- Left column (75%): Table
- Right sidebar (25%): Recent searches + quick actions

RIGHT SIDEBAR:

RECENT SEARCHES CARD:
- Title: "Recent Searches"
- List of last 5 searches:
  * Search term (clickable)
  * Timestamp: "2 hours ago"
  * Clear icon (x) to remove
- Each search click: re-applies that search

QUICK FILTERS CARD:
- Title: "Quick Filters"
- Preset filter buttons:
  * "High-Value Customers" (HPP plans > 2)
  * "New Customers" (joined last 30 days)
  * "Inactive Accounts" (no activity 90+ days)
  * "No HPP Plans" (potential upsell)
- Click button: applies filter to table

BULK ACTIONS CARD (if rows selected):
- Title: "Bulk Actions"
- Checkbox in table header to select all
- Actions:
  * "Export Selected" (CSV)
  * "Send Message" (email blast)
  * "Assign To" (assign to admin)
- Selected count: "5 customers selected"

Use consistent card styling, proper spacing.
```

---

## Screen 6: Service Requests Page

**Purpose:** Monitor and manage all service requests
**Route:** `/service-requests`
**Complexity:** High

### Build Prompts

#### Prompt 1: Service Requests - Dashboard View
```
Create the Service Requests page (/service-requests):

HEADER:
- Title: "Service Requests"
- Subtitle: "Monitor and manage all service requests"
- "Create Service Request" button (primary blue)

STATUS OVERVIEW CARDS (5 columns):
Compact KPI cards with counts and trends:

1. Requested (yellow):
   - Icon: Clock
   - Count: 18
   - Trend: +3 from yesterday
   - Click: filters to "Requested"

2. Assigned (indigo):
   - Icon: UserCheck
   - Count: 32
   - Trend: +5

3. En Route (blue):
   - Icon: Navigation
   - Count: 24
   - No trend

4. On-Site (purple):
   - Icon: MapPin
   - Count: 8
   - No trend

5. Completed (green):
   - Icon: CheckCircle
   - Count: 45 today
   - Trend: +12% vs yesterday

Each card:
- Clickable to filter table
- Active state: darker background
- Badge with count

Use grid-cols-5 gap-4, responsive to grid-cols-2 on smaller screens.
```

#### Prompt 2: Service Requests - Filters & Table
```
Continue Service Requests page:

FILTERS SECTION (white card, grid-cols-5):

1. Search:
   - Input: "Search by customer, ID, or contractor"
   - Search icon

2. Status:
   - Dropdown: All, Requested, Assigned, En Route, On-Site, Completed, Cancelled

3. Service Type:
   - Dropdown: All, HPP Covered, Ad-Hoc

4. Date Range:
   - Date range picker: Today, Last 7 days, Last 30 days, Custom

5. Contractor:
   - Dropdown: All Contractors, then list of contractors

"Clear All Filters" button if filters active.

SERVICE REQUESTS TABLE:
Header:
- Title: "Service Requests (127 active)"
- Right side:
  * "Columns" dropdown
  * "Export" button
  * "Refresh" button (rotate icon)

Table columns:
1. Request ID (monospace, sortable)
2. Customer (name + ID)
3. Service Type (icon + label)
4. Status (colored badge)
5. Contractor (name + logo)
6. Scheduled Date (sortable)
7. Priority (badge if urgent)
8. Actions (view button)

Sample rows (10 requests with varied data):

Row 1:
- ID: SR-2025-1142
- Customer: Eleanor Mitchell (DKE-458923)
- Type: HVAC Maintenance (with icon)
- Status: Completed (green)
- Contractor: Carolina Comfort
- Date: Nov 15, 2025
- Priority: Normal
- Actions: View

Row 2:
- ID: SR-2025-1139
- Customer: Michael Chen
- Type: Water Heater Repair
- Status: En Route (blue)
- Contractor: Triangle Plumbing
- Date: Nov 19, 2025 (Today, bold)
- Priority: Urgent (red badge)
- Actions: View + Track

(Add 8 more varied rows)

Table features:
- Alternating rows
- Hover state
- Click row: navigate to /service-requests/:id
- Sortable columns
- Status filter chips above table
- Color-coded left border by status

PAGINATION:
- "Showing 1-10 of 127 requests"
- Page controls

Make table responsive, scrollable.
```

#### Prompt 3: Service Requests - Bulk Actions & Filters
```
Continue Service Requests page, add advanced features:

ACTIVE FILTERS DISPLAY (above table):
If any filters active, show as removable chips:
- "Status: En Route" (x to remove)
- "Type: HPP" (x)
- "Date: Last 7 days" (x)
- "Clear all" link

BULK ACTIONS:
Add checkbox column (first column) in table:
- Checkbox in header: select all on page
- Checkboxes in rows

When rows selected, show floating action bar (sticky bottom):
- Background: dark blue
- Text: "5 requests selected"
- Actions (buttons):
  * "Reassign Contractor"
  * "Update Status"
  * "Export Selected"
  * "Cancel"
- Close button (x)

SORTING:
Click column header to sort:
- First click: ascending (up arrow)
- Second click: descending (down arrow)
- Third click: clear sort
- Only one column sorted at a time
- Active column: bold header

SAVED VIEWS (optional, top right):
Dropdown: "My Views"
- All Requests (default)
- My Assigned Requests
- Urgent Requests
- HPP Requests Only
- Ad-Hoc Requests Only
- "Create New View" (saves current filters)

Add loading states, empty states for filtered results.
```

---

## Screen 7: Service Catalog Page

**Purpose:** Manage ad-hoc service offerings
**Route:** `/catalog`
**Complexity:** Medium-High

### Build Prompts

#### Prompt 1: Service Catalog - Header & Stats
```
Create the Service Catalog page (/catalog):

HEADER:
- Title: "Service Catalog"
- Subtitle: "Manage ad-hoc service offerings and pricing"
- "Create New Service" button (primary blue, plus icon)

CATALOG STATS (4 columns):
Compact cards:

1. Total Services:
   - Count: 24
   - Icon: Wrench
   - Subtitle: "Available to customers"

2. Active:
   - Count: 18 (green)
   - Icon: CheckCircle
   - Percentage: 75%

3. Draft:
   - Count: 4 (yellow)
   - Icon: FileEdit

4. Inactive:
   - Count: 2 (gray)
   - Icon: XCircle

Cards with colored left border matching status.

FILTERS SECTION (white card, grid-cols-4):

1. Search:
   - Input: "Search services..."
   - Search icon

2. Category:
   - Dropdown: All Categories, HVAC, Plumbing, Electrical, Appliance, Water Heater

3. Status:
   - Dropdown: All, Active, Draft, Inactive

4. Pricing Type:
   - Dropdown: All, Fixed Price, Variable Price, Quote Required

"Clear Filters" button.
```

#### Prompt 2: Service Catalog - Services Table
```
Continue Service Catalog page:

SERVICES TABLE:
Header:
- Title: "Services (24 total)"
- Right side:
  * "Import Services" (CSV upload)
  * "Export" button

Table columns:
1. Service Name (bold, sortable)
2. Code (monospace, small)
3. Category (badge with icon)
4. Pricing Type (badge)
5. Base Price (sortable, bold)
6. Availability (regions count)
7. Status (badge)
8. Actions (edit, duplicate, delete)

Sample services (10 rows):

Row 1:
- Name: HVAC Seasonal Cleaning & Check
- Code: HVAC-CLEAN-001
- Category: HVAC (blue badge, thermometer icon)
- Type: Fixed Price
- Price: $99.00
- Availability: "12 regions" (link)
- Status: Active (green)
- Actions: Edit, Duplicate, Deactivate (3-dot menu)

Row 2:
- Name: Ceiling Fan Installation
- Code: ELEC-FAN-001
- Category: Electrical (yellow badge, zap icon)
- Type: Variable Price
- Price: $120 - $190
- Availability: "8 regions"
- Status: Active
- Actions: (same)

Row 3:
- Name: Water Heater Inspection
- Code: WH-INSP-001
- Category: Water Heater (red badge, flame icon)
- Type: Fixed Price
- Price: $75.00
- Availability: "15 regions"
- Status: Active
- Actions: (same)

Row 4:
- Name: Emergency Plumbing Service
- Code: PLUMB-EMER-001
- Category: Plumbing (blue badge, droplets icon)
- Type: Quote Required
- Price: "Custom quote"
- Availability: "All regions"
- Status: Active
- Actions: (same)

Row 5:
- Name: HVAC System Replacement
- Code: HVAC-REPL-001
- Category: HVAC
- Type: Quote Required
- Price: "Custom quote"
- Availability: "10 regions"
- Status: Draft (yellow)
- Actions: Edit, Publish

(Add 5 more varied services)

Table features:
- Status badge colors
- Category icons
- Hover state
- Click row: opens edit modal
- Sortable by name, price
- Bulk actions: select multiple to activate/deactivate

THREE-DOT MENU per row:
- Edit (opens edit modal)
- Duplicate (copies service with new code)
- View Details (expands row)
- Activate/Deactivate (toggle)
- Delete (confirmation required)

STATUS TOGGLE:
Quick toggle to activate/deactivate without opening edit modal.
```

#### Prompt 3: Service Catalog - Create/Edit Service Modal
```
Create modal for creating/editing services:

MODAL: "Create New Service" or "Edit Service"
- Full-screen or large modal
- Multi-step form (3 steps with indicator)

STEP 1: Basic Information
- Service Name (required):
  * Text input
  * Example: "HVAC Seasonal Cleaning & Check"

- Service Code (required, auto-generated from name):
  * Text input, uppercase
  * Example: "HVAC-CLEAN-001"
  * Validation: must be unique

- Category (required):
  * Dropdown: HVAC, Plumbing, Electrical, Appliance, Water Heater, Other
  * Icon displayed next to selection

- Description (required):
  * Textarea, 500 char max
  * Rich text editor (bold, italic, bullets)
  * Example: "22-point inspection, filter replacement, coil cleaning"

- Scope of Work:
  * Textarea, 1000 char max
  * Detailed checklist of what's included
  * Bullet format

- Duration (required):
  * Number input + unit dropdown (minutes/hours)
  * Example: "2 hours"

"Continue to Pricing" button

STEP 2: Pricing
- Pricing Type (required):
  * Radio buttons:
    1. Fixed Price (flat rate)
    2. Variable Price (range)
    3. Quote Required (custom)

- IF Fixed Price:
  * Base Price (required): $99.00
  * Tax included toggle

- IF Variable Price:
  * Min Price: $120
  * Max Price: $190
  * Price note: "Final price depends on complexity"

- IF Quote Required:
  * Estimated range (optional): $500 - $2,000
  * Quote process description

Regional Pricing Overrides (optional):
- Table: Region | Base Price | Override Price
- Can set different prices per region
- Default: use base price

Cost to Duke (optional):
- What Duke pays contractor: $125
- Customer pays: $99
- Duke subsidy: $26 (auto-calculated, highlighted)

"Continue to Availability" button

STEP 3: Availability & Publishing
- Geographic Availability:
  * Checkboxes: Select all regions or specific
  * Regions list: Durham, Raleigh, Charlotte, etc. (12 regions)
  * OR Zip codes (textarea, comma-separated)

- Contractor Associations:
  * Multi-select: Which contractors can perform this service
  * List of contractors with checkboxes
  * "All qualified contractors" option

- Service Requirements:
  * Checkboxes:
    - Licensed contractor required
    - Background check required
    - Insurance minimum: $1M
    - Tools/equipment needed

- Customer Visibility:
  * Toggle: "Show in customer app"
  * Toggle: "Featured service" (appears at top)

- Service Status:
  * Radio buttons:
    - Draft (not visible to customers)
    - Active (available for booking)
    - Inactive (hidden but not deleted)

PREVIEW SECTION:
- Preview how service appears in customer app
- Card mockup showing:
  * Service name
  * Price
  * Description
  * Rating (placeholder)
  * "Book Now" button

MODAL FOOTER:
- "Cancel" button (confirm if changes made)
- "Save as Draft" button (secondary)
- "Publish Service" button (primary blue)

Form validation:
- Required field errors
- Price validation (min < max)
- Code uniqueness check
- Success message on save

After save:
- Close modal
- Refresh table
- Show success toast: "Service created successfully"
```

---

## Screen 8: Reminders Page

**Purpose:** Manage proactive maintenance reminders
**Route:** `/reminders`
**Complexity:** Medium

### Build Prompts

#### Prompt 1: Reminders Page - Header & Stats
```
Create the Reminders page (/reminders):

HEADER:
- Title: "Maintenance Reminders"
- Subtitle: "Manage proactive maintenance notifications"
- "Create New Reminder" button (primary blue, bell-plus icon)

REMINDER STATS (4 columns):
Cards with icons:

1. Total Reminders:
   - Count: 18
   - Icon: Bell
   - Subtitle: "Active reminders"

2. Active:
   - Count: 15 (green)
   - Icon: BellRing
   - Sent this month: 2,456

3. Scheduled:
   - Count: 3 (blue)
   - Icon: Calendar
   - Will send: "Next 30 days"

4. Inactive:
   - Count: 3 (gray)
   - Icon: BellOff

FILTERS SECTION (white card, grid-cols-4):

1. Search:
   - Input: "Search reminders..."

2. Asset Category:
   - Dropdown: All Categories, HVAC, Plumbing, Electrical, Appliance, Water Heater

3. Frequency:
   - Dropdown: All, Monthly, Quarterly, Annually, Seasonal

4. Status:
   - Dropdown: All, Active, Inactive

"Clear Filters" button.
```

#### Prompt 2: Reminders Table
```
Continue Reminders page:

REMINDERS TABLE:
Header:
- Title: "Reminders (18 total)"
- Tabs above table:
  * "All Reminders" (default)
  * "Active" (15)
  * "Inactive" (3)

Table columns:
1. Reminder Title (bold, sortable)
2. Asset Category (badge with icon)
3. Frequency (badge)
4. Linked Service (link or "None")
5. Recipients (count)
6. Last Sent (date)
7. Status (toggle switch)
8. Actions (edit, duplicate, delete)

Sample reminders (10 rows):

Row 1:
- Title: Change HVAC Filter
- Category: HVAC (blue badge, thermometer icon)
- Frequency: Quarterly (4x/year)
- Service: "HVAC Filter Replacement" (link)
- Recipients: 6,234 customers
- Last Sent: Nov 1, 2025
- Status: Active (toggle ON, green)
- Actions: Edit, Duplicate

Row 2:
- Title: Flush Water Heater Tank
- Category: Water Heater (red badge, flame icon)
- Frequency: Annually (1x/year)
- Service: "Water Heater Maintenance" (link)
- Recipients: 4,567 customers
- Last Sent: Sep 15, 2025
- Status: Active
- Actions: (same)

Row 3:
- Title: Test Smoke & CO Detectors
- Category: General Home (gray badge, home icon)
- Frequency: Monthly (12x/year)
- Service: None
- Recipients: 12,458 customers (all)
- Last Sent: Nov 1, 2025
- Status: Active
- Actions: (same)

Row 4:
- Title: Seasonal AC Check (Spring)
- Category: HVAC
- Frequency: Seasonal (2x/year)
- Service: "HVAC Seasonal Check" (link)
- Recipients: 6,234 customers
- Last Sent: Mar 1, 2025
- Status: Active
- Actions: (same)

Row 5:
- Title: Clean Refrigerator Coils
- Category: Appliance (green badge, package icon)
- Frequency: Bi-annually (2x/year)
- Service: None
- Recipients: 8,900 customers
- Last Sent: May 15, 2025
- Status: Active
- Actions: (same)

Row 6:
- Title: Inspect Plumbing Fixtures
- Category: Plumbing
- Frequency: Annually
- Service: "Plumbing Inspection"
- Recipients: 5,678 customers
- Last Sent: Jan 10, 2025
- Status: Inactive (toggle OFF, gray)
- Actions: Edit, Activate

(Add 4 more)

Table features:
- Status toggle: quick activate/deactivate
- Click row: opens edit modal
- Hover state
- Sortable by title, frequency, recipients
- Bulk actions: select multiple to activate/deactivate

RECIPIENTS COLUMN:
- Shows count
- Click count: opens modal with recipient list
- Filter options: All, HPP customers, Non-HPP, etc.
```

#### Prompt 3: Create/Edit Reminder Modal
```
Create modal for creating/editing reminders:

MODAL: "Create New Reminder" or "Edit Reminder"
- Medium modal, scrollable

FORM SECTIONS:

1. BASIC INFORMATION:
   - Reminder Title (required):
     * Text input
     * Example: "Change HVAC Filter"
     * Character limit: 100

   - Description (required):
     * Textarea, 500 char max
     * What the reminder is about
     * Example: "Replace your HVAC air filter for optimal performance and air quality"

   - Asset Category (required):
     * Dropdown with icons:
       - HVAC
       - Plumbing
       - Electrical
       - Appliance
       - Water Heater
       - General Home Maintenance

2. FREQUENCY SETTINGS:
   - Frequency Type (required):
     * Radio buttons:
       1. Monthly (12 times/year)
       2. Quarterly (4 times/year)
       3. Bi-annually (2 times/year)
       4. Annually (1 time/year)
       5. Seasonal (custom schedule)
       6. Custom (define exact dates)

   - IF Seasonal:
     * Checkboxes: Spring, Summer, Fall, Winter
     * Month selection for each season

   - IF Custom:
     * Add date picker for each occurrence
     * "Add Another Date" button

   - Time to Send:
     * Time picker: default 9:00 AM
     * Timezone: Customer's local time

   - Days Before Event:
     * Number input: Send X days before due date
     * Example: "7 days before"
     * Help text: "Gives customer time to book service"

3. CONTENT SETTINGS:
   - Notification Title:
     * Text input for push notification
     * Example: "Time to change your HVAC filter"
     * Preview on the right (phone mockup)

   - Message Body:
     * Textarea for notification content
     * Variables available: {customer_name}, {asset_name}, {due_date}
     * Example: "Hi {customer_name}, it's been 3 months since your last filter change..."

   - Call-to-Action:
     * Dropdown:
       - Book Service (opens booking flow)
       - Mark as Done (dismisses reminder)
       - Learn More (opens article)
       - No action

4. SERVICE LINKING (Optional):
   - Link to Bookable Service:
     * Dropdown: Select service from catalog
     * If selected, "Book Service" button appears in reminder
     * Shows service name and price

   - Link to HPP Plan (Optional):
     * Dropdown: Select HPP plan
     * Reminder only sent to customers with this plan

5. TARGET AUDIENCE:
   - Who receives this reminder:
     * Radio buttons:
       1. All customers with this asset type
       2. Only HPP plan holders
       3. Only customers without HPP
       4. Custom filter (advanced)

   - Estimated Recipients:
     * Shows count: "~6,234 customers"
     * Updates based on filters

6. PREVIEW SECTION:
   - Preview how reminder appears:
     * Push notification mockup
     * In-app notification card
     * Email version (if email enabled)

7. STATUS & SCHEDULING:
   - Status (required):
     * Radio buttons:
       - Active (will send automatically)
       - Inactive (draft, won't send)

   - Schedule Start Date:
     * Date picker: When to start sending
     * Default: Today

   - Schedule End Date (optional):
     * Date picker: When to stop
     * Leave blank for ongoing

MODAL FOOTER:
- "Cancel" button
- "Save as Draft" button (sets status to Inactive)
- "Activate Reminder" button (primary blue, sets Active)

Form validation:
- Required fields
- Preview updates in real-time
- Character limits enforced

After save:
- Close modal
- Refresh table
- Show toast: "Reminder created successfully"
- If active: "First notification will send on [date]"
```

#### Prompt 4: Reminders - Analytics Dashboard (Optional)
```
Add analytics section at bottom of Reminders page (optional):

REMINDER PERFORMANCE SECTION:
Collapsible section: "Reminder Analytics"

METRICS CARDS (4 columns):

1. Sent This Month:
   - Count: 2,456
   - Trend: +12% vs last month

2. Open Rate:
   - Percentage: 68%
   - Industry benchmark: 55% (comparison)

3. Action Rate:
   - Percentage: 32%
   - "Booked service" or "Marked done"

4. Dismissal Rate:
   - Percentage: 45%
   - Customers who dismissed

PERFORMANCE TABLE:
Top 5 performing reminders:
- Reminder name
- Sent count
- Open rate
- Action rate
- Revenue generated (if linked to paid service)

CHARTS:
1. Line chart: Reminder sends over time (last 6 months)
2. Bar chart: Action rate by reminder type
3. Pie chart: Top reminder categories

"View Full Analytics" button → opens detailed analytics page

This section helps admins see which reminders are most effective.
```

---

## Additional Features Checklist

Before finalizing these 5 additional screens, ensure:

✅ **Customers Page:**
- Search works across multiple fields
- Filters are combinable
- Table is sortable and paginated
- Links to customer profile work
- Export functionality works
- Loading/empty states

✅ **Service Requests Page:**
- Status badges are color-coded correctly
- Filters work together
- Bulk actions available
- Real-time status updates (simulate)
- Links to service details work
- Urgent requests highlighted

✅ **Service Catalog Page:**
- Create/edit modal validates all fields
- Pricing types work correctly
- Regional overrides functional
- Preview shows accurate representation
- Activate/deactivate toggle works
- Duplicate feature copies correctly

✅ **Reminders Page:**
- Frequency options are clear
- Preview updates in real-time
- Recipient count calculates correctly
- Service linking works
- Active/inactive toggle works
- Analytics show meaningful data

✅ **HPP Plans Management Page:**
- Enrollment stats dashboard displays correctly
- Multi-line enrollment trend chart works
- Plan catalog table is sortable by all columns
- Search and category filters function properly
- Create/edit modal validates all required fields
- Multi-tab modal navigation works smoothly
- Plan details view shows comprehensive analytics
- Revenue, enrollment, and utilization charts render
- Customer feedback integration displays reviews
- Status badges (Active/Inactive/Draft) work correctly
- Duplicate plan feature copies all data
- Integration with Customer Profile HPP tab works

---

## Screen 9: HPP Plans Management

**Purpose:** Manage all Home Protection Plan offerings, pricing, and enrollment analytics
**Route:** `/hpp-plans`
**Complexity:** High

This is the master catalog for all HPP plan offerings - where admins manage plan types, pricing, coverage details, and track enrollment metrics.

#### Prompt 1: HPP Plans Page - Header & Stats Dashboard

```
Create the HPP Plans Management page (/hpp-plans) with enrollment analytics:

HEADER SECTION:
- Title: "Home Protection Plans"
- Subtitle: "Manage plan offerings, pricing, and coverage"
- "Create New Plan" button (plus icon, primary #0066CC)

STATS DASHBOARD (4 KPI cards in grid):

Card 1 - Total Active Plans:
- Large number: "12"
- Label: "Active Plan Types"
- Change indicator: "+2 this quarter" (green up arrow)
- Icon: Shield (blue)

Card 2 - Total Enrollments:
- Large number: "847,256"
- Label: "Active Enrollments"
- Change indicator: "+4.2% from last month" (green)
- Icon: Users

Card 3 - Monthly Recurring Revenue:
- Large number: "$8.4M"
- Label: "Total MRR"
- Change indicator: "+$234K this month" (green)
- Icon: DollarSign

Card 4 - Average Plans per Customer:
- Large number: "2.3"
- Label: "Plans/Customer"
- Change indicator: "+0.2 from last year" (green)
- Icon: TrendingUp

ENROLLMENT TREND CHART (full width white card):
- Title: "Enrollment Trends - Last 12 Months"
- Line chart showing enrollments per month
- Multiple lines for top 5 plan types
- Legend with plan names and colors
- Y-axis: Number of enrollments
- X-axis: Months (Jan - Dec)

Duke Energy colors throughout. Tailwind CSS. Responsive grid.
```

#### Prompt 2: HPP Plans Page - Plan Catalog Table

```
Add the HPP Plans catalog table below the enrollment chart:

FILTERS SECTION (white card):
Grid layout (3 columns):

Column 1 - Search:
- Search input with icon
- Placeholder: "Search by plan name or code"

Column 2 - Category Filter:
- Dropdown: "All Categories"
- Options: "All Categories", "Line Protection", "HVAC", "Appliances", "Plumbing", "Electrical", "Water Heater"

Column 3 - Status Filter:
- Dropdown: "All Statuses"
- Options: "All Statuses", "Active", "Inactive", "Draft"

PLANS TABLE (white card):
Sortable columns:
1. Plan Code (e.g., "HVAC-PLUS")
2. Plan Name (e.g., "HVAC Protection Plan Plus")
3. Category (badge: "HVAC", "Line Protection", etc.)
4. Monthly Price ($9.99 - $19.99)
5. Active Enrollments (number with trend indicator)
6. Monthly Revenue (price × enrollments)
7. Status (badge: "Active" green, "Inactive" gray, "Draft" yellow)
8. Actions (3-dot menu)

Sample data (12 plans):

Row 1:
- WH-STD | Water Heater Protection Plan | Water Heater | $9.99 | 125,834 (↑2.1%) | $1,257K | Active | •••

Row 2:
- HVAC-PLUS | HVAC Protection Plan Plus | HVAC | $14.99 | 98,456 (↑3.8%) | $1,476K | Active | •••

Row 3:
- LINE-WATER | Water Line Protection | Line Protection | $6.99 | 245,123 (↑1.2%) | $1,713K | Active | •••

Row 4:
- LINE-SEWER | Sewer Line Protection | Line Protection | $7.99 | 198,456 (↑0.8%) | $1,586K | Active | •••

Row 5:
- ELEC-BASIC | Electrical System Protection | Electrical | $12.99 | 87,234 (↑4.5%) | $1,133K | Active | •••

Row 6:
- PLUMB-STD | In-Home Plumbing Protection | Plumbing | $11.99 | 45,678 (↓1.2%) | $547K | Active | •••

Row 7:
- APPL-KITCHEN | Kitchen Appliance Bundle | Appliances | $19.99 | 34,567 (↑5.6%) | $691K | Active | •••

Row 8:
- HVAC-BASIC | HVAC Protection Plan Basic | HVAC | $9.99 | 56,789 (↑2.3%) | $567K | Active | •••

Row 9:
- ELEC-PLUS | Electrical System Plus | Electrical | $16.99 | 23,456 (↑6.2%) | $399K | Active | •••

Row 10:
- WH-PREMIUM | Water Heater Premium | Water Heater | $14.99 | 12,345 (↑8.1%) | $185K | Active | •••

Row 11:
- SMART-HOME | Smart Home Protection | Electrical | $24.99 | 4,567 (new) | $114K | Active | •••

Row 12:
- POOL-HVAC | Pool & Spa HVAC | HVAC | $29.99 | 0 | $0 | Draft | •••

Actions menu options:
- Edit Plan
- View Enrollments
- Duplicate Plan
- Change Status
- View Analytics

Table pagination: "Showing 1-12 of 12 plans"

Sortable by any column (clicking header). Default sort: Monthly Revenue (descending).
```

#### Prompt 3: HPP Plans Page - Create/Edit Plan Modal

```
Create a modal that opens when "Create New Plan" or "Edit Plan" is clicked:

MODAL HEADER:
- Title: "Create New HPP Plan" (or "Edit HPP Plan")
- Close X button
- Width: 700px max

MODAL CONTENT (scrollable, multi-tab):

TAB 1 - BASIC INFORMATION (active by default):

Form fields:

1. Plan Code:
   - Input field
   - Placeholder: "e.g., HVAC-PLUS"
   - Helper text: "Unique identifier (uppercase, hyphens allowed)"
   - Validation: Required, 3-20 characters

2. Plan Name:
   - Input field
   - Placeholder: "e.g., HVAC Protection Plan Plus"
   - Helper text: "Customer-facing plan name"
   - Validation: Required

3. Category:
   - Dropdown with icon
   - Options: "Line Protection", "HVAC", "Appliances", "Plumbing", "Electrical", "Water Heater"
   - Icon displays based on selection

4. Short Description:
   - Textarea (3 rows)
   - Placeholder: "Brief description for marketing materials"
   - Character count: "0/150"

5. Coverage Description:
   - Textarea (5 rows)
   - Placeholder: "Detailed coverage information for customers"
   - Character count: "0/500"
   - Helper text: "This appears in plan details on customer app"

TAB 2 - PRICING & BILLING:

6. Monthly Price:
   - Input with $ prefix
   - Placeholder: "9.99"
   - Helper text: "Recurring monthly charge"
   - Validation: Required, positive number

7. Installation Fee:
   - Input with $ prefix
   - Placeholder: "0.00"
   - Helper text: "One-time setup fee (optional)"
   - Toggle: "Waive for Duke native customers"

8. Service Call Fee:
   - Input with $ prefix
   - Placeholder: "0.00"
   - Helper text: "Per-visit fee when service is requested"
   - Options: "$0 (Fully covered)", "$75", "$95", "Custom"

9. Annual Service Limit:
   - Number input
   - Placeholder: "Unlimited"
   - Options: "Unlimited", "2", "3", "4", "Custom"
   - Helper text: "Maximum service calls per year"

10. Billing Eligibility:
    - Checkbox group:
      ☑ Duke Energy utility bill
      ☑ Credit/Debit card
      ☐ Contractor direct billing

TAB 3 - COVERAGE DETAILS:

11. Covered Components:
    - Multi-select tag input
    - Placeholder: "Add covered items"
    - Example tags: "Compressor", "Condenser", "Evaporator Coil", "Air Handler"
    - Button: "+ Add Component"

12. Exclusions:
    - Multi-select tag input
    - Placeholder: "Add exclusions"
    - Example tags: "Pre-existing damage", "Improper installation", "Cosmetic issues"

13. Eligibility Requirements:
    - Checkbox group:
      ☐ System must be less than 10 years old
      ☐ Inspection required before enrollment
      ☐ Duke Energy customer only
      ☐ Home must be primary residence

14. Waiting Period:
    - Dropdown: "No waiting period", "30 days", "60 days", "90 days"
    - Helper text: "Time before coverage becomes active"

TAB 4 - TERMS & CONDITIONS:

15. Contract Terms:
    - Rich text editor
    - Default template loads
    - Formatting toolbar (bold, italic, bullets, links)

16. Cancellation Policy:
    - Radio buttons:
      ○ Cancel anytime, no fee
      ○ 30-day notice required
      ○ Minimum 12-month commitment
      ○ Custom policy

17. Auto-Renewal:
    - Toggle switch: ON/OFF
    - Helper text: "Automatically renew plan annually"

MODAL FOOTER:
- "Cancel" button (secondary, left)
- "Save as Draft" button (secondary)
- "Publish Plan" button (primary #0066CC, right)

Validation: Highlight required fields if "Publish" clicked without completion.
Form autosaves as draft every 30 seconds.

Duke colors, Tailwind CSS, Lucide React icons.
```

#### Prompt 4: HPP Plans Page - Plan Details View & Analytics

```
Create a detailed plan view that opens when clicking a plan row:

PLAN DETAILS HEADER:
- Back button (arrow-left icon) → returns to plans table
- Plan icon (based on category)
- Plan Code badge: "HVAC-PLUS"
- Plan Name: "HVAC Protection Plan Plus"
- Status badge: "Active" (green)
- Actions dropdown (right):
  - Edit Plan
  - Change Status
  - Duplicate Plan
  - View Customer Feedback
  - Download Report

OVERVIEW STATS (4 cards):

Card 1 - Active Enrollments:
- Number: "98,456"
- Trend: "+3.8% this month" (green)

Card 2 - Monthly Revenue:
- Number: "$1,476,293"
- Trend: "+$51,234 this month" (green)

Card 3 - Average Customer Tenure:
- Number: "4.7 years"
- Trend: "+0.3 years YoY" (green)

Card 4 - Customer Satisfaction:
- Number: "4.6/5.0"
- Trend: "92% satisfaction" (green)

TABS SECTION:

TAB 1 - PLAN DETAILS (active):

Section: Basic Information
- Category: "HVAC" (with icon)
- Monthly Price: "$14.99"
- Service Call Fee: "$0 (Fully covered)"
- Annual Limit: "Unlimited service calls"
- Waiting Period: "30 days"

Section: Coverage
- List of covered components (8-10 items with checkmarks)
- List of exclusions (4-6 items with X icons)

Section: Eligibility
- Requirements list (3-4 items)

Section: Terms
- Contract terms (expandable/collapsible)
- Cancellation policy
- Auto-renewal: "Yes"

TAB 2 - ENROLLMENT ANALYTICS:

Chart 1: Enrollment Trends (line chart, 12 months)
- New enrollments per month
- Cancellations per month
- Net growth trend line

Chart 2: Enrollment by Customer Type (pie chart)
- Duke Native with Utility Billing: 68%
- Duke Native with Card: 22%
- Non-Native: 10%

Chart 3: Geographic Distribution (bar chart)
- Top 10 zip codes by enrollment count

Metrics Table:
- Total lifetime enrollments
- Active enrollments
- Cancelled (total)
- Cancellation rate: "8.2% annually"
- Average enrollment duration: "4.7 years"
- Reactivation rate: "12%"

TAB 3 - REVENUE ANALYTICS:

Chart 1: Monthly Revenue Trend (area chart, 12 months)
- Recurring revenue
- Installation fees
- Total revenue

Metrics:
- Total Monthly Recurring Revenue: "$1,476,293"
- Average Revenue Per Enrollment: "$14.99"
- Total YTD Revenue: "$16.2M"
- Projected Annual Revenue: "$19.8M"
- Revenue Growth Rate: "+4.2% YoY"

TAB 4 - SERVICE UTILIZATION:

Chart 1: Service Requests per Month (bar chart)
Chart 2: Average Cost per Service Call (line chart)

Metrics Table:
- Total service calls (12 months): "34,567"
- Average calls per enrollment: "0.35/year"
- Most common service reason: "Compressor failure" (32%)
- Average repair cost: "$850"
- Claims ratio: 57% (cost vs. revenue)

TAB 5 - CUSTOMER FEEDBACK:

Rating distribution (bar chart):
- 5 stars: 68%
- 4 stars: 24%
- 3 stars: 5%
- 2 stars: 2%
- 1 star: 1%

Recent reviews (list):
- Customer name, rating, date, comment (5 most recent)
- Each with link to full customer profile

Common feedback themes (tag cloud):
- "Fast service" (152 mentions)
- "Great value" (98 mentions)
- "Professional contractors" (87 mentions)

Duke colors throughout, Tailwind CSS, interactive charts with Recharts.
```

---

## Integration Points

These screens should integrate with existing screens:

**From Dashboard:**
- Click "Service Requests" count → /service-requests (filtered to active)
- Click "View All Customers" → /customers
- Click "Active HPP Plans" or MRR metric → /hpp-plans

**From Customers Page:**
- Click customer row → /customers/:id (existing Customer Profile)
- "Create Service Request" → opens booking modal

**From Customer Profile:**
- Click HPP Plan in "HPP Plans" tab → /hpp-plans/:planCode (plan details view)

**From Service Requests Page:**
- Click request row → /service-requests/:id (existing Service Request Detail)

**From Service Catalog:**
- "Linked Service" in Reminders → /catalog/:serviceId

**From Reminders:**
- "Linked Service" → /catalog/:serviceId
- Click recipient count → /customers (filtered by reminder audience)

**From HPP Plans:**
- Click "View Enrollments" → /customers (filtered by plan)
- Click customer name in reviews → /customers/:id (Customer Profile)
- "Create New Plan" → opens plan creation modal
- Click plan row → plan details view with full analytics

---

**Document Version:** 1.3
**Last Updated:** November 20, 2025 (Added HPP Plans to navigation menu and updated documentation structure)
**Created By:** Orases Product Team
**For:** Duke Energy Residential Solutions Admin Portal Prototype

**Version History:**
- v1.0: Initial 4 core screens (Dashboard, Customer Profile, Service Request, Enrollment Queue)
- v1.1: Added 4 supporting screens (Customers, Service Requests, Service Catalog, Reminders)
- v1.2: Added Screen 9 (HPP Plans Management)
- v1.3: Updated navigation menu (8 items), Table of Contents, and added Admin Portal Overview
