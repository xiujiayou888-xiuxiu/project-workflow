# Interaction Control Specification

Use this after the UI style direction is approved and before implementing any visible interface. A control is any button, link, input, select, tab, menu, toggle, upload/drop zone, pagination item, modal action, keyboard shortcut, or destructive operation that a user can operate.

## Rule

Every meaningful control receives a stable `UI-CTRL-*` ID. A control without a clear purpose, visible outcome, and verification path must not be built. Do not use fake buttons, dead icons, or controls that only look interactive.

## Control Inventory

Create `PROJECT_ROOT/docs/06-交互控件规格.md`:

```markdown
# 交互控件规格

- 项目：
- UI 方案：
- 产品/架构来源：
- 版本：

| UI-CTRL-ID | 页面/位置 | 控件与文案/图标 | 关联 REQ/CARD | 用户目的 | 出现条件/权限 | 触发动作 | 系统结果/API | 默认与状态 | 失败/恢复 | 无障碍/键盘/触控 | 组件/文件 | 验收证据 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| UI-CTRL-001 |  |  |  |  |  |  |  |  |  |  |  |  |

## 控件详情

### UI-CTRL-001 - [名称]

- 关联需求/功能卡：REQ- / CARD-
- 用户要完成的事：
- 显示文案、图标与视觉优先级：
- 出现、隐藏、禁用和权限条件：
- 触发方式：点击 / 键盘 / 触控 / 快捷键
- 触发后系统行为：
- 输入、校验与确认文案：
- 成功后的结果和下一步：
- 默认、hover/focus、pressed、disabled、loading、success、error 状态：
- 空数据、重复操作、网络失败、超时和恢复行为：
- 手机端和无障碍说明：
- 涉及组件/文件/API：
- 验收步骤与证据：
```

## State Rules

- Primary action: state the user value clearly; disable it only for a known reason and explain the reason nearby when needed.
- Destructive action: name the consequence, require suitable confirmation, and explain whether undo/recovery exists.
- Long-running action: prevent accidental duplicate submission, show progress, and leave a recoverable result or retry path.
- Form/input: label the expected format, validate before/after submission, and place a useful error near the field.
- Icon-only control: provide a familiar icon, accessible name/tooltip, fixed hit area, and visible focus state.
- Async failure: keep entered data when safe, name the failure in plain language, and offer retry or an alternative path.

## Acceptance

For every critical control, provide one of:

- browser/manual evidence: page -> operate control -> see expected result
- automated UI/integration test
- API request/response evidence plus visible UI result
- desktop and mobile screenshot for a control whose visual state matters

Review every `UI-CTRL-*` after implementation. If its implementation, label, permission, state, or result differs from the specification, update the spec and obtain required approval before acceptance.
