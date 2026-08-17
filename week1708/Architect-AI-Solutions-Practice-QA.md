# Architect AI Solutions for Business Productivity — Extended Practice Bank
Covers: Generative AI, Copilot Studio, Dynamics 365 Copilot, Power Platform, ALM, Responsible AI, ROAI, Data Governance

---

## SECTION 1 — 10 HOTSPOT Questions

**H1.** You are configuring grounding for a Copilot Studio agent. You need to select the correct action for each scenario.
- Agent returns outdated pricing data → **Refresh/re-sync the knowledge source**
- Agent returns answers outside the approved topic scope → **Restrict the agent to specific knowledge sources/topics**

*Reasoning: Stale data needs a refresh; scope creep needs source/topic restriction, not retraining the base model.*

**H2.** You are designing agent governance controls.
- Prevent agents from accessing sensitive Dataverse tables → **Apply column-level/table-level security roles**
- Track who published changes to an agent → **Enable solution history/audit logging**

*Reasoning: Security roles control data access; audit logs provide traceability of changes.*

**H3.** You are choosing orchestration types for two agents.
- Agent needs deterministic, rule-based conversation flow → **Classic (topic-based) orchestration**
- Agent needs to dynamically reason across multiple actions/tools → **Generative orchestration**

**H4.** You are validating a RAG (retrieval-augmented generation) knowledge source.
- Ensure retrieved chunks are relevant → **Test with varied real-world queries and review relevance scores**
- Ensure answers stay grounded (no hallucination) → **Enable/require citations and restrict to knowledge-source-only answers**

**H5.** You are designing a multi-environment ALM strategy.
- Isolate in-development agent changes → **Use a Dev environment with unmanaged solutions**
- Promote tested changes safely → **Use Test/Prod environments with managed solutions via pipelines**

**H6.** You are selecting a testing type for each requirement.
- Confirm the agent still works after a model/config update → **Regression testing**
- Confirm response quality degradation over time → **Drift testing**

**H7.** You are designing Responsible AI controls.
- Prevent agents from generating harmful/off-brand content → **Configure content moderation and topic boundaries**
- Ensure explainability of AI-driven decisions → **Enable transparency notes / document model behavior**

**H8.** You are choosing a scaling approach for AI adoption.
- Standardize reusable components across teams → **Center of Excellence (CoE) starter kit**
- Track solution health and usage at scale → **CoE Governance and telemetry dashboards**

**H9.** You are selecting cost-optimization actions.
- Reduce token usage for high-volume simple queries → **Use a smaller/standard language model**
- Reduce latency for complex reasoning tasks → **Use a larger model only where needed (selective routing)**

**H10.** You are validating an agent prior to go-live.
- Confirm functional accuracy → **User acceptance testing (UAT)**
- Confirm the agent performs under expected load → **Performance/load testing**

---

## SECTION 2 — 10 Case Study Questions

*(Case study scenario: A financial services company is deploying Copilot Studio agents across sales, support, and finance. Sensitive customer data (IDs, names) must be tracked for auditing. The company wants to scale responsibly while minimizing admin overhead.)*

**C1.** Which framework should govern the overall AI adoption strategy?
**Answer: A. Microsoft Cloud Adoption Framework for Azure** — provides enterprise-wide strategy, governance, and landing zone guidance.

**C2.** Which tool should be used to track agent usage and health across the organization?
**Answer: Microsoft Power Platform Center of Excellence (CoE) Starter Kit** — gives centralized visibility and governance.

**C3.** Which approach ensures sensitive data shared via agents is auditable?
**Answer: Enable Microsoft Purview auditing / DLP policies on the environment.**

**C4.** Which solution type should be used to promote the finance agent from Dev to Prod with minimal effort?
**Answer: Managed solution via a deployment pipeline.**

**C5.** Which testing approach validates that the sales and finance agents don't return conflicting information from shared data?
**Answer: Integration testing.**

**C6.** Which knowledge source strategy avoids duplicated/inconsistent product or policy data across agents?
**Answer: Centralize in Microsoft Dataverse and reference it from each agent.**

**C7.** Which framework guides conversational design quality (tone, clarity, escalation paths)?
**Answer: Microsoft Power Platform Well-Architected Framework (or Success by Design, depending on phase).**

**C8.** Which mechanism should escalate high-risk fraud cases to a human instead of auto-closing them?
**Answer: A task/approval agent that routes high-risk scores to a human analyst.**

**C9.** Which control minimizes the risk of the agent going out of approved topic scope?
**Answer: Restrict orchestration to approved topics/actions and disable open-ended generative fallback where not needed.**

**C10.** Which approach should be used to evaluate ROI as the company scales from pilot to enterprise-wide deployment?
**Answer: A horizon-based framework, balancing quick wins with long-term strategic value.**

---

## SECTION 3 — 10 Dropdown Questions

**D1.** To minimize hallucination in a customer-facing agent, you should restrict responses to ▢▢▢.
**Answer: only the configured knowledge sources (grounded answers only).**

**D2.** To reduce agent response latency for simple FAQ-style queries, you should use ▢▢▢.
**Answer: a smaller/standard language model instead of a larger generative model.**

**D3.** To promote an agent solution with the least administrative effort, you should export it as a(n) ▢▢▢.
**Answer: managed solution.**

**D4.** To validate that prompts behave consistently under different phrasing, you should use ▢▢▢.
**Answer: varied-phrasing test prompts (prompt validation testing).**

**D5.** To centralize product/customer data for multiple AI systems with built-in classification, you should use ▢▢▢.
**Answer: Microsoft Dataverse.**

**D6.** To index unstructured and semi-structured data (files, logs, APIs) as a Copilot Studio knowledge source, you should use ▢▢▢.
**Answer: Azure AI Search.**

