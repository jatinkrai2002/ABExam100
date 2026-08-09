# AB-100 Exam Question Bank
### Architect AI Solutions for Business Productivity — Solution Architect Level

Prepared as an internal exam-setter deliverable for jitendraco. Grounded in the two source modules: *Manage testing AI-powered business solutions* and *Design ALM process for AI-powered business solutions* + *Design responsible AI security, governance, risk management, and compliance*.

---

## 0. Exam-Setter Analysis (Summary)

### Top 5 Strongest Questions in This Bank (with reasoning)

| # | Question (short form) | Why it's strong |
|---|---|---|
| 1 | SS-03 (below): Which environment gate criterion applies at Gate D→E in the AI data ALM process | Directly traceable to a specific named phase table in the source; only one option matches the literal gate text — no ambiguity. |
| 2 | MS-02: Select all controls that belong to "defense in depth" for agent security | Source explicitly lists identity, data governance, observability, and threat protection as the layered stack — clean multi-select with a clear boundary between correct/incorrect options. |
| 3 | DD-04: Order the Data ALM phases A→G | Phases are explicitly labeled A through G in sequence in the source — unambiguous correct order, tests real process comprehension not memorization of trivia. |
| 4 | CS-A Q3 (case study): Given a canary rollout requirement, which ALM gate must the team satisfy before Prod | Forces the candidate to apply Gate D→E logic to a scenario rather than recall a list — genuine architect-level reasoning. |
| 5 | YN-01 Q2: "A model can be promoted to Prod without a documented rollback plan." | Tests a hard governance rule (Gate 2 requires rollback plan) with a definitive Yes/No answer traceable to source text — no interpretation needed. |

### 3 Red Flags (recap, see above for full explanation)
1. Out-of-syllabus product/SKU trivia not stated in source text.
2. Heavy redundancy across the three security/governance units risks "which unit is this from" ambiguity — avoid unit-attribution questions.
3. Source diagram defects (duplicate "Level 4" in test maturity ladder) — do not build ordering questions directly from that diagram without correcting it first.

### Strong Sections
- ALM promotion gates (Foundry / custom models / D365 F&SC / Copilot Studio agents) — precise, enumerable criteria.
- Responsible AI's six principles — clean, closed taxonomy.
- Audit trail categories (model changes vs. data changes vs. Foundry control-plane) — well partitioned.
- Data ALM Phase A–G lifecycle — sequential and complete.
- RACI table for AI data — good source for matching/drag-drop.

### Weak Sections
- Copilot test case blueprint table (garbled PDF extraction, columns cut off) — do not test exact field wording.
- Test maturity ladder graphic — contains a duplicate "Level 4" defect; unusable for ordering questions as-is.
- The three overlapping security/governance units — good for concept questions, unsafe for "which module teaches this" questions.

---

## 1. Single-Select Multiple Choice (10) — "Choose the best architectural decision"

**SS-01**
A solution architect is designing an environment strategy for Copilot Studio agents, connectors, and actions. The customer wants to guarantee no untested change reaches end users directly.
Which environment design principle should the architect enforce?

- A. Allow direct editing in Production for urgent fixes
- B. Use managed solutions only in Test and Prod, with no direct editing in Production
- C. Use a single shared environment for Dev, Test, and Prod to reduce cost
- D. Allow makers to publish directly from Dev to Prod

**Answer: B** — The source explicitly lists "No direct editing in production" and "Managed solutions only in Test and Prod" as core environment design principles for Copilot Studio ALM.

---

**SS-02**
An architect must decide how a Copilot-driven test case generation strategy is initiated. What should be defined *before* Copilot is used to generate test cases?

- A. The number of Copilot licenses required
- B. The testing objectives (test categories, business rules, risks, compliance requirements)
- C. The UI theme for the test dashboard
- D. The Azure region hosting the test environment

**Answer: B** — Section 2.1 "Define the testing objectives" is explicitly the required first step before prompting Copilot.

---

**SS-03**
In the AI data ALM process, which of the following is required as evidence at **Gate D → E (Stage & Approve → Deploy & Serve)**?

