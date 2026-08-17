# AB-100: Agentic AI Business Solutions Architect — Practice Question Bank

These are original practice questions I've written to mirror the style, difficulty, and topic distribution of AB-100 (Copilot Studio, Microsoft Foundry, Dynamics 365 AI, Power Platform, ALM/Deploy domain). They are not reproductions of real exam items — treat them as a study tool, not a leaked question bank. Answers and rationale are included so you can check your reasoning, not just the letter.

---

## Section 1 — Single-Select Multiple Choice (10)

**Q1.** A retailer wants a Copilot Studio agent to answer questions using unstructured PDF product manuals stored in SharePoint, with minimal setup and no custom indexing pipeline. What should you configure as the knowledge source?
A. Azure AI Search index
B. SharePoint site/folder as a generative answers knowledge source
C. Azure Cosmos DB with vector search
D. Dataverse table import

**Answer: B** — Native SharePoint knowledge sources in Copilot Studio handle document ingestion and grounding automatically; Azure AI Search (A) is the right call only when you need custom indexing, chunking control, or non-SharePoint structured content.

---

**Q2.** You are designing an agent that must call a legacy on-premises SOAP API not exposed to the internet. Which component should you use to let the agent invoke this system securely?
A. A generative AI orchestration prompt
B. An on-premises data gateway with a custom connector
C. Azure AI Search connector
D. A Power Automate cloud-only flow

**Answer: B** — The on-premises data gateway is the standard bridge for reaching internal systems from cloud services like Copilot Studio/Power Platform; cloud-only flows (D) cannot reach non-internet-exposed endpoints.

---

**Q3.** A CFO wants an agent that flags invoices exceeding a variable, business-rule-driven threshold before approval. Which Copilot Studio capability best fits deterministic, rule-based logic rather than generative reasoning?
A. Generative orchestration with a broad system prompt
B. Topics with classic (structured) trigger phrases and conditions
C. A single knowledge-source-only agent
D. An autonomous agent with no topics

**Answer: B** — Deterministic business rules map to classic topics/conditions, which are predictable and auditable; generative orchestration (A) is better for open-ended reasoning, not strict rule enforcement.

---

**Q4.** You need to ensure an agent's responses to regulated financial questions never hallucinate figures and are always traceable to source documents. What should you enable?
A. Increase model temperature
B. Strict grounding to knowledge sources with citations enabled
C. Disable knowledge sources entirely
D. Use only generative orchestration with no knowledge sources

**Answer: B** — Grounding + citations constrains answers to source material and lets reviewers trace outputs; raising temperature (A) increases variability, the opposite of what's needed.

---

**Q5.** Which Azure service would you recommend for centrally monitoring token usage, latency, and error rates across multiple Foundry-hosted agents in production?
A. Azure Monitor / Application Insights
B. Azure DevOps Boards
C. Microsoft Purview only
D. Power BI Desktop

**Answer: A** — Azure Monitor/App Insights is purpose-built for telemetry (latency, errors, usage) across Azure-hosted workloads including Foundry agents; Purview (C) is for governance/data classification, not runtime telemetry.

---

**Q6.** A company wants to prevent an agent from being manipulated by malicious instructions embedded inside a user-uploaded document (prompt injection via content). What is the most effective mitigation to recommend?
A. Increase the agent's max response length
B. Content filtering/prompt shields plus instruction-hierarchy separation between system and content
C. Remove all knowledge sources
D. Rely solely on end-user training

**Answer: B** — Prompt shields and clear system/content separation are the recommended technical mitigation for indirect prompt injection; user training (D) helps but isn't a technical control.

---

**Q7.** You must choose a deployment approach for a Copilot Studio agent that guarantees isolated dev, test, and prod environments with promotion via solutions. What should you use?
A. Manual export/import of individual topics
B. Managed environments with solution-based ALM across environment tiers
C. A single shared environment for all stages
D. Direct publishing from a developer's default environment to production

**Answer: B** — Solution-based ALM across dev/test/prod managed environments is the supported pattern for isolation and repeatable promotion in Power Platform/Copilot Studio.

---

