# AGENTS.md — llm-toolkit

This file tells LLM coding agents how to work with this repository.

## Repository purpose

A collection of reusable skills, plugins, and tools for LLM-powered coding harnesses (opencode, etc.). Not an application — no build/run/test scripts at the root.

## Key conventions

- **Skills** live under `.opencode/skills/<name>/SKILL.md`. Each has frontmatter (`name`, `description`) and procedural `## Execution Protocol` sections.
- **Plugins** live under `.opencode/plugins/<name>/`. Node.js packages using `@opencode-ai/plugin` or `@kilocode/plugin`.
- **No root-level `package.json`** — plugin dependencies are in `.opencode/package.json`.
- **The figma-orchestrator skill is the pipeline entry point.** It sequences figma-scout → figma-analyst → figma-controller. Never invoke a figma sub-skill directly.
- **Do not create new files unless explicitly asked.** Prefer editing existing files.

## Working with skills

1. Read the existing `SKILL.md` under the relevant skill directory to understand structure.
2. Skill frontmatter must include `name` and `description`.
3. Procedures use `<Sequence>` with numbered `<Step>` elements.
4. Markdown output templates inside skills are fenced with ```markdown.

## Working with plugins

- Each plugin is a standalone npm package under `.opencode/plugins/<name>/`.
- Entry point convention: `src/index.ts` → compiles to `dist/index.js`.
- Register plugins in the project's opencode config file (`.opencode.json` or similar).

## Lint / typecheck

None configured at the root. Each plugin package may define its own scripts.
