---
role: SHIP ORCHESTRATOR
---

### GOAL
Run a fully hands-off pipeline to ship a feature.

### PHASES
1.  Developer
2.  Reviewer
3.  Project Manager

### INPUTS
- `.dtaipd/artifacts/<feature>/*`
- `.dtaipd/.flow/guards.md`
- `/.dtaipd/core/**` (brand, product, UX guidelines)
- Repo state (diff + tree)

### RULES
- Only edit files in `PROD_ROOTS`.
- Enforce `LIMITS` & `REQUIREMENTS` from `guards.md`.

# /ship — Shipping Pipeline (Dev → Review → PM)

Preflight
- Ensure artifacts exist for the feature and match the latest prototype.

Execution (TDD‑first)
- For each task:
  1) Write failing tests (unit/e2e/visual as applicable).
  2) Commit: `test(<scope>): ...`.
  3) Implement code until tests pass.
  4) Commit: `feat|fix(<scope>): ...`.

Git + PR
- Branch: `feat/<feature-slug>`.
- Open PR and request reviewers.
- Attach links to `spec.md`, acceptance tests, `visual.png`, ADR.
- Ensure lint/typecheck and tests pass locally (or in CI if configured).

PM & Review Gates
- Reviewer enforces patterns and blocks drift.
- PM verifies acceptance criteria, writes `.dtaipd/artifacts/<feature>/Recap.md` and merges when all checks pass.

## Developer

Goal
- Implement the feature described in `.dtaipd/artifacts/<feature>` into PRODUCTION code, tests first.

Tasks
1.  Plan change set: ensure the number of files to be modified is ≤ `MAX_FILES_PER_PR` (see guards).
2.  Write tests for each acceptance check first (unit/e2e/visual as applicable).
3.  Implement production code to satisfy the tests.
4.  Draft Pull Request:
    - Include a summary of what was changed and why.
    - List the files that were changed.
    - Provide justifications for any new modules.
    - Document any risks and follow-up tasks.

## Reviewer

Goal
- Perform an automated and strict review of the changes.

Checks
- Scope: Changes are confined to `PROD_ROOTS`.
- File Count: Modified files ≤ `MAX_FILES_PER_PR` (or a justification is provided).
- Test Mapping: Tests map one-to-one with acceptance checks.
- Style: Naming/style follow guidelines in `/.dtaipd/core/ux/**`.
- Code Quality: No dead code or unnecessary abstractions.

Outputs
- Review notes.
- Small diffs applied directly to the code when safe.
- Updated pull request with reviewer notes appended.

## Project Manager

Goal
- Enforce process gates, run tests (locally or via CI if configured), finalize the PR, and write a recap.

Gates
- File/Diff Cap: Ensure the changes are within defined limits.
- Test Mapping: Verify tests are present and mapped to acceptance checks.
- Acceptance Coverage: Confirm all acceptance checks are covered.
- Production Scope: Ensure no modifications outside of `PROD_ROOTS`.

Output
- A finalized pull request.
- A recap of the changes in `.dtaipd/artifacts/<feature>/Recap.md`.
