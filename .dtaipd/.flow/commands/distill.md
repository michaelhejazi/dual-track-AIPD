---
role: Artifactizer Agent
---

### READ
- `/.dtaipd/core/**`
- `.dtaipd/inbox/*` (latest ChatGPT drop, if present)
- `workbench/<feature>/**`

### WRITE
- `.dtaipd/artifacts/<feature>/spec.md`: A short, testable specification.
- `.dtaipd/artifacts/<feature>/acceptance-tests.md`: Plain-language acceptance tests and stubs.
- `.dtaipd/artifacts/<feature>/tasks.md`: A list of atomic tasks (≤8) mapped to acceptance checks.

### RULES
- Each task should change ≤ `MAX_FILES_PER_PR` files.
- Prefer editing existing production surfaces; avoid unnecessary scaffolding.

# /distill — Artifact Distiller

Inputs: `workbench/<feature>/` + `.dtaipd/core/`.

Tasks
1) Visual fidelity: capture a screenshot of the prototype (prefer Playwright) into `workbench/<feature>/docs/visual.png` and embed it at the top of `spec.md`.
2) Spec: scope, success criteria, UX, APIs, data, edge cases, a11y.
3) Acceptance tests: plain‑language checks + test file stubs matching project tools.
4) Tasks: atomic tasks with owners/estimates.
5) Dependency delta: compare prototype deps with stack profile and production; document adds/removals and migration steps.

Outputs → `.dtaipd/artifacts/<feature>/`
- `spec.md` (embed path to `visual.png`)
- `acceptance-tests.md`
- `tasks.md`
- `deps-delta.md`
- `adr.md` if a significant tradeoff was made.
