# PMO AI Tool — Technical Design Reference

**Stakeholder Source:** Senior PMOs (MUFG, Citi, and other financial services clients)
**RAID Log Format:** Risks, Actions, Issues, Decisions

---

## Section 1: PMO Workflows — Agentic vs Deterministic

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
| Governance compliance check | ✅ Agentic | Assessing adequacy requires judgment, not a checklist |
| Stakeholder comms drafting | ✅ Agentic | Tone, audience framing, and content selection require judgment |
| Financial variance analysis | ✅ Agentic | Interpreting budget signals requires context and judgment |

---

### Volume × Value Scoring

| Work Stream | Volume (1-5) | Non-Det (1-5) | Score | Priority |
|---|---|---|---|---|
| Meeting Intelligence | 5 | 5 | 25 | ★ Wave 1 |
| Personal Task Mgmt | 5 | 4 | 20 | Wave 3 |
| Proactive Risk Monitoring | 4 | 5 | 20 | Wave 3 |
| Governance Monitoring | 4 | 5 | 20 | ★ Wave 2 |
| Status Reports | 4 | 4 | 16 | ★ Wave 2 |
| **Change Request Management** | **4** | **4** | **16** | **★ Wave 2** |
| Stakeholder Communications | 4 | 4 | 16 | ★ Wave 2 |
| Lessons Learned | 3 | 5 | 15 | Wave 4 *(high priority)* |
| Strategic Resourcing | 3 | 4 | 12 | Wave 3 |
| Benefits Tracking | 3 | 4 | 12 | Wave 3 *(new)* |
| Dependency Tracking | 3 | 4 | 12 | Wave 4 |
| Project Mobilisation / PID | 2 | 3 | — | Wave 4 *(new)* |
| Onboarding Access | 3 | 2 | 6 | RPA/Hybrid |

---

### Recommended Five Work Streams (Initial Focus)

1. **Meeting Intelligence** — RAID extraction, JIRA updates, meeting notes to all invitees *(PRIMARY)*
2. **Status Reports & Scorecards** — synthesis, milestone health monitoring, and generation
3. **Governance Monitoring** — continuous compliance checking and scorecard generation
4. **Stakeholder Communications** — trigger-aware comms drafting and governed distribution
5. **Change Request Management** — impact assessment drafting, approval routing, and status tracking

---

## Section 2: Cognitive Load Map

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

### The Five Priority Work Streams

| Stream | Description | Volume | Time | Evidence |
|---|---|---|---|---|
| 1. Meeting Intelligence | RAID extraction, JIRA updates, meeting notes to all invitees | ~80/mo | ~30 min/mtg | "Raw meeting notes," "action items," "RAID logs" — stakeholder-quoted |
| 2. Status Reports | Synthesis, milestone health monitoring, scorecards | ~50/mo | ~45 min/rpt | "Automate reports, automate scorecards" — stakeholder-quoted |
| 3. Governance Monitoring | Continuous compliance checking, scorecard generation | Weekly per project | ~2 hrs/manual review | "Inconsistent governance" — Problem Statement; validated by regulated programme pipeline (IRB, AML, SEPA) |
| 4. Stakeholder Communications | Trigger-aware comms drafting, governed distribution | Event-driven | ~30–60 min/communication | "A key aspect of the PMO role is stakeholder management" — stakeholder-quoted |
| 5. Change Request Management | Impact assessment drafting, approval routing, status tracking | Per change request | ~30–60 min/CR | Confirmed in 100% of PMO role specifications reviewed (6/6 AIB roles) |

---

### Stream 1: Meeting Intelligence — Full Decomposition

**Job to be Done**

> JtD-MEETING: Transform raw meeting transcripts into structured RAID entries (Risks, Actions, Issues, Decisions) with owners and due dates, update JIRA and RAID logs, and generate structured meeting notes (narrative summary + RAID action list at foot) distributed to all invited participants — ensuring nothing falls through.

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
- **[1.7] Meeting Notes Generation** — Draft structured meeting notes: narrative summary of key topics and decisions, followed by the full RAID action list at the foot (owners, due dates, classifications). Retrieve invitee list from meeting calendar invitation. Route for human review before distribution to all invited participants via Outlook.

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
| 1.7 Meeting Notes | M | M | M | L | M |

