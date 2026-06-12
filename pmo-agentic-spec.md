# PMO AI Platform — Problem Statement & Success Metrics

---

## 1. Operational Context

Financial services PMOs managing multi-project portfolios spend the majority of their working time on coordination, recording, and reporting tasks that are repetitive, judgment-intensive, and performed manually across fragmented systems. The current operational state is:

- **80 meetings per PMO per month** require follow-up. Each follow-up takes 20–30 minutes of manual work: re-reading notes, classifying items into RAID categories, updating SharePoint RAID logs, updating JIRA tickets, and writing meeting notes for distribution.
- **50 status reports per PMO per month** each take 45 minutes to produce: manually collecting data from JIRA, SharePoint, and MS Project; reconciling inconsistencies; calculating RAG scores; writing narratives; and producing separate versions for different audiences.
- **Governance reviews** are conducted manually, periodically, and inconsistently across projects. Gaps are discovered in audits or steering committee sessions rather than in advance.
- **Stakeholder communications** — escalation notices, steering committee packs, milestone slip notifications — are written from scratch under time pressure with no standard trigger mechanism and no access to assembled project context at the moment of writing.
- **Change impact assessments** are assembled manually by cross-referencing the project plan, RAID log, and financial position — a process taking 30–60 minutes per change request.

There is no single system connecting meeting output to governance records to reporting to communications. Work is duplicated across Outlook, Teams, SharePoint, JIRA, and Excel with no structured handoff between them.

---

## 2. Problem from the PMO's Perspective

A PMO analyst managing three concurrent projects across an 80-meeting-per-month workload spends an estimated 40 hours per month on meeting follow-up alone (80 meetings × 30 minutes average). A further 37.5 hours per month are spent on status report production (50 reports × 45 minutes). This is 77.5 hours per month — nearly two full working weeks — on coordination and synthesis work before any active project management, stakeholder engagement, or escalation judgment has occurred.

The specific friction points are:

- RAID items raised in meetings are not consistently captured. Risks discussed verbally are not logged. Decisions are disputed post-meeting because no governed record exists.
- JIRA tickets are updated manually after meetings — or not updated at all. PMOs spend time chasing project managers for updates that should have been recorded at the point of discussion.
- Meeting notes are written separately from RAID updates and JIRA updates, creating three separate manual tasks for one meeting.
- Status reports are written multiple times for different audiences from the same underlying data. A project that is Red RAG for schedule but Green for budget requires the PMO to construct that nuance manually for each audience version.
- Governance gaps — missing approvals, overdue reviews, absent documentation — are discovered when they cause problems rather than when they can still be resolved.
- When a project moves to Red RAG or a risk escalates, the PMO must draft an escalation notice from scratch while simultaneously managing the escalation itself.

---

## 3. Problem from the Business's Perspective

At a loaded cost rate of $75 per hour:

| Task | Current time/month per PMO | Annual cost per PMO |
|---|---|---|
| Meeting follow-up | 40 hrs (80 mtgs × 30 min) | $36,000 |
| Status reporting | 37.5 hrs (50 reports × 45 min) | $33,750 |
| Change impact assessment | Variable — est. 5 hrs | $4,500 |
| Stakeholder communications drafting | Variable — est. 5 hrs | $4,500 |
| **Total** | **~87.5 hrs/month** | **~$78,750** |

A 50% reduction in the time spent on these tasks — a conservative target — produces $39,375 in annual savings per PMO. Across a portfolio PMO function of 10 PMOs, this is $393,750 annually.

Beyond direct cost, the business risks are:

- **Governance risk:** Inconsistent RAID log maintenance and governance review creates audit exposure. A single missed risk that escalates to a project failure at a tier-1 financial services client carries a cost that dwarfs the entire year's efficiency saving.
- **Client relationship risk:** Delayed, inconsistent, or inaccurate stakeholder communications damage client trust. Communications written under pressure without assembled context are more likely to contain errors or omissions.
- **Knowledge loss:** When a PMO rotates off a project, RAID history, decision records, and project context leave with them. No structured capture mechanism exists.
- **Scalability:** The current model scales linearly with headcount. Adding one project adds proportional administrative overhead. An AI-assisted model breaks this linear relationship.

---

## 4. Investment Justification

The platform addresses the highest-volume, highest-frequency PMO tasks with the lowest ambiguity in the automation candidate set. Meeting follow-up, status reporting, and governance monitoring are performed at known cadences with known inputs. The judgment-intensive components — RAID classification, narrative authoring, escalation decisions — are supported rather than replaced, preserving accountability while eliminating the surrounding coordination burden.

The quantifiable Wave 1–2 annual saving per PMO is **$54,750**, derived as follows:

| Workstream | Estimated Annual Saving |
|---|---|
| Meeting Intelligence (Wave 1) | ~$18,000 |
| Status Reports (Wave 2) | ~$26,250 |
| Stakeholder Communications (Wave 2) | ~$4,500 |
| Change Request Management (Wave 2) | ~$6,000 |
| **Total** | **~$54,750** |

---

## 5. Success Metrics

### Primary Metrics (Wave 1 — Meeting Intelligence)

| Metric | Baseline | Target | Measurement Method |
|---|---|---|---|
| RAID item capture rate | Unknown — items are lost and not counted | ≥ 95% of items discussed in meetings are proposed for logging | Spot-check audit of processed transcripts vs manually reviewed transcripts on 10% sample |
| R/A/I/D classification accuracy | N/A — manual, inconsistent | ≥ 85% correct on first proposal | Human review of accepted/rejected/modified proposals; classification error rate logged per item |
| Owner assignment accuracy | N/A | ≥ 90% correct on first proposal | Audit log of owner changes made by PMO at review time |
| RAID proposal acceptance rate | N/A | ≥ 80% accepted without modification | Approval workflow log — accepted vs modified vs rejected |
| Time from transcript upload to draft available | 20–30 min manual | ≤ 30 minutes | Platform processing timestamp log |
| Meeting notes review and send time | 20–30 min manual | ≤ 5 minutes PMO review time | Session log from approval interface |

### Primary Metrics (Wave 2 — Status Reports)

| Metric | Baseline | Target | Measurement Method |
|---|---|---|---|
| Report production time | 45 min per report | ≤ 10 min PMO review time | Session log from report approval interface |
| RAG status accuracy | Manual, inconsistent | ≥ 90% match to PMO judgment on review | Audit of PMO overrides to AI-calculated RAG |
| Narrative acceptance rate | N/A | ≥ 75% approved without material changes | Approval workflow log — accepted vs materially edited |
| Data collection success rate | Manual, error-prone | ≥ 99% automated collections complete without error | API call success log |

### Primary Metrics (Wave 2 — Governance, Comms, Change Requests)

| Metric | Baseline | Target | Measurement Method |
|---|---|---|---|
| Governance gap detection lead time | Gaps found at audit | 100% of active projects assessed weekly; high-severity gaps flagged within 2 hours of assessment | Assessment run log and gap creation timestamp |
| False positive rate (gaps) | N/A | ≤ 10% of flagged gaps dismissed by PMO as non-genuine | Gap dismissal log |
| Stakeholder comm trigger accuracy | N/A | ≥ 95% of genuine trigger events detected | Manual audit of RAG changes vs draft generation log |
| Change request assessment time | 30–60 min manual | ≤ 5 min PMO review time | Session log from CR approval interface |

### Governance Safety Metrics (Zero Tolerance)

| Metric | Target |
|---|---|
| RAID entries created without PMO approval | 0 |
| External communications sent without PMO approval | 0 |
| High-priority JIRA updates applied without PMO confirmation | 0 |
| RAID items without source traceability to transcript | 0 |

### Leading Indicators

- RAID proposal acceptance rate trending upward week-on-week in weeks 2–8 (indicates model calibrating to client taxonomy)
- PMO session time in the review interface decreasing in weeks 4–8 (indicates trust building and review becoming more efficient)
- Number of governance gaps dismissed as non-genuine trending downward (indicates false positive rate improving)

### Lagging Indicators

- Reduction in missed RAID items identified through retrospective audit at 90 days
- Reduction in disputed decisions at steering committee (qualitative, gathered via PMO feedback at 90 days)
- Governance audit findings at next scheduled audit cycle


---

# PMO AI Platform — Delegation Analysis

---

## Classification Key

| Level | Definition |
|---|---|
| **FA** — Fully Agentic | Agent executes with no human review required. Output is deterministic, low-stakes, or trivially reversible. |
| **AO** — Agent-Led, Human Oversight | Agent executes; human reviews on exception (confidence below threshold, escalation trigger, or anomaly). |
| **HS** — Human-Led, Agent Support | Human decides; agent assembles context, drafts proposals, or flags options. Human can reject without consequence. |
| **HO** — Human Only | No agent action permitted. Human decides and executes. Violation = governance breach. |

---

## Stream 1: Meeting Intelligence

| # | Task | Level | Justification |
|---|---|---|---|
| 1.1 | Transcript ingestion and preprocessing | FA | Deterministic parsing. No judgment involved. Failure is detectable (empty output, parse error). Risk of incorrect ingestion is caught at the next human-review step. |
| 1.2 | Speaker identification and labelling | FA | Pattern-matching against known participant names from project context. Errors are visible to the PMO at review and do not propagate without approval. |
| 1.3 | Meeting summary generation | AO | Synthesis requires judgment about what is significant. Confidence scoring applied; summaries with aggregated confidence below 0.75 are flagged. Output does not write to any system — it is a draft for review. |
| 1.4 | Action (A) extraction | AO | Actions are the most syntactically explicit RAID type ("will do", "can you", "I'll send"). Extractable with high confidence in most cases. Flag items below 0.80 confidence; otherwise queue for PMO review in standard flow. Cost of a missed action is high; cost of a false positive is low (PMO rejects in review). |
| 1.5 | Risk (R) extraction | HS | Risk language is ambiguous and context-dependent. The same statement ("we might miss the deadline") can be a Risk, an Issue, or neither depending on project phase and speaker. Agent surfaces candidates with evidence; human classifies. Misclassifying a Risk as an Action results in no mitigation planning — a governance failure. |
| 1.6 | Issue (I) extraction | HS | Issues require distinguishing current problems from historical references and hypotheticals. Severity assessment requires business context the agent does not hold. Agent surfaces candidates; human classifies and sets severity. |
| 1.7 | Decision (D) extraction | HS | Decisions are governance-critical records. Incorrectly logging a discussion point as a Decision creates a false record that can be cited in dispute resolution or audit. All Decision candidates must be confirmed by human. |
| 1.8 | RAID item classification (R/A/I/D assignment) | HS | Classification errors have downstream governance consequences. Even where agent confidence is high, the PMO must confirm the type before any entry is created. Agent proposes; human confirms. |
| 1.9 | Owner assignment | AO | Owners are usually explicit in meeting language. Agent assigns based on transcript evidence; flags "someone should" constructions and external owners for human confirmation. Owner errors result in actions not being completed — high consequence, but detectable at the next review. |
| 1.10 | Due date inference | AO | Converting "by end of week" to a specific date is deterministic given the meeting date. Agent infers and flags all inferred dates for PMO confirmation; explicit dates pass without flagging. |
| 1.11 | JIRA ticket matching | AO | Ticket matching uses project context, keyword analysis, and explicit ticket references. Confidence below 0.80 is flagged; agent never creates new JIRA tickets without PMO confirmation; agent never changes ticket status without PMO confirmation. |
| 1.12 | Meeting notes draft generation | HS | Notes are distributed externally and represent the organisation's formal record. Agent produces the first draft; PMO reviews and approves before distribution. PMO edits are expected and normal. |
| 1.13 | Distribution list confirmation | AO | Standing lists are pre-configured per meeting series. Agent pre-populates; PMO confirms or edits before send. Agent never sends without the explicit send action from PMO. |
| 1.14 | Meeting notes distribution | HO | External communication. No autonomous sending permitted. PMO must click send after reviewing both the content and the recipient list. Violation = unauthorised external communication. |
| 1.15 | RAID log entry creation | HO | RAID log is a formal governance artifact. All entries require explicit PMO approval. The agent proposes the entry in the correct schema; the PMO approves, modifies, or rejects. Zero exceptions. |
| 1.16 | JIRA ticket update application | HO (high-priority) / AO (low-priority) | High-priority tickets (Priority: Highest/High or labelled executive-visible) require explicit PMO confirmation before any update. Low-priority ticket comments may be applied after PMO batch review. |

