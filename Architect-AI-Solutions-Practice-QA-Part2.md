# Architect AI Solutions for Business Productivity — Practice Bank Part 2
Covering: Agentic AI, AI transformation strategy, Microsoft AI ecosystem, Copilot & Agents, Azure AI, Governance/Security/Responsible AI, Process automation, Solution planning, Enterprise adoption, Stakeholder engagement, Implementation planning, Risk/compliance, Data strategy, AI-powered apps, Lifecycle management, Scenarios, Multi-select.

> Correction to Part 1: Q4 (second prompt, "retrieve product info from a knowledge base") — the correct choice, now that full options are visible, is **"Use responses with only reference sources and limit the response scope"** (not the open-ended-questions option). This directly enforces grounded, consistent answers, whereas adding open-ended questions is a testing technique, not a fix.

---

## 1. Agentic AI Concepts and Architectures

**1.1** What primarily distinguishes an "agentic" AI solution from a traditional single-turn generative AI prompt?
A. It uses a larger language model
B. **It can autonomously plan, take multi-step actions, and use tools/data to complete a goal**
C. It only works within Microsoft 365
D. It requires no grounding data
**Answer: B** — Agentic AI is defined by autonomous, goal-driven, multi-step reasoning and action-taking (often via tools/connectors), not just single-response generation.

**1.2** In a multi-agent architecture, what is the role of an "orchestrator" agent?
A. Generates the underlying language model
B. **Routes tasks to specialized sub-agents and coordinates their outputs**
C. Stores all Dataverse data
D. Replaces the need for grounding
**Answer: B**

**1.3 (Multi-select)** Which of the following are core components of an agentic AI architecture? (Choose all that apply)
A. **Planning/reasoning layer**
B. **Tool/action invocation (connectors, APIs, skills)**
C. **Memory/state management**
D. A fixed, non-configurable UI
**Answer: A, B, C** — A fixed UI is not a defining architectural component of agentic systems.

---

## 2. AI Business Transformation Strategies

**2.1** A company wants to move from isolated AI pilots to enterprise-wide adoption. What should be established first?
A. A large marketing campaign
B. **A clear AI strategy aligned to business goals with executive sponsorship**
C. Purchasing the most powerful available model
D. Disabling all pilot projects
**Answer: B**

**2.2** Which approach best supports scaling AI adoption while managing risk incrementally?
A. Deploy all AI initiatives simultaneously across the company
B. **Use a phased rollout — pilot, validate, then scale with governance checkpoints**
C. Skip pilots and go straight to production
D. Only use AI in one department indefinitely
**Answer: B**

---

## 3. Microsoft AI Ecosystem and Services

**3.1** Which Microsoft service is best suited for building low-code conversational AI agents grounded in enterprise data?
A. Azure Machine Learning
B. **Microsoft Copilot Studio**
C. Azure Databricks
D. Power BI
**Answer: B**

**3.2** Which Azure service provides foundation models and orchestration for building custom generative AI solutions with more code-level control than Copilot Studio?
A. Power Automate
B. **Azure AI Foundry**
C. Dataverse
D. Microsoft Purview
**Answer: B**

---

## 4. Microsoft Copilot and AI Agents

**4.1** What is the difference between a "declarative agent" and a "custom engine agent" in the Microsoft 365 Copilot ecosystem?
A. There is no difference
B. **A declarative agent configures/extends the existing Copilot orchestrator and model; a custom engine agent brings its own orchestration and/or model**
C. Declarative agents cannot use knowledge sources
D. Custom engine agents cannot be published to Teams
**Answer: B**

**4.2** Which Copilot Studio feature allows an agent to call an external Azure Function to complete a business task?
A. Adaptive Cards
B. **Actions/Connectors (custom or prebuilt)**
C. Topics only
D. Entities
**Answer: B**

**4.3 (Multi-select)** Which of the following are valid knowledge sources for a Copilot Studio agent? (Choose all that apply)
A. **Dataverse**
B. **SharePoint/public websites**
C. **Uploaded files**
D. A Power BI report screenshot pasted as an image
**Answer: A, B, C**

---

## 5. Azure AI Capabilities

**5.1** Which Azure AI capability should you use to extract structured data (fields, tables) from scanned invoices?
A. Azure AI Search
B. **Azure AI Document Intelligence**
C. Azure AI Speech
D. Azure AI Translator
**Answer: B**

**5.2** Which Azure AI service provides vector search and hybrid semantic ranking to support RAG-based grounding?
A. Azure Cosmos DB (default configuration)
B. **Azure AI Search**
C. Azure Data Factory
D. Azure Logic Apps
**Answer: B**

---

## 6. AI Governance, Security, Privacy, and Responsible AI

