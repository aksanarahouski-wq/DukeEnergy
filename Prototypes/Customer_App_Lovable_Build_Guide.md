# Customer Mobile App - Lovable Build Guide
## Duke Energy Residential Solutions Home Services App

**Created:** November 20, 2025
**Last Updated:** Based on Customer App Preliminary Scope (Session 3)
**Purpose:** Complete guide for building customer-facing mobile app prototypes in Lovable.dev
**Target Platform:** Mobile-first (iOS/Android) with responsive web support
**Reference:** Based on Customer_App_Preliminary_Scope_and_Flows.md

---

## ⚠️ IMPORTANT MVP UPDATES (Session 3)

**This guide reflects key scope changes from Session 3 discovery workshop:**

1. **Contractor Assignment**: Pre-assigned primary contractor only (NO marketplace/selection in MVP)
2. **Payment Processing**: Contractors collect on-site (NO in-app payment in MVP)
3. **Contractor Ratings**: NOT displayed in MVP (external survey only)
4. **Emergency Services**: Routed to phone call (NOT booked in app)
5. **Pizza Tracker / GPS**: Confirmed Phase 2 only (NOT in MVP)
6. **Status Updates**: Manual admin updates only - 3 statuses (Pending Confirmation, Confirmed, Completed)
7. **Contractor Inventory**: NEW feature - contractors can add inventory during service visits

**What This Means for Build:**
- Simpler booking flow (no contractor marketplace UI)
- No payment integration/forms needed for MVP launch
- Limited appointment statuses (no real-time GPS tracking)
- Emphasis on "call us" fallbacks for exceptions
- Phase 2 enhancements clearly marked throughout guide

---

