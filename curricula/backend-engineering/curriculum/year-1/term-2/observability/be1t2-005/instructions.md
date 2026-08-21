# Logs, Metrics and Traces on the Request Path

**Task ID:** `be1t2-005`
**Estimated effort:** 14 hours
**Module:** Observability

## Why this task exists

You cannot operate or defend a service you cannot see. This task
instruments the existing Python API so a single request is visible as
structured logs, a scrapeable metric, and a trace. Later tasks will
ask you to point at these signals under load and during a failure
drill — they have to exist first.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use OpenTelemetry for traces (and metrics if you emit through it).
Prometheus format is acceptable for the scrapeable metric even if a
collector is not running yet.

## Work to complete

1. Emit structured JSON logs from the API. Every request log line
   includes a request id. Propagate that id to at least one
   downstream log line (a database query log or a queue publish log).
2. Expose request count and request latency as metrics. A `/metrics`
   scrape in Prometheus text format is enough; an OpenTelemetry
   export is also fine.
3. Produce a trace for a request that includes at least two spans —
   the HTTP handler and either the database call or the queue
   publish. Export one trace as a file in the repository.
4. Document the exact commands to run the service, scrape metrics,
   and produce one trace on a clean checkout.
5. Grep the log samples and the logging configuration for tokens,
   passwords, and secrets. Fix anything that leaks. Commit the grep
   command you used.
6. Add the instrumentation incrementally: logs first, then metrics,
   then traces. Do not drop a complete observability stack in one
   commit.

You do not need a production collector cluster. You do need artifacts
a mentor can open without your laptop's UI still running.

## Required evidence

- Committed sample log lines from a single request that share one
  request id, including a line from a downstream call
- A scrape or export of metrics that includes request count and a
  latency histogram or summary
- A trace export (JSON, Jaeger dump, or collector file) showing at
  least two spans for one request
- README commands to run the service and produce logs, a metrics
  scrape, and one trace
- Git history showing logs, then metrics, then traces as separate
  commits, plus a grep proving no secrets in logs

Submit a repository URL plus a commit reference. Do not submit only
screenshots of a dashboard.

## Acceptance criteria

- [ ] A single request produces at least two structured log lines
      that share one request id, one of them from a database or
      queue call.
- [ ] A metrics endpoint or collector export includes a
      request-count metric and a latency histogram or summary.
- [ ] A committed trace export for one request contains at least
      two spans.
- [ ] A grep of committed log samples and logging configuration
      shows no token, password, or secret values.

The mentor may send one request live and ask you to retrieve its
request id, its metric increment, and its trace without searching
by timestamp alone.

## Reflection

Answer these in your own words after doing the work:

1. If a request is slow, which of the three signals do you look at
   first, and why?
2. What did you almost log that would have been a secret?
3. What is a span that you did *not* add, and what would it have
   told you?

Also record:

- What took longer than expected?
- What would you instrument differently next time?
- What remains unclear?

## Mentor review guide

- Ask the apprentice to pick one request id and walk from log line
  to metric to trace.
- Confirm the trace has two real spans, not one span renamed twice.
- Reject logs that include Authorization headers or connection
  strings with passwords.

Suggested review outcome: **Approve**, **Request revision**, or
**Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes.
Solution generation is not the intended path for this task. Material
AI assistance must be disclosed with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the
mentor approves the demonstrated signals — not when a `/metrics`
endpoint merely returns text.
