# Accident Record App (RAF-Aligned) — Product Blueprint

## 0) Short Answer: Is your simplified idea acceptable?

Yes — it is absolutely acceptable and strategically strong.

Your direction is clear:

- a downloadable app
- public users self-report accidents with simple forms
- upload scene images
- capture GPS instantly
- create a permanent record usable later (legal/insurance)

That is a practical MVP and a credible business foundation.

---

## 1) Product Goal (Plain Language)

Build a **mobile-first accident evidence app** that helps any person:

1. report an accident quickly,
2. capture trustworthy proof at the scene,
3. store it safely for future legal/insurance use,
4. share it with qualified legal/tow/commercial partners under consent.

---


## 1A) What Are the Possibilities Now? (Decision Map)

Right now you have six realistic paths. You can run one, or combine them:

1. **Simple Public MVP (Fastest)**
   - self-report form + photos + GPS + weather + PDF
   - best for proving adoption quickly
2. **Legal-Ready Evidence Platform**
   - adds stronger audit trail, consent versioning, and tamper checks
   - best for high trust with attorneys and insurers
3. **Partner Marketplace Model**
   - route consented high-quality cases to law firms and tow operators
   - best for revenue growth
4. **White-Label SaaS**
   - same platform sold to multiple firms with tenant branding
   - best for B2B scale
5. **Hybrid Consumer + Enterprise**
   - public app + firm dashboard + partner onboarding
   - best for balanced growth and resilience
6. **Geo-Intelligence Expansion**
   - accident hotspot targeting, dynamic dispatch, predictive alerts
   - best for long-term competitive advantage

### Recommended Sequence

- **Now (0-3 months):** Path 1
- **Next (3-6 months):** Path 2 + Path 3
- **Scale (6-12 months):** Path 4 + selective Path 6

This gives you fast launch, then monetization, then durable scale.

---

## 2) UI/UX Flow (Screen by Screen)

## Screen 1 — Splash / App Load

**Purpose:** brand + warm start.

- App logo/tenant logo
- “Preparing secure capture...”
- preload config, permissions state, offline cache

---

## Screen 2 — Welcome / Value Proposition

**Purpose:** explain why user should continue.

- “Record your accident in minutes.”
- “Secure evidence. Permanent record. Easy sharing.”
- CTAs:
  - `Report Accident Now` (Primary)
  - `Learn More` (Secondary)

---

## Screen 3 — Consent & Legal Basis (Required)

**Purpose:** explicit legal consent before capture.

Sections:

- privacy notice summary
- terms for storing personal data, location, media, weather snapshot
- optional marketing consent toggle
- optional partner-sharing consent toggle (law firms / towing)

Actions:

- `I Agree and Continue`
- `Decline`

Store:

- consent version
- timestamp
- GPS availability state
- device/session id

---

## Screen 4 — Permissions Gate

**Purpose:** request required hardware permissions.

Permissions:

- Location (foreground, optionally background)
- Camera
- Photos/Media library
- Notifications

UX:

- one permission card at a time
- explain “why this matters” in plain words

---

## Screen 5 — Home Dashboard

**Purpose:** central navigation.

Cards:

- `Start New Accident Report`
- `My Reports`
- `Upload More Evidence`
- `Emergency Contacts`
- `Help`

Top area:

- status chip: Online/Offline
- quick sync button

---

## Screen 6 — Incident Start (Button Push Trigger)

**Critical requirement from you:** on first button press, GPS and weather must be captured immediately.

Flow when user taps `Start New Accident Report`:

1. Create local draft report id.
2. Capture GPS coordinates + accuracy + timestamp.
3. Call weather API by coordinates and store snapshot (temp, rain, visibility, wind).
4. Open camera quick-capture mode.

Show confirmation:

- “Location locked”
- “Weather snapshot saved”

---

## Screen 7 — Guided Form (Stepper)

Simple self-complete flow:

1. **Accident basics** (date/time auto + editable)
2. **Location verify** (map pin and address)
3. **Vehicles involved**
4. **Injuries / severity**
5. **Witnesses (optional)**
6. **Tow truck details (if present)**
7. **Police/case number (optional now, add later)**

Design:

- progress bar
- save & exit
- large touch targets
- plain-language helper text

---

## Screen 8 — Camera + Evidence Upload

Evidence blocks:

- scene photos
- vehicle damage photos
- license disk / plate photos
- voice note (optional)
- document upload (if available)

Metadata auto-attach per file:

- GPS
- timestamp
- device id hash

---

## Screen 9 — Review & Submit

- full summary preview
- missing fields warnings
- consent reminder for partner sharing
- `Submit Report`
- `Save Offline` (if no network)

