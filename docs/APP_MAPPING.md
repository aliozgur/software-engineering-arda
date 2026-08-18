# apprenti.dev App Mapping

The repository is intentionally shaped for the mobile app.

- Curriculum -> `curriculum.json`, term manifests and task definitions
- Progression -> `curriculum.json` `progression` (`sequential` or `random`)
- Task detail -> `task.json` + `instructions.md`
- Resource library -> `resources/*.json`
- Competency map -> `competencies/*.json`
- Learner notes/reflections -> fork-specific Markdown (`reflection.md`, `evidence.md`, `notes/*.md`) plus note metadata JSON
- Learner time -> `learners/<id>/tasks/<task-id>/worklog.json` (`1h` / `30m` / `1h 30m`)
- Submission -> fork-specific JSON
- Mentor review -> fork-specific JSON
- SQLite -> local projection/cache/search/embeddings/drafts/sync metadata

Local LLMs and cloud providers are runtime concerns and are not embedded in the curriculum. The application can route
educational capabilities (explain, hint, quiz, pre-review, reflection coach) to a local model or configured provider.
