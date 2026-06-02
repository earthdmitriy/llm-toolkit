# llm-toolkit

A collection of reusable skills, plugins, hooks, and tools for LLM-powered coding agents — primarily targeting [opencode](https://opencode.ai).

## Structure

```
.opencode/
├── skills/          # OpenCode skills (reusable agent directives)
│   └── spec-architect/  # Converts feature prompts into production-grade spec.md files
└── plugins/         # OpenCode plugins (TypeScript/Node)
```

## Contents

| Artifact | Description |
|----------|-------------|
| **spec-architect** | A discovery-driven opencode skill that deconstructs ambiguous feature requests into explicit, production-grade specification documents. Walks through environment audit, blast radius analysis, dependency mapping, data contracts, system mechanics, and testing strategy. |

## Usage

Skills live under `.opencode/skills/` and are loaded by the LLM agent when the task matches the skill description. Plugins live under `.opencode/plugins/` and are registered in the opencode configuration.

Refer to the [opencode documentation](https://opencode.ai/docs) for configuring skills and plugins.
