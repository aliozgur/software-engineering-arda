# Correlate Logs, Metrics, and Traces for One Failure

**Task ID:** `pd1t2-005`
**Estimated effort:** 13 hours
**Module:** Telemetry correlation

## Why this task exists

Three isolated backends are not observability. You need one request — a failure you caused — that you can find in a log line, a metric movement, and a trace. Term 3 incidents will assume you can join those three without guessing.

This is an apprenticeship task, not a content-consumption checkbox. Reading OpenTelemetry and Prometheus docs is only preparation. Completion requires a diagnosis note that names one trace id.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/

Keep the local Prometheus and trace backend from the previous two tasks. Structured logs may go to stdout collected by the cluster or to a local file; do not require a paid log product.

## Work to complete

1. Change request logging so each request (or each failed request) emits a structured line that includes the trace id (and span id if you have it). JSON or `key=value` is acceptable; free-form prose logs are not.
2. Add a documented way to trigger one failure: a route that returns 5xx, a forced timeout, or a dependency you take down. The trigger must be a command or request a mentor can replay.
3. Trigger it once. Capture: the log line, the PromQL (or graph) that moved, and the trace for that trace id.
4. Write `DIAGNOSIS.md` for that single request: timestamp, trace id, what you triggered, which span or log line shows the failure, which metric moved and by how much.
5. Document how to start logs + Prometheus + the trace backend from this repository.

## Required evidence

- Committed logging change that emits structured request logs including a trace id field
- A diagnosis note that names one request by trace id and timestamp and attaches the matching log line, metric movement, and trace
- Command or script that deliberately triggers the documented failure
- README stating how to start logs, Prometheus, and the trace backend from this repository
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit three unrelated screenshots from different times of day.

## Acceptance criteria

- [ ] Structured request logs (JSON or key=value) include a trace id field on the request path that failed.
- [ ] The diagnosis note names one request (trace id plus timestamp) and shows the matching log line, a metric that moved, and the matching trace.
- [ ] The failure is triggered by a documented action (forced 5xx, timeout, or bad dependency), not an unexplained crash.
- [ ] The diagnosis note states the failing span or log line and the metric that moved. All three backends start locally from the repository.

A mentor should be able to replay the trigger and find the same join key.

## Reflection

Answer these in your own words after doing the work:

1. If the trace id had been missing from the log, what would you have tried next — and why is that slower?
2. Which of the three signals would you trust first at 02:00, and which one can lie while the others look fine?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to hide the diagnosis note and find the request from the trace id in the logs only.
- Do not approve a note that describes "the system was slow" without a trace id, or logs that are unstructured paragraphs.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — performing the join and writing the diagnosis yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved one failure joined across logs, metrics and traces. LEARN BY DOING. GROW THROUGH MENTORSHIP.
