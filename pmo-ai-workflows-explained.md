# PMO AI Tool — How the Workflows Work

A plain-English guide to what the AI does, why it works that way, and what value it delivers.

---

## Overview

Thirteen workstreams have been assessed and mapped across surveys, interviews, the Problem Statement, and real-world PMO job specifications from financial services clients (AIB). Five are selected for the initial focus — all five are grounded in direct evidence (stakeholder quotes and/or confirmed presence in 100% of PMO role specifications reviewed), all are deliverable without significant pre-conditions, and together they cover the full breadth of a PMO's week.

The **EPAM PMO AI Platform** is a browser-based web application built, hosted, and managed by EPAM. PMOs access it via any browser using their existing organisational credentials (Azure AD SSO). It is not a Microsoft Teams app, Copilot extension, or plugin — it is an independent EPAM product that integrates with Microsoft tools and JIRA as data sources.

The platform is built as an **orchestrated multi-agent system**: a central agent receives unstructured inputs (transcripts, status data, emails, project plans) and routes them to specialist sub-agents, each focused on a specific output. The PMO validates and approves outputs before anything is written to a system or sent externally. Notifications are delivered to the user via Teams or Outlook, directing them into the EPAM platform to take action.

| # | Work Stream | Score | Wave |
|---|---|---|---|
| 1 | **Meeting Intelligence** | 25 | ★ Wave 1 |
| 2 | **Status Reports & Scorecards** | 16 | ★ Wave 2 |
| 3 | **Governance Monitoring** | 20 | ★ Wave 2 |
| 4 | **Stakeholder Communications** | 16 | ★ Wave 2 |
| 5 | **Change Request Management** | 16 | ★ Wave 2 |
| 6 | Proactive Risk Monitoring | 20 | Wave 3 |
| 7 | Personal Task Management | 20 | Wave 3 |
| 8 | Strategic Resourcing | 12 | Wave 3 |
| 9 | Benefits Tracking | 12 | Wave 3 |
| 10 | Lessons Learned & Knowledge Capture | 15 | Wave 4 — high priority |
| 11 | Dependency Tracking | 12 | Wave 4 |
| 12 | Project Mobilisation / PID | — | Wave 4 |
| 13 | Onboarding Access | 6 | RPA — not AI-first |

> **One rule applies across all streams:** The AI proposes, humans approve. Nothing gets written to a system or sent externally without a PMO sign-off.

---

## Work Stream 1: Meeting Intelligence *(Score: 25 — Primary)*

*"No more lost action items. No more 'I thought we decided X.'"*

### The Problem

After a meeting, a PMO typically spends 20–30 minutes re-reading notes to find action items, guessing who owns what, deciding what is a Risk vs an Issue vs a Decision, manually updating JIRA and the RAID log, and writing a follow-up email. This happens ~80 times a month. Items get missed. Decisions get disputed.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Ingest transcript** | PMO uploads or pastes the transcript into the platform and selects the associated project. System identifies speakers and links to project context. Where Graph API has been provisioned by IT, retrieval is automatic — but manual upload is the default. | Upload transcript after the meeting — one action, under a minute |
| **Generate meeting notes** | Produces structured meeting notes covering key topics, discussion, and decisions — with all RAID items listed at the foot | Reviews and approves before distribution |
| **Extract RAID items** | Identifies Risks, Actions, Issues, and Decisions with confidence scores | Reviews flagged items; approves all entries |
| **Assign owners & dates** | Infers who owns each action and converts vague dates to specific ones | Confirms ambiguous cases |
| **Propose JIRA updates** | Matches actions to existing tickets; prepares comments, status changes, new tickets | Confirms before any update is applied |
| **Propose RAID log entries** | Formats items into RAID schema and queues for approval | Approves each entry — nothing is written without sign-off |
| **Distribute meeting notes** | Pre-populates the distribution list from the PMO-configured standing list for that meeting series. PMO confirms or edits the list, then sends via Outlook. | Confirms recipient list and sends — one action; AI never sends independently |

**Why it is primary:** Highest score, fully standalone, and it acts as the foundation — the actions, decisions, and RAID items it captures feed directly into Status Reports, Personal Task Management, Strategic Resourcing, and Governance Monitoring.

