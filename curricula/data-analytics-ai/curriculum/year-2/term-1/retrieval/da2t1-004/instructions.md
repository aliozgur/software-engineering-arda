# Retrieval-Grounded Answers

**Task ID:** `da2t1-004`  
**Estimated effort:** 12 hours  
**Module:** retrieval

## Why this task exists

Grounding is a data problem: chunking, retrieval, citations, and refusal when the store has no answer.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Hugging Face NLP Course**: https://huggingface.co/learn/nlp-course/
- **OpenAI prompting guidance**: https://platform.openai.com/docs/guides/prompt-engineering

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Index a small corpus you own or that is licensed (docs from this repo, or a public domain set).
2. Implement retrieval (even BM25 or TF-IDF is enough) and generate an answer only from retrieved passages.
3. Show a correct citation, a missed retrieval, and a forced refusal.
4. Measure hit rate on a 10-question eval set you wrote first.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Answers that are not in the store must refuse.
- [ ] Citations point at retrieved text, not the model's memory.
- [ ] The eval set was written before tuning.
- [ ] Chunk size is justified in a short note.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What query would retrieve the wrong neighbor?
2. How is this different from 'search then read' without a generator?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask a question whose answer is adjacent but not present.
- Reject uncited fluent paragraphs.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
