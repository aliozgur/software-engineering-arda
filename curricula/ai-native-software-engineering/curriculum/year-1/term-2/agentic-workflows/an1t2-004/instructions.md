# Diagnosing a Failed or Runaway Agentic Session

**Task ID:** `an1t2-004`  
**Estimated effort:** 9 hours  
**Module:** Agentic Workflows

## Why this task exists

Eventually, an agentic session goes off track: it edits a file it shouldn't have, invents an API that doesn't exist, or does far more than you asked. That's not a reason to avoid agentic sessions — it's a reason to practice recovering from one safely, so a drifted session costs you a rollback instead of a mess you have to untangle by hand. This task asks you to deliberately create the conditions for drift, rather than hoping you never encounter it.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence of the drift, the recovery, and a follow-up that actually stayed in scope.

## Authoritative resources

- **Best practices for agentic coding** (primary): https://code.claude.com/docs/en/best-practices

## Work to complete

1. Pick a task that is open-ended enough to invite drift — underspecified scope, a request phrased as a goal rather than a bounded change, or a codebase area the assistant hasn't seen before.
2. Give the assistant that open-ended prompt and let the session run longer than you would for a tightly-scoped task. Keep a log or transcript summary.
3. Identify specifically where it drifted: an unrelated file it touched, an API it assumed exists but doesn't, or work beyond what you asked for.
4. Using version control, isolate and revert or discard the unwanted portion of the change while keeping anything genuinely usable.
5. Write a narrower follow-up prompt that fixes the scope problem you identified, run it, and verify the result.

## Required evidence

- The original open-ended prompt and a log or transcript summary of what the session actually did
- A specific description of where the session drifted from the intended scope (an unrelated file edited, an invented API, or work beyond what was asked)
- Git history showing the unwanted portion of the change was isolated and reverted or discarded, while any usable part was kept
- The narrower follow-up prompt and evidence that it stayed in scope and passed verification
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references showing the drifted state, the revert/discard, and the follow-up.

## Acceptance criteria

- [ ] The drift description names a specific file, decision, or behavior that was outside the original intent, not a general complaint.
- [ ] Git history shows a revert, reset, or discard operation isolated to the unwanted portion, distinguishable from any kept work.
- [ ] The follow-up session's diff stays within the boundaries stated in its own narrower prompt.
- [ ] The follow-up change passes a verification step shown in the evidence.

The mentor may ask you to show exactly which commit or hunk you discarded and which you kept, and why that split was the right one.

## Reflection

Answer these in your own words after doing the work:

1. What in your original prompt made drift more likely, in hindsight?
2. What signal told you the session had drifted, and how long did it take you to notice?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask what would have happened if the apprentice had accepted the drifted change wholesale rather than isolating it.
- Verify the discarded portion is genuinely gone from the final state, not merely noted as "ignored."

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed because both the drifted session and the narrower follow-up are the intended path — the skill being assessed is diagnosing drift and recovering with version control, not avoiding AI. The apprentice must be able to explain exactly what drifted and why the recovery approach was correct. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
