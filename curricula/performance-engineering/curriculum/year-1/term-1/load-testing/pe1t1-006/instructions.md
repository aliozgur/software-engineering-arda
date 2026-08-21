# Load Test to the Knee

**Task ID:** `pe1t1-006`
**Estimated effort:** 12 hours
**Module:** Load testing

## Why this task exists

The quality-engineering path (`qt1t2-001`) establishes a baseline SLO against
one workload shape. The software-engineering performance task (`y3t2-004`)
asks for a repeatable load test as one step among many. This task is the
missing measurement: **step the load until the SLO breaks**, name that offered
load, and quote the resource that is full. `pe1t1-007` will refuse invented
inputs — it will cite this knee.

## Authoritative resources

- **Prometheus Documentation** (primary): https://prometheus.io/docs/introduction/overview/
  — scrape the service and PostgreSQL (or the runtime) so saturation is a
  number, not a feeling.
- **OpenTelemetry Documentation** (reference): https://opentelemetry.io/docs/
  — traces under load if you need to see which span grows as you approach
  the knee.
- **PostgreSQL Documentation** (reference): https://www.postgresql.org/docs/current/
  — connection limits, lock waits, and `pg_stat_activity` / `pg_stat_statements`
  when the origin of saturation is the database.

Any load generator you can run with one command is acceptable (k6, vegeta,
hey, wrk, locust, or a small custom driver). There is no required vendor.

## Work to complete

1. Point the generator at the service you have been measuring (the path should
   still hit PostgreSQL or the store you used in `pe1t1-004` / `pe1t1-005`).
   Restate the `pe1t1-001` SLO at the top of the report (percentile + error
   rate). If you change it, say why — do not silently loosen it after the
   first ramp.
2. Write a script whose **one documented command** applies a stated shape
   (arrival rate or VU count, duration, think time if any).
3. Run **at least three load levels** (stepped or ramped). For each level
   record offered load, p95, and error rate. Commit raw output.
4. Name the **knee**: the lowest offered load at which the SLO fails. That
   is a number (RPS, or VUs if you explain the conversion).
5. At the knee, quote **one saturation signal** you measured: CPU percent,
   open db connections vs `max_connections`, lock wait count, or queue
   depth. A sentence that "the database was probably slow" is not a signal.
6. Pick one operating point **below** the knee. Run it **three times**.
   Report the p95 range. `pe1t1-007` will use the SLO-meeting rate from
   this point, not the knee itself, as sustainable capacity.

## Required evidence

- Load script and the one command
- Three-or-more-level table (load, p95, error rate) plus raw logs
- Knee statement (number + which SLO clause failed)
- Saturation note with a measured resource value at the knee
- Three-run p95 range at one sub-knee operating point
- Reflection notes

## Acceptance criteria

- [ ] One documented command produces the workload; the script states
      arrival rate or VU count and duration.
- [ ] At least three load levels are reported, each with offered load, p95
      latency, and error rate.
- [ ] The knee is the lowest reported offered load at which the SLO from
      `pe1t1-001` (latency percentile or error rate) fails; that load is a
      number.
- [ ] The saturation note quotes a measured value for one named resource at
      the knee, not a guess about what "must have" saturated.
- [ ] Three runs at one operating point below the knee report a numeric p95
      range.

The mentor may ask you to add one more step just below and just above the
knee. If the failure is not reproducible, the knee is not established.

## Reflection

Answer these in your own words after doing the work:

1. Which SLO clause failed first at the knee — latency or errors — and what
   saturation number sits next to that failure?
2. How wide was p95 at the sub-knee operating point, and what load would you
   publish as "safe" given that range?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask whether the SLO was copied from `pe1t1-001` or edited after the ramp.
- Ask what would happen to the knee if the cache from `pe1t1-004` were
  flushed at the start of each step.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up
challenge**.

## AI use policy

Mode: **guided**

AI may explain load-generator APIs and quiz you on saturation vs load. It
must not invent RPS, p95, or saturation figures. Disclose material AI
assistance with provider/model, purpose, and verification performed.

## Completion gate

Complete only after the stepped table, the numbered knee, and the measured
saturation signal are submitted and the mentor approves.