**Boundary justification for 1.15:** The RAID log is referenced in audit, escalation, and dispute resolution. An agent-created entry that turns out to be incorrect cannot be quietly corrected — it is a governance record. The cost of requiring human approval (30 seconds per item) is negligible against the cost of a contested or incorrect entry. This boundary is architectural, not aspirational.

**Boundary justification for 1.7 (Decisions):** "Let's go with vendor A" may be a firm decision or the opening of a negotiation depending on who said it, in what context, and whether it was challenged. The agent cannot reliably determine this from transcript text alone. All Decision candidates are flagged for confirmation regardless of confidence score.

---

## Stream 2: Status Reports & Scorecards

| # | Task | Level | Justification |
|---|---|---|---|
| 2.1 | Data collection from JIRA, SharePoint, MS Project | FA | API calls with defined schemas. Success/failure is binary. Failed collections queue for retry and alert PMO. No judgment involved. |
| 2.2 | Milestone health monitoring (continuous) | FA (detection) / AO (notification) | Detecting that a milestone is overdue or within 14 days with no completion signal is a rule-based computation. Notifying the PMO of the condition is an automated action. The PMO's response to the notification is human-led. |
| 2.3 | Financial analysis — variance calculation | FA | Budget vs actuals, burn rate, variance percentage are arithmetic calculations applied to retrieved data. The numbers are deterministic; their interpretation is not. |
| 2.4 | Financial trend interpretation | AO | "Spend is decelerating" is deterministic. "This deceleration is a risk to delivery" requires project context. Agent applies configured thresholds (e.g. forecast overrun >10% of remaining budget = flag); PMO reviews flagged interpretations. |
| 2.5 | RAG score calculation | FA (calculation) / HO (final status) | RAG calculation against configured criteria is deterministic. PMO must be able to override the calculated status before distribution. A calculated Red that the PMO has context to explain as Amber cannot be sent without the PMO making that judgment. Distribution is blocked until PMO either confirms or overrides. |
| 2.6 | Cross-source data reconciliation | AO | Detecting conflicts between JIRA and MS Project milestone status is deterministic. Resolving which is correct is a PMO judgment. Agent flags all conflicts in RAG-affecting fields; report generation is blocked until PMO resolves. |
| 2.7 | Narrative generation | HS | The status report narrative is the PMO's professional assessment. Agent generates the first draft, informed by RAID items from Wave 1; PMO rewrites, edits, or approves. Agent draft is explicitly labelled as draft. |
| 2.8 | Audience-adapted output generation | HS | Tone and detail level selection requires understanding of recipient seniority and preferences. Agent applies configured templates per audience type; PMO reviews each version independently before approval. |
| 2.9 | Report distribution | HO | Report is an external communication sent to clients and senior stakeholders. PMO must approve each audience version independently. Agent distributes only after explicit per-version approval. |

**Boundary justification for 2.5 (RAG override):** The RAG status on a report sent to a programme director is a statement of record. If the agent calculates Red and the PMO knows the issue was resolved this morning, an automated Red report reaching the programme director before the PMO can intervene is a serious client relationship failure. The override mechanism is not a convenience feature — it is a governance requirement.

---

## Stream 3: Governance Monitoring

| # | Task | Level | Justification |
|---|---|---|---|
| 3.1 | Governance assessment scheduling and execution | FA | Running configured checks against evidence sources on a weekly schedule is deterministic and automated. No judgment is involved in the scheduling or the evidence retrieval. |
| 3.2 | Gap detection — evidence matching | AO | Comparing retrieved evidence against defined governance standards is rule-based. A document exists or it does not. An approval is recorded or it is not. Where evidence cannot be retrieved, the gap is flagged as unresolvable rather than assumed compliant. |
| 3.3 | Gap severity classification | HS | Severity depends on the governance standard violated. Standards carry pre-configured severity levels (High/Medium/Low). Agent applies the configured severity; PMO may escalate or downgrade with a recorded reason. Downgrade without a reason is not permitted. |
| 3.4 | Scorecard generation | FA | Scorecard content is derived entirely from gap records and their statuses. No judgment is applied in scorecard generation itself. |
| 3.5 | Escalation draft (High severity gaps) | HS | Agent drafts the escalation notice for PMO review. Content must be traceable to the specific gap record. PMO edits and approves before any escalation is sent. |
| 3.6 | Escalation sending | HO | Governance escalations sent to sponsors or directors carry reputational and relationship consequences. No autonomous sending permitted. |
| 3.7 | Gap resolution tracking | FA | Updating gap status when PMO marks a gap as resolved, in progress, or dismissed is a state update triggered by explicit PMO action. Automated only after human initiates. |
| 3.8 | Gap dismissal without reason | HO | A PMO may not dismiss a governance gap without recording a reason. The platform must enforce this at the UI level — the dismiss action is not available until a reason field is completed. |

**Boundary justification for 3.2 (assumed compliant):** A governance check that returns no evidence must default to a gap, not a pass. Assuming compliance where evidence is absent is indistinguishable from a genuine governance failure and undermines the purpose of automated checking.

---

## Stream 4: Stakeholder Communications

