# PMO AI TOOL — WEEK 2 DELIVERABLES

**Date:** Week 2 Submission
**Scenario:** PMO AI Tool — Meeting Intelligence Focus
**Stakeholder Source:** Senior PMOs (MUFG meeting notes)
**RAID Log Format:** Risks, Actions, Issues, Decisions

> **Note:** No legacy billing system applies to this scenario. All systems referenced are from stakeholder meeting notes.

---

## Deliverable 0: PMO Workflows — Agentic vs Deterministic

### What is a RAID Log?

RAID = **R**isks (future threats), **A**ctions (commitments with owners), **I**ssues (current problems), **D**ecisions (what was agreed). A formal PMO governance artifact. Decisions (D) prevent disputes: *"I thought we decided X."*

---

### Classification of All PMO Workflows

| Workflow | Type | Reasoning |
|---|---|---|
| Meeting transcription | ❌ Deterministic | Mature ML; no judgment |
| Decision extraction (D) | ✅ Agentic | "Agreed" vs "considered" needs interpretation |
| Action extraction (A) | ✅ Agentic | Commitments; owner/date inference |
| Risk identification (R) | ✅ Agentic | "Might miss deadline" — worth logging? |
| Issue identification (I) | ✅ Agentic | Active problems vs future concerns |
| Owner assignment | ✅ Agentic | Explicit vs inferred |
| Due date inference | ✅ Agentic | "By end of week" → actual date |
| JIRA ticket update | ❌ Deterministic | API call once decided |
| RAID log write | ❌ Deterministic | Write once classified |
| Meeting summary | ✅ Agentic | Synthesis and prioritization |
| Follow-up email draft | ✅ Agentic | Tone and audience adaptation |
| PM tool data collection | ❌ Deterministic | API calls |
| RAG score calculation | ❌ Deterministic | Formula-based |
| Status narrative | ✅ Agentic | Metrics → story |
| Executive summary | ✅ Agentic | Audience framing |
| Report distribution | ❌ Deterministic | Email automation |
| Resource end-date tracking | ❌ Deterministic | Date comparison |
| Skills matching | ✅ Agentic | Best fit with trade-offs |
| Gap identification | ✅ Agentic | Forward-looking synthesis |
| Email commitment extraction | ✅ Agentic | "I'll send by Friday" |
| Reminder generation | ⚡ Hybrid | Timing deterministic; content agentic |
| Checklist management | ❌ Deterministic | State updates |
| Onboarding access check | ❌ Deterministic | API/RPA |
| Onboarding exceptions | ✅ Agentic | Context-dependent judgment |

---

### Volume × Value Scoring

| Work Stream | Volume (1-5) | Non-Det (1-5) | Score | Priority |
|---|---|---|---|---|
| Meeting Intelligence | 5 | 5 | 25 | ★ PRIMARY |
| Personal Task Mgmt | 5 | 4 | 20 | High |
| Status Reports | 4 | 4 | 16 | High |
| Strategic Resourcing | 3 | 4 | 12 | Medium |
| Onboarding Access | 3 | 2 | 6 | RPA/Hybrid |

---

### Recommended Four Work Streams

1. **Meeting Intelligence** — RAID extraction, JIRA updates *(PRIMARY)*
2. **Status Reports & Scorecards** — synthesis and generation
3. **Strategic Resourcing** — proactive gap detection and matching
4. **Personal Task Management** — email intelligence and reminders

---

## Deliverable 1: Cognitive Load Map

### Frame

- **Objective:** Reduce PMO time on meeting follow-up, status synthesis, and coordination by 50%.
- **Stakeholders:** Senior PMOs, Project Managers, Program Directors, Portfolio Director
- **Constraints:** Integrate with Jira, SharePoint, Teams/Zoom, Outlook. Human approval required for all RAID log entries (governance artifact), high-priority JIRA updates, and external communications.

**Assumptions:**
- `[ASSUMPTION: High]` ~80 meetings/month require follow-up
- `[ASSUMPTION: High]` RAID items frequently lost after meetings
- `[ASSUMPTION: Medium]` Decisions often disputed ("I thought we agreed X")
- `[ASSUMPTION: Medium]` JIRA is primary project tracking system

**Open Questions:** Meeting platforms in use? Meetings currently recorded? RAID log schema and location? Definition of "high-priority" JIRA ticket?

---

### The Four Work Streams