- A. A signed reproducibility log only
- B. CAB approval, deployment runbooks, and rollback plans
- C. A profiling report and lineage IDs
- D. A data contract and catalog policy proof

**Answer: B** — Per the Gate table, Gate D→E requires "CAB approval; deployment runbooks and rollback plans ready."

---

**SS-04**
A team is designing a promotion path for a Microsoft Foundry agent. Which activity belongs specifically to **Promotion Gate 2 (Test → Prod)**, not Gate 1 (Dev → Test)?

- A. Initial safety and guardrail checks
- B. Verification of data source mappings
- C. Human validation of agent reasoning
- D. Code or prompt quality review

**Answer: C** — "Human validation of agent reasoning" is listed only under Gate 2 (Test → Prod); the other three are Gate 1 criteria.

---

**SS-05**
An architect is designing identity for AI agents operating across Microsoft clouds. What is the recommended authentication approach for agent-to-Azure calls?

- A. Static API keys stored in the agent configuration
- B. Shared service principal credentials across all agents
- C. Managed identities to remove secrets and simplify rotation
- D. User-delegated OAuth tokens cached indefinitely

**Answer: C** — The source states "Prefer managed identities for agent-to-Azure authentication to remove secrets and simplify rotation."

---

**SS-06**
Which control is described as enforcing that agents only use data "in the right places, for the right duration"?

- A. Threat protection
- B. Data governance and protection (DLP, sensitivity labels, residency, retention)
- C. Observability and cost governance
- D. Development and interoperability standards

**Answer: B** — This is the stated goal of the "Data governance and protection" section.

---

**SS-07**
A financial services customer requires that AI-driven journal postings and purchase order approvals cannot occur without safeguards. Which control category from the D365 Finance and Supply Chain ALM unit directly addresses this?

- A. Version control for models
- B. Guardrails for business-critical processes (e.g., posting journals, approving purchase orders)
- C. Synthetic dataset generation
- D. Environment variables for endpoints

**Answer: B** — Explicitly named under "Risk & Compliance Controls" in the D365 F&SC ALM unit.

---

**SS-08**
Which of the following best distinguishes the "red" dataset from the "gold" dataset in the environment strategy for AI data ALM?

- A. Red is used only in Production; gold is used only in Dev
- B. Red is mutable and experimental; gold is frozen and promoted
- C. Red contains PII; gold never contains PII
- D. Red and gold refer to model versions, not datasets

**Answer: B** — Directly stated: "Red gold datasets pattern: red (mutable, experimental) vs. gold (frozen, promoted)."

---

**SS-09**
An architect reviewing an AI solution for Responsible AI adherence needs to evaluate whether the system "empowers people of all abilities and backgrounds." Which RAI principle does this map to?

- A. Fairness
- B. Transparency
- C. Inclusiveness
- D. Accountability

**Answer: C** — Inclusiveness is defined exactly this way in the RAI principles list.

---

**SS-10**
When validating data residency for a Copilot Studio agent, what should the architect confirm regarding unpublished agents and preview features?

- A. They always share identical residency rules with published agents
- B. They may follow different residency rules than published agents and must be validated separately
- C. They are exempt from all residency requirements
- D. They automatically inherit tenant-wide DLP policy with no further review needed

**Answer: B** — The source explicitly instructs architects to validate "Whether unpublished agents and preview features follow different residency rules."

---

## 2. Multi-Select Multiple Choice (10) — "Select two or three correct answers"

**MS-01** (Select 3)
Which of the following are explicitly listed as AI assets that must be governed under ALM for Copilot Studio?

- A. Agents (conversational or autonomous)
- B. Custom connectors
- C. Actions, skills, and prompt assets
- D. The end user's personal calendar
- E. Employee performance reviews

**Answer: A, B, C**

---

**MS-02** (Select 3)
Per the "defense in depth" approach to AI agent security, which controls form part of the layered posture?

- A. Identity and access boundaries
- B. Secure data governance
- C. Disabling all logging to reduce cost
- D. Monitoring and anomaly detection
- E. Granting broad access "just in case" a future task needs it

**Answer: A, B, D**

---

