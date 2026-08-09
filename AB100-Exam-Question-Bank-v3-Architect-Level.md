# AB-100 Exam Question Bank — v3 (Architect Level, Difficulty 9/10)

These questions require synthesizing multiple units at once (ALM gates + security + residency + testing + governance in a single scenario), the way a real solution architect has to reconcile competing constraints for one customer. Every "wrong" option is wrong for a specific, defensible reason — not just a distractor.

---

## 1. Drag-and-Drop (10) — Architect Level

**DD-01 — Multi-Agent Deployment Under Conflicting Constraints**
A global insurer is deploying three AI components for a claims-automation solution:
- A Copilot Studio agent that drafts customer correspondence (low risk, high change frequency)
- A Microsoft Foundry agent that adjudicates claims under $5,000 autonomously (high risk, regulated action)
- A custom fraud-detection model retrained monthly (high risk, drift-sensitive)

Constraints:
- The Foundry agent's autonomous adjudication is a "data-modifying, high-risk action" requiring the strictest promotion controls.
- The fraud model must never see production claims data during training.
- The correspondence agent changes weekly and cannot tolerate multi-day release cycles.

Match each component to the correct promotion/deployment pattern.

**Items:** Fast automated pipeline with lightweight Gate 1 checks and frequent Dev→Test→Prod cycles | Full Gate 1 + Gate 2 promotion with mandatory human validation of reasoning, rollback plan, and CAB approval before Prod | Automated pipeline with strict Dev/Test-only training data enforcement, golden-set evaluation, and Model Card produced before promotion

**Targets:** Copilot Studio correspondence agent | Foundry claims-adjudication agent | Fraud-detection model

**Answer:**
- Correspondence agent → Fast automated pipeline, lightweight Gate 1, frequent cycles (low risk, high change velocity — heavyweight CAB gating here would be over-engineering and fail the "cannot tolerate multi-day cycles" constraint)
- Foundry adjudication agent → Full Gate 1 + Gate 2 with human validation, rollback, CAB approval (high-risk, data-modifying action explicitly requires this per Promotion Gate 2 criteria)
- Fraud-detection model → Automated pipeline with Dev/Test-only training enforcement + golden-set evaluation + Model Card (matches the "never train on production data" constraint and custom-model ALM requirements)

*Architect trap: a naive answer applies the same heavyweight gate to all three, which fails the correspondence agent's velocity constraint and is over-governed; an equally naive answer applies the lightweight pattern to all three, which violates the adjudication agent's regulatory risk.*

---

**DD-02 — Residency vs. Latency Trade-off**
A EU-based bank requires in-region data processing by default. A US subsidiary needs low-latency access to the same Copilot Studio agent for a pilot. Order the correct decision sequence per the Residency Decision Tree, given the pilot is *not* pre-approved for overflow.

**Items:** Block the feature for the US subsidiary or defer until overflow is approved | Check if in-region capacity is available | Check if overflow is allowed for this workload tier | Enable cross-region processing under admin control

**Answer (correct order):**
Check if in-region capacity is available → (No) → Check if overflow is allowed for this workload tier → (Not pre-approved = No) → Block the feature for the US subsidiary or defer until overflow is approved
*(Note: "Enable cross-region processing under admin control" is a distractor — it only applies if overflow IS allowed, which this scenario explicitly rules out.)*

---

**DD-03 — Layered Security Control Mapping Under a Prompt-Injection Incident**
A support agent was found to leak internal pricing data after a crafted prompt-injection attempt embedded in an uploaded PDF. Match each remediation to the correct control layer it primarily addresses.

**Items:** Sanitize tool inputs and strip unsafe embedded content from uploaded files | Apply DLP policy to block pricing data from appearing in outputs | Restrict the agent's connector scope so pricing tables aren't queryable at all | Add anomaly alerting for unusual data-access spikes

**Targets:** Input/output filtering | Data governance (DLP/sensitivity) | Identity & access (least privilege) | Observability

**Answer:**
- Input/output filtering → Sanitize tool inputs and strip unsafe embedded content
- Data governance → Apply DLP policy to block pricing data in outputs
- Identity & access → Restrict connector scope (least privilege)
- Observability → Anomaly alerting for data-access spikes
*(Architect insight: this is a layered-defense question — a single fix is insufficient; the real answer is that all four apply simultaneously, but each maps to a distinct control layer, which is what a defense-in-depth review actually checks for.)*

