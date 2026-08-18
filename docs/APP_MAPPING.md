# apprenti.dev App Mapping

The repository is intentionally shaped for the mobile app.

- Curricula in this repo -> [curricula.json](../curricula.json): root `curriculum.json` plus `curricula/*/curriculum.json`
- Curriculum -> each manifest’s `curriculum.json`, term files and task definitions
- Progression -> `curriculum.json` `progression` (`sequential` or `random`)
- Task detail -> `task.json` + `instructions.md`
- Resource library -> `resources/*.json`
- Competency map -> `competencies/*.json`
- Learner notes/reflections -> `learners/<id>/` (`reflection.md`, `evidence.md`, `notes/*`, `worklog.json`)
- Learner time -> `learners/<id>/tasks/<task-id>/worklog.json` (`1h` / `30m` / `1h 30m`)
- Submission -> `learners/<id>/submissions/`
- Mentor review -> `mentors/<id>/reviews/`
- Personal overlay (do not share as a new base) -> `learners/`, `mentors/` — see [GIT_FORK_MODEL.md](GIT_FORK_MODEL.md)
- SQLite -> local projection/cache/search/embeddings/drafts/sync metadata

Local LLMs and cloud providers are runtime concerns and are not embedded in the curriculum. The application can route
educational capabilities (explain, hint, quiz, pre-review, reflection coach) to a local model or configured provider.
