# PMO AI Tool — How the Workflows Work

A plain-English guide to what the AI does, why it works that way, and what value it delivers.

---

## Overview

Nine workstreams were assessed. Five are recommended for the initial focus, selected on the basis of how frequently the work happens and how much judgment it requires — the two factors that make AI most valuable.

| # | Work Stream | Score | Initial Focus |
|---|---|---|---|
| 1 | **Meeting Intelligence** | 25 | ★ Yes — primary |
| 2 | **Personal Task Management** | 20 | ★ Yes |
| 3 | **Proactive Risk Monitoring** | 20 | ★ Yes |
| 4 | **Status Reports & Scorecards** | 16 | ★ Yes |
| 5 | **Change Request Management** | 16 | ★ Yes |
| 6 | Lessons Learned & Knowledge Capture | 15 | Later — needs data foundation |
| 7 | Strategic Resourcing | 12 | Later — data-dependent |
| 8 | Dependency Tracking | 12 | Later — needs mature data |
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

**Why Meeting Intelligence is primary:** It is the highest-scoring workstream and acts as the foundation — the data it captures (RAID items, decisions, actions) feeds directly into Status Reports, Personal Task Management, and Risk Monitoring.

**Value:** Follow-up from ~30 minutes to under 5. RAID items captured consistently. Decisions documented, preventing costly disputes.

---

## Work Stream 2: Personal Task Management *(Score: 20)*

*"One place for everything you have committed to doing."*

### The Problem

A PMO's commitments are scattered across emails, meeting action items, JIRA tickets, and Teams messages. Without a consolidated view, things get missed. Estimated cost: up to 2 hours a day in inbox scanning and mental overhead.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Email scanning** | Reads the last 3 days of emails; extracts commitments made or received | Reviews the list |
| **Cross-source consolidation** | Combines tasks from email, meetings (Wave 1 output), and JIRA into one list; removes duplicates | Spot-checks |
| **Prioritisation** | Ranks by urgency, requester importance, and project priority; surfaces overdue items | Adjusts if needed |
| **Completion detection** | Monitors sent folder and JIRA changes to auto-tick completed tasks | Confirms if uncertain |
| **Reminder generation** | Sends reminders at the right time via the preferred channel | Nothing |
| **Checklist interface** | Presents a clean daily task list with tick-off | Works through the list |

**Why it scores high:** It is daily, continuous, and requires reading comprehension to distinguish a soft commitment (*"I'll try"*) from a hard one (*"I will send it Friday"*). Volume is maximum (5) and judgment requirement is high (4).

**Value:** Nothing slips through. Estimated saving: up to 2 hours per day.

---

## Work Stream 3: Proactive Risk Monitoring *(Score: 20)*

*"Know about risks before they reach a meeting — when there's still time to act."*

### The Problem

The Meeting Intelligence stream captures risks that people *mention* in meetings. But many risks never get mentioned in a meeting — they emerge gradually from data: a milestone slipping, a budget trending over, a resource becoming unavailable. By the time these appear in a meeting, it's often too late to prevent the impact.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Data monitoring** | Continuously scans JIRA, MS Project, and SharePoint for signals: milestone slippage, budget trends, overdue actions, resource changes | Nothing — runs automatically |
| **Signal synthesis** | Combines weak signals across projects to identify emerging risks (e.g. delayed milestone + resource change + overdue action = escalating risk) | Reviews alerts |
| **Risk scoring** | Assesses likelihood and potential impact; assigns severity | Validates assessment |
| **Alert generation** | Raises a risk proposal with supporting evidence and suggested owner | Approves or dismisses — nothing is logged without sign-off |
| **Trend reporting** | Surfaces patterns across the portfolio (e.g. three projects showing similar early warning signs) | Acts on portfolio-level insight |

**Why it scores high:** Non-determinism is 5 — synthesising multiple weak data signals into a meaningful risk assessment is exactly the kind of pattern recognition where AI excels and where humans struggle at scale.

**Why it's distinct from Meeting Intelligence:** Meeting Intelligence is reactive (works from what was said). Proactive Risk Monitoring is predictive (works from what the data shows). Together they form a complete risk intelligence loop.

**Value:** Risks surfaced weeks earlier, when mitigation is still possible. Portfolio-wide patterns visible that no individual PMO would spot manually.

---

## Work Stream 4: Status Reports & Scorecards *(Score: 16)*

*"Stop spending a day a week pulling numbers and writing the same report."*

### The Problem

PMOs spend significant time each week collecting data from JIRA, SharePoint, and MS Project, calculating RAG scores, writing the narrative, and formatting and distributing reports. The data collection is mechanical; the narrative requires real judgment.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Data collection** | Pulls metrics automatically from JIRA, SharePoint, MS Project via API | Nothing — fully automated |
| **RAG calculation** | Applies the formula to produce Red/Amber/Green scores | Reviews the output |
| **Reconciliation** | Flags inconsistencies across data sources | Resolves conflicts |
| **Narrative writing** | Drafts the "so what" story behind the numbers | Reviews and refines |
| **Executive summary** | Tailors the narrative for senior audience | Approves before sharing |
| **Distribution** | Sends the report to the right people | Nothing — fully automated once approved |

