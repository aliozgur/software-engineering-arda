# Declare the Local Runtime in OpenTofu

**Task ID:** `pd1t2-002`
**Estimated effort:** 14 hours
**Module:** Infrastructure as code

## Why this task exists

Hand-applied manifests work until two people apply them in a different order. OpenTofu gives you a plan you can read before anything changes, and a state file that names what exists. This task is the first time you declare the local runtime — Docker or Kubernetes against kind/minikube — so later you can detect drift and review a plan.

This is an apprenticeship task, not a content-consumption checkbox. Reading OpenTofu docs is only preparation. Completion requires apply, empty re-plan, destroy and re-apply.

## Authoritative resources

- **OpenTofu Documentation** (reference): https://opentofu.org/docs/

Use the official OpenTofu documentation as the primary source. Prefer the `tofu` CLI. If you consult a Terraform provider registry page (for example the Kubernetes or Docker provider), record the URL. Do not require a paid cloud provider.

## Work to complete

Target the local engine or the cluster from `pd1t2-001`. Typical shapes: Docker provider (network, volume, container) or Kubernetes provider (namespace, ConfigMap, Deployment). Mix is allowed if every resource is real and inspectable.

1. Install OpenTofu. Commit a `required_version` constraint. Use a **local** backend.
2. Write configuration that declares **at least three** distinct resources (not three `null_resource` placeholders). Each must correspond to something a mentor can see in `docker` or `kubectl` / the cluster.
3. Run `tofu init` and `tofu plan` from a clean checkout. Save the plan output. Then `tofu apply`. Capture `tofu state list`.
4. Run `tofu plan` again with no edits. The plan must show no unexpected changes. If it does, fix the configuration until a re-plan is clean, and say what drifted.
5. `tofu destroy`, then apply again. Confirm the same resource addresses return. Gitignore `*.tfstate` and `.terraform/`. Commit the `.gitignore` and a short `INFRA.md` that lists init / plan / apply / destroy.

## Required evidence

- Committed OpenTofu configuration plus `tofu init` and `tofu plan` output from a clean checkout
- `tofu apply` output and `tofu state list` showing at least three distinct resource addresses
- A second `tofu plan` with no edits showing no unexpected changes
- Command output of `tofu destroy` followed by a re-apply that recreates the same resource addresses
- A note stating the backend is local (or otherwise free) and that `terraform.tfstate` is gitignored
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus a commit/tag reference. Do not commit live state that contains secrets. Do not submit only a screenshot of a GUI.

## Acceptance criteria

- [ ] `tofu init` and `tofu plan` succeed from a clean checkout using only committed files.
- [ ] `tofu apply` creates at least three distinct resources a mentor can inspect via `tofu state list` and the actual Docker or Kubernetes objects.
- [ ] A second apply with no configuration edits produces a plan with no unexpected changes.
- [ ] `tofu destroy` removes the declared resources; a follow-up apply recreates them. State files are gitignored. No paid cloud account is required.

A mentor should be able to match each state address to a real object.

## Reflection

Answer these in your own words after doing the work:

1. What does an empty plan prove, and what can still be true in the cluster that OpenTofu cannot see?
2. Why is the state file not committed here, and what would go wrong if two people applied from two laptops against the same cluster with two local state files?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to pick one resource address and show the corresponding live object without looking at the HCL first.
- Do not approve a stack whose three resources are `null_resource` / `random_id` only, or a repo that commits `terraform.tfstate`.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — writing the configuration yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved apply, a clean re-plan, destroy and re-apply against local infrastructure. LEARN BY DOING. GROW THROUGH MENTORSHIP.
