# Customer Mobile App - Lovable Build Prompts
## Copy-Paste Prompts for Duke Energy Home Services App

**Last Updated:** Based on Customer App Preliminary Scope (Session 3)
**Instructions:** Copy each prompt below directly into Lovable's chat interface. Build in the order listed.

---

## ⚠️ IMPORTANT MVP UPDATES (Session 3)

**These prompts reflect key scope changes from Session 3 discovery workshop:**

1. **Contractor Assignment**: Pre-assigned primary contractor only (NO marketplace/selection in MVP)
2. **Payment Processing**: Contractors collect on-site (NO in-app payment in MVP)
3. **Contractor Ratings**: NOT displayed in MVP (external survey only)
4. **Emergency Services**: Routed to phone call (NOT booked in app)
5. **Pizza Tracker / GPS**: Confirmed Phase 2 only (NOT in MVP)
6. **Status Updates**: Manual admin updates only - 3 statuses (Pending Confirmation, Confirmed, Completed)
7. **Contractor Inventory**: NEW feature - contractors can add inventory during service visits

**What This Means for Prototype:**
- Simpler booking flow (no contractor selection step complexity)
- No payment integration required for initial launch
- Limited appointment statuses (no real-time tracking)
- Focus on manual admin workflow with phone support as backup
- Phase 2 enhancements clearly marked throughout prompts

---

## 🚀 SETUP PHASE

### Prompt 1: Initialize Mobile App Project
```
Create a new React mobile application called "Duke Energy Home Services".
This is a MOBILE-FIRST app for iOS and Android customers.

Set up the following:
- React with mobile-optimized components
- React Router for navigation
- Tailwind CSS configured for mobile (touch targets, safe areas)
- Lucide React for icons
- Bottom tab navigation (not sidebar)

Configure Tailwind with Duke Energy mobile design system:

Primary colors:
- duke-blue: #0066CC
- duke-blue-dark: #0052A3
- duke-blue-light: #E6F2FF

Status colors:
- success: #28A745
- warning: #FFC107
- danger: #DC3545
- info: #17A2B8

Mobile-specific settings:
- Minimum touch target: 44px
- Bottom navigation height: 60px
- Border radius: 12px (larger for mobile)
- Font family: Inter
- Base font size: 16px (mobile optimized)

Create safe area support for iOS notch/island:
- Use env(safe-area-inset-top) and env(safe-area-inset-bottom)

Create folder structure:
- /components (reusable mobile components)
- /screens (main app screens)
- /navigation (tab navigation)
- /data (mock data)
- /types (TypeScript types)
```

### Prompt 2: Create Bottom Tab Navigation
```
Create a bottom tab navigation component (src/navigation/TabNavigation.tsx) with 5 tabs:

Tab bar design:
- Fixed at bottom of screen
- Height: 60px + safe-area-inset-bottom
- Background: white
- Top shadow: 0 -2px 8px rgba(0,0,0,0.08)
- No border, just shadow

5 Tabs (icons from lucide-react):
1. Home (Home icon) → /
   - Label: "Home"
2. Book (Calendar icon) → /book
   - Label: "Book"
3. My Home (House icon) → /my-home
   - Label: "My Home"
4. Plans (Shield icon) → /plans
   - Label: "Plans"
5. Account (User icon) → /account
   - Label: "Account"

Tab styling:
- Active tab:
  * Icon color: #0066CC (duke-blue)
  * Label color: #0066CC
  * Font weight: 600
  * Optional: small blue dot above icon

- Inactive tab:
  * Icon color: #6C757D (gray-600)
  * Label color: #6C757D
  * Font weight: 400

- Icon size: 24px
- Label: text-xs (12px)
- Each tab: flex-col items-center justify-center
- Minimum touch target: 44x44px

Create placeholder screen components for each tab:
- HomeScreen (/)
- BookServiceScreen (/book)
- MyHomeScreen (/my-home)
- PlansScreen (/plans)
- AccountScreen (/account)

Wrap app in TabNavigation component.
Use React Router to handle navigation.
```

### Prompt 3: Create Reusable Mobile Components - MVP UPDATED
```
Create 8 reusable mobile components in src/components/:

1. MobileCard.tsx:
interface MobileCardProps {
  children: ReactNode;
  onPress?: () => void;
  className?: string;
}
Styling: bg-white rounded-xl p-4 shadow-sm, active:scale-98 transition

2. StatusBadge.tsx:
interface StatusBadgeProps {
  status: 'active' | 'inactive' | 'pending-confirmation' | 'confirmed' | 'completed' | 'cancelled';
  size?: 'sm' | 'md';
}
Color mapping (MVP UPDATED - Session 3):
- active: green
- inactive: gray
- pending-confirmation: yellow (NEW for MVP)
- confirmed: blue
- completed: green
- cancelled: red
Styling: rounded-full px-3 py-1 text-xs font-semibold

3. QuickActionButton.tsx:
interface QuickActionButtonProps {
  icon: ReactNode;
  label: string;
  onPress: () => void;
  variant?: 'primary' | 'secondary';
}
Primary: bg-blue-600 text-white
Secondary: bg-white border border-gray-300
Height: 48px, rounded-xl, full-width

4. ProgressCircle.tsx:
interface ProgressCircleProps {
  percentage: number;
  size: number;
  color: string;
  showLabel?: boolean;
}
Use SVG to create circular progress indicator
Center label showing percentage

5. ContractorCard.tsx (MVP UPDATED - Session 3):
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
  isPreAssigned?: boolean; // NEW for MVP
  showRequestChange?: boolean; // NEW for MVP
}
**MVP CHANGES:**
- NO rating or reviewCount (Phase 2 feature)
- NO isRecommended flag (not relevant when pre-assigned)
- NO isSelected state (contractor is pre-assigned, not selectable)
- Card shows: logo, name, phone, description, badge, price (if ad-hoc)
- If isPreAssigned=true: Blue border, not clickable, informational only
- If showRequestChange=true: Shows "Request Change" link below card

6. AppointmentCard.tsx (MVP UPDATED):
interface AppointmentCardProps {
  appointment: {
    serviceType: string;
    date: string;
    time: string;
    contractor: string;
    status: 'pending-confirmation' | 'confirmed' | 'completed';
  };
  onPress: () => void;
}
Compact card showing appointment details, status badge
MVP: NO countdown for pending appointments (show "Awaiting confirmation")
Countdown only shown for confirmed appointments

7. InventoryItemCard.tsx:
interface InventoryItemCardProps {
  item: {
    name: string;
    category: string;
    brand: string;
    age: number;
    isCovered: boolean;
    lastService?: string;
    photo?: string;
  };
  onPress: () => void;
}
Card with: optional photo, name, brand, age, coverage badge, "Book Service" button

8. PlanCard.tsx:
interface PlanCardProps {
  plan: {
    name: string;
    code: string;
    price: number;
    status: string;
    coverageSummary: string[];
  };
  isEnrolled: boolean;
  onEnroll?: () => void;
  onManage?: () => void;
}
Large card with: shield icon, plan name, price, coverage bullets
Button changes based on enrollment status

Export all components as default.
Use mobile-optimized spacing and touch targets.

**MVP KEY CHANGES (Session 3):**
- ContractorCard: Removed ratings, simplified for pre-assigned contractor display
- AppointmentCard: Added "pending-confirmation" status support
- StatusBadge: Added "pending-confirmation" status
```

### Prompt 4: Create Mock Data
```
Create src/data/mockData.ts with sample customer data:

Export the following objects:

1. currentCustomer:
   - id: "DKE-458923"
   - firstName: "Eleanor"
   - lastName: "Mitchell"
   - email: "eleanor.mitchell@email.com"
   - phone: "(919) 555-0142"
   - customerType: "duke-native"
   - profileCompletionScore: 65
   - loyaltyPoints: 850
   - homeHealthScore: 78
   - properties: [{ address: "2847 Oak Street", city: "Durham", state: "NC", zip: "27705" }]

2. hppPlans array (2 plans):
   Plan 1: Water Heater Protection ($9.99/mo, active, enrolled 2019-03)
   Plan 2: HVAC Protection ($14.99/mo, active, enrolled 2020-06)

3. inventory array (4 items):
   - Carrier HVAC (8 years old, covered, last service Nov 2025)
   - Rheem Water Heater (6 years old, covered, last service Sep 2025)
   - Bosch Dishwasher (not covered, 3 years old)
   - Samsung Refrigerator (not covered, 4 years old)

4. appointments array (3 appointments):
   - Upcoming: HVAC Maintenance, Nov 22, 9am-12pm, confirmed
   - Past: Water Heater Repair, Sep 3, completed
   - Past: HVAC Repair, May 12, completed

5. maintenanceReminders array (3 reminders):
   - Change HVAC Filter (due in 5 days)
   - Flush Water Heater (due in 3 months)
   - Check smoke detectors (due next week)

6. serviceHistory array (6 completed services with dates, contractors, ratings)

7. availableServices array (5 ad-hoc services):
   - HVAC Cleaning & Check ($99)
   - Ceiling Fan Installation ($120-$190)
   - Water Heater Inspection ($75)
   - Electrical Outlet Installation ($85)
   - Plumbing Drain Cleaning ($95)

Use realistic data with proper TypeScript interfaces.
Export as named exports.
```

---

## 📱 SCREEN 1: HOME DASHBOARD

### Prompt 5: Home Dashboard - Header & Hero
```
Create src/screens/HomeScreen.tsx:

Import currentCustomer, appointments, maintenanceReminders from mockData.
Import QuickActionButton, ProgressCircle, StatusBadge, MobileCard components.

Layout: Single scrollable column with safe area padding at top.

HEADER (fixed position):
- Safe area padding at top
- Greeting: "Hi, Eleanor!" (text-2xl font-bold)
- Notification bell icon (top-right with red dot badge if unread)
- Background: white with bottom shadow

HOME HEALTH CARD (hero):
- Large card with blue gradient background (from-blue-500 to-blue-600)
- Text: white
- Large number: 78/100 (text-4xl font-bold)
- Label: "Home Health Score"
- Status: "Good" with checkmark icon
- Subtitle: "2 items need attention"
- Tap to expand (show alert for now)
- Rounded-2xl, padding-6

PROFILE COMPLETION CARD:
- White card below hero
- ProgressCircle component: 65% (blue color, size 80)
- Title: "Complete Your Home Profile" (font-semibold)
- Subtitle: "5 of 12 appliances added"
- Progress bar below circle (full width)
- Reward text: "Add 2 more to earn 50 points"
- Small badge icons showing completed milestones
- "Add Appliance" button (secondary style)

LOYALTY POINTS CARD:
- White card
- Star icon (yellow, large)
- Points: 850 points (text-2xl font-bold)
- Value: "$8.50 toward services" (text-sm text-gray-600)
- Progress to next tier:
  * "150 more for Silver Status"
  * Small progress bar
- Gradient border (purple to yellow)

Use proper spacing between cards (space-y-4).
All cards should have rounded-xl and shadow-sm.
```

### Prompt 6: Home Dashboard - Quick Actions & Appointments
```
Continue HomeScreen.tsx:

QUICK ACTIONS SECTION:
- Section title: "Quick Actions" (text-lg font-semibold mb-3)
- Two large buttons (stacked, space-y-3):

  Button 1 - Book Service:
  - Use QuickActionButton component
  - Icon: Calendar from lucide-react
  - Label: "Book Service"
  - Variant: primary
  - Full width, height 56px
  - OnPress: navigate to /book

  Button 2 - Add to Inventory:
  - Icon: Plus
  - Label: "Add to Inventory"
  - Variant: secondary
  - Full width, height 56px
  - OnPress: navigate to /my-home

UPCOMING APPOINTMENTS SECTION:
- Section title: "Upcoming Appointments" (with count badge "1")
- Show first 2 upcoming appointments using AppointmentCard component
- Each card shows:
  * Service type: "HVAC Maintenance"
  * Date: "Friday, Nov 22"
  * Time: "9:00 AM - 12:00 PM"
  * Countdown: "In 2 days" (highlighted)
  * Contractor: "Carolina Comfort"
  * Status badge: "Confirmed" (blue)
  * Tap card → show alert "Navigate to appointment details"

- If more than 2: "View All Appointments →" link
- If zero: Empty state with "No upcoming appointments" and "Book Service" button

Add padding and spacing between sections.
```

