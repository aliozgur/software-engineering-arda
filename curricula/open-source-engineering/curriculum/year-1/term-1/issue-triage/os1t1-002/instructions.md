# Triage a Real Public Issue

**Task ID:** `os1t1-002`
**Estimated effort:** 7 hours
**Module:** Issue Triage

## Why this task exists

Maintainers do not start from a patch. They start from a thread: is this real, is it
already filed, is it in scope, can someone else reproduce it? This task asks you to do
that work on **one real public issue**, and to leave a note that another person can
check against the thread.

Posting the comment upstream is welcome when it adds information the project asked
for. It is not required this week. A complete unposted comment is the fallback. What
is not allowed is inventing an issue, or triaging a ticket you created only to satisfy
this task.

## Authoritative resources

- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics — especially
  honesty about what you reproduced, and respect in any text that might be posted
  under your name.

Use the project's own issue template, CONTRIBUTING, and label set as the rest of the
primary source. Record any additional pages you used.

## Work to complete

1. Pick one **open** public issue on the project from `os1t1-001`. If you must switch
   projects, write a short contribution-surface addendum (URL, SPDX, CONTRIBUTING
   path-or-absent) in the same note before you triage. Do not file a new issue solely
   so you have something to triage.
2. Read the entire thread, including closed duplicates linked from it. List every
   environment fact the reporter already gave (version, OS, steps, expected vs actual).
3. Attempt reproduction on the commit or release the issue names, or on current
   default-branch HEAD if no version is named. Number the steps you actually ran.
   End with exactly one result line:
   - `reproduced`
   - `not-reproduced`
   - `blocked-with-reason`
4. Choose **one** recommended next action and use it as a heading:
   - `close-as-duplicate` — include the other issue URL
   - `ask-for-info` — list the missing facts as a checklist
   - `accept-as-bug` — one sentence on user-visible impact
   - `reject-as-wontfix` — quote the policy sentence
   - `ready-for-PR` — one sentence on the smallest change that would address it
5. Propose at least one label from the project's existing labels. If the project has
   no labels, say so and name one label it would need.
6. Write the comment you would post (reproduction result, environment, next action).
   Post it only if it adds a fact the thread lacks and you are willing to own the
   follow-up. Otherwise mark the comment `UNPOSTED`.

## Required evidence

- The public upstream issue URL that was triaged
- A committed triage note with numbered reproduction steps, an explicit result
  (`reproduced` / `not-reproduced` / `blocked-with-reason`), proposed label(s), and a
  single recommended-next-action heading
- Captured command output or a log excerpt from the reproduction attempt, stored as a
  file, not only a screenshot
- Either the public comment URL if a triage comment was posted, or the exact comment
  text marked `UNPOSTED`
- Reflection notes answering the questions below
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus an immutable commit reference for the note and the
captured output.

## Acceptance criteria

- [ ] The issue URL is a public issue on a real repository (the project from
      `os1t1-001`, or a newly mapped public project named in the note).
- [ ] The triage note contains numbered reproduction steps and exactly one result line
      that is `reproduced`, `not-reproduced`, or `blocked-with-reason`.
- [ ] The note proposes at least one label that already exists on the project, or
      states that the project has no labels and names one label the project would need.
- [ ] The note has a single heading whose text is one of: `close-as-duplicate`,
      `ask-for-info`, `accept-as-bug`, `reject-as-wontfix`, `ready-for-PR`.
- [ ] If the heading is `close-as-duplicate`, the note includes the duplicate issue
      URL; if `reject-as-wontfix`, the note quotes a sentence from CONTRIBUTING or
      project policy.

The mentor may ask you to change the next-action heading live and justify the new
choice from the same thread.

## Reflection

Answer these in your own words after doing the work:

1. What fact was missing from the original report that most delayed your result line?
2. If a maintainer discarded your next-action heading, which heading would you argue
   for instead, and which sentence in the thread supports that?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

Open the issue URL. Confirm the result line is possible from the captured output. Do
not approve a note that restates the issue title without numbered steps. If a comment
was posted, read it for tone: no sarcasm, no diagnosis the apprentice did not run.

If the apprentice has no mentor this term, a peer who did not write the note can apply
the same checks.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is not the
intended path for this task. Do not let an assistant author a comment you then post
under your name. The apprentice must be able to defend every reproduction step and
the next-action heading. Material AI assistance must be recorded in the submission
notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

This task is not complete when you have read the issue. It is complete only after the
triage note, the captured reproduction attempt, and the posted or `UNPOSTED` comment
are submitted and approved against the acceptance criteria.
