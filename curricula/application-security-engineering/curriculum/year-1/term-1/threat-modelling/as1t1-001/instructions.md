# Threat-Model a System You Own

**Task ID:** `as1t1-001`  
**Estimated effort:** 10 hours  
**Module:** Threat modelling

## Why this task exists

The reference software-engineering path asks for a first threat model as one
design activity. This task goes further: the model is a working register that
later tasks update, not a one-off diagram. You will classify data, write
abuse cases a mentor can argue with, and leave residual risk explicit so
"we thought about security" is not an uncheckable claim.

This is an apprenticeship task, not a reading checkbox. Completion requires
evidence that you can apply and explain the ideas.

## Scope rule

Work only on an application you own or a local lab you start and stop
yourself. Do not send attack traffic to any third-party host. Reading about
a vulnerability class is in scope; reproducing it against someone else's
system is not.

## Authoritative resources

- **OWASP Top 10** (primary): https://owasp.org/www-project-top-ten/

Use the linked documentation as the primary source. You may use additional
sources, but record them in your learning notes and prefer primary
documentation over tutorial aggregation sites.

## Work to complete

1. Choose the HTTP application you will harden for the rest of this path.
   Use a system you already own, or stand up a small local lab you control
   with at least one authenticated flow, one per-user resource, one
   input that is stored or reflected, and one persistent store. Record the
   repository URL and the commit you started from.
2. Draw a data-flow diagram. Number every trust boundary. Label external
   actors, processes, and data stores. Mermaid in the threat-model document
   is enough; a committed image is also fine.
3. Classify every data store and every flow that crosses a trust boundary
   as public, internal, confidential, or secret. Write one sentence per
   classification explaining what would go wrong if that data leaked.
4. Using STRIDE as a prompt — not as a scoring ritual — list at least eight
   threats. For each, name the component, the boundary it crosses, and the
   matching OWASP Top 10 category, or mark it `outside Top 10`.
5. Rewrite at least two of those threats as abuse cases:
   `As an attacker who …, I can …, which harms …`.
6. Open a residual-risk register. Every threat starts as `open`,
   `mitigated`, or `accepted`. You are not required to implement
   mitigations in this task; you are required to say what you would fix
   first and why.

## Required evidence

- Committed threat-model document (for example `docs/threat-model.md`)
  containing the DFD as Mermaid or a committed image
- Data-classification table in that document covering every data store and
  every flow that crosses a trust boundary
- Residual-risk register in that document with status on every listed threat
- Git history showing the model written in more than one commit (DFD, then
  classification, then threats, then residual risk)
- Reflection note answering the task questions

Where documents are produced, submit a repository URL plus an immutable
commit or tag reference. Do not submit only screenshots of the model.

## Acceptance criteria

- [ ] The DFD shows at least 3 processes, 2 data stores, and 2 numbered
      trust boundaries.
- [ ] Every data store and every data flow that crosses a trust boundary is
      classified as public, internal, confidential, or secret.
- [ ] The register lists at least 8 threats; each names the component, the
      trust-boundary crossing, an OWASP Top 10 category or the label
      `outside Top 10`, and a status of open, mitigated, or accepted.
- [ ] At least 2 threats are written as abuse cases in the form: As an
      attacker who …, I can …, which harms ….
- [ ] No secret values, passwords, tokens, or connection strings appear in
      the committed model or elsewhere in the repository.

The mentor may ask you to walk a stolen-session or malicious-client
assumption through the DFD live. A generic Top 10 restatement that does
not name this system's components is not enough.

## Reflection

Answer these in your own words after doing the work:

1. Which trust-boundary crossing would you fix first, and what evidence
   from the classification table supports that order?
2. Which threat did you mark accepted, and what would have to change
   before you would reopen it?
3. Where did STRIDE help, and where did it produce a label that did not
   change any decision?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to point at one numbered boundary and name what
  a malicious client on the untrusted side can already do today.
- Reject a model that only restates OWASP category names without
  components, flows, or data classes from this system.
- Challenge one accepted risk: is it accepted, or just unexamined?

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**. Prefer questions that force reasoning over requests
for cosmetic polish.

## AI use policy

Mode: **guided**

AI may be used for explanation, hints and quizzes. Solution generation is
not the intended path for this task. The apprentice must be able to
explain, modify and defend every submitted artifact. Material AI
assistance must be recorded in the submission notes with the
provider/model (if known), purpose, and verification performed.

## Completion gate

Do not mark this task complete when the reading ends. It is complete only
after the evidence is submitted and the mentor approves the demonstrated
competency.