**Q8.** Which Responsible AI principle is primarily addressed by requiring human review before an autonomous agent executes an irreversible action (e.g., issuing a refund over $10,000)?
A. Transparency
B. Human oversight / accountability
C. Fairness
D. Inclusiveness

**Answer: B** — Human-in-the-loop checkpoints for high-impact actions map to the accountability/human oversight principle in Microsoft's Responsible AI framework.

---

**Q9.** A Dynamics 365 Finance customer wants an in-app Copilot experience that answers "how do I" questions using official Microsoft help content plus company-specific policy documents. What should you recommend?
A. Build a fully custom agent from scratch in Foundry only
B. Extend the built-in Dynamics 365 Finance Copilot with additional knowledge sources
C. Disable the built-in Copilot and use email support
D. Use Power BI Q&A visuals

**Answer: B** — Extending the existing in-app Copilot with supplemental knowledge sources is the recommended low-effort, high-fit approach rather than rebuilding from scratch.

---

**Q10.** You need to choose between Conversational Language Understanding (CLU), classic topics, and generative orchestration for an agent handling highly varied natural-language requests where intent isn't easily enumerated. What is the best fit?
A. Classic topics only
B. Generative orchestration
C. CLU with a fixed intent list only
D. No AI capability, static FAQ

**Answer: B** — Generative orchestration is designed for open-ended, high-variability intent handling where a fixed set of trigger phrases or intents would be impractical to enumerate.

---

## Section 2 — Multi-Select Multiple Choice (10)

**Q11.** Which two factors should you evaluate when deciding whether an agent should use generative orchestration versus classic topics? (Choose 2)
A. The variability and unpredictability of user phrasing
B. The color scheme of the Copilot Studio canvas
C. Whether responses must be deterministic/auditable for compliance
D. The number of Teams channels the org uses

**Answer: A, C**

---

**Q12.** Which two elements are part of a mature ALM strategy for Copilot Studio and Foundry agents? (Choose 2)
A. Automated CI/CD pipelines with solution checker/validation gates
B. Publishing directly to production without a test environment
C. Version-controlled solutions in a source repository
D. Allowing all makers to edit production directly

**Answer: A, C**

---

**Q13.** Which two risks should a security review specifically assess for an agent that can call external tools/APIs on a user's behalf? (Choose 2)
A. Over-permissioned connections that exceed least-privilege
B. Font rendering issues in the chat widget
C. Data exfiltration via tool outputs returned to untrusted contexts
D. The agent's average response character count

**Answer: A, C**

---

**Q14.** Which two metrics are most useful for a quarterly business review of agent effectiveness? (Choose 2)
A. Escalation/handoff rate to human agents
B. The exact GPT model version string
C. Task completion / resolution rate
D. Number of environment variables defined

**Answer: A, C**

---

**Q15.** When designing a multi-agent orchestration where a "router" agent delegates to specialist agents, which two design considerations matter most? (Choose 2)
A. Clear, non-overlapping scope/responsibility boundaries per specialist agent
B. Using the same exact system prompt for every specialist agent
C. A reliable handoff/context-passing mechanism between agents
D. Disabling logging on the router agent

**Answer: A, C**

---

**Q16.** Which two capabilities does Microsoft Foundry provide that are relevant to enterprise agent governance? (Choose 2)
A. Centralized model/connection management and access control
B. Automatic invoice generation for customers
C. Content safety and evaluation tooling for deployed models/agents
D. Built-in HR payroll processing

**Answer: A, C**

---

**Q17.** Which two are valid reasons to use Azure AI Search as a knowledge source instead of a native SharePoint/Dataverse connector? (Choose 2)
A. You need custom chunking, embeddings, or hybrid semantic + keyword search
B. The content is a single small FAQ document
C. You need to index data from multiple heterogeneous sources into one searchable index
D. You want to avoid any indexing at all

**Answer: A, C**

---

**Q18.** Which two practices support the Responsible AI principle of transparency in an agent solution? (Choose 2)
A. Disclosing to users that they are interacting with an AI agent
B. Hiding all citations from end users
C. Providing citations/sources for generated answers
D. Suppressing all error messages

**Answer: A, C**

---

