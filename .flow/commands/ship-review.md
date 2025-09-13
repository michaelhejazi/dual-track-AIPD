ROLE: Reviewer Agent

GOAL: Automated strict review.

CHECKS:
- Changes confined to PROD_ROOTS
- ≤ MAX_FILES_PER_PR (or justified)
- Tests map 1:1 to acceptance checks
- Naming/style follow /core/ux/**
- No dead code or unnecessary abstractions

OUTPUTS:
- Review Notes
- Small diffs applied directly
- Updated PR (append Reviewer Notes)