---

### Stream 2 (Wave 2): Status Reports & Scorecards — Summary Decomposition

**Job to be Done**

> JtD-STATUS: Automatically collect project data from all configured sources, monitor milestone health proactively between reporting cycles, calculate RAG status, reconcile data conflicts, generate audience-adapted narrative reports informed by Wave 1 RAID and decision outputs, and distribute approved reports to the right stakeholders — replacing manual data extraction and multi-version report writing.

**Micro-Tasks**

- **[2.1] Data Collection** — Pull metrics from JIRA, SharePoint, and MS Project via API on a scheduled or on-demand basis; record data pull timestamp
- **[2.2] Milestone Health Monitoring** — Check all active milestones against plan on a continuous basis; flag milestones at risk of slipping before the next reporting cycle; notify PMO immediately for any overdue or dependency-blocked milestone
- **[2.3] Financial Analysis** — Calculate budget vs actuals, spend variance, and burn rate trend; flag projects where current trajectory exhausts budget before completion
- **[2.4] RAG Calculation** — Apply configured criteria across schedule, budget, risk, and resource dimensions; flag deteriorations prominently for PMO review before report is finalised
- **[2.5] Cross-Source Reconciliation** — Detect and surface conflicts between data sources (e.g. JIRA vs MS Project); block report generation for unresolved conflicts in RAG-affecting fields
- **[2.6] Narrative Generation** — Draft "so what" explanation of the numbers, informed by Wave 1 RAID items, decisions, and risks; indicate where no material change occurred
- **[2.7] Audience Adaptation** — Generate separate versions for Board/Executive, Steering Group, and Project Team from a single data pull
- **[2.8] Approval & Distribution** — Present all versions for PMO review; distribute approved versions via Outlook to configured recipient lists; log approving user and timestamp

---

### Stream 3 (Wave 2): Governance Monitoring — Summary Decomposition

**Job to be Done**

> JtD-GOVERNANCE: Continuously assess every active project against configured governance standards, detect gaps by type and severity, generate per-project scorecards, and surface escalation drafts for PMO review — ensuring governance failures are caught before they reach audits or steering committees.

**Micro-Tasks**

- **[3.1] Standards Assessment** — Run weekly checks of each project against all applicable governance rules; retrieve evidence from SharePoint, RAID logs, and JIRA
- **[3.2] Gap Detection** — Classify each gap by type (Missing Document, Overdue Approval, etc.) and severity (High/Medium/Low); suppress duplicates; age persistent gaps in place
- **[3.3] Scorecard Generation** — Produce per-project and portfolio-level scorecards; calculate trend versus previous assessment
- **[3.4] Escalation Drafting** — For High severity gaps, draft an escalation notice for PMO review; never send independently
- **[3.5] Resolution Tracking** — Track gap status (Open, In Progress, Resolved, Dismissed); enforce mandatory reason for all dismissals; maintain full audit trail

---

### Stream 4 (Wave 2): Stakeholder Communications — Summary Decomposition

**Job to be Done**

> JtD-COMMS: Detect events that require a stakeholder communication, assemble the relevant project context automatically, and generate accurate audience-adapted draft communications for PMO review — ensuring the right message reaches the right person at the right moment, without the PMO having to start from scratch under pressure.

**Micro-Tasks**

- **[4.1] Trigger Detection** — Monitor for RAG changes, milestone slips, High severity RAID items, governance gap escalations, and milestone completions; apply configurable mandatory vs optional draft rules per client
- **[4.2] Context Gathering** — Pull relevant context from Wave 1 RAID items and decisions, Wave 2 status report and RAG history, governance gap records, and JIRA
- **[4.3] Draft Generation** — Generate accurate, source-traceable draft communication; confidence-flag any uncertain statements; never fabricate content
- **[4.4] Audience Adaptation** — Generate separate versions for different recipient types (sponsor, programme director, project team, executive) from the same underlying context
- **[4.5] Distribution** — Send approved communications via Outlook; log all drafts (sent, edited, and discarded) to audit trail

