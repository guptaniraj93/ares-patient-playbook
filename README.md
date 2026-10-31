# Ares Patient Operations Playbook

Interactive, **draft** operating SOP for patient intake, physician consultations, CCM/RPM coordination, daily CRM queues, reminders, exception handling, and the billing lifecycle from **Step 0 through payment**.

## Open the playbook

Open `index.html` in a browser, or visit the repository's GitHub Pages deployment if enabled. No dependencies or real patient data are needed.

### Sections

- **Patient Journey:** live verified Original Medicare transfer → EHR intake → 20-minute physician consultation with video-first / consent-documented telephone fallback → CCM consent/enrollment → optional separate RPM discussion → monthly care and follow-up.
- **Step 0 → Payment:** nine interactive stages from Grove Health P.A. infrastructure/credentialing through claims submission, ERA posting, denials, and compliance audits. Hover to see a summary, click to inspect handoffs and evidence.
- **Daily CRM Queue:** proactive operational tasks and escalations.
- **SMS Library:** administrative message drafts; no initial cold outreach, and welcome only after CCM enrollment with appropriate messaging consent.
- **Exception Playbooks, Systems & Roles, Open Decisions.**

## Confirmed Ares operating rules

1. The lead-transfer representative sends **Medicare number, first name, last name and address**, having already verified **Original Medicare**, and transfers the live call.
2. The transfer representative creates the Practice Fusion patient record before the handoff. The physician first confirms Medicare ID.
3. The initial physician intake has an Ares operational **20-minute requirement**. **Doxy.me video is the default**; use audio-only phone only when the patient explicitly cannot join video and record consent and reason under approved policy. This does **not** by itself establish Medicare audio-only telehealth reimbursement.
4. **CCM is offered first.** RPM is an optional subsequent enrollment call with separate clinical order and patient consent.
5. **No patient portal** is used in the Ares operating model, even if a vendor offers one.
6. Internal transfer representatives initiate physician follow-up visits, using the same video-first script.
7. CRM coordinates task ownership; Practice Fusion stores clinical records; ChronicCareIQ supports RPM/device data and potentially time/billing evidence subject to integration validation; Aircall is the phone/SMS channel.
8. **Welcome SMS only follows confirmed CCM enrollment** and appropriate messaging consent. No pre-enrollment initial-call SMS.
9. Ares aims to complete core monthly CCM activity by **day 15**, but services and Medicare-qualifying time can continue to the end of the relevant period.

## Grove billing path from the newly supplied document

The document **“CCM + RPM Workflow — Step 0 to Payment” (30 Oct 2026)** identifies **Grove Health P.A.** as the billing entity and describes credentialing, practitioner supervision, program eligibility, consent and plans, CCM monthly services, optional RPM, an APCM alternative, 837P claim submission via SPOT/clearinghouse, 835 ERA posting, denial management, and audit controls.

Treat this as a **source-proposed billing model requiring operational and credentialing sign-off**, not proof that every enrollment, Medicare rule, payer contract, NPI, claims route or telehealth visit is verified.

## Tool ownership in the Workflow tab

The **Workflow** tab is the active section; the other tabs are intentionally blank. Tool mapping is a proposed integration/ownership model, not a claim that integrations are live.

| Tool | Role | Primary workflow stages |
| --- | --- | --- |
| CRM (not selected) | Operational patient status, daily queue, task routing, enrollment and follow-up automation | 1–5, 7–8 |
| Aircall | Live lead transfers, calls, follow-up transfers, approved SMS | 1–5 |
| Doxy.me | Video-first physician visits (fallback via phone when documented) | 2 and follow-ups |
| Practice Fusion | Clinical source of truth: patient demographics, Medicare ID, encounters, diagnoses, care plan and consent | 1–7 |
| ChronicCareIQ | RPM readings and device status; candidate source of clinical minutes subject to vendor/billing validation | 4–5, 7 |
| Grove billing, SPOT / clearinghouse | Claim preparation/submission, payments, ERA, denials and reconciliation | 0, 6–8 |

**Proposed interfaces:** Aircall → CRM (calls and transfers); Practice Fusion → CRM (confirmed CCM enrollment and welcome-message trigger); CCIQ → CRM (monitoring tasks); CCIQ → billing (validated time and RPM evidence); billing → CRM (claim/denial task visibility). Confirm API availability, HIPAA/BAA and record ownership before implementing.

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
