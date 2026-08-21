# Respond to Review Feedback Like a Teammate

**Task ID:** `ef1t2-002`
**Estimated effort:** 5 hours
**Module:** Code Review

## Why this task matters

Receiving review is a different skill from giving it. The unprofessional patterns are easy to spot later: a force-push that rewrites history a reviewer already read, a silent extra commit with no reply, or a comment you disagreed with and simply ignored. This task asks you to treat review as a written conversation — reply to every comment, land what you accept as its own commit, and decline what you don't with a reason a teammate can live with.

## Authoritative resource

- **Pro Git** (reference): https://git-scm.com/book/en/v2

Use its branching and collaboration chapters when you need to reason about appending commits versus rewriting history. Prefer the book over blog posts about "squash and force-push everything."

## What you'll do

1. Start from a pull request you authored — reuse `ef1t1-002` / `ef1t1-006` if it is still open, or open a small new one. It needs incoming written review comments before you start responding.
2. If no reviewer is available (mentorship is optional), have a peer apply a written review using the same rules as `ef1t2-001`. If you are working alone, wait until the next day, review your own PR as if you were a teammate, write at least 5 comments into a `incoming-review.md` file, commit that file, and only then respond as the author. The comments must exist as a committed artifact before your first reply.
3. Reply to every incoming comment. Each reply is one of: you will change it (say what), you decline it (say why), or you need a clarification (ask a specific question).
4. Land at least two accepted changes as separate commits *after* the review comments exist. Name the comment in the commit message. Do not squash or force-push the commits the reviewer already saw.
5. Re-run at least one concrete verification command after the changes and record its output in the response note.
6. Write a single review-response note that maps every comment to a reply type and a commit SHA or a written decline.

## Evidence to submit

- A link to the pull request showing incoming comments and your replies, or the comment thread copied into a Markdown file if the host hid them.
- `git log` output from the reviewed branch showing commits appended after the first review comment, with messages that name the comment they address.
- A review-response note listing every incoming comment, your reply type (accepted, declined, or clarified), and a commit SHA or a written decline reason.
- An AI disclosure entry if AI helped draft any reply or change.

## Acceptance criteria

- [ ] Every incoming review comment has a written reply from you on the PR or in the submitted note.
- [ ] At least 2 accepted comments are landed as separate commits after the first review comment exists, and those commit messages name the comment they address.
- [ ] At least one comment is either declined in writing with a reason, or accepted with a named verification command that was re-run after the change.
- [ ] History after review started is append-only: the submitted `git log` or host UI shows no force-push that rewrote the already-reviewed commits.

Check your own submission against each line above before asking for review — a mentor will check the same four things.

## Reflection

Answer these in your own words after doing the work:

1. Which comment did you want to ignore, and what did you write instead?
2. If a teammate had already pulled your branch before you were tempted to rebase, what would a force-push have done to their copy?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you can respond to review without rewriting history?

## Mentor review guide

- Read the incoming comments first, then the replies. A missing reply is a revision, even if the code changed.
- Confirm at least two post-review commits exist and that their messages name a comment.
- Ask why they declined one comment, or how they re-verified an accepted one. "I just fixed it" is not enough.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI assistance for this task

Mode: **guided**. Explanations and hints about how to phrase a decline or how append-only history works are allowed. Generating your replies or the follow-up commits for you is not — you have to be able to defend every reply and every SHA in the response note. Disclose any AI use: what you asked, and what you verified yourself afterward.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and a mentor — or a documented self-check against every acceptance criterion, if you are working without one — confirms the demonstrated competency.
