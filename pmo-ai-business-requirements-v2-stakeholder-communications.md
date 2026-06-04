# PMO AI Tool — Business Requirements: Stakeholder Communications (Wave 2)

**Scope:** Stakeholder Communications
**Version:** v0.1 — draft for review
**Status:** Pending stakeholder validation
**Depends on:** Wave 1 (Meeting Intelligence) and Wave 2 (Status Reports, Governance Monitoring) outputs — project context from these workstreams informs the content of all drafted communications

> This document covers Wave 2 requirements for the Stakeholder Communications workstream. See `pmo-ai-business-requirements-v1-meeting-intelligence.md` for Wave 1, `pmo-ai-business-requirements-v2-status-reports.md` for Status Reports, and `pmo-ai-business-requirements-v2-governance-monitoring.md` for Governance Monitoring.
>
> **Platform note:** The PMO AI Platform is an **EPAM-built, browser-based web application** hosted on Azure and managed by EPAM. Microsoft tools (Outlook, Teams, SharePoint) are data integrations only — the platform itself runs independently on EPAM infrastructure.
>
> **Architecture note:** Stakeholder Communications is a specialist sub-agent that monitors for trigger events across the platform and generates draft communications for PMO review. It draws on outputs from Meeting Intelligence, Status Reports, and Governance Monitoring to produce contextually accurate drafts. No communication is ever sent without explicit PMO approval.

---

## 1. Trigger Detection

| # | Requirement | Why |
|---|---|---|
| BR-SC-01 | The system must monitor for defined trigger events that indicate a stakeholder communication may be required. The minimum set of triggers is: RAG status deterioration, milestone slip, new High severity Risk or Issue, governance gap escalation, and project milestone completion. | Waiting for the PMO to decide when to communicate is the current model — and it results in communications that are delayed or skipped under pressure. Automatic trigger detection ensures the PMO is prompted at the right moment. |
| BR-SC-02 | The set of trigger events must be configurable per client and per communication type, including whether a trigger generates a mandatory draft or an optional prompt. | Some triggers always require communication (e.g. RAG moving to Red on a high-profile project); others are context-dependent. Rigid rules will generate drafts the PMO dismisses almost every time, eroding trust in the feature. |
| BR-SC-03 | When a trigger event is detected, the system must determine the appropriate communication type and the appropriate recipient before generating a draft. | A trigger that produces the wrong communication type or targets the wrong person creates more work for the PMO than writing from scratch. Type and recipient determination must be accurate before drafting begins. |
| BR-SC-04 | The system must not generate a draft for the same trigger event more than once unless the underlying situation changes materially (e.g. RAG moves from Amber to Red, then further deteriorates). | Duplicate drafts for the same event create noise. Once a draft has been generated and either sent, dismissed, or is pending review, the system must not re-generate it. |
| BR-SC-05 | Where a trigger event resolves before the PMO has reviewed the draft (e.g. a milestone slip is corrected), the system must alert the PMO that the draft may no longer be relevant. | Sending a communication about a problem that has already been resolved is worse than not sending anything. The PMO must be informed when the underlying situation changes. |

---

## 2. Context Gathering

| # | Requirement | Why |
|---|---|---|
| BR-SC-06 | Before generating a draft, the system must gather all relevant project context from available sources: Wave 1 RAID items and decisions, Wave 2 status report data and RAG history, governance gap records, and JIRA ticket status. | A communication draft that lacks context — or gets context wrong — requires extensive PMO editing before it can be sent. Rich, accurate context at the point of drafting is what makes the output useful rather than just a starting point for manual rewriting. |
| BR-SC-07 | The system must identify the trigger event's causal context — what led to the trigger, not just that it occurred. | "Project Apex has moved to Red" is less useful than "Project Apex has moved to Red following vendor disclosure of a one-week delay, with the integration milestone at risk." The latter is ready to send; the former requires the PMO to supply all the substance. |
| BR-SC-08 | Where context is ambiguous or incomplete (e.g. a RAG deterioration with no corresponding meeting decision or risk explaining why), the system must flag this to the PMO rather than generating a draft based on incomplete information. | A draft generated from incomplete context will contain gaps the PMO may not immediately notice. Surfacing the gap forces the PMO to supply the missing context before drafting, not after reviewing an inaccurate draft. |
| BR-SC-09 | Context gathering must not require any PMO input for standard trigger events — it must run automatically. | If the PMO must assemble context before a draft can be generated, the feature adds steps rather than removing them. |

---

## 3. Draft Generation

