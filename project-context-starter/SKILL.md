---
name: project-context-starter
description: >
  Initialize or repair a project's durable knowledge architecture before
  substantial work. Use when starting a new project, first joining an existing
  repository, or when the user asks for a clear AGENTS/README/docs source of
  truth, read order, intake policy, or future-task handoff. Preserve mature
  project conventions and create only missing layers. Do not use for ordinary
  Q&A, one-off analysis, temporary debugging, context auto-compaction, or
  stage-close reconciliation; route confirmed multi-layer drift to neat-freak.
---

# Project Context Starter

建立项目启动和接手时的最小知识框架。让未来任务先读对文件、知道每类信息的权威位置，并避免把大上下文或 Agent Memories 误当成项目文档。

本 Skill 负责启动和修复入口，不负责阶段收尾审计。项目文件是权威层；任务上下文和 Memories 是辅助层。

## Startup Workflow

### 1. Inventory before writing

- 确认项目根和当前工作目录；目标根目录不明确时先询问。
- 列出根文件和文档目录，检查 `AGENTS.override.md`、`AGENTS.md`、`CLAUDE.md`、`README.md`、`docs/`、`.codex/`、`.agents/` 及项目声明的等价文件。
- 读取当前生效的规则链和现有文档入口，再决定是否需要修改。
- 检查工作区状态，保留用户已有修改，不用模板覆盖成熟项目。

### 2. Classify the project

- 新项目：建立最小可用入口。
- 已有但混乱：指定权威文件，合并重复入口，不复制整段内容。
- 成熟项目：沿用现有命名、目录和文档体系，只补缺失的边界或指针。
- 多项目工作区：先确定当前项目与工作区规则的覆盖关系，再添加项目局部说明。

### 3. Define the source-of-truth map

为项目实际存在的知识层指定唯一职责：

| 层 | 内容 |
|---|---|
| `AGENTS.md` / `CLAUDE.md` | Agent 必须遵守的长期规则、命令、权限边界、验证标准和第一读序 |
| `README.md` | 人类入口、项目目的、最短启动路径和关键文档链接 |
| `docs/` | 架构、接口、运行手册、决策、项目上下文和可维护的长期经验 |
| progress / issue tracker | 当前里程碑、已完成项、开放项和下一步 |
| 当前任务 | 临时推测、探索日志和未稳定调试信息 |
| Agent Memories | 可选的辅助回忆，不承担必须执行规则的唯一副本 |

不要为了形式完整而同时创建所有层。先服从项目现有约定。

### 4. Create the minimum viable framework

按项目规模选择：

- 小型项目：通常只需要简洁的 `AGENTS.md` 和 `README.md`。
- 持续迭代项目：按需增加 `docs/project-context.md` 和 progress 文档。
- 复杂或多人项目：仅在确有维护责任时增加 decisions、architecture、runbook、integration 等文档。

遵守以下写入原则：

- 优先更新现有文件，不创建平行真相。
- 规则文件只保留下一次 Agent 必须看到的内容，不写 changelog。
- 详细过程放入 `docs/`，规则文件只留必要短指针。
- 不创建空文档、占位目录或没有维护者的模板。
- 使用绝对日期记录决定和状态，不把所有历史文字机械改写。

### 5. Set the intake and continuity policy

把后续变化分成三级：

1. 单点 durable 更新：直接修改对应权威文件。
2. 轻量 checkpoint：只更新 progress 文档或生成简短任务交接，不启动全项目审计。
3. 重型 reconcile：当阶段结束、发布、正式交接，或多个知识层已确认漂移时调用 `$neat-freak`。

自动压缩、新开任务或上下文变长本身不触发 `$neat-freak`。未完成调试、普通问答和一次性分析不持久化。

### 6. Output the startup handoff

交付以下内容：

- 实际读取、创建或更新的文件。
- 每类知识的权威文件和第一读序。
- 哪些候选文件因项目规模不需要创建。
- 一条可直接用于未来任务的启动提示词。
- 权限、sandbox、依赖或 Memory 能力限制。

## Default File Pattern

仅在没有更强项目约定时参考以下结构：

- `AGENTS.md`：Agent 规则、读序、权限和验收标准。
- `README.md`：项目概览和人类入口。
- `docs/project-context.md`：目标、当前状态、重要约束和文档地图。
- `docs/progress.md`：当前里程碑、开放项和下一步。
- `docs/decisions.md` 或 ADR：已确认的长期决定和理由。

小项目使用更少文件。没有内容就不要创建。

## Memory Handling

在 Codex 中：

- 把本地 Memories 视为后台生成的辅助回忆，不直接编辑其生成文件。
- 把必须生效的项目规则放在项目规则文件，把团队和项目事实放在检入版本控制的文档。
- 只有用户明确要求持久化 Memory，且当前运行环境提供受支持更新机制时才写入。
- 不把特定会话内部的 Memory 路径固化成跨平台 Skill 契约。

没有可写 Memory 系统时，完成项目文件框架并明确报告未执行 Memory 写入。

## Permission Rules

如果读取或写入项目文件、全局 Skill、Memory、GUI、网络或依赖被阻止：

- 使用当前工具的授权机制请求最小必要权限。
- 无法请求时，准确说明受阻对象和恢复方法。
- 必要层未建立时，不声称启动框架已经完成。

## Quality Check

完成前验证：

- 未来 Agent 有明确的第一读文件和读序。
- 每类知识只有一个主权威位置。
- `AGENTS.md` / `CLAUDE.md` 简洁且不是历史日志。
- 详细过程位于 `docs/`，没有跨层全文复制。
- Memory、任务上下文和项目文档的边界清楚。
- `$neat-freak` 只在多层漂移或阶段性审计时触发。
- 最终结果列出实际修改、未创建项及限制。
