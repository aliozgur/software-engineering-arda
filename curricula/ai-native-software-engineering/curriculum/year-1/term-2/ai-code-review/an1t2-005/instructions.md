# Reviewing Someone Else's Work as an AI-Assisted Reviewer

**Task ID:** `an1t2-005`  
**Estimated effort:** 7 hours  
**Module:** AI Code Review

## Why this task exists

an1t1-002 practiced reviewing AI-generated code as its author. This task flips the seat: you're the reviewer of someone else's real change, and you're allowed to use AI to draft your review comments. The risk here is different — a reviewer who just forwards the AI's comments isn't reviewing at all, they're relaying. The evidence this task asks for is specifically what you added that the draft didn't have.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires a real diff and a comment the AI draft didn't produce.

## Authoritative resources

- **Google engineering practices: code review** (primary): https://google.github.io/eng-practices/review/

## Work to complete

1. Find a real change set to review — a pull request in an open-source project you contribute to, a colleague's change (with their consent), or a mentor-supplied diff from a real codebase. It must have genuine context, not a synthetic snippet built for this exercise.
2. Ask an AI assistant to draft review comments on the diff. Save that unedited draft as a commit or dated file before you write the final review.
3. Do your own review. Decide, for each AI-drafted comment, whether to keep it, edit it, or drop it — and why.
4. Find and add at least one substantive comment (correctness, security, or missing test coverage) that the AI draft did not raise.
5. Deliver the final review (post it, or write it up as if posting).

## Required evidence

- The AI-drafted review comments, saved as a commit or dated file before the final review was written
- The final review actually posted or delivered, showing which AI-drafted comments were kept, dropped, or edited and why
- At least one substantive review comment (correctness, security, or missing test coverage, not style) absent from the AI draft, with the reasoning behind it
- A note on one AI-drafted comment that was dropped because it was wrong, irrelevant, or already addressed
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit the unedited AI draft, the final review, and a link or reference to the real change set reviewed.

## Acceptance criteria

- [ ] The unedited AI-drafted comments are retained separately from the final review, and are dated or committed before it.
- [ ] At least one substantive comment in the final review has no equivalent in the AI draft.
- [ ] At least one AI-drafted comment is explicitly marked dropped, with a stated reason.
- [ ] The reviewed change set is a real diff from an actual project, not a synthetic snippet with no real context.

The mentor may ask you to justify the comment the AI draft missed: what about the diff's actual context made it visible to you and not to the AI?

## Reflection

Answer these in your own words after doing the work:

1. What kind of issue did the AI draft consistently miss or get wrong?
2. What made the AI-drafted comments useful anyway, even with that gap?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to defend the dropped AI comment: was it actually wrong, or just uncomfortable to raise?
- Verify the added substantive comment is genuinely absent from the AI draft, not a rephrasing of something already there.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes to help draft and refine review comments. Solution generation is not the intended path for this task — the skill being assessed is your judgment as a reviewer, not generating a fix for the change set. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