### Prompt 7: Home Dashboard - Reminders & Activity
```
Continue HomeScreen.tsx:

MAINTENANCE REMINDERS SECTION:
- Section title: "Maintenance Reminders" (with Bell icon)
- Show first 3 reminders (from maintenanceReminders data)
- Each reminder card:
  * Appliance icon (based on category)
  * Title: "Change HVAC Filter"
  * Due date: "Due in 5 days" (color based on urgency: red <7 days, yellow <14 days, green >14 days)
  * Two small buttons side-by-side:
    - "Mark Done" (gray, outline)
    - "Book Service" (blue, primary)
  * Swipe left to dismiss (show "Dismissed" snackbar)

- "View All Reminders →" link if more than 3

RECENT ACTIVITY SECTION:
- Section title: "Recent Activity"
- Timeline of last 5 activities:
  * Small colored icon circle (green checkmark, blue plus, etc.)
  * Activity text: "Service completed: HVAC Maintenance"
  * Timestamp: "2 days ago"
  * Connecting vertical line between items (except last)
- Each item: text-sm, gray text, with icon

Bottom padding to clear tab bar (pb-20).

Test scrolling behavior and safe area.
Make cards tappable with subtle active state.
```

---

## 📅 SCREEN 2: BOOK SERVICE FLOW

### Prompt 8: Book Service - Setup Modal Navigation
```
Create src/screens/BookServiceScreen.tsx as a full-screen modal:

This screen should feel like a modal with:
- Full-screen overlay
- Close X button (top-right)
- Back button (top-left) when in steps 2+
- Step indicator at top

Create state management:
- const [currentStep, setCurrentStep] = useState(1) // 1-6
- const [selectedCategory, setSelectedCategory] = useState(null)
- const [selectedItem, setSelectedItem] = useState(null)
- const [issueDescription, setIssueDescription] = useState('')
- const [selectedContractor, setSelectedContractor] = useState(null)
- const [selectedDate, setSelectedDate] = useState(null)
- const [selectedTime, setSelectedTime] = useState(null)

HEADER (fixed):
- Progress bar showing step X of 6
- Close X button → confirm exit
- Back button (< icon) if step > 1
- Safe area padding

CONTENT AREA:
- Conditionally render based on currentStep
- Scrollable content
- Bottom padding for buttons

FOOTER (fixed at bottom):
- "Continue" button (primary, full width)
- Only enabled when step requirements met
- Safe area padding at bottom

We'll build each step in next prompts.
```

### Prompt 9: Book Service - Step 1 (Service Type)
```
Continue BookServiceScreen.tsx:

Create Step 1 content (when currentStep === 1):

TITLE:
- "What do you need help with?" (text-xl font-bold mb-6)

SERVICE CATEGORY CARDS (2 columns grid):
Create 6 large category cards:

1. Heating & Cooling
   - Icon: Thermometer (lucide-react, size 32, blue)
   - Label: "Heating & Cooling"
   - Card: white bg, rounded-xl, p-4, shadow

2. Plumbing
   - Icon: Droplets
   - Label: "Plumbing"

3. Electrical
   - Icon: Zap
   - Label: "Electrical"

4. Appliances
   - Icon: Refrigerator (or Package)
   - Label: "Appliances"

5. Water Heater
   - Icon: Flame
   - Label: "Water Heater"

6. Other
   - Icon: MoreHorizontal
   - Label: "Other Service"

Each card:
- Aspect ratio: square or slightly taller
- Icon centered at top
- Label below icon (text-sm font-medium)
- Tap to select:
  * Selected: border-2 border-blue-600, bg-blue-50
  * Unselected: border border-gray-200
- Active state: scale-98

Grid: grid-cols-2 gap-4

OnPress:
- setSelectedCategory(category)
- Enable "Continue" button
- OnContinue: setCurrentStep(2)

Mobile optimized spacing and touch targets.
```

### Prompt 10: Book Service - Step 2 (Select/Add Item)
```
Continue BookServiceScreen.tsx:

Create Step 2 content (when currentStep === 2):

TITLE:
- "Which [category] needs service?" (insert selectedCategory)
- Example: "Which HVAC system needs service?"

IF CUSTOMER HAS INVENTORY IN THIS CATEGORY:

Show list of existing inventory items (filter by selectedCategory):
- Use InventoryItemCard component
- Each card shows:
  * Name: "Carrier HVAC - Living Room"
  * Details: "8 years old"
  * Last service: "Nov 2025"
  * Tap to select (radio button style)
- Selected card: blue border

"Add New Item" button at bottom (secondary)
"Skip - I'll describe it" link (text button)

IF NO INVENTORY IN THIS CATEGORY:

Show quick add form:
- Label: "Tell us about your [category]"
- Form fields:
  * Brand (dropdown with common brands + "Other")
    - For HVAC: Carrier, Trane, Lennox, Rheem, etc.
  * Age (dropdown)
    - Options: Less than 5 years, 5-10 years, 10-15 years, 15+ years
  * Location (optional dropdown)
    - Living Room, Basement, Garage, etc.
- "Save & Continue" button (primary)
- "Skip for Now" link (contractor will collect)

OnPress Continue:
- setSelectedItem(item or newItemData)
- setCurrentStep(3)

Use proper form styling: labels, borders, focus states.
Mobile-optimized dropdown and inputs.
```

### Prompt 11: Book Service - Step 3 (Describe Issue)
```
Continue BookServiceScreen.tsx:

Create Step 3 content (when currentStep === 3):

TITLE:
- "What's the problem?"

SYMPTOM CHECKLIST (if category has common issues):
For HVAC, show checkboxes:
- "Not cooling or heating properly"
- "Strange or loud noise"
- "Bad smell or odor"
- "System won't turn on"
- "High energy bills"
- "Other (describe below)"

User can select multiple.

FREE TEXT AREA:
- Label: "Additional details"
- Textarea:
  * Placeholder: "Describe the issue in your own words..."
  * Rows: 4
  * Max length: 500 characters
  * Character counter: "0/500"
  * Border, rounded, proper padding

EMERGENCY TRIAGE (NEW - Session 3):
After user describes issue, show qualifying questions:
- If HVAC issue:
  * "Is your home temperature below 60°F with freezing temps outside?"
  * "Is anyone in your home vulnerable to extreme temperatures?"
- If Electrical:
  * "Is anything sparking or smoking?"
  * "Do you smell burning?"
- If Gas-related:
  * "Do you smell gas?"
  * "Do you hear hissing sounds?"

IF EMERGENCY DETECTED:
- Stop booking flow
- Show alert banner (red):
  * "⚠️ This appears to be an emergency"
  * "Please call us immediately at 1-800-XXX-XXXX"
  * For gas: "🚨 SAFETY ALERT: If you smell gas, evacuate immediately and call your gas utility"
- "Call Now" button (links to phone call)
- "This is NOT an emergency" link (continues booking)

FOR HPP CUSTOMERS (if currentCustomer has plans and NOT emergency):

Show coverage check section:
- Banner: "Checking your coverage..."
- Info card:
  * Icon: Shield (blue)
  * Text: "You have HVAC Protection Plan"
  * Status: "✅ This service is likely covered"
  * OR "⚠️ This may not be covered - estimated cost: $120-$180"
- Small print: "Final coverage determined by contractor"

OnPress Continue:
- setIssueDescription(text + checklist)
- setCurrentStep(4)

Mobile keyboard handling (resize content when keyboard open).
```

### Prompt 12: Book Service - Step 4 (Select Contractor) - MVP UPDATED
```
Continue BookServiceScreen.tsx:

Create Step 4 content (when currentStep === 4):

**MVP APPROACH (Session 3): PRE-ASSIGNED CONTRACTOR ONLY**
- Customer does NOT select contractor
- System auto-assigns primary contractor based on trade + zip code
- Same experience for BOTH HPP covered AND ad-hoc services
- Contractor marketplace deferred to Phase 2

TITLE: "Your Assigned Contractor"

Single large ContractorCard:
- Use ContractorCard component
- Contractor data (pre-assigned based on trade + zip):
  * Name: "Carolina Comfort Services"
  * Logo: (placeholder or image)
  * Phone: "(919) 555-0987"
  * Badge: "Primary Contractor" (blue)
  * Serves: "Durham, NC"
  * Brief description: "Licensed & insured HVAC specialists serving Durham since 2005"
- Card styling: larger, more prominent
- Pre-selected (blue border) - NOT selectable, just informational
- NO rating displayed (ratings are Phase 2)

FOR AD-HOC SERVICES - Display Pricing:
- Show price on contractor card:
  * Fixed price: "$99"
  * Variable price: "$120-$190" (range)
- Text: "Payment collected by contractor at service completion"
- "Accepted payment methods: Cash, check, credit card"

FOR HPP COVERED SERVICES:
- Show: "$0 - Covered by your plan"
- No payment details needed

ALTERNATE CONTRACTOR REQUEST:
Small text below card:
- "Need a different contractor?"
- Link/button: "Request Change" → Shows modal:
  * "To request a different contractor, please call us at 1-800-XXX-XXXX"
  * "Our team will check availability and call you back within 2 hours"
  * "Close" button
- (Does NOT show list of contractors to choose from - this is manual admin process)

INFO TEXT:
- "This contractor is assigned based on your location and service type"
- "They meet our quality and licensing requirements"

OnPress Continue:
- setSelectedContractor(contractor) // pre-assigned contractor
- setCurrentStep(5)

**PHASE 2 FEATURE (Not in MVP):**
- Multiple contractor options with ratings
- Customer selection based on price/rating/availability
- In-app contractor reviews and ratings display
```

### Prompt 13: Book Service - Step 5 (Date & Time)
```
Continue BookServiceScreen.tsx:

Create Step 5 content (when currentStep === 5):

TITLE: "When works for you?"

EARLIEST AVAILABLE BANNER:
- Info card at top
- Icon: Clock
- Text: "Soonest: Tomorrow at 9:00 AM"
- Tap to auto-select

CALENDAR SECTION:
Week view calendar (horizontal scroll):
- Show 14 days starting from today
- Each day card:
  * Day name: "Mon"
  * Date: "22"
  * Month: "Nov" (small)
  * Available: blue border, white bg
  * Unavailable: gray border, gray text, disabled
  * Selected: blue bg, white text
  * Tap to select date

Buffer info banner:
- "⚡ Emergency service: 24-hour response"
- OR "🗓️ Standard service: 3-5 business days"

TIME SLOT SELECTION:
Once date selected, show time slots:
- Title: "Available times"
- 3-4 time slot cards:
  * "Morning (8am - 12pm)"
  * "Afternoon (12pm - 4pm)"
  * "Evening (4pm - 8pm)"
- Each as button card
- Selected: blue bg, white text
- Unselected: white bg, blue border

ARRIVAL WINDOW INFO:
- Small text: "Your contractor will arrive between 9:00 AM - 12:00 PM"

OnPress Continue:
- setSelectedDate(date)
- setSelectedTime(time)
- setCurrentStep(6)

Horizontal scroll for calendar.
Mobile-optimized date picker.
```