| Stream | Description | Volume | Time | Stakeholder Quote |
|---|---|---|---|---|
| 1. Meeting Intelligence | RAID extraction, JIRA updates | ~80/mo | ~30 min/mtg | "Raw meeting notes," "action items," "RAID logs" |
| 2. Status Reports | Synthesis, scorecards | ~50/mo | ~45 min/rpt | "Automate reports, automate scorecards" |
| 3. Strategic Resourcing | Gap detection, matching | ~40/mo | ~60 min/case | "Resources finishing up, match it up, skills pool" |
| 4. Personal Task Mgmt | Email intelligence, reminders | Continuous | ~2 hrs/day | "Read emails, checklist, tick off" |

---

### Stream 1: Meeting Intelligence — Full Decomposition

**Job to be Done**

> JtD-MEETING: Transform raw meeting transcripts into structured RAID entries (Risks, Actions, Issues, Decisions) with owners and due dates, update JIRA and RAID logs, and generate follow-up — ensuring nothing falls through.

**Micro-Task Inventory**

- **[1.1] Meeting Content Ingestion** — Receive transcript, identify speakers, clean text, link to project context.
- **[1.2] Meeting Summary Generation** — Identify topics, extract discussion points, generate audience-adapted executive summary.
- **[1.3] RAID Item Extraction:**
  - **[1.3.1] Risk (R):** Detect risk language ("might fail," "concerned about"), assess likelihood, identify owner, propose mitigation if discussed
  - **[1.3.2] Action (A):** Identify action language ("will do," "can you"), distinguish from suggestions, extract owner and due date, flag ambiguous items
  - **[1.3.3] Issue (I):** Detect issue language ("is broken," "blocked"), distinguish from risks, assess severity, identify owner
  - **[1.3.4] Decision (D):** Identify decision language ("agreed," "decided"), distinguish from proposals, capture decision-maker, note dissent
- **[1.4] RAID Classification & Confidence** — Classify as R/A/I/D, generate confidence score per item, flag low-confidence (<0.80) for human review, cross-reference existing entries.
- **[1.5] JIRA Integration** — Match actions to existing tickets, identify new tickets needed, prepare updates, flag high-priority for human review.
- **[1.6] RAID Log Maintenance** — Format per schema, set severity for R/I, set due dates for A, link D to source meeting, route ALL entries for human approval.
- **[1.7] Follow-Up Generation** — Draft email with RAID items, owners/dates, key decisions, next meeting. Route for human review before send.

**Cognitive Dimensions**

| Micro-Task | Load | Input | Determinism | Exceptions | Risk |
|---|---|---|---|---|---|
| 1.1 Ingestion | L | L | H | L | L |
| 1.2 Summary | H | L | L | M | M |
| 1.3.1 Risk (R) | H | L | L | H | H |
| 1.3.2 Action (A) | H | L | L | H | H |
| 1.3.3 Issue (I) | H | L | L | M | H |
| 1.3.4 Decision (D) | H | L | L | M | H |
| 1.4 Classification | H | M | L | H | H |
| 1.5 JIRA | M | M | M | M | H |
| 1.6 RAID Log | M | M | M | M | H |
| 1.7 Follow-Up | M | M | M | L | M |

---

### Stream 4: Personal Task Management — Full Decomposition

**Job to be Done**

> JtD-PERSONAL: Consolidate all commitments (emails, meetings, messages) into a single actionable task list, track completion, and provide reminders.

**Micro-Tasks**

- **4.1 Email Intelligence:** Scan inbox (3-day window), extract commitments and requests, identify deadlines
- **4.2 Cross-Source Consolidation:** Aggregate from email + meetings + JIRA, deduplicate, reconcile conflicts
- **4.3 Prioritization:** Apply due date urgency, requester importance, project priority; surface overdue items
- **4.4 Completion Detection:** Monitor sent folder, JIRA changes; confirm with user if uncertain
- **4.5 Reminder Generation:** Calculate timing, generate content, deliver via preferred channel
- **4.6 Checklist Interface:** Present daily list, allow tick-off, track completion rate

---

### Cognitive Zones & Breakpoints

```
🟢 CAPTURE → 🟡 INTERPRET → 🟠 CLASSIFY → 🔴 SYNTHESIZE → ⚫ REVIEW → 🟣 EXECUTE

BP1: Understanding Gate (Interpret → Classify)
  Risk: Misinterpreted content → wrong RAID classification

BP2: Confidence Gate (Classify → Synthesize)
  Risk: Low-confidence items need human judgment

BP3: Governance Gate (Synthesize → Execute)
  Risk: All RAID entries and external comms require human approval
```

