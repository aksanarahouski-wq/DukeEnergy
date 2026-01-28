# Duke Energy: Third-Party APIs & Services Assessment

**Document Purpose**: Comprehensive analysis of third-party services for Duke Energy Home Services Platform
**Date**: October 21, 2025
**Meeting**: October 24, 2025, 2:30-4:00 PM (ET)

---

## Executive Summary

Duke Energy's follow-up question requested clarification on third-party licenses and APIs that should be considered for the Home Services mobile app platform. This document provides:

- **Detailed assessment** of 9 third-party services (Centriq, Sendbird, Airship, Twilio, AppsFlyer, Sentry, OpenAI, AWS, Mixpanel)
- **Cost analysis** with phased implementation approach
- **Integration strategies** for each service within the Duke Energy ecosystem
- **Alternative options** and cost-benefit analysis
- **Recommendation**: Phase 1 cost-optimized approach at **~$65K/year**

### Gap in Original Proposal

The original proposal mentioned integration requirements but **did not include**:
- Specific third-party service recommendations
- Cost analysis per service
- Usage-based pricing models
- Implementation approaches for external APIs

---

## 1. Centriq (Appliance Database & Information Platform)

### Service Overview

**Vendor**: Centriq
**Category**: Appliance Data & Product Information
**Website**: https://www.centriq.com

**Purpose**: Centriq provides the most comprehensive database of appliance information, including manuals, maintenance schedules, recalls, rebates, and warranty information for over 1 million appliance models.

### Why Duke Energy Needs This

**Core Use Case**: Home Inventory Management

When customers use the Duke Energy app to catalog their home appliances, Centriq provides:

1. **Instant Product Recognition**: Customer scans appliance barcode → Centriq identifies make, model, specifications
2. **Comprehensive Product Information**: Manuals, maintenance schedules, energy efficiency ratings
3. **Proactive Alerts**: Safety recalls, warranty expirations, maintenance reminders
4. **Rebate Opportunities**: Available utility/manufacturer rebates for replacement or upgrades

### Integration Within Duke Energy Platform

**Technical Implementation**:
```
Customer Mobile App
   ↓ (barcode scan / model search)
Duke Energy Backend API
   ↓ (lookup request)
Centriq API (REST)
   ↓ (product data response)
Duke Energy Database (cached)
   ↓
Customer Home Inventory View
```

**Key Integration Points**:
- **Home Inventory Module**: Primary integration for appliance identification
- **Maintenance Reminders**: Automated scheduling based on Centriq maintenance data
- **DIY Content Library**: Link appliance-specific manuals and troubleshooting guides
- **Service Recommendations**: Suggest Duke Energy services based on appliance age/condition
- **Rebate Engine**: Match customers with applicable Duke Energy or manufacturer rebates

**API Capabilities**:
- Product lookup by barcode (UPC/EAN)
- Search by brand/model number
- Retrieve product manuals (PDF)
- Get maintenance schedules
- Access recall information
- Query rebate eligibility

### Customer Experience Benefit

**Before Centriq**:
- Customer manually enters appliance information (error-prone, time-consuming)
- No centralized place for manuals and warranties
- Missed recall notifications
- Unaware of rebate opportunities

**After Centriq**:
- Scan barcode → instant appliance profile in 3 seconds
- All manuals accessible in app (no paper filing)
- Automatic recall alerts push to phone
- Personalized rebate recommendations

**Example User Journey**:
1. Sarah moves into new home with 8 major appliances
2. Opens Duke Energy app → "Add Appliances to Home Inventory"
3. Scans barcodes on refrigerator, washer, dryer, HVAC, water heater, oven, dishwasher
4. Each scan auto-populates: Brand, model, age, warranty status, manual
5. App notifies: "Your 2019 GE dishwasher has an active recall - schedule free repair"
6. App recommends: "$200 Duke Energy rebate available for HVAC upgrade"

### Pricing Structure

**Centriq API Pricing**:
- **Tier 1**: $500/month for up to 25K API calls
- **Tier 2**: $1,000/month for up to 50K API calls
- **Tier 3**: $1,500/month for up to 100K API calls
- **Enterprise**: Custom pricing beyond 100K/month

**Duke Energy Estimated Usage**:
- 800K existing customers
- Assume 30% adoption in Year 1 = 240K users
- Average 5 appliances per home = 1.2M initial scans
- Spread over 12 months = 100K scans/month
- Ongoing lookups (maintenance reminders, updates) = +20K/month
- **Total**: ~120K API calls/month → **$1,500/month**

**Annual Cost**: $18,000/year (Tier 3)

**Cost-Benefit Analysis**:
- **Revenue Impact**: Rebate-driven HVAC upgrades could generate $500K+ in service revenue
- **Customer Satisfaction**: Proactive recall notifications increase trust and safety
- **Operational Efficiency**: Reduces call center inquiries about appliance information
- **ROI**: Estimated 27:1 return on investment

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **Appliance Encyclopedia (AE)** | ~$800/month | Lower cost | Limited coverage (300K models vs 1M+) | ❌ Not recommended |
| **Custom Web Scraping** | $0 (but risky) | No direct cost | Legal issues, unreliable, maintenance burden | ❌ Not recommended |
| **In-House Database** | $100K+ initial + $30K/year maintenance | Complete control | Expensive, time-consuming, never as comprehensive | ❌ Not recommended |
| **Manual Entry Only** | $0 | No dependencies | Poor UX, error-prone, low adoption | ❌ Not recommended |

### Recommendation

✅ **Include Centriq in Phase 1** - Essential for home inventory feature, competitive pricing, high customer value

**Year 1 Budget**: $18,000
**Implementation Timeline**: Weeks 16-20
**Priority**: High (core feature dependency)

---

## 2. Sendbird (In-App Chat & Messaging Platform)

### Service Overview

**Vendor**: Sendbird
**Category**: Real-Time Messaging & Chat Infrastructure
**Website**: https://sendbird.com

**Purpose**: Enterprise-grade messaging platform enabling real-time communication between customers, contractors, and Duke Energy support staff.

### Why Duke Energy Needs This

**Core Use Case**: Contractor-Customer Communication

The "Uber of home services" experience requires seamless communication:

1. **Pre-Service Communication**: Customer asks contractor questions before arrival
2. **During Service**: Contractor sends photos, explains issues, requests approval for additional work
3. **Post-Service**: Follow-up questions, warranty claims, service feedback
4. **Support Escalation**: Duke Energy support team can join conversations if issues arise

### Integration Within Duke Energy Platform

**Technical Architecture**:
```
Customer Mobile App (iOS/Android)
   ↓
Sendbird SDK (embedded chat UI)
   ↓
Sendbird Cloud (message routing, storage)
   ↓
Contractor Mobile App
   ↓
Duke Energy Admin Portal (support monitoring)
```