| # | Requirement | Why |
|---|---|---|
| BR-SC-10 | The system must generate draft communications for the following types at minimum: escalation notice (RAG change), milestone slip notification, risk or issue escalation to sponsor, governance gap notice, milestone completion announcement, and steering committee briefing. | These are the most time-consuming and pressure-sensitive communications in a PMO's week. Automating the first draft for each removes the most painful manual writing tasks. |
| BR-SC-11 | Every draft must be accurate to the current project state at the time of generation — it must not contain stale data, incorrect figures, or references to events that have since been resolved. | An inaccurate draft that the PMO sends without catching the error is a governance and relationship failure. Accuracy at the point of generation is the primary quality requirement for this workstream. |
| BR-SC-12 | Every draft must include: the trigger event that caused it, the relevant project context, any required actions or decisions, and a clear proposed subject line. | A draft missing any of these elements is not ready to review — it is a prompt for the PMO to write the communication themselves. A complete draft should be reviewable in under two minutes. |
| BR-SC-13 | Draft communications must not be fabricated — every factual statement in the draft must be traceable to a specific source (RAID log entry, status report data point, JIRA ticket, or meeting decision). | If the PMO cannot verify where each statement comes from, they cannot confidently send the draft. Source traceability is as important here as it is for RAID items in Wave 1. |
| BR-SC-14 | The system must indicate its confidence in the draft's accuracy. Drafts with any low-confidence elements must be flagged for additional PMO attention before sending. | A draft that includes an inference the system is uncertain about is risky to send unchecked. Flagging uncertainty prompts the PMO to verify before sending. |

---

## 4. Audience Adaptation

| # | Requirement | Why |
|---|---|---|
| BR-SC-15 | The system must generate audience-appropriate drafts — the tone, level of detail, and framing must be appropriate for the recipient type (sponsor, programme director, project team, executive, or steering committee). | A communication drafted for a sponsor reads differently from one drafted for a project team. Generic drafts that require heavy reformatting for the audience defeat the purpose of automating the drafting step. |
| BR-SC-16 | Where the same trigger event warrants communications to multiple recipients at different levels, the system must generate separate drafts for each recipient type from the same underlying context. | A milestone slip may require both a sponsor escalation and a team briefing. Both should be available for review — and must be consistent with each other even though they differ in tone and detail. |
| BR-SC-17 | Audience-specific communication formats and tone guidelines must be configurable per client. | Different clients and cultures have different communication conventions. What is appropriate for one programme director may be too formal or too casual for another. |

---

## 5. Review & Approval

| # | Requirement | Why |
|---|---|---|
| BR-SC-18 | Every draft communication must be presented to the PMO for review before any send action is available. | No AI-generated external communication may bypass PMO review. This is a non-negotiable governance requirement consistent across all workstreams. |
| BR-SC-19 | The system must never send a communication without explicit PMO approval. | External communications carry reputational, legal, and relational risk. There is no trigger event severe enough to justify autonomous sending. |
| BR-SC-20 | The PMO must be able to edit any draft before sending, including subject line, recipient, body text, and any attached data. | A draft that the PMO cannot edit without leaving the tool is not a useful draft. Editing must be possible inline, without switching to a separate email client. |
| BR-SC-21 | The PMO must be able to discard any draft without sending, without being required to provide a reason. | PMOs sometimes decide a communication is not needed after reading the draft. The tool must not force justification for not sending. |
| BR-SC-22 | Where a draft has been pending PMO review for more than a configurable period without action, the system must send a reminder via Teams or Outlook. | A draft sitting unreviewed is a missed communication. Reminders ensure the PMO is aware of pending drafts without the tool taking any autonomous action. |

---

## 6. Distribution & Record-Keeping

| # | Requirement | Why |
|---|---|---|
| BR-SC-23 | Once approved, the system must send the communication via Outlook to the specified recipient(s) automatically. | Manual sending after approval adds no value and creates an opportunity for the approved version to be modified outside the tool's audit trail. |
| BR-SC-24 | Every sent communication must be recorded with: the trigger event, the original draft content, the PMO edits made (if any), the approving PMO user, the timestamp, and the recipient list. | Communications are governance artefacts. If a sponsor later disputes what they were told, or when, the record must be available. |
| BR-SC-25 | Sent communications must be stored in the tool's audit log and optionally written to a designated SharePoint folder per project, as configured by the PMO Lead. | Some clients will want communications stored in their project records in SharePoint. This must be configurable — the system must not write to SharePoint without it being explicitly enabled. |
| BR-SC-26 | Communication history must be searchable by project, recipient, date, and communication type. | The PMO must be able to retrieve the history of communications on a project quickly — for audit, for context before a meeting, or to check what was last said to a particular stakeholder. |

---

## 7. Integrations

> These are data integrations — the EPAM platform reads from client systems for context and writes approved outputs via Outlook. It does not run inside any client system.

