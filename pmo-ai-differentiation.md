# PMO AI Tool — Why This, Not What You Already Have

A response to the most important challenge in any pitch:

> *"We already have Copilot / Teams / an internal AI tool. Why do we need this?"*

This document explains what existing tools already cover, where the genuine gap is, and what the EPAM PMO AI Platform does that those tools do not.

---

## The EPAM product distinction

Before addressing individual workstreams, the most important point of differentiation is architectural:

**This is an EPAM-built standalone web application — not a Microsoft Teams tab, not a Copilot extension, not a plugin.**

It integrates *with* Microsoft tools (Teams, SharePoint, Outlook, MS Project) and JIRA as data sources, but the platform itself is designed, built, hosted, and roadmapped by EPAM. This matters for three reasons:

1. **It cannot be replicated by a Microsoft product update.** A Copilot feature release in six months does not obsolete this platform, because this platform does things Copilot architecturally cannot — system write-back with governed approval workflows, RAID-specific taxonomy, cross-source synthesis with audit trail.
2. **EPAM controls the roadmap.** New capabilities (Governance Monitoring, Stakeholder Communications, Lessons Learned) are delivered by EPAM on EPAM's timeline, not dependent on Microsoft's product decisions.
3. **It is a commercial EPAM asset.** The platform, its IP, and its client relationships belong to EPAM — not to a third-party tool vendor.

---

## The honest framing

Several capabilities in this tool are available in some form today through Microsoft Copilot for M365, Zoom AI Companion, Power BI, or an internal AI tool. We should not pretend otherwise.

The differentiation is not in reading a meeting or pulling a number from a spreadsheet. It is in **what happens after** — turning AI output into governed, traceable, approved updates to project management systems, with a consistent workflow that runs whether or not someone remembers to trigger it.

Generic AI gives you better output. This EPAM platform gives you a managed PMO process.

---

## Work Stream 1: Meeting Intelligence

### What existing tools already do

| Tool | What it covers |
|---|---|
| Microsoft Copilot for M365 | Meeting summaries, action item lists, meeting notes drafts, speaker attribution |
| Zoom AI Companion | Meeting summaries, action items, smart chapters |
| Internal AI (ChatGPT / Claude with transcript) | Summaries, action extraction, decision lists, draft notes |

If summarisation and action extraction were all this stream did, it would be very hard to justify. That capability is effectively commoditised.

### Where the genuine gap is

**1. RAID classification, not just action items**

Generic AI extracts "action items." It does not classify items into the formal PMO taxonomy of Risks, Actions, Issues, and Decisions — and it does not know the governance-critical difference between a Risk (a future threat that needs mitigation planning) and an Issue (a current problem needing immediate resolution). It does not assign confidence scores, and it has no concept of which items to hold for human review versus which to progress automatically.

**2. System write-back with a governed approval workflow**

Copilot gives you text. This tool proposes structured entries into your SharePoint RAID log in the correct schema, routed through a defined approval chain. It matches actions to specific JIRA tickets and proposes the update against the right ticket. No generic AI tool has knowledge of your RAID log schema, your JIRA project structure, or your approval hierarchy.

**3. Governance controls and audit trail**

Nothing gets written to a record or sent externally without explicit human approval. Every proposal is logged with its confidence score, the PMO's decision, and who approved it — at the individual RAID item level. This produces an auditable record of AI-assisted governance decisions. Copilot has no equivalent. It outputs text; what happens next is up to the user, and often nothing happens.

**4. Traceability to source**

Every RAID item is traced back to the meeting ID, timestamp, and speaker. If a decision is ever disputed — *"I never agreed to that"* — the PMO can point to the exact moment in the recording it came from. Generic summaries do not do this at the individual item level.

**5. Meeting notes structure and distribution to all invitees**

Copilot produces a summary for the person who asked for it. This tool produces structured meeting notes — narrative summary, decisions, and RAID action list at the foot — and distributes them via Outlook to every person who was *invited* to the meeting, not just those who attended. The invitee list is retrieved from the calendar invitation. People who could not attend receive the same governed record as those who were present. No generic AI tool manages this distribution step.

**6. Consistency**

A PMO using Copilot or an internal AI uses it when they remember to, with no standard process and no guaranteed connection to downstream systems. This tool runs as a standardised automated workflow for every meeting — the consistency is part of the governance value.

### The one-line answer for the pitch

> *"Copilot gives you better notes for yourself. This gives you an automated PMO governance workflow — RAID classification, system write-back, approval routing, structured minutes sent to all invitees, and a full audit trail. Those are different things."*

---

## Work Stream 2: Status Reports & Scorecards

### What existing tools already do