**Q19.** Which two considerations should guide your choice between Model Context Protocol (MCP) and Agent2Agent (A2A) for an integration? (Choose 2)
A. MCP is typically used to connect an agent to tools/data sources
B. A2A is typically used for agent-to-agent communication and delegation across systems
C. MCP and A2A are mutually exclusive and can never be used in the same solution
D. Both protocols eliminate the need for authentication

**Answer: A, B**

---

**Q20.** Which two items should be included in a data loss prevention (DLP) review before deploying an agent broadly? (Choose 2)
A. Which connectors are classified as business vs. non-business data groups
B. The agent's avatar image
C. Whether sensitive data could flow to an ungoverned connector
D. The number of topics in the agent

**Answer: A, C**

---

## Section 3 — Drag-and-Drop (Match / Order) (10)

For each, match the item on the left to the correct target on the right (answers given below each question).

**Q21. Match the deployment method to the agent platform requirement**
Items: 1) Copilot Studio agent needing automated, repeatable, no-manual-intervention deployment  2) Foundry agent in a code-first repo needing the same
Targets: A) Solution pipelines (managed environments, ALM CI/CD)  B) Azure DevOps/GitHub Actions pipeline deploying Foundry resources via IaC (Bicep/ARM/Terraform)

**Answer:** 1→A, 2→B

---

**Q22. Match the testing type to its purpose**
Items: 1) Integration testing  2) User acceptance testing (UAT)
Targets: A) Validates data exchange correctly flows between Dynamics 365 Sales and Finance  B) Confirms the solution aligns with real business workflows as judged by end users

**Answer:** 1→A, 2→B

---

**Q23. Order the ALM promotion steps (1 = first, 4 = last)**
Items: Develop in dev environment | Export as managed solution | Import/test in test environment | Deploy to production environment

**Answer:** 1) Develop in dev environment → 2) Export as managed solution → 3) Import/test in test environment → 4) Deploy to production environment

---

**Q24. Match the Responsible AI principle to its implementation example**
Items: 1) Fairness  2) Privacy & Security  3) Accountability
Targets: A) Encrypting data at rest and enforcing least-privilege connections  B) Testing the agent across diverse user groups to avoid biased outcomes  C) Requiring human approval before high-impact autonomous actions

**Answer:** 1→B, 2→A, 3→C

---

**Q25. Match the knowledge source type to the best-fit scenario**
Items: 1) Dataverse table  2) Azure AI Search index  3) Public website
Targets: A) Structured CRM records needing real-time query  B) Heterogeneous multi-source content needing custom relevance tuning  C) Publicly available product documentation pages

**Answer:** 1→A, 2→B, 3→C

---

**Q26. Order the incident response steps for an agent producing harmful output (1 = first, 4 = last)**
Items: Disable/pause the agent | Root-cause analysis using telemetry/logs | Notify stakeholders | Apply fix and re-test before re-enabling

**Answer:** 1) Disable/pause the agent → 2) Notify stakeholders → 3) Root-cause analysis using telemetry/logs → 4) Apply fix and re-test before re-enabling

---

**Q27. Match the orchestration pattern to its description**
Items: 1) Hub-and-spoke (router + specialists)  2) Sequential pipeline  3) Peer-to-peer via A2A
Targets: A) One agent classifies and hands off to the right specialist  B) Agents pass output as input to the next in fixed order  C) Independent agents negotiate/delegate tasks directly to each other

**Answer:** 1→A, 2→B, 3→C

---

**Q28. Match the monitoring signal to what it reveals**
Items: 1) Token usage trend  2) Escalation rate  3) Latency P95
Targets: A) Cost growth and potential prompt-size issues  B) Agent capability gaps needing more training/topics  C) User experience/responsiveness under load

**Answer:** 1→A, 2→B, 3→C

---

**Q29. Order the steps to add a new knowledge source to a production agent safely**
Items: Validate source content quality/format | Test in a non-production environment | Add source in dev and configure grounding | Promote via managed solution to production

**Answer:** 1) Validate source content quality/format → 2) Add source in dev and configure grounding → 3) Test in a non-production environment → 4) Promote via managed solution to production

---

**Q30. Match the governance control to the risk it addresses**
Items: 1) DLP policy  2) Environment strategy (dev/test/prod separation)  3) Content moderation/filters
Targets: A) Sensitive data flowing to unapproved connectors  B) Untested changes reaching real users  C) Generation of harmful or inappropriate content

