# PMO AI Tool — Business Requirements: Governance Monitoring (Wave 2)

**Scope:** Governance Monitoring
**Version:** v0.2 — updated 2026-06-11: regulatory compliance checking reframed as client onboarding config (not Wave 3+ deferral); OI-GM-05 updated to reflect regulatory programmes in immediate pipeline
**Status:** Pending stakeholder validation
**Depends on:** Wave 1 (Meeting Intelligence) outputs — RAID logs, decision records, and meeting summaries are the primary evidence source for governance checks

> This document covers Wave 2 requirements for the Governance Monitoring workstream. See `pmo-ai-business-requirements-v1-meeting-intelligence.md` for Wave 1 and `pmo-ai-business-requirements-v2-status-reports.md` for Status Reports.
>
> **Platform note:** The PMO AI Platform is an **EPAM-built, browser-based web application** hosted on Azure and managed by EPAM. Microsoft tools (SharePoint, JIRA, Outlook) are data integrations only — the platform itself runs independently on EPAM infrastructure.
>
> **Architecture note:** Governance Monitoring is a specialist sub-agent within the orchestrated multi-agent platform. It reads structured outputs from the Meeting Intelligence and Status Reports sub-agents and checks them against a configured set of governance standards. It proposes actions to the PMO — it does not resolve gaps independently.

---

## 1. Governance Standards Configuration

| # | Requirement | Why |
|---|---|---|
| BR-GM-01 | The system must maintain a configurable set of governance standards and criteria per client, covering at minimum: required documentation, approval gates, review cadences, and change control requirements. | Governance standards vary by client, project type, and regulatory environment. A fixed set of rules will be wrong for any client that deviates from a default assumption. |
| BR-GM-02 | Governance standards must be configurable by a PMO Lead without requiring code changes or EPAM involvement. | Standards change as clients evolve their governance frameworks. PMO Leads must be able to update rules quickly without raising a change request to the development team. |
| BR-GM-03 | Each governance standard must specify: what is being checked, the evidence source (e.g. SharePoint document, RAID log entry, JIRA field), the review cadence, and the severity if breached (High, Medium, or Low). | A governance check without a defined evidence source cannot be evaluated automatically. Cadence and severity determine how the system schedules and prioritises its checks. |
| BR-GM-04 | Standards must be versionable — when a governance standard is changed, the previous version must be retained in the audit log with an effective date. | Governance frameworks are updated periodically. Retaining version history allows the system to correctly evaluate projects against the standard that applied at any given point in time, and supports audit evidence. |

---

## 2. Project Assessment

| # | Requirement | Why |
|---|---|---|
| BR-GM-05 | The system must assess each active project against all applicable governance standards on a configurable schedule — at minimum weekly, and on demand. | Weekly assessment ensures gaps are caught promptly. On-demand assessment allows the PMO to run a check before a steering committee or milestone review. |
| BR-GM-06 | Assessment must be triggered automatically — it must not require manual initiation for scheduled runs. | If the PMO must remember to trigger governance checks, the checks will be skipped during busy periods — exactly when governance gaps are most likely to accumulate. |
| BR-GM-07 | The system must draw on Wave 1 (Meeting Intelligence) outputs as primary evidence for checks where relevant — e.g. decisions recorded, RAID items logged, action owners assigned. | Wave 1 generates structured, traceable project records that are the most reliable evidence for governance checks. Using this data avoids duplication of effort and ensures checks reflect the actual state of project work. |
| BR-GM-08 | Where evidence for a governance check cannot be automatically retrieved, the system must flag the check as unresolvable and present it to the PMO to resolve manually. | Some evidence may require human judgment to locate or evaluate — for example, a document that exists but is in an unexpected location. The system must not silently mark a check as passed when it could not find evidence. |
| BR-GM-09 | The system must not mark a governance check as passed unless it has retrieved specific, traceable evidence. A check with no evidence found must be flagged as a gap, not assumed compliant. | Assumed compliance without evidence is indistinguishable from a governance failure. The default state when evidence is absent must be "gap", not "pass". |