| Tool | What it covers |
|---|---|
| Power BI / Tableau | Automated data collection, RAG dashboards, scheduled distribution |
| Microsoft Copilot | Narrative generation from data, executive summaries |
| JIRA built-in reporting | Project-level metrics and burndown charts |

If the organisation already has Power BI and Copilot, they have automated data collection and can generate narratives. The challenge is valid here too.

### Where the genuine gap is

**1. Cross-source synthesis informed by meeting intelligence**

A Power BI dashboard pulls numbers. It does not know that a milestone is amber *because* a vendor risk was raised in last Tuesday's meeting and an action owner is blocked. The PMO AI tool synthesises data signals *with* the RAID items, decisions, and flagged risks from Stream 1 — producing a narrative that explains not just what the numbers show, but why, grounded in what was actually discussed in meetings.

**2. Inconsistency across sources**

Real-world project data is rarely clean. JIRA shows one status, MS Project shows another, SharePoint shows a third. Generic tools pull each source independently. This tool reconciles discrepancies, flags contradictions, and brings them to the PMO before the report is written — rather than the PMO discovering the inconsistency after the report has been sent to senior stakeholders.

**3. Audience-adapted narrative at scale**

Writing different versions of the same report for the project team, the programme director, and the executive committee takes time and judgment. The AI generates audience-adapted narratives from the same underlying data, with the PMO reviewing rather than writing.

**4. Governed distribution**

Nothing is distributed without PMO approval. The approval step is built into the workflow — it cannot be bypassed. Reports produced by Power BI or Copilot have no equivalent governance gate before distribution.

### The one-line answer for the pitch

> *"Power BI tells you what the numbers are. This tells you what they mean — drawing on meeting intelligence, resolving data conflicts, and producing audience-adapted narratives that a PMO approves before they go out."*

---

## Work Stream 3: Governance Monitoring

### What existing tools already do

| Tool | What it covers |
|---|---|
| SharePoint / document libraries | Stores governance documents — but does not check whether they exist or are current |
| Audit tools (e.g. manual checklists) | Periodic point-in-time governance reviews, manually triggered |
| Microsoft Copilot | Can answer questions about specific documents if asked — but requires manual prompting |

There is no tool on the market that continuously and automatically checks whether active projects are meeting their governance standards. Governance today is either periodic (a review conducted monthly or quarterly), reactive (triggered by a problem), or dependent on a specific individual's diligence.

### Where the genuine gap is

**1. Continuous automated checking versus periodic manual review**

Manual governance reviews happen when someone schedules one — which means they happen less often than they should, and gaps accumulate between reviews. This tool checks every active project against every applicable standard on a weekly cadence, automatically. Gaps are surfaced the week they appear, not in the next quarterly audit.

**2. Evidence-based checking using Wave 1 outputs**

Because Wave 1 (Meeting Intelligence) generates structured RAID logs and decision records, Governance Monitoring has real, traceable evidence to check against. A governance check for "has a risk log been maintained?" can be answered by reading the RAID log entries Wave 1 has been writing — not by asking someone to go and check a SharePoint folder manually.

**3. Portfolio-wide visibility**

A PMO managing multiple projects cannot keep governance standards in their head for every project simultaneously. This tool monitors the whole portfolio and surfaces a governance scorecard across all active projects, so the PMO can see which projects need attention without manually reviewing each one.

**4. Gaps flagged before they become audit findings**

The first time most organisations discover governance gaps is during an audit or a steering committee review that goes badly. By then it is too late to fix without embarrassment or escalation. This tool surfaces gaps early — when there is still time to resolve them quietly.

**5. Consistent standards across projects and PMOs**

Governance quality today depends on which PMO is conducting the review and how rigorous they are. This tool applies the same standards to every project, every week, regardless of who is working on it.

### The one-line answer for the pitch

> *"There is no tool that checks whether your projects are actually meeting their governance standards — until now. This does it automatically, every week, across every project, using the evidence Wave 1 generates."*

---

## Work Stream 4: Stakeholder Communications

### What existing tools already do

| Tool | What it covers |
|---|---|
| Microsoft Copilot | Can draft an email if you describe what you want it to say |
| Outlook templates | Static templates for recurring communication types |
| Internal AI (ChatGPT / Claude) | Can draft communications from prompts, but requires the user to supply all context |

The tools for *writing* communications exist. The problem is not the writing. The problem is knowing what to write, when to write it, and having the right information assembled at the moment you need it — which is usually the moment when a project has just escalated and the PMO is already stretched.

### Where the genuine gap is

**1. Trigger detection — the tool knows when a communication is needed**

Copilot drafts emails you ask it to draft. This tool detects the events that should trigger a stakeholder communication — a RAG status change, a milestone slip, a risk escalation — and initiates the draft automatically. The PMO does not have to remember that this event requires a sponsor notification; the tool does.