| # | Requirement | Why |
|---|---|---|
| BR-SC-27 | The system must consume Wave 1 (Meeting Intelligence) outputs — RAID items, decisions, and action records — as context for communication drafts. | RAID items and decisions are the most important context for escalation notices and stakeholder briefings. Without Wave 1 outputs, drafts lack the detail that makes them useful. |
| BR-SC-28 | The system must consume Wave 2 Status Report outputs — RAG status, RAG history, financial health, and report narrative — as context for communications triggered by status changes. | Status report data provides the quantitative basis for communications triggered by RAG changes or financial deterioration. |
| BR-SC-29 | The system must consume Wave 2 Governance Monitoring outputs — gap records and scorecard data — as context for governance-related communications. | Governance gap escalations must draw on current, accurate governance monitoring data, not on the PMO's recollection of what gaps exist. |
| BR-SC-30 | The system must integrate with Outlook via the Microsoft Graph API to send approved communications. | Outlook is the primary external communication channel. Direct integration ensures sent items are consistently formatted and logged. |
| BR-SC-31 | The system must integrate with SharePoint via the Microsoft Graph API to optionally write approved communications to project communication records. | Clients who maintain communication records in SharePoint should be able to have approved communications written there automatically, where configured. |
| BR-SC-32 | All integrations must use OAuth 2.0 authentication, consistent with Wave 1 and Wave 2 standards. | Required by Microsoft Graph and consistent with the platform security standard. |

---

## 8. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-SC-33 | Time from trigger event detection to draft available for PMO review | ≤ 15 minutes | The value of a timely escalation declines rapidly. A 15-minute window ensures the PMO can respond to urgent events the same day they occur. |
| BR-SC-34 | Draft acceptance rate (PMO sends without material changes) | ≥ 75% | Consistent with the status report narrative target. If the PMO rewrites most drafts, the AI is providing a prompt rather than a near-finished output — which is not the design intent. |
| BR-SC-35 | Trigger detection accuracy (proportion of genuine trigger events correctly detected) | ≥ 95% | Missed trigger events mean missed communications. The system must reliably detect the events that warrant a stakeholder notification. |
| BR-SC-36 | False trigger rate (drafts generated for events that did not warrant communication, per PMO review) | ≤ 10% | Consistent with the governance monitoring false positive target. Too many unnecessary drafts erode PMO trust and add review overhead. |
| BR-SC-37 | Distribution success rate (approved communications delivered to all recipients via Outlook) | ≥ 99.5% | A communication approved for sending that does not reach its recipient is a governance failure. Near-perfect reliability is required. |

---

## 9. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-SC-38 | Zero communications must be sent without explicit PMO approval. | Non-negotiable across all workstreams. External communications carry reputational, legal, and relational risk. |
| BR-SC-39 | Zero communications must be generated that are not directly traceable to a defined trigger event and a set of named source data points. | Hallucinated or uncorroborated statements in a stakeholder communication could misrepresent project status, damage relationships, or create a false governance record. |
| BR-SC-40 | All communication drafts must be retained in the audit log regardless of whether they were sent, edited and sent, or discarded. | The record of what was drafted — including discarded drafts — provides evidence of the PMO's decision-making and communications governance. |
| BR-SC-41 | PII in communication drafts must be handled in accordance with the platform's data minimisation and masking policies, consistent with Wave 1 standards. | Communication drafts may reference individuals. PII handling must be consistent across the platform. |
| BR-SC-42 | Communication templates and trigger rules may only be changed with PMO Lead approval before deployment. | Templates and trigger rules determine what is communicated and to whom. Unauthorised changes could result in communications going to wrong recipients or missing required content. |

---

## 10. Out of Scope (Wave 2 — Stakeholder Communications)

| Item | Status |
|---|---|
| Inbound communication management — reading and triaging stakeholder emails | Wave 3+ — requires inbox access and more complex intent classification |
| Automated stakeholder sentiment monitoring | Wave 3+ |
| Meeting invitation and scheduling management | Out of scope — not a communications drafting problem |
| Real-time communications (Teams chat, instant messages) | Out of scope — this workstream covers formal written communications via Outlook |
| Any communication sent without PMO approval | Out of scope permanently |

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-SC-01 | What is the full list of trigger events that require a stakeholder communication — and for each, is the communication mandatory or conditional on context? | Cannot configure trigger detection rules without this list |
| OI-SC-02 | Who are the standard stakeholder roles and recipients for each communication type per client — sponsor, programme director, executive sponsor, steering committee chair? | Cannot determine correct recipients without the stakeholder map per client |
| OI-SC-03 | Are there any regulatory communication requirements with specific timelines (e.g. incident reporting obligations under DORA or FCA requirements)? | Regulatory timelines require hard triggers and guaranteed delivery — different from discretionary communications |
| OI-SC-04 | Should sent communications be written to SharePoint project records, or is the tool's own audit log sufficient? | Affects the SharePoint integration scope for this workstream |
| OI-SC-05 | Are there client-specific tone, style, or format requirements for different communication types? | Templates must reflect actual client conventions to produce drafts that do not need reformatting |
| OI-SC-06 | Is steering committee pack preparation in scope for Wave 2, or deferred — it is a significant PMO effort item but requires a more complex template than escalation notices? | Affects the communication type scope and build complexity for Wave 2 |

---

*Version: v0.1 | Relates to: pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1-meeting-intelligence.md, pmo-ai-business-requirements-v2-status-reports.md, pmo-ai-business-requirements-v2-governance-monitoring.md*
