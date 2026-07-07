---
name: project-context-starter
description: Use at the start of a new project, when first joining an existing project, or when the user wants clean context management, AGENTS/README/docs layering, long-term memory capture, deduplication/compression rules, durable project-rule intake, and documentation alignment. This skill sets up the project knowledge framework and routes later stage-close cleanup to neat-freak. Do not use for ordinary Q&A, one-off analysis, or unstable mid-debugging work.
---

# Project Context Starter

Use this skill to establish a clean project knowledge system before substantial work begins. Its job is project startup and onboarding, not end-of-session cleanup. For later stage-close synchronization, context compression preparation, stale docs, or multi-document reconciliation, route to `neat-freak`.

## Startup Workflow

1. **Inventory before writing**
   - Identify the project root and list existing root files.
   - Check for `AGENTS.md`, `CLAUDE.md`, `README.md`, `docs/`, `.codex/`, `.agents/`, and equivalent project guidance files.
   - Read existing project guidance before proposing or writing replacements.
   - If the target project root is ambiguous, ask the user to choose before creating files.

2. **Classify the project state**
   - New project: no durable guidance exists, so create a minimal framework.
   - Existing but messy project: consolidate and point to authoritative files instead of duplicating rules.
   - Mature project: preserve current conventions and add only missing boundaries or pointers.

3. **Create or align the knowledge layers**
   - `AGENTS.md` / `CLAUDE.md`: agent-facing rules only. Include hard constraints, commands, permission rules, read-order, memory policy, and red lines. Keep it concise; do not turn it into a changelog.
   - `README.md`: human-facing project entry. Include purpose, how to start, and key document links.
   - `docs/`: project knowledge. Put project context, decisions, progress, runbooks, schemas, integration notes, and long-term experience here.
   - Agent memory: store only durable cross-session facts, stable preferences, project rules, and pointers that cannot safely live only in project docs.

4. **Set the intake policy**
   - Stable project facts, rules, interfaces, environment variables, long-term decisions, and repeated lessons should be added to the right layer.
   - Temporary brainstorming, ordinary Q&A, one-off analysis, unverified claims, and unstable debugging notes should not be persisted.
   - Prefer updating existing docs over adding new files. Prefer a short pointer in `AGENTS.md` to copying detailed docs.
   - Use absolute dates, not "today", "recently", or similar relative time.

5. **Define the `neat-freak` boundary**
   - Run `neat-freak` before context auto-compaction or a new thread if the session created durable facts, rules, interfaces, environment variables, long-term decisions, or multi-document sync needs.
   - Run `neat-freak` at phase close, handoff, stale-doc cleanup, or when docs/memory may have diverged.
   - Do not mechanically trigger `neat-freak` for ordinary questions, single-point analysis, or unfinished debugging.

6. **Output the startup handoff**
   - Summarize which files exist, which were created or should be created, and which file is the authority for each knowledge layer.
   - Give the user a short "next thread prompt" that tells future agents which project files to read first.
   - Call out any permission, sandbox, missing dependency, or unavailable-memory limitation plainly.

## Default File Pattern

When no stronger project convention exists, use this minimal structure:

- `AGENTS.md`: agent rules, read-order, memory policy, permission rules, and `neat-freak` trigger boundary.
- `README.md`: project overview and human entry.
- `docs/project-context.md`: goal, current state, important constraints, and document map.
- `docs/progress.md`: current milestone, completed work, open tasks, and next action.
- `docs/decisions.md`: durable decisions with dates and rationale.

Use fewer files for small projects. Do not create empty docs just to satisfy the pattern.

## Memory Handling

For Codex-style memory:

- Do not edit `MEMORY.md` directly.
- If the user explicitly asks to persist memory, add a small note under `~/.codex/memories/extensions/ad_hoc/notes/` with a timestamped slug.
- Keep memory notes short and tagged as project facts, rules, preferences, or limitations.
- If a fact is needed by every future agent working in the project, prefer putting it in project docs and storing only a memory pointer.

For projects with no writable memory system, write the durable policy into project docs and report that no agent-memory write was performed.

## Permission Rules

If reading or writing project files, global skill directories, memory notes, GUI previews, network resources, or system dependencies is blocked:

- Ask for authorization using the available tool mechanism when possible.
- Otherwise tell the user exactly what was blocked and how they can modify permissions or install dependencies.
- Do not claim setup is complete when a required layer was not created.

## Quality Check

Before finishing, verify:

- The project has a clear first-read file for future agents.
- `AGENTS.md` is concise and not a history log.
- Detailed procedures live in `docs/`, not duplicated across layers.
- Memory policy distinguishes durable facts from transient conversation.
- The `neat-freak` trigger boundary is written down.
- The final response lists created/updated files and any limitations.
