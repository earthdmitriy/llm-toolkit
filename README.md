# llm-toolkit

A collection of reusable skills, plugins, hooks, and tools for LLM-powered coding agents — primarily targeting [opencode](https://opencode.ai).

## Structure

```
.opencode/
├── skills/           # OpenCode skills (reusable agent directives)
│   ├── figma-orchestrator/   # Entry point — coordinates the 3-phase Figma pipeline
│   ├── figma-scout/          # Phase 1: scans chaotic Figma frames, indexes elements
│   ├── figma-analyst/        # Phase 2: transforms index into structured spec draft
│   ├── figma-controller/     # Phase 3: validates links, finds contradictions, finalizes spec
│   └── spec-architect/       # Converts feature prompts into production-grade spec.md files
└── plugins/          # OpenCode plugins (TypeScript/Node)
```

## Skills

| Skill | Entry | Description |
|-------|-------|-------------|
| **figma-orchestrator** | ✓ | Master coordinator that sequences figma-scout → figma-analyst → figma-controller, manages state and transient file handoffs |
| **figma-scout** | | Crawls Figma frames via MCP, harvests text/components/validation hints, outputs `figma-index.json` |
| **figma-analyst** | | Reconstructs business logic from raw index, interviews user on blind spots, drafts `figma-spec.md` |
| **figma-controller** | | Anti-hallucination link verification, isolates layout contradictions, produces final `figma-spec.md` |
| **spec-architect** | | Discovery engine that turns ambiguous feature prompts into explicit, production-grade spec documents |

## Figma Pipeline

The **figma-orchestrator** skill is the entry point for extracting technical specifications from Figma designs. It invokes the three pipeline phases in sequence:

1. **Scout** — Ingests the Figma root node, interviews the user for detached spec frames, deep-crawls and indexes all elements into `figma-index.json`.
2. **Analyst** — Reads the index, groups scattered elements into logical fields, identifies gaps via interactive questions, and drafts `figma-spec.md`.
3. **Controller** — Validates every Figma URL against the live MCP, corrects hallucinations, surfaces designer contradictions, and writes the final production spec.

## Usage

Skills live under `.opencode/skills/` and are loaded by the LLM agent when the task matches the skill description. Plugins live under `.opencode/plugins/` and are registered in the opencode configuration.

Refer to the [opencode documentation](https://opencode.ai/docs) for configuring skills and plugins.
