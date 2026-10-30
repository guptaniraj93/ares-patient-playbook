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
