# PMO AI Tool — Business Requirements: Status Reports & Scorecards (Wave 2)

**Scope:** Status Reports & Scorecards
**Version:** v0.1 — draft for review
**Status:** Pending stakeholder validation
**Depends on:** Wave 1 (Meeting Intelligence) outputs — RAID items, decisions, and meeting summaries feed into report narratives

> This document covers Wave 2 requirements for the Status Reports & Scorecards workstream only. See `pmo-ai-business-requirements-v1.md` for Wave 1 (Meeting Intelligence).

---

## 1. Data Collection

| # | Requirement | Why |
|---|---|---|
| BR-SR-01 | The system must automatically pull project metrics from JIRA, SharePoint, and MS Project via their respective APIs on a configurable schedule (e.g. weekly) and on demand. | PMOs currently export data manually from each system and combine it. Automation eliminates this step entirely and ensures data is always current at the point of reporting. |
| BR-SR-02 | The system must support configurable data sources per client — not all clients will use the same combination of tools. | Different clients use different toolsets. A fixed assumption about which systems are in use will break for any client that deviates from the default. |
| BR-SR-03 | Where a data source API is unavailable, the system must queue the report, alert the PMO, and not generate a report from incomplete data. | A report built on partial data is worse than no report — it creates a false picture of project health. The PMO must be aware when data is missing. |
| BR-SR-04 | The system must record the timestamp of each data pull so the PMO knows how current the report data is. | Report recipients need to know when the data was collected. Stale data presented as current undermines trust in the report. |

---

## 2. Financial Analysis

| # | Requirement | Why |
|---|---|---|
| BR-SR-05 | The system must calculate budget vs actuals per project, including spend to date and forecast cost to completion. | Financial health is a core component of any status report. PMO survey respondents explicitly identified financial data analysis as an unmet need. |
| BR-SR-06 | The system must calculate budget variance (actual spend vs planned spend at this point in the project) and flag projects where variance exceeds a configurable threshold. | A project can be on schedule but over budget, or within budget but slipping. Variance against plan is more informative than raw spend figures alone. |
| BR-SR-07 | The system must identify spend trends (accelerating, stable, or decelerating) and surface projects where the current burn rate is projected to exhaust the budget before project completion. | Trend is more valuable than snapshot. A project 10% over budget and accelerating needs urgent attention; a project 10% over but slowing does not. |
| BR-SR-08 | Financial data used in reports must not be stored in debug or trace logs. | Financial data is commercially sensitive. Exposing it in logs creates a data security risk, particularly in shared or multi-client environments. |

---

## 3. RAG Status Calculation

| # | Requirement | Why |
|---|---|---|
| BR-SR-09 | The system must calculate a RAG (Red / Amber / Green) status for each project based on configurable criteria covering schedule, budget, risk, and resource dimensions. | RAG is the standard PMO health indicator. Automating the calculation ensures it is applied consistently across all projects using the same criteria, not dependent on individual PMO judgment. |
| BR-SR-10 | RAG criteria must be configurable per client and per project type — not all clients or project types use the same thresholds. | A threshold appropriate for a three-month project may be wrong for a three-year programme. Rigid defaults will produce incorrect statuses for a significant proportion of projects. |
| BR-SR-11 | Where a project's RAG status has deteriorated since the last report (e.g. Green to Amber, or Amber to Red), the system must flag this change prominently for PMO review before the report is finalised. | Downward RAG movements are the most important signal in a status report. They must not be buried in a table — they require explicit PMO acknowledgement before being reported to stakeholders. |
| BR-SR-12 | The system must not change a project's RAG status without the PMO being able to review and override the calculated status before the report is distributed. | The RAG status is a governance judgment, not just a calculation. The PMO may have context the data does not reflect. Automated status changes without review could embarrass the PMO or misrepresent the project to leadership. |

---

## 4. Cross-Source Data Reconciliation