**D7.** To ensure sensitive data shared by an agent is tracked for auditing, you should enable ▢▢▢.
**Answer: Microsoft Purview auditing / data loss prevention (DLP) policies.**

**D8.** To support voice-channel integration for an agent, the recommended language model is ▢▢▢.
**Answer: Natural language understanding + (NLU+).**

**D9.** To calculate ROAI accurately, the first step is to ▢▢▢.
**Answer: identify and quantify all development, deployment, and operating costs.**

**D10.** To keep a human in the loop for high-risk decisions, you should configure a(n) ▢▢▢.
**Answer: task agent that generates recommendations/scores for human review, not autonomous action.**

---

## SECTION 4 — 10 Generic Multiple-Choice Questions

**G1.** What is the primary purpose of grounding in a generative AI agent?
A. Reduce hosting costs B. **Anchor responses to verified, relevant data** C. Improve UI design D. Simplify licensing
**Answer: B**

**G2.** Which Power Platform component enforces row-level and column-level data security?
A. Power Automate B. **Dataverse security roles** C. Power BI workspace roles D. Copilot Studio topics
**Answer: B**

**G3.** What is the main benefit of a managed solution over an unmanaged solution when deploying to production?
A. Easier to edit in place B. **Prevents unintended customization and simplifies lifecycle management** C. Cheaper licensing D. Faster agent responses
**Answer: B**

**G4.** Which testing type is best suited to confirm an agent still behaves correctly after a model version upgrade?
A. Exploratory testing B. **Regression testing** C. Load testing D. Unit testing
**Answer: B**

**G5.** Which factor most directly indicates whether to build, buy, or extend an AI component?
A. Marketing trends B. **Cost-benefit and ROI analysis relative to existing capabilities** C. Number of competitors D. Developer preference
**Answer: B**

**G6.** What is a key Responsible AI consideration when deploying an autonomous agent that can take real-world actions?
A. Response speed B. **Human oversight/escalation for high-impact decisions** C. UI branding D. Number of supported languages
**Answer: B**

**G7.** Which Microsoft framework is most relevant for designing a resilient, secure, and cost-optimized Power Platform architecture?
A. ITIL B. **Microsoft Power Platform Well-Architected Framework** C. TOGAF D. Zachman Framework
**Answer: B**

**G8.** What should you do first when an agent gives inconsistent answers to differently phrased but equivalent questions?
A. Increase the model size B. **Review and standardize the underlying prompt/topic instructions** C. Disable the topic D. Add more connectors
**Answer: B**

**G9.** Which component allows Microsoft 365 Copilot to call custom logic hosted in Azure?
A. Power BI dataflow B. **Copilot Studio skills / plugins** C. SharePoint list D. Dataverse view
**Answer: B**

**G10.** What is the primary risk of using an unmanaged solution in a production environment?
A. Higher licensing cost B. **Uncontrolled customization that can break the solution or complicate updates** C. Slower agent responses D. Reduced data security
**Answer: B**

---

## SECTION 5 — 10 Yes/No Questions (with reasoning)

**Y1.** Does retraining an agent always fix poor grounding results?
**No** — grounding issues are usually caused by poor-quality or missing source data, not the model itself; cleansing/verifying the data source is the correct fix.

**Y2.** Should managed solutions be used when deploying a tested agent from Dev to Prod?
**Yes** — managed solutions minimize administrative effort and prevent unintended edits in production.

**Y3.** Is it acceptable for an autonomous fraud-detection agent to auto-close all non-fraud cases without human review?
**No** — Responsible AI and audit requirements typically require a human analyst to make the final decision, especially for financial risk cases.

**Y4.** Can Microsoft Dataverse serve as a centralized data source for multiple AI systems, including external AI models?
**Yes** — Dataverse supports built-in classification/protection and can expose data via connectors to Copilot Studio, Dynamics 365, and external AI systems.

**Y5.** Is a simple cost-and-benefit analysis sufficient to evaluate ROAI across a full portfolio of AI initiatives at different maturity stages?
**No** — a horizon-based framework is recommended to balance short-term returns with long-term/strategic value across a portfolio.

**Y6.** Should cross-region data movement be disabled by default when a Canadian environment connects to a US-based Azure OpenAI instance?
**No** (in context of the scenario) — it must be explicitly *enabled* for the required connector dependency to function, while still governed by residency policy.

**Y7.** Does adding a grounding data source generally improve an agent's domain-specific reasoning accuracy?
**Yes** — grounding provides authoritative reference data that reduces hallucination and improves domain accuracy.

**Y8.** Is it best practice to store shared prompt templates only in individual users' personal notes for a multi-business-unit prompt library?
**No** — best practice is centralized storage (e.g., a Git repository or managed template library) to support governance and version control.

**Y9.** Should Azure AI Search be used to make heterogeneous data (SQL, flat files, APIs, logs) usable as a Copilot Studio knowledge source?
**Yes** — Azure AI Search indexes and unifies heterogeneous data into a searchable format Copilot Studio can query.

**Y10.** Is the ALM Accelerator for Microsoft Power Platform the recommended tool specifically for designing conversational user experience quality?
**No** — the ALM Accelerator governs application lifecycle management (build/release pipelines); conversational UX quality is guided by the Power Platform Well-Architected Framework / Success by Design.

---

*Note: Items in Section 3 of the original PDF (Q3, Q4, Q6, Q13, Q14, Q17) were partially cut off in the source screenshots (dropdown/drag-drop option lists extended beyond the visible page). Answers above reflect the most defensible choice based on visible options and standard Microsoft Copilot Studio / Power Platform guidance — if you can share the full, un-cropped option lists for those items, I can confirm or refine those specific answers.*