---

**DD-04 — Ordering a Cross-Module ALM Release for a Regulated Workload**
A pharmaceutical company's Foundry agent uses grounding data from Dataverse and a custom model trained on clinical trial data. Order the correct end-to-end release sequence combining data ALM and agent ALM.

**Items:** Freeze gold datasets and sign immutability attestations | Deploy validated agent bundle to Prod with region/residency enforcement | Run evaluation suite on golden sets and produce Model Card | Execute canary runs using masked/representative Prod-like data | Ingest and profile clinical trial data, generate lineage

**Answer (correct order):**
Ingest and profile clinical trial data, generate lineage → Run evaluation suite on golden sets and produce Model Card → Execute canary runs using masked/representative Prod-like data → Freeze gold datasets and sign immutability attestations → Deploy validated agent bundle to Prod with region/residency enforcement

---

**DD-05 — Matching Testing Types to a Multi-App Regulatory Scenario**
A logistics firm needs to validate an AI solution spanning Dynamics 365 Supply Chain, Finance, and a Foundry agent that reroutes shipments automatically. Match the correct testing type to each requirement.

**Items:** Confirms shipment reroute logic doesn't violate customs/compliance rules under edge-case inputs | Confirms data consistency when a shipment update in Supply Chain triggers a Finance ledger entry | Confirms the agent doesn't regress after a prompt template change | Confirms the reasoning quality of the agent's autonomous rerouting decision

**Targets:** Scenario/edge-case testing | Integration/end-to-end testing | Regression testing | Model/agent behavior evaluation

**Answer:**
- Customs/compliance edge cases → Scenario/edge-case testing
- Supply Chain→Finance data consistency → Integration/end-to-end testing
- No regression after prompt change → Regression testing
- Reasoning quality of autonomous decision → Model/agent behavior evaluation

---

**DD-06 — Order the Incident Response Sequence for a Compromised Model Endpoint**
A model endpoint is suspected of leaking training data. Order the correct incident response sequence.

**Items:** Restore service using a prior validated version after root cause is addressed | Disable the compromised endpoint | Notify stakeholders and begin investigation | Preserve inference logs and model artifacts for forensic analysis

**Answer (correct order):** Disable the compromised endpoint → Preserve inference logs and model artifacts for forensic analysis → Notify stakeholders and begin investigation → Restore service using a prior validated version after root cause is addressed

---

**DD-07 — Matching RACI Roles to a Cross-Border Data Movement Decision**
A multinational retailer needs sign-off to enable cross-region overflow for an AI workload. Match each role to its RACI designation for "Residency configuration," per the AI data RACI table.

**Items:** Data Owner | AI Architect | Security/Compliance | Platform Admin

**Targets:** Consulted | Accountable | Responsible | Responsible

**Answer:** Data Owner → Consulted; AI Architect → Accountable; Security/Compliance → Responsible; Platform Admin → Responsible
*(Architect trap: many candidates assume Security/Compliance is Accountable for a compliance decision — but the source table places Accountability with the AI Architect, who owns the overall design decision, while Security/Compliance is Responsible for execution.)*

---

**DD-08 — Order a Model Retraining Cycle Triggered by Detected Drift**
A demand-forecasting model shows accuracy degradation flagged by drift monitoring. Order the correct remediation sequence.

**Items:** Redeploy through Gate 1 and Gate 2 promotion checks | Detect drift vs. baseline metrics | Retrain using updated, versioned Dev/Test data | Re-run evaluation suite against golden sets | Trigger an incident/backlog item with trace IDs

**Answer (correct order):** Detect drift vs. baseline metrics → Trigger an incident/backlog item with trace IDs → Retrain using updated, versioned Dev/Test data → Re-run evaluation suite against golden sets → Redeploy through Gate 1 and Gate 2 promotion checks

---

**DD-09 — Matching Governance Controls to Agent Personas in a Zero-Trust Design**
A manufacturer is designing three agent personas: a read-only analytics agent, an agent that updates inventory records, and an agent that can trigger supplier payments. Match the appropriate access pattern to each persona.

