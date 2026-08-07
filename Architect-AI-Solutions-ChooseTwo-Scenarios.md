# Architect AI Solutions for Business Productivity — "Choose Two" Scenario Question Bank

Format matches the Question 5 style: scenario + requirements + "Which two actions should you include?" Each correct selection is worth one point.

---

**Question 1.**
A company uses a Microsoft Copilot Studio agent that answers HR policy questions. The agent occasionally gives outdated answers because HR updates policy documents monthly.
You need to design a solution that meets the following requirements:
- The agent's answers must reflect the latest approved policy documents.
- Changes to source documents must be traceable.

Which two actions should you include in the design?
A. Store policy documents in SharePoint with version history enabled and connect it as a knowledge source.
B. Hardcode policy answers directly into the agent's topics.
C. Configure the agent to re-sync/re-index the knowledge source on a scheduled basis after each policy update.
D. Disable the knowledge source and rely on the base language model.
E. Increase the agent's response length limit.

**Answer: A, C**
*SharePoint with version history provides traceability of document changes (A). Scheduled re-sync ensures the agent's grounded answers reflect the latest approved version (C). Hardcoding (B) isn't traceable or scalable; disabling grounding (D) increases hallucination risk; response length (E) is unrelated.*

---

**Question 2.**
A financial services company is deploying an autonomous Copilot Studio agent to triage support tickets. Compliance requires that any action affecting a customer's account be reviewable after the fact, and no ticket involving a transaction dispute may be closed without human sign-off.

Which two actions should you include in the design?
A. Enable transcript/interaction logging and auditing for the agent.
B. Allow the agent to auto-close all tickets to improve efficiency.
C. Configure a human-approval step (task agent) for transaction-dispute tickets specifically.
D. Remove logging to reduce storage costs.
E. Restrict the agent to a single generic topic for all ticket types.

**Answer: A, C**
*Logging/auditing (A) satisfies the after-the-fact reviewability requirement. A human-approval gate scoped to dispute tickets (C) satisfies the sign-off requirement while still allowing automation elsewhere. B and D directly violate the stated requirements; E doesn't address either requirement.*

---

**Question 3.**
A company is fine-tuning a Microsoft Foundry model for domain-specific customer support. The security team requires that training data never leaves the company's approved Azure region, and that access to the training dataset is limited to the ML engineering team only.

Which two actions should you include in the design?
A. Store the training data in a storage account provisioned in the approved region.
B. Grant all employees read access to the training data for transparency.
C. Apply role-based access control (RBAC) scoped to the ML engineering team on the storage account.
D. Enable public blob access for easier data sharing.
E. Store the training data in a region chosen for lowest cost, regardless of compliance.

**Answer: A, C**
*Regional storage placement (A) satisfies data residency; RBAC scoping (C) satisfies least-privilege access. B, D, and E all violate the stated security requirements.*

---

**Question 4.**
A retail company wants Copilot Studio agents in two different Power Platform environments (Marketing and Customer Service) to use the same, always-current product catalog data, without duplicating storage or risking inconsistent data.

Which two actions should you include in the design?
A. Centralize the product catalog in Microsoft Dataverse in a single environment.
B. Export a static CSV copy of the catalog to each environment monthly.
C. Use cross-environment data sharing/virtual tables (or a connector) so both agents reference the same source.
D. Let each team independently maintain its own copy of the catalog.
E. Store the catalog only in each agent's local topic variables.

**Answer: A, C**
*Centralizing in Dataverse (A) creates a single source of truth; cross-environment access via virtual tables/connectors (C) lets both agents reference it live without duplication. B, D, and E all introduce duplication or staleness.*

---

**Question 5.**
A company is designing ALM for a Copilot Studio agent used across Dev, Test, and Prod environments. Stakeholders require that changes are peer-reviewed before promotion and that a failed deployment can be quickly rolled back.

Which two actions should you include in the design?
A. Use solution pipelines with a required pull-request/review step before promotion.
B. Deploy directly to Prod by editing the agent in place.
C. Maintain versioned managed solution exports so a previous version can be redeployed if needed.
D. Skip Test environment validation to save time.
E. Allow any team member to publish directly to Prod without review.