| # | Requirement | Why |
|---|---|---|
| BR-SR-13 | Where data from different sources conflicts (e.g. JIRA shows a milestone as complete but MS Project shows it as in progress), the system must flag the conflict for PMO resolution before generating the report. | Silently choosing one source over another produces a report the PMO cannot stand behind. Conflicts must be surfaced so the PMO can determine which is correct. |
| BR-SR-14 | The system must not generate a report where unresolved data conflicts exist in fields that affect RAG status or financial health indicators. | A conflict in a minor field may be acceptable to proceed with. A conflict in schedule status or budget figures directly affects the report's accuracy and cannot be glossed over. |
| BR-SR-15 | The system must log all detected conflicts and their resolutions, including which source was used and who made the decision. | The reconciliation decision is an editorial judgment. Logging it creates an audit trail and allows future review of how conflicts were handled. |

---

## 5. Narrative Generation

| # | Requirement | Why |
|---|---|---|
| BR-SR-16 | The system must generate a narrative summary for each project explaining what the data means — not just restating the numbers. | A table of RAG statuses tells stakeholders what has happened. A narrative tells them why it matters and what is being done about it. PMOs currently spend the most time writing this part. |
| BR-SR-17 | Narrative generation must incorporate relevant RAID items, decisions, and risks from Wave 1 Meeting Intelligence outputs where available. | The narrative is more accurate and contextually richer when it draws on what was actually discussed in meetings — not just what the project data shows. A risk raised in a meeting last week is relevant context for a report generated this week. |
| BR-SR-18 | The narrative must be produced as a draft for PMO review — it must not be distributed without explicit PMO approval. | The narrative represents the PMO's professional assessment. The AI drafts it; the PMO owns it. Distribution without review could result in inaccurate or inappropriate statements reaching senior stakeholders. |
| BR-SR-19 | Where a project has no significant developments to report, the system must indicate this explicitly rather than generating filler content. | A narrative that says nothing meaningful wastes the reader's time and devalues the report. "No material change this period" is a valid and useful statement. |

---

## 6. Audience-Adapted Output

| # | Requirement | Why |
|---|---|---|
| BR-SR-20 | The system must generate separate report versions for at least three audience levels: Board/Executive (concise), Steering Group (detailed), and Project Team (action-focused). | Different audiences need different levels of detail. Currently PMOs manually create multiple versions of the same report, which is time-consuming and introduces inconsistency. |
| BR-SR-21 | All audience versions must be derived from the same single data pull — no separate manual versions. | Manual versioning introduces the risk of inconsistency: the executive report says one thing, the steering group pack says another. A single data source guarantees all versions are consistent. |
| BR-SR-22 | The level of detail, tone, and format for each audience version must be configurable per client. | Different clients have different reporting conventions and stakeholder preferences. Rigid templates will not meet the needs of every client. |
| BR-SR-23 | Each audience version must be independently approvable — the PMO must be able to approve the executive summary without approving the team update, and vice versa. | Different audience versions may go to different approvers. Bundling approval for all versions together creates bottlenecks if one version needs more work than others. |

---

## 7. Approval & Distribution

| # | Requirement | Why |
|---|---|---|
| BR-SR-24 | The system must present all report versions to the PMO for review before any distribution action is available. | Reports sent to senior stakeholders represent the organisation. A human must verify accuracy and appropriateness before they go out. |
| BR-SR-25 | The system must never distribute a report without explicit PMO approval. | Automated distribution of an incorrect or premature report could seriously damage client relationships or misrepresent project status to leadership. |
| BR-SR-26 | Once approved, the system must distribute each report version to the correct recipient list automatically. | Distribution is purely mechanical once the report is approved — it should not require manual effort from the PMO. |
| BR-SR-27 | The approving PMO user, timestamp, and report version must be logged for every distribution event. | Creates an audit trail of who approved what was sent to whom and when — important for governance and for resolving any subsequent disputes about what was reported. |

---

## 8. Integrations

| # | Requirement | Why |
|---|---|---|
| BR-SR-28 | The system must integrate with JIRA via REST API to retrieve ticket status, milestone completion, and project health metrics. | JIRA is the primary project tracking system. Direct API integration ensures data is current and removes the manual export step. |
| BR-SR-29 | The system must integrate with SharePoint via the Microsoft Graph API to retrieve RAID log entries, project documentation, and list data. | RAID log data and project documents live in SharePoint. Incorporating them into the report narrative requires API access. |
| BR-SR-30 | The system must integrate with MS Project via the Microsoft Graph API to retrieve schedule data, milestone status, and resource allocation. | MS Project holds the plan. Schedule and milestone data from MS Project is essential for RAG calculation and progress reporting. |
| BR-SR-31 | The system must consume Wave 1 (Meeting Intelligence) outputs — specifically RAID items, decisions, and meeting summaries — as inputs to narrative generation. | Meeting intelligence is the richest source of context for explaining what is happening on a project. Without it, the narrative is limited to what the structured data shows. |
| BR-SR-32 | The system must integrate with Outlook via the Microsoft Graph API to distribute approved reports to defined recipient lists. | Automated distribution via Outlook eliminates the manual step of copying approved content into emails and sending to the right people. |
| BR-SR-33 | All integrations must use OAuth 2.0 authentication. | Consistent with Wave 1 security standards and required by the Microsoft Graph and Jira APIs. |

