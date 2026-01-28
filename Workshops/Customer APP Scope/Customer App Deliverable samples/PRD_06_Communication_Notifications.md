# PRD #6: Communication & Notifications

**Product Requirements Document**
**Duke Energy Residential Solutions - Home Services Mobile App**

**Version:** 1.0
**Last Updated:** January 2026
**Document Owner:** Orases Product Team
**Stakeholders:** Duke Residential Solutions Product Team, Duke IT, Customer Experience, Operations

---

## EXECUTIVE SUMMARY

### What We're Building

A comprehensive multi-channel notification system that keeps customers informed throughout their service journey with real-time updates via:
- **Push Notifications** - Instant alerts on mobile devices (iOS/Android)
- **SMS Notifications** - Text message updates (fallback if app not installed/open)
- **Email Notifications** - Detailed summaries and receipts
- **In-App Notifications** - Notification center with full history

**Key Notification Types:**
- **Service Booking**: Confirmation, scheduling, reminders
- **Contractor Updates**: Assigned, en route, arrived, completed
- **Payment & Billing**: Payment confirmations, receipts, failed payments
- **Plan Management**: Enrollment confirmations, renewal reminders, cancellation confirmations
- **Maintenance Reminders**: Proactive reminders based on home inventory
- **Promotional Offers**: Seasonal discounts, limited-time offers, referral bonuses

### Why It Matters

**For Customers:**
- **Transparency**: Know exactly where contractor is, when they'll arrive, what's happening
- **Peace of Mind**: Automatic updates eliminate "Where's my contractor?" anxiety
- **Control**: Choose how and when to receive notifications (preferences management)
- **No Missed Updates**: Multi-channel delivery ensures customers never miss critical updates

**For Duke Business:**
- **Customer Satisfaction**: 90% satisfaction with contractor communication target (per RFP)
- **Call Center Reduction**: Proactive notifications reduce "Where's my contractor?" calls by 30-40%
- **Engagement**: Push notifications drive app opens (3x higher engagement vs. no notifications)
- **Retention**: Timely maintenance reminders drive repeat bookings (40% increase in preventative maintenance)
- **Conversion**: Promotional notifications drive service bookings and plan enrollments (15-20% conversion)

**For Contractors:**
- **Reduced Calls**: Customers don't call asking for updates (system provides updates automatically)
- **Improved Perception**: Transparent communication improves contractor ratings (0.3-0.5 star increase)
- **Easier Coordination**: Automated notifications reduce contractor administrative burden

### Key Features

✅ **Push Notifications** - Instant alerts for booking confirmations, contractor updates, service completions
✅ **SMS Notifications** - Text messages for critical updates (fallback for customers without app)
✅ **Email Notifications** - Detailed summaries, receipts, documentation
✅ **In-App Notification Center** - Full history of all notifications with deep links to relevant screens
✅ **Notification Preferences** - Customer controls channels (push, SMS, email), frequency, types
✅ **Multi-Language Support** - English and Spanish (Phase 1), expand to additional languages (Phase 2)
✅ **Rich Notifications** - Images (contractor photo, truck), action buttons ("View Order", "Call Contractor")
✅ **Scheduled Notifications** - Maintenance reminders, appointment reminders (24 hours before service)
✅ **Event-Driven Architecture** - Real-time triggers from order status changes, payment events, plan changes

### Success Metrics

- **Notification Delivery Rate**: 98%+ successful delivery (not bounced or failed)
- **Open Rate**: 65%+ for push notifications, 25%+ for SMS, 35%+ for email
- **Customer Satisfaction**: 90%+ satisfaction with contractor communication (per RFP target)
- **Call Center Impact**: 30-40% reduction in "Where's my contractor?" calls
- **App Engagement**: 3x increase in daily active users (notifications drive app opens)
- **Opt-Out Rate**: <5% of customers opt out of notifications
- **Conversion Rate**: 15-20% conversion from promotional notifications to service bookings

---

## 1. BACKGROUND & PROBLEM STATEMENT

### 1.1 Current State

**How Customers Receive Service Updates Today:**

**Option 1: Wait for Phone Calls**
- Contractor calls customer to confirm service appointment (if they remember)
- Contractor calls customer when en route (sometimes forgotten)
- Customer has no visibility until contractor arrives
- **Pain Point**: Missed calls, voicemails, uncertainty about arrival time

**Option 2: Call Contractor for Updates**
- Customer calls contractor asking: "When are you coming?"
- Contractor may be driving, doesn't answer
- Customer calls Duke call center asking for update
- Call center has limited visibility into contractor status
- **Pain Point**: Wasted time calling for updates, frustration, poor experience

**Option 3: No Updates at All**
- Customer books service via phone, receives no confirmation
- No reminder before appointment
- No notification when contractor is en route
- Customer doesn't know service is complete until contractor leaves
- **Pain Point**: "Did they forget about me?" anxiety, poor transparency

**For Duke Business:**
- High volume of "Where's my contractor?" calls to call center (30-40% of support calls)
- Low customer satisfaction with contractor communication (40-50 NPS)
- Contractors field repetitive calls from anxious customers
- No mechanism for proactive communication (maintenance reminders, promotional offers)

### 1.2 Problems This Deliverable Solves

**Problem 1: "Where's My Contractor?" Anxiety**
- **Impact**: 30-40% of call center calls are customers asking for contractor ETA
- **Root Cause**: No proactive communication, customers left wondering
- **Cost**: Each call = $15-20 in call center cost, contractors interrupted by calls
- **Customer Quote**: *"I took the whole day off work waiting. Contractor showed up at 4pm. If I'd known, I could have run errands in the morning."* - Customer survey

