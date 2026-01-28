# Lovable Build Prompts - Quick Reference
## Copy-Paste Prompts for Duke Energy Admin Portal

**Instructions:** Copy each prompt below directly into Lovable's chat interface. Build in the order listed.

**Total Prompts:** 32
**Total Screens:** 5 core screens (Dashboard, Customer Profile, Service Request Detail, Enrollment Queue, HPP Plans Management)

**Build Order:**
1. Setup Phase (Prompts 1-4)
2. Dashboard (Prompts 5-8)
3. Customer Profile View (Prompts 9-13)
4. Service Request Detail (Prompts 14-18)
5. Enrollment Queue (Prompts 19-24)
6. HPP Plans Management (Prompts 27-30)
7. Final Polish (Prompts 31-32)

---

## 🚀 SETUP PHASE

### Prompt 1: Initialize Project
```
Create a new React admin dashboard application called "Duke Energy Admin Portal".
Set up the following:
- React Router v6 for navigation between screens
- Tailwind CSS for styling
- Lucide React for icons
- Recharts for data visualization

Configure Tailwind with the Duke Energy color palette:
Primary colors:
- duke-blue: #0066CC
- duke-blue-dark: #0052A3
- duke-blue-light: #E6F2FF

Status colors:
- success: #28A745
- warning: #FFC107
- danger: #DC3545
- info: #17A2B8

Neutral colors:
- Use default Tailwind gray scale (50-900)

Use Inter font family for all typography (imported from Google Fonts).

Create the basic folder structure:
- /components (reusable components)
- /pages (route pages)
- /data (mock data)
- /types (TypeScript types)
```

### Prompt 2: Create Base Layout
```
Create a BaseLayout component (src/components/BaseLayout.tsx) with:

1. Left sidebar (w-64, white background, shadow):
   - Top section with Duke Energy branding:
     * Blue rounded square with white lightning bolt icon (Zap from lucide-react)
     * "Duke Energy" title (text-lg, font-bold)
     * "Admin Portal" subtitle (text-xs, text-gray-500)
     * Bottom border

   - Navigation menu (flex-1, p-4):
     * 8 menu items using NavLink from react-router-dom:
       1. Dashboard → "/" (Home icon)
       2. Customers → "/customers" (Users icon)
       3. Service Requests → "/service-requests" (ClipboardList icon)
       4. Enrollments → "/enrollments" (UserPlus icon)
       5. HPP Plans → "/hpp-plans" (Shield icon)
       6. Service Catalog → "/catalog" (Wrench icon)
       7. Reminders → "/reminders" (Bell icon)
       8. Analytics → "/analytics" (BarChart3 icon)

     * Active link styling:
       - bg-duke-blue (blue background)
       - text-white
       - rounded-lg

     * Inactive link styling:
       - text-gray-700
       - hover:bg-gray-100
       - rounded-lg

     * Each link: flex items-center space-x-3 px-4 py-3

   - Bottom user profile section (p-4, border-t):
     * Gray circular avatar with user icon
     * "Jessica Davis" (text-sm, font-semibold)
     * "Back Office Admin" (text-xs, text-gray-500)

2. Main content area (flex-1):
   - Top header (bg-white, border-b, px-8, py-4, sticky top-0, z-10):
     * Left: Back navigation link (← Back to Dashboard)
     * Right: Notification bell icon with red dot badge

   - Content area:
     * bg-gray-50
     * overflow-y-auto
     * Renders {children}

Create routes in App.tsx for all 4 pages (placeholder pages for now):
- Dashboard (/)
- CustomerProfile (/customers/:id)
- ServiceRequestDetail (/service-requests/:id)
- EnrollmentQueue (/enrollments)

Wrap all routes with BaseLayout component.
```

### Prompt 3: Create Reusable Components
```
Create 5 reusable components in src/components/:

1. StatusBadge.tsx:
interface StatusBadgeProps {
  status: 'pending' | 'in-progress' | 'assigned' | 'en-route' | 'on-site' | 'completed' | 'cancelled';
  size?: 'sm' | 'md';
}

Color mapping:
- pending: yellow (bg-yellow-100 text-yellow-700)
- in-progress: blue (bg-blue-100 text-blue-700)
- assigned: purple (bg-purple-100 text-purple-700)
- en-route: blue (bg-blue-100 text-blue-700)
- on-site: blue (bg-blue-100 text-blue-700)
- completed: green (bg-green-100 text-green-700)
- cancelled: red (bg-red-100 text-red-700)

Styles: rounded-full, px-2 py-1 (sm) or px-3 py-1 (md), text-xs font-semibold
Include icon from lucide-react before text

2. KPICard.tsx:
interface KPICardProps {
  icon: React.ReactNode;
  iconColor: string;
  title: string;
  value: string | number;
  trend?: { value: string; direction: 'up' | 'down' };
  subtitle: string;
  borderColor: string;
}

Styles: bg-white rounded-lg shadow p-6 border-l-4
Top row: title (text-sm text-gray-600 font-medium) and icon (text-2xl)
Middle: value (text-3xl font-bold) and trend indicator
Bottom: subtitle (text-xs text-gray-500)

3. Avatar.tsx:
interface AvatarProps {
  initials: string;
  size?: 'sm' | 'md' | 'lg';
  color?: string;
}

Circular div with centered initials, colored background
Size mapping: sm=w-8 h-8, md=w-10 h-10, lg=w-16 h-16

4. TimelineItem.tsx:
interface TimelineItemProps {
  dotColor: string;
  title: string;
  timestamp: string;
  description?: string;
  isLast?: boolean;
}

Styles: relative pl-6
Dot: absolute left-0 top-0 w-4 h-4 rounded-full border-2 border-white
Connecting line (if !isLast): absolute left-1.5 top-4 h-full w-0.5 bg-gray-200

5. DataTable.tsx:
interface DataTableProps {
  columns: Array<{ key: string; label: string; render?: (value: any, row: any) => React.ReactNode }>;
  data: any[];
  onRowClick?: (row: any) => void;
}

Standard table with:
- thead: bg-gray-50 border-b
- th: px-6 py-3 text-left text-xs font-medium text-gray-600 uppercase
- tbody: bg-white divide-y divide-gray-200
- tr: hover:bg-gray-50 cursor-pointer (if onRowClick)
- td: px-6 py-4

Export all components as default.
```