---

### Cognitive Hotspots

| Hotspot | Challenge | Example | Mitigation |
|---|---|---|---|
| RAID Classification | Same statement could be R, I, or neither | "We might miss the deadline" | Confidence scoring + mandatory approval |
| Decision vs Proposal | "Let's do X" — agreed or just discussed? | "Let's use the new vendor" | All D entries flagged for confirmation |
| Action Extraction | Implicit vs explicit commitments | "We should look into that" vs "I will send it Friday" | Confidence scoring; flag ambiguous owners |
| Email Commitments | Varying commitment strength | "I'll try" vs "I will send it Friday" | Conservative extraction; weekly review |

---

### Assumptions Register

| ID | Assumption | Confidence | Validation |
|---|---|---|---|
| A-01 | Meetings are recorded/transcribed | Medium | Ask stakeholder |
| A-02 | JIRA is primary tracking system | Medium | System inventory |
| A-03 | RAID log is formal governance artifact | Medium | Confirm with compliance |
| A-04 | Decisions frequently disputed after meetings | High | Implied by pain points |
| A-05 | ~80 meetings/month need follow-up | Medium | Validate volume |

---

## Deliverable 2: Delegation Suitability Matrix

**Suitability Gate: PASS**

RAID classification requires reasoning (not rules). Patterns exist. APIs available. Governance manageable with HITL.

---

### Full Matrix

#### Stream 1: Meeting Intelligence

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Ingestion | L | H | H | L | L | Fully Agentic |
| Summary | L | L | M | M | M | Agent-Led + Oversight |
| Risk ID (R) | L | L | M | H | H | Human-Led + Support |
| Action (A) | L | L | M | H | H | Agent-Led + Oversight |
| Issue ID (I) | L | L | M | M | H | Human-Led + Support |
| Decision (D) | L | L | M | M | H | Human-Led + Support |
| RAID classify | M | L | M | H | H | Human-Led + Support |
| Owner assign | L | L | M | H | H | Agent-Led + Oversight |
| JIRA update | M | M | H | M | H | Agent-Led + Oversight |
| RAID entry | M | M | M | M | H | Human-Led + Support |
| Follow-up draft | M | L | M | M | H | Human-Led + Support |
| Follow-up send | H | H | H | L | H | Human Only |

#### Stream 2: Status Reports

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Data collection | H | H | H | L | L | Fully Agentic |
| Metric calc | H | H | H | L | L | Fully Agentic |
| Reconciliation | M | M | M | M | M | Agent-Led + Oversight |
| Narrative | L | L | M | H | M | Human-Led + Support |
| Exec summary | M | L | M | H | H | Human-Led + Support |
| Distribution | H | H | H | L | L | Fully Agentic |

#### Stream 3: Strategic Resourcing

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Resource tracking | H | H | H | L | L | Fully Agentic |
| Skills inventory | H | H | M | M | L | Fully Agentic |
| Gap detection | M | M | M | M | M | Agent-Led + Oversight |
| Match recommend | M | L | M | H | H | Human-Led + Support |
| Resource commit | L | L | M | H | H | Human Only |

#### Stream 4: Personal Task Management

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Email scanning | M | H | H | L | L | Fully Agentic |
| Commitment extract | L | M | M | H | M | Agent-Led + Oversight |
| Task consolidation | M | M | H | M | L | Agent-Led + Oversight |
| Prioritization | M | M | M | M | L | Agent-Led + Oversight |
| Completion detect | M | M | M | M | L | Agent-Led + Oversight |
| Reminder gen | H | H | H | L | L | Fully Agentic |
| Checklist mgmt | H | H | H | L | L | Fully Agentic |

---

### Distribution Summary

| Archetype | Count | % |
|---|---|---|
| Fully Agentic | 10 | 31% |
| Agent-Led + Oversight | 10 | 31% |
| Human-Led + Support | 9 | 28% |
| Human Only | 3 | 9% |

> ✓ **Anti-Pattern Check:** 69% require human involvement. RAID entries always need approval.

---

### RAID-Specific Delegation

