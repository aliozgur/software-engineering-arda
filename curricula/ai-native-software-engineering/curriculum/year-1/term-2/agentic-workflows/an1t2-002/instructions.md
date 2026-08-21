# Verifying a Multi-File Agentic Change

**Task ID:** `an1t2-002`  
**Estimated effort:** 8 hours  
**Module:** Agentic Workflows

## Why this task exists

A single-file agentic session (an1t1-004) is easy to check: read the diff, run the check, done. A change spread across three or more files can be locally reasonable in every individual file and still be globally wrong — an interface changed in one place, a caller left calling the old signature in another. This task pushes your verification skill from "does each file look right" to "do the changed pieces actually work together."

This is an apprenticeship task, not a content-consumption checkbox. Completion requires an integration-level check, not just a pass on each file's own unit tests.

## Authoritative resources

- **Best practices for agentic coding** (primary): https://code.claude.com/docs/en/best-practices

## Work to complete

1. Pick a feature that genuinely requires touching three or more files (e.g. a new field that flows through a data model, a service layer, and an API handler).
2. Before running the session, write the plan or scoping prompt naming the files expected to change. Commit it.
3. Run the agentic session and capture the resulting diff.
4. Write and run an integration-level test, or a documented manual walkthrough, that exercises at least two of the changed files together — not each file's unit tests in isolation.
5. Note any file that changed outside your original plan, and whether that was justified.

## Required evidence

- The plan or scoping prompt given to the assistant, committed before the session, naming the files expected to change
- The resulting diff across all changed files
- An integration-level test or documented manual walkthrough exercising the interaction between at least two of the changed files, run and shown passing
- A note on any file changed that was not in the original plan, and why
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references for the plan, the diff, and the integration-level check.

## Acceptance criteria

- [ ] The diff touches three or more files.
- [ ] An integration-level check exists that exercises at least two changed files together, not only unit tests of each file in isolation.
- [ ] The integration-level check is shown passing against the final change.
- [ ] Any out-of-plan file change is explicitly noted and justified.

The mentor may ask you to break the interaction deliberately (revert one file, keep the others) and show that your integration-level check catches it.

## Reflection

Answer these in your own words after doing the work:

1. What would each file's unit tests have missed here, that the integration-level check caught (or would have caught)?
2. Did the session touch anything outside your plan? If so, was that a scope problem or a reasonable side effect?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to identify the specific seam between two files where a mismatch could hide from per-file testing.
- Verify the integration-level check would actually fail if one of the changed files were reverted.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed because the agentic implementation is the intended path — the skill being assessed is holistic verification of a multi-file change, not writing each file by hand. The apprentice must be able to explain, modify, test, and defend every changed file and the interactions between them. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
