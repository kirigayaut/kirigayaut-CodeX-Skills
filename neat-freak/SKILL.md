---
name: neat-freak
description: >
  Audit and reconcile durable project knowledge after a milestone, release,
  handoff, or confirmed documentation drift. Compare code, configuration, and
  actual workflows with AGENTS.md or CLAUDE.md, README.md, and affected docs;
  merge duplicates, remove stale guidance, and report unresolved conflicts.
  Use when multiple durable knowledge layers may have diverged, when the user
  explicitly invokes $neat-freak or /neat, or asks for a stage-close rules and
  documentation audit. Do not trigger merely because context is long or
  auto-compaction is near, for ordinary Q&A, one-file edits, temporary
  debugging, or a simple progress checkpoint. Codex 5.6-first with safe
  cross-platform fallbacks.
---

# neat-freak.5.6soi时代适配版

把本 Skill 当作低频的项目知识一致性审计器，不要把它当作上下文压缩器、会话摘要器、变更日志生成器或 Codex Memory 编辑器。

大上下文、自动压缩和 Memories 负责帮助任务继续；本 Skill 负责让未来任务和人类读者拿到可信、精简、可验证的项目知识。

## 核心边界

按以下优先级判断权威层：

| 层 | 职责 | 处理原则 |
|---|---|---|
| 代码、配置、测试、可观察行为 | 当前实际状态 | 用来核验文档事实；若实现与已确认设计冲突，不要擅自宣布任一方为准 |
| `AGENTS.md` / `CLAUDE.md` | Agent 必须遵守的项目规则 | 只放长期有效的约束、命令、红线和读序，不写历史叙事 |
| `README.md` / `docs/` | 人类和未来 Agent 的项目知识 | 维护架构、接入、运维、决策和使用说明 |
| progress / changelog / git history | 当前进度和历史事件 | 不回填到规则文件 |
| Agent Memories | 辅助回忆 | 不作为必须执行规则或项目事实的唯一来源 |

坚持以下不变量：

- 项目文件是项目知识的权威层。
- 上下文即将自动压缩，本身不是触发条件。
- 单点事实只更新其权威文件，不启动全套审计。
- 生成式 Memories 可以辅助发现线索，但不能替代代码和项目文档核验。
- 不强制 `AGENTS.md` 与 `CLAUDE.md` 使用某种固定同源方式；先服从项目现有约定。

## 选择审计范围

默认执行 `delta` 范围：

1. 读取项目规则链和文档入口。
2. 用本轮对话、`git status`、`git diff`、提交记录或用户点名的改动确定影响面。
3. 只读取和修改受影响的权威文档及其直接引用。

仅在以下情况扩大为 `full` 范围：

- 用户明确要求全项目审计。
- 准备正式发布、移交或归档，且多个知识层长期未维护。
- 已发现广泛的死链接、重复规则或相互冲突的文档。
- 项目根规则、文档结构或跨项目协议发生变化。

跨项目扫描只覆盖有证据的直接依赖方。不要因为目录相邻就扫描所有项目。

## 执行流程

### 1. 建立事实基线

- 确认项目根、当前分支、工作区状态和权限边界。
- 读取适用的 `AGENTS.override.md`、`AGENTS.md`、`CLAUDE.md`、`README.md` 和文档索引。
- 保留用户未提交的修改；遇到重叠编辑时先理解再合并。
- 核对规则文件声明的权威来源、读序和覆盖关系，不自行发明新的层级。
- 对照真实代码、配置、测试或可观察行为验证路径、命令、接口、环境变量和状态。

### 2. 建立变更影响表

把候选信息分到唯一主层：

- Agent 每次都必须遵守，否则容易犯错 -> 规则文件。
- 人类或未来接手者需要理解、接入或运维 -> `README.md` 或 `docs/`。
- 只是里程碑状态、完成项或下一步 -> progress、changelog 或 git history。
- 尚未验证、仍在调试或一次性上下文 -> 不持久化。
- 跨项目个人偏好 -> 仅在用户明确要求且平台提供受支持写入方式时进入 Memory。

遇到 API、环境变量、数据模型、部署、退役或跨项目协议变化时，读取 [references/sync-matrix.md](references/sync-matrix.md)。

### 3. 对齐项目知识

- 先修改面向人的 `docs/` 和 `README.md`，再修改 Agent 规则文件。
- 更新既有条目，避免在文件顶部不断追加本轮故事。
- 合并重复事实；删除已被当前权威内容取代的活跃说明。
- 保留真正的历史记录，但把它放在 changelog、ADR 或 git history，而不是规则文件。
- 只创建确有受众和维护责任的新文档，不创建空壳文件。
- 对无法判断的实现与设计冲突，保留原状并列出证据与待决问题。

### 4. 安全处理 Memories

平台记忆边界不明确时，读取 [references/agent-paths.md](references/agent-paths.md)。

在 Codex 中：

- 把 `$CODEX_HOME/memories/` 视为生成式辅助状态；不要直接编辑、压缩、删除或重排其中的生成文件。
- 把必须始终生效的规则写入适用的 `AGENTS.md`，把项目事实写入已检入版本控制的文档。
- 仅在用户明确要求持久化 Memory 时，使用当前运行环境提供的受支持更新机制；若没有该机制，明确报告未写入。

在其他平台中：

- 先确认平台文档和实际可用工具，再决定 Memory 是否可写。
- 未确认写入语义时保持只读，不套用 Codex 或 Claude Code 的内部路径和尺寸限制。

所谓知识“毕业”，是把稳定且应共享的事实提升到项目文档；不要求删除生成式历史记录。

### 5. 验证

- 检查所有修改后的路径、命令、链接和引用是否真实存在。
- 搜索同一事实是否仍有互相冲突的活跃版本。
- 检查 `AGENTS.md` / `CLAUDE.md` 没有变成 changelog，且新增内容确实是长期规则。
- 检查日期使用绝对日期；历史文字中的相对时间不做无意义机械替换。
- 检查 `git diff` 只包含本次授权范围内的变更。
- 运行项目已有的文档校验、链接检查或相关测试；无法运行时说明原因。
- 不因“文档更整齐”擅自删除文件、重命名目录、改远程、改部署或改外部系统。

## 输出格式

只报告实际变化和需要决策的事项：

```text
同步完成

项目知识
- 更新：<文件> - <对齐了什么>
- 删除：<文件或条目> - <为何已过期>

规则审计
- 修复：<可安全修复的问题>
- 待确认：<冲突、证据和建议>

Memory
- 未直接修改 Codex 生成式 Memories
- <仅在确有受支持写入时列出实际动作>

验证
- <执行的检查及结果>
```

没有变化时直接说明“审计完成，未发现需要修改的漂移”，不要制造文件改动来证明 Skill 被运行过。

## 停止条件

在以下情况停止修改并向用户报告：

- 两个权威来源互相冲突，且无法从代码、测试或明确决策判断现行版本。
- 修复需要删除、重命名、迁移或修改外部系统，而用户没有授权。
- 目标项目、依赖项目或全局配置不在可访问范围内。
- 现有工作区修改与本次任务重叠，无法在不覆盖用户工作的情况下继续。
