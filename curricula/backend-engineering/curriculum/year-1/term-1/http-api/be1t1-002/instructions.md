# HTTP Fundamentals for a Backend Service

**Task ID:** `be1t1-002`
**Estimated effort:** 12 hours
**Module:** Http Api

## Why this task exists

A framework will happily choose status codes and methods for you if you let
it. This task asks you to make those choices by hand first, so the fluency is
actually yours before it gets convenient to stop thinking about it.

## Authoritative resources

- **HTTP Semantics — RFC 9110** (deep_dive): https://www.rfc-editor.org/rfc/rfc9110
- **MDN Web Docs** (reference): https://developer.mozilla.org/
- **Python 3 Tutorial** (reference): https://docs.python.org/3/tutorial/

Use the linked documentation as the primary source. Prefer the RFC over
secondary summaries when method/status semantics get ambiguous.

## Work to complete

1. Capture a raw HTTP request/response for at least two different methods
   (for example using `curl -v` or a packet capture) and annotate every
   header line with what it does.
2. Build a minimal HTTP API in Python (the standard library's `http.server`
   or a micro-framework such as Flask) exposing at least three routes.
3. Choose a status code and method for each route deliberately, and be ready
   to justify each choice to a mentor without notes.
4. Return consistent JSON error bodies for at least two failure cases (not
   found, bad input) — the same shape every time, not ad hoc per route.
5. Write a curl-based smoke test script exercising every route, including
   both failure cases.

## Required evidence

- The annotated raw request/response capture, committed as a text file
- Git history showing the API built incrementally — routes, then error
  handling, then the smoke test
- The curl smoke test script and a paste of its output
- README explaining the method/status choice for each route

## Acceptance criteria

- [ ] Each route responds with a status code that matches HTTP semantics for
      its outcome.
- [ ] At least one endpoint demonstrates an idempotent method and one
      demonstrates a non-idempotent method, and the README names which is
      which.
- [ ] Error responses are valid JSON with a consistent shape across
      endpoints.
- [ ] The curl smoke test script exercises every route, including both
      failure cases, and is committed to the repository.

The mentor may give you three new scenarios live and ask you to choose the
method/status without looking anything up.

## Reflection

Answer these in your own words after doing the work:

1. What makes an operation idempotent, and which of your routes actually is?
2. Where did you choose 200 versus 201 versus 204, and why?
3. What is the difference between transport-level success and
   application-level success?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?

## Mentor review guide

- Give three new API scenarios live and ask the apprentice to choose
  method/status semantics without notes.
- Review the contract (routes, statuses, error shape) before implementation
  details.

Suggested review outcome: **Approve**, **Request revision**, or **Create
follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution
generation is not the intended path for this task. Material AI assistance
must be disclosed with the provider/model (if known), purpose, and
verification performed.

## Completion gate

This task is complete only once the evidence is submitted and the mentor
approves the demonstrated understanding — not when the routes merely
respond.
