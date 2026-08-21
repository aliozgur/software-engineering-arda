# Refactor Existing Code Without Changing Behavior

**Task ID:** `ef1t2-003`
**Estimated effort:** 8 hours
**Module:** Refactoring

## Why this task matters

A pull request titled "cleanup" that also changes behavior is how regressions sneak past a tired reviewer. The professional split is boring and reliable: pin what the code does today with tests, then change only structure, one smell per commit, and keep the tests green after every step. If a test would have to change, you are no longer refactoring — you are changing behavior, and that belongs in a different change.

## Authoritative resources

- **Harvard CS50P — Introduction to Programming with Python** (primary): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use CS50P's testing material and the Python docs for the language constructs you touch. This is not a language-fundamentals task — you already write Python. The work is keeping behavior stable while you change shape.

## What you'll do

1. Start from existing Python you did not write for this task: the module you characterized in `ef1t1-004`, the codebase from `ef1t1-003`, or another small untested module. If it still has no tests, write characterization tests first and commit them *before* any refactor. Those tests describe current behavior, including surprises.
2. Record the exact test command and its full output. That is your before-snapshot. Do not start refactoring until that command is green.
3. Perform at least three distinct, named refactorings, each in its own commit. Allowed examples: extract a function, rename for meaning, reduce nesting, remove duplicated logic, split a module that has two reasons to change. Forbidden in the same commit: a new feature, a bug fix, a drive-by formatting sweep of unrelated files.
4. After each commit, re-run the same test command. If it fails, revert that commit's production change before continuing.
5. If you believe a public signature must change, it may only be a rename. List the old and new signature in your note and update every caller in that same commit. Any other signature change is a behavior change — put it back.
6. Write a refactoring note that maps each commit SHA to the smell you saw and the files you touched.

## Evidence to submit

- Test-command output captured before the first refactor commit and after the last, both showing zero failures.
- `git log` of the refactor branch with at least 3 commits that each contain only a named refactor.
- A refactoring note that maps each of those commit SHAs to the smell it addressed and the files it touched.
- The production-code diff for the branch.
- An AI disclosure entry if AI suggested a refactoring or rewrote a function.

## Acceptance criteria

- [ ] The documented test command run before the first refactor and after the last shows zero failures, and the passing-test count after is greater than or equal to the count before.
- [ ] At least 3 commits exist whose messages name a refactoring (for example extract function, rename, reduce nesting, remove duplication) and whose diffs contain no new feature and no bug fix.
- [ ] The refactoring note lists each of those commit SHAs, the smell addressed, and the file paths touched.
- [ ] No public function signature in the refactored module changed unless the note lists that exact signature and shows the rename-only caller updates landed in the same commit.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer these in your own words after doing the work:

1. Which smell was hardest to name before you changed the code, and what made it visible?
2. If a test had failed after the second commit, what would you have done instead of "fixing the test to match the new code"?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which commit best proves the tests — not your memory — protected the behavior?

## Mentor review guide

- Diff the before/after test output. A drop in passing-test count, or any failure, is a revision.
- Open each of the three named commits. A feature or bug fix mixed into a "refactor" commit is a revision.
- Ask them to point at one smell in the pre-refactor code and show the commit that addressed only that smell.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations of a refactoring name or a Python construct are allowed. Having AI rewrite the module or generate the three commits for you is not — you must be able to defend why each commit is behavior-preserving. Disclose any AI use: what you asked, and how you verified the tests still pinned the original behavior.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
