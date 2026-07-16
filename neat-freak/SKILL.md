---
name: neat-freak
description: >
  Audit and reconcile durable project guidance and checked-in documentation
  after a milestone, release, formal handoff, or confirmed multi-file drift.
  Compare current code, configuration, tests, and workflows with applicable
  AGENTS.md guidance, README.md, and affected docs; update stale instructions,
  remove active duplication, and report unresolved conflicts. Use for
  stage-close knowledge hygiene or an explicit $neat-freak invocation. Do not
  use for context compaction, ordinary Q&A, unfinished debugging, one-file
  edits, or routine progress updates.
---

# Neat Freak

把本 Skill 当作低频的项目知识一致性审计器。不要把它当作上下文压缩器、会话摘要器或 Codex Memories 编辑器。

当前任务的上下文由 Codex 的任务记录和压缩机制处理；Memories 提供可选的跨任务召回；项目规则与检入版本控制的文档承担必须长期可用的知识。使用本 Skill 对齐最后一层。

## 核心边界

按以下职责判断权威位置：

| 层 | 职责 | 处理原则 |
|---|---|---|
| 代码、配置、测试、可观察行为 | 当前实现证据 | 用来核验文档事实；与已确认设计冲突时停止并报告 |
| 适用的 `AGENTS.override.md`、`AGENTS.md` 或已配置 fallback | Agent 必须遵守的项目指导 | 只保留长期规则、命令、验收标准和必要读序 |
| `README.md` 与检入版本控制的 `docs/` | 人类和未来任务使用的项目知识 | 维护架构、接口、接入、运维和决策说明 |
| progress 文档或 issue tracker | 当前里程碑、开放项和下一步 | 不回填到规则文件 |
| changelog 与 git history | 历史记录 | 保留准确历史，不当作当前操作说明 |
| Memories | 可选召回层 | 不作为必须执行规则或项目事实的唯一来源 |

坚持以下不变量：

- 自动压缩、在支持界面手动 `/compact` 或新开任务本身不触发本 Skill。
- 单点事实只更新对应权威文件，不升级为全项目审计。
- 项目文件优先于对生成式 Memory 的手工整理。
- 只有重复出现且必须每次遵守的指导才进入 `AGENTS.md`。
- 不把未配置的其他平台规则文件默认视为 Codex 指令源。

## 选择审计范围

默认执行 `delta` 范围：

1. 读取当前生效的项目规则链和文档入口。
2. 用用户点名的改动、当前任务、`git status`、`git diff` 或提交范围确定影响面。
3. 只读取和修改受影响的权威文件及其直接引用。

仅在以下情况扩大为 `full` 范围：

- 用户明确要求全项目审计。
- 准备正式发布、移交或归档，且多个知识层长期未维护。
- 已发现广泛的死链接、重复规则或互相冲突的活跃文档。
- 项目根规则、文档结构或跨项目协议发生变化。

跨项目扫描只覆盖有证据的直接依赖方。

## 执行流程

### 1. 建立事实基线

- 确认项目根、当前分支、工作区状态和权限边界。
- 读取适用的规则链、`README.md`、文档索引和任务直接涉及的文档。
- 保留用户未提交的修改；遇到重叠编辑时先理解再合并。
- 对照代码、配置、测试或可观察行为验证路径、命令、接口、环境变量和状态。

### 2. 路由候选信息

- 每次都必须遵守，否则会反复出错 -> 适用的 `AGENTS.md`。
- 人类或未来任务需要理解、接入或运维 -> `README.md` 或对应 `docs/`。
- 只是当前里程碑、完成项或下一步 -> progress 文档或 issue tracker。
- 是发布或退役历史 -> changelog 或 git history。
- 尚未验证、仍在调试或一次性 -> 留在当前任务，不持久化。
- 是可复用流程而非项目事实 -> 考虑独立 Skill，不塞进规则或 Memory。

当 durable 变化涉及多个知识层或影响范围不明确时，读取 [references/sync-matrix.md](references/sync-matrix.md)。

### 3. 对齐项目知识

- 优先更新现有权威条目，不创建平行真相。
- 合并重复的活跃说明，删除已被当前权威内容取代的操作指导。
- 保留真正的历史记录，但不要把历史叙事写进规则文件。
- 只创建有明确受众和维护责任的新文档，不创建空壳文件。
- 无法判断实现与设计谁应为准时，保留原状并列出证据和待决问题。

### 4. 遵守 Memory 边界

任务涉及 Memories、Skill 发现位置或规则加载链时，读取 [references/agent-paths.md](references/agent-paths.md)。

- 不直接编辑、压缩、删除或重排 `$CODEX_HOME/memories/` 下的生成文件。
- 不擅自修改当前任务的 `/memories` 使用或生成设置。
- 用户明确要求持久化 Memory 时，只使用当前运行环境提供的受支持机制。
- 没有受支持写入机制时，把 durable 内容写入正确的项目文件，并明确报告未写入 Memory。

### 5. 验证

- 检查修改后的路径、命令、链接和引用是否真实存在。
- 搜索同一事实是否仍有互相冲突的活跃版本。
- 检查规则文件没有变成 changelog，且新增内容确实需要长期生效。
- 检查 `git diff` 只包含本次授权范围内的变更。
- 运行项目已有的文档校验、链接检查或相关测试；无法运行时说明原因。
- 不因“文档更整齐”擅自删除文件、重命名目录、改远程、改部署或改外部系统。

## 输出

只报告实际变化、验证结果和需要决策的冲突。没有变化时直接说明“审计完成，未发现需要修改的漂移”，不要制造改动来证明 Skill 已运行。

若任务涉及 Memory，额外说明使用了哪种受支持机制，或明确说明未修改生成式 Memories。

## 停止条件

停止修改并报告以下情况：

- 两个权威来源互相冲突，且无法从代码、测试或明确决策判断现行版本。
- 修复需要删除、重命名、迁移或修改外部系统，而用户没有授权。
- 目标项目或直接依赖项目不在可访问范围内。
- 现有工作区修改与本次任务重叠，无法在不覆盖用户工作的情况下继续。