**MS-03** (Select 2)
Which two elements are required as evidence for **Gate 2 (Test → Prod)** in the custom AI model ALM lifecycle?

- A. Security and compliance approvals granted
- B. Rollback plan confirmed
- C. Training data meets quality standards
- D. Documentation created

**Answer: A, B** (C and D belong to Gate 1: Dev → Test)

---

**MS-04** (Select 3)
Which of the following are named Responsible AI principles in the source material?

- A. Fairness
- B. Reliability and Safety
- C. Scalability
- D. Privacy and Security
- E. Portability

**Answer: A, B, D**

---

**MS-05** (Select 2)
Which two practices are recommended to reduce AI model drift and data poisoning risk?

- A. Track data lineage for all training sources
- B. Disable retraining permanently once a model reaches production
- C. Validate newly introduced data before use in retraining pipelines
- D. Allow unrestricted public internet ingestion for freshness

**Answer: A, C**

---

**MS-06** (Select 3)
Which categories of AI vulnerabilities are explicitly described in the "Analyze AI vulnerabilities" unit?

- A. Prompt manipulation risks
- B. Model behavior vulnerabilities
- C. Data exposure vulnerabilities
- D. Network cable degradation
- E. Identity, access, and RBAC gaps

**Answer: A, B, C, E** — *(Note: this is actually 4 correct; use as a "select all that apply" variant, or trim option E to force exactly 3 — flagged for calibration.)*

---

**MS-07** (Select 2)
Which two controls are recommended specifically for securing grounding data retrieval workflows (e.g., RAG)?

- A. Connector-level authorization restricting which data types the model can query
- B. Allowing the model unrestricted field access to improve recall
- C. Structured query filtering preventing access to disallowed fields
- D. Removing all logging to reduce retrieval latency

**Answer: A, C**

---

**MS-08** (Select 3)
Which of the following are listed as recommended environments in the ALM strategy for AI in Dynamics 365 Customer Service / Customer Engagement?

- A. Development (DEV)
- B. Test/Validation (TEST)
- C. Sandbox-of-Sandboxes (nested sandbox)
- D. Pre-Production (UAT/PREPROD)
- E. Production (PROD)

**Answer: A, B, D, E** — *(4 correct — same calibration note as MS-06; consider trimming distractors to force exactly 3.)*

---

**MS-09** (Select 2)
According to the audit trail unit, which two attributes should recommended audit logs include?

- A. Immutable, timestamped change records
- B. Full raw content of every prompt and dataset for convenience
- C. Role-based attribution linked to identity provider
- D. Automatic deletion after 24 hours regardless of workload risk

**Answer: A, C** — (B is explicitly discouraged: "logs capture metadata, not content, to avoid unnecessary exposure.")

---

**MS-10** (Select 3)
Which of these are named as AI assets to govern in the D365 Finance and Supply Chain ALM unit?

- A. AI models (prediction, scoring, classification, anomaly detection)
- B. Prompts and instructions for Copilot assistance
- C. Knowledge sources (documents, task guides, structured data entities)
- D. Employee salary bands
- E. Marketing campaign creative assets

**Answer: A, B, C**

---

## 3. Drag-and-Drop (10)

**DD-01 — Match the ALM environment to its purpose (D365 F&SC)**
Match: DEV / TEST / PROD
Targets:
1. Execute approved AI capabilities in live financial and supply chain workloads
2. Build and iterate AI models, prompts, orchestration logic, and integrations
3. Validate with safe, anonymized production-like data; perform regression checks

**Answer:** DEV→2, TEST→3, PROD→1

---

**DD-02 — Order the Action lifecycle (Copilot Studio ALM)**
Items: Build, Design, Monitor, Promote, Validate

**Answer (correct order):** Design → Build → Validate → Promote → Monitor

---

**DD-03 — Match the RAI principle to its definition**
Match: Fairness / Transparency / Accountability / Privacy and Security
Targets:
1. Solutions should be understandable, with clear disclosures on how AI is used
2. AI systems should treat all groups equitably
3. Organizations retain responsibility for decisions made by AI
4. Protect personal and organizational data through strong controls

**Answer:** Fairness→2, Transparency→1, Accountability→3, Privacy and Security→4

