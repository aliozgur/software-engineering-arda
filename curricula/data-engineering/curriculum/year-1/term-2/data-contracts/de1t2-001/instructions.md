# Write a Data Contract Producers Cannot Ignore

**Task ID:** `de1t2-001`
**Estimated effort:** 8 hours
**Module:** Data Contracts

## Why this task exists

Quality rules in tests catch what you already thought of. A contract is the
agreement a producer can break on a Tuesday without telling you. It has to
be a file: grain, keys, types, nulls, freshness, owner, version. The load
path has to read that file. A wiki page nobody validates is hope.

This is still not analytics. You are not profiling a dataset for
interesting columns. You are stating what a consumer is allowed to assume.

## Authoritative resources

- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — types and constraints as the physical edge of the contract.
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
  — enough to write a validator that exits non-zero.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Write a contract file (JSON, YAML, or Markdown with a machine-readable
   section). It must name: grain (one sentence), primary key, every field's
   type and nullability, a freshness SLA (for example "staging max
   event_time no older than 6 hours at publish"), owner, and version.
2. Write a validator the job can run against a batch. Rejection is a
   non-zero process exit or an equivalent hard failure the orchestrator
   could see — not a log line that publish ignores.
3. Demonstrate a missing required field: rejected, not published, output
   includes the field name.
4. Demonstrate an additive optional field: accepted, and the contract
   states whether that requires a minor version bump. The validator
   enforces the rule you wrote.
5. Demonstrate a removed or renamed required field: classified as breaking
   in a changelog, rejected by the validator. Write a short consumer note:
   three assumptions a downstream job may make after a successful
   validate.

## Required evidence

- The contract file
- Validator output rejecting a batch that is missing a required field,
  including the field name
- Validator output accepting a batch that only adds an optional field,
  plus the contract rule that allows it
- Validator output rejecting a removed or renamed required field, plus the
  changelog line that marks it breaking
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. The validator must be
runnable from a documented command.

## Acceptance criteria

- [ ] The contract file names grain, primary key, every field's type and
      nullability, a freshness SLA, an owner, and a version.
- [ ] A batch missing a required field is rejected by the validator with a
      non-zero exit or equivalent, is not published, and the captured
      output includes the field name.
- [ ] A batch that only adds an optional field is accepted without a major
      version bump, or the contract requires a minor bump and the
      validator enforces that rule — the chosen rule is written in the
      contract.
- [ ] Removing or renaming a required field is classified as breaking in
      the contract changelog and is rejected by the validator.

The mentor may add a field to a fixture and ask "breaking or not?" before
you run anything. If you need to run the validator to know, the changelog
is not yet a decision record.

## Reflection

Answer these in your own words after doing the work:

1. What may a consumer assume after validate succeeds, and what must they
   still not assume?
2. Who owns a freshness miss — producer, pipeline, or consumer — in your
   contract, and where is that sentence?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to walk a breaking change as if they were the producer:
which version number moves, who is notified, what happens to in-flight
batches. Do not approve a contract that is only a JSON Schema of types
with no grain, SLA, or owner.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
classify a change as additive or breaking without the model. Material AI
assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when a contract file exists. It is complete once
the three validator demonstrations and the consumer note are submitted and
the mentor approves the demonstrated competency.
