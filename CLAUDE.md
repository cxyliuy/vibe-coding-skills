```
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.
```

## Project Overview

This is a documentation-first repository containing coding skills for the Vibe platform. It focuses on providing structured guidelines for planning, executing, and refactoring tasks.

## Repository Structure

- `stage-plan/SKILL.md`: Planning-stage behavior and output format
- `stage-execute/SKILL.md`: Execution-stage behavior and guardrails
- `refactor-table-alignment/SKILL.md`: UI table alignment refactor rules

Each skill is self-contained in its own directory with supporting files placed under that skill folder.

## Development Commands

There is no compiled build pipeline. Use lightweight checks:

```bash
# List all files
rg --files

# Check Markdown structure
rg -n "^---|^# " */SKILL.md AGENTS.md README.md

# Show git diff
git diff -- README.md AGENTS.md */SKILL.md

# Optional: Lint Markdown (if markdownlint is installed)
markdownlint README.md AGENTS.md */SKILL.md
```

## Coding Style Guidelines

- Use concise, instructional Markdown with explicit rules and actionable wording
- Prefer short sections, ATX headings (`#`, `##`), and fenced code blocks for commands
- Keep examples concrete and minimal
- Skill directories: kebab-case (e.g., `stage-plan`)
- Skill spec file: always `SKILL.md` (uppercase)

## Commit Guidelines

Use short imperative subjects:

```
<Verb> <scope> <intent>
```

Examples:
- `Refactor stage-execute output order wording`
- `Add metadata section to SKILL.md`

## PR Guidelines

Include:
- What changed and why
- Files touched (e.g., `stage-plan/SKILL.md`)
- Validation commands run and results
- Linked issue/task when available

## Documentation Validation

For documentation changes, validate:
- Clear title and section hierarchy
- Valid referenced paths/commands
- At least one example snippet for behavior changes
