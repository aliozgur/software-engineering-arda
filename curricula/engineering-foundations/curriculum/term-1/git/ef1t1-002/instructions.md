# Open Your First Feature Branch and Pull Request

**Task ID:** `ef1t1-002`
**Estimated effort:** 5 hours
**Module:** Git

## Why this task matters

Branch, commit, push, open a pull request — this loop is how almost every real change reaches a shared codebase. It is easy to fumble under time pressure if you have never done it slowly and correctly first. This task exists so your first real branch-and-PR happens here, with room to get it wrong and fix it, not on your first week ticket.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (primary): https://missing.csail.mit.edu/2026/

## What you'll do

1. Pick a repository: a personal project, a fork of a small open-source project, or a practice repository your mentor points you to. It needs a `main` (or equivalent) branch you can safely branch from.
2. Decide on a branch-naming convention (e.g. `feature/<short-description>`) and write down what it means.
3. Create the branch and make one small, real change — not a placeholder file. A real change fixes something, adds something small, or improves a sentence in documentation.
4. Split the work into at least two commits, each with a message describing what changed and why.
5. Push the branch and open a pull request against the base branch. Write a description: what changed, why, and how a reviewer can verify it.
6. Note the PR's URL — you will need it as evidence and again in `ef1t1-006`.

## Evidence to submit

- A link to the actual pull request.
- The branch's commit log (`git log` output, or the PR's commits tab).
- The PR description text.
- An AI disclosure entry if AI helped write commit messages or the PR description.

## Acceptance criteria

- [ ] The branch name follows a consistent, documented convention that you can explain.
- [ ] The branch contains at least two commits, each with a message describing what changed and why, not just "wip" or "fix".
- [ ] A pull request exists comparing the branch to the base branch, with a description stating what changed, why, and how to verify it.
- [ ] The PR is linked in the submission and remains viewable by the mentor.

## Reflection

1. What would you have squashed or split differently if you had planned your commits before making them?
2. What is the smallest change you could imagine still being worth its own PR, versus batched into a larger one?

## Mentor review guide

- Open the linked pull request. Do not approve a description that only restates the branch name.
- Read the commit messages. Reject `wip`, `fix`, or one-word messages even if the diff is real.
- Ask the apprentice to walk through how a reviewer would verify the change using only the PR text.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations, hints, and quizzes about Git and PR conventions are allowed. Generating your commit messages or PR description for you is not — you should be able to defend every line of both.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
