# Delivery Grounding

Use this to keep the workflow attached to real project delivery. A document is a decision record, not proof that a product exists. A requirement is only complete when a normal user or another AI can locate and verify its actual implementation.

## Implementation Anchor

Every meaningful `REQ-*`, `ADR-*`, `AI-FLOW-*`, `UI-CTRL-*`, `CARD-*`, `PAR-*`, and review fix must have at least one concrete anchor:

- code file, component, route, API endpoint, database migration, or configuration
- command output such as build, test, lint, migration, or package result
- manual/browser path with real input and visible expected output
- deployed URL, package, installer, or generated user-facing file
- explicit user-approved non-code decision, only when implementation is intentionally out of scope

Do not use “已规划”, “已设计”, “已考虑”, a generic screenshot, or an AI self-report as the only anchor.

## First Slice Rule

After architecture approval, build one small but real end-to-end slice before expanding scope. It must include one user action, the required data/API/logic, a visible result, and verification evidence. Use it to expose wrong architecture early.

## Delivery Verification

Create `PROJECT_ROOT/docs/21-落地验证清单.md` before final acceptance:

```markdown
# 落地验证清单

- 项目：
- 版本：
- 项目根目录：
- 验证人：
- 最终结论：可交付 / 需继续落地

| 类型 | ID | 承诺内容 | 实际实现位置 | 如何运行/验证 | 证据路径/URL | 状态 | 缺口/下一步 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 需求 | REQ-001 |  |  |  |  |  |  |
| 架构 | ADR-001 |  |  |  |  |  |  |
| AI能力 | AI-FLOW-001 |  |  |  |  |  |  |
| 控件 | UI-CTRL-001 |  |  |  |  |  |  |
| 审查修复 | FIX-001 |  |  |  |  |  |  |

## 首个垂直切片
- SLICE-001：
- 实际运行结果：
- 证据：

## 未落地内容
- 
```

## Stop Conditions

Stop and return the work to the relevant card when:

- an accepted requirement has no actual implementation location or verification evidence
- a design decision cannot identify what it changes in the project
- a UI control has no working implementation or a review fix only exists in prose
- a claimed feature requires fake data, a dead control, or an untested happy path to appear complete

Use the smallest next implementation action. Do not write another planning document unless it unlocks a real code, test, or delivery action.