---

**DD-04 — Order the AI Data ALM Phases**
Items: Deploy & Serve, Plan & Catalog, Develop & Evaluate, Ingest & Prepare, Stage & Approve, Operate & Monitor, Evolve & Retire

**Answer (correct order = A→G):**
Plan & Catalog → Ingest & Prepare → Develop & Evaluate → Stage & Approve → Deploy & Serve → Operate & Monitor → Evolve & Retire

---

**DD-05 — Match the control area to its Gate in the AI Data ALM Gate table**
Match: A→B / B→C / C→D / D→E / E→F
Targets:
1. Evaluation & safety
2. Compliance & residency
3. Catalog & ownership
4. Runtime readiness
5. Data quality & lineage

**Answer:** A→B→3, B→C→5, C→D→1, D→E→2, E→F→4

---

**DD-06 — Match the connector release flow step to its position**
Items: Apply DLP, Approve Security, Author, Publish to Prod, Validate Auth

**Answer (correct order):** Author → Validate Auth → Apply DLP → Approve Security → Publish to Prod

---

**DD-07 — Match the RACI role to its accountability for Residency Configuration (AI data RACI table)**
Match: Data Owner / AI Architect / Security-Compliance / Platform Admin
Targets: Consulted / Accountable / Responsible / Responsible

**Answer:** Data Owner→Consulted (C), AI Architect→Accountable (A), Security/Compliance→Responsible (R), Platform Admin→Responsible (R)

---

**DD-08 — Order the Responsible AI Lifecycle stages**
Items: Build, Deploy, Design, Monitor, Validate

**Answer (correct order):** Design → Build → Validate → Deploy → Monitor

---

**DD-09 — Match the vulnerability category to its example**
Match: Prompt manipulation / Data exposure / Identity & RBAC gaps / Agent workflow vulnerability
Targets:
1. Excessive permissions allow the model to access data it doesn't need
2. "Ignore previous instructions…" style override attempts
3. Autonomous tool use without proper guardrails
4. Attacker interacts with the model using elevated privileges

**Answer:** Prompt manipulation→2, Data exposure→1, Identity & RBAC gaps→4, Agent workflow vulnerability→3

---

**DD-10 — Order the Continuous Improvement loop (Copilot Studio ALM)**
Items: Analyze, Improve, Monitor, Release, Validate

**Answer (correct order):** Monitor → Analyze → Improve → Release → Validate → (loops back to Monitor)

---

## 4. Dropdown / Complete-the-Diagram (10)

**DO-01**
"In the Environment & Data Flow diagram, data moves from Dev (Red data) → Test (Repro runs, evaluation sets) → Pre-Prod (___) → Prod (Gold only)."
Options: [Gold candidates | Raw ingestion | Draft prompts | Archived snapshots]

**Answer: Gold candidates**

---

**DO-02**
"In the Residency Decision Tree, if in-region capacity is unavailable and overflow is allowed for the workload tier, the architect should ___."
Options: [Block the feature entirely | Enable cross-region processing under admin control | Delete the workload | Migrate the entire tenant]

**Answer: Enable cross-region processing under admin control**

---

**DO-03**
"In the RBAC design table, the Publisher role is scoped with ___ at the Azure Roles level."
Options: [Least privilege | Full Owner access | No access | Global Admin]

**Answer: Least privilege**

---

**DO-04**
"In the Data Governance Layers diagram, the layer that sits between 'Agent Runtime' and 'User Output & Logging' is ___."
Options: [DLP & Sensitivity Filters | Marketing Automation | Payment Processing | Identity Federation]

**Answer: DLP & Sensitivity Filters**

---

**DO-05**
"In the Retrieval Access Flow for grounding data, the correct order is: Prompt → ___ → Search Index → Sanitization Layer → Model Context Injection."
Options: [Policy Check | Billing Check | UI Rendering | Backup Snapshot]

**Answer: Policy Check**

---

**DO-06**
"In the Model Hardening Blueprint, Step 2 ('Private Endpoints') focuses on ___."
Options: [Using private network endpoints to limit exposure and control access | Detecting prompt injection | Validating training data lineage | Setting retention policy]

