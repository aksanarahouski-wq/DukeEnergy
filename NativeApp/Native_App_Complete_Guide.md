# Native App Development: Complete Guide
### What You Need to Know as Product Manager
### Duke Energy RS Home Services App — React Native + Laravel + AWS

---

## Table of Contents

1. [How a Native App Actually Works](#1-how-a-native-app-actually-works)
2. [Architecture of This Specific App](#2-architecture-of-this-specific-app)
3. [The Tool Ecosystem — What Each Tool Does](#3-the-tool-ecosystem)
4. [Building the App — Phase by Phase](#4-building-the-app)
5. [Testing — What Gets Tested and How](#5-testing)
6. [Deployment — Getting the App to Users](#6-deployment)
7. [Monitoring and Support — After Launch](#7-monitoring-and-support)
8. [Version Upgrades and Ongoing Releases](#8-version-upgrades)
9. [Pitfalls to Avoid](#9-pitfalls-to-avoid)
10. [Dos and Don'ts](#10-dos-and-donts)
11. [Glossary](#11-glossary)

---

## 1. How a Native App Actually Works

### The Basics

A native app is software installed directly on a phone. When a user opens the Duke Home Services app, here's what's actually happening:

```
User taps app icon
    → App launches on the phone (React Native code runs locally)
    → App calls our backend server (Laravel API on AWS)
    → Server talks to Duke's systems (Commerce, Dynamics)
    → Data flows back: Server → App → User sees their HPP plans, service history, etc.
```

The app is NOT a website in a wrapper. It runs compiled code on the device, has access to the phone's hardware (camera, push notifications, storage), and can work partially offline.

### What "React Native" Means

React Native is a framework created by Meta (Facebook). It lets you write one codebase in JavaScript/TypeScript that compiles into both an iOS app and an Android app. This is important because:

- **One team writes code once** — not two separate teams for iOS and Android
- **The output is a real native app** — not a web page, not a hybrid. It compiles to actual native components
- **It shares ~85-90% of code between platforms** — some platform-specific code is still needed (maybe 10-15%)
- **Used by major companies** — Meta, Microsoft, Shopify, Discord, Bloomberg

What React Native is NOT:
- It is not the same as React (which is for websites). Same language, different target
- It is not Cordova/PhoneGap (those are web pages in a shell). React Native renders actual native UI components
- It does not produce identical pixel-for-pixel apps on both platforms — iOS and Android have different design patterns, and the app should respect them

### What the User's Phone Does vs. What the Server Does

| Responsibility | Phone (React Native) | Server (Laravel on AWS) |
|---|---|---|
| Show the UI | Yes | No |
| Store user session/login | Yes (secure storage) | Yes (auth tokens) |
| Call Duke's Commerce/Dynamics APIs | No — never directly | Yes — all external calls go through our server |
| Cache data for offline use | Yes (local storage) | No |
| Send push notifications | Receives them | Triggers them |
| Process business logic (coverage checks, contractor matching) | No | Yes |
| Store customer data permanently | No | Yes (PostgreSQL database) |

**Key concept:** The phone is a "thin client." It displays information and collects input. All real logic, data storage, and external integrations happen on the server. The phone never talks directly to Duke's systems — everything goes through our Laravel API.

---

## 2. Architecture of This Specific App

### The Full Stack Diagram

```
┌─────────────────────────────────────────────────────────────────────┐
│                        USER DEVICES                                  │
│                                                                      │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐      │
│   │ iOS App       │  │ Android App  │  │ Web App (Vue.js PWA) │      │
│   │ React Native  │  │ React Native │  │ Browser-based        │      │
│   └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘      │
│          │                  │                      │                  │
└──────────┼──────────────────┼──────────────────────┼─────────────────┘
           │                  │                      │
           │          HTTPS (encrypted)              │
           │                  │                      │
┌──────────┼──────────────────┼──────────────────────┼─────────────────┐
│          ▼                  ▼                      ▼    AWS CLOUD    │
│   ┌─────────────────────────────────────────────────────────┐       │
│   │                    AWS WAF (Firewall)                     │       │
│   └─────────────────────────┬───────────────────────────────┘       │
│                              │                                       │
│   ┌─────────────────────────▼───────────────────────────────┐       │
│   │              LOAD BALANCER (distributes traffic)          │       │
│   └─────────────────────────┬───────────────────────────────┘       │
│                              │                                       │
│   ┌─────────────────────────▼───────────────────────────────┐       │
│   │              LARAVEL API (Backend)                        │       │
│   │                                                           │       │
│   │  • Authentication & authorization                         │       │
│   │  • Business logic (coverage checks, contractor matching)  │       │
│   │  • Push notification dispatch                             │       │
│   │  • API gateway to Duke systems                            │       │
│   │  • Admin portal backend                                   │       │
│   └──────┬──────────────┬──────────────────┬────────────────┘       │
│          │              │                  │                         │
│          ▼              ▼                  ▼                         │
│   ┌───────────┐  ┌───────────┐  ┌─────────────────────┐            │
│   │ PostgreSQL │  │   Redis   │  │ File Storage (S3)   │            │
│   │ Database   │  │  Cache    │  │ Images, documents   │            │
│   └───────────┘  └───────────┘  └─────────────────────┘            │
│                                                                      │
│   ┌──────────────────────────────────────────────────────────┐      │
│   │              PUSH NOTIFICATION SERVICES                    │      │
│   │  • APNs (Apple Push Notification service) — for iOS       │      │
│   │  • FCM (Firebase Cloud Messaging) — for Android           │      │
│   └──────────────────────────────────────────────────────────┘      │
│                                                                      │
└──────────────────────────────┬───────────────────────────────────────┘
                               │
                          VPN / Secure Connection
                               │
┌──────────────────────────────▼───────────────────────────────────────┐
│                        DUKE ENERGY SYSTEMS                            │
│                                                                       │
│   ┌──────────────────┐  ┌────────────────────┐  ┌────────────────┐  │
│   │ SAP Commerce      │  │ Microsoft Dynamics  │  │ Duke Data      │  │
│   │ (Duke Electric    │  │ (P&G Gas customers, │  │ Fabric         │  │
│   │  customers, HPPs) │  │  service requests)  │  │ (Enterprise)   │  │
│   └──────────────────┘  └────────────────────┘  └────────────────┘  │
│                                                                       │
└───────────────────────────────────────────────────────────────────────┘
```

### How Data Flows for Key Features

**Customer books an HPP service request:**
```
1. Customer opens app → taps "Book Service"
2. App sends request to Laravel API: POST /api/service-requests
3. Laravel checks coverage: calls Commerce API for HPP plan details
4. Laravel matches contractor: queries PostgreSQL (trade + zip code)
5. Laravel creates service request in PostgreSQL (status: "Pending Confirmation")
6. Laravel sends push notification to admin portal: "New service request"
7. App shows customer: "Your request has been submitted"
8. Admin contacts contractor manually (MVP) → updates status in admin portal
9. Laravel sends push notification to customer: "Contractor confirmed for Tuesday"
```

**Customer scans a barcode for home inventory:**
```
1. Customer taps "Add Appliance" → "Scan Barcode"
2. React Native accesses phone camera (native hardware access)
3. Barcode library reads the UPC code
4. App sends barcode to Laravel API: POST /api/inventory/lookup
5. Laravel queries product database (or external API) for make/model
6. Data returns to app → customer confirms details → saved to PostgreSQL
```

### Why This Architecture Matters for You as PM

- **The phone app and the web app share the same backend.** Changes to business logic (coverage rules, contractor matching) happen once in Laravel. Both apps benefit immediately.
- **Duke's systems are never exposed directly.** Our API is the only thing that touches Commerce and Dynamics. This is a security requirement and simplifies Duke IT's involvement.
- **The admin portal is a separate web app (Vue.js)** that talks to the same Laravel API. Admin changes (updating a service request status) are immediately reflected in the customer app.
- **Redis caching matters for performance.** When 800K customers check their HPP plans, we don't hit Commerce for every single request — we cache the results.

---

## 3. The Tool Ecosystem

### What Each Tool Does and Why You Need to Know It

#### Development Tools

| Tool | What It Does | Who Uses It | Why It Matters to You |
|---|---|---|---|
| **React Native CLI** | Creates and runs the mobile app project | Developers | The foundation — if this breaks, nothing works |
| **Xcode** | Apple's IDE — required to build/test/submit iOS apps | Developers (on Macs) | iOS builds can ONLY happen on Macs. No exceptions. Budget for Mac hardware. |
| **Android Studio** | Google's IDE — required to build/test Android apps | Developers | Android builds work on Mac, Windows, or Linux |
| **VS Code** | Code editor where most React Native code is written | Developers | The daily workhorse |
| **Node.js / npm** | JavaScript runtime and package manager | Developers | React Native depends on this; version mismatches cause build failures |
| **CocoaPods** | iOS dependency manager | Developers | Installs native iOS libraries; fragile — a common source of build errors |
| **Gradle** | Android build system | Developers | Compiles the Android app; slow builds are normal (5-15 minutes) |
| **Laravel / Composer** | Backend framework and PHP package manager | Backend developers | The API that powers everything |

#### Testing Tools

| Tool | What It Does | Why It Matters |
|---|---|---|
| **Jest** | Unit testing for React Native code | Catches logic bugs before they ship |
| **React Native Testing Library** | Tests UI components in isolation | Verifies screens render correctly |
| **Detox or Appium** | End-to-end testing — simulates a real user tapping through the app | Catches integration bugs across screens |
| **PHPUnit** | Unit testing for Laravel backend | Catches API and business logic bugs |
| **Postman** | API testing tool — manually test API endpoints | Used during development and QA |

#### Build and Deployment Tools

| Tool | What It Does | Why It Matters |
|---|---|---|
| **Fastlane** | Automates iOS and Android builds, screenshots, and app store submissions | Without this, every release is hours of manual clicking |
| **EAS Build (Expo)** | Cloud build service for React Native (alternative to local builds) | Builds iOS apps without needing a Mac for every developer |
| **App Store Connect** | Apple's portal to manage iOS app submissions | Where you upload builds, manage TestFlight, respond to reviews |
| **Google Play Console** | Google's portal to manage Android app submissions | Same as above but for Android |
| **GitHub Actions / CI** | Automated build pipeline — runs tests and creates builds on every code change | Prevents broken code from reaching users |
| **CodePush (App Center)** | Pushes JavaScript-only updates to the app WITHOUT going through app stores | Critical for fast bug fixes — skip the 1-3 day review |

#### Monitoring and Operations Tools

| Tool | What It Does | Why It Matters |
|---|---|---|
| **Sentry** | Crash reporting — shows exactly where and why the app crashed | You see crashes in real time with stack traces |
| **Firebase Analytics** | Usage analytics — which screens do users visit, where do they drop off | Informs product decisions |
| **AWS CloudWatch** | Server monitoring — CPU, memory, API response times | Catches server issues before users notice |
| **Datadog or New Relic** | Application performance monitoring (APM) | Shows slow API calls, database bottlenecks |
| **PagerDuty or Opsgenie** | Alert escalation — pages the on-call engineer when something breaks | Ensures someone responds to production issues |

#### Accounts You Will Need (As PM, Know These Exist)

| Account | Owner | Cost | Lead Time |
|---|---|---|---|
| **Apple Developer Account** | Duke Energy (organization account) | $99/year | 1-5 business days to verify |
| **Google Play Developer Account** | Duke Energy | $25 one-time | 1-2 days |
| **Apple Developer Enterprise Account** (optional, for internal distribution) | Duke Energy | $299/year | Longer — Apple interviews you |
| **AWS Account** | Orases (managed) | Usage-based | Already have |
| **Firebase Account** | Orases (managed) | Free tier covers most needs | Instant |
| **Sentry Account** | Orases (managed) | Free tier or ~$26/month | Instant |
| **App Store Connect** | Linked to Apple Developer Account | Included | Same as Apple Dev |
| **Google Play Console** | Linked to Google Play Developer | Included | Same as Google Dev |

**Critical note:** The Apple Developer Account must be an **Organization account** under Duke Energy, not a personal account. This requires a D-U-N-S number (business identifier). If Duke doesn't have one, it takes 5-14 business days to get. **Start this process immediately after the platform decision is made.**

---

## 4. Building the App — Phase by Phase

### Phase 1: Project Setup and Foundation (Weeks 1-4 of development)

What happens:
- React Native project initialized with TypeScript
- Navigation structure set up (tab bar, screen stack)
- Authentication flow (login, registration, forgot password)
- API client configured to talk to Laravel backend
- Push notification infrastructure (APNs + FCM)
- CI/CD pipeline — automated builds on every code push
- App store accounts created and configured
- Design system established (Duke brand colors, typography, components)

**What can go wrong:**
- Apple Developer Account takes too long to verify → delays TestFlight
- Duke brand guidelines conflict with iOS/Android platform design patterns
- VPN setup between AWS and Duke systems takes longer than expected

**What you should be asking:**
- "Do we have the Apple Developer account set up?"
- "Can we build and run on both iOS and Android simulators?"
- "Is the CI pipeline producing builds automatically?"

### Phase 2: Core Features (Weeks 4-16)

Build the MVP features in priority order:
1. Registration and account linking (Commerce/Dynamics API dependent)
2. Home profile and HPP plan display
3. Service booking flow (symptom intake → coverage check → contractor match → confirmation)
4. Home inventory with barcode scanning
5. Notification center
6. Maintenance reminders
7. Service history
8. DIY content library

**What can go wrong:**
- Duke APIs not ready — team builds against mocks, then has to re-integrate later
- Barcode scanning library doesn't work well on older devices
- Push notifications are more complex than expected (especially iOS)
- Performance issues with large data sets (customer with 10+ properties, 50+ inventory items)

### Phase 3: Polish and Integration (Weeks 16-24)

- Real API integration replacing all mocks
- Performance optimization
- Offline capability implementation
- Accessibility compliance (ADA — screen readers, font scaling)
- Deep linking (app opens to the right screen from a push notification or email link)
- Analytics instrumentation
- Error handling and edge cases

### Phase 4: Testing and Launch Prep (Weeks 24-36)

Covered in detail in Section 5 and 6 below.

---

## 5. Testing — What Gets Tested and How

### Testing Pyramid (From Most to Least Frequent)

```
         ┌───────────┐
         │  Manual    │  ← QA team, UAT (Duke)
         │  Testing   │     Least automated, most expensive
         ├───────────┤
         │   E2E     │  ← Detox/Appium — simulates real user flows
         │   Tests   │     Slow to run (30-60 min), catches integration bugs
         ├───────────┤
         │Integration│  ← API tests — does the app talk to the server correctly?
         │  Tests    │     Medium speed, catches contract mismatches
         ├───────────┤
         │           │
         │   Unit    │  ← Jest — tests individual functions
         │   Tests   │     Fast (seconds), catches logic bugs
         │           │     Most automated, cheapest
         └───────────┘
```

### Types of Testing Specific to This Project

**1. Device Testing**
- iOS: Test on iPhone SE (smallest screen), iPhone 15 (standard), iPhone 15 Pro Max (largest), iPad
- Android: Test on at least 5 device sizes. Android fragmentation is the #1 testing challenge — there are thousands of device/OS combinations
- **Minimum Android OS**: Decide early. Supporting Android 8+ covers ~95% of users. Android 6-7 adds pain for little gain
- **Minimum iOS**: iOS 16+ covers ~95% of iPhones. Don't support iOS 14 — it's not worth it

**2. Network Testing**
- Test on slow 3G connections (Duke's rural service territory)
- Test with no connection (offline mode)
- Test with connection dropping mid-request (booking a service, then losing signal)

**3. Push Notification Testing**
- Test notifications when app is open, in background, and completely closed — they behave differently in each state
- Test notification tap → app opens to correct screen (deep linking)
- Test notification permissions denied — graceful fallback

**4. Barcode Scanning Testing**
- Test in low light
- Test with damaged/blurry barcodes
- Test with barcodes not in the product database (graceful "not found" handling)
- Test on older phone cameras

**5. Integration Testing with Duke Systems**
- Test with Commerce API returning slow responses (>5 seconds)
- Test with Commerce API returning errors (500s)
- Test with stale/cached data vs. fresh data
- Test customer with 0 HPP plans, 1 plan, and maximum plans

**6. User Acceptance Testing (UAT)**
- Duke stakeholders test the app on real devices
- Must cover all 3 customer types: HPP customer, utility-only customer, non-native customer
- Must test the full service booking flow end-to-end
- Per SOW: 10 business day review period per deliverable

### Testing Environments

| Environment | Purpose | Who Has Access | Data |
|---|---|---|---|
| **Local (Simulator)** | Developer testing on their machine | Developers | Fake/seed data |
| **Development** | Shared dev server, latest code | Dev team | Fake data |
| **Staging** | Pre-production mirror | Dev team + QA + Duke PM | Anonymized real-structure data |
| **Production** | Live — real users | Everyone | Real data |

**Beta Testing Programs:**
- **iOS**: TestFlight — Apple's official beta program. Up to 10,000 external testers. Duke stakeholders install TestFlight app, then get access to beta builds
- **Android**: Google Play Internal Testing → Closed Testing → Open Testing. Similar concept, different process

---

## 6. Deployment — Getting the App to Users

### The App Store Submission Process

This is one of the most misunderstood parts of native app development. Here's exactly what happens:

#### iOS (Apple App Store)

```
Code complete
    → Build the app (signed with Apple certificates)
    → Upload to App Store Connect
    → Submit for App Review
    → Apple reviews (1-3 days, sometimes longer)
    → If approved → release to users
    → If rejected → fix issues, resubmit, wait again
```

**What Apple reviews:**
- Privacy compliance (must declare all data collected)
- No crashes on launch
- All features work as described
- No placeholder content ("Lorem ipsum")
- Privacy policy URL is live and accessible
- App doesn't use private APIs or violate guidelines
- In-app purchases go through Apple's system (not relevant for MVP — no in-app payments)

**Common rejection reasons for apps like ours:**
- "Insufficient description" — app description doesn't explain what it does clearly
- "Broken links" — privacy policy URL returns 404
- "Login required but no demo account" — Apple reviewers need a test account to log in. **You must provide Apple a demo login.** This means building a demo mode or providing credentials
- "Incomplete information" — not explaining why the app needs camera access (barcode scanning)
- "Metadata" — screenshots don't match actual app appearance

**Apple-specific requirements:**
- Privacy "nutrition labels" — must declare every type of data collected (name, email, location, etc.)
- App Tracking Transparency — if using any analytics that tracks across apps, must show ATT prompt
- Camera usage description — must explain WHY the app needs camera ("Scan barcodes to add appliances to your home inventory")
- Push notification usage description — must explain why

#### Android (Google Play Store)

```
Code complete
    → Build the app (signed with upload key)
    → Upload to Google Play Console
    → Submit for review
    → Google reviews (hours to 2-3 days, usually faster than Apple)
    → If approved → release to users
```

**Google is generally less strict than Apple**, but they check:
- Data safety section (similar to Apple's privacy labels)
- Target API level compliance (Google requires targeting recent Android versions)
- No policy violations (malware, deceptive behavior)

**Google-specific requirements:**
- Data safety form — similar to Apple's privacy labels
- Content rating questionnaire — categorize your app's content
- Target audience declarations — this app is not for children, declare that

### First Submission vs. Updates

**First submission takes the longest:**
- Apple sometimes takes 7+ days for brand-new apps from new developer accounts
- Budget 2 weeks for the first submission cycle
- Have a "soft launch" plan — release to a limited audience first

**Updates are faster:**
- Typically 1-2 days for Apple, hours for Google
- But if you change something significant (new permissions, new data collection), review takes longer

### CodePush — The Secret Weapon

React Native has a unique advantage: **CodePush** (or similar OTA update tools) can push JavaScript bundle updates directly to users' phones without going through the app store.

What this means:
- Bug fix in the UI? Push it in minutes, not days
- Text change, layout fix, color correction? Instant
- **But**: native code changes (new camera feature, new native library) still require an app store update

**Limitations:**
- Apple's guidelines say CodePush updates cannot change the app's primary purpose or add major features
- Use it for bug fixes and minor improvements only
- Don't abuse it or Apple will reject future submissions

### Release Strategy for This Project

**Recommended approach:**

| Release Type | Frequency | Goes Through App Store? | Example |
|---|---|---|---|
| **Major release** | Monthly or per sprint milestone | Yes | New feature: maintenance reminders |
| **Minor release** | Bi-weekly | Yes (but fast review for minor changes) | Bug fixes, performance improvements |
| **Hotfix** | As needed | CodePush (no store) | Crash fix, text correction |
| **Backend update** | Anytime | No — server only | New API endpoint, business logic change |

---

## 7. Monitoring and Support — After Launch

### What to Monitor

#### App Health (Sentry + Firebase)

| Metric | What It Tells You | Alert Threshold |
|---|---|---|
| **Crash-free rate** | % of sessions without a crash | Alert if below 99.5% |
| **ANR rate** (Android Not Responding) | App freezes on Android | Alert if above 0.5% |
| **App launch time** | How long from tap to usable screen | Alert if above 3 seconds |
| **API error rate** | % of API calls that fail | Alert if above 1% |
| **Push notification delivery rate** | % of sent notifications that reach the device | Alert if below 95% |

#### Server Health (AWS CloudWatch + Datadog)

| Metric | What It Tells You | Alert Threshold |
|---|---|---|
| **API response time (p95)** | 95th percentile response speed | Alert if above 500ms |
| **Server CPU usage** | Is the server overloaded | Alert if above 80% sustained |
| **Database connections** | Is the database running out of connections | Alert if above 80% of max |
| **Error rate (5xx)** | Server errors | Alert if above 0.5% |
| **Redis cache hit rate** | Is caching working | Alert if below 90% |

#### Business Metrics (Firebase Analytics + Custom Dashboard)

| Metric | Duke's Target | How We Track |
|---|---|---|
| Service booking completion rate | >80% of started bookings finish | Funnel analytics |
| Time to book | <3 minutes | Timestamp from start to confirmation |
| Home inventory completion | 80% with at least 1 item | Database query |
| Push notification opt-in rate | >70% | Firebase |
| Daily active users | Track growth curve | Firebase |
| NPS score | 70+ | In-app survey |

### Incident Response

**When something breaks in production:**

```
Severity 1 (Critical): App crashes on launch, service booking broken
    → Alert fires → On-call engineer responds within 15 min
    → Fix deployed via CodePush (if JS) or emergency app store submission
    → Customer communication: push notification or email with ETA

Severity 2 (High): One feature broken, workaround exists
    → Alert fires → Engineer responds within 1 hour
    → Fix in next release cycle (1-3 days)

Severity 3 (Medium): Cosmetic issues, minor UX problems
    → Logged in Jira → Fixed in next sprint

Severity 4 (Low): Enhancement requests, edge cases
    → Backlog → Prioritized normally
```

### App Store Ratings and Reviews

**This is your public reputation.** Things to know:

- Users with bad experiences leave reviews. Users with good experiences don't (usually)
- You can prompt users for a review using Apple's `SKStoreReviewController` — but you get **3 prompts per year per user**. Time them after a positive moment (service completed successfully, good experience)
- **Respond to every negative review** in App Store Connect and Google Play Console. This is visible to all potential users
- A rating below 4.0 is a red flag for new users. Below 3.5 is a serious problem
- Both stores support "What's New" notes with each release — use these to show users you're actively improving

### Hypercare Period (Per SOW: 10 Calendar Days Post Each Production Release)

During hypercare:
- Same dev team monitors production
- Prioritize bug fixes over new features
- Daily status check on crash rates, error rates, user feedback
- Any defects found are classified and triaged per SOW defect handling process

---

## 8. Version Upgrades and Ongoing Releases

### React Native Upgrades

**This is one of the biggest ongoing costs of a React Native app.** React Native releases new versions roughly every 3-4 months. Each upgrade can be:

- **Minor** (0.73 → 0.74): Usually smooth, 1-2 days of work
- **Major** (0.74 → 0.75 with architecture changes): Can take 1-2 weeks. Breaking changes are common

**The "New Architecture" transition:**
React Native has been migrating to a new internal architecture (Fabric renderer, TurboModules, JSI). As of 2025-2026, this is largely complete, but some third-party libraries may still need updates. Your team should be on the new architecture from day one.

**Upgrade strategy:**
- Don't fall more than 2 versions behind — the longer you wait, the harder it gets
- Test thoroughly on both iOS and Android after every upgrade
- Budget 1-2 sprint days per quarter for React Native upgrades

### iOS and Android OS Upgrades

Every September, Apple releases a new iOS version. Every fall, Google releases a new Android version.

**What this means for you:**
- Apple announces new iOS at WWDC (June) → gives developers 3 months to update
- Some OS changes break things: new permission requirements, deprecated APIs, UI changes
- You MUST test on the new OS beta before it launches to find problems early
- Budget 1-2 weeks of engineering time each September for OS compatibility testing

**Common issues with OS upgrades:**
- Push notification behavior changes (Apple changes these frequently)
- New privacy requirements (Apple adds new ones every year)
- UI components look different (especially with major iOS design refreshes)
- Camera API changes affecting barcode scanning

### Third-Party Library Maintenance

The app will use 50-100+ third-party libraries (navigation, camera, push notifications, analytics, etc.). These need ongoing maintenance:

- Security patches — if a library has a vulnerability, update immediately
- Compatibility fixes — when React Native or iOS/Android updates break a library
- Deprecations — library authors stop maintaining; you need to find alternatives

**Budget for this:** ~10% of ongoing engineering time goes to maintenance, upgrades, and dependency management. This is normal and unavoidable.

### App Store Policy Changes

Apple and Google change their policies regularly. Examples:
- Apple required App Tracking Transparency (ATT) in iOS 14.5 — broke many apps' analytics
- Google required target API level 33+ — apps targeting older APIs were delisted
- Apple required privacy manifests in 2024 — all apps needed to declare SDK usage

**Your team must monitor:**
- Apple Developer News and Google Play Console announcements
- React Native community channels for reports of breaking changes
- Library changelogs for compatibility notes

---

## 9. Pitfalls to Avoid

### Architecture Pitfalls

1. **Don't skip the API design phase.** If the API contract between the app and server isn't well-defined before coding starts, you'll waste sprints on rework. The app team and backend team will build incompatible things.

2. **Don't let the app talk directly to Duke's APIs.** Everything goes through your Laravel backend. Direct connections create security risks, coupling, and make it impossible to add caching or fallback logic.

3. **Don't build the web app (Vue.js PWA) as an afterthought.** The proposal says "feature parity." If the web app isn't designed alongside the mobile app, it will always feel like a second-class citizen. Share the API, design the flows together.

4. **Don't ignore offline from the start.** Retrofitting offline support is 5x harder than building it in. Define early: what works offline (viewing cached plans, saved inventory) and what doesn't (booking a service, making payment).

### Development Pitfalls

5. **Don't let developers only test on simulators.** The iOS Simulator and Android Emulator hide real-world problems: camera doesn't work in simulators, push notifications behave differently, performance is misleading (simulators run on your fast Mac, not a $200 Android phone).

6. **Don't ignore Android.** Teams tend to develop primarily on iOS and treat Android as "it probably works." Android has 10x more device fragmentation. Test on real low-end Android devices early and often.

7. **Don't use Expo for this project.** Expo is a popular React Native framework that simplifies development but limits native module access. For this project (barcode scanning, deep push notification control, potential offline/Bluetooth in Phase 2), you need full React Native CLI — not Expo's managed workflow. (Note: Expo's bare workflow is fine, but confirm this with the tech lead.)

8. **Don't underestimate push notification complexity.** Push notifications touch: APNs certificates, FCM setup, notification channels (Android), permission handling, background vs. foreground behavior, deep linking, silent notifications, and notification grouping. Budget 2-3 sprints for push notifications alone.

### Testing Pitfalls

9. **Don't skip accessibility testing.** Duke is a utility company — their customer base includes elderly and disabled users. Screen reader support (VoiceOver on iOS, TalkBack on Android), dynamic font sizes, and color contrast are not optional. Accessibility lawsuits against apps are increasing.

10. **Don't assume "works on my phone" means it works.** The PM or QA lead should maintain a device matrix — a list of specific phone models and OS versions that every release is tested on.

### Deployment Pitfalls

11. **Don't submit to the App Store for the first time the week before launch.** Apple's first review of a new app can take 7+ days and frequently results in rejection. Submit a minimal "coming soon" version 4-6 weeks before launch to establish the app listing and clear the first review.

12. **Don't forget the Apple demo account.** Apple reviewers must be able to log in. They won't create a Duke Energy account. Build a demo mode or maintain test credentials that Apple can use.

13. **Don't hard-code anything environment-specific.** API URLs, feature flags, analytics keys — all must be configurable per environment (dev, staging, production). A hard-coded staging URL shipping to production is a common catastrophic mistake.

14. **Don't forget app store metadata.** Screenshots (6.7" and 5.5" for iPhone, multiple sizes for Android), description, keywords, privacy policy URL, support URL, marketing URL — all required before first submission. This takes more time than you'd expect. Budget a full day.

### Support Pitfalls

15. **Don't launch without crash reporting.** If you can't see crashes in real time, you won't know the app is broken until users leave 1-star reviews. Sentry or equivalent must be integrated before the first beta build.

16. **Don't ignore app store reviews.** A 1-star review saying "app crashes when I try to book service" that goes unanswered for 2 weeks is visible to every potential user. Assign someone to monitor and respond daily post-launch.

17. **Don't assume CodePush fixes everything.** If the bug is in native code (camera module, push notification handler), CodePush can't help. You need a full app store submission, which takes 1-3 days.

---

## 10. Dos and Don'ts

### Do

- **Do establish the Apple Developer Account (organization) immediately** after the platform decision. The D-U-N-S number verification can take 2 weeks.
- **Do require the design team to follow both iOS Human Interface Guidelines and Android Material Design** — the app should feel native on each platform, not identical.
- **Do implement feature flags from day one.** This lets you turn features on/off without deploying new code. Critical for MVP when features may not be ready (e.g., ad-hoc services only in pilot markets).
- **Do set up the CI/CD pipeline in Sprint 1.** Automated builds catch problems early and save hundreds of hours over the project.
- **Do test on real devices every sprint.** Minimum: 1 iPhone, 1 high-end Android, 1 low-end Android.
- **Do plan for app store review time in every release.** Never promise "fix will be live tomorrow" — App Store review takes 1-3 days.
- **Do keep the app size small.** Users on slow connections (rural Duke territory) may abandon downloads over 100MB. Target under 50MB for the initial download.
- **Do build analytics in from the start.** You need data to prove Duke's KPIs (3-minute booking time, 40% call center reduction). If you don't track from day one, you can't prove value.
- **Do create a device testing lab** (even if it's just 5-6 phones) for QA.
- **Do document the build and release process.** If only one developer knows how to submit to the App Store, that's a bus factor of 1.

### Don't

- **Don't let the client see the app only in demos.** Get TestFlight and internal testing builds to Duke's PM weekly. Frequent hands-on testing catches UX problems early.
- **Don't treat the admin portal as lower priority.** In MVP, admin IS the automation layer. If the admin portal is clunky, contractors don't get contacted within the 1-hour SLA, and customers have a bad experience.
- **Don't build custom UI components when React Native has good ones.** Use established libraries (React Navigation, React Native Paper, or similar) instead of building from scratch.
- **Don't promise feature parity between iOS and Android if there are platform differences.** Be transparent — some features work differently (notification grouping, background refresh behavior).
- **Don't store sensitive data in AsyncStorage.** Use React Native Keychain (iOS) / Encrypted SharedPreferences (Android) for auth tokens. AsyncStorage is NOT encrypted.
- **Don't skip the privacy policy.** The app collects personal data (name, address, phone, home inventory). Privacy policy must be written by legal, not engineering. Start the Duke legal review in Week 1.
- **Don't use console.log in production builds.** It leaks data and degrades performance. Strip all logs in release builds.
- **Don't ignore the web version (Vue.js PWA).** The SOW includes it. If the web version launches broken or incomplete, Duke will rightly consider that a miss.
- **Don't let state management get out of control.** Pick a state management approach (Redux, Zustand, React Query for server state) in Sprint 1 and stick with it. Mixing approaches causes maintenance nightmares.
- **Don't skip error boundaries.** When one screen crashes, the whole app shouldn't crash. React error boundaries catch component failures gracefully.

---

## 11. Glossary

| Term | What It Means |
|---|---|
| **APNs** | Apple Push Notification service — Apple's system for delivering push notifications to iPhones |
| **App Store Connect** | Apple's web portal where you manage your iOS app listing, builds, reviews, and analytics |
| **AsyncStorage** | React Native's simple key-value storage on the device — NOT encrypted, NOT for sensitive data |
| **Build** | The process of turning source code into an installable app file (.ipa for iOS, .apk/.aab for Android) |
| **Bundle** | The JavaScript code package that React Native runs on the device |
| **CI/CD** | Continuous Integration / Continuous Deployment — automated systems that build, test, and deploy code |
| **CocoaPods** | Dependency manager for iOS native libraries |
| **CodePush** | Microsoft's service for pushing JavaScript updates to React Native apps without app store review |
| **Code Signing** | Cryptographic proof that the app was built by an authorized developer — required by both Apple and Google |
| **D-U-N-S Number** | Dun & Bradstreet business identifier — required by Apple for organization developer accounts |
| **Deep Linking** | URLs that open a specific screen inside the app (e.g., tapping a notification opens the service request detail) |
| **Detox** | End-to-end testing framework for React Native — simulates user interactions |
| **EAS** | Expo Application Services — cloud build and submission tools for React Native |
| **Error Boundary** | A React component that catches JavaScript errors in child components and shows a fallback UI instead of crashing |
| **Fabric** | React Native's new rendering system (part of the "New Architecture") — faster and more efficient |
| **Fastlane** | Automation tool for building, signing, and submitting iOS and Android apps |
| **FCM** | Firebase Cloud Messaging — Google's system for delivering push notifications to Android devices |
| **Feature Flag** | A toggle that enables/disables a feature without deploying new code |
| **Google Play Console** | Google's web portal for managing Android app listings, builds, reviews, and analytics |
| **Gradle** | Build system for Android apps — compiles code, manages dependencies, produces the final APK/AAB |
| **Hermes** | JavaScript engine optimized for React Native — faster startup and lower memory usage than the default engine |
| **Hot Reload** | React Native feature that updates the UI instantly as developers change code — speeds up development |
| **JSI** | JavaScript Interface — part of React Native's new architecture that enables faster communication between JavaScript and native code |
| **Keychain** | iOS secure storage for sensitive data (tokens, passwords). Android equivalent: EncryptedSharedPreferences |
| **Metro** | React Native's JavaScript bundler — packages all JS code for the app |
| **Native Module** | Custom code written in Swift/Kotlin that bridges React Native to platform-specific features (camera, Bluetooth, etc.) |
| **OTA Update** | Over-The-Air update — pushing changes to the app without going through the app store (see CodePush) |
| **Provisioning Profile** | iOS certificate that links an app to a developer account, specific devices, and permissions |
| **React Navigation** | The standard navigation library for React Native — handles screen stacks, tabs, drawers |
| **Redux / Zustand** | State management libraries — manage the app's data flow between components |
| **Simulator (iOS) / Emulator (Android)** | Virtual phones that run on your computer for testing. Not the same as real devices |
| **TestFlight** | Apple's official beta testing platform — up to 10,000 external testers can install pre-release builds |
| **TurboModules** | Part of React Native's new architecture — loads native modules on demand for faster startup |
| **TypeScript** | Typed version of JavaScript — catches bugs at compile time. Industry standard for React Native projects |
| **Xcode** | Apple's development environment — required to build any iOS app. Only runs on macOS |

---

*Prepared for: Aksana Rahouski, Product Manager (Orases)*
*Context: Duke Energy RS Home Services & Warranty Application*
*Tech stack: React Native (mobile) + Vue.js (web) + Laravel (backend) + PostgreSQL + AWS*
