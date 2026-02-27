**PRODUCT REQUIREMENTS DOCUMENT**

**Fleet Manager Mobile e-PR Application**

| Document Version | v1.1 — DRAFT (Updated) |
| :---- | :---- |
| **Date** | February 2026 |
| **Previous Version** | v1.0 — February 2026 |
| **Product Owner** | Fleet Manager — A-Sonic Logistics Pte Ltd |
| **Platform** | Progressive Web App (PWA) — iOS & Android |
| **Classification** | Confidential — Internal Use Only |

| v1.1 CHANGE SUMMARY: (1) Approval workflow confirmed — 2-tier amount-based, FM self-approve or OM approve, same rule for urgent repairs. (2) Scope tightened — office-based analytics removed from mobile; laptop remains the tool for P\&L, compliance management, and reporting. (3) Approval on mobile confirmed for both FM and OM. (4) PWA recommended over native app for 2-FM user base. (5) Backup approver remains the last critical open item. |
| :---- |

# **1\. Executive Summary**

Fleet Managers at A-Sonic Logistics spend the majority of their working day in the field — at workshops, depots, and breakdown sites. The existing Fleet Management System (FMS) requires a laptop to create Electronic Purchase Requisitions (e-PRs), which violates the company's core "e-PR First" policy and causes workshops to begin repairs without authorisation.

This PRD defines a focused mobile solution — a Progressive Web App (PWA) extending the existing FMS — that gives the Fleet Manager four specific capabilities on their smartphone: creating e-PRs, tracking e-PR status, capturing and attaching photos, and receiving push notifications on approval decisions. Everything else — analytics, P\&L, compliance management, reporting — remains on the laptop where it belongs.

| Scope discipline: The mobile app solves one problem — the FM cannot create and track e-PRs away from a laptop. It is not a mobile dashboard. It is not a reporting tool. Keeping it narrow keeps it fast, maintainable, and genuinely useful in the field. |
| :---- |

# **2\. Problem Statement**

## **2.1 The Core Problem**

The FM is physically at the breakdown site or workshop — the exact moment the e-PR needs to be created — but has no way to create one without returning to a laptop. This single gap produces a cascade of downstream problems:

* Workshop starts work on verbal instruction, no authorisation on record

* FM creates the e-PR retrospectively back at the office, breaking the audit trail

* For urgent repairs, the FM cannot leave the site, so the e-PR is delayed or skipped entirely

* FM calls the office repeatedly to check if an e-PR has been approved, wasting time for both parties

## **2.2 What Is NOT the Problem**

The FM has a laptop and uses it effectively for office-based work. The following are not mobile problems and are explicitly out of scope for this app:

* Reviewing P\&L or cost analytics — done at a desk, on the FMS web interface

* Managing compliance renewals (COE, road tax, insurance) — scheduled, office-based task

* Generating management reports — Finance and management function, web only

* Invoice matching and PO management — Finance function, web only

# **3\. Objectives & Success Metrics**

## **3.1 Objectives**

* FM can create any e-PR type entirely from their smartphone, without ever needing a laptop in the field

* FM knows the approval status of any e-PR in real time, without calling the office

* OM can approve or reject e-PRs from their phone, completing the approval chain without a laptop

* FM receives instant push notification when an e-PR is approved — can immediately instruct the workshop to proceed

* FM can capture quotation and damage photos within the e-PR creation flow, no separate steps

## **3.2 Success Metrics**

| Metric | Baseline | Target (6 months post-launch) |
| ----- | ----- | ----- |
| Retrospective e-PRs (created after work started) | \> 30% of e-PRs | \< 5% of e-PRs |
| e-PR creation time from decision to submit | 45–90 min (laptop needed) | \< 5 min on mobile |
| Approval turnaround (FM self-approve) | Hours (laptop needed) | Instant — on submission |
| Approval turnaround (OM approve) | \> 2 hours | \< 30 minutes |
| FM satisfaction score (app usability) | N/A | \>= 4.0 / 5.0 |
| Unauthorised repair spend incidents | Not tracked | Zero — all work preceded by approved e-PR |

# **4\. User Roles**

| Role | Primary Device | Mobile Actions | Laptop Actions |
| ----- | ----- | ----- | ----- |
| **Fleet Manager (FM)** | Mobile (field) \+ Laptop (office) | Create e-PRs, attach photos, track status, receive approval notifications, self-approve within threshold | P\&L dashboard, compliance management, reports, PO management, invoice matching |
| **Operations Manager (OM)** | Mobile \+ Laptop | Approve / reject e-PRs above FM threshold, add comments, receive push notifications | Full FMS access — all modules |
| **Management / C-Level** | Laptop (primary) | Backup approver only (if OM unavailable — TBD) | P\&L analytics, management reports, read-only fleet overview |

