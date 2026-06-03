# PMO AI Tool — How the Workflows Work

A plain-English guide to what the AI does, why it works that way, and what value it delivers.

---

## Overview

Nine workstreams were assessed. Four are selected for the initial focus — all four are grounded in direct stakeholder quotes, all four are deliverable without significant pre-conditions, and together they cover the full breadth of a PMO's week.

| # | Work Stream | Score | Wave |
|---|---|---|---|
| 1 | **Meeting Intelligence** | 25 | ★ Wave 1 |
| 2 | **Status Reports & Scorecards** | 16 | ★ Wave 1 |
| 3 | **Personal Task Management** | 20 | ★ Wave 1 |
| 4 | **Strategic Resourcing** | 12 | ★ Wave 1 |
| 5 | Proactive Risk Monitoring | 20 | Wave 2 |
| 6 | Change Request Management | 16 | Wave 2 |
| 7 | Lessons Learned & Knowledge Capture | 15 | Wave 3 |
| 8 | Dependency Tracking | 12 | Wave 3 |
| 9 | Onboarding Access | 6 | RPA — not AI-first |

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

**Why it is primary:** Highest score, fully standalone, and it acts as the foundation — the actions, decisions, and RAID items it captures feed directly into Status Reports, Personal Task Management, and Strategic Resourcing.

**Value:** Follow-up time from ~30 minutes to under 5. RAID items captured consistently. Decisions documented, preventing costly disputes. Estimated annual saving: ~$18,000.

---

## Work Stream 2: Status Reports & Scorecards *(Score: 16)*

*"Stop spending a day a week pulling numbers and writing the same report."*

### The Problem

PMOs spend significant time each week collecting data from JIRA, SharePoint, and MS Project, calculating RAG scores, writing the narrative that explains what the numbers mean, and formatting and distributing reports. The data collection is purely mechanical — but the narrative requires real judgment about what matters and how to frame it for the audience.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Data collection** | Pulls metrics automatically from JIRA, SharePoint, MS Project via API | Nothing — fully automated |
| **RAG calculation** | Applies the formula to produce Red/Amber/Green scores | Reviews the output |
| **Reconciliation** | Flags inconsistencies across data sources | Resolves conflicts |
| **Narrative writing** | Drafts the "so what" story behind the numbers | Reviews and refines |
| **Executive summary** | Tailors the narrative for senior audience | Approves before sharing |
| **Distribution** | Sends the report to the right people | Nothing — fully automated once approved |

**Why data collection is fully automated but narrative is not:** Pulling numbers from an API is deterministic — the same query always returns the same result. Writing the narrative requires understanding what the numbers *mean* in context, which projects matter most to leadership right now, and how to frame the story for different audiences.

**Why it is ranked #2:** Status reports are produced by every PMO, every week. The time saving is immediately visible and measurable. Unlike some other streams it doesn't depend on any prior data or special setup — it works from day one against existing JIRA and SharePoint data.

**Value:** A report that currently takes 45 minutes takes 10. Estimated annual saving: ~$26,250.

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

**Why it requires AI and not just a to-do list app:** The hard part is extracting commitments from email. The AI must distinguish a hard commitment (*"I will send it Friday"*) from a soft one (*"I'll try"*) and a request to you (*"can you check?"*) from information (*"FYI the meeting moved"*). That reading comprehension is where AI adds the value.

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

**Why the matching step needs AI:** Identifying who is available is easy — a query against a spreadsheet. Recommending *who to assign* requires weighing competing factors: this person has the right skills but finishes in 3 weeks; that person is available now but is a stretch; the project director prefers someone with banking experience. That trade-off reasoning is where AI adds genuine value over a simple lookup.

**Why resource commitments are always human-only:** Telling someone they are being moved to a new project is a management decision with HR, contractual, and relationship implications. The AI informs the decision — it never makes it.

**Value:** Resource gaps surface weeks earlier, when there is still time to act. The right person is more likely to be available. Estimated value: qualitative — one avoided wrong placement is worth weeks of rework.

---

## Work Streams Deferred to Later Waves

The following were assessed but are not in the initial focus. They are deferred either because they depend on data that earlier waves will build, or because they have pre-conditions that may not be in place on day one.

---

### Proactive Risk Monitoring *(Score: 20 — Wave 2)*

**The concept:** Continuously scan project data — milestone slippage, budget trends, overdue actions, resource changes — and surface emerging risks before they are raised in a meeting.

**Why deferred:** This stream's value depends entirely on project data being clean, current, and consistently maintained in JIRA and MS Project. In many organisations this is not the case on day one. If the underlying data is unreliable, the monitoring generates noise rather than insight, which erodes trust. It is a high-potential Wave 2 capability once Wave 1 has established good data hygiene and integration foundations.

---

### Change Request Management *(Score: 16 — Wave 2)*

**The concept:** When a change request comes in (scope, timeline, budget), the AI cross-references the project plan, RAID log, and open actions to draft an impact assessment and route it for approval.

**Why deferred:** No direct stakeholder quote supports this — it was identified through analysis of typical PMO work rather than stated customer pain. It also requires change management processes to be reasonably mature. A strong Wave 2 addition once the core four are delivering.

---

### Lessons Learned & Knowledge Capture *(Score: 15 — Wave 3)*

**The concept:** Synthesise retrospectives into searchable knowledge and proactively surface relevant past experience when a new similar project starts.

**Why deferred:** Meaningful pattern recognition requires a body of structured project data to work from. This accumulates as earlier streams operate. Most valuable in Wave 3 once Meeting Intelligence and Status Reports have generated a rich data set.

---

### Dependency Tracking *(Score: 12 — Wave 3)*

**The concept:** Monitor cross-project dependencies and flag when a delay in one project is likely to impact another before the PMO realises it.

**Why deferred:** Requires a mature, connected data model across projects. Most effective once the earlier waves are established and generating reliable structured data.

---

### Onboarding Access *(Score: 6 — RPA/Hybrid)*

**The concept:** Check that new joiners have been set up with access to all required tools and systems.

**Why not AI:** The core work is rule-based — a checklist pass/fail check. Existing automation tooling (e.g. Power Automate) handles this reliably without AI. The only AI-relevant piece is handling exceptions, which is a small slice. Revisit in Wave 4.

---

## Summary: What Changes for a PMO

| Today | With the AI Tool |
|---|---|
| 30 min writing up meeting notes | Draft ready automatically after the meeting |
| RAID items lost or forgotten | Captured from every meeting; in the log within 30 min |
| JIRA updated manually (or not at all) | Updates proposed automatically after each meeting |
| Status reports take 45 min each | Takes 10 min to review and approve |
| Commitments missed across email and meetings | One consolidated daily task list |
| Resource gaps spotted too late | Flagged weeks in advance with a match recommendation ready |

**The AI handles the repetitive and analytical work. The PMO retains control over everything that matters.**

---

*Document version: v3.0 | Relates to: pmo-ai-tool-deliverables.md*