### Prompt 4: Create Mock Data
```
Create src/data/mockData.ts with TypeScript interfaces and sample data:

1. Customer interface and eleanorMitchell object:
   - id: "DKE-458923"
   - name: "Eleanor Mitchell"
   - type: "duke-native"
   - status: "active"
   - email: "eleanor.mitchell@email.com"
   - phone: "(919) 555-0142"
   - address: "2847 Oak Street, Durham, NC 27705"
   - city: "Durham"
   - state: "NC"
   - zip: "27705"
   - utilityAccount: "3456789012"
   - propertyType: "Single Family Home"
   - homeSize: 2400
   - yearBuilt: 1998
   - memberSince: "2019-03-15"
   - lastLogin: "2025-11-18T15:42:00"
   - hppPlans: [
       { id: "WH-STD", name: "Water Heater Protection Plan", code: "WH-STD", price: 9.99, enrolledDate: "2019-03", claimsFiled: 2 },
       { id: "HVAC-PLUS", name: "HVAC Protection Plan", code: "HVAC-PLUS", price: 14.99, enrolledDate: "2020-06", claimsFiled: 4 }
     ]
   - paymentMethod: { type: "visa", last4: "4829" }
   - autoPay: true
   - loyaltyPoints: 850

2. ServiceRequest interface and serviceRequests array (5 items):
   - id: "SR-2025-1142"
   - customerId: "DKE-458923"
   - customerName: "Eleanor Mitchell"
   - type: "hpp"
   - category: "hvac"
   - title: "HVAC Annual Maintenance"
   - description: "Annual preventive maintenance..."
   - status: "completed"
   - contractor: { name: "Carolina Comfort Services", contact: "Mike Thompson", phone: "(919) 555-0987", rating: 5.0 }
   - scheduledDate: "2025-11-15"
   - scheduledTime: "8:00 AM - 11:00 AM"
   - createdDate: "2025-11-10"
   - completedDate: "2025-11-15"

3. EnrollmentQueueItem interface and enrollmentQueue array (5 items with varied statuses)

4. InventoryItem interface and inventoryItems array (4 items: water heater, hvac, dishwasher, refrigerator)

5. dashboardKPIs object with all 4 metrics

Export all as named exports.
```

---

## 📊 SCREEN 1: OPERATIONS DASHBOARD

### Prompt 5: Dashboard KPI Cards
```
Create src/pages/Dashboard.tsx:

Import KPICard component and dashboardKPIs from mockData.

Create 4 KPI cards in a grid (grid-cols-4 gap-4):

1. Active Service Requests:
   - Icon: ClipboardList (blue)
   - Title: "Active Service Requests"
   - Value: 127
   - Trend: { value: "8.2%", direction: "up" }
   - Subtitle: "vs last week"
   - Border: blue-500

2. Pending Enrollments:
   - Icon: UserPlus (blue)
   - Value: 12
   - Trend: { value: "15%", direction: "down" }
   - Subtitle: "in review queue"
   - Border: blue-500

3. Open Tickets:
   - Icon: AlertCircle (amber)
   - Value: 8
   - No trend, instead show badge: "3 urgent" (red)
   - Subtitle: "requires attention"
   - Border: amber-500

4. Today's Completions:
   - Icon: CheckCircle (green)
   - Value: 45
   - Trend: { value: "12%", direction: "up" }
   - Subtitle: "great progress!"
   - Border: green-500

Wrap in container: max-w-7xl mx-auto px-8 py-6
```

### Prompt 6: Quick Actions & Recent Activity
```
Continue Dashboard.tsx, add 2-column layout (grid-cols-2 gap-6) below KPI cards:

LEFT COLUMN - Quick Actions card:
- White card: bg-white rounded-lg shadow-md p-6
- Title: "Quick Actions" with Zap icon
- 2x2 grid of action buttons (grid-cols-2 gap-4):

  1. Create Service Request:
     - bg-blue-600 text-white
     - Wrench icon
     - rounded-lg p-4
     - hover:bg-blue-700 hover:scale-105

  2. Process Enrollment:
     - bg-green-600 text-white
     - UserCheck icon

  3. View Escalations:
     - bg-red-600 text-white
     - AlertTriangle icon

  4. Generate Report:
     - bg-gray-600 text-white
     - FileText icon

RIGHT COLUMN - Recent Activity card:
- White card with "Recent Activity" title (Clock icon)
- List of 5 activities, each with:
  * Colored icon circle (size-6)
  * Activity text (text-sm)
  * Timestamp (text-xs text-gray-500)
  * Space between items

Activities:
1. CheckCircle (green): "Service request SR-2025-1142 completed" • "5 minutes ago"
2. UserPlus (blue): "New enrollment submitted by Robert Martinez" • "12 minutes ago"
3. HardHat (purple): "Contractor assigned to SR-2025-1139" • "28 minutes ago"
4. CreditCard (blue): "Eleanor Mitchell updated payment method" • "1 hour ago"
5. CheckCircle (green): "Escalation ticket #EI-2947 resolved" • "2 hours ago"

Add "View All Activity →" link at bottom (text-blue-600)
```

### Prompt 7: Service Requests Chart
```
Continue Dashboard.tsx, add chart section below the 2-column section:

Import { PieChart, Pie, Cell, ResponsiveContainer, Legend } from 'recharts'

Create white card with:
- Title: "Service Requests by Status"
- Subtitle: "Last 30 days"

Chart data:
const chartData = [
  { name: 'Requested', value: 18, color: '#FFC107' },
  { name: 'Assigned', value: 32, color: '#6366F1' },
  { name: 'En Route', value: 24, color: '#3B82F6' },
  { name: 'On-Site', value: 8, color: '#8B5CF6' },
  { name: 'Completed', value: 45, color: '#28A745' },
];

Render PieChart with:
- ResponsiveContainer (width="100%", height={300})
- Pie with innerRadius={60}, outerRadius={100}
- Map over data using Cell component for colors
- Display "127 Total" in center using custom label
- Legend at bottom with horizontal layout

Add padding and proper spacing.
```

### Prompt 8: Recent Service Requests Table
```
Continue Dashboard.tsx, add table at bottom:

Import DataTable component and serviceRequests from mockData.

Create white card with:
- Title: "Recent Service Requests"
- "View All Requests →" link on right

Use DataTable component with columns:
1. Request ID (render as monospace font, link to detail page)
2. Customer Name
3. Service Type
4. Status (render StatusBadge component)
5. Contractor (contractor name)
6. Scheduled Date (format date nicely)
7. Actions (render "View →" link)

Pass first 5 serviceRequests items to data prop.

Add onRowClick handler that navigates to /service-requests/:id using useNavigate from react-router-dom.

Style table: full width, alternating row colors, hover effects.
```

---

## 👤 SCREEN 2: CUSTOMER PROFILE

