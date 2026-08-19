# Intellectus — GDPR Compliance Recommendation Memo

**To:** Data Protection Officer / Legal Counsel
**Subject:** First-pass GDPR assessment of Intellectus
**Recommendation:** Proceed with conditions

Intellectus can continue toward production, but the current public/demo boundary should remain in place until the system is ready to handle real client personal data. The MVP is comparatively controlled: it relies on bounded public evidence, sample data and mandatory consultant review. The material GDPR risk appears when Intellectus starts accepting internal documents about employees, volunteers, donors or beneficiaries.

Three actions should be completed before that change.

**First, define the permitted data and lawful basis for each purpose.** The client should decide which personal data the diagnostic actually needs, document the original purpose of internal source documents and assess whether reuse for Intellectus is compatible. Legitimate interests may support bounded public professional research, but it should not become a blanket justification for internal personal data. Unnecessary identifiers should be removed before processing, and special-category data should be excluded by default unless an Article 9 condition is established.

**Second, complete the processor and transfer review.** Every production provider involved in hosting, workflow execution, storage, research or AI inference should be mapped. Required DPAs must be in place, subprocessors identified and processing locations confirmed. If data leaves the EEA, the applicable transfer mechanism must be documented rather than assumed.

**Third, complete DPIA screening and make data-subject rights operational.** A production deployment involving vulnerable beneficiaries, sensitive information or combined datasets may meet multiple DPIA criteria. The architecture must also support access, correction and deletion across source documents, workflow records and generated outputs.

Residual risks remain even after these controls. Internal documents may contain unexpected sensitive information; AI-generated analysis can create inaccurate or excessive inferences; and third-party providers introduce continuing retention, transfer and subprocessor risk. Mandatory consultant review should therefore remain a documented approval gate, not simply a user-interface step.

This assessment is not a legal opinion, formal DPIA or certification of compliance. The client's DPO or legal counsel should validate the final production design before real internal personal data is enabled.