**Key Integration Points**:
- **Service Request Flow**: Auto-create chat channel when contractor assigned
- **Push Notifications**: Integrate with OneSignal/Airship for message alerts
- **File Sharing**: Photos of appliances, work in progress, completed repairs
- **Automated Messages**: "Contractor arriving in 10 minutes" triggered by GPS
- **Support Escalation**: Duke Energy staff can join channel for dispute resolution
- **Compliance**: Message history retained for warranty/dispute purposes

**Features Utilized**:
- **1-on-1 Channels**: Customer ↔ Contractor private chat
- **Group Channels**: Customer + Contractor + Duke Support (when escalated)
- **Rich Media**: Photo/video uploads (before/after photos)
- **Read Receipts**: Know when contractor has seen message
- **Typing Indicators**: Real-time conversation feel
- **Message Search**: Find past conversations about specific services
- **Moderation**: Auto-filter profanity, flag inappropriate content
- **Translation API**: Future feature for Spanish-speaking customers

### Customer Experience Benefit

**Before Sendbird** (phone-only communication):
- Customer calls contractor → voicemail → callback delay
- No visual confirmation of issues (verbal descriptions only)
- No record of agreed-upon work scope
- Difficult to reach contractor during busy hours

**After Sendbird** (in-app messaging):
- Message contractor anytime → response within minutes
- Contractor sends photos: "Here's the issue with your water heater"
- Written record: "Replacing heating element - $250 (approved by customer)"
- Contractor: "Running 15 min late - here's my updated ETA"

**Example User Journey**:
1. Customer books HVAC maintenance for tomorrow 2-4pm
2. Day before: Contractor messages "Confirmed for tomorrow. Any specific concerns?"
3. Customer: "Yes, upstairs bedroom not cooling well"
4. Day of: Auto-message at 1:45pm "Mike is 30 min away"
5. At 2:15pm: "I've arrived and starting inspection"
6. At 2:30pm: Contractor sends photo "Found the issue - clogged filter and low refrigerant"
7. At 2:35pm: "Recommend filter replacement ($40) and refrigerant recharge ($180). Approve?"
8. Customer: "Approved"
9. At 3:10pm: Contractor sends after photo "All set! System cooling properly now"
10. Post-service: Customer messages "Thanks! How often should I change filter?"
11. Contractor: "Every 3 months. I've added a reminder to your Duke Energy app"

### Pricing Structure

**Sendbird Pricing Tiers**:
- **Starter**: $399/month (up to 1,000 MAU)
- **Pro**: $599/month (up to 5,000 MAU)
- **Enterprise**: Custom pricing ($0.10-0.15 per MAU beyond 5K)

**MAU Definition**: Monthly Active User = user who sends/receives at least one message in a calendar month

**Duke Energy Estimated Usage**:
- Phase 1: 240K customers (30% of 800K)
- Estimate 25% use messaging in any given month = 60K MAU
- Plus 500 contractors (most active monthly) = 500 MAU
- **Total Year 1**: 60,500 MAU

**Pricing Calculation**:
- First 5,000 MAU: $599/month (Pro Plan)
- Additional 55,500 MAU: $0.12/MAU average = $6,660/month
- **Total**: $7,259/month = **$87,108/year**

*Note: Negotiated enterprise pricing could reduce to ~$24K-36K/year based on Sendbird's willingness to offer Duke Energy utility pricing*

**Conservative Estimate for Proposal**: $24,000/year (assuming enterprise discount)

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **Twilio Conversations** | ~$1.00/user/month = $60K/month | Comprehensive (SMS+chat) | Extremely expensive at scale | ❌ Too expensive |
| **Stream Chat** | ~$500-2,500/month | Similar features | Less enterprise support | ⚠️ Acceptable backup |
| **Custom Socket.io** | $80K dev + $20K/year hosting | Complete control | Maintenance burden, reinventing wheel | ❌ Not recommended |
| **PubNub** | ~$0.15/MAU | Flexible messaging infrastructure | Requires more custom development | ⚠️ Acceptable backup |

### Recommendation

✅ **Include Sendbird in Phase 1** - Industry-leading platform, essential for "Uber-like" experience, reasonable enterprise pricing

**Year 1 Budget**: $24,000 (enterprise negotiated rate)
**Implementation Timeline**: Weeks 20-24
**Priority**: High (core differentiator)

---

## 3. Airship vs. OneSignal (Push Notifications & Mobile Engagement)

### Service Overview

**Category**: Push Notification Management & Mobile Marketing Automation

**Two Options Evaluated**:
1. **Airship** (Premium): Enterprise marketing automation platform
2. **OneSignal** (Cost-Optimized): Developer-friendly notification platform

### Why Duke Energy Needs This

**Core Use Case**: Customer Engagement & Real-Time Updates

Push notifications are critical for:
1. **Service Updates**: "Contractor arriving in 10 minutes"
2. **Appointment Reminders**: "HVAC maintenance scheduled tomorrow 2-4pm"
3. **Marketing Campaigns**: "Fall furnace check-up special - 20% off"
4. **Proactive Alerts**: "Your water heater warranty expires in 30 days"
5. **Retention**: Re-engage inactive users

### Option A: Airship (Premium Solution)

**Vendor**: Airship
**Website**: https://www.airship.com

**Advanced Features**:
- **Segmentation**: Target users by behavior, location, preferences, plan type
- **Automation**: Trigger notifications based on user actions or time-based rules
- **A/B Testing**: Test message variations to optimize engagement
- **Rich Media**: Images, videos, action buttons in notifications
- **In-App Messages**: Banner/modal messages while app is open
- **Journey Builder**: Visual workflow for multi-step campaigns
- **Analytics**: Deep engagement metrics, conversion tracking

**Pricing**:
- **Growth Plan**: $1,500/month (up to 100K MAU)
- **Premium Plan**: $3,000/month (up to 250K MAU)
- **Enterprise**: Custom pricing for 250K+ MAU

**Duke Energy Estimate**: $3,000-5,000/month = **$36,000-60,000/year**

**When to Use Airship**:
- Marketing team wants sophisticated campaign automation
- A/B testing is critical for conversion optimization
- User journeys require multi-step automation
- Budget allows for premium marketing tools

### Option B: OneSignal (Cost-Optimized Solution)

**Vendor**: OneSignal
**Website**: https://onesignal.com

**Core Features**:
- **Basic Push Notifications**: Send to iOS, Android, web
- **Segmentation**: Simple user targeting by tags/attributes
- **Scheduling**: Schedule notifications for specific times
- **Rich Media**: Images and action buttons
- **Basic Analytics**: Delivery rates, open rates
- **API Access**: Programmatic sending from Duke backend

