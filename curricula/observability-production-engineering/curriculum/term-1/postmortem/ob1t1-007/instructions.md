# A Blameless Postmortem You Would Not Be Ashamed to Share

**Task ID:** `ob1t1-007`
**Estimated effort:** 8 hours
**Module:** Postmortem

## Why this task exists

`ob1t1-006` produced a timeline and a restore. This task is the learning half of
incident work: write it so another apprentice could act, and so nobody has to defend
themselves as a person. Blame is easy to slip into ("I should have checked X"). The
craft is naming the condition that made X easy to miss.

You will also write a deliberately blameful paragraph and then rewrite it. The pair is
evidence that you can see the difference, not that you believe the blameful version.

## Authoritative resources

- **Site Reliability Engineering (Google SRE Book)** (primary):
  https://sre.google/sre-book/postmortem-culture/ — Chapter 15, Postmortem Culture:
  Learning from Failure.
  Use Appendix D as a shape, not as text to copy:
  https://sre.google/sre-book/example-postmortem/

## Work to complete

1. Write a postmortem of the `ob1t1-006` incident (if that incident was too thin, you
   may re-run one injector mode and use the new timeline — say so). Required sections:
   - Summary (what the user saw, in two or three sentences).
   - Impact: a user-visible effect **and** a duration or a request-count (for example
     "checkout POST p99 above 2s for 14 minutes" or "23 of 80 sampled requests returned
     503"). An internal exception name alone is not impact.
   - Timeline, adapted from `ob1t1-006`, still distinguishing fact from later analysis.
   - Contributing factors — at least two. Factors are system conditions (missing alert,
     no timeout, runbook gap, a deploy without a canary). They are not people.
   - What went well, what went poorly.
   - Follow-ups (step 3).
2. Write a **blameful draft paragraph** (four to eight sentences) that explains the
   same incident by naming a person or a personal failing. Then rewrite it so every
   clause names a system condition, a missing signal, or a missing guard. Keep both
   paragraphs in the submission, labeled `blameful-draft` and `rewrite`.
3. List follow-up actions in a table with columns: action, label
   (`detection` / `prevention` / `response`), owner **role** (not a personal name),
   and a one-line **done-when** criterion. You need at least one of each label.
   Example done-when: "Paging rule `SLOBudgetBurn` has a `promtool` unit test that
   fails if the healthy fixture fires."
4. Mark one follow-up as something you can implement in `ob1t1-008` (or this same
   week). If none of them fit, add a fourth follow-up that does.

Do not invent a more dramatic outage than you ran. Inflated impact is a form of
fiction; a mentor can compare it to the `ob1t1-006` captures.

## Required evidence

- A postmortem document covering summary, user-visible impact, timeline, contributing
  factors, what went well, what went poorly, and follow-ups
- A blameful-paragraph draft and its rewrite in the same submission
- A follow-up table with at least one action labeled detection, one labeled
  prevention, and one labeled response, each with a done-when line
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Markdown in-repo is the expected
artifact.

## Acceptance criteria

- [ ] The postmortem names at least two contributing factors, none of which is a
      person's name or a personal attribute (careless, lazy, should have known).
- [ ] Follow-up actions include at least one labeled detection, one labeled
      prevention, and one labeled response, each with a one-line done-when criterion.
- [ ] A blameful paragraph and its rewrite both appear; the rewrite contains no
      personal name and no "should have known" phrasing.
- [ ] The impact section states a user-visible effect and a duration or request-count,
      not only an internal error name.

The mentor may highlight any sentence that still smuggles blame ("obviously", "simply
forgot") and ask for a rewrite. If you are working without a mentor, search your own
document for those words and for every personal pronoun used as a cause; fix them
before submitting.

## Reflection

Answer these in your own words after doing the work:

1. Which contributing factor, if it had been absent, would have made this incident
   shorter — detection, prevention, or response — and what in the timeline supports
   that?
2. Quote one sentence from your rewrite that was hardest to de-personalize. What
   system noun replaced the person?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: read the blameful draft only to
confirm the rewrite actually changed the causal language. Do not approve a follow-up
list that is only "be more careful" or "add more metrics" with no done-when.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain blameless language and quiz you on contributing-factor versus root-cause
theater. AI must not write the postmortem or the rewrite for you. If you use a linter
or a model to flag blame words, disclose that and still own the final sentences.
Disclose material AI use: provider or model if known, purpose, and verification
performed.

## Completion gate

This task is not complete when the document has the right headings. It is complete
once impact is quantified, factors are systems, follow-ups are labeled with
done-when, and the rewrite would be safe to read aloud in a review.
