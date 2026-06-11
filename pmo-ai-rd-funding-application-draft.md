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

The platform directly improves the following PMO processes, each validated through surveys and interviews with PMOs at financial services clients and confirmed through review of real PMO role specifications from AIB:

**Meeting follow-up (currently: 20–30 min per meeting / ~80 meetings/month)**
AI agents extract and classify RAID items, propose JIRA updates, and draft follow-up emails. Follow-up time reduces from ~30 minutes to under 5 minutes. All outputs require PMO approval before any system is updated.

**Status reporting (currently: ~45 min per report / ~50 reports/month)**
AI agents pull data from JIRA, SharePoint, and MS Project; reconcile inconsistencies; monitor milestone health proactively; analyse budget variance; and generate audience-adapted narratives for executives, steering groups, and project teams — from a single data source.

**Governance monitoring (currently: inconsistent, audit-driven, often too late)**
AI agents continuously check every project against defined governance standards — documentation, approvals, and gate criteria — generating per-project scorecards and flagging gaps before they become audit findings or escalations.

**Stakeholder communications (currently: written from scratch, under pressure, inconsistently)**
AI agents detect trigger events (RAG changes, milestone slips, risk escalations) and draft tailored communications for the appropriate audience — escalation notices, steering committee briefings, milestone announcements, and steering committee packs — drawing on live project context from meeting intelligence and status reports.

**Change request management (currently: impact assessed manually by cross-referencing plan, RAID, and financials)**
AI agents assemble impact assessments automatically from live project data when a change request is received; draft the assessment covering schedule, cost, and risk; route it to the correct approver; and track it through to closure. Change Control appears in 100% of real PMO role specifications reviewed — it is a core daily task, not an occasional one.

---

### Q5. Development of leading edge technology ✅

The platform applies the following leading-edge technologies in a novel combination:

- **Large Language Models (LLMs)** — applied to domain-specific PMO classification tasks (RAID taxonomy, commitment extraction, risk signal synthesis) rather than general-purpose generation
- **Multi-agent orchestration** — a central orchestrator routes inputs to specialist sub-agents (Meeting Intelligence, Report Generation, Governance Monitoring, Stakeholder Communications), each with defined scope, confidence thresholds, and escalation rules
- **Governed agentic AI** — a novel architectural pattern in which AI autonomy levels are explicitly defined and enforced (from fully agentic to human-only) at the workflow level, not as a post-hoc safety layer. This is particularly relevant in regulated financial services environments where AI governance is a compliance requirement
- **Cross-source signal synthesis** — combining structured data (JIRA, MS Project, SharePoint) with unstructured data (meeting transcripts, emails) to identify emerging risks before they are raised by humans
- **Microsoft Graph API + JIRA REST API integration** — enabling real-time, bidirectional data flows between AI outputs and enterprise project management systems

---

### Q6. Digital Process Innovation ✅

The project represents end-to-end digital process innovation across five core PMO workflows:

- **Meeting-to-governance pipeline:** Transforms an entirely manual, error-prone process (listening → noting → classifying → logging → updating) into an automated, governed digital workflow triggered by a meeting transcript
- **Automated multi-audience reporting:** Eliminates manual data extraction and report formatting; continuous milestone health monitoring runs between reporting cycles; a single data pull generates multiple audience-adapted outputs automatically
- **Continuous governance assurance:** Replaces periodic, inconsistent manual governance reviews with automated, standards-based checking across the full project portfolio every week
- **Event-driven stakeholder communications:** Replaces reactive, from-scratch drafting with AI-triggered communications that draw on live project context — drafted automatically when a RAG changes, a milestone slips, or a risk escalates; includes steering committee pack generation
- **Change request management pipeline:** Replaces manual cross-referencing of plan, RAID, and financial data with an automated impact assessment workflow — triggered when a change request is received, assembled from live project data, and routed through a governed approval process

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

