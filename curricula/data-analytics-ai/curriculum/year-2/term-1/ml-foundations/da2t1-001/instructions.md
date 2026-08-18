# Generalization, Leakage, and Validation Design

**Task ID:** `da2t1-001`  
**Estimated effort:** 10 hours  
**Module:** ml-foundations

## Why this task exists

Year 2 starts by making validation the product. If the split is wrong, every later LLM demo is untrusted too.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **scikit-learn Cross-validation**: https://scikit-learn.org/stable/modules/cross_validation.html
- **Introduction to Statistical Learning (Python)**: https://www.statlearning.com/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Build a pipeline with a baseline, a model, and two validation schemes (e.g. random vs grouped or time).
2. Show that the headline score changes when the scheme matches the deployment unit.
3. Document a leakage you introduced on purpose and then removed.
4. Write the validation design as if it were part of a spec.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Both schemes are implemented in code.
- [ ] The deployment unit (user, day, store, document) is named.
- [ ] The intentional leak is visible in a commit and then gone.
- [ ] The spec would let a teammate reproduce the split.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which scheme would you ship, and why is the other flattering?
2. What validation can you not do with the data you have?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask what happens when a new group appears at test time.
- Reject a single random split on grouped data.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **restricted**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