**6.1** Which Microsoft framework/tooling should you use to monitor and prevent sensitive data (e.g., PII) from leaving approved boundaries via an AI agent?
A. Azure Monitor only
B. **Microsoft Purview (DLP, sensitivity labels, auditing)**
C. Power Automate approvals
D. Copilot Studio analytics
**Answer: B**

**6.2** Which Responsible AI principle is most directly addressed by requiring human review before an autonomous agent finalizes a high-impact decision?
A. Inclusiveness
B. **Accountability**
C. Reliability & safety only
D. Privacy
**Answer: B** — Human-in-the-loop for high-impact decisions is primarily an accountability control (though it also supports safety).

**6.3 (Multi-select)** Which actions help mitigate the risk of an AI agent generating harmful, biased, or off-brand content? (Choose all that apply)
A. **Configure content moderation/safety filters**
B. **Restrict the agent to approved topics and grounding sources**
C. **Regularly review transcripts/logs for drift**
D. Disable all logging to reduce data footprint
**Answer: A, B, C** — Disabling logging removes the ability to audit and detect issues, which works against governance.

---

## 7. Business Process Automation

**7.1** A company wants to automate invoice approval routing based on amount thresholds, combined with an AI agent that flags anomalies. Which combination of Microsoft tools fits best?
A. Power BI + Excel only
B. **Power Automate (workflow/approvals) + Copilot Studio or Azure AI agent (anomaly detection/flagging)**
C. SharePoint only
D. Teams chat only
**Answer: B**

**7.2** What is a key risk of fully automating a business process end-to-end without any human checkpoint?
A. Increased administrative overhead
B. **Errors or edge cases may go undetected and compound before being caught**
C. Slower processing time
D. Reduced scalability
**Answer: B**

---

## 8. AI Solution Planning and Architecture

**8.1** When architecting an AI solution, which activity should occur before selecting specific tools/technologies?
A. Provisioning Azure infrastructure
B. **Defining business requirements, success criteria, and constraints**
C. Writing the agent's system prompt
D. Choosing the UI framework
**Answer: B**

**8.2 (Multi-select)** Which factors should influence the "build vs. buy vs. extend" decision for an AI component? (Choose all that apply)
A. **Cost and time to market**
B. **Availability of a fitting Microsoft/partner solution**
C. **Required customization and differentiation**
D. The personal preference of a single developer
**Answer: A, B, C**

---

## 9. Enterprise AI Adoption Strategies

**9.1** Which structure helps an enterprise maintain consistent standards, reusable components, and governance as AI adoption scales across business units?
A. Ad hoc departmental scripts
B. **A Center of Excellence (CoE)**
C. A single developer owning all AI projects
D. No shared standards, to maximize flexibility
**Answer: B**

**9.2** What is a common barrier to enterprise AI adoption that a CoE model directly addresses?
A. Too much available compute
B. **Inconsistent governance and duplicated effort across teams**
C. Excess documentation
D. Overly fast deployment cycles
**Answer: B**

---

## 10. Stakeholder Engagement and Requirements Gathering

**10.1** During requirements gathering for an AI agent, which technique best surfaces real user needs and edge cases?
A. Guessing based on similar past projects only
B. **Structured interviews/workshops with business stakeholders and end users**
C. Reviewing competitor marketing material
D. Skipping requirements and iterating in production
**Answer: B**

**10.2** Why is it important to involve compliance/legal stakeholders early when designing an AI agent that processes customer PII?
A. It is not necessary if the agent is internal-only
B. **Early involvement identifies regulatory/privacy constraints before architecture decisions are locked in**
C. It only matters after go-live
D. Compliance review only applies to financial data
**Answer: B**

---

## 11. AI Implementation Planning

**11.1** Which of the following should be included in an AI solution implementation plan?
A. Only the go-live date
B. **Environment strategy (Dev/Test/Prod), ALM approach, testing plan, rollback plan, and success metrics**
C. Just the model selection
D. Marketing collateral only
**Answer: B**

**11.2** What is the purpose of a pilot phase before full-scale AI agent rollout?
A. To delay the project indefinitely
B. **To validate assumptions, gather real usage data, and reduce risk before wider deployment**
C. To avoid writing documentation
D. To bypass stakeholder sign-off
**Answer: B**

---

## 12. Risk Assessment and Compliance

**12.1** Which activity should be performed to identify potential harms (bias, privacy, security) before deploying a customer-facing AI agent?
A. Skip directly to deployment and monitor afterward only
B. **Conduct a Responsible AI impact assessment**
C. Only test with internal employees forever
D. Rely solely on the vendor's marketing claims
**Answer: B**

**12.2 (Multi-select)** Which risks should be assessed when an AI agent will process regulated data (e.g., financial or health data)? (Choose all that apply)
A. **Data residency and cross-border transfer**
B. **Access control and least-privilege data exposure**
C. **Auditability of AI-driven decisions**
D. The color scheme of the agent's UI
**Answer: A, B, C**

---

## 13. Data Strategy for AI Solutions

