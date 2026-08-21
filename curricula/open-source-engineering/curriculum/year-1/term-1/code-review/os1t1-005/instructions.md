# Review a Pull Request You Did Not Author

**Task ID:** `os1t1-005`
**Estimated effort:** 7 hours
**Module:** Code Review

## Why this task exists

You have opened and defended your own change. Maintainers spend most of their time on
**other people's** diffs. This task asks you to review one real public pull request
you did not write, with findings a mentor can open on that same URL.

Posting the review is a real contribution when it is factual, scoped, and something
you will answer if the author replies. If you should not post this week (the thread
is already noisy, you cannot own follow-up, the project asks contributors not to
drive-by review), the fallback is a complete `UNPOSTED` review that still quotes
`path:line` locations from that public diff. Do not review a pull request you created
only for this task, and do not invent a simulated author.

## Authoritative resources

- **Pro Git** (reference): https://git-scm.com/book/en/v2 — use it to read the
  incoming commits (`git fetch`, `git log`, `git show`) rather than only the host's
  Files tab.
- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics — respect and
  honesty: do not praise what you did not read, and do not attribute motive.

Prefer a pull request on the project from `os1t1-001`. A different public project is
allowed if you record its URL and SPDX identifier in the note.

## Work to complete

1. Choose one **open** public pull request whose author login is not yours. Record
   both logins. Fetch the head branch if you can clone; otherwise work from the
   host diff and record that you could not fetch.
2. Read the linked issue (if any), CONTRIBUTING, and the full diff. List every
   top-level path. Run the project's documented test or lint command on that branch
   if you can clone it; if you cannot, write the blocker and review from the diff
   alone.
3. Write at least three findings that name **distinct file paths** from the diff.
   Label each finding exactly one of: `defect`, `convention`, `question`, `praise`.
   At least one finding must not be `praise`.
4. Choose exactly one summary state: `approve`, `request-changes`, or `comment`.
   One sentence must say why that state, not another.
5. Post the review if you can own a reply this week and the comment adds a fact or
   a precise question. Otherwise mark the entire review body `UNPOSTED`. Do not
   paste a generic "LGTM" with no file names.

## Required evidence

- The public pull-request URL reviewed, whose author login is not the apprentice's
  login
- The posted review URL, or the full review markdown marked `UNPOSTED`
- A findings list in which each item is labeled `defect`, `convention`, `question`,
  or `praise`, naming a file path from the diff
- A one-line summary state that is exactly `approve`, `request-changes`, or
  `comment`
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

## Acceptance criteria

- [ ] The reviewed pull-request URL is public and the pull-request author login is
      different from the apprentice's login, both recorded in the note.
- [ ] The review names at least three distinct file paths that appear in that pull
      request's diff.
- [ ] Each finding is labeled exactly one of `defect`, `convention`, `question`, or
      `praise`, and at least one finding is not `praise`.
- [ ] The summary state is exactly one of: `approve`, `request-changes`, `comment`.
- [ ] If the review was posted, the note includes the public review URL; if not, the
      review body is marked `UNPOSTED` and still quotes at least three `path:line`
      locations from the diff.

The mentor may hide your summary state and ask you to re-derive it from the findings
list alone.

## Reflection

Answer these in your own words after doing the work:

1. Which finding would you drop first if the author asked for a smaller review, and
   why that one?
2. What did you fetch or show with Git that the Files tab did not make obvious (or
   what did you fail to fetch, and what did that hide)?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open the PR URL and confirm the three paths exist in the diff. Reject a review that
only restates the PR title, or a review of the apprentice's own PR. Check tone: no
sarcasm, no capability insults, no undisclosed generated dump.

If the apprentice has no mentor this term, a peer who is not the PR author can apply
the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant write findings you post under
your name. The apprentice must be able to open each `path:line` and defend the
label. Material AI assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when you have "looked at a PR." It is complete only after
the public PR URL, the labeled findings, and the posted or `UNPOSTED` review are
submitted and approved against the acceptance criteria.
