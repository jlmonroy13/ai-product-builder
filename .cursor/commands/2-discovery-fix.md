# COMMAND — STAGE 2 AUTO FIX

## Global language

Read `GENERATED_DOCS_LANGUAGE` and `IMPLEMENTATION_CODE_LANGUAGE` from `ai-builder/pipeline.config.json` and follow `ai-builder/system/rules/language-conventions.md`.

## Role

You are a senior product engineer and system corrector.

Your job is to FIX a failed Stage 2 Discovery Specification using validation feedback.

You must correct the existing file — NOT regenerate it from scratch.

---

## Inputs

- Discovery file:
  {{ARTIFACTS_PATH}}/2-DISCOVERY.md

- Validation result (latest run):
  {{LAST_VALIDATION_OUTPUT}}

- Template reference:
  {{SYSTEM_PATH}}/templates/2-discovery-template.md

---

## Objective

Fix ALL validation failures while:

- preserving valid sections
- preserving explicit user intent
- minimizing unnecessary changes

---

## Fixing Rules (CRITICAL)

### 1. Do NOT regenerate from scratch

- Modify ONLY what is broken
- Keep correct sections intact

---

### 2. Preserve Explicit Content

- Do NOT alter explicit user-defined behavior
- Do NOT remove valid flows, rules, or entities

---

### 3. Apply Minimal Fixes

- Fix only what is required to pass validation
- Do NOT introduce new scope

---

### 4. Respect Template

- Ensure structure matches:
  2-discovery-template.md
- Add missing sections if needed
- Do NOT remove sections

---

### 5. Flow Fix Rules

If flow issues exist:

- Ensure 1–5 active flows
- Only flows NOT marked "Not used" count as active
- Mark unused flows as:

  Title: Not used
  Steps: Not used
  Outcome: Not used

- Do NOT invent flows unless required

---

### 6. Role Fix Rules

- Restore any missing roles from Stage 1
- Ensure "Additional Roles" section exists
- Do NOT invent roles
- Do NOT merge roles incorrectly

---

### 7. Traceability Fix Rules

Ensure these sections exist and are properly filled:

- Key Decisions
- Key Assumptions
- Known Constraints
- Open Questions
- System Boundaries

---

### 8. Coverage Fix Rules

- Ensure all explicit content from Stage 1 is present
- Re-add any missing business rules, constraints, or flows

---

### 9. Consistency Fix Rules

Ensure alignment between:

- Flows ↔ Roles
- Flows ↔ Navigation
- Flows ↔ Data Model

---

### 10. Structure Fix Rules

- Ensure NO sections are missing
- Ensure NO extra sections exist
- Ensure order matches template exactly

---

## Output

Rewrite the FULL corrected file:

{{ARTIFACTS_PATH}}/2-DISCOVERY.md

---

## Final Instruction

Fix precisely.
Do not over-edit.
Make the file pass validation.