---

## Screen 10 — Report Submitted

- permanent reference number
- share/export options
- “View Full Report” CTA

---

## Screen 11 — View Full Report (Editable)

Must support:

- timeline of captured events
- media gallery
- map snapshot
- weather snapshot
- edit allowed fields with audit trail
- regenerate PDF after edits

---

## Screen 12 — My Reports

- list of all reports
- sync status (local-only / synced)
- filters: draft, submitted, shared

---

## Screen 13 — Onboarding to Commercial Partnering

For firms/tow operators/pro partners:

- organization registration
- verification docs
- agreement acceptance (commercial buy-in)
- payout / billing profile setup

---

## Screen 14 — Offer / Match Screen (Optional Premium)

If user opted in:

- show partner offers (law firm / tow)
- explain fee model transparently
- `Accept`, `Decline`, `Contact Later`

---

## 3) Wireframe Visuals (Low-Fidelity Text Sketch)

## 3.1 Welcome

```text
+----------------------------------+
| Logo                             |
|                                  |
| Record your accident in minutes  |
| Secure evidence. Permanent file. |
|                                  |
| [ Report Accident Now ]          |
| [ Learn More ]                   |
+----------------------------------+
```

## 3.2 Consent

```text
+----------------------------------+
| Consent & Privacy                |
| [ ] I agree to data storage      |
| [ ] I agree to location capture  |
| [ ] Share with partners (opt-in) |
|                                  |
| [ I Agree and Continue ]         |
| [ Decline ]                      |
+----------------------------------+
```

## 3.3 Guided Capture

```text
+----------------------------------+
| Step 2/7: Location               |
| [ Map Preview ]                  |
| Accuracy: 8m                     |
| Weather: Light rain, 17C         |
|                                  |
| [ Back ]            [ Next ]     |
+----------------------------------+
```

## 3.4 Full Report

```text
+----------------------------------+
| REF: RAF-2026-000123             |
| Status: Submitted                |
|                                  |
| Timeline | Media | Map | Weather |
|                                  |
| [ Edit Report ] [ Export PDF ]   |
+----------------------------------+
```

---

## 4) Figma Structure (Recommended)

Create one Figma file with pages:

1. `00_Foundations`
   - colors, type scale, spacing, icons
2. `01_Components`
   - buttons, inputs, cards, steppers, toasts, permission cards
3. `02_UserApp_Mobile`
   - all screens above
4. `03_PartnerPortal_Web` (future)
5. `04_AdminWorkbench_Web` (future)
6. `05_Prototypes`
   - happy path, offline path, error path

Component naming:

- `Button/Primary`
- `Form/TextInput/Error`
- `Card/ReportSummary`
- `Map/LocationLock`

---

## 5) React Native Component Mapping

## 5.1 Suggested Folder Structure

```text
src/
  app/
  screens/
    WelcomeScreen.tsx
    ConsentScreen.tsx
    PermissionScreen.tsx
    HomeScreen.tsx
    IncidentStartScreen.tsx
    GuidedFormScreen.tsx
    EvidenceCaptureScreen.tsx
    ReviewSubmitScreen.tsx
    ReportDetailScreen.tsx
    ReportsListScreen.tsx
    PartnerOnboardingScreen.tsx
  components/
    buttons/
    forms/
    camera/
    location/
    weather/
    reports/
  services/
    gpsService.ts
    weatherService.ts
    cameraService.ts
    storageService.ts
    syncService.ts
    pdfService.ts
    pricingService.ts
  store/
    reportStore.ts
    consentStore.ts
    tenantStore.ts
```

## 5.2 Key Components

- `StartReportButton`
- `LocationLockBanner`
- `WeatherSnapshotCard`
- `CameraCapturePanel`
- `OfflineSyncStatus`
- `ConsentBlock`
- `PartnerOfferCard`
- `DynamicPriceBreakdown`

---

## 6) Core Functional Requirements (Now)

## A) GPS + Weather on First Button Press

When `StartReportButton` is tapped:

- must capture GPS immediately
- must fetch weather immediately
- must persist both into local draft report
- must show success/failure state to user

## B) Camera + GPS Properly Plugged In

Each image should save:

- file uri
- capture timestamp
- GPS at capture
- hash for integrity check (future legal chain)

## C) Local Storage (Offline-First)

Use local DB (SQLite/Realm) for:

- drafts
- media index
- sync queue
- consent records

## D) PDF Generation

Generate user-friendly PDF report with:

- report details
- image thumbnails
- map + coordinates
- weather conditions
- consent and submission timestamps

## E) Cloud Storage Completion