| Type | Archetype | Rationale |
|---|---|---|
| R (Risks) | Human-Led + Support | Risk assessment needs business context |
| A (Actions) | Agent-Led + Oversight | More concrete; reviewable by exception |
| I (Issues) | Human-Led + Support | Severity assessment needs judgment |
| D (Decisions) | Human-Led + Support | Governance critical — must confirm what was agreed |

> **Governance Rule:** All RAID log entries require human approval before creation.

---

### Prioritized Backlog

| # | Task | Archetype | Rationale |
|---|---|---|---|
| 1 | Meeting → RAID extraction | Human-Led + Support | "RAID logs, action items" |
| 2 | Meeting → Action Items | Agent-Led + Oversight | "action items" |
| 3 | Decision Logging | Human-Led + Support | Prevents "I thought we decided X" disputes |
| 4 | Personal Task List | Agent-Led + Oversight | "checklist, tick off" |
| 5 | JIRA Updates | Agent-Led + Oversight | "updating JIRA board" |
| 6 | Report Automation | Agent-Led + Oversight | "automate reports" |
| 7 | Resource Gap Alerts | Agent-Led + Oversight | "resources finishing up" |

---

## Deliverable 3: Volume × Value Analysis

### Stream Scoring

| Stream | Vol | Non-Det | Score | Justification |
|---|---|---|---|---|
| 1. Meeting Intelligence | 5 | 5 | 25 | Every meeting; RAID classification is judgment-intensive |
| 2. Status Reports | 4 | 4 | 16 | Synthesis + audience adaptation |
| 3. Strategic Resourcing | 3 | 4 | 12 | Trade-off analysis |
| 4. Personal Task Mgmt | 5 | 4 | 20 | Daily email comprehension |

---

### Quadrant

```
NON-DETERMINISM
        Low ◄───────────────────► High

 High 5 ┼───────────┬─────────────────┐
         │           │ ★ MEETING      │
         │           │   INTELLIGENCE │
    V 4 ┼───────────┼─────────────────┤
    O    │           │ PERSONAL TASKS │
    L    │           │ STATUS REPORTS │
    U 3 ┼───────────┼─RESOURCING─────┤
    M    │           │                │
    E 2 ┼───────────┼─────────────────┤
 Low 1 ┼───────────┴─────────────────┘
```

**Winner: Meeting Intelligence (Score 25)**

Why it wins:
- Maximum score — highest volume × highest non-determinism
- Explicitly requested — "Raw meeting notes," "action items," "RAID logs"
- Governance value — Decisions (D) prevent costly disputes; Risks (R) caught early
- Foundation — meeting outputs feed status reports, personal tasks, resourcing

---

### Economics

| Value Driver | Calculation | Annual |
|---|---|---|
| Follow-up time freed | 40 hrs/mo × 50% × 12 × $75 | ~$18,000 |
| Reduced dropped items | Qualitative | TBD |
| Fewer decision disputes | Qualitative | TBD |
| **Quantifiable** | | **~$18,000** |

---

### Sequencing

| Wave | Stream | Rationale |
|---|---|---|
| 1 | Meeting Intelligence | Highest score; builds foundation |
| 2 | Personal Tasks + Status Reports | Leverages Wave 1 outputs |
| 3 | Strategic Resourcing | Builds on data foundation |

---

## Deliverable 4: Agent Purpose Document

**Agent Name:** PMO Meeting Intelligence Agent (MeetingBot)

### Purpose Statement

> "I make sure meetings produce results. I identify Risks, Actions, Issues, and Decisions, assign owners, and track everything in your systems. No more lost action items. No more 'I thought we decided X.' Every meeting moves work forward."

---

### Scope

#### In-Scope (v1)

| Capability | Description |
|---|---|
| Meeting ingestion | Process transcripts from Teams/Zoom |
| Speaker identification | Identify who said what |
| Summary generation | Executive summary with key topics |
| Risk identification (R) | Detect future problems mentioned |
| Action extraction (A) | Tasks with owners and dates |
| Issue identification (I) | Current problems needing resolution |
| Decision extraction (D) | What was agreed |
| RAID classification | R/A/I/D with confidence scores |
| JIRA integration | Match/create/update tickets |
| RAID log proposals | Entries for human approval |
| Follow-up drafts | Email for human review |
| Audit logging | Full traceability |

#### Guardrails — Agent MUST NOT:

