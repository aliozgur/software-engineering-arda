# Respond to a Simulated Incident Before You Finish Root Cause

**Task ID:** `ob1t1-006`
**Estimated effort:** 10 hours
**Module:** Incident Response

## Why this task exists

You now have logs, metrics, traces, an SLO, and a paging alert. This task is the first
time those signals have to support a response, not a write-up. The hard part is the
order: mitigate the user-visible symptom, then diagnose. A timeline that mixes facts
and guesses as if they were the same thing is how incidents get longer.

Mentorship is optional. You will build a small injector that can apply three failure
modes and pick one without telling you which until after you record "restored." A
mentor can pick the mode for you if one is present; otherwise a script or a second
person does.

LEARN BY DOING. GROW THROUGH MENTORSHIP. A runbook you only read is not a response.

## Authoritative resources

- **Site Reliability Engineering (Google SRE Book)** (primary):
  https://sre.google/sre-book/managing-incidents/ — Chapter 14, Managing Incidents.
  Also read https://sre.google/sre-book/being-on-call/ (Chapter 11) and
  https://sre.google/sre-book/effective-troubleshooting/ (Chapter 12).
  Appendix C is a useful incident-state shape:
  https://sre.google/sre-book/example-incident-state-document/

## Work to complete

1. On the service from earlier tasks, implement an injector (script, flag, or config
   switch) that can apply **at least three** named failure modes. They must be
   operationally distinct — for example: elevated 5xx on the entry service, added
   latency on one downstream dependency, and a broken or hung dependency that surfaces
   as timeouts. A single "set error_rate=1" with three names is not three modes.
2. **Before** you start the incident, write a runbook that covers **detect** and
   **mitigate** for at least two of those modes. Commit it. Copy the commit hash (or
   `sha256` of the runbook file) into a note you will paste as the timeline's first
   line. Do not edit the runbook again until after you write "restored."
3. Start the incident:
   - If a mentor or friend is available, they pick a mode and run the injector without
     telling you which.
   - If you are solo, write a wrapper that chooses a mode at random, applies it, and
     writes the chosen name to a file you are not allowed to open until the restoration
     line exists in the timeline. State which method you used.
4. Work from alerts, dashboards, logs, and traces — not from the injector source and
   not from the sealed mode file. Keep a timestamped timeline. Every line is labeled
   **FACT** (you observed it) or **HYPOTHESIS** (you have not confirmed it). You need
   at least six lines, at least three FACT and at least two HYPOTHESIS.
5. Mitigate first: restore the user-visible symptom (errors down, latency back under
   the SLI threshold, or the dependency unblocked — whatever the user would notice).
   Write a restoration line with a timestamp. Only after that line may you write a
   root-cause line.
6. Capture at least two distinct signal types you actually used (paging alert firing,
   a PromQL result, a log excerpt with a correlation id, a trace). Cite them from the
   timeline by filename or query.

You will write the postmortem in `ob1t1-007`. Do not spend this task polishing
prose — spend it on the timeline and the restore-before-diagnose order.

## Required evidence

- A runbook covering detect and mitigate for at least two named failure modes,
  committed before the timeline starts
- An injector script or config that can apply at least three named failure modes
- A timestamped incident timeline with each line labeled FACT or HYPOTHESIS
- Captured artifacts for at least two distinct signal types cited in the timeline
- A restoration note stating the user-visible symptom, the mitigation action, and the
  timeline timestamp when service was called restored
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. The sealed mode file or mentor note
revealing which mode was injected belongs in the submission **after** the restoration
line, so a reviewer can confirm you did not diagnose from the label.

## Acceptance criteria

- [ ] The runbook file is committed, and the timeline's first entry quotes that commit
      hash or a file checksum as the runbook version in force.
- [ ] The timeline contains at least six timestamped entries; at least three are
      labeled FACT and at least two are labeled HYPOTHESIS.
- [ ] The restoration timestamp in the timeline is at or before the first entry that
      names a root cause.
- [ ] At least two distinct signal types (logs, metrics, traces, or alerts) are cited
      in the timeline, each with a captured artifact in the submission.

The mentor may start a second mode after restore and ask you to keep the same
timeline discipline. If you are working without a mentor, do not inject a second mode
unless the first restore is already recorded.

## Reflection

Answer these in your own words after doing the work:

1. Which timeline line, looking back, was a hypothesis you treated as a fact — and
   what did that cost you in minutes or extra steps?
2. What signal, if it had been in the runbook's "open this first" list, would have
   shortened time-to-mitigate?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: hide the injector mode, score the
timeline's FACT/HYPOTHESIS hygiene as heavily as the technical fix, and refuse a
submission whose first "root cause" line is earlier than restore.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain incident roles and quiz you on mitigate-versus-diagnose. AI must not
write the timeline or tell you which failure mode is active from a paste of your
signals. If you paste telemetry into a chat, disclose it and still produce a timeline
in your own words. Disclose material AI use: provider or model if known, purpose, and
verification performed.

## Completion gate

This task is not complete when the service is green again. It is complete once the
timeline shows restore before root cause, two signal artifacts exist, and the runbook
version in force is quoted on line one.
