# Threat Modelling and Secure Design

**Task ID:** `y3t2-001`  
**Estimated effort:** 14 hours  
**Module:** Security

## Why this task exists

Make security a design activity rather than a final checklist.

This is an apprenticeship task, not a content-consumption checkbox. Reading or watching material is only preparation.
Completion requires evidence that you can apply and explain the ideas.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Use the linked course/documentation as the primary source. You may use additional sources, but record them in your
learning notes and prefer primary documentation over tutorial aggregation sites.

## Work to complete

1. Create a data-flow diagram for an existing project.
2. Identify assets, trust boundaries and attacker goals.
3. Use a lightweight threat-modelling method such as STRIDE as a prompt, not a scoring ritual.
4. Prioritize threats by plausible impact/likelihood.
5. Implement mitigations for the top risks and record residual risk.

## Required evidence

- Git history showing incremental work
- README or technical note explaining the result
- Executable code/configuration when the task includes implementation
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Where code is produced, submit a repository URL plus an immutable commit/tag reference when possible. Do not submit
only screenshots of code.

## Acceptance criteria

- [ ] Threat model is specific to the system.
- [ ] Trust boundaries are visible.
- [ ] Mitigations map to threats.
- [ ] Secrets are not stored in Git.

The mentor may request a live explanation, modification or failure demonstration before approval. Passing automated
tests alone is not proof of understanding.

## Reflection

Answer these in your own words after doing the work:

1. Which threat changed the architecture?
2. What risk did you consciously accept?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Challenge assumptions: stolen token, malicious client, compromised dependency.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that
force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, quizzes and review unless the mentor further restricts it. Solution generation
is not the intended path for this task.
The apprentice must be able to explain, modify, test and defend every submitted artifact. Material AI assistance must
be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the
mentor approves the demonstrated competency.