**Problem 2: Missed Appointments**
- **Impact**: 10-15% no-show rate (customer forgets appointment, contractor shows up)
- **Root Cause**: No appointment reminder 24 hours before service
- **Cost**: Wasted contractor time, rescheduling burden, poor customer experience
- **Solution**: Automated appointment reminders reduce no-shows by 60% (industry benchmark)

**Problem 3: Low App Engagement**
- **Impact**: Customers download app, book service once, never return
- **Root Cause**: No reason to open app after booking (no updates, no reminders)
- **Opportunity**: Push notifications drive 3x higher daily active users vs. apps without notifications
- **Revenue Impact**: Higher engagement = more repeat bookings, plan enrollments, ad-hoc services

**Problem 4: Lack of Transparency Creates Poor Experience**
- **Impact**: 90% satisfaction target for contractor communication (per RFP) not achievable without transparency
- **Root Cause**: Customers feel "in the dark" about service status
- **Competitive Benchmark**: Uber-like experience requires real-time updates ("Your driver is 3 minutes away")
- **Customer Expectation**: Modern consumers expect Amazon/Uber-level communication transparency

**Problem 5: Missed Upsell and Retention Opportunities**
- **Impact**: Customers don't return for preventative maintenance (poor retention)
- **Root Cause**: No proactive reminders ("Your HVAC needs seasonal tune-up")
- **Revenue Impact**: Proactive maintenance reminders drive 40% increase in preventative service bookings
- **Plan Enrollment**: Post-service enrollment prompts convert 25% of ad-hoc customers to plan holders

### 1.3 Impact if Not Addressed

**Customer Experience:**
- **Low satisfaction**: 90% communication satisfaction target impossible without proactive notifications
- **High call volume**: Call center overwhelmed with "Where's my contractor?" calls
- **Poor perception**: Customers perceive Duke as outdated, not tech-forward

**Operational Costs:**
- **Call center burden**: 30-40% of calls are status inquiries = $500K+ annual cost
- **No-show costs**: 10-15% no-show rate = wasted contractor time, rescheduling overhead

**Revenue Loss:**
- **Low retention**: Customers don't return for repeat services (no maintenance reminders)
- **Missed upsells**: Can't send contextual offers (plan enrollment, seasonal promotions)
- **Low engagement**: App becomes single-use (book once, never return)

---

## 2. GOALS & SUCCESS CRITERIA

### 2.1 Primary Goals

**Goal 1: Achieve 90% Customer Satisfaction with Contractor Communication**
- **Target**: 90%+ satisfaction (per RFP target)
- **Measurement**: Post-service survey question: "How satisfied were you with communication during your service?"
- **Success Criteria**:
  - Customers receive confirmation within 5 minutes of booking
  - Customers receive reminder 24 hours before appointment
  - Customers notified when contractor is en route
  - Customers notified when service is complete

**Goal 2: Reduce "Where's My Contractor?" Call Volume by 30-40%**
- **Target**: 30-40% reduction in status inquiry calls
- **Baseline**: 30-40% of current call center volume = ~10,000 calls/month
- **Target**: Reduce to ~6,000-7,000 calls/month
- **Cost Savings**: ~$600K-$1M annual savings in call center costs

**Goal 3: Increase App Engagement by 3x**
- **Target**: 3x increase in daily active users (DAU) vs. baseline (no notifications)
- **Mechanism**: Push notifications drive app opens (customers tap notification → app opens)
- **Measurement**: DAU before notifications vs. after notifications launch

**Goal 4: Reduce No-Show Rate by 60%**
- **Target**: Reduce no-shows from 10-15% to 4-6%
- **Mechanism**: Automated appointment reminders 24 hours before service
- **Cost Savings**: Reduced wasted contractor time, fewer rescheduling calls

**Goal 5: Drive 40% Increase in Preventative Maintenance Bookings**
- **Target**: 40% increase in preventative services (HVAC tune-ups, water heater flushing, etc.)
- **Mechanism**: Proactive maintenance reminders based on home inventory data
- **Revenue Impact**: 40% increase = $10M+ additional GMV (if 100K customers book preventative services @ $100 avg)

### 2.2 Non-Goals (Explicitly Out of Scope)

❌ **Two-Way SMS Communication** - Customers cannot reply to SMS (one-way notifications only)
❌ **In-App Chat** - No real-time messaging between customer and contractor (phone/email only)
❌ **Voice Calls** - System does not initiate automated phone calls
❌ **Social Media Notifications** - No Facebook Messenger, WhatsApp integration (MVP)
❌ **Contractor-to-Customer Messaging** - Contractors cannot send custom messages via app (standardized templates only)
❌ **Real-Time GPS Tracking Notifications** - "Pizza tracker" ETA updates require FSM tool integration (Phase 2)

### 2.3 Success Metrics (Detailed)

**Delivery & Performance:**
- Notification delivery rate: 98%+ (successful delivery, not bounced)
- Push notification delivery time: <5 seconds from trigger event
- SMS delivery time: <30 seconds from trigger event
- Email delivery time: <5 minutes from trigger event
- Notification processing throughput: 10,000 notifications/minute

**Engagement:**
- Push notification open rate: 65%+ (industry benchmark: 40-60%)
- SMS open rate: 25%+ (industry benchmark: 15-25%)
- Email open rate: 35%+ (industry benchmark: 20-30%)
- Click-through rate (CTR): 15%+ tap "View Order" or action button

