# Learning Model

## Roles

**Apprentice** performs the work, produces evidence, reflects, and remains accountable for understanding.
**Mentor** curates, reviews, asks questions, introduces constraints, and approves demonstrated competence.

## State flow

`not_started -> in_progress -> submitted -> approved`

A review may instead move a submission to `revision_requested`, after which a new or revised submission is made.

## Progression

A curriculum manifest may set `progression` to `sequential` or `random`.

- **Sequential:** the apprentice may not submit task N while any earlier path task is still unsubmitted (`not_started`, `in_progress`, or `revision_requested`). Waiting on a mentor (`submitted` / `resubmitted`) does not block the next submit.
- **Random:** tasks may be submitted in any order.

This repository is sequential. Path order comes from `term.json` task lists in academic order (year, then term-1 / term-2, then summer) — not from sorting task ids.

## Evidence over completion

Task completion is not based on watching videos or checking boxes. Evidence may include source repositories,
immutable commit/tag references, test results, design documents, packet captures, benchmark reports, demos,
incident timelines, reflections and oral review.

## Competency levels

1. Foundation
2. Apprentice
3. Practitioner
4. Journeyman
5. Mastery Evidence

Levels should be awarded from accepted evidence across multiple tasks, not from self-rating.

## Mentor behavior

Prefer questions such as “why?”, “what fails?”, “what alternative did you reject?”, and “show me”.
Avoid becoming the implementation engine. Create follow-up challenges when understanding is shallow.
