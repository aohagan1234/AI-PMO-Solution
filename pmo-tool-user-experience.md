# PMO AI Tool — How It Works & User Experience

A walkthrough of how a PMO interacts with the tool day-to-day.

---

## What It Is

The tool is an **EPAM-built web application** — PMOs open a browser, log in with their existing Microsoft credentials (no separate password, no installation), and everything they need is in one place. It works on laptop, tablet, or phone.

It connects to the tools PMOs already use — Microsoft Teams, SharePoint, Outlook, JIRA — and pulls everything together into a single governed workspace. The PMO doesn't manage multiple systems. The tool does that for them.

---

## A Day in the Life

### After the Meeting Ends (Same Day)

A meeting ends at 3 PM. Teams transcribes the recording. Within minutes of the transcript being ready, the tool processes it — RAID items extracted, JIRA updates prepared, follow-up emails drafted.

By 3:20 PM, the PMO gets a Teams notification:

```
📋  Project Apex Steering just processed
    6 items ready for your review
    Meeting ended 3:00 PM  ·  Ready at 3:18 PM

    [Review now →]    [Review in morning queue →]
```

If the PMO is free, they click **Review now** and clear the items before end of day. If they're still in back-to-back meetings, they click **Review in morning queue** — or simply ignore it — and the items wait in their dashboard.

Either way, nothing is lost and nothing requires action that evening. The tool holds everything until the PMO is ready.

---

### The Home Dashboard

The next morning — or whenever they next open the tool — the first thing they see is a single view of everything needing their attention. Any meetings reviewed same-day are already cleared. Anything deferred, or processed after they logged off, is waiting in the queue. Nothing is buried. Nothing requires searching.

```
┌──────────────────────────────────────────────────────────┐
│  Good morning, Sarah              Tuesday 3 June 2026    │
├─────────────────┬──────────────────┬─────────────────────┤
│  REVIEW QUEUE   │   MY TASKS       │   ALERTS            │
│                 │                  │                     │
│  3 meetings     │  8 tasks today   │  2 resource gaps    │
│  14 items       │  2 overdue  ⚠️   │  1 report due Fri   │
│  pending        │                  │                     │
│  [Open →]       │  [Open →]        │  [View →]           │
└─────────────────┴──────────────────┴─────────────────────┘
```

---

## The Four Core Interactions

---

### 1. Meeting Review Queue

The tool presents each AI-proposed item one at a time — one decision per card. No walls of text, no re-reading notes.

```
┌──────────────────────────────────────────────────────────┐
│  Project Apex Steering  │  Item 1 of 6  │  🟠 RISK       │
├──────────────────────────────────────────────────────────┤
│  Vendor delivery timeline at risk              87% conf. │
│                                                          │
│  Vendor may need an additional week due to               │
│  staffing issues, pushing the 15 June milestone.         │
│                                                          │
│  📍 James Chen, 23:14 —                                  │
│     "the vendor mentioned they're struggling with        │
│      staffing and might need another week"               │
│                                                          │
│  Owner: James Chen    Severity: High                     │
│                                                          │
│  [✓ Approve]    [✏ Modify]    [✗ Reject]                 │
└──────────────────────────────────────────────────────────┘
```

Each card shows:
- **What type of item it is** — Risk, Action, Issue, or Decision
- **The AI's confidence score** — items below 80% are flagged in amber/red for extra care
- **The exact source quote** — traceable to the speaker and timestamp in the transcript
- **Proposed owner and severity**
- **Three choices** — approve, modify, or reject

The PMO works through all 14 items across three meetings in about 10–15 minutes. Every approved item is written to the SharePoint RAID log and JIRA automatically. The meeting notes — covering what was discussed, what was decided, and the full action list at the foot — are drafted and ready to send to all invited participants with one click.

**What happens without the tool:** 60–90 minutes of re-reading notes, guessing at owners, manually updating JIRA, writing up minutes from scratch — often the day after the meeting, and often not sent to everyone who was invited.

---

### 2. Governance Dashboard

After clearing the review queue the PMO opens the governance dashboard. Every project in the portfolio has been checked overnight against the defined governance standards — documentation in place, approvals obtained, gates passed. Gaps are surfaced automatically.

```
┌──────────────────────────────────────────────────────────┐
│  Governance  │  Tuesday 3 June          3 projects flagged│
├──────────────────────────────────────────────────────────┤
│  🔴  Project Apex                        2 gaps           │
│      ❌  Steering committee pack — 3 days overdue         │
│      ❌  Change request CR-014 — no sign-off recorded     │
├──────────────────────────────────────────────────────────┤
│  🟡  Platform Migration                  1 gap            │
│      ⚠️  Risk review overdue — last conducted 6 weeks ago │
├──────────────────────────────────────────────────────────┤
│  ✅  Risk & Governance Weekly            All clear        │
└──────────────────────────────────────────────────────────┘
```