**Customer Satisfaction:**
- Communication satisfaction: 90%+
- "Notifications are helpful": 85%+ agree
- "Too many notifications": <10% (opt-out rate low)

**Business Impact:**
- Call center call reduction: 30-40%
- No-show rate reduction: 60% (from 10-15% to 4-6%)
- Preventative maintenance bookings increase: 40%
- Promotional notification conversion: 15-20% (click notification → book service)
- App engagement (DAU): 3x increase

**Opt-Out Rates:**
- Push notification opt-out: <5%
- SMS opt-out: <3%
- Email opt-out: <2%

---

## 3. SCOPE DEFINITION

### 3.1 In Scope for Phase 1 (MVP)

#### 3.1.1 Push Notifications (iOS & Android)

**Notification Types:**

**Service Booking Notifications:**
- ✅ Booking confirmed: "Service booked! [Contractor] will arrive [Date] [Time]"
- ✅ Appointment reminder (24 hours before): "Reminder: [Contractor] arrives tomorrow [Time]"
- ✅ Contractor assigned (if manual assignment): "Good news! [Contractor] has been assigned to your service"

**Contractor Status Notifications:**
- ✅ Contractor en route: "Your contractor is on the way! Estimated arrival: [Time]"
- ✅ Contractor arrived: "Your contractor has arrived and is starting work"
- ✅ Service in progress: "Your service is underway. [Contractor] is working on your [Service]"
- ✅ Service complete: "Your service is complete! Please rate your experience"

**Payment & Billing Notifications:**
- ✅ Payment successful: "Payment confirmed! $[Amount] charged to [Payment Method]"
- ✅ Payment failed: "Payment failed. Please update your payment method"
- ✅ Refund processed: "Your refund of $[Amount] has been processed"
- ✅ Receipt available: "Your receipt is ready. Tap to view"

**Plan Management Notifications:**
- ✅ Plan enrolled: "You're enrolled! [Plan Name] is now protecting your home"
- ✅ Plan cancelled: "[Plan Name] has been cancelled. Coverage ends [Date]"
- ✅ Plan renewal reminder (30 days before): "Your [Plan Name] renews on [Date]. Review your plan"
- ✅ Payment method expiring (30 days before): "Your payment method expires soon. Update now"

**Maintenance Reminder Notifications:**
- ✅ Seasonal reminders: "It's spring! Time for your HVAC tune-up. Book now and save $10"
- ✅ Equipment age reminders: "Your water heater is 12 years old (avg lifespan 10-15 years). Consider replacement"
- ✅ Recall alerts: "RECALL ALERT: Your [Appliance Model] has a safety recall. Schedule free repair"

**Promotional Notifications:**
- ✅ Limited-time offers: "Limited Time: $20 off HVAC tune-ups this month!"
- ✅ First-time customer offer: "Welcome! $10 off your first service. Book now"
- ✅ Referral program: "Refer a friend, earn $25 credit"

**Push Notification Features:**
- Rich notifications (images, contractor photo, truck logo)
- Action buttons ("View Order", "Call Contractor", "Book Service")
- Deep links (tap notification → open specific screen in app)
- Notification badges (app icon shows unread count)
- Sound and vibration (customizable per notification type)

#### 3.1.2 SMS Notifications

**SMS Use Cases:**
- Fallback for customers who haven't installed app yet (booked service via web)
- Critical alerts (contractor en route, service cancelled, payment failed)
- Appointment reminders (24 hours before service)

**SMS Message Types:**

**Service Booking:**
- "Duke Energy: Service booked! [Contractor] arrives [Date] [Time]. View details: [Link]"
- "Duke Energy: Reminder - [Contractor] arrives tomorrow [Time]. Questions? Call [Phone]"

**Contractor Updates:**
- "Duke Energy: Your contractor is on the way! ETA [Time]. Track status: [Link]"
- "Duke Energy: Service complete! Rate experience: [Link]"

**Payment & Billing:**
- "Duke Energy: Payment of $[Amount] confirmed. Receipt: [Link]"
- "Duke Energy: Payment failed. Update method: [Link]"

**SMS Features:**
- Short URLs (bit.ly or similar) linking to app or mobile web
- Sender ID: "Duke Energy" or "Duke Home" (branded)
- Opt-out link: "Reply STOP to unsubscribe"
- Delivery tracking (track if SMS delivered successfully)
- Rate limiting (max 3 SMS per day per customer to avoid spam perception)

**SMS Gateway:**
- Twilio (recommended for reliability and deliverability)
- AWS SNS (alternative, lower cost but less feature-rich)
- Support for US and Canada phone numbers (international Phase 2)

#### 3.1.3 Email Notifications

**Email Message Types:**

**Service Booking Emails:**
- ✅ Booking confirmation: Subject: "Service Confirmed: [Service] on [Date]"
  - Full booking details (service, contractor, date/time, property address)
  - Contractor contact info (phone, email)
  - "Add to Calendar" button (iCal attachment)
  - Link to reschedule or cancel
- ✅ Appointment reminder (24 hours before): Subject: "Tomorrow: [Service] with [Contractor]"
  - Service details, preparation instructions
  - "What to expect" section
  - Contact contractor button

**Service Status Emails:**
- ✅ Service completion summary: Subject: "Service Complete: [Service] on [Date]"
  - Work performed summary (contractor notes)
  - Before/after photos (if contractor uploaded)
  - Receipt or invoice
  - "Rate Your Experience" link

**Payment & Billing Emails:**
- ✅ Payment receipt: Subject: "Receipt: $[Amount] for [Service]"
  - Itemized receipt (service, parts, labor if applicable)
  - Payment method (Apple Pay xxxx-1234)
  - PDF receipt attachment
