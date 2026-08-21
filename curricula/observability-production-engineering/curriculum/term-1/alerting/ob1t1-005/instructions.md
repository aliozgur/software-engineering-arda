# Alerts That Page a Human, and Alerts That Should Not

**Task ID:** `ob1t1-005`
**Estimated effort:** 8 hours
**Module:** Alerting

## Why this task exists

Once you have an SLO (`ob1t1-004`), the next question is who gets interrupted when the
budget burns. Paging on every blip trains people to ignore pages. This task is the
judgment call: which condition deserves a human now, which can wait, and which should
never have been an alert.

You will prove the paging rule with two captures — silent when healthy, firing when you
burn the budget — not with a slide that says "we should page on errors."

## Authoritative resources

- **Site Reliability Engineering (Google SRE Book)** (primary):
  https://sre.google/sre-book/practical-alerting/ — Chapter 10, Practical Alerting.
  Also skim https://sre.google/sre-book/eliminating-toil/ (Chapter 5) for what a bad
  page costs.
- **Prometheus Documentation** (reference): https://prometheus.io/docs/alerting/latest/overview/
  — alerting rules and, if you use it, Alertmanager routing.

## Work to complete

1. Start from the SLIs and remaining-budget queries in `ob1t1-004`. If those queries
   cannot drive an alert, say what you had to change and why.
2. Write **at least three** alert rules in a checked-in rules file (Prometheus
   `alerting` rules, or an equivalent that a mentor can open):
   - At least one labeled **page**.
   - At least one labeled **ticket** or **info** (does not page a human immediately).
   - At least one candidate you considered as a page and **rejected** — keep it in the
     justification note, not necessarily as a disabled rule.
3. The paging rule must reference an SLI, SLO, or burn-rate over a documented window —
   not only `up == 0` on a single process. A host-down rule may exist as the ticket/info
   rule if you want one, but it cannot be your only paging condition.
4. Write a routing table: who is notified (a role is enough — "on-call apprentice",
   "ticket queue"), after what delay, and which dashboard or query they open first.
   Alertmanager config is welcome; a Markdown table is enough if you are not running AM.
5. Capture two evaluations of the **same** paging rule:
   - Healthy traffic: the paging alert is inactive / not firing.
   - Induced SLO burn (errors, latency past the SLI threshold, or a burn-rate you
     defined): the paging alert is firing.
6. In the justification note, name the rejected paging candidate and write one sentence
   of toil it would cause (example: "page on every 404 would fire on bot scans and train
   the on-call to mute the phone").

## Required evidence

- An alert-rules file with at least three rules, each labeled page or ticket/info
- A routing table or Alertmanager-equivalent config naming who is notified and after
  what delay
- Captured evaluation output showing the paging alert inactive under a healthy state
- Captured evaluation output showing the paging alert firing under an induced failure
- A page-versus-ticket justification note that includes the rejected paging candidate
- Reflection notes answering the questions below

Submit a repository URL plus a commit reference. Rule evaluation output can be
`promtool` test results, a Prometheus `/api/v1/alerts` snapshot, or a log line from
your alerter — not only a screenshot of a green dashboard.

## Acceptance criteria

- [ ] At least one rule is marked as paging and at least one is marked as non-paging.
- [ ] The paging rule's condition references an SLI or SLO-related query from
      `ob1t1-004` (or an equivalent burn-rate), not a host-down ping alone.
- [ ] Captured evaluation output shows the paging alert inactive in the healthy capture
      and firing in the induced-failure capture.
- [ ] The justification note names one alert candidate that was rejected as a page and
      states the toil it would cause in one sentence.

The mentor may ask you to lower a threshold until the paging alert flaps, then ask what
you would change. If you are working without a mentor, induce a short blip that should
**not** page (below your window or burn-rate) and capture that the paging alert stayed
inactive.

## Reflection

Answer these in your own words after doing the work:

1. If this paging alert fired twice in one night and both times the service was fine
   five minutes later, which part of the rule would you change first — threshold,
   window, or severity — and why that one?
2. What would the on-call do in the first two minutes after this page, using only the
   routing table you wrote?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves you learned the objective?

## Mentor review guide

Mentorship is optional. When a mentor is present: open the rules file and ask which
rule they would delete if they could keep only one. Do not approve a set where every
rule pages.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain burn-rate alerting and PromQL `ALERT` syntax, hint when a window is too
short, and quiz you on page-versus-ticket. AI must not generate the full rules file or
the justification note. Disclose material AI use: provider or model if known, purpose,
and how you verified both captures.

## Completion gate

This task is not complete when the rules file parses. It is complete once both captures
exist, the rejected page is named, and you can defend why a human should wake up for
exactly the paging rule.