Store media and PDFs in managed object storage with:

- tenant-aware paths
- signed upload URLs
- lifecycle rules

## F) Full Report Edit View

Allow edits only to safe fields, keep audit trail:

- what changed
- who changed
- when changed

---

## 7) Missing Business Component You Mentioned (High-Value Case Routing)

You are correct: large law firms and tow operators pay for high-quality, valid cases.

Implement a **case marketplace / lead-routing layer**:

- score each case quality + severity + documentation completeness
- match eligible cases to subscribed firms/operators
- enforce consent and conflict rules
- track acceptance and outcomes

### Fair Handling Model

- user consent first (always)
- transparent partner disclosure
- no exclusive lock-in without clear user approval
- audit every share event

---

## 8) White-Label + Multi-Tenant Architecture

To make this platform white-labeled and multi-tenant:

## 8.1 Tenant Model

Core entities include `tenant_id`:

- users
- reports
- media
- pricing rules
- partner contracts

## 8.2 Branding

Per tenant config:

- app name
- logo
- color theme
- legal text
- support contacts

## 8.3 Access Isolation

- row-level security / strict tenant scoping
- tenant-specific storage buckets/prefixes
- per-tenant API keys and webhook secrets

## 8.4 Commercial Agreements

Onboarding includes:

- legal contract acceptance
- billing plan selection
- payout terms
- SLA tier

---

## 9) Pricing Model Simulations (South Africa-Oriented)

## 9.1 Simple Commercial Options

1. **Per active case fee**
2. **Subscription + usage**
3. **Success fee on converted matters**

## 9.2 Illustrative SA Scenario (Example Only)

- Monthly reports captured: 2,000
- Qualified serious cases: 18% = 360
- Partner acceptance rate: 45% = 162
- Platform fee per accepted qualified case: R450
- Monthly case-routing revenue: R72,900

This is only a planning example — calibrate with real partner data.

## 9.3 Dynamic Pricing Engine per Case Value

Price can be adjusted using weighted inputs:

- severity score
- evidence completeness
- response speed
- geo risk zone
- partner demand level

Pseudo formula:

`price = base_rate * severity_factor * completeness_factor * demand_factor`

---

## 10) Consent Screen (Detailed Requirements)

Must include:

- clear purpose of data collection
- mandatory vs optional data
- partner-sharing opt-in separated from core usage consent
- withdrawal mechanism
- versioned legal text

Store immutable consent events for legal defensibility.

---

## 11) Marketing Campaign (Adoption + Quality)

Your goals:

1. app downloads,
2. deep usage,
3. user trust,
4. high-quality case intake,
5. activation in high accident-probability zones.

## 11.1 Campaign Strategy

### Campaign A — “Be Ready Before an Accident”

- target: general drivers and commuters
- message: “Protect yourself with a permanent digital record.”
- channels: Meta, TikTok, radio snippets, commuter influencers

### Campaign B — “At-Scene Capture in 3 Minutes”

- target: users likely to witness/report accidents
- message: speed + legal readiness
- channels: YouTube shorts, WhatsApp share creatives, roadside QR posters

### Campaign C — “Trusted Legal Follow-Through”

- target: users unsure about legal process
- message: confidence and transparency
- channels: testimonial creatives, explainer reels

## 11.2 Geo-Activation (High Accident Probability)

- run location-targeted campaigns around high-incident corridors
- partner with tow networks, petrol stations, taxi associations
- deploy QR signage at strategic points
- increase ad bid multipliers in high-risk geos

## 11.3 Activation Funnel KPIs

- CPI (cost per install)
- onboarding completion rate
- consent completion rate
- first report creation rate
- evidence completeness score
- partner conversion rate

---

## 12) Delivery Plan: “Continue with A / Proceed with B”

## Track A (Product Build)

1. consent + permissions + incident start
2. GPS + weather + camera metadata capture
3. guided forms + offline storage
4. submit + cloud sync + PDF
5. full report edit screen + audit

## Track B (Commercial + Scale)

1. partner onboarding + commercial agreements
2. multi-tenant white-label controls
3. dynamic pricing engine
4. case routing marketplace
5. geo-marketing operations dashboard

Run A and B in parallel with shared compliance governance.

---

## 13) Final Recommendation

Stop broad solution design here and execute this scope:

- keep the first version simple (forms + images + trusted capture)
- ensure consent, GPS, weather, and timestamp integrity from first tap
- build offline-first reliability and legal-grade record outputs
- add white-label multi-tenant design early to avoid rework
- monetize through transparent, consent-based partner routing

This is a realistic, comprehensible, and commercially viable path.