- Send emails without human approval
- Create RAID entries without human approval
- Update high-priority JIRA tickets without confirmation
- Fabricate RAID items not discussed in the meeting
- Log proposals as decisions
- Assign ownership to people not in the meeting

---

### KPIs

#### Primary

| Metric | Current | Target |
|---|---|---|
| RAID capture rate | Unknown (many lost) | ≥95% |
| Time to follow-up | Hours to days | ≤30 min |
| Decision log completeness | Low | ≥95% |
| RAID proposal acceptance | N/A | ≥80% |
| R/A/I/D classification accuracy | N/A | ≥85% |
| Owner assignment accuracy | N/A | ≥90% |

#### Safety (Zero Tolerance)

| Metric | Target |
|---|---|
| RAID entries without approval | 0 |
| Emails sent without approval | 0 |
| Decisions logged incorrectly | 0 |

---

### Autonomy Matrix

```
LEVEL 4 — AGENT EXECUTES (No approval)
  • Meeting ingestion and processing
  • Speaker identification
  • Summary draft generation
  • JIRA ticket matching (read-only)
  • Audit logging

LEVEL 3 — AGENT EXECUTES → HUMAN OVERSIGHT ON TRIGGERS
  • Action extraction (A) — flag if confidence <0.80
  • Owner assignment — flag if ambiguous
  • Due date inference — flag if implicit
  • JIRA comments on low-priority tickets

LEVEL 2 — AGENT PROPOSES → HUMAN APPROVES
  • ALL Risk entries (R)
  • ALL Issue entries (I)
  • ALL Decision entries (D)
  • Low-confidence Action entries (A)
  • JIRA ticket creation
  • JIRA status changes
  • Follow-up email content

LEVEL 1 — HUMAN DECIDES → AGENT SUPPORTS
  • Ambiguous R vs I classification
  • Decision vs proposal distinction
  • Severity assessment

LEVEL 0 — HUMAN ONLY
  • Sending follow-up emails
  • Final RAID log entry creation
  • Resource commitments
```

---

### Escalation Triggers

| Code | Condition | Priority |
|---|---|---|
| LOW_CONFIDENCE | RAID confidence <0.80 | MEDIUM |
| AMBIGUOUS_R_VS_I | Could be Risk or Issue | MEDIUM |
| DECISION_VS_PROPOSAL | Uncertain if agreed | HIGH |
| AMBIGUOUS_OWNER | "Someone should..." | MEDIUM |
| EXTERNAL_OWNER | Owner outside org | HIGH |
| HIGH_SEVERITY_RISK | Critical risk detected | HIGH |
| SENSITIVE_CONTENT | HR/legal/financial | HIGH |

---

### Failure Modes

| Failure | Detection | Fallback |
|---|---|---|
| Transcript unavailable | No file/API response | Request manual notes |
| Low-quality transcript | Low confidence scores | Flag for manual review |
| Decision logged as proposal | Post-hoc audit | All D entries need approval |
| Risk misclassified as Issue | Post-hoc audit | All R/I entries need approval |
| Action missed | Post-hoc audit | Conservative extraction |
| JIRA API unavailable | Timeout | Queue updates; alert IT |

---

### RAID Log Schema

| Field | Type | Required | Notes |
|---|---|---|---|
| entry_id | auto | Yes | Unique ID |
| type | enum | Yes | RISK / ACTION / ISSUE / DECISION |
| title | string | Yes | Brief description |
| description | string | Yes | Full details |
| severity | enum | R, I | LOW / MEDIUM / HIGH / CRITICAL |
| status | enum | Yes | OPEN / IN_PROGRESS / CLOSED |
| owner | person | Yes | Responsible person |
| due_date | date | A | Target date |
| decision_maker | person | D | Who decided |
| source_meeting | string | Yes | Meeting reference |
| created_by | person | Yes | Human who approved |
| agent_proposed | boolean | Yes | True if agent-proposed |

---

### Audit Trail

Every action logs: `meeting_id`, `timestamp`, `event_type`, `raid_type` (R/A/I/D), `extraction_content`, `confidence_score`, `human_decision` (APPROVED/REJECTED/MODIFIED), `human_id`, `final_action`.

---

## Deliverable 5: System/Data Inventory

### Systems Inventory