**Items:** Read-only RBAC scope with no write actions enabled | Scoped write access to inventory tables only, with DLP on export actions | Scoped write access plus mandatory multi-step human approval before execution, with full audit trail

**Targets:** Analytics agent | Inventory-update agent | Supplier-payment agent

**Answer:**
- Analytics agent → Read-only RBAC scope
- Inventory-update agent → Scoped write access to inventory tables + DLP on export
- Supplier-payment agent → Scoped write access + mandatory multi-step approval + full audit trail
*(This mirrors "Restrict privileged access... require multi-step approvals for sensitive model updates" applied to agent action design, not just model updates — a legitimate extrapolation an architect must reason through.)*

---

**DD-10 — Order the Responsible AI Review Combined with a Fairness Finding**
During a Responsible AI review, a fairness testing pass reveals disparate outcomes for one customer segment. Order the correct remediation sequence.

**Items:** Redeploy after governance board sign-off | Document the fairness gap and root cause in the RAI review report | Apply mitigation (data rebalancing, threshold adjustment) and re-test | Escalate to governance board for review of significant model changes | Detect and validate the disparate impact using fairness testing on real-world scenarios

**Answer (correct order):** Detect and validate the disparate impact using fairness testing → Document the fairness gap and root cause in the RAI review report → Apply mitigation and re-test → Escalate to governance board for review of significant model changes → Redeploy after governance board sign-off

---

## 2. Drop-Down / Diagram Completion (10) — Architect Level

**DO-01**
A bank's AI architecture diagram shows: Data Sources → Agent Runtime → [___] → User Output & Logging. The bank has just added a *new* requirement: block outbound transmission of any field carrying a "Highly Confidential" sensitivity label, even if DLP rules haven't been explicitly written for that field yet.
Which layer, and what capability within it, satisfies this?

**Drop-down:** DLP & Sensitivity Filters, configured to surface/enforce the highest sensitivity label present, not just explicit DLP rules | Agent Runtime, with token limits reduced | User Output & Logging, with output truncated | Data Sources, with the field deleted from the source system

**Answer: DLP & Sensitivity Filters, configured to surface/enforce the highest sensitivity label present** — matches "Apply sensitivity labels to knowledge sources; surface the highest label in responses where supported," which is broader than relying on pre-written DLP rules alone.

---

**DO-02**
An architect is completing a Gate table for a Foundry agent that also touches Dynamics 365 Finance data. The customer asks: "At which gate do we confirm the agent's cost and performance under real ERP workload constraints, not synthetic load?"

**Drop-down:** Gate 2 (Test → Prod) — Performance verified under ERP workload constraints | Gate 1 (Dev → Test) — Initial safety checks | Gate A→B — Catalog & ownership | Gate D→E — Compliance & residency

**Answer: Gate 2 (Test → Prod) — Performance verified under ERP workload constraints** (D365 F&SC ALM Gate 2 criteria, distinct from the generic AI-data Gate D→E which is about compliance/residency, not ERP load).

---

**DO-03**
Complete the Model Hardening Blueprint for a scenario where the customer specifically flags *training-time* poisoning as their top concern (not runtime attacks).
Which step of the blueprint should be emphasized most, and why?

**Drop-down:** Step 4, Validation Pipeline — validate models and data to maintain quality and compliance, including new-data validation before retraining | Step 2, Private Endpoints — network isolation | Step 3, Threat Protection — runtime detection | Step 1, Secure Compute — compute isolation

**Answer: Step 4, Validation Pipeline** — poisoning is a training-data integrity risk; the blueprint's guidance to "validate newly introduced data before using it in retraining pipelines" is the direct control, not network isolation or runtime threat detection (which address different attack surfaces).

---

**DO-04**
A customer wants their architecture diagram to show where "Human-in-the-loop" (HITL) sits relative to drift detection for a fraud model. Complete: "Detect data drift vs. baselines → trigger safeguard actions (___, HITL)."

**Drop-down:** Circuit breakers | Load balancers | CDN caching | Autoscaling rules