### Prompt 9: Customer Profile Header
```
Create src/pages/CustomerProfile.tsx:

Import useParams from react-router-dom to get customer ID.
Import eleanorMitchell from mockData.
Import Avatar component.

Create customer header card (bg-white rounded-lg shadow-md p-6 mb-6):

Layout: flex items-start justify-between

LEFT SIDE:
- Large Avatar (size="lg", initials="EM", color="bg-blue-100 text-blue-600")
- Next to avatar:
  * Name: "Eleanor Mitchell" (text-2xl font-bold)
  * Two badges inline:
    - "Duke Native" (blue badge)
    - "Active" (green badge with CheckCircle icon)
  * 2-column grid of customer details:
    Row 1: ID (with IdCard icon, monospace) | Email (with Mail icon)
    Row 2: Phone (with Phone icon) | Address (with Home icon)
    Row 3: Member Since (with Calendar icon) | Last Login (with Clock icon)
  * Each row: icon (text-gray-600), label (text-gray-600), value (font-medium text-gray-800)

RIGHT SIDE - action buttons:
- "Edit Profile" (primary blue button)
- "Send Message" (secondary white button with border)
- More menu (icon button with MoreVertical icon)

Use proper spacing, icons from lucide-react, responsive flex layout.
```

### Prompt 10: Customer Profile Tabs
```
Continue CustomerProfile.tsx, add tabs navigation:

Create state: const [activeTab, setActiveTab] = useState('overview')

Tab options: overview, inventory, hpp-plans, service-history, loyalty

Render tab bar (bg-white rounded-t-lg shadow-md border-b):
- nav element with flex space-x-8 px-6
- 5 tab buttons:
  1. Overview (Info icon)
  2. Inventory (Package icon)
  3. HPP Plans (Shield icon)
  4. Service History (History icon)
  5. Loyalty (Star icon)

Active tab styles:
- text-blue-600 font-semibold
- border-b-3 border-blue-600
- py-4

Inactive tab styles:
- text-gray-600
- hover:text-blue-600
- py-4

Each button onClick updates activeTab state.

Below tabs, create tab content container (bg-white rounded-b-lg shadow-md p-6):
- Conditionally render content based on activeTab value
- Start with Overview tab content (next prompt)
```

### Prompt 11: Overview Tab Content
```
Continue CustomerProfile.tsx, create Overview tab content:

TOP SECTION - 3 Quick Stats Cards (grid-cols-3 gap-4):

1. Active HPP Plans:
   - Gradient: bg-gradient-to-br from-blue-50 to-blue-100
   - Border: border-blue-200
   - Icon: Shield (blue)
   - Value: 2 (text-3xl font-bold text-blue-800)
   - Subtitle: "Water Heater + HVAC" (text-xs)

2. Service Requests:
   - Gradient: green
   - Icon: Wrench
   - Value: 6
   - Subtitle: "All completed"

3. Loyalty Points:
   - Gradient: purple
   - Icon: Star
   - Value: 850
   - Subtitle: "$8.50 value"

BOTTOM SECTION - 2 columns (grid-cols-2 gap-6):

LEFT COLUMN:
1. Account Information card:
   - Title with UserCircle icon
   - List of key-value pairs with bottom borders:
     * Duke Utility Account: 3456789012
     * Property Type: Single Family Home
     * Home Size: 2,400 sq ft
     * Year Built: 1998
     * Payment Method: Visa •••• 4829 (with CreditCard icon)
     * Auto-Pay: Enabled (green badge with check)

2. Recent Service Requests:
   - 2 service request cards
   - Each card: title, StatusBadge, request ID, date
   - "View All Service History →" link

RIGHT COLUMN:
1. Recent Activity timeline:
   - Use TimelineItem component
   - 5 activities with colored dots, titles, timestamps

2. Admin Notes:
   - 2 note cards (yellow and blue backgrounds)
   - Each: title, content, date, author name
   - "Add Note" button (blue) at bottom

Import TimelineItem component, use proper spacing.
```

### Prompt 12: Inventory Tab
```
Continue CustomerProfile.tsx, create Inventory tab content:

Header (flex justify-between items-center mb-6):
- Title: "Home Inventory"
- "Add Item" button (blue, Plus icon)

Grid of inventory cards (grid-cols-2 gap-4):

Card structure (border rounded-lg p-4 hover:shadow-md transition):
- Top row (flex justify-between):
  * Icon circle (w-12 h-12 rounded-lg flex items-center justify-center)
  * Coverage badge (green "Covered" or gray "Not Covered")
- Title (font-semibold text-gray-800)
- Model (text-sm text-gray-600 mb-2)
- Details list (space-y-1 text-xs text-gray-500):
  * Install Date
  * Warranty
  * Last Service

4 Cards:

1. Water Heater:
   - Icon: Flame (blue bg)
   - Badge: Covered (green)
   - Model: Rheem ProTech 50-Gallon Electric
   - Install: March 2019
   - Warranty: 10 years (expires March 2029)
   - Last Service: September 2025

2. HVAC System:
   - Icon: Wind (blue bg)
   - Badge: Covered
   - Model: Carrier Infinity 3-Ton Heat Pump
   - Install: June 2020
   - Warranty: 15 years (expires June 2035)
   - Last Service: November 2025

3. Dishwasher:
   - Icon: Utensils (gray bg)
   - Badge: Not Covered (gray)
   - Model: Bosch 800 Series
   - Install: January 2022
   - Warranty: 2 years (expired January 2024)
   - Last Service: None

4. Refrigerator:
   - Icon: Refrigerator (gray bg)
   - Badge: Not Covered
   - Model: Samsung French Door 28 cu ft
   - Install: April 2021
   - Warranty: 1 year (expired April 2022)
   - Last Service: None

Use lucide-react icons, proper hover effects.
```

### Prompt 13: HPP Plans & Other Tabs
```
Continue CustomerProfile.tsx:

HPP PLANS TAB:
Header with title and subtitle.

Two plan cards (space-y-4):

Card structure (border-2 border-blue-200 bg-blue-50 rounded-lg p-5):
- Top: Icon + Title + Code + Active badge
- 3-column info grid:
  * Monthly Price (large, bold)
  * Enrolled Since
  * Claims Filed
- Coverage Details (white nested card with green check bullets)
- Two buttons: "View Plan Details" (blue) + "Manage" (white)

Plan 1: Water Heater Protection ($9.99, 4 coverage items)
Plan 2: HVAC Protection ($14.99, 5 coverage items)

Bottom summary card (gray bg):
- "Total Monthly HPP Investment" with Info icon
- $24.98 per month (large)
- Billing note (small text)

SERVICE HISTORY TAB:
Title + subtitle ("6 total service requests")
List of 6 service request cards (space-y-3):
- Each card: border rounded-lg p-4 hover:shadow-md
- Request ID + Status badge
- Title (bold)
- Description (2 lines)
- Footer with 3 items: HPP badge, Contractor, Rating
- Make cards clickable

LOYALTY TAB:
Featured card (purple gradient):
- 850 Points (large)
- Progress bar (850/1500 for Gold)
- "650 more points" message

2-column grid:
- How to Earn Points (4 bullets)
- Membership Tiers (3 tiers)

Points History:
- 4 transaction cards
- Green for earned (Plus icon)
- Red for redeemed (Minus icon)
- Each with description, date, points
```

---

## 📋 SCREEN 3: SERVICE REQUEST DETAIL