**Answer:** 1→A, 2→B, 3→C

---

## Section 4 — Drop-Down Selection (Complete the Diagram/Statement) (10)

Fill each blank by choosing from the options in brackets.

**Q31.** A finance approval agent must never approve payments over policy limits without a human. This requires [ Human-in-the-loop checkpoint / Fully autonomous execution / Generative-only response ].
**Answer:** Human-in-the-loop checkpoint

**Q32.** To search across PDFs, database records, and API results as a single grounded knowledge base, use [ Azure AI Search / A single Dataverse table / Plain text topic responses ].
**Answer:** Azure AI Search

**Q33.** For repeatable, environment-isolated deployment of Copilot Studio agents, use [ Managed solutions promoted through environments / Manual copy-paste of topics / Shared dev/prod environment ].
**Answer:** Managed solutions promoted through environments

**Q34.** To let one agent call a specialized pricing-calculation agent hosted elsewhere, the recommended open protocol is [ Agent2Agent (A2A) / SMTP / FTP ].
**Answer:** Agent2Agent (A2A)

**Q35.** To give an agent access to a specific external tool's live data (e.g., a ticketing system) in a standardized way, use [ Model Context Protocol (MCP) / RSS feed / Static CSV upload ].
**Answer:** Model Context Protocol (MCP)

**Q36.** To detect and block attempts to override an agent's system instructions via user or document content, enable [ Prompt shields / Higher temperature / Larger context window ].
**Answer:** Prompt shields

**Q37.** To track cost, latency, and failure trends for agents running in Foundry over time, integrate with [ Azure Monitor / Outlook Calendar / SharePoint versioning ].
**Answer:** Azure Monitor

**Q38.** To ensure sensitive customer data isn't sent to an ungoverned third-party connector, configure [ Data Loss Prevention (DLP) policies / A longer system prompt / A new topic ].
**Answer:** Data Loss Prevention (DLP) policies

**Q39.** For a scenario needing flexible handling of open-ended, unpredictable user requests without enumerating every intent, choose [ Generative orchestration / Classic topics with fixed trigger phrases / No AI ].
**Answer:** Generative orchestration

**Q40.** To validate that an agent solution passes governance/quality checks automatically before deployment, include a [ Solution checker in the CI/CD pipeline / Manual email approval only / No validation step ].
**Answer:** Solution checker in the CI/CD pipeline

---

## Section 5 — Case Study (Multi-Part, Scenario-Based)

### Case Study: Contoso Manufacturing

**Background:**
Contoso Manufacturing runs Dynamics 365 Finance, Dynamics 365 Supply Chain Management, and Dynamics 365 Sales. They want to deploy:
- A Copilot Studio customer-facing agent for order status and returns.
- A Foundry-hosted internal agent that analyzes supply chain disruptions using data from SQL, flat files, and a public logistics API.
- A multi-agent setup where the customer-facing agent can delegate complex return-eligibility questions to an internal policy agent.

**Requirements:**
- Customer data must never leave approved, DLP-governed connectors.
- The supply chain agent's answers must be traceable to source data.
- Deployment must be fully automated with dev/test/prod isolation.
- High-impact actions (e.g., approving returns over $5,000) require human approval.
- The company must be able to monitor cost and latency across all agents.

**Q41.** Which knowledge source strategy should you recommend for the supply chain disruption agent, given its mixed SQL, flat-file, and API data?
A. Azure AI Search index built from all three sources
B. Only a Dataverse table
C. Only the public API, ignoring internal data
D. No structured knowledge source, generative-only

**Answer: A** — heterogeneous sources need a unified, custom index.

**Q42.** What governance control most directly ensures customer data doesn't flow through unapproved connectors?
A. DLP policy scoping connectors into business/non-business groups
B. A longer topic name
C. Disabling the agent's avatar
D. Increasing max tokens

**Answer: A**

**Q43.** How should the return-eligibility delegation between the customer-facing agent and internal policy agent be implemented?
A. Agent2Agent (A2A) communication pattern
B. Copy-pasting the policy document into every customer chat
C. A shared Excel file updated manually
D. Disabling the internal agent

