# Analyst Workstation and Reproducible Work

**Task ID:** `da1t1-001`  
**Estimated effort:** 8 hours  
**Module:** foundations

## Why this task exists

An analysis you cannot rerun is not evidence. Set up a repeatable Python environment, version the work, and separate exploration from claims.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **MIT Missing Semester**: https://missing.csail.mit.edu/2026/
- **Python 3 Tutorial**: https://docs.python.org/3/tutorial/
- **Pro Git**: https://git-scm.com/book/en/v2

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a Git repository with a virtual environment, a requirements or lock file, and a README that states how to rerun the work.
2. Write one script and one notebook that load the same small CSV and print the same summary statistics.
3. Commit in small steps. Show at least one fix after a failed run.
4. Document when you would use a notebook versus a script.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] A clean clone plus documented commands reproduces the summary.
- [ ] Git history has meaningful commits, not a single dump.
- [ ] The README names Python version and dependencies.
- [ ] The apprentice can explain the difference between the working tree and a notebook output cell.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What makes an analysis reproducible enough for a mentor to rerun?
2. When is a notebook the wrong artifact to submit?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to delete caches and rerun from a fresh clone.
- Do not approve a repo that only works on their laptop path.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
