# Duke Energy x Orases — Pre-Kickoff Alignment Meeting Agenda
### Project: RS Home Services & Warranty Application | SOW #1

**Meeting Date:** March 6, 2026
**Duration:** 60–90 minutes
**Attendees (Orases):** Aksana Rahouski (Product Manager), supporting sales team
**Attendees (Duke Energy):** Joshua (Product Manager)

---

## Purpose of This Meeting

The SOW is not yet signed. This is a pre-kickoff alignment call — an open, collaborative conversation to get to know each other, surface the right questions early, and make sure both teams are set up for a strong start once we execute. The tone here is exploratory, not operational.

The goal is to leave with a shared sense of how we'll work together, who the key people are on both sides, and a short list of things to align on before the formal kickoff. We are not making binding decisions today — we are opening the right conversations.

---

## Agenda

### 1. Introductions (10 min)

- Brief introductions: Aksana Rahouski (Product Manager, Orases) and Joshua (Duke Energy PM)
- **Understand the scope of Joshua's authority:** We know from the SOW that Joshua is the designated Product Owner. What we want to understand is how decisions flow — what can he approve independently (sprint estimates, deliverable acceptance, scope prioritization) vs. what requires escalation to executive sponsors?
- **Identify executive sponsors and stakeholders:** Who are the executive sponsors for this project? What level of visibility and involvement do they expect? The SOW requires monthly stakeholder meetings with Duke's executive sponsors — we want to know who those people are and confirm they're bought in to that commitment.
- Identify other Duke team members we'll work with regularly — IT contacts, business SMEs, operations leads

---

### 2. Project Overview & Scope Alignment (20 min)

Walk through the high-level scope to confirm both teams are aligned before we execute. Surface any questions or changes that have come up since the proposal.

**Key points to confirm:**

