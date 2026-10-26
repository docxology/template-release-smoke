# docs/ — template-release-smoke

Human-facing documentation entry point. Agent-facing rules:
[`AGENTS.md`](AGENTS.md). Root overview: [`../README.md`](../README.md).

## What this repo is

Public integration smoke-test repository for the docxology/template unified
release orchestrator (`scripts/publish/publish_project_release.py` in the
template monorepo). It exists only to validate end-to-end GitHub release
creation and asset upload during automated publishing tests. Releases
attach rendered manuscript PDFs from the template workspace; they do not
mirror template source code. Do not cite releases or Zenodo records
created from this smoke test (from `../README.md`).

## Repository contents

This checkout intentionally contains only `README.md` and this `docs/`
folder. There is no source code, test suite, or pipeline configuration
here — the release orchestrator operates on this repository remotely.

## How to run / test

Nothing to run locally. The repository is exercised by the template
monorepo's publishing tests; see the publishing guide linked from the root
`README.md` (docxology/template, `docs/guides/publishing-guide.md`).

## Maintenance

Keep this folder minimal. Update only when the smoke-test's purpose or the
related links in the root `README.md` change.