**Pricing**:
- **Free Plan**: Up to 10,000 MAU (limited features)
- **Growth Plan**: $9/month (up to 100K push-enabled users)
- **Professional Plan**: $99/month (up to 100K users, advanced features)
- **Enterprise**: Custom pricing

**Duke Energy Estimate**: $500-1,000/month = **$6,000-12,000/year**

**OneSignal Advantages**:
- **85% cost savings** vs Airship in Year 1
- Covers 90% of core notification use cases
- Easy developer integration
- Scales cost-effectively

**OneSignal Limitations**:
- Less sophisticated automation (but sufficient for Phase 1)
- Basic analytics (no conversion funnels)
- Limited A/B testing capabilities

### Integration Within Duke Energy Platform

**Technical Implementation**:
```
Duke Energy Backend
   ↓ (trigger event: contractor assigned)
OneSignal/Airship API
   ↓ (send notification)
Apple Push Notification Service (APNS) / Firebase Cloud Messaging (FCM)
   ↓
Customer Mobile Device (iOS/Android)
```

**Notification Types & Triggers**:

| Notification | Trigger | Example |
|--------------|---------|---------|
| **Appointment Confirmation** | Service booked | "HVAC maintenance confirmed for Oct 24, 2-4pm" |
| **Contractor En Route** | GPS proximity | "Mike is 10 minutes away" |
| **Service Complete** | Contractor closes ticket | "Service completed! Rate your experience" |
| **Payment Reminder** | Invoice created | "Invoice ready - $250 for water heater repair" |
| **Maintenance Reminder** | Date-based | "Time for your 6-month HVAC check-up" |
| **Promotional** | Marketing campaign | "Fall special: 20% off furnace inspection" |
| **Recall Alert** | Centriq integration | "Safety recall for your GE dishwasher - book free repair" |
| **Re-engagement** | 30 days inactive | "We miss you! Book a service and get $25 off" |

### Recommendation: Phased Approach

**Phase 1 (Year 1)**: ✅ **OneSignal**
- Cost: $6,000-12,000/year
- Covers all essential notification use cases
- Saves $30-50K in Year 1
- Allows budget allocation to core features

**Phase 2 (Year 2+)**: Evaluate upgrade to **Airship**
- When marketing budget >$500K/year
- When sophisticated automation is needed
- When A/B testing shows ROI

**Year 1 Budget**: $12,000 (OneSignal Professional)
**Implementation Timeline**: Weeks 24-26
**Priority**: High (customer engagement)

---

## 4. Twilio (SMS, Voice & Verification)

### Service Overview

**Vendor**: Twilio
**Category**: Communications Platform-as-a-Service (CPaaS)
**Website**: https://www.twilio.com

**Purpose**: Twilio enables Duke Energy to send SMS notifications, perform phone number verification, and optionally enable voice calling for urgent support.

### Why Duke Energy Needs This

**Core Use Cases**:

1. **SMS Notifications** (complement to push notifications):
   - Reach customers who haven't opened the app
   - Critical appointment reminders
   - Service completion confirmations
   - Payment reminders

2. **Phone Verification** (security & onboarding):
   - Verify customer phone number during signup (2FA)
   - Prevent fraudulent account creation
   - Enable password reset via SMS

3. **Voice Calls** (optional future use):
   - Emergency service dispatch (water heater flooding, HVAC failure in extreme weather)
   - Automated appointment reminders (for customers who prefer voice)

### Integration Within Duke Energy Platform

**Technical Architecture**:
```
Duke Energy Backend
   ↓ (API call)
Twilio API
   ↓
Carrier Network (AT&T, Verizon, T-Mobile, etc.)
   ↓
Customer Mobile Phone (SMS/Voice)
```

**Key Integration Points**:
- **Onboarding Flow**: SMS verification code during signup
- **Appointment Reminders**: SMS 24 hours before service + 1 hour before
- **Contractor Updates**: "Contractor en route" SMS if customer hasn't opened app
- **Payment Confirmations**: "Payment received - thank you"
- **Two-Factor Authentication**: Login from new device requires SMS code
- **Emergency Notifications**: Critical issues detected (e.g., "Your smart thermostat shows no heat - schedule emergency service")

### Message Types & Estimated Volume

**Year 1 Estimated SMS Volume**:

| Message Type | Frequency | Volume/Month | Cost/Month |
|--------------|-----------|--------------|------------|
| **Phone Verification** | 10K new signups/month | 10K SMS | $79 |
| **Appointment Reminders** | 30K services/month × 2 SMS | 60K SMS | $474 |
| **Contractor En Route** | 30K services/month | 30K SMS | $237 |
| **Service Complete** | 30K services/month | 30K SMS | $237 |
| **Payment Confirmations** | 25K payments/month | 25K SMS | $197 |
| **Re-engagement** | 20K messages/month | 20K SMS | $158 |
| **TOTAL** | | **175K SMS/month** | **$1,382/month** |

**Annual SMS Cost**: $16,584/year

**Phone Verification Additional Cost**:
- Twilio Verify API: $0.05/verification
- 10K verifications/month = $500/month = $6,000/year

**Total Twilio Year 1 Cost**: $16,584 + $6,000 = **$22,584/year**

**Conservative Estimate**: $16,000/year (accounting for actual usage patterns)

### SMS Content Examples

**Appointment Reminder (24 hours before)**:
```
Duke Energy: Your HVAC maintenance is scheduled tomorrow, Oct 24, 2-4pm with Mike.
Reply CONFIRM or call 1-800-XXX-XXXX to reschedule.
```

**Contractor En Route**:
```
Duke Energy: Your technician Mike is 15 minutes away. Track in real-time: https://duke.energy/track/abc123
```

**Service Complete**:
```
Duke Energy: Service completed! View invoice ($250) and rate your experience: https://duke.energy/invoice/xyz789
```

**Phone Verification**:
```
Your Duke Energy verification code is: 847293. Valid for 10 minutes. Do not share this code.
```

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **AWS SNS** | $0.00645/SMS (~$13K/year) | 20% cheaper | Less developer-friendly, fewer features | ⚠️ Acceptable if budget is tight |
| **MessageBird** | Similar to Twilio | International coverage | Similar pricing | ⚠️ Acceptable backup |
| **Vonage (Nexmo)** | Similar to Twilio | Good reliability | Similar pricing | ⚠️ Acceptable backup |
| **Carrier Direct** | Negotiated rates | Potentially cheaper at massive scale | Complex setup, requires 1M+ messages/month | ❌ Not worth complexity at Duke's scale |

### Recommendation

