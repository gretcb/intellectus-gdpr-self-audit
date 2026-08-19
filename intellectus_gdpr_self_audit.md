# Intellectus — GDPR Self-Audit

## Scope and method

This self-audit assesses Intellectus, the Project 3 system that was actually built, together with its intended evolution from the demonstrated public/demo MVP to production use with real client data. The production assessment considers a Spanish social-impact organisation providing operational information, a challenge description and potentially personal-data-containing internal documents. Prospective production processing is explicitly distinguished from functionality and controls evidenced in the current MVP.

Three labels are used throughout the assessment:

- **Observed / stated** — explicitly included in the agreed scenario or project design.
- **Prospective** — relevant to production use with real personal data but not evidenced as implemented.
- **TBD** — insufficient evidence; technical, contractual or legal confirmation is required.

Working rule: a control that is not documented is not counted as a control that exists.

## Evidence vs assumptions

| Element | Status | Treatment in this audit |
|---|---|---|
| Client is a Spanish social-impact organisation | Observed / stated | Treated as a scenario fact |
| Web application → n8n → research services | Observed / stated | Treated as the base workflow |
| Internal documents may contain employee, volunteer, donor or beneficiary data | Observed / stated | Treated as a genuine scenario risk |
| Consultant review before client use | Observed / stated | Design safeguard; operational effectiveness TBD |
| External AI provider | Possible, not confirmed | TBD; no provider or contract assumed |
| Hosting and processing region | Not evidenced | TBD |
| DPAs with providers | Not evidenced | TBD |
| SCCs, adequacy or other transfer mechanism | Not evidenced | TBD |
| Retention and deletion periods | Not evidenced | TBD |
| Processing scale | Not evidenced | TBD |
| Actual presence of Article 9 data | Not evidenced | TBD; treated as an input risk |
| Operational data-subject-rights workflow | Not evidenced | TBD |

# Phase 1 — Personal Data Inventory

| Data category | Source | Specific purpose | Retention | Leaves the EEA? |
|---|---|---|---|---|
| Employee/volunteer names, roles and professional data, if present | Internal documents | Understand responsibilities, processes and organisational context where necessary | **TBD — define by purpose** | **TBD — depends on hosting/providers** |
| Performance, incident, opinion or employment/volunteering-related text, if present | Internal documents | Analyse causes and evidence behind the organisational challenge | **TBD** | **TBD** |
| Donor data, if present | Internal documents | Analyse fundraising, donor-management or resilience issues only where relevant | **TBD** | **TBD** |
| Beneficiary data, if present | Internal documents | Analyse service delivery or impact only where necessary | **TBD** | **TBD** |
| Professional information about identifiable people | Research services / public sources | Add context and verify external evidence | **TBD** | **TBD** |
| Challenge description containing references to individuals | Organisation input | Define the problem and diagnostic scope | **TBD** | **TBD** |
| Inferences or findings about identifiable individuals, if generated | Intellectus output | Support the diagnostic only where strictly necessary | Must follow the underlying purpose; **TBD** | **TBD** |
| Article 9 data, if present | Mainly internal documents | Not required by default; any use requires specific justification | Exclude/minimise unless lawfully justified; period **TBD** | **TBD** |

## Purpose limitation risk

There is a clear risk of secondary use.

Internal documents may originally have been collected for HR administration, volunteer management, donor relationships, service delivery or beneficiary support and later reused for an AI-assisted organisational diagnostic.

That further use cannot automatically be assumed compatible.

Before internal documents are processed, the controller should document:

1. the original purpose;
2. the new diagnostic purpose;
3. the relationship between the two;
4. the collection context;
5. the reasonable expectations of the individuals;
6. the nature of the data;
7. the safeguards available.

Where identification is unnecessary, personal data should be removed, aggregated or pseudonymised before entering the workflow.

**Status: production gap. Compatibility has not been established.**

# Phase 2 — Role Map

