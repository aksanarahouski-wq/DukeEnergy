# Customer App Platform Decision: Native vs. PWA
### Duke Energy RS Home Services & Warranty Application
### Prepared for: Pre-Kickoff Alignment — Section 4G

**Decision Required Before:** Sprint 1
**Decision Owner:** Duke Energy + Orases Tech Lead
**Prepared by:** Aksana Rahouski, Product Manager (Orases)

---

## Context

The customer-facing application platform has not been finalized. This decision gates all frontend architecture, push notification infrastructure, barcode scanning implementation, offline capability approach, and mobile app deployment setup.

This document compares the two options — **Native (React Native)** and **PWA (Progressive Web App)** — across the capabilities that matter for this project, and frames the short-term and long-term investment implications.

---

## What Are the Two Options?

### Native App (React Native)
- A real app downloaded from the Apple App Store and Google Play Store
- Lives on the user's home screen like any other app
- Built with React Native — one codebase produces both iOS and Android apps
- Requires app store accounts, review cycles, and distribution infrastructure

### PWA (Progressive Web App)
- A website that behaves like an app — can be "installed" from the browser to the home screen
- Runs in the browser engine, not as a standalone application
- No app store involvement — users access it via a URL
- Deployed like a website with instant updates

---

## Capability Comparison

