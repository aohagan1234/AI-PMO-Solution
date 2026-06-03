# PMO AI Tool — How the Workflows Work

A plain-English guide to what the AI does, why it works that way, and what value it delivers.

---

## Overview

Eleven workstreams were assessed across surveys, interviews, and the Problem Statement. Four are selected for the initial focus — all four are grounded in direct stakeholder quotes, all four are deliverable without significant pre-conditions, and together they cover the full breadth of a PMO's week.

The tool is built as an **orchestrated multi-agent system**: a central agent receives unstructured inputs (transcripts, status data, emails, project plans) and routes them to specialist sub-agents, each focused on a specific output. The PMO validates and approves outputs before anything is written to a system or sent externally.

| # | Work Stream | Score | Wave |
|---|---|---|---|
| 1 | **Meeting Intelligence** | 25 | ★ Wave 1 |
| 2 | **Status Reports & Scorecards** | 16 | ★ Wave 2 |
| 3 | **Personal Task Management** | 20 | ★ Wave 2 |
| 4 | **Strategic Resourcing** | 12 | ★ Wave 2 |
| 5 | Proactive Risk Monitoring | 20 | Wave 3 |
| 6 | Governance Monitoring | 20 | Wave 3 — high priority |
| 7 | Change Request Management | 16 | Wave 3 |
| 8 | Stakeholder Communications | 16 | Wave 3 — high priority |
| 9 | Lessons Learned & Knowledge Capture | 15 | Wave 4 — high priority |
| 10 | Dependency Tracking | 12 | Wave 4 |
| 11 | Onboarding Access | 6 | RPA — not AI-first |

> **One rule applies across all streams:** The AI proposes, humans approve. Nothing gets written to a system or sent externally without a PMO sign-off.

---

## Work Stream 1: Meeting Intelligence *(Score: 25 — Primary)*

*"No more lost action items. No more 'I thought we decided X.'"*

### The Problem

After a meeting, a PMO typically spends 20–30 minutes re-reading notes to find action items, guessing who owns what, deciding what is a Risk vs an Issue vs a Decision, manually updating JIRA and the RAID log, and writing a follow-up email. This happens ~80 times a month. Items get missed. Decisions get disputed.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Ingest transcript** | Reads the Teams/Zoom transcript, identifies speakers, links to project | Nothing — picked up automatically |
| **Generate summary** | Produces a structured summary of topics, discussion, and next steps | Reviews and approves before sharing |
| **Extract RAID items** | Identifies Risks, Actions, Issues, and Decisions with confidence scores | Reviews flagged items; approves all entries |
| **Assign owners & dates** | Infers who owns each action and converts vague dates to specific ones | Confirms ambiguous cases |
| **Propose JIRA updates** | Matches actions to existing tickets; prepares comments, status changes, new tickets | Confirms before any update is applied |
| **Propose RAID log entries** | Formats items into RAID schema and queues for approval | Approves each entry — nothing is written without sign-off |
| **Draft follow-up email** | Writes the follow-up with RAID items, owners, dates, and decisions | Reviews and sends — AI never sends independently |

**Why it is primary:** Highest score, fully standalone, and it acts as the foundation — the actions, decisions, and RAID items it captures feed directly into Status Reports, Personal Task Management, Strategic Resourcing, and Governance Monitoring.

**What stakeholders said:** *"Raw meeting notes," "action items," "RAID logs"* — directly quoted. PMO survey respondents confirmed they currently use Copilot for meeting minutes but find it *"not always accurate"* and output is *"not sufficiently tailored to PMO needs."*

**Value:** Follow-up time from ~30 minutes to under 5. RAID items captured consistently. Decisions documented. Estimated annual saving: ~$18,000.

---

## Work Stream 2: Status Reports & Scorecards *(Score: 16)*

*"Stop spending a day a week pulling numbers and writing the same report."*

### The Problem

