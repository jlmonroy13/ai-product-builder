# Stage 1 — Idea normalization

Follow **exactly** `ai-builder/system/prompts/1-idea.md` (role, rules, output format).

- Resolve `{{ARTIFACTS_PATH}}` as `projects/default-project/artifacts` (see `pipeline.config.json`).
- Save the stage output to `projects/default-project/artifacts/1-IDEA.md` when persisting artifacts.

The user provides the raw product idea in natural language in this chat.
