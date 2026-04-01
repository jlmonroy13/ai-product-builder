# Stage 3b — UI validation

Follow **exactly** `ai-builder/system/prompts/3b-ui-validation.md` (role, rules, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `projects/default-project/artifacts` (see `pipeline.config.json`).
- Required inputs are defined in that prompt (e.g. `2-DISCOVERY.md`).
- Save the stage output to `projects/default-project/artifacts/3B-UI-VALIDATION.md` when persisting artifacts.