- ✅ Payment failed: Subject: "Action Required: Payment Failed for [Service]"
  - Failed payment details
  - Link to update payment method
  - Grace period deadline

**Plan Management Emails:**
- ✅ Plan enrollment confirmation: Subject: "Welcome to [Plan Name]!"
  - Plan details and coverage summary
  - Terms & Conditions PDF attachment
  - "View My Plans" button
- ✅ Plan cancellation confirmation: Subject: "[Plan Name] Cancelled"
  - Cancellation effective date
  - Final charge details
  - Re-enrollment instructions

**Maintenance Reminder Emails:**
- ✅ Seasonal maintenance: Subject: "Spring HVAC Tune-Up: Schedule Now"
  - Why seasonal maintenance matters (benefits)
  - Special offer (if applicable)
  - "Book Service" button
- ✅ Equipment age alerts: Subject: "Your [Appliance] May Need Attention"
  - Appliance age and typical lifespan
  - Recommended service or replacement
  - "Request Quote" button

**Email Features:**
- Responsive HTML templates (mobile-friendly)
- Duke Energy branding (logo, colors, typography)
- Personalization (customer name, property address, service details)
- Unsubscribe link (footer): "Manage notification preferences"
- Email tracking (open rates, click rates via tracking pixels)

**Email Service Provider (ESP):**
- SendGrid (recommended for transactional emails, strong deliverability)
- Mailgun (alternative, good API)
- AWS SES (low cost, but requires more setup for deliverability)

#### 3.1.4 In-App Notification Center

**Notification Center Features:**
- ✅ List of all notifications (chronological, newest first)
- ✅ Notification cards display:
  - Icon (service, contractor, payment, plan)
  - Heading: "Service Complete"
  - Message: "Your HVAC Tune-Up is complete! Please rate your experience."
  - Timestamp: "2 hours ago"
  - Read/unread indicator (blue dot for unread)
  - Action button: "View Order" or "Rate Service"
- ✅ Filter notifications:
  - All Notifications (default)
  - Services (booking, contractor updates, completions)
  - Payments (payment confirmations, receipts, failures)
  - Plans (enrollments, renewals, cancellations)
  - Reminders (maintenance, appointments, renewals)
- ✅ Mark all as read
- ✅ Delete notification (swipe to delete)
- ✅ Deep links (tap notification → navigate to relevant screen)

**Empty State:**
- "No notifications yet. We'll keep you updated on your services and plans!"

**Notification Retention:**
- Keep notifications for 90 days (auto-delete after 90 days)
- Customer can manually delete anytime

#### 3.1.5 Notification Preferences

**Preference Settings Screen:**
- ✅ Customer controls notification channels:
  - **Push Notifications**: On/Off toggle (per notification type)
  - **SMS**: On/Off toggle (per notification type)
  - **Email**: On/Off toggle (per notification type)
- ✅ Notification types:
  - **Service Updates**: Booking confirmations, contractor updates, completions (default: ON for all channels)
  - **Payment & Billing**: Payment confirmations, receipts, failed payments (default: ON for push/email, OFF for SMS)
  - **Plan Management**: Enrollments, renewals, cancellations (default: ON for email, OFF for push/SMS)
  - **Maintenance Reminders**: Seasonal reminders, equipment age alerts (default: ON for push/email, OFF for SMS)
  - **Promotional Offers**: Limited-time offers, discounts, referrals (default: ON for push/email, OFF for SMS)
- ✅ Quiet Hours:
  - Enable quiet hours (no push notifications during specified time)
  - Start time: 9:00 PM (default)
  - End time: 8:00 AM (default)
  - Applies to: Promotional and reminder notifications only (service updates bypass quiet hours)

**Default Settings (Sensible Defaults):**
- Service updates: All channels ON (critical updates)
- Payments: Push and email ON, SMS OFF (not urgent enough for SMS)
- Plans: Email ON, push and SMS OFF (low urgency)
- Reminders: Push and email ON, SMS OFF
- Promotions: Push and email ON, SMS OFF (respect SMS spam concerns)

**Opt-Out Mechanisms:**
- **Push**: System-level (iOS/Android settings) OR in-app toggle
- **SMS**: Reply "STOP" to any SMS OR in-app toggle
- **Email**: Unsubscribe link in footer OR in-app toggle

#### 3.1.6 Event-Driven Architecture

**Notification Trigger Events:**

**Service Booking Events:**
- `service.booked` → Send booking confirmation (push, SMS, email)
- `service.scheduled` → Send scheduling confirmation (push, email)
- `service.reminder` → Send 24-hour appointment reminder (push, SMS, email)

**Contractor Status Events:**
- `contractor.assigned` → Send contractor assignment notification (push, email)
- `contractor.en_route` → Send "contractor on the way" notification (push, SMS)
- `contractor.arrived` → Send "contractor arrived" notification (push)
- `service.in_progress` → Send "service underway" notification (push)
- `service.completed` → Send service completion notification (push, SMS, email)

**Payment Events:**
- `payment.successful` → Send payment confirmation (push, email)
- `payment.failed` → Send payment failure alert (push, SMS, email)
- `refund.processed` → Send refund confirmation (push, email)

**Plan Management Events:**
- `plan.enrolled` → Send enrollment confirmation (push, email)
- `plan.cancelled` → Send cancellation confirmation (push, email)
- `plan.renewal_reminder` → Send renewal reminder 30 days before (push, email)
- `payment_method.expiring` → Send payment expiration warning (push, email)