**Answer: A, C**
*A pull-request/review gate (A) satisfies peer review; versioned managed solutions (C) enable rollback. B, D, and E all bypass governance and rollback safety.*

---

**Question 6.**
A company wants to evaluate the ROI of an AI-based document processing agent. Leadership wants the analysis to be defensible and wants to know both what the solution costs and how much manual effort it saves.

Which two actions should you include in the design?
A. Quantify all development, deployment, and ongoing operating costs.
B. Rely solely on a competitor benchmarking report.
C. Measure the reduction in manual processing hours/costs after deployment.
D. Skip cost tracking since the solution is "innovation," not an expense.
E. Estimate ROI once, before deployment, and never revisit it.

**Answer: A, C**
*Full cost quantification (A) and measured labor/time savings (C) together produce a defensible ROI comparison. B is an indirect, unreliable proxy; D and E undermine analysis accuracy and ongoing validity.*

---

**Question 7.**
A company is designing a RAG-based Copilot Studio agent to answer questions from a large, frequently updated internal wiki (structured and unstructured content, includes logs and APIs). The company needs accurate retrieval and minimal hallucination.

Which two actions should you include in the design?
A. Index the content using Azure AI Search to enable semantic/hybrid retrieval.
B. Configure the agent to answer strictly from retrieved, cited knowledge-source content.
C. Allow the agent to freely generate answers from the base model when retrieval confidence is low.
D. Store the wiki content only as unindexed flat files with no search layer.
E. Disable citations to keep responses concise.

**Answer: A, B**
*Azure AI Search (A) provides the retrieval layer needed for heterogeneous, frequently updated content. Restricting to grounded, cited answers (B) minimizes hallucination. C, D, and E all increase hallucination risk or reduce retrieval quality.*

---

**Question 8.**
A company plans to scale AI adoption from one successful pilot to 10 business units. Leadership wants consistent governance and reusable components without slowing down each team's ability to build.

Which two actions should you include in the design?
A. Establish a Center of Excellence (CoE) with shared standards, templates, and governance policies.
B. Require every business unit to build entirely from scratch with no shared assets.
C. Provide a curated library of reusable, approved components (connectors, templates, prompts) that teams can adopt.
D. Centralize all development under a single team so no other unit can build agents.
E. Leave governance undefined so teams can move faster.

**Answer: A, C**
*A CoE (A) and a reusable component library (C) together balance consistency/governance with team autonomy and speed. B and D block scaling; E creates governance risk.*

---

**Question 9.**
A healthcare company's Copilot Studio agent occasionally surfaces protected health information (PHI) in responses to staff who are not authorized to view it. You need to correct this while preserving the agent's usefulness.

Which two actions should you include in the design?
A. Apply row-level/column-level security or sensitivity-based filtering on the underlying data source so unauthorized fields are never returned.
B. Grant the agent's service account full unrestricted access to all patient data.
C. Configure the agent to respect user-context permissions (respond only with data the requesting user is authorized to see).
D. Remove all patient-related knowledge sources entirely.
E. Log a warning but still return the PHI.

**Answer: A, C**
*Data-level security filtering (A) and honoring the requester's own permissions (C) prevent unauthorized PHI exposure while keeping the agent functional. B directly causes the problem; D removes usefulness entirely; E doesn't prevent the exposure.*

---

**Question 10.**
A manufacturing company's AI agent for equipment troubleshooting has started giving less accurate answers over the past few months as new equipment models were introduced. You need to restore accuracy while maintaining a repeatable process for future updates.

Which two actions should you include in the design?
A. Add the new equipment documentation to the agent's grounding/knowledge source.
B. Ignore the drift since usage may decline naturally.
C. Establish a recurring review cycle to update grounding data as new equipment is released.
D. Increase the model's maximum output token limit.
E. Retrain the base foundation model from scratch every time new equipment launches.

**Answer: A, C**
*Adding current documentation (A) directly fixes the accuracy gap; a recurring update cycle (C) prevents future drift as new equipment launches (this is a lifecycle/monitoring pattern, not a one-time fix). D is unrelated; E is unnecessarily costly compared to updating grounding data.*

