# AI System Card and Evaluation Harness

**Task ID:** `da2t1-005`  
**Estimated effort:** 12 hours  
**Module:** ai-systems

## Why this task exists

Close the first AI term by describing the system as a reviewer would: purpose, data, eval, failure modes, and human oversight.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Datasheets for Datasets**: https://arxiv.org/abs/1803.09010
- **ACM Code of Ethics**: https://www.acm.org/code-of-ethics

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Write a system card for the retrieval or LLM task you built.
2. Package a small eval harness that can be rerun (script + cases + scores).
3. List misuse, over-trust, and a kill switch or refusal policy.
4. Present to the mentor as if they were a risk reviewer, not a demo audience.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] The card states who should not use the system.
- [ ] Eval numbers come from the harness, not from memory.
- [ ] Oversight is operational (who looks, how often), not a slogan.
- [ ] The apprentice can name the worst failure they actually saw.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What would you measure next if this shipped to ten users?
2. Which stakeholder is missing from the card?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Play a hostile user. Ask for the refusal.
- Do not approve a card that only lists benefits.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