---

## 9. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-SR-34 | Time from scheduled data pull to draft report available for PMO review | ≤ 60 minutes | PMOs need time to review and approve before the reporting deadline. A one-hour generation window allows same-day turnaround for most reporting cycles. |
| BR-SR-35 | Narrative acceptance rate (PMO approves without material changes) | ≥ 75% | If the PMO rewrites most narratives, the AI is not saving time. 75% is a meaningful quality floor — below this, the tool creates more work, not less. |
| BR-SR-36 | Data collection success rate (all configured sources retrieved without error) | ≥ 99% | Frequent data collection failures would require manual fallback and undermine trust in automated reporting. |
| BR-SR-37 | RAG status accuracy (AI-calculated RAG matches PMO judgment) | ≥ 90% | If the AI frequently calculates the wrong RAG, the PMO must review every project individually — eliminating the time saving. |
| BR-SR-38 | Distribution success rate (approved reports delivered to all recipients) | ≥ 99.5% | A missed distribution is a governance failure. Reports not received by stakeholders undermine the entire reporting process. |

---

## 10. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-SR-39 | Zero reports must be distributed without PMO approval. | Reports to senior stakeholders carry reputational and governance weight. Autonomous distribution is not acceptable under any circumstances. |
| BR-SR-40 | Financial data (budget, actuals, variance) must be masked in all debug, trace, and audit logs. | Financial data is commercially sensitive and may be subject to confidentiality obligations. Exposure in logs creates security and contractual risk. |
| BR-SR-41 | RAG thresholds and calculation criteria may only be changed with PMO Lead approval before deployment. | These directly determine how projects are characterised to senior stakeholders. Unauthorised changes could systematically misrepresent portfolio health. |
| BR-SR-42 | Recipient lists for each report audience must be defined and approved by the PMO Lead before the first distribution cycle. | Sending a detailed project report to the wrong audience is a data protection and governance risk. Recipient lists must be explicitly authorised, not inferred. |
| BR-SR-43 | The system must maintain a full record of every report generated, including the data snapshot used, the approved narrative, the approving user, and the distribution list. | Provides the evidence trail needed if a report is ever challenged, a project status is disputed, or an audit requires evidence of what was reported and when. |

---

## 11. Out of Scope (Wave 2 — Status Reports)

| Item | Status |
|---|---|
| Real-time dashboards or live data feeds | Out of scope — scheduled reporting is sufficient for Wave 2 |
| Predictive forecasting or trend modelling beyond burn rate | Wave 3 (Proactive Risk Monitoring) |
| Automated escalation based on RAG status | Wave 3 (Governance Monitoring) |
| Financial reconciliation across billing systems | Out of scope — finance systems integration is a separate workstream |

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-SR-01 | What RAG criteria and thresholds are used per client? | Cannot calculate RAG status without defined criteria |
| OI-SR-02 | What are the report formats and templates currently in use? | Audience-adapted output must match existing conventions |
| OI-SR-03 | Who receives each report audience version at each client? | Cannot configure distribution without approved recipient lists |
| OI-SR-04 | Is MS Project the scheduling tool used, or does the client use an alternative (e.g. Smartsheet, Primavera)? | Integration scope depends on the scheduling tool in use |
| OI-SR-05 | What is the current reporting cycle frequency (weekly, fortnightly, monthly)? | Determines the scheduled trigger for automated data collection |
| OI-SR-06 | Does the client have existing Power BI dashboards? If so, should the tool write to them or replace them? | Integration or replacement approach affects build scope significantly |

---

*Version: v0.1 | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1.md*