**2. Context awareness — drawn from live project data**

When an escalation notice is needed, this tool has already assembled the relevant context: what changed, when, what the RAID log says about the underlying cause, what the RAG history shows, and what actions are already in place. A generic AI tool requires the PMO to supply all of this. The difference between a draft that needs extensive editing and one that can be sent with minor changes is whether the AI had the right information to start with.

**3. Audience adaptation built in**

The same trigger event may require a brief escalation note to an executive sponsor, a more detailed briefing for the programme director, and a different framing for the project team. This tool generates separate, appropriately toned drafts for each recipient type from the same underlying context. Writing three versions manually — or prompting a generic AI three times with different instructions — is exactly the kind of time pressure a PMO does not need at the moment a project escalates.

**4. Governed sending — approval built into the workflow**

No communication is sent without explicit PMO approval. The draft is presented for review in the EPAM platform, with inline editing available, before any send action is accessible. Generic AI tools have no equivalent — they output text, and what happens next is up to the user. In a regulated financial services environment, a communication sent without review is a governance risk, not just an inconvenience.

### The one-line answer for the pitch

> *"Copilot drafts the email you ask it to write. This drafts the email you should be writing — triggered automatically when a project escalates, assembled from live project data, and routed through approval before it reaches a sponsor."*

---

## Summary

| Stream | Wave | What existing tools give you | What the EPAM platform adds |
|---|---|---|---|
| Meeting Intelligence | 1 | Better notes and action lists (Copilot) | RAID classification, system write-back, structured minutes to all invitees, approval workflow, full audit trail |
| Status Reports | 2 | Data dashboards and narrative drafts (Power BI + Copilot) | Cross-source reconciliation, meeting-informed narrative, financial variance analysis, governed distribution |
| Governance Monitoring | 2 | Periodic manual reviews, document storage (SharePoint) | Continuous automated checking against governance standards, evidence-based gap detection, portfolio scorecard |
| Stakeholder Communications | 2 | Email drafting tools that require manual prompting (Copilot) | Trigger-aware drafting from live project data, audience adaptation, approval-gated sending |

**Wave 3 (planned):** Personal Task Management (automatic cross-source commitment consolidation) and Strategic Resourcing (proactive gap alerts with match recommendations) extend the platform further once the Wave 1–2 data foundations are in place.

**The common thread:** existing tools produce output. The EPAM PMO AI Platform produces *governed outcomes* — with human approval built into every step that matters, delivered as an EPAM-owned, EPAM-hosted product that no Microsoft update can replace.

---

## What PMOs on Client Site Actually Said

The following is drawn from surveys and interviews conducted with PMOs across financial services clients (MUFG, Citi, and others). These responses validate the differentiation above and provide direct evidence for the pitch.

**On current AI tools:**

> *"I use Copilot on Teams where meetings are recorded. It can summarise the call and I can ask for specific details. It is not always accurate but definitely helps with minutes."*

> *"Copilot in emails, but this is a separate application to emails and would be good if it came up as a prompt when writing emails."*

> *"Outputs not sufficiently tailored to PMO needs."* — Cited as a challenge by multiple respondents.

These responses confirm that generic AI tools are being used but falling short — inaccurate, not integrated into the workflow, and not tailored to PMO-specific needs. This is the gap the tool fills.

**On where AI should go further:**

> *"Automation of basic admin tasks and/or repetitive tasks would save significant time — Minutes and Actions taking, Project descriptions, risks, benefits descriptions. Email automations. Collating information that is saved in various systems in order to be included in a report."* — ADC

> *"AI tooling to analyse complex and large financial data would provide valuable insights."* — Caitlin

> *"Citi needs predictive PMOs — do not view them as advisory, can do more with AI than they are doing. Health scorecards, steering committee reports."* — Chirantan interview

> *"Share resource calendar, capacity utilisation of shared resources and predict availability. Where we map resources are going to be free — link in resource supply with client demand."* — Chirantan interview

**On governance and oversight:**

All respondents who answered Q9 either strongly agreed or agreed that *"clear governance or guidance on AI use would be helpful"* and that *"training would improve effective use."* This validates the human-in-the-loop design of the tool — PMOs want AI assistance but with clear controls, not autonomous AI acting on their behalf.

**On stakeholder management:**

> *"A key aspect of the PMO role is stakeholder management. AI can assist in saving time on routine tasks and providing valuable insight, but this should not be the only focus on improving PMO delivery."* — ADC and Caitlin (independently)

This is an important nuance for the pitch: the tool is positioned as freeing PMO time *for* stakeholder management, not replacing it.

---

*Version: v1.1 | Relates to: pmo-ai-workflows-explained.md, pmo-ai-tool-deliverables.md*
