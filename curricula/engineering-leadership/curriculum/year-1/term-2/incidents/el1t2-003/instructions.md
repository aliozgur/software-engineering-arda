# Lead the Incident Comms, Not the Debugger

**Task ID:** `el1t2-003`
**Estimated effort:** 8 hours
**Module:** Incidents

## Why this task exists

When Checkout is down, the instinct of a strong IC is to grab the debugger. The lead job is often the **channel**: who knows what, which decision was made on which information, and what words go to customers versus execs. "I mentored the team through the incident" is not evidence. A comms timeline, a contemporaneous decision log, and a blameless postmortem are.

This is an apprenticeship task. Reading is preparation. Completion requires the three artifacts written against the timeline below — not a general essay on incident command.

## Authoritative resources

- **Staff Engineer (Will Larson)** (primary): https://staffeng.com/ — read the material on being a right-hand / tech-lead during high-stakes work, and on writing that other people can act on.
- **Postmortem Culture: Learning from Failure** (additional, freely available): https://sre.google/sre-book/postmortem-culture/ — use this for the blameless bar and for what a follow-up looks like. Record that you used it in your notes.

## Scenario

You are **incident lead for comms** on Harborline Checkout. Jordan is in the code. You do not get to "also be the person who found the bug" in the write-up. Use only the facts at each timestamp. Do not invent a root cause before 16:40.

**Clock (treat as the only source of truth)**

| Time | Fact |
| --- | --- |
| 14:02 | Pager: checkout p99 latency > 4s for 10 minutes. Error rate 8%. |
| 14:08 | Jordan: "Redis CPU is 90%. I am going to restart the primary." |
| 14:10 | Morgan (EM) in Slack: "Customer success is asking if we should post to the status page." |
| 14:18 | Restart complete. Error rate 12%. Latency worse. |
| 14:22 | Sam: "I think I shipped a retry loop this morning. Should I revert?" You have not seen the PR. |
| 14:25 | Data platform: "Our warehouse job is also slow. Same Redis?" |
| 14:31 | You still have no confirmed cause. Mobile reports checkout blank for ~15% of users. |
| 14:40 | Identity (Alex): "Our token endpoint is fine. We are not paging." |
| 15:05 | Jordan finds `timeout=None` on a new Identity call in Checkout (related to last week's webhook work). Not proven as cause. |
| 15:20 | You must choose: revert Sam's morning PR (unreviewed by you), or raise Identity call timeout and rate-limit retries. |
| 15:35 | Error rate back to 1% after **one** of those actions (you must record which you chose and what you knew). |
| 16:40 | Post-incident: logs show the retry loop + missing timeout amplified a slow Identity dependency. Sam's PR was a contributing factor. So was the review that never happened. So was no load-shed on webhook retries. |

**Audiences you must write for at least once:** engineering channel, and either customer-status **or** exec (Morgan).

**Rules**

- Updates before 16:40 must not state a root cause as fact.
- The decision log is contemporaneous: write what you knew at 14:08, 14:22, 15:20 — not "we later learned."
- The postmortem may name Sam's PR as a contributing **change**. It may not say Sam is careless, junior, or "the problem."

## Work to complete

1. Write a **comms timeline** with at least **four** timestamped updates. Each update: timestamp, audience, the message (or a faithful draft), and what changed since the last update. Use at least **two** audiences.
2. Write a **decision log** with at least **three** entries. Each entry: timestamp, decision, information known then, and the rejected option (for example: restart Redis vs wait; revert vs rate-limit; post to status page vs wait).
3. Write a **blameless postmortem**: summary, at least **two** contributing factors, what went well, what went poorly, and at least **two** follow-ups. Each follow-up has an **owner role** (Checkout tech lead, Identity, platform — not "Sam should be more careful") and a tag: **detect**, **prevent**, or **respond**.
4. Include one **external status snippet** (≤80 words) that does not speculate on cause.
5. Commit timeline, decision log, and postmortem as separate files. Incremental commits are expected.

## Required evidence

- A comms timeline with at least four timestamped updates, at least two audiences, and no root-cause-as-fact in updates before the postmortem
- A decision log with at least three entries, each stating the information known at that time rather than the later truth
- A blameless postmortem naming at least two contributing factors, containing zero sentences that blame a person's character or competence, and at least two follow-ups each tagged detect, prevent, or respond with an owner role

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The timeline has at least four timestamped updates and at least two different audiences; no comms-timeline update states a root cause as fact.
- [ ] The decision log has at least three entries; each entry states what was known at that timestamp, not the cause learned later.
- [ ] The postmortem names at least two contributing factors, contains no sentence that attributes the outage to a person's character or competence, and lists at least two follow-ups each with an owner role and a detect/prevent/respond tag.

## Reflection

Answer in your own words after doing the work:

1. At 14:08, what would you have said to Jordan that is a comms decision, not a debugging instruction?
2. Which sentence in your first postmortem draft was closest to blame, and how did you rewrite it?

Also record: what took longer than expected, what you would practice again, what remains unclear, and which artifact best proves you led comms rather than the debugger.

## Mentor review guide

- Search the postmortem for names plus adjectives (careless, should have known, junior mistake). Request revision if found.
- Ask what the 14:10 status-page decision was, using only the decision log. If the log cheats with 16:40 knowledge, request revision.

Suggested review outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain blameless language, offer hints if an update leaks cause too early, and quiz you on detect/prevent/respond. AI must not write the timeline, the decision log, or the postmortem for you. Disclose any material AI use with provider/model (if known), purpose, and verification.

## Completion gate

This task is not complete when the incident "has a write-up." It is complete when a mentor can replay your decisions from the log without the later truth, and the postmortem names systems and missing reviews — not people as the defect.
