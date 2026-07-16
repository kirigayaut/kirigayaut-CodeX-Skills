<div align="center">

# kirigayaut CodeX Skills

Personal Agent Skills for clean project context, memory hygiene, and reusable Codex workflows.

[![Skills](https://img.shields.io/badge/Skills-2-10B981?style=for-the-badge)](#skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](./LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-8B5CF6?style=for-the-badge)](https://agentskills.io)

</div>

## Skills

| Skill | Purpose | When to use |
| --- | --- | --- |
| [project-context-starter](./project-context-starter/SKILL.md) | Establish the minimum source-of-truth map for a project. | Start or join a project, repair its entry flow, or define AGENTS/README/docs boundaries. |
| [Neat Freak](./neat-freak/SKILL.md) | Audit and reconcile durable project guidance. | Run at a milestone, release, formal handoff, or confirmed multi-file documentation drift. |

## Install

Ask your Agent Skills-compatible coding agent to install either skill:

```text
https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/project-context-starter
https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/neat-freak
```

Example prompt:

```text
Install these skills:
https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/project-context-starter
https://github.com/kirigayaut/kirigayaut-CodeX-Skills/tree/main/neat-freak
```

## project-context-starter

`project-context-starter` is a startup and onboarding skill. It reads existing guidance first, defines one authority for each knowledge layer, creates only missing files, and separates project docs from task context and optional Memories.

Good triggers:

- `Use $project-context-starter to set up clean project context for this project.`
- `Start this repo with clean AGENTS/docs/memory rules.`
- `Help me prepare this project so future tasks have durable context.`

## Neat Freak

The stable technical ID and invocation remain `neat-freak` and `$neat-freak`.

The skill is maintained against current Codex behavior instead of carrying a model-version suffix. It treats task compaction and Memories as context aids rather than project authorities, defaults to a change-scoped audit, and expands only for releases, formal handoffs, broad drift, or explicit requests.

Good triggers:

- `Use $neat-freak to reconcile the project docs after this release.`
- `The API and environment variables changed; audit affected rules and docs.`
- `Prepare a verified documentation handoff for the next maintainer.`

Non-triggers:

- Context is merely approaching automatic compaction.
- Ordinary Q&A or unfinished debugging.
- A one-file typo or simple progress checkpoint.

## Repository Layout

```text
project-context-starter/
  SKILL.md
  agents/
    openai.yaml
neat-freak/
  SKILL.md
  LICENSE
  agents/
    openai.yaml
  references/
    agent-paths.md
    sync-matrix.md
```

## License

MIT

`neat-freak` is adapted from [KKKKhazix/khazix-skills](https://github.com/KKKKhazix/khazix-skills) under the MIT License. The upstream copyright notice is preserved in `neat-freak/LICENSE`.