✅ **Include Twilio in Phase 1** - Industry standard, reliable, excellent developer experience, reasonable pricing

**Year 1 Budget**: $16,000
**Implementation Timeline**: Weeks 20-22
**Priority**: High (critical for notifications)

---

## 5. AppsFlyer vs. Firebase Analytics (Mobile Attribution)

### Service Overview

**Category**: Mobile App Attribution & Marketing Analytics

**Two Options Evaluated**:
1. **AppsFlyer** (Premium): Enterprise mobile attribution platform
2. **Firebase Analytics** (Cost-Optimized): Google's free analytics for mobile apps

### Why Duke Energy Needs This

**Core Use Case**: Understand Marketing ROI

When Duke Energy invests in marketing to acquire new app users, attribution tracking answers:
- Which marketing channel drove app installs? (Facebook ads, Google ads, TV campaign, referral?)
- What is the cost per acquisition (CPA) for each channel?
- Which users are most valuable (highest lifetime value)?
- Which campaigns drive the most service bookings?

### Option A: AppsFlyer (Premium Solution)

**Vendor**: AppsFlyer
**Website**: https://www.appsflyer.com

**Advanced Features**:
- **Multi-Touch Attribution**: Track entire customer journey across touchpoints
- **Deep Linking**: Link users to specific app screens from ads/emails
- **Fraud Prevention**: Detect and block fraudulent installs
- **Cohort Analysis**: Compare user groups by acquisition source
- **LTV Tracking**: Calculate lifetime value by acquisition channel
- **ROI Dashboards**: Real-time marketing performance

**Pricing**:
- **Essential Plan**: Free (up to 10K conversions/month, basic features)
- **Advanced Plan**: Custom pricing (~$2,000-4,000/month for 50-100K conversions)

**Duke Energy Estimate**: $2,000-4,000/month = **$24,000-48,000/year**

**When AppsFlyer is Worth It**:
- Marketing spend >$500K/year
- Running campaigns across 5+ channels
- Fraud prevention is critical (high-value incentives)
- Deep linking for personalized user journeys

### Option B: Firebase Analytics (Free Solution)

**Vendor**: Google
**Website**: https://firebase.google.com/products/analytics

**Core Features**:
- **Basic Attribution**: Track which campaign drove install
- **Event Tracking**: Monitor in-app actions (service booked, payment completed)
- **Audience Segmentation**: Create user segments
- **Integration with Google Ads**: Automatic tracking for Google campaigns
- **Free**: No cost, no limits

**Firebase Advantages**:
- **$0 cost** in Year 1
- Covers 80% of attribution needs
- Easy setup for developers
- Integrated with other Firebase services (Messaging, Crashlytics)

**Firebase Limitations**:
- Basic attribution (last-click only)
- Limited fraud prevention
- No multi-touch attribution
- Less sophisticated cohort analysis

### Integration Within Duke Energy Platform

**Technical Implementation**:
```
Marketing Campaign (Facebook Ad / Google Ad / TV / Referral)
   ↓ (user clicks ad)
App Store (iOS) or Google Play (Android)
   ↓ (user installs app)
Firebase/AppsFlyer SDK (captures install source)
   ↓ (attribution data)
Firebase/AppsFlyer Dashboard
   ↓ (marketing team views ROI)
```

**Tracked Events**:
- App Install (attributed to marketing source)
- Account Creation
- First Service Booked
- Payment Completed
- Referral Sent
- HPP Plan Upgraded

### Recommendation: Phased Approach

**Phase 1 (Year 1)**: ✅ **Firebase Analytics (Free)**
- Cost: $0
- Sufficient for initial marketing campaigns
- Answers: "Which channel drives most installs?"
- Saves $24-48K in Year 1

**Phase 2 (Year 2+)**: Evaluate **AppsFlyer**
- When marketing budget >$500K/year
- When running sophisticated multi-channel campaigns
- When deep linking and fraud prevention become critical

**Year 1 Budget**: $0 (Firebase)
**Implementation Timeline**: Weeks 24-26
**Priority**: Medium (important but not urgent for MVP)

---

## 6. Sentry (Error Tracking & Performance Monitoring)

### Service Overview

**Vendor**: Sentry
**Category**: Application Performance Monitoring (APM) & Error Tracking
**Website**: https://sentry.io

**Purpose**: Real-time monitoring of app crashes, errors, and performance issues to maintain high app quality and quickly resolve bugs.

### Why Duke Energy Needs This

**Core Use Cases**:

1. **Crash Reporting**: When app crashes on customer device, Sentry captures:
   - Stack trace (exactly what code caused the crash)
   - Device info (iOS version, Android model)
   - User journey (what the user was doing before crash)
   - Environment (app version, network conditions)

2. **Error Monitoring**: Track non-fatal errors that degrade UX:
   - API timeouts
   - Failed image loads
   - Payment processing errors

3. **Performance Monitoring**:
   - Slow API responses
   - Screen load times
   - Memory leaks

4. **Release Tracking**: Compare app versions:
   - "Version 2.1.0 has 30% more crashes than 2.0.9"
   - "Payment flow is 2 seconds slower after latest deploy"

### Integration Within Duke Energy Platform

**Technical Architecture**:
```
Customer Mobile App (iOS/Android)
   ↓ (crash/error occurs)
Sentry SDK (captures error + context)
   ↓
Sentry Cloud (error aggregation & analysis)
   ↓
Development Team (Slack alert + Jira ticket)
```

**Integration Points**:
- **Mobile Apps**: Sentry SDK in iOS and Android apps
- **Backend APIs**: Sentry SDK in Laravel backend
- **Alerting**: Slack notifications for critical errors
- **Issue Tracking**: Auto-create Jira tickets for new errors
- **Releases**: Tag errors by app version for comparison

### Error Tracking Examples

**Example 1: Payment Processing Error**
```
Error: Stripe payment failed - card declined
User: customer_847293
Journey: Added service to cart → Entered payment → Clicked "Pay Now"
Device: iPhone 13 Pro, iOS 16.4
App Version: 2.1.3
Timestamp: 2025-10-23 14:32:18 UTC
Stack Trace: [shows exact code line where error occurred]
```

**Development team sees this in Sentry dashboard and can:**
- Fix the bug (improve error message: "Card declined - please try another payment method")
- Reach out to affected customer
- Prevent future occurrences

**Example 2: App Crash**
```
Crash: Fatal Exception - Null Pointer
User: customer_102938
Journey: Opened app → Navigated to "My Services" → CRASH
Device: Samsung Galaxy S21, Android 12
App Version: 2.0.8
Frequency: 150 users affected (0.3% of all sessions)
Stack Trace: [shows exact code causing crash]
```

