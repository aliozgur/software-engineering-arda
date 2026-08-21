# Ship a Bad Release, Observe It, Roll It Back

**Task ID:** `pd1t3-005`
**Estimated effort:** 22 hours
**Module:** Incident response

## Why this task exists

The philosophy of this path is one sentence: build a real pipeline, ship through it, observe what happens, and be able to roll it back. This task is that sentence end-to-end. A hotfix that rewrites the bad image is not a rollback. A green smoke after you secretly patched `main` is not a rollback. You need two versions, a visible failure, and traffic back on the previous version.

This is an apprenticeship task, not a content-consumption checkbox. Mentorship is optional on this path; if you have a mentor, treat the live rollback as the review. Completion requires `INCIDENT.md` and a workload that shows `vN-1`.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/
- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/

Reuse the pipeline from `pd1t3-002`, the versions from `pd1t1-005`, and the signals from Term 2 / `pd1t3-004`. Stay on kind/minikube or the local stack. No paid cloud.

## Work to complete

1. Ensure a **good** versioned artifact exists (`vN-1` — the last release you trust). Record its git tag and image tag.
2. Cut a **bad** version (`vN`) that fails in a way your SLO or alert can see: elevated 5xx, a timeout, a broken dependency call. Deploy *that* version through the same process you used in `pd1t3-002` (pipeline job, or the documented apply of a pipeline-produced artifact — not an unpublished laptop-only image).
3. While `vN` serves traffic, capture: the firing alert or SLO burn, and a matching trace id or structured log line.
4. Roll back to `vN-1` using the documented release process: redeploy the previous tag via the pipeline, OpenTofu, or apply of the previous manifests. Do **not** rebuild `vN` with a fix and call that a rollback. Do **not** `docker tag` the bad image as the old version.
5. Show the running workload's image tag or version label is `vN-1`. Show the alert resolved. Send a smoke request that succeeds.
6. Write `INCIDENT.md`: detect / mitigate / resolve times (clock times you recorded), what each signal showed, one concrete follow-up (a gate, a test, a probe). No names, no blame.

## Required evidence

- Two versioned artifacts (good `vN-1` and bad `vN`) with git tags or image tags a mentor can list
- Captured alert or SLO burn plus a matching trace or structured log from the period the bad version served traffic
- Proof the rollback returned the workload to `vN-1` (image tag or version label on the running objects) using the documented release process, not by rewriting the bad image
- `INCIDENT.md` with detect / mitigate / resolve timestamps, what the signals showed, and one concrete follow-up, with no individual blame
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus both version identifiers. Do not submit a hotfix commit on `vN` as the mitigation.

## Acceptance criteria

- [ ] Two versioned artifacts exist (bad `vN` and good `vN-1`); after rollback the running workload shows `vN-1` as the image tag or version label.
- [ ] The bad release is shown deployed first, with a captured alert or SLO burn and a matching trace or structured log.
- [ ] Rollback uses the documented release process (pipeline, OpenTofu, or apply of the previous tag) and does not overwrite or rebuild the bad image as a hotfix.
- [ ] After rollback the alert resolves and a smoke request succeeds. `INCIDENT.md` includes a timeline, the signals, and one follow-up, without blaming a person.

A mentor should be able to list two tags and see the old one on the live workload after mitigate.

## Reflection

Answer these in your own words after doing the work:

1. What would have made rollback *unsafe* (incompatible schema, one-way migration), and did you have that risk here?
2. Which signal told you to roll back, and which signal only confirmed it after the fact?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- If a mentor is present, ask for a live second rollback: deploy `vN` again, then return to `vN-1`, and have the apprentice narrate the signals before they click.
- Do not approve a hotfix-forward on the bad tag, a missing `vN-1` artifact, or an incident note that blames a person.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**. Prefer questions that force reasoning over requests for cosmetic polish.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — performing the rollback and writing the incident note yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor — or you, if you are on the optional-mentorship path, with the same evidence bar — has approved a two-version rollback under observation. LEARN BY DOING. GROW THROUGH MENTORSHIP.
