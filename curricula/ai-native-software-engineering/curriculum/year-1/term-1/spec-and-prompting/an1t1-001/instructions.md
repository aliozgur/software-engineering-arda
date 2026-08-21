# Writing a Spec Precise Enough to Implement With AI

**Task ID:** `an1t1-001`  
**Estimated effort:** 6 hours  
**Module:** Spec and Prompting

## Why this task exists

An AI assistant will happily generate code from a one-line request. What comes back will look plausible and will usually be wrong in some way that a vague request could never have caught. Treating the spec you hand the assistant as a real engineering artifact — versioned, specific, checkable — is the first habit this curriculum builds, because every later task assumes you can do this.

This is an apprenticeship task, not a content-consumption checkbox. Reading the linked material is only preparation. Completion requires evidence that you wrote a spec, used it, and can show the gap between what you asked for and what you got.

## Authoritative resources

- **Anthropic prompt engineering** (primary): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview
- **OpenAI prompting guidance** (reference): https://platform.openai.com/docs/guides/prompt-engineering

Use these as your primary sources for how to write instructions an AI assistant can act on precisely. You may use other sources, but record them in your notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Pick a small, real feature or fix — something you'd actually want in a project you maintain, not a toy exercise invented for this task.
2. Write `SPEC.md` before requesting any AI-generated code. Name the files or interfaces involved, state at least one thing explicitly out of scope, and state a concrete verification step (a command or test that will tell you the feature works).
3. Commit the spec on its own.
4. Give the spec to an AI assistant and request an implementation. Save the exact prompt text you used.
5. Review what comes back against your spec. Make the corrections it actually needs — do not silently accept output that drifts from the spec, and do not silently accept output that's wrong just because it runs.
6. Write a short correction note: what you changed in the AI's output, and why each change was necessary.

## Required evidence

- `SPEC.md`, committed before any AI-generated implementation code exists
- Git history showing at least two incremental commits: the spec commit, then one or more implementation commits after it
- The saved prompt or transcript showing the exact spec text given to the assistant
- A correction note listing specific changes made to the AI-generated output and why each was needed
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus a commit or tag reference. Do not submit only a description of what you did — the commits themselves are the evidence.

## Acceptance criteria

- [ ] `SPEC.md` exists as a commit that predates the first commit containing AI-generated implementation code.
- [ ] The spec names the files or interfaces involved, states at least one explicit out-of-scope item, and states a concrete verification step.
- [ ] The correction note lists at least one specific change made to the AI-generated code, not a general approval.
- [ ] The AI disclosure entry names the tool/model used and what was independently verified.

The mentor may ask you to walk through the diff between what your spec asked for and what the AI produced. Passing tests alone does not prove you wrote a spec that mattered.

## Reflection

Answer these in your own words after doing the work:

1. What part of your spec turned out to be ambiguous even though it felt precise when you wrote it?
2. What would you have missed if you'd reviewed the AI's output without the spec in front of you?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at the exact spec sentence that each correction traces back to.
- Reject a submission where the spec was written or edited after the implementation — that defeats the point.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed for this task because generating the implementation *from your spec* is the intended path — the skill being assessed is the spec and the corrections, not writing the first draft by hand. The apprentice must still be able to explain, modify, test, and defend every submitted artifact. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