### Prompt 14: Book Service - Step 6 (Review & Confirm) - MVP UPDATED
```
Continue BookServiceScreen.tsx:

Create Step 6 content (when currentStep === 6):

TITLE: "Review Your Booking"

SUMMARY SECTIONS (stacked cards):

1. SERVICE DETAILS CARD:
   - Section label: "Service" (gray text, small)
   - Service type: "HVAC Repair" (bold)
   - Item: "Carrier HVAC - Living Room" (with icon)
   - Issue: "Strange grinding noise" (truncated if long)
   - "Edit" link (top-right) → goes back to step 3

2. CONTRACTOR CARD:
   - Section label: "Contractor"
   - Company: "Carolina Comfort Services"
   - Phone: "(919) 555-0987" (tap to call)
   - NO rating displayed (Phase 2 feature)
   - "Edit" link → back to step 4 (shows "Request Change" modal)

3. SCHEDULE CARD:
   - Section label: "Schedule"
   - Date: "Friday, March 15, 2025"
   - Time: "9:00 AM - 12:00 PM"
   - Add to calendar toggle (switch)
   - "Edit" link → back to step 5

4. COST CARD:
   - Section label: "Cost"
   - IF HPP:
     * "$0 - Covered by your plan" (green text, shield icon)
     * Plan name: "HVAC Protection Plan"
     * Small text: "Service covered at no charge"
   - IF AD-HOC:
     * Price: "$99.00" (large, bold) or "$120-$190" (range)
     * Payment method below

**MVP PAYMENT APPROACH (Session 3): CONTRACTOR COLLECTS ON-SITE**

FOR AD-HOC SERVICES ONLY:

PAYMENT COLLECTION INFO:
- Section label: "Payment"
- Large text: "$99.00"
- Info banner (light blue background):
  * Icon: Info circle
  * "Payment will be collected by your contractor at service completion"
- Accepted payment methods (with icons):
  * Cash
  * Check
  * Credit/Debit Card (via contractor's card reader)
- Small text: "Your contractor is equipped with secure payment processing"

NO PAYMENT METHOD SELECTION:
- Remove "How would you like to pay?" section
- Remove Apple Pay/Google Pay/Credit Card options
- Remove "Pay Now" vs "Pay at Completion" toggle
- (In-app payment deferred to Phase 2)

BOOKING STATUS INFO:
- Info banner:
  * "Your booking will be confirmed within 24 hours"
  * "We'll contact your contractor and update you once confirmed"
- For HPP covered: "Confirmation typically within 2-4 hours"

TERMS & CONDITIONS:
- Checkbox: "I agree to terms and conditions"
- Link: "View terms" (opens modal)
- Required to enable button
- Terms include: cancellation policy, contractor payment terms

CONFIRM BUTTON (sticky at bottom):
- Large primary button: "Confirm Booking"
- Disabled until terms checked
- Full width, height 56px
- OnPress: create booking (no payment processing)

OnPress Confirm:
- Show loading spinner ("Creating your booking...")
- Create service request in backend
- Navigate to confirmation screen
- Show success animation

Make cards collapsible to save space.
Clear section separation.

**PHASE 2 FEATURE (Not in MVP):**
- In-app payment (Apple Pay, Google Pay, Credit Card)
- Customer pre-pays at booking
- Payment processed before confirmation
```

### Prompt 15: Book Service - Confirmation Screen - MVP UPDATED
```
Create a confirmation screen component (BookingConfirmation.tsx):

This replaces the booking flow content after successful booking.

LAYOUT (centered, full screen):

SUCCESS ANIMATION:
- Large checkmark in circle (green, animated)
- Use CSS animation: scale and fade in

CONFIRMATION MESSAGE:
- Title: "Booking Submitted!" (text-2xl font-bold)
- Status: "Pending Confirmation" (yellow badge)
- Message: "We're contacting your contractor" (text-gray-600)

REFERENCE NUMBER:
- Label: "Service Request Number"
- Number: #SR-2025-1142 (monospace, large)
- Copy button (tap to copy)

SUMMARY CARD (compact):
- Service: HVAC Repair
- Contractor: Carolina Comfort Services
- Requested Date: "Friday, March 15"
- Requested Time: "9:00 AM - 12:00 PM"
- Cost: $0 (HPP covered) or "$99 (pay at completion)" (ad-hoc)

**MVP STATUS APPROACH (Session 3): MANUAL CONFIRMATION**

WHAT HAPPENS NEXT CARD (prominent):
- Icon: Clock
- Title: "What Happens Next?"
- Timeline/Steps:
  1. "We're contacting Carolina Comfort Services" (in progress icon)
  2. "Contractor confirms availability (within 24 hours)"
  3. "You'll receive confirmation notification"
  4. "Contractor will arrive at scheduled time"

INFO BANNER:
- Light blue background
- "You'll receive confirmation within 24 hours"
- "We'll notify you via [push/SMS/email] when your appointment is confirmed"
- Contact info: "Questions? Call us at 1-800-XXX-XXXX"

ACTIONS (stacked buttons):
1. "View Appointment Status" (primary blue)
   - Navigate to appointment details (shows "Pending Confirmation" status)
2. "Back to Home" (secondary)
   - Navigate back to home dashboard
3. "Book Another Service" (text button)
   - Restart booking flow

NO "ADD TO CALENDAR" BUTTON YET:
- Removed until appointment confirmed
- Will be available once contractor confirms
- (Prevents calendar clutter with unconfirmed bookings)

Post-confirmation actions:
- Show push notification: "Your service request has been submitted"
- Add appointment to "My Appointments" with status "Pending Confirmation"
- Update home dashboard with pending appointment
- Backend: Admin team receives notification to contact contractor

Celebration confetti animation (optional - maybe wait for confirmed status).
Proper spacing and padding.

**PHASE 2 ENHANCEMENT (With FSM):**
- Immediate confirmation: "Your appointment is confirmed!"
- Add to calendar button available immediately
- No manual admin step required
```

---

## 🏠 SCREEN 3: MY HOME (INVENTORY)

### Prompt 16: My Home - Main Screen Layout
```
Create src/screens/MyHomeScreen.tsx:

This screen shows home inventory with gamification.

HEADER (fixed):
- Title: "My Home" (text-2xl font-bold)
- Add button (+ icon) top-right
- Safe area padding

PROFILE COMPLETION SECTION:
- Large hero card with gradient (blue)
- ProgressCircle component: 65% (size 100)
  * Center label: "65%"
- Title: "You're making great progress!" (white text)
- Subtitle: "5 of 12 appliances added"
- Reward progress bar:
  * "Add 2 more to earn 50 points"
  * Small progress bar (white with blue fill)
- Badge icons showing milestones:
  * 3 badges earned (colored)
  * 2 badges locked (gray)

INVENTORY CATEGORIES:
Each category is a collapsible section:

Section header (tap to expand/collapse):
- Category name: "Heating & Cooling"
- Item count: "(2 items)"
- Chevron icon (up if expanded, down if collapsed)
- Divider line

1. HEATING & COOLING (2 items) - Expanded by default:
   Item 1 - Carrier HVAC:
   - Use InventoryItemCard component
   - Photo (if available)
   - Name: "Carrier HVAC" (bold)
   - Location: "Living Room" (small, gray)
   - Age: "8 years old"
   - Status badge: "Well Maintained" (green)
   - Coverage badge: "HPP Covered" (blue shield)
   - Last service: "Nov 15, 2025"
   - Next maintenance: "Nov 2026"
   - "Book Service" button (small, secondary)

2. PLUMBING (1 item):
   - Rheem Water Heater (similar card)

3. ELECTRICAL (0 items) - Collapsed:
   - Empty state when expanded:
     * Icon: Zap (gray)
     * Text: "No electrical items yet"
     * "Add Item" button (secondary)

4. APPLIANCES (3 items):
   - Dishwasher, Refrigerator, Washer cards

Bottom padding to clear tab bar.
Smooth expand/collapse animation.
```

### Prompt 17: My Home - Add Item Flow (Modal) - MVP UPDATED
```
Create AddInventoryItemModal component:

Full-screen modal with steps.

STEP 1: Choose Method
- Title: "Add Appliance or System"
- Three option cards (NEW - Session 3 added contractor option):

  Option 1 - Scan Barcode:
  - Icon: Camera (large)
  - Label: "Scan Barcode"
  - Description: "Use your camera to scan"
  - Tap → trigger camera (show alert "Camera feature" for prototype)

  Option 2 - Enter Manually:
  - Icon: Keyboard
  - Label: "Enter Manually"
  - Description: "Type in the details"
  - Tap → go to Step 2

  Option 3 - Added by Contractor:
  - Icon: User-Check
  - Label: "During Service Visit"
  - Description: "Ask your technician to add details"
  - Badge: "Recommended" (green)
  - Tap → Shows info modal:
    * "Our technicians can capture appliance details during service visits"
    * "This ensures accurate data and saves you time"
    * "Just ask your technician to scan your appliance information"
    * "You'll be notified when they add it to your profile"

STEP 2: Item Details Form
- Title: "Tell us about your [item]"
- Form fields (all with proper labels):

  1. Category (required):
     - Dropdown: HVAC, Plumbing, Electrical, Appliance, Water Heater, Other

  2. Type (required, changes based on category):
     - If HVAC: Heat Pump, Central AC, Furnace, etc.
     - Dropdown

  3. Brand (required):
     - Searchable dropdown with common brands
     - "Other" option with text input

  4. Model Number (optional):
     - Text input
     - Placeholder: "e.g., ABC-123"

  5. Serial Number (optional):
     - Text input

  6. Install Date / Age (required):
     - Date picker OR age dropdown
     - "I don't know" option (estimates based on property)

  7. Location (optional):
     - Dropdown: Living Room, Basement, Garage, Kitchen, etc.

  8. Photo (optional):
     - "Upload Photo" button
     - Shows thumbnail if uploaded

"Continue" button (enabled when required fields filled)

STEP 3: Warranty Info (optional)
- Title: "Warranty Information"
- Toggle: "Under warranty?"
  - If yes:
    * Warranty expires: date picker
    * "Upload warranty document" button (photo/PDF)
  - If no: skip

"Skip" button (text)
"Continue" button

STEP 4: Confirmation
- Success animation
- "+50 points earned!" (large, with star animation)
- Summary of item added
- Tip: "💡 TIP: Your technician can update this information during service visits"
- "View in My Home" button
- "Add Another" button (secondary)

OnComplete:
- Add item to inventory
- Update profile completion score
- Close modal
- Refresh My Home screen

Form validation and error messages.
Mobile-optimized inputs.

**NEW MVP FEATURE (Session 3): Contractor Inventory Capture**
- Contractors can add/update inventory during service visits
- Customer receives notification: "Your technician added details about your HVAC system"
- Customer reviews contractor-added data and earns +10 points for confirmation
- Implementation: TBD (email photos to admin, simple form in portal, or Phase 2 mobile app)
```

### Prompt 18: My Home - Item Details Screen
```
Create InventoryItemDetailScreen component:

This screen shows when tapping an inventory item card.

HEADER:
- Back button (< icon)
- Item name: "Carrier HVAC"
- Edit button (pencil icon, top-right)

HERO SECTION:
- Large photo of item (if available)
  * Placeholder gray box if no photo
  * "Add Photo" button overlay
- Location: "Living Room" (with house icon)

INFORMATION CARDS (stacked):

1. BASIC INFO CARD:
   - Brand: Carrier
   - Model: Infinity 3-Ton
   - Serial Number: CAR123456789 (monospace, copyable)
   - Install Date: June 15, 2020
   - Age: 5 years old

2. WARRANTY CARD:
   - Status: "Under Warranty" (green badge)
   - Expires: June 15, 2035
   - Warranty document: "View warranty.pdf" (link)

3. COVERAGE CARD:
   - HPP Coverage: "Covered" (green, shield icon)
   - Plan: "HVAC Protection Plan"
   - Link: "View plan details"

4. MAINTENANCE CARD:
   - Last Service: "Nov 15, 2025" (with link to service record)
   - Next Service: "Nov 2026"
   - Status: "Up to date" (green checkmark)
   - Maintenance history: "6 services" (link to full history)

5. HEALTH STATUS CARD:
   - Health Score: 85/100 (green)
   - Status: "Good condition"
   - Age indicator: "5 years old (typical lifespan: 15-20 years)"
   - Recommendation: "Schedule annual maintenance"

ACTION BUTTONS (sticky at bottom):
- "Book Service" (primary blue, full width)
- "Schedule Maintenance" (secondary, full width)

Three-dot menu (top-right):
- Edit Item
- Upload Photo
- View Service History
- Delete Item (red text, confirmation alert)

Scrollable content.
Clear section separation.
```

---

## 🛡️ SCREEN 4: MY PLANS

