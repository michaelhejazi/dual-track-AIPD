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
