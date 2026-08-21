# Debug a Reported Bug Methodically

**Task ID:** `ef1t1-005`
**Estimated effort:** 6 hours
**Module:** Debugging

## Why this task matters

Anyone can eventually stumble into a fix by changing things until the symptom disappears. What a mentor actually needs to see is whether you can debug *methodically*: reproduce the problem on demand, narrow down where behavior diverges from expectation, and prove the fix actually addresses the cause. The only way to demonstrate that after the fact is to have written it down as you went.

## Authoritative resources

- **MIT — The Missing Semester of Your CS Education** (primary): https://missing.csail.mit.edu/2026/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

## What you'll do

1. Find a real bug: something you broke yourself, a bug your mentor assigns, or a genuinely open, small issue on an open-source project.
2. Reproduce it with the smallest possible failing case — a short script or a failing test, not "run the whole app and watch."
3. Debug it methodically: form a hypothesis about the cause, test it (with a debugger, print/logging statements, or by narrowing the input), and record the result — whether it confirmed or ruled out the hypothesis — before moving to the next one.
4. Keep going until you've isolated the actual cause. Write down at least 3 hypotheses you tried, in order, including the wrong ones.
5. Fix the bug. Confirm the previously-failing case now passes and nothing else broke.
6. Add an automated regression test that would fail again if this bug came back.

## Evidence to submit

- Commit history showing a failing reproduction, then a fix, then a regression test, as separate, ordered commits.
- The debugging log naming the hypotheses tried and how each was ruled in or out.
- Test run output before and after the fix.
- An AI disclosure entry if AI suggested a hypothesis or fix.

## Acceptance criteria

- [ ] A written debugging log records at least 3 hypotheses tried in order, including ones that turned out wrong.
- [ ] A minimal, reproducible failing case exists before the fix, as a script or a failing test.
- [ ] After the fix, the previously failing case passes, and any pre-existing tests still pass.
- [ ] A new automated test exists that would fail again if the bug reappeared.

## Reflection

1. Which wrong hypothesis cost you the most time, and what would have ruled it out sooner?
2. What made the failing case hard (or easy) to minimize down to its smallest form?

## Mentor review guide

- Read the debugging log before the diff. If the log starts at the correct answer, the process was not recorded.
- Confirm the commit order: failing reproduction, then fix, then regression test.
- Ask them to break the fix on purpose and show the new test fail.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. You may ask an AI assistant to explain error messages or quiz you on debugging technique. If you disclose that AI suggested a hypothesis or fix, you must also record how you independently verified it — a suggestion you didn't verify is not evidence of understanding.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
