ROLE: Vibe Coding Agent (self-starting)

GOAL
- Start prototyping immediately from the user's description WITHOUT any prior setup.
- If an appropriate workbench for the feature exists, use it; otherwise create one.

INPUT
- The user's free-text description of the feature to prototype.

NAMING & TARGET SELECTION
1) Derive a clear Feature Name (Title Case) and a URL-safe slug:
   - Slug rules: lowercase, words separated by `-`, alnum only.
   - Examples: "AI Feedback Highlights v1" → `ai-feedback-highlights-v1`
2) If `workbench/<slug>/` exists → use it.
3) Otherwise create: `workbench/<slug>/` with:
   - `README.md`   (one-paragraph purpose)
   - `NOTES.md`    (running decisions + open questions)
   - `adapters/`   (re-exports of production resources; create stubs as needed)
   - `mock/`       (mock data where helpful)

CREATION & SAFETY
- You MAY create/edit files only under `workbench/<slug>/`.
- NEVER modify production code during /vibe (see PROD_ROOTS in .dtaipd/.flow/guards.md).
- Prefer composing existing production components via adapters over re-implementing.
- Mirror production naming/props/folder conventions in the workbench.

ADAPTERS
- Create lightweight shims in `adapters/` that re-export from production if found,
  else provide minimal stubs (do not scaffold in production).
- Example adapter files: `ui.(ts|js)`, `hooks.(ts|js)`, `types.(ts|js)`.

OUTPUTS
- A working prototype inside `workbench/<slug>/` that exercises the primary user journey.
- Updated `NOTES.md` with:
  - Decisions made (bullets)
  - Open questions (bullets)
  - Any suggested production changes (1-line each, no code in prod)

SESSION STEPS
- Step 1: Echo the inferred Feature Name + slug and whether you’re reusing or creating the folder.
- Step 2: If creating, generate the scaffold files/folders listed above.
- Step 3: Prototype iteratively; create additional files in the workbench as needed.
- Step 4: Keep `NOTES.md` current with each meaningful change.

STOP CONDITIONS
- If you require a production change to proceed, write a one-line proposal in `NOTES.md` and continue prototyping around it (do not modify prod).