# AGENTS.md — template-release-smoke

Guidance for agents working in this repository.

## What this repository is

A deliberately empty integration fixture for the `docxology/template` unified release
orchestrator (`scripts/publish/publish_project_release.py`). It exists so that automated
publishing tests can create a real GitHub release and upload real assets against a
throwaway target. Releases attach rendered manuscript PDFs from the template workspace;
they never carry template source code.

**Releases and Zenodo records produced from this repository are test artifacts. Do not
cite them.**

## What is here

| Path | Role |
|---|---|
| `README.md` | Human entry point: purpose and links to the template repository |
| `docs/AGENTS.md` | Notes on the `docs/` folder itself |
| `docs/README.md` | Documentation index |
| `docs/manuscript/MANUSCRIPT_STATUS.md` | Why no publication manuscript applies |

There is no `src/`, no `tests/`, no scripts and no build configuration — by design. The
release orchestrator lives in the template monorepo and drives this repository remotely.

## Working here

- Keep it minimal. Adding code, tests or build configuration defeats the purpose of the
  fixture and changes what the publishing tests are actually exercising.
- Do not add a CI workflow; the absence of one is part of the fixture.
- There is no test suite and no lint gate, so a change here is verified by the template
  repository's publishing tests, not by anything local.

## Relationship to `docs/AGENTS.md`

`docs/AGENTS.md` documents the `docs/` folder only. This file is the repository-level entry
point; the two should not restate each other.
