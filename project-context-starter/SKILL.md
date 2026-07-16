---
name: project-context-starter
description: >
  Initialize or repair a project's durable guidance before substantial work.
  Use when starting a new project, first joining an existing repository, or
  when the user asks for a clear AGENTS.md, README.md, and docs source-of-truth
  map, read order, intake policy, or future-task entry flow. Preserve mature
  project conventions and create only missing layers. Do not use for ordinary
  Q&A, temporary debugging, context compaction, or stage-close reconciliation;
  route confirmed multi-file drift to $neat-freak.
---

# Project Context Starter

建立项目启动和接手时的最小知识框架。让未来任务先读对文件、知道每类信息的权威位置，并避免把当前任务、Memories 或 Skills 误当成项目事实库。

本 Skill 只负责建立或修复知识入口。项目规则和检入版本控制的文档是 durable 层；当前任务和 Memories 是上下文层；Skills 是可复用流程层。

## Startup Workflow

### 1. Inventory before writing

- 确认项目根、当前工作目录和工作区状态；目标根目录不明确时先询问。
- 读取当前生效的 `AGENTS.override.md`、`AGENTS.md` 和已配置 fallback，再读取 `README.md` 与文档入口。
- 仅在项目实际使用时检查 `.codex/`、`.agents/skills/`、架构文档、runbook、progress 或 issue tracker。
- 保留用户已有修改，不用模板覆盖成熟项目。

### 2. Classify the project

- 新项目：建立最小可用入口。
- 已有但混乱：指定权威文件，合并重复入口，不复制整段内容。
- 成熟项目：沿用现有命名、目录和文档体系，只补缺失的边界或指针。
- 多项目工作区：先确认工作区规则和项目局部规则的覆盖关系。

### 3. Define the source-of-truth map

为项目实际需要的知识层指定唯一职责：

| 层 | 内容 |
|---|---|
| 适用的 `AGENTS.md` | 必须长期遵守的命令、约束、验收标准和必要读序 |
| `README.md` | 人类入口、项目目的、最短启动路径和关键文档链接 |
| 检入版本控制的 `docs/` | 架构、接口、运行手册、决策和可维护的长期经验 |
| progress 或 issue tracker | 当前里程碑、开放项和下一步 |
| 当前任务 | 临时推测、探索日志和未稳定调试信息 |
| Memories | 可选的跨任务召回，不承担必须执行规则的唯一副本 |
| Skills | 可复用工作流，不承担项目现行事实的唯一副本 |

不要为了形式完整而创建所有层。先服从项目现有约定。

### 4. Create the minimum viable framework

按项目规模选择：

- 小型项目：通常只需要简洁的 `AGENTS.md` 和 `README.md`。
- 持续迭代项目：按需增加项目上下文和 progress 文档。
- 复杂或多人项目：仅在确有维护责任时增加 decisions、architecture、runbook 或 integration 文档。
- 项目专属的重复流程：仅在多次任务都会复用时考虑 `.agents/skills/`，不要把一次性说明包装成 Skill。

遵守以下写入原则：

- 优先更新现有文件，不创建平行真相。
- 规则文件只保留未来任务必须看到的内容，不写 changelog。
- 详细过程放入 `docs/`，规则文件只留必要短指针。
- 不创建空文档、占位目录或没有维护责任的模板。
- 使用绝对日期记录决定和状态，不机械改写历史文字。

### 5. Set the intake and continuity policy

把后续变化分成三级：

1. 单点 durable 更新：直接修改对应权威文件。
2. 轻量 checkpoint：只更新 progress 或生成简短任务交接。
3. 重型 reconcile：阶段结束、发布、正式交接，或多个知识层确认漂移时调用 `$neat-freak`。

自动压缩、在支持界面手动 `/compact`、新开任务或上下文变长本身不触发 `$neat-freak`。未完成调试、普通问答和一次性分析不持久化。

### 6. Output the startup handoff

交付以下内容：

- 实际读取、创建或更新的文件。
- 每类知识的权威文件和未来任务的第一读序。
- 哪些候选层因项目规模不需要创建。
- 一条可直接用于未来任务的简短启动提示词。
- 未能读取的权威文件、权限限制或当前 Memory 能力边界。

## Default File Pattern

仅在没有更强项目约定时参考：

- `AGENTS.md`：Agent 规则、必要读序和验收标准。
- `README.md`：项目概览、人类入口和关键链接。
- 项目上下文文档：目标、当前状态、重要约束和文档地图。
- progress 文档：当前里程碑、开放项和下一步。
- ADR 或 decisions 文档：已确认的长期决定和理由。

小项目使用更少文件；没有内容就不要创建。

## Memory Boundary

- 使用产品提供的 `/memories` 或设置控制 Memory 使用和生成；本 Skill 不改变该设置。
- 不直接编辑 Codex 生成式 Memory 文件。
- 必须可靠生效的项目规则放在 `AGENTS.md`，团队和项目事实放在检入版本控制的文档。
- 用户明确要求持久化 Memory 时，只使用当前环境提供的受支持机制；没有该机制时明确报告未写入。

## Quality Check

完成前验证：

- 未来任务有明确的第一读文件和读序。
- 每类知识只有一个主权威位置。
- `AGENTS.md` 简短、具体且不是历史日志。
- 详细过程位于对应文档，没有跨层全文复制。
- Memories、Skills、当前任务和项目文档的边界清楚。
- `$neat-freak` 只在确认存在阶段性或多文件对齐需求时触发。
- 最终结果列出实际修改、未创建项和限制。
