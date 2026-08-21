# Measure Suite Quality with Mutation Testing

**Task ID:** `qt1t1-003`  
**Estimated effort:** 14 hours  
**Module:** Mutation testing

## Why this task exists

Line and branch coverage only prove code executed during a test run, not that a
test would notice a wrong result. Mutation testing exposes assertions that are
too weak or missing entirely, which a coverage percentage cannot detect.

This is an apprenticeship task, not a content-consumption checkbox. A high
coverage number without a mutation score is not the work.

## Authoritative resources

- **Stryker Mutator Documentation** (primary): https://stryker-mutator.io/docs/

Use the official Stryker documentation as the primary source. You may use
additional sources, but record them in your learning notes and prefer primary
documentation over tutorial aggregation sites.

## Work to complete

1. Choose an existing module with a real test suite — not a file you write only
   so Stryker has something to mutate. Record both the line-coverage percentage
   and the mutation score for that same module before you change any test.
2. Read the surviving mutants. Pick at least three and describe each as the
   undetected wrong behavior a user or caller would see, not as a mutator name
   (`>=` became `>` is not enough; say what decision that would get wrong).
3. Add or strengthen tests until at least two of those mutants are killed.
   Commit each change tied to a specific surviving mutant. Re-run Stryker and
   record the after score.
4. Deliberately leave one surviving mutant alive. Write a justification that
   names the mutant and why killing it is not worth the test cost (equivalent
   mutant, uninteresting boundary, code you intend to delete). "I ran out of
   time" is not a justification.
5. Keep the before and after Stryker output (or HTML report) with the command
   and a timestamp.

## Required evidence

- Mutation test output before and after, committed or pasted with the command
  and a timestamp
- Commits adding or strengthening tests, each tied to a specific surviving
  mutant
- A written justification for the one surviving mutant left un-killed
- A reflection note answering the task's questions

Where code is produced, submit a repository URL plus an immutable commit or tag
reference when possible. Do not submit only a coverage percentage.

## Acceptance criteria

- [ ] A baseline mutation score and line-coverage percentage are both recorded
      for the same module.
- [ ] At least 3 surviving mutants are individually described in terms of the
      undetected wrong behavior.
- [ ] At least 2 of those mutants are killed by a new or strengthened test,
      shown by a before/after mutation score.
- [ ] One surviving mutant is deliberately left alive with a written
      justification.

The mentor may pick a surviving mutant you did not discuss and ask whether you
would kill it and why. A higher score with no before/after pair is not enough.

## Reflection

Answer these in your own words after doing the work:

1. What did the mutation score reveal that the coverage percentage hid?
2. For the mutant you left alive, what would have to change about the product
   before you would spend a test on it?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to walk through one killed mutant: original code, mutant,
  and the assertion that now fails.
- Do not approve a run that only reports a score with no mutant-level write-up.

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