**Answer: Circuit breakers** — explicitly paired with HITL in the source: "Detect data drift vs. baselines; trigger safeguard actions (circuit breakers, HITL)."

---

**DO-05**
Complete the RBAC design diagram where the customer wants to know which role should hold approval authority for publishing to Production and for high-risk capability changes.

**Drop-down:** Security Admin / Publisher approval workflow, distinct from Maker | Maker role, self-approved | Environment Admin only, no separate approval needed | Any authenticated user with a Copilot Studio license

**Answer: Security Admin / Publisher approval workflow, distinct from Maker** — "Distinct roles for Maker, Publisher, Environment Admin, and Security Admin... Require approvals for publishing to production."

---

**DO-06**
A regulated customer's Foundry agent diagram must show where secrets are separated from development artifacts. Complete: "Data, security, and residency controls" must enforce ___.

**Drop-down:** Separation of production secrets from development artifacts, using secure identity management for agent actions | Shared secrets vault across all environments for simplicity | Secrets embedded directly in agent prompt templates | Secrets stored in the source code repository for traceability

**Answer: Separation of production secrets from development artifacts, using secure identity management for agent actions**

---

**DO-07**
Complete the audit-trail architecture diagram: the customer wants Foundry activity logs exported to their existing SIEM. Which two Foundry-native capabilities does this diagram need?

**Drop-down:** Foundry activity logs exported to Azure Monitor / Log Analytics / SIEM tools (e.g., Microsoft Sentinel), plus diagnostics/tracing for execution path visibility | A manually maintained spreadsheet of changes | A single unstructured text log file per model | Screenshots of the model registry taken weekly

**Answer: Foundry activity logs exported to Azure Monitor / Log Analytics / SIEM tools, plus diagnostics/tracing**

---

**DO-08**
A customer's compliance officer asks the architect to complete this statement for their audit-retention diagram: "Regulated workloads should retain audit logs for ___."

**Drop-down:** 12–24 months, per the recommended pattern for regulated workloads (vs. 90 days for low-risk, indefinite for incident-related archives) | Exactly 30 days for all workloads | Indefinitely for all workloads regardless of risk | No retention requirement if logs contain no PII

**Answer: 12–24 months, per the recommended pattern for regulated workloads**

---

**DO-09**
Complete the grounding-data access diagram for a scenario where the customer wants model-tuning operations completely isolated from production inference. What environment design principle fills the blank: "Model tuning access requires ___."

**Drop-down:** Segregated environments for development, evaluation, and production, insulated from production operations | The same environment as production inference, with extra logging | A shared identity between tuning and inference workloads | No environment segregation, since tuning is a one-time event

**Answer: Segregated environments for development, evaluation, and production, insulated from production operations**

---

**DO-10**
A customer's architecture review flags that their agent's connector allow-list is undocumented. Complete the Development and Interoperability Standards diagram: "Agents must use ___ for structured tool/data access, and ___ for controlled delegation across agents."

**Drop-down:** Model Context Protocol (MCP); Agent-to-Agent (A2A) | REST APIs only; SOAP for legacy systems | GraphQL; Webhooks | OData; SFTP

**Answer: Model Context Protocol (MCP); Agent-to-Agent (A2A)** — explicitly named as the standard protocols for tool/data access and controlled agent delegation.

---

## 3. Case Studies (2–3 scenarios, 8 questions total) — Architect Level

### Case Study 1 — Meridian Health Network (Regulated, Multi-Region)

*This is a case study. Information provided in an individual question does not apply to other questions in this case study.*

**Overview**
Meridian Health Network operates hospitals across the EU and US. It is deploying a Foundry agent that summarizes patient intake notes for clinicians and a custom AI model that flags high-risk readmission candidates. The solution draws on Dataverse patient records, a Dynamics 365 Customer Service case history, and a third-party lab-results API.

**Existing Environment**
- EU patient data must remain in-region by regulatory mandate; no pre-approved overflow exists for this workload tier.
- The readmission model is retrained quarterly using updated clinical data.
- The intake-summarization agent is considered a high-risk, data-sensitive capability because it surfaces PHI (protected health information).
- Meridian's security team mandates managed identities for every agent and pipeline, with no embedded secrets anywhere.
- A prior incident involved a prompt-injection attempt via a malicious PDF lab report; leadership now requires this class of attack be mitigated architecture-wide, not just patched once.

