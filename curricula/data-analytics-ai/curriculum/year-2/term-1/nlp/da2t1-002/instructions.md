# Text as Data and Embeddings Intuition

**Task ID:** `da2t1-002`  
**Estimated effort:** 10 hours  
**Module:** nlp

## Why this task exists

Before prompting an API, represent text with bags-of-words or embeddings and show that 'similar' is a choice.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Hugging Face NLP Course**: https://huggingface.co/learn/nlp-course/
- **scikit-learn Text feature extraction**: https://scikit-learn.org/stable/modules/feature_extraction.html#text-feature-extraction

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Build a tiny labeled text set (or a public one) and a bag-of-words baseline.
2. Compare cosine similarity on two embedding or TF-IDF representations.
3. Show one pair that is lexically close and semantically not, or the reverse.
4. Write limits of embeddings for the decision you care about.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] A baseline without a neural net exists.
- [ ] Similarity examples are concrete documents.
- [ ] Preprocessing is documented.
- [ ] The apprentice can explain a dimension as a statistical object, not a mystery.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What meaning cannot live in a bag of words?
2. When would you refuse an embedding search as the product?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask them to break their own similarity function with a counterexample.
- Reject API-only demos with no baseline.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