| Workstream | Wave | Estimated Annual Saving |
|---|---|---|
| Meeting Intelligence | 1 | ~$18,000 |
| Status Reports | 2 | ~$26,250 |
| Governance Monitoring | 2 | Qualitative (one avoided audit finding or governance failure = significant rework and reputational cost) |
| Stakeholder Communications | 2 | ~$4,500 (est. — drafting time eliminated across escalations, milestone notices) |
| Change Request Management | 2 | ~$6,000 (est. — impact assessment drafting and approval routing across ~10 CRs/month) |
| **Total (quantifiable, Wave 1–2)** | | **~$54,750 per PMO** |
| Personal Task Management *(Wave 3)* | 3 | ~$8,250 |
| Strategic Resourcing *(Wave 3)* | 3 | Qualitative (one avoided wrong placement = weeks of rework) |
| Benefits Tracking *(Wave 3)* | 3 | Qualitative (benefits realisation visibility prevents undetected programme underdelivery) |

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

> *"We give your PMOs back the time they spend on things that shouldn't need them — meeting follow-up, status reporting, governance checking, and stakeholder communications — so they can focus on the decisions and relationships that only a PMO can handle."*

Specific value delivered:

- **No more lost RAID items:** Every meeting produces a structured RAID proposal within 30 minutes of the transcript being ready, logged after PMO approval
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

The platform is an **EPAM-built, cloud-hosted web application** — not a Microsoft Teams extension or Copilot plugin. It integrates with clients' existing tools (Teams, SharePoint, JIRA, Outlook) as data sources, but the platform itself is designed, built, owned, and hosted by EPAM. Clients access it via browser.

Delivery follows a phased wave approach:

| Wave | Capabilities | Rationale |
|---|---|---|
| Wave 1 | Meeting Intelligence | Highest value; builds the data and integration foundation (Teams/Zoom, JIRA, SharePoint) |
| Wave 2 | Status Reports + Governance Monitoring + Stakeholder Communications + Change Request Management | Leverage Wave 1 outputs; all four confirmed as core daily PMO tasks in 100% of real role specifications reviewed; change request impact assessment draws on live RAID and plan data Wave 1 generates |
| Wave 3 | Personal Task Management + Strategic Resourcing + Proactive Risk Monitoring + Benefits Tracking | Require mature data foundations and richer AI context from Waves 1–2 |
| Wave 4 | Lessons Learned + Dependency Tracking + Project Mobilisation / PID | Require mature data across the full portfolio |

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

The PMO AI Platform is an **EPAM-built, standalone web application** — the only AI product built specifically for financial services PMO governance workflows. This is a deliberate architectural choice: the platform integrates with Microsoft and Atlassian tools as data sources but is independent of their product roadmaps. It cannot be replicated by a Copilot update or a Teams plugin.

Unlike generic AI tools (Copilot, ChatGPT) which produce text output, this platform produces governed outcomes:

- **EPAM product, not a Microsoft extension:** A standalone platform with EPAM's branding, roadmap, and IP — not dependent on Microsoft's feature decisions
- **PMO-specific taxonomy:** Classifies content using formal RAID methodology, not generic action items
- **System write-back:** Proposes structured entries directly into RAID logs and JIRA, in the correct schema
- **Enforced approval workflow:** Nothing reaches a system of record without explicit human sign-off
- **Full audit trail:** Every AI proposal and human decision is logged — essential for regulated environments
- **Cross-source intelligence:** Synthesises meeting transcripts, project data, and email into a single coherent view
- **Consistent governance:** Applies the same standards across every project, not dependent on who reviews it
- **Multi-client SaaS:** A single platform serves multiple financial services clients with per-client configuration and data isolation

Validated by PMOs on client sites who confirmed that current tools are *"not sufficiently tailored to PMO needs"* and produce outputs that are *"not always accurate."*

---

### Q22. Upfront investment required ❌

> **TEAM INPUT REQUIRED**
> Please provide estimates for: development resource costs, infrastructure/cloud costs, tooling/API costs, and sales/marketing investment required to be credible in the market.

---

### Q23. Scalability ✅

The platform is designed for scalability from the outset as a multi-tenant SaaS product:

- **Cloud-native architecture:** Deployed on Microsoft Azure using containerised microservices (Docker / Kubernetes), enabling horizontal scaling per workload. Individual agent components scale independently — a client with high meeting volume scales the Meeting Intelligence agent without affecting others.
- **Multi-tenant design with per-client isolation:** A single platform deployment serves multiple financial services clients. Each client's data (transcripts, RAID logs, project data) is isolated at the database and storage layer — no cross-client data exposure.
- **Stateless agent processing:** AI agents process inputs and produce outputs without persistent state, enabling parallel processing and elastic scaling during peak periods (e.g. end-of-week reporting cycles).
- **Configuration over code:** All client-specific settings (RAG thresholds, RAID schemas, JIRA field mappings, confidence thresholds, approval workflows) are stored as configuration, not hardcoded. Onboarding a new client requires configuration, not re-development.
- **API-first integrations:** All connections to Microsoft Graph, JIRA REST API, and Zoom use standard REST APIs. Adding a new client's tool instance requires new OAuth credentials and configuration — no new code.
- **Performance targets:** The platform is designed to support concurrent processing across a portfolio of 10+ financial services clients, with meeting processing completing within 30 minutes of transcript availability.

