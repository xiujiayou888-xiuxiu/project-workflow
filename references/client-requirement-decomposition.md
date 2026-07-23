# Client Requirement Decomposition

Use this only in `客户交付` mode. The client source is the baseline. Preserve it before interpreting it, and make every interpretation traceable.

## Rules

- Record every client source: message, meeting note, document, image, URL, repository, or prior system. Store a path/link and date; do not rely on chat memory.
- Do not rewrite a vague client statement into a technical promise. Map it to a `REQ-*`, mark it as ambiguous, contradictory, client-provided, excluded, or awaiting approval.
- Ask questions only to close high-impact gaps: exact user/result, acceptance, authority, data/permission, dependency, deadline, budget, ownership, and support.
- Preserve the original wording in a source column. Place AI interpretation in a separate column.
- No requirement enters a feature card until its scope and acceptance status are `Approved`.

## Output

Create `PROJECT_ROOT/docs/00-客户需求原文与拆解.md`:

```markdown
# 客户需求原文与拆解

- 项目模式：客户交付
- 客户/决策人：
- 项目根目录：
- 基线版本：
- 来源清单：

## 需求追踪
| REQ-ID | 客户原文/来源 | AI 拆解 | 验收证据 | 状态 | 缺口/冲突 | 需要谁确认 |
| --- | --- | --- | --- | --- | --- | --- |

## 客户明确不做
## AI 不作承诺的事项
## 待确认问题
## 与报价、边界、风险文档的关联
```

## Stop Conditions

Do not produce a fixed quote, fixed delivery date, or implementation plan when a core source requirement has no acceptance definition, a decision-maker is missing, sources conflict, or a required client dependency has no owner/date.
