# Visualization That Argues

**Task ID:** `da1t2-001`  
**Estimated effort:** 8 hours  
**Module:** visualization

## Why this task exists

A chart is a sentence. Design encodings so a reader can recover the claim without the caption doing all the work.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **Matplotlib Quick start**: https://matplotlib.org/stable/users/explain/quick_start.html
- **Foundation of visualization notes (UW CSE512)**: https://courses.cs.washington.edu/courses/cse512/24sp/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Rebuild one misleading chart (pie-with-3D, truncated axis, or dual axis) and a honest replacement.
2. Produce three charts for one dataset: distribution, comparison, and change over time.
3. Each chart title must be a claim the ink supports.
4. Write what a reader might still misread.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Axes, units, and filters are labeled.
- [ ] The misleading example is explained, not only replaced.
- [ ] Color is used for a meaning, not decoration.
- [ ] The apprentice can justify the geometry (bar vs line vs scatter).

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which encoding did the most work in your best chart?
2. What would you remove to make the claim clearer?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Cover the title and ask them to state the claim from the ink only.
- Reject rainbow colormaps on unordered categories.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
