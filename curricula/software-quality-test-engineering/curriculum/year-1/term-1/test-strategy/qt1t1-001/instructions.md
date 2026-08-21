# Map a Test Strategy to Real Risk

**Task ID:** `qt1t1-001`  
**Estimated effort:** 10 hours  
**Module:** Test strategy

## Why this task exists

Undirected test-writing produces suites that are expensive to maintain and still miss
the failures that matter. A risk-to-layer map is the artifact a team actually uses to
decide what to test next, instead of testing everything a little or testing whatever
is easiest to reach.

This is an apprenticeship task, not a content-consumption checkbox. Reading is only
preparation. Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

No single official document is the source of truth for this task. Use the primary
documentation of the language, test runner, and system you already work in. If you
consult extra material, record it in your learning notes and prefer primary
documentation over tutorial aggregation sites.

## Work to complete

1. Pick a real system you control — a service, library, or application you can change
   and run locally. A toy CRUD demo built only for this task is not enough; the risks
   have to be ones a user or operator would actually notice.
2. List at least eight distinct failure modes. Each row is one wrong thing that can
   happen (wrong total, lost write, leaked token, silent timeout), not a test-type
   name. Write them in `docs/test-strategy.md` (or an equivalent committed Markdown
   file).
3. Map each failure mode to exactly one test layer — unit, integration, contract,
   end-to-end, or synthetic. Do not put the same risk on two layers "to be safe."
   If two layers could catch it, pick the cheapest one that would actually notice
   and write why the others are the wrong first choice.
4. Implement at least five passing tests, each referencing its risk by name in the
   test name or a comment so a mentor can join the table to the suite.
5. Revert one corresponding production fix (or deliberately break the behavior one
   of those tests claims to protect). Capture the failing run, restore the fix, and
   capture the passing run.
6. Document a single command that runs the full suite to completion, and run it.

## Required evidence

- Git history showing the suite built up incrementally, not in one commit
- A committed risk-to-test-layer table (e.g. `docs/test-strategy.md`)
- Command and output showing the full suite passing
- A commit or diff showing one test failing when its fix is reverted, then passing
  again once restored
- A reflection note answering the task's questions

Where code is produced, submit a repository URL plus an immutable commit or tag
reference when possible. Do not submit only screenshots of code.

## Acceptance criteria

- [ ] The risk table lists at least 8 distinct failure modes, each mapped to exactly
      one test layer.
- [ ] At least 5 listed risks have a passing test that references the risk by name
      or comment.
- [ ] At least 1 test is shown failing when its corresponding fix is reverted, and
      passing again once restored.
- [ ] The full suite runs to completion with a single documented command.

The mentor may request a live explanation of why one risk sits on its chosen layer
before approval. A green suite alone is not proof of a strategy.

## Reflection

Answer these in your own words after doing the work:

1. Which failure mode were you most tempted to put on two layers, and what made you
   pick the one you kept?
2. Which listed risk still has no test, and what would have to go wrong in production
   before you would add one?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Point at one row in the table and ask why that layer, not the cheaper or more
  expensive neighbor.
- Do not approve a generic pyramid copied from a blog with dummy risks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. The apprentice must be able to explain, modify, test
and defend every submitted artifact. Material AI assistance must be recorded in the
submission notes with the provider/model (if known), purpose, and verification
performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the
evidence is submitted and the mentor approves the demonstrated competency.
