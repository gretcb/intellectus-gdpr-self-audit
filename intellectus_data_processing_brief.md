# Intellectus — Data Processing Brief

## System and scope

Intellectus is a consultant-facing diagnostic system developed for social-impact organisations. It helps structure an organisational challenge, gather and separate evidence from assumptions, identify gaps and root causes, and prepare a draft diagnostic for consultant review.

The current Project 3 MVP and the intended production model need to be separated for GDPR purposes. The demonstrated MVP uses bounded public evidence, controlled fixtures and sample data. The public project repository does not contain private client datasets. A future deployment, however, could allow a client to submit internal documents containing personal data.

## Personal data

### Demonstrated MVP

Personal data may arise indirectly in public-source research, for example:

- names of founders, directors or employees;
- professional roles;
- public professional statements;
- other information relating to identifiable people contained in public sources.

Public availability does not by itself remove information from GDPR scope.

The MVP also processes consultant-entered organisational context and controlled fictional/sample records.

### Intended production use

If internal client documents are enabled, Intellectus could additionally receive:

- employee and volunteer names and roles;
- professional contact information;
- comments written by or about individuals;
- consultant notes referring to identifiable people;
- donor information;
- beneficiary information;
- attributes or inferences generated from those materials.

Internal documents may also contain Article 9 data, including health, disability, ethnicity, religious or political beliefs, trade-union membership or other special-category information. Intellectus does not need these categories by default, so their ingestion should not be treated as necessary simply because they appear in a source document.

## Sources

The demonstrated workflow uses:

1. consultant/user input through the web interface;
2. public web research;
3. a local RAG knowledge corpus;
4. controlled fixtures and retained sample runs.

A future production workflow may also use internal organisational documents and consultant notes supplied by the client.

## Purposes

Information is processed to:

1. understand the organisation and its challenge;
2. identify evidence, unknowns and gaps;
3. support root-cause analysis;
4. develop priorities, recommendations and KPIs;
5. prepare a draft diagnostic for consultant review.

The system does not need to identify individuals for every one of these purposes. Where identity adds no analytical value, personal data should be removed, redacted, aggregated or anonymised before processing.

## Processing chain

The demonstrated path is:

Client / Consultant input
→ Intellectus web application
→ n8n workflow orchestration
→ public research and specialist analysis
→ structured validated response
→ consultant review
→ client-facing diagnostic

The current retained MVP does not establish that a production external LLM processes private client data.

If a hosted AI provider, hosted n8n service, cloud storage provider or additional research vendor is introduced, its role, DPA, processing location, subprocessors and transfer mechanism must be checked before personal data is sent to it.

## Storage and processing location

The Project 3 documentation does not establish a complete production hosting model, retention schedule or international-transfer mechanism for real client data.

Current status:

**TBD — vendor and legal review before production use.**

No EU-only hosting, adequacy decision or Standard Contractual Clauses are assumed without evidence.

## Decisions affecting individuals

Intellectus is designed as consultant decision support, not as an autonomous decision-maker about individuals.

It does not currently hire, dismiss, rank, score, approve or reject employees, volunteers, donors or beneficiaries. A consultant must review the evidence, hypotheses and proposed recommendations before an output is used with a client.

On the current facts, the system does not perform solely automated decision-making with legal or similarly significant effects under Article 22. This conclusion would need to be revisited if future versions were used to evaluate or recommend actions concerning identifiable individuals.

## Current conclusion

The demonstrated MVP has limited personal-data exposure. The material GDPR risk appears when moving from public/demo evidence to real internal client documents.

Before that transition, Intellectus needs documented lawful bases, purpose limitation, minimisation rules, processor governance, retention, transfer controls, data-subject-rights procedures and formal DPIA screening.