<div align="center">

# kirigayaut CodeX Skills

Personal Agent Skills for clean project context, memory hygiene, and reusable Codex workflows.

[![Skills](https://img.shields.io/badge/Skills-1-10B981?style=for-the-badge)](#skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](./LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-8B5CF6?style=for-the-badge)](https://agentskills.io)

</div>

## Skills

| Skill | Purpose | When to use |
| --- | --- | --- |
| [project-context-starter](./project-context-starter/SKILL.md) | Set up clean project context, documentation layers, and long-term memory rules. | Use at the start of a new project, when joining an existing project, or when a workspace needs clear AGENTS/README/docs/memory boundaries. |

## Install

Ask your Agent Skills-compatible coding agent to install:

```text
https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/project-context-starter
```

Example prompt:

```text
Install this skill: https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/project-context-starter
```

## project-context-starter

`project-context-starter` is a startup and onboarding skill. It inventories a project, reads existing guidance first, separates agent rules from human docs, defines what should enter durable memory, and sets the boundary for when later cleanup should route to `neat-freak`.

Good triggers:

- `Use $project-context-starter to set up clean project context for this project.`
- `Start this repo with clean AGENTS/docs/memory rules.`
- `Help me prepare this project so future threads have durable context.`

## Repository Layout

```text
project-context-starter/
  SKILL.md
  agents/
    openai.yaml
```

## License

MIT