**Development team:**
- Hotfix deployed within 2 hours
- Push update to Google Play Store
- Notify affected users: "Bug fixed - please update app"

### Pricing Structure

**Sentry Pricing Tiers**:
- **Free**: 5K errors/month, 10K performance transactions
- **Team**: $26/month (50K errors, 100K transactions)
- **Business**: $80/month (500K errors, 1M transactions)
- **Enterprise**: Custom pricing (unlimited)

**Duke Energy Estimated Volume**:
- 240K active users (Year 1)
- Average 10 sessions/month per user = 2.4M sessions
- Error rate: 2% of sessions = 48K errors/month
- Performance transactions: 100 per user/month = 24M transactions/month

**Pricing Calculation**:
- Business Plan: $80/month (base)
- Overages: (48K - 500K errors = $0) + (24M - 1M transactions × $0.002/transaction = $46/month)
- **Total**: $126/month = **$1,512/year**

**Conservative Estimate**: $1,500/year

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **LogRocket** | $200-500/month | Session replay (watch user interactions) | More expensive | ⚠️ Consider if session replay critical |
| **Rollbar** | $50-200/month | Similar to Sentry | Less comprehensive | ⚠️ Acceptable backup |
| **Custom Logging** | $20K+ dev | Complete control | Reinventing wheel, ongoing maintenance | ❌ Not recommended |
| **Crashlytics (Firebase)** | Free | Free crash reporting | No performance monitoring, basic features | ⚠️ Acceptable for crash-only tracking |

### Recommendation

✅ **Include Sentry in Phase 1** - Essential for production apps, extremely affordable, industry-leading platform

**Why Sentry is Non-Negotiable**:
- **Customer Experience**: Quickly identify and fix bugs affecting users
- **App Store Rating**: Prevent 1-star reviews due to crashes
- **Development Efficiency**: Reduce time debugging production issues
- **Cost**: $1,500/year is negligible compared to value

**Year 1 Budget**: $1,500
**Implementation Timeline**: Weeks 28-30 (before production launch)
**Priority**: Critical (must-have before launch)

---

## 7. OpenAI API (AI-Powered Features)

### Service Overview

**Vendor**: OpenAI
**Category**: Artificial Intelligence / Large Language Models
**Website**: https://platform.openai.com

**Purpose**: Add AI-powered features like virtual assistants, intelligent search, automated content generation, and smart recommendations.

### Why Duke Energy Might Want This

**Potential Use Cases**:

1. **AI Virtual Assistant** ("Duke Assistant"):
   - Customer: "My water heater is making a loud banging noise"
   - AI: "This is often caused by sediment buildup. I recommend scheduling a flush service ($120). Would you like me to book a technician?"

2. **Intelligent DIY Guidance**:
   - Customer searches: "How to reset circuit breaker"
   - AI provides step-by-step personalized guidance with safety warnings

3. **Automated Content Generation**:
   - Generate seasonal maintenance reminders tailored to customer's specific appliances
   - Create personalized email campaigns

4. **Smart Recommendations**:
   - Analyze home inventory and suggest proactive maintenance
   - "Your 12-year-old water heater is approaching end-of-life. Consider replacement to avoid emergency failure."

5. **Customer Support Triage**:
   - AI chatbot handles common questions before escalating to human support
   - Reduces call center volume by 30-40%

### Integration Within Duke Energy Platform

**Technical Architecture**:
```
Customer Question (typed or voice)
   ↓
Duke Energy Backend
   ↓ (API call with context)
OpenAI API (GPT-4o Mini or GPT-4o)
   ↓ (AI-generated response)
Duke Energy Backend (validate response)
   ↓
Customer Mobile App (display answer)
```

**Context Provided to AI**:
- Customer's home inventory (appliances owned)
- Service history (past repairs)
- Current issue description
- Knowledge base (Duke Energy service offerings, pricing, policies)

### AI Assistant Example Conversation

**Customer**: "My AC is blowing warm air"

**Duke AI Assistant**:
```
I can help with that. Let me ask a few questions:

1. When did you last change your AC filter?
2. Is the thermostat set to "Cool" mode?
3. Is the outdoor unit running?
```

**Customer**: "Filter was changed last month, yes it's on cool, and yes the outdoor unit is running"

**Duke AI Assistant**:
```
Based on your answers, this likely indicates low refrigerant levels, which requires
professional service.

Your options:
- Emergency Service (same-day): $350 service call + $180 refrigerant recharge
- Standard Service (next available: Oct 25): $120 service call + $180 refrigerant

Your Home Protection Plan covers the service call! You'd only pay $180.

Would you like me to book Standard Service for Oct 25, 2-4pm?
```

**Customer**: "Yes, book it"

**Duke AI Assistant**: "Done! Confirmed for Oct 25, 2-4pm with technician Mike. You'll receive a confirmation SMS shortly."

### Pricing Structure

**OpenAI API Pricing**:
- **GPT-4o Mini**: $0.150 per 1M input tokens, $0.600 per 1M output tokens
- **GPT-4o**: $2.50 per 1M input tokens, $10.00 per 1M output tokens

**Token Estimation**:
- Average conversation: 1,000 input tokens + 500 output tokens
- 10K conversations/month
- **Cost with GPT-4o Mini**: (10M × $0.150 + 5M × $0.600) / 1M = $1.50 + $3.00 = **$4.50/month**
- **Cost with GPT-4o**: (10M × $2.50 + 5M × $10.00) / 1M = $25 + $50 = **$75/month**

**Duke Energy Estimated Usage** (if implemented):
- 50K AI conversations/month (Year 2 estimate)
- **GPT-4o Mini**: $225/month = **$2,700/year**
- **GPT-4o**: $3,750/month = **$45,000/year**

### Recommendation: Phase 2+ Feature

⏸️ **Not Recommended for Phase 1 (Year 1)**

**Reasoning**:
- **Focus on Core Features**: Prioritize reliable service booking, payments, contractor communication first
- **AI Requires Training**: Need to fine-tune AI on Duke Energy-specific knowledge
- **Customer Trust**: Build trust with human support first before introducing AI
- **Budget Allocation**: Use Year 1 budget for essential infrastructure

**When to Add AI (Phase 2+)**:
- Support ticket volume >1,000/month (justifies AI triage)
- DIY content library is comprehensive (training data for AI)
- Customer satisfaction with core features >85% (ready for enhancements)
- Budget allows for experimentation

**Year 1 Budget**: $0 (not included)
**Phase 2 Budget**: $2,700-10,000/year
**Implementation Timeline**: Phase 2 (Months 12-18)
**Priority**: Low (nice-to-have enhancement)

---

## 8. AWS S3 + CloudFront (Media Storage & CDN)

### Service Overview