| Entity | Provisional role | Activity | DPA / contract status |
|---|---|---|---|
| Spanish social-impact organisation | **Controller, in principle** | Determines the purpose of the diagnostic and what information is provided | No DPA with itself; must document processor instructions |
| Intellectus operator | **Likely processor**, if acting only on client instructions | Processes information to produce diagnostic support | **TBD — Article 28 agreement required before real data** |
| Reviewing consultant | Authorised person under the organisation employing or engaging them; separate role **TBD** | Reviews evidence and diagnostic before use | Do not assume a separate role without contractual context |
| n8n infrastructure | **TBD depending on deployment** | Workflow orchestration and possible execution logs | If self-hosted, n8n GmbH may not process content; if n8n Cloud is used, assess vendor role and contract |
| Research services | **TBD by provider and transmitted data** | Search, verification or enrichment | **TBD** |
| External AI provider, if enabled | Likely processor/subprocessor only if acting on instructions and without its own purpose | Model inference on submitted content | **TBD — DPA and terms required before personal data is sent** |
| Hosting / storage provider, if any | Likely processor/subprocessor | Storage, logs and backups | **TBD** |

The classification depends on who determines the purposes and essential means of processing.

If the Intellectus operator or any provider reuses client personal data for model training, product analytics, service improvement or another independent purpose, the processor analysis must be revisited.

## International transfers

There is not enough evidence to confirm whether personal data leaves the EEA.

Before production, the following must be established for each provider:

- storage region;
- processing region;
- remote access locations;
- subprocessors;
- onward transfers.

If a transfer to a third country takes place, the applicable Chapter V mechanism must be identified.

This may involve an adequacy decision or Article 46 safeguards such as SCCs where appropriate.

**No transfer mechanism is assumed.**

**Status: TBD and a go-live condition.**

# Phase 3 — Lawful Basis Assessment

| Purpose | Proposed lawful basis | Rationale | Legal review |
|---|---|---|---|
| Receive organisational context and minimum professional contact data | **Article 6(1)(f) — legitimate interests, provisional** | There is a genuine interest in delivering the service and coordinating the diagnostic, provided processing is limited to what is necessary | Yes — LIA A |
| Research public professional information where necessary to verify context | **Article 6(1)(f) — legitimate interests, provisional** | Relevant public information may help verify facts, but public availability does not remove GDPR protection | Yes — LIA B |
| Analyse employee or volunteer data contained in internal documents | **TBD — legal review** | Necessity, original purpose and reasonable expectations have not been established | Yes |
| Analyse donor data | **TBD — legal review** | The basis depends on the original relationship, purpose, necessity and transparency | Yes |
| Analyse beneficiary data | **TBD — legal review** | Potential vulnerability and higher impact make a blanket legitimate-interest basis inappropriate | Yes |
| Process special-category data | **TBD — Article 6 basis + Article 9(2) condition required** | Article 9 requires an additional condition | Yes — blocking if these data enter the workflow |
| Generate a diagnostic containing personal data | Follows the lawful basis of the underlying purpose | Producing an output does not create a new lawful basis | Yes where identifiable data are included |

Article 6(1)(b) is not proposed as a general basis.

A consulting contract may be concluded with a legal entity. That does not automatically make the processing of employee, volunteer, donor or beneficiary data necessary for a contract with those individuals.

## LIA A — Organisational context and minimum professional contact data

### Purpose test

The organisation and Intellectus operator have a specific and legitimate interest in coordinating the service and understanding the organisational challenge.

**Result:** satisfied in principle.

### Necessity test

Processing should be limited to the professional information genuinely needed to deliver the service.

If a role or function is sufficient, additional personal information should not be retained.

**Result:** satisfied only where minimisation is applied.

### Balancing test

The privacy impact is relatively limited where processing concerns predictable professional information used within a business relationship.

The balance becomes less favourable where the data include personal assessments, sensitive information or information that the individual would not reasonably expect to be reused.

**Conclusion:** legitimate interests may be workable with minimisation and transparency, but the LIA should be documented before production.

## LIA B — Public professional research

### Purpose test

Verifying facts relevant to an organisational diagnostic can constitute a specific legitimate interest.

**Result:** potentially satisfied.

### Necessity test

The need for personal information should be assessed for each research activity.

If the same objective can be achieved using non-personal organisational information, the less intrusive option should be preferred.

**Result:** conditional.

### Balancing test

The fact that information has already been published may reduce expectations of confidentiality, but it does not remove the individual’s GDPR rights.

The assessment should consider:

- the context in which the information was published;
- how old it is;
- whether several sources are being combined;
- whether new inferences are being made.

**Conclusion:** public professional information should not be treated as a general licence to collect information about individuals. Use should remain bounded, necessary and documented.

# Phase 4 — Risk and Rights Analysis

## Special-category data — Article 9

The scenario does not confirm that Intellectus processes special-category data.

