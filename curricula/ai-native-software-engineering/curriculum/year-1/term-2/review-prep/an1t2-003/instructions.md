# Preparing a Design Review With AI Assistance

**Task ID:** `an1t2-003`  
**Estimated effort:** 7 hours  
**Module:** Review Prep

## Why this task exists

An AI assistant can draft a competent-looking design document in minutes. What it can't do is have actually weighed the trade-off for your specific system, or be the one accountable when a reviewer asks "why not the other approach?" This task practices using the draft as a starting point while making sure you — not the draft — are the one who can defend the decision in the room.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence that you found something in the AI draft worth correcting, not just polished its prose.

## Authoritative resources

- **Google engineering practices: code review** (primary): https://google.github.io/eng-practices/review/

While this guide is about code review, its standard for what counts as a substantive comment versus a stylistic one applies directly to design review as well.

## Work to complete

1. Pick a real design decision you need to make or defend — an architecture choice, a data model decision, an API shape — for a system you actually work on.
2. Ask an AI assistant to draft a design document (problem, options considered, recommendation, trade-offs). Keep this first draft unmodified and commit or date it before you revise anything.
3. Revise the document. Rewrite at least one trade-off section in your own words, naming a concrete alternative you considered and rejected, with a stated reason.
4. While revising, find at least one factual claim or option in the AI draft that was wrong or inapplicable to your specific system. Note what it was and how you found out.

## Required evidence

- The unmodified first AI-drafted section, committed or dated before the revised version exists
- The revised design document, with at least one trade-off section rewritten in your own words with a concrete alternative considered and rejected
- A note naming one factual claim or option in the AI draft that turned out to be wrong or inapplicable, and how you found that out
- Git history or dated files showing the draft saved before the revision, not a single combined dump
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit the unmodified draft and the revised document as separate files or a diff, plus your note.

## Acceptance criteria

- [ ] The unmodified AI draft is retained and distinguishable from the revised document.
- [ ] The AI draft is committed or dated before the revised document.
- [ ] The revised document states at least one alternative that was considered and rejected, with a stated reason.
- [ ] The note names a specific inaccurate or inapplicable claim from the AI draft, not a general disclaimer.
- [ ] The final document names the specific system or feature it concerns, not a generic template restated.

The mentor may run this as an actual design review conversation and ask you to defend the recommendation against the alternative you rejected.

## Reflection

Answer these in your own words after doing the work:

1. What did the AI draft get plausibly wrong about your specific system, and why did it make that mistake?
2. What in the final document is something only you could have written, not the AI?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask "why not X" about the rejected alternative and expect a substantive answer, not a restatement of the document.
- Check that the corrected claim is genuinely specific to this system, not a generic caveat that would apply to any design doc.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed because drafting the initial design document is the intended starting point — the skill being assessed is the revision and the defended trade-off, not writing the first draft from a blank page. The apprentice must be able to defend every claim and recommendation in the final version as their own. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
