# PMO AI Tool — Business Requirements: Strategic Resourcing (Wave 2)

**Scope:** Strategic Resourcing
**Version:** v0.1 — draft for review
**Status:** Pending stakeholder validation
**Depends on:** Wave 1 (Meeting Intelligence) outputs — resource-related decisions and RAID items from meetings provide context for resourcing recommendations

> This document covers Wave 2 requirements for the Strategic Resourcing workstream only. See `pmo-ai-business-requirements-v1.md` for Wave 1 (Meeting Intelligence).

---

## 1. Resource Tracking

| # | Requirement | Why |
|---|---|---|
| BR-RS-01 | The system must monitor project end dates for all tracked resources and generate proactive alerts when a resource is projected to become available within a configurable lead time (default: 4–6 weeks). | The core problem is that gaps are identified too late. A 4–6 week lead time gives the PMO enough runway to find a suitable replacement before the gap becomes a crisis. |
| BR-RS-02 | The system must track changes to resource availability — including early project completions, extensions, unplanned absences, and departures — and update gap projections accordingly. | Availability changes constantly. A static view of resource end dates will be wrong within days. Only continuous monitoring keeps the picture current. |
| BR-RS-03 | The system must distinguish between confirmed gaps (resource is definitely leaving a project) and potential gaps (project may end early or resource may be reallocated) and communicate this distinction clearly in alerts. | Acting on a potential gap with the same urgency as a confirmed one wastes time. PMOs need to know how certain an alert is before deciding how to respond. |
| BR-RS-04 | Resource tracking data must be sourced from the authoritative system of record (SharePoint resource tracker, MS Project, or HR system) — not maintained manually within the tool. | A separate resource database that diverges from the system of record creates confusion. The tool must read from wherever the organisation already manages resource data. |

---

## 2. Skills Inventory

| # | Requirement | Why |
|---|---|---|
| BR-RS-05 | The system must maintain a queryable skills and experience record for each tracked resource, including: skill areas, seniority level, sector experience, certifications, and prior project history. | Identifying who is available is trivial. Recommending the right person requires knowing what they can do. The skills inventory is what makes the matching step meaningful. |
| BR-RS-06 | The skills taxonomy (skill categories and labels) must be configurable per client organisation. | Different clients categorise skills differently. A fixed taxonomy will either be too generic to be useful or will use labels that don't map to the client's actual roles and capabilities. |
| BR-RS-07 | The system must flag skills records that have not been updated within a configurable period (default: 90 days) as potentially stale, and prompt the relevant resource or PMO to review them. | An outdated skills record is worse than no record — it produces incorrect recommendations. Regular refresh prompts keep the inventory accurate. |
| BR-RS-08 | PMOs must be able to update skills records directly within the tool. Updates must be logged with the updating user and timestamp. | Skills data changes as people complete projects, gain certifications, or develop in their roles. The PMO must be able to maintain accuracy without relying on a separate admin process. |

---

## 3. Gap Detection

| # | Requirement | Why |
|---|---|---|
| BR-RS-09 | The system must proactively identify upcoming resourcing gaps at the project level — not wait for a gap to occur before alerting. | Reactive gap management is the current state and the source of the problem. The value of the tool is in making gap detection proactive, not slightly faster after the fact. |
| BR-RS-10 | Gap detection must cross-reference upcoming resource availability against the confirmed project demand pipeline to identify where supply does not meet demand. | A resource becoming available is only a gap problem if there is an open demand that needs filling. Alerting on availability without checking against demand produces false alarms. |
| BR-RS-11 | Where multiple gaps are detected simultaneously, the system must prioritise them by project criticality and gap lead time, surfacing the most urgent first. | PMOs cannot act on all gaps at once. A gap on a critical client-facing programme with two weeks' lead time must take priority over a gap on a low-priority internal project with six weeks' notice. |
| BR-RS-12 | Gap alerts must include: the affected project, the role required, the lead time available, and the confidence level of the gap projection. | An alert without context is not actionable. The PMO needs to understand what kind of resource is needed, and how certain the gap is, before they can act on it. |
| BR-RS-13 | The system must incorporate resource-related RAID items and decisions from Wave 1 Meeting Intelligence as additional context for gap detection. | If a meeting last week produced a decision to extend a project, or a risk was raised about a key resource departing, that context is directly relevant to resourcing projections. |

---

## 4. Match Recommendation

| # | Requirement | Why |
|---|---|---|
| BR-RS-14 | For each identified gap, the system must recommend one or more candidate resources, ranked by fit. | The gap alert tells the PMO there is a problem. The recommendation gives them a starting point for solving it — reducing the research burden significantly. |
| BR-RS-15 | Each recommendation must include a clear explanation of the trade-offs — for example: "Candidate A is the best skill match but is not available for three weeks. Candidate B is available immediately but is a stretch for the seniority required." | A recommendation without reasoning is not useful. The PMO needs to understand why a candidate is recommended and what the compromises are before making a decision. |
| BR-RS-16 | The matching algorithm must consider the following factors: availability date, skill match, seniority level, relevant sector experience, project priority, and any expressed preferences from the project or programme director. | Single-factor matching (e.g. availability only) produces poor recommendations. The value of AI matching is its ability to weigh multiple factors simultaneously and surface the best overall fit. |
| BR-RS-17 | The system must present at least two candidate options per gap where available, to give the PMO a genuine choice rather than a single recommendation to rubber-stamp. | One recommendation is a forced decision. Two or more options surface the trade-offs and give the PMO agency in the final decision. |
| BR-RS-18 | Where no suitable match exists within the current resource pool, the system must clearly indicate this and suggest what type of external hire or contractor engagement may be required. | Knowing there is no internal fit is actionable information. The PMO can then engage with recruitment or contracting early, rather than discovering the gap has no internal solution at the last minute. |

