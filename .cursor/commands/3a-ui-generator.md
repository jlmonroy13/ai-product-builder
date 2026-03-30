# Stage 3a — UI generator prompt

Follow **exactly** `system/prompts/3a-ui-generator.md` (role, rules, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `projects/default-project/artifacts` (see `pipeline.config.json`).
- Required input includes `projects/default-project/artifacts/2-DISCOVERY.md`.
- Save the stage output to `projects/default-project/artifacts/3-UI-PROMPT.md` when persisting artifacts.
