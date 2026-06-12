# PMO AI Tool — Business Requirements (Iteration 1)

**Scope:** Meeting Intelligence (Wave 1)
**Version:** v0.4 — updated 2026-06-12: manual transcript upload adopted as default input method; distribution lists managed in-tool rather than retrieved via calendar API; Graph API integrations reclassified as optional enhancements
**Status:** Pending stakeholder validation

> These requirements cover Wave 1 only. Wave 2 workstreams — Status Reports, Governance Monitoring, Stakeholder Communications, and Change Request Management — have their own requirements documents. Wave 3 workstreams — Personal Task Management, Strategic Resourcing, Benefits Tracking, and Proactive Risk Monitoring — and Wave 4 workstreams are out of scope for this document.

> **Platform note:** The PMO AI Platform is an **EPAM-built, browser-based web application** hosted on Microsoft Azure and managed by EPAM. PMOs access it via browser using Azure AD SSO. It is not a Microsoft Teams app or Copilot plugin — it is an independent EPAM product. Microsoft tools (Teams, SharePoint, Outlook) and JIRA are data integrations only.
>
> **Architecture note:** The platform uses an orchestrated multi-agent system. A central orchestrator receives unstructured inputs and routes them to specialist sub-agents. This document covers requirements for the Meeting Intelligence sub-agent and its integrations. The orchestration layer will be covered in a separate architecture document.

---

## 1. Meeting Processing

| # | Requirement | Why |
|---|---|---|
| BR-01 | The system must accept meeting transcripts via manual upload as the primary input method. The PMO uploads or pastes the transcript directly into the platform after the meeting. | Manual upload avoids dependency on Microsoft Graph API or Zoom API tenant permissions, which require IT security approval and may have long provisioning lead times. The full AI workflow runs identically regardless of how the transcript arrives. |
| BR-01a | The system must support automatic transcript retrieval via Microsoft Teams Graph API or Zoom REST API as an optional enhancement, where IT has provisioned the necessary permissions. | API-based retrieval eliminates the manual upload step entirely and enables fully automated processing. This is the preferred end state where permissions allow, but is not a dependency for the tool to deliver value. |
| BR-02 | The system must identify and label speakers within the transcript where possible. | Knowing who said what is essential for assigning ownership of actions and decisions. Without speaker attribution, ownership must be guessed. |
| BR-03 | The system must link each processed meeting to its relevant project context. The PMO selects the project at upload time. | RAID items and JIRA updates need to be associated with the correct project. Without this link, extracted items cannot be routed to the right log or ticket. |
| BR-04 | The system must process transcripts asynchronously — real-time processing is not required in this iteration. | Real-time processing adds significant complexity and is not needed. PMOs need the output shortly after uploading the transcript, not during the meeting. |
| BR-05 | Where a transcript is of insufficient quality for reliable extraction, the system must alert the PMO and indicate which sections are affected. | The process must not silently fail on poor-quality input. If extraction confidence is low across a significant portion of the transcript, the PMO needs to know before reviewing proposals. |

---

## 2. Meeting Notes & Distribution

| # | Requirement | Why |
|---|---|---|
| BR-06 | The system must generate meeting notes for each processed meeting. The notes must follow a consistent structure: key topics discussed, discussion points and context, decisions made — followed by an action section at the foot listing all RAID items with owners, due dates, and classifications. | This is the single post-meeting output sent to participants. Combining the narrative summary with the action list in one document means recipients get the full picture — what was discussed, what was decided, and what happens next — without receiving two separate communications. |
| BR-07 | The system must use a PMO-configured distribution list as the default recipient list for meeting notes. Distribution lists are configured per recurring meeting series and can be edited by the PMO before each send. | Automatically retrieving the invitee list from a calendar event requires Graph API calendar permissions, which carry the same IT approval requirements as transcript retrieval. PMO-configured standing lists avoid this dependency while ensuring notes consistently reach the right people. For recurring governance meetings the list is set once and reused; for ad hoc meetings the PMO adjusts it at review time. |
| BR-07a | Where Graph API calendar permissions have been provisioned, the system may optionally retrieve the invitee list from the meeting invitation to pre-populate the distribution list. The PMO must confirm or edit the list before sending. | Auto-retrieval reduces setup effort where permissions allow, but the PMO confirmation step is retained regardless — the list is a PMO decision, not an automated one. |
| BR-08 | The meeting notes must be produced as a draft for PMO review — they must not be distributed without human approval. | Meeting notes are sent externally and represent the organisation. A human must verify accuracy, tone, and completeness before they go out. |

---

## 3. RAID Extraction

