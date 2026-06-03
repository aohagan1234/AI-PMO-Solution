# R&D Funding Application — Draft Responses
### First Derivative | Internal Application Form for R&D Project Funding

**Status key:**
- ✅ Draft ready — drawn from existing project documents
- ⚠️ Partial draft — needs team input to complete
- ❌ Team input required — cannot be drafted without further information

---

## Section 1: Project Overview

---

### Q1. Working title of proposed project ✅

**PMO AI Intelligence Platform**

*Alternative: AI-Powered Project Management Office (PMO) Automation Suite*

---

### Q2. Succinct summary (max 100 words) ✅

Project Management Offices spend the majority of their time on repetitive, judgment-intensive work: extracting action items from meetings, writing status reports, tracking resources, and managing commitments across fragmented systems. This project will build an AI-powered PMO platform using an orchestrated multi-agent architecture, where specialist AI agents transform unstructured inputs — meeting transcripts, project data, emails — into governed, structured outputs. Every AI action requires human approval before reaching a system of record. The platform will reduce PMO administrative overhead by an estimated 50%, while improving governance consistency, risk visibility, and decision traceability across client portfolios.

---

## Section 2: Key Technical Criteria (Invest NI)

---

### Q3. New scientific or technical knowledge ⚠️

The project will advance knowledge in the following technically novel areas:

**1. Domain-specific agentic AI for governance-critical workflows**
Existing large language model (LLM) applications focus on general-purpose text generation. This project develops and evaluates LLM-based agents specifically trained and prompted for PMO governance taxonomy — classifying meeting content into formal RAID categories (Risks, Actions, Issues, Decisions) with confidence scoring. The challenge of accurately distinguishing a Risk from an Issue, or a Decision from a proposal, in natural language is a non-trivial classification problem that requires domain-specific evaluation frameworks not currently available.

**2. Confidence-scored classification with human-in-the-loop enforcement**
The project will research optimal confidence thresholds for AI-assisted classification in governance contexts — specifically, how to calibrate AI confidence scores to minimise false positives (incorrect RAID entries) while maximising recall (ensuring nothing is missed). This produces novel knowledge about human-AI collaboration patterns in high-accountability environments where errors have downstream legal or governance consequences.

**3. Multi-agent orchestration for cross-source PMO intelligence**
The platform will develop an orchestrator-agent architecture that routes unstructured inputs from multiple sources (transcripts, project management tools, emails) to specialist sub-agents, synthesises their outputs, and manages approval workflows. Research questions include: how to handle conflicting signals across sources, how to maintain context across agent interactions, and how to enforce governance rules as architectural constraints rather than post-hoc checks.

> ⚠️ **TEAM INPUT NEEDED:** If there is a planned academic partnership (see Q7), the research questions above could be formalised as a joint research agenda. This section will be stronger with a named academic collaborator.

---

### Q4. Product or process development and improvements ✅

The platform directly improves the following PMO processes, each validated through surveys and interviews with PMOs at financial services clients:

**Meeting follow-up (currently: 20–30 min per meeting / ~80 meetings/month)**
AI agents extract and classify RAID items, propose JIRA updates, and draft follow-up emails. Follow-up time reduces from ~30 minutes to under 5 minutes. All outputs require PMO approval before any system is updated.

**Status reporting (currently: ~45 min per report / ~50 reports/month)**
AI agents pull data from JIRA, SharePoint, and MS Project; reconcile inconsistencies; analyse budget variance; and generate audience-adapted narratives for executives, steering groups, and project teams — from a single data source.

**Personal task management (currently: ~2 hours/day)**
AI agents consolidate commitments from email, meetings, and JIRA into a single daily task list, with PMO-context-aware prioritisation and automatic completion detection.

**Strategic resourcing (currently: reactive, manual, frequently too late)**
AI agents monitor resource end dates, detect upcoming gaps, and recommend best-fit placements with trade-off explanations — surfacing gaps weeks earlier than current manual processes allow.

---

### Q5. Development of leading edge technology ✅

The platform applies the following leading-edge technologies in a novel combination:

- **Large Language Models (LLMs)** — applied to domain-specific PMO classification tasks (RAID taxonomy, commitment extraction, risk signal synthesis) rather than general-purpose generation
- **Multi-agent orchestration** — a central orchestrator routes inputs to specialist sub-agents (Meeting Intelligence, Report Generation, Resourcing, Task Management), each with defined scope, confidence thresholds, and escalation rules
- **Governed agentic AI** — a novel architectural pattern in which AI autonomy levels are explicitly defined and enforced (from fully agentic to human-only) at the workflow level, not as a post-hoc safety layer. This is particularly relevant in regulated financial services environments where AI governance is a compliance requirement
- **Cross-source signal synthesis** — combining structured data (JIRA, MS Project, SharePoint) with unstructured data (meeting transcripts, emails) to identify emerging risks before they are raised by humans
- **Microsoft Graph API + JIRA REST API integration** — enabling real-time, bidirectional data flows between AI outputs and enterprise project management systems