**What stakeholders said:** *"Raw meeting notes," "action items," "RAID logs"* — directly quoted. PMO survey respondents confirmed they currently use Copilot for meeting minutes but find it *"not always accurate"* and output is *"not sufficiently tailored to PMO needs."*

**Value:** Meeting notes drafted automatically — narrative summary, decisions, and action list in one document, sent to all invitees. What previously took 20–30 minutes of writing takes under 5 minutes to review and approve. RAID items captured consistently. Decisions documented. Estimated annual saving: ~$18,000.

---

## Work Stream 2: Status Reports & Scorecards *(Score: 16)*

*"Stop spending a day a week pulling numbers and writing the same report."*

### The Problem

PMOs spend significant time each week collecting data from JIRA, SharePoint, and MS Project, calculating RAG scores, writing the narrative that explains what the numbers mean, and producing multiple versions of the same report for different audiences. Survey respondents specifically highlighted financial data analysis as an unmet need: *"AI tooling to analyse complex and large financial data would provide valuable insights."*

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Data collection** | Pulls metrics automatically from JIRA, SharePoint, MS Project via API | Nothing — fully automated |
| **Milestone health monitoring** | Checks all active milestones against plan; flags any at risk of slipping *before* the next reporting cycle — not just at report time | Reviews flagged milestones; confirms owner and action |
| **Financial analysis** | Analyses budget vs actuals, spend trends, and variance; flags projects with deteriorating financial health | Reviews analysis |
| **RAG calculation** | Applies the formula to produce Red/Amber/Green scores | Reviews the output |
| **Reconciliation** | Flags inconsistencies across data sources | Resolves conflicts |
| **Narrative writing** | Drafts the "so what" story behind the numbers, informed by meeting intelligence outputs | Reviews and refines |
| **Audience-adapted output** | Generates separate versions for executives, steering groups, and project teams from one data source | Approves before sharing |
| **Distribution** | Sends the report to the right people | Nothing — fully automated once approved |

**Why financial analysis is included:** Multiple survey respondents called this out explicitly and it is listed as a core pain in the Problem Statement. Budget variance and financial health are part of every status report — treating them as a distinct AI-assisted step makes the output more valuable than a RAG dashboard alone.

**Why narrative writing needs AI not just Power BI:** Writing the narrative requires understanding what the numbers *mean* in context — which projects matter most to leadership right now, and why something is red. Power BI shows the numbers; the AI explains them.

**What stakeholders said:** *"Automate reports, automate scorecards."* Problem Statement: *"Multiple versions of the same report are created manually for executives, stakeholders and project teams."*

**Value:** A report taking 45 minutes takes 10. Estimated annual saving: ~$26,250.

---

## Work Stream 3: Governance Monitoring *(Score: 20)*

*"Every project checked against the same standard, automatically, every week."*

### The Problem

Governance standards are applied unevenly across projects and teams. Quality depends on who conducts the review and when. Projects can progress with documentation gaps, missing approvals, and overdue governance gates — and nobody notices until an audit, an escalation, or a steering committee meeting that goes badly.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Standards check** | Continuously checks each project against defined governance criteria — documentation in place, approvals obtained, gates passed | Reviews the scorecard |
| **Gap detection** | Identifies missing documents, overdue reviews, and unresolved change requests | Prioritises which gaps to act on |
| **Scorecard generation** | Produces a per-project governance scorecard showing compliant, amber, and failing items | Reviews and shares with sponsors where needed |
| **Escalation drafting** | Drafts an escalation notice for any gap classified as high severity | Reviews and sends — AI never sends independently |
| **Trend monitoring** | Tracks governance health across the portfolio over time; flags deteriorating projects | Reviews portfolio view |

**Why it works in Wave 2:** Governance checks are most valuable when they have structured data to check against — RAID logs, decision records, meeting summaries. Wave 1 (Meeting Intelligence) generates exactly this data. Running Governance Monitoring after Wave 1 means checks are based on real, current project data rather than manually maintained spreadsheets.

