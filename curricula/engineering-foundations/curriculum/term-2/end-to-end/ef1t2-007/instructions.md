# Ship a Scoped Change End to End

**Task ID:** `ef1t2-007`
**Estimated effort:** 9 hours
**Module:** End to End

## Why this task matters

A junior engineer's week is rarely a puzzle from a textbook. It is a written request, a plan you can defend, a change small enough to review, tests that prove the new path, and a pull request that does not make the reviewer reverse-engineer your intent. This task is that loop, done once slowly, with the plan committed before the code so the process is visible. LEARN BY DOING. GROW THROUGH MENTORSHIP.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2
- **Harvard CS50P — Introduction to Programming with Python** (primary): https://cs50.harvard.edu/python/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

You already have the Git and Python mechanics from earlier tasks. Use these as references, not as a new language track.

## What you'll do

1. Start from a written request. A mentor can assign one. If you are working without a mentor, write a one-paragraph ticket as if it arrived from a teammate, commit it, and then treat it as incoming — do not keep editing the ticket to match whatever you later built.
2. In an *existing* Python codebase (the one from `ef1t1-003` / `ef1t2-004` is the default), write a plan before any implementation: files you will touch, risks, tests you will add or run, an integer hour estimate, and what is out of scope. Commit that plan.
3. Implement the request in incremental commits. Each commit should be a step a reviewer could understand alone. A single "all the work" commit fails this task.
4. Add or adjust automated tests so the new behavior has coverage. Keep the production diff reviewable: prefer at most 200 lines of production code. If you cannot stay under that, the estimate note must say why and name the next split you would make.
5. Open a pull request. The description states the problem first, then the change, then the exact verification command and the result you got, then out of scope. A reviewer who has not seen the ticket should still know what to check.
6. Record planned hours versus actual hours, and one thing you would split or estimate differently next time.

## Evidence to submit

- The incoming request text, committed as its own file or quoted in the plan.
- A plan commit that precedes every implementation commit and includes files, risks, tests, an hour estimate, and out of scope.
- `git log` showing incremental implementation commits, not a single final commit.
- Test-command output for the documented verification command, showing the new behavior covered and passing.
- A pull request link plus the raw description text (problem, change, verification command and its result, out of scope).
- An estimate-versus-actual note with hours and one thing you would split or estimate differently next time.
- An AI disclosure entry if AI helped plan, implement, or write the pull request.

## Acceptance criteria

- [ ] A plan commit exists before any implementation commit and names files to touch, risks, tests to add or run, an integer hour estimate, and out of scope.
- [ ] The pull request description includes the problem, the change, at least one concrete verification command with its recorded result, and what was left out of scope.
- [ ] Automated tests covering the new behavior pass via a single documented command whose output is in the evidence.
- [ ] The production-code diff is at most 200 lines, or the estimate note states why a larger change could not be split and names the next split.
- [ ] The estimate-versus-actual note records planned hours, actual hours, and one named thing that would be estimated or scoped differently next time.

Check your own submission against each line above before asking for review — a mentor will check the same five things.

## Reflection

Answer these in your own words after doing the work:

1. Where did the estimate go wrong, in hours, and what in the plan failed to predict that?
2. If a reviewer opened only the pull request — not your plan, not this task — what would they still be missing, and what would you add to the description?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you shipped a scoped change, not a pile of unreviewed work?

## Mentor review guide

- Confirm `git log` order: request and plan before implementation. A rewritten history that hides that order is a revision.
- Cover the diff and read only the PR description. If you cannot say how to verify the change, request revision.
- Count production diff lines. Over 200 without a named next split is a revision.
- Ask one question about a risk listed in the plan that they did not mention in the PR. The answer should exist.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations, hints, and quizzes about planning or Git/PR mechanics are allowed. Generating the plan, the implementation, or the pull request description for you is not — you must be able to defend the estimate, the diff, and every verification claim. Disclose any AI use: what you asked, and what you verified yourself afterward.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