---

**Question 11.**
A company wants an AI agent to automate expense report approvals, but internal audit requires that any approval decision be explainable and that expenses above a threshold always involve a human.

Which two actions should you include in the design?
A. Log the agent's reasoning/decision factors for each approval so decisions can be explained later.
B. Auto-approve every expense regardless of amount to maximize speed.
C. Route expenses above the threshold to a human approver via a task/approval step.
D. Disable logging for approved (non-flagged) expenses to save cost.
E. Allow the agent to change the approval threshold dynamically without oversight.

**Answer: A, C**
*Decision logging (A) satisfies explainability; a threshold-based human approval routing (C) satisfies the human-in-the-loop requirement. B and E violate the requirements; D undermines explainability/auditability.*

---

**Question 12.**
A company is designing a data strategy to support multiple AI systems (Copilot Studio agents, Dynamics 365 apps, and a custom Azure AI Foundry model) that all need access to the same governed customer data with built-in classification.

Which two actions should you include in the design?
A. Centralize customer data in Microsoft Dataverse.
B. Apply Microsoft Purview sensitivity labels/classification to the centralized data.
C. Create separate, disconnected copies of customer data for each AI system.
D. Store customer data only in each application's local cache.
E. Disable classification to simplify access.

**Answer: A, B**
*Centralizing in Dataverse (A) provides a single governed source for all consuming systems; applying Purview classification (B) satisfies the built-in classification requirement. C, D, and E create fragmentation and reduce governance.*

---

**Question 13.**
A company plans a phased enterprise AI rollout. Leadership wants to validate assumptions with real users before broad investment, while still capturing measurable success criteria to justify scaling.

Which two actions should you include in the design?
A. Run a scoped pilot with a defined group of real users.
B. Skip the pilot and deploy directly to all users to save time.
C. Define success metrics (e.g., adoption rate, task completion time, accuracy) before the pilot begins.
D. Define success metrics only after the pilot concludes.
E. Deploy the pilot with no defined scope or exit criteria.

**Answer: A, C**
*A scoped pilot (A) validates assumptions with limited risk; pre-defined success metrics (C) allow objective evaluation of whether to scale. B, D, and E undermine the ability to validate and measure results properly.*

---

**Question 14.**
A company's Copilot Studio agent for Dynamics 365 Contact Center must support a voice channel and must not use generative orchestration, per a compliance requirement for deterministic conversation flows.

Which two actions should you include in the design?
A. Configure the agent to use Natural Language Understanding + (NLU+) as the language model.
B. Configure the agent to use generative orchestration for flexible responses.
C. Build the agent using classic (topic-based) orchestration with defined conversation paths.
D. Configure the agent to use a large open-ended generative model.
E. Build the agent with no defined topics, relying entirely on free-form generation.

**Answer: A, C**
*NLU+ (A) supports voice channel integration; classic topic-based orchestration (C) satisfies the deterministic, non-generative-orchestration requirement. B, D, and E all violate the "no generative orchestration" constraint.*

---

**Question 15.**
A company wants to reduce hallucinations in a customer-facing Copilot Studio agent while also making sure the agent doesn't answer questions outside its intended scope (e.g., legal advice).

Which two actions should you include in the design?
A. Restrict the agent's knowledge sources to only approved, relevant content.
B. Configure topic/content boundaries so the agent declines out-of-scope requests (e.g., legal advice) and redirects appropriately.
C. Allow the agent to answer any question using its base model knowledge when the knowledge source has no answer.
D. Remove all topic boundaries to make the agent maximally helpful.
E. Increase the creativity/temperature setting to generate more varied answers.

**Answer: A, B**
*Restricting knowledge sources (A) reduces hallucination; explicit topic boundaries with graceful decline/redirect (B) prevents out-of-scope responses (e.g., legal advice). C, D, and E all increase risk of inaccurate or out-of-scope answers.*

---

**Question 16.**
A global company must deploy a Copilot Studio agent that uses Dataverse data stored in the EU while calling a connector to an Azure OpenAI instance hosted in the US. Data protection policy requires cross-border movement to be explicitly governed and reviewable.