**Requirements**
1. EU clinician queries must never trigger cross-region processing.
2. The readmission model must never train on live PHI directly from Production.
3. The intake agent must have layered protections against embedded malicious content in uploaded documents, not a single point fix.
4. Every promotion of the readmission model to Production must include a documented rollback plan and CAB approval.

**Case Study 1 — Q1**
A US-based data scientist proposes routing EU clinician queries through a US region temporarily during a capacity shortage, without new approvals, citing the pilot exemption used in an unrelated non-clinical workload. What should the architect do?

- A. Approve the routing since a pilot exemption previously existed for a different workload
- B. Reject the routing; per the Residency Decision Tree, overflow requires explicit approval for *this* workload tier, and none exists — in-region capacity issues should block or defer the feature, not silently reroute
- C. Approve the routing only for read-only queries
- D. Approve the routing but disable logging to reduce audit exposure

**Answer: B** — Precedent from an unrelated workload does not satisfy the explicit, per-workload-tier overflow approval requirement; this is a classic architect trap where surface-level precedent is used to justify a policy violation.

---

**Case Study 1 — Q2**
Which data preparation approach satisfies Requirement 2 while still keeping the quarterly retraining realistic and useful?

- A. Train directly on live Production PHI but delete the training copy after each run
- B. Use versioned, de-identified/curated Dev/Test datasets refreshed each quarter from a controlled pipeline, with lineage and hashes stamped per snapshot
- C. Train on the third-party lab API's public sample dataset only, ignoring internal clinical data entirely
- D. Skip retraining and rely on the original launch model indefinitely

**Answer: B** — Matches "never train on production knowledge" combined with the versioned, lineage-stamped curated dataset approach from the AI Data ALM process (Phase B — Ingest & Prepare).

---

**Case Study 1 — Q3**
Given the prior prompt-injection incident and the requirement for layered (not single-point) protection, which combination of controls should the architect recommend for the intake agent?

- A. Input sanitization only — strip unsafe embedded content from uploaded PDFs
- B. DLP policy only — prevent PHI from appearing in outputs
- C. A layered stack: input/output filtering (sanitize uploaded content), data governance (DLP/sensitivity labels on PHI), least-privilege connector scope, and observability (anomaly alerting on unusual access patterns) — combined, not standalone
- D. Rely entirely on the underlying model's built-in safety training, since it already resisted the original attack

**Answer: C** — This is the defense-in-depth principle applied directly; any single control (A, B, or D alone) leaves other attack surfaces exposed and fails "mitigated architecture-wide, not just patched once."

---

**Case Study 1 — Q4**
Which gate requirement, if skipped, would most directly violate Requirement 4?

- A. Skipping the CAB approval step because the evaluation metrics exceeded baseline
- B. Skipping the initial Dev-stage prompt drafting review
- C. Skipping the data profiling step during ingestion
- D. Skipping the connector authentication validation step

**Answer: A** — Requirement 4 explicitly ties CAB approval and rollback plan documentation to *every* Production promotion, independent of how strong the evaluation metrics are; this is the same trap as Gate 2's rollback-plan requirement being metric-independent.

---

### Case Study 2 — Vantage Global Logistics (Multi-App, High Automation)

*This is a case study. Information provided in an individual question does not apply to other questions in this case study.*

**Overview**
Vantage Global Logistics runs Dynamics 365 Supply Chain Management and Dynamics 365 Finance. It is deploying a Foundry agent that autonomously reroutes shipments and automatically posts related cost adjustments to the Finance ledger when reroutes occur. This is explicitly flagged as a business-critical, data-modifying automation.

**Existing Environment**
- The company uses Azure DevOps for all release pipelines; managed solutions are used in Test and Prod only.
- A recent audit found inconsistent testing: some releases skipped end-to-end validation of the Supply Chain → Finance data handoff.
- The agent's connector to the Finance ledger was flagged as high-risk because it can post financial entries.
- Leadership wants confidence that if the agent's reasoning is later found flawed, the team can trace exactly which release and data snapshot caused it.

