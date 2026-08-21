# Scoping a Bounded Agentic Coding Session

**Task ID:** `an1t1-004`  
**Estimated effort:** 6 hours  
**Module:** Agentic Workflows

## Why this task exists

An agentic session — one where the assistant reads files, plans, and edits across several steps with less turn-by-turn supervision than a single request-response exchange — is only safely reviewable afterward if you scoped it and gave it a way to check its own work before it started. This task is your first deliberate practice at that discipline, on a task small enough that a mistake costs you little.

This is an apprenticeship task, not a content-consumption checkbox. Completion requires evidence that the scope and the check existed before the session ran, not that you wrote them up afterward to match what happened.

## Authoritative resources

- **Best practices for agentic coding** (primary): https://code.claude.com/docs/en/best-practices
- **Anthropic prompt engineering** (reference): https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview

## Work to complete

1. Pick a small, multi-step task (a handful of related edits, not a single one-line fix, and not a whole feature) on a project you maintain.
2. Before starting the session, write and save the scoping prompt: what files or area are in scope, and at least one thing explicitly out of scope.
3. Also before starting, define the verification check — a test or command that will tell you whether the result works — and commit it if it's code (e.g. a test file).
4. Run the agentic session. Keep a summary log of what the assistant read, planned, and changed.
5. Review the resulting diff file by file against your stated scope. Run the verification check. Write a short decision note on any file that landed outside the stated scope.

## Required evidence

- The exact scoping prompt given to the assistant, saved before the session started
- A record of the verification command or test defined and committed before the session ran
- A summary log of what the assistant read, planned, and changed during the session
- The resulting diff, reviewed file by file against the original scope, with a short decision note on any out-of-scope file
- AI disclosure entry naming the tool/model used, purpose, and what was independently verified

Submit a repository URL plus commit references for the verification check and the resulting change.

## Acceptance criteria

- [ ] The verification command or test is committed before the agentic session's changes are committed.
- [ ] The saved scoping prompt names the files or area in scope and at least one explicit out-of-scope boundary.
- [ ] The diff touches only files inside the stated scope, or any file outside scope is explicitly flagged and justified in the review note.
- [ ] The verification check is shown passing against the final change.

The mentor may ask you to show the scoping prompt before seeing the diff, then predict what should and shouldn't have changed.

## Reflection

Answer these in your own words after doing the work:

1. Did the session stay inside your stated scope on its own, or did you have to intervene? What tipped you off?
2. What would have happened if you hadn't defined the verification check before running the session?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask for the timestamp or commit order proving the scope and check predate the session's changes.
- Ask what the apprentice would have done differently if the diff had touched a file outside the stated scope.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints, and quizzes. Solution generation is allowed because running the agentic session *is* the point of this task. The apprentice must be able to explain, modify, test, and defend every change the session made. Material AI assistance must be recorded in the submission notes with the provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only after the evidence is submitted and the mentor approves the demonstrated competency.
