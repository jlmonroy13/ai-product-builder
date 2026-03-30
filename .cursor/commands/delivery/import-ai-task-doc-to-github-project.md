You import a **markdown document of repeated `# AI TASK` blocks** (for example `projects/default-project/artifacts/8-AI-TASKS.md` from Stage 8) into **GitHub Issues** and attach each issue to the repository’s **GitHub Project (v2)** so work appears as board cards (table or board layout—**not** a design tool).

**Single-run rule:** Parse the source, map every AI TASK to one execution-ready issue body, create or update issues via `gh`, add them to the Project, set fields when possible, and report a structured summary. Prefer **no duplicate issues** for the same logical task.

**Input (required):** Either:

- the **repository-relative path** to the markdown file (for example `projects/default-project/artifacts/8-AI-TASKS.md`), **or**
- the **full pasted content** of that file in the chat.

**Input (optional):**

- **Stage / milestone label:** a string such as `Stage 8` if the user wants it in titles, labels, or a Project field (for example from a heading like `# AI execution tasks (Stage 8)`).
- **Dry run:** if the user asks for preview only, output the list of planned issue titles and bodies **without** calling `gh issue create` / `gh project item-add`.

**Repo constants (this repository):**

- Default artifacts directory: **`projects/default-project/artifacts`** (`ARTIFACTS_PATH` in `pipeline.config.json`). Stage 8 AI tasks are typically saved as **`8-AI-TASKS.md`** (see `.cursor/commands/8-ai-execution.md`).

---

## Prerequisites

- **GitHub CLI:** `gh` authenticated for the target repo (`gh auth login`).
- **Project scope:** if `gh project` commands fail, run `gh auth refresh -s project`.
- **Pinned Project (recommended):** `docs/engineering/GITHUB_PROJECT.md` with YAML `owner` and `project_number` (from **`/configure-github-project`** or manual copy from `docs/engineering/GITHUB_PROJECT.example.md`). If missing, use `gh project list` and **ask** which project to use when ambiguous.
- **Issue body standard:** every created/updated issue must follow the section layout in `.github/ISSUE_TEMPLATE/feature.md` **below that template’s YAML frontmatter** (do not paste the template’s `---` metadata into the issue body).

---

## Document format you must support

1. **Preamble (optional):** Intro text before the first `# AI TASK` (for example “One AI TASK per ticket…”, paths note). Extract a **stage name** from a top-level heading like `# AI execution tasks (Stage 8)` when present.
2. **Repeated blocks:** Each block starts with a level-1 heading `# AI TASK` and contains subsections introduced as **`## Title`**, **`## Related Ticket`**, **`## Context`**, **`## Files to Create / Modify`**, **`## Implementation Requirements`**, **`## Constraints`**, **`## Done Criteria`**, **`## Notes`** (tolerate minor heading wording variants such as “Files to create or modify”, “File(s) to create / modify”).
3. **Split rule:** Treat each `# AI TASK` … up to the next `# AI TASK` or end-of-file as **one** work item.

If the file does not use this structure, stop and describe what is missing instead of inventing tasks.

---

## Mapping: AI TASK → `feature.md` issue body

Map into **the same headings and order** as `.github/ISSUE_TEMPLATE/feature.md`:

| Source | Target section |
|--------|----------------|
| `## Title` | Start **Summary** with the title; first line can repeat it for clarity. |
| `## Context` | **Summary** (continuation) and **Why this matters** (use Context for “why”; split if long). |
| `## Implementation Requirements` + `## Files to Create / Modify` | **Scope** (bullets) and **Technical Notes** (files list + implementation bullets). |
| `## Constraints` | **Technical Notes** (prepend as a “Constraints” sub-bullet list) and/or **Out of Scope** when constraints imply exclusions. |
| `## Done Criteria` | **Acceptance Criteria** (preserve checkboxes; normalize to `- [ ]`). |
| `## Notes` | **Technical Notes** (append) or **Dependencies** if notes describe blockers. |
| `## Related Ticket` | **References** (line: related ticket name); if identical to Title, one line is enough. |

Always include **References** with:

- Path to the source file if it lives in the repo (repo-relative), e.g. `projects/default-project/artifacts/8-AI-TASKS.md`.
- A line such as: `Imported from AI TASK doc (Stage N)` when a stage was inferred or provided.
- Cross-links to planning artifacts when the preamble or task mentions them: prefer repo paths such as `projects/default-project/artifacts/4-SYSTEM-DESIGN.md`, `7-PLANNING.md`, `5-SCREEN-SPECS.md` **if** those files exist; otherwise cite the filename without fabricating paths.

**QA Notes:** Derive from **Done Criteria** and **Implementation Requirements**: environment, commands to run, manual steps, expected results. If the source is thin, state minimal reproducible checks aligned with the acceptance bullets.

**Done Checklist:** Include the template’s default items from `feature.md` and ensure acceptance criteria from the source are reflected (avoid duplicate checklists that contradict).

---

## Issue titles

- Prefer: `[AI Task] <Title>` using the **`## Title`** value.
- If the user asked to emphasize stage: `[Stage N] [AI Task] <Title>` **or** add a `stage:N` label instead—**not** both unless requested.

---

## GitHub execution

1. **Discover existing issues:** `gh issue list --search "in:title <keywords>"` or search for `[AI Task]`; if an issue with the **same title** (match the `[AI Task] <Title>` pattern or the raw `<Title>`) already exists, **update** it with `gh issue edit` when the user wants sync, instead of creating duplicates. If unsure, **ask once** or prefer **update** when bodies differ and the user asked to import/sync.
2. **Create:** `gh issue create` with title and body (use a temp file or stdin for multiline bodies; avoid shell-escaping bugs).
3. **Project:** Resolve `owner` and `project_number` from `docs/engineering/GITHUB_PROJECT.md` when valid YAML is present; then for each issue:
   - `gh project item-add <project_number> --owner <owner> --url <issue_url>`
   - `gh project field-list <project_number> --owner <owner>` / `gh project item-list` as needed; use `gh project item-edit` to set **Status** (backlog / Todo / equivalent), and any **Stage**, **Milestone**, **Iteration**, or **Priority** field **only if** it exists and option IDs or values are known from `field-list`.
4. **Order:** Add items in **document order** so the board/table order matches the file (GitHub may not preserve visual order in all views—note that in the report).

---

## Output format

End with an **Import report** containing:

- Source: path or “pasted content”
- Stage (if any)
- Table: **order index** | **issue #** | **title** | **created vs updated** | **linked to project (yes/no)**
- Fields that could not be set (with reason)
- Next steps (short: implement from issues; open PRs linked to issues)

---

## Important

- Do **not** stop after printing shell commands for the user—**run** them when this is not a dry run.
- Preserve **technical precision** from the source (API paths, enums, status codes); do not summarize away acceptance criteria.
- Comments in code you add in the repo: **English only** (user rule).
