# Data Quality, Missingness, and Leakage Preliminaries

**Task ID:** `da1t2-002`  
**Estimated effort:** 8 hours  
**Module:** data-quality

## Why this task exists

Missingness and target leakage decide whether later ML is theater. Practice diagnosing them on a table before you fit anything.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **pandas Missing data**: https://pandas.pydata.org/docs/user_guide/missing_data.html
- **Datasheets for Datasets**: https://arxiv.org/abs/1803.09010

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Profile missingness by column and by plausible mechanism (MCAR/MAR/MNAR — in your own words).
2. Show one imputation that would change a group comparison and say why you reject or accept it.
3. Invent (or find) a column that would leak a future label if used as a feature. Explain the timeline.
4. Write a data-quality checklist you will reuse on the milestone.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Missingness is shown as counts and as a story about the process.
- [ ] No silent fillna without a written rule.
- [ ] The leakage example includes when the field becomes known.
- [ ] The checklist is specific enough to apply to a new file.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What missingness pattern would make you stop the analysis?
2. How is leakage different from a merely correlated feature?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask when each column is generated in the real workflow.
- Reject 'I dropped all nulls' with no impact analysis.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
