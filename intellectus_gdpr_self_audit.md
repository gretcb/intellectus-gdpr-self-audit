# Intellectus — GDPR Self-Audit

## Assessment approach

This assessment covers the Intellectus Project 3 MVP and its intended evolution toward real client use.

Three labels are used throughout:

- **Observed** — supported by the current implementation or project documentation.
- **Prospective** — would arise if real internal client data is enabled.
- **TBD** — cannot be established from the current project and requires legal, contractual or vendor confirmation.

An undocumented control is not counted as a control that exists.

---

# Phase 1 — Personal Data Inventory

| Data category | Source | Purpose | Retention period | Crosses EU border? |
|---|---|---|---|---|
| Organisation and challenge context | Web intake / consultant | Frame the diagnostic | Not defined for production | TBD |
| Public professional information about identifiable people | Public web sources | Understand organisational context | Not defined for production | TBD |
| Public statements attributed to identifiable people | Public web sources | Evidence gathering | Not defined for production | TBD |
| Consultant-entered free text | Web intake | Context and diagnostic analysis | Not defined for production | TBD |
| Controlled fictional/sample records | Fixtures and demo data | Testing and demonstration | Repository/test lifecycle | No personal-data issue where genuinely fictional |
| Employee information | Future client documents | Organisational analysis where necessary | TBD before activation | TBD |
| Volunteer information | Future client documents | Organisational analysis where necessary | TBD before activation | TBD |
| Donor information | Future client documents | Organisational analysis where necessary | TBD before activation | TBD |
| Beneficiary information | Future client documents | Organisational analysis where necessary | TBD before activation | TBD |
| Potential Article 9 data | Future internal documents | Not required by default; may appear incidentally | Exclude/minimise unless specifically justified | TBD |
| Inferences about identifiable people | Derived from input evidence | Diagnostic support where necessary | Must follow underlying purpose and retention rules | TBD |

## Purpose limitation

The demonstrated MVP mainly uses public evidence and controlled inputs.

The higher-risk reuse occurs if internal documents are added. Those documents may originally have been collected for HR administration, volunteer management, donor management, safeguarding or beneficiary service delivery. Using the same identifiable information for an AI-assisted organisational diagnostic is a separate use and cannot simply be assumed compatible.

Before enabling internal documents, the controller should:

1. identify the original collection purpose;
2. assess compatibility with the new diagnostic purpose;
3. establish whether identifiable information is actually necessary;
4. remove or anonymise unnecessary personal data;
5. establish a lawful basis for the remaining processing.

**Current status: unresolved for production use.**

---

# Phase 2 — Role Map

| Entity | Role | Processing activity | DPA in place? |
|---|---|---|---|
| Client social-impact organisation | Controller | Determines why its information is submitted and what business purpose the diagnostic serves | N/A as controller |
| Intellectus service operator | Likely processor in the intended client-service model | Processes data on the client's instructions to produce diagnostic support | Required before real client personal data is processed |
| Consultant / project team | Depends on operating model | Intake, review and use of diagnostic output | TBD — role should be documented |
| n8n hosting/provider | Processor or subprocessor if hosted infrastructure receives personal data | Workflow orchestration and execution data | TBD |
| Hosting/storage provider | Processor/subprocessor | Application or document storage | TBD |
| External AI provider, if enabled | Processor/subprocessor in the expected service model | Model inference on submitted content | Not part of the demonstrated retained MVP; DPA required before use with personal data |
| External research provider, if client data is transmitted | Processor/subprocessor or separate controller depending on service | Research/enrichment | TBD |

The classification above assumes Intellectus acts only on the client's documented instructions. If the Intellectus operator independently reuses client personal data for its own model training, product development or other purposes, the role analysis would change and cannot be treated as a straightforward processor relationship.

## International transfers

No complete production transfer map is documented.

Before processing real client data, each relevant vendor must be checked for:

- processing and storage region;
- subprocessors;
- access from outside the EEA;
- applicable adequacy decision, SCCs or other transfer mechanism;
- supplementary safeguards where required.