Which two actions should you include in the design?
A. Explicitly enable and document approved cross-region data movement for the required connector dependency.
B. Validate the configuration against Microsoft Purview Data Loss Prevention (DLP) policies before deployment.
C. Silently allow the connector to move data without documentation.
D. Migrate the entire EU tenant to the US to avoid the issue.
E. Block all connectors regardless of business need.

**Answer: A, B**
*Explicitly enabling and documenting the necessary cross-region flow (A) satisfies "governed" movement; validating against Purview DLP (B) satisfies "reviewable" compliance. C lacks documentation; D and E are disproportionate/non-viable responses.*

---

**Question 17.**
A company's Foundry-based agent solution suffers from slow response times on complex multi-step tasks and inconsistent accuracy on domain-specific questions. Leadership wants both issues addressed without a full re-architecture.

Which two actions should you include in the design?
A. Move to a multi-agent architecture so complex tasks are split across specialized agents (improves performance/latency).
B. Add a relevant grounding data source for the domain-specific content (improves accuracy).
C. Reduce the number of available actions/tools to zero to simplify the agent.
D. Combine all tasks into a single larger prompt to reduce agent count.
E. Disable grounding to speed up responses.

**Answer: A, B**
*Splitting work across a multi-agent architecture (A) addresses latency on complex tasks; adding a grounding source (B) addresses domain accuracy. C, D, and E would worsen one or both issues.*

---

**Question 18.**
A company is building a shared prompt library used by multiple business units. Requirements: prompts must be reusable/consistent, and changes must be governed with rollback capability, while minimizing new tooling costs.

Which two actions should you include in the design?
A. Define standardized, reusable prompt templates for common scenarios.
B. Store and version the prompt templates in an existing source-control repository (e.g., Git) the company already uses.
C. Let each business unit maintain its own private, ungoverned prompt copies.
D. Purchase a new, dedicated prompt-management SaaS platform regardless of cost.
E. Avoid versioning prompts to keep the process simple.

**Answer: A, B**
*Standardized templates (A) ensure consistency; using existing source control (B) provides governance/version control/rollback without new tooling cost. C undermines consistency; D contradicts the cost-minimization requirement; E removes governance.*

---

**Question 19.**
A company wants to ensure its autonomous procurement agent complies with Responsible AI principles, specifically around fairness and accountability, when recommending vendor selections.

Which two actions should you include in the design?
A. Regularly audit the agent's vendor recommendations for bias or unfair patterns (e.g., consistently favoring a subset of vendors without justification).
B. Allow the agent to finalize vendor contracts autonomously with no review.
C. Require human review and sign-off before any vendor recommendation becomes a binding decision.
D. Disable all logging of the agent's recommendation reasoning.
E. Base recommendations solely on the lowest price with no other governance.

**Answer: A, C**
*Bias auditing (A) supports fairness; human sign-off before binding decisions (C) supports accountability. B and D remove oversight/traceability; E oversimplifies and risks unfair or non-compliant outcomes without governance context.*

---

**Question 20.**
A company is monitoring a production Copilot Studio agent and wants to detect both immediate failures and slow, long-term quality degradation (drift), so it can respond appropriately to each.

Which two actions should you include in the design?
A. Implement real-time monitoring/alerting for failed or low-confidence responses.
B. Establish periodic (e.g., monthly/quarterly) quality reviews comparing current response accuracy against a baseline to detect drift.
C. Only check the agent once at initial launch.
D. Treat all issues, immediate or gradual, with the same one-time fix and no further monitoring.
E. Disable alerting to avoid noise from the monitoring system.

**Answer: A, B**
*Real-time alerting (A) catches immediate failures; periodic baseline comparison (B) catches gradual drift that real-time alerts would miss. C, D, and E all remove the ongoing monitoring needed to catch one or both failure types.*

---

*These questions mirror the "choose two" scenario format and span agentic AI architecture, Copilot Studio/Foundry design, Responsible AI, governance, ALM, data strategy, ROI, and lifecycle monitoring — consistent with the topic list provided earlier.*