**What stakeholders said:** *"Inconsistent governance"* is listed as a core problem in the Problem Statement, which explicitly proposes a Governance Agent: *"Continuously assesses projects against governance standards, checking documentation, approvals and criteria. Provides consistent oversight via scorecards and actionable remediation, replacing inconsistent manual audits."*

**Value:** Every project assessed against the same standard, every week, without depending on who happens to be reviewing it. Governance gaps surface before they become audit findings or steering committee failures.

---

## Work Stream 4: Stakeholder Communications *(Score: 16)*

*"The right message to the right person, drafted and ready — without writing from scratch."*

### The Problem

Drafting escalation notices, steering committee packs, milestone announcements, and executive briefings takes significant PMO time and is inconsistent in quality. When a project moves to Red RAG, someone needs to notify the programme director — usually urgently, usually while managing everything else the RAG change has triggered. Stakeholder communications get rushed, delayed, or skipped entirely.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Trigger detection** | Monitors for events that typically require a stakeholder communication — RAG change, milestone slip, risk escalation, decision reversal | Reviews triggered drafts |
| **Context gathering** | Pulls the relevant project context — what changed, when, who owns the response, what is being done about it | Confirms the context is accurate |
| **Draft generation** | Writes a tailored communication appropriate to the audience — escalation notice for sponsor, briefing for programme director, summary for project team | Reviews, edits if needed, approves |
| **Audience adaptation** | Adjusts tone and detail level for different recipients from the same underlying information | Confirms the right version reaches the right person |
| **Distribution** | Sends via Outlook on PMO approval | Nothing — fully automated once approved |

**Why it works in Wave 2:** Stakeholder communications draw on project context — meeting decisions, open risks, current RAG status — that Wave 1 (Meeting Intelligence) and Wave 2 Status Reports generate. Without that context, drafts would be generic. With it, they are accurate and specific enough to send with minimal editing.

**What stakeholders said:** Multiple respondents wrote: *"A key aspect of the PMO role is stakeholder management."* The Problem Statement includes a dedicated Comms Drafting Agent. The challenge is not writing well — it is writing quickly, accurately, and from the right information when under pressure.

**Value:** No more starting from scratch on escalation notices at the wrong moment. Consistent, accurate communications drafted automatically when triggered. The PMO reviews and approves — they never write the first draft.

---

## Work Stream 5: Change Request Management *(Score: 16)*

*"Impact assessed, routed for approval — without the PMO having to start from scratch."*

### The Problem

When a change request comes in, a PMO must cross-reference the project plan, RAID log, open actions, and financial position to understand the impact before it can be assessed. This takes time and requires the PMO to hold a lot of context simultaneously. Change Control appears in every PMO role specification reviewed — it is a core, ongoing task that occurs throughout a project's lifecycle, not an occasional activity.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Trigger detection** | Identifies a new change request submitted via JIRA, SharePoint, or a meeting decision | Reviews the flagged request |
| **Impact assessment draft** | Cross-references the project plan, RAID log, open actions, and financial data to draft an impact assessment covering schedule, cost, and risk | Reviews, refines, and confirms the assessment |
| **Routing** | Identifies the correct approver based on change type and scale; prepares the approval package | Confirms routing and approver before submission |
| **Status tracking** | Monitors the change through the approval process; flags overdue approvals for PMO follow-up | Reviews status; chases approvals as needed |
| **RAID update proposal** | Proposes new or updated RAID entries if the change introduces risks or issues | Approves before any RAID update is written |
| **Closure notification** | Drafts a notification to relevant stakeholders when a change is approved or rejected | Reviews and sends via Stakeholder Communications workflow |

**Why it is in Wave 2:** Change Control was originally deferred to Wave 3 on the basis of no direct stakeholder quote. Review of real PMO role specifications across six AIB programmes confirmed it appears in 100% of roles — tied with RAID management and Status Reporting as the most universal PMO task. It also scored 16 (identical to Status Reports and Stakeholder Communications). The original deferral rationale no longer holds.

**What the evidence shows:** Change Control/Maintenance/Management is listed as a required task in every PMO demand form reviewed — across regulatory programmes (IRB, AML, SEPA), operational programmes (ESASS), and transformation programmes (CLMP). It is a daily task, not an occasional one.