---

### Stream 5 (Wave 2): Change Request Management — Summary Decomposition

**Job to be Done**

> JtD-CHANGE: When a change request is received, automatically assemble a draft impact assessment from live project data — cross-referencing the plan, RAID log, and financials — route it to the correct approver, track it through to closure, and keep the RAID log and stakeholders updated throughout. Confirmed present in 100% of PMO role specifications reviewed.

**Micro-Tasks**

- **[5.1] Trigger Detection** — Identify a new change request submitted via JIRA, SharePoint, or a meeting decision; link to the relevant project context
- **[5.2] Impact Assessment Draft** — Cross-reference the project plan, RAID log, open actions, and financial position to draft an assessment covering schedule impact, cost impact, and risk implications
- **[5.3] Approval Routing** — Identify the correct approver based on change type and scale; prepare the approval package; flag high-impact changes for escalated review
- **[5.4] Status Tracking** — Monitor the change through the approval process; flag overdue approvals for PMO follow-up; never close a change without explicit PMO confirmation
- **[5.5] RAID Update Proposal** — Propose new or updated RAID entries where the change introduces risks or issues; route all proposals for PMO approval
- **[5.6] Closure Notification** — Draft a notification to relevant stakeholders when a change is approved or rejected; route through Stakeholder Communications workflow for PMO review and send

---

### Stream 7 (Wave 3): Personal Task Management — Summary Decomposition

> *Personal Task Management was reassigned to Wave 3. Wave 2 now comprises Streams 1–5: Meeting Intelligence, Status Reports, Governance Monitoring, Stakeholder Communications, and Change Request Management.*

**Job to be Done**

> JtD-PERSONAL: Consolidate all commitments (emails, meetings, messages) into a single actionable task list, track completion, and provide reminders.

**Micro-Tasks**

- **[7.1] Email Intelligence** — Scan inbox (3-day window), extract commitments and requests, identify deadlines
- **[7.2] Cross-Source Consolidation** — Aggregate from email + meetings + JIRA, deduplicate, reconcile conflicts
- **[7.3] Prioritisation** — Apply due date urgency, requester importance, project priority; surface overdue items
- **[7.4] Completion Detection** — Monitor sent folder, JIRA changes; confirm with user if uncertain
- **[7.5] Reminder Generation** — Calculate timing, generate content, deliver via preferred channel
- **[7.6] Checklist Interface** — Present daily list, allow tick-off, track completion rate

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

## Section 3: Delegation Suitability Matrix

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
| Meeting notes draft | M | L | M | M | H | Human-Led + Support |
| Meeting notes send | H | H | H | L | H | Human Only |

#### Stream 2: Status Reports

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Data collection | H | H | H | L | L | Fully Agentic |
| Metric calc | H | H | H | L | L | Fully Agentic |
| Reconciliation | M | M | M | M | M | Agent-Led + Oversight |
| Narrative | L | L | M | H | M | Human-Led + Support |
| Exec summary | M | L | M | H | H | Human-Led + Support |
| Distribution | H | H | H | L | L | Fully Agentic |

#### Stream 3: Governance Monitoring (Wave 2)

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Standards assessment | H | M | H | M | M | Agent-Led + Oversight |
| Gap detection | M | M | M | M | H | Agent-Led + Oversight |
| Severity classification | M | L | M | H | H | Human-Led + Support |
| Scorecard generation | H | H | H | L | L | Fully Agentic |
| Escalation drafting | M | L | M | M | H | Human-Led + Support |
| Escalation send | H | H | H | L | H | Human Only |
| Resolution tracking | H | H | H | L | L | Fully Agentic |