### Prompt 19: Plans Screen - Main Layout
```
Create src/screens/PlansScreen.tsx:

HEADER:
- Title: "My Protection Plans" (text-2xl font-bold)
- Info button (? icon) → explains HPP plans

CURRENT PLANS SECTION:
- Section title: "Active Plans" (with count badge "2")

Plan Card 1 - Water Heater Protection:
- Use PlanCard component
- Large shield icon with water drop
- Plan name: "Water Heater Protection Plan"
- Plan code: "WH-STD" (small, gray)
- Status badge: "Active" (green)
- Pricing:
  * $9.99/month (large, bold)
  * Billing: "On your Duke Energy bill" (small, with icon)
- Enrolled: "Since March 2019" (calendar icon)
- Claims: "2 claims filed" (with link)
- Coverage summary (3 bullets):
  * "Repairs to tank and components"
  * "Labor and service calls"
  * "No deductible"
- Buttons:
  * "View Details" (secondary, full width)
  * Three-dot menu: Upgrade, Manage, Cancel

Plan Card 2 - HVAC Protection:
Similar structure with:
- Shield icon with thermometer
- $14.99/month
- 4 claims filed
- 5 coverage bullets

TOTAL INVESTMENT CARD:
- Light blue background
- Icon: Info circle
- Title: "Total Protection Investment"
- Amount: $24.98/month (text-2xl font-bold)
- Breakdown: "2 active plans"
- Billing info: "Billed monthly on Duke Energy statement"

AVAILABLE PLANS SECTION:
- Section title: "Add More Protection"
- Subtitle: "Protect more of your home"

Show 3 available plans to enroll:
1. Plumbing Protection ($12.99/mo)
2. Electrical Protection ($11.99/mo)
3. Appliance Protection ($14.99/mo)

Each card (smaller than active plans):
- Icon
- Plan name
- Price: "From $12.99/month"
- What's covered (3 bullets, small text)
- "Learn More" button (text link)
- "Enroll" button (primary, smaller)

Bottom padding for tab bar.
Smooth scrolling.
```

### Prompt 20: Plan Details Screen
```
Create PlanDetailScreen component:

Shows when tapping "View Details" on a plan.

HEADER:
- Back button
- Plan name: "HVAC Protection Plan"
- Share button (to share with family)

HERO SECTION:
- Large shield icon with blue gradient background
- Plan name (white text)
- Monthly price: $14.99/month (large, white)
- Status badge: "Active"

OVERVIEW CARD:
- Quick stats (3 columns):
  * Enrolled: "June 2020"
  * Claims Filed: "4"
  * Coverage: "Comprehensive"

WHAT'S COVERED SECTION:
Expandable accordion:
- "What's Covered" (expanded by default)
- Checkmark list:
  * Heating and cooling system repairs
  * Annual maintenance visit included
  * No deductible or trip charges
  * Covers heat pumps, furnaces, AC units
  * Thermostat repairs
- "What's NOT Covered" (collapsed)
  - X icon list:
    * Cosmetic issues
    * Pre-existing conditions
    * Improper maintenance
- "Coverage Limits" (collapsed)

BILLING SECTION:
- Monthly cost: $14.99
- Billing method: "Duke Energy utility bill"
- Next billing date: "Dec 1, 2025"
- "Update Payment Method" link

CLAIMS HISTORY:
- List of past claims (4 total)
- Each shows:
  * Date
  * Service type
  * Contractor
  * Status: "Completed"
  * "View details" link

FAQ SECTION (collapsed accordions):
- "How do I file a claim?"
- "Can I upgrade my plan?"
- "What's the cancellation policy?"
- Each expands to show answer

TERMS & CONDITIONS:
- Link: "View full terms and conditions"
- Opens PDF or modal

ACTIONS (sticky bottom):
- "Upgrade Plan" button (primary)
- "Manage Plan" button (secondary)
- "Cancel Plan" link (red text, confirmation)

Scrollable, clear sections.
```

### Prompt 21: Enroll in Plan Flow
```
Create EnrollInPlanModal component:

Multi-step enrollment flow for new HPP plan.

STEP 1: Review Plan
- Plan details (same as Plan Detail screen but condensed)
- What's covered (bullets)
- Price breakdown:
  * Monthly: $12.99
  * Annual: $155.88 (save $xx)
- Terms preview
- "Continue to Payment" button

STEP 2: Choose Payment Method
- Title: "How would you like to pay?"
- Payment options (radio cards):

  Option 1 - Add to Utility Bill (RECOMMENDED):
  - Icon: File/Document
  - Label: "Add to Duke Energy bill"
  - Description: "Easiest option, no extra fees"
  - Badge: "Recommended"
  - Info: "Prorated for first month"

  Option 2 - Credit/Debit Card:
  - Icon: CreditCard
  - Label: "Pay by card"
  - Description: "Charged monthly"
  - If selected: show card form
    * Card number
    * Expiry
    * CVV
    * Billing zip
  - Save for future toggle

  Option 3 - Bank Account (ACH):
  - Icon: Bank
  - Label: "Pay by bank account"
  - Description: "Lower fees than credit card"
  - If selected: show bank form
    * Routing number
    * Account number
    * Account type

"Continue" button (enabled when method selected)

STEP 3: Review & Accept Terms
- Summary:
  * Plan: Plumbing Protection
  * Price: $12.99/month
  * Billing: Duke Energy bill
  * Start date: "December 1, 2025"
  * First charge: "Prorated: $4.33"

Terms acceptance:
- Checkbox: "I have read and agree to the terms and conditions"
- Link to view terms
- Required

Digital signature:
- Text input: "Type your full name to sign"
- Placeholder: "Eleanor Mitchell"

"Complete Enrollment" button (disabled until terms + signature)

STEP 4: Confirmation
- Success animation
- Title: "Welcome to Plumbing Protection!"
- Confirmation message
- Plan card (summary)
- Enrollment details:
  * Confirmation #: ENR-2025-456
  * Effective date: Dec 1, 2025
  * First billing: Dec 15, 2025
- Email sent confirmation
- "View My Plans" button
- "Done" button

OnComplete:
- Add plan to customer's plans
- Navigate to Plans screen
- Show plans tab

Form validation.
Loading states.
Error handling.
```

---

## 📅 SCREEN 5: MY APPOINTMENTS

### Prompt 22: Appointments Screen - Tabs & List
```
Create src/screens/AppointmentsScreen.tsx:

HEADER:
- Title: "My Appointments" (text-2xl font-bold)
- Filter button (funnel icon, top-right)

TABS (Segmented control):
- "Upcoming" (default, count badge)
- "Past"
- Active tab: blue background
- Inactive: gray text

UPCOMING APPOINTMENTS TAB:

Show list of upcoming appointments (from appointments data):

Appointment Card 1:
- Use AppointmentCard component
- Status badge: "Confirmed" (blue, top-right)
- Service icon: Thermometer (HVAC)
- Service type: "HVAC Maintenance"
- Date & time:
  * Date: "Friday, Nov 22" (large)
  * Time: "9:00 AM - 12:00 PM"
  * Countdown: "In 2 days" (highlighted, blue)
- Contractor section:
  * Logo (small circle)
  * Name: "Carolina Comfort"
  * Rating: 4.8 stars
  * Phone: "(919) 555-0987" (tap to call)
- HPP coverage badge: "Covered - No charge"
- Quick actions (horizontal buttons):
  * "Track" (if FSM available, map icon)
  * "Reschedule" (calendar icon)
  * "Details" (chevron)
- Tap card → navigate to appointment details

If no upcoming:
- Empty state:
  * Calendar icon (large, gray)
  * "No upcoming appointments"
  * "Book Service" button (primary)

PAST APPOINTMENTS TAB:

Show completed appointments (different card style):

Past Appointment Card:
- Status badge: "Completed" (green)
- Service type + icon
- Date: "Nov 15, 2025" (smaller)
- Contractor + rating
- Cost: $0 or $99
- "Rate Service" button (if not rated, yellow star)
- "View Details" button
- "Book Again" button (for ad-hoc)

Filter options (bottom sheet when filter tapped):
- All Services
- HPP Only
- Ad-Hoc Only
- Date range picker

Pull-to-refresh on both tabs.
Proper empty states.
```

### Prompt 23: Appointment Details Screen - MVP UPDATED
```
Create AppointmentDetailScreen component:

HEADER:
- Back button
- Title: "Appointment Details"
- Three-dot menu (Cancel, Reschedule, Share)

**MVP STATUS APPROACH (Session 3): LIMITED STATUSES, NO REAL-TIME TRACKING**
- Only 3 statuses in MVP: "Pending Confirmation", "Confirmed", "Completed"
- NO intermediate statuses: "Dispatched", "En Route", "On-Site", "In Progress"
- Status updates manually entered by admin team
- Pizza tracker (GPS tracking) NOT available in MVP - deferred to Phase 2

STATUS BANNER (colored based on status):
- "Pending Confirmation" (yellow):
  * "Waiting for contractor confirmation"
  * Icon: Clock
  * "Typically confirmed within 24 hours"
- "Confirmed" (blue):
  * "Your appointment is confirmed"
  * Icon: Checkmark
  * Contractor name displayed
- "Completed" (green):
  * "Service completed on [date]"
  * Icon: Checkmark
- Background color matches status

SERVICE INFORMATION CARD:
- Service type: "HVAC Maintenance" (bold, with icon)
- Description: "Annual preventive maintenance"
- Inventory item: "Carrier HVAC - Living Room" (link to inventory)
- Issue: "Routine maintenance - no issues reported"
- IF EMERGENCY-FLAGGED: Red banner "Emergency service - priority scheduling"

CONTRACTOR INFORMATION CARD:
- Company name: "Carolina Comfort Services"
- NO rating displayed (Phase 2 feature)
- Brief description: "Licensed & insured HVAC specialists"
- Contact info:
  * Phone: "(919) 555-0987" (large, tap to call)
  * "Call Contractor" button (primary)
- IF STATUS = "Pending": Show "Contractor will be in touch within 24 hours"
- NO "Message" button (in-app messaging is Phase 2)
- NO technician name until day-of (contractors often assign day-of)

SCHEDULE CARD:
- Date: "Friday, November 22, 2025" (large)
- Time window: "9:00 AM - 12:00 PM"
- Duration: "Estimated 2 hours" (if known)
- Add to calendar button (only if status = "Confirmed")
- Location: "2847 Oak Street, Durham, NC"
- IF STATUS = "Pending": Show "Requested time - awaiting confirmation"

COST CARD:
- IF HPP:
  * "$0 - Covered by your plan" (green, shield icon)
  * Plan: "HVAC Protection Plan" (link to plan details)
  * Small text: "No payment required"
- IF AD-HOC:
  * Price: "$99.00" (large, bold)
  * Payment method: "Payment will be collected by contractor at completion"
  * Accepted methods: Cash, check, credit card
  * NO "Paid via Apple Pay" or pre-paid options (Phase 2 feature)

NO GPS TRACKING IN MVP:
- Remove "Track Contractor" map section
- Remove "En Route" status
- Remove ETA display
- (Pizza tracker is Phase 2 feature requiring FSM tool)

MVP WORKAROUND FOR UPDATES:
- Info banner (if confirmed):
  * "Your contractor will call or text before arriving"
  * "Most contractors send 'on my way' notifications"
  * Phone number to call contractor directly displayed

STATUS TIMELINE (SIMPLIFIED FOR MVP):
Vertical timeline with only 3 steps:
1. Requested (checkmark if complete, icon with timestamp)
   - "Nov 10, 2025 at 2:15 PM"
2. Confirmed (checkmark if complete, or pending)
   - "Nov 10, 2025 at 4:30 PM" OR "Awaiting confirmation"
3. Completed (checkmark if complete, or pending)
   - "Nov 22, 2025 at 11:45 AM" OR "Scheduled for Nov 22"

ACTIONS (sticky bottom):
- IF STATUS = "Pending Confirmation" or "Confirmed" AND >24 hours away:
  * "Reschedule" button (secondary, full width)
    - Opens modal: "Call us to reschedule at 1-800-XXX-XXXX"
    - (Self-service reschedule is Phase 2 with FSM integration)
- IF STATUS = "Pending Confirmation" or "Confirmed":
  * "Cancel Appointment" button (red text)
    - Opens modal: "Are you sure? Call 1-800-XXX-XXXX to cancel"
    - (Self-service cancel with guardrails is Phase 2)
- IF STATUS = "Completed":
  * "Book Again" button (primary)
  * "View Service Details" button

Three-dot menu options:
- Add to Calendar (if confirmed)
- Share Appointment Details
- Report Issue (opens support form)
- Call Support: 1-800-XXX-XXXX

Scrollable content.
Manual refresh (pull-to-refresh) to check for status updates.
Info banner if last updated >24 hours ago: "Status not updated recently? Call us"

**PHASE 2 ENHANCEMENTS (With FSM Tool):**
- GPS tracking with live map and ETA
- Real-time status updates (Dispatched, En Route, On-Site, In Progress)
- In-app messaging with contractor
- Self-service reschedule (date picker)
- Technician name and photo displayed
- Contractor ratings visible
```