### Prompt 14: Service Request Header & Layout
```
Create src/pages/ServiceRequestDetail.tsx:

Import useParams, useNavigate from react-router-dom.
Import service request data from mockData.

TOP:
Back link: "← Back to Dashboard" (text-blue-600, clickable)

HEADER CARD (bg-white rounded-lg shadow-md p-6 mb-6):
- Top row (flex justify-between items-center):
  * Left: Request ID (text-2xl font-bold monospace) + 2 badges (Completed green, HPP Covered blue)
  * Right: 2 buttons - "Escalate" (red) + "Actions" (blue)
- Bottom row: 3 info items with icons (Created, Completed, Resolution Time)

MAIN LAYOUT:
Create grid-cols-3 gap-6 container:
- Left area: col-span-2 (main content)
- Right area: col-span-1 (sidebar)

Start with placeholder divs for each section.
We'll build content in next prompts.
```

### Prompt 15: Main Content - Customer & Service Details
```
Continue ServiceRequestDetail.tsx, build left column content:

CUSTOMER INFORMATION CARD:
- Title: "Customer Information" with User icon
- Flex layout:
  * Avatar (EM initials, large)
  * Name + Duke Native badge
  * 2-column grid of details (ID, Email, Phone, Address)
  * "View Full Profile →" link
- Import Avatar component

SERVICE DETAILS CARD (below customer card):
- Title: "Service Details" with ClipboardList icon
- Sections (space-y-4):

  1. Service Type:
     - Label (text-sm text-gray-600)
     - Value: "HPP - Annual Maintenance" (bold)

  2. Category:
     - Label
     - Value: "HVAC" with Wind icon (blue)

  3. Problem Description:
     - Label
     - Gray box (bg-gray-50 border rounded p-4):
       "Annual preventive maintenance for HVAC system as part of HVAC Protection Plan. Customer scheduled routine service appointment."

  4. Related Inventory Item:
     - Blue box (bg-blue-50 border-blue-200 rounded p-3):
       * Flex layout: Icon + Name/Model + "View Details →" link

  5. HPP Plan Coverage:
     - Green box (bg-green-50 border-green-200 rounded p-3):
       * Plan name + Active badge
       * Coverage note

Use proper spacing, consistent styling.
```

### Prompt 16: Contractor Notes & Admin Notes
```
Continue ServiceRequestDetail.tsx left column:

CONTRACTOR WORK NOTES CARD:
- Title: "Contractor Work Notes" with MessageSquare icon
- Two note entries (space-y-4):

Note 1 (larger, bg-gray-50 border rounded p-4):
- Header row:
  * HardHat icon + "Mike Thompson, Carolina Comfort Services"
  * Timestamp on right: "Nov 15, 2025 at 10:45 AM"
- Content paragraph
- Bullet list (ml-4 space-y-1):
  * 7 work items performed
  * Each with bullet point (•)
- Footer paragraph with recommendation

Note 2 (smaller, bg-blue-50 border-blue-200 rounded p-3):
- Same contractor, earlier time
- Shorter content: "Arrived on-site. Customer very friendly. Starting annual maintenance inspection."

ADMIN NOTES CARD:
- Title: "Admin Notes"
- "Add Note" button on right (blue, Plus icon)
- One note card (bg-yellow-50 border-yellow-200 rounded p-3):
  * Title + Date (flex justify-between)
  * Content paragraph
  * Author line: "— Jessica Davis"

Use consistent spacing, proper text sizing.
```

### Prompt 17: Sidebar - Contractor & Schedule
```
Continue ServiceRequestDetail.tsx, build right sidebar (space-y-6):

CONTRACTOR INFORMATION CARD:
- Title: "Contractor" with HardHat icon
- Centered section:
  * Large Building icon in blue circle (w-16 h-16)
  * Company name (font-semibold)
  * Type: "Primary HVAC Contractor" (text-xs text-gray-500)
  * 5 gold stars + 5.0 rating
- Contact details (left-aligned, text-sm, space-y-2):
  * Technician: Mike Thompson (User icon)
  * Phone: (919) 555-0987 (Phone icon)
  * Email: dispatch@carolinacomfort.com (Mail icon, text-xs)
  * Service Area: Durham, Raleigh, Chapel Hill (MapPin icon)
- "Reassign Contractor" button (full width, white with blue border, RefreshCw icon)

SCHEDULE CARD:
- Title: "Schedule" with Calendar icon
- Key-value pairs (space-y-3):
  * Each pair: Label (text-xs text-gray-600) + Value (text-sm font-semibold text-gray-800)
  * Scheduled Date: Friday, November 15, 2025
  * Time Window: 8:00 AM - 11:00 AM
  * Actual Arrival: 8:15 AM
  * Completion Time: 10:45 AM
  * Duration: 2 hours 30 minutes

Use white cards, shadow, rounded corners, padding.
```

### Prompt 18: Sidebar - Timeline & Quick Actions
```
Continue ServiceRequestDetail.tsx sidebar:

STATUS HISTORY CARD:
- Title: "Status History" with Clock icon
- Vertical timeline using TimelineItem component:
  * Import TimelineItem
  * 5 events:
    1. Completed (green dot): "Service completed successfully. Customer satisfaction rating: 5/5" • Nov 15, 10:45 AM
    2. On-Site (blue dot): "Contractor arrived at property" • Nov 15, 8:15 AM
    3. En Route (purple dot): "Contractor en route to customer location" • Nov 15, 7:50 AM
    4. Assigned (indigo dot): "Assigned to Carolina Comfort Services" • Nov 11, 9:30 AM
    5. Requested (yellow dot, isLast=true): "Service request created by customer via mobile app" • Nov 10, 2:15 PM

QUICK ACTIONS CARD:
- Title: "Quick Actions" with Zap icon
- 4 stacked buttons (space-y-2, full width):
  1. "Update Status" (primary blue, RefreshCw icon)
  2. "Export Details" (white with border, Download icon)
  3. "Email Customer" (white with border, Mail icon)
  4. "Cancel Request" (white with red border + red text, XCircle icon)

Each button: flex items-center justify-center, icon on left, proper padding.

Test the entire page layout, verify responsive behavior.
```

---

## 📝 SCREEN 4: ENROLLMENT QUEUE

