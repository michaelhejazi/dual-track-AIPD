# Cursor Rules (Minimal)

## Context Priority
- Prefer reading from:
  1) `.dtaipd/core/**` (brand, product, UX, tech stack)
  2) `.dtaipd/.flow/**` (prompts and guards)
  3) `workbench/**` (current prototype)

## Command Write Bounds
- `/capture`: write only `.dtaipd/inbox/SUMMARY.md`.
- `/vibe`: write only under `workbench/<feature>/` and `.dtaipd/`.
- `/distill`: write only under `.dtaipd/artifacts/<feature>/` and `workbench/<feature>/docs/visual.png`.
- `/ship`: write only under `PROD_ROOTS` and `.dtaipd/artifacts/<feature>/Recap.md`.

## Quality
- **Stack alignment**: adhere to `.dtaipd/core/tech-stack/stack.md`; record deviations.
- **TDD**: write failing tests first, then code.
- **Small edits**: keep change sets atomic and reversible per `guards.md`.