PMOs spend significant time each week collecting data from JIRA, SharePoint, and MS Project, calculating RAG scores, writing the narrative that explains what the numbers mean, and producing multiple versions of the same report for different audiences. Survey respondents specifically highlighted financial data analysis as an unmet need: *"AI tooling to analyse complex and large financial data would provide valuable insights."*

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Data collection** | Pulls metrics automatically from JIRA, SharePoint, MS Project via API | Nothing — fully automated |
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

## Work Stream 3: Personal Task Management *(Score: 20)*

*"One place for everything you have committed to doing."*

### The Problem

A PMO's commitments are scattered across emails, meeting action items, JIRA tickets, and Teams messages. Without a consolidated view, things get missed. Estimated cost: up to 2 hours a day in inbox scanning, mental context-switching, and chasing overdue items.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Email scanning** | Reads the last 3 days of emails; extracts commitments made or received | Reviews the list |
| **Cross-source consolidation** | Combines tasks from email, meetings (Stream 1 output), and JIRA into one list; removes duplicates | Spot-checks |
| **Prioritisation** | Ranks by urgency, requester importance, and project priority; surfaces overdue items | Adjusts if needed |
| **Completion detection** | Monitors sent folder and JIRA changes to auto-tick completed tasks | Confirms if uncertain |
| **Reminder generation** | Sends reminders at the right time via the preferred channel | Nothing |
| **Checklist interface** | Presents a clean daily task list with tick-off | Works through the list |

**Why it requires AI and not just a to-do list:** The hard part is extracting commitments from email. The AI must distinguish a hard commitment (*"I will send it Friday"*) from a soft one (*"I'll try"*) and a request (*"can you check?"*) from information (*"FYI the meeting moved"*). That reading comprehension is where AI adds the value.

**What stakeholders said:** *"Read emails, checklist, tick off."* Survey respondents also noted Copilot is useful for emails but *"would be good if it came up as a prompt when writing emails"* — indicating current tools are not integrated into the workflow.

**Value:** Nothing slips through. One consolidated daily list replaces inbox scanning, note re-reading, and JIRA checking. Estimated annual saving: ~$8,250.

---

## Work Stream 4: Strategic Resourcing *(Score: 12)*

*"Know about resource gaps before they become a crisis."*

### The Problem

PMOs often find out a resource is finishing a project too late to find a suitable replacement. Matching the right person to a new role requires knowing availability, skills, project priority, and context — information that currently lives in different spreadsheets, SharePoint lists, and people's heads.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Resource tracking** | Monitors project end dates and flags resources finishing in the next 4–6 weeks | Reviews alerts |
| **Skills inventory** | Maintains an up-to-date view of skills, experience, and availability across the pool | Validates accuracy |
| **Gap detection** | Identifies upcoming resourcing gaps before they happen | Prioritises which gaps to act on |
| **Match recommendation** | Suggests the best-fit resource(s) with a trade-off explanation (availability vs skill fit vs project priority) | Makes the final decision |
| **Resource commitment** | N/A — humans only | Confirms the assignment |

**Why the matching step needs AI:** Identifying who is available is a simple query. Recommending *who to assign* requires weighing competing factors simultaneously — availability, skill fit, project priority, and seniority requirements. That trade-off reasoning is where AI adds genuine value over a spreadsheet lookup.

**Why resource commitments are always human-only:** Moving someone to a new project has HR, contractual, and relationship implications. The AI informs the decision — it never makes it.

**What stakeholders said:** *"Resources finishing up, match it up, skills pool."* Interview: *"Share resource calendar, capacity utilisation of shared resources and predict availability. Where we map resources are going to be free — link in resource supply with client demand."*

**Value:** Resource gaps surface weeks earlier. The right person is more likely to be available. One avoided wrong placement is worth weeks of rework.

---

## Work Streams Deferred to Later Waves

These were assessed and validated but require the data foundations that earlier waves build, or have pre-conditions not in place on day one.

---

