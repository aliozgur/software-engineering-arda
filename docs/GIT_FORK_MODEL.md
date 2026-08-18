# Git Fork Model

The canonical repository should remain usable as upstream curriculum. Learner/mentor pairs fork it.

## Ownership boundaries

- `curriculum/**`, `resources/**`, `competencies/**`, `schemas/**`: upstream/curator-owned.
- `learners/<id>/**`: apprentice-owned durable learning records (state, reflection, evidence note, notes).
- `mentors/<id>/reviews/**`: mentor-owned review records.

Separating ownership minimizes same-file conflicts.

## Commit intent

Prefer meaningful domain commits rather than autosave commits:

- `learner(arda): submit y1t2-003`
- `mentor(ali): request revision for y1t2-003`
- `mentor(ali): approve y1t2-003`
- `curriculum: clarify transaction isolation task`

Transient typing/autosave belongs in the app's SQLite projection until the user explicitly saves/submits/publishes.

## Remote neutrality

Git is the persistence model. GitHub and GitLab can be initial remotes, but curriculum semantics must not depend on
Pull Requests, Issues, Projects, or provider-specific database APIs.