---

### Q6. Digital Process Innovation ✅

The project represents end-to-end digital process innovation across four core PMO workflows:

- **Meeting-to-governance pipeline:** Transforms an entirely manual, error-prone process (listening → noting → classifying → logging → updating) into an automated, governed digital workflow triggered by a meeting transcript
- **Automated multi-audience reporting:** Eliminates manual data extraction and report formatting; a single data pull generates multiple audience-adapted outputs automatically
- **Proactive resource intelligence:** Shifts resource management from reactive (manual checking of spreadsheets) to proactive (continuous monitoring with automated gap alerts)
- **Unified task consolidation:** Replaces fragmented personal task management across email, calendar, and project tools with a single AI-consolidated daily task list

The innovation is not incremental — it removes entire manual steps from PMO workflows rather than making existing steps marginally faster.

---

### Q7. Collaboration with NI college or university ❌

> **TEAM INPUT REQUIRED**
> This criterion significantly increases approval likelihood. Has any outreach been made to Ulster University, Queen's University Belfast, or another NI institution?
> Potential collaboration angles:
> - Research partnership on AI confidence scoring and governance enforcement
> - PhD studentship focused on agentic AI in regulated environments
> - Joint publication on human-in-the-loop AI design patterns for financial services
> Please confirm if a collaboration is planned or in discussion.

---

### Q8. Commercial viability ✅

**Target market:** Financial services PMOs — a segment with high meeting volume, complex governance requirements, and strong demand for automation. Initial target clients include MUFG, Citi, Bank of America, Bank of Ireland, AIB, Mizuho, Natwest, and Northern Trust — all existing First Derivative relationships.

**Validated demand:** PMO surveys conducted across client sites confirm demand. Direct stakeholder quotes include: *"Raw meeting notes, action items, RAID logs"*, *"Automate reports, automate scorecards"*, *"Resources finishing up, match it up."* A senior PMO at Citi stated: *"Citi needs predictive PMOs — can do more with AI than they are doing."*

**Quantified time savings (per PMO, annually):**

| Workstream | Estimated Annual Saving |
|---|---|
| Meeting Intelligence | ~$18,000 |
| Status Reports | ~$26,250 |
| Personal Task Management | ~$8,250 |
| Strategic Resourcing | Qualitative (one avoided wrong placement = weeks of rework) |
| **Total (quantifiable)** | **~$52,500 per PMO** |

At scale across a portfolio PMO function (10+ PMOs), the annual value exceeds $500,000 — making a subscription or licensing model commercially viable.

> ⚠️ **TEAM INPUT NEEDED:** Specific client contract references, signed LOIs, or confirmed pilots would strengthen this section significantly.

---

## Section 3: Additional Criteria

---

### Q9. NI job creation and/or retention ❌

> **TEAM INPUT REQUIRED**
> Please confirm: How many team members working on this project are based in Northern Ireland? Will this project require new hires based in NI? What is the expected headcount over the project duration?
> This is a key Invest NI criterion — a clear NI employment story is essential.

---

### Q10. Delivery location ❌

> **TEAM INPUT REQUIRED**
> Please confirm the primary delivery location(s). Invest NI requires a strong NI reference point. Are core team members based in Belfast, Newry, or elsewhere in NI?

---

### Q11. Skills to sell, solution and deliver ⚠️

First Derivative has the domain expertise and client relationships to sell and deliver this solution:

- **PMO domain expertise:** Deep experience delivering PMO services across tier-1 financial services institutions, with existing relationships at MUFG, Citi, Bank of America, AIB, Bank of Ireland, Mizuho, Natwest, and Northern Trust
- **AI/technology capability:** Experience building and deploying AI solutions in enterprise environments, including integration with Microsoft 365, JIRA, and SharePoint ecosystems
- **Client proximity:** PMOs currently embedded on client sites across the target accounts, with direct visibility of the pain points this tool addresses

> ⚠️ **TEAM INPUT NEEDED:** Please add specific named capabilities, certifications, or prior AI delivery examples to strengthen this section.

---

### Q12–13. Who will work on the project / total hours ❌

> **TEAM INPUT REQUIRED**
> Please provide:
> - Named individuals, titles, levels, and locations
> - Estimated hours per person for the project duration
> *The Template Automation Work Plan spreadsheet in the Leah documents folder may be the right place to capture this detail.*