**Value:** Impact assessments that currently take 30–60 minutes of cross-referencing are drafted in under 5 minutes. Change requests are tracked consistently, approvals are chased automatically, and the RAID log stays current. Governance of changes is documented end-to-end.

---

## Work Streams Deferred to Later Waves

These were assessed and validated but require the data foundations that earlier waves build, or have pre-conditions not in place on day one.

---

### Personal Task Management *(Score: 20 — Wave 3)*

**The problem:** A PMO's commitments are scattered across emails, meeting action items, JIRA tickets, and Teams messages. Without a consolidated view, things get missed. Estimated cost: up to 2 hours a day in inbox scanning, mental context-switching, and chasing overdue items.

**What AI would do:** Extract commitments from email, combine with meeting actions and JIRA tasks into one prioritised daily list, detect completions automatically, and send reminders via Teams or Outlook.

**Why deferred:** The most complex step — extracting hard commitments from natural language email — requires distinguishing *"I'll send it Friday"* from *"I'll try"* and *"can you check?"* from *"FYI."* The completion detection feature also needs careful design to avoid silently dropping commitments. Deferred to Wave 3 once the governance and meeting data pipelines are mature and the AI's understanding of project context is richer.

---

### Strategic Resourcing *(Score: 12 — Wave 3)*

**The problem:** PMOs often find out a resource is finishing a project too late to find a suitable replacement. Matching the right person requires knowing availability, skills, project priority, and context — information that currently lives in different spreadsheets, SharePoint lists, and people's heads. Resource Maintenance/Management appears in 83% of PMO role specifications reviewed and covers two distinct activities that should be treated separately:

**Component A — Routine Resource Admin** (onboarding, offboarding, system access tracking, contract management): Administrative, repetitive, and largely rules-based. Closely related to the Onboarding Access workstream (RPA/Hybrid). Can be automated earlier than Component B.

**Component B — Strategic Resourcing** (skills matching, forward gap analysis, availability planning): The original Wave 3 design. Depends on structured data quality from earlier waves.

**What AI would do (Component B):** Monitor project end dates, flag gaps 4–6 weeks out, and recommend the best-fit resource with a trade-off explanation. Resource commitments always remain human-only.

**Why deferred:** The matching recommendations depend entirely on a clean, current skills inventory and resource availability data — a data quality pre-condition that is not reliably in place on day one. Most valuable in Wave 3 once structured project data from earlier waves improves the underlying information quality.

---

### Benefits Tracking *(Score: 12 — Wave 3)*

**The problem:** Benefits Maintenance/Management appears in 83% of PMO role specifications reviewed but is not addressed by any existing workstream. Benefits realisation is a recurring PMO task — tracking whether planned benefits are being achieved, reporting deviations to governance forums, and keeping the benefits register current throughout the project lifecycle.

**What AI would do:** Monitor the benefits register against the baseline defined in the PID/business case; flag deviations between planned and realised benefits; generate benefits realisation reports for steering committees as part of the status reporting cycle; draft escalations when benefits are at risk.

**Why deferred:** Benefits data depends on structured project records from earlier waves (RAID logs for risks to benefit delivery, status reports for progress tracking) and requires the benefits baseline to be clearly defined at project initiation. Wave 3 once data quality from earlier waves is established.

---

### Proactive Risk Monitoring *(Score: 20 — Wave 3)*

**The concept:** Continuously scan project data — milestone slippage, budget trends, overdue actions, resource changes — and surface emerging risks before they are raised in a meeting.

**Why deferred:** Value depends entirely on project data being clean and current. In many organisations this is not the case on day one. Wave 3 once data hygiene and integration are established through earlier waves.

---


### Lessons Learned & Knowledge Capture *(Score: 15 — Wave 4, High Priority)*

**The problem:** When PMs leave or rotate, institutional knowledge about risks, decisions, and context disappears with them. Lessons from completed projects are rarely captured in a usable form and almost never surfaced on new projects.

**What the Problem Statement says:** *"Knowledge Loss"* is explicitly listed as a core problem: *"When PMs leave or rotate, institutional knowledge about risks, decisions, and context often disappears with them. AI systems could prevent this."*