# **5\. Scope**

## **5.1 In Scope — Mobile App**

| Feature | Detail |
| ----- | ----- |
| **e-PR Creation** | All 5 maintenance types: Preventive Maintenance, Corrective (Accident), Corrective (Urgent Repair), General Breakdown, Equipment Servicing. Adaptive form — maintenance type drives conditional fields. |
| **Photo Attachment** | In-app camera capture or file picker for quotations, damage photos, fault evidence. Up to 10 photos per e-PR. |
| **Draft Save** | Auto-save every 30 seconds. FM can resume incomplete e-PRs from a drafts list. No data lost on interruption. |
| **e-PR Submission** | Submit with review confirmation screen. System-generated reference number on submission. |
| **Approval — FM Self-Approve** | e-PRs at or below the defined threshold are auto-approved on submission. No waiting, FM proceeds immediately. |
| **Approval — OM on Mobile** | e-PRs above threshold route to OM. OM reviews all fields and attachments on their phone, approves or rejects with a comment. |
| **Push Notifications** | OM notified of pending approval. FM notified of approval or rejection outcome. Urgent flag triggers priority notification. |
| **e-PR Status Tracking** | FM views all their e-PRs with real-time status. Tap to view full detail, approval history, and comments. |
| **Recall Before Approval** | FM can withdraw a submitted e-PR that is still Pending OM Approval to make corrections. |
| **Asset Quick-Search** | Search vehicle by plate number or fleet number, equipment by ID. List cached for offline use. |

## **5.2 Explicitly Out of Scope — Mobile (Laptop Only)**

| These features are available in the FMS web interface on laptop. They are intentionally excluded from the mobile app to keep the mobile experience fast and focused. |
| :---- |

* P\&L analytics and per-vehicle cost dashboards

* Compliance and renewal management (COE, road tax, insurance)

* Management and Finance reports

* PO generation and management

* Invoice matching and payment processing

* Workshop and vendor registry management

* User administration and role configuration

* Pre-use checklists (handled via TMS driver app)

* Fuel logging (handled via TMS driver app)

# **6\. Approval Workflow**

| CONFIRMED DECISION: 2-tier amount-based approval. FM self-approves at or below threshold. OM approves above threshold. Same rule applies to ALL maintenance types including urgent repairs — urgency does not bypass the amount rule. |
| :---- |

## **6.1 Approval Tiers**

| Tier | Condition | Approver | Outcome |
| :---: | ----- | ----- | ----- |
| **Tier 1** | Estimated cost at or below threshold (TBD — SGD amount to be confirmed) | FM — self-approves | Auto-approved on submission. FM proceeds immediately. |
| **Tier 2** | Estimated cost above threshold | OM — approves on mobile | Pending until OM approves or rejects. FM notified of outcome. |

## **6.2 Approval Flow — Step by Step**

| Step | Action | Tier 1 (FM Self-Approve) | Tier 2 (OM Approve) |
| ----- | ----- | ----- | ----- |
| 1 | FM completes and submits e-PR on mobile | Same | Same |
| 2 | System checks estimated cost vs threshold | At or below — auto-approved | Above — routes to OM |
| 3 | Notification sent | FM receives: "e-PR EPR-XXXX approved. You may instruct the workshop." | OM receives push notification: "e-PR EPR-XXXX awaiting your approval. Est. cost: $X." |
| 4 | Approval action | None required — instant | OM opens app, reviews all fields and photos, approves or rejects with comment |
| 5 | FM notified of outcome | Already notified at step 3 | FM receives push notification of OM decision. If rejected, FM sees comment and can edit and resubmit. |
| 6 | PO generated | System auto-generates PO on approval | Same |

## **6.3 Urgent Repair Handling**

| CONFIRMED: Urgent repairs follow the same amount-based approval rule. There is no special escalation or bypass for urgency. However, an Urgent flag on the e-PR triggers a priority push notification to the OM — distinct sound and banner — to prompt faster action. |
| :---- |

Practical implication: an urgent repair below the threshold is self-approved by the FM instantly — the FM can instruct the workshop immediately. An urgent repair above the threshold still requires OM approval, but the priority notification is designed to minimise the wait.

