# Tool Dispatch Execution

## Purpose

Make every tool recommendation actionable and auditable. A role is a planning label; a selected tool is an execution commitment.

## Dispatch States

Use exactly one state per `TOOL-*` task:

| State | Meaning | May Advance? |
| --- | --- | --- |
| `待选择` | tool scan has not chosen a concrete tool | no |
| `待批准` | tool, input, scope, output, and cost are ready | no |
| `执行中` | current agent is performing the approved task | no |
| `已派发` | another AI/person/tool received the handoff packet | no |
| `工具阻塞` | selected tool cannot be used; fallback or user action is needed | no |
| `待验证` | an output was reported but evidence is not checked | no |
| `已验证` | output path and acceptance evidence are checked | yes |

Never call a task complete merely because a prompt was generated, a tool was recommended, or a user opened an app.

## Scan Before Selection

At project start, run a safe scan before any tool is named in a user action card. Save it as `PROJECT_ROOT/docs/00-工具与权限扫描.md` and link it from `项目路径索引.md`.

The scan must distinguish:

- `已检测可用`: command/application/capability is present and usable from current evidence
- `已检测但需登录/授权`: present, but a human account, API key, or permission is still required
- `浏览器可用待确认`: a public web service can be opened, but account/plan limits are unknown
- `未检测`: do not dispatch work to it

If environment access is limited, say exactly what was observable and what could not be checked. Never infer that an installed app is logged in, paid, or controllable.

## Selection Order

Choose the cheapest concrete tool that can complete the current step with adequate reliability:

| Work | First choice when detected | Fallback | Reasoning |
| --- | --- | --- | --- |
| Requirement, product, architecture, review, cross-file investigation | active terminal/workspace AI such as Codex, Claude Code, or ZCode | current chat agent with project files | high; very high only for material risk |
| Single-file UI or local edit | detected Cursor/Windsurf/VS Code with project open | active workspace AI | medium/high |
| Multi-file implementation | active workspace/terminal AI with tests | AI IDE plus terminal commands | high |
| UI exploration | Figma when design system is needed; v0/Bolt only for approved visual draft | AI IDE implementation from approved style doc | high for design decisions |
| Browser verification | Playwright/browser capability | user follows a focused manual checklist | medium/high |
| Git history/commit | active terminal Git or GitHub Desktop when visual history helps | Git CLI | medium |
| Second review | a different available model/vendor | independent second session of the available model, marked as lower independence | high/very high |

Never choose a paid browser service, new plugin, or premium model merely because it exists. Use it only when its added value is needed for the approved step and record the cost reason.

## Current Agent First

When the active agent can read/write the project, run commands, inspect the browser, or edit code, it should complete those parts itself after approval. The user should not be told to manually relay a document creation, repository edit, test, or simple investigation to another AI just because that AI is installed.

Use another AI only when it provides a distinct required capability, separate independent review, or an environment the active agent cannot access. Handoff must include exact paths and output obligations.

## Who Dispatches

Choose one of these explicitly in each action card:

| Situation | Dispatch method | What the user does |
| --- | --- | --- |
| Current agent has the required access and user approved | current agent executes directly | only confirm and later inspect the result |
| Another detected tool is controllable by the current agent | current agent opens/uses it and records evidence | only approve any account/cost/destructive action |
| Another detected tool requires the user's local login, visible UI, or manual approval | current agent prepares a complete handoff prompt | open the named tool and paste/send exactly once |
| Tool is not detected or cannot be used | do not dispatch; mark `工具阻塞` and choose fallback | approve fallback or complete the stated setup |

Do not say “我已经派发” unless the current agent actually started the target tool/session or the user confirms the prompt was sent. Do not say “已完成” until the artifact and evidence are verified.

## Required Dispatch Record

Add this row to `AI执行清单-进度表.md` for every material step and summarize it in `项目状态.md`:

```markdown
| TOOL-ID | STEP | Work | Selected concrete tool | Model/reasoning | Owner | Input paths | Output path | Status | Evidence / blocker | Fallback |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TOOL-001 | STEP 3 | Architecture | Codex terminal | High | Current agent | [absolute paths] | [absolute path] | 待批准 | - | Claude Code |
```

For an approved parallel wave, add `Wave` and `PAR-ID` to the same record and dispatch all `待批准` tasks in that wave together. Do not mark the wave complete until the coordinator verifies every returned artifact and the planned integration evidence.

Each parallel dispatch must also name its mandatory delivery record: `PROJECT_ROOT/docs/并行任务/PAR-XXX-任务与交付.md`. The worker's handoff prompt must state that chat text alone is not a delivery and include the code branch/worktree or exclusive source scope.

## User-Facing Rule

The user sees only the selected tool and the one action they need to take. Use this wording when the current agent will execute after approval:

```markdown
**执行工具：** Codex（我会直接完成）
**你只需确认：** 是否执行。
```

Use this wording when the user must hand off work:

```markdown
**执行工具：** Cursor（因为需要在你的本地界面检查页面效果）
**你要做：** 打开 Cursor，粘贴下面这段提示词。
```

If blocked, say what is unavailable, why the fallback is needed, and whether the user needs to log in, install something, or choose another route. Do not make the user infer the next action.

## Verification

Before updating the next step, confirm the relevant evidence:

- documents: file exists and contains required sections
- code: changed files plus relevant test/build/lint evidence
- UI: preview/screenshot/browser result
- deployment: URL plus production-safe smoke test
- external handoff: returned report plus artifact path and evidence

Record the evidence location and mark the `TOOL-*` task `已验证`. Only then release the next step.