## Table of Contents
1. [Duke Energy Mobile Design System](#duke-energy-mobile-design-system)
2. [App Architecture & Navigation](#app-architecture--navigation)
3. [MVP Screens Overview](#mvp-screens-overview)
4. [Screen 1: Home Dashboard](#screen-1-home-dashboard)
5. [Screen 2: Book Service](#screen-2-book-service)
6. [Screen 3: My Home (Inventory)](#screen-3-my-home-inventory)
7. [Screen 4: My Plans](#screen-4-my-plans)
8. [Screen 5: My Appointments](#screen-5-my-appointments)
9. [Screen 6: Service History](#screen-6-service-history)
10. [Screen 7: My Account](#screen-7-my-account)
11. [Reusable Components](#reusable-components)
12. [Sample Data](#sample-data)

---

## Duke Energy Mobile Design System

### Color Palette (Mobile Optimized)

```css
/* Primary Brand Colors */
--duke-blue: #0066CC
--duke-blue-dark: #0052A3
--duke-blue-light: #E6F2FF
--duke-blue-hover: #0055B3

/* Status Colors */
--success: #28A745
--warning: #FFC107
--danger: #DC3545
--info: #17A2B8

/* Neutral Colors */
--white: #FFFFFF
--gray-50: #F8F9FA
--gray-100: #F1F3F5
--gray-200: #E9ECEF
--gray-300: #DEE2E6
--gray-400: #CED4DA
--gray-500: #ADB5BD
--gray-600: #6C757D
--gray-700: #495057
--gray-800: #343A40
--gray-900: #212529
--black: #000000

/* Overlay Colors */
--overlay: rgba(0, 0, 0, 0.5)
--overlay-light: rgba(0, 0, 0, 0.25)
```

### Typography (Mobile Optimized)

```css
/* Font Family */
--font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif
--font-mono: 'SF Mono', 'Roboto Mono', monospace

/* Font Sizes (Mobile First) */
--text-xs: 0.75rem      /* 12px - Captions, labels */
--text-sm: 0.875rem     /* 14px - Secondary text */
--text-base: 1rem       /* 16px - Body text */
--text-lg: 1.125rem     /* 18px - Subheadings */
--text-xl: 1.25rem      /* 20px - Card titles */
--text-2xl: 1.5rem      /* 24px - Screen titles */
--text-3xl: 1.875rem    /* 30px - Hero numbers */
--text-4xl: 2.25rem     /* 36px - Large numbers */

/* Font Weights */
--font-normal: 400
--font-medium: 500
--font-semibold: 600
--font-bold: 700

/* Line Heights */
--leading-tight: 1.25
--leading-normal: 1.5
--leading-relaxed: 1.75
```

### Mobile-Specific Spacing

```css
/* Safe Areas (iOS notch, Android nav) */
--safe-top: env(safe-area-inset-top)
--safe-bottom: env(safe-area-inset-bottom)

/* Spacing Scale */
--space-1: 0.25rem   /* 4px */
--space-2: 0.5rem    /* 8px */
--space-3: 0.75rem   /* 12px */
--space-4: 1rem      /* 16px */
--space-5: 1.25rem   /* 20px */
--space-6: 1.5rem    /* 24px */
--space-8: 2rem      /* 32px */

/* Touch Targets (Minimum 44x44px for accessibility) */
--touch-min: 44px
--button-height: 48px
--tab-bar-height: 60px
```

### Component Styles (Mobile)

**Cards:**
- Background: White
- Border: None (use shadow instead)
- Border Radius: 12px (larger for mobile)
- Shadow: 0 2px 8px rgba(0,0,0,0.08)
- Padding: 16px
- Active State: Scale down slightly (0.98)

**Buttons:**
- Primary: Blue background (#0066CC), white text
- Secondary: White background, blue border
- Tertiary: Transparent, blue text
- Border Radius: 12px
- Height: 48px (touch-friendly)
- Padding: 12px 24px
- Active State: Slightly darker + scale(0.98)

**Bottom Navigation:**
- Height: 60px + safe-area-inset-bottom
- Background: White
- Shadow: 0 -2px 8px rgba(0,0,0,0.08)
- Active Tab: Blue icon + blue text
- Inactive Tab: Gray icon + gray text

**Status Badges:**
- Border Radius: 16px (pill)
- Padding: 4px 12px
- Font Size: 12px
- Font Weight: 600

**Progress Bars:**
- Height: 8px
- Border Radius: 4px
- Background: Gray 200
- Fill: Duke Blue or gradient

---

## App Architecture & Navigation

### Navigation Structure

**Bottom Tab Bar (5 Tabs):**
1. **Home** (Home icon) → Dashboard
2. **Book** (Calendar/Plus icon) → Service Booking
3. **My Home** (House icon) → Inventory
4. **Plans** (Shield icon) → HPP Plans
5. **Account** (User icon) → Profile/Settings

**Top Navigation:**
- Status bar (system)
- Optional header (screen title + optional actions)
- Safe area padding for notch/island

**Modal Flows:**
- Service booking (full-screen)
- Appointment details
- Add inventory item
- Enroll in plan
- Payment method

**Navigation Patterns:**
- Tab bar always visible (except modals)
- Back button in top-left when in stack
- Swipe-to-go-back gesture
- Pull-to-refresh on list screens

### Screen Hierarchy

```
App Root
├── Tab Navigator
│   ├── Home Dashboard
│   ├── Book Service
│   │   ├── Select Service Type
│   │   ├── Select Inventory Item
│   │   ├── Describe Issue
│   │   ├── Select Contractor
│   │   ├── Select Date/Time
│   │   └── Confirm & Pay
│   ├── My Home
│   │   ├── Add Inventory Item
│   │   └── Item Details
│   ├── My Plans
│   │   └── Enroll in Plan
│   └── My Account
│       ├── Edit Profile
│       ├── Payment Methods
│       └── Settings
├── My Appointments (Accessible from Home)
│   └── Appointment Details
└── Service History (Accessible from Account)
    └── Service Details
```

---

## MVP Screens Overview

### Core Screens (MVP)

1. **Home Dashboard**
   - Profile completion score
   - Loyalty points
   - Quick actions (Book Service, Add to Inventory)
   - Upcoming appointments
   - Maintenance reminders
   - Home health score

2. **Book Service**
   - Service type selection (HPP covered vs. ad-hoc)
   - Issue description
   - Inventory selection/addition
   - Contractor matching
   - Date/time selection
   - Payment (if ad-hoc)
   - Confirmation

3. **My Home (Inventory)**
   - Profile completion progress
   - List of appliances/systems
   - Add new items (manual or barcode scan)
   - Item details (make, model, age, warranty)
   - Maintenance schedules

4. **My Plans**
   - Current HPP plans
   - Plan details
   - Available plans to enroll
   - Enrollment flow
   - Manage/cancel plans

5. **My Appointments**
   - Upcoming appointments
   - Past appointments
   - Appointment details
   - Reschedule/cancel
   - Track contractor (if FSM enabled)

6. **Service History**
   - All completed services
   - Service details
   - Invoices/receipts
   - Export options
   - Linked to inventory items

7. **My Account**
   - User profile
   - Payment methods
   - Notification preferences
   - Settings
   - Help & support

---

## Screen 1: Home Dashboard

**Purpose:** Main landing screen showing customer's home health, quick actions, and engagement drivers

**Layout:** Single scroll view with sections

### Key Elements

1. **Header (Fixed)**
   - Welcome message: "Hi, Eleanor!"
   - Notification bell icon (badge if unread)
   - Safe area padding

2. **Home Health Card (Hero)**
   - Large card with gradient background
   - Home Health Score: 78/100 (large number)
   - Status: "Good" with icon
   - Subtitle: "2 items need attention"
   - Tap to expand → shows details

3. **Profile Completion Card**
   - Progress bar (e.g., 65% complete)
   - Title: "Complete Your Home Profile"
   - Subtitle: "Earn 50 points for each appliance added"
   - "Add Appliance" button
   - Gamification: Badge icons for milestones

4. **Loyalty Points Card**
   - Icon: Star
   - Points: 850 points
   - Value: "$8.50 toward services"
   - Progress to next tier: "150 more for Silver"
   - Small progress bar

5. **Quick Actions (2 Buttons)**
   - "Book Service" (primary blue, large)
   - "Add to Inventory" (secondary white, border)
   - Full width, stacked

6. **Upcoming Appointments Section**
   - Section title: "Upcoming Appointments" (with count badge)
   - Appointment cards (max 2 shown):
     * Service type icon
     * Contractor name
     * Date & time
     * Status badge
     * "View Details" link
   - "View All" link if more than 2

7. **Maintenance Reminders Section**
   - Section title: "Maintenance Reminders" (bell icon)
   - Reminder cards (max 3 shown):
     * Appliance name & icon
     * Reminder text: "Change HVAC filter"
     * Due date: "Due in 5 days"
     * Two buttons: "Mark Done" + "Book Service"
   - "View All Reminders" link

8. **Recent Activity**
   - Timeline of recent actions:
     * "Service completed: HVAC Maintenance" - 2 days ago
     * "Added water heater to inventory" - 5 days ago
     * "Earned 100 loyalty points" - 1 week ago
   - Small icon + timestamp for each

### Interactions

- Pull to refresh
- Tap Home Health Card → expands to show detailed breakdown
- Tap Profile Completion → navigates to My Home
- Tap Loyalty Points → navigates to rewards screen
- Tap "Book Service" → opens booking flow modal
- Tap appointment card → shows appointment details
- Swipe reminder card left → "Dismiss" or "Snooze"

---

## Screen 2: Book Service

**Purpose:** Multi-step flow for booking HPP covered or ad-hoc services

**Presentation:** Full-screen modal with step indicator

**MVP UPDATES (Session 3):**
- Emergency triage questions added in Step 3
- Contractor pre-assigned in Step 4 (no selection)
- Payment collected on-site (no in-app payment in Step 6)
- Booking status "Pending Confirmation" (manual admin confirmation required)

### Step Indicator
- Progress bar at top: Step X of 6
- Back button (top-left)
- Close X button (top-right, confirms cancellation)

### Step 1: Service Type Selection

**Layout:**
- Title: "What do you need help with?"
- 5 large category cards (2 columns):
  1. Heating & Cooling (🌡️ icon)
  2. Plumbing (🚰 icon)
  3. Electrical (⚡ icon)
  4. Appliances (🍳 icon)
  5. Water Heater (💧 icon)
- Each card shows icon + label
- Active state: Blue border

**Interaction:**
- Tap card → proceeds to Step 2
- Shows relevant inventory items in Step 2 based on selection

### Step 2: Select or Add Item

**If Customer Has Inventory in This Category:**
- Title: "Which [system] needs service?"
- List of customer's items:
  * Example: "Carrier HVAC - Living Room (8 years old)"
  * Tap to select
- "Add New Item" button at bottom
- "Skip - I'll describe it" link

**If No Inventory:**
- Title: "Tell us about your [system]"
- Quick add form:
  * Brand (dropdown with common brands + "Other")
  * Age (dropdown: <5 yrs, 5-10 yrs, 10-15 yrs, 15+ yrs)
  * Location (optional: Living room, Basement, etc.)
- "Save & Continue" button
- "Skip for Now" link (contractor will collect)

**Interaction:**
- Selecting item or completing form → proceeds to Step 3

### Step 3: Describe the Issue

**Layout:**
- Title: "What's the problem?"
- Symptom checklist (if applicable):
  * Common issues as checkbox options
  * Example for HVAC:
    - Not cooling/heating
    - Strange noise
    - Bad smell
    - Won't turn on
    - Other (opens text field)
- OR Free-text area:
  * Placeholder: "Describe the issue..."
  * Character count: 0/500

**MVP ADDITION (Session 3): Emergency Triage**
After user describes issue, show qualifying questions:
- If HVAC: "Is your home temperature below 60°F with freezing temps outside?"
- If Electrical: "Is anything sparking or smoking?"
- If Gas-related: "Do you smell gas?"

**If Emergency Detected:**
- Stop booking flow
- Show alert banner (red): "⚠️ This appears to be an emergency"
- Display: "Please call us immediately at 1-800-XXX-XXXX"
- For gas leaks: "🚨 SAFETY ALERT: Evacuate and call gas utility"
- "Call Now" button (links to phone)
- "This is NOT an emergency" link (continues booking)

**For HPP Customers (if NOT emergency):**
- Coverage check result:
  * ✅ "Likely covered under your [Plan Name]"
  * OR
  * ⚠️ "May not be covered. Estimated cost: $120-$180"
- Small print: "Final coverage determined by contractor"

**Interaction:**
- "Continue" button (always enabled if not emergency)
- If emergency detected → routes to phone call
- If not covered → continues to contractor assignment (same as covered in MVP)

### Step 4: Contractor Assignment (MVP UPDATED - Session 3)

**MVP APPROACH: PRE-ASSIGNED CONTRACTOR ONLY**
- Same experience for BOTH HPP covered AND ad-hoc services
- Customer does NOT select contractor
- System auto-assigns primary contractor based on trade + zip code
- Contractor marketplace deferred to Phase 2

**For ALL Services (HPP & Ad-Hoc):**
- Title: "Your Assigned Contractor"
- Single contractor card (large, pre-assigned):
  * Logo (if available)
  * Company name: "Carolina Comfort Services"
  * Badge: "Primary Contractor"
  * Brief description: "Licensed & insured HVAC specialists serving Durham since 2005"
  * Contact phone number: "(919) 555-0987"
  * Service area: "Serves Durham, NC"
  * NO rating displayed (Phase 2 feature)
- Card styling: Blue border, informational only (not selectable/clickable)

**For Ad-Hoc Services:**
- Display pricing on card:
  * Fixed price: "$99"
  * Variable price: "$120-$190"
- Payment info: "Payment collected by contractor at service completion"
- Accepted methods: "Cash, check, credit card"

**For HPP Covered Services:**
- Display: "$0 - Covered by your plan"
- No payment details needed

**Alternate Contractor Request:**
- Small text link below card: "Need a different contractor?"
- Tap → Shows modal:
  * "To request a different contractor, please call us at 1-800-XXX-XXXX"
  * "Our team will check availability and call you back within 2 hours"
  * Close button
- Does NOT show list of contractors (manual admin process)

**Info Banner:**
- "This contractor is assigned based on your location and service type"
- "They meet our quality and licensing requirements"

**Interaction:**
- No selection needed (contractor pre-assigned)
- "Continue" button always enabled
- Proceeds to Step 5 (date/time selection)

**Phase 2 Feature (Not in MVP):**
- Multiple contractor options with ratings
- Customer selection based on price/rating/availability
- In-app contractor reviews displayed

### Step 5: Select Date & Time

**Layout:**
- Title: "When works for you?"
- Calendar picker (week view, scrollable)
  * Available dates highlighted
  * Unavailable dates grayed out
  * Today and selected date marked
- Time slot selection:
  * Morning (8am-12pm)
  * Afternoon (12pm-4pm)
  * Evening (4pm-8pm)
  * Specific times (if contractor offers)
- Earliest available badge: "Soonest: Tomorrow at 9am"

**Buffer Communication:**
- Info banner:
  * "Emergency services available within 24 hours"
  * OR "Non-emergency: 3-5 business days"

**Interaction:**
- Select date + time → both required
- "Continue" button enabled when both selected
- Shows estimated arrival window: "Arrive between 9am-12pm"

### Step 6: Review & Confirm (MVP UPDATED - Session 3)

**Layout:**
- Title: "Review Your Booking"
- Summary sections:

  **Service Details:**
  - Service type: "HVAC Repair"
  - Item: "Carrier HVAC - Living Room"
  - Issue: "Strange grinding noise"
  - "Edit" link (goes back to step 3)

  **Contractor:**
  - Company name: "Carolina Comfort Services"
  - Contact phone: "(919) 555-0987"
  - NO rating displayed (Phase 2 feature)
  - "Edit" link (shows "Request Change" modal)

  **Schedule:**
  - Date: "Friday, March 15, 2025"
  - Time: "9:00 AM - 12:00 PM"
  - Add to calendar toggle (optional)
  - "Edit" link (back to step 5)

  **Cost:**
  - IF HPP:
    * "$0 - Covered by your plan"
    * Plan name: "HVAC Protection Plan"
    * "Service covered at no charge"
  - IF Ad-Hoc:
    * Price: "$99.00" (large, bold)
    * Payment method info below

**MVP PAYMENT APPROACH (Session 3): CONTRACTOR COLLECTS ON-SITE**

**For Ad-Hoc Services ONLY:**
- Section label: "Payment"
- Price: "$99.00" (large)
- Info banner (light blue):
  * Icon: Info circle
  * "Payment will be collected by your contractor at service completion"
- Accepted payment methods (with icons):
  * Cash
  * Check
  * Credit/Debit Card (via contractor's card reader)
- Small text: "Your contractor is equipped with secure payment processing"

**NO PAYMENT METHOD SELECTION IN MVP:**
- Remove "How would you like to pay?" section
- Remove Apple Pay/Google Pay/Credit Card options
- Remove "Pay Now" vs "Pay at Completion" toggle
- In-app payment deferred to Phase 2

**Booking Status Info:**
- Info banner:
  * "Your booking will be confirmed within 24 hours"
  * "We'll contact your contractor and update you once confirmed"
- For HPP: "Confirmation typically within 2-4 hours"

**Terms:**
- Checkbox: "I agree to terms and conditions"
- Link to terms (opens modal)
- Required to enable button
- Terms include: cancellation policy, contractor payment terms

**Actions:**
- "Confirm Booking" button (large, primary)
  * Disabled until terms checked
  * Full width, height 56px
  * OnPress: create booking (NO payment processing)

**Interaction:**
- Tap "Confirm Booking"
  * Show loading spinner: "Creating your booking..."
  * Create service request in backend
  * Navigate to confirmation screen
  * Show success animation

**Phase 2 Feature (Not in MVP):**
- In-app payment (Apple Pay, Google Pay, Credit Card)
- Customer pre-pays at booking
- Payment processed before confirmation

### Step 7: Confirmation (MVP UPDATED - Session 3)

**MVP STATUS APPROACH: MANUAL CONFIRMATION REQUIRED**

**Layout:**
- Success animation (checkmark)
- Title: "Booking Submitted!"
- Status badge: "Pending Confirmation" (yellow)
- Message: "We're contacting your contractor"

**Reference Number:**
- Label: "Service Request Number"
- Number: #SR-2025-1142 (monospace, large)
- Copy button

**Summary Card (compact):**
- Service: HVAC Repair
- Contractor: Carolina Comfort Services
- Requested Date: "Friday, March 15"
- Requested Time: "9:00 AM - 12:00 PM"
- Cost: $0 (HPP covered) or "$99 (pay at completion)"

**What Happens Next Card (prominent):**
- Icon: Clock
- Title: "What Happens Next?"
- Timeline/Steps:
  1. "We're contacting Carolina Comfort Services" (in progress icon)
  2. "Contractor confirms availability (within 24 hours)"
  3. "You'll receive confirmation notification"
  4. "Contractor will arrive at scheduled time"

**Info Banner:**
- Light blue background
- "You'll receive confirmation within 24 hours"
- "We'll notify you via [push/SMS/email] when your appointment is confirmed"
- Contact: "Questions? Call us at 1-800-XXX-XXXX"

**Actions:**
1. "View Appointment Status" (primary blue)
   - Navigate to appointment details (shows "Pending Confirmation")
2. "Back to Home" (secondary)
   - Navigate to home dashboard
3. "Book Another Service" (text button)

**NO "Add to Calendar" Yet:**
- Removed until appointment confirmed
- Will be available once contractor confirms
- Prevents calendar clutter with unconfirmed bookings

**Post-Confirmation:**
- Push notification: "Your service request has been submitted"
- Appointment added to "My Appointments" with status "Pending Confirmation"
- Update home dashboard with pending appointment
- Backend: Admin team receives notification to contact contractor

**Phase 2 Enhancement (With FSM):**
- Immediate confirmation: "Your appointment is confirmed!"
- Add to calendar available immediately
- No manual admin step required

---

## Screen 3: My Home (Inventory)

**Purpose:** Home inventory management with gamification

**Layout:** Scrollable list with sections

### Header (Fixed)
- Title: "My Home"
- Add button (+ icon, top-right)

### Profile Completion Section
- Large progress circle: 65% complete
- Title: "You're making great progress!"
- Subtitle: "5 of 12 appliances added"
- Reward progress:
  * "Add 2 more to earn 50 points"
  * Small progress bar

### Inventory Categories
Each category is an expandable section:

1. **Heating & Cooling (2 items)**
   - Card for each item:
     * Icon + item name: "Carrier HVAC - Living Room"
     * Age: 8 years old
     * Status badge: "Well Maintained" (green)
     * Last service: "Nov 15, 2025"
     * Next maintenance: "Nov 2026"
   - Tap → Item Details screen

2. **Plumbing (1 item)**
   - Water Heater card (similar layout)

3. **Electrical (0 items)**
   - Empty state:
     * Icon + "No electrical items yet"
     * "Add Item" button

4. **Appliances (3 items)**
   - Cards for dishwasher, refrigerator, washer

**Item Card Details:**
- Photo (if uploaded)
- Name + location
- Make/model (small text)
- Age (with warning if old)
- Warranty status:
  * "Under Warranty" (green) OR "Out of Warranty" (gray)
- HPP coverage badge (if covered)
- Quick actions:
  * "Book Service" button
  * Three-dot menu: Edit, Delete

### Add Item Flow (Modal)

**Step 1: Scan or Enter**
- Title: "Add Appliance or System"
- Two options:
  1. "Scan Barcode" (camera icon, large button)
  2. "Enter Manually" (keyboard icon, large button)

**Step 2: Item Details**
If scanned: Pre-fill what's found
If manual:
- Category (dropdown)
- Type (dropdown based on category)
- Brand (search/select)
- Model number (text field)
- Serial number (optional)
- Age/Install date (date picker)
- Location (dropdown)
- Photo (upload from camera/gallery)

**Step 3: Warranty Info**
- Warranty status (toggle)
- Warranty expires: (date picker)
- Upload warranty doc (optional)

**Confirmation:**
- "Add to My Home" button
- Shows points earned animation: "+50 points!"

---

## Screen 4: My Plans

**Purpose:** View and manage HPP plans

**Layout:** Scrollable with sections

### Current Plans Section
- Title: "My Protection Plans"
- Plan cards (stacked):

**Plan Card (Example: HVAC):**
- Icon: Shield with HVAC symbol
- Plan name: "Heating & Cooling Protection"
- Plan code: HVAC-PLUS (small, gray)
- Status badge: "Active" (green)
- Coverage summary:
  * "Covers repairs and annual maintenance"
  * "No deductible, no trip charges"
- Pricing:
  * $14.99/month
  * Billing method: "On your Duke Energy bill"
- Enrolled: "Since June 2020"
- Claims: "4 claims filed"
- Buttons:
  * "View Details" (secondary)
  * Three-dot menu: Upgrade, Manage, Cancel

**Total Investment Card:**
- Background: Light blue
- Icon: Info circle
- Text: "Total Protection Investment"
- Amount: $24.98/month (large, bold)
- Subtitle: "2 active plans"

### Available Plans Section
- Title: "Add More Protection"
- Subtitle: "Protect more of your home"
- Plan cards (browse):
  * Similar to current plans but with:
    - "Add Plan" button instead of Manage
    - Price comparison: "From $9.99/month"
    - What's covered (3 bullets)
    - "Learn More" link

### Plan Details Screen (Modal)

**Layout:**
- Hero section:
  * Large icon
  * Plan name
  * Monthly price
- What's Covered section:
  * Checkmark list of covered items
  * "What's NOT Covered" (expandable)
- FAQ section (expandable)
- Terms & Conditions (link)
- "Enroll Now" button (sticky at bottom)

### Enrollment Flow

**Step 1: Review Plan**
- Plan details summary
- Price breakdown
- "Continue" button

**Step 2: Payment Method**
- Choose billing method:
  * Add to utility bill (recommended)
  * Credit/debit card
  * ACH bank account
- For utility bill: Just needs confirmation
- For card/ACH: Payment form

**Step 3: Terms**
- Checkbox: Accept terms
- Digital signature (name)
- "Complete Enrollment" button

**Step 4: Confirmation**
- Success message
- Plan added to "My Plans"
- Email confirmation sent
- First billing date displayed

---

## Screen 5: My Appointments

**Purpose:** View and manage upcoming/past appointments

**Layout:** Tabbed list view

### Tabs (Segmented Control)
- "Upcoming" (default)
- "Past"

### Upcoming Appointments

**Appointment Card:**
- Status badge: "Confirmed" (blue) / "In Progress" (yellow) / "Completed" (green)
- Service type: "HVAC Repair"
- Date: "Friday, March 15"
- Time: "9:00 AM - 12:00 PM"
- Countdown: "In 2 days"
- Contractor:
  * Company name
  * Star rating
  * Phone number (tap to call)
- "Track Contractor" button (if FSM enabled, shows map)
- Actions:
  * "Reschedule" button
  * "Cancel" button (less prominent)
  * Three-dot menu: Add to calendar, Contact contractor

**Empty State:**
- Icon: Calendar with checkmark
- Text: "No upcoming appointments"
- "Book Service" button

### Past Appointments

**Appointment Card (Past):**
- Service type + icon
- Date: "Nov 15, 2025"
- Contractor + rating
- Status: "Completed"
- "Rate Service" button (if not rated)
- "View Details" button
- "Book Again" button (for ad-hoc services)

**Filter Options:**
- Dropdown: "All Services" / "HPP Only" / "Ad-Hoc Only"
- Date range picker

### Appointment Details Screen

**Layout:**
- Header: Back button + "Appointment Details"
- Status banner (colored):
  * Current status: "Confirmed" with icon
  * Estimated arrival (if en route)
- Service Information:
  * Type
  * Item serviced
  * Issue description
- Contractor Information:
  * Company name + logo
  * Technician name (if assigned)
  * Contact phone
  * Star rating
- Schedule:
  * Date
  * Time window
  * Add to calendar button
- Cost:
  * $0 (HPP) or price (ad-hoc)
  * Payment status (if ad-hoc)
- Status Timeline:
  * Requested → Confirmed → Contractor En Route → In Progress → Completed
  * Each step with timestamp

**Track Contractor (If Available):**
- Embedded map showing:
  * Customer's address (pin)
  * Contractor's location (moving pin)
  * ETA: "15 minutes away"
- "Call Contractor" button

**Actions:**
- "Reschedule" button (if >24 hours away)
- "Cancel Appointment" button
- "Report Issue" link

---

## Screen 6: Service History

**Purpose:** Complete record of all services

**Layout:** Filterable list

### Header
- Title: "Service History"
- Filter button (top-right)
- Export button (share icon)

### Filters (Bottom Sheet)
- Date range:
  * Last 30 days
  * Last 6 months
  * Last year
  * All time
  * Custom (date picker)
- Service type:
  * All services
  * HPP covered
  * Ad-hoc
- Category:
  * All categories
  * HVAC, Plumbing, Electrical, etc.
- Status:
  * Completed
  * Cancelled
- "Apply Filters" button

### Service Record Card
- Date: "Nov 15, 2025"
- Service type + icon
- Appliance: "Carrier HVAC - Living Room"
- Contractor: Company name + rating
- Technician: "Mike Thompson"
- Cost: $0 (HPP) or $99 (ad-hoc)
- Status badge: "Completed"
- "View Details" button

### Service Detail Screen

**Layout:**
- Service summary (same as card)
- Work Performed:
  * Detailed description from contractor
  * Bullet list of tasks completed
- Parts Used:
  * List of parts with costs (if applicable)
- Photos:
  * Before/after photos (if contractor added)
- Invoice:
  * "View Invoice" button → PDF
  * "Download" button
  * "Email to Me" button
- Linked Appliance:
  * "View in My Home" link
- Service Updates History:
  * Timeline of status changes
- Rating:
  * Star rating given
  * Written review (if any)
  * "Edit Rating" link

**Export Options:**
- Export single service (PDF)
- Export all history (CSV)
- Share with home buyer (generates link)

---

## Screen 7: My Account

**Purpose:** User profile and settings

**Layout:** Grouped list (iOS Settings style)

### Profile Section
- Large avatar (with edit button)
- Name: "Eleanor Mitchell"
- Email: eleanor.mitchell@email.com
- Phone: (919) 555-0142
- "Edit Profile" button

### Account Settings

**My Properties:**
- List of properties:
  * 2847 Oak Street, Durham, NC (Primary)
  * "Add Property" button

**Payment Methods:**
- Saved payment methods:
  * Visa •••• 4829 (default badge)
  * Duke Energy Bill
  * "Add Payment Method" button
- Each method has edit/delete

**Notification Preferences:**
- Push Notifications (toggle)
- SMS (toggle)
- Email (toggle)
- Reminder Frequency (dropdown)

**Communication Preferences:**
- Preferred contact method (radio):
  * Push
  * SMS
  * Email
- Appointment reminders (toggles):
  * 1 day before
  * Morning of
  * When contractor en route

### App Settings

**Security:**
- Change Password
- Enable Biometric Login (toggle)
- Two-Factor Authentication (toggle)

**Preferences:**
- Language: English (dropdown)
- Units: Imperial (dropdown)
- Theme: Light / Dark / Auto (segmented control)

### Support & Legal

**Help & Support:**
- FAQs
- Contact Support (opens chat or phone)
- Report a Problem

**Legal:**
- Terms of Service
- Privacy Policy
- Licenses

**About:**
- App Version: 1.0.0
- "Check for Updates" button

### Sign Out
- "Sign Out" button (red text)
- Confirmation alert

---

## Reusable Components

### Component Library

#### 1. ServiceCategoryCard
```typescript
interface ServiceCategoryCardProps {
  icon: string;
  label: string;
  onPress: () => void;
  isSelected?: boolean;
}
```
Large card for service type selection, icon + label, blue border when selected

#### 2. ContractorCard (MVP UPDATED - Session 3)
```typescript
interface ContractorCardProps {
  contractor: {
    name: string;
    logo?: string;
    phone: string;
    price?: number;
    description?: string;
    badge?: string; // e.g., "Primary Contractor"
  };
  onPress?: () => void;
  isPreAssigned?: boolean;
  showRequestChange?: boolean;
}
```
**MVP CHANGES:**
- NO rating or reviewCount (Phase 2 feature)
- NO availability field (static buffers used instead)
- NO isRecommended flag (not relevant when pre-assigned)
- NO isSelected state (contractor pre-assigned, not selectable)
- Displays contractor info for informational purposes only
- If isPreAssigned=true: Blue border, non-clickable
- If showRequestChange=true: Shows "Request Change" link

#### 3. AppointmentCard (MVP UPDATED - Session 3)
```typescript
interface AppointmentCardProps {
  appointment: {
    id: string;
    serviceType: string;
    date: string;
    time: string;
    contractor: string;
    status: 'pending-confirmation' | 'confirmed' | 'completed';
  };
  onPress: () => void;
}
```
**MVP CHANGES:**
- Added 'pending-confirmation' status (NEW for MVP)
- Removed 'in-progress' status (no real-time tracking in MVP)
- NO countdown for pending appointments (show "Awaiting confirmation")
- Countdown only shown for confirmed appointments
- Shows appointment summary with status badge

#### 4. InventoryItemCard
```typescript
interface InventoryItemCardProps {
  item: {
    id: string;
    name: string;
    category: string;
    brand: string;
    model: string;
    age: number;
    isUnderWarranty: boolean;
    isCovered: boolean;
    lastService?: string;
    nextMaintenance?: string;
    photo?: string;
  };
  onPress: () => void;
}
```
Displays inventory item with status badges and quick actions

#### 5. PlanCard
```typescript
interface PlanCardProps {
  plan: {
    id: string;
    name: string;
    code: string;
    price: number;
    billingMethod: string;
    status: 'active' | 'inactive';
    enrolledDate: string;
    claimsCount: number;
    coverageSummary: string[];
  };
  isEnrolled: boolean;
  onViewDetails: () => void;
  onEnroll?: () => void;
}
```
Displays HPP plan with pricing and coverage summary

#### 6. ProgressCircle
```typescript
interface ProgressCircleProps {
  percentage: number;
  size: number;
  strokeWidth: number;
  color: string;
  showLabel?: boolean;
}
```
Circular progress indicator for profile completion

#### 7. StatusBadge
```typescript
interface StatusBadgeProps {
  status: 'active' | 'inactive' | 'confirmed' | 'in-progress' | 'completed' | 'cancelled';
  size?: 'sm' | 'md';
}
```
Colored pill badge for status display

#### 8. QuickActionButton
```typescript
interface QuickActionButtonProps {
  icon: ReactNode;
  label: string;
  onPress: () => void;
  variant?: 'primary' | 'secondary';
}
```
Large touch-friendly button with icon for dashboard quick actions

#### 9. TimeSlotPicker
```typescript
interface TimeSlotPickerProps {
  availableSlots: Array<{ time: string; label: string }>;
  selectedSlot?: string;
  onSelect: (slot: string) => void;
}
```
Time slot selection component with visual indication

#### 10. BottomSheet
```typescript
interface BottomSheetProps {
  isOpen: boolean;
  onClose: () => void;
  children: ReactNode;
  snapPoints?: string[];
}
```
Reusable bottom sheet for filters, options, forms

---

## Sample Data

### Mock Data Structure

Create `src/data/mockData.ts`:

```typescript
// Customer Profile
export const currentCustomer = {
  id: "DKE-458923",
  firstName: "Eleanor",
  lastName: "Mitchell",
  email: "eleanor.mitchell@email.com",
  phone: "(919) 555-0142",
  customerType: "duke-native", // duke-native | p&g | non-native
  profileCompletionScore: 65,
  loyaltyPoints: 850,
  homeHealthScore: 78,
  properties: [
    {
      id: "prop-1",
      address: "2847 Oak Street",
      city: "Durham",
      state: "NC",
      zip: "27705",
      isPrimary: true,
      propertyType: "Single Family Home",
      squareFeet: 2400,
      yearBuilt: 1998
    }
  ],
  paymentMethods: [
    { id: "pm-1", type: "visa", last4: "4829", isDefault: true },
    { id: "pm-2", type: "duke-bill", label: "Duke Energy Bill" }
  ],
  notificationPreferences: {
    push: true,
    sms: true,
    email: true,
    reminderFrequency: "weekly"
  }
};

// HPP Plans
export const hppPlans = [
  {
    id: "plan-1",
    code: "WH-STD",
    name: "Water Heater Protection Plan",
    category: "water-heater",
    price: 9.99,
    billingMethod: "utility-bill",
    status: "active",
    enrolledDate: "2019-03-15",
    claimsCount: 2,
    coverageSummary: [
      "Repairs to water heater tank and components",
      "Labor and service calls included",
      "No deductible or trip charges",
      "Covers up to 50-gallon electric or gas units"
    ]
  },
  {
    id: "plan-2",
    code: "HVAC-PLUS",
    name: "HVAC Protection Plan",
    category: "hvac",
    price: 14.99,
    billingMethod: "utility-bill",
    status: "active",
    enrolledDate: "2020-06-10",
    claimsCount: 4,
    coverageSummary: [
      "Heating and cooling system repairs",
      "Annual maintenance visit included",
      "No deductible or trip charges",
      "Covers heat pumps, furnaces, and AC units",
      "Thermostat repairs included"
    ]
  }
];

// Home Inventory
export const inventory = [
  {
    id: "inv-1",
    category: "hvac",
    type: "Heat Pump",
    name: "Carrier HVAC",
    location: "Living Room",
    brand: "Carrier",
    model: "Infinity 3-Ton",
    serialNumber: "CAR123456789",
    installDate: "2020-06-15",
    age: 5,
    isUnderWarranty: true,
    warrantyExpires: "2035-06-15",
    isCoveredByHPP: true,
    hppPlanId: "plan-2",
    lastService: "2025-11-15",
    nextMaintenance: "2026-11-15",
    healthStatus: "good",
    photo: "/images/hvac-unit.jpg"
  },
  {
    id: "inv-2",
    category: "water-heater",
    type: "Electric Tank",
    name: "Rheem Water Heater",
    location: "Basement",
    brand: "Rheem",
    model: "ProTech 50-Gallon",
    installDate: "2019-03-20",
    age: 6,
    isUnderWarranty: true,
    warrantyExpires: "2029-03-20",
    isCoveredByHPP: true,
    hppPlanId: "plan-1",
    lastService: "2025-09-03",
    nextMaintenance: "2026-09-03",
    healthStatus: "good"
  },
  // Add more items...
];

// Appointments
export const appointments = [
  {
    id: "apt-1",
    serviceRequestId: "SR-2025-1142",
    customerId: "DKE-458923",
    propertyId: "prop-1",
    serviceType: "HVAC Maintenance",
    category: "hvac",
    inventoryItemId: "inv-1",
    description: "Annual preventive maintenance",
    status: "confirmed",
    isHPPCovered: true,
    hppPlanId: "plan-2",
    cost: 0,
    contractor: {
      id: "con-1",
      name: "Carolina Comfort Services",
      logo: "/images/contractor-logo.png",
      rating: 4.8,
      reviewCount: 245,
      phone: "(919) 555-0987",
      technician: "Mike Thompson"
    },
    scheduledDate: "2025-11-22",
    scheduledTime: "9:00 AM - 12:00 PM",
    createdDate: "2025-11-10T14:15:00",
    canReschedule: true,
    canCancel: true
  },
  // Add more appointments...
];

// Service History
export const serviceHistory = [
  {
    id: "srv-1",
    serviceRequestId: "SR-2025-1142",
    customerId: "DKE-458923",
    propertyId: "prop-1",
    serviceType: "HVAC Maintenance",
    category: "hvac",
    inventoryItemId: "inv-1",
    description: "Annual preventive maintenance for HVAC system",
    status: "completed",
    isHPPCovered: true,
    cost: 0,
    contractor: {
      name: "Carolina Comfort Services",
      technician: "Mike Thompson",
      rating: 5.0
    },
    scheduledDate: "2025-11-15",
    completedDate: "2025-11-15T10:45:00",
    workPerformed: [
      "Cleaned condenser coils",
      "Checked refrigerant levels - within normal range",
      "Replaced air filter (16x25x1 MERV 11)",
      "Tested thermostat operation - working properly",
      "Verified proper airflow throughout system"
    ],
    partsUsed: [],
    photos: ["/images/service-photo-1.jpg"],
    invoice: "/invoices/SR-2025-1142.pdf",
    customerRating: 5,
    customerReview: "Excellent service, very professional"
  },
  // Add more service history...
];

// Maintenance Reminders
export const maintenanceReminders = [
  {
    id: "rem-1",
    inventoryItemId: "inv-1",
    title: "Change HVAC Filter",
    description: "Replace air filter for optimal performance",
    dueDate: "2025-12-01",
    frequency: "quarterly",
    category: "hvac",
    priority: "medium",
    isDismissed: false,
    canBookService: true
  },
  {
    id: "rem-2",
    inventoryItemId: "inv-2",
    title: "Flush Water Heater",
    description: "Annual tank flush to remove sediment",
    dueDate: "2026-03-20",
    frequency: "annually",
    category: "water-heater",
    priority: "low",
    isDismissed: false,
    canBookService: true
  },
  // Add more reminders...
];

// Available Ad-Hoc Services
export const adHocServices = [
  {
    id: "svc-1",
    name: "HVAC Seasonal Cleaning & Check",
    category: "hvac",
    description: "22-point inspection, filter replacement, coil cleaning",
    price: 99,
    priceType: "fixed",
    rating: 4.7,
    reviewCount: 156,
    duration: "2 hours",
    availability: "Available this week"
  },
  {
    id: "svc-2",
    name: "Ceiling Fan Installation",
    category: "electrical",
    description: "Professional installation of customer-provided ceiling fan",
    priceMin: 120,
    priceMax: 190,
    priceType: "range",
    rating: 4.5,
    reviewCount: 89,
    duration: "1-2 hours",
    availability: "3-5 days"
  },
  // Add more services...
];

export default {
  currentCustomer,
  hppPlans,
  inventory,
  appointments,
  serviceHistory,
  maintenanceReminders,
  adHocServices
};
```

---

## Build Order Recommendation

### Phase 1: Foundation (Day 1)
1. Initialize Lovable project with React Native / React
2. Set up Duke Energy design tokens
3. Create bottom tab navigation
4. Build reusable components (buttons, cards, badges)
5. Create mock data file

### Phase 2: Core Screens (Days 2-3)
1. Home Dashboard (high priority)
2. My Home / Inventory (foundational feature)
3. My Plans (show existing plans)
4. My Account (settings)

### Phase 3: Booking Flow (Days 3-4)
1. Book Service - Service Type Selection
2. Book Service - Item Selection
3. Book Service - Issue Description
4. Book Service - Contractor Selection
5. Book Service - Date/Time Selection
6. Book Service - Review & Confirm
7. Book Service - Confirmation

### Phase 4: Supporting Screens (Day 5)
1. My Appointments
2. Appointment Details
3. Service History
4. Service Details

### Phase 5: Polish (Day 5-6)
1. Animations and transitions
2. Loading states
3. Empty states
4. Error handling
5. Responsive design testing
6. Accessibility (touch targets, labels)

---

**Document Version:** 1.0
**Last Updated:** November 20, 2025
**Created By:** Orases Product Team
**For:** Duke Energy Residential Solutions Customer Mobile App