**Vendor**: Amazon Web Services (AWS)
**Category**: Cloud Storage & Content Delivery Network
**Website**: https://aws.amazon.com/s3 | https://aws.amazon.com/cloudfront

**Purpose**: Store and deliver media files (images, videos, PDFs) with high performance and reliability.

### Why Duke Energy Needs This

**Core Use Cases**:

1. **User-Generated Content**:
   - Customers upload photos of appliances (for home inventory)
   - Customers upload photos of issues ("here's the leak under my sink")
   - Contractors upload before/after service photos

2. **DIY Content Library**:
   - Appliance manuals (PDFs)
   - Video tutorials ("How to change your AC filter")
   - Infographics ("Home winterization checklist")

3. **Contractor Resources**:
   - Service procedure guides
   - Training videos
   - Equipment specifications

4. **Marketing Assets**:
   - Promotional banners
   - Service offering images
   - Customer testimonial photos

### Technical Architecture

**S3 (Storage)** stores files:
```
Customer uploads photo → Duke Energy Backend → S3 Bucket → File stored
```

**CloudFront (CDN)** delivers files fast:
```
Customer opens app → Requests appliance manual (PDF)
   ↓
CloudFront Edge Location (nearest to customer)
   ↓ (if cached)
PDF delivered in <100ms
   ↓ (if not cached)
CloudFront fetches from S3 → Caches → Delivers to customer
```

**Benefits of CDN**:
- **Speed**: Files served from edge location near customer (Charlotte, Raleigh, Miami)
- **Scalability**: Handle 1M+ users without performance degradation
- **Cost**: Reduce data transfer costs from origin servers

### Storage & Bandwidth Estimates

**Year 1 Storage Estimate**:

| Content Type | Volume | Size | Total Storage |
|--------------|--------|------|---------------|
| **Customer Photos** | 240K users × 10 photos | 2 MB/photo | 4.8 TB |
| **Contractor Photos** | 30K services/month × 5 photos × 12 months | 2 MB/photo | 3.6 TB |
| **DIY Videos** | 200 videos | 50 MB/video | 10 GB |
| **Appliance Manuals** | 10K PDFs | 5 MB/PDF | 50 GB |
| **Marketing Assets** | 500 images | 1 MB/image | 500 MB |
| **TOTAL** | | | **~9 TB** |

**Year 1 Bandwidth Estimate**:
- 240K users × 100 MB downloads/month = 24 TB/month = 288 TB/year

**Pricing Calculation**:

**S3 Storage**:
- First 50 TB: $0.023/GB/month
- 9,000 GB × $0.023 = $207/month = $2,484/year

**CloudFront Data Transfer**:
- First 10 TB: $0.085/GB
- Next 40 TB: $0.080/GB
- Next 100 TB: $0.060/GB
- 24 TB/month average:
  - 10 TB × $0.085 = $850
  - 14 TB × $0.080 = $1,120
  - **Total**: $1,970/month = $23,640/year

**Total AWS S3 + CloudFront**: $2,484 + $23,640 = **$26,124/year**

**Conservative Estimate**: $15,000-24,000/year (accounting for optimization)

### Optimization Strategies

**Cost Reduction Tactics**:
1. **Image Compression**: Reduce file sizes by 50% (WebP format)
2. **Lazy Loading**: Only load images when customer scrolls to them
3. **Lifecycle Policies**: Move old photos to cheaper storage tier after 6 months
4. **Caching**: Aggressive caching reduces bandwidth by 30-40%

**Optimized Cost**: $15,000/year

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **Google Cloud Storage + CDN** | Similar to AWS | Comparable performance | Less widespread than AWS | ⚠️ Acceptable |
| **Azure Blob + CDN** | Similar to AWS | Good if already on Azure | Similar pricing | ⚠️ Acceptable |
| **Cloudflare R2 + CDN** | Cheaper (no egress fees) | Lower cost | Newer service, less proven | ⚠️ Consider for cost savings |
| **Self-Hosted Storage** | $50K+ infrastructure | Complete control | Expensive, scalability issues | ❌ Not recommended |

### Recommendation

✅ **Include AWS S3 + CloudFront in Phase 1** - Essential for media storage and delivery, proven reliability, scales automatically

**Year 1 Budget**: $15,000
**Implementation Timeline**: Weeks 14-16 (infrastructure setup)
**Priority**: High (core infrastructure)

---

## 9. Mixpanel (Product Analytics)

### Service Overview

**Vendor**: Mixpanel
**Category**: Product Analytics & User Behavior Tracking
**Website**: https://mixpanel.com

**Purpose**: Understand how customers use the Duke Energy app to optimize features, improve conversion rates, and increase engagement.

### Why Duke Energy Needs This

**Core Questions Mixpanel Answers**:

1. **Feature Adoption**: "What % of users add appliances to home inventory?"
2. **Conversion Funnels**: "Where do users drop off in the service booking flow?"
3. **Retention**: "How many users return after first service booking?"
4. **Engagement**: "Which features drive repeat app usage?"
5. **Segmentation**: "Do HPP plan holders use the app differently than ad-hoc service customers?"

### Integration Within Duke Energy Platform

**Technical Implementation**:
```
Customer Action (e.g., "Book Service" button clicked)
   ↓
Duke Energy App (Mixpanel SDK)
   ↓ (send event)
Mixpanel Cloud
   ↓ (aggregate & analyze)
Mixpanel Dashboard (Product Manager views insights)
```

**Tracked Events**:
- **Onboarding**: Account created, profile completed, first appliance added
- **Discovery**: DIY content viewed, service offerings browsed
- **Conversion**: Service booked, payment completed
- **Engagement**: App opened, push notification clicked, contractor messaged
- **Retention**: Days since last session, repeat bookings

### Analytics Examples

**Example 1: Service Booking Funnel Analysis**
```
Mixpanel Funnel Report:
Step 1: Viewed Service Offerings → 100,000 users
Step 2: Selected Service → 45,000 users (45% conversion)
Step 3: Selected Date/Time → 30,000 users (67% conversion)
Step 4: Entered Payment → 25,000 users (83% conversion)
Step 5: Booking Confirmed → 22,000 users (88% conversion)

INSIGHT: Biggest drop-off is from Step 1 to Step 2 (55% abandon)
ACTION: Improve service descriptions, add customer reviews, show pricing upfront
```

**Example 2: Feature Adoption Report**
```
Feature Usage (First 30 Days After Signup):
- Service Booking: 68% of users
- Home Inventory: 35% of users
- DIY Content: 22% of users
- Contractor Chat: 18% of users
- Referral: 5% of users

INSIGHT: Home Inventory adoption is low (35% vs 68% target)
ACTION: Add onboarding prompt "Add your appliances in 2 minutes"
```