**Why data collection is fully automated but narrative is not:** Pulling numbers from an API is deterministic — the same query always returns the same result. Writing the narrative requires understanding what the numbers *mean* in context, which projects matter most, and how to frame the story for the audience.

**Value:** A report that currently takes 45 minutes takes 10. Estimated annual saving across ~50 reports/month: ~$26,000.

---

## Work Stream 5: Change Request Management *(Score: 16)*

*"Faster, more consistent decisions on change — with a full paper trail."*

### The Problem

PMOs regularly receive requests to change project scope, timeline, or budget. Assessing the impact — what does this change affect, what is the knock-on to other workstreams, does it need escalation? — is time-consuming and often inconsistent. A senior PMO might assess a change differently to a junior one. Some assessments get skipped entirely.

### How It Works

| Step | What the AI Does | What the PMO Does |
|---|---|---|
| **Change request intake** | Receives the request; classifies type (scope/time/cost/resource) and links to affected project | Reviews classification |
| **Impact assessment** | Cross-references the project plan, RAID log, dependencies, and open actions to assess scope of impact | Reviews draft assessment |
| **Risk identification** | Flags risks introduced by the change (schedule knock-ons, resource conflicts, budget pressure) | Validates |
| **Recommendation** | Drafts an approval recommendation with supporting evidence and suggested conditions | Makes the final decision |
| **Approval routing** | Routes to the correct approver based on change type and size | Approves or rejects |
| **Audit trail** | Logs the request, assessment, recommendation, and decision | Nothing — automatic |

**Why it scores high:** The impact assessment is highly non-deterministic — it requires reading context, cross-referencing multiple sources, and exercising judgment about what matters. The output is also high-stakes: a missed impact from a poorly assessed change can derail a programme.

**Value:** Faster decisions; more consistent quality of assessment; full audit trail of every change request and the rationale behind approvals.

---

## Work Streams Deferred to Later Waves

The following streams were assessed but are not in the initial focus. They are deferred because they either require a data foundation that earlier streams will build, or because their volume and AI-fit is lower.

---

### Lessons Learned & Knowledge Capture *(Score: 15)*

**The problem:** Lessons from completed projects are rarely captured usefully and almost never surfaced when a new similar project starts. Institutional knowledge is lost.

**What AI would do:** Synthesise retrospectives and lessons into searchable knowledge; identify patterns across projects; proactively surface relevant past experience at the start of new projects.

**Why deferred:** To surface meaningful lessons, there needs to be a body of structured project data to draw from. This accumulates as earlier streams (Meeting Intelligence, Status Reports) operate. Most valuable in Wave 3 or 4 once data is mature.

---

### Strategic Resourcing *(Score: 12)*

**The problem:** Resource gaps are identified too late. Matching the right person to a role requires knowing availability, skills, and project context — information that currently lives in different places.

**What AI would do:** Monitor resource end dates; flag upcoming gaps proactively; recommend best-fit resources with trade-off explanation.

**Why deferred:** Data-dependent — needs a well-maintained skills inventory and project data, which earlier streams help build. Valuable but not the highest-impact starting point.

---

### Dependency Tracking *(Score: 12)*

**The problem:** When one project slips, it affects others — but this is rarely tracked proactively. PMOs find out about dependency impacts reactively, often after the damage is done.

**What AI would do:** Monitor cross-project dependencies; flag when a delay in Project A is likely to impact Project B; surface dependency risks before they reach a meeting.

**Why deferred:** Requires a mature, connected data model across projects. Most effective once Meeting Intelligence and Proactive Risk Monitoring are established and generating structured data.

---

### Onboarding Access *(Score: 6 — RPA/Hybrid)*

**The problem:** New joiners sometimes wait for access to tools that wasn't set up on time.

**What AI would do:** The access checking part is handled by RPA (rule-based, not AI). The only AI-relevant piece is handling exceptions — unusual access requests needing judgment. This is a small slice of the overall workload.

**Why deferred:** The core work is better served by existing RPA tooling. The AI exceptions piece will be revisited in Wave 4.

---

## Summary: What Changes for a PMO

| Today | With the AI Tool |
|---|---|
| 30 min writing up meeting notes | Draft ready automatically after the meeting |
| RAID items lost or forgotten | Captured from every meeting; in the log within 30 min |
| JIRA updated manually (or not at all) | Updates proposed automatically after each meeting |
| Risks only surface when someone raises them | Proactive alerts from data signals — before the meeting |
| Status reports take 45 min each | Takes 10 min to review and approve |
| Change assessments are slow and inconsistent | Consistent AI-drafted impact assessment; faster approval |
| Commitments missed across email and meetings | One consolidated daily task list |

**The AI handles the repetitive and analytical work. The PMO retains control over everything that matters.**

---

*Document version: v2.0 | Relates to: pmo-ai-tool-deliverables.md*