---

## 📋 SCREEN 6: SERVICE HISTORY

### Prompt 24: Service History Screen
```
Create src/screens/ServiceHistoryScreen.tsx:

HEADER:
- Title: "Service History" (text-2xl font-bold)
- Filter button (funnel icon)
- Export button (share icon)

FILTER BAR (horizontal scroll chips):
- "All" (active, blue)
- "HPP Covered"
- "Ad-Hoc"
- "HVAC"
- "Plumbing"
- "Electrical"
- Each chip: pill shape, tap to filter

SERVICE RECORD CARDS:

Show list of completed services (from serviceHistory data):

Service Record Card:
- Date: "Nov 15, 2025" (gray, top)
- Service type + icon: Thermometer + "HVAC Maintenance"
- Inventory item: "Carrier HVAC - Living Room" (small, link)
- Contractor:
  * Company: "Carolina Comfort Services"
  * Technician: "Mike Thompson"
  * Rating: 5 stars (gold)
- Cost:
  * "$0" (green) if HPP
  * "$99" if ad-hoc
- Status badge: "Completed" (green)
- "View Details" button
- Card border: left edge colored by category (blue for HVAC, etc.)

List is scrollable (infinite scroll or pagination).

Empty state (if filtered to no results):
- Icon: ClipboardX
- "No services found"
- "Clear filters" button

Filter bottom sheet (when filter button tapped):
- Date range:
  * Last 30 days (default)
  * Last 6 months
  * Last year
  * All time
  * Custom (date pickers)
- Service type:
  * All services
  * HPP covered
  * Ad-hoc
- Category:
  * All categories
  * HVAC, Plumbing, Electrical, etc.
- Status:
  * Completed (default)
  * Cancelled
- "Apply Filters" button

Export options (bottom sheet):
- Export selected service (PDF)
- Export all history (CSV)
- Share with home buyer (generates shareable link)
- Email to me

Pull-to-refresh.
Search bar (optional, searches description).
```

### Prompt 25: Service Detail Screen
```
Create ServiceDetailScreen component:

HEADER:
- Back button
- Title: "Service Details"
- Share button

SERVICE SUMMARY CARD:
- Date: "November 15, 2025"
- Service type: "HVAC Maintenance" (bold, icon)
- Inventory: "Carrier HVAC - Living Room" (link)
- Status: "Completed" (green badge)
- Contractor: Company + technician
- Cost: $0 or amount

WORK PERFORMED CARD:
- Title: "Work Performed"
- Description from contractor:
  * "Completed annual preventive maintenance on Carrier Infinity heat pump system."
- Bullet list of tasks:
  * Cleaned condenser coils
  * Checked refrigerant levels
  * Replaced air filter
  * Tested thermostat
  * (7 items total from mock data)
- Contractor notes/recommendations:
  * "System operating efficiently. Recommend next maintenance in 12 months."

PARTS USED CARD (if applicable):
- Title: "Parts & Materials"
- Table/list:
  * Air Filter (16x25x1 MERV 11): $15.00
  * Labor: Included
  * Total: $15.00 (or "Covered by plan")

PHOTOS SECTION (if contractor added):
- Title: "Service Photos"
- Horizontal scroll of photos:
  * Before/after photos
  * Work area photos
  * Tap to expand fullscreen

INVOICE CARD:
- Title: "Invoice & Receipt"
- Invoice number: #INV-2025-1142
- Date: Nov 15, 2025
- Amount: $0 (HPP) or $99
- Buttons:
  * "View Invoice" (opens PDF modal)
  * "Download" (saves to device)
  * "Email to Me"

LINKED APPLIANCE CARD:
- Title: "Service For"
- Appliance: "Carrier HVAC - Living Room" (icon + name)
- "View in My Home" link (navigate to item detail)

SERVICE TIMELINE:
Vertical timeline (collapsed by default):
- "View Status Updates" (expandable)
- Shows all status changes with timestamps:
  * Requested: Nov 10 at 2:15 PM
  * Confirmed: Nov 10 at 2:20 PM
  * Contractor En Route: Nov 15 at 7:50 AM
  * On-Site: Nov 15 at 8:15 AM
  * Completed: Nov 15 at 10:45 AM

YOUR RATING CARD:
- Title: "Your Rating"
- Star rating: 5 stars (large, gold)
- Your review: "Excellent service, very professional"
- Date: "Nov 15, 2025"
- "Edit Rating" link

ACTIONS (sticky bottom):
- "Book Service Again" button (primary)
  * Pre-fills booking with same item/contractor
- "Report Issue" link (red text)

Scrollable.
Clear section separation.
PDF viewer for invoice.
```

---

## 👤 SCREEN 7: MY ACCOUNT

### Prompt 26: Account Screen - Main Layout
```
Create src/screens/AccountScreen.tsx:

This screen uses iOS Settings-style grouped list design.

PROFILE SECTION (header):
- Large circular avatar (or initials)
- Tap to edit photo
- Name: "Eleanor Mitchell" (text-xl font-bold)
- Email: eleanor.mitchell@email.com
- Phone: (919) 555-0142
- "Edit Profile" button (secondary, below info)

ACCOUNT SETTINGS GROUP:
- Group title: "ACCOUNT" (gray, uppercase, small)

List items (each tappable row):
1. My Properties
   - Icon: Home
   - Label: "My Properties"
   - Subtitle: "1 property"
   - Chevron right
   - OnPress: navigate to properties list

2. Payment Methods
   - Icon: CreditCard
   - Label: "Payment Methods"
   - Subtitle: "Visa •••• 4829"
   - Chevron
   - OnPress: navigate to payment methods

3. Notification Preferences
   - Icon: Bell
   - Label: "Notifications"
   - Toggle switch (right side, no chevron)
   - OnToggle: update preferences

4. Communication Preferences
   - Icon: MessageSquare
   - Label: "Communication"
   - Subtitle: "Push, SMS, Email"
   - Chevron
   - OnPress: navigate to comm prefs

APP SETTINGS GROUP:
- Group title: "APP SETTINGS"

5. Security
   - Icon: Lock
   - Label: "Security & Privacy"
   - Chevron

6. Biometric Login
   - Icon: Fingerprint
   - Label: "Face ID / Touch ID"
   - Toggle switch

7. Language
   - Icon: Globe
   - Label: "Language"
   - Subtitle: "English"
   - Chevron

8. Theme
   - Icon: Moon
   - Label: "Appearance"
   - Subtitle: "Light"
   - Chevron

HELP & SUPPORT GROUP:
- Group title: "HELP & SUPPORT"

9. Help Center
   - Icon: HelpCircle
   - Label: "Help Center"
   - Chevron

10. Contact Support
    - Icon: MessageCircle
    - Label: "Contact Support"
    - Chevron

11. FAQs
    - Icon: FileQuestion
    - Label: "FAQs"
    - Chevron

LEGAL GROUP:
- Group title: "LEGAL"

12. Terms of Service
    - Label
    - Chevron

13. Privacy Policy
    - Label
    - Chevron

ABOUT:
- App version: "Version 1.0.0 (Build 123)"
- Small gray text, centered
- "Check for Updates" button

SIGN OUT:
- "Sign Out" button (red text, centered)
- OnPress: confirmation alert
- "Are you sure you want to sign out?"

List item styling:
- White background
- Border between items
- Padding: 16px
- Hover/active state
- Icons: 20px, gray-600
- Labels: font-medium
- Subtitles: text-sm, gray-500
- Chevrons: gray-400, 16px

Bottom padding for tab bar.
```

### Prompt 27: Account Sub-Screens
```
Create supporting screens for Account section:

1. EDIT PROFILE SCREEN:
   - Header: "Edit Profile" with Save button
   - Form fields:
     * First Name
     * Last Name
     * Email
     * Phone
     * All editable text inputs
   - "Save Changes" button
   - "Cancel" link

2. MY PROPERTIES SCREEN:
   - Header: "My Properties"
   - List of properties:
     * Primary property card (badge)
     * Address, city, state, zip
     * Property details (sq ft, year built)
     * "Manage" button
   - "Add Property" button
   - OnTap: navigate to property details

3. PAYMENT METHODS SCREEN:
   - Header: "Payment Methods"
   - List of saved payment methods:
     * Visa •••• 4829 (default badge)
     * Duke Energy Bill
     * Each with edit/delete options
   - "Add Payment Method" button
   - OnTap method: set as default option

4. ADD PAYMENT METHOD SCREEN:
   - Header: "Add Payment Method"
   - Payment type selector:
     * Credit/Debit Card
     * Bank Account (ACH)
   - Form fields based on type:
     * Card: number, expiry, CVV, zip
     * Bank: routing, account, type
   - "Set as default" toggle
   - "Add" button

5. NOTIFICATION PREFERENCES SCREEN:
   - Header: "Notification Preferences"
   - Toggle switches:
     * Push Notifications (master)
     * SMS Notifications
     * Email Notifications
   - Reminder frequency dropdown:
     * Weekly, Bi-weekly, Monthly
   - Appointment reminders (sub-toggles):
     * 1 day before
     * Morning of
     * When contractor en route
   - "Save" button

6. SECURITY SCREEN:
   - Header: "Security & Privacy"
   - Options:
     * Change Password (navigate to form)
     * Two-Factor Authentication (toggle)
     * Biometric Login (toggle, same as main)
     * Connected Devices (list)
   - Privacy section:
     * Data sharing preferences
     * Location services toggle
     * Analytics opt-out toggle

7. HELP CENTER SCREEN:
   - Header: "Help Center"
   - Search bar: "Search help articles..."
   - Categories (cards):
     * Getting Started
     * Booking Services
     * My Plans
     * Billing & Payments
     * Technical Support
   - Each expands to articles list
   - Contact Support button at bottom

All screens:
- Consistent header with back button
- Form validation where needed
- Loading states
- Success/error messages
- Mobile-optimized inputs
```

---

## ✅ FINAL POLISH

### Prompt 28: Add Loading & Empty States
```
Add loading and empty states to all list screens:

LOADING STATES:
Create LoadingCard component:
- Skeleton loader (animated gray blocks)
- Mimics card structure
- Shimmer animation (light sweep across)

Use in:
- Home dashboard (while loading appointments)
- My Home (while loading inventory)
- Appointments list
- Service History list
- Plans list

Empty state patterns:
- Large icon (gray, 64px)
- Heading: "No [items] yet"
- Description: Short explanation
- Primary action button
- Illustration (optional)

Empty states needed:
1. No upcoming appointments:
   - Icon: Calendar with checkmark
   - "No upcoming appointments"
   - "Book your first service"
   - "Book Service" button

2. No inventory items:
   - Icon: Box
   - "No appliances added yet"
   - "Start building your home profile"
   - "Add Appliance" button

3. No service history:
   - Icon: ClipboardX
   - "No service history"
   - "Book your first service to see history"
   - "Browse Services" button

4. No reminders:
   - Icon: BellOff
   - "No reminders set"
   - "Add appliances to get maintenance reminders"

5. Filtered results empty:
   - Icon: Search
   - "No results found"
   - "Try adjusting your filters"
   - "Clear Filters" button

Error states:
- Network error
- API failure
- Permission denied
- "Try Again" button

Add pull-to-refresh to all lists:
- Visual indicator (spinner at top)
- OnRefresh: reload data
- Success/error feedback
```

