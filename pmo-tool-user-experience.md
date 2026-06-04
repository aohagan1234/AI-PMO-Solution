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

By 4 PM, the PMO gets a Teams notification:

```
📋  3 meetings processed overnight
    Project Apex Steering       →  6 items to review
    Platform Migration Stand-up →  3 items to review
    Risk & Governance Weekly    →  5 items to review

    [Open Review Queue →]
```

They click the link and land directly in the tool.

---

### The Home Dashboard

The first thing they see is a single view of everything needing their attention today. Nothing is buried. Nothing requires searching.

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

The PMO works through all 14 items across three meetings in about 10–15 minutes. Every approved item is written to the SharePoint RAID log and JIRA automatically. The follow-up email is drafted and ready to send with one click.

**What happens without the tool:** 60–90 minutes of re-reading notes, guessing at owners, manually updating JIRA, writing emails from scratch — often the day after the meeting.

---

### 2. Daily Task Checklist

After clearing the review queue the PMO opens their task list. Every commitment they have made — across email, meetings, and JIRA — is consolidated into one prioritised list. They did not have to build this list. It built itself.

```
┌──────────────────────────────────────────────────────────┐
│  My Tasks  │  Tuesday 3 June                  8 tasks   │
├──────────────────────────────────────────────────────────┤
│  ⚠️  OVERDUE                                              │
│  [ ]  Send budget update to James             2 Jun      │
│       📧  Email commitment                               │
├──────────────────────────────────────────────────────────┤
│  TODAY                                                   │
│  [ ]  Update Project Apex RAID log            3 Jun      │
│       🤝  Meeting action  ·  Project Apex SC             │
│  [ ]  Review UAT test cases                  3 Jun      │
│       📧  Email from Sarah OBrien                        │
│  [ ]  Confirm resource for Platform Mig       3 Jun      │
│       🔔  Resource alert  ·  gap in 27 days              │
│  [ ]  Steering committee pack — Apex          5 Jun      │
│       📋  Report due                                     │
└──────────────────────────────────────────────────────────┘
```

Each task shows where it came from:
- 📧 Email commitment extracted from inbox
- 🤝 Meeting action item from the review queue
- 📋 JIRA ticket assigned to them
- 🔔 Resource or governance alert

They tick items off as they go. Completions are auto-detected where possible — if they send the email, the task closes itself. Reminders arrive via Teams or Outlook for anything approaching its due date.

**What happens without the tool:** Two hours a day scanning inbox, re-reading meeting notes, and checking the JIRA board — then still missing things.

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

### 4. Resource Gap Alert

The alert on the home dashboard flagged a resource gap 27 days out on Platform Migration. The PMO clicks through:

```
┌──────────────────────────────────────────────────────────┐
│  Resource Gap  ·  Platform Migration  ·  27 days         │
│  Senior PMO Analyst needed  ·  available from 30 June    │
├──────────────────────────────────────────────────────────┤
│  ⭐  David Walsh              Best overall fit           │
│      ✅ Available 25 Jun                                  │
│      ✅ 8 years PMO experience                           │
│      ✅ Financial services sector background             │
│      ⚠️  Currently on Project Apex — confirm release     │
│                                                          │
│  2.  Emma Byrne               Good skills, later start   │
│      ✅ Strong JIRA / Agile delivery background          │
│      ⚠️  Not available until 14 July — 2 weeks late      │
│      ⚠️  No prior financial services client experience   │
│                                                          │
│  [Confirm David Walsh]    [Confirm Emma Byrne]           │
│  [View full resource pool]  [Flag — no suitable match]   │
└──────────────────────────────────────────────────────────┘
```

The tool has already done the matching work — it knows who is available, what their skills are, and what the trade-offs are between candidates. The PMO reads the recommendation, makes a call, and confirms. The resource tracker updates automatically.

**What happens without the tool:** The gap is found with a week's notice when someone mentions it in a meeting. There is no recommendation ready. The PMO scrambles.

---

## What the Morning Looks Like

| Task | Without the Tool | With the Tool |
|---|---|---|
| Meeting follow-up (3 meetings) | 60–90 min re-reading notes | 10–15 min in the review queue |
| RAID log updated | Later that day, or never | Done before 9:30am |
| JIRA updated | Manual, often forgotten | Automatic on approval |
| Follow-up emails sent | Written from scratch, often delayed | Draft ready, sent in 2 minutes |
| Daily task list | Mental model across inbox, notes, and JIRA | One screen, already consolidated |
| Status report | 45 min to write, multiple manual versions | 10 min to review and approve |
| Resource gap identified | Found too late, no plan ready | Flagged 4 weeks early with a recommendation |

---

## The Principle Behind It

The PMO is not replaced. Every decision that matters — approving a RAID entry, confirming a resource, signing off a report, sending a communication — still requires a human.

What changes is everything around those decisions. The tool handles the gathering, classifying, drafting, matching, and consolidating. The PMO handles the judging, approving, and acting.

**The tool does the work that shouldn't need a PMO. The PMO does the work that only a PMO can do.**

---

*Version: v1.0 | Relates to: pmo-ai-workflows-explained.md, pmo-ai-business-requirements-v1.md*
