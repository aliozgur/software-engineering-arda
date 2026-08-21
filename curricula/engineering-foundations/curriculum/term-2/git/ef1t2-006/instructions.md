# Find a Regression with git bisect

**Task ID:** `ef1t2-006`
**Estimated effort:** 6 hours
**Module:** Git

## Why this task matters

When something that used to work stops working, the useful question is not "what looks suspicious in the latest diff?" It is "which commit first made the check fail?" `git bisect` answers that by binary-searching history. Guessing from `git log` is faster only when you are lucky. This task makes you run the method that still works when the history is long and the break is quiet.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (primary): https://missing.csail.mit.edu/2026/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use Pro Git's debugging chapter for bisect. Use Missing Semester for the surrounding Git mental model. Use the Python docs only as far as you need to write a small check script.

## What you'll do

1. Use a Git repository with Python code and a real regression in history. You may construct this on a disposable branch: start from working behavior, make at least eight commits of mixed real work, and let one middle commit silently break a previously-working behavior. Hide the break — do not put `BREAKS THE PARSER` in the commit message.
2. Write a small automated check (a script or a single `pytest` invocation wrapped so it can be used by `git bisect run`) that exits `0` when the old behavior holds and non-zero when the regression is present. Commit the check. Confirm it fails on `HEAD` and passes on a known-good ancestor.
3. Run `git bisect` from that known-good commit to the known-bad tip. Prefer `git bisect run <check>` so the log is mechanical. If you mark commits by hand, record every mark.
4. When bisect reports the first bad commit, open that commit's diff. Write one sentence on the change that caused the break — not "this commit is bad," but which edit did it.
5. Save the full `git bisect log`. Reset the bisect state when you are done. Do not "just look at `git log` and guess" — without a bisect log this task is incomplete.
6. Record `git rev-list --count <good>..<bad>` (or the equivalent range you bisected) and confirm it is at least 8.

## Evidence to submit

- The full `git bisect log` (or an equivalent recorded session) showing at least 3 bisect steps.
- The committed automated check script that exits 0 on good behavior and non-zero on the regression.
- A written note naming the first bad commit's full SHA, its subject line, and one sentence on the change that caused the break.
- `git rev-list --count` output showing at least 8 commits in the bisected range.
- An AI disclosure entry if AI helped write the check script or interpret the bisect result.

## Acceptance criteria

- [ ] A `git bisect log` (or equivalent recorded session) exists and shows at least 3 bisect steps that marked commits good or bad.
- [ ] The automated check script is committed in the repository and is the classifier used during bisect (named in the log or in the run command).
- [ ] The note names the first bad commit's full SHA and subject, plus one sentence on the causal change in that commit's diff.
- [ ] `git rev-list --count` from the known-good commit to the known-bad tip is at least 8.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer these in your own words after doing the work:

1. What would have gone wrong if your check exited non-zero for an unrelated reason (a missing dependency, a flaky test)?
2. Why is a commit message like "fix stuff" useless once you are bisecting, and what would you write instead next time?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you searched history instead of guessing?

## Mentor review guide

- Read the bisect log. Fewer than three steps, or a log that only names the answer with no marks, is a revision.
- Run the check on the reported good ancestor and on the reported bad commit if the repo is available. The exits must disagree.
- Ask them to point at the causal hunk in the first bad commit. If they only know the SHA, request revision.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations of what `git bisect` does to `HEAD`, or why a check must be deterministic, are allowed. Having AI tell you which commit is bad from a pasted `git log` is not — the log of the bisect you ran is the evidence. Disclose any AI use: what you asked, and how you verified the check's exit codes yourself.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
