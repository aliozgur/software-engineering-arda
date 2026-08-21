# Modularize the Stack and Review a Plan

**Task ID:** `pd1t3-001`
**Estimated effort:** 18 hours
**Module:** IaC modules

## Why this task exists

A single root file that creates "the" stack cannot be reviewed the way a change to shared infrastructure must be reviewed. You need a child module with a contract, two instances that share it, and a plan you saved *before* apply so a mentor can see you read it.

This is an apprenticeship task, not a content-consumption checkbox. Reading OpenTofu module docs is only preparation. Completion requires two instances and a plan that matched apply.

## Authoritative resources

- **OpenTofu Documentation** (reference): https://opentofu.org/docs/

Use the official module and plan documentation. Stay on the local Docker or kind/minikube runtime. No paid cloud account.

## Work to complete

Refactor the stack from `pd1t2-002` (or the equivalent you now apply with OpenTofu).

1. Extract at least one child module with typed inputs and outputs. The child module must not hard-code the environment name.
2. Call that module from the root **twice** — two namespaces, two Compose project names, two label prefixes, or two equivalent isolated instances. Differences belong in `tfvars` (or `-var`) files, not in a fork of the module.
3. Run `tofu validate`. Then make one documented change (add a label, change a replica count, add a ConfigMap key). Save `tofu plan -out` (or the full text plan). Apply that plan. Confirm apply did not add surprises vs the saved plan.
4. Write `MODULE.md`: every input, every output, and one thing this module is **not** allowed to do (for example "must not create a second cluster").
5. Keep state gitignored. Document which var-file applies to which instance.

## Required evidence

- Committed root module that calls at least one child module used in two named instances or environments
- `tofu validate` output and a saved `tofu plan` for a documented change that later matches the apply
- tfvars or equivalent files that carry per-environment differences without editing the child module
- `MODULE.md` listing inputs, outputs, and one thing the module is not allowed to do
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not submit a module that is only a moved copy of the root with no second instance.

## Acceptance criteria

- [ ] The root module calls at least one child module that is applied in two named instances or environments (for example two namespaces or two Compose projects).
- [ ] `tofu validate` succeeds from a clean checkout.
- [ ] A saved `tofu plan` for a documented change is attached, and a subsequent apply matches that plan (no extra destroys or creates).
- [ ] Values that differ per environment live in tfvars or equivalent, not in edits to the child module. `MODULE.md` lists inputs, outputs, and one explicit non-goal.

A mentor should be able to read the plan and say what will change before opening apply output.

## Reflection

Answer these in your own words after doing the work:

1. What would you reject in a module review even if `tofu validate` passed?
2. Why is applying an unsaved plan riskier than applying a plan file you just reviewed?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to explain one resource in the saved plan without applying it again.
- Do not approve a "module" that is unused, used only once, or that duplicates the whole root with copy-paste.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — drawing the module boundary yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved two module instances and a plan that matched apply. LEARN BY DOING. GROW THROUGH MENTORSHIP.
