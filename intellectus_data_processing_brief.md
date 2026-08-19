# Intellectus — Data Processing Brief

## Scenario and scope

This audit covers Intellectus, the AI-assisted organisational diagnostic system built for Project 3.

The demonstrated Project 3 MVP uses the Intellectus web application, n8n-based workflow orchestration, public research and mandatory consultant review. The current public/demo implementation does not claim to process real private client documents.

For GDPR stress-testing, this audit also assesses the intended production boundary in which a Spanish social-impact organisation could submit information about its operations, a description of its challenge and internal documents that may contain personal data relating to employees, volunteers, donors or beneficiaries.

Prospective production risks are clearly separated from controls and data flows demonstrated in the system that was actually built.

The working flow is:

```text
Spanish social-impact organisation
        ↓
Intellectus web application
        ↓
n8n
        ↓
Research services
        ↓
Potential external AI provider
        ↓
Draft diagnostic
        ↓
Mandatory consultant review
        ↓
Client use
```

This assessment distinguishes between three levels of evidence:

- **Observed / stated** — explicitly included in the agreed scenario or project design.
- **Prospective** — relevant to production use with real personal data but not evidenced as implemented.
- **TBD** — facts that are not sufficiently documented and must be confirmed before production.

Lack of evidence is not treated as evidence of compliance.

## Personal data and sources

The scenario may involve personal data because internal documents and external research can refer to identified or identifiable people.

| Data category | Source | Current status |
|---|---|---|
| Names, roles and professional information of employees or volunteers | Internal documents / organisation input | Possible; exact fields TBD |
| Donor information | Internal documents | Possible; detail TBD |
| Beneficiary information | Internal documents | Possible; detail TBD |
| Free text written by or about individuals | Internal documents / challenge description | Possible |
| Professional information from external sources | Research services | Possible; provider and queries TBD |
| Inferences about identifiable individuals | Diagnostic output | Prospective / depends on input |
| Article 9 special-category data | Internal documents | **TBD — not confirmed** |

Internal documents could contain information about health, disability, ethnic origin, religion, political opinions, trade-union membership or other special categories under Article 9.

The scenario does not confirm that these categories are actually present.

The volume, frequency and number of data subjects are also currently unknown.

## Processing purposes

Information is used to:

1. understand the organisation and the challenge being analysed;
2. review internal evidence;
3. supplement the analysis with external research where necessary;
4. identify root causes, evidence gaps and possible actions;
5. prepare a draft organisational diagnostic;
6. submit the diagnostic to human review before it is used with the client.

Identifying an individual is not necessary for every purpose.

Where identity does not add value to the analysis, personal data should be removed, redacted, aggregated, anonymised or pseudonymised as appropriate.

## Processing actors

The Spanish organisation decides why the diagnostic is requested and what information is provided.

The legal role of the Intellectus operator and each third party cannot be determined from the technical architecture alone. Controller, processor and subprocessor roles depend on what each party actually does with the data and whose instructions it follows.

The presence of n8n in the workflow does not, by itself, prove that n8n GmbH processes client content. This depends on whether the deployment is self-hosted or cloud-based.

The identity, location and contractual terms of any external AI provider or research service are also **TBD**.

## Storage and international transfers

The current scenario does not establish where the application, n8n instance, logs, documents, outputs or subprocessors are hosted.

Current status:

- storage location: **TBD**;
- processing location: **TBD**;
- transfers outside the EEA: **TBD**;
- transfer mechanism: **TBD — no adequacy decision or SCCs assumed**;
- retention and deletion periods: **TBD**.

Before real personal data is processed, Intellectus needs a documented map covering providers, subprocessors, hosting regions, retention and data flows.

## Decisions affecting individuals

Intellectus produces an organisational diagnostic.

The scenario requires a consultant to review the diagnostic before it is used with the client.

No hiring, dismissal, ranking, scoring, eligibility decision or other individual decision with legal or similarly significant effects is described.

Based on the available facts, there is no evidence of a decision based solely on automated processing within the meaning of GDPR Article 22.

However, human review must be meaningful. The consultant must be able to inspect the evidence, challenge inferences, and modify or reject conclusions.

Evidence that this review is formally governed and recorded is currently **TBD**.

## Conclusion

Intellectus falls within GDPR scope whenever internal documents or research contain personal data.

The main compliance risk arises when real internal documentation enters a processing chain whose contracts, hosting, retention, transfers and data-subject-rights procedures have not yet been evidenced.

**Production rule:** real personal data should not be sent to any component whose role, contract, location, retention and support for data-subject rights have not been documented.

## References

- GDPR, Articles 4, 5, 6, 9, 22, 28, 35 and 44–46
- EDPB Guidelines 07/2020 on the concepts of controller and processor
- EDPB Guidelines on automated individual decision-making and profiling