---

### Q14. Competitors and what they are doing ✅

| Competitor | Offering | Gap vs PMO AI Platform |
|---|---|---|
| Microsoft Copilot for M365 | Meeting summaries, action lists, email drafts | No RAID classification, no system write-back, no approval workflow, no audit trail |
| Zoom AI Companion | Meeting summaries, action items, smart chapters | No PMO taxonomy, no governance integration |
| Power BI + Copilot | Data dashboards, narrative generation | No cross-source reconciliation, no meeting intelligence integration, no governed distribution |
| ServiceNow (project modules) | Workflow automation, reporting | Heavy enterprise implementation; not AI-native; not PMO-specific |
| Monday.com / Asana AI | Task management with AI features | General-purpose; no RAID taxonomy, no financial services governance |

**Key differentiator:** Competitors produce AI-generated output. This platform produces governed outcomes — with human approval built into every step that matters, and a full audit trail suitable for regulated financial services environments.

---

### Q15. Has the client requested this project innovation? ✅

Yes. The project originated from direct stakeholder feedback at financial services clients. PMO surveys and interviews conducted across MUFG, Citi, and other client sites confirmed the pain points and appetite for this solution. Specific client quotes include:

- *"Raw meeting notes, action items, RAID logs"* — MUFG PMO
- *"Automate reports, automate scorecards"* — MUFG PMO
- *"Resources finishing up, match it up, skills pool"* — MUFG PMO
- *"Citi needs predictive PMOs — do not view them as advisory, can do more with AI"* — Citi PMO interview
- *"Automation of basic admin tasks would save significant time — minutes and actions, project descriptions, risks"* — PMO survey respondent

Survey data shows all respondents either agreed or strongly agreed that AI could save time on routine PMO tasks and that governance guidance around AI use would be valuable.

---

### Q16. Client value proposition ✅

> *"We give your PMOs back the time they spend on things that shouldn't need them — meeting follow-up, status reporting, resource tracking, and personal task overload — so they can focus on stakeholder management, governance, and strategic decision support."*

Specific value delivered:

- **No more lost RAID items:** Every meeting produces a structured, approved RAID log entry within 30 minutes
- **No more decision disputes:** Every decision is documented with source traceability to the meeting transcript
- **Reports in 10 minutes, not 45:** Status reports are auto-generated with audience-adapted versions from a single data pull
- **Resource gaps caught early:** Proactive alerts surface resourcing issues weeks before they become crises
- **Consistent governance:** Every project assessed against governance standards automatically, not dependent on who happens to review it

The tool frees PMO time for the work only humans can do: stakeholder relationships, escalation judgment, and strategic advice.

---

### Q17. Key client decision-makers and access ⚠️

Target accounts and contacts are being developed through existing embedded PMO relationships:

| Client | First Derivative Contact |
|---|---|
| MUFG | Nikolas (confirmed outreach) |
| Citi | Gavin |
| AIB | Olivia |
| Mizuho | Ana |
| Natwest | Leah |
| Northern Trust | Dearbhla |
| Bank of America | To be confirmed |
| Bank of Ireland | To be confirmed |

> ⚠️ **TEAM INPUT NEEDED:** Please confirm specific decision-maker names and seniority at each client, and whether any have been briefed on this initiative.

---

### Q18. Pricing ❌

> **TEAM INPUT REQUIRED**
> No pricing model has been defined. Suggested options to consider:
> - Per-seat subscription (per PMO user/month)
> - Per-project or per-portfolio licence
> - Managed service / outcome-based pricing
> - Bundled with existing PMO managed service contracts
> Please confirm the intended commercial model.

---

### Q19. How will we deliver it? ✅

Delivery follows a phased wave approach, building on a foundational integration layer:

| Wave | Capabilities | Rationale |
|---|---|---|
| Wave 1 | Meeting Intelligence | Highest value; builds the data and integration foundation (Teams/Zoom, JIRA, SharePoint) |
| Wave 2 | Status Reports + Personal Task Management + Strategic Resourcing | Leverage Wave 1 outputs; can run in parallel |
| Wave 3 | Governance Monitoring + Stakeholder Communications + Proactive Risk Monitoring + Change Request Management | Require Wave 1–2 data foundations |
| Wave 4 | Lessons Learned + Dependency Tracking | Require mature data across the full portfolio |

Each wave will include: requirements validation with client PMOs, agent development and testing against labelled sample data, human-in-the-loop integration, and PMO training. Accuracy targets (≥85% RAID classification, ≥95% capture rate) will be validated before each wave is released to production.

