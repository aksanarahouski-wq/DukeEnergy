# Executive Summary: Duke Energy Clarification Response

**Date**: October 21, 2025
**Meeting**: October 24, 2025, 2:30-4:00 PM (ET)

---

## Quick Reference: Key Responses

### 1. Training & Train-the-Trainer Program

**Structure**: 3-Phase Program (Weeks 38-44)

| Phase | Duration | Participants | Deliverables |
|-------|----------|--------------|--------------|
| **Phase 1**: Core Team Training | 2 weeks | 8-12 Duke trainers | System admin training, hands-on labs |
| **Phase 2**: Certification | 1 week | Same trainers | Facilitator guide, presentations, certification |
| **Phase 3**: Rollout | 4 weeks | End users | Duke-led training with Orases support |

**Post-Launch Support**:
- Months 1-3: Weekly office hours (included in warranty)
- Months 4-12: Quarterly refreshers (ongoing support contract)

**Success Metrics**: 90% trainer certification, 80% user completion, <5% basic functionality tickets

---

### 2. Content Management System (CMS)

**Recommendation**: **Strapi Headless CMS** + Custom Extensions

**Why Strapi?**
- Open-source (no licensing fees)
- API-first (perfect for mobile + web)
- Self-hosted (Duke Energy control)
- Modern, scalable Node.js platform

**Key Features**:
- Content versioning and approval workflows
- Role-based access (Admin, Manager, Creator, Reviewer)
- Media library with video hosting integration
- Product catalog management
- Multi-region content support

**Cost**:
- Initial Setup: Included in proposal
- Year 1 Operations: $6,000-15,000 (hosting, CDN, media storage)
- Optional Enterprise Support: $12,000/year

**Alternative**: Custom CMS ($150K-300K) - Not recommended

---

### 3. Native vs. Responsive Mobile App

**Approach**: **React Native** (Native Apps) + **Vue.js PWA** (Web)

#### Feature Comparison

| Capability | Native Apps | PWA |
|-----------|-------------|-----|
| **Platform** | iOS & Android App Stores | Any web browser |
| **Offline Access** | ✅ Full offline functionality | ⚠️ Limited (cached pages) |
| **Performance** | ✅ Near-native, 60fps | ✅ Good (some limitations) |
| **Device APIs** | ✅ Camera, biometrics, push | ⚠️ Limited browser access |
| **Updates** | ⚠️ App store review (1-3 days) | ✅ Instant updates |
| **Installation** | Requires download | Optional "Add to Home" |

#### Features ONLY in Native Apps
1. Barcode/QR code scanning (appliance inventory)
2. Biometric authentication (Face ID, Touch ID)
3. Rich push notifications (images, actions, deep links)
4. Full offline mode (complete functionality)
5. Background data sync
6. Native camera integration (better quality)

#### User Journey
- **Native Apps**: Primary users (customers, contractors) - Best performance and UX
- **PWA**: New users, occasional access, desktop staff - No download barrier

**Code Sharing**: 90% shared business logic between all platforms

**Timeline Advantage**: React Native saves 8-12 weeks vs. separate native development

---

### 4. Third-Party Services & Costs

#### Phase 1: Cost-Optimized Approach (Year 1)

| Service | Purpose | Annual Cost | Status |
|---------|---------|-------------|--------|
| **Centriq** | Appliance database (manuals, recalls) | $12,000 | ✅ Include |
| **Sendbird** | In-app messaging (customer-contractor) | $24,000 | ✅ Include |
| **OneSignal** | Push notifications (cost-optimized) | $6,000 | ✅ Include |
| **Twilio** | SMS notifications & verification | $16,000 | ✅ Include |
| **Sentry** | Error tracking & monitoring | $1,500 | ✅ Include |
| **AWS S3/CloudFront** | Media storage & CDN | $15,000 | ✅ Include |
| **Mixpanel** | Product analytics | $3,000 | ✅ Include |
| **Firebase Analytics** | Basic attribution | $0 (Free) | ✅ Include |

**Phase 1 Total**: **~$65,000/year**

#### Phase 2: Growth & Marketing Tools (Year 2+)

| Service | Purpose | Annual Cost | When to Add |
|---------|---------|-------------|-------------|
| **Airship** | Advanced push & marketing automation | +$30,000 | When MAU > 100K |
| **AppsFlyer** | Mobile attribution & fraud prevention | +$24,000 | Marketing budget > $500K |
| **OpenAI API** | AI virtual assistant | +$2,000-12,000 | Support volume > 1K/mo |

**Phase 2 Additional**: **+$40-60,000/year**

