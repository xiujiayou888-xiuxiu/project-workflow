# Parallel Agent Orchestration

Use this only when the project has already passed requirements confirmation and the architecture baseline. It governs same-model or mixed-model workers without losing the path-first, one-step-at-a-time project workflow.

## Capability Check

First record one actual execution engine in `docs/18-并行协作计划.md`:

| Engine | Use When | User Operation | Limitation |
| --- | --- | --- | --- |
| GPT-5.6 `ultra` automatic orchestration | the tool scan confirms `ultra` and user approves the added cost | send one master prompt to the selected `ultra` task | internal worker details may be abstracted by the platform; coordinator still verifies artifacts |
| Codex subagents/worktrees | the app can start independent tasks with isolated worktrees | coordinator creates worker tasks from `PAR-*` packets | only isolated code cards may run in parallel |
| Separate sessions of the same AI | the user can open multiple independent chats/agents | copy one prepared packet to each named session | user relays worker results to the coordinator |
| Sequential fallback | none of the above is available | coordinator runs the planned lanes one at a time | do not call it parallel |

Do not assume a model supports automatic parallelism because it has high reasoning. Confirm the available mode in the tool scan.

If the tool scan cannot read the current model setting or entitlement, ask the user one direct question: “你的模型选择里是否看得到 GPT-5.6 `ultra`？” Until confirmed, use Codex worktrees, separate sessions, or sequential fallback; never claim automatic orchestration is active.

## User Controls

| User Says | Coordinator Does |
| --- | --- |
| `自动判断并行` | use single-thread by default; enable parallel only after the eligibility gate |
| `强制单线` | use no workers, even if `ultra` is available |
| `优先省钱` | avoid `ultra`; use a small number of normal/high-reasoning workers only when a high-risk review justifies it |
| `使用 ultra` | confirm visible availability, explain added cost, then request approval before sending the master prompt |

## When To Use It

Enable parallel work only when all are true:

1. The PRD and architecture gate are approved.
2. At least two outputs have no shared code, data schema, API contract, or decision dependency.
3. Every worker has an exclusive write scope and target path.
4. The coordinator has time and budget to review and integrate every result.
5. The user approves any higher token, cloud, or tool cost.

Stay sequential for beginner/Demo work, a single core feature, database migrations, shared authentication, shared API contracts, deployment, production incidents, or any uncertain requirement.

## Parallel Waves

Do not make tools wait once a safe wave exists. The coordinator must first complete the shared foundation and freeze contracts, then dispatch every eligible independent `PAR-*` task in that wave at the same time.

Use this order:

1. **Wave 0 - shared foundation, sequential:** requirements, architecture, database/auth/API contracts, routing, shared types, environment/config, design system, and task boundaries.
2. **Wave 1+ - isolated feature work, parallel:** only cards with exclusive write scopes and fixed inputs/outputs. Assign each to the most suitable detected tool/agent.
3. **Wave merge - coordinator-led:** verify every return, merge one at a time, run affected tests after each merge, and test the connected user journey.
4. **Next wave - dependent work:** release only the cards whose required inputs are now verified.
5. **Final wave - integration/review:** integration fixes and independent review can run in parallel only if they do not edit the same files; production changes remain sequential.

Request one approval for the whole wave, not one approval per worker. The user-facing proposal must show a short table: task name, selected concrete tool, output path, completion signal, and cost note. Keep locks and detailed prompts in `docs/18-并行协作计划.md` unless the user asks to expand them.

Never parallelize merely to occupy tools. A task that shares database schema, auth, routing, public API/types, environment config, a component interface, or the same files must wait for the coordinator's sequential decision.

## Shared Contract Freeze

Before any parallel implementation, the coordinator freezes and owns these shared contracts:

- database schema, migrations, and seed data
- authentication, permissions, and session behavior
- shared types and public API request/response contracts
- public UI component interfaces and routing
- environment variable names and deployment configuration

Workers may read the contracts but cannot change them. A worker that discovers a required change records it as `CONTRACT-CHANGE-*` in its result; the coordinator decides it sequentially, updates the canonical contract, and only then starts affected work.

## Roles And Write Ownership

| Role | Can Write | Must Not Write |
| --- | --- | --- |
| Coordinator | canonical project state, paths, decisions, execution plan, traceability, integration, review, final docs | worker-owned implementation files while a lock is active |
| Planning worker | assigned `docs/并行任务/PAR-*.md` only | canonical docs and code |
| Review worker | assigned review file only | source code and canonical docs |
| Implementation worker | assigned files/folders or dedicated branch/worktree | state, paths, decisions, execution plan, traceability, integration, review docs, another worker's scope |

Only the coordinator may mark a `PAR-*` task accepted, update project progress, or release a merge to the main branch.

## Worker Delivery Locations

Before dispatching a worker, create this file in the canonical project root:

`PROJECT_ROOT/docs/并行任务/PAR-XXX-任务与交付.md`

It is the worker's delivery record. Every worker must write or return content for this exact path. The coordinator does not rely on chat history to integrate work.

Use this structure:

```markdown
# PAR-XXX - 任务与交付

- 波次：Wave N
- 卡片：CARD-XXX
- 任务目标：
- 执行工具/Agent：
- 分支或工作区：
- 允许修改：
- 禁止修改：
- 输入路径：
- 代码/文件产物路径：
- 预览、测试或命令证据路径：
- 依赖的契约版本：
- 下游消费者/总装步骤：
- 状态：待批准 / 执行中 / 待验证 / 已验证 / 阻塞

## 实际交付
- 做了什么：
- 修改/生成文件：
- Git 分支与提交：
- 测试或预览证据：
- 已知限制/阻塞：
- 建议总装顺序：

## 交接给总控
- 是否符合输入/输出契约：
- 是否需要 CONTRACT-CHANGE：
- 总控验收结论：
```

