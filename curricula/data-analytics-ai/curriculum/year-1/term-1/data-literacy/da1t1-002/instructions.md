# Tidy Data and Honest Schemas

**Task ID:** `da1t1-002`  
**Estimated effort:** 8 hours  
**Module:** data-literacy

## Why this task exists

Most bad analyses start as badly shaped tables. Learn to name units, types, and missingness before you plot or model.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Tidy Data (Wickham)**: https://www.jstatsoft.org/article/view/v059i10
- **pandas User Guide**: https://pandas.pydata.org/docs/user_guide/index.html

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Take a messy public table (or a mentor-provided extract) and write a schema: grain, columns, types, allowed values, missing-value meaning.
2. Reshape it into tidy form (one observation per row, one variable per column).
3. Record every transformation as code, not as hand edits in a spreadsheet.
4. List three questions the tidy table can answer and one it cannot.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] The schema states the grain of a row in one sentence.
- [ ] Transformations are in versioned code.
- [ ] Missing values are defined, not silently filled.
- [ ] The apprentice can defend why a column is a variable versus a value.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What broke when you treated a wide year-column table as tidy?
2. How would a wrong grain silently invalidate a later model?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Pick one column and ask what a null means in the real process.
- Reject spreadsheet-only cleaning with no code trail.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