#### Cost-Saving Strategies
1. **Start Free/Low-Cost**: Use OneSignal vs. Airship (saves $30K Year 1)
2. **Firebase vs. AppsFlyer**: Free attribution initially (saves $24K Year 1)
3. **Defer AI Features**: Focus on core functionality first (saves $2-12K Year 1)

**Total Savings Year 1**: **~$56,000**

#### Alternatives Evaluated
- **OneSignal** vs. Airship: 80% features, 85% cost savings
- **AWS SNS** vs. Twilio: 20% cheaper but fewer features
- **Stream Chat** vs. Sendbird: Similar pricing, Sendbird more established
- **Firebase** vs. AppsFlyer: Free vs. $24K, upgrade when marketing scales

---

## Financial Impact Summary

| Category | Phase 1 (Year 1) | Phase 2 (Year 2+) |
|----------|------------------|-------------------|
| **Third-Party Services** | $65,000/year | $105,000-125,000/year |
| **CMS Operations** | $6,000-15,000/year | $6,000-15,000/year |
| **Total Ongoing Costs** | **$71,000-80,000/year** | **$111,000-140,000/year** |

**Note**: These are operational costs. Initial development/setup is included in the proposal.

---

## Key Decision Points for Meeting

### Training
- [ ] How many internal trainers will Duke Energy assign?
- [ ] Virtual vs. on-site training preference?
- [ ] Existing LMS system integration requirements?

### CMS
- [ ] Who will be primary content administrators?
- [ ] Content approval workflows for compliance?
- [ ] Expected content volume (articles, videos)?
- [ ] Any existing content to migrate?

### Native vs. PWA
- [ ] Expected mobile vs. desktop usage split?
- [ ] Features that must work offline?
- [ ] Contractor app: Separate or same app with roles?

### Third-Party Services
- [ ] Marketing budget for user acquisition?
- [ ] Existing vendor relationships to leverage?
- [ ] Appetite for Phase 2 marketing tools?
- [ ] White-label/multi-tenant architecture for future?

---

## Meeting Deliverables Checklist

**Pre-Meeting (By October 22)**:
- [ ] Comprehensive written response (PDF)
- [ ] Visual presentation deck
- [ ] CMS interface mockup
- [ ] Third-party cost spreadsheet
- [ ] Updated project timeline

**During Meeting**:
- [ ] Live demo: Native vs. PWA comparison
- [ ] CMS workflow demonstration
- [ ] Q&A for each section
- [ ] Capture action items and next steps

**Post-Meeting**:
- [ ] Meeting notes and action items summary
- [ ] Revised proposal (if needed)
- [ ] Updated pricing matrix
- [ ] Contract next steps timeline

---

## Talking Points

### Why This Approach Wins

**Training**:
- "Duke Energy maintains control by training internal trainers"
- "Scalable model: Train 10 trainers who can train 1,000+ users"
- "Reduces long-term dependency on Orases"

**CMS**:
- "Strapi gives you full control without vendor lock-in"
- "API-first architecture is future-proof for additional channels"
- "Open-source means no licensing surprises"

**Native vs. PWA**:
- "React Native gives true native performance with 90% code sharing"
- "PWA reduces friction for new user acquisition"
- "8-12 week time savings vs. separate native development"

**Third-Party Services**:
- "Cost-optimized Phase 1 keeps operational costs manageable"
- "Clear upgrade path when marketing scales"
- "All services are industry leaders with proven reliability"

---

## Risk Mitigation

| Risk | Mitigation |
|------|-----------|
| **High operational costs** | Phased approach saves $56K in Year 1; upgrade when justified by usage |
| **CMS vendor lock-in** | Open-source Strapi; can self-maintain or change providers |
| **Native app performance concerns** | React Native provides near-native performance; extensive testing in weeks 32-36 |
| **Training effectiveness** | Train-the-trainer model with certification ensures quality; success metrics tracked |
| **Third-party service outages** | All recommended services have 99.9%+ SLAs; backup strategies in place |

---

## Next Steps After Meeting

1. **Immediate** (Within 48 hours):
   - Send meeting notes and action items
   - Clarify any outstanding technical questions

2. **Week of October 28**:
   - Provide revised proposal (if changes needed)
   - Submit updated pricing matrix with operational costs
   - Share detailed implementation plan

3. **Early November**:
   - Contract finalization
   - Project kickoff planning
   - Team introductions

---

## Contact Information

**Project Team**:
- [Project Executive]: Strategy and partnership
- [Technical Architect]: CMS and technical architecture
- [Development Lead]: Third-party integrations
- [Training Lead]: Training program delivery

**For Questions Before Meeting**:
[Contact Email]
[Contact Phone]

---

**Meeting Confirmed**: October 24, 2025, 2:30-4:00 PM (ET)