For code, use one of these delivery modes, in this priority order:

1. **Dedicated Git branch/worktree:** worker changes code only in its branch/worktree; it saves the delivery record in the canonical project docs path or returns its exact content. Coordinator checks and merges the commit.
2. **Exclusive folder/file scope:** when worktrees are unavailable, the worker edits only its assigned files in the shared root and writes the delivery record. Coordinator checks the diff before accepting it.
3. **No write access:** worker returns `目标绝对路径 + 完整文件内容 + changed-file list + verification`; coordinator writes the files in the canonical root and records that it performed the application.

Do not put finished code into an arbitrary desktop folder, an agent-private workspace, or an untracked chat attachment. Every code result must be reachable from the project path index through its branch/worktree or declared output paths.

## Required Plan

Create `PROJECT_ROOT/docs/18-并行协作计划.md` before starting workers:

```markdown
# 并行协作计划

- 项目：
- 执行引擎：GPT-5.6 ultra / Codex worktrees / separate sessions / sequential fallback
- 协调者：
- 预算与成本上限：
- 当前架构版本：
- PRD/追踪矩阵：
- 启动批准：
- 每个任务最大轮次/超时：

## 并行判断
- 为什么可以并行：
- 不能并行的项目：
- 合并门禁：

## 任务表
| PAR-ID | 目标 | Agent/会话 | 推理强度 | 只读输入 | 允许写入 | 禁止写入 | 分支/工作区 | 产物绝对路径 | 依赖 | 完成标志 | 最大轮次/超时 | 成本上限 | 失败后接手者 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## 启动顺序与汇总顺序
1. 
```

Add a `波次` column to the task table and group dispatches by that wave. A wave cannot be marked complete until its worker evidence, coordinator reviews, merge checks, and connected-flow test are recorded.

For every `PAR-*`, use the standard cross-agent handoff packet plus these additions:

- engine and worker identity
- no-shared-write rule
- exclusive files/folders or branch/worktree
- upstream dependency and downstream consumer
- `docs/18-并行协作计划.md` as an input
- target section in `docs/19-并行结果汇总.md`
- maximum rounds/time, cost ceiling, stop condition, and fallback owner

## GPT-5.6 Ultra Master Prompt

When the scan confirms GPT-5.6 `ultra`, give the user one prompt like this. Replace every bracket with actual paths and approved task details.

```text
请使用可用的多 Agent 并行能力执行本次“并行规划/审查”，但由你作为协调者统一汇总，不要让并行工作扩大项目范围。

先读取：
1. [项目路径索引绝对路径]
2. [项目状态绝对路径]
3. [PRD绝对路径]
4. [技术架构绝对路径]
5. [并行协作计划绝对路径]

本次只允许并行完成计划中列出的 PAR-001 到 PAR-00N。每个工作流只能写入自己的指定产物路径，不得修改项目状态、路径索引、执行清单、决策记录、需求追踪、总装或最终审查文档。

完成后，由协调者：
1. 检查每个 PAR 的产物和验收证据。
2. 识别冲突、重叠和未解决问题。
3. 把汇总写入：[PROJECT_ROOT/docs/19-并行结果汇总.md]。
4. 不要开始下一阶段，等待我确认汇总结果。
```

## Merge And Acceptance

Before the next phase, the coordinator creates `PROJECT_ROOT/docs/19-并行结果汇总.md`:

```markdown
# 并行结果汇总

| PAR-ID | 实际产物路径 | 验收证据 | 状态 | 冲突/缺口 | 协调者决定 |
| --- | --- | --- | --- | --- |

## 合并检查
- 已验证的共同输入：
- 需求编号与架构决策对照：
- API/共享类型/数据库契约差异：
- 实际 Git diff 是否只在允许范围：
- 重叠修改：
- 未解决风险：
- 需要顺序处理的后续工作：
- 是否批准进入下一阶段：
```

For parallel code, integrate one worker result at a time. First compare the worker's `REQ-*`, `ADR-*`, shared contracts, changed-file scope, and Git diff to the approved `PAR-*` row. Run the affected tests after each merge, then run the full critical journey before declaring the combined result ready. A worker's self-report is not acceptance evidence.

## Coordinator Assembly Contract

After a wave returns, the coordinator must assemble from saved artifacts, not memory:

1. Read every `docs/并行任务/PAR-XXX-任务与交付.md` in the wave.
2. Confirm each declared branch/worktree, output path, commit, test/preview evidence, and contract version.
3. Reject any delivery that has no saved record, writes outside scope, lacks evidence, or requires an unapproved contract change.
4. Merge verified branches one at a time, or apply verified exclusive-scope changes one at a time.
5. Update `docs/19-并行结果汇总.md` with actual accepted paths/commits and conflicts.
6. Run the connected user journey and write the complete integration checklist, unresolved gaps, and evidence to `docs/08-总装集成.md`.
7. Only then mark the wave integrated and release dependent tasks.

The user-facing summary can simply say “第 N 波已总装完成”; the detailed merge history remains in the listed documents for any later AI to read.

## Timeout And Downgrade

Stop a worker immediately when it exceeds its planned round/time limit, crosses its cost ceiling, changes forbidden scope, cannot produce required evidence, or discovers an unresolved shared-contract change. Mark the task `Blocked` in the result summary. The coordinator then either assigns one narrowly scoped retry or completes the same task sequentially. Do not leave a timed-out worker as an invisible background dependency.