| System | Purpose | Owner | Access | Availability | Risk |
|---|---|---|---|---|---|
| Microsoft Teams | Meeting transcripts | IT | Graph API | High | Low |
| Zoom | Meeting transcripts (alt) | IT | REST API | Medium | Low |
| Jira | Project tracking | PMO/IT | REST API | High | Low |
| SharePoint | RAID logs, documents | IT | Graph API | High | Medium |
| Outlook | Email | IT | Graph API | High | Low |
| MS Project | Project scheduling | PMO | Graph API | Medium | Medium |

---

### Critical Data Objects

| Object | System of Record | Key | Sensitivity |
|---|---|---|---|
| Meeting Transcript | Teams/Zoom | meeting_id | Medium (PII possible) |
| RAID Entry | SharePoint | entry_id | Medium (audit requirement) |
| JIRA Ticket | Jira | ticket_key | Low |
| Meeting Summary | Agent store | summary_id | Low |

---

### Key Interfaces

#### Teams (Graph API)

**Auth:** OAuth 2.0 (Azure AD) | **Base:** `https://graph.microsoft.com/v1.0/`

| Operation | Method | Endpoint |
|---|---|---|
| List meetings | GET | `/me/onlineMeetings` |
| Get transcript | GET | `/me/onlineMeetings/{id}/transcripts` |
| Get attendees | GET | `/me/onlineMeetings/{id}/attendanceReports` |

#### Jira (REST API)

**Auth:** API Token or OAuth 2.0 | **Base:** `https://{org}.atlassian.net/rest/api/3/`

| Operation | Method | Endpoint |
|---|---|---|
| Search issues | GET | `/search` |
| Create issue | POST | `/issue` |
| Update issue | PUT | `/issue/{issueKey}` |
| Add comment | POST | `/issue/{issueKey}/comment` |

#### SharePoint — RAID Log (Graph API)

**Auth:** OAuth 2.0 (Azure AD)

| Operation | Method | Endpoint |
|---|---|---|
| Get entries | GET | `/sites/{siteId}/lists/{listId}/items` |
| Create entry | POST | `/sites/{siteId}/lists/{listId}/items` |
| Update entry | PATCH | `/sites/{siteId}/lists/{listId}/items/{id}` |

---

### RAID Log Schema *(Expected — Validate with Stakeholder)*

| Field | Type | Required | Notes |
|---|---|---|---|
| entry_id | auto | Yes | |
| type | enum | Yes | RISK/ACTION/ISSUE/DECISION |
| title | string(100) | Yes | |
| description | string(1000) | Yes | |
| severity | enum | R, I | LOW/MEDIUM/HIGH/CRITICAL |
| status | enum | Yes | OPEN/IN_PROGRESS/CLOSED |
| owner | person | Yes | |
| due_date | date | A | |
| decision_maker | person | D | |
| source_meeting | string | Yes | |
| created_by | person | Yes | Human who approved |
| agent_proposed | boolean | Yes | |

---

### Data Flow

```
Teams/Zoom ──► Agent [Ingest → Extract → Classify → Generate] ──► Proposals
                               ↕                                      ↓
                         Jira (read)                             PMO Analyst
                                                                     ↓
                                                       Approve ──► Jira / SharePoint / Outlook
```

---

### Risks & Mitigations

| Risk | Impact | Mitigation |
|---|---|---|
| Transcript unavailable | High | Manual notes fallback |
| Poor transcript quality | High | Flag for manual review |
| JIRA rate limiting | Medium | Throttling; batch updates |
| SharePoint permissions | Medium | IT to provision access |
| PII in transcripts | Medium | PII detection; masking in logs |

---

### Blockers

| Item | Impact | Resolution |
|---|---|---|
| Teams transcription API access | BLOCKING | IT to provision Graph API permissions |
| RAID log SharePoint schema | MEDIUM | PMO to document current schema |
| JIRA project field mappings | MEDIUM | PMO to provide per-project config |

---

### Compounding Opportunities

| Integration | Reuse Across Agents |
|---|---|
| Teams Graph API | Status reporting, resource tracking |
| Jira REST API | All agents needing project data |
| SharePoint Graph API | All agents needing document/list access |
| Audit logging pipeline | All agents |
| Proposal/approval workflow | All agents with governance requirements |

---

## Deliverable 6: Discovery Questions

### Top 10 Design-Changing Questions

