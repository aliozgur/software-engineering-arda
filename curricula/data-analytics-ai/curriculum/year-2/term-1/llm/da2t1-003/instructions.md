# LLM Workflows With Evaluation, Not Vibes

**Task ID:** `da2t1-003`  
**Estimated effort:** 12 hours  
**Module:** llm

## Why this task exists

An LLM is a component. Treat prompts as code: version them, hold out cases, and measure something besides 'it looked good'.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **OpenAI prompting guidance**: https://platform.openai.com/docs/guides/prompt-engineering
- **Anthropic prompt engineering**: https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Pick a narrow task (classify, extract, or rewrite) with 20+ labeled examples.
2. Write two prompts. Score both on a held-out set with a written rubric or exact-match rule.
3. Log model, date, prompt hash, and failures.
4. Disclose every generation. Do not hide edits you made after the model.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] The metric is defined before looking at the second prompt's score.
- [ ] Failures are shown, not only wins.
- [ ] A no-LLM baseline exists (keyword rule or smaller classifier).
- [ ] Cost/latency is mentioned even if only as an order of magnitude.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What did the metric miss that a mentor would still reject?
2. When must a human stay in the loop?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask to add an adversarial example and rerun.
- Reject a chat log with no held-out set.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
