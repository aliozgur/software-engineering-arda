# Test-Driven Verification of AI-Generated Code

**Task ID:** `an1t1-003`  
**Estimated effort:** 8 hours  
**Module:** Verification

## Why this task exists

If you write tests after looking at what the AI produced, the tests tend to describe what the code does rather than what it should do — they mirror the implementation instead of checking it. Writing the tests first, from the intended behavior, and never editing them to match a convenient AI answer, is what makes verification independent instead of theater.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence that the tests existed, and failed, before any implementation did.

## Authoritative resources

- **Martin Fowler — Test-Driven Development** (primary): https://martinfowler.com/bliki/TestDrivenDevelopment.html
- **Anthropic prompt engineering** (reference): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

Use Fowler's red-green-refactor description as the process model. Use the prompt guide only when you request the implementation *after* the failing tests exist. You may use official documentation for your project's test runner; record extra sources in your notes.

## Work to complete

1. Pick a small feature with clear input/output behavior, on a project you actually maintain.
2. Write the test suite first, from the intended behavior, not from any code yet. Commit it on its own.
3. Run the tests against a stub or empty implementation and capture the failing output.
4. Request an AI-generated implementation. Run the untouched test suite against it and capture the passing output.
5. If a test turns out to be wrong once you see the real implementation (an actually incorrect assumption, not an inconvenient one), change it — but write down why, explicitly, before you do.

## Required evidence

- A commit containing only the test suite, before any implementation commit exists
- A test run log showing the tests failing against a stub or empty implementation
- A test run log showing the AI-generated implementation passing the untouched test suite
- A note describing any test you had to change after seeing the AI's implementation, and whether that change was justified
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references for the test-only commit and the implementation commit.

## Acceptance criteria

- [ ] The test-suite commit precedes the implementation commit in git history.
- [ ] A failing test run against a stub implementation is included as evidence.
- [ ] A passing test run against the AI-generated implementation is included as evidence.
- [ ] Any post-hoc test change is explicitly justified in the note, not silently made.

The mentor may ask you to point to the specific line of the spec or ticket that each test traces back to. A test suite written to match the implementation, rather than the intended behavior, does not pass this bar even if all evidence items are technically present.

## Reflection

Answer these in your own words after doing the work:

1. Did any test fail against the AI's implementation on the first try? What did that reveal?
2. What's the difference between a test you changed because it was wrong, and one you changed because it was inconvenient?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Check the git timestamps yourself rather than trusting the narrative — the ordering claim is the entire point of this task.
- Ask about any test change: was it caught by rereading the spec, or by seeing what the AI produced?

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed for the *implementation* only — the test suite must remain your own, independent work, written before you request code. The apprentice must be able to explain what each test would catch if the implementation drifted. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