---

### Q24. Security ✅

Security is built into the platform architecture at multiple levels:

- **Authentication:** All integrations use OAuth 2.0 via Azure Active Directory — no passwords stored, access revocable
- **Human-in-the-loop enforcement:** No AI action writes to an external system or sends a communication without explicit PMO approval — reducing the attack surface of automated actions
- **PII handling:** Meeting transcripts may contain personal information. The platform detects and masks PII in all debug, trace, and audit logs
- **Audit trail:** Every AI proposal and human decision is logged with timestamp, user ID, and confidence score — providing a complete chain of evidence for compliance review
- **Data minimisation:** The platform processes data in transit; meeting transcripts are not stored longer than required for the processing workflow
- **Role-based access:** Approval workflows are role-gated — only authorised PMO users can approve RAID entries, JIRA updates, or outbound communications
- **EPAM-managed infrastructure:** The platform is hosted and managed by EPAM on Azure. EPAM is responsible for infrastructure security, patching, and monitoring — clients do not manage the platform environment
- **Data isolation:** Each client's data is stored in isolated Azure resources. No client data is accessible to other clients or used to train shared models

> ⚠️ **TEAM INPUT NEEDED:** Specific data residency requirements per jurisdiction (FCA, PRA, GDPR), penetration testing schedule, and ISO 27001 / SOC 2 certification roadmap should be confirmed with EPAM's security team.

---

### Q25. User experience and user journeys ⚠️

The PMO AI Platform is a **browser-based web application built by EPAM**, accessible on desktop and mobile. PMOs log in via their organisation's Azure AD credentials (SSO). The platform does not require installation — it is accessed like any web application.

Notifications (new items to review, overdue tasks, resource alerts) are delivered to the user via Microsoft Teams messages and/or Outlook, directing them into the EPAM platform to take action.

**The platform has six core screens:**

1. **Home Dashboard** — Single view of pending review items, today's tasks, governance alerts, change requests pending assessment, and reports due. Everything requiring PMO action is surfaced here.

2. **Meeting Review Queue** — Presents AI-proposed RAID items, JIRA updates, and follow-up email drafts from processed meetings. Each item shows the source quote from the transcript, confidence score, and proposed classification. PMO approves, modifies, or rejects each item individually.

3. **Governance & Change Request Dashboard** — Per-project governance scorecards showing compliance status, open gaps, and pending change requests. Each change request shows the AI-drafted impact assessment (schedule, cost, risk) for PMO review and approval routing.

4. **Report Review & Approval** — Draft status reports presented per audience version (Executive, Steering, Team). PMO edits narrative and approves each version before automated distribution. Includes milestone health alerts surfaced between reporting cycles.

5. **Daily Task Checklist** *(Wave 3)* — Consolidated task list drawn from email commitments, meeting action items, and JIRA. Ranked by priority. Tick-off interface with completion detection.

6. **Resource Alert Interface** *(Wave 3)* — Gap alerts with lead time, role required, and ranked match recommendations with trade-off explanations. PMO confirms resource assignment.

**Primary user journeys:**

- **Post-meeting review:** Meeting ends → transcript ingested → notifications sent via Teams → PMO opens platform in browser → reviews and approves RAID items and follow-up email → approved items written to SharePoint and JIRA.
- **Daily task management:** PMO opens platform → views consolidated prioritised task list → works through items → completions auto-detected where possible.
- **Report approval:** Report cycle triggers → PMO receives Teams notification → opens platform → reviews AI-drafted report → approves → platform distributes automatically via Outlook.
- **Resource gap response:** PMO receives Teams alert → opens platform → reviews gap and match recommendations → confirms assignment → platform updates resource tracker.

> ⚠️ **TEAM INPUT NEEDED:** Wireframes or UX mockups should be developed to support this section for the full application. EPAM's design team should own this.

