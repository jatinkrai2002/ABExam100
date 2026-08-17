# Architect AI Solutions for Business Productivity — Answer Key (Source 20 Questions)
*(From questions-test-questions.pdf, with full option lists confirmed)*

**1.** B — Verify and cleanse the Dataverse data.
*Poor grounding results usually trace back to poor source data quality, not agent retraining or UI elements.*

**2.** C — Export as a managed solution and import into Prod1.
*Managed solutions are the standard, low-effort way to promote Copilot Studio/Power Platform components across environments (Dev → Prod).*

**3.** HOTSPOT
- Prompt validation techniques: **Use prompts that have varied phrasing.**
- Metrics: **Response relevance and accuracy.**

**4.** HOTSPOT
- "Help the customer as best you can" → **Rewrite the prompt with clear and task-specific instructions.**
- Retrieve product info from knowledge base → **Use responses with only reference sources and limit the response scope.**
*(This restricts the agent to grounded answers, ensuring consistency and accuracy — the other two options either add uncontrolled variability or remove grounding entirely.)*

**5.** D — Ensure cross-region data movement is enabled for the Canadian environment and connector dependencies.
*Data resides in Canada; the Azure OpenAI connector call to the US requires cross-region movement to be explicitly permitted under residency policy — you don't move the tenant or force OpenAI storage to the US.*

**6.** DRAG DROP
- Properly exchanges data between the Dynamics 365 apps → **Integration testing**
- Aligns with defined user workflows and business processes → **User acceptance testing**

**7.** D — Identify and quantify all the development, deployment, and operating costs.
*You must establish the cost baseline before ROAI can be calculated accurately.*

**8.** A — Microsoft Dataverse.
*Provides a governed, centralized data store with built-in classification/protection and serves multiple consumers (Copilot Studio, Dynamics 365, external AI via connectors).*

**9.** B — A horizon-based framework (e.g., Three Horizons model).
*Balances near-term returns against long-term/strategic value across a portfolio of initiatives at different maturity stages.*

**10.** D — Centralize the product catalog data in Microsoft Dataverse and expose it to both agents.
*Avoids duplication/inconsistency from per-agent scraping or separate custom tables.*

**11.** A — Azure AI Search.
*Indexes heterogeneous sources (SQL, files, APIs, logs) into a searchable knowledge index usable by Copilot Studio.*

**12.** C — Configure a task agent to generate fraud risk scores for the human analyst to review.
*Keeps a human in the loop for the final decision, unlike an autonomous closing agent.*

**13.** DRAG DROP
- To improve performance: **Move to a multi-agent architecture** (splits the single overloaded agent/prompt, reducing latency).
- To improve accuracy: **Add a grounding data source** (directly resolves incomplete results and weak domain-specific reasoning by anchoring responses to authoritative data). *Upgrading to a larger generative AI model is a reasonable secondary/alternate answer for the accuracy row if the exam allows multiple selections — grounding is the primary fix.*

**14.** HOTSPOT
- Ensure consistent AI responses: **Define standardized prompt templates.**
- Support governance and version control: **Store prompts in a Git repository.**

**15.** A — Microsoft Copilot Studio skills.
*Skills are the mechanism for extending Microsoft 365 Copilot to call external/Azure-hosted logic.*

**16.** D — A file upload.
*Adding a file-based knowledge source lets Copilot answer from internal process documents without creating new topics in the finance-and-operations Copilot.*

**17.** DRAG DROP
- Agent1 (simple/short phrases, standard model, no generative orchestration) → **Natural language understanding (NLU)**
- Agent2 (Dynamics 365 Contact Center voice channel) → **Natural language understanding + (NLU+)** *(NLU+ is required for voice/telephony channel support.)*

**18.** B — Map the field display names as business terms.
*Lowest-effort way to align non-standard schema names with meaningful terms Copilot can use for summarization.*

**19.** A — Microsoft Cloud Adoption Framework for Azure. *(Confirmed correct in your source PDF.)*

**20.**
- For Microsoft Copilot Studio best practices → **The ALM Accelerator for Microsoft Power Platform**
- For conversational user experiences → **Microsoft Power Platform Well-Architected Framework**
*(Confirmed correct in your source PDF.)*

---

For the extended 50-question practice set (10 each of HOTSPOT, Case Study, Dropdown, Generic, and Yes/No) built around these same exam domains, see **Architect-AI-Solutions-Practice-QA.md** (Part 1) and **Architect-AI-Solutions-Practice-QA-Part2.md** (Part 2 — covering agentic AI, governance, adoption strategy, risk/compliance, and scenario-based multi-select questions).