| # | Task | Level | Justification |
|---|---|---|---|
| 4.1 | Trigger event detection | AO | RAG deterioration, milestone slip, new High-severity RAID item, and governance gap escalation are detectable from platform data. Agent monitors continuously; PMO reviews triggered drafts. False positives (triggers that don't require communication) are handled by PMO dismissal — low cost. |
| 4.2 | Context gathering | FA | Pulling relevant RAID items, RAG history, governance gap records, and JIRA data for a triggered event is an automated data assembly step. No judgment is applied. |
| 4.3 | Draft generation | HS | Communication content is the PMO's voice. Every factual statement must be source-traceable; agent flags uncertain statements. PMO reviews, edits, and approves before any send action is available. |
| 4.4 | Audience adaptation | HS | Adjusting tone for a sponsor vs a programme director requires understanding of relationship dynamics the agent does not hold. Agent applies configured templates; PMO reviews each version. |
| 4.5 | Communication sending | HO | All external communications require explicit PMO approval. No trigger event is severe enough to justify autonomous sending. This boundary is absolute. |
| 4.6 | Pending draft timeout reminder | AO | If a draft has been pending review for more than a configurable period (default: 4 hours for High-severity triggers; 24 hours for others), agent sends a reminder notification to the PMO via Teams. Agent does not escalate the communication autonomously. |

**Boundary justification for 4.5:** An autonomous escalation notice sent to a client director about a project problem that the PMO was already managing would damage the client relationship and create a false impression of the governance process. The risk of a missed communication is lower than the risk of an unsanctioned one.

---

## Stream 5: Change Request Management

| # | Task | Level | Justification |
|---|---|---|---|
| 5.1 | Change request trigger detection | AO | New CRs submitted via JIRA or SharePoint form are detectable by monitoring defined channels. Agent flags new CRs to PMO; does not act on them until PMO initiates impact assessment. |
| 5.2 | Impact data assembly | FA | Pulling the current project plan, open RAID items, financial position, and open actions is a data retrieval step. No judgment involved. |
| 5.3 | Impact assessment draft | HS | Determining whether a scope change creates schedule risk requires interpreting the plan's float, the RAID log's open risks, and the financial headroom. Agent produces a structured draft covering schedule, cost, and risk dimensions; PMO reviews, edits, and confirms before routing. |
| 5.4 | Approval routing | AO | Routing to the correct approver based on CR scale and type is rule-based if routing rules are configured. Agent applies rules and flags CRs that do not match any configured routing rule for PMO manual assignment. |
| 5.5 | CR status tracking | FA | Monitoring the approval workflow and detecting overdue approvals is automated. Agent sends reminder notifications to the PMO for approvals overdue by >1 business day. |
| 5.6 | RAID update proposal | HS | If the CR introduces new risks or issues, agent proposes RAID entries using the Wave 1 workflow. Same governance rules apply — all proposals require PMO approval. |
| 5.7 | Closure notification draft | HS | Agent drafts the closure communication once a CR is approved or rejected. PMO reviews and sends via the Stakeholder Communications workflow. |

---

## Delegation Summary

| Level | Count | % of total tasks |
|---|---|---|
| Fully Agentic (FA) | 10 | 30% |
| Agent-Led, Human Oversight (AO) | 12 | 36% |
| Human-Led, Agent Support (HS) | 9 | 27% |
| Human Only (HO) | 5 | 15% |

**Governance check:** 42% of tasks require direct human involvement (HS + HO). All tasks that produce external communications, create governance records, or apply irreversible changes to project systems are HS or HO. No FA task writes to an external system or produces an external communication.


---

# PMO AI Platform — Agent Specification

---

## Platform Architecture

The PMO AI Platform is an orchestrated multi-agent system. A central orchestrator receives inputs (transcript uploads, API-pulled data, scheduled triggers) and routes them to five specialist sub-agents. Each sub-agent produces proposals that flow into a unified PMO approval interface. No sub-agent writes to an external system or sends an external communication without an explicit PMO approval action recorded in the audit log.

The platform is an EPAM-built, browser-based web application hosted on Microsoft Azure. Client tools (SharePoint, JIRA, Outlook) are data integrations — the platform reads from and writes approved outputs to them. It does not run inside any client system.

---

---

## Entity Definitions

### Entity: RAID Entry

| Attribute | Type | Constraints | Notes |
|---|---|---|---|
| `entry_id` | UUID | Primary key, immutable, generated on creation | |
| `meeting_id` | UUID | Foreign key → Meeting, required; ON DELETE RESTRICT | Source meeting reference |
| `raid_type` | enum | [RISK, ACTION, ISSUE, DECISION], required | |
| `title` | string | Max 200 chars, required | Brief description |
| `description` | string | Max 2000 chars, required | Full details |
| `severity` | enum | [LOW, MEDIUM, HIGH, CRITICAL], required for RISK and ISSUE; null for ACTION and DECISION | |
| `status` | enum | [OPEN, IN_PROGRESS, CLOSED], required, default OPEN | |
| `owner_name` | string | Max 200 chars, required for ACTION; nullable for others | |
| `owner_email` | string | RFC 5322 format, nullable | |
| `due_date` | date | ISO 8601, required for ACTION; nullable for others | |
| `date_inferred` | boolean | Required, default false | True if due date was inferred from relative language |
| `decision_maker` | string | Max 200 chars, required for DECISION; null for others | |
| `source_quote` | string | Max 1000 chars, required | Verbatim text from transcript that triggered this item |
| `source_timestamp` | string | Max 20 chars, nullable | Position in transcript (e.g., "23:14") |
| `source_speaker` | string | Max 200 chars, nullable | Speaker name if identifiable |
| `confidence_score` | decimal | 0.00–1.00, required | Extraction confidence |
| `agent_proposed` | boolean | Required, immutable | True if proposed by agent; false if human-created |
| `pmo_decision` | enum | [APPROVED, MODIFIED, REJECTED], nullable | Set when PMO acts on proposal |
| `pmo_user_id` | UUID | Foreign key → User, nullable | PMO who approved/rejected |
| `created_at` | timestamp | ISO 8601 UTC, immutable | |
| `approved_at` | timestamp | ISO 8601 UTC, nullable | When PMO approved |
| `sharepoint_item_id` | string | Max 100 chars, nullable | ID of written SharePoint list item |
| `jira_ticket_key` | string | Max 20 chars, nullable | Associated JIRA ticket if any |

**State Machine — RAID Entry proposal lifecycle:**
```
PROPOSED → PMO_REVIEW → APPROVED → WRITTEN_TO_SHAREPOINT → CLOSED
                     → MODIFIED → APPROVED → WRITTEN_TO_SHAREPOINT → CLOSED
                     → REJECTED → CLOSED
```

**Constraints:**
- `pmo_decision` must not be set without `pmo_user_id`
- `sharepoint_item_id` must be null until `pmo_decision = APPROVED` and write succeeds
- Once `pmo_decision` is set, `raid_type`, `source_quote`, `confidence_score`, and `agent_proposed` are immutable
- `date_inferred = true` requires `due_date` to be set AND the original relative text to be stored in `description`

---

### Entity: Meeting Record

| Attribute | Type | Constraints | Notes |
|---|---|---|---|
| `meeting_id` | UUID | Primary key, immutable, generated on upload | |
| `project_id` | UUID | Foreign key → Project, required; ON DELETE RESTRICT | Selected by PMO at upload |
| `series_id` | UUID | Foreign key → MeetingSeries, nullable; ON DELETE SET NULL | If part of a recurring series |
| `transcript_filename` | string | Max 255 chars, required | Original filename |
| `transcript_format` | enum | [VTT, TXT, DOCX], required | |
| `transcript_word_count` | integer | ≥ 0, required | Calculated on ingest |
| `upload_mode` | enum | [MANUAL_UPLOAD, GRAPH_API], required | |
| `uploaded_by` | UUID | Foreign key → User, required, immutable | |
| `uploaded_at` | timestamp | ISO 8601 UTC, immutable | |
| `status` | enum | See state machine below, required | |
| `processing_started_at` | timestamp | ISO 8601 UTC, nullable | |
| `proposals_ready_at` | timestamp | ISO 8601 UTC, nullable | |
| `review_started_at` | timestamp | ISO 8601 UTC, nullable | |
| `approved_at` | timestamp | ISO 8601 UTC, nullable | |
| `distributed_at` | timestamp | ISO 8601 UTC, nullable | |
| `distribution_list_confirmed` | boolean | Required, default false | PMO must confirm before send |
| `notes_draft` | text | Max 50KB, nullable | Agent-generated meeting notes |
| `notes_approved_content` | text | Max 50KB, nullable | Final approved version |
| `processing_error` | string | Max 500 chars, nullable | Error message if processing failed |
| `created_at` | timestamp | ISO 8601 UTC, immutable | |
| `updated_at` | timestamp | ISO 8601 UTC | |

**State Machine — Meeting Record:**

```
UPLOADED → PROCESSING → PROPOSALS_READY → IN_REVIEW → PARTIALLY_APPROVED → APPROVED → DISTRIBUTED → CLOSED
                     → FAILED (terminal)
```

**Full Transition Table:**

| From | To | Trigger | Prerequisites |
|---|---|---|---|
| UPLOADED | PROCESSING | Agent begins extraction | transcript_word_count > 0 |
| PROCESSING | PROPOSALS_READY | Extraction complete | At least 0 proposals generated; processing_error IS NULL |
| PROCESSING | FAILED | Unrecoverable error | All retry attempts exhausted |
| PROPOSALS_READY | IN_REVIEW | PMO opens review interface | |
| IN_REVIEW | PARTIALLY_APPROVED | PMO acts on some items | ≥1 item approved or rejected; ≥1 item still pending |
| IN_REVIEW | APPROVED | PMO resolves all items | All proposals in [APPROVED, MODIFIED, REJECTED]; notes_approved_content IS NOT NULL; distribution_list_confirmed = true |
| PARTIALLY_APPROVED | APPROVED | PMO resolves remaining items | Same prerequisites as IN_REVIEW → APPROVED |
| APPROVED | DISTRIBUTED | Distribution executed | acknowledged_at IS NOT NULL; all approved RAID entries written |
| DISTRIBUTED | CLOSED | Audit record finalised | All write operations confirmed |
| Any | FAILED | Unrecoverable processing error | — |

**Constraints:**
- DISTRIBUTED state requires `distribution_list_confirmed = true` — enforced at API layer
- APPROVED state requires `notes_approved_content IS NOT NULL` — cannot approve without notes
- FAILED is terminal; no transition out of FAILED
- `notes_draft` is set only by the agent; `notes_approved_content` is set only on PMO approval

---

## Sub-Agent 1: Meeting Intelligence Agent

### Purpose
Transform a PMO-uploaded meeting transcript into: structured RAID proposals (R/A/I/D), JIRA update proposals, and a draft set of meeting notes — all presented for PMO review in a single interface session.

### Scope

**In scope:**
- Transcript ingestion from PMO manual upload (Teams .vtt, plain text, .docx)
- Speaker identification and labelling
- RAID item extraction with confidence scoring
- Due date normalisation
- JIRA ticket matching and update proposals
- Meeting notes draft generation (narrative + RAID action list)
- Distribution list pre-population from configured standing lists
- Audit logging of all proposals and PMO decisions

**Out of scope:**
- Real-time (in-meeting) processing
- Audio file transcription
- Automatic transcript retrieval (Graph API — optional enhancement, not required for operation)
- Automatic calendar invitee list retrieval (optional enhancement)
- Any write to RAID log or JIRA without PMO approval

### Users and Stakeholders
- **Primary user:** PMO Analyst — uploads transcript, reviews proposals, approves or rejects each item
- **Secondary stakeholder:** Meeting participants — receive approved meeting notes via Outlook
- **Audit stakeholder:** PMO Lead, Compliance — review audit log of all proposals and decisions

### Inputs

| Input | Source | Format | Required |
|---|---|---|---|
| Meeting transcript | PMO manual upload | .vtt, .txt, .docx | Required |
| Project context record | Platform project registry | JSON — project name, RAID log ID, JIRA project key, standing DL ID | Required |
| Existing RAID log entries | SharePoint via Graph API | List items | Required for duplicate detection |
| Existing JIRA tickets | JIRA via REST API | Issue objects | Required for ticket matching |
| Standing distribution list | Platform DL registry | List of email addresses | Required for notes distribution |

### Outputs

| Output | Destination | Approval Required |
|---|---|---|
| RAID item proposals (R/A/I/D, confidence score, source quote) | PMO review interface | Yes — per item |
| JIRA update proposals (match, comment, status change) | PMO review interface | Yes — per ticket |
| Meeting notes draft (narrative + RAID action list) | PMO review interface | Yes — before distribution |
| Confirmed distribution list | PMO review interface | Yes — PMO confirms or edits before send |
| Approved RAID entries | SharePoint RAID log | Automated after PMO approval |
| Approved JIRA updates | JIRA | Automated after PMO approval |
| Approved meeting notes | Outlook → recipients | Automated after PMO approval and DL confirmation |
| Full audit record | Platform audit log | Automated |

### Decision Logic

**Transcript processing:**
- IF speaker labels are present in the transcript THEN preserve them against each extracted item
- IF speaker labels are absent THEN extract items without owner assignment; flag all owner fields as unresolved for PMO assignment
- IF transcript word count is below 200 words THEN flag as potentially incomplete before processing; do not block processing

**RAID extraction:**
- IF extracted text contains action language ("will", "I'll", "can you", "to do", "action:") AND confidence ≥ 0.80 THEN classify as Action (A) and queue for standard PMO review
- IF extracted text contains action language AND confidence < 0.80 THEN classify as Action (A) candidate and escalate for PMO review with low-confidence flag
- IF extracted text contains risk language ("might", "could fail", "at risk", "concern", "worried") THEN classify as Risk (R) candidate and escalate as HS — PMO must confirm type
- IF extracted text contains issue language ("is blocked", "broken", "failing", "not working") THEN classify as Issue (I) candidate and escalate as HS — PMO must confirm type
- IF extracted text contains decision language ("agreed", "decided", "we'll go with", "confirmed") THEN classify as Decision (D) candidate — ALL D candidates escalate for PMO confirmation regardless of confidence score
- IF a single text segment contains language consistent with both R and I THEN flag as AMBIGUOUS_R_I escalation; present both options to PMO for selection
- IF owner is explicitly named in the transcript for an item THEN assign that person as proposed owner
- IF owner language is vague ("someone should", "the team will") THEN flag as AMBIGUOUS_OWNER; do not assign
- IF owner is not a meeting participant or referenced individual THEN flag as EXTERNAL_OWNER

**Due date normalisation:**
- IF transcript contains a relative date reference ("by end of week", "next sprint", "by Friday") THEN convert to an ISO 8601 date using the meeting date as reference; flag the inferred date with the original text
- IF transcript contains an explicit date THEN use it directly; do not flag

**JIRA matching:**
- IF an action item contains an explicit JIRA ticket reference (e.g. "AP-123") THEN match to that ticket directly; confidence = 1.0
- IF no explicit reference but keyword and project context match an existing open ticket with similarity score ≥ 0.80 THEN propose match; queue for PMO confirmation
- IF similarity score < 0.80 THEN propose new ticket creation; queue for PMO confirmation
- IF JIRA API is unavailable THEN queue all proposals; alert PMO; do not proceed with any JIRA action until API is restored

**Notes distribution:**
- IF standing distribution list exists for the meeting series THEN pre-populate; present to PMO for confirmation
- IF no standing list exists THEN present empty list; PMO must populate before send action is available
- IF PMO has not confirmed distribution list THEN send action is disabled regardless of notes approval status

### Escalation Triggers

| Code | Condition | Behaviour |
|---|---|---|
| LOW_CONFIDENCE | Any RAID item confidence < 0.80 | Flag item in review interface with confidence score and source quote; item cannot be auto-approved |
| AMBIGUOUS_R_I | Item consistent with both Risk and Issue | Present both options; require PMO to select type before item can proceed |
| DECISION_CANDIDATE | Any item with Decision language | Flag for mandatory PMO confirmation regardless of confidence score |
| AMBIGUOUS_OWNER | Owner language is vague or absent | Block owner field; PMO must assign manually |
| EXTERNAL_OWNER | Proposed owner not in meeting or project team | Flag; PMO must confirm or reassign |
| SENSITIVE_CONTENT | Item contains HR, legal, or financial PII | Flag item; mask in audit log; require explicit PMO confirmation before logging |
| LOW_TRANSCRIPT_QUALITY | >30% of extraction attempts return confidence < 0.60 | Alert PMO at upload time; recommend re-upload or manual note supplementation |

### Integration Contracts

#### SharePoint RAID Log (Microsoft Graph API)

**Auth:** OAuth 2.0, Azure AD delegated permissions: `Sites.ReadWrite.All`
**Credentials:** OAuth 2.0 client credentials stored in Azure Key Vault; secret name: `sharepoint-graph-client-secret`. Access token cached in memory; refreshed 60 seconds before expiry.
**Base URL:** `https://graph.microsoft.com/v1.0`
**Timeout:** 10 seconds per request
**Rate limit:** 600 requests per minute per app registration (Microsoft throttling). IF response HTTP 429 THEN retry after `Retry-After` header value (seconds).
**Retry logic:**
- HTTP 200: no retry
- HTTP 429: retry after `Retry-After` header; max 3 retries
- HTTP 500/503: exponential backoff 2s, 4s, 8s; max 3 retries
- HTTP 400/401/403: do not retry; log and alert PMO
- Timeout: retry once after 5 seconds; if still timeout, log and alert PMO
**Fallback:** If all retries exhausted → retain approved item in WRITE_PENDING queue; retry every 5 minutes for 1 hour; alert PMO after 3 consecutive failures

**Read existing entries (duplicate check):**
```
GET /sites/{siteId}/lists/{raidListId}/items?$filter=fields/SourceMeetingId eq '{meeting_id}'
Response 200:
{
  "value": [
    {
      "id": "string",
      "fields": {
        "Title": "string",
        "RaidType": "RISK|ACTION|ISSUE|DECISION",
        "SourceMeetingId": "string"
      }
    }
  ]
}
```

**Write approved RAID entry:**
```
POST /sites/{siteId}/lists/{raidListId}/items
Request body:
{
  "fields": {
    "Title": "string (max 200 chars, required)",
    "Description": "string (max 2000 chars, required)",
    "RaidType": "RISK|ACTION|ISSUE|DECISION (required)",
    "Severity": "LOW|MEDIUM|HIGH|CRITICAL (required for RISK/ISSUE; null otherwise)",
    "Status": "OPEN",
    "OwnerName": "string (required for ACTION)",
    "DueDate": "YYYY-MM-DD (required for ACTION)",
    "DateInferred": "true|false",
    "SourceQuote": "string (max 1000 chars)",
    "SourceMeetingId": "string (meeting_id)",
    "AgentProposed": "true",
    "ApprovedByUserId": "string (pmo_user_id)",
    "ConfidenceScore": "decimal 0.00-1.00"
  }
}
Response 201:
{ "id": "string (sharepoint_item_id)", "fields": { ... } }
Response 400:
{ "error": { "code": "string", "message": "string" } }
```

**Data mapping — internal RAID Entry → SharePoint fields:**
| Internal field | SharePoint column | Notes |
|---|---|---|
| `entry_id` | not stored | Platform-only ID |
| `meeting_id` | `SourceMeetingId` | String |
| `raid_type` | `RaidType` | Enum value |
| `title` | `Title` | Required |
| `description` | `Description` | Required |
| `severity` | `Severity` | Null for ACTION/DECISION |
| `owner_name` | `OwnerName` | |
| `due_date` | `DueDate` | ISO 8601 |
| `source_quote` | `SourceQuote` | |
| `pmo_user_id` | `ApprovedByUserId` | |
| `confidence_score` | `ConfidenceScore` | |

**Scope-out:** Exact SharePoint column internal names (not display names) must be confirmed per client before build. The mapping above uses assumed column names that must be validated.

---

#### JIRA REST API

**Auth:** OAuth 2.0 (preferred) or API Token in `Authorization: Bearer {token}` header. Credentials stored in Azure Key Vault; secret name: `jira-api-token-{client-id}`.
**Base URL:** `https://{org}.atlassian.net/rest/api/3`
**Timeout:** 8 seconds per request
**Rate limit:** 1000 requests per 10-minute window (Atlassian standard). IF HTTP 429 THEN retry after `Retry-After` header value.
**Retry logic:**
- HTTP 200/201: no retry
- HTTP 429: retry after `Retry-After` header; max 3 retries
- HTTP 500/503: exponential backoff 2s, 4s; max 2 retries
- HTTP 400/401/403/404: do not retry; log error; alert PMO if 401/403
- Timeout: retry once after 3 seconds; if timeout again, queue and alert PMO

**Read open tickets for matching:**
```
GET /search?jql=project={projectKey}+AND+status+not+in+(Done,Closed)&fields=summary,status,assignee,priority
Response 200:
{
  "issues": [
    {
      "id": "string",
      "key": "string (e.g. AP-123)",
      "fields": {
        "summary": "string",
        "status": { "name": "string" },
        "assignee": { "displayName": "string", "emailAddress": "string" },
        "priority": { "name": "string" }
      }
    }
  ]
}
```

**Add comment (approved):**
```
POST /issue/{issueKey}/comment
Request: { "body": { "type": "doc", "version": 1, "content": [{ "type": "paragraph", "content": [{ "type": "text", "text": "string" }] }] } }
Response 201: { "id": "string", "created": "ISO8601" }
Response 404: { "errorMessages": ["Issue not found"] }
```

**Create ticket (approved):**
```
POST /issue
Request:
{
  "fields": {
    "project": { "key": "string" },
    "summary": "string (max 255 chars, required)",
    "description": { "type": "doc", "version": 1, "content": [...] },
    "issuetype": { "name": "Task|Bug|Story" },
    "assignee": { "accountId": "string" },
    "priority": { "name": "string" },
    "duedate": "YYYY-MM-DD"
  }
}
Response 201: { "id": "string", "key": "string (e.g. AP-124)" }
Response 400: { "errors": { "field": "message" }, "errorMessages": ["string"] }
```

**Fallback:** IF JIRA API unavailable AND approved action is queued THEN queue update in WRITE_PENDING status; retry every 5 minutes for 1 hour; alert PMO after 3 failed retries. Do not discard approved actions.

**Scope-out:** Per-project field mappings (custom fields, priority label values, transition IDs for status changes, issuetype names) must be confirmed per client before build. Transition IDs are not predictable — must be retrieved via `GET /issue/{key}/transitions` per project.

---

#### Outlook (Microsoft Graph API)

**Auth:** OAuth 2.0, delegated permissions: `Mail.Send`. Access token scoped to the PMO user's identity via delegated flow — agent sends on behalf of the authenticated PMO user, not as a service account.
**Credentials:** OAuth 2.0 client ID and secret stored in Azure Key Vault; secret name: `outlook-graph-client-secret`.
**Base URL:** `https://graph.microsoft.com/v1.0`
**Timeout:** 10 seconds
**Rate limit:** 10,000 requests per 10 minutes per user. No burst concern at PMO volumes.
**Retry logic:**
- HTTP 202: success; no retry
- HTTP 429: retry after `Retry-After`; max 2 retries
- HTTP 500/503: retry once after 5 seconds; if still failing, alert PMO with full recipient list and approved content for manual send
- HTTP 400/401: do not retry; log and alert PMO immediately (likely auth or content error)

**Send approved meeting notes:**
```
POST /me/sendMail
Request:
{
  "message": {
    "subject": "string (max 255 chars — e.g. 'Meeting Notes: {meeting series name} — {date}')",
    "body": {
      "contentType": "HTML",
      "content": "string (approved notes HTML — max 1MB)"
    },
    "toRecipients": [
      { "emailAddress": { "address": "string", "name": "string" } }
    ]
  },
  "saveToSentItems": true
}
Response 202: (no body — accepted for delivery)
Response 400: { "error": { "code": "string", "message": "string" } }
```

**Guardrail — enforced before send call is made:**
- `toRecipients` list must have ≥1 entry
- `toRecipients` list must be confirmed by PMO (`distribution_list_confirmed = true`)
- `pmo_decision` on notes draft must be APPROVED
- PMO approval event must exist in audit log with matching `meeting_id` and `event_type = NOTES_APPROVED`
- IF any guardrail fails THEN abort send; log `SEND_BLOCKED` event with specific reason; alert PMO

**Fallback:** If send fails after retries → alert PMO with full approved content and recipient list; PMO can forward manually from their Outlook client. Set meeting status to SEND_FAILED (not DISTRIBUTED). Retry resumes when PMO triggers manual retry from platform UI.

### State Model

Each processed meeting progresses through the following states:

```
UPLOADED → PROCESSING → PROPOSALS_READY → IN_REVIEW → APPROVED → DISTRIBUTED → CLOSED
                                                ↓
                                         PARTIALLY_APPROVED (some items pending)
```

- `UPLOADED`: Transcript received; processing queued
- `PROCESSING`: Agent is extracting, classifying, and preparing proposals
- `PROPOSALS_READY`: All proposals available in PMO review interface; notification sent to PMO via Teams
- `IN_REVIEW`: PMO has opened the review interface
- `PARTIALLY_APPROVED`: PMO has approved some items; others pending or escalated
- `APPROVED`: All items resolved (approved, modified, or rejected); notes approved; DL confirmed
- `DISTRIBUTED`: Notes sent; RAID entries written; JIRA updates applied
- `CLOSED`: Audit record finalised; meeting record locked

### Error Handling

| Error Condition | Behaviour |
|---|---|
| JIRA API unavailable at write time | Queue approved update; retry every 5 minutes for 1 hour; alert PMO after 3 failed retries; do not lose approved action |
| SharePoint API unavailable at write time | Same retry pattern as JIRA; alert PMO |
| Outlook send failure | Retry once after 2 minutes; if second attempt fails, alert PMO with full recipient list and approved notes so PMO can send manually |
| Transcript upload fails validation (unreadable format) | Reject with specific error; prompt re-upload; do not create a partial record |
| Processing timeout (>30 minutes) | Alert PMO; offer option to retry or proceed with manual review of raw transcript |

### Audit Log Requirements

Every event must log: `meeting_id`, `timestamp`, `event_type`, `agent_id`, `item_id` (where applicable), `raid_type` (R/A/I/D), `proposed_content`, `confidence_score`, `escalation_code` (where applicable), `pmo_user_id`, `pmo_decision` (APPROVED / MODIFIED / REJECTED), `final_content`, `target_system`, `write_status`.

Audit log entries are append-only. No entry may be deleted or modified after creation.

---

## Sub-Agent 2: Status Report Agent

### Purpose
Automatically collect project data from configured sources, detect milestone health issues between reporting cycles, calculate RAG scores, generate audience-adapted draft reports informed by Wave 1 RAID outputs, and present them for PMO review and approval before distribution.

### Scope

**In scope:**
- Scheduled and on-demand data collection from JIRA, SharePoint, MS Project
- Milestone health monitoring (continuous between report cycles)
- Financial variance calculation and trend detection
- RAG score calculation per configured criteria
- Cross-source conflict detection
- Narrative generation incorporating Wave 1 RAID context
- Audience-adapted draft generation (Board/Executive, Steering Group, Project Team)
- Report distribution after per-version PMO approval

**Out of scope:**
- Predictive forecasting beyond burn rate projection
- Integration with external billing or finance systems
- Real-time dashboards or live data feeds

### Inputs

| Input | Source | Required |
|---|---|---|
| JIRA ticket status, milestone completion | JIRA REST API | Required |
| Project plan, milestone dates, resource allocation | MS Project via Graph API | Required |
| RAID log entries and decisions | SharePoint via Graph API | Required |
| RAG calculation criteria | Platform configuration per client | Required |
| Report templates per audience | Platform configuration per client | Required |
| Wave 1 meeting RAID outputs | Platform internal store | Required for narrative enrichment |

### Outputs

| Output | Approval Required |
|---|---|
| Milestone at-risk alert to PMO | No (notification only) |
| Draft report per audience version | Yes — per version |
| Distributed approved report | Automated after per-version approval |

### Decision Logic

**Milestone health:**
- IF a milestone due date has passed with no completion signal from JIRA or MS Project THEN flag as OVERDUE; notify PMO immediately
- IF a milestone is due within 14 calendar days AND no completion signal is present AND no progress update has been made in the last 5 business days THEN flag as AT_RISK
- IF a dependency of a milestone has slipped by >0 days THEN flag the dependent milestone as AT_RISK_DEPENDENCY

**Financial analysis:**
- IF actual spend > planned spend at current date by > configured threshold (default: 10%) THEN flag as OVER_BUDGET
- IF forecast cost to completion > remaining budget THEN flag as PROJECTED_OVERRUN
- IF weekly burn rate has decreased by >20% for 2 consecutive weeks THEN flag as DECELERATING (may indicate under-delivery risk)

**RAG calculation:**
- IF schedule dimension is AT_RISK or OVERDUE for any milestone with Critical path = true THEN schedule RAG = Red
- IF schedule dimension is AT_RISK for non-critical milestone only THEN schedule RAG = Amber
- IF budget dimension is PROJECTED_OVERRUN THEN budget RAG = Red
- IF budget dimension is OVER_BUDGET but not PROJECTED_OVERRUN THEN budget RAG = Amber
- IF any open Risk with severity = Critical exists in RAID log THEN risk RAG = Red
- IF overall RAG has deteriorated since last report THEN flag as RAG_DETERIORATION; block distribution until PMO acknowledges deterioration

**Cross-source conflict:**
- IF JIRA shows milestone status = Done AND MS Project shows = In Progress THEN flag as DATA_CONFLICT; block report generation for that project until PMO resolves
- IF conflict affects a field that determines RAG status THEN report generation for that project is blocked until resolved
- IF conflict is in a non-RAG field THEN report may proceed with conflict noted in PMO review interface

### Integration Contracts

- JIRA: `GET /rest/api/3/search` for ticket and milestone status
- MS Project: `GET /sites/{siteId}/lists/{planListId}/items` for schedule data
- SharePoint RAID: `GET /sites/{siteId}/lists/{raidListId}/items` for risk and decision context
- Outlook: `POST /me/sendMail` for approved report distribution

### Escalation Triggers

| Code | Condition | Behaviour |
|---|---|---|
| RAG_DETERIORATION | Overall RAG has worsened since last report | Block distribution; require PMO acknowledgement; trigger Stakeholder Communications Agent |
| DATA_CONFLICT | Conflicting status in RAG-affecting fields | Block report generation; alert PMO with specific conflicting values |
| PROJECTED_OVERRUN | Forecast spend exceeds remaining budget | Flag in report; set budget RAG ≥ Amber |
| MISSED_DATA_SOURCE | A configured source API is unavailable | Queue report; alert PMO; do not generate from incomplete data |

---

## Sub-Agent 3: Governance Monitoring Agent

### Purpose
Continuously assess every active project against configured governance standards, detect and classify gaps, generate per-project scorecards, and surface escalation drafts for PMO review — ensuring governance failures are detected before they reach audits or steering committees.

### Decision Logic (key rules)

- IF evidence for a governance check cannot be retrieved THEN classify the check as UNRESOLVABLE_GAP; do not assume compliant
- IF evidence is retrieved and matches the governance standard THEN classify as COMPLIANT
- IF a gap is detected AND the same gap already exists in OPEN or IN_PROGRESS status THEN update the existing gap record (age it); do not create a duplicate
- IF a gap is detected with configured severity = High THEN notify PMO immediately (not at next scheduled summary); draft escalation notice
- IF a PMO attempts to dismiss a gap without entering a dismissal reason THEN block the dismiss action at the UI level
- IF evidence that justified a dismissal is subsequently removed (e.g. document deleted from SharePoint) THEN re-open the gap automatically

### Integration Contracts

- SharePoint: `GET /sites/{siteId}/lists/{docsLibraryId}/items` for document evidence
- JIRA: `GET /rest/api/3/issue/{key}` for change request and approval status
- Platform internal RAID store: read Wave 1 outputs as governance evidence
- Outlook: `POST /me/sendMail` for approved escalation notices only

---

## Sub-Agent 4: Stakeholder Communications Agent

### Purpose
Detect events that require a stakeholder communication, assemble project context automatically, and generate accurate audience-adapted draft communications for PMO review.

### Trigger Detection Rules

- IF Status Report Agent raises RAG_DETERIORATION THEN generate mandatory draft: Escalation Notice
- IF a milestone is flagged AT_RISK on a project with programme-level visibility (configured flag) THEN generate optional draft: Milestone Slip Notification
- IF Governance Monitoring Agent raises a High-severity gap escalation THEN generate mandatory draft: Governance Gap Notice
- IF a RAID item with severity = Critical is approved by PMO in Wave 1 THEN generate optional draft: Risk Escalation to Sponsor
- IF a milestone is marked Complete in JIRA or MS Project THEN generate optional draft: Milestone Completion Announcement
- IF the same trigger event is already associated with a draft in PENDING_REVIEW status THEN do not generate a duplicate draft
- IF a trigger event resolves before the PMO reviews the associated draft (e.g. RAG returns to Amber) THEN flag the draft as TRIGGER_RESOLVED; do not auto-discard but alert PMO

### Draft Generation Rules

- IF draft is generated THEN every factual statement must reference a specific source: RAID item ID, RAG history record, governance gap ID, or JIRA ticket key
- IF a source cannot be verified for a statement THEN the statement must be omitted or flagged as UNVERIFIED; agent must not fabricate content
- IF a trigger requires communications to multiple audience levels THEN generate separate drafts for each level from the same source context

### Pending Review Timeout Rules

- IF a draft triggered by a High-severity event has been in PENDING_REVIEW for > 4 hours THEN send reminder notification to PMO via Teams
- IF a draft triggered by a non-high-severity event has been in PENDING_REVIEW for > 24 hours THEN send reminder notification
- Agent does not escalate or send the communication autonomously under any timeout condition

---

## Sub-Agent 5: Change Request Management Agent

### Purpose
Detect new change requests, assemble impact assessment data from live project sources, draft a structured impact assessment for PMO review, route the CR to the correct approver, and track it through to closure.

### Decision Logic

- IF a new item is created in the configured JIRA CR project or SharePoint CR list THEN trigger CR workflow; notify PMO
- IF the CR scope field indicates schedule impact AND the project plan has zero float on the affected path THEN flag schedule impact as HIGH in draft assessment
- IF forecast cost of CR exceeds available budget reserve (configured threshold, default: 5% of remaining budget) THEN flag cost impact as HIGH
- IF an open RAID Risk directly references the change area (keyword match + project context) THEN include it in the draft assessment as a related risk
- IF the CR scale matches a configured routing rule THEN assign proposed approver; flag for PMO confirmation before routing
- IF no routing rule matches THEN flag as ROUTING_UNRESOLVED; PMO must assign approver manually before routing proceeds
- IF a CR approval has been pending for > 1 business day without a response THEN notify PMO; do not auto-escalate

---

## Platform-Wide Requirements

| # | Requirement |
|---|---|
| P-01 | The platform must enforce human approval before any write to an external system (SharePoint, JIRA) or send via Outlook. This constraint must be implemented at the API call layer — no code path may bypass it. |
| P-02 | All sub-agents must emit structured events to the audit log on every state transition. The audit log is append-only and not accessible to any sub-agent for modification. |
| P-03 | The platform must support per-client configuration for: RAG thresholds, governance standards, JIRA field mappings, RAID log schema, distribution lists, routing rules, and communication templates. Configuration is stored separately from application code. |
| P-04 | All configuration changes must be versioned. Each version must record the changing user, timestamp, and previous value. |
| P-05 | PII detected in transcript content or communication drafts must be masked in all debug, trace, and audit logs. PII detection runs as a pre-processing step before any content is written to a log. |
| P-06 | Human override always takes precedence. IF a PMO modifies an agent proposal THEN the modified version is recorded as the authoritative output; the original proposal is retained in the audit log as the agent's suggestion only. |
| P-07 | All Microsoft Graph and JIRA API calls must use OAuth 2.0. Access tokens must not be stored in application logs. Token refresh is handled by the platform authentication layer. |
| P-08 | The platform must operate in two modes per client: default mode (manual transcript upload; no Graph API transcript permissions required) and enhanced mode (automatic transcript retrieval where IT has provisioned Graph API scopes). Mode selection is per-client configuration. |


---

# PMO AI Platform — Economics Alignment

---

## Operation Cost Classification

| Operation | Type | Cost Level | Frequency | Notes |
|---|---|---|---|---|
| Transcript upload validation | Check | Cheap | Per meeting upload | Format and size validation only |
| Speaker label parsing | Validate | Cheap | Per meeting | Deterministic text parsing |
| RAID item extraction (LLM call) | Generate | Moderate | Per meeting | One LLM call per transcript; primary cost driver in Wave 1 |
| Confidence scoring | Validate | Cheap | Per extracted item | Deterministic scoring against extraction result |
| JIRA ticket matching | Coordinate | Expensive | Per action item | External API call per potential match; batch where possible |
| SharePoint RAID read (duplicate check) | Coordinate | Expensive | Per meeting | One API call per meeting |
| SharePoint RAID write | Coordinate | Expensive | Per approved item | One API call per item; batched where API supports |
| Outlook send | Coordinate | Expensive | Per meeting (once approved) | One API call; not repeatable without PMO action |
| Status report data collection (JIRA + SharePoint + MS Project) | Coordinate | Very Expensive | Per report cycle | 3 external API calls minimum per project per report |
| Report narrative generation (LLM call) | Generate | Moderate | Per report per audience | 3 LLM calls per project (3 audience versions) |
| Governance standards assessment (SharePoint scan) | Coordinate | Expensive | Weekly per project | N API calls per project where N = number of evidence sources |
| CR impact assessment draft (LLM call) | Generate | Moderate | Per CR | One LLM call per change request |

---

## Cost Optimisation Decisions

### JIRA Ticket Matching — Batching
**Problem:** Matching 5 action items from a meeting against an open JIRA backlog of 200 tickets would require 5 separate `GET /search` calls under a naïve approach.
**Chosen approach:** Single bulk `GET /search` call retrieves all open tickets for the project at the start of meeting processing. Action items are matched in-memory against the cached result set. One API call per meeting, not per action item.
**Cache TTL:** Project ticket cache expires after 1 hour. If cache is expired at meeting upload time, refresh before matching begins.

### LLM Call Scope — Single Pass Extraction
**Problem:** Calling the LLM separately for RAID extraction, summary generation, and confidence scoring would triple token costs per meeting.
**Chosen approach:** Single LLM call with structured output prompt that returns RAID items, confidence scores, and meeting summary in one response. Prompt engineering handles all three outputs simultaneously.
**Token budget per meeting:** Maximum 8,000 input tokens (transcript); maximum 4,000 output tokens (structured RAID + summary). Transcripts exceeding 8,000 input tokens are chunked into overlapping segments; results merged and deduplicated.

### Status Report Data Collection — Scheduled Batch
**Problem:** Report data collection for 10 projects requires 30+ API calls (3 sources × 10 projects). If triggered simultaneously, this hits rate limits.
**Chosen approach:** Collection is staggered — one project per 30-second interval. All collections complete before narrative generation begins. If any collection fails, the report for that project is queued rather than generated from partial data.

### Governance Assessment — Incremental Checking
**Problem:** Full governance assessment for 20 active projects weekly would require checking every evidence source for every project from scratch.
**Chosen approach:** Only projects with changes since the last assessment (detected via SharePoint `lastModifiedDateTime` comparison) are fully re-assessed. Projects with no changes receive a "no change" pass automatically. Full assessment on all projects on Monday; incremental on other days.

### Circuit Breakers
| Integration | Circuit Opens After | Reset Attempt After | Fallback During Open |
|---|---|---|---|
| SharePoint | 5 consecutive failures | 60 seconds | Queue writes; alert PMO |
| JIRA | 5 consecutive failures | 60 seconds | Queue writes; alert PMO |
| Outlook | 3 consecutive failures | 120 seconds | Alert PMO with manual send instructions |
| MS Project (Graph) | 5 consecutive failures | 60 seconds | Queue report; alert PMO; do not generate from incomplete data |

---

## Token Budget Constraints

| Operation | Max Input Tokens | Max Output Tokens | Action if Exceeded |
|---|---|---|---|
| Meeting RAID extraction | 8,000 | 4,000 | Chunk transcript; process in overlapping 6,000-token segments |
| Status report narrative (per audience) | 4,000 | 1,500 | Summarise input context before generation; never truncate output |
| CR impact assessment | 3,000 | 1,000 | Summarise project data inputs before generation |
| Governance escalation draft | 2,000 | 800 | Summarise gap evidence before generation |

---

# PMO AI Platform — Governance

---

## Applicable Regulations and Compliance Context

| Regulation / Standard | Applicability | Implication for Platform |
|---|---|---|
| GDPR (EU) / UK GDPR | Meeting transcripts contain names, roles, and project-sensitive content of identifiable individuals | PII in transcripts must be masked in debug, trace, and audit logs. Data minimisation: transcripts stored only for the duration of processing + 30 days; raw transcript content not retained in long-term logs. Right to erasure: structured RAID entries reference speaker names — if a deletion request is received, speaker references in RAID entries must be anonymised, not deleted (RAID entry is a project governance record). |
| FCA / PRA (Financial Services) | Platform is deployed to support regulated financial services clients | Platform must not store client project data (including RAID entries, meeting content) in a way that creates regulatory reporting obligations for EPAM. Client data residency options must be documented per client. |
| AIB Change Methodology (and equivalent client governance frameworks) | Governance Monitoring Agent enforces client-specific governance rules | Rule configurations must be client-approved before deployment. Changes to governance rules require client sign-off, not just EPAM approval. |
| SOX (where applicable) | Some PMO clients operate in SOX-controlled environments | RAID log entries and approval workflows must produce an auditable record of who approved what, when — sufficient to satisfy change management audit requirements. |

---

## Audit Trail Schema

Every platform action that affects external systems or produces a governed output must emit an audit event. The audit log is append-only — no deletion or modification permitted.

| Field | Type | Required | Notes |
|---|---|---|---|
| `log_id` | UUID | Yes | Unique per event |
| `timestamp` | ISO 8601 UTC | Yes | Event time |
| `event_type` | enum | Yes | See event types below |
| `meeting_id` | UUID | Conditional | Required for Meeting Intelligence events |
| `item_id` | UUID | Conditional | RAID entry or report ID where applicable |
| `agent_id` | string | Yes | e.g. `meeting-intelligence-agent-v1` |
| `pmo_user_id` | UUID | Conditional | Required for all human decision events |
| `proposed_content` | JSON | Conditional | Agent's proposal, where applicable (max 5KB) |
| `confidence_score` | decimal | Conditional | 0.00–1.00 where applicable |
| `human_decision` | enum | Conditional | APPROVED / MODIFIED / REJECTED — set only on human action |
| `final_content` | JSON | Conditional | Approved or modified content actually written (max 5KB) |
| `target_system` | string | Conditional | SharePoint / JIRA / Outlook where a write occurred |
| `write_status` | enum | Conditional | SUCCESS / FAILED / QUEUED |
| `escalation_code` | string | Conditional | Escalation trigger code if applicable |

**Event types:** `TRANSCRIPT_UPLOADED`, `PROCESSING_STARTED`, `RAID_ITEM_PROPOSED`, `RAID_ITEM_APPROVED`, `RAID_ITEM_MODIFIED`, `RAID_ITEM_REJECTED`, `NOTES_DRAFT_GENERATED`, `NOTES_APPROVED`, `NOTES_SEND_REQUESTED`, `NOTES_SENT`, `SEND_BLOCKED`, `RAID_ENTRY_WRITTEN`, `RAID_WRITE_FAILED`, `JIRA_UPDATE_PROPOSED`, `JIRA_UPDATE_APPLIED`, `JIRA_UPDATE_REJECTED`, `ESCALATION_TRIGGERED`, `UNAUTHORISED_WRITE_ATTEMPT`, `GOVERNANCE_GAP_DETECTED`, `GOVERNANCE_GAP_DISMISSED`, `REPORT_DISTRIBUTED`, `COMMS_DRAFT_GENERATED`, `COMMS_SENT`, `CR_IMPACT_ASSESSED`

---

## Retention Periods

| Data Type | Retention | Basis |
|---|---|---|
| Audit log (all event types) | 7 years | Financial services governance audit requirement |
| Approved RAID entries | Retained until project closure + 3 years | Client governance record retention |
| Meeting transcript (raw) | 30 days from upload | Data minimisation; processed content retained in structured form |
| Meeting notes (approved content) | 3 years from project closure | Governance record |
| Debug and trace logs | 30 days | Operational troubleshooting only |
| Access tokens | Not stored; in-memory only | Security requirement |
| Governance gap records | 7 years | Audit evidence |

---

## HITL Checkpoints and SLAs

| Decision | Approval Required From | Escalation if Not Actioned Within | Next Step |
|---|---|---|---|
| RAID entry creation | Approving PMO user | 48 hours: reminder sent to PMO | After 72 hours: alert PMO Lead; item remains in PENDING_REVIEW indefinitely until human acts |
| Meeting notes distribution | PMO who uploaded transcript | 4 hours for High-severity meeting content; 24 hours for standard | Reminder sent at SLA; notes are never auto-sent |
| Governance escalation notice | PMO Lead | 4 hours from High-severity gap detection | Reminder sent; escalation never auto-sent |
| Status report distribution | Approving PMO per audience version | 4 hours from draft ready | Reminder sent; report never auto-distributed |
| Change request routing | PMO who received the CR | 4 hours from CR detected | Reminder sent; CR never auto-routed |

---

## Non-Repudiation

The platform must produce evidence that cannot be plausibly denied by the approving party:

- Every PMO approval action records: `pmo_user_id`, `timestamp`, `session_id`, `ip_address` (hashed for privacy), `decision` (APPROVED/MODIFIED/REJECTED), `final_content_hash` (SHA-256 of the approved content)
- The `final_content_hash` allows verification that the content now in SharePoint matches what the PMO approved — detecting any post-approval modification
- Audit log entries are append-only and cryptographically signed (HMAC with a platform key stored in Azure Key Vault) — any tampering with the log is detectable
- PMOs cannot access the audit log write path — they can only read audit records via the platform UI, not modify or delete them

---

## Data Deletion and the Right to Erasure

| Request Type | Action | What Is Retained |
|---|---|---|
| Delete speaker reference from RAID entry | Anonymise `source_speaker` and `source_quote` fields (replace with `[REDACTED]`) | Entry remains for governance record; provenance is preserved without PII |
| Delete meeting transcript | Raw transcript deleted from platform storage after standard 30-day window; earlier deletion on request | Structured RAID proposals and approved entries are not deleted — they are governance records |
| Full project data deletion (end of client contract) | Raw transcripts, unprocessed drafts deleted; audit logs retained per retention schedule | Audit logs retained 7 years per governance requirement; cannot be deleted on request |

**Cascade rules:**
- Deleting a MeetingSeries does not delete Meeting Records — series reference is SET NULL
- Deleting a Project blocks deletion if active RAID entries exist — ON DELETE RESTRICT
- Deleting a User sets `uploaded_by` and `pmo_user_id` to a retained `[DELETED USER]` placeholder — ON DELETE SET PLACEHOLDER (to preserve governance record without live PII reference)

---

# PMO AI Platform — Validation Design

---

## Validation Principles

1. Every success metric from the Problem Statement has a corresponding test.
2. Delegation boundaries are tested explicitly — not just happy paths.
3. Quiet failure (the agent is wrong and no one notices) is as important to test as loud failure.
4. Acceptance criteria are stated as pass/fail conditions, not qualitative judgements.

---

## Test Categories

| Category | Purpose |
|---|---|
| **Unit** | Single agent, single function, controlled input |
| **Integration** | Agent + external system interaction |
| **Simulation** | Full workflow with synthetic data matching real meeting/project patterns |
| **Delegation Boundary** | Specifically tests that human-only tasks cannot be executed without approval |
| **UAT** | Real PMO using real transcripts; output assessed by PMO against their own judgment |
| **Monitoring** | Ongoing production signals |

---

## Scenario 1: Happy Path — Standard Steering Committee Meeting

**Scenario:** A PMO uploads a 45-minute steering committee transcript for Project Apex. The meeting covered project status, two risks raised by the programme director, three action items with named owners and explicit dates, and one confirmed decision to extend the project timeline. A standing distribution list exists for the Project Apex Steering series.

**Test steps:**
1. PMO uploads transcript (.vtt format) and selects "Project Apex Steering" as meeting series
2. Platform processes transcript and presents proposals in review interface within 30 minutes
3. PMO reviews all proposals and approves all without modification
4. PMO confirms standing distribution list and approves notes
5. Platform writes RAID entries to SharePoint, updates JIRA, and sends notes via Outlook

**Acceptance criteria:**

| Criterion | Pass Condition |
|---|---|
| Processing time | Proposals available in PMO interface ≤ 30 minutes after upload |
| RAID capture | All 6 extractable items (2 R, 3 A, 1 D) present in proposals |
| Classification accuracy | All 6 items correctly typed (R/A/I/D) without PMO correction |
| Owner assignment | All 3 action owners correctly assigned from transcript; no AMBIGUOUS_OWNER flags |
| Due date normalisation | All explicit dates correctly parsed; no inferred dates flagged |
| Decision handling | Decision item carries DECISION_CANDIDATE escalation flag regardless of confidence |
| Notes draft | Narrative summary is present; RAID action list appears at foot; format matches configured template |
| Distribution | Notes sent to all addresses on standing list; no additional addresses added |
| RAID log write | 6 entries created in SharePoint RAID log with correct schema; `agent_proposed = true`; `created_by = PMO user ID` |
| Audit trail | Every item has a complete log entry including confidence score and PMO decision |

**Failure definition:** Any one of the 6 items missing from proposals; any item incorrectly typed without PMO correction; notes distributed before PMO approval action recorded; RAID entries created before PMO approval action recorded.

---

## Scenario 2: Edge Case — Ambiguous Meeting with External Owner and Disputed Decision

**Scenario:** A PMO uploads a 30-minute risk review transcript. The meeting contains: one statement that could be a Risk or Issue ("the integration test environment is down and it might cause the milestone to slip"), one action assigned to a contractor not in the meeting ("we need Smith & Co to confirm by Friday"), and one disputed decision ("let's go with option B — actually, can we revisit that before we finalise"). No standing distribution list exists for this meeting series.

**Test steps:**
1. PMO uploads transcript; selects project
2. Platform processes and presents proposals
3. PMO reviews proposals with multiple escalation flags
4. PMO resolves each flag, rejects the disputed decision, assigns a distribution list manually, approves notes
5. Platform executes approved actions only

**Acceptance criteria:**

| Criterion | Pass Condition |
|---|---|
| Ambiguous R/I | Item flagged with AMBIGUOUS_R_I; both Risk and Issue options presented; item cannot proceed without PMO type selection |
| External owner | Action for "Smith & Co" flagged with EXTERNAL_OWNER; owner field not auto-populated; PMO must assign or confirm manually |
| Disputed decision | Both "let's go with option B" and "can we revisit" text included in Decision candidate context; flagged with DECISION_CANDIDATE; presented as requiring PMO confirmation |
| No standing DL | Send action is disabled until PMO manually populates the recipient list |
| Rejected decision | Rejected decision must be recorded in audit log as REJECTED with PMO user ID; must not appear in RAID log; must not appear in distributed notes action list |
| Partial approval | Platform correctly processes and writes only approved/modified items; rejected items are closed in audit log |

**Failure definition:** AMBIGUOUS_R_I item proceeds with a system-chosen type without PMO selection; external owner is assigned without PMO action; disputed decision is logged as a Decision without PMO confirmation; send action available before distribution list is populated.

---

## Scenario 3: Failure Mode — Delegation Boundary Test (No Approval Path)

**Scenario:** A simulated test in which the application layer is instructed to attempt writing a RAID entry to SharePoint without a recorded PMO approval event in the audit log. This tests that the enforcement is architectural, not reliant on the UI flow being followed correctly.

**Test steps:**
1. Bypass the approval UI and call the SharePoint write function directly with a valid RAID payload but no corresponding PMO approval event in the audit log
2. Observe system response
3. Repeat for JIRA update and Outlook send

**Acceptance criteria:**

| Action | Expected result |
|---|---|
| SharePoint RAID write without approval event | Request rejected with `403 APPROVAL_REQUIRED`; no entry created in SharePoint; event logged to audit as `UNAUTHORISED_WRITE_ATTEMPT` |
| JIRA update without approval event | Request rejected with `403 APPROVAL_REQUIRED`; no ticket updated; event logged |
| Outlook send without approval event | Request rejected with `403 APPROVAL_REQUIRED`; no email sent; event logged |
| Audit log write attempt (modification of existing entry) | Request rejected; append-only constraint enforced |

**Failure definition:** Any write to an external system or Outlook send completes without a recorded PMO approval event. This is a critical failure — the platform's core governance guarantee has been violated.

---

## Scenario 4: Edge Case — RAG Deterioration Blocking Distribution

**Scenario:** The Status Report Agent calculates Red RAG for Project Beacon (was Amber last week). The PMO has approved the Executive audience version but not the Steering Group version. A downstream process attempts to distribute the Executive version.

**Acceptance criteria:**

| Criterion | Pass Condition |
|---|---|
| RAG deterioration flagged | RAG_DETERIORATION alert sent to PMO before any version is available for approval |
| Approval independence | PMO can approve Executive version independently without requiring Steering Group version to be approved first |
| Distribution independence | Platform distributes Executive version immediately after that version's approval; does not wait for Steering Group version |
| Stakeholder comms trigger | RAG_DETERIORATION event triggers Stakeholder Communications Agent to draft Escalation Notice for the same project |

**Failure definition:** Executive version distributes before PMO approves it; RAG_DETERIORATION does not trigger Stakeholder Communications Agent; deterioration is not visible in the report approval interface.

---

## Scenario 5: Failure Mode — Quiet Failure (Missed RAID Item)

**Scenario:** A transcript contains a clearly stated risk ("we might not have enough capacity to complete the testing phase by the deadline") that uses indirect language rather than explicit risk markers. The agent does not propose this item. The PMO approves the other proposals and distributes the notes. The risk is never logged.

**Why this matters:** This is the quiet failure mode. The agent produces proposals, the PMO approves them, the audit log records a clean run — and a genuine risk is undetected. There is no error, no flag, and no alert. The gap only becomes visible when the risk materialises.

**Detection approach:**
- During UAT: PMO reviewer is asked to identify all items they would manually log from the transcript before seeing agent proposals. Agent proposals are compared against the PMO's independent list. Discrepancies are flagged and categorised.
- In production: 10% random sample of processed transcripts are reviewed by PMO Lead post-distribution. Independently identified items not in the agent proposals are recorded as missed items. Capture rate is calculated monthly.
- Alert trigger: IF monthly capture rate falls below 90% on the sample THEN trigger model review; alert EPAM delivery team.

**Acceptance criterion:** Capture rate ≥ 95% on sampled transcripts across the first 90 days of production operation.

---

## Scenario 6: Integration Test — SharePoint API Unavailable at Write Time

**Scenario:** PMO approves a RAID entry. The SharePoint API returns a 503 error.

**Acceptance criteria:**

| Criterion | Pass Condition |
|---|---|
| Approved item not lost | Approved item retained in platform queue with status WRITE_PENDING |
| Retry behaviour | Platform retries every 5 minutes; maximum 12 retries (1 hour) |
| PMO alert | After 3 consecutive failed retries, PMO receives alert with item details and queue status |
| Manual recovery | PMO can export approved item details for manual entry if queue is not resolved within 1 hour |
| No duplicate write | If API recovers during retry window, item is written exactly once; retry mechanism checks for existing entry before writing |

**Failure definition:** Approved item is lost (not in queue, not written, not alerted); duplicate entry is written to SharePoint on retry.

---

## Scenario 7: Edge Case — Empty and Null Input Handling

**Scenario:** A PMO uploads a transcript that is technically valid format but contains only the meeting header (date, attendees) with no substantive discussion — e.g., a 2-minute check-in call where all participants said "nothing to add, all on track."

**Acceptance criteria:**

| Criterion | Pass Condition |
|---|---|
| No fabrication | Agent must not generate RAID proposals if no extractable content exists; `proposals` array is empty (`[]`), not omitted |
| Processing completes | Meeting record transitions to `PROPOSALS_READY` even with zero proposals; not `FAILED` |
| PMO notification | PMO receives notification: "No RAID items detected in this transcript" — not silently empty |
| Notes draft still generated | Narrative summary is generated ("Short check-in; no actions, risks, or decisions raised") — even with zero RAID items |
| Word count threshold | IF `transcript_word_count` < 50 THEN flag as LOW_CONTENT before processing; do not block, but note in proposal interface |

**Failure definition:** Agent generates placeholder or filler RAID items from a content-free transcript; meeting enters `FAILED` state when no proposals exist; PMO receives no notification about empty result.

---

## Scenario 8: Edge Case — Boundary Values

**Scenario:** Tests of specific numeric thresholds and limits.

| Test | Input | Expected Outcome |
|---|---|---|
| Confidence exactly at threshold | Action item with confidence_score = 0.80 (exactly at threshold) | Must proceed to standard review without LOW_CONFIDENCE flag. Boundary is ≥ 0.80. |
| Confidence just below threshold | Action item with confidence_score = 0.799 | Must be flagged LOW_CONFIDENCE; cannot proceed without PMO confirmation |
| Transcript at word count limit | Transcript with exactly 8,000 tokens | Processed in single pass; no chunking |
| Transcript just over limit | Transcript with 8,001 tokens | Chunked into two overlapping segments; results merged; no duplicate items |
| Due date inferred as today | "by end of today" on a Monday | Inferred date = today's date; `date_inferred = true`; flagged for PMO confirmation |
| Due date in the past | "we should have done this last week" | Flag as PAST_DUE_DATE escalation; do not create action item with past due date without PMO override |
| Max field length | `source_quote` = exactly 1000 characters | Accepted without truncation |
| Over max field length | `source_quote` = 1001 characters | Truncated to 1000 characters; truncation recorded in item description |

---

## Scenario 9: Edge Case — Concurrent Actions (Race Condition)

**Scenario:** Two PMOs are reviewing the same meeting's proposals simultaneously in separate browser sessions. PMO A approves a RAID item. PMO B simultaneously rejects the same item.

**Expected behaviour:**
- The platform must use optimistic locking on RAID item state. Each item carries an `etag` value; the approval/rejection action must include the current `etag`.
- IF PMO A's action commits first THEN PMO B's action must return `409 Conflict` with message: "This item was modified by another user. Please refresh."
- The item's final state is determined by whichever action committed first.
- No item may end up in both APPROVED and REJECTED state.
- Both actions are logged in the audit trail regardless of which succeeded.

**Acceptance criteria:**
- Exactly one outcome (APPROVED or REJECTED) is recorded for the item
- The losing PMO's session shows a conflict notification
- Both PMO actions are in the audit log with their respective decisions and timestamps
- No duplicate RAID entries are written to SharePoint

**Failure definition:** Both actions succeed, creating two conflicting states; item state is indeterminate; SharePoint write occurs twice.

---

## Monitoring Signals (Production)

| Signal | Measurement | Alert Threshold |
|---|---|---|
| RAID capture rate (sampled) | Monthly audit of 10% random sample | Alert if < 90% |
| RAID proposal acceptance rate | Approval log — approved without modification / total proposals | Alert if < 70% for 2 consecutive weeks |
| Average PMO review session time | Session log | Alert if average > 20 min (suggests review complexity is too high) |
| False positive rate — governance gaps | Gap dismissal log — dismissed without action / total gaps | Alert if > 15% in any week |
| Delegation boundary violation attempts | Audit log — UNAUTHORISED_WRITE_ATTEMPT events | Alert on any occurrence (zero tolerance) |
| API failure rate | Integration call log | Alert if > 1% for any integration in any 24-hour window |
| Draft acceptance rate — comms | Comms approval log — sent without material edit / total sent | Alert if < 65% for 2 consecutive weeks (suggests drafts require too much PMO editing) |

---

## UAT Acceptance Gate

Before Wave 1 is released to production at any client site:

1. A minimum of 10 real meeting transcripts from the client's own meetings must be processed and reviewed by a PMO who also independently identifies RAID items before seeing proposals
2. Capture rate on those 10 transcripts must be ≥ 90%
3. No delegation boundary violation must be observed in any UAT session
4. The PMO reviewer must rate the meeting notes draft as "requires minor edits or no edits" for ≥ 7 of the 10 transcripts
5. The PMO reviewer must confirm the distribution list workflow is operationally viable for their meeting patterns


---

# PMO AI Platform — Assumptions & Unknowns

---

## Section A: Assumptions

These are statements treated as true for the purpose of this specification. Status: [Known] = confirmed by stakeholder or evidence; [Assumed] = reasonable inference not yet verified; [Flagged] = must be validated before the affected component is built.

| ID | Assumption | Basis | Status | Risk if Wrong | Validate With | Validation Question |
|---|---|---|---|---|---|---|
| A-01 | Meetings are transcribed by Teams or Zoom and the PMO can export or copy the transcript file | PMO survey data confirms Teams transcription is in use; transcript export is a standard Teams feature | [Assumed] | Manual upload model is blocked — core Wave 1 dependency fails | PMO contact at each client + IT | "Can you export a .vtt transcript from a completed Teams meeting today? Can you demonstrate it?" |
| A-02 | The RAID log for each client exists as a structured list in SharePoint with consistent field names across projects within that client | PMO survey respondents described SharePoint as the RAID log location | [Assumed] | Write-back integration fails if RAID log is per-project Excel or uses inconsistent schemas | PMO Lead at each client | "Can you share the SharePoint list schema (List Settings → Columns) for your RAID log?" |
| A-03 | JIRA is the primary project tracking system and PMOs have read access to the relevant project boards | Multiple PMO survey respondents cited JIRA; JIRA updates explicitly named as a pain point | [Assumed] | JIRA integration contracts do not apply; integration scope expands if a different tool is used | PMO Lead + IT | "Which system does your team use for project tracking? Do PMOs currently have JIRA API access?" |
| A-04 | RAG criteria are definable per client — there is someone who can specify what constitutes Red, Amber, and Green | PMO practice implies RAG is in use; no universal standard exists | [Flagged] | Report automation blocked if criteria cannot be defined | PMO Lead + Portfolio Director | "Can you provide your RAG thresholds in writing? Who has authority to approve the RAG configuration for this deployment?" |
| A-05 | Governance standards to be checked are documented at least informally and can be translated into platform-configurable rules | Problem Statement identifies governance inconsistency as a pain; implies standards exist | [Flagged] | Governance Monitoring Agent cannot operate without configured rules; this is a client readiness problem | PMO Lead + Compliance | "What governance standards do your PMOs currently enforce? Where are they documented? Who owns them?" |
| A-06 | PMOs have authority to approve RAID log entries without sign-off from a separate compliance role | RAID entry creation described as current PMO task | [Assumed] | Approval workflow requires a second-tier review layer not currently specified | PMO Lead + Compliance | "Who currently has authority to create a RAID entry? Does anyone else need to approve it?" |
| A-07 | 80 meetings/month and 50 reports/month are representative of target client workloads | Stated as ~80/month and ~50/month per PMO survey | [Assumed] | If higher: infrastructure sizing insufficient; if lower: ROI case weakens | PMO at target clients | "How many meetings per month do you personally follow up on? How many status reports do you produce?" |
| A-08 | Meeting notes are currently distributed to participants, creating an established expectation | Problem statement describes notes as "often delayed" implying they are sent | [Assumed] | If notes are not currently sent at all, this is a new communication channel — change management implications differ | PMO at target clients | "Do you currently send meeting notes to all invitees after every meeting? How?" |

---

## Section B: Unknowns

These must be answered before the component they affect can be built or contracted. They are not answerable by inference from available information.

### Unknown 1: Transcript export access per client

**Question:** Can PMOs at each target client site export a Teams transcript file from a recorded meeting? Some organisations disable transcript download for information security reasons; others restrict it to the meeting organiser only.

**Why this matters:** Manual transcript upload is the default input model for Wave 1. If transcript export is blocked, there is no fallback that does not require Graph API access — which the manual upload model was designed to avoid. This must be confirmed per client before build, not assumed.

**How to resolve:** Request confirmation from the PMO contact at each target client that they can export a .vtt or copy transcript text from a completed Teams meeting. This takes one test and five minutes.

---

### Unknown 2: RAID log schema per client

**Question:** What are the exact field names, data types, column IDs, and required fields in the SharePoint RAID log list at each client? Does the schema vary between programmes within the same client?

**Why this matters:** The agent specification writes structured RAID entries to SharePoint using a defined schema. If the schema differs from what is assumed — different field names, lookup columns, choice fields with specific permitted values — every write will fail validation or create malformed entries. This is not a design-time issue; it requires the actual list schema from the client's SharePoint tenant.

**How to resolve:** PMO at each client exports the SharePoint list column definitions (List Settings → Columns). EPAM configures the per-client RAID schema in the platform before build of that client's write-back integration.

**Scope-out note:** The agent specification does not define the RAID log field names — it defines the logical schema. Exact field mappings are a client configuration deliverable, not a build assumption.

---

### Unknown 3: Governance standards documentation and ownership

**Question:** Are the governance standards a PMO is expected to enforce on each project documented anywhere? If so, where (process document, methodology guide, per-programme checklist)? Who has authority to define what constitutes a governance gap?

**Why this matters:** The Governance Monitoring Agent checks projects against "configured governance standards." If no standards are documented, the configuration cannot be populated, and the agent has nothing to check against. This is a client readiness problem — not something EPAM can solve through product design. Building the agent and delivering it to a client without documented standards results in a tool that cannot run.

**How to resolve:** Before Wave 2 Governance Monitoring build for any client, the client's PMO Lead must provide: a list of governance standards to be enforced, the evidence source for each standard (SharePoint document, JIRA field, RAID log entry), the severity of each standard if breached, and confirmation of who can update the standards configuration.

---

### Unknown 4: Speaker identification quality in client transcripts

**Question:** How accurately does Teams transcription identify and label individual speakers in the transcripts produced at each client's meetings? Speaker label quality varies significantly depending on microphone setup, number of speakers, and whether participants have distinct voice profiles registered.

**Why this matters:** Owner assignment accuracy (target ≥ 90%) depends on the agent being able to attribute statements to named speakers. If the transcript shows "Speaker 1", "Speaker 2" rather than names, or mislabels speakers, the agent cannot reliably assign owners — and the AMBIGUOUS_OWNER escalation rate will be high enough to negate the time-saving value of the tool.

**How to resolve:** PMO at each target client provides 3 sample transcripts from recent meetings. EPAM assesses speaker label quality in each sample before committing to the 90% owner assignment accuracy target for that client.

---

### Unknown 5: Change request submission channel per client

**Question:** Where do change requests currently arrive? Options include: a dedicated JIRA issue type, a SharePoint form, an email to the PMO, a verbal request in a meeting, or no formal process at all.

**Why this matters:** The Change Request Management Agent (Wave 2) triggers on a new item appearing in a configured channel. If there is no defined channel — if change requests arrive informally or inconsistently — the trigger cannot be configured and the automation cannot start. A change request submitted via email that the PMO then enters manually will not be detected.

**How to resolve:** For each target client, confirm the current change request submission mechanism and agree a single configured trigger channel before building the CR workflow. If no formal process exists, agree with the client what the channel will be before build.

---

### Unknown 6: MS Project usage and data currency

**Question:** Do all clients use MS Project as their project scheduling tool? If they do, is the plan kept current (updated weekly or more frequently), or is it a point-in-time document updated at milestones only?

**Why this matters:** The Status Report Agent depends on MS Project data for milestone health monitoring and RAG calculation. If clients use Smartsheet, Primavera, a custom SharePoint list, or plain Excel for scheduling, the MS Project integration does not apply and a new integration must be scoped. If MS Project is used but not kept current, milestone health monitoring will produce stale outputs that undermine rather than support the PMO.

**How to resolve:** Confirm scheduling tool per client; confirm average update frequency of the plan. If not MS Project, scope the alternative integration before Wave 2 build. If plan currency is poor, establish a data quality baseline before enabling automated milestone monitoring.

---

### Unknown 7: Data residency and regulatory constraints on transcript processing

**Question:** Do any target clients — particularly those in regulated environments (FCA, PRA, AIB's Central Bank obligations) — have requirements that prohibit meeting transcript content from being processed outside their Azure tenant or transmitted to a third-party-hosted application?

**Why this matters:** The platform is hosted on EPAM-managed Azure infrastructure. Transcripts uploaded to the platform are transmitted to EPAM's Azure tenant for processing. In some regulated financial services environments, particularly those subject to data sovereignty requirements, this may not be permissible without explicit approval from the information security or data protection function. The manual upload model does not eliminate this concern — it removes the API permission issue but not the data transfer issue.

**How to resolve:** Obtain written confirmation from the information security function at each target client that transmitting meeting transcript content to an EPAM-managed Azure environment for processing is permissible under their data classification policy. Where it is not, the client-hosted deployment model (platform deployed within the client's own Azure tenant) must be offered instead — at different commercial terms.

---

## Summary Table

| ID | Type | Status | Affects | Validate With | Priority |
|---|---|---|---|---|---|
| A-01 | Assumption | [Assumed] | Wave 1 input model | PMO contact + IT per client | Before Wave 1 build |
| A-02 | Assumption | [Assumed] | Wave 1 RAID write-back | PMO Lead per client | Before Wave 1 integration build |
| A-03 | Assumption | [Assumed] | Wave 1 JIRA integration | PMO Lead + IT per client | Before Wave 1 integration build |
| A-04 | Assumption | [Flagged] | Wave 2 Status Reports RAG | PMO Lead + Portfolio Director | Before Wave 2 build — **blocking** |
| A-05 | Assumption | [Flagged] | Wave 2 Governance Monitoring | PMO Lead + Compliance | Before Wave 2 build — **blocking** |
| A-06 | Assumption | [Assumed] | Wave 1 approval workflow | PMO Lead + Compliance | At client onboarding |
| A-07 | Assumption | [Assumed] | ROI case, infrastructure sizing | PMOs at target clients | Before commercial proposal |
| A-08 | Assumption | [Assumed] | Change management approach | PMOs at target clients | At client onboarding |
| U-01 | Unknown | [Flagged] | Wave 1 input model | PMO contact + IT per client | **Resolve before Wave 1 build starts** |
| U-02 | Unknown | [Flagged] | Wave 1 RAID write-back | PMO Lead per client | **Resolve before integration build** |
| U-03 | Unknown | [Flagged] | Wave 2 Governance Monitoring | PMO Lead + Compliance | **Resolve before Wave 2 build** |
| U-04 | Unknown | [Flagged] | Owner assignment accuracy target | PMOs at target clients | Resolve before UAT commitment |
| U-05 | Unknown | [Flagged] | Wave 2 Change Request trigger | PMO Lead per client | **Resolve before Wave 2 build** |
| U-06 | Unknown | [Flagged] | Wave 2 milestone monitoring | PMO Lead + IT per client | **Resolve before Wave 2 build** |
| U-07 | Unknown | [Flagged] | Platform deployment model + all data | IS/DPO per client | **Resolve before client contract** |
| U-07 | Unknown | Platform deployment model | **Resolve before client contract** |
