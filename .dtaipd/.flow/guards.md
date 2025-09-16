# Guardrails

## Roots
- PROD_ROOTS: everything except the following: [workbench/, .dtaipd/, .cursor/]
- WORKBENCH_ROOT: "workbench/"
- CONTEXT_ROOT: ".dtaipd/"

## File Caps
- /vibe: May write only under `workbench/` and `.dtaipd/`.
- /distill: May write only under `.dtaipd/artifacts/` and prototype docs under `workbench/<feature>/docs/`.
- /ship: May write to PROD_ROOTS and `.dtaipd/artifacts/`.

## Task Caps
- Keep tasks atomic and reversible.
- Map each task to a commit in /ship.

## Safety
- Prefer adapters/read-only access to production assets during /vibe.
- Any introduction of new dependencies must be justified and recorded in artifacts.
- Significant changes require an ADR.