---

## 5. Resource Commitment

| # | Requirement | Why |
|---|---|---|
| BR-RS-19 | The system must never confirm, communicate, or record a resource assignment without explicit PMO authorisation. Resource commitment is a human-only decision with no exceptions. | Moving a person to a new project has HR, contractual, relationship, and commercial implications. No AI should make or communicate this decision. The tool supports the decision — it does not make it. |
| BR-RS-20 | Once a PMO has confirmed a resource assignment, the system must update the resource tracker and project record to reflect the new allocation. | The confirmation should flow back into the system of record automatically — avoiding the manual update step that often leads to data being out of date. |
| BR-RS-21 | The system must log every resource assignment decision, including: the gap identified, the recommendation presented, the PMO who confirmed the assignment, and the timestamp. | Creates an audit trail of resourcing decisions that can be reviewed if an assignment is later questioned or disputed. |

---

## 6. Integrations

| # | Requirement | Why |
|---|---|---|
| BR-RS-22 | The system must integrate with the client's SharePoint resource tracker and/or MS Project via the Microsoft Graph API to read resource records, project allocations, and end dates. | Resource data lives in these systems. Reading directly from them ensures the tool is working from the same source of truth as the PMO. |
| BR-RS-23 | The system must integrate with the HR system where an API is available, to read availability, role profiles, and skills data. | HR systems often hold the most authoritative record of a person's skills and availability. Where an API exists, this is the preferred data source. |
| BR-RS-24 | The system must consume resource-related outputs from Wave 1 Meeting Intelligence — specifically RAID items, decisions, and action items referencing resourcing. | Meeting outputs provide context that structured data alone cannot — for example, a verbal commitment to keep a resource on a project, or a risk raised about a key person leaving. |
| BR-RS-25 | All integrations must use OAuth 2.0 authentication. | Consistent with Wave 1 security standards. Resource and HR data is sensitive and must be accessed through properly permissioned, auditable channels. |

---

## 7. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-RS-26 | Gap detection lead time (average weeks of notice before a gap occurs) | ≥ 4 weeks | Four weeks is the minimum needed for a realistic chance of finding and confirming a replacement. Less than this and the proactive detection value is lost. |
| BR-RS-27 | Match recommendation acceptance rate (PMO proceeds with one of the recommended candidates) | ≥ 70% | If the PMO ignores most recommendations and finds their own candidates, the tool is not adding value to the matching step. |
| BR-RS-28 | Skills inventory completeness (proportion of tracked resources with a current, non-stale record) | ≥ 90% | Below this threshold, the matching algorithm is working with incomplete information and recommendations will be unreliable. |
| BR-RS-29 | Alert false positive rate (gaps flagged that do not materialise) | ≤ 15% | Frequent false alarms desensitise PMOs to alerts. The gap detection must be reliable enough that alerts are taken seriously. |

---

## 8. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-RS-30 | Resource assignments must always be human-confirmed — zero exceptions. The system must enforce this at the workflow level, not rely on user discipline. | This is the highest-stakes decision in the resourcing workflow. It must be architecturally impossible for an assignment to be recorded or communicated without a human having explicitly authorised it. |
| BR-RS-31 | Skills data and availability data is personal information relating to identified individuals. PII protections (masking, access controls, retention limits) apply to all such data in system logs and records. | HR and skills data about named individuals is subject to GDPR and equivalent data protection regulations. Mishandling it creates legal and regulatory exposure. |
| BR-RS-32 | Access to the full resource pool data (skills, availability, project history) must be role-gated — not all users of the platform need or should have access to all resource information. | Resource data includes personal information and commercially sensitive capability details. Broad access increases the risk of misuse or inadvertent disclosure. |
| BR-RS-33 | Changes to the matching algorithm criteria or weighting must require PMO Lead approval before deployment. | The matching criteria determine who gets recommended for roles. Unauthorised changes could introduce bias, favour certain individuals, or produce systematically poor recommendations. |

---

## 9. Out of Scope (Wave 2 — Strategic Resourcing)

| Item | Status |
|---|---|
| External recruitment or contractor sourcing | Out of scope — the tool identifies the need but does not manage the recruitment process |
| Automated resource booking or calendar management | Out of scope — assignment confirmation is human-only |
| Skills gap training recommendations | Wave 3 consideration |
| Predictive demand forecasting beyond confirmed pipeline | Wave 3 (Proactive Risk Monitoring) |

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-RS-01 | Where is the authoritative resource record held — SharePoint, MS Project, HR system, or a combination? | Determines the primary data source for resource tracking and skills inventory |
| OI-RS-02 | Is there an HR system with an available API? If so, which system? | Determines whether HR integration is feasible or whether skills data must be maintained manually |
| OI-RS-03 | What is the standard alert lead time used today when flagging resource gaps? | Calibrates the default alert threshold to match existing PMO practice |
| OI-RS-04 | Who has authority to confirm a resource assignment at each client? | Determines the approval routing for resource commitments |
| OI-RS-05 | What skills taxonomy is used — is there an existing role/skills framework, or does one need to be defined? | Cannot build a meaningful skills inventory without an agreed taxonomy |
| OI-RS-06 | Is resource data currently consistent and up to date, or is there a known data quality problem? | Data quality is a prerequisite for reliable gap detection and matching. If the data is poor, a data remediation workstream may be needed before this capability can be built. |

---

*Version: v0.1 | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1.md*
