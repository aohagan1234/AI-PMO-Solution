# PMO AI Tool — Business Requirements (Iteration 1)

**Scope:** Meeting Intelligence (Wave 1)
**Version:** v0.1 — draft for review
**Status:** Pending stakeholder validation

> These requirements cover the first iteration only. Streams 2–4 (Status Reports, Strategic Resourcing, Personal Task Management) are out of scope for this iteration.

---

## 1. Meeting Processing

| # | Requirement |
|---|---|
| BR-01 | The system must accept meeting transcripts from Microsoft Teams and/or Zoom as the primary input source. |
| BR-02 | The system must identify and label speakers within the transcript where possible. |
| BR-03 | The system must link each processed meeting to its relevant project context. |
| BR-04 | The system must process transcripts asynchronously — real-time processing is not required in this iteration. |
| BR-05 | Where a transcript is unavailable or of insufficient quality, the system must alert the PMO and request manual notes as a fallback. |

---

## 2. Meeting Summary

| # | Requirement |
|---|---|
| BR-06 | The system must generate a structured summary of each meeting, covering key topics, discussion points, and proposed next steps. |
| BR-07 | The summary must be produced as a draft for PMO review — it must not be distributed without human approval. |

---

## 3. RAID Extraction

| # | Requirement |
|---|---|
| BR-08 | The system must extract and classify RAID items from the transcript into four categories: Risk (R), Action (A), Issue (I), and Decision (D). |
| BR-09 | Each extracted RAID item must include: item type, title, description, proposed owner, and (where applicable) due date or decision-maker. |
| BR-10 | The system must assign a confidence score to every extracted RAID item. |
| BR-11 | Any item with a confidence score below 0.80 must be automatically flagged for PMO review before it can proceed. |
| BR-12 | The system must distinguish between a Decision (something agreed) and a proposal (something suggested but not agreed). All potential Decisions must be flagged for PMO confirmation. |
| BR-13 | The system must distinguish between a Risk (future threat) and an Issue (current problem). Where the classification is ambiguous, it must be flagged for PMO judgment. |
| BR-14 | The system must not fabricate RAID items — every extracted item must be traceable to specific content in the source transcript. |
| BR-15 | Ownership must only be assigned to individuals who were present in or referenced during the meeting. Ambiguous ownership must be flagged. |
| BR-16 | Vague due dates (e.g. "by end of week", "next sprint") must be converted to specific dates, with the inferred date flagged for PMO confirmation. |

---

## 4. RAID Log

| # | Requirement |
|---|---|
| BR-17 | The system must propose RAID log entries but must not create them without explicit PMO approval. This applies to all four item types without exception. |
| BR-18 | Every RAID log entry must record: item type, title, description, severity (for R and I), status, owner, due date (for A), decision-maker (for D), source meeting reference, approving PMO user, and whether the entry was agent-proposed. |
| BR-19 | Every RAID item must be traceable back to the source meeting, timestamp within the meeting, and speaker (where identifiable). |
| BR-20 | A full audit log must be maintained for every action taken, including: what the agent proposed, the confidence score, and the human decision (approved, rejected, or modified). |

---

## 5. JIRA Integration

| # | Requirement |
|---|---|
| BR-21 | The system must read existing JIRA tickets to match action items from meetings to relevant open tickets. |
| BR-22 | The system must propose JIRA updates (new tickets, status changes, comments, assignee updates) but must not apply them without PMO confirmation. |
| BR-23 | Any update to a ticket classified as high-priority (Priority: Highest or High, or labelled "executive-visible") must always require explicit PMO approval — this cannot be automated. |
| BR-24 | Where the JIRA API is unavailable, proposed updates must be queued and the PMO alerted. Updates must not be silently lost. |

---

## 6. Follow-Up Email

| # | Requirement |
|---|---|
| BR-25 | The system must draft a follow-up email for each processed meeting, including RAID items, owners, due dates, and key decisions. |
| BR-26 | The system must never send an email without explicit PMO approval. |
| BR-27 | The draft email must be presented to the PMO for review before any send action is available. |

---

## 7. Escalation & Human Review

| # | Requirement |
|---|---|
| BR-28 | The system must escalate to the PMO under the following conditions: confidence score below 0.80; ambiguous Risk vs Issue classification; uncertain Decision vs proposal; ambiguous or external item owner; high-severity risk detected; content flagged as sensitive (HR, legal, or financial). |
| BR-29 | Escalated items must remain in a pending state until the PMO resolves them — they must not proceed automatically after a timeout. |

---

## 8. Integrations

| # | Requirement |
|---|---|
| BR-30 | The system must integrate with Microsoft Teams via the Microsoft Graph API to retrieve meeting transcripts and attendance data. |
| BR-31 | The system must integrate with Zoom via REST API as an alternative transcript source. |
| BR-32 | The system must integrate with Jira via REST API for reading and proposing ticket updates. |
| BR-33 | The system must integrate with SharePoint via the Microsoft Graph API for RAID log read and write operations. |
| BR-34 | All integrations must use OAuth 2.0 authentication. |

---

## 9. Accuracy & Performance Targets

| # | Requirement | Target |
|---|---|---|
| BR-35 | RAID item capture rate | ≥ 95% of items discussed |
| BR-36 | R/A/I/D classification accuracy | ≥ 85% correct |
| BR-37 | Owner assignment accuracy | ≥ 90% correct |
| BR-38 | RAID proposal acceptance rate | ≥ 80% (indicator of quality) |
| BR-39 | Time from meeting end to follow-up draft available | ≤ 30 minutes |
| BR-40 | Meeting processing success rate | ≥ 99% |

---

## 10. Governance & Compliance

| # | Requirement |
|---|---|
| BR-41 | Zero RAID log entries must be created without PMO approval. |
| BR-42 | Zero emails must be sent without PMO approval. |
| BR-43 | Zero high-priority JIRA updates must be applied without PMO approval. |
| BR-44 | The system must detect and mask personally identifiable information (PII) in all debug, trace, and audit logs. |
| BR-45 | Any change to the confidence thresholds, autonomy levels, JIRA field mappings, RAID schema, or email templates must require PMO Lead approval before deployment. |

---

## 11. Out of Scope (Iteration 1)

The following are explicitly out of scope and will be considered in later iterations:

- Status report generation and distribution
- Strategic resourcing gap detection and matching
- Personal task management and email scanning
- Onboarding access checking (handled by existing RPA tooling)
- Real-time meeting processing
- Automatic sending of any communication

---

## Open Items — Requires Stakeholder Input

| # | Question | Impact if Unresolved |
|---|---|---|
| OI-01 | Are meetings currently recorded and transcribed in Teams/Zoom? | Cannot process meetings without transcripts |
| OI-02 | What is the current RAID log schema and location in SharePoint? | Cannot propose RAID entries |
| OI-03 | What JIRA fields are used per project? | Cannot match or update tickets accurately |
| OI-04 | What defines a "high-priority" JIRA ticket in this context? | Cannot apply correct approval rules |
| OI-05 | Who has authority to approve RAID log entries? | Cannot design the approval workflow |
| OI-06 | Does the Graph API access for Teams transcripts need to be provisioned by IT? | Blocking — cannot begin without this |

---

*Version: v0.1 | Relates to: pmo-ai-tool-deliverables.md*
