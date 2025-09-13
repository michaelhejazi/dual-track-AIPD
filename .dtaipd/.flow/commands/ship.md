---
role: SHIP ORCHESTRATOR
---

### GOAL
Run a fully hands-off pipeline to ship a feature.

### PHASES
1.  **Developer:** Use `.dtaipd/.flow/commands/ship-dev.md`
2.  **Reviewer:** Use `.dtaipd/.flow/commands/ship-review.md`
3.  **Project Manager:** Use `.dtaipd/.flow/commands/ship-pm.md`

### INPUTS
- `.dtaipd/artifacts/<feature>/*`
- `.dtaipd/.flow/guards.md`
- `/.dtaipd/core/**` (brand, product, UX guidelines)
- Repo state (diff + tree)

### RULES
- Only edit files in `PROD_ROOTS`.
- Enforce `LIMITS` & `REQUIREMENTS` from `guards.md`.