**Maintenance Events:**
- `maintenance.seasonal_reminder` → Send seasonal maintenance reminder (push, email)
- `equipment.age_alert` → Send equipment age alert based on inventory (push, email)
- `recall.alert` → Send CPSC recall alert (push, SMS, email - critical)

**Promotional Events:**
- `promotion.limited_time` → Send limited-time offer (push, email)
- `promotion.first_time_discount` → Send first-time customer offer (push, email)
- `referral.bonus_available` → Send referral bonus notification (push, email)

**Event Processing:**
- Events published to message queue (AWS SQS, RabbitMQ, or similar)
- Notification service subscribes to queue, processes events
- Check customer preferences (is push enabled for this event type?)
- Compose notification message (templating)
- Send notification via appropriate channels (push, SMS, email)
- Log notification delivery (tracking, analytics)

#### 3.1.7 Notification Templates

**Template Structure:**
- Template ID (e.g., `service_booked_push`)
- Template content with variables: `"Service booked! {{contractor_name}} will arrive {{date}} {{time}}"`
- Variables replaced at runtime with customer/service data
- Multi-language support (English, Spanish)

**Template Management:**
- Stored in database (easy updates without code deployment)
- Version history (track template changes over time)
- A/B testing support (test different message variations)
- Preview mode (preview notification before sending)

**Template Examples:**

**Push Notification Template:**
```json
{
  "template_id": "service_booked_push",
  "title": "Service Booked!",
  "body": "{{contractor_name}} will arrive {{date}} at {{time}}",
  "deep_link": "dukeapp://service/{{service_id}}",
  "action_buttons": [
    {"label": "View Order", "action": "open_service_detail"},
    {"label": "Call Contractor", "action": "call_contractor"}
  ]
}
```

**SMS Template:**
```
Duke Energy: Service booked! {{contractor_name}} arrives {{date}} {{time}}. View details: {{short_url}}
```

**Email Template:**
```html
Subject: Service Confirmed: {{service_name}} on {{date}}

<h1>Your service is confirmed!</h1>
<p>{{contractor_name}} will arrive at {{property_address}} on {{date}} between {{time_window}}.</p>

<a href="{{deep_link}}" style="button">View Order Details</a>
```

---

## 4. FUNCTIONAL REQUIREMENTS

### 4.1 Push Notification Infrastructure

**FR-1: Push Notification Service Integration**
- **Requirement**: System shall integrate with push notification service for iOS and Android
- **Service**: Firebase Cloud Messaging (FCM) - supports both iOS and Android
- **Device Registration**:
  - Upon app install, register device token with FCM
  - Store device token in database (linked to customer account)
  - Support multiple devices per customer (phone + tablet)
- **Token Refresh**: Handle token expiration, update database when token refreshes

**FR-2: Push Notification Delivery**
- **Requirement**: System shall send push notifications to customer devices with <5 second delivery time
- **Delivery Flow**:
  1. Event triggered (e.g., service booked)
  2. Check customer preferences (is push enabled for service updates?)
  3. Retrieve device tokens for customer
  4. Compose notification (title, body, deep link, action buttons)
  5. Send to FCM API
  6. FCM delivers to device
  7. Log delivery status (delivered, failed, device unavailable)
- **Performance**: Process 10,000 notifications/minute

**FR-3: Rich Push Notifications**
- **Requirement**: System shall support rich push notifications with images and action buttons
- **Features**:
  - **Images**: Contractor photo, truck logo, service icon
  - **Action Buttons**: "View Order", "Call Contractor", "Reschedule"
  - **Deep Links**: Tap notification → open specific screen in app
  - **Badge Count**: Show unread notification count on app icon
- **Platform Support**: iOS (UNUserNotificationCenter), Android (NotificationCompat)

**FR-4: Notification Badges**
- **Requirement**: System shall display unread notification count on app icon
- **Logic**:
  - Increment badge count when new notification arrives
  - Decrement badge count when customer views notification
  - Reset badge count when customer opens notification center
- **Platform Support**: iOS (native badge), Android (notification dot)

**FR-5: Quiet Hours**
- **Requirement**: System shall respect customer's quiet hours preferences for non-urgent notifications
- **Logic**:
  - If quiet hours enabled (9 PM - 8 AM default)
  - Check notification urgency: Service updates = urgent (bypass), Promotional = non-urgent (hold)
  - If non-urgent + within quiet hours → queue notification, send when quiet hours end
  - If urgent → send immediately regardless of quiet hours
- **Override**: Critical alerts (contractor arrived, payment failed) always bypass quiet hours

### 4.2 SMS Notification Infrastructure

**FR-6: SMS Service Integration**
- **Requirement**: System shall integrate with SMS gateway for text message delivery
- **Service**: Twilio (recommended) or AWS SNS
- **Phone Number Validation**:
  - Customer provides phone number during registration
  - Validate phone number format (E.164 format: +1XXXXXXXXXX)
  - Verify phone number ownership (SMS verification code during registration)

**FR-7: SMS Delivery**
- **Requirement**: System shall send SMS notifications with <30 second delivery time
- **Delivery Flow**:
  1. Event triggered (e.g., contractor en route)
  2. Check customer preferences (is SMS enabled for service updates?)
  3. Retrieve customer phone number
  4. Compose SMS message (max 160 characters, include short URL)
  5. Send to Twilio API
  6. Twilio delivers SMS
  7. Log delivery status (delivered, failed, unsubscribed)
- **Performance**: Process 5,000 SMS/minute

**FR-8: SMS Rate Limiting**
- **Requirement**: System shall limit SMS frequency to avoid spam perception
- **Limits**:
  - Max 3 SMS per customer per day (for non-urgent notifications)
  - Urgent notifications (service updates) exempt from limit
  - Promotional SMS: Max 2 per week