**Current status: cannot determine from the MVP.**

---

# Phase 3 — Lawful Basis Assessment

| Purpose | Proposed lawful basis | Justification | Legal review? |
|---|---|---|---|
| Use public professional information to understand organisational context | Legitimate interests | Bounded professional research may support a legitimate organisational diagnostic, subject to necessity and balancing | Yes — LIA documented below |
| Process consultant/client contact and contextual information | Legitimate interests | Limited business-contact processing is reasonably connected to delivering the consulting service | Yes — LIA documented below |
| Process employee/volunteer data from internal documents | TBD — legal review | The need for identifiable data and compatibility with the original collection purpose are not established | Yes |
| Process donor data | TBD — legal review | Donors may not reasonably expect their information to be reused for AI-assisted diagnostics | Yes |
| Process beneficiary data | TBD — legal review | Potential vulnerability and purpose mismatch materially increase privacy risk | Yes |
| Process Article 9 data | TBD — Article 6 basis plus Article 9 condition required | Article 6 alone is insufficient for special-category processing | Yes |
| Generate recommendations containing personal data | Follows the lawful basis of the underlying processing | AI generation does not create a new lawful basis | Yes where identifiable information is used |

## Legitimate Interests Assessment

### 1. Purpose test

**Public professional research:** The organisation has a legitimate interest in understanding publicly documented facts relevant to its operations and context.

**Client/consultant business context:** There is a legitimate operational interest in receiving the information required to provide the diagnostic service.

**Result:** satisfied in principle.

### 2. Necessity test

Processing should be limited to information that materially contributes to the diagnostic. Identifiable information should not be retained merely because it appears in a source.

Less intrusive alternatives include:

- removing names where roles are sufficient;
- redacting irrelevant information;
- aggregating findings;
- using organisational-level evidence instead of person-level evidence.

**Result:** only satisfied where minimisation is applied.

### 3. Balancing test

Public professional information used in a bounded business context creates a lower privacy impact than private employee, donor or beneficiary data. Nevertheless, individuals may still have privacy interests and rights even where information is publicly accessible.

The balance becomes materially less favourable where the system handles vulnerable people, sensitive information, unexpected secondary uses or person-level inferences.

**Result:** legitimate interests may support bounded public/business-context processing but should not be used as a blanket basis for all future Intellectus processing.

---

# Phase 4 — Risk and Rights Analysis

## Special-category data — Article 9

**Current MVP:** no systematic use of Article 9 information is demonstrated.

**Production risk:** internal documents from social-impact organisations may contain health, disability, ethnic origin, religious beliefs, political opinions, trade-union membership or other sensitive information.

No Article 9 condition is currently documented. Intellectus should therefore default to excluding or redacting these categories unless processing is demonstrably necessary and both a valid Article 6 basis and Article 9 condition are established.

**Assessment: significant prospective gap.**

## Automated decision-making — Article 22

The current system does not make solely automated decisions with legal or similarly significant effects on individuals.

The output supports a consultant's organisational diagnostic and human review is mandatory before client use.

The safeguard must remain meaningful. A consultant should be able to:

- inspect the supporting evidence;
- challenge an inference;
- reject or modify a recommendation;
- identify unknowns and unsupported claims.

If Intellectus later scores, ranks or recommends consequential action concerning identifiable people, the Article 22 assessment must be reopened.

**Current assessment: Article 22 not triggered by the demonstrated use case.**

## DPIA trigger

A formal DPIA screening should be completed before real internal client data is enabled.

| EDPB criterion | Assessment |
|---|---|
| Evaluation or scoring of people | Not part of the current design; could become relevant if person-level evaluation is added |
| Automated decision-making with significant effects | Not demonstrated |
| Systematic monitoring | Not demonstrated |
| Sensitive / special-category data | Potentially applicable with internal client documents |
| Large-scale processing | Not demonstrated |
| Matching or combining datasets | Potentially applicable if multiple client/research sources are combined |
| Vulnerable data subjects | Potentially applicable, particularly beneficiaries |
| Innovative technology | Applicable — AI-assisted diagnostic workflow |
| Processing that may prevent exercise of rights / cross-border complexity | Potentially applicable depending on architecture |

