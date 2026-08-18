# Logs, Metrics and Traces

**Task ID:** `y3t2-003`  
**Estimated effort:** 16 hours  
**Module:** Observability

## Why this task exists

Design software so production behavior can be understood.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Add structured logs with correlation identifiers.
2. Expose a small set of meaningful metrics.
3. Instrument one cross-component request with OpenTelemetry tracing.
4. Create a dashboard or query set for latency, errors and throughput.
5. Write a runbook for one failure mode.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Signals answer specific operational questions.
- [ ] No passwords/tokens/personal secrets are logged.
- [ ] Trace connects relevant components.
- [ ] Runbook contains detection, diagnosis and recovery steps.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What question does each metric answer?
2. When is a log insufficient compared with a trace?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Inject latency/error and ask apprentice to diagnose using telemetry.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