### Prompt 29: Add Animations & Transitions
```
Add micro-interactions and transitions throughout the app:

SCREEN TRANSITIONS:
- Slide from right when pushing new screen
- Slide from left when going back
- Fade for modals
- Slide up for bottom sheets
- Duration: 300ms
- Easing: ease-in-out

BUTTON INTERACTIONS:
- Scale down to 0.98 on press
- Slight opacity change
- Haptic feedback (on capable devices)
- Loading spinner replaces text when processing

CARD INTERACTIONS:
- Subtle shadow increase on tap
- Scale: 0.98 on active
- Smooth transition (150ms)

LIST ANIMATIONS:
- Stagger fade-in when loading (50ms delay between items)
- Slide in from left/right alternating
- Fade out when removing

SUCCESS ANIMATIONS:
- Checkmark circle (scale + fade in)
- Confetti particles for achievements
- Star burst for points earned
- Bounce effect for badges

PROGRESS ANIMATIONS:
- Progress bars fill smoothly (500ms)
- Circular progress animate from 0
- Percentage counter animates up

SKELETON LOADERS:
- Shimmer sweep animation
- 1.5s duration
- Infinite loop
- Light gray → lighter gray → light gray

PULL TO REFRESH:
- Pull distance threshold: 80px
- Spinner rotation
- Bounce back animation

TAB TRANSITIONS:
- Slide content left/right when changing tabs
- Icon scale up slightly when active
- Blue dot fade in/out

FORM INTERACTIONS:
- Input focus: border color change (300ms)
- Label float up on focus
- Error shake animation
- Success checkmark fade in

SWIPE GESTURES:
- Swipe left on reminder → delete option
- Swipe right on appointment → reschedule
- Smooth follow motion
- Snap to position when released

Add loading state to all buttons:
- Spinner replaces text
- Button disabled during loading
- Success checkmark after completion
```

### Prompt 30: Responsive Design & Accessibility
```
Make all screens fully responsive and accessible:

RESPONSIVE BREAKPOINTS:
- Mobile: <640px (primary)
- Tablet: 640-1024px
- Desktop: >1024px (web version)

Responsive adjustments:
1. Home Dashboard:
   - Tablet: 2-column grid for cards
   - Desktop: 3-column grid
   - Max width: 1200px centered

2. Book Service:
   - Tablet: Side-by-side step view
   - Desktop: Summary sidebar

3. My Home:
   - Tablet: 3-column inventory grid
   - Desktop: 4-column grid

4. Plans:
   - Tablet: 2-column plan cards
   - Desktop: 3-column

ACCESSIBILITY:
1. Touch targets:
   - Minimum: 44x44px
   - Buttons: 48px height
   - Icons: 24px with padding

2. Color contrast:
   - Text: WCAG AA compliant
   - 4.5:1 ratio for body text
   - 3:1 ratio for large text
   - Don't rely on color alone for info

3. Labels & ARIA:
   - All inputs have labels
   - Buttons have descriptive text
   - Icons have aria-labels
   - Form errors announced
   - Loading states announced

4. Keyboard navigation (web):
   - Tab order logical
   - Focus indicators visible
   - Enter/Space activate buttons
   - Escape closes modals

5. Screen reader support:
   - Semantic HTML
   - Heading hierarchy
   - Alt text for images
   - Live regions for updates

6. Font scaling:
   - Support system font size preferences
   - Text remains readable when scaled
   - No hard-coded font sizes in px

SAFE AREAS:
- iOS notch/island: env(safe-area-inset-top)
- Android nav: env(safe-area-inset-bottom)
- Bottom tab bar accounts for safe area
- Modals respect safe areas

PERFORMANCE:
- Lazy load images
- Virtual lists for long lists (>50 items)
- Debounce search inputs (300ms)
- Optimize re-renders (React.memo)
- Image optimization (WebP)

TESTING CHECKLIST:
✅ All touch targets >= 44px
✅ Color contrast passes WCAG AA
✅ All images have alt text
✅ Forms have proper labels
✅ Keyboard navigation works
✅ Screen reader compatible
✅ Works on iPhone SE (small screen)
✅ Works on iPad (tablet)
✅ Works on desktop web
✅ Dark mode (optional)
✅ Landscape orientation

Add dark mode toggle (optional):
- Dark background: #1a1a1a
- Dark cards: #2a2a2a
- Adjusted text colors
- Icons adjusted for visibility
- Toggle in Account > Appearance
```

---

## 📋 BUILD ORDER SUMMARY

### Week 1: Foundation
**Day 1:**
- ✅ Setup project (Prompt 1)
- ✅ Bottom tab navigation (Prompt 2)
- ✅ Reusable components (Prompt 3)
- ✅ Mock data (Prompt 4)

**Day 2:**
- ✅ Home Dashboard (Prompts 5-7)
- ✅ Test navigation between tabs

### Week 2: Core Features
**Day 3:**
- ✅ Book Service setup & Steps 1-2 (Prompts 8-10)

**Day 4:**
- ✅ Book Service Steps 3-6 (Prompts 11-14)
- ✅ Confirmation screen (Prompt 15)

**Day 5:**
- ✅ My Home main screen (Prompt 16)
- ✅ Add item flow (Prompt 17)
- ✅ Item details (Prompt 18)

### Week 3: Plans & Appointments
**Day 6:**
- ✅ Plans main screen (Prompt 19)
- ✅ Plan details (Prompt 20)
- ✅ Enroll flow (Prompt 21)

**Day 7:**
- ✅ Appointments list (Prompt 22)
- ✅ Appointment details (Prompt 23)

### Week 4: History & Account
**Day 8:**
- ✅ Service History (Prompt 24)
- ✅ Service details (Prompt 25)

**Day 9:**
- ✅ Account main screen (Prompt 26)
- ✅ Account sub-screens (Prompt 27)

**Day 10:**
- ✅ Loading & empty states (Prompt 28)
- ✅ Animations (Prompt 29)
- ✅ Responsive & accessibility (Prompt 30)

---

## 🎯 SUCCESS CRITERIA

Before presenting to Duke Energy team:

✅ **Functionality:**
- All 7 main screens built and navigable
- Book service flow works end-to-end
- Tab navigation smooth
- Forms validate properly
- Mock data realistic

✅ **Design:**
- Duke Energy branding consistent
- Mobile-first design
- Touch-friendly (44px min)
- Clear visual hierarchy
- Status badges color-coded

✅ **User Experience:**
- Smooth animations
- Loading states
- Empty states
- Error handling
- Success feedback

✅ **Performance:**
- Fast load times
- Smooth scrolling
- No jank in animations
- Efficient re-renders

✅ **Accessibility:**
- Proper labels
- Color contrast
- Touch targets
- Screen reader support

✅ **Polish:**
- Consistent spacing
- Aligned elements
- Proper shadows
- Readable text
- Professional appearance

---

---

## 🛠️ ADDITIONAL FEATURE: AD-HOC SERVICE BOOKING

### Prompt 31: Ad-Hoc Service Catalog Screen (Browse Services)
```
Create src/screens/AdHocServiceCatalogScreen.tsx:

This screen allows customers to browse and book services NOT covered by their HPP plans.

HEADER (fixed):
- Title: "Home Services" (text-2xl font-bold)
- Filter button (funnel icon, top-right)
- Search bar: "Search services..." (below title)

FILTER CHIPS (horizontal scroll):
- "All Services" (active, blue)
- "HVAC"
- "Plumbing"
- "Electrical"
- "Appliances"
- Each chip: pill shape, tap to filter

SERVICE CATEGORIES:

1. FEATURED SERVICES SECTION:
   - Section title: "Popular Services" (with fire icon)
   - Horizontal scroll of service cards:

   Service Card 1 - HVAC Tune-Up:
   - Large card with photo/illustration
   - Icon: Thermometer (top-left)
   - Service name: "HVAC Seasonal Tune-Up" (bold)
   - Price: "$99" (large, duke-blue, prominent)
   - Description: "22-point inspection, filter replacement, coil cleaning"
   - Duration: "~2 hours"
   - Badge: "Most Popular" (gold)
   - Rating: 4.8 stars (127 reviews)
   - "Book Now" button (primary blue)

   Service Card 2 - Plumbing Drain Cleaning:
   - Icon: Droplets
   - Service name: "Professional Drain Cleaning"
   - Price: "$95" (fixed rate)
   - Description: "Clear clogs from sinks, tubs, showers"
   - Duration: "~1 hour"
   - Rating: 4.7 stars
   - "Book Now" button

   Service Card 3 - Ceiling Fan Installation:
   - Icon: Zap
   - Service name: "Ceiling Fan Installation"
   - Price: "$120-$190" (range)
   - Description: "Professional installation of customer-provided fan"
   - Duration: "1-2 hours"
   - Rating: 4.5 stars
   - "Book Now" button

2. PREVENTATIVE MAINTENANCE SECTION:
   - Section title: "Preventative Maintenance"
   - Subtitle: "Keep your home running smoothly"
   - Service cards (stacked):

   Service Card - Water Heater Flush:
   - Icon: Flame
   - Name: "Water Heater Flush & Inspection"
   - Price: "$75"
   - Description: "Annual maintenance to extend lifespan"
   - Duration: "1 hour"
   - Savings badge: "Save $30 vs. emergency repair"
   - "Book Now" button

   Service Card - Appliance Check:
   - Icon: Package
   - Name: "Appliance Safety Check"
   - Price: "$85"
   - Description: "Inspect refrigerator, dishwasher, washer/dryer"
   - Duration: "1.5 hours"
   - "Book Now" button

3. REPAIRS & INSTALLATIONS SECTION:
   - Section title: "Repairs & Installations"
   - Subtitle: "Need something fixed or installed?"
   - Service cards:

   Service Card - Outlet Installation:
   - Icon: Zap
   - Name: "Electrical Outlet Installation"
   - Price: "$85-$120"
   - Description: "Add outlets where you need them"
   - Pricing note: "Price varies by location and complexity"
   - "Book Now" button

   Service Card - Garbage Disposal:
   - Icon: Droplets
   - Name: "Garbage Disposal Replacement"
   - Price: "$150-$250"
   - Description: "Remove old unit and install new disposal"
   - Pricing note: "Customer provides disposal unit"
   - "Book Now" button

EACH SERVICE CARD STYLING:
- White background, rounded-xl
- Shadow: 0 2px 8px rgba(0,0,0,0.08)
- Padding: 16px
- Service photo/illustration at top (if available)
- Icon in category color (blue for HVAC, etc.)
- Name: text-lg font-semibold
- Price: text-2xl font-bold text-duke-blue
- Description: text-sm text-gray-600
- Metadata (duration, rating) in small gray text
- "Book Now" button: full width within card, primary blue

PRICING DISPLAY RULES:
- Fixed price: "$99" (single large number)
- Price range: "$120-$190" (with "Starting at" label for low end)
- Variable pricing: "$85+" (with "Varies by scope" subtitle)
- Discount badge: "Save $30" (green background, white text)

FILTER BOTTOM SHEET (when filter button tapped):
- Price Range:
  * Under $100
  * $100-$200
  * $200-$500
  * Over $500
- Service Type:
  * Preventative Maintenance
  * Repairs
  * Installations
  * Emergency
- Availability:
  * This week
  * Within 3 days
  * Within 5 days
  * Anytime
- "Apply Filters" button

OnPress "Book Now":
- Navigate to booking flow (same as HPP booking)
- Pre-fill service type and category
- Show ad-hoc pricing in review step
- Payment collection by contractor at completion

Empty state (if filtered to no results):
- Icon: Search
- "No services found"
- "Try adjusting your filters"
- "Clear Filters" button

Pull-to-refresh to reload services.
Infinite scroll or pagination for long lists.
```