---

## 3. Gap Detection & Classification

| # | Requirement | Why |
|---|---|---|
| BR-GM-10 | The system must classify each detected gap by type: Missing Document, Overdue Approval, Overdue Review, Unresolved Change Request, or Governance Gate Failure. | Different gap types require different PMO responses. Classifying them correctly ensures the right person takes the right action — a missing document needs a different response than an unresolved change request. |
| BR-GM-11 | Each gap must be classified by severity (High, Medium, or Low) based on the configured standard it relates to. | Severity determines how urgently the gap must be addressed and whether an immediate alert is sent to the PMO. Not all governance gaps are equally urgent. |
| BR-GM-12 | High severity gaps must trigger an immediate PMO notification via Teams or Outlook, separate from the regular weekly summary. | A High severity gap — such as a missing sign-off on a change already in progress — cannot wait for the next scheduled review. The PMO must know immediately. |
| BR-GM-13 | Every gap must include: which governance standard was breached, what evidence was expected, what evidence was found (if any), when the gap was first detected, and how long it has been open. | Without this information, the PMO cannot investigate or resolve the gap efficiently. Knowing when a gap was first detected is particularly important — a gap open for three days is treated differently from one open for three weeks. |
| BR-GM-14 | The system must not generate duplicate gap records for the same breach on the same project — if a gap remains unresolved, it must persist as the same record, not be re-raised as a new gap each assessment cycle. | Duplicate gap records create noise and inflate the apparent number of governance issues. A persistent gap should age in place, making its duration visible. |

---

## 4. Scorecard Generation

| # | Requirement | Why |
|---|---|---|
| BR-GM-15 | The system must generate a governance scorecard for each project, showing the status of every applicable governance standard: Compliant (green), At Risk (amber), or Non-Compliant (red). | A per-project scorecard gives the PMO an at-a-glance view of governance health without checking individual items manually. It is also a shareable artefact for sponsors and steering committees. |
| BR-GM-16 | The scorecard must show trend — whether governance health has improved, remained stable, or deteriorated since the previous assessment. | Trend is more important than snapshot. A project consistently amber is less concerning than a project that moved from green to red in one week. |
| BR-GM-17 | A portfolio-level scorecard must be available showing governance health across all active projects, allowing the PMO to identify which projects need immediate attention. | With multiple projects running simultaneously, the PMO needs a portfolio view to prioritise where to spend their time. |
| BR-GM-18 | Scorecards must be producible on demand for steering committee or audit purposes. | PMOs are sometimes asked to demonstrate governance compliance at short notice. The system must be able to generate a point-in-time scorecard without manual compilation. |
| BR-GM-19 | The scorecard must be produced as a draft for PMO review before being shared externally — it must not be distributed automatically. | Scorecards shared externally represent the PMO's assessment of project governance. The PMO must review them before they are seen by sponsors, steering committees, or auditors. |

---

## 5. Escalation & PMO Notification

| # | Requirement | Why |
|---|---|---|
| BR-GM-20 | The system must notify the PMO of new governance gaps via Teams or Outlook, with sufficient context for the PMO to decide their immediate response without having to open the tool first. | A notification with no context is unhelpful. The PMO needs to know what the gap is, on which project, and how severe — in the notification itself. |
| BR-GM-21 | For High severity gaps, the system must draft an escalation notice to the relevant sponsor or stakeholder. This draft must be presented for PMO review — the system must not send it independently. | High severity gaps may need to be communicated to sponsors. Drafting the notice saves the PMO time, but the decision to send and the content must remain with the PMO. |
| BR-GM-22 | The system must provide a weekly governance summary across all projects, delivered at a configurable time. | A weekly summary gives the PMO a structured cadence for governance review, rather than relying on individual gap notifications that may be missed in a busy inbox. |
| BR-GM-23 | Notifications must link directly to the relevant gap or scorecard in the tool, not just to the tool's home screen. | A notification that requires the PMO to navigate to find the relevant item adds unnecessary friction. |