#### Stream 4: Stakeholder Communications (Wave 2)

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Trigger detection | H | M | H | M | M | Agent-Led + Oversight |
| Context gathering | H | H | H | L | L | Fully Agentic |
| Draft generation | L | L | M | H | H | Human-Led + Support |
| Audience adaptation | M | L | M | H | M | Human-Led + Support |
| Communication send | H | H | H | L | H | Human Only |

#### Stream 5: Change Request Management

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Trigger detection | H | M | H | M | M | Agent-Led + Oversight |
| Impact assessment draft | L | L | M | H | H | Human-Led + Support |
| Approval routing | H | H | H | L | M | Agent-Led + Oversight |
| Status tracking | H | H | H | L | L | Fully Agentic |
| RAID update proposal | M | L | M | H | H | Human-Led + Support |
| Closure notification draft | L | L | M | H | M | Human-Led + Support |
| Communication send | H | H | H | L | H | Human Only |

#### Stream 6: Strategic Resourcing (Wave 3)

| Task | Input | Det. | Tools | Except. | Risk | Archetype |
|---|---|---|---|---|---|---|
| Resource tracking | H | H | H | L | L | Fully Agentic |
| Skills inventory | H | H | M | M | L | Fully Agentic |
| Gap detection | M | M | M | M | M | Agent-Led + Oversight |
| Match recommend | M | L | M | H | H | Human-Led + Support |
| Resource commit | L | L | M | H | H | Human Only |

#### Stream 7: Personal Task Management (Wave 3)

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

## Section 4: Volume × Value Analysis

### Full Stream Scoring (All Workstreams)

| Stream | Vol | Non-Det | Score | Wave | Justification |
|---|---|---|---|---|---|
| 1. Meeting Intelligence | 5 | 5 | 25 | ★ Wave 1 | Every meeting; RAID classification is judgment-intensive |
| 2. Personal Task Mgmt | 5 | 4 | 20 | Wave 3 | Daily; email commitment extraction requires reading intent — deferred due to NLP complexity |
| 3. Proactive Risk Monitoring | 4 | 5 | 20 | Wave 3 | Synthesising weak signals requires judgment — deferred pending data quality |
| 4. Governance Monitoring | 4 | 5 | 20 | ★ Wave 2 | Evidence-based checks use Wave 1 RAID outputs; addresses directly-cited governance inconsistency |
| 5. Status Reports | 4 | 4 | 16 | ★ Wave 2 | High volume; narrative synthesis, financial analysis + audience adaptation |
| 6. **Change Request Mgmt** | **4** | **4** | **16** | **★ Wave 2** | **Present in 100% of PMO role specifications reviewed; same score as Status Reports and Stakeholder Comms; original deferral reason (no stakeholder quote) negated by job spec evidence** |
| 7. Stakeholder Communications | 4 | 4 | 16 | ★ Wave 2 | Builds on Wave 1 + 2 context; trigger-detection and drafting under pressure is high-pain |
| 8. Lessons Learned | 3 | 5 | 15 | Wave 4 | Lower volume; pattern recognition across projects is highly non-deterministic |
| 9. Strategic Resourcing | 3 | 4 | 12 | Wave 3 | Trade-off analysis; deferred pending data quality pre-condition; split into admin (RPA-adjacent) and strategic matching components |
| 10. Benefits Tracking | 3 | 4 | 12 | Wave 3 | Present in 83% of PMO role specifications; depends on structured project data from earlier waves |
| 11. Dependency Tracking | 3 | 4 | 12 | Wave 4 | Cross-project impact assessment; medium volume |
| 12. Project Mobilisation / PID | 2 | 3 | — | Wave 4 | PID in 67% of specs; Project Drive org in 100%; one-off per project; templates from earlier waves required |
| 13. Onboarding Access | 3 | 2 | 6 | RPA | Mostly rule-based; RPA handles the majority |

---

### Quadrant

