# PMO AI Tool — Business Requirements: Personal Task Management (Wave 2)

**Scope:** Personal Task Management
**Version:** v0.1 — draft for review
**Status:** Pending stakeholder validation
**Depends on:** Wave 1 (Meeting Intelligence) outputs — action items from meetings feed directly into the consolidated task list

> This document covers Wave 2 requirements for the Personal Task Management workstream only. See `pmo-ai-business-requirements-v1.md` for Wave 1 (Meeting Intelligence).

---

## 1. Email Scanning

| # | Requirement | Why |
|---|---|---|
| BR-PT-01 | The system must scan the PMO's Outlook inbox over a configurable lookback window (default: 3 days) to identify emails containing commitments or tasks. | A 3-day window captures commitments that may have been missed in the last working period without creating an unmanageable backlog. The window must be configurable for different working patterns. |
| BR-PT-02 | The system must distinguish between three types of email content: (a) a commitment made by the PMO, (b) a task or request directed at the PMO, and (c) informational content requiring no action. | Treating all emails as tasks creates noise. The value of the tool is in extracting only the items that require action — not flagging every email the PMO receives. |
| BR-PT-03 | The system must distinguish between hard commitments ("I will send it by Friday") and soft commitments ("I'll try to get to it this week") and treat them differently in priority and urgency. | A hard commitment to a stakeholder is a deadline. A soft commitment is an intention. Treating them the same leads to over-prioritising low-stakes items or under-urgency real deadlines. |
| BR-PT-04 | Where commitment ownership is ambiguous (e.g. a group email where it is unclear who is responsible), the item must be flagged for PMO confirmation rather than automatically added to the task list. | Incorrectly attributing a task to the wrong person — or to the PMO when it was intended for someone else — creates confusion and erodes trust in the tool. |
| BR-PT-05 | The system must not store email content beyond what is required to process and extract the task. Raw email body content must not appear in audit logs or system records. | Email inboxes contain personal and commercially sensitive information. Storing email content creates a data protection risk, particularly in multi-client environments. |

---

## 2. Cross-Source Task Consolidation

| # | Requirement | Why |
|---|---|---|
| BR-PT-06 | The system must consolidate tasks from three sources into a single list: (a) email commitments extracted per Section 1, (b) action items assigned to the PMO from Wave 1 Meeting Intelligence, and (c) JIRA tickets assigned to the PMO. | PMOs currently maintain mental models across email, meeting notes, and JIRA simultaneously. Consolidating these into one list removes the cognitive overhead of tracking multiple systems. |
| BR-PT-07 | The system must deduplicate tasks that appear in multiple sources — for example, an action item from a meeting that also has a corresponding JIRA ticket. | Without deduplication, the PMO would see the same task multiple times and lose confidence in the list's accuracy. |
| BR-PT-08 | Where a task from one source appears to relate to a task from another source, the system must link them rather than treat them as separate items. | Linking provides context — the PMO can see that a task in their email is connected to an open JIRA ticket, giving them the full picture in one place. |
| BR-PT-09 | The consolidated list must clearly indicate the source of each task (email / meeting / JIRA) so the PMO understands where it came from. | Source visibility helps the PMO validate the list and trace back to the original context if needed. |

---

## 3. Prioritisation

| # | Requirement | Why |
|---|---|---|
| BR-PT-10 | The system must rank tasks by a combination of: due date urgency, requester seniority, project priority, and RAID context (e.g. tasks related to an open critical risk are elevated). | A flat list ordered only by due date misses important context. A task requested by a programme director on a red-status project should rank higher than a routine admin task due the same day. |
| BR-PT-11 | Overdue tasks must be surfaced at the top of the list with a clear overdue indicator, regardless of original priority. | An overdue commitment is always urgent by definition. Burying it in the middle of a ranked list is a design failure. |
| BR-PT-12 | The PMO must be able to manually adjust the priority or defer any task. The AI-assigned priority is a recommendation, not a constraint. | The AI does not have full context about everything in the PMO's day. Manual override is essential for the tool to be trusted and used consistently. |
| BR-PT-13 | Priority must be recalculated each time the task list is refreshed — a task that was low priority yesterday may become urgent today. | Static priorities decay in accuracy quickly. Daily recalculation ensures the list reflects current reality, not the situation from when the task was first created. |

