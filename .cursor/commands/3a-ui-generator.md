# Stage 3a — UI generator prompt

Follow **exactly** `ai-builder/system/prompts/3a-ui-generator.md` (role, rules, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `ai-builder/project/artifacts` (see `pipeline.config.json`).
- Required input includes `ai-builder/project/artifacts/2-DISCOVERY.md`.
- Save the stage output to `ai-builder/project/artifacts/3-UI-PROMPT.md` when persisting artifacts.
