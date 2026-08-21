# Orchestrate a DAG That Tells the Truth After Failure

**Task ID:** `de1t2-002`
**Estimated effort:** 10 hours
**Module:** Orchestration

## Why this task exists

Cron that runs `python -m pipeline` as one blob cannot tell you which step
failed, cannot skip a downstream gate honestly, and cannot retry load
without extracting again. An orchestrator is useful only if task states
match reality: failed means failed, skipped means skipped, success means
the contract for that task held.

Apache Airflow is the default here because its documentation is public and
its DAG model is the industry baseline. Prefect, Dagster, or a thin
scheduler you write are acceptable if they can show the same dependency
and retry evidence.

## Authoritative resources

- **Apache Airflow Documentation** (primary): https://airflow.apache.org/docs/apache-airflow/stable/
  — DAGs, task dependencies, retries, task states (`success`, `failed`,
  `skipped`, `up_for_retry`, `upstream_failed`).
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Define a DAG (or equivalent) with four tasks: `extract` → `validate` →
   `load` → `quality_gate`. `quality_gate` must not start if `load` failed.
2. For each task, write what "success" means in one sentence (not "the
   process exited 0" alone — name the warehouse or contract condition).
   Set a documented retry count and timeout on `load`.
3. Inject a failure in `load` (raise, bad credentials, or a check you
   flip). Capture scheduler UI or logs: `validate` succeeded, `load`
   failed, `quality_gate` skipped or upstream-failed — not success.
4. Capture consumer-facing warehouse counts before and after that run.
   Last-good must hold.
5. Retry only `load`. When it succeeds, `quality_gate` must run and
   succeed without a new `extract`. Show that in run history or task
   instance logs.

Local Airflow (or the alternative) is expected. You do not need a
production cluster. Capture states as text logs or exported task-instance
rows if the UI is awkward to screenshot; screenshots are allowed as
supplements, not as the only evidence.

## Required evidence

- The DAG or equivalent definition showing the four tasks and
  dependencies
- Scheduler UI or log evidence that `quality_gate` is skipped or
  upstream-failed after an injected load failure
- Before and after warehouse counts across that failed run
- Run history showing a successful load retry followed by `quality_gate`
  success without a new extract
- A note stating retry count, timeout, and the success meaning of each
  task
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference for the DAG code.

## Acceptance criteria

- [ ] The DAG definition lists extract, validate, load, and quality_gate,
      with quality_gate downstream of load.
- [ ] After an injected load failure, the scheduler UI or task logs show
      quality_gate in a skipped or upstream-failed state, not success.
- [ ] The consumer-facing warehouse table is unchanged across the failed
      run, shown by before and after counts.
- [ ] A retry of load that succeeds is followed by quality_gate success
      without re-running extract, shown in task instance logs or run
      history.

The mentor may fail `validate` instead of `load` and ask which tasks must
not run. If `load` still runs, the dependencies are wrong.

## Reflection

Answer these in your own words after doing the work:

1. Why is a skipped quality_gate different from a successful one that
   checked nothing?
2. When would you clear and rerun from extract instead of retrying load,
   and how does the watermark or staging table influence that call?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to read a task-instance row and explain every state
transition on the failed run. Do not approve a single-task DAG that wraps
the whole pipeline, even if Airflow is "installed."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
explain each task state without the model. Material AI assistance must be
recorded in the submission notes with the provider/model (if known),
purpose, and verification performed.

## Completion gate

This task is not complete when the DAG runs green once. It is complete
once the failed-run states, last-good counts, and load-only retry are
submitted and the mentor approves the demonstrated competency.