- **Override**: Critical alerts exempt from rate limiting

**FR-9: SMS Opt-Out Handling**
- **Requirement**: System shall process SMS opt-out requests (STOP replies)
- **Opt-Out Flow**:
  1. Customer replies "STOP" to any SMS
  2. Twilio forwards reply to webhook
  3. System marks customer as SMS opt-out in database
  4. System sends confirmation SMS: "You've unsubscribed from Duke Energy SMS. Reply START to resubscribe."
  5. Future SMS notifications not sent to this customer
- **Opt-In**: Customer can reply "START" to re-enable SMS or toggle in app preferences

**FR-10: Short URL Generation**
- **Requirement**: SMS messages shall include short URLs linking to app or mobile web
- **URL Shortener**: Bitly API or custom URL shortener
- **Example**: "View details: bit.ly/duke-order-12345"
- **Deep Link Handling**: Short URL redirects to app (if installed) or mobile web (if not)

### 4.3 Email Notification Infrastructure

**FR-11: Email Service Integration**
- **Requirement**: System shall integrate with email service provider for email delivery
- **Service**: SendGrid (recommended) or AWS SES
- **Email Validation**:
  - Customer provides email during registration
  - Validate email format
  - Send verification email (confirm ownership)

**FR-12: Email Delivery**
- **Requirement**: System shall send email notifications with <5 minute delivery time
- **Delivery Flow**:
  1. Event triggered (e.g., service completed)
  2. Check customer preferences (is email enabled for service updates?)
  3. Retrieve customer email address
  4. Compose email (HTML template with variables replaced)
  5. Send to SendGrid API
  6. SendGrid delivers email
  7. Log delivery status (delivered, bounced, opened, clicked)
- **Performance**: Process 10,000 emails/minute

**FR-13: Email Templates**
- **Requirement**: System shall use responsive HTML email templates with Duke branding
- **Template Features**:
  - Responsive design (mobile-friendly)
  - Duke Energy logo, colors, typography
  - Personalization (customer name, service details)
  - Action buttons ("View Order", "Book Service")
  - Footer with unsubscribe link, contact info
- **Template Management**: Store templates in database, version control

**FR-14: Email Tracking**
- **Requirement**: System shall track email open rates and click rates
- **Tracking Mechanisms**:
  - **Open tracking**: 1x1 transparent pixel in email, logs when loaded
  - **Click tracking**: Links wrapped with tracking redirect, logs when clicked
- **Metrics Collected**:
  - Email sent: Timestamp
  - Email delivered: Timestamp (or bounced)
  - Email opened: Timestamp, device type
  - Email clicked: Timestamp, which link clicked
- **Dashboard**: Display email performance metrics (open rate, click rate per template)

**FR-15: Email Unsubscribe**
- **Requirement**: System shall provide unsubscribe link in all marketing emails
- **Unsubscribe Flow**:
  1. Customer clicks "Unsubscribe" link in email footer
  2. Opens unsubscribe page (web): "Unsubscribe from Duke Energy emails"
  3. Options:
     - Unsubscribe from promotional emails only (keep service updates)
     - Unsubscribe from all emails (except critical: payment failures, cancellations)
  4. Customer selects preference, clicks "Unsubscribe"
  5. System updates customer preferences in database
  6. Confirmation: "You've unsubscribed. You can re-enable emails anytime in app settings."
- **Legal Compliance**: CAN-SPAM Act requires unsubscribe link, process within 10 business days

### 4.4 Notification Preferences Management

**FR-16: Notification Preferences Screen**
- **Requirement**: System shall provide UI for customers to manage notification preferences
- **Settings Options**:
  - **Service Updates**: Push ON, SMS ON, Email ON (defaults)
  - **Payments**: Push ON, SMS OFF, Email ON
  - **Plans**: Push OFF, SMS OFF, Email ON
  - **Reminders**: Push ON, SMS OFF, Email ON
  - **Promotions**: Push ON, SMS OFF, Email ON
- **Toggle Behavior**: Customer taps toggle, preference saved immediately (no "Save" button required)
- **Sync**: Preferences synced across all devices (stored server-side)

**FR-17: Quiet Hours Setting**
- **Requirement**: System shall allow customer to set quiet hours (no notifications during specified time)
- **Settings**:
  - Enable quiet hours: Toggle (default OFF)
  - Start time: Time picker (default 9:00 PM)
  - End time: Time picker (default 8:00 AM)
  - Applies to: Promotional and reminder notifications only (service updates bypass)
- **Logic**: If current time is within quiet hours AND notification is non-urgent → queue until quiet hours end

**FR-18: Preference Defaults**
- **Requirement**: System shall apply sensible default preferences for new customers
- **Defaults**:
  - Service updates: All channels ON (critical)
  - Payments: Push and email ON, SMS OFF
  - Plans: Email ON, push and SMS OFF
  - Reminders: Push and email ON, SMS OFF
  - Promotions: Push and email ON, SMS OFF
  - Quiet hours: OFF (no quiet hours by default)
- **Onboarding**: During registration, briefly explain notification preferences, allow customization

### 4.5 In-App Notification Center

**FR-19: Notification List Display**
- **Requirement**: System shall display chronological list of all notifications in notification center
- **Display**: Notification cards (icon, heading, message, timestamp, read/unread indicator)
- **Sorting**: Newest first (default), customer can sort by oldest first
- **Pagination**: Load 20 notifications per page, infinite scroll to load more
- **Performance**: Load first 20 notifications within 1 second

