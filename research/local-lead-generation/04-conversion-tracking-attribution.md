# Report 4 — Conversion Tracking and Attribution for an OAS Ottawa Backflow Pilot

**Research date:** 2026-07-15  
**Decision scope:** How OAS should capture, qualify, attribute, dispute, and reconcile calls/forms through booked and paid backflow work.  
**Evidence labels:** **Fact** = directly supported by an authoritative source; **Inference** = recommended design derived from evidence; **Unknown** = must be learned in the pilot or resolved in the legal review (Report 7).

## Executive conclusion

The episode is directionally right that call tracking and CRM access matter, but weekly call volume is not proof of a viable lead-generation business. OAS needs an auditable chain from **search exposure → visit → call/form → unique lead → qualified need → appointment → completed work → invoice → paid revenue**. Search Console measures organic discovery, GA4 measures web behaviour, CallRail captures calls/forms, the CRM owns lead status, and the job/accounting system owns revenue.

The primary pilot metric should not be raw calls. It should be **paid completed backflow jobs attributable to a valid lead**, with qualified leads, booked appointments, response time, duplicates, spam, and disputes as diagnostic metrics. Do not record calls by default until the privacy notice, consent flow, access controls, and retention/deletion policy are approved. PIPEDA and the Privacy Commissioner treat recordings, contact details, and call content as personal information.

## Episode hypothesis

Episode 315 proposes that:

- CallRail can show calls, answer behaviour, and lead volume.
- Contractors can be evaluated through follow-up and secret-shopping.
- CRM/accounting access can verify revenue share.
- Calls plus rank reports permit light weekly management.

Treat these as hypotheses. The episode does not define a qualified lead, disclose duplicate/spam policy, establish who owns personal information, explain call-recording consent, reconcile a call to a paid job, or specify which attribution model governs payment. “I sent a call” and “that call caused revenue” are different claims.

## Authoritative current evidence

### 1. Call and form capture

**Fact — high confidence.** CallRail's [DNI documentation](https://support.callrail.com/hc/en-us/articles/5711814948877-Dynamic-number-insertion-overview) says its JavaScript swaps a canonical website number for a tracking number routed to the destination phone. A source-level number represents one campaign; a website pool retains visitor/source detail. CallRail stores source in a cookie for return visits.

**Inference — high confidence.** For the OAS pilot, keep one real OAS business number in the HTML and use a small DNI pool only on the website. Test organic Google, direct, referral, and tagged campaign sessions. Avoid putting a disposable tracking number everywhere until number ownership, Google Business Profile representation, and offboarding have been tested.

