# Alert on a Burned SLO, Not on a Noisy Threshold

**Task ID:** `pd1t3-004`
**Estimated effort:** 18 hours
**Module:** Alerting

## Why this task exists

A CPU alert at 70% will page you during a harmless spike and stay silent during a user-facing outage that uses little CPU. This curriculum measures the service you already scrape. You need one SLO, one alert that fires when you burn it, and a runbook the annotation points at.

This is an apprenticeship task, not a content-consumption checkbox. Reading Prometheus alerting docs is only preparation. Completion requires fire *and* resolve that you caused.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/

Use official Prometheus docs for recording rules, alerting rules and Alertmanager (Alertmanager is optional if you can show the alert via the Prometheus alerts API or UI). Stay local. Do not require a paid incident product.

## Work to complete

Use the metrics from `pd1t2-003` and the failure trigger from `pd1t2-005` if it still fits; otherwise add a documented error or latency trigger.

1. Write one SLO in `SLO.md`: indicator (availability or latency), objective (for example 99% success over a window you can actually burn in a lab), and window. Keep the window short enough that you can burn it in this task (minutes, not 30 days).
2. Add a Prometheus rule file: a burn-rate or error-budget alert derived from that SLO. A lone `up == 0` or `cpu > 70` rule does not satisfy this task unless it is *in addition* to the SLO-style alert.
3. Put a runbook section in the repo (in `SLO.md` or `RUNBOOK.md`) that says what to check first. Point the alert's annotation at that file or heading.
4. Inject the documented failure until the alert fires. Capture the firing state. Remove the failure. Capture the resolved state.
5. Write one paragraph justifying the threshold (why this burn, why this window) — not "copied from a blog".

## Required evidence

- Committed Prometheus rule file defining at least one SLO-style alert (error-budget or burn), not only a raw CPU threshold
- Captured Alertmanager or Prometheus alerts API/UI output showing the alert firing under the documented failure
- Captured output showing the same alert resolved after the failure was removed
- A written SLO, window, and burn or budget threshold with a one-paragraph justification, plus a runbook section in the same repository that the alert annotation points to
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus the captures. Do not submit a rule you never fired.

## Acceptance criteria

- [ ] A committed Prometheus rule file defines at least one SLO-style alert (burn or error-budget), not only a raw host CPU or memory threshold.
- [ ] Injecting the documented failure makes the alert fire; removing the failure makes it resolve. Both states are captured.
- [ ] The SLO, window, and threshold are written down with a one-paragraph justification — not left as an uncommented copy-paste.
- [ ] The alert annotation includes a pointer to a runbook section in the same repository. No alert is defined that the apprentice cannot both fire and resolve.

A mentor should be able to replay the inject and see the same alert name.

## Reflection

Answer these in your own words after doing the work:

1. What false positive would this alert still produce, and what would you change before you would page a person?
2. Why is a 30-day SLO the wrong window for this lab, and when would you still write one for a real service?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to compute, on paper, how many failed requests burn the SLO in their window.
- Do not approve a CPU-only threshold, or an alert that fired once and was never shown resolved.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — choosing the SLO and writing the rule yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved an SLO-style alert that you both fired and resolved. LEARN BY DOING. GROW THROUGH MENTORSHIP.