---

## 6. Gap Resolution Tracking

| # | Requirement | Why |
|---|---|---|
| BR-GM-24 | Every gap must have a resolution status: Open, In Progress, Escalated, Resolved, or Dismissed. | Without a clear status on each gap, the PMO cannot tell at a glance what still needs attention and what has been dealt with. |
| BR-GM-25 | The PMO must be able to update the resolution status of any gap directly in the tool. | Gaps are resolved through actions that happen outside the tool — a document gets uploaded, an approval gets obtained. The PMO must be able to mark these as resolved when done. |
| BR-GM-26 | Every dismissal must require a reason, recorded against the gap. A gap may not be dismissed without a reason. | Dismissing a governance gap without a reason creates an unexplained hole in the governance record. The reason is evidence that the PMO made a deliberate, informed decision. |
| BR-GM-27 | The system must automatically re-open a dismissed gap if the evidence it was dismissed against is subsequently removed or invalidated. | A gap dismissed because a document was uploaded should not remain dismissed if that document is later deleted. The system must re-check its evidence and re-raise gaps accordingly. |
| BR-GM-28 | Resolved and dismissed gaps must be retained in the audit log and must remain searchable — they must not be deleted. | Governance records are subject to audit. Evidence that a gap was identified, investigated, and resolved or consciously dismissed is as important as the gap itself. |

---

## 7. Integrations

> These are data integrations — the EPAM platform reads from client systems to gather evidence for governance checks. It does not run inside SharePoint, JIRA, or any other client system.

| # | Requirement | Why |
|---|---|---|
| BR-GM-29 | The system must integrate with SharePoint via the Microsoft Graph API to read project documentation, list data, and RAID log entries as evidence for governance checks. | SharePoint is the primary location for project governance documentation. Reading directly allows automated checks against what is actually there, not what someone remembers uploading. |
| BR-GM-30 | The system must consume Wave 1 (Meeting Intelligence) outputs — RAID items, decisions, and action records — as evidence inputs for governance checks. | Wave 1 generates the most structured and reliable record of project activity. Using these outputs avoids duplicating data capture and ensures checks reflect actual work. |
| BR-GM-31 | The system must integrate with JIRA via REST API to verify the status of change requests, approvals, and issue resolutions used as governance evidence. | JIRA is the source of truth for change requests and issue resolution in many clients' governance frameworks. |
| BR-GM-32 | The system must integrate with Outlook via the Microsoft Graph API to deliver notifications and escalation drafts to the PMO. | PMOs receive notifications in Outlook or Teams — the system must reach them through the channels they already use. |
| BR-GM-33 | All integrations must use OAuth 2.0 authentication, consistent with Wave 1 standards. | Required by Microsoft Graph and Jira APIs. Consistent with the security approach established in Wave 1. |

---

## 8. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-GM-34 | Gap detection recall (proportion of actual governance gaps identified by the system) | ≥ 95% | Missing a governance gap is the primary failure mode. If the system misses 1 in 20 gaps, PMOs cannot rely on it as their governance assurance mechanism. |
| BR-GM-35 | False positive rate (gaps flagged that turn out not to be genuine after PMO review) | ≤ 10% | If the PMO must investigate and dismiss a high proportion of flagged items, the tool creates more work than it saves. |
| BR-GM-36 | Time from assessment trigger to scorecard available for PMO review | ≤ 2 hours | A 2-hour window ensures results are available before the PMO's working day begins when assessments run overnight. |
| BR-GM-37 | Assessment completion rate (assessments that complete without system error) | ≥ 99% | Governance assessments that fail silently are a trust and compliance risk. Near-perfect reliability is required. |
| BR-GM-38 | PMO gap acceptance rate (gaps the PMO confirms as genuine after review) | ≥ 85% | If fewer than 85% of flagged gaps are confirmed genuine, the signal-to-noise ratio is too low to be useful. |