## **6.4 Approval SLA Recommendation**

To avoid workshop idle time on urgent high-value repairs, the following SLA is recommended for OM approval response. This is an operational policy decision, not a system constraint — the system will support configuring an escalation timeout but the threshold must be agreed by management.

| e-PR Type | Recommended OM Response SLA | If SLA Breached |
| ----- | ----- | ----- |
| Standard (non-urgent) | 4 business hours | System sends reminder notification to OM |
| Urgent flag | 30 minutes | System escalates to backup approver (TBD — see Open Item \#1) |

# **7\. Functional Requirements**

## **7.1 Authentication**

| ID | Requirement | Detail |
| ----- | ----- | ----- |
| **AUTH-01** | Single sign-on with FMS | Same credentials as the FMS web platform. No separate mobile accounts. |
| **AUTH-02** | Biometric login | Face ID / fingerprint after initial login. Falls back to PIN. |
| **AUTH-03** | Session timeout | 8-hour inactivity timeout. Draft e-PRs preserved through expiry. |
| **AUTH-04** | Role-based UI | App shows only screens relevant to the logged-in user's role. FM sees creation \+ tracking. OM sees approval queue \+ creation. |

## **7.2 e-PR Creation**

### **Maintenance Types & Conditional Fields**

| Maintenance Type | Conditional Fields (in addition to core fields) |
| ----- | ----- |
| **Preventive Maintenance** | Current odometer reading, next service due mileage, PM schedule reference |
| **Corrective — Accident** | Incident report number (link or create new), damage description, damage photos (camera), insurance claim flag |
| **Corrective — Urgent Repair** | Breakdown location (GPS auto-fill or manual override), estimated recovery time, replacement vehicle required (Y/N) |
| **General Breakdown** | Fault description, fault photos (camera) |
| **Equipment Servicing** | Equipment type, serial number, last service date |

### **Core Fields (All Types)**

| Field | Detail | Input Type |
| ----- | ----- | ----- |
| **Asset** | Search by plate or fleet number. Shows current status. Recent assets surfaced first. | Searchable list, cached offline |
| **Maintenance Type** | First field — drives all conditional logic. | Large icon-based selector |
| **Workshop / Vendor** | Filtered to approved vendors for the selected maintenance type. | Searchable dropdown |
| **Scope of Work** | Description of work. Pre-populated templates available per type. | Multi-line text \+ templates |
| **Estimated Cost (SGD)** | Drives approval tier routing. System displays which tier will apply as FM types the amount. | Numeric with live tier indicator |
| **Quotation Attachment** | Photo or PDF of quotation. Mandatory for costs above $500 (configurable). | Camera or file picker |
| **Urgency Flag** | Marks e-PR urgent — triggers priority push notification to approver. Does not bypass approval rule. | Toggle switch |
| **Notes** | Free-text. Optional. Voice-to-text supported. | Multi-line, optional |

### **Live Approval Tier Indicator**

As the FM enters the Estimated Cost, the form displays a real-time indicator showing which approval tier applies. This prevents the FM being surprised by an OM-routed e-PR when they expected instant approval.

| Amount Entered | Indicator Shown |
| ----- | :---: |
| At or below threshold | **Self-approve — will be approved instantly on submission** |
| Above threshold | **Requires OM approval — will be sent to OM** |

## **7.3 Photo Capture & Attachment**

| ID | Requirement | Detail |
| ----- | ----- | ----- |
| **PHOTO-01** | In-app camera | Camera launches within the app flow. No switching to native camera app. |
| **PHOTO-02** | Up to 10 photos per e-PR | Thumbnail grid shown in form. Individual photos deletable before submission. |
| **PHOTO-03** | Auto-compression | Images compressed to max 2MB before upload. Quality prompt if image appears blurry. |
| **PHOTO-04** | PDF upload | FM can attach emailed quotations saved to phone as PDF. |
| **PHOTO-05** | Readability prompt | After capturing a quotation photo, app prompts: "Is the quotation number and amount clearly visible?" FM confirms before continuing. |

## **7.4 Draft Save**

| ID | Requirement | Detail |
| ----- | ----- | ----- |
| **DRAFT-01** | Auto-save every 30 seconds | No data lost on phone call interruption, app backgrounding, or accidental close. |
| **DRAFT-02** | Draft list | FM can see all saved drafts, resume, or delete. Drafts show asset name and maintenance type. |
| **DRAFT-03** | Offline draft creation | FM can complete a draft while offline. Queued for submission when connectivity resumes. |
| **DRAFT-04** | Offline asset cache | Vehicle and equipment list cached locally (24-hour TTL). Asset selection works without connectivity. |
| **DRAFT-05** | Sync-on-reconnect notification | FM notified when a queued e-PR has been successfully submitted after connectivity returns. |

## **7.5 e-PR Status Tracking**

| ID | Requirement | Detail |
| ----- | ----- | ----- |
| **LIST-01** | My e-PRs list | All e-PRs raised by the FM, most recent first. Colour-coded status badges. |
| **LIST-02** | Filter and search | Filter by status, type, asset, date. Search by e-PR number or plate. |
| **LIST-03** | e-PR detail view | Full read-only view: all fields, attachments, approval history with timestamps and OM comments. |
| **LIST-04** | OM approval queue | OM sees a Pending Approvals tab with badge count showing how many e-PRs need action. |
| **LIST-05** | Recall function | FM can withdraw a Pending Approval e-PR to edit and resubmit. Not available once OM has acted. |

## **7.6 Push Notifications**

| ID | Trigger | Recipient | Message |
| ----- | ----- | ----- | ----- |
| **NOTIF-01** | e-PR submitted — above threshold | OM | \[Asset\] — EPR-XXXX awaiting approval. Est. cost: $X. Tap to review. |
| **NOTIF-02** | e-PR submitted — urgent flag | OM (priority) | URGENT — EPR-XXXX needs immediate approval. \[Asset\] breakdown in progress. |
| **NOTIF-03** | e-PR approved (auto or OM) | FM | EPR-XXXX APPROVED. You may instruct the workshop to proceed. |
| **NOTIF-04** | e-PR rejected by OM | FM | EPR-XXXX REJECTED. Reason: \[comment\]. Tap to edit and resubmit. |
| **NOTIF-05** | Offline e-PR synced and submitted | FM | Your queued e-PR has been submitted. Reference: EPR-XXXX. |
| **NOTIF-06** | OM SLA breach — urgent e-PR unactioned \> 30 min | Backup approver (TBD) | URGENT — EPR-XXXX has not been actioned. Escalated to you for approval. |

# **8\. e-PR Status Lifecycle**

| From | To | Trigger |
| ----- | :---: | ----- |
| — | **Draft** | FM starts a new e-PR (auto-save begins) |
| **Draft** | **Pending OM Approval** | FM submits — estimated cost above threshold |
| **Draft** | **Approved** | FM submits — estimated cost at or below threshold (auto-approve) |
| **Pending OM Approval** | **Draft** | FM recalls the e-PR before OM acts |
| **Pending OM Approval** | **Approved** | OM approves on mobile |
| **Pending OM Approval** | **Rejected** | OM rejects with mandatory comment |
| **Rejected** | **Pending OM Approval** | FM edits and resubmits |
| **Approved** | **PO Issued** | FMS auto-generates PO (web function — no mobile action needed) |

# **9\. Technical Approach**

| DECISION: Progressive Web App (PWA) over native iOS/Android app. Rationale: only 2 Fleet Managers, no App Store deployment overhead, single codebase shared with the FMS web platform, full camera and GPS access via browser APIs, push notifications supported on iOS 16.4+ and all Android. |
| :---- |

## **9.1 Why PWA**

* Single codebase — the PWA is the mobile-optimised view of the existing FMS web application, not a separate product

* No App Store — no Apple/Google review cycles, no certificate renewals, no deployment pipeline for 2 users

* FM adds the app to their home screen — looks and feels like a native app with offline support

* Drivers are unaffected — they stay on the TMS app for fuel logging and checklists

* OM approves via the same PWA or via the standard FMS web interface on laptop — same data, same approval engine

## **9.2 Recommended Stack**

| Layer | Recommendation | Rationale |
| ----- | ----- | ----- |
| **Frontend Framework** | React (Next.js) — align with TMS frontend if already decided | Mobile-first rendering, PWA support built-in via next-pwa |
| **Styling** | Tailwind CSS — mobile-first breakpoints | Fast to build large-tap-target, high-contrast field UI |
| **PWA Layer** | Service Worker \+ Web App Manifest | Offline draft caching (IndexedDB), home screen install, push notifications |
| **Offline Storage** | IndexedDB | Draft e-PRs and asset cache stored locally on device |
| **Push Notifications** | Web Push API — FCM for Android, APNs for iOS | Supported iOS 16.4+, all modern Android |
| **Camera / GPS** | Native browser APIs (getUserMedia, Geolocation) | No native SDK needed. Works in PWA on both platforms. |
| **Backend / API** | Existing FMS REST API — no new backend | Mobile app is a frontend client only. Same API as web. |
| **Auth** | Existing FMS SSO — JWT stored in secure keychain | No new auth system. Tokens never in localStorage. |

# **10\. Non-Functional Requirements**

| Category | Requirement | Target |
| ----- | ----- | ----- |
| **Performance** | App load (cold start on 4G) | \< 3 seconds |
| **Performance** | e-PR form load | \< 2 seconds on 4G |
| **Performance** | Photo upload (2MB, 4G) | \< 10 seconds |
| **Security** | Data in transit | TLS 1.3 for all API calls |
| **Security** | Offline data at rest | AES-256 for locally cached drafts and asset data |
| **Security** | Auth token storage | Secure keychain (iOS) / keystore (Android). Never localStorage. |
| **Usability** | One-hand operation | Core actions reachable with thumb in bottom 60% of screen |
| **Usability** | Touch targets | Minimum 44×44pt. Works in direct sunlight (high contrast). |
| **Compatibility** | iOS | iOS 16.4+ (required for PWA push notifications) |
| **Compatibility** | Android | Android 10 (API 29\) and above |
| **Availability** | API uptime | \>= 99.5% during 07:00–22:00 SGT |
| **Locale** | Language, currency, date | English (SG), SGD, DD/MM/YYYY |

# **11\. Open Items — Decisions Required Before Development**

| Item \#1 is the most critical. Until the backup approver is defined, the system cannot handle OM unavailability — which will happen and will cause an operational crisis the first time it does. |
| :---- |

| \# | Open Item | Decision Owner | Target Date |
| ----- | ----- | ----- | ----- |
| **1** | **CRITICAL — Backup approver when OM is unavailable.** If the OM is on leave, unreachable, or does not respond within the SLA, who approves high-value e-PRs? Options: (A) Management auto-escalated by system, (B) FM flags "approver unavailable" and system routes to Management, (C) OM nominates a deputy before going on leave. Without this decision, a high-value urgent repair will be stuck with no approval path. | Fleet Manager \+ Management | **Before development starts** |
| 2 | Approval threshold amount (SGD). What is the exact dollar amount below which the FM self-approves? Suggested starting point: SGD 500, but must be confirmed by management. | Fleet Manager \+ Management | Week 1 |
| 3 | FMS API readiness. Does the existing FMS REST API support all required mobile endpoints, or do new endpoints need to be built? Particularly: e-PR CRUD, file upload, push notification token registration. | FMS Development Team | Week 2 |
| 4 | Push notification infrastructure. Is FCM/APNs already integrated in the FMS notification service? If not, this needs to be built as part of the mobile project. | FMS Development Team | Week 2 |
| 5 | e-PR First enforcement process. The mobile app removes the friction excuse but cannot enforce behaviour. What is the consequence for a workshop that starts work without an e-PR number? Finance must be aligned to block payment for unmatched invoices. | FM \+ Finance \+ Management | Week 1 |

# **12\. Release Plan**

| Phase | Timeline | Deliverables | Exit Criteria |
| ----- | ----- | ----- | ----- |
| **Phase 0 Discovery** | Weeks 1–2 | FM field shadowing, wireframes, API readiness confirmed, all open items resolved | Wireframes signed off. Open items \#1–5 resolved. |
| **Phase 1 Core e-PR** | Weeks 3–10 | Auth (SSO \+ biometric), all 5 e-PR types, photo capture, draft save, submission, auto-approval (Tier 1), e-PR list and status tracking | FM can create and self-approve all 5 e-PR types end-to-end on iOS and Android |
| **Phase 2 OM Approval** | Weeks 11–14 | Tier 2 routing to OM, OM approval/rejection on mobile, push notifications, recall function, backup approver escalation | Full approval chain completable by FM and OM without a laptop |
| **Phase 3 Offline** | Weeks 15–18 | Offline draft creation, asset cache, offline photo queue, sync-on-reconnect | e-PR created and submitted successfully with zero connectivity |
| **Phase 4 Pilot & Rollout** | Weeks 19–22 | 2-week FM pilot, UAT, feedback, production release, FM and OM onboarding | Zero critical bugs. FM satisfaction \>= 4.0/5.0. Retrospective e-PR rate \< 10%. |

*— End of Document — v1.1 —*