### Prompt 19: Enrollment Queue Header & Stats
```
Create src/pages/EnrollmentQueue.tsx:

PAGE HEADER (mb-6):
- Title: "HPP Enrollment Queue" (text-2xl font-bold)
- Subtitle: "Manual processing for customer enrollments (MVP fallback)" (text-gray-600)

SUMMARY CARDS (grid-cols-4 gap-4 mb-6):
Use KPICard component for 4 cards:

1. Pending:
   - Icon: Clock (yellow)
   - Value: 8
   - Subtitle: "Awaiting review"
   - Border: yellow-500

2. In Progress:
   - Icon: Loader (blue, can use RefreshCw)
   - Value: 4
   - Subtitle: "Being processed"
   - Border: blue-500

3. Processed Today:
   - Icon: CheckCircle (green)
   - Value: 15
   - Trend: { value: "25%", direction: "up" }
   - Subtitle: "vs yesterday"
   - Border: green-500

4. Avg Process Time:
   - Icon: Timer (gray)
   - Value: "12m"
   - Subtitle: "Per enrollment"
   - Border: gray-500

Wrap in max-w-7xl mx-auto px-8 py-6 container.
```

### Prompt 20: Filters Section
```
Continue EnrollmentQueue.tsx, add filters (white card, mb-6):

Grid layout (grid-cols-4 gap-4):

Column 1 - Status Filter:
- Label: "Status"
- Select dropdown:
  * Options: All Statuses, Pending, In Progress, Processed
  * Tailwind select styling
  * border rounded-lg px-3 py-2

Column 2 - Date Range:
- Label: "Date Range"
- Select dropdown:
  * Options: Today, Last 7 Days, Last 30 Days, Custom

Column 3 - Assigned To:
- Label: "Assigned To"
- Select dropdown:
  * Options: All Admins, Jessica Davis (Me), Mark Thompson, Sarah Chen, Unassigned

Column 4 - Search:
- Label: "Search"
- Text input with search icon:
  * Placeholder: "Name, email, or phone"
  * Relative positioning for icon
  * Search icon positioned absolute left-3 top-3

Each filter:
- Label: block text-sm font-medium text-gray-700 mb-2
- Input: w-full border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500

Card: bg-white rounded-lg shadow-md p-6
```

### Prompt 21: Enrollment Queue Table
```
Continue EnrollmentQueue.tsx, create table card:

Import enrollmentQueue from mockData.
Import Avatar and StatusBadge components.

TABLE CARD HEADER (px-6 py-4 border-b flex justify-between):
- Title: "Queue (12 items)"
- Right side buttons:
  * "Export" (white with border, FileDown icon)
  * "Refresh" (blue border, RotateCw icon)

TABLE (w-full):
Columns: Customer, Contact, Requested Plans, Submitted, Status, Assigned To, Actions

5 Sample Rows:

Row 1 - Pending:
- Avatar: "RM" (purple bg)
- Name: Robert Martinez + "New Customer" (gray, small)
- Email: robert.martinez@email.com
- Phone: (919) 555-0234
- Plans: 2 blue badges (Water Heater, HVAC)
- Submitted: Nov 19, 2025 + 9:15 AM (small)
- Status: StatusBadge "pending"
- Assigned: "Unassigned" (gray text)
- Actions: "Process" (blue button) + "Assign to Me" (white button)

Row 2 - Pending (similar to Row 1):
- Lisa Wong, Duke Customer, 1 plan (Plumbing)

Row 3 - In Progress (bg-blue-50):
- David Kim, P&G Customer
- Status: StatusBadge "in-progress"
- Assigned: Avatar + "Jessica Davis"
- Actions: "Continue" (blue) + "View" (white)

Row 4 - In Progress:
- Jennifer Taylor, 2 plans
- Assigned to: Mark Thompson

Row 5 - Processed (bg-green-50):
- Michael Patel
- Status: StatusBadge "completed"
- Actions: "View" button only

TABLE FOOTER - Pagination (px-6 py-4 border-t flex justify-between):
- Left: "Showing 1-5 of 12 enrollments"
- Right: Page buttons (Previous disabled, 1 active, 2, 3, Next)

Style: bg-white rounded-lg shadow-md overflow-hidden
```

### Prompt 22: Process Enrollment Modal - Setup
```
Continue EnrollmentQueue.tsx, create modal:

Add state:
- const [isModalOpen, setIsModalOpen] = useState(false)
- const [modalStep, setModalStep] = useState(1)
- const [selectedCustomer, setSelectedCustomer] = useState(null)

Create modal JSX (at end of component):

MODAL STRUCTURE:
- Overlay (if isModalOpen):
  * fixed inset-0 bg-black bg-opacity-50 z-50
  * onClick to close modal
- Modal Content:
  * fixed inset-0 flex items-center justify-center z-50
  * Content box: bg-white rounded-lg shadow-xl max-w-3xl w-full mx-4 max-h-[90vh] overflow-auto
  * Stop propagation on content onClick

MODAL HEADER (bg-duke-blue px-6 py-4 rounded-t-lg flex justify-between):
- Title: "Process Enrollment" (text-xl font-bold text-white)
- Close button: X icon (white, hover effect)

MODAL BODY (p-6):
- Conditionally render based on modalStep:
  * Step 1: Search CRM content
  * Step 2: Select Plans content
  * Step 3: Review & Submit content

Connect "Process" button in table to open modal:
- onClick={() => { setIsModalOpen(true); setModalStep(1); }}

We'll build step content in next prompts.
```

### Prompt 23: Modal Step 1 - Search CRM
```
Continue EnrollmentQueue.tsx modal, create Step 1 content:

INFO BANNER (bg-blue-50 border border-blue-200 rounded-lg p-4 mb-4):
- Title: "Customer: Robert Martinez" (text-lg font-semibold)
- Subtitle: "Step 1 of 3: Search for existing customer in CRM" (text-sm text-gray-600)

SEARCH INPUT (mb-4):
- Label: "Search CRM"
- Input with search icon:
  * Placeholder: "Search by account #, email, phone, or address"
  * Full width, padded, pl-10 for icon
  * Search icon absolute positioned

SEARCH RESULTS (bg-gray-50 border rounded-lg p-4):
- Label: "Search Results:" (text-sm font-medium mb-3)
- 2 result cards (space-y-2):

Result Card 1:
- bg-white border rounded p-3 hover:bg-blue-50 cursor-pointer
- Flex layout justify-between
- Left side:
  * Name: "Robert Martinez" (text-sm font-semibold)
  * Account: "Duke Account: 3456789123 • robert.martinez@email.com" (text-xs text-gray-600)
  * Address: "1847 Elm Street, Durham, NC 27703" (text-xs text-gray-500)
- Right side:
  * "Select" button (blue)
  * onClick: setSelectedCustomer(result1), setModalStep(2)

Result Card 2:
- Similar structure, different data:
  * "Robert J. Martinez"
  * P&G Account: 9876543210

FOOTER (pt-4 border-t flex justify-between):
- Left: "Create New Customer" button (white, UserPlus icon)
- Right: "Cancel" button (white)

Use proper spacing, consistent with design system.
```