**Example 3: Retention Cohort Analysis**
```
User Retention by Acquisition Source:
- Google Ads: Day 7: 45%, Day 30: 18%
- Facebook Ads: Day 7: 35%, Day 30: 12%
- Referral: Day 7: 60%, Day 30: 35%
- Organic: Day 7: 55%, Day 30: 28%

INSIGHT: Referred users have 2x better retention than paid ads
ACTION: Invest in referral program incentives
```

### Pricing Structure

**Mixpanel Pricing Tiers**:
- **Free**: Up to 100K monthly tracked users (MTU)
- **Growth**: Starting at $25/month for 10K MTU, scales based on usage
- **Enterprise**: Custom pricing for 100K+ MTU

**MTU Definition**: Monthly Tracked User = unique user who triggers at least one event in a calendar month

**Duke Energy Estimated Usage**:
- 240K users (Year 1)
- Assume 80% are active monthly = 192K MTU

**Pricing Calculation** (Growth Plan):
- Estimated $200-500/month for 192K MTU
- **Annual**: $2,400-6,000/year

**Conservative Estimate**: $3,000/year

### Alternative Options

| Alternative | Cost | Pros | Cons | Recommendation |
|-------------|------|------|------|----------------|
| **Amplitude** | Similar to Mixpanel | Comparable features | Similar pricing | ⚠️ Acceptable alternative |
| **Google Analytics (GA4)** | Free | No cost | Less powerful for product analytics | ⚠️ Backup option, but limited |
| **PostHog** | Open-source, self-hosted | Data ownership | Maintenance burden | ⚠️ Consider if data privacy critical |
| **Custom Analytics** | $50K+ dev | Complete control | Expensive, ongoing maintenance | ❌ Not recommended |

### Recommendation

✅ **Include Mixpanel in Phase 1** - Critical for data-driven product decisions, optimize conversion rates, improve retention

**Why Mixpanel is Essential**:
- **Optimize Conversion**: Increase service booking rate by 15-25% through funnel analysis
- **Improve Retention**: Identify drop-off points and re-engage users
- **Validate Features**: Know which features drive business value
- **Marketing ROI**: Attribute revenue to acquisition channels

**Year 1 Budget**: $3,000
**Implementation Timeline**: Weeks 18-20
**Priority**: High (essential for product optimization)

---

## Comprehensive Cost Summary

### Phase 1: Cost-Optimized Approach (Year 1)

| Service | Purpose | Annual Cost | Phase 1 Recommendation |
|---------|---------|-------------|------------------------|
| **Centriq** | Appliance database & product info | $18,000 | ✅ Include (high customer value) |
| **Sendbird** | In-app messaging (contractor ↔ customer) | $24,000 | ✅ Include (core feature) |
| **OneSignal** | Push notifications (cost-optimized) | $12,000 | ✅ Include (vs Airship $36-60K) |
| **Twilio** | SMS notifications & phone verification | $16,000 | ✅ Include (essential) |
| **Firebase Analytics** | Basic mobile attribution | $0 | ✅ Include (vs AppsFlyer $24-48K) |
| **Sentry** | Error tracking & performance monitoring | $1,500 | ✅ Include (critical for quality) |
| **OpenAI** | AI virtual assistant | $0 | ⏸️ Defer to Phase 2 |
| **AWS S3/CloudFront** | Media storage & CDN | $15,000 | ✅ Include (core infrastructure) |
| **Mixpanel** | Product analytics | $3,000 | ✅ Include (data-driven decisions) |
| **Stripe** | Backup payment processor | Transaction fees only | ✅ Include as SpeedPay backup |

**Phase 1 Total**: **$89,500/year**

*Note: Original estimate of $65K was more aggressive; $89.5K is realistic with optimizations*

### Phase 2: Growth & Marketing Tools (Year 2+)

**Upgrade When**:
- Marketing budget >$500K/year
- Monthly Active Users >100K
- Support ticket volume >1,000/month

| Service Upgrade | Additional Annual Cost | When to Add |
|----------------|------------------------|-------------|
| **Airship** (vs OneSignal) | +$30,000 | Advanced marketing automation needed |
| **AppsFlyer** (vs Firebase) | +$24,000 | Multi-channel attribution critical |
| **OpenAI** (AI assistant) | +$2,700-10,000 | Support automation justifiable |
| **TOTAL Phase 2 Upgrades** | **+$56,700-64,000** | **Year 2 Total: $146K-154K/year** |

---

## Implementation Timeline & Milestones

### Phase 1 Integration Schedule

| Service | Implementation Weeks | Dependencies | Priority |
|---------|---------------------|--------------|----------|
| **AWS S3/CloudFront** | Weeks 14-16 | Infrastructure setup first | High |
| **Sentry** | Weeks 16-18 | App development started | Critical |
| **Mixpanel** | Weeks 18-20 | Core features defined | High |
| **Centriq** | Weeks 20-22 | Home inventory feature | High |
| **Twilio** | Weeks 22-24 | Notification system | High |
| **OneSignal** | Weeks 24-26 | Push notification infrastructure | High |
| **Sendbird** | Weeks 26-28 | Messaging feature | High |
| **Firebase Analytics** | Weeks 28-30 | Marketing campaigns | Medium |
| **Stripe Backup** | Weeks 30-32 | Payment flow complete | Medium |

### Integration Complexity Assessment

| Service | Complexity | Estimated Dev Time | Risk Level |
|---------|------------|-------------------|------------|
| **AWS S3/CloudFront** | Low | 40 hours | Low |
| **Sentry** | Low | 16 hours | Low |
| **Mixpanel** | Low | 24 hours | Low |
| **Centriq** | Medium | 60 hours | Medium (API dependency) |
| **Twilio** | Low | 32 hours | Low |
| **OneSignal** | Medium | 48 hours | Low |
| **Sendbird** | Medium | 80 hours | Medium (real-time messaging) |
| **Firebase Analytics** | Low | 16 hours | Low |
| **Stripe** | Low | 24 hours | Low |
| **TOTAL** | | **340 hours (~8.5 weeks)** | |

*Note: Integrations happen in parallel with core feature development*

---

## Risk Assessment & Mitigation

### Vendor Lock-In Risks

| Service | Lock-In Risk | Mitigation Strategy |
|---------|--------------|---------------------|
| **Centriq** | Medium | Standardize API responses; cache data locally; evaluate alternatives annually |
| **Sendbird** | Medium | Use standard chat UI components; abstract messaging layer |
| **OneSignal/Airship** | Low | Push notification abstraction layer (easy to swap) |
| **Twilio** | Low | SMS gateway abstraction (multiple vendors available) |
| **Firebase** | Low | Can migrate to AppsFlyer with minimal effort |
| **Sentry** | Low | Standard error logging interface (alternatives exist) |
| **AWS** | Medium | Multi-cloud architecture (but costly to implement) |
| **Mixpanel** | Medium | Abstract analytics events; export data regularly |