**Answer: A**

**Q44.** What should trigger human review for a return request?
A. Return value exceeding the defined policy threshold (e.g., $5,000)
B. Any return under $10
C. Every single interaction regardless of value
D. Never — full autonomy for all returns

**Answer: A**

**Q45.** Which deployment approach satisfies "fully automated with dev/test/prod isolation"?
A. CI/CD pipeline promoting managed solutions across managed environments
B. Manual export/import by a single admin
C. Editing directly in production
D. Ad hoc publishing from developer sandboxes

**Answer: A**

**Q46.** What should you configure to make the supply chain agent's answers traceable to source data?
A. Grounding with citations enabled against the AI Search index
B. Disabling citations for a cleaner UI
C. Free-form generative answers with no source linkage
D. Removing the knowledge source

**Answer: A**

**Q47.** What is the best way to monitor cost and latency across all three agents centrally?
A. Azure Monitor/Application Insights dashboards spanning the agents' hosting environments
B. Manually asking each agent for its own stats
C. Reviewing Dynamics 365 Sales pipeline reports
D. No monitoring needed post-launch

**Answer: A**

**Q48.** Which testing type validates that the return-eligibility handoff between the two agents functions correctly end-to-end?
A. Integration testing
B. Unit testing of a single topic in isolation
C. Load testing of the UI theme
D. Spelling/grammar review only

**Answer: A**

---

## Section 6 — Yes/No Hotspot Questions

*(Format note: in the real exam, these appear as a set of statements under one scenario, answered Yes/No, and cannot be revisited after submission — so treat each set as final once you decide.)*

**Scenario:** A sales team uses a Copilot Studio agent via headset in a call center. The agent can look up order status, and can also issue refunds. Refunds under $500 are auto-approved; refunds $500+ require supervisor approval. All conversations are logged for quality review, but credit card numbers must never appear in logs.

**Statement 1:** The agent should escalate to a human supervisor automatically when a refund request is $500 or more.
**Answer: Yes** — Reason: this matches the stated business rule for human-in-the-loop approval above a threshold; it's a deterministic policy, not a judgment call for the agent to override.

**Statement 2:** Credit card numbers should be redacted or excluded from conversation logs even though full logging is otherwise required.
**Answer: Yes** — Reason: sensitive payment data (PCI-scoped) must be excluded/masked from logs regardless of a general logging requirement; this is a security/compliance control, not optional.

**Statement 3:** The agent should be allowed to auto-approve a $500 refund if the customer sounds frustrated, to improve satisfaction.
**Answer: No** — Reason: the $500 threshold is a fixed governance rule; allowing sentiment to override a compliance threshold undermines the control and introduces inconsistent, unaudited exceptions.

---

**Scenario 2:** An HR-facing autonomous agent in Dynamics 365 can update employee records and trigger onboarding workflows without a human in the loop, based on a nightly batch trigger.

**Statement 1:** Because the agent runs autonomously, it does not need any monitoring or telemetry review.
**Answer: No** — Reason: autonomous agents require monitoring even more than human-in-the-loop ones, since there's no real-time human check on individual actions; telemetry is how errors get caught.

**Statement 2:** Changes made by the autonomous agent should still be traceable to a specific run/trigger for audit purposes.
**Answer: Yes** — Reason: auditability of autonomous actions is a core accountability requirement, especially for HR/PII data changes.

**Statement 3:** The agent should have unrestricted write access to all HR fields, including compensation, to simplify configuration.
**Answer: No** — Reason: least-privilege access design means the agent's permissions should be scoped tightly to onboarding-relevant fields, not broadened for convenience.

---

## How to Use This Bank

- Work through each section untimed first, writing out *why* each wrong answer is wrong — that reasoning is what the real exam tests (per your notes, it's scenario/trade-off based, not recall-based).
- Re-take Section 5 (case study) timed, since real case studies are the format most people underestimate.
- Since Deploy-domain content (ALM, monitoring, security, Responsible AI) is ~40-45% of the real exam, most of Sections 1-6 here lean that direction on purpose — if you found those items easy, that's a good sign; if not, that's where to spend remaining study time.
