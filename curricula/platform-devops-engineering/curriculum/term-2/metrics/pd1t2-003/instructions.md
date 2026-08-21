# Scrape Service Metrics with Prometheus

**Task ID:** `pd1t2-003`
**Estimated effort:** 12 hours
**Module:** Metrics

## Why this task exists

You cannot roll back with confidence if you cannot see whether the new version is worse. Prometheus on the local cluster or Compose stack is how this curriculum measures the service. You need a target that is UP, two series that move when you exercise the app, and PromQL you can defend.

This is an apprenticeship task, not a content-consumption checkbox. Reading Prometheus docs is only preparation. Completion requires before/after query results you caused.

## Authoritative resources

- **Prometheus Documentation** (reference): https://prometheus.io/docs/introduction/overview/

Use the official Prometheus documentation as the primary source. Run Prometheus locally (Compose, kind/minikube, or a local binary). Do not require a paid hosted metrics product.

## Work to complete

Instrument the same service, or add a documented exporter sidecar if the language makes in-process metrics unreasonable — say which you chose and why.

1. Expose a `/metrics` endpoint (or an exporter Prometheus scrapes) with at least two named series: a request-count style counter (or equivalent) and one other (latency histogram, in-flight gauge, error counter).
2. Commit a Prometheus scrape config that points at that target. Start Prometheus locally. Show the target as UP.
3. Write two PromQL expressions that answer operational questions ("how many requests in the last 5 minutes?", "what is the p95 of request duration?" — match what you actually exported).
4. Capture each query's result. Then apply a documented load (a script, `hey`/`ab`, or a loop of curl). Capture the same queries again and show the series moved.
5. Give at least one series a label for the service name or environment. Document how to start Prometheus and open the expression browser.

## Required evidence

- Committed Prometheus scrape configuration and the service change that exposes `/metrics` or an exporter
- Captured Prometheus targets page or API output showing the scrape target as UP
- Two named PromQL queries plus captured results taken before and after a documented load that changes those series
- README commands that start Prometheus locally and open the expression browser
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit only a screenshot of a green target with no query results.

## Acceptance criteria

- [ ] Prometheus scrape configuration is committed and Prometheus shows the apprentice's service target as UP.
- [ ] The service exposes at least two named metrics (a request-count style series and one other) that change when a documented load is applied.
- [ ] The evidence note includes the exact PromQL for two operational questions and a captured result for each, before and after the load.
- [ ] At least one metric series includes a label that names the service or the local environment.

A mentor should be able to replay the load command and see the same series move.

## Reflection

Answer these in your own words after doing the work:

1. What does a UP target prove, and what can still be broken in the service while the target stays UP?
2. Why did you choose those two PromQL questions — what decision would you make from each result?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to name a metric they did *not* export and say whether PromQL can invent it.
- Do not approve a scrape of `localhost:9090` (Prometheus scraping itself) as the only application target, or queries with no before/after capture.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — choosing metrics and writing PromQL yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved an UP target and two queries that move under documented load. LEARN BY DOING. GROW THROUGH MENTORSHIP.