However, internal documents from a social-impact organisation could contain information relating to health, disability, ethnic origin, religion, political opinions, trade-union membership or other protected categories.

No Article 9(2) condition is currently documented.

If these data appear, the default approach should be to exclude or redact them unless the organisation can demonstrate:

- necessity;
- a valid Article 6 basis;
- a specific Article 9(2) condition.

**Status: potentially high risk and a blocking condition if these data are processed without a documented legal basis.**

## Automated decision-making — Article 22

Based on the current scenario, Intellectus does not make a solely automated individual decision producing legal or similarly significant effects.

It produces an organisational diagnostic, and consultant review is mandatory before client use.

The safeguard only works if the review is meaningful.

The consultant should have the competence and authority to:

- inspect source evidence;
- identify errors;
- challenge inferences;
- change or reject the output.

There should also be evidence that the review actually took place.

**Status of review procedure and audit trail: TBD.**

**Conclusion:** Article 22 does not appear to apply to the current scenario. The assessment must be reopened if Intellectus begins scoring, ranking or recommending consequential action about individuals.

## DPIA screening

The relevant question is whether the processing is likely to result in a high risk to the rights and freedoms of individuals.

The EDPB uses nine criteria as guidance.

| EDPB criterion | Intellectus assessment |
|---|---|
| Evaluation or scoring of individuals | **Not observed.** The current diagnostic is organisational |
| Automated decision-making with legal or similar significant effect | **Not observed** due to mandatory human review |
| Systematic monitoring | **Not observed / TBD** |
| Sensitive or highly personal data | **TBD / potentially applicable** through internal documents |
| Large-scale processing | **TBD** — volume, frequency, duration and scope are unknown |
| Matching or combining datasets | **TBD / potentially applicable** if internal documents and external research are combined at individual level |
| Vulnerable data subjects | **TBD / potentially applicable** — the term “beneficiary” alone is not enough to assume vulnerability |
| Innovative use of technology | **Yes, reasonably applicable** due to AI-assisted diagnostic processing |
| Processing preventing individuals from exercising rights or using a service/contract | **Not observed** |

International transfers are not one of the nine standard EDPB criteria. They should be assessed separately under GDPR Chapter V.

**Conclusion:** A formal DPIA screening must be completed before any real internal client documents enter the workflow. For the current public/demo MVP, the available evidence does not establish that a full DPIA is already required. However, if the intended production deployment includes internal documents containing sensitive or highly personal information, vulnerable data subjects, combined client and public-source datasets, and AI-supported analysis, Intellectus should complete a full DPIA before the pilot begins. The final decision must be documented against the actual production scope, data categories, scale, providers and safeguards.

## Data-subject-rights friction

| Right | Operational risk | Current status |
|---|---|---|
| Information / transparency | Data may come indirectly from internal documents or research, so the organisation must determine what information must be provided and through which channel | **TBD** |
| Access | The same person may appear across documents, logs, prompts, responses and the diagnostic | **TBD — no evidenced workflow** |
| Rectification | Correcting the source document does not automatically correct previously generated outputs | **TBD** |
| Erasure | Deletion may need to propagate across storage, logs, backups and processors | **TBD** |
| Objection | Particularly relevant where Article 6(1)(f) is relied upon | **TBD** |
| Restriction | The organisation must be able to suspend relevant processing where the right applies | **TBD** |

The controller must be able to respond to data-subject requests within the GDPR time limits.

A production design should maintain sufficient traceability to locate information across the full processing chain.

**Minimum technical traceability requirement:**

```text
data subject
→ source
→ workflow / run
→ provider
→ output
→ storage location
→ correction / deletion action
```

# Phase 5 — Law Stacking

## AI Act

There is currently no evidence that Intellectus falls within an Annex III high-risk use case.

The current system supports an organisational diagnostic and is not described as being used for recruitment, employment management, access to essential services or another listed consequential decision about individuals.

The classification should be reassessed if the purpose changes.

Relevant AI Act checks for the current design include:

- AI literacy obligations;
- transparency requirements where applicable;
- effective human oversight;
- clear communication of the role of AI in the diagnostic process.

## ePrivacy

The scenario does not provide enough information about cookies, tracking pixels, fingerprinting or access to information stored on a user’s device.

**Status: TBD, not N/A.**

If the production web application uses non-essential tracking technologies, an ePrivacy / Spanish LSSI consent assessment will be required.

## Data Act

