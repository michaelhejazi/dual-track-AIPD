PROD_ROOTS:
  - app/
  - components/
  - lib/
  - styles/

LIMITS:
  MAX_TASKS_PER_SPEC: 8
  MAX_FILES_PER_PR: 10

REQUIREMENTS:
  - Tests must map 1:1 to acceptance checks in .dtaipd/artifacts/<feature>/acceptance-tests.md
  - Prefer edits to existing modules; any new module requires a 1-line justification in PR body
  - Do not modify workbench/, .dtaipd/artifacts/, .dtaipd/core/ during /ship