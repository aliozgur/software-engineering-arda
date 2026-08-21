# Refactoring AI-Generated Code for Maintainability

**Task ID:** `an1t2-001`  
**Estimated effort:** 8 hours  
**Module:** Refactoring

## Why this task exists

Code that passes its tests can still be a mess: a 90-line function doing three things, duplicated logic across two branches, a class that mixes I/O with business rules. AI-generated code has this problem at least as often as human-written code, because "make the tests pass" and "produce a maintainable design" are different goals the assistant wasn't necessarily optimizing for. Refactoring it under test, deliberately, is where your design judgment shows up independent of whether you or an AI wrote the first draft.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence that behavior didn't change and that each refactor step had a specific, named reason.

## Authoritative resources

- **Martin Fowler — Catalog of Refactorings** (primary): https://refactoring.com/catalog/
- **Google engineering practices: code review** (reference): https://google.github.io/eng-practices/review/

Use the catalog to name the smell and the refactor, not as a list to apply mechanically. The review guide is useful for judging whether the post-refactor design is actually simpler for the next reader.

## Work to complete

1. Take a working AI-generated implementation with an existing test suite — one of your own from an earlier task, or generate a fresh one for this purpose.
2. Confirm the test suite passes as-is and capture that run.
3. Refactor in one or more separate commits, each targeting one named design smell (long function, duplicated logic, mixed responsibilities, etc.). Do not change observable behavior.
4. Confirm the test suite still passes after each refactor commit, or at minimum after the full sequence, and capture that run.

## Required evidence

- The pre-refactor version and post-refactor version, both committed, with the refactor in one or more commits separate from the original generation
- A passing test run immediately before the refactor and an identical passing test run immediately after, proving behavior didn't change
- A note naming the specific design smell targeted by each refactor commit (e.g. long function, duplicated logic, mixed responsibilities)
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references for the pre-refactor state, each refactor commit, and the two test runs.

## Acceptance criteria

- [ ] At least one refactor commit exists that is separate from the original AI-generated commit.
- [ ] The test suite passes both immediately before and immediately after the refactor, shown by two separate test run logs.
- [ ] No function in the post-refactor diff exceeds 40 lines, or any exception is explicitly justified in the note.
- [ ] Each refactor commit's message or the accompanying note names the specific design smell it addressed.

The mentor may ask you to point to the exact smell a given commit fixed, or to demonstrate that a deliberately reintroduced bug is caught by the existing tests.

## Reflection

Answer these in your own words after doing the work:

1. What made you notice this particular smell in code that otherwise "worked"?
2. Did refactoring under test change your confidence in the result, compared to refactoring without running anything?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Diff the pre- and post-refactor behavior yourself against a case not in the test suite, if one comes to mind.
- Challenge any refactor commit whose stated smell doesn't match what actually changed.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed because proposing a refactor or naming a smell can be part of the work — you must still be able to explain why each change was made and confirm behavior didn't shift. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