**FR-20: Read/Unread Tracking**
- **Requirement**: System shall track which notifications customer has viewed
- **Logic**:
  - When customer opens notification center, mark all visible notifications as "read"
  - Blue dot indicator on unread notifications
  - Badge count on Notification Center icon (shows unread count)
- **Mark All as Read**: Customer can tap "Mark All as Read" button

**FR-21: Notification Deep Links**
- **Requirement**: System shall navigate customer to relevant screen when tapping notification
- **Deep Link Mapping**:
  - Service booked → Service detail screen
  - Payment confirmed → Receipt screen
  - Plan enrolled → Plan detail screen
  - Maintenance reminder → Service catalog (filtered to relevant service)
- **Fallback**: If deep link target unavailable, navigate to app home

**FR-22: Delete Notification**
- **Requirement**: System shall allow customer to delete notifications
- **Interaction**: Swipe left on notification → "Delete" button appears
- **Confirmation**: No confirmation required (immediate delete)
- **Undo**: Optional "Undo" snackbar appears after delete (5 second undo window)

**FR-23: Notification Retention**
- **Requirement**: System shall auto-delete notifications after 90 days
- **Logic**: Daily cron job deletes notifications older than 90 days
- **Customer Override**: Customer can manually delete anytime (swipe to delete)

### 4.6 Multi-Language Support

**FR-24: Language Selection**
- **Requirement**: System shall support notifications in English and Spanish (Phase 1)
- **Language Detection**: Use customer's app language preference (set in profile settings)
- **Fallback**: If customer language not supported, default to English

**FR-25: Template Localization**
- **Requirement**: All notification templates shall have English and Spanish versions
- **Storage**: Templates stored with language code (en-US, es-US)
- **Variables**: Variables ({{contractor_name}}, {{date}}) language-agnostic (remain unchanged)
- **Date/Time Formatting**: Format dates and times according to customer's locale

---

## 5. DEPENDENCIES & RISKS

### 5.1 Technical Dependencies

**Dependency 1: Push Notification Service (Firebase Cloud Messaging)**
- **Description**: Third-party service for push notification delivery
- **Required for**: Push notifications to iOS and Android devices
- **Risk**: FCM service outage = no push notifications delivered
- **Mitigation**: Monitor FCM status, have fallback to SMS/email for critical notifications

**Dependency 2: SMS Gateway (Twilio or AWS SNS)**
- **Description**: Third-party service for SMS delivery
- **Required for**: Text message notifications
- **Risk**: High SMS volume may require rate limit increases, cost per SMS
- **Mitigation**: Start with Twilio (reliable), rate limit SMS to 3/day to control costs

**Dependency 3: Email Service Provider (SendGrid or AWS SES)**
- **Description**: Third-party service for email delivery
- **Required for**: Email notifications, receipts, confirmations
- **Risk**: Poor sender reputation = emails land in spam
- **Mitigation**: Use SendGrid (high deliverability), implement DKIM/SPF/DMARC authentication

**Dependency 4: Service Order APIs**
- **Description**: Backend APIs that trigger notification events (service booked, contractor assigned, etc.)
- **Required for**: Event-driven notifications
- **Risk**: If APIs don't emit events, notifications won't trigger
- **Mitigation**: Ensure all service order state changes emit events to message queue

**Dependency 5: Customer Preference Storage**
- **Description**: Database storing customer notification preferences
- **Required for**: Respecting opt-outs, quiet hours, channel preferences
- **Risk**: If preference data lost, customers receive unwanted notifications (opt-out violations)
- **Mitigation**: Database backups, redundancy, strict data integrity checks

### 5.2 Business Dependencies

**Dependency 1: Notification Content Approval**
- **Description**: Duke legal/marketing must approve notification messaging
- **Decision Required**: Exact wording for critical notifications (payment failures, cancellations, legal disclaimers)
- **Timeline**: Approval needed before launch (2-4 weeks for legal review)
- **Owner**: Duke legal + Duke marketing team

**Dependency 2: Contractor Participation**
- **Description**: Contractors must update service status via contractor portal to trigger notifications
- **Risk**: If contractors don't update status, customers don't receive "en route" or "completed" notifications
- **Mitigation**: Train contractors on status updates, make status updates mandatory in contractor workflow

**Dependency 3: Promotional Calendar**
- **Description**: Duke marketing defines promotional notification calendar (seasonal offers, limited-time discounts)
- **Decision Required**: When to send promotions, how often, target audience
- **Timeline**: Rolling calendar, updated monthly
- **Owner**: Duke marketing team

### 5.3 Risks

**Risk 1: Notification Fatigue / Spam Perception**
- **Description**: Too many notifications annoy customers, leading to opt-outs or app uninstalls
- **Probability**: Medium (if not carefully managed)
- **Impact**: High (defeats purpose of notifications if customers opt out)
- **Mitigation**:
  - Default settings are conservative (no promotional SMS, limited promotional push)
  - Rate limiting (max 3 SMS/day, max 5 push/day for non-urgent)
  - Quiet hours support
  - Easy opt-out mechanisms
- **Monitoring**: Track opt-out rates, if >5% investigate and adjust

**Risk 2: SMS Cost Overruns**
- **Description**: SMS costs $0.0075-$0.01 per message, high volume = significant cost
- **Probability**: Medium (if SMS overused)
- **Impact**: Medium (budget overrun, but manageable)
- **Mitigation**:
  - Default SMS OFF for non-critical notifications
  - Rate limit SMS to 3/day per customer
  - Use push and email as primary channels, SMS as fallback