**13.1** Why is data quality assessment a critical first step before deploying grounding data to an AI agent?
A. It has no real impact on agent output
B. **Poor-quality source data directly degrades the relevance and accuracy of agent responses**
C. It only matters for structured data
D. It is only relevant for training custom models
**Answer: B**

**13.2** Which approach ensures a single, consistent version of business data is available to multiple AI systems (agents, apps, analytics)?
A. Let each system maintain its own copy
B. **Establish a centralized, governed data layer (e.g., Dataverse) as the source of truth**
C. Export data to spreadsheets for each team
D. Avoid data governance to increase speed
**Answer: B**

---

## 14. AI-Powered Business Applications

**14.1** A sales team wants an AI agent embedded in Dynamics 365 Sales to summarize customer interactions and suggest next steps. Which capability should be used?
A. Power BI report subscriptions
B. **Copilot in Dynamics 365 Sales (embedded AI capabilities)**
C. A standalone Power App with no AI
D. Manual email templates
**Answer: B**

**14.2** Which factor most determines whether an AI-powered business application should use a prebuilt Copilot vs. a custom-built agent?
A. The color of the app icon
B. **Whether the required scenario/workflow is already covered by prebuilt capabilities vs. needing custom logic/data**
C. The number of app users
D. The app's release date
**Answer: B**

---

## 15. Monitoring, Optimization, and AI Lifecycle Management

**15.1** Which practice helps detect gradual degradation in an AI agent's response quality over time (model or data drift)?
A. One-time testing at launch only
B. **Ongoing monitoring with drift/quality metrics and periodic re-evaluation**
C. Disabling logging to save storage
D. Ignoring user feedback
**Answer: B**

**15.2** After identifying that an agent's model has degraded in accuracy, what is an appropriate lifecycle action?
A. Immediately decommission the entire solution
B. **Re-evaluate grounding data, refine prompts, and/or retrain/update the model as needed**
C. Ignore it since usage will decline naturally
D. Increase the agent's response length
**Answer: B**

---

## 16. Real-World Business Scenarios / Case Study Style

**Scenario:** A global retailer wants to deploy an AI agent to help store associates check inventory across regions, with data residency requirements varying by country, and requires human approval for any inventory transfer above a set value.

**16.1** Which Microsoft component should store and govern the multi-region inventory data used by the agent?
**Answer: Microsoft Dataverse, configured per regional environment/data residency requirements.**

**16.2** Which control ensures high-value inventory transfers are not executed autonomously by the agent?
**Answer: A human-in-the-loop approval step (e.g., Power Automate approval or a task agent that routes the decision to a manager) rather than autonomous execution.**

**16.3** Which testing type validates that the agent correctly retrieves inventory data across multiple regional Dataverse environments without errors?
**Answer: Integration testing.**

---

## 17. Multi-Select Scenario-Based Questions

**17.1 Scenario:** A healthcare provider is deploying a Copilot Studio agent to help staff answer patient scheduling questions, using data that includes some PHI (protected health information).

Which actions should be included in the solution? (Choose all that apply)
A. **Apply data classification/sensitivity labels and DLP policies to restrict PHI exposure**
B. **Restrict the agent's knowledge sources to only what's needed for scheduling (least privilege)**
C. **Log and audit all agent interactions involving PHI for compliance**
D. Allow the agent unrestricted access to all clinical records to "future-proof" it
**Answer: A, B, C** — Option D violates least-privilege and Responsible AI/compliance principles.

**17.2 Scenario:** A manufacturing company's AI agent frequently gives incomplete answers and is slow, and stakeholders also want better long-term governance as more departments adopt it.

Which actions should be included in the recommendation? (Choose all that apply)
A. **Add a relevant grounding data source to reduce incomplete answers**
B. **Establish a Center of Excellence to govern adoption across departments**
C. **Move to a multi-agent architecture to reduce response latency for complex tasks**
D. Remove all knowledge sources to speed up responses
**Answer: A, B, C** — Removing knowledge sources would speed responses at the cost of accuracy, which contradicts the goal.

**17.3 Scenario:** A company is evaluating ROAI across a mix of a mature production AI agent, a mid-stage pilot, and an early-stage experimental use case.

Which elements should the ROAI evaluation approach include? (Choose all that apply)
A. **A horizon-based view balancing near-term ROI (mature agent) against long-term strategic value (experimental use case)**
B. **Full cost quantification (development, deployment, operating) for each initiative**
C. **Differentiated success metrics appropriate to each initiative's maturity stage**
D. Applying the exact same ROI formula and timeline expectations to all three regardless of maturity
**Answer: A, B, C** — Option D ignores that initiatives at different maturity stages need different evaluation approaches.

---

*As with Part 1, any drag-drop/hotspot style question here that would normally show a bounded dropdown list is written out in full since no source PDF constrained the options for this set.*