The PMO clicks into Project Apex. Each gap shows what is missing, how long it has been outstanding, and what governance rule it breaks. They resolve each one — escalating to a sponsor, noting an action, or dismissing with a reason. Nothing is auto-remediated.

**What happens without the tool:** Governance gaps accumulate silently until an audit or steering committee review surfaces them. By then it is too late to resolve without embarrassment or escalation.

---

### 3. Report Approval

On report day, the tool has already pulled all the data and written the first draft. The PMO doesn't collect data or write the report — they review and approve it.

```
┌──────────────────────────────────────────────────────────┐
│  Status Report  ·  Project Apex  ·  Week ending 6 Jun    │
│  Data pulled: 08:15 today  ·  3 audience versions ready  │
├──────────────────────────────────────────────────────────┤
│  [Executive]  [Steering Group ✓]  [Project Team]         │
├──────────────────────────────────────────────────────────┤
│  RAG:  🔴 RED  (was 🟡 AMBER)   ⚠️ deterioration flagged │
│                                                          │
│  Project Apex has moved to Red this week following       │
│  vendor disclosure of a potential one-week delay to      │
│  the 15 June integration milestone. A risk has been      │
│  logged and James Chen is engaging the vendor for a      │
│  revised timeline by 5 June. Budget remains within       │
│  tolerance (+2% variance).                               │
│                                                          │
│  [✏ Edit]    [✓ Approve & Distribute]                   │
└──────────────────────────────────────────────────────────┘
```

The tool generates three versions of the same report — one for the executive, one for the steering group, one for the project team — each tailored to that audience. The PMO reviews each version, makes any edits, and approves. Distribution to the right people happens automatically via Outlook.

Nothing is sent without approval. If a RAG status has deteriorated since last week, it is flagged prominently so it cannot be missed.

**What happens without the tool:** 45 minutes per report, manually pulling data from three systems, writing multiple versions, copying into email and sending individually.

---

### 4. Stakeholder Communication Draft

Project Apex moved to Red RAG status this morning — confirmed in the status report after the vendor risk was flagged in yesterday's meeting review. Before the PMO has written a single word, the tool has drafted an escalation notice for the programme director.

```
┌──────────────────────────────────────────────────────────┐
│  Draft Ready  ·  Escalation Notice  ·  Project Apex      │
│  Triggered by: RAG moved Red  ·  3 Jun 2026             │
├──────────────────────────────────────────────────────────┤
│  To: David Murphy (Programme Director)                   │
│  Subject: Project Apex — Status change to Red            │
│                                                          │
│  Project Apex has moved to Red this week following       │
│  vendor disclosure of a potential one-week delay to the  │
│  15 June integration milestone. James Chen is engaging   │
│  the vendor for a revised timeline by 5 June. Budget     │
│  remains within tolerance (+2% variance).                │
│                                                          │
│  No immediate action required from you at this stage —  │
│  we will provide an update by 6 June.                    │
│                                                          │
│  [✏ Edit]    [✓ Send via Outlook]    [✗ Discard]        │
└──────────────────────────────────────────────────────────┘
```

The tool knows the project context, the risk that triggered the change, and who the programme director is. The PMO reads the draft, adjusts the tone if needed, and sends in under two minutes. The AI never sends independently.

**What happens without the tool:** The PMO notices the RAG change, starts an email from scratch, refers back to meeting notes for the detail, and tries to remember the sponsor's address. Ten minutes later, a rushed escalation goes out — or doesn't, because something else came up first.

---

## What the Morning Looks Like

| Task | Without the Tool | With the Tool |
|---|---|---|
| Meeting follow-up (3 meetings) | 60–90 min re-reading notes | 10–15 min in the review queue |
| RAID log updated | Later that day, or never | Same day if reviewed promptly, or first thing next morning |
| JIRA updated | Manual, often forgotten | Automatic on approval |
| Meeting notes sent to all invitees | Written from scratch, often delayed, often sent only to attendees | Draft ready, sent to all invited participants in 2 minutes |
| Governance gaps | Found in audits or escalations, too late | Every project checked weekly; gaps flagged automatically |
| Escalation notices | Written from scratch under pressure | Drafted automatically on trigger; PMO reviews and sends |
| Status report | 45 min to write, multiple manual versions | 10 min to review and approve |

---

## The Principle Behind It

The PMO is not replaced. Every decision that matters — approving a RAID entry, confirming a resource, signing off a report, sending a communication — still requires a human.

What changes is everything around those decisions. The tool handles the gathering, classifying, drafting, matching, and consolidating. The PMO handles the judging, approving, and acting.

**The tool does the work that shouldn't need a PMO. The PMO does the work that only a PMO can do.**

---

*Version: v1.0 | Relates to: pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1.md*
