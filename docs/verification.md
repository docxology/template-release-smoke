# Verify the manuscript locally

Use Git, uv, Python 3.14 or newer, Pandoc, and XeLaTeX. Install the required TeX packages listed in the [template output guide](https://github.com/docxology/template/blob/87704feae0a4490ef7dad9c931d268e8c30273c2/docs/usage/output-formats.md). uv can provision Python with `uv python install 3.14`.

From a clean checkout of this repository, save its absolute path. Prepare the renderer in a fresh temporary directory:

```sh
project_root="$(pwd -P)"
verification_dir="$(mktemp -d)"
git clone https://github.com/docxology/template.git "$verification_dir/template"
cd "$verification_dir/template"
git checkout --detach 87704feae0a4490ef7dad9c931d268e8c30273c2
uv sync --locked --no-dev
mkdir -p projects/working "$verification_dir/project"
git clone --no-hardlinks "$project_root" "$verification_dir/project/template-release-smoke"
git -C "$verification_dir/project/template-release-smoke" checkout --detach "$(git -C "$project_root" rev-parse HEAD)"
ln -s "$verification_dir/project/template-release-smoke" projects/working/template-release-smoke

uv run --no-sync python scripts/pipeline/stage_03_render.py --project working/template-release-smoke
uv run --no-sync python scripts/pipeline/stage_04_validate.py --project working/template-release-smoke
```

Stage 04 reads the detached project's Git index to bind the manuscript to the outputs. Follow the links from the [root README](../README.md), [documentation index](README.md), and [manuscript index](manuscript/README.md) to check navigation.

Under `"$verification_dir/project/template-release-smoke/output"`, open `pdf/template-release-smoke_combined.pdf` and `web/index.html`. Check for the abstract, fixture scope, local verification boundary, and the upstream publishing guide in the references. Read `reports/validation_report.json` and `reports/rendered_provenance.json` for the validation and source records.

The upstream [publishing guide](https://github.com/docxology/template/blob/87704feae0a4490ef7dad9c931d268e8c30273c2/docs/guides/publishing-guide.md) describes the credentialed integration checks. The commands above validate manuscript artifacts locally and require no publishing credentials.
