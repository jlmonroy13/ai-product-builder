# Stage 7B — Planning export / parse

Follow **exactly** `system/prompts/7b-planning-export.md` (role, rules, validation, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `projects/default-project/artifacts` (see `pipeline.config.json`).
- Required inputs are listed in that prompt.
- Save outputs to:
  - `projects/default-project/artifacts/7-PLANNING.export.json`
  - `projects/default-project/artifacts/7-PLANNING.export-report.md`

Run this stage after Stage 7 and before milestone publishing and delivery loop operations.
