# AGENTS.md — docs/ (template-release-smoke)

## Layout

- `README.md` — human entry point (purpose, related links)
- `AGENTS.md` — this file
- `manuscript/MANUSCRIPT_STATUS.md` — why no publication manuscript applies

## Repo conventions observed

- Minimal by design: no `src/`, `tests/`, scripts, or build configuration;
  the release orchestrator in the template monorepo drives this repo
  remotely during publishing tests.
- Releases from this repo are test artifacts and must not be cited.

## Maintaining these docs

Keep both files short and factual, derived only from repo files. Do not
add content describing functionality this repo does not have.
