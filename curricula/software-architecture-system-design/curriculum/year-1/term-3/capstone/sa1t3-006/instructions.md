# End-to-End Architecture: Present, Defend, Revise

**Task ID:** `sa1t3-006`
**Estimated effort:** 10 hours
**Module:** Capstone

## Why this task exists

Every earlier task isolated one kind of judgment: a budget, a style, a store,
a cache, a failure, an SLO, a boundary, a region, a cut, a migration. This
closing task asks you to compose them for one problem and then defend the
composition when a constraint changes. The skill is not producing a polished
deck. The skill is revising the one decision the new constraint actually
invalidated, and leaving the rest standing.

You set up the session. Mentorship is optional in this curriculum; if a
mentor is unavailable, brief a peer to play a skeptical reviewer and to
introduce exactly one changed constraint. LEARN BY DOING. GROW THROUGH
MENTORSHIP. — the growth here is the live revision, not the first draft.

## Authoritative resources

- **adr.github.io** (primary): https://adr.github.io/ — specifically
  superseding and amending, not deleting.
- **OpenTelemetry Documentation** (supporting): https://opentelemetry.io/docs/
  — enough to keep the diagnostic story in signal vocabulary (span, metric,
  log event), not "we would look at the logs."

Use official documentation as the primary source. If you use other material,
record it in your notes.

## Work to complete

1. Scope a problem. You may compose from the running scenario used this year,
   or substitute a real system you have direct knowledge of, or take a
   mentor assignment. It must be large enough to need at least three distinct
   architecture decisions and one quantitative model. It must not be a
   restatement of a single earlier task with the title changed.
2. Build the packet:
   - An NFR sheet with at least four quantified budgets (reuse and revise
     earlier numbers; do not invent a clean sheet that ignores them).
   - At least three ADRs, each tracing to a named NFR or constraint. You may
     reuse earlier ADRs if they still hold; mark any you are carrying forward.
   - One quantitative model — capacity, SLO/error budget, or cost — with
     formulas visible.
   - One system diagram (style, data flow, or region topology — pick the
     view the decisions actually depend on).
   - A short diagnostic story: two failures and the signal that distinguishes
     them.
3. Arrange a defense. Ask the reviewer to introduce exactly one changed
   constraint partway through — a budget cut, a residency rule, a tighter
   SLO, a team-size change, a dependency that must now be treated as
   hostile. Take notes on the question that most challenged the packet and
   on any question you could not fully answer.
4. Write a superseding or amended ADR for the decision the constraint
   invalidated. Do not rewrite the packet from scratch. Add a side-by-side
   note: what the constraint invalidated, and what still stands.

## Required evidence

- An architecture packet containing an NFR sheet, at least three ADRs each
  tracing to a stated NFR, one quantitative model, one system diagram, and a
  short diagnostic story naming the signals that would distinguish two
  failures
- Defense-session notes naming the changed constraint and the specific
  question that most challenged the original packet
- A superseding or amended ADR that addresses the changed constraint without
  silently deleting the originals, plus a side-by-side note of what the
  constraint invalidated

Submit a repository URL plus a commit reference. The packet, the notes, and
the revision must be separately inspectable.

## Acceptance criteria

- [ ] The packet contains at least three ADRs, and each ADR names the NFR or
      constraint it responds to.
- [ ] The diagnostic story names two failures and the specific signal that
      would distinguish them, using the same vocabulary as a prior
      observability or SLO artifact.
- [ ] Defense notes name one changed constraint and one question the
      apprentice could not fully answer live; a second ADR marks the
      invalidated decision as superseded or amended rather than replacing
      it silently.

## Reflection

1. What did the changed constraint actually invalidate — a number, an
   alternative you had dismissed, or a boundary you had never drawn?
2. Which earlier task's artifact held up in the defense, and which one
   turned out to be decorative once someone pushed on it?

Also record: what took longer than expected, what you'd practice again, what
remains unclear, and which artifact best proves you met the objective.

## Mentor review guide

- Choose a constraint that invalidates one decision, not the whole packet.
  The point is a targeted revision.
- Ask the apprentice to recompute or re-score live from the quantitative
  model. If the model cannot absorb a changed input, it was a picture.
- Approve on whether the revision responds to the constraint that was
  actually raised, not on deck polish.

Suggested outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**. AI may explain, quiz, and — specifically for this task —
act as a coach to help you rehearse the defense before the real session. AI
must not generate the packet, choose the three decisions, or draft the
revised ADR. The revision has to reflect what the defense actually exposed.
Disclose any material AI use, including any rehearsal session.

## Completion gate

This task is not complete when the packet looks coherent. It is complete
once the notes show a real question you struggled with, and the superseding
ADR responds to that specific constraint rather than smoothing the whole
design over.
