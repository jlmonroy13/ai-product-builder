# AI Product Builder

This repository contains a reusable AI-driven product pipeline.

## Structure

- `system/` → reusable prompts, templates, and rules
- `projects/` → project-specific artifacts, UI assets, execution logs, and context
- `engine/` → future execution and automation layer
- `pipeline.config.json` → source of truth for path variables

## Path Variables

Prompts and templates use variables such as:

- `{{ARTIFACTS_PATH}}`
- `{{SCREENSHOTS_PATH}}`
- `{{PROMPTS_PATH}}`
- `{{TEMPLATES_PATH}}`
- `{{RULES_PATH}}`

This allows the pipeline to scale across multiple projects without rewriting internal references.
