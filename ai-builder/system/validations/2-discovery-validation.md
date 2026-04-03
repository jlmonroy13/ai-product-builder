# STAGE 2 — DISCOVERY VALIDATION CHECKLIST

## Global language (CRITICAL)

Expect narrative content in the language set by `GENERATED_DOCS_LANGUAGE` in `ai-builder/pipeline.config.json`. See `ai-builder/system/rules/language-conventions.md`.

## Structure (CRITICAL)

- [ ] Matches template exactly
- [ ] The artifact H1 is `# STAGE 2 — DISCOVERY` (not the template file’s `DISCOVERY TEMPLATE` title)
- [ ] No sections missing

---

## Coverage (CRITICAL)

- [ ] All explicit info preserved

---

## Roles (CRITICAL)

- [ ] Primary user exists
- [ ] Additional roles preserved

---

## Flows (CRITICAL)

- [ ] 1–5 active flows
- [ ] Unused slots marked "Not used"
- [ ] No artificial flows

---

## Scope (CRITICAL)

- [ ] No new features introduced

---

## Consistency (CRITICAL)

- [ ] Flows align with data, roles, navigation

---

## Traceability

- [ ] Decisions documented
- [ ] Assumptions present
- [ ] Constraints present

---

## Final

If any critical fails → FAIL
Else → PASS
