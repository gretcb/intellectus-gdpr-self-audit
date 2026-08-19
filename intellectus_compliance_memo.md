# Intellectus — GDPR Compliance Recommendation Memo

**To:** DPO / Legal Counsel, Spanish social-impact organisation  
**Subject:** Privacy conditions for using Intellectus with internal documents  
**Recommendation:** **Proceed with conditions**

Intellectus can continue to move towards production, but real internal documents containing personal data should not enter the workflow until several controls are in place. The design already includes an important safeguard: the diagnostic cannot be used directly and must first be reviewed by a consultant. That review matters, but it does not resolve the underlying questions around lawful basis, data minimisation, third-party providers, international transfers or data-subject rights.

The first priority is to **define the purpose and lawful basis for each type of processing**. The organisation needs to separate information that is genuinely required for the diagnostic from information that simply happens to appear in a document. Employee, volunteer, donor and beneficiary data may have been collected for a different original purpose. Compatibility therefore needs to be assessed, unnecessary identifiers should be removed, and the legal basis should be documented. If Article 9 special-category data appear, they should not be processed unless a valid condition has been established or the data are excluded from the workflow.

The second priority is to **complete the provider and contract map before real data starts moving through the system**. The n8n deployment model, research services, hosting and any external AI provider must be confirmed. Article 28 terms should be in place for processors and subprocessors, and any transfer outside the EEA must have a documented Chapter V mechanism. These points are currently TBD and should not be treated as resolved.

The third priority is to **complete DPIA screening and make retention and data-subject rights operational**. AI-assisted processing is an innovative use of technology, and additional criteria may apply if the deployment involves sensitive data, vulnerable individuals or meaningful dataset combination. The system also needs to support access, correction and deletion across documents, logs, providers and generated outputs.

Residual risks will remain even after these controls are implemented, including unexpected sensitive data in source documents, inaccurate inferences and reliance on third-party providers. Mandatory consultant review should remain a real approval control, with authority to reject conclusions and evidence that the review took place.

This memo is a first-pass compliance assessment. **It is not a legal opinion, a DPIA or a certification of compliance.** The final production design should be validated by the organisation’s DPO or legal counsel before real personal data is processed.