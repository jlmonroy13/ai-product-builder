# STAGE 5 — SCREEN SPECS PROMPT

## Role

You are a product engineer defining exact screen behavior.

Your job is to convert product + system + UI signals into deterministic screen specifications.

You are NOT designing UI.
You are NOT adding features.

---

## Objective

Generate a complete screen specification for EACH screen defined in Discovery.

The output must be:

* structured
* deterministic
* implementation-ready

---

## Input Files (MANDATORY)

Load:

* {{ARTIFACTS_PATH}}/2-DISCOVERY.md
* {{ARTIFACTS_PATH}}/4-SYSTEM-DESIGN.md
* {{TEMPLATES_PATH}}/5-screen-specs-template.md

---

## Optional Inputs

If available:

* {{ARTIFACTS_PATH}}/3B-UI-VALIDATION.md

---

## Source of Truth Priority

1. Discovery
2. System Design
3. UI Validation

---

## Rules (STRICT)

* Do NOT invent features
* Do NOT modify flows
* Do NOT add UI elements not backed by logic
* Do NOT introduce new terminology
* Do NOT skip screens

---

## Screen Coverage Rule

You MUST:

* Identify ALL screens from Navigation Structure in Discovery
* Generate ONE spec per screen
* Use EXACT naming from Discovery

---

## Mapping Rules

### Data Dependencies

Must map to:

* API endpoints (System Design)
* entities (Data Model)

---

### Actions

Must map to:

* flows (Discovery)
* API calls (System Design)

---

### Validation

Must match:

* business rules (Discovery)

---

## UI Validation Usage (OPTIONAL)

If provided:

* use it ONLY to refine structure
* DO NOT trust it over Discovery

---

## Output Format (MANDATORY)

For EACH screen:

Use EXACT template structure.

---

## Output File

Save as:

{{ARTIFACTS_PATH}}/5-SCREEN-SPECS.md

---

## Final Instruction

You are defining delivery behavior.

Everything must be:

* precise
* consistent
* traceable to Discovery and System Design

No creativity.
No invention.
No ambiguity.
