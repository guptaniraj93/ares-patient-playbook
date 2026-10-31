# Ares Patient Operations Playbook

Interactive, **draft** operating SOP for patient intake, physician consultations, CCM/RPM coordination, daily CRM queues, reminders, exception handling, and the billing lifecycle from **Step 0 through payment**.

## Open the playbook

Open `index.html` in a browser, or visit the repository's GitHub Pages deployment if enabled. No dependencies or real patient data are needed.

### Sections

- **Patient Journey:** live verified Original Medicare transfer → EHR intake → 20-minute physician consultation using interim Google Meet video-first / documented telephone fallback → CCM consent/enrollment → optional separate RPM discussion → monthly care and follow-up.
- **Step 0 → Payment:** nine interactive stages from Grove Health P.A. infrastructure/credentialing through claims submission, ERA posting, denials, and compliance audits. Hover to see a summary, click to inspect handoffs and evidence.
- **Daily CRM Queue:** proactive operational tasks and escalations.
- **SMS Library:** administrative message drafts; no initial cold outreach, and welcome only after CCM enrollment with appropriate messaging consent.
- **Exception Playbooks, Systems & Roles, Open Decisions.**

## Confirmed Ares operating rules

1. The lead-transfer representative sends **Medicare number, first name, last name and address**, having already verified **Original Medicare**, and transfers the live call.
2. The transfer representative creates the Practice Fusion patient record before the handoff. The physician first confirms Medicare ID.
3. The initial physician intake has an Ares operational **20-minute requirement**. **Google Meet is the interim video-first platform**, subject to HIPAA configuration review. Use audio-only phone only when the patient explicitly cannot join video and record the patient's response and reason under approved policy. This does **not** by itself establish Medicare audio-only telehealth reimbursement.
4. **CCM is offered first.** RPM is an optional subsequent enrollment call with separate clinical order and patient consent.
5. **No patient portal** is used in the Ares operating model, even if a vendor offers one.
6. Internal transfer representatives initiate physician follow-up visits, using the same video-first script.
7. CRM coordinates task ownership; Practice Fusion stores clinical records; ChronicCareIQ supports RPM/device data and potentially time/billing evidence subject to integration validation; Aircall is the phone/SMS channel.
8. **Welcome SMS only follows confirmed CCM enrollment** and appropriate messaging consent. No pre-enrollment initial-call SMS.
9. Ares aims to complete core monthly CCM activity by **day 15**, but services and Medicare-qualifying time can continue to the end of the relevant period.

## Grove billing path from the newly supplied document

The document **“CCM + RPM Workflow — Step 0 to Payment” (30 Oct 2026)** identifies **Grove Health P.A.** as the billing entity and describes credentialing, practitioner supervision, program eligibility, consent and plans, CCM monthly services, optional RPM, an APCM alternative, 837P claim submission via SPOT/clearinghouse, 835 ERA posting, denial management, and audit controls.

Treat this as a **source-proposed billing model requiring operational and credentialing sign-off**, not proof that every enrollment, Medicare rule, payer contract, NPI, claims route or telehealth visit is verified.

## Call Scripts tab

The **Call Scripts** tab contains 12 draft, searchable, role-filterable voice-call guides from live lead transfer through physician intake, CCM-first consent, monthly care, separate optional RPM enrollment, device assistance, clinical escalation and disenrollment. Each includes suggested dialogue, record requirements, exception handling and a copy control. Scripts are not connected to Aircall and have not received clinical or compliance approval.

## Tool ownership in the Workflow tab

The **Workflow** tab is the active section; the other tabs are intentionally blank. Tool mapping is a proposed integration/ownership model, not a claim that integrations are live.

| Tool | Role | Primary workflow stages |
| --- | --- | --- |
| CRM (not selected) | Operational patient status, daily queue, task routing, enrollment and follow-up automation | 1–5, 7–8 |
| Aircall | Live lead transfers, calls, follow-up transfers, approved SMS | 1–5 |
| Google Meet (interim) | Video-first physician visits, subject to covered Workspace configuration and executed BAA; phone fallback when documented | 2 and follow-ups |
| Fireflies.ai (conditional) | Physician-reviewed meeting transcript and draft notes only after verified HIPAA plan, Private Storage, BAA, recording/consent and retention controls | 2 and follow-ups |
| Doxy.me (vendor review) | Future option for lower-friction phone-to-video workflow; not current default | 2 and follow-ups |
| Practice Fusion | Clinical source of truth: patient demographics, Medicare ID, encounters, diagnoses, care plan and consent | 1–7 |
| ChronicCareIQ | RPM readings and device status; candidate source of clinical minutes subject to vendor/billing validation | 4–5, 7 |
| Grove billing, SPOT / clearinghouse | Claim preparation/submission, payments, ERA, denials and reconciliation | 0, 6–8 |

