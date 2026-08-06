# Project overview

lisa is a single-file CSS library that combines a simple normalizer with a class based system like TailwindCSS.

## Spacing

The following spacing units are used:
- 8px: tight interals like icon gaps, button padding, etc., every micro-adjusement uses this as a base.
- 16px: standard gap between related elements
- 32px: container padding and verical rhythm
- 40px: layout-level spacing
- 80px: section-breaks

# Code style

- Use comments only to document a function/file/etc. according to proper
  conventions, or where code would be confusing without extra context.
- Keep lines below ≈90 characters.
- Use short and descriptive rules names.
- Avoid excessively long rules.

# Workflow

- Update FEATURES.md if needed.

# Git conventions

- Do all work on a branch off `main` and merge it back; don't commit changes
  directly to `main`. The one exception is the root commit that scaffolds a
  repository, which has no branch to come from.
- Name branches `<type>/<short-description>`, reusing the commit types below:
  `feat/template-loader`, `fix/empty-content-dir`, `chore/bump-ruff`.
- Write commit subjects as `<type>: <summary>` — imperative mood, ≤72
  characters, no trailing period. Types: `feat`, `fix`, `refactor`, `perf`,
  `docs`, `test`, `chore`. Add a body when the *why* isn't obvious from the diff.
- Keep each commit to one logical change. Formatting-only churn goes in its own
  `chore:` commit.
- Rebase an unmerged branch onto `main` to keep its history linear, then merge
  with `--no-ff` so the branch stays visible. Never rewrite commits already on
  `main`.
- Delete branches once they're merged.