```
NON-DETERMINISM
        Low ◄───────────────────────────────► High

 High 5 ┼───────────────┬────────────────────────┐
         │               │ ★ MEETING INTELLIGENCE │
         │               │                        │
    V 4 ┼───────────────┼────────────────────────┤
    O    │               │ ★ PERSONAL TASKS       │
    L    │               │   PROACTIVE RISK        │
    U    │               │   GOVERNANCE MONITORING│
    M    │               │ ★ STATUS REPORTS       │
         │               │   CHANGE REQUESTS      │
    E    │               │   STAKEHOLDER COMMS    │
      3 ┼───────────────┼────────────────────────┤
         │               │   LESSONS LEARNED      │
         │               │ ★ RESOURCING           │
         │               │   DEPENDENCY TRACKING  │
    Low  ├───────────────┼────────────────────────┤
         │ ONBOARDING    │                        │
       1 ┼───────────────┴────────────────────────┘

★ = Selected for Wave 1
```

---

### Top 5 Selected — Reasoning

**Why these five?**

| Stream | Score | Reason for Selection |
|---|---|---|
| Meeting Intelligence | 25 | Highest score; every meeting; foundation for all other streams; directly stakeholder-quoted |
| Status Reports | 16 | Universal PMO pain; immediately demonstrable; self-contained — works without other streams; directly stakeholder-quoted |
| Governance Monitoring | 20 | Wave 1 generates the RAID logs and decision records needed as evidence; addresses directly-cited governance inconsistency problem; no generic tool does this |
| Stakeholder Communications | 16 | Builds directly on Wave 1 and Wave 2 outputs for context; drafting under pressure is a high-pain PMO task; stakeholder management explicitly cited |
| Change Request Management | 16 | Present in 100% of real PMO role specifications reviewed (6/6 AIB roles); same score as Status Reports and Stakeholder Communications; original deferral reason (no stakeholder quote) was negated by job spec evidence confirming it is a core daily PMO task, not an occasional one |

**All five are grounded in direct evidence and build logically on each other.**

**Why Personal Task Management and Strategic Resourcing remain in Wave 3:**

| Stream | Score | Why Deferred to Wave 3 |
|---|---|---|
| Personal Task Management | 20 | Email commitment extraction (distinguishing hard vs soft commitments) requires complex NLP. Completion detection via sent folder monitoring is fragile. Better once Wave 1–2 RAID context is mature. |
| Strategic Resourcing | 12 | Matching recommendations depend entirely on a clean, current skills inventory — a data quality pre-condition that is often not met on day one. Wave 3 once data foundations are in place. Routine resource admin (onboarding/offboarding tracking) is a separate, simpler component that may be addressed via RPA/Hybrid earlier. |
| Benefits Tracking | 12 | Requires structured benefits baseline data from PIDs and a body of project records from earlier waves. Wave 3 once data quality is established. |

**Why not the others in Waves 1–2?**

| Stream | Score | Why Deferred |
|---|---|---|
| Proactive Risk Monitoring | 20 | Dependent on project data being clean and current. No stakeholder quote. Wave 3 once data foundations are established. |
| Lessons Learned | 15 | Needs a body of structured data from earlier streams. **High-priority Wave 4** — explicitly called out in Problem Statement as a core pain (knowledge loss when PMs rotate). |
| Dependency Tracking | 12 | Requires a mature, connected data model across projects. Wave 4. |
| Project Mobilisation / PID | — | One-off per project; meaningful quality depends on established templates from earlier waves. Wave 4. |
| Onboarding Access | 6 | Core work handled by RPA. AI adds value only at the exception margin. |

---

### Economics

