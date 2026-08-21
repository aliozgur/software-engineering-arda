# Load Once, Then Prove You Can Load Again

**Task ID:** `de1t1-002`
**Estimated effort:** 8 hours
**Module:** Batch ETL

## Why this task exists

The previous task gave you schemas. This task gives you a job. The job is not
done when the first run finishes green. It is done when a second run against
the same snapshot leaves the warehouse key set unchanged.

This is still not analysis. pandas is allowed as a transform tool if you can
test the transform. It is not allowed as a place to hide a one-off notebook
cleanse that nobody can rerun.

## Authoritative resources

- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
- **pandas User Guide** (reference): https://pandas.pydata.org/docs/user_guide/index.html
  — use it only if a transform earns a function you can call twice.

Use official documentation as the primary source. If you use anything else,
record it in your notes.

## Work to complete

1. Write a Python extract that reads the operational source (files, a fixture
   HTTP endpoint, or a dump you control) into `staging`. This task is a full
   extract, not incremental.
2. Transform and load into `warehouse`. ELT in SQL or ETL in Python are both
   acceptable. Write one paragraph naming which you chose and what would make
   you switch.
3. Document the command that runs the whole job from a clean shell
   (`python -m ...`, a Makefile target, or equivalent). No GUI-only clicks.
4. Run the job twice against an unchanged source snapshot. Capture warehouse
   row counts and the ordered list or hash of primary keys after each run.
5. State how staging is reset on a full extract (truncate, replace, swap).
   The second extract must not append a second copy of the same source snapshot
   into staging unless you can prove the warehouse load still de-duplicates.

## Required evidence

- The job command and the Python or SQL entrypoint it runs
- Captured warehouse row counts and primary-key queries after run 1 and run 2
- A short note naming the staging replace-or-truncate strategy
- Git history with at least three commits that are not a single final dump
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Do not submit only screenshots
of a notebook.

## Acceptance criteria

- [ ] The job is invoked by a documented command that takes no hidden manual
      GUI steps.
- [ ] After two full runs on an unchanged source snapshot, the warehouse row
      count is identical and the primary-key set is identical, shown as two
      captured count or key queries.
- [ ] A note names whether staging is truncated, replaced, or swapped before
      each full extract.
- [ ] Git history contains at least three commits that each change the job or
      schema, not one commit of the finished tree.

The mentor may ask you to run the command while they watch, then run it again
immediately. If the second run needs a manual delete, the job is not a job yet.

## Reflection

Answer these in your own words after doing the work:

1. If the process dies after writing staging but before writing the warehouse,
   what does the next full run do, and is that written down?
2. Where would a pandas one-liner have hidden a grain change, if you used
   pandas at all — or why you did not?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Ask the apprentice to add one source row and rerun. The warehouse should gain
exactly that key, not a full restatement they cannot explain. Do not approve a
notebook whose only "job" is "Run All."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not
the intended path for this task. The apprentice must be able to explain, modify
and rerun every submitted job. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

This task is not complete when the first load succeeds. It is complete once the
second-run evidence is submitted and the mentor approves the demonstrated
competency.
