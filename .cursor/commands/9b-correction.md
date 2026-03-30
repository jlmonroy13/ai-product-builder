# Stage 9b — Pipeline correction

Follow **exactly** `system/prompts/9b-correction.md` (role, rules, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `projects/default-project/artifacts` (see `pipeline.config.json`).
- Required inputs are listed in that prompt (multiple prior artifacts).
- Save the stage output to `projects/default-project/artifacts/9B-PIPELINE-CORRECTION.md` when persisting artifacts.