**What AI would do:** Synthesise retrospectives and project histories into searchable knowledge. Identify patterns across projects. Proactively surface relevant past experience when a new similar project starts.

**Why deferred:** Meaningful pattern recognition requires a body of structured project data. This accumulates as Waves 1–3 operate. **This is a high-priority Wave 4 item** — explicitly named as a core problem in the Problem Statement, not a nice-to-have.

---

### Dependency Tracking *(Score: 12 — Wave 4)*

**The concept:** Monitor cross-project dependencies and flag when a delay in one project is likely to impact another before the PMO realises it.

**Why deferred:** Requires a mature, connected data model across projects. Most effective once earlier waves are generating reliable structured data.

---

### Project Mobilisation / PID *(Wave 4)*

**The problem:** PID (Project Initiation Document) preparation appears in 67% of PMO role specifications reviewed. Project Drive/SharePoint organisation (setting up document structures, folder hierarchies, and governance templates at project start) appears in 100%. Neither is currently addressed by any workstream. Getting a new project set up correctly from day one — with the right governance framework, document structure, and communication templates in place — is time-consuming, inconsistent, and often done differently by each PMO.

**What AI would do:** Generate a draft PID using project context provided at initiation; create a standard SharePoint project folder structure from a configured template; pre-populate governance document templates; set up the RAID log schema and initial communication templates for the project. The PMO reviews and approves all outputs before use.

**Why deferred:** Project mobilisation is a one-off activity per project rather than a recurring workflow, and meaningful draft quality depends on having established templates and governance standards from earlier waves. Suited to Wave 4 alongside Lessons Learned.

---

### Onboarding Access *(Score: 6 — RPA/Hybrid)*

**The concept:** Check that new joiners have been set up with access to all required tools and systems.

**Why not AI:** The core work is rule-based — a checklist pass/fail check. Existing automation tooling (e.g. Power Automate) handles this reliably. The only AI-relevant piece is handling exceptions, which is a small slice. Revisit in Wave 4.

---

## Summary: What Changes for a PMO

| Today | With the AI Tool |
|---|---|
| 30 min writing up meeting notes | PMO uploads transcript; draft ready within minutes |
| RAID items lost or forgotten | Processed within 30 min of transcript; in the log after PMO approval |
| JIRA updated manually (or not at all) | Updates proposed automatically after each meeting |
| Milestone slippage spotted at report time, not before | Milestone health checked continuously; at-risk milestones flagged before the reporting cycle |
| Status reports take 45 min each, multiple manual versions | One data pull; AI generates audience-adapted versions in 10 min |
| Financial analysis done separately in Excel | Variance analysis and budget health built into every report |
| Governance gaps found too late — in audits or escalations | Every project checked against governance standards every week |
| Change impact assessed manually by cross-referencing plan, RAID, and financials | Impact assessment drafted automatically from live project data; routed for approval (Wave 2) |
| Steering committee packs written from scratch each cycle | Draft generated from current project data, ready to review and send (Wave 2) |
| Escalation emails written from scratch under pressure | Triggered automatically on RAG change or risk escalation; draft ready to review |
| Benefits realisation tracked in a spreadsheet, updated manually | Benefits register monitored continuously; deviations flagged automatically (Wave 3) |
| Commitments missed across email and meetings | One consolidated daily task list (Wave 3) |
| Resource gaps spotted too late | Flagged weeks in advance with a match recommendation ready (Wave 3) |
| New project setup inconsistent; PID and folder structure done differently each time | Standard PID and project folder structure generated from templates at initiation (Wave 4) |
| Institutional knowledge lost when PMs leave | Captured, structured, and surfaced automatically (Wave 4) |

**The AI handles the repetitive and analytical work. The PMO retains control over everything that matters.**

---

*Document version: v5.0 | Updated: 2026-06-11 — Change Request Management elevated to Wave 2; Benefits Tracking and Project Mobilisation / PID added; Plan/Milestone Monitoring added to Status Reports; Strategic Resourcing split clarified. Changes driven by review of 6 real PMO role specifications (AIB). | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-differentiation.md*