**Requirements**
1. The agent must not autonomously post ledger entries above a materiality threshold without human approval.
2. Every release must validate that a Supply Chain reroute event correctly and consistently produces the matching Finance ledger entry.
3. The connector used to post to Finance must go through full security review before every Production publish, not just the first time.
4. The team must be able to trace any flawed ledger entry back to a specific model/agent version and specific data snapshot.

**Case Study 2 — Q1**
Which access-pattern design satisfies Requirement 1 without eliminating the automation's core value?

- A. Full autonomous posting with no human step, since the agent passed initial testing
- B. Scoped write access to post ledger entries, with mandatory human approval required only above a defined materiality threshold, and full audit trail on every action
- C. Read-only access — the agent may only recommend but never post anything
- D. Remove the agent's Finance connector entirely and route everything through email approval

**Answer: B** — This mirrors the tiered persona-access design pattern (from DD-09): full autonomy is too risky for a data-modifying, business-critical action, but pure read-only defeats the automation's purpose; the threshold-based approval is the correct middle design.

---

**Case Study 2 — Q2**
Which testing type directly addresses the audit finding referenced in Requirement 2?

- A. Unit testing of the reroute algorithm in isolation
- B. Integration/end-to-end testing validating cross-app data flow between Supply Chain and Finance
- C. UI regression testing of the Supply Chain dashboard
- D. Load testing of the Finance API under peak traffic

**Answer: B** — Directly matches the source's rationale for why end-to-end tests must validate cross-app data flow: "AI output quality depends on consistent, trusted, and well-timed input data from across integrated systems."

---

**Case Study 2 — Q3**
Which ALM principle, applied correctly, satisfies Requirement 3 (repeated security review, not one-time)?

- A. Publish connectors to Prod once security review passes at initial launch, then treat subsequent releases as pre-approved
- B. Apply the full connector release flow (Author → Validate Auth → Apply DLP → Approve Security → Publish to Prod) on every release that touches this connector, not only the first
- C. Delegate all future security reviews to the Platform Admin without Security team involvement
- D. Skip DLP re-validation if the connector's authentication method hasn't changed

**Answer: B** — The connector ALM release flow is a per-release gate, not a one-time approval; treating it as "grandfathered" after the first pass is the exact trap this question tests.

---

**Case Study 2 — Q4**
Which combination of controls best satisfies Requirement 4 (traceability of a flawed ledger entry to a specific version and data snapshot)?

- A. Immutable, timestamped, role-attributed audit logs for model/agent version changes, correlated with versioned/lineage-stamped data snapshots and tracing fields (correlation ID, model version)
- B. A weekly manual export of the model registry to a spreadsheet
- C. Reliance on the Finance team's own ledger reconciliation process alone
- D. Deleting older model versions after each promotion to reduce storage cost

**Answer: A** — Combines audit-trail requirements (immutable logs, role attribution) with data lineage/versioning and tracing fields (correlation ID, model version) — this is the only option that actually enables the traceability leadership asked for; D is actively counterproductive since it destroys the very versions needed for tracing.

---

## 4. Yes/No Hotspot Questions — Architect Level (3 statements per scenario; cannot be revisited after submission)

### Hotspot Scenario 1 — Sales Executives Using Headset-Based Agent Queries (Extended, Multi-Constraint)
*Sales executives use headsets to query an AI agent for account summaries during live customer calls. The agent has access to CRM data, call transcripts, and a connector to a pricing system. The company has a strict "no direct production edits" policy and requires that any escalation path preserve context so a human doesn't have to ask the customer to repeat themselves.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | Should the agent be allowed to modify pricing directly through its connector without a separate approval step, given it's only "assisting" a live call? | **No** | Pricing changes are a data-modifying, business-critical action; per governance principles, high-risk capability changes require approval workflows regardless of the "assist-only" framing — the risk is in the connector's write capability, not the agent's stated intent. |
| 2 | If the agent escalates to a human after repeated failures, should the escalation preserve the conversation context (transcript, CRM lookups already performed) rather than starting cold? | **Yes** | This follows directly from the requirement that a human "doesn't have to ask the customer to repeat themselves" — architecturally this means the escalation path must carry forward session context, consistent with the observability/tracing guidance (correlation IDs, session continuity) rather than treating escalation as a hard reset. |
| 3 | Is it acceptable to log the full pricing figures discussed on the call in plaintext for training-data purposes, since pricing isn't classified as PII? | **No** | Sensitivity classification isn't limited to PII — pricing data can carry its own sensitivity label per DLP policy design ("Apply sensitivity labels to knowledge sources; surface the highest label"), and using live call content for training without going through the curated Dev/Test pipeline violates "never train on production knowledge." |