| # | Question | Why It Changes the Design |
|---|---|---|
| 1 | "Are meetings currently recorded and transcribed? Teams, Zoom, or both?" | Determines primary integration target |
| 2 | "When you capture RAID items today, what's the process? Where do they go?" | Reveals current state gap; lived vs documented |
| 3 | "What makes an action item 'clear' vs 'ambiguous'? Give me two examples." | Calibrates extraction confidence thresholds |
| 4 | "How do you distinguish a Decision from a discussion? Example of each?" | Critical for D classification — governance-critical |
| 5 | "For RAID logs — who approves entries? Is there an audit requirement?" | Determines governance constraints; shapes approval workflow |
| 6 | "If the agent extracted a RAID item incorrectly, how would you know? Consequence?" | Shapes accuracy requirements and review workflow strictness |
| 7 | "What % of meetings produce JIRA-worthy actions vs informal tracking?" | Scales JIRA integration scope |
| 8 | "What makes a JIRA ticket 'high-priority' where you'd want manual confirmation?" | Defines escalation criteria for autonomy matrix |
| 9 | "Do follow-up emails go to everyone or action owners? Who approves before sending?" | Defines email scope and recipient rules |
| 10 | "If we build one thing first — summaries, RAID extraction, or JIRA updates — which gives the most value fastest?" | Forces prioritization; shapes Wave 1 scope |

---

### Grouped Questions

#### A. Meeting Intelligence

| Question | Design Impact |
|---|---|
| "Show me how RAID items are captured today — the reality, not the ideal." | Grounds requirements in lived work |
| "What language indicates a Decision vs a suggestion? Examples?" | Calibrates D detection |
| "When someone says 'by end of week' — how do you translate that?" | Date inference rules |
| "Are there meetings where you explicitly don't want RAID items tracked?" | Scope exclusions |

#### B. JIRA Integration

| Question | Design Impact |
|---|---|
| "How do you know which JIRA ticket an action relates to?" | Matching logic |
| "What fields do you update after meetings — status, comments, assignee?" | Update scope |
| "Ticket types where automatic updates would be unwelcome?" | Exclusions |

#### C. RAID Governance

| Question | Design Impact |
|---|---|
| "Walk me through the last time something became a Risk in the RAID log." | Grounds R detection |
| "Who has authority to create RAID entries? Review process?" | Approval workflow |
| "Consequence if a Risk is identified but not logged?" | Risk tolerance |
| "What's the RAID log schema? SharePoint, Excel, or other?" | Technical integration |

#### D. Follow-Up & Communication

| Question | Design Impact |
|---|---|
| "What goes in a good follow-up email? What tone?" | Email generation template |
| "Meetings where follow-ups shouldn't be sent?" | Scope exclusions |
| "If the agent drafted a follow-up with a mistake, when would you catch it?" | Review workflow timing |

#### E. Systems

| Question | Design Impact |
|---|---|
| "What meeting platform(s)? All Teams, all Zoom, or mix?" | Integration targets |
| "Where does the 'official' action list live — JIRA, SharePoint, project plan?" | Data reconciliation |
| "Other systems containing RAID-related information?" | Integration scope |

#### F. Organizational

| Question | Design Impact |
|---|---|
| "How would PMs react to AI-generated action lists from their meetings?" | Change management approach |
| "If meetings produced automatic RAID extraction, what would your team do with freed time?" | Value proposition; headcount implications |
| "Who else needs to approve connecting to Teams/JIRA/SharePoint?" | Stakeholder identification |

---

### Evasion Detection

| Probe | Signal | Follow-Up |
|---|---|---|
| "You said PMs update JIRA, but you also mentioned chasing." | Contradiction | "When did a PM last update JIRA on time without a reminder?" |
| "You said RAID logs are 'updated weekly' but also 'often stale.'" | Minimizing | "When did a stale entry last cause a problem?" |
| "You said matching is 'straightforward' then described five edge cases." | Oversimplification | "If you had to pick one complexity, which matters most?" |

---

## Deliverable 7: CLAUDE.md

### Project Intent

AI agent for PMO meeting intelligence. Transforms meeting transcripts into structured RAID entries (Risks, Actions, Issues, Decisions) with owners, due dates, and system updates.

**Objective:** Every meeting produces tracked results — no lost actions, documented decisions, current JIRA.

---

### Non-Negotiables

> 🛑 **No RAID Entries Without Approval**
> RAID logs are governance artifacts. All entries require explicit human approval. Violation = GOVERNANCE BREACH.

> 🛑 **No Emails Without Approval**
> Follow-up emails represent the organization. Violation = UNAUTHORIZED COMMUNICATION.