---

## 4. Completion Detection

| # | Requirement | Why |
|---|---|---|
| BR-PT-14 | The system must monitor the PMO's Outlook sent folder to detect emails that fulfil outstanding commitments, and auto-mark the corresponding task as complete where evidence is clear. | Manually ticking off tasks is friction. If the PMO has clearly sent the promised document, the task should be closed automatically — reducing maintenance overhead. |
| BR-PT-15 | The system must monitor JIRA for ticket status changes (e.g. moved to Done or Closed) and auto-mark the corresponding task as complete. | JIRA updates are a reliable signal that work has been completed. Using them for completion detection keeps the list current without requiring manual input. |
| BR-PT-16 | Where the system cannot confidently determine whether a task is complete, it must flag it for PMO confirmation rather than auto-closing or leaving it open. | An incorrectly closed task that is still outstanding is worse than one that stays open. When in doubt, ask. |
| BR-PT-17 | The PMO must always be able to reopen a task that was auto-closed in error. | Auto-detection is not perfect. The PMO must have full control to correct mistakes without friction. |

---

## 5. Reminders

| # | Requirement | Why |
|---|---|---|
| BR-PT-18 | The system must generate reminders for tasks approaching their due date, with timing configurable per task type and urgency level. | A reminder the day before a due date is useful. A reminder three weeks before is noise. The timing must be proportionate to the urgency and nature of the task. |
| BR-PT-19 | Reminders must be delivered via the PMO's preferred channel (Microsoft Teams or Outlook), configurable per user. | Different PMOs prefer different channels. A reminder that lands in a channel the PMO doesn't monitor is not a reminder. |
| BR-PT-20 | The system must not generate reminder volume that becomes noise — repeated or excessive reminders for the same task must be suppressed after a configurable threshold. | If the tool sends too many reminders, PMOs will ignore or dismiss all of them. Reminder fatigue is a real risk that degrades the tool's effectiveness. |
| BR-PT-21 | Reminders for tasks originating from external commitments (i.e. the PMO promised something to a client or stakeholder) must be given higher urgency weighting than internal tasks. | Missing an external commitment has greater reputational and relationship consequences than missing an internal one. The reminder system must reflect this difference. |

---

## 6. Daily Checklist Interface

| # | Requirement | Why |
|---|---|---|
| BR-PT-22 | The system must present a clean daily task list, ordered by priority, accessible at the start of each working day. | The primary user value is a single place to start the day. The list must be ready and accurate when the PMO begins work. |
| BR-PT-23 | The PMO must be able to manually tick off completed tasks at any time, independent of auto-detection. | The PMO is always in control of their own task list. Manual completion should be instant and frictionless. |
| BR-PT-24 | The system must show task completion rate over time (e.g. last 7 days, last 30 days) to help PMOs identify patterns in their workload. | Completion rate trends help PMOs identify whether they are systematically overloaded, or whether certain task types are consistently slipping. This is a management insight, not just a task tool. |
| BR-PT-25 | The task list must be accessible on both desktop and mobile. | PMOs are frequently away from their desk — in meetings, on client site, travelling. A mobile-accessible list ensures the tool is useful throughout the working day. |

---

## 7. Integrations

