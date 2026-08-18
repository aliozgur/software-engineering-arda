# Tabular Python You Can Trace

**Task ID:** `da1t1-003`  
**Estimated effort:** 10 hours  
**Module:** python

## Why this task exists

pandas is easy to copy and hard to trust. Build filters, joins, and group-bys you can explain row by row.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **pandas User Guide**: https://pandas.pydata.org/docs/user_guide/index.html
- **Python 3 Tutorial**: https://docs.python.org/3/tutorial/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Load two related tables and join them on a documented key.
2. Compute group summaries and at least one window or rank.
3. Write tests or assertions for row counts before and after the join.
4. Show one incorrect join (duplicated keys) and how you detected it.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Join keys and expected cardinality are written down.
- [ ] A test or assertion fails if the join explodes.
- [ ] The apprentice can trace three rows through the pipeline by hand.
- [ ] No unexplained chained one-liners that the apprentice cannot unpack.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What does a left join keep that an inner join drops, in this dataset?
2. How did you notice a duplicate key?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask them to predict row count before running the join.
- Do not approve if they cannot explain `how=` and the key.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **restricted**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