The intended production model could meet at least two criteria, particularly innovative technology combined with vulnerable data subjects, sensitive information or dataset combination.

**Conclusion:** DPIA screening is required before production use with real internal data. If the actual deployment confirms two or more relevant high-risk criteria, a DPIA should be completed before that processing begins.

**Current project status:** no formal DPIA is evidenced.

## Data-subject-rights friction

### Right of access

Personal information could appear in source documents, n8n execution data and generated outputs.

The current project does not demonstrate an end-to-end method for locating all records relating to one person.

**Status: gap for production.**

### Right to rectification

Correcting an original source does not automatically prove that previously generated findings or retained workflow data have also been corrected.

**Status: gap for production.**

### Right to erasure

The MVP does not demonstrate deletion across every potential processing layer, including uploaded documents, application storage, workflow history and future third-party processors.

**Status: gap for production.**

### Right to object

Where legitimate interests is relied upon, the controller needs an operational process for receiving and assessing objections.

**Status: not demonstrated.**

### Operational requirement

A production design should be able to trace:

**data subject → source → processing run → generated output → storage location → deletion/correction action**

without relying on manual guesswork.

---

# Phase 5 — Law Stacking

## AI Act cross-check

**Current hypothesis: minimal/limited-risk decision-support use, not an Annex III high-risk use case.**

Intellectus currently supports an organisational consultant and does not make employment, education, credit, essential-service or other consequential decisions about individuals.

The AI Act can still add governance expectations beyond GDPR, including transparency, AI literacy, documentation and effective human oversight.

This classification must be reassessed if Intellectus is later used to score, rank or recommend consequential actions concerning identifiable individuals.

## ePrivacy check

The demonstrated core workflow does not depend on advertising cookies, tracking pixels, telecommunications metadata or device-level behavioural tracking.

**Current assessment: not applicable to the demonstrated processing.**

If analytics or tracking technologies are added to the production web application, ePrivacy consent requirements must be assessed separately.

## Data Act check

The demonstrated system does not use connected-product data, IoT data or a cloud-switching use case.

**Current assessment: not applicable.**

---

# Accountability Check

Could the current Project 3 documentation alone demonstrate GDPR compliance to a regulator?

**No.**

The technical MVP documents the workflow and review boundary well, but several production compliance artifacts are missing or incomplete.

| Compliance evidence | Current status |
|---|---|
| Data processing brief | Completed in this lab |
| Personal data inventory | Completed as first-pass assessment |
| Controller/processor role map | Provisional |
| Lawful basis assessment | Partial / production legal review required |
| LIA | Preliminary assessment completed |
| Article 9 assessment | Production condition not established |
| DPIA screening | Not formally completed |
| DPIA | Not completed |
| Vendor DPAs | Not evidenced |
| Subprocessor register | Not evidenced |
| International transfer assessment | Not evidenced |
| Privacy notice covering Intellectus processing | Not evidenced |
| Retention schedule | Not evidenced |
| Data-subject-rights procedure | Not evidenced |
| Incident response procedure | Not evidenced |
| Human-review control | Present as a design principle; production governance still required |

---

# Overall Assessment

## PROCEED WITH CONDITIONS

The demonstrated public/demo MVP does not need to be stopped.

The production boundary should, however, remain closed to real internal client personal data until the following minimum controls are completed:

1. lawful basis and purpose compatibility are established for each production processing purpose;
2. unnecessary personal and special-category data are technically minimised before processing;
3. controller/processor roles, DPAs, subprocessors and international transfers are documented;
4. DPIA screening is completed and a DPIA performed if required;
5. retention and data-subject-rights procedures are operational;
6. mandatory consultant review is preserved as an auditable production control.

The central GDPR risk is not the existing public-data demonstration. It is an uncontrolled transition from that evidence boundary to private client documents without adding the governance that the new data requires.