**Proposed interfaces:** Aircall → CRM (calls and transfers); Practice Fusion → CRM (confirmed CCM enrollment and welcome-message trigger); CCIQ → CRM (monitoring tasks); CCIQ → billing (validated time and RPM evidence); billing → CRM (claim/denial task visibility). Confirm API availability, HIPAA/BAA and record ownership before implementing.

## Interim physician video + transcription workflow (31 Oct 2026)

**Interim platform decision:** Aircall remains the voice, call-transfer, phone fallback and SMS service. Use Google Meet for physician video encounters **only after** verifying the participating Google Workspace account is covered by an executed Google BAA, Meet is an in-scope service, and access/security controls are configured. Doxy.me remains under UX evaluation, not the interim default.

**Fireflies.ai is conditional, not automatically approved:** Before enabling it on real patient visits, confirm the applicable Enterprise HIPAA offering, Private Storage, an executed BAA, the recording/transcription notice and consent policy, access/retention controls, and relevant workflow review. Until these gates are complete, **do not join, record, transcribe, upload or share patient encounters using Fireflies**. Clinicians must review any future AI-generated notes before entering the final clinical record in Practice Fusion.

1. Lead-transfer representative creates the Practice Fusion patient record and transfers the ready patient live through Aircall. No pre-enrollment initial SMS.
2. Physician first verifies the Medicare ID, then explicitly asks whether the patient can join video.
3. If yes, use an approved Google Meet link and assist the patient in joining; if the patient explicitly cannot use video, document that response and continue by Aircall phone under approved policy.
4. Physician performs the clinical intake (Ares-required 20 minutes for the initial intake) or follow-up. The same video-first script applies to internal-transfer-initiated follow-up visits; **follow-up duration remains an open decision**.
5. Fireflies may capture meeting notes **only after all compliance and recording gates are approved**; otherwise, the physician documents directly.
6. Physician reviews and finalizes relevant notes in Practice Fusion, and the CRM tracks completed and outstanding follow-up tasks.
7. The welcome SMS is triggered **only after confirmed CCM enrollment and appropriate SMS consent**. Optional RPM is offered on a later, separate call.

### Vendor UX review — conversations not yet completed

- **Doxy.me:** Test one-tap join for elderly patients, browser/device access, SMS join links, waiting rooms, accessibility, identity and consent, handoff from Aircall, disconnect recovery and integration feasibility.
- **Aircall:** Investigate warm transfer into physician queue, call failure/disconnect retry, click-to-SMS Meet links, call-to-video handoff, CRM events, compliant logs and patient support workflows.
- Record vendor responses and decisions in GitHub issues. No vendor has been contacted by this repository update.

### Privacy and hosting

The playbook is a static SOP reference with no live clinical integrations. **Do not commit patient PHI, call recordings, Medicare numbers or production credentials.** GitHub Pages sites should be treated as publicly accessible unless a separately verified restricted-access configuration is in place. Repository privacy and published-site privacy are different concerns.

## Key unresolved decisions

- Does ChronicCareIQ offer a patient portal (notwithstanding the Ares decision not to use one)?
- On lead-transfer drop-off, should the incomplete EHR chart remain, and what CRM status is assigned?
- What exact CRM status and event identifies a successfully enrolled patient and fires the welcome message?
- Must physician encounters have video recordings, or are consented audio recordings sufficient?
- How does Grove demonstrate an established patient/practitioner relationship for transferred leads?
- Which audio-only initiating and follow-up E/M visits are billable under current Medicare requirements?
- Has Grove billing enrollment, practitioner reassignment, payer routing and SPOT/clearinghouse setup been validated?
- Who owns coding, claim review, coinsurance, denials and audits?

## Important boundaries

This is a **static process reference**, not connected to CRM, EHR, telephony, clinical triage, billing or payment systems. Do not enter protected health information (PHI). Any scripts, thresholds, time accounting, Medicare code rules and legal statements require approval from Grove's clinical, billing and compliance leads before use in production.

## Deploy to Surge

A GitHub Actions workflow at `.github/workflows/deploy-surge.yml` deploys `index.html` to Surge on pushes to `main` (and through manual **Run workflow**). No deployment occurs until credentials and a domain are configured.

1. In the repository, open **Settings → Secrets and variables → Actions**.
2. Create repository **secrets** `SURGE_TOKEN` (Surge authentication token) and `SURGE_LOGIN` (account email). Get the token locally by authenticating with Surge CLI and following Surge's token instructions; do not commit credentials.
3. Create repository **variable** `SURGE_DOMAIN` with the intended full Surge hostname, such as `ares-patient-playbook.surge.sh` (only if available/owned).
4. Open **Actions → Deploy Ares Playbook to Surge → Run workflow** or push a change to `index.html`. Inspect the workflow run for the actual published URL or any authentication/domain errors.

Only public-safe reference material should be published; do not add real patient PHI to the static site.