No connected products or IoT-generated data are described in the current scenario.

The potential use of cloud services is not enough, on its own, to determine which Data Act switching obligations would apply.

**Status:** no material impact demonstrated for the current personal-data workflow. Reassess once the production cloud architecture is confirmed.

# Accountability Check

Could the current documentation demonstrate full GDPR compliance to a supervisory authority?

**No.**

The current assessment identifies several controls that would still need evidence before production use with real personal data.

| Accountability evidence | Current status |
|---|---|
| Data processing brief | Completed in this lab |
| Data and purpose inventory | Completed as a first-pass assessment |
| Controller / processor map | Completed provisionally |
| LIA | Preliminary assessment completed for two purposes |
| Article 28 DPAs | **TBD / not evidenced** |
| Subprocessor register | **TBD / not evidenced** |
| Record of Processing Activities (ROPA) | **TBD / not evidenced** |
| Formal DPIA screening | Recommended; not yet evidenced |
| Full DPIA | **Not completed** |
| Privacy notice covering Intellectus processing | **TBD / not evidenced** |
| Retention and deletion policy | **TBD / not evidenced** |
| Data-subject-rights procedure | **TBD / not evidenced** |
| International transfer map and mechanism | **TBD / not evidenced** |
| Evidence of meaningful human review | Design requirement exists; procedure / audit trail **TBD** |
| Incident-response process | **TBD / not evidenced** |

# Data Protection by Design

Highest-risk activity assessed: ingestion of internal documents that may contain personal data relating to employees, volunteers, donors or beneficiaries.

| Principle | Current state | Assessment | Required change |
|---|---|---|---|
| Data minimisation | No evidenced pre-ingestion filter | **FAIL / TBD** | Redact or exclude unnecessary personal data before it reaches n8n or an AI provider |
| Purpose limitation | Secondary use is not assessed per document/source | **FAIL / TBD** | Record original purpose and compatibility |
| Access control | No RBAC model is evidenced | **UNKNOWN** | Define roles, permissions and access logs |
| Retention | No automatic deletion rule or schedule is evidenced | **FAIL / TBD** | Define retention periods and verifiable deletion |
| Data-subject rights | No end-to-end traceability is evidenced | **FAIL / TBD** | Implement workflows for access, rectification, erasure, restriction and objection |
| Incident handling | No documented process is evidenced | **UNKNOWN** | Define detection, escalation and breach-assessment procedures |

# Blocking Actions and Owners

| Priority | Action | Primary owner | Closure criterion |
|---|---|---|---|
| **P0** | Complete the real data map: providers, hosting, logs, subprocessors, data sent and processing regions | **Intellectus operator** | Approved technical diagram and processing register |
| **P0** | Determine Article 6 basis by purpose, secondary-use compatibility and Article 9 treatment | **Client + Legal/DPO** | Lawful bases documented; LIA / Article 9 condition completed where required |
| **P0** | Confirm roles and put Article 28 DPAs in place before processor access to real data | **Client + Legal + Intellectus operator** | Contracts signed and subprocessors documented |
| **P0** | Resolve international transfers | **Intellectus operator + Legal** | Countries, Chapter V mechanism and safeguards documented |
| **P0** | Complete formal DPIA screening and a full DPIA if required | **Client + DPO/Legal** | Documented decision; DPIA approved where necessary |
| **P1** | Define retention, deletion, data-subject-rights procedures and evidence of human review | **Client + Intellectus operator** | End-to-end procedures tested |

# Overall Recommendation

**PROCEED WITH CONDITIONS**

Development and testing of Intellectus can continue.

However, the workflow should not be opened to real internal documents containing personal data until the P0 actions above are closed.

The strongest element of the current design is mandatory consultant review.

The main compliance gaps sit around the model rather than inside it: lawful basis, secondary-use compatibility, data minimisation, processor governance, international transfers, DPIA screening, retention and the operational ability to honour data-subject rights.

## References

- GDPR: https://eur-lex.europa.eu/eli/reg/2016/679/oj
- EDPB Guidelines 07/2020 on controller and processor concepts
- EDPB guidance on legitimate interests
- EDPB guidance on DPIAs and high-risk processing
- EDPB guidance on automated decision-making and profiling
- AEPD guidance on Data Protection Impact Assessments
- European Commission guidance on Standard Contractual Clauses
- European Commission guidance on the AI Act
- European Commission guidance on the Data Act