| # | Requirement | Why |
|---|---|---|
| BR-08 | The system must extract and classify RAID items from the transcript into four categories: Risk (R), Action (A), Issue (I), and Decision (D). | This is the core value of the tool. RAID items are currently lost or missed after meetings. Systematic extraction ensures nothing falls through. |
| BR-09 | Each extracted RAID item must include: item type, title, description, proposed owner, and (where applicable) due date or decision-maker. | An incomplete RAID item is not actionable. Owners and dates are what turn a logged item into something that actually gets done. |
| BR-10 | The system must assign a confidence score to every extracted RAID item. | Not all extractions are equally certain. Confidence scores allow the system to handle clear cases automatically and flag ambiguous ones for human review, rather than treating everything the same. |
| BR-11 | Any item with a confidence score below 0.80 must be automatically flagged for PMO review before it can proceed. | Below this threshold, the risk of a wrong classification or missed item is too high to allow automatic progression. Human judgment is required. |
| BR-12 | The system must distinguish between a Decision (something agreed) and a proposal (something suggested but not agreed). All potential Decisions must be flagged for PMO confirmation. | Decisions are governance-critical. Incorrectly logging a proposal as a decision creates a false record that can be cited in future disputes. |
| BR-13 | The system must distinguish between a Risk (future threat) and an Issue (current problem). Where the classification is ambiguous, it must be flagged for PMO judgment. | The two require different responses — Risks need mitigation planning, Issues need immediate resolution. Misclassifying one as the other leads to the wrong action being taken. |
| BR-14 | The system must not fabricate RAID items — every extracted item must be traceable to specific content in the source transcript. | Trust in the tool depends on accuracy. Invented items would undermine confidence and create incorrect project records that could affect decisions. |
| BR-15 | Ownership must only be assigned to individuals who were present in or referenced during the meeting. Ambiguous ownership must be flagged. | Assigning an action to the wrong person means it does not get done. Guessing ownership without a basis in the meeting is not reliable enough. |
| BR-16 | Vague due dates (e.g. "by end of week", "next sprint") must be converted to specific dates, with the inferred date flagged for PMO confirmation. | Action items without a specific date rarely get done. Converting vague language into real dates makes the commitment concrete, while flagging the inference protects against misinterpretation. |

---

## 4. RAID Log

| # | Requirement | Why |
|---|---|---|
| BR-17 | The system must propose RAID log entries but must not create them without explicit PMO approval. This applies to all four item types without exception. | The RAID log is a formal governance document. Entries may be referenced in audits, escalations, and dispute resolution. Only a human can take responsibility for what is recorded. |
| BR-18 | Every RAID log entry must record: item type, title, description, severity (for R and I), status, owner, due date (for A), decision-maker (for D), source meeting reference, approving PMO user, and whether the entry was agent-proposed. | A complete schema ensures the log is usable for governance and reporting. Missing fields — especially the approving user and source meeting — make the record incomplete and harder to audit. |
| BR-19 | Every RAID item must be traceable back to the source meeting, timestamp within the meeting, and speaker (where identifiable). | If a RAID entry is ever questioned, the PMO must be able to point to exactly where in the meeting it came from. Without traceability, the log cannot be defended. |
| BR-20 | A full audit log must be maintained for every action taken, including: what the agent proposed, the confidence score, and the human decision (approved, rejected, or modified). | The audit log provides accountability. It shows what the AI recommended and what the human decided, enabling quality review, performance improvement, and evidence of oversight. |

---

## 5. JIRA Integration

| # | Requirement | Why |
|---|---|---|
| BR-21 | The system must read existing JIRA tickets to match action items from meetings to relevant open tickets. | Action items from meetings often relate to work already tracked in JIRA. Matching them avoids duplicate tickets and ensures updates go to the right place. |
| BR-22 | The system must propose JIRA updates (new tickets, status changes, comments, assignee updates) but must not apply them without PMO confirmation. | JIRA is the primary project tracking system. Incorrect updates — even to low-priority tickets — create noise and erode trust. All changes must be reviewed before they are applied. |
| BR-23 | Any update to a ticket classified as high-priority (Priority: Highest or High, or labelled "executive-visible") must always require explicit PMO approval — this cannot be automated. | High-priority tickets are visible to senior stakeholders. An incorrect automated update to one of these could cause confusion or misrepresent project status to leadership. |
| BR-24 | Where the JIRA API is unavailable, proposed updates must be queued and the PMO alerted. Updates must not be silently lost. | If proposed updates disappear when the API is down, action items from that meeting will never be logged. Queuing ensures nothing is lost and the PMO is aware of the delay. |

---

## 6. Meeting Notes Distribution