### Prompt 24: Modal Steps 2 & 3
```
Continue EnrollmentQueue.tsx modal:

STEP 2 - SELECT PLANS:
Info banner: "Step 2 of 3: Select HPP Plans"
Subtitle: "Customer requested: Water Heater, HVAC"

Plan selection cards (space-y-3):
- Create 2 checkboxes with plan cards
- Each card (border-2 rounded-lg p-4):
  * Checkbox (checked by default)
  * Title: Water Heater Protection Plan / HVAC Protection Plan
  * Code + Price: "WH-STD • $9.99/month" (text-xs text-gray-600)
  * Blue border if selected

Total price box (bg-gray-50 border rounded p-3):
- "Total Monthly Price:" label
- "$24.98" (text-2xl font-bold text-blue-600)

Footer:
- "Back" button (onClick: setModalStep(1))
- "Next: Review" button (blue, onClick: setModalStep(3))

STEP 3 - REVIEW & SUBMIT:
Info banner: "Step 3 of 3: Review & Submit"
Subtitle: "Verify enrollment details before submitting"

Customer Information card (white border rounded p-4 mb-4):
- Title: "Customer Information"
- 2-column key-value grid:
  * Name: Robert Martinez
  * Account: 3456789123 (monospace)
  * Email: robert.martinez@email.com
  * Phone: (919) 555-0234

Selected Plans card (white border rounded p-4):
- Title: "Selected Plans"
- Plan list with prices:
  * Water Heater Protection Plan: $9.99/mo
  * HVAC Protection Plan: $14.99/mo
  * Border top before total
  * Total: $24.98/mo (large, blue, bold)

Footer:
- "Back" button (onClick: setModalStep(2))
- "Submit Enrollment" button (green, CheckCircle icon)
  * onClick: alert success, close modal, reset step

Use React state for checkbox selections.
Test full modal flow.
```

---

## 🛡️ SCREEN 5: HPP PLANS MANAGEMENT

### Prompt 27: HPP Plans Page - Header & Stats Dashboard
```
Create src/pages/HppPlans.tsx:

PAGE HEADER (mb-6):
- Title: "Home Protection Plans" (text-2xl font-bold)
- Subtitle: "Manage plan offerings, pricing, and coverage" (text-gray-600)
- "Create New Plan" button (blue, Plus icon)

STATS DASHBOARD (grid-cols-4 gap-4 mb-6):
Use KPICard component for 4 cards:

1. Total Active Plans:
   - Icon: Shield (blue)
   - Value: 12
   - Subtitle: "Active Plan Types"
   - Trend: { value: "+2 this quarter", direction: "up" }

2. Total Enrollments:
   - Icon: Users (blue)
   - Value: "847,256"
   - Subtitle: "Active Enrollments"
   - Trend: { value: "+4.2% from last month", direction: "up" }

3. Monthly Recurring Revenue:
   - Icon: DollarSign (green)
   - Value: "$8.4M"
   - Subtitle: "Total MRR"
   - Trend: { value: "+$234K this month", direction: "up" }

4. Average Plans per Customer:
   - Icon: TrendingUp (green)
   - Value: "2.3"
   - Subtitle: "Plans/Customer"
   - Trend: { value: "+0.2 from last year", direction: "up" }

ENROLLMENT TREND CHART (white card, p-6 mb-6):
- Title: "Enrollment Trends - Last 12 Months" (text-lg font-semibold mb-4)
- Use Recharts LineChart (width: 100%, height: 300px):
  * Data: 12 months (Jan-Dec) with enrollments for 5 plan types
  * 5 lines: Water Heater (blue), HVAC (red), Line Protection (green), Electrical (purple), Plumbing (orange)
  * Legend at bottom
  * XAxis: Month names
  * YAxis: "Enrollments"
  * Tooltip with plan name and count

Sample data for chart:
const enrollmentData = [
  { month: 'Jan', WH: 11200, HVAC: 8300, Line: 20100, Elec: 7100, Plumb: 3800 },
  { month: 'Feb', WH: 11500, HVAC: 8500, Line: 20500, Elec: 7300, Plumb: 3900 },
  // ... continue for all 12 months with slight upward trends
];

Wrap in max-w-7xl mx-auto px-8 py-6 container.
```

### Prompt 28: HPP Plans Page - Plan Catalog Table
```
Continue HppPlans.tsx, add filters and table:

FILTERS SECTION (white card, p-4 mb-6):
Grid layout (grid-cols-3 gap-4):

Column 1 - Search:
- Input with Search icon
- Placeholder: "Search by plan name or code"
- value/onChange state

Column 2 - Category Filter:
- Label: "Category"
- Select dropdown:
  * Options: "All Categories", "Line Protection", "HVAC", "Appliances", "Plumbing", "Electrical", "Water Heater"

Column 3 - Status Filter:
- Label: "Status"
- Select dropdown:
  * Options: "All Statuses", "Active", "Inactive", "Draft"

PLANS TABLE (white card, p-6):
Columns: Plan Code | Plan Name | Category | Monthly Price | Active Enrollments | Monthly Revenue | Status | Actions

Sample data (12 plans) - create array:
const hppPlans = [
  { code: 'WH-STD', name: 'Water Heater Protection Plan', category: 'Water Heater', price: 9.99, enrollments: 125834, trend: '+2.1%', status: 'active' },
  { code: 'HVAC-PLUS', name: 'HVAC Protection Plan Plus', category: 'HVAC', price: 14.99, enrollments: 98456, trend: '+3.8%', status: 'active' },
  { code: 'LINE-WATER', name: 'Water Line Protection', category: 'Line Protection', price: 6.99, enrollments: 245123, trend: '+1.2%', status: 'active' },
  { code: 'LINE-SEWER', name: 'Sewer Line Protection', category: 'Line Protection', price: 7.99, enrollments: 198456, trend: '+0.8%', status: 'active' },
  { code: 'ELEC-BASIC', name: 'Electrical System Protection', category: 'Electrical', price: 12.99, enrollments: 87234, trend: '+4.5%', status: 'active' },
  { code: 'PLUMB-STD', name: 'In-Home Plumbing Protection', category: 'Plumbing', price: 11.99, enrollments: 45678, trend: '-1.2%', status: 'active' },
  { code: 'APPL-KITCHEN', name: 'Kitchen Appliance Bundle', category: 'Appliances', price: 19.99, enrollments: 34567, trend: '+5.6%', status: 'active' },
  { code: 'HVAC-BASIC', name: 'HVAC Protection Plan Basic', category: 'HVAC', price: 9.99, enrollments: 56789, trend: '+2.3%', status: 'active' },
  { code: 'ELEC-PLUS', name: 'Electrical System Plus', category: 'Electrical', price: 16.99, enrollments: 23456, trend: '+6.2%', status: 'active' },
  { code: 'WH-PREMIUM', name: 'Water Heater Premium', category: 'Water Heater', price: 14.99, enrollments: 12345, trend: '+8.1%', status: 'active' },
  { code: 'SMART-HOME', name: 'Smart Home Protection', category: 'Electrical', price: 24.99, enrollments: 4567, trend: 'new', status: 'active' },
  { code: 'POOL-HVAC', name: 'Pool & Spa HVAC', category: 'HVAC', price: 29.99, enrollments: 0, trend: '-', status: 'draft' },
];

Table rendering:
- Map through hppPlans array
- Category: render badge with colored background (tailwind based on category)
- Monthly Price: format as $X.XX
- Active Enrollments: show number with trend indicator (↑ green or ↓ red)
- Monthly Revenue: calculate (price × enrollments), format as $XXK or $X.XM
- Status: render StatusBadge (active=green, inactive=gray, draft=yellow)
- Actions: 3-dot menu (MoreVertical icon) with dropdown:
  * Edit Plan
  * View Enrollments
  * Duplicate Plan
  * Change Status
  * View Analytics

Add sorting functionality (useState for sortColumn and sortDirection).
Clicking column headers should sort table.

Table footer:
- "Showing 1-12 of 12 plans"

Make table sortable, hoverable rows (hover:bg-blue-50).
```

