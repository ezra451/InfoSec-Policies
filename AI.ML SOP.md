## Artificial Intelligence Standard Operating Procedure
### 1.	POLICY

It is the policy of [The Company] to design, develop, deploy, and operate Artificial Intelligence (AI) and Machine Learning (ML) systems in a manner that is trustworthy, ethical, compliant, secure, and transparent. This procedure mandates the integration of AI safety, governance, and security best practices, including adherence to the [The Company] AI Use policy and the OWASP Top 10 for LLM Applications and OWASP Top 10 for Machine Learning to protect organizational assets, user privacy, and maintain public trust.  AI/ML initiatives must incorporate risk assessment, mitigation strategies, continuous monitoring, and clear accountability from inception through retirement.
### 2.	PURPOSE / SCOPE		
The primary purpose of this Standard Operating Procedure is to provide a mandatory, structured guidance and framework for managing the entire lifecycle of AI/ML systems and services. It ensures that AI/ML adoption within the organization is consistent, minimizes risks associated with bias, non-compliance, system failure, security vulnerabilities, information integrity and confidentiality, and maximizes the positive impact of AI on business objectives.
This SOP applies to all [The Company] personnel including third-party vendors employed or contracted by [The Company] in the Americas and involved in the design, development, procurement, deployment, use, maintenance, or governance of any system or service utilizing Artificial Intelligence (AI) or Machine Learning (ML) models. This includes:
-	Custom-developed AI/ML models.
-	Commercial Off-The-Shelf (COTS) AI/ML solutions.
-	Integration of third-party AI/ML APIs/services (e.g., Large Language Models - LLMs).
-	Data pipelines and infrastructure used for AI/ML training and inference.

### 3.	ASSOCIATED DOCUMENTS
 3.1.	Artificial Intelligence and Machine Learning Policy
 3.2.	Acceptable Use Policy
 3.3.	Data Security Policy

### 4.	ROLES & RESPONSIBILITIES
 4.1.	IT and Information Security Team: Conducts software and security reviews, manages threat modeling (especially against OWASP Top 10 for AI/ML risks), and implements protective technical and governance controls in deployment environments. May assist others as needed
 4.2.	AI/ML Development Team: Executes the SOP procedures, performs or facilitates Adversarial Testing, maintains complete model documentation, and implements secure coding practices.
 4.3.	Legal and Compliance: Interprets relevant laws and regulations and ensures the SOF and specific AI deployments are compliant.

### 5. DEFINITIONS / EQUIPMENT & MATERIALS
##### 5.1.	AI/ML System: A complete solution comprising the model, training data, inference environment, and all associated data pipelines and user interfaces.
##### 5.2.	Model Card: A standardized document providing essential information about an ML model, including its intended use, performance metrics, training data characteristics, and ethical considerations.
##### 5.3.	Data Poisoning: An attack where a threat actor introduces corrupted data into the training set to subtly alter the model's behavior or degrade its performance.
##### 5.4.	Model Inversion: An attack that attempts to reconstruct the training data, potentially revealing sensitive information about the individuals whose data was used.
##### 5.5.	Prompt Injection: An attack specific to LLMs where malicious input is designed to override the system's instructions or guardrails, forcing it to perform unintended actions (e.g., violating a policy).
##### 5.6.	Adversarial Testing: A security practice involving the creation of deliberately misleading or manipulated inputs (adversarial examples) to test the robustness and security of an AI/ML model.

### 6.	PROCEDURE OVERVIEW DIAGRAM
##### 6.1.	N/A

### 7.	PROCEDURE		
#####  7.1.	The AI/ML lifecycle incorporates security and governance checks into every stage, forming a continuous MLOps loop with integrated Trust and Safety gates.
#####  7.2.	Key Security & Governance Gates:
#####  7.2.1.	Risk Assessment (Pre-Design): Initial assessment to identify potential societal, ethical, and security risks.
#####  7.2.2.	Training Data Vetting (Data Preparation): Auditing data for bias, quality, privacy compliance, and potential poisoning (OWASP ML06: Data Poisoning).
#####  7.2.3.	Adversarial Testing (Modeling & Evaluation): Focused testing to mitigate OWASP LLM01: Prompt Injection and OWASP LLM02: Broken Access Control (via injection) or OWASP ML02: Insecure Model Design.
#####  7.2.4.	Deployment Environment Hardening (Deployment): Securing the infrastructure against OWASP LLM03: Insecure Configuration and OWASP ML04: Insecure Infrastructure.
#####  7.2.5.	Drift Monitoring (Monitoring): Continuous observation for model performance degradation or data drift, which can indicate potential training data or input manipulation.

#### 7.3.	Project Initiation and Ethical Design (Security by Design)
#####  7.3.1.	Approval All new AI/ML projects whether related to a service or new development, must be presented to IT and Information Security for review and approval based on a preliminary risk assessment.
#####  7.3.2.	Threat Modeling: The development team, in collaboration with the Security Team, must perform threat modeling for the AI/ML system, specifically addressing risks from the OWASP Top 10 for AI/ML.
- Focus: OWASP ML01: Model Evasion
-	ML02: Insecure Model Design
-	LLM01: Prompt Injection.

