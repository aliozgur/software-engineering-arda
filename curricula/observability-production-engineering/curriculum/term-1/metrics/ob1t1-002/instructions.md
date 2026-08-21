# Metrics That Matter: RED Dashboards, Not Vanity Numbers

**Task ID:** `ob1t1-002`
**Estimated effort:** 8 hours
**Module:** Metrics

## Why this task exists

It is easy to instrument dozens of metrics and still be unable to answer "is this healthy
right now." This task forces the opposite discipline: pick a small number of metrics,
justify each one against a real operational question, and prove the resulting dashboard
actually changes shape when the system gets unhealthy.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
  — read about metric types (counter, gauge, histogram, summary) and PromQL basics.
- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/ — the metrics
  section, if you instrument via an OTel SDK rather than a native Prometheus client.

## Work to complete

1. Use the service from `ob1t1-001` (or another one under some load, real or synthetic).
2. Instrument the RED set for one chosen operation: **R**ate (requests/sec), **E**rrors
   (error rate), **D**uration (a latency histogram, not a bare average). Cap yourself at
   six metrics total and write a one-sentence justification per metric naming the
   operational question it answers.
3. Deliberately name one "vanity metric" candidate you considered and rejected (for
   example, total lines executed, or a raw request counter with no error/latency context)
   and write why it wouldn't inform any real decision.
4. Expose the metrics on a scrape endpoint and confirm Prometheus, or `promtool check
   metrics`, can parse it without errors.
5. Write four PromQL queries: request rate, error rate, p95 latency, p99 latency. Capture
   their output twice — once under a normal/healthy state, once after you've induced an
   unhealthy state (added latency, forced errors, or similar).
6. Assemble the four queries into one fixed dashboard definition (a Grafana JSON export,
   or a documented Prometheus console/rules file) rather than ad hoc queries typed each
   time.

## Required evidence

- A metrics justification note, including the rejected vanity-metric candidate and why
- `promtool`/scrape validation output
- The four PromQL queries with captured output under both states
- A dashboard definition file or export
- Reflection notes

## Acceptance criteria

- [ ] Prometheus (or `promtool check`) validates the exposed metrics endpoint without
      errors.
- [ ] The latency metric is a histogram or summary, and captured queries include p95 and
      p99 — not a single average.
- [ ] Each of the at most six exposed metrics has a one-sentence justification tying it to
      a named operational question.
- [ ] The dashboard/query set shows a visibly different result between the healthy and
      induced-unhealthy capture.

The mentor may point at one of your six metrics and ask you to defend keeping it over a
metric you rejected. If you are working without a mentor, write that defense yourself for
the metric you are least sure about.

## Reflection

1. Which metric would have told you the least if you'd kept the vanity metric instead of
   it — walk through specifically what it would have hidden from you.
2. At what p99 value would you personally want to be paged, and what made you pick that
   number rather than a rounder one?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: ask the apprentice to add a metric live
during review and argue whether it belongs in the dashboard or is another vanity metric.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended
path for this task. Material AI assistance must be recorded in the submission notes with
provider/model (if known), purpose, and verification performed.

## Completion gate

Complete only once the dashboard is shown changing shape between the healthy and
unhealthy capture, and the demonstrated competency is approved.
