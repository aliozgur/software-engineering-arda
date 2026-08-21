# Ship a Maintainer Packet for a Real Project

**Task ID:** `os1t1-007`
**Estimated effort:** 9 hours
**Module:** Maintainership

## Why this task exists

The earlier tasks isolated one skill at a time: map, triage, contribute, respond,
review, license and version. A maintainer does those in the same week, on the same
project, and then writes down what a release may promise. This task is that week, as
a packet a mentor can open.

Use the **same real public project** as `os1t1-001` unless it is abandoned — if you
switch, the note must say why and include the new URL and SPDX identifier. Do **not**
create a new repository, fake issues, or simulated contributors for this task. If you
cannot post triage comments, reviews, or a release this week, write complete
`UNPOSTED` drafts that still cite real public URLs. LEARN BY DOING. GROW THROUGH
MENTORSHIP — the doing here is judgment on a live project, not a stage set.

## Authoritative resources

- **Semantic Versioning 2.0.0** (primary): https://semver.org/
- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics
- **Pro Git** (reference): https://git-scm.com/book/en/v2 — use it to name commits
  and tags (`git log`, `git show`, `git tag`) rather than only the host's Releases
  UI.

## Work to complete

1. Freeze the project URL at the top of the packet. Confirm it is the public
   repository from `os1t1-001` or document the switch.
2. **Triage.** Pick at least three distinct public issues (open or recently closed).
   You may reuse `os1t1-002` as one row. For each row write exactly one heading from
   `close-as-duplicate`, `ask-for-info`, `accept-as-bug`, `reject-as-wontfix`,
   `ready-for-PR`. Apply the same citation rules as `os1t1-002` (duplicate URL;
   policy quote for wontfix).
3. **Review.** Review at least one public pull request on that repository. You may
   reuse the PR from `os1t1-005` if it is on this project; otherwise choose another.
   Name at least two file paths from the diff. Post if you can own follow-up;
   otherwise mark the body `UNPOSTED`.
4. **Release notes.** Draft notes for the **next** version that would include a real
   set of already-merged or already-opened changes. Start with `X.Y.Z` and a bump
   type (`major` / `minor` / `patch`) justified by SemVer 2.0.0 against the public
   API you named in `os1t1-006`. List at least three changes, each paired with a
   commit SHA or pull-request URL **from that repository**. Do not invent changelog
   lines.
5. **Support boundary.** Write `will-respond` (at least two items) and
   `will-not-respond` (at least two items): issue types, response time you would
   actually keep, and work you would decline. Keep it small enough that you could
   honor it for a month.

If you are a maintainer with publish rights, you may post the notes or cut the tag.
That is welcome, not required. An `UNPOSTED` draft with real SHAs meets the task.

## Required evidence

- The public project URL used for the packet (the project from `os1t1-001` unless
  the note records why it was abandoned)
- A triage table of at least three distinct public issue URLs, each with a
  recommended-next-action heading from the `os1t1-002` closed set
- A review of at least one public pull-request URL naming at least two file paths
  from that diff (posted review URL or `UNPOSTED` body)
- A release-notes draft that starts with version `X.Y.Z` and a SemVer bump type,
  and lists at least three changes each with a commit SHA or pull-request URL from
  that repository
- A support-boundary note with a `will-respond` list and a `will-not-respond` list,
  each with at least two items
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

## Acceptance criteria

- [ ] Every URL in the packet is a real public issue, pull request, commit, or
      repository page; the note contains no invented contributor, issue, or
      community.
- [ ] The triage table has at least three distinct public issue URLs, each with
      exactly one recommended action from: `close-as-duplicate`, `ask-for-info`,
      `accept-as-bug`, `reject-as-wontfix`, `ready-for-PR`.
- [ ] The pull-request review names the pull-request URL and at least two file paths
      that appear in that diff.
- [ ] The release-notes draft starts with a version string of the form `X.Y.Z` and a
      bump type of `major`, `minor`, or `patch`, and lists at least three changes
      each paired with a commit SHA or pull-request URL from that repository.
- [ ] The support-boundary note contains a `will-respond` list and a
      `will-not-respond` list, each with at least two items.

The mentor may pick one release-notes line and ask you to show the SHA or PR in the
repository, then ask whether that line alone would have forced a different bump.

## Reflection

Answer these in your own words after doing the work:

1. Which of the three jobs — triage, review, release notes — would slip first if you
   had half the hours, and what in the packet would a newcomer lose?
2. What is one request in `will-not-respond` that a user might still think is
   reasonable, and how would you point them at a documented boundary?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open every URL. Reject any packet that creates a toy project, files issues against
itself for volume, or lists changelog items that are not in the named repository.
Ask the apprentice to defend the bump type from SemVer 2.0.0 using only the three
listed changes.

If the apprentice has no mentor this term, a peer who did not write the packet can
apply the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant invent issues, reviews, or
changelog lines. The apprentice must be able to open every URL and defend every
heading. Material AI assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when the packet looks like a changelog. It is complete
only after the real URLs, the triage table, the review, the versioned notes, and
the support boundary are submitted and approved against the acceptance criteria.
LEARN BY DOING. GROW THROUGH MENTORSHIP.