---

### Q20. How will we sell it and who will sell it? ❌

> **TEAM INPUT REQUIRED**
> Please confirm:
> - Is this positioned as a standalone product or an add-on to existing PMO managed service contracts?
> - Who owns the commercial conversation at each target client?
> - Is there a planned go-to-market timeline or pilot programme?

---

## Section 4: Software Offering

---

### Q21. Value proposition — what sets the product apart ✅

The PMO AI Platform is the only AI tool built specifically for financial services PMO governance workflows. Unlike generic AI tools (Copilot, ChatGPT) which produce text output, this platform produces governed outcomes:

- **PMO-specific taxonomy:** Classifies content using formal RAID methodology, not generic action items
- **System write-back:** Proposes structured entries directly into RAID logs and JIRA, in the correct schema
- **Enforced approval workflow:** Nothing reaches a system of record without explicit human sign-off
- **Full audit trail:** Every AI proposal and human decision is logged — essential for regulated environments
- **Cross-source intelligence:** Synthesises meeting transcripts, project data, and email into a single coherent view
- **Consistent governance:** Applies the same standards across every project, not dependent on who reviews it

Validated by PMOs on client sites who confirmed that current tools are *"not sufficiently tailored to PMO needs"* and produce outputs that are *"not always accurate."*

---

### Q22. Upfront investment required ❌

> **TEAM INPUT REQUIRED**
> Please provide estimates for: development resource costs, infrastructure/cloud costs, tooling/API costs, and sales/marketing investment required to be credible in the market.

---

### Q23. Scalability ⚠️

The platform is designed for scalability from the outset:

- **API-first architecture:** All integrations use standard REST APIs (JIRA, Microsoft Graph, SharePoint) — adding new clients requires configuration, not re-development
- **Multi-agent design:** Individual agents can be scaled independently based on workload — a client with high meeting volume can scale Meeting Intelligence without scaling all components
- **Stateless agent design:** Agents process inputs and produce outputs without persistent state, enabling horizontal scaling
- **Configurable per client:** Governance rules, confidence thresholds, RAID schemas, and JIRA field mappings are configuration, not code — allowing rapid client onboarding

> ⚠️ **TEAM INPUT NEEDED:** Cloud platform choice (Azure, AWS, GCP), containerisation approach (Kubernetes, etc.), and expected concurrent user volumes need to be defined.

---

### Q24. Security ✅

Security is built into the platform architecture at multiple levels:

- **Authentication:** All integrations use OAuth 2.0 via Azure Active Directory — no passwords stored, access revocable
- **Human-in-the-loop enforcement:** No AI action writes to an external system or sends a communication without explicit PMO approval — reducing the attack surface of automated actions
- **PII handling:** Meeting transcripts may contain personal information. The platform detects and masks PII in all debug, trace, and audit logs
- **Audit trail:** Every AI proposal and human decision is logged with timestamp, user ID, and confidence score — providing a complete chain of evidence for compliance review
- **Data minimisation:** The platform processes data in transit; meeting transcripts are not stored longer than required for the processing workflow
- **Role-based access:** Approval workflows are role-gated — only authorised PMO users can approve RAID entries, JIRA updates, or outbound communications

> ⚠️ **TEAM INPUT NEEDED:** Specific data residency requirements (particularly for financial services clients), penetration testing plans, and ISO 27001 / SOC 2 certification approach should be added.

---

### Q25. User experience and user journeys ⚠️

The platform supports the following primary user journeys:

**Journey 1 — Post-meeting review (PMO Analyst)**
Meeting ends → transcript auto-ingested → RAID proposals and follow-up email draft appear in review queue within 30 minutes → PMO reviews, approves/modifies/rejects each item → approved items written to RAID log and JIRA → follow-up email sent.

**Journey 2 — Daily task check (PMO)**
PMO opens daily checklist → consolidated task list drawn from email, meetings, and JIRA → items ranked by priority → PMO works through list, ticking off completed items → AI auto-detects completions where possible.

**Journey 3 — Status report approval (PMO Lead)**
Report cycle triggered → data automatically pulled from JIRA/SharePoint/MS Project → AI generates draft narratives for each audience → PMO Lead reviews, refines, approves → reports distributed automatically.

**Journey 4 — Resource gap alert (PMO Lead)**
System detects resource finishing in 4 weeks → alert raised with match recommendation → PMO Lead reviews recommendation and trade-offs → resource commitment confirmed by PMO Lead.

> ⚠️ **TEAM INPUT NEEDED:** Wireframes or UX mockups should be developed to support this section for the full application.

---

### Q26. Subscription model ❌

