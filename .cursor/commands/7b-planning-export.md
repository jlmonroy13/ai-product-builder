# Stage 7B — Planning export / parse

Follow **exactly** `ai-builder/system/prompts/7b-planning-export.md` (role, rules, validation, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `ai-builder/project/artifacts` (see `pipeline.config.json`).
- Required inputs are listed in that prompt.
- Save outputs to:
  - `ai-builder/project/artifacts/7-PLANNING.export.json`
  - `ai-builder/project/artifacts/7-PLANNING.export-report.md`

Run this stage after Stage 7 and before milestone publishing and delivery loop operations.
