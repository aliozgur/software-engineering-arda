# Critical Review of AI-Generated Code

**Task ID:** `an1t1-002`  
**Estimated effort:** 7 hours  
**Module:** AI Code Review

## Why this task exists

An AI-generated draft that compiles and runs is not the same thing as an AI-generated draft that's correct, secure, or maintainable. Rubber-stamping is the failure mode this whole curriculum is built against — this task makes you practice the opposite: treating a generated draft as a first pass that you're accountable for reviewing, not a finished answer.

This is an apprenticeship task, not a content-consumption checkbox. Reading the linked material is only preparation. Completion requires evidence that your review found something real.

## Authoritative resources

- **Google engineering practices: code review** (primary): https://google.github.io/eng-practices/review/

Use this as your primary source for what a substantive review actually looks for, beyond style. You may use other sources, but record them in your notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Pick a small function or module (20-100 lines is plenty) and generate an implementation with AI assistance.
2. Commit the unmodified AI draft on its own, before you touch it.
3. Review the draft the way the linked guide describes: correctness first, then security, then readability and maintainability. Write down every issue you find, categorized.
4. Fix at least one correctness or security issue in a follow-up commit that references your review note.
5. Note one AI suggestion — a comment, a variable name, a whole approach — that you deliberately did not adopt, and why.

## Required evidence

- The unmodified AI-generated first draft, kept separate from your edits (a distinct commit or attached diff)
- A written review note listing each issue found, categorized as correctness, security, readability, or maintainability
- A follow-up commit fixing at least one correctness or security issue found in review, referencing the review note
- A note naming one AI suggestion you rejected and the concrete reason it was not adopted
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references for the draft, the review note, and the fix.

## Acceptance criteria

- [ ] The unmodified AI draft is present in git history or an attached diff, separate from the corrected version.
- [ ] The review note identifies at least three distinct issues, at least one of which is correctness or security, not only style.
- [ ] At least one identified issue is fixed in a commit that references the review note.
- [ ] The rejected-suggestion note names the specific suggestion and the concrete reason it was not adopted.

The mentor may ask you to defend why an issue you flagged actually matters, or point to one you missed. Finding zero real issues in an AI draft is itself worth questioning.

## Reflection

Answer these in your own words after doing the work:

1. What kind of issue was hardest to spot in the AI draft, and why?
2. If you had only skimmed the draft instead of reviewing it structurally, what would you have missed?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask what the apprentice would have shipped if this had been a real deadline and they hadn't done the structured review.
- Challenge any "clean code" claim that isn't backed by a specific example in the review note.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed for this task because generating the first draft under review is the intended path — the skill being assessed is the review and the rejected suggestion, not writing the draft by hand. The apprentice must be able to explain, modify, test, and defend every submitted artifact, including exactly what the review changed. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