### Prompt 32: Ad-Hoc Service Detail Screen
```
Create ServiceDetailScreen component (modal or full screen):

This screen shows detailed information about a specific ad-hoc service before booking.

HEADER:
- Back button (< icon)
- Title: Service name
- Share button (share icon, top-right)

HERO SECTION:
- Large service photo/illustration
- Service category badge: "HVAC Service" (blue)
- Popular badge: "Most Booked" (gold, if applicable)

SERVICE OVERVIEW CARD:
- Service name: "HVAC Seasonal Tune-Up" (text-xl font-bold)
- Rating: 4.8 stars (large, gold) with "(127 reviews)"
- Price: "$99" (text-3xl font-bold, duke-blue)
  * For range: "$120-$190" with "Final price determined on-site"
- Duration: "Approximately 2 hours"
- Next availability: "This week" (with calendar icon)

WHAT'S INCLUDED SECTION:
- Title: "What's Included"
- Checkmark list:
  * 22-point HVAC system inspection
  * Clean condenser and evaporator coils
  * Check refrigerant levels
  * Replace standard air filter (up to 16x25x1)
  * Test thermostat operation
  * Verify proper airflow
  * Check electrical connections
  * Lubricate moving parts
- Each with green checkmark icon

WHY BOOK THIS SERVICE SECTION:
- Title: "Why Book This Service?"
- Benefit cards (3 cards, small):

  Card 1 - Save Money:
  - Icon: DollarSign (green circle)
  - Title: "Prevent Costly Repairs"
  - Text: "Regular maintenance can prevent 95% of breakdowns"

  Card 2 - Efficiency:
  - Icon: Zap (blue circle)
  - Title: "Lower Energy Bills"
  - Text: "Well-maintained systems use 15-20% less energy"

  Card 3 - Comfort:
  - Icon: ThermometerSun (orange circle)
  - Title: "Better Comfort"
  - Text: "Optimal performance year-round"

PRICING DETAILS SECTION:
- Title: "Pricing & Payment"
- Price breakdown (if applicable):
  * Service: $89
  * Parts (filter): $10
  * Total: $99
- Payment info card (light blue background):
  * Icon: Info circle
  * "Payment collected by contractor at service completion"
  * "Accepted methods: Cash, check, credit card"
  * "Your contractor is equipped with secure payment processing"

CUSTOMER REVIEWS SECTION:
- Title: "Customer Reviews" (with star icon)
- Average rating: 4.8 out of 5 (127 reviews)
- Rating breakdown (bars):
  * 5 stars: 85 reviews (68%)
  * 4 stars: 32 reviews (25%)
  * 3 stars: 7 reviews (6%)
  * 2 stars: 2 reviews (1%)
  * 1 star: 1 review (1%)

Recent reviews (show 3):
Review Card 1:
- Customer name: "John D." (with avatar or initials)
- Rating: 5 stars (gold)
- Date: "2 weeks ago"
- Review text: "Technician was professional and thorough. Explained everything clearly. Great service!"
- Verified purchase badge: "✓ Verified Service"

Review Card 2:
- Customer: "Sarah M."
- Rating: 5 stars
- Date: "1 month ago"
- Review: "Very satisfied with the service. Arrived on time and completed work quickly."

"View All Reviews" link (opens reviews modal)

FREQUENTLY ASKED QUESTIONS:
- Expandable accordions:

  Q1: "How long does this service take?"
  A: "Approximately 2 hours, but may vary based on system condition and accessibility."

  Q2: "Do I need to be home?"
  A: "Yes, someone 18+ must be present during the service."

  Q3: "What if additional repairs are needed?"
  A: "Our technician will provide a detailed quote before performing any additional work."

  Q4: "Is this service covered by my protection plan?"
  A: "This is an ad-hoc service. Check your plan details to see if annual maintenance is included."

  Q5: "Can I schedule for a specific day?"
  A: "Yes! Choose your preferred date and time during booking."

SERVICE AREA:
- Title: "Service Area"
- Text: "Available in Durham, Raleigh, Chapel Hill, and surrounding areas"
- Map icon or small map thumbnail
- "Check Availability" link (enters zip code to verify)

ACTIONS (sticky at bottom):
- "Book This Service" button (primary blue, large, full width)
  * OnPress: Navigate to booking flow
  * Pre-fill service type = HVAC
  * Pre-fill service = HVAC Tune-Up
  * Pre-fill price = $99
- Small text: "No commitment until you confirm booking"

Three-dot menu (top-right):
- Share service
- Add to favorites
- Report issue

Scrollable content.
Clear section separation.
Mobile-optimized spacing.
```

### Prompt 33: Non-Native Customer Flow - Ad-Hoc Only
```
Create a variation of the booking flow for NON-NATIVE customers (no HPP plans):

SCENARIO: Customer does NOT have Duke utility service or HPP plans. They only want ad-hoc services.

STARTING POINT: Home Dashboard (Non-Native Version)

HOME DASHBOARD DIFFERENCES FOR NON-NATIVE:
- NO HPP Plans section
- NO "Covered by your plan" messaging
- Emphasis on ad-hoc services
- Hero card: "Welcome to Duke Energy Home Services" (instead of Home Health Score)
  * Message: "Professional home services without a subscription"
  * Subtitle: "Book services as you need them"
  * "Browse Services" button

QUICK ACTIONS (2 large buttons):
1. "Browse Services" (primary blue)
   - Navigate to Ad-Hoc Service Catalog
2. "Build Home Profile" (secondary)
   - Navigate to My Home inventory
   - Subtitle: "Get personalized service recommendations"

BOOKING FLOW FOR NON-NATIVE (Ad-Hoc Service):

STEP 1: Service Type Selection
- Same as existing flow
- NO coverage check messaging
- NO "Is this covered?" text

STEP 2: Select or Add Item
- Same as existing
- Emphasize: "Help us serve you better"
- Optional: "Skip - describe issue only"

STEP 3: Describe Issue
- Same symptom checklist
- NO "Coverage Check" section (skip that)
- NO "Likely covered" messaging
- Emergency triage still applies

STEP 4: Contractor Assignment (Same as MVP)
- Pre-assigned primary contractor
- Price displayed prominently: "$99"
- Payment info: "Payment collected at service completion"
- NO "$0 covered" option

STEP 5: Date & Time
- Same as existing flow
- Buffer info: "Standard service: 3-5 business days"

STEP 6: Review & Confirm
- Service Details card
- Contractor card
- Schedule card
- COST CARD (always shows price):
  * Price: "$99.00" (large, bold)
  * Payment section:
    - "Payment collected by contractor at service completion"
    - Accepted methods: Cash, check, credit card
    - NO "Covered by plan" messaging
- Terms checkbox (required)

STEP 7: Confirmation
- "Booking Submitted!"
- Status: "Pending Confirmation" (yellow)
- Reference number
- Summary with price: "$99 - Pay at completion"
- What happens next (same as existing)

AFTER FIRST SERVICE COMPLETION:

Show promotional banner on Home Dashboard:
- Background: Light blue gradient
- Icon: Shield
- Title: "Protect Your Home with a Plan"
- Message: "Save money and get priority service"
- Subtitle: "Starting at $9.99/month"
- "Explore Plans" button (navigates to Plans catalog)

UPSELL TOUCHPOINTS:
1. After booking ad-hoc service: "Would you like to add a protection plan?"
2. After service completion: "Join a plan and save on future services"
3. In account settings: "Protection Plans" menu item always visible
```

### Prompt 34: Sample Ad-Hoc Service Variations (Mock Data)
```
Add to src/data/mockData.ts - expand adHocServices array with more examples:

Export additional ad-hoc services to demonstrate various pricing models and categories:

// HVAC Services
{
  id: "svc-1",
  name: "HVAC Seasonal Tune-Up",
  category: "hvac",
  description: "22-point inspection, filter replacement, coil cleaning",
  price: 99,
  priceType: "fixed",
  includes: [
    "22-point system inspection",
    "Clean condenser and evaporator coils",
    "Check refrigerant levels",
    "Replace standard air filter",
    "Test thermostat operation",
    "Verify proper airflow",
    "Check electrical connections",
    "Lubricate moving parts"
  ],
  duration: "2 hours",
  rating: 4.8,
  reviewCount: 127,
  availability: "This week",
  badge: "Most Popular"
},

{
  id: "svc-2",
  name: "Emergency HVAC Repair",
  category: "hvac",
  description: "24-hour emergency repair service for heating or cooling failures",
  priceMin: 150,
  priceMax: 500,
  priceType: "range",
  pricingNote: "Price varies by issue complexity and parts needed",
  includes: [
    "Emergency diagnostic service",
    "Labor for repairs",
    "Priority scheduling (24 hours)"
  ],
  excludes: [
    "Parts and materials (quoted separately)"
  ],
  duration: "2-4 hours",
  rating: 4.6,
  reviewCount: 89,
  availability: "24 hours",
  badge: "Emergency Service"
},

// Plumbing Services
{
  id: "svc-3",
  name: "Professional Drain Cleaning",
  category: "plumbing",
  description: "Clear clogs from sinks, tubs, showers, and toilets",
  price: 95,
  priceType: "fixed",
  includes: [
    "Snake drain to clear clogs",
    "Inspect drain for issues",
    "Test water flow"
  ],
  duration: "1 hour",
  rating: 4.7,
  reviewCount: 156,
  availability: "3-5 days"
},

{
  id: "svc-4",
  name: "Toilet Replacement",
  category: "plumbing",
  description: "Remove old toilet and install customer-provided new toilet",
  priceMin: 150,
  priceMax: 250,
  priceType: "range",
  pricingNote: "Price varies by toilet type and installation complexity",
  includes: [
    "Remove and dispose of old toilet",
    "Install new wax ring",
    "Install new toilet",
    "Test for leaks",
    "Caulk around base"
  ],
  excludes: [
    "New toilet (customer provides)",
    "Water supply line replacement (if needed)"
  ],
  duration: "2-3 hours",
  rating: 4.5,
  reviewCount: 78,
  availability: "3-5 days"
},

// Electrical Services
{
  id: "svc-5",
  name: "Ceiling Fan Installation",
  category: "electrical",
  description: "Professional installation of customer-provided ceiling fan",
  priceMin: 120,
  priceMax: 190,
  priceType: "range",
  pricingNote: "Price varies by fan size and mounting complexity",
  includes: [
    "Install ceiling fan bracket",
    "Wire and mount ceiling fan",
    "Install fan blades",
    "Test operation",
    "Clean up"
  ],
  excludes: [
    "Ceiling fan (customer provides)",
    "New electrical wiring (quoted separately if needed)"
  ],
  duration: "1-2 hours",
  rating: 4.5,
  reviewCount: 92,
  availability: "3-5 days"
},

{
  id: "svc-6",
  name: "Electrical Outlet Installation",
  category: "electrical",
  description: "Add new electrical outlets where you need them",
  priceMin: 85,
  priceMax: 150,
  priceType: "range",
  pricingNote: "Price varies by location and whether new wiring is required",
  includes: [
    "Install new outlet box",
    "Wire outlet to existing circuit",
    "Install outlet cover",
    "Test for proper operation"
  ],
  duration: "1-2 hours",
  rating: 4.6,
  reviewCount: 64,
  availability: "5-6 days"
},

// Water Heater Services
{
  id: "svc-7",
  name: "Water Heater Flush & Inspection",
  category: "water-heater",
  description: "Annual maintenance to extend water heater lifespan",
  price: 75,
  priceType: "fixed",
  includes: [
    "Flush sediment from tank",
    "Inspect anode rod",
    "Check temperature and pressure relief valve",
    "Test thermostat",
    "Inspect for leaks"
  ],
  duration: "1 hour",
  rating: 4.8,
  reviewCount: 143,
  availability: "3-5 days",
  savingsNote: "Preventative maintenance can extend lifespan by 3-5 years"
},

// Appliance Services
{
  id: "svc-8",
  name: "Appliance Safety Check",
  category: "appliance",
  description: "Comprehensive inspection of refrigerator, dishwasher, and washer/dryer",
  price: 85,
  priceType: "fixed",
  includes: [
    "Inspect refrigerator seals and temperature",
    "Check dishwasher spray arms and filters",
    "Test washer hoses and connections",
    "Inspect dryer vent for clogs",
    "Provide maintenance recommendations"
  ],
  duration: "1.5 hours",
  rating: 4.7,
  reviewCount: 89,
  availability: "3-5 days"
},

{
  id: "svc-9",
  name: "Garbage Disposal Replacement",
  category: "plumbing",
  description: "Remove old disposal and install new unit",
  priceMin: 150,
  priceMax: 250,
  priceType: "range",
  pricingNote: "Customer provides disposal unit",
  includes: [
    "Disconnect and remove old disposal",
    "Install new mounting assembly",
    "Wire and mount new disposal",
    "Connect drain plumbing",
    "Test operation"
  ],
  excludes: [
    "New garbage disposal (customer provides)"
  ],
  duration: "2-3 hours",
  rating: 4.6,
  reviewCount: 71,
  availability: "3-5 days"
}

Add pricing display helper functions:

export const formatServicePrice = (service) => {
  if (service.priceType === 'fixed') {
    return `$${service.price}`;
  } else if (service.priceType === 'range') {
    return `$${service.priceMin}-$${service.priceMax}`;
  } else {
    return `$${service.priceMin}+`;
  }
};

export const getServicePriceLabel = (service) => {
  if (service.priceType === 'fixed') {
    return 'Fixed Price';
  } else if (service.priceType === 'range') {
    return 'Price Range';
  } else {
    return 'Starting At';
  }
};
```