> **TEAM INPUT REQUIRED**
> See Q18. Pricing and commercial model not yet defined. This section cannot be drafted without that input.

---

### Q27. Infrastructure and technology stack ⚠️

**Core components:**

| Layer | Technology |
|---|---|
| AI / LLM | Large language models (Claude / GPT-4 class) via API — model-agnostic design |
| Orchestration | Multi-agent framework (LangGraph or equivalent) managing specialist sub-agents |
| Integrations | Microsoft Graph API (Teams, SharePoint, Outlook), JIRA REST API, Zoom API |
| Authentication | OAuth 2.0 / Azure Active Directory |
| Data storage | Cloud-hosted (to be confirmed) — structured outputs stored per client configuration |
| Audit logging | Append-only audit log per action — immutable record of all AI proposals and human decisions |

> ⚠️ **TEAM INPUT NEEDED:** Cloud platform (Azure preferred given Microsoft integrations), containerisation, CI/CD pipeline, and SLA commitments need to be defined.

---

### Q28. Deployment model ❌

> **TEAM INPUT REQUIRED**
> Options to consider:
> - **Multi-tenant SaaS** — most scalable; lower per-client cost; data segregation required
> - **Single-tenant hosted** — preferred by some financial services clients for data isolation
> - **Client-hosted / hybrid** — for clients with strict data residency requirements (common in financial services)
> Please confirm the intended deployment approach.

---

### Q29. Customer support ❌

> **TEAM INPUT REQUIRED**
> Please define: support tiers (L1/L2/L3), SLAs, support channels, and whether support is delivered by First Derivative directly or via a third party.

---

### Q30. Continuous improvement ⚠️

The platform is designed for continuous improvement through several mechanisms:

- **Human feedback loop:** Every PMO approval, rejection, or modification of an AI proposal is logged and can be used to fine-tune confidence thresholds and improve classification accuracy over time
- **Acceptance rate monitoring:** If the RAID proposal acceptance rate falls below 80%, this triggers a review of extraction logic — a built-in quality gate
- **Versioned configuration:** All client-specific settings (thresholds, schemas, field mappings) are versioned, allowing rollback and audit of configuration changes
- **Wave-based roadmap:** The phased delivery approach (four waves) ensures the codebase grows incrementally with validated foundations at each stage before new capabilities are added

> ⚠️ **TEAM INPUT NEEDED:** Formal release cadence, codebase management approach (branching strategy, CI/CD, testing standards), and product ownership model should be defined.

---

### Q31. Compliance ✅

The platform is designed with compliance as a first-class concern, particularly relevant for financial services clients:

- **GDPR:** PII in meeting transcripts is detected and masked in logs. Data minimisation is applied — transcripts are processed, not stored indefinitely. Data subject rights (access, deletion) are supported through the audit log and data management pipeline
- **Financial services regulation:** The human-in-the-loop design ensures no AI action creates a regulated record (RAID entry, JIRA ticket, external communication) without human authorisation — maintaining clear accountability
- **Audit requirements:** The full audit trail (AI proposal → confidence score → human decision → final action) supports internal and external audit requirements in regulated environments
- **Access controls:** Role-based access and OAuth 2.0 authentication ensure only authorised users can approve actions with governance implications
- **Change control:** All changes to confidence thresholds, autonomy levels, and governance rules require PMO Lead approval before deployment — preventing unauthorised expansion of AI autonomy

> ⚠️ **TEAM INPUT NEEDED:** Specific regulatory frameworks applicable to target clients (FCA, PRA, MiFID II, etc.) should be referenced where relevant. Data residency commitments for each jurisdiction should be confirmed.

---

## Summary of Team Input Required

| Q# | Item | Priority |
|---|---|---|
| Q7 | University/college collaboration | High — increases approval likelihood |
| Q9 | NI job creation/retention headcount | High — core Invest NI criterion |
| Q10 | NI delivery location(s) | High — core Invest NI criterion |
| Q12–13 | Team members, titles, hours | High — required field |
| Q17 | Named client decision-makers | Medium |
| Q18 / Q26 | Pricing and subscription model | Medium |
| Q20 | Go-to-market and sales approach | Medium |
| Q22 | Upfront investment estimate | Medium |
| Q27 / Q28 | Cloud platform, deployment model | Medium |
| Q29 | Support model and SLAs | Low |
| Q24 (add) | Data residency and certifications | Medium — financial services context |

---

*Version: v0.1 draft | Based on: pmo-ai-tool-deliverables.md, pmo-ai-workflows-explained.md, pmo-ai-differentiation.md, pmo-ai-business-requirements-v1.md*
