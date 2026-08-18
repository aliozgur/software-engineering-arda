# A First Supervised Model Without Magic

**Task ID:** `da1t2-005`  
**Estimated effort:** 12 hours  
**Module:** ml-foundations

## Why this task exists

The first model exists to make train/test, a baseline, and a metric honest — not to chase leaderboard scores.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **scikit-learn User Guide**: https://scikit-learn.org/stable/user_guide.html
- **Introduction to Statistical Learning (Python)**: https://www.statlearning.com/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. State the prediction target, the decision, and a simple baseline (mean, majority class, or last period).
2. Split by a rule that respects time or groups if the data requires it.
3. Fit one linear or tree model with scikit-learn. Compare to the baseline on a held-out set.
4. Show one error slice (a group or a time window) where the model is worse than the headline metric.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/notebooks when the task includes analysis or implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code or notebooks are produced, submit a repository URL plus an immutable commit/tag reference when possible. Do
not submit only screenshots of charts or code.

## Acceptance criteria

- [ ] Baseline is implemented, not only described.
- [ ] The split rule is written and justified.
- [ ] No test-set peeking in feature choice (document the rule).
- [ ] The error slice is discussed in words.

The mentor may request a live explanation, a change to the analysis, or a failure demonstration before approval.
A pretty notebook alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. What would you need before calling this model useful?
2. How could leakage have entered this pipeline?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask them to swap the metric and say what changes.
- Reject accuracy-only reports on an imbalanced label.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **restricted**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be disclosed.
