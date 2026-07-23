# Decision Grill And Glossary

Use this to stress-test a meaningful plan or decision while preserving the language and decisions another AI must understand. It is inspired by the useful workflow behind `grill-with-docs`, adapted for this Chinese project workflow.

## Purpose

Expose unclear terms, hidden assumptions, conflicting requirements, boundary failures, and irreversible choices before they become code, a client commitment, or a production incident. Do not use it to perform an endless interview or generate documents without a real decision.

## When To Run

Run only when a decision affects scope, price, acceptance, security, data ownership, architecture, a public contract, a client commitment, or an expensive-to-reverse path. For routine code tasks, rely on the approved glossary/ADRs and continue.

## Grilling Method

1. **Ground first:** read `项目状态.md`, PRD/client baseline, current glossary, `决策记录.md`, risk register, architecture, and existing code/contracts. Search before asking.
2. **Name the decision:** give it a `GRILL-*` ID and say what must be decided now, what is already known, and what remains uncertain.
3. **Challenge ambiguity:** identify fuzzy words such as “用户”, “管理员”, “订单”, “完成”, “上线”, “支持”, “数据删除”, “AI 自动处理”, or client-specific terms. Ask what they mean in this project.
4. **Test scenarios:** use one normal journey plus one boundary/failure/abuse scenario. Check ownership, permissions, source of truth, cost, acceptance, and recovery.
5. **Compare alternatives:** for consequential choices, show the simplest viable option and any genuinely material alternative. State tradeoffs in plain language.
6. **Ask minimally:** ask one decision-changing question at a time. If the user gives a conservative instruction, record it as `AI默认建议，待确认` rather than inventing certainty.
7. **Write durable results:** update the glossary, ADR only when warranted, risk register, and grill record. Then announce the gate decision.

## Glossary Rules

Create `PROJECT_ROOT/项目术语表.md` as the canonical shared language. Do not include generic technical terms unless the project uses them in a special way. Record terms that can cause scope, data, permission, acceptance, billing, or customer misunderstanding.

```markdown
# 项目术语表

- 项目：
- 最后更新：
- 维护规则：本文件是跨 AI、客户和项目成员的术语基线；修改核心术语必须记录来源和批准。

| TERM-ID | 术语 | 本项目定义 | 可用别名 | 禁止/易混淆说法 | 来源/证据 | 所有者 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| TERM-001 |  |  |  |  |  |  | 已确认/待确认 |

## 术语冲突与待确认
```

## ADR Threshold

Write `ADR-*` in `PROJECT_ROOT/决策记录.md` only when the decision changes a hard-to-reverse boundary, cost, ownership, public contract, security posture, data model, architecture, or client commitment. Use the existing ADR template. Do not create ADRs for routine implementation details.

## Output

Create or update `PROJECT_ROOT/docs/25-关键决策压测记录.md`:

```markdown
# 关键决策压测记录

## GRILL-001 - [decision]
- 触发原因与关联 REQ/SCOPE/CHANGE/ADR：
- 已读取的证据：
- 当前术语与定义：
- 已知事实：
- 假设与未知项：
- 正常场景：
- 边界/失败场景：
- 候选方案与取舍：
- 本轮关键问答：
- 已确认决定：
- 新增/更新 TERM、ADR、RISK：
- 放行结论：通过 / 有条件通过 / 阻塞
- 下一步与责任人：
```

## Stop Conditions

Block the next gate when a core term has competing meanings, an acceptance condition cannot be tested, a party/data owner is unclear, a high-cost assumption lacks evidence, or a proposed change conflicts with an approved ADR/scope without an explicit change decision.
