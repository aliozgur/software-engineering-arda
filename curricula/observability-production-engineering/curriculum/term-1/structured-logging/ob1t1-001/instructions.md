# Structured Logging You Can Actually Query

**Task ID:** `ob1t1-001`
**Estimated effort:** 6 hours
**Module:** Structured Logging

## Why this task exists

Every task later in this term — dashboards, traces, SLOs, alerts, postmortems — assumes
you already produce logs that are consistent enough to query mechanically. A log line
that's only readable by a human scrolling past it is a cost, not a signal. This task is
where you build the habit of designing a log schema on purpose, instead of sprinkling
`print`/`console.log` calls as you go.

LEARN BY DOING. GROW THROUGH MENTORSHIP. Reading is preparation; the schema, the
queries, and the redaction rule are the work.

## Authoritative resources

- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/ — read the
  logs section for how structured logs relate to traces and metrics.
- **The Twelve-Factor App** (reference): https://12factor.net/logs — factor XI, "Logs,"
  on treating logs as event streams rather than files you manage yourself.

Use official documentation as your primary source. If you use anything else, record it in
your notes.

## Work to complete

1. Pick a running service — an existing project of yours, or a small new one — with at
   least one request or operation path that has multiple internal steps worth logging.
2. Define a log schema before you write any log call: fixed field names (`timestamp`,
   `level`, `service`, `request_id`, `event`, plus two or three domain-specific fields),
   written down in a short schema note with what each field means.
3. Emit structured logs (JSON or a documented `key=value` format) at each meaningful step
   of one request path, all sharing a single correlation id (`request_id`) that is
   generated once at entry and carried through every downstream call.
4. Decide on three specific operational questions you want your logs to answer (for
   example: "how many requests failed with a 5xx in the last hour," or "show me the full
   path of request X"). Write and run one query or filter command per question (`jq`,
   `grep`, a log tool's query language — your choice) and capture the output.
5. Deliberately log a secret or credential value once, on purpose, then apply a redaction
   rule so it never appears in the output. Write down the rule and show a before/after
   line.

## Required evidence

- A log schema note naming each field and its meaning
- A log excerpt showing the full correlation-id chain for one request (at least three
  lines sharing the same id)
- The three query/filter commands and their captured output
- A written redaction rule with a before/after example line
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference where the logging code lives, alongside
the captured log/query output as files (not only screenshots).

## Acceptance criteria

- [ ] Every log line for the demonstrated request path parses as valid structured data
      (JSON or your documented key=value format).
- [ ] All log lines from one request share one identical correlation id value, shown
      across at least three lines.
- [ ] Each of the three named operational questions has a corresponding query and its
      captured output.
- [ ] No line in the submitted log sample contains a raw password, API key, token, or
      personal secret value.

The mentor may ask you to add a fourth operational question live and answer it with a new
query, or point at a log line and ask what question it fails to answer on its own. If you
are working without a mentor, write that fourth question yourself after the first three
are captured, and answer it with a new query against the same sample — do not add new
log fields to satisfy it.

## Reflection

Answer these in your own words after doing the work:

1. Which of your log fields would you drop first if storage cost forced you to cut one,
   and why that one?
2. Show one query a plain, unstructured text log could not answer without manual parsing
   — what made the structured version tractable?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional on this path. When a mentor is present: ask the apprentice to
answer a new operational question live, using only the existing log schema and a new
query — not new logging code. If they can't, the schema is probably missing a field the
whole task depended on.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the intended
path for this task. The apprentice must be able to explain, modify and defend every
submitted log line and query. Material AI assistance must be recorded in the submission
notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when the logging code runs without errors. It is complete once
the three queries are shown answering their stated questions, the redaction rule is
demonstrated, and the mentor (or, if you are working solo, your own recorded review
against the checklist above) approves the demonstrated competency.