---

## 9. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-GM-39 | Zero governance gaps must be marked as resolved or dismissed without explicit PMO action. | Auto-resolving gaps would undermine the entire purpose of the workstream. The system detects and surfaces — humans resolve and dismiss. |
| BR-GM-40 | Zero escalation notices or external communications related to governance gaps must be sent without explicit PMO approval. | Governance escalations sent without PMO review could damage stakeholder relationships or incorrectly characterise a project's compliance position to a sponsor. |
| BR-GM-41 | A complete audit trail must be maintained for every gap, including: when it was first detected, every assessment result, every PMO action taken, and the final resolution. | Governance monitoring is itself subject to audit. The system must demonstrate that every gap was identified, tracked, and resolved through an authorised process. |
| BR-GM-42 | Governance standard configurations must be change-controlled — every change must record who made it, when, and what was changed. | Unauthorised changes to standards could silently narrow the scope of governance monitoring without the PMO's knowledge. |
| BR-GM-43 | The system must mask any personally identifiable information (PII) in governance logs and trace data, consistent with Wave 1 standards. | Governance check evidence may reference individuals. PII must be handled consistently across the platform. |

---

## 10. Out of Scope (Wave 2 — Governance Monitoring)

| Item | Status |
|---|---|
| Automated gap remediation — the system resolving governance gaps without PMO action | Out of scope permanently — all resolution requires human action |
| Regulatory compliance checking (e.g. DORA, MiFID II, FCA-specific rule sets) | The governance check *engine* is in scope for Wave 2. Defining the specific regulatory rule sets requires specialist legal/compliance input and must be completed as a client onboarding activity before Wave 2 goes live — not deferred until Wave 3. EPAM will work with each client's compliance team to configure rules at onboarding. Default configuration will not include regulatory rules until confirmed by the client. |
| Real-time (sub-hourly) governance monitoring | Out of scope for Wave 2 — weekly scheduled assessment is sufficient |
| External audit portal or read-only auditor access | Future consideration — out of scope for Wave 2 |
| Governance monitoring for non-project processes (e.g. team or operational governance) | Out of scope — this workstream covers project governance only |

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-GM-01 | What governance standards and criteria apply — are they defined at EPAM level, per client, per project type, or a combination? | Cannot configure assessment rules without knowing what the standards are |
| OI-GM-02 | What is the authoritative evidence source for each governance check — SharePoint only, or also JIRA, email, or manual confirmation? | Evidence source determines whether a check can be automated or requires PMO input |
| OI-GM-03 | Who has authority to define and update governance standards — PMO Lead, client governance team, or both? | Determines the approval process for standard configuration and changes |
| OI-GM-04 | What is the current governance review cadence in practice — weekly, per milestone, or ad hoc? | Determines the default assessment schedule |
| OI-GM-05 | What are the client-specific regulatory requirements (e.g. DORA, MiFID II, FCA, AIB Change Methodology) that must be reflected in governance standards, and who in the client compliance team will define and sign off the rule configurations? | Regulatory rule definitions must be confirmed by the client compliance team as a Wave 2 onboarding deliverable. Three of the first six AIB roles reviewed are in regulated programmes (IRB, AML, SEPA) with hard compliance deadlines — regulatory governance is a live Wave 2 requirement, not a Wave 3+ consideration. |
| OI-GM-06 | Should governance scorecards be automatically distributed to sponsors or steering committees, or only available on demand? | Affects the distribution workflow design — automated scorecard distribution has different implications from distributing status reports |

---

*Version: v0.1 | Relates to: pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1-meeting-intelligence.md, pmo-ai-business-requirements-v2-status-reports.md*