**Answer: Using private network endpoints to limit exposure and control access**

---

**DO-07**
"On the Copilot Studio environment diagram, DEV is (Unmanaged), TEST is (Managed), and PROD is (___)."
Options: [Managed | Unmanaged | Hybrid | Sandboxed]

**Answer: Managed**

---

**DO-08**
"In the AI Data ALM Gate table, the evidence required at Gate B→C is ___."
Options: [Profiling report; lineage IDs | CAB approval | Dashboards; alarms; budget guard | Residency mapping; approval memo]

**Answer: Profiling report; lineage IDs**

---

**DO-09**
"In the Copilot test case strategy map, after 'Copilot Test Case Drafts,' the next stage is ___."
Options: [Architect Validation Pass | Final Test Case Library | Business Requirements | Architect Prompt Plan]

**Answer: Architect Validation Pass**

---

**DO-10**
"In the D365 F&SC environment table, the environment used to 'Validate with safe, anonymized production-like data' is ___."
Options: [TEST | DEV | PROD | Sandbox-Preview]

**Answer: TEST**

---

## 5. Case Studies (2–3 scenarios, 8 questions total)

### Case Study A — Contoso Retail Customer Service Copilot (3 questions)

**Scenario:** Contoso is deploying a Copilot Studio agent for Dynamics 365 Customer Service to summarize cases and suggest next-best actions. The agent will access customer interaction data, case history, and knowledge articles. Compliance requires that no direct edits happen in Production and that all prompts undergo regression testing before release. The security team also requires that sensitive customer data never appears in agent prompts unnecessarily.

**A-Q1.** Which environment should the team use to run regression tests for prompts, summarization consistency, and classification accuracy before Pre-Production?
- A. Dev
- B. Test/Validation
- C. Prod
- D. Pre-Prod only

**Answer: B (Test/Validation)** — regression testing for prompts and classification accuracy is explicitly assigned to the Test/Validation environment.

**A-Q2.** Which principle should guide how much customer data is exposed to the model in prompts?
- A. Maximize context by including full case history in every prompt
- B. Data minimization — use the minimum data required for the model's purpose
- C. Include raw PII to improve summarization accuracy
- D. Data does not need governance once inside a prompt

**Answer: B** — "Data minimization: Use the minimum data required for the model's purpose" is an explicit model security control.

**A-Q3.** Before deployment to Prod, which artifact confirms the release is safe to ship per the AI Release Readiness Checklist for D365 AI?
- A. A checklist confirming data quality, knowledge source alignment, prompt regression testing, safety/compliance verification, environment variables, deployment pipeline success, and monitoring dashboards readiness
- B. A single sign-off email from the product owner
- C. A verbal confirmation from the Dev team lead
- D. Nothing — Copilot Studio auto-validates releases

**Answer: A** — directly matches the "AI Release Readiness Checklist" items listed in the source.

---

### Case Study B — Fabrikam Finance AI Forecasting Model (3 questions)

**Scenario:** Fabrikam is building a custom AI model to predict cash flow anomalies for Dynamics 365 Finance. The model must pass through Dev → Test → Prod, comply with data residency rules for financial data, and be monitored for prediction drift after go-live.

**B-Q1.** Which gate criteria must be satisfied before this model can move from Test to Prod?
- A. Only that training data meets quality standards
- B. Model evaluation thresholds met, no bias/unsafe output, performance verified under ERP workload constraints, security/compliance/residency reviews complete, and deployment package approved
- C. A single stakeholder sign-off with no formal evaluation
- D. Completion of Dev-stage prompt drafting only

**Answer: B** — this matches Gate 2 (TEST → PROD) criteria in the D365 F&SC ALM unit exactly.

**B-Q2.** After go-live, what should the team monitor to detect whether the model's predictions are degrading over time?
- A. UI click-through rate only
- B. Prediction drift (accuracy changes over time) and data drift (input patterns deviating from training data)
- C. Number of licenses consumed
- D. Screen resolution compatibility

**Answer: B** — explicitly named under "Operational Monitoring" in the D365 F&SC unit.