- **Cost Model**: 100K customers x 3 SMS/day x 30 days x $0.01 = $90K/month (if all customers opted in)
- **Realistic Cost**: Assume 30% SMS opt-in rate = $27K/month

**Risk 3: Email Deliverability Issues**
- **Description**: Emails land in spam folder, customers don't receive critical notifications
- **Probability**: Medium (common issue with transactional emails)
- **Impact**: High (customers miss payment confirmations, appointment reminders)
- **Mitigation**:
  - Use reputable ESP (SendGrid) with high sender reputation
  - Implement SPF, DKIM, DMARC email authentication
  - Monitor bounce rates and spam complaints
  - Avoid spammy language in subject lines
- **Monitoring**: Track delivery rate (>98% target), open rate (>35% target)

**Risk 4: Device Token Expiration**
- **Description**: Push notification device tokens expire, notifications fail to deliver
- **Probability**: Low (FCM handles token refresh automatically)
- **Impact**: Medium (push notifications fail for subset of users)
- **Mitigation**:
  - Handle token refresh events from FCM
  - Retry failed notifications via SMS/email
  - Monitor delivery failure rates

**Risk 5: Notification Delay**
- **Description**: Notifications arrive late (contractor arrived 30 minutes ago, customer receives notification now)
- **Probability**: Low (with proper infrastructure)
- **Impact**: High (defeats purpose of real-time updates)
- **Mitigation**:
  - Use message queue (AWS SQS) for event processing
  - Monitor notification latency (<5 sec for push, <30 sec for SMS, <5 min for email)
  - Auto-scaling for notification service (handle traffic spikes)

---

## 6. IMPLEMENTATION PLAN

### 6.1 Development Phases

**Phase 1: Foundation (Weeks 1-3)**
- Set up notification service architecture
- Integrate Firebase Cloud Messaging (FCM) for push notifications
- Integrate Twilio for SMS notifications
- Integrate SendGrid for email notifications
- Build notification preferences storage (database schema)
- Implement event-driven architecture (message queue)

**Phase 2: Core Notifications (Weeks 4-8)**
- Implement service booking notifications (push, SMS, email)
- Implement contractor status notifications (en route, arrived, completed)
- Implement payment notifications (success, failure, refund)
- Build notification templates (English)
- Test notification delivery end-to-end

**Phase 3: In-App Notification Center (Weeks 9-11)**
- Build notification center UI (list view, filters, read/unread)
- Implement deep links (tap notification → navigate to screen)
- Implement mark as read/delete functionality
- Test notification center UX

**Phase 4: Preferences & Personalization (Weeks 12-14)**
- Build notification preferences screen (channel toggles, type toggles)
- Implement quiet hours functionality
- Implement opt-out handling (SMS STOP, email unsubscribe)
- Test preference persistence across devices

**Phase 5: Maintenance & Promotional Notifications (Weeks 15-17)**
- Implement maintenance reminders (seasonal, equipment age alerts)
- Implement promotional notifications (limited-time offers, referrals)
- Build notification scheduling (send reminders 24 hours before appointment)
- Test promotional notification targeting

**Phase 6: Multi-Language & Polish (Weeks 18-20)**
- Add Spanish language support (translate all templates)
- Implement rich push notifications (images, action buttons)
- Performance testing (notification delivery latency, throughput)
- Bug fixes and UX refinements

**Phase 7: Launch (Week 21)**
- Duke approval for notification messaging
- Soft launch to pilot group (100 customers)
- Monitor metrics (delivery rate, open rate, opt-out rate)
- Full launch to all customers

### 6.2 Success Criteria for Launch

**Launch Readiness:**
- ✅ Push notification delivery rate >98%
- ✅ SMS delivery rate >98%
- ✅ Email delivery rate >98%
- ✅ Notification latency <5 sec (push), <30 sec (SMS), <5 min (email)
- ✅ Customer preferences working (opt-outs respected)
- ✅ Duke legal approval for all notification templates
- ✅ Pilot group feedback positive (>80% satisfaction)

---

## 7. SUCCESS METRICS & MEASUREMENT

### 7.1 Key Performance Indicators (KPIs)

**Delivery & Performance:**
- Push notification delivery rate: 98%+
- SMS delivery rate: 98%+
- Email delivery rate: 98%+
- Push notification latency: <5 seconds
- SMS latency: <30 seconds
- Email latency: <5 minutes

**Engagement:**
- Push notification open rate: 65%+
- SMS open rate: 25%+
- Email open rate: 35%+
- Click-through rate (CTR): 15%+

**Customer Satisfaction:**
- Communication satisfaction: 90%+
- "Notifications are helpful": 85%+ agree
- Opt-out rate: <5%

**Business Impact:**
- Call center call reduction: 30-40%
- No-show rate reduction: 60%
- Preventative maintenance bookings increase: 40%
- Promotional notification conversion: 15-20%
- App engagement (DAU): 3x increase

---

## 8. APPENDIX

### 8.1 Glossary

- **Push Notification**: Alert displayed on mobile device (iOS/Android)
- **FCM**: Firebase Cloud Messaging (Google's push notification service)
- **SMS**: Short Message Service (text messaging)
- **ESP**: Email Service Provider (SendGrid, AWS SES)
- **Deep Link**: Link that opens specific screen in app
- **Opt-Out**: Customer choosing not to receive notifications
- **Quiet Hours**: Time period when non-urgent notifications suppressed
- **Event-Driven Architecture**: System where events trigger actions (service booked → send notification)

---

END OF PRD #6: COMMUNICATION & NOTIFICATIONS