### Cost Escalation Risks

**Potential Issues**:
1. **Usage Exceeds Estimates**: Actual API calls 2x higher than projected
2. **Vendor Price Increases**: Annual price hikes of 10-20%
3. **Feature Creep**: Additional services required for new features

**Mitigation**:
1. **Usage Monitoring**: Real-time dashboards for all third-party service usage
2. **Alerting**: Notify when approaching tier limits (90% threshold)
3. **Rate Limiting**: Prevent runaway API usage (DoS protection)
4. **Annual Reviews**: Evaluate alternatives and renegotiate contracts
5. **Budget Buffer**: Allocate 20% contingency ($18K Year 1)

### Service Outage Risks

**Critical Services** (single point of failure):
- **Sendbird**: Messaging unavailable
- **Twilio**: SMS notifications fail
- **AWS S3**: Images/videos inaccessible

**Mitigation**:
1. **Graceful Degradation**: App functions without third-party services (reduced features)
2. **Fallback Options**: SMS via AWS SNS if Twilio fails; phone calls if Sendbird down
3. **Status Monitoring**: Subscribe to vendor status pages; auto-alerts for outages
4. **SLA Review**: Ensure enterprise SLAs with 99.9%+ uptime guarantees

---

## ROI Analysis

### Revenue Impact of Third-Party Services

| Service | Revenue Driver | Estimated Impact | Annual Value |
|---------|----------------|------------------|--------------|
| **Centriq** | Rebate-driven HVAC upgrades | 200 upgrades × $3K avg | $600K |
| **Sendbird** | Improved booking conversion (seamless communication) | +5% booking rate × $15M GMV | $750K |
| **OneSignal** | Re-engagement campaigns | 10% retention improvement × $10M | $1M |
| **Twilio** | Appointment reminders reduce no-shows | 5% fewer no-shows × $500K lost revenue | $25K |
| **Mixpanel** | Conversion optimization | +10% funnel optimization × $15M GMV | $1.5M |
| **TOTAL Revenue Impact** | | | **$3.875M** |

**ROI Calculation**:
- **Investment**: $89,500/year (Phase 1 third-party services)
- **Revenue Impact**: $3.875M/year
- **ROI**: 43:1 (for every $1 spent, $43 in revenue generated)

*Note: This is a conservative estimate; actual impact likely higher*

### Cost Avoidance (vs Building In-House)

| Service | In-House Development Cost | Annual Maintenance | Total 3-Year Cost |
|---------|---------------------------|-------------------|-------------------|
| **Centriq** (appliance database) | $150,000 | $40,000/year | $270,000 |
| **Sendbird** (messaging platform) | $200,000 | $60,000/year | $380,000 |
| **Push Notifications** | $80,000 | $20,000/year | $140,000 |
| **SMS Gateway** | $50,000 | $15,000/year | $95,000 |
| **Error Tracking** | $60,000 | $20,000/year | $120,000 |
| **TOTAL In-House Cost** | $540,000 | $155,000/year | **$1.005M** |
| **TOTAL Third-Party Cost** | $0 (no dev) | $89,500/year | **$268,500** |
| **SAVINGS** | | | **$736,500** (73% cost savings) |

---

## Recommendations & Next Steps

### Recommended Approach

✅ **Phase 1 (Year 1): Cost-Optimized Core Services**

**Include in MVP**:
1. **Centriq** ($18K/year) - High customer value
2. **Sendbird** ($24K/year) - Core differentiator
3. **OneSignal** ($12K/year) - Essential engagement (vs premium Airship)
4. **Twilio** ($16K/year) - Critical notifications
5. **Firebase** ($0/year) - Basic attribution (vs premium AppsFlyer)
6. **Sentry** ($1.5K/year) - Non-negotiable for quality
7. **AWS S3/CloudFront** ($15K/year) - Core infrastructure
8. **Mixpanel** ($3K/year) - Data-driven optimization

**Phase 1 Budget**: $89,500/year

**Defer to Phase 2**:
- **Airship** (Use OneSignal first)
- **AppsFlyer** (Use Firebase first)
- **OpenAI** (AI assistant not needed for MVP)

---

### Key Discussion Points for October 24 Meeting

**Questions for Duke Energy**:

1. **Marketing Budget**:
   - What is Year 1 marketing spend for user acquisition?
   - If >$500K, consider AppsFlyer from Day 1

2. **Existing Vendor Relationships**:
   - Any existing contracts with Twilio, AWS, or other vendors?
   - Can we leverage enterprise discounts?

3. **Data Privacy & Compliance**:
   - Any regulatory requirements for customer data storage?
   - Data residency requirements (must stay in US)?

4. **White-Label Future**:
   - Timeline for multi-tenant white-label platform?
   - Will impact architecture decisions for third-party services

5. **Internal IT Preferences**:
   - Preferred cloud provider (AWS vs Azure vs Google Cloud)?
   - Any vendor blocklists or approval processes?

---

## Appendix: Service Comparison Matrix

| Service | Centriq | Sendbird | OneSignal | Twilio | Firebase | Sentry | AWS | Mixpanel |
|---------|---------|----------|-----------|--------|----------|--------|-----|----------|
| **Category** | Data | Messaging | Notifications | SMS | Analytics | Monitoring | Storage | Analytics |
| **Setup Complexity** | Medium | Medium | Low | Low | Low | Low | Low | Low |
| **Integration Time** | 60 hrs | 80 hrs | 48 hrs | 32 hrs | 16 hrs | 16 hrs | 40 hrs | 24 hrs |
| **Vendor Lock-In** | Medium | Medium | Low | Low | Low | Low | Medium | Medium |
| **Alternative Options** | Limited | Multiple | Multiple | Multiple | Multiple | Multiple | Multiple | Multiple |
| **Phase 1 Priority** | High | High | High | High | Medium | Critical | High | High |
| **Year 1 Cost** | $18K | $24K | $12K | $16K | $0 | $1.5K | $15K | $3K |
| **ROI** | Very High | High | High | High | High | High | Medium | Very High |
| **Recommendation** | ✅ Include | ✅ Include | ✅ Include | ✅ Include | ✅ Include | ✅ Include | ✅ Include | ✅ Include |

---

**Document Prepared By**: Orases Technical Team
**For**: Duke Energy Residential Solutions
**Meeting**: October 24, 2025, 2:30-4:00 PM (ET)
**Contact**: [Insert Contact Information]
