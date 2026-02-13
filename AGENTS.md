# Repository Guidelines

## Project Structure & Module Organization

This repository is documentation-first and organized by skill folder:

- `README.md`: minimal project entry point.
- `stage-plan/SKILL.md`: planning-stage behavior and output format.
- `stage-execute/SKILL.md`: execution-stage behavior and guardrails.
- `refactor-table-alignment/SKILL.md`: UI table alignment refactor rules.

Keep each skill self-contained in its own directory. If a skill needs supporting files, place them under that skill folder (for example, `stage-execute/scripts/` or `stage-execute/assets/`).

## Build, Test, and Development Commands

There is no compiled build pipeline in this repo. Use lightweight checks:

```bash
rg --files
rg -n "^---|^# " */SKILL.md AGENTS.md README.md
git diff -- README.md AGENTS.md */SKILL.md
```

Optional (if installed):

```bash
markdownlint README.md AGENTS.md */SKILL.md
```

## Coding Style & Naming Conventions

- Use concise, instructional Markdown with explicit rules and actionable wording.
- Prefer short sections, ATX headings (`#`, `##`), and fenced code blocks for commands.
- Keep examples concrete and minimal.
- Naming conventions:
  - Skill directories: kebab-case (for example, `stage-plan`).
  - Skill spec file: always `SKILL.md` (uppercase).

## Testing Guidelines

For documentation changes, validate structure and clarity rather than runtime behavior:

- Ensure each updated doc has a clear title and section hierarchy.
- Verify referenced paths/commands are valid in this repository.
- When changing behavior rules, include at least one example snippet showing expected usage.

## Commit & Pull Request Guidelines

Recent commits use short imperative subjects (for example, `Add ...`, `Refactor ...`, `Rename ...`, `Delete ...`). Follow that pattern:

- Commit message format: `<Verb> <scope> <intent>`
- Example: `Refactor stage-execute output order wording`

PRs should include:

- What changed and why.
- Files touched (for example, `stage-plan/SKILL.md`).
- Validation commands run and results.
- Linked issue/task when available.

## Agent-Specific Notes

- Prefer minimal, diff-driven edits.
- Avoid expanding scope beyond the requested change.
- If required context is missing or instructions conflict, stop and request clarification.
