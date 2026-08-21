# Close the Review Loop

**Task ID:** `os1t1-004`
**Estimated effort:** 8 hours
**Module:** Review Cycle

## Why this task exists

A pull request that never absorbs review is still a private patch with extra
ceremony. This task is the loop: someone else looks at the change, you answer every
item, and the history shows what you did after that look.

If a maintainer reviews your upstream or fork PR this week, use that thread. If
nobody reviews it in time, the fallback is still on the **same real PR**: write a
line-by-line self-review (at least four items), then ask a mentor or a peer who did
not author the patch to review that same public PR and record their items. Do not
invent a fake reviewer or a simulated community.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2 — *Distributed Git* and
  *Rewriting History*. Use them to decide whether you add commits or rebase, given
  what the project already asked for.
- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics — respect and
  honesty in every reply you put under your name.

## Work to complete

1. Stay on the pull request from `os1t1-003`. If that PR was closed without review,
   open a follow-up PR on the same public fork or upstream for the same issue and say
   so in the note. Do not switch to a toy repository.
2. Wait for, or request, review. If a maintainer comment exists, every comment is a
   row. If none exists by the time you must submit, write a self-review with at least
   four items (defect, convention, test gap, or scope), dated in the note, then obtain
   a second-person review of the same PR (mentor or peer). Record their handle or
   name and the date.
3. For each item, reply in complete sentences that name the file or line. Either
   push a follow-up commit and record its SHA, or write `no change` and a one-sentence
   reason. Do not reply with only "fixed" or only an emoji.
4. Prefer additional commits over a history rewrite when other people can already see
   the branch. If CONTRIBUTING requires squash-and-force-push, do that **after** the
   review table is complete, and keep the pre-squash SHAs in the note.
5. Leave the upstream issue URL in the PR description. If review changes the scope,
   add a sentence that says what is now out of scope and whether a follow-up issue
   exists (URL or `not filed`).

## Required evidence

- The pull-request URL from `os1t1-003` (upstream or public fork)
- Review thread URL(s), or a committed self-review dated in the note plus the
  second-person reviewer's name or handle and date
- A table with one row per review item: comment summary, reply, and either a
  follow-up commit SHA or the phrase `no change` plus a one-sentence reason
- Git log showing a commit timestamp after the first review comment or after the
  self-review date, unless every row is `no change`
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

## Acceptance criteria

- [ ] The table has one row for every review comment on the pull request, or — if no
      maintainer review exists — at least four self-review items plus every item the
      second-person reviewer raised.
- [ ] Each row contains a comment summary, a reply that names the file or line under
      discussion, and either a commit SHA or the exact phrase `no change` plus a
      one-sentence reason.
- [ ] At least one commit on the branch has an author date after the first review
      comment (or after the recorded self-review date), unless every row is marked
      `no change`.
- [ ] The pull-request description still contains the upstream issue URL from
      `os1t1-003`.
- [ ] Every reply is written as one or more complete sentences; no reply is only an
      emoji, only "fixed", or only a pasted patch with no explanation.

The mentor may pick one `no change` row and ask you to defend it from CONTRIBUTING or
from the issue's acceptance condition.

## Reflection

Answer these in your own words after doing the work:

1. Which review item changed the diff the most, and which SHA is the first commit
   that contains that change?
2. When would you choose rebase-and-force-push on this branch, and what would you
   lose that `git log` currently shows?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Walk the table against the PR thread. Count rows. Reject a submission whose only
follow-up is a force-push that erased the review trail with no pre-squash SHAs in
the note. If you were the second-person reviewer, say so in your review outcome.

If the apprentice has no mentor, the peer who performed the second-person review
must not be the only person who then "approves" the task; a third person or a
later self-check against the criteria should confirm the table is complete.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant write review replies you post
under your name. The apprentice must be able to defend every `no change` reason and
every follow-up hunk. Material AI assistance must be recorded in the submission
notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when you have "addressed comments." It is complete only
after the review table, the PR URL, and the follow-up history (or an all-`no change`
table) are submitted and approved against the acceptance criteria.