##### 7.3.3	Internal System Documentation (Mandatory): For systems developed by or on behalf of the company, the development team must create the Data Architecture Documentation detailing:
-	Data Handling: The flow of data from ingestion to output.
-	Data Transformation: The algorithms and steps used to clean, label, and feature-engineer the data.
-	Data Storage: Where training and inference data residues are physically and logically stored (including jurisdiction).
- Data Protection: Encryption mechanisms (at rest and in transit), access controls, and retention policies.
-	Data Map or Diagram: Should include the above data sources, processes, transforms, stores. 
##### 7.3.4	Model Card Creation: A preliminary Model Card must be drafted, documenting the intended use, scope, and initial ethical considerations.

#### 7.4	Data Sourcing and Preparation (Preventing Poisoning and Leakage)
##### 7.4.1	Data Vetting and Compliance: All training and testing data must be sourced ethically and comply with the Acceptable Use and related Data Policies. 
###### 7.4.1.1	Personal Identifiable Information (PII) must be anonymized or pseudonymized.
###### 7.4.1.2	Proprietary [The Company] information must be protected.
##### 7.4.2	Poisoning Prevention: Implement robust data validation checks and integrity monitoring to prevent OWASP ML06: Data Poisoning. Training data sources must be authenticated and immutable.
##### 7.4.3	Sensitive Data Handling: Use techniques like Differential Privacy or Federated Learning when handling highly sensitive data to mitigate OWASP ML05: Insecure Data Handling and LLM06: Sensitive Information Disclosure.

#### 7.5	Third-Party AI Systems Vetting and Use
##### 7.5.1	Vendor Trust and Security Assessment (Mandatory): Before contracting any third-party AI service that handles company data (including chatbots, LLMs, or transcription services), the Procurement and InfoSec teams must acquire and review the following vendor documentation:
-	Trust and Privacy: Vendor's public privacy policy, data usage agreements, and Model Card (if available).
-	Data Security Information: SOC 2 Type 2 report, ISO 27001 certificate, or equivalent security audit reports.
-	Data Handling Commitment: Contractual commitment on data retention, deletion, and guarantee that company data will not be used for vendor model retraining.
##### 7.5.2	Transcription and Recording Consent Procedures: For all third-party transcription services, the following procedures are mandatory:
-	Approval Acquisition: The user/system initiating the transcription must obtain, consent from all participants being recorded or transcribed.
-	Proprietary Data Scrubbing: Implement an approved technical process (e.g., regex filtering, PII detection models) to perform Data Scrubbing on audio transcripts for proprietary, financial, or sensitive information before it is stored or transmitted to third-party services.

#### 7.6	Model Development and Validation (Robustness and Security Testing)
###### 7.6.1	Secure Code Review: All model code and ML-Ops pipeline scripts must undergo a security review, looking for vulnerabilities related to OWASP LLM04: Denial of Service or ML07: Improper Error Handling.
###### 7.6.2	Adversarial Testing: The Model Development Team must dedicate resources to Adversarial Testing. This includes:
-	Testing for Prompt Injection (LLM01) by attempting to override system prompts.
-	Testing for Model Inversion (ML08) or Membership Inference attacks to ensure training data cannot be reconstructed.
-	Testing for Evasion Attacks (ML01) by crafting minimal perturbations that cause misclassification.
##### 7.6.3	Bias and Fairness: The model must be evaluated against fairness metrics for different demographic groups to identify and mitigate algorithmic bias. Results must be documented in the Model Card.

#### 7.7	Deployment and Infrastructure Security
##### 7.7.1	Isolation and Access Control: The AI/ML inference environment must be strictly isolated. Implement principle of least privilege and strong authentication to prevent OWASP LLM02: Broken Access Control and ML03: Insecure Access Control.
##### 7.7.2	 Configuration Hardening: Ensure all components, including model servers, APIs, and containers, adhere to hardened configurations to avoid OWASP LLM03: Insecure Configuration and ML04: Insecure Infrastructure. API calls should use signed tokens and rate-limiting.
##### 7.7.3	Input Validation: Implement strict input sanitation and validation at the API gateway to mitigate risks like OWASP LLM05: Overreliance (by rejecting overly complex or ambiguous prompts) and LLM07: Vulnerable Dependencies.

#### 7.8	Monitoring, Maintenance, and Retirement
##### 7.8.1	Continuous Monitoring: Establish real-time monitoring of model performance (drift, accuracy) and security metrics (input attempts, suspicious queries).
##### 7.8.2	Retraining and Patching: Implement a structured process for model retraining or patching to address newly identified security vulnerabilities or performance degradation. This is crucial for mitigating ML09: Improper Error Handling (to prevent leakage) and LLM08: Supply Chain Vulnerabilities.
##### 7.8.3	Incident Response: Define clear procedures for responding to AI/ML specific incidents, such as a successful Data Poisoning attack or a Prompt Injection breach.
##### 7.8.4	Model Retirement: When a model is decommissioned, ensure all associated data, infrastructure, and access tokens are securely purged and archived according to retention policies.

### 8	ATTACHMENTS

### 9	REFERENCES

- OWASP Top 10 for Machine Learning (ML)
- NIST AI Risk Management Framework (AI RMF)

