# SQL for Analysis, Not Just CRUD

**Task ID:** `da1t1-005`  
**Estimated effort:** 10 hours  
**Module:** sql

## Why this task exists

If the question is about a warehouse or an OLTP database, the first draft of the answer is a query. Learn SELECT as an analysis tool.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **CS50 SQL**: https://cs50.harvard.edu/sql/
- **PostgreSQL Documentation**: https://www.postgresql.org/docs/current/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Load or use a small relational schema (SQLite or PostgreSQL).
2. Write queries for filter, aggregate, and a join that answers a business question.
3. Write one window-function or CTE query and explain it in comments.
4. Compare one answer computed in SQL versus the same answer in pandas. They must match.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Queries are saved as files, not only run in a GUI.
- [ ] The join condition and grain are commented.
- [ ] SQL and pandas results match on the agreed metric.
- [ ] The apprentice can explain why a GROUP BY column is or is not in the SELECT list.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What analysis belongs in SQL versus in Python after extract?
2. How would a wrong grain in SQL create a fake trend?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask them to change the grain and predict what breaks.
- Reject screenshots of a query tool with no .sql files.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **restricted**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
