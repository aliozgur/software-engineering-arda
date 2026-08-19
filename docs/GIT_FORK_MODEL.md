# Git Fork Model

The canonical repository should remain usable as upstream curriculum. A mentor or apprentice forks it, clones it in apprenti.dev, then records pair work in **known overlay folders**. The app does not publish or sanitize a fork. People who copy or share the repository themselves must strip personal folders.

## Curriculum (shareable)

These paths are curator-owned. They are what you keep if you republish a fork as a new base:

- `curricula.json` (list of manifests in this working copy)
- `curricula/software-engineering/**` (Software Engineering manifest and task tree)
- `curricula/data-analytics-ai/**` (Data Analytics and AI)
- `curricula/**` (other curricula)
- `resources/**`
- `competencies/**`
- `schemas/**`
- curriculum `docs/**` (not personal notes)

## Personal overlay (do not share)

The app writes apprentice and mentor records **only** here:

| Folder | Owner | Contents |
|---|---|---|
| `learners/<id>/**` | apprentice | `profile.json` at the learner root; `c/<curriculum-id>/tasks/…` for each curriculum |
| `mentors/<id>/**` | mentor | `c/<curriculum-id>/reviews/` for each curriculum |

If you want to share the fork as curriculum, **delete `learners/` and `mentors/`** from the copy you publish. Removing them from the current tree is the minimum. Older Git commits can still contain those files; start a new repository from the remaining folders, or rewrite history yourself.

Do not put pair records under `curricula/`.

## Ownership and conflicts

Separating overlay folders from curriculum minimizes same-file conflicts:

- `curricula/**`, `resources/**`, `competencies/**`, `schemas/**`: curator
- `learners/<id>/**`: that apprentice
- `mentors/<id>/**`: that mentor

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