| # | Requirement | Why |
|---|---|---|
| BR-25 | The system must send the approved meeting notes via Outlook to the distribution list confirmed by the PMO at review time. The distribution list is drawn from the PMO-configured standing list for that meeting series, editable before each send. | Participants who could not attend need the notes. The standing list approach ensures consistent distribution without requiring calendar API access. The PMO edits the list at review time to account for one-off additions or exclusions. |
| BR-25a | The system must allow the PMO to maintain distribution lists per recurring meeting series within the platform. Changes to a standing list must apply to all future meetings in that series unless overridden. | Recurring governance meetings (steering committees, workstream calls) have consistent attendee sets. Configuring the list once and reusing it removes the need to manage recipients at every send. |
| BR-26 | The system must never send meeting notes without explicit PMO approval. | Meeting notes are an external communication that represents the organisation and creates a formal record of what was discussed, decided, and committed to. Sending without review risks an inaccurate or incomplete record reaching participants. |
| BR-27 | The draft meeting notes must be presented to the PMO for review in full — including the narrative summary, the decisions, the RAID action list at the foot, and the confirmed distribution list — before any send action is available. | The PMO must review the document as participants will receive it, and confirm who will receive it, in one step. Splitting these into separate screens risks approving content without verifying recipients, or vice versa. |

---

## 7. Escalation & Human Review

| # | Requirement | Why |
|---|---|---|
| BR-28 | The system must escalate to the PMO under the following conditions: confidence score below 0.80; ambiguous Risk vs Issue classification; uncertain Decision vs proposal; ambiguous or external item owner; high-severity risk detected; content flagged as sensitive (HR, legal, or financial). | Each of these conditions represents a situation where the AI cannot reliably determine the correct outcome. Escalating ensures a human makes the call rather than the system defaulting to a potentially wrong answer. |
| BR-29 | Escalated items must remain in a pending state until the PMO resolves them — they must not proceed automatically after a timeout. | An unresolved escalation left to time out and auto-proceed defeats the purpose of the escalation. Pending items must require a deliberate human decision. |

---

## 8. Integrations

> The EPAM platform operates in two modes: **default mode** (manual transcript upload, no API permissions required) and **enhanced mode** (automatic transcript retrieval via API, where IT has provisioned permissions). All integrations are optional enhancements in Wave 1 except SharePoint (RAID log) and JIRA (ticket updates), which are required for write-back functionality. The platform itself runs independently on EPAM-managed Azure infrastructure.

| # | Requirement | Type | Why |
|---|---|---|---|
| BR-30 | The EPAM platform must provide a transcript upload interface allowing the PMO to paste or upload a transcript file directly into the platform. The system must accept plain text, .docx, and .vtt (Teams transcript) formats. | **Required (default)** | This is the primary input method. No IT permissions required. The full AI workflow runs from a manually uploaded transcript identically to an API-retrieved one. |
| BR-31 | The EPAM platform may optionally integrate with Microsoft Teams via the Microsoft Graph API to retrieve transcripts automatically where IT has provisioned the necessary permissions. | **Optional enhancement** | Eliminates the manual upload step. Requires IT to grant specific Graph API scopes — provisioning may take time and is not required for Wave 1 to function. |
| BR-32 | The EPAM platform may optionally integrate with Zoom via REST API for automatic transcript retrieval where Zoom is the meeting platform and API access has been provisioned. | **Optional enhancement** | Supports clients using Zoom as their primary meeting platform. Same provisioning considerations as the Teams integration. |
| BR-33 | The EPAM platform must integrate with JIRA via REST API for reading existing tickets and proposing updates. | **Required** | JIRA is the primary project tracking tool. Direct API integration avoids manual copy-paste and ensures proposed updates are accurately formatted for the target ticket. |
| BR-34 | The EPAM platform must integrate with SharePoint via the Microsoft Graph API for RAID log read and write operations. | **Required** | The RAID log lives in SharePoint. The integration allows the system to propose structured entries directly into the log rather than requiring the PMO to copy items across manually. |
| BR-35 | The EPAM platform must integrate with Outlook via the Microsoft Graph API to send approved meeting notes to the confirmed distribution list. | **Required** | Outlook is the distribution channel. Direct integration ensures the approved document is sent correctly and logged without the PMO switching to a separate email client. |
| BR-36 | All integrations must use OAuth 2.0 authentication. | **Required** | OAuth 2.0 is the security standard required for Microsoft Graph and JIRA APIs. It ensures access is properly permissioned, auditable, and can be revoked without changing passwords. |

---

## 9. Accuracy & Performance Targets