> 🛑 **No High-Priority JIRA Updates Without Confirmation**
> High-priority = Priority Highest/High OR label "executive-visible." Violation = STAKEHOLDER TRUST BREACH.

> 🛑 **Source Traceability Required**
> Every RAID item must trace to: meeting_id, timestamp in meeting, speaker (if identifiable). Violation = AUDIT FAILURE.

> 🛑 **No Fabricated Content**
> Agent must not generate RAID items not discussed in the meeting. Violation = TRUST VIOLATION.

---

### Build Loop

```
1. PROMPT:   "Build confident parts. List clarifications. Build."
2. REVIEW:   matches spec? questions = gaps? couldn't build = gaps?
3. DIAGNOSE: spec ambiguity | builder misread | design gap | delegation boundary gap
4. REVISE    autonomy matrix / escalation triggers first
5. RE-RUN
```

### Gap Diagnosis

| Signal | Category | Fix |
|---|---|---|
| "What's high-priority?" | Spec ambiguity | Define criteria explicitly |
| Creates RAID without approval | Builder misread | Highlight non-negotiable |
| Asks about confidence threshold | Delegation boundary gap | Clarify autonomy matrix |

---

### Assumptions Protocol

Tag all unconfirmed statements: `[ASSUMPTION: High/Medium/Low]`

| ID | Assumption | Confidence | Status |
|---|---|---|---|
| U1 | Teams meetings recorded | Medium | VALIDATE |
| U2 | Transcription API accessible | Medium | VALIDATE |
| U3 | JIRA is primary tracking | Medium | Confirm |
| U4 | RAID log is SharePoint list | Low | VALIDATE |

---

### Engineering Conventions

- Process transcripts asynchronously (not real-time in v1)
- Confidence scores for all extractions; flag <0.80 for human review
- Match JIRA by: explicit ticket mention, project context, keywords
- All JIRA status changes require human confirmation
- All RAID entries require human approval — no exceptions
- All emails require human approval — no exceptions
- PII detection and masking in debug/trace logs

---

### Monitoring

#### Offline Tests

| Test | Pass Criteria |
|---|---|
| RAID extraction accuracy | ≥90% on labeled samples |
| R/A/I/D classification | ≥85% correct |
| Owner assignment | ≥85% correct |
| No unauthorized actions | 0 violations |
| Source traceability | 100% of items traced |

#### Online Monitoring

| Metric | Normal | Warning | Critical |
|---|---|---|---|
| Processing success | ≥99% | <95% | <90% |
| Extraction confidence (avg) | ≥0.85 | <0.75 | <65% |
| Proposal acceptance rate | ≥80% | <70% | <60% |
| RAID accuracy (spot-check) | ≥90% | <85% | <80% |

---

### Change Control — Requires PR + Approval

| Change | Approver |
|---|---|
| Autonomy matrix | PMO Lead |
| Confidence thresholds | PMO Lead |
| JIRA field mappings | PMO Lead |
| RAID log schema | PMO Lead + Compliance |
| Email template | PMO Lead |

---

### Known Gaps

| ID | Gap | Status | Impact |
|---|---|---|---|
| U1 | Teams transcription API access | BLOCKING | Cannot process meetings |
| U2 | RAID log SharePoint schema | MEDIUM | Cannot propose entries |
| U3 | JIRA field mappings | MEDIUM | Cannot match tickets |
| U4 | High-priority ticket definition | LOW | Using assumed criteria |

---

### Escalation Codes

```
LOW_CONFIDENCE         MEDIUM   Confidence <0.80
AMBIGUOUS_R_VS_I       MEDIUM   Could be Risk or Issue
DECISION_VS_PROPOSAL   HIGH     Uncertain if agreed
AMBIGUOUS_OWNER        MEDIUM   "Someone should..."
EXTERNAL_OWNER         HIGH     Owner outside org
HIGH_SEVERITY_RISK     HIGH     Critical risk
SENSITIVE_CONTENT      HIGH     HR/legal/financial
```

---

### Default Thresholds

```yaml
extraction:
  confidence_threshold: 0.80
jira:
  high_priority_always_confirm: true
  auto_comment_low_priority: true
raid:
  always_require_approval: true
email:
  always_require_approval: true
```

---

*End of PMO AI Tool Deliverables — Complete Package*
*Agent version: v1.0-design*