**Fact — high confidence.** CallRail supports form tracking, but unwanted submissions must be classified. Its [form guide](https://support.callrail.com/hc/en-us/articles/5711640220045-Getting-started-with-form-tracking) recommends reCAPTCHA and allows spam submissions to be removed from logs, reports, and billing. Its [spam guide](https://support.callrail.com/hc/en-us/articles/5711519520525-How-CallRail-prevents-spam) supports marking unwanted calls and forms as spam.

### 2. GA4 lead funnel and attribution

**Fact — high confidence.** Google recommends `generate_lead`, `qualify_lead`, `disqualify_lead`, `working_lead`, `close_convert_lead`, and `close_unconvert_lead`. See [GA4 recommended events](https://support.google.com/analytics/answer/9267735?hl=en). A converted lead may carry currency and value.

**Inference — high confidence.** A successful backflow form submission or first valid call creates `generate_lead`; qualification and closing events should originate from the CRM outcome, not from page views or arbitrary call duration. A click on a phone link is intent, not a lead; a ringing call is an interaction, not necessarily a qualified lead.

**Fact — high confidence.** CallRail's [GA4 integration](https://support.callrail.com/hc/en-us/articles/9495611166733-Google-Analytics-4-GA4-integration) sends calls, texts, chats, and forms as GA4 events. For interactions with session data, CallRail can send the GA session ID so built-in attribution can work. For interactions without session data, its [GA4 data guidance](https://support.callrail.com/hc/en-us/articles/12381200845965-Your-CallRail-data-in-Google-Analytics-4) warns that standard source/medium/campaign fields may be unavailable and attribution arrives as custom parameters; custom dimensions/metrics are therefore needed.

**Fact — high confidence.** GA4 defaults to data-driven attribution and provides path/model comparisons, but models distribute *credit*; they do not prove causation. See [How GA4 attributes key events](https://support.google.com/analytics/answer/12958241?hl=en).

### 3. Search Console is discovery data, not revenue truth

**Fact — high confidence.** Search Console's [Performance report](https://support.google.com/webmasters/answer/7576553?hl=en) reports clicks, impressions, CTR, and average position. Its [data caveats](https://support.google.com/webmasters/answer/96568?hl=en) say rare/sensitive queries and lower rows may be omitted, data normally lags two to three days, and its California date boundary can differ from GA.

**Inference — high confidence.** Never reconcile Search Console clicks one-for-one with GA sessions, CallRail calls, or CRM leads. Use it to explain discovery and content performance. Use CRM and job/payment records for commercial outcomes.

### 4. CRM linkage and offline revenue feedback

**Fact — high confidence.** CallRail's [HubSpot integration](https://support.callrail.com/hc/en-us/articles/5711820544269-HubSpot-integration) sends calls, texts, and forms to contact timelines; its [ROI report](https://support.callrail.com/hc/en-us/articles/5711638757389-ROI-by-source-custom-report) can use HubSpot deals when prerequisites are met. HubSpot attribution depends on subscription, and deduplication varies by identifier and creation method.

**Inference — high confidence.** The CRM should be the canonical operational record, but invoice/payment status must be reconciled from the job/accounting system. Every raw inquiry receives an immutable `lead_id`; every job receives a `job_id`; every invoice receives an `invoice_id`. Never overwrite original source fields when a later interaction occurs.

**Fact — high confidence.** For future paid search, Google's [enhanced conversions for leads](https://support.google.com/google-ads/answer/14274408?hl=en) can upload qualified/converted offline outcomes and use hashed first-party contact data plus GCLID where available. Google recommends “qualified lead” or “converted lead” as the goal and retaining GCLID for accuracy.

**Inference — high confidence.** Do not enable enhanced conversions in the first organic pilot merely because it exists. Add it only with a documented purpose, lawful/meaningful consent, data map, and enough Google Ads volume to justify the privacy and implementation burden.

### 5. Privacy and consent implications

This is a measurement design summary, not legal advice; Report 7 must resolve the legal detail.

**Fact — high confidence.** PIPEDA applies to private-sector commercial collection, use, or disclosure of personal information. The Privacy Commissioner's [requirements in brief](https://www.priv.gc.ca/en/privacy-topics/privacy-laws-in-canada/the-personal-information-protection-and-electronic-documents-act-pipeda/pipeda_brief/) cover consent, minimization, retention, safeguards, openness, and access. [Meaningful consent](https://www.priv.gc.ca/en/privacy-topics/business-privacy/collecting-personal-information/consent/gl_omc_201805/) requires understanding the nature, purpose, and consequences.

**Fact — high confidence.** The Privacy Commissioner's [call-recording guidance](https://www.priv.gc.ca/en/privacy-topics/surveillance/02_05_d_14/) says businesses should record only for appropriate purposes, tell the customer the call is being recorded, state why, and seek consent. Recordings must be handled appropriately through disposal, and outsourced providers must also comply.

**Inference — high confidence.** The form should identify OAS, the service purpose, which operating partner receives the request (if any), the contact channels requested, and link to the privacy notice. Consent to answer a requested quote is not blanket consent to future marketing or automated texts. Minimize fields; do not collect medical, tenant, payment, or building-security details unless operationally necessary. If calls are recorded later, play a clear notice before substantive collection, provide an alternative where required, restrict access, and define deletion periods.

### 6. Speed-to-lead

**Evidence — medium confidence.** A 2021 InsideSales/XANT analysis reports 55 million activities on 5.7 million inbound leads at 400+ companies and says conversion was eight times higher for attempts in the first five minutes than later attempts. This is vendor research, not an Ottawa trades experiment; the public methodology is limited and the effect should not be imported as a universal causal law.

**Pilot inference — medium-high confidence.** Adopt a **ten-minute business-hours response target** as the initial operating standard, not a promised conversion multiplier. Separately measure the first-five-minute band. Track median and 90th-percentile time to first human attempt, missed-call callback time, connection rate, and booking rate by response-time band. The pilot's own results should decide whether a tighter five-minute target is economically important for backflow enquiries.

## Ottawa application and measurement design

### A. Funnel and definitions

| Stage | Operational definition | System of record |
|---|---|---|
| Search exposure | Search Console impression/click for an OAS URL | Search Console |
| Visit | GA4 session with original source/medium/campaign and landing page | GA4 |
| Raw inquiry | Connected call, voicemail, or successfully submitted form | CallRail |
| Unique lead | Raw inquiry deduplicated to one person/property/service need | CRM |
| Working lead | First human contact attempt logged | CRM |
| Qualified lead | Meets the pilot qualification rule below | CRM |
| Booked | Date/time accepted for a test, survey, or repair visit | CRM/job system |
| Completed | Technician marks the agreed service complete | Job system |
| Converted | Valid invoice issued for completed work | Accounting/job system |
| Paid | Payment received and not refunded/charged back | Accounting system |

### B. Backflow qualified-lead rule

A lead is qualified only when all required conditions are met:

1. The property is within the pilot's actual Ottawa service area.
2. The person/property has a credible need for annual device testing, a premise survey, a failed-device repair/replacement, or related compliant backflow work OAS offers.
3. Contact information works and the person can authorize access or connect OAS to the responsible property/facility manager.
4. The requested work is within Alex/OAS's current credentials, insurance, equipment, and capacity.
5. The inquiry is not spam, a vendor pitch, job applicant, wrong service, test call, or duplicate of the same active need.

Tag qualified leads by type: `annual_test`, `survey`, `failed_device`, `repair_replace`, `other_valid`. Disqualify with one controlled reason. Do not let a contractor mark leads invalid without a reason and evidence.

### C. Duplicate, spam, and dispute policy

- **Duplicate:** same normalized phone/email or property and substantially the same need within 30 days of an open lead. Link it; do not count a new lead.
- **Renewal/repeat:** a new annual cycle or genuinely new device/work order. Count separately from acquisition leads.
- **Spam:** automated solicitation, test/malicious traffic, nonsense data, or unrelated vendor outreach. Exclude from conversion counts.
- **Wrong number/wrong service:** nonqualified, not spam.
- **Dispute:** operator has 48 hours after delivery to challenge qualification with a coded reason and evidence. OAS reviews source, timestamps, notes, and lawful evidence. Preserve the original record and status history; define in the contract whether the 48-hour clock pauses outside business days.

### D. Minimum data contract

Capture IDs for lead/interaction/CRM/job/invoice; Toronto and UTC timestamps; original/latest source and landing-page/UTM/GCLID where applicable; channel; protected normalized contact/property identifiers; notice/consent version; response, qualification, booking, completion and payment timestamps; outcome reasons; and job value, cost, and refund status.

Do not store full call transcripts or unnecessary building details in analytics tools. Keep personal information in the controlled CRM/job system.

### E. Dashboard

Review weekly: discovery (impressions/clicks/CTR); acquisition (sessions and inquiries); quality (unique/qualified/spam/duplicate); response (answer rate and median/P90 response); sales (booked/completed); economics (paid revenue, direct cost and cost per outcome); and integrity (unattributed, disputed, missing, failed-sync or refunded records). Reconcile commercially each month.

Report first-touch and last-non-direct attribution side by side. Do not blend them into one unexplained “source of truth.” For an organic-only pilot, deterministic first-touch is sufficient for operations; GA4 modelled attribution is secondary context.

## Skills and tools to acquire

- CallRail DNI, routing, missed-call alerts, spam controls, and QA
- GA4 events/DebugView/custom dimensions plus Search Console interpretation
- CRM lifecycle, deduplication, immutable source, and audit design
- Form validation and server-confirmed success events
- UTM/GCLID and offline-conversion governance
- Privacy notice, consent, retention, access, and processor review
- Lead classification, invoice reconciliation, and dashboard anomaly checks

## Pilot exercise

Run an eight-week instrumented backflow pilot:

1. **Week 0 — definitions:** approve the funnel, qualification rule, duplicate window, dispute rule, data owner, privacy notice, and retention periods.
2. **Week 0 — setup:** Search Console property; GA4; canonical phone plus CallRail DNI pool; one tested form; CRM pipeline; job/invoice linkage.
3. **Week 0 — QA:** simulate organic, direct, referral, and UTM visits; successful/failed/spam forms; answered/missed/repeat calls; duplicate person/property; booked, lost, completed, paid, and refunded outcomes.
4. **Weeks 1–2 — baseline:** operate without automated scoring. Manually classify every interaction within one business day and inspect sync errors daily.
5. **Weeks 3–8 — operating test:** enforce the ten-minute business-hours response target where practical, while measuring the first-five-minute band separately; review weekly; reconcile invoices monthly.
6. **End:** calculate conversion and economics by channel, response band, lead type, and landing page. Audit ten random records from first click/call through final payment.

### QA acceptance cases

Prove that DNI swaps and routes; original source survives repeat/direct visits; a form fires once after success; repeat callers deduplicate; spam/tests are excluded; missed calls receive an owner and callback time; conversion requires an invoice; and dashboard totals reconcile to raw interactions and accounts within documented exclusions.

## Completion test

This gap is closed for a pilot only when at least 95% of inquiries attach to CRM records; at least 90% of non-spam leads receive a qualification outcome within one business day; booked/completed/paid stages have owners and timestamps; paid jobs trace to lead/job/invoice/payment IDs; source survives later interactions; written duplicate/spam/dispute rules reproduce decisions; recording is off or fully governed; and ten sampled records reconcile end to end. OAS must state revenue by source with an explicit rule and uncertainty.

## Unknowns and conflicts

- **Unknown:** Actual Ottawa backflow search-to-call, call-to-qualified, booking, completion, and revenue rates. Only the pilot can establish them.
- **Unknown:** Whether CallRail's current Canadian-number inventory and pricing suit the pilot; verify in-account before design lock.
- **Unknown:** Whether the chosen CRM tier supports required attribution/audit features. Do not assume paid HubSpot reports are available.
- **Unknown:** Final PIPEDA controller/processor roles when OAS routes a lead to a partner; Report 7 must resolve.
- **Conflict:** CallRail says its DNI cookies are “strictly necessary,” but the business remains responsible for notice, and Canadian legal characterization must be independently reviewed.
- **Conflict:** GA4 modelled credit may differ from CallRail deterministic source and CRM original source. Preserve all three and explain their purposes.
- **Conflict:** Fast response encourages automation; text/call consent and anti-spam/telemarketing rules limit what automation may send.
- **Unknown:** Appropriate retention period for recordings/transcripts. Default to no recording until decided.

## Failure modes

- Paying on raw calls; treating phone clicks as calls or calls as jobs
- Firing conversions before confirmed form success
- Claiming visitor attribution from one static number
- Overwriting original source or ignoring repeats, duplicates, spam, and tests
- Silent/indefinite recording or undisclosed partner data sharing
- Letting the contractor alone decide validity
- Optimizing ads to raw inquiries instead of qualified/converted leads
- Expecting tool totals to match or assuming unavailable CRM features
- Uploading offline customer data without purpose and consent review

## Source table

| Source | Date | Evidence type | Confidence | What it establishes |
|---|---|---|---|---|
| [CallRail — Dynamic number insertion overview](https://support.callrail.com/hc/en-us/articles/5711814948877-Dynamic-number-insertion-overview) | Updated 2026-07-13 | Primary vendor documentation | High | DNI, source versus visitor pools, routing, cookie behaviour |
| [CallRail — Getting started with form tracking](https://support.callrail.com/hc/en-us/articles/5711640220045-Getting-started-with-form-tracking) | Updated 2025-11-12 | Primary vendor documentation | High | Form capture, spam classification, reCAPTCHA recommendation |
| [CallRail — How CallRail prevents spam](https://support.callrail.com/hc/en-us/articles/5711519520525-How-CallRail-prevents-spam) | Updated 2025-12-16 | Primary vendor documentation | High | Spam treatment for calls/forms |
| [CallRail — GA4 integration](https://support.callrail.com/hc/en-us/articles/9495611166733-Google-Analytics-4-GA4-integration) | Updated 2026-01-14 | Primary vendor documentation | High | Call/form events sent to GA4 |
| [CallRail — CallRail data in GA4](https://support.callrail.com/hc/en-us/articles/12381200845965-Your-CallRail-data-in-Google-Analytics-4) | Updated 2025-11-12 | Primary vendor documentation | High | Session and no-session attribution limitations |
| [CallRail — HubSpot integration](https://support.callrail.com/hc/en-us/articles/5711820544269-HubSpot-integration) | Updated 2026-06-02 | Primary vendor documentation | High | Calls/forms on CRM contact timelines |
| [CallRail — Qualify leads](https://support.callrail.com/hc/en-us/articles/5711776551437-How-to-qualify-leads-in-CallRail) | Updated 2025-12-04 | Primary vendor documentation | High | Manual/automated qualification, tags, and values |
| [Google Analytics — Recommended events](https://support.google.com/analytics/answer/9267735?hl=en) | Accessed 2026-07-15; living documentation | Primary platform documentation | High | Full online/offline lead event family |
| [Google Analytics — Recommended-event reference](https://developers.google.com/analytics/devguides/collection/ga4/reference/events) | Updated 2026-06-26 | Primary platform documentation | High | Converted-lead value and currency semantics |
| [Google Analytics — Attribution of key events](https://support.google.com/analytics/answer/12958241?hl=en) | Accessed 2026-07-15 | Primary platform documentation | High | Data-driven default, paths, model comparison |
| [Google Search Console — Performance report](https://support.google.com/webmasters/answer/7576553?hl=en) | Accessed 2026-07-15 | Primary platform documentation | High | Organic clicks, impressions, CTR, position |
| [Google Search Console — Data caveats](https://support.google.com/webmasters/answer/96568?hl=en) | Accessed 2026-07-15 | Primary platform documentation | High | Privacy omissions, top-row limits, lag, timezone differences |
| [HubSpot — Deduplicate records](https://knowledge.hubspot.com/records/deduplication-of-records) | Accessed 2026-07-15; living documentation | Primary vendor documentation | Medium-high | Identifier- and method-dependent deduplication |
| [HubSpot — Attribution report definitions](https://knowledge.hubspot.com/reports/understand-attribution-reporting) | Updated 2026-03-22 | Primary vendor documentation | Medium-high | Contact, deal, and revenue attribution concepts |
| [Google Ads — Enhanced conversions for leads](https://support.google.com/google-ads/answer/14274408?hl=en) | Accessed 2026-07-15 | Primary platform documentation | High | Hashed first-party data, GCLID, qualified/converted offline goals |
| [Office of the Privacy Commissioner — PIPEDA in brief](https://www.priv.gc.ca/en/privacy-topics/privacy-laws-in-canada/the-personal-information-protection-and-electronic-documents-act-pipeda/pipeda_brief/) | Modified 2024-05-01 | Federal regulator guidance | High | Commercial applicability and ten principles |
| [Office of the Privacy Commissioner — Meaningful consent](https://www.priv.gc.ca/en/privacy-topics/business-privacy/collecting-personal-information/consent/gl_omc_201805/) | Modified 2025-08-11 | Federal regulator guidance | High | Nature, purpose, and consequences must be understandable |
| [Office of the Privacy Commissioner — Recording customer calls](https://www.priv.gc.ca/en/privacy-topics/surveillance/02_05_d_14/) | Published 2018-03-06 | Federal regulator guidance | High | Notice, purpose, consent, handling, and processor responsibility |
| [InsideSales — 2021 Lead Response Research](https://www.insidesales.com/response-time-matters/) | 2021 study; accessed 2026-07-15 | Vendor observational study | Medium | Large-sample association between response speed and conversion; not Ottawa-specific causation |