| Capability | Native (React Native) | PWA |
|---|---|---|
| **Push notifications** | Full support, both iOS and Android | Works on Android. **Unreliable on iOS** — Apple added partial PWA push support in 2023, but it is limited and inconsistent |
| **Barcode scanning** | Full camera access, fast, reliable | Works but inconsistent across devices and browsers |
| **Offline capability** | Strong — can cache data and function without connectivity | Basic — can cache pages, but limited offline functionality |
| **App store presence** | Yes — discoverable in App Store / Google Play | No — users find it only via URL |
| **Performance** | Near-native speed, smooth animations | Good but noticeably slower on complex screens |
| **Installation** | User downloads from store (familiar experience) | User must "Add to Home Screen" from browser (most users don't know how) |
| **Updates** | Submitted to app stores; review takes 1–3 days | Instant — update the server, everyone gets it immediately |
| **App store review** | Required — Apple can reject or delay releases | None needed |
| **IoT / Bluetooth access** | Full hardware access | No Bluetooth; limited hardware access |
| **Biometric authentication** | Full Face ID / Touch ID / fingerprint support | Limited browser-based support |

---

## Short-Term Investment (Phase 1 / MVP)

### PWA: Lower upfront cost
- One web codebase, no app store setup
- No Apple/Google review cycles to manage
- No code signing certificates, provisioning profiles, or TestFlight setup
- Simpler DevOps — deploy like a website
- **Estimated savings: 15–20% less frontend effort in Phase 1**

### Native: Higher upfront cost
- App store account setup (Apple $99/year, Google $25 one-time)
- Code signing and app distribution pipeline
- TestFlight (iOS beta) and Play Store internal testing tracks
- App store compliance (privacy labels, screenshots, descriptions)
- Push notification infrastructure (APNs for iOS, FCM for Android)

### Cost Framing
If the frontend work represents ~$200K of the MVP budget, native adds roughly **$30K–$40K** in additional setup, tooling, and deployment complexity compared to PWA.

---

## Long-Term Investment (Phase 2+ and Beyond)

This is where the picture shifts. **Native wins long-term.**

### 1. Customer Acquisition
Duke's goal is **250K non-native customers within 24 months**. An App Store / Google Play listing is a discovery and acquisition channel. PWAs have zero app store visibility.

### 2. IoT and Smart Home Integration (Phase 2/3)
The product roadmap includes IoT device integration and smart home features. Native apps have full Bluetooth and hardware access. PWAs do not support Bluetooth and have limited device API access.

### 3. Push Notifications Are Business-Critical
The "Uber of home services" experience depends on real-time updates: "your contractor is on the way," "job complete — please rate." iOS push notifications for PWAs are too unreliable for a business-critical flow serving **800K+ customers**.

### 4. Brand Credibility
Duke Energy is a major utility company. Competitors and market comparables (American Home Shield, Frontdoor) all have native apps. A PWA-only approach may feel like a half-measure to customers and internal stakeholders.

### 5. Barcode Scanning for Home Inventory
**80% home inventory completion** is a project KPI. Native camera access is significantly more reliable for scanning product barcodes than browser-based implementations.

### 6. Offline Capability in Duke's Service Territory
Customers in Duke's territory include rural areas across NC, SC, IN, OH, and FL where connectivity may be spotty. Native handles offline scenarios more robustly.

### 7. Avoiding the "Build It Twice" Problem
Choosing PWA now to save 15–20% and then switching to native in Phase 2 means **rebuilding the entire frontend**. The short-term savings are consumed by the cost of migration, and you lose months of schedule.

---

## Decision Matrix

| Factor | Weight | Native | PWA | Notes |
|---|---|---|---|---|
| Push notification reliability (iOS) | **Critical** | **Strong** | Weak | Core to the "real-time updates" value proposition |
| App store presence / discoverability | High | **Yes** | No | Required for 250K non-native customer acquisition goal |
| Barcode scanning reliability | High | **Strong** | Inconsistent | Required for 80% home inventory completion KPI |
| Offline capability | Medium | **Strong** | Limited | Important for rural service territory |
| IoT / hardware access (Phase 2+) | Medium | **Full** | None | Bluetooth required for smart home roadmap |
| Upfront cost (Phase 1) | Medium | Higher | **Lower** | ~$30K–$40K difference on frontend work |
| Deployment speed | Low | Slower (store reviews) | **Faster** | 1–3 day review cycles vs. instant |
| Long-term total cost of ownership | **Critical** | **Lower** | Higher | PWA → Native migration costs exceed upfront savings |

---

## Recommendation

**Build native (React Native) from day one.**

The PWA saves 15–20% on frontend costs in the first 6 months, but creates technical debt that must be repaid when push notifications, app store presence, and hardware access become requirements. With a 44-week runway to MVP (September 30, 2026), there is sufficient time to set up the native pipeline correctly.

The only scenario where PWA is the right choice: if Duke needs a proof-of-concept live in 8 weeks and plans to rebuild afterward. That is not the case for this engagement.

---

## Questions for Duke (Meeting Discussion)

These questions help confirm or adjust the recommendation based on Duke's specific situation:

| Question | If Yes → | If No → |
|---|---|---|
| Does Duke have existing app store developer accounts? | Lower setup cost for native | Minor — accounts take 1 day to create |
| Is App Store / Play Store presence important for customer acquisition and brand? | Strong signal toward native | Unusual for a consumer product; explore reasoning |
| Is barcode scanning for home inventory a must-have at MVP? | Native is significantly more reliable | PWA could work, but still carries risk |
| What is Duke IT's security posture on native app distribution vs. web-only? | May have existing MDM or app distribution policies to align with | Need to understand their specific concerns |
| Does Duke have plans for IoT / smart home features in Phase 2? | Native is required for Bluetooth/hardware access | Reduces one advantage of native, but others remain |

---

## Next Steps

1. **Discuss this document with Duke's Product Owner and IT stakeholders**
2. **Confirm decision before Sprint 1 begins** — this gates all frontend architecture work
3. **If native is confirmed:** Orases will include app store account setup, CI/CD pipeline for mobile builds, and push notification infrastructure in the Sprint 1 technical foundation work

---

*Source documents: SOW #1 V6, Kickoff Meeting Agenda (Section 4G), Discovery Findings & Updated Scope (Dec 2025), Customer App Scope*
*Prepared by: Aksana Rahouski, Product Manager (Orases)*