| # | Requirement | Why |
|---|---|---|
| BR-PT-26 | The system must integrate with Outlook via the Microsoft Graph API to scan the inbox and monitor the sent folder. | Outlook is the primary email platform. Graph API access is required to read inbox content and detect sent responses. |
| BR-PT-27 | The system must integrate with JIRA via REST API to retrieve tickets assigned to the PMO and monitor ticket status changes. | JIRA is where project actions are formally tracked. Pulling assigned tickets into the consolidated list ensures nothing tracked in JIRA is missed. |
| BR-PT-28 | The system must consume action items assigned to the PMO from Wave 1 Meeting Intelligence outputs. | Meeting action items are a primary source of PMO commitments. Without Wave 1 integration, the task list is incomplete by definition. |
| BR-PT-29 | The system must integrate with Microsoft Teams for reminder delivery. | Teams is the primary collaboration platform. Delivering reminders where the PMO is already working reduces the friction of acting on them. |
| BR-PT-30 | All integrations must use OAuth 2.0 authentication. | Consistent with Wave 1 security standards and required by the Microsoft Graph and JIRA APIs. |

---

## 8. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-PT-31 | Commitment extraction precision (tasks extracted that are genuine commitments) | ≥ 85% | If more than 1 in 7 items on the list are not real commitments, the PMO will stop trusting the list and revert to managing manually. |
| BR-PT-32 | Commitment extraction recall (proportion of real commitments successfully captured) | ≥ 90% | Missing more than 1 in 10 genuine commitments defeats the purpose of the tool. The PMO cannot rely on it if significant items are regularly missed. |
| BR-PT-33 | Completion detection accuracy (auto-closures that are genuinely complete) | ≥ 95% | An incorrectly auto-closed task is a dropped commitment. This must be a high-accuracy operation. |
| BR-PT-34 | Task list refresh time (from trigger to updated list available) | ≤ 5 minutes | The list should update quickly enough to be trusted as current throughout the working day. |

---

## 9. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-PT-35 | Email body content must not be stored in any system log, database, or audit record beyond the active processing window. | Email inboxes contain personal, confidential, and commercially sensitive content. Retention beyond processing creates data protection and legal risk. |
| BR-PT-36 | PII appearing in extracted task descriptions must be masked in all audit logs. | Tasks may reference personal details of stakeholders or colleagues. These must not be exposed in system logs. |
| BR-PT-37 | The system must not send any reminder or notification to a third party (i.e. anyone other than the PMO themselves) without explicit PMO authorisation. | Sending automated reminders to clients, stakeholders, or colleagues on behalf of the PMO without their knowledge is inappropriate and could damage relationships. |
| BR-PT-38 | Access to the task list is personal — each PMO's task list must only be accessible to that individual and their explicitly authorised delegates. | Task lists contain personal commitments and workload information. Cross-visibility without consent is a privacy concern and could be used inappropriately. |

---

## 10. Out of Scope (Wave 2 — Personal Task Management)

| Item | Status |
|---|---|
| Team task management or delegation workflows | Out of scope — this tool manages the individual PMO's tasks only |
| Integration with non-Outlook email clients | Out of scope — Outlook is the standard platform in target clients |
| Automated task creation on behalf of others | Out of scope — the PMO's own commitments only |
| Proactive commitment extraction from Teams chat messages | Wave 3 consideration — scope limited to email and meeting outputs in Wave 2 |

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-PT-01 | What is the preferred reminder channel — Teams, Outlook, or both? | Affects integration scope and reminder delivery design |
| OI-PT-02 | Should the task list be visible to the PMO's line manager or team lead? | Determines access control model |
| OI-PT-03 | What JIRA project boards are relevant for each PMO? | Scoping JIRA integration to the right boards avoids surfacing irrelevant tickets |
| OI-PT-04 | Is there an existing personal task management tool in use (e.g. Microsoft To Do, Planner)? If so, should this integrate with or replace it? | Determines whether we need to coexist with or supersede existing tooling |
| OI-PT-05 | What lookback window is appropriate for email scanning? 3 days is assumed — does this match actual working patterns? | Too short misses items; too long creates an unmanageable backlog |

---

*Version: v0.1 | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1.md*