- **What we're building:** Customer-facing app + Admin portal backend. No contractor portal changes in Phase 1 — contractors continue using existing Commerce CRM.
- **Three customer types the app serves:** Existing HPP customers (800K+), existing Duke/P&G utility customers without HPPs, and non-native customers (homeowners outside Duke's utility territory). All three are in MVP scope.
- **Two back-end CRM systems:** SAP Commerce for Duke electric customers, Microsoft Dynamics for P&G gas customers. We are building the integration layer that connects both. Confirm Duke's understanding of this split and any constraints on data access.
- **Customer app platform — TBD (decision needed):** It is not yet decided whether the customer app will be built as native iOS and Android apps or as a web PWA (Progressive Web App). This is a significant architectural and cost decision that must be resolved before development planning begins. See Section 4G below.
- **What Phase 1 is NOT:** No FSM integration, no in-app payments, no real-time contractor GPS tracking, no contractor marketplace. These are Phase 2.
- **MVP target: September 30, 2026.** Phase 1 complete: December 31, 2027. Note: these dates were established in the SOW as targets. The formal MVP scope definition — what's actually in and out — will be produced during the first 4–8 weeks of workshops and PRD work. We want to confirm Duke's understanding of this: September 30 is the target, and the PRD process is how we agree on what "done" means.
- **T&M engagement:** The SOW has written approval requirements before work begins. We want to align with Joshua on what that process should look like — per sprint, per PRD, or something else — and make sure it works for both teams.
- **The bridge gap reality:** Phase 1 includes significant manual fallback processes (admin manually contacts contractors within 1 hour of booking, manually updates statuses). This is intentional — we cannot wait 6–12 months for FSM/API availability. Duke's ops team needs to be staffed and trained for this.

**Questions to ask Duke:**
- Are there any scope concerns or additions that came up since the proposal?
- Has the business case or priority ranking of features changed?

---

### 3. How We'll Run This Project (20 min)

Align on the operating model before any work begins.

#### Sprint Cadence
- 2-week sprints
- The SOW has written approval requirements before work begins. What does that look like in practice — do we want approval before every sprint, or does PRD approval cover the sprint-level work within it? We want to define a process that gives Duke the visibility they need without creating unnecessary overhead for Joshua's team.
- Demos when meaningful functionality is ready — not necessarily every sprint. We'll flag when something is worth showing.

#### Sprint Status Reports — Let's Define This Together
The SOW requires written sprint status updates. What we want to figure out with Joshua:
- **What format is actually useful for him?** A short email summary? A Confluence page update? A Trello board update he can already see? We don't want to create paperwork that no one reads.
- **How often?** Every sprint, or only when there's something material to report?
- **What level of detail?** High-level milestone progress, or hour-by-hour burn? Let's let Joshua tell us what arms him best with his stakeholders.

#### Tools — Confirm What Works
- Jira (Orases internal tracking)
- Trello (Duke-facing visibility board — we'll set this up in Week 1)
- Confluence (all documentation, PRDs, TRDs, meeting notes, approval records)
- Email (primary async communication for client-facing updates and approvals)
- Video calls — **confirm Duke's preference: Google Meet or Teams?**

#### Meetings — Proposed Recurring Cadence (Open to Adjustment)
| Meeting | Proposed Frequency | Participants | Purpose |
|---|---|---|---|
| Sprint kickoff | Every 2 weeks | Joshua + Aksana | Review priorities, approve next sprint estimate |
| Sprint status | Every 2 weeks | Joshua + Aksana | Status update — format TBD with Joshua |
| Tech sync | Weekly (during API work) | Duke IT + Orases Tech Lead | API progress, integration blockers |
| Stakeholder review | Monthly | Duke executive sponsors + Orases | High-level progress, milestone visibility |
| Ad hoc | As needed | Joshua + Aksana | Scope questions, blockers, reprioritization |

These are a starting point — we want Joshua's input on what cadence actually works.

#### Scope Changes — How Do We Handle Them?
When Duke wants something that adds cost or time beyond what's in an approved PRD, we need a lightweight process to document it and get written sign-off before we act on it. We're not looking to create bureaucracy — we want a clear paper trail that protects both sides and gives Joshua what he needs to go back to his stakeholders.

**Open question for this meeting:** Where should that documentation live — Confluence, email, both? We'd like to define this with Joshua and the team before we formalize it.

---

### 4. Critical Path Items to Align On (25 min)

These are the highest-risk items we've identified. We want to open these conversations now so we can hit the ground running once the SOW is executed — not discover them after Sprint 1 is underway.

#### 4A. Governance Structure & Executive Sponsors
- **Joshua's role is confirmed in the SOW** — we know he is the designated Product Owner. What we want to understand is the full governance picture: what decisions can he make independently, and what requires escalation or executive sign-off?
- **Who are the executive sponsors?** The SOW requires monthly stakeholder meetings with Duke executive sponsors. We need to know who they are, confirm they're aware of this commitment, and understand how they want to be kept informed.
- **Why it matters:** Without a clear escalation path, decisions that need executive input will stall. Getting the sponsor names and their expected involvement locked in early protects the timeline.

#### 4B. Duke IT Introduction & API Roadmap (CRITICAL PATH)
- **Context:** Our entire MVP architecture assumes Duke will deliver: (1) Customer Validation API, (2) HPP Plan Lookup API. These were flagged as "WILL EXIST by MVP launch" in our scope docs. Service Request Creation and Enrollment APIs may NOT exist — we've built manual fallback for those.
- **HPP coverage rules — unresolved blocker:** Today, HPP coverage rules (what each plan covers, what is excluded, what triggers eligibility) are not systematized or accessible via API. Resolving this is a critical dependency for the app's core service booking flow — we cannot do a coverage check without structured data. We need Duke to tell us: Is this data in Commerce? Is it accessible via API? Who owns it on the business side?
- **What we need:**
  - Meeting scheduled with Duke IT within 2 weeks (per RFP commitment)
  - API documentation or draft specs for Commerce CRM and Dynamics integrations
  - Sandbox environment access timeline
  - Confirmation of which APIs are in Duke IT's roadmap and estimated delivery dates
  - Duke IT's security/network requirements for our AWS infrastructure to connect to their systems (VPN setup needed)
- **Ask Duke today:** Who is the Duke IT contact? Can we schedule that technical session before end of this week?
- **Risk if delayed:** We can start building with mock APIs, but real APIs are required for beta testing. A 2-month Duke IT delay cascades directly into the MVP date.

#### 4C. Ad-Hoc Service Catalog Definition (HIGH RISK)
- **Context:** The ad-hoc service catalog does not exist today. It must be built from scratch. We need 5–10 defined services with flat-rate pricing to build the MVP catalog screens and booking flows.
- **What we need:**
  - Which services will Duke launch with? (Suggestions from our scope: HVAC tune-up ~$99, water heater flush, air filter change)
  - Which 1–2 pilot markets? (Our scope suggested Orlando area)
  - Pricing approved by whom? (Product Manager level, or executive approval required?)
  - Have contractor flat-rate negotiations begun? Who is leading that on Duke's side?
- **Target deadline:** Service catalog defined by Weeks 8–12 from kickoff (SOW requirement). That is approximately May 2026.
- **Ask Duke today:** Who owns this on your side? Is there a business owner for ad-hoc services?

#### 4D. Contractor Data Export
- **Context:** Our MVP admin portal includes a Contractor Configuration Management system — we need Duke to export contractor data (name, contact, trades, zip codes served, primary/secondary designation) from the existing Commerce CRM so we can seed the app backend.
- **What we need:**
  - Duke to confirm who can pull a CSV/JSON export of current contractor records
  - Estimated 125–140 contractors across 4–5 states (NC, SC, FL, OH, IN)
  - Format: Contractor ID, name, business name, phone, email, trades, zip codes, primary/backup status
- **Target:** Export provided within first 4 weeks of kickoff
- **Ask Duke today:** Who owns contractor data in Commerce CRM? Can we schedule a call to define the export format?

#### 4E. FSM Tool Timeline
- **Context:** FSM (Field Service Management) tool is NOT in Phase 1 scope. However, when Duke selects FSM (Service Power or Service Bench), Orases needs 2–3 months to integrate. We need visibility into Duke's timeline so we can plan Phase 2.
- **Ask Duke today:** Where is Duke in the FSM vendor evaluation? Is there a target selection date?
- **Why it matters:** Our architecture is being built with abstraction layers specifically so FSM integration doesn't require rebuilding the UI. But we need to know the timing to plan Phase 2 resources.

#### 4G. Customer App Platform Decision (DECISION NEEDED BEFORE SPRINT 1)
- **Context:** The customer-facing application platform has not been finalized. The two options are:
  - **Native iOS + Android apps** (React Native or Swift/Kotlin): Better performance, push notifications, barcode scanning, offline capability, app store distribution — but requires App Store/Play Store review cycles and more complex deployment
  - **Web PWA (Progressive Web App)**: Single codebase, no app store approval required, accessible via browser — but limited access to device hardware (camera for barcode scanning, push notifications vary by platform), and no app store presence
- **Why it matters architecturally:** The choice affects frontend technology stack, push notification infrastructure, barcode scanning implementation, offline capability approach, and mobile app deployment setup (App Store/Play Store). It also affects the DevOps/security budget and timeline.
- **Key questions for Duke:**
  - Does Duke have an existing mobile app or app store developer accounts?
  - Is app store presence (Apple App Store, Google Play) important for customer acquisition and brand credibility?
  - Is barcode scanning for home inventory a must-have at MVP, or can it be deferred?
  - What is Duke's IT security posture around native app distribution vs. web-only?
- **Target:** Decision confirmed before Sprint 1 begins. This cannot be deferred — it gates all frontend architecture decisions.
- **Ask Duke today:** Who has authority to make this decision? Can we get a preliminary read today?

#### 4F. Legal & Compliance Contacts
- **Legal context:** Customer-facing terms of service, privacy policy, and contractor agreements require Duke legal review before app store submission. This process must start early — legal review can take 4–8 weeks.
- **Brand and web standards:** Already linked in the SOW appendix — we have access to both the Brand Standards document and the Web Standards guide. No action needed from Duke on this. We will review and follow them as design work begins.
- **Ask Duke today:** Who is the Duke legal contact for privacy and customer communications review? When should we initiate that process?

---

### 5. Duke SME Availability & Access (10 min)

Per the SOW, Duke is responsible for:
- Providing timely feedback and written approvals
- Giving access to SMEs for requirements validation
- Providing system access (APIs, infrastructure)
- Completing UAT and providing formal written acceptance

**Confirm:**
- Who are the key SMEs we'll be working with? (Operations, IT, Legal, Product/Business)
- What is their weekly availability during the requirements definition phase? (We need 10–15 hrs/week)
- What is the process for getting access to Duke's systems (VPN, Commerce CRM read access for data understanding, Dynamics)?

---

### 6. Immediate Next Steps — Close with Action Items (10 min)

Before leaving this meeting, confirm owners and dates for:

| Action Item | Owner | Target |
|---|---|---|
| Execute SOW #1 | Duke + Orases | Before formal kickoff |
| Identify executive sponsors by name; confirm monthly stakeholder meeting commitment | Joshua | This week |
| Identify Duke IT contact; schedule technical API session | Duke + Aksana | Within 2 weeks of SOW execution |
| Provide Commerce CRM and Dynamics API documentation (or draft) | Duke IT | TBD at tech session |
| Confirm pilot market(s) for ad-hoc service launch | Duke Business | TBD |
| Identify ad-hoc service catalog business owner | Duke | This week |
| Provide contractor data export (CSV/JSON) | Duke IT/Ops | Within 4 weeks of SOW execution |
| Identify Duke legal contact for privacy/terms review | Duke | This week |
| Confirm customer app platform decision (native vs. PWA) | Duke + Orases Tech Lead | Before Sprint 1 |
| Align on sprint status report format and frequency | Joshua + Aksana | Before Sprint 1 |
| Align on scope change documentation process (where and how) | Joshua + Aksana | Before Sprint 1 |
| Confirm preferred video meeting platform (Google Meet vs. Teams) | Joshua | This week |
| Confirm recurring meeting cadence and send calendar invites | Both | This week |

---

## What We Are NOT Doing in This Meeting

- Detailed requirements gathering (that happens in formal workshops, Weeks 1–8)
- Technical architecture decisions (those require Duke IT in the room)
- Finalizing user stories or backlog items
- Design reviews

---

## Background Context for Orases Team

**This is a pre-kickoff call — the SOW is not yet signed.** The tone should be warm, collaborative, and exploratory. We are building trust with Joshua, not running a project governance session. That said, there are real risks worth understanding coming into this conversation.

**The highest risks coming into this engagement:**

1. **SOW not yet executed** — Keep the conversation at the alignment/relationship level. Do not present anything as contractually required until the SOW is signed.

2. **Executive sponsors not yet identified** — We don't know who above Joshua is ultimately accountable for this project. Getting those names is a top priority — without them, we have no escalation path when decisions stall.

3. **MVP scope is not formally defined** — September 30, 2026 is the target date, but what counts as MVP has not been approved in writing by Duke. The PRD process is how that gets settled. Don't present September 30 as a hard commitment.

4. **Duke IT API delays** — Customer validation and HPP plan APIs must exist by MVP launch. Service Request and Enrollment APIs may not — we have manual fallback. Getting the IT meeting on the calendar is a priority.

5. **HPP coverage rules not accessible** — Coverage eligibility rules are not in a structured, API-accessible format today. This is a blocking dependency for the app's core booking flow. Needs an owner and a resolution path early.

6. **Ad-hoc catalog doesn't exist** — This is brand new. Duke needs to negotiate contractor flat rates, define scope of work, and confirm pricing. Needs to be complete by Weeks 8–12.

7. **Contractor data in Commerce CRM** — We need this to seed our contractor matching algorithm. Needs an owner on Duke's side.

8. **Customer app platform not decided** — Native iOS/Android vs. web PWA is still TBD. This gates all frontend architecture decisions and must be resolved before Sprint 1.

9. **Legal review takes time** — Start the conversation about privacy policy and ToS early, or it will block app store submission later.

---

*Document prepared for: First Client Engagement Meeting — Duke Energy x Orases*
*Prepared by: Aksana Rahouski*
*Source documents: SOW #1 V6, Discovery Findings & Updated Scope (Dec 2025), Customer App Scope, Admin Portal Scope, Contractor Portal Scope*
