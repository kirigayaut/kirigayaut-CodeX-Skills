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
| [neat-freak.5.6soi时代适配版](./neat-freak/SKILL.md) | Audit and reconcile durable project knowledge. | Run at a milestone, release, formal handoff, or confirmed multi-layer documentation drift. |

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
- `Help me prepare this project so future threads have durable context.`

## neat-freak.5.6soi时代适配版

The user-facing name is `neat-freak.5.6soi时代适配版`; the stable technical ID remains `neat-freak` for compatibility with existing invocations and project references.

This edition treats large context windows, compaction, and Codex Memories as continuity aids rather than project authorities. It defaults to a change-scoped audit and expands to a full project review only for releases, formal handoffs, broad drift, or explicit requests.

Good triggers:

- `Use $neat-freak to reconcile the project docs after this release.`
- `The API and environment variables changed; audit affected rules and docs.`
- `Prepare a verified documentation handoff for the next maintainer.`

Non-triggers:

- Context is merely approaching auto-compaction.
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
