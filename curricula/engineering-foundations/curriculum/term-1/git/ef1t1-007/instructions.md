# Resolve a Merge Conflict and Clean Up History with Rebase

**Task ID:** `ef1t1-007`
**Estimated effort:** 5 hours
**Module:** Git

## Why this task matters

Merge conflicts and messy local history are routine parts of working with other people in the same codebase, not rare disasters. The skill worth building now, before it happens on something that matters, is handling both calmly: resolving a conflict without losing either side's intent, and cleaning up your own history with rebase without losing any work in the process.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2
- **MIT — The Missing Semester of Your CS Education** (primary): https://missing.csail.mit.edu/2026/

## What you'll do

**Part 1 — Merge conflict**

1. Create two branches from the same starting point that both edit the same lines of the same file, in different ways.
2. Merge one into the other and resolve the resulting conflict by hand, keeping both intended changes wherever they don't genuinely conflict.

**Part 2 — Rebase**

3. On a separate, disposable branch, make several small, messy commits on purpose: typos, "wip", a change you then partially revert.
4. Use rebase to squash, reorder, or edit those commits into a small number that tell a clear story.
5. Before you consider it done, make sure you could still recover the pre-rebase state if you needed to (reflog, or a backup branch/tag made before you started).
6. Write, in your own words, why the "same" commit has a different hash before and after the rebase.

## Evidence to submit

- The repository or branch showing the merge commit and the conflicted-then-resolved file.
- `git log` (or reflog) output showing commit hashes before and after the rebase.
- The written explanation of why rebase changes commit hashes.
- An AI disclosure entry if AI helped resolve the conflict or plan the rebase.

## Acceptance criteria

- [ ] The conflicted merge is completed: the merge commit exists, and the resolved file contains the intended content from both sides where they don't actually conflict.
- [ ] A written note explains, in your own words, why the same logical change has a different commit hash before and after a rebase.
- [ ] The cleaned-up branch has fewer commits than the messy branch, and no remaining commit message is only "wip", "fix", "typo", or a single word.
- [ ] No work from the rebased branch was lost — the pre-rebase state is still recoverable.

## Reflection

1. What did you do, specifically, to make sure the rebase didn't lose anything?
2. If a teammate had already pulled your messy branch before you rebased it, what would go wrong, and how would you avoid that?

## Mentor review guide

- Open the merge commit and the resolved file. Both sides' intended non-conflicting content should still be there.
- Ask why the rebased commit hashes changed. A correct "Git recomputed the snapshot/parent" answer is required; "because I rebased" is not.
- Confirm a reflog entry or backup branch/tag still points at the pre-rebase state.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations of what a given conflict marker or rebase step means are allowed. Resolving the conflict or performing the rebase for you is not — you need to be able to walk a mentor through exactly what you did and why the history looks the way it does afterward.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
