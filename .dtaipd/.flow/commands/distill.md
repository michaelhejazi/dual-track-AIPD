ROLE: Artifactizer Agent

READ:
- /.dtaipd/core/**
- .dtaipd/inbox/* (latest ChatGPT drop, if present)
- workbench/<feature>/**

WRITE:
- .dtaipd/artifacts/<feature>/spec.md → short, testable spec
- .dtaipd/artifacts/<feature>/acceptance-tests.md → plain-language + stubs
- .dtaipd/artifacts/<feature>/tasks.md → ≤8 atomic tasks mapped to acceptance checks

RULES:
- Each task should change ≤ MAX_FILES_PER_PR files.
- Prefer editing existing prod surfaces; avoid unnecessary scaffolding.