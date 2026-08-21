# Threat Modeling a System Boundary

**Task ID:** `sa1t3-002`
**Estimated effort:** 8 hours
**Module:** Security

## Why this task exists

This curriculum does not ask you to write secure code. It asks you to decide
where trust stops, what is allowed to cross, and which residual risk you are
willing to carry. Those decisions constrain every later control. A threat list
that ends in "sanitize input" has not left the implementation layer; a threat
list that ends in "this data class never leaves the payment boundary" has.

Reading about threat categories is preparation. Completion requires a diagram
with named crossings, four controls that change the architecture, and one ADR
that admits leftover risk.

## Authoritative resources

- **The Twelve-Factor App** (supporting): https://12factor.net/ — the config
  and backing-services factors are the ones that force credentials and
  attached resources out of the deployable. Use them when a threat is "the
  secret is in the image" or "the store is reachable from everywhere."

Use official documentation as the primary source. If you use other material
(a threat-modeling method you already know), record it in your notes. You are
not required to use any named method verbatim; you are required to produce
the artifacts below.

## Work to complete

1. Take a prior system diagram (`sa1t2-001` or `sa1t3-001`). Draw at least two
   trust boundaries — for example, public internet to edge, application to
   datastore, application to a payment or identity provider. Name who or what
   is allowed to cross each (a role, a network, a service identity).
2. List at least four threats that become possible if a boundary is crossed
   wrongly or skipped. Pair each with one architectural control: a tighter
   boundary, a dedicated credential store, a network restriction, a
   data-class rule (this field never appears in logs; this class never leaves
   region R), or a separation of a privileged store. "Validate input" and
   "use HTTPS" do not count unless you also state the boundary or store the
   control creates.
3. Choose the control you are least sure about. Write an ADR that names a
   rejected weaker control (a shared admin network, a long-lived secret in
   config, a single datastore for privileged and unprivileged data) and
   states one residual risk the chosen control does not remove.
4. If `sa1t2-001` already classified a sensitive element, reuse that
   classification and state whether this task tightens or leaves it.

## Required evidence

- A diagram that marks at least two trust boundaries on a prior system design
  and names who is allowed to cross each
- A threat list of at least four threats, each paired with one architectural
  control rather than a coding checklist item
- An ADR for one of those controls that names a rejected weaker control and
  the residual risk accepted by the chosen option

Submit a repository URL plus a commit reference.

## Acceptance criteria

- [ ] The diagram marks at least two trust boundaries and names the principal
      or network that is allowed to cross each.
- [ ] At least four threats each have a corresponding architectural control;
      none of those four controls is only "validate input" or "use HTTPS"
      without a stated boundary or store.
- [ ] The ADR names a rejected weaker control and states one residual risk
      the chosen control does not remove.

## Reflection

1. Which threat did you almost dismiss as "someone else's problem," and what
   boundary actually owns it?
2. What residual risk would you be unwilling to accept if the data class in
   the ADR were payment credentials instead of the class you used?

Also record: what took longer than expected, what you'd practice again, what
remains unclear.

## Mentor review guide

- Point at a box that sits on a boundary and ask what happens if that box is
  compromised. Approve only if the residual-risk sentence still holds.
- Do not approve a threat list that is a restated OWASP top ten with no
  boundary on the diagram.

Suggested outcome: **Approve**, **Request revision**, or **Discuss live**.

## AI use policy

Mode: **guided**. AI may explain trust-boundary vocabulary and quiz your
understanding of residual risk. AI must not produce the threat list or the
ADR for your specific diagram. Disclose any material AI use.

## Completion gate

This task is not complete when four threats are named. It is complete once
you can point at a boundary, name who crosses it, and state a risk the
chosen control leaves in place.