### Prompt 29: HPP Plans - Create/Edit Plan Modal
```
Add plan creation modal to HppPlans.tsx:

State: const [showPlanModal, setShowPlanModal] = useState(false);
State: const [modalTab, setModalTab] = useState(1); // tabs 1-4

MODAL (when showPlanModal is true):
- max-w-3xl
- Title: "Create New HPP Plan"
- Close button (X)

TABS (mb-6):
4 tabs with underline indicator:
1. "Basic Information" (active: blue underline)
2. "Pricing & Billing"
3. "Coverage Details"
4. "Terms & Conditions"

TAB 1 - BASIC INFORMATION (when modalTab === 1):

Form fields (space-y-4):

1. Plan Code:
   - Label: "Plan Code" (required)
   - Input: placeholder "e.g., HVAC-PLUS"
   - Helper text: "Unique identifier (uppercase, hyphens allowed)"

2. Plan Name:
   - Label: "Plan Name" (required)
   - Input: placeholder "e.g., HVAC Protection Plan Plus"
   - Helper text: "Customer-facing plan name"

3. Category:
   - Label: "Category" (required)
   - Select: "Line Protection", "HVAC", "Appliances", "Plumbing", "Electrical", "Water Heater"

4. Short Description:
   - Label: "Short Description"
   - Textarea (rows=3): placeholder "Brief description for marketing materials"
   - Character count: "0/150"

5. Coverage Description:
   - Label: "Coverage Description"
   - Textarea (rows=5): placeholder "Detailed coverage information for customers"
   - Character count: "0/500"
   - Helper text: "This appears in plan details on customer app"

TAB 2 - PRICING & BILLING (when modalTab === 2):

6. Monthly Price:
   - Label: "Monthly Price" (required)
   - Input with $ prefix: placeholder "9.99"
   - Helper text: "Recurring monthly charge"

7. Installation Fee:
   - Label: "Installation Fee"
   - Input with $ prefix: placeholder "0.00"
   - Checkbox: "Waive for Duke native customers"

8. Service Call Fee:
   - Label: "Service Call Fee"
   - Radio buttons: "$0 (Fully covered)", "$75", "$95", "Custom"

9. Annual Service Limit:
   - Label: "Annual Service Limit"
   - Radio buttons: "Unlimited", "2", "3", "4", "Custom"

10. Billing Eligibility:
    - Label: "Billing Eligibility"
    - Checkboxes:
      ☑ Duke Energy utility bill
      ☑ Credit/Debit card
      ☐ Contractor direct billing

TAB 3 - COVERAGE DETAILS (when modalTab === 3):

11. Covered Components:
    - Label: "Covered Components"
    - Multi-tag input (like chips)
    - Example tags: "Compressor", "Condenser", "Evaporator Coil", "Air Handler"
    - "+ Add Component" button

12. Exclusions:
    - Label: "Exclusions"
    - Multi-tag input
    - Example tags: "Pre-existing damage", "Improper installation", "Cosmetic issues"

13. Eligibility Requirements:
    - Label: "Eligibility Requirements"
    - Checkboxes:
      ☐ System must be less than 10 years old
      ☐ Inspection required before enrollment
      ☐ Duke Energy customer only
      ☐ Home must be primary residence

14. Waiting Period:
    - Label: "Waiting Period"
    - Select: "No waiting period", "30 days", "60 days", "90 days"

TAB 4 - TERMS & CONDITIONS (when modalTab === 4):

15. Contract Terms:
    - Label: "Contract Terms"
    - Textarea (rows=8) with sample contract text

16. Cancellation Policy:
    - Label: "Cancellation Policy"
    - Radio buttons:
      ○ Cancel anytime, no fee
      ○ 30-day notice required
      ○ Minimum 12-month commitment
      ○ Custom policy

17. Auto-Renewal:
    - Label: "Auto-Renewal"
    - Toggle switch (ON/OFF)
    - Helper text: "Automatically renew plan annually"

MODAL FOOTER (border-t pt-4):
- Left side: "Cancel" button (white)
- Right side (flex gap-2):
  * "Save as Draft" button (white)
  * "Publish Plan" button (blue)
  * If not on tab 4, show "Next" button to increment modalTab

Add tab navigation (Previous/Next buttons).
Form autosave notification: "Draft saved" (after 30s timeout).
```

