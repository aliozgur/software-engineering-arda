# Knowing When Not to Reach for AI

**Task ID:** `an1t1-006`  
**Estimated effort:** 10 hours  
**Module:** Judgment

## Why this task exists

Everything else in this term has practiced using AI well: precise specs, critical review, independent verification, scoped agentic sessions. This task is the other half of the same skill — recognizing a piece of work where the risk of an unverified or premature AI suggestion outweighs the speed gain, and deliberately not reaching for it. That judgment call, made explicitly and defended, is the term's milestone.

This is an apprenticeship task, not a content-consumption checkbox. You must find a real situation, not construct an artificial one to satisfy the rubric.

## Authoritative resources

- **ACM Code of Ethics** (primary): https://www.acm.org/code-of-ethics
- **OWASP Top 10** (reference): https://owasp.org/www-project-top-ten/

Use these to ground your reasoning about accountability and security-sensitive risk. You may use other sources, but record them in your notes.

## Work to complete

1. Identify a real, upcoming piece of work in a project you're actually working on — not a hypothetical — that falls into one of: an irreversible operation (data migration, destructive script, a production config change with no easy rollback), security-sensitive code (authentication, authorization, secrets handling, cryptography), or a requirement that is still genuinely unclear (you'd be guessing, not implementing).
2. Before starting the work, write a decision memo: name the specific risk, and explain why it justifies not using AI-generated implementation code for this piece. Commit the memo on its own.
3. Do the work without AI-generated implementation code. You may still use AI for explanation or to talk through a checklist — note that separately and be explicit that it's distinct from the withheld part.
4. Once done, write a reflection on what would have had to be true for the decision to go the other way — a concrete condition, not a hedge like "if I had more time."

## Required evidence

- A decision memo, written and committed before starting the work, naming the specific risk and why it justified not using AI generation for this piece
- Git history or a work log showing incremental progress on the withheld work without AI-generated implementation code
- A note on where AI was still used for the task, if at all, distinguished clearly from what was deliberately withheld
- A reflection on what would have had to be true for the decision to go the other way

Submit a repository URL or work log reference plus the decision memo and reflection as committed files or notes.

## Acceptance criteria

- [ ] The decision memo is committed before the implementation work it concerns.
- [ ] The named risk is one of: an irreversible operation, security-sensitive code, or an explicitly unclear requirement, and the memo explains which and why.
- [ ] No AI-generated implementation code appears in the submitted work for the withheld part, per the disclosure entry.
- [ ] The reflection names a concrete condition, not a vague hedge, under which the decision would have been different.

The mentor may ask you to defend the decision against a counterargument: "an AI assistant could have caught this faster." A memo that would apply to any task with equal force, rather than this specific one, does not meet the bar.

## Reflection

Answer these in your own words after doing the work:

1. What made this particular piece of work risky enough to warrant withholding AI generation?
2. Where was the line, for you, between "AI could help here" and "AI should not touch this"?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Push on whether the risk named is real for this specific piece of work, or a generic justification that could be copy-pasted onto any task.
- Ask what evidence would have changed the apprentice's mind mid-task.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes about the surrounding material. Solution generation is not the intended path for this task — withholding generated implementation code is the judgment being assessed. Any AI use that still happens (for example, talking through a checklist) must be disclosed with the provider/model (if known), purpose, and what was independently verified, and must be distinguished from the withheld part.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