### Prompt 35: Ad-Hoc Service Booking Confirmation Updates
```
Update the BookingConfirmation.tsx component to better handle ad-hoc services:

AD-HOC SPECIFIC CONFIRMATION MESSAGING:

COST REMINDER CARD (for ad-hoc only):
- Prominent card below summary
- Background: Light yellow (#FFF9E6)
- Border: 2px solid #FFC107 (warning color)
- Icon: AlertCircle (orange)
- Title: "Payment at Service Completion"
- Message: "Your technician will collect $99 at the end of your service"
- Accepted methods list (with icons):
  * Cash
  * Check
  * Credit/Debit Card
- Small text: "Please have payment ready when service is completed"

WHAT TO EXPECT CARD:
- Title: "What to Expect"
- Timeline steps:
  1. "We'll contact Carolina Comfort Services" (in progress)
     - "Confirming availability within 24 hours"
  2. "You'll receive confirmation"
     - "Via push notification and email"
  3. "Contractor arrives at scheduled time"
     - "Friday, March 15, 9:00 AM - 12:00 PM"
  4. "Service completed & payment collected"
     - "$99 - Cash, check, or credit card"
  5. "Rate your experience"
     - "Help us improve our service"

PREPARATION TIPS (expandable section):
- Title: "Prepare for Your Service" (chevron to expand)
- When expanded, show tips:
  * "Clear area around equipment for easy access"
  * "Secure pets in separate room"
  * "Have payment ready ($99)"
  * "List any questions for technician"

PROMOTIONAL BANNER (for non-native customers):
- Show after first ad-hoc service booking
- Background: Blue gradient
- Icon: Shield
- Title: "Save Money with a Protection Plan"
- Message: "Get priority service and save up to 20% on repairs"
- Price: "Plans starting at $9.99/month"
- "Learn More" button (navigate to Plans catalog)
- Dismissible (X button)

ADD TO ACTIONS:
- "Manage Payment" button (if payment integration available in Phase 2)
  * Shows saved payment methods
  * Allows pre-authorization (future)

PUSH NOTIFICATION CONTENT:
- Title: "Service Request Submitted"
- Message: "We're confirming your $99 HVAC Tune-Up for March 15"
- Action: "View Details"

EMAIL CONFIRMATION (mention in UI):
- "Confirmation email sent to eleanor.mitchell@email.com"
- Link: "Resend Email"
```

### Prompt 36: Create /services Route and Screen
```
Create the /services route to fix the 404 error. This route should display the Ad-Hoc Service Catalog.

ROUTE SETUP:
- Add route to router configuration: /services
- Component: ServicesScreen (or AdHocServiceCatalogScreen from Prompt 31)
- Navigation: Accessible from menu/navigation

If you already built AdHocServiceCatalogScreen from Prompt 31:
- Create src/screens/ServicesScreen.tsx that imports and renders AdHocServiceCatalogScreen
- OR simply update your router to point /services to AdHocServiceCatalogScreen

If you haven't built the service catalog yet, create src/screens/ServicesScreen.tsx:

HEADER (fixed):
- Title: "Browse Services" (text-2xl font-bold)
- Subtitle: "Professional home services" (text-sm text-gray-600)
- Search bar: "Search services..." (below title)
  * Icon: Search (left)
  * Placeholder: "Search by service name or category"
  * OnChange: filter services
- Filter button (funnel icon, top-right)
  * Opens filter bottom sheet

HERO BANNER (optional):
- Background: Blue gradient (from-duke-blue to-duke-blue-dark)
- Text: White
- Title: "Professional Home Services"
- Subtitle: "Transparent pricing, trusted contractors"
- Icon: Wrench or tools icon
- Dismissible (X button)

FILTER CHIPS (horizontal scroll):
- "All Services" (active, blue bg, white text)
- "HVAC" (gray bg, gray text)
- "Plumbing"
- "Electrical"
- "Appliances"
- "Water Heater"
- Each chip: pill shape (rounded-full), tap to filter

SERVICE CATEGORIES SECTIONS:

1. FEATURED SERVICES:
   Section title: "Popular Services" (text-lg font-semibold mb-4)

   Display service cards in grid (2 columns on mobile, 3 on tablet):

   Service Card Structure:
   - White background, rounded-xl, shadow-sm
   - Padding: 16px
   - Service category icon (top-left, colored circle):
     * HVAC: Thermometer (blue)
     * Plumbing: Droplets (teal)
     * Electrical: Zap (yellow)
     * Appliance: Package (purple)
   - Service name: "HVAC Tune-Up" (text-lg font-semibold)
   - Price: "$99" (text-2xl font-bold, duke-blue)
     * For ranges: "$120-$190" (text-xl)
   - Rating: 4.8 stars + "(127)" reviews (text-xs, gray)
   - Duration: "~2 hours" (text-xs, gray)
   - Description: "22-point inspection, filter replacement..." (text-sm, gray-600, 2 lines max, truncate)
   - Badge (if applicable): "Most Popular" (top-right, gold bg, white text, small)
   - "Book Now" button (primary blue, full width, mt-3)

   Featured Services to display:
   1. HVAC Seasonal Tune-Up - $99
   2. Professional Drain Cleaning - $95
   3. Ceiling Fan Installation - $120-$190

2. PREVENTATIVE MAINTENANCE:
   Section title: "Preventative Maintenance"
   Subtitle: "Keep your home running smoothly" (text-sm, gray)

   Service cards (same structure as above):
   1. Water Heater Flush & Inspection - $75
      - Badge: "Save $30" (green bg)
   2. Appliance Safety Check - $85
   3. HVAC Filter Replacement - $45

3. REPAIRS & INSTALLATIONS:
   Section title: "Repairs & Installations"
   Subtitle: "Expert fixes and installations" (text-sm, gray)

   Service cards:
   1. Electrical Outlet Installation - $85-$120
   2. Garbage Disposal Replacement - $150-$250
   3. Toilet Replacement - $150-$250
   4. Light Fixture Installation - $95-$150

4. EMERGENCY SERVICES:
   Section title: "Emergency Services"
   Banner: Red border, light red background
   Icon: AlertCircle (red)
   Text: "24/7 emergency service available"
   Phone: "Call 1-800-XXX-XXXX for immediate assistance"

   Service cards:
   1. Emergency HVAC Repair - $150-$500
      - Badge: "24/7 Available" (red)
   2. Emergency Plumbing - $125-$400
   3. Emergency Electrical - $175-$450

PRICING DISPLAY RULES:
- Fixed price: "$99" (single number, large)
- Price range: "$120-$190" (connected with dash)
- Variable: "$85+" (with plus sign)
- Show "Starting at" label for ranges (text-xs above price)

FILTER BOTTOM SHEET:
When filter button tapped, slide up bottom sheet with:

Title: "Filter Services" (text-xl font-bold)

Filter sections:
1. Price Range:
   - Radio buttons:
     * Under $100
     * $100-$200
     * $200-$500
     * Over $500
     * Any price (default)

2. Category:
   - Checkboxes (multi-select):
     * HVAC
     * Plumbing
     * Electrical
     * Appliances
     * Water Heater
     * Other

3. Service Type:
   - Checkboxes:
     * Preventative Maintenance
     * Repairs
     * Installations
     * Emergency

4. Availability:
   - Radio buttons:
     * This week
     * Within 3 days
     * Within 5 days
     * Anytime (default)

5. Rating:
   - Radio buttons:
     * 4.5+ stars
     * 4.0+ stars
     * 3.5+ stars
     * Any rating (default)

Actions at bottom:
- "Clear All" button (text button, left)
- "Apply Filters" button (primary blue, right)

SEARCH FUNCTIONALITY:
- Filter services by name or description as user types
- Show "No results found" if search returns empty
- Clear search button (X icon in search bar)

EMPTY STATE (when filtered to no results):
- Icon: Search (large, gray)
- Text: "No services found"
- Subtitle: "Try adjusting your filters or search"
- "Clear Filters" button (primary)
- "View All Services" button (secondary)

SERVICE CARD INTERACTIONS:
OnPress service card:
- Navigate to Service Detail Screen (from Prompt 32)
- OR navigate to booking flow with pre-filled service

OnPress "Book Now" button:
- Navigate to booking flow (Book Service - Step 1)
- Pre-fill service category
- Pre-fill service type
- Pre-fill pricing
- Continue through normal booking flow

INFINITE SCROLL:
- Show 12 services initially
- Load more as user scrolls
- Loading indicator at bottom
- "Load More" button as alternative

PULL TO REFRESH:
- Pull down to refresh service list
- Spinner animation
- Update service availability/pricing

NAVIGATION INTEGRATION:
- Update your router/navigation to include /services route
- Link from Home Dashboard "Browse Services" button
- Link from menu/navigation drawer
- Link from "Book Service" quick action (alternative flow)

MOBILE OPTIMIZATIONS:
- Service cards: grid-cols-1 on small mobile, grid-cols-2 on larger screens
- Touch targets: minimum 44x44px
- Sticky header with search bar
- Bottom padding to clear navigation/tab bar
- Safe area padding for notch/island

DATA SOURCE:
- Import adHocServices from mockData.ts (from Prompt 34)
- Or use your existing services data
- Map through services array to render cards

Example router update (if using React Router):
```
import ServicesScreen from './screens/ServicesScreen';

<Route path="/services" element={<ServicesScreen />} />
```

Example component structure:
```typescript
import React, { useState } from 'react';
import { adHocServices } from '../data/mockData';

const ServicesScreen = () => {
  const [filteredServices, setFilteredServices] = useState(adHocServices);
  const [searchQuery, setSearchQuery] = useState('');
  const [selectedCategory, setSelectedCategory] = useState('all');

  // Filter logic, search logic, etc.

  return (
    <div className="services-screen">
      {/* Header */}
      {/* Search bar */}
      {/* Filter chips */}
      {/* Service sections */}
    </div>
  );
};

export default ServicesScreen;
```

ACCESSIBILITY:
- All buttons have aria-labels
- Service cards have proper heading hierarchy
- Color contrast meets WCAG AA
- Keyboard navigation support
- Screen reader announcements for filters

Test the /services route to ensure it renders correctly and no longer shows 404.
```

---

**END OF AD-HOC SERVICE PROMPTS**

These additional prompts provide:
1. Ad-hoc service catalog/browse screen
2. Detailed service information screen
3. Non-native customer flow (no HPP plans)
4. Expanded mock data with various pricing models
5. Enhanced confirmation messaging for ad-hoc bookings

Copy these prompts AFTER building the core MVP prompts (1-30).
They extend the existing prototype with richer ad-hoc service experiences.

---

**END OF PROMPTS**

Copy these prompts sequentially into Lovable.
Test each screen after building.
Adjust styling as needed for Duke Energy brand.

Good luck building! 🚀📱
