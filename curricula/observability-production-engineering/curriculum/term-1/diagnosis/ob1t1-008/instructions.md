# Diagnose With Logs, Metrics, and Traces Together

**Task ID:** `ob1t1-008`
**Estimated effort:** 10 hours
**Module:** Diagnosis

## Why this task exists

You spent the term adding signals. This task asks the opposite question: when would
trusting only one of them send you to the wrong component? You will induce a failure
that looks like one story in metrics and a different story once logs and a trace are
in the same note — then write the runbook you wish the `ob1t1-006` on-call had.

If you marked a follow-up in `ob1t1-007` as "do this week," implement it here and
point at it from the runbook. That is optional only if none of those follow-ups fit
a one-task change; if so, say which follow-up you deferred and why.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/ — traces
  and context propagation, for the span you will cite.
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — the first-pass query you will deliberately let mislead you.
- **The Twelve-Factor App** (reference): https://12factor.net/logs — logs as a queryable
  event stream, not a file you SSH in to tail once.

You may also revisit the SRE book troubleshooting chapter if you need a diagnosis
shape: https://sre.google/sre-book/effective-troubleshooting/

## Work to complete

1. Design and inject a failure that a **metrics-only** reader would mis-attribute or
   leave incomplete. Examples that fit this bar:
   - Entry-service error rate rises because a downstream span is slow and the client
     times out — metrics say "API errors," the trace names the slow child.
   - Success rate stays high while logs show retries and the trace shows repeated
     child spans — metrics say healthy, users feel delay.
   - A saturation metric on the entry process spikes while the trace shows time spent
     in a dependency, not in the process you would scale.

   Write a short injection note: what you changed, and in one sentence why a RED
   dashboard alone would tell the wrong first story.
2. Capture the metrics first. Write a **metrics-only first-pass** note that states a
   conclusion (component, cause class, or "scale this process") **before** you open
   the trace. Attach the query output. This note is supposed to be incomplete or
   wrong; do not edit it after you see the trace. Commit it, or timestamp the file.
3. Pull the matching log excerpt (same correlation / request id as `ob1t1-001`) and
   the trace. Write a **combined diagnosis** that cites:
   - one metric or PromQL result,
   - one log line that includes the correlation id,
   - one span name and its duration.
   The combined diagnosis must revise or narrow the first-pass conclusion in a
   sentence a mentor can highlight (for example: "first pass: scale entry; revised:
   wait on `billing-lookup` 1.8s").
4. Write a runbook another on-call could follow on a weekday they have never seen
   your repo:
   - **Detect** — which alert or query, and what "bad" looks like.
   - **Diagnose** — which three checks (metric, log filter, trace) and in what order.
   - **Recover** — the mitigation action (feature flag, retry budget, disable a
     caller, roll back, restart a dependency — something you actually ran or can run).

   Each section needs at least one concrete command, query, or action. The runbook
   must not say to open application source (`foo.py:40`, "read the handler"). Config
   or query files that an on-call would already have in the ops repo are fine.
5. Close with a five-line note: what you would change about the `ob1t1-004` SLO or
   the `ob1t1-005` paging rule after this diagnosis. If the answer is "nothing," say
   what you checked that kept them unchanged.

## Required evidence

- A failure-injection note describing the induced condition and why a metrics-only
  read would mislead
- A metrics-only first-pass note stating the incorrect or incomplete conclusion, with
  the query output attached
- A log excerpt (correlation id visible) and a trace export that revise that
  conclusion
- A combined diagnosis note that cites one metric/query result, one log line, and one
  span name/duration
- A runbook with labeled Detect, Diagnose, and Recover sections, each containing a
  concrete command, query, or action
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Prefer file artifacts over
screenshots; if you include a UI screenshot of a trace, also export the trace id and
span list as text.

## Acceptance criteria

- [ ] The metrics-only first-pass note states a conclusion that the combined diagnosis
      revises or narrows.
- [ ] The combined diagnosis cites at least one metric or query result, one log line
      with a correlation id, and one span name with a duration.
- [ ] The runbook has three labeled sections — Detect, Diagnose, Recover — each with
      at least one concrete command, query, or action.
- [ ] The runbook contains no instruction to open application source (no file names
      with line numbers, no "read foo.py").

The mentor may hide the injection note and ask you to walk Detect → Diagnose → Recover
from the runbook only. If you are working without a mentor, wait an hour (or the next
day), reopen only the runbook, and time yourself through one replay of the same
failure; record the minutes in the reflection.

## Reflection

Answer these in your own words after doing the work:

1. If you had been allowed only one of the three signals during this failure, which
   one would have been least wrong — and what would you still have missed?
2. What from `ob1t1-006` would have gone faster if this runbook had existed then?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: cover the injection note, hand the
apprentice only the runbook, and see whether Detect still finds the symptom. Do not
approve a first-pass note that was clearly written after the trace (the revision
sentence will be missing or cosmetic).

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain when signals disagree and quiz you on which signal to open first.
AI must not write the first-pass note, the combined diagnosis, or the runbook.
Disclose material AI use: provider or model if known, purpose, and how you verified
each cited number (query result, log line, span duration).

## Completion gate

This task is not complete when all three signals exist in the repo. It is complete
once the first-pass conclusion is visibly revised by the combined diagnosis, the
runbook can be followed without source, and the demonstrated competency is approved.
