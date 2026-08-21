# Capstone: Disclosed AI-Assisted Feature Delivery End-to-End

**Task ID:** `an1t2-006`  
**Estimated effort:** 14 hours  
**Module:** Capstone

## Why this task exists

Every earlier task in this curriculum isolated one discipline: writing a spec, reviewing AI output critically, verifying independently, scoping and recovering agentic sessions, refactoring, preparing a review, knowing when to withhold AI entirely. Real feature work needs all of them at once, on a piece of work that's genuinely ambiguous rather than pre-cleared for you. This capstone is where that has to hold together.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires the full disclosed trail — spec through refactor — not a single polished final diff.

## Authoritative resources

- **Best practices for agentic coding** (primary): https://code.claude.com/docs/en/best-practices
- **Google engineering practices: code review** (reference): https://google.github.io/eng-practices/review/

## Work to complete

1. Choose one real, moderately ambiguous feature — something where at least one requirement genuinely needs your own interpretation, not just AI's.
2. Write a spec before any implementation, explicitly noting the requirement(s) you had to clarify or interpret yourself.
3. Implement it with AI assistance, including at least one agentic step that changes multiple files together.
4. Verify the result with a test suite written before or independent of the AI-generated implementation.
5. Critically review the AI-generated output: find and fix at least one real issue distinct from what the spec already asked for.
6. Refactor anything that needs it for maintainability, under test.
7. Keep a disclosure log covering every material AI use across the whole task: tool/model, purpose, and what you independently verified.

## Required evidence

- A spec written before implementation, including at least one requirement you had to clarify or interpret yourself because it was originally ambiguous
- Git history showing spec, tests, agentic implementation step(s), review notes, and refactor as separable, ordered commits
- A test suite written before or independent of the AI-generated implementation, shown passing on the final code
- A critical review note listing issues found in the AI-generated output and which were fixed
- A disclosure log covering every material AI use across the whole task: tool/model, purpose, and what was independently verified

Submit a repository URL plus commit references spanning the whole sequence, and the disclosure log as a committed file.

## Acceptance criteria

- [ ] Git history shows the spec commit precedes the implementation commits.
- [ ] At least one implementation step is an agentic, multi-file change, identifiable in the evidence.
- [ ] The independent test suite passes against the final submitted code, shown in a test run log.
- [ ] The critical review note lists at least one issue that was found and fixed, distinct from the original spec's requirements.
- [ ] The disclosure log accounts for every commit that contains AI-generated content.

The mentor may request a live walkthrough of the whole sequence — spec, agentic diff, verification, review, refactor — and ask you to defend any single step in isolation.

## Reflection

Answer these in your own words after doing the work:

1. Which discipline from earlier in the curriculum did you almost skip under time pressure, and what made you keep it?
2. What part of the requirement did you have to interpret yourself, and how did you decide?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Treat this as a real feature review: ask about the ambiguous requirement first, then the trail of evidence.
- Reject a submission where any single stage (spec, verification, review, refactor) is missing from the evidence, even if the final code looks fine.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed across the implementation stages of this task because delivering a real feature with disclosed AI assistance is the intended path — the skill being assessed is the full trail (spec, verification, review, refactor, disclosure), not writing every line by hand. The apprentice must be able to explain, modify, test, and defend every submitted artifact, including the agentic step. Material AI assistance must be recorded in the disclosure log with the provider/model (if known), purpose, and verification performed for each stage.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
