# Detect Drift and Choose a Remediation

**Task ID:** `pd1t3-003`
**Estimated effort:** 18 hours
**Module:** Drift

## Why this task exists

Someone will change a live object outside OpenTofu — a `kubectl edit`, a dashboard click, a "quick" docker update. If your only response is `tofu destroy`, you do not operate infrastructure; you reset a lab. This task is two experiments: revert once, and import or codify once, each with a plan you can show.

This is an apprenticeship task, not a content-consumption checkbox. Reading OpenTofu drift and import docs is only preparation. Completion requires two remediations that are not destroy-the-world.

## Authoritative resources

- **OpenTofu Documentation** (reference): https://opentofu.org/docs/

Use official documentation for `plan`, `apply`, and `import` (or the equivalent refresh/import workflow for your provider version). Stay on the local stack.

## Work to complete

Use the modular stack from `pd1t3-001`.

**Experiment A — revert**

1. Apply the stack so state matches reality.
2. Change one attribute out of band (`kubectl edit` a label, `docker update`, edit a ConfigMap key). Document the exact command.
3. Run `tofu plan`. Save the excerpt that names the resource address and the drifted attribute.
4. Apply to restore declared state. Show the follow-up plan no longer lists that drift.

**Experiment B — import or codify**

5. Create *another* out-of-band change — either a new object you did not declare, or an attribute you decide should become the new source of truth.
6. Either `tofu import` the object into state and then align the configuration, **or** change the configuration to match reality (codify). Do not only destroy.
7. Show a follow-up plan that is empty for that resource.
8. Write a short defense: why revert was right for A and import-or-codify was right for B. Name the risk of the choice you did *not* take in each experiment.

## Required evidence

- Plan excerpt after a documented out-of-band change showing the drifted resource address and attribute
- Experiment A notes: apply that restored the declared state, plus the empty or restoring plan excerpt
- Experiment B notes: either an import or a configuration change that codified the out-of-band object, plus a subsequent empty plan
- A short defense of why revert was chosen for A and import-or-codify for B
- Reflection notes answering the task questions
- AI disclosure entry when AI materially influenced the work

Submit a repository URL plus the note. Do not submit a single destroy/apply cycle as both experiments.

## Acceptance criteria

- [ ] After a documented out-of-band change, `tofu plan` shows that specific drift (resource address and the drifted attribute).
- [ ] Experiment A restores declared state by apply (revert); the follow-up plan no longer lists that drift.
- [ ] Experiment B either imports the out-of-band resource or updates the configuration to match it (codify), and the follow-up plan is empty for that resource.
- [ ] Destroy is not the only remediation demonstrated. Both experiments include plan excerpts in the notes.

A mentor should see two different choices, not the same apply twice.

## Reflection

Answer these in your own words after doing the work:

1. When is codifying a "quick fix" the wrong move even if it makes the plan empty?
2. What would you need (policy, review, lock) before you would allow `tofu apply` to revert production drift without a conversation?

Also record:

- What took longer than expected?
- What would you practice again?
- What remains unclear?
- Which artifact best proves that you learned the objective?

## Mentor review guide

- Ask the apprentice to defend the Experiment B choice against the alternative they did not take.
- Do not approve if both experiments are `tofu destroy` / re-apply, or if the plan excerpt does not name an attribute.

Suggested review outcome: **Approve**, **Request revision**, or **Create follow-up challenge**.

## AI use policy

Mode: **guided**. AI may be used for explanation, hints and quizzes. Solution generation is not allowed for this task — choosing the remediation yourself is the point. Any material AI assistance must be disclosed with the provider/model (if known), what it was used for, and how you verified the result.

## Completion gate

This task is complete only once the evidence is submitted and a mentor has approved two remediations with plan excerpts. LEARN BY DOING. GROW THROUGH MENTORSHIP.
