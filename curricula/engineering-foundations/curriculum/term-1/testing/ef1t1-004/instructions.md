# Write Characterization Tests for Existing Code

**Task ID:** `ef1t1-004`
**Estimated effort:** 6 hours
**Module:** Testing

## Why this task matters

Most real test-writing isn't test-driven development against a blank file — it's adding a safety net to code that already exists, has no tests, and that you don't fully trust yet. A characterization test describes what the code *actually does*, right now, so that later changes can't silently break behavior someone (maybe you) depended on.

## Authoritative resources

- **Harvard CS50P — Introduction to Programming with Python** (primary): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

## What you'll do

1. Choose an untested Python function or small module with at least modest branching logic. Use the codebase you mapped in `ef1t1-003`, another small open-source project, or a snippet your mentor provides.
2. Using `pytest` (or `unittest`), write tests that describe what the code currently does — not what you think it should do.
3. Cover: at least one normal-input case, at least one edge case (empty input, boundary value, largest/smallest expected size), and at least one invalid or unexpected input.
4. Run the tests and confirm all pass against the code as it exists today.
5. While writing tests, if you find behavior that looks like a bug, do not fix it. Write down what you found instead — characterizing includes documenting the surprises.

## Evidence to submit

- The test file(s), committed with a message describing what they characterize.
- Console output of the test run showing all tests passing.
- A short note identifying the surprising or edge-case behavior found.
- An AI disclosure entry if AI helped generate test cases.

## Acceptance criteria

- [ ] At least 6 test cases exist, covering normal input, at least one edge case, and at least one invalid or unexpected input.
- [ ] All tests pass against the existing code, unmodified.
- [ ] A comment or accompanying note names at least one place where the code's current behavior looks surprising or wrong, without fixing it.
- [ ] Tests run with a single documented command, and that command's output is included in the evidence.

## Reflection

1. Which test case took the longest to design, and why?
2. If you had to change this code next week, which of your tests would you trust most to catch a regression?

## Mentor review guide

- Run the documented test command yourself. All tests must pass against unmodified production code.
- Count the cases. Fewer than 6, or no edge/invalid case, is a revision.
- Ask which surprising behavior they left unfixed, and why a later change would be unsafe without that test.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Hints on test design and explanations of `pytest`/`unittest` mechanics are allowed. Generating the full test suite for you is not — you should be able to explain why each test case exists and what it would catch.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