---

### Q26. Subscription model ❌

> **TEAM INPUT REQUIRED**
> See Q18. Pricing and commercial model not yet defined. This section cannot be drafted without that input.

---

### Q27. Infrastructure and technology stack ✅

The platform is a cloud-hosted web application designed, built, and maintained by EPAM.

| Layer | Technology | Notes |
|---|---|---|
| **Frontend** | React (TypeScript) | EPAM-built browser-based web application; responsive for desktop and mobile; EPAM-branded |
| **Backend API** | Python (FastAPI) | RESTful API layer; handles business logic, workflow orchestration, and integration calls |
| **AI / LLM** | Anthropic Claude / OpenAI GPT-4 class via API | Model-agnostic design — not locked to a single provider; model can be swapped without re-architecture |
| **Agent orchestration** | LangGraph | Multi-agent framework managing specialist sub-agents (Meeting Intelligence, Report Generation, Resourcing, Task Management); each agent has defined scope, confidence thresholds, and escalation rules |
| **Cloud hosting** | Microsoft Azure | Preferred due to Microsoft 365 integration ecosystem (Graph API); all infrastructure EPAM-managed |
| **Containerisation** | Docker / Kubernetes (AKS) | Containerised microservices enable independent scaling per agent; Kubernetes manages orchestration |
| **Database** | Azure PostgreSQL | Structured data (RAID entries, task records, audit log); per-client schema isolation |
| **Document / file storage** | Azure Blob Storage | Transcript storage (processing window only); approved report versions; per-client containers |
| **Authentication** | OAuth 2.0 / Azure Active Directory | Client SSO — PMOs log in with their existing organisational credentials; no separate password |
| **Integrations (data sources)** | Microsoft Graph API, JIRA REST API, Zoom REST API | These are data integrations only — the platform reads from and writes to client systems; it does not run inside them |
| **Notifications** | Microsoft Graph API (Teams, Outlook) | Notifications delivered to users via their existing Teams and Outlook channels |
| **CI/CD** | Azure DevOps / GitHub Actions | Automated build, test, and deployment pipeline; EPAM-managed |
| **Monitoring** | Azure Monitor + Application Insights | Platform health, error tracking, performance metrics, and LLM usage monitoring |
| **Audit logging** | Append-only Azure Table Storage | Immutable record of every AI proposal, confidence score, and human decision |

---

### Q28. Deployment model ✅

The platform offers three deployment models to accommodate the varying data residency and security requirements of financial services clients:

| Model | Description | Best For |
|---|---|---|
| **Multi-tenant SaaS** (default) | Single EPAM-managed Azure deployment; all clients share infrastructure with data isolation at the application and database layer. EPAM manages all hosting, updates, and monitoring. | Clients with standard data residency requirements; lowest cost; fastest onboarding |
| **Single-tenant hosted** | Dedicated Azure infrastructure per client, EPAM-managed. Each client has their own isolated environment — no shared infrastructure. | Clients requiring physical data isolation (common in tier-1 financial services) |
| **Client-hosted** | Platform deployed within the client's own Azure tenant. EPAM provides the application; the client's IT team manages infrastructure. | Clients with strict data sovereignty requirements or internal security policies prohibiting third-party hosting |

**Default recommendation:** Multi-tenant SaaS for initial client engagements, with single-tenant as the standard option for tier-1 financial services clients (MUFG, Citi, etc.) who typically require dedicated infrastructure.

EPAM manages all platform updates, security patching, and monitoring across all deployment models except client-hosted.

---

### Q29. Customer support ⚠️

As an EPAM-built and EPAM-managed platform, customer support is delivered by EPAM:

| Tier | Scope | Channel |
|---|---|---|
| **L1 — User support** | Login issues, access queries, general usage questions | EPAM helpdesk (email / ticketing system) |
| **L2 — Application support** | Configuration changes, integration issues, accuracy concerns, workflow adjustments | EPAM delivery team with SLA response times |
| **L3 — Platform / engineering** | Bug fixes, infrastructure issues, security incidents | EPAM engineering team |

Platform availability target: 99.5% uptime (excluding scheduled maintenance windows).

> ⚠️ **TEAM INPUT NEEDED:** Specific SLA response times per tier, support hours (business hours vs 24/7), and escalation path for client-specific configuration issues need to be confirmed with EPAM's managed services team.

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