### Governance Monitoring *(Score: 20 — Wave 3, High Priority)*

**The problem:** Governance standards are applied unevenly across projects and teams. Quality depends on who conducts the review and when. Projects can progress with gaps that go unnoticed until they create downstream risk.

**What the Problem Statement says:** *"Inconsistent governance"* is listed as a core problem. The Problem Statement explicitly proposes a **Governance Agent**: *"Continuously assesses projects against governance standards, checking documentation, approvals and criteria. Provides consistent oversight via scorecards and actionable remediation, replacing inconsistent manual audits."*

**What AI would do:** Continuously check whether projects have the required documentation in place, approvals obtained, and governance gates passed. Flag gaps before they become blockers. Generate a governance scorecard per project. Escalate deteriorating projects automatically.

**Why deferred:** Governance checks need structured project data — RAID logs, decision records, meeting summaries — that Wave 1 (Meeting Intelligence) will generate. Most valuable once that data pipeline is running.

---

### Stakeholder Communications *(Score: 16 — Wave 3, High Priority)*

**The problem:** Drafting escalation notices, steering committee packs, milestone announcements, and tailored executive briefings takes significant PMO time and is inconsistent in quality. Multiple respondents flagged stakeholder management as a core part of the role that AI should support.

**What respondents said:** ADC and Caitlin both wrote: *"A key aspect of the PMO role is stakeholder management."* Interview: *"AI can monitor whether key stakeholders turn up for meetings and whether it is a priority for them."* The Problem Statement includes a dedicated **Comms Drafting Agent**.

**What AI would do:** Draft escalation notices, milestone communications, steering committee summaries, and tailored briefings for different audiences — drawing on project data and meeting intelligence. Route all drafts for PMO approval before sending.

**Why deferred:** Stakeholder communications are most valuable when they draw on rich meeting and project context from Waves 1 and 2. The infrastructure to generate high-quality comms exists once Meeting Intelligence and Status Reports are in place.

---

### Proactive Risk Monitoring *(Score: 20 — Wave 3)*

**The concept:** Continuously scan project data — milestone slippage, budget trends, overdue actions, resource changes — and surface emerging risks before they are raised in a meeting.

**Why deferred:** Value depends entirely on project data being clean and current. In many organisations this is not the case on day one. Wave 3 once data hygiene and integration are established through earlier waves.

---

### Change Request Management *(Score: 16 — Wave 3)*

**The concept:** When a change request comes in, the AI cross-references the project plan, RAID log, and open actions to draft an impact assessment and route it for approval.

**Why deferred:** No direct stakeholder quote. Requires change management processes to be mature. Strong Wave 3 addition.

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

### Onboarding Access *(Score: 6 — RPA/Hybrid)*

**The concept:** Check that new joiners have been set up with access to all required tools and systems.

**Why not AI:** The core work is rule-based — a checklist pass/fail check. Existing automation tooling (e.g. Power Automate) handles this reliably. The only AI-relevant piece is handling exceptions, which is a small slice. Revisit in Wave 4.

---

## Summary: What Changes for a PMO

| Today | With the AI Tool |
|---|---|
| 30 min writing up meeting notes | Draft ready automatically after the meeting |
| RAID items lost or forgotten | Captured from every meeting; in the log within 30 min |
| JIRA updated manually (or not at all) | Updates proposed automatically after each meeting |
| Status reports take 45 min each, multiple manual versions | One data pull; AI generates audience-adapted versions in 10 min |
| Financial analysis done separately in Excel | Variance analysis and budget health built into every report |
| Commitments missed across email and meetings | One consolidated daily task list |
| Resource gaps spotted too late | Flagged weeks in advance with a match recommendation ready |
| Institutional knowledge lost when PMs leave | Captured, structured, and surfaced automatically (Wave 4) |

**The AI handles the repetitive and analytical work. The PMO retains control over everything that matters.**

---

*Document version: v4.0 | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-differentiation.md*