| Value Driver | Calculation | Annual |
|---|---|---|
| Meeting follow-up time freed | 40 hrs/mo × 50% × 12 × $75 | ~$18,000 |
| Status report time freed | 50 reports/mo × 35 min saved × 12 × $75/hr | ~$26,250 |
| Governance monitoring (audit findings avoided) | Qualitative — one avoided audit finding or escalation failure is significant | TBD |
| Stakeholder communications drafting | 20 comms/mo × 30 min saved × 12 × $75/hr | ~$4,500 est. |
| Change request impact assessment | 10 CRs/mo × 40 min saved × 12 × $75/hr | ~$6,000 est. |
| Personal task management *(Wave 3)* | 1 hr/day × 50% × 220 days × $75 | ~$8,250 |
| Strategic resourcing *(Wave 3)* | Qualitative — cost of one wrong placement | TBD |
| Reduced dropped items / decision disputes | Qualitative | TBD |
| **Quantifiable total (Wave 1–2)** | | **~$54,750** |

---

### Sequencing

| Wave | Streams | Rationale |
|---|---|---|
| 1 | Meeting Intelligence | Highest score; builds the data and integration foundation all subsequent waves depend on |
| 2 | Status Reports + Governance Monitoring + Stakeholder Communications + Change Request Management | Leverage Wave 1 RAID and decision outputs; governance checks, comms drafting, and change impact assessment are most valuable once structured project data exists; Change Request Management confirmed as universal PMO task (100% of role specifications) |
| 3 | Personal Task Management + Strategic Resourcing + Proactive Risk Monitoring + Benefits Tracking | Require mature data foundations and richer AI context from Waves 1–2 |
| 4 | Lessons Learned + Dependency Tracking + Project Mobilisation / PID | Require mature data across the full portfolio; Lessons Learned is high priority within this wave |

---

## Section 5: Agent Purpose Document

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
| Meeting notes drafts | Structured notes — narrative summary, decisions, and RAID action list at foot — for human review and distribution to all invited participants via Outlook |
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
| Meeting notes sent without approval | 0 |
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
  • Meeting notes content

LEVEL 1 — HUMAN DECIDES → AGENT SUPPORTS
  • Ambiguous R vs I classification
  • Decision vs proposal distinction
  • Severity assessment

LEVEL 0 — HUMAN ONLY
  • Sending meeting notes
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

## Section 6: System/Data Inventory

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
| Get attendees (actual) | GET | `/me/onlineMeetings/{id}/attendanceReports` |
| Get invitees (full list) | GET | `/me/events/{eventId}` (calendar event — participants array) |

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

## Section 7: Discovery Questions

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
| 9 | "Meeting notes go to all invited participants — not just those who attended. Is the calendar invite list maintained accurately, and are there meeting types where this distribution should be restricted?" | Defines distribution scope, invitee list reliability, and any exclusions |
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

#### D. Meeting Notes & Distribution

| Question | Design Impact |
|---|---|
| "What goes in good meeting notes? What structure and tone do you expect?" | Meeting notes template and format |
| "Are there meeting types where notes shouldn't be distributed to all invitees (e.g. 1:1s, HR discussions)?" | Scope exclusions and distribution rules |
| "If the agent drafted notes with a mistake, when would you catch it?" | Review workflow timing |
| "Is the calendar invite list always accurate — are there cases where people are invited but shouldn't receive notes?" | Distribution list reliability |

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

## Section 8: Agent Configuration Reference

### Project Intent

AI agent for PMO meeting intelligence. Transforms meeting transcripts into structured RAID entries (Risks, Actions, Issues, Decisions) with owners, due dates, and system updates.

**Objective:** Every meeting produces tracked results — no lost actions, documented decisions, current JIRA.

---

### Non-Negotiables

> 🛑 **No RAID Entries Without Approval**
> RAID logs are governance artifacts. All entries require explicit human approval. Violation = GOVERNANCE BREACH.

> 🛑 **No Meeting Notes Without Approval**
> Meeting notes are distributed to all invited participants and represent the organisation. Violation = UNAUTHORIZED COMMUNICATION.

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
- All meeting notes require human approval before distribution — no exceptions
- Meeting notes distributed to full invitee list from calendar invite, not just transcript attendees
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
| Meeting notes template | PMO Lead |

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

*Relates to: pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1-meeting-intelligence.md, pmo-ai-differentiation.md*