**B-Q3.** Which control specifically protects financial data residency requirements for this model?
- A. Sensitivity labelling enforcement and data residency requirements for financial data
- B. Reducing model parameter count
- C. Increasing token limits
- D. Disabling audit logging to reduce noise

**Answer: A** — listed directly under "Risk & Compliance Controls."

---

### Case Study C — Northwind Traders Security Review (2 questions)

**Scenario:** Northwind's security team is reviewing an autonomous AI agent that reads support tickets and updates a knowledge base automatically. The review must assess identity design, data boundaries, and incident response readiness.

**C-Q1.** What is the recommended way to assign the agent's identity across Dev, Test, and Prod?
- A. Share a single identity across all environments for simplicity
- B. Assign a unique cloud identity per agent, per environment (prod, pre-prod, dev), with recorded ownership, version, and lifecycle metadata
- C. Use the security architect's personal credentials
- D. No identity is required for read-only agents

**Answer: B** — directly stated under "Agent identity."

**C-Q2.** As part of incident response readiness, what should be predefined for this agent?
- A. Steps to disable a compromised model endpoint, preserve logs, notify stakeholders, and recover safely
- B. A plan to permanently delete all logs immediately after any incident
- C. A policy that agents can never be disabled once published
- D. Nothing formal — ad hoc response is sufficient for read-only agents

**Answer: A** — matches "Incident response for AI models" guidance exactly.

---

## 6. Yes/No Hotspot Questions (cannot be revisited after submission)

### Hotspot Scenario 1 — Copilot Studio Agent Governance
*A company deploys a Copilot Studio agent that reads ticket data and updates knowledge articles automatically. Read each statement and select Yes or No.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | The agent should be granted broad, standing access to all knowledge sources "in case it needs them later." | **No** | Violates least-privilege / data minimization principles stated throughout the security and governance units. |
| 2 | Publishing changes to Production requires an approval workflow, not direct editing. | **Yes** | "No direct editing in production" and "Require approvals for publishing to production" are explicit environment design principles. |
| 3 | Once deployed, the agent requires no further evaluation because it passed initial testing. | **No** | Source requires "Scheduled reviews for accuracy, data freshness, and risk reassessment" as ongoing lifecycle governance — agents are never "set and forget." |

---

### Hotspot Scenario 2 — Custom AI Model Promotion
*An architect is preparing to promote a custom AI model for cash-flow anomaly detection from Test to Production.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | A model can be promoted to Prod without a documented rollback plan if the evaluation metrics are strong. | **No** | Gate 2 (Test→Prod) explicitly requires "Rollback plan confirmed" as a mandatory criterion, independent of evaluation results. |
| 2 | Security and compliance approvals are required before promotion. | **Yes** | Explicitly listed under Gate 2 (Test → Prod) criteria. |
| 3 | Training on production knowledge sources is acceptable during the Develop & Evaluate phase to improve accuracy. | **No** | The source states "Train/iterate using Dev/Test data; never train on production knowledge." |

---

### Hotspot Scenario 3 — Data Residency and Compliance
*A regulated customer wants to validate that a generative AI feature does not move data outside its approved region.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | All Copilot Studio agents follow identical data residency rules regardless of publish status. | **No** | Source explicitly instructs validating "whether unpublished agents and preview features follow different residency rules." |
| 2 | DLP rules can be used to prevent sensitive data from being used in AI prompts or outputs. | **Yes** | Explicitly stated under Purview controls for Microsoft 365 Copilot. |
| 3 | In a regulated scenario, cross-region overflow processing should be enabled by default for performance. | **No** | Source states: "In regulated scenarios, set the default to in-region and require explicit approval to enable overflow processing." |

---

## Calibration Notes for the Exam Committee
- **MS-06 and MS-08** currently have 4 correct answers against a "select 3" instruction — either expand to "select all that apply" or trim one distractor before publishing.
- Avoid sourcing any drag-and-drop/ordering item from the **Copilot Test Maturity Ladder** graphic until the duplicate "Level 4" defect in the source PDF is corrected — currently unusable for a scored item.
- Recommend a technical review pass on the Copilot test case blueprint table (garbled column text in source) before building any exact-field-recall questions from it.