---

### Hotspot Scenario 2 — Cross-Border M&A Data Consolidation
*A multinational is merging two subsidiaries' Dynamics 365 environments, each in a different data residency region. An AI agent will be used temporarily to reconcile duplicate customer records across both regions during the migration window.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | Is it acceptable to run this reconciliation agent with a single shared identity across both regional environments to simplify the temporary migration? | **No** | Even for temporary/migration workloads, the principle "assign a unique cloud identity per agent, per environment... with recorded ownership, version, and lifecycle metadata" still applies; a shared identity removes traceability exactly when cross-region data handling needs it most. |
| 2 | Does cross-region record matching during this migration require the same in-region-first, explicit-overflow-approval decision process as any other AI workload? | **Yes** | The Residency Decision Tree doesn't carve out an exception for temporary/migration workloads — "temporary" is not one of the stated exemption criteria; the same explicit approval gate applies. |
| 3 | Once the migration is complete, is it acceptable to leave the reconciliation agent's elevated cross-region access permissions active indefinitely "in case it's needed again"? | **No** | This directly contradicts least-privilege and lifecycle governance principles ("criteria for archiving or retiring unused agents"); temporary elevated access must be retired, not left standing as a convenience. |

---

### Hotspot Scenario 3 — Autonomous Supplier Payment Agent Under Drift
*An AI agent autonomously approves supplier payments under a defined materiality threshold. Six months after go-live, drift monitoring shows the agent's approval pattern has shifted meaningfully from its original validated baseline, though no individual payment has yet caused a loss.*

| # | Statement | Answer | Reason |
|---|---|---|---|
| 1 | Because no financial loss has occurred yet, is it acceptable to defer investigation until the next scheduled quarterly review? | **No** | Drift detection guidance requires that when drift exceeds thresholds, the system should "auto-open an incident, route to data owner, and pause affected actions" — the trigger is the drift signal itself, not realized loss; waiting for harm before acting inverts the intended safeguard. |
| 2 | Should the agent's autonomous approval capability be paused (or its threshold tightened) while the drift is investigated? | **Yes** | This is the explicit safeguard action tied to drift detection — "trigger safeguard actions (circuit breakers, HITL)" — pausing or narrowing scope is the circuit-breaker response, not a discretionary choice. |
| 3 | If the root cause is found to be a legitimate shift in supplier behavior (not a model defect), can the team simply raise the drift-monitoring threshold to stop the alerts, without retraining or re-evaluating the model? | **No** | The correct response to confirmed drift — even a "legitimate" shift — is to retrain on updated, versioned data and re-run evaluation against golden sets before redeployment, per the retrain/re-evaluate/redeploy cycle; silencing the alert by loosening thresholds bypasses governance rather than resolving the underlying model-data mismatch. |

---

## Architect-Level Calibration Notes
- Every "wrong" option above is wrong for a *specific, named* reason traceable to source guidance — not generic distractor noise. This is what separates a 9/10 difficulty item from a recall item: the incorrect options represent plausible real-world shortcuts (precedent reuse, "it's just a pilot," "no loss yet") that an under-experienced architect might actually take.
- Case Study 2's Q4 (traceability) and Hotspot Scenario 3 both hinge on the same underlying principle (drift/incident response is trigger-based, not harm-based) tested from two different angles — intentional, to check whether the candidate generalizes the principle or only memorized one phrasing of it.
- If your exam platform enforces "no revisit" per hotspot block, double check Hotspot Scenario 1, Q1 vs Q3: a candidate who gets Q1 wrong (allows autonomous pricing edits) is likely to also misjudge Q3 in the same direction — this is intentional correlation to catch candidates who don't understand the underlying least-privilege principle versus those who got lucky on one item.