| # | Requirement | Target | Why |
|---|---|---|---|
| BR-35 | RAID item capture rate | ≥ 95% | If the tool misses more than 1 in 20 RAID items, PMOs cannot trust it as a replacement for manual review. |
| BR-36 | R/A/I/D classification accuracy | ≥ 85% | Misclassification leads to wrong actions — a Risk treated as an Action, or a Decision left unlogged. 85% sets a meaningful minimum before the tool is useful. |
| BR-37 | Owner assignment accuracy | ≥ 90% | An action with the wrong owner does not get done. High accuracy here is essential for accountability. |
| BR-38 | RAID proposal acceptance rate | ≥ 80% | This measures quality from the PMO's perspective. If fewer than 4 in 5 proposals are accepted, the tool is generating too much noise and creating more work, not less. |
| BR-39 | Time from meeting end to follow-up draft available | ≤ 30 minutes | The value of a follow-up email drops quickly as time passes. Thirty minutes is the target to keep the output relevant and timely. |
| BR-40 | Meeting processing success rate | ≥ 99% | Frequent processing failures would require constant manual fallback and undermine trust in the tool. |

---

## 10. Governance & Compliance

| # | Requirement | Why |
|---|---|---|
| BR-41 | Zero RAID log entries must be created without PMO approval. | The RAID log is a governance artifact. Any entry without human approval cannot be considered authoritative and exposes the organisation to audit risk. |
| BR-42 | Zero emails must be sent without PMO approval. | External communications carry reputational and legal risk. There is no scenario where autonomous email sending is acceptable in this tool. |
| BR-43 | Zero high-priority JIRA updates must be applied without PMO approval. | High-priority tickets are visible to senior stakeholders. An incorrect automated update could misrepresent project status at the worst possible moment. |
| BR-44 | The system must detect and mask personally identifiable information (PII) in all debug, trace, and audit logs. | Meeting transcripts may contain personal information about individuals. Storing this in logs without masking creates a data privacy risk and potential regulatory exposure. |
| BR-45 | Any change to the confidence thresholds, autonomy levels, JIRA field mappings, RAID schema, or email templates must require PMO Lead approval before deployment. | These settings directly control what the AI does and does not do autonomously. Unauthorised changes could silently expand AI autonomy beyond what has been agreed, bypassing governance controls. |

---

## 11. Out of Scope (Wave 1)

The following are out of scope for this document. Confirmed future waves are noted.

| Item | Status |
|---|---|
| Status report generation and distribution | Wave 2 — confirmed |
| Governance monitoring and compliance checking | Wave 2 — confirmed |
| Stakeholder communications drafting | Wave 2 — confirmed |
| Personal task management and email scanning | Wave 3 — confirmed |
| Strategic resourcing gap detection and matching | Wave 3 — confirmed |
| Proactive risk monitoring from project data signals | Wave 3 — confirmed |
| Change request management and impact assessment | Wave 2 — confirmed |
| Lessons learned and knowledge capture | Wave 4 — confirmed, high priority |
| Dependency tracking | Wave 4 — confirmed |
| Onboarding access checking | RPA — not AI-first; handled by existing automation tooling |
| Real-time (in-meeting) processing | Out of scope — asynchronous processing is sufficient for Wave 1 |
| Automatic sending of any communication | Out of scope permanently — all external communications require human approval |

---

## Open Items — Requires Stakeholder Input

| # | Question | Status | Impact if Unresolved |
|---|---|---|---|
| OI-01 | Are meetings currently transcribed in Teams/Zoom, and are PMOs comfortable copying/exporting the transcript for upload? | **Partially answered** — PMO surveys confirm Teams transcription is in use. Confirm that PMOs are willing to do the upload step and that transcripts are accessible to them (some clients may restrict transcript download). | If transcripts cannot be exported by the PMO, the manual upload model doesn't work |
| OI-02 | What is the current RAID log schema and location in SharePoint? | **Open** | Cannot propose RAID entries in the correct format |
| OI-03 | What JIRA fields are used per project? | **Open** | Cannot match or update tickets accurately |
| OI-04 | What defines a "high-priority" JIRA ticket in this context? | **Open** — assumed to be Priority: Highest/High or labelled "executive-visible" but must be confirmed per client | Cannot apply correct approval rules |
| OI-05 | Who has authority to approve RAID log entries? | **Open** — governance model varies by client | Cannot design the approval workflow |
| OI-06 | Will IT provision Graph API access for Teams transcript retrieval as an optional enhancement? If so, what is the lead time? | **Open — not blocking for Wave 1** | Automatic transcript retrieval is an enhancement. Wave 1 functions without it. Provisioning in parallel while the manual workflow is live is the recommended approach. |
| OI-07 | Are there meeting types that should be explicitly excluded from processing (e.g. HR, 1:1s, confidential)? | **Open** — identified through survey analysis | Scope exclusions must be defined before build; incorrect processing of sensitive meetings creates a trust risk |
| OI-08 | What is the expected volume of meetings per month across the target client portfolio? | **Open** — estimated at ~80/month per PMO based on stakeholder input; needs confirmation | Affects infrastructure sizing and performance SLA targets |

---

*Version: v0.3 | Relates to: pmo-ai-tool-deliverables.md, pmo-ai-workflows-explained.md*