### Prompt 30: HPP Plans - Plan Details View
```
Create plan details view that opens when clicking a table row:

Create new state: const [selectedPlan, setSelectedPlan] = useState(null);

When selectedPlan exists, show plan details view instead of table:

PLAN DETAILS HEADER:
- Back button (ArrowLeft icon) + "Back to Plans" (onClick: setSelectedPlan(null))
- Plan icon (based on category: Shield, Zap, Home, Droplet, Wrench)
- Plan Code badge: "HVAC-PLUS" (blue)
- Plan Name: "HVAC Protection Plan Plus" (text-2xl font-bold)
- Status badge: "Active" (green)
- Actions dropdown (right side):
  * Edit Plan
  * Change Status
  * Duplicate Plan
  * View Customer Feedback
  * Download Report

OVERVIEW STATS (grid-cols-4 gap-4 mb-6):
4 KPI cards:

1. Active Enrollments: "98,456" (trend +3.8%)
2. Monthly Revenue: "$1,476,293" (trend +$51,234)
3. Average Customer Tenure: "4.7 years" (trend +0.3 years)
4. Customer Satisfaction: "4.6/5.0" (92% satisfaction)

TABS SECTION (5 tabs):
1. Plan Details
2. Enrollment Analytics
3. Revenue Analytics
4. Service Utilization
5. Customer Feedback

TAB 1 - PLAN DETAILS:

Section cards (space-y-4):

Basic Information card:
- Category: "HVAC" (with icon)
- Monthly Price: "$14.99"
- Service Call Fee: "$0 (Fully covered)"
- Annual Limit: "Unlimited service calls"
- Waiting Period: "30 days"

Coverage card:
- Covered Components (list with checkmarks):
  * Compressor
  * Condenser
  * Evaporator Coil
  * Air Handler
  * Thermostat
  * Refrigerant Lines
- Exclusions (list with X icons):
  * Pre-existing damage
  * Improper installation
  * Cosmetic issues
  * Filters

Eligibility card:
- Requirements (list):
  * System must be less than 10 years old
  * Duke Energy customer preferred
  * Home must be primary residence

Terms card:
- Contract terms (expandable text)
- Cancellation policy: "Cancel anytime, no fee"
- Auto-renewal: "Yes"

TAB 2 - ENROLLMENT ANALYTICS:

Chart 1: Enrollment Trends (LineChart, 12 months)
- New enrollments per month (blue line)
- Cancellations per month (red line)
- Net growth (green area)

Chart 2: Enrollment by Customer Type (PieChart)
- Duke Native with Utility Billing: 68%
- Duke Native with Card: 22%
- Non-Native: 10%

Metrics table:
- Total lifetime enrollments: 145,234
- Active enrollments: 98,456
- Cancelled: 46,778
- Cancellation rate: 8.2% annually
- Average duration: 4.7 years
- Reactivation rate: 12%

TAB 3 - REVENUE ANALYTICS:

Chart: Monthly Revenue Trend (AreaChart, 12 months)
- Recurring revenue (blue)
- Installation fees (green)
- Total (dark blue)

Metrics:
- Total MRR: $1,476,293
- Average per enrollment: $14.99
- Total YTD: $16.2M
- Projected annual: $19.8M
- Growth rate: +4.2% YoY

TAB 4 - SERVICE UTILIZATION:

Chart 1: Service Requests per Month (BarChart)
Chart 2: Average Cost per Service Call (LineChart)

Metrics:
- Total calls (12mo): 34,567
- Avg per enrollment: 0.35/year
- Most common reason: "Compressor failure" (32%)
- Avg repair cost: $850
- Claims ratio: 57%

TAB 5 - CUSTOMER FEEDBACK:

Rating distribution (BarChart):
- 5 stars: 68%
- 4 stars: 24%
- 3 stars: 5%
- 2 stars: 2%
- 1 star: 1%

Recent reviews (list of 5):
- Customer name + avatar
- Star rating (5 stars)
- Date
- Comment text
- Link to customer profile

Common themes (tag cloud):
- "Fast service" (152 mentions)
- "Great value" (98 mentions)
- "Professional contractors" (87 mentions)

Use Recharts for all charts. Add tab state management.
```

---

## ✅ FINAL STEPS

### Prompt 31: Responsive Design & Polish
```
Review all pages (Dashboard, Customer Profile, Service Request Detail, Enrollment Queue, HPP Plans) and make responsive:

1. Adjust grid layouts for mobile:
   - grid-cols-4 → sm:grid-cols-2 lg:grid-cols-4
   - grid-cols-2 → lg:grid-cols-2
   - grid-cols-3 → lg:grid-cols-3

2. Make sidebar collapsible on mobile:
   - Add hamburger menu icon
   - Sidebar slides out on mobile
   - Overlay when open

3. Make tables horizontally scrollable on mobile:
   - Wrap tables in overflow-x-auto

4. Adjust text sizes for mobile:
   - Large headings: text-xl lg:text-2xl
   - Cards: p-4 lg:p-6

5. Test modal on mobile:
   - max-w-3xl → max-w-full on sm
   - Adjust padding

6. Add loading states:
   - Skeleton loaders for tables
   - Loading spinner for modal submission

7. Add hover/focus states:
   - All buttons should have hover effect
   - Links should have hover color change
   - Cards should have hover shadow increase

8. Test navigation:
   - All NavLinks should work
   - Back buttons should navigate correctly
   - Breadcrumbs if needed
```

### Prompt 32: Add Interactivity & State Management
```
Enhance interactivity across pages:

1. Dashboard:
   - Quick Actions should navigate to respective pages
   - Table rows should navigate to detail pages
   - Chart should be interactive (tooltips)

2. Customer Profile:
   - Tab switching should work smoothly
   - Edit Profile button should show modal (build simple form modal)
   - Send Message button should show message composer
   - Service request cards should link to detail page

3. Service Request Detail:
   - "Reassign Contractor" button shows contractor selection modal
   - "Update Status" shows status update form
   - "Add Note" shows note form
   - All actions show confirmation before executing

4. Enrollment Queue:
   - Filters should actually filter the table (use useMemo)
   - Search should work (filter by name/email/phone)
   - "Assign to Me" button should update row
   - Pagination should work (slice data array)

5. HPP Plans:
   - Table filters (search, category, status) should work (use useMemo)
   - Clicking table row should show plan details view
   - Tab switching in plan details should work
   - Create/edit modal should have working tab navigation
   - Plan modal form validation should work
   - "Duplicate Plan" should copy all data to new plan

6. Add toast notifications:
   - Install react-hot-toast
   - Show success/error toasts for actions
   - Success: green, Error: red

7. Add form validation:
   - Modal forms should validate before submit
   - Show error messages for required fields
```

---

## 🎨 OPTIONAL ENHANCEMENTS

### Additional Features (if time permits):

```
1. Add dark mode toggle:
   - Use Tailwind dark: classes
   - Store preference in localStorage
   - Toggle in user profile menu

2. Add keyboard shortcuts:
   - Cmd/Ctrl + K for search
   - Esc to close modals
   - Arrow keys for table navigation

3. Add animations:
   - Framer Motion for page transitions
   - Smooth tab switching
   - Modal slide-in animations
   - Loading skeletons

4. Add export functionality:
   - Export table data to CSV
   - Print service request details
   - Download PDF reports

5. Add bulk actions:
   - Select multiple enrollments
   - Batch assign to admin
   - Batch status update

6. Add real-time updates:
   - WebSocket connection simulation
   - Live notification updates
   - Auto-refresh dashboard metrics

7. Add advanced search:
   - Global search (Cmd+K)
   - Search across all entities
   - Recent searches history

8. Add user preferences:
   - Save filter preferences
   - Customize dashboard layout
   - Set notification preferences
```

---

## 📋 TESTING CHECKLIST

Before finalizing, test:

✅ All navigation links work
✅ All buttons have proper hover states
✅ All modals open and close correctly
✅ All forms validate properly
✅ All tables are sortable/filterable
✅ Responsive design works on mobile/tablet/desktop
✅ No console errors
✅ Icons render correctly
✅ Colors match Duke Energy brand
✅ Typography is consistent
✅ Spacing is consistent throughout
✅ Loading states display properly
✅ Error states display properly
✅ Success messages display properly

---

**END OF PROMPTS**

Copy these prompts one by one into Lovable in the order listed.
Build incrementally and test after each major section.

Good luck! 🚀
