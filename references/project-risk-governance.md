# Project Risk Governance

Use this for every commissioned project and for any own project with material money, personal data, public users, external vendors, or delivery commitments. It is a delivery-control system, not legal, financial, insurance, tax, or compliance advice.

## Risk Register Rules

- Keep exactly one live register at `PROJECT_ROOT/docs/00-项目风险总表.md`; link to detailed scope, quote, change, security, release, and review evidence instead of copying it.
- Assign each risk a stable `RISK-*` ID, category, likelihood, impact, owner, trigger, prevention, fallback, decision, and evidence.
- Reassess the register at G0-G6, after any change request, after a failed test/review, and before release/handover.
- Do not use an AI as the risk owner. A person or named client-side role must own the decision.
- Do not record passwords, API keys, private data, or contract secrets in the register.

## Categories To Check

| Category | Ask Before Commitment |
| --- | --- |
| Business/value | Is there a paying decision-maker, a real outcome, a budget reality, and a success measure? |
| Scope/change | Are V1, exclusions, revisions, content, migration, integrations, and acceptance explicit? |
| Commercial | Is estimate basis clear; are recurring costs, client delay, dependency changes, and payment checkpoints considered? |
| Legal/compliance | Does the work involve regulated data/business, IP/licensing, contracts, public claims, or jurisdiction-specific obligations needing review? |
| Data/security | Who owns data/accounts; what access is necessary; what must never be exposed; how are backups and deletion handled? |
| Technical | Are existing systems, APIs, model quality, scale, performance, and recovery understood enough for the delivery promise? |
| Delivery | Are client inputs, approval timing, responsible people, third-party dependencies, and acceptance process scheduled? |
| Release/operations | Are environments, monitoring, logs, rollback, ownership, support, cost limits, and incident escalation known? |

## Severity And Response

Score `likelihood × impact`, each from 1 to 5. Severity is not only the score: privacy, security, legal/compliance, and irreversible data loss may be P0 even at low likelihood.

| Severity | Meaning | Required Response |
| --- | --- | --- |
| P0 | Could cause unlawful/unacceptable exposure, irreversible loss, material security breach, or make delivery impossible | stop; remove/transfer risk or obtain a qualified external decision before proceeding |
| P1 | Could materially change scope, cost, deadline, acceptance, or user trust | document mitigation, owner, fallback, and explicit project-owner/client decision before the affected work |
| P2 | Manageable risk with limited impact | schedule owner/checkpoint and verify at the next gate |

## Output

Create `PROJECT_ROOT/docs/00-项目风险总表.md`:

```markdown
# 项目风险总表

- 项目/客户：
- 当前阶段：G0 / G1 / G2 / G3 / G4 / G5 / G6
- 最后更新：
- 当前结论：可继续 / 限制条件下继续 / 暂停

| RISK-ID | 类别 | 风险与触发条件 | 可能性 | 影响 | 级别 | 预防措施 | 兜底/停止动作 | 责任人 | 当前决定 | 证据/关联文档 | 下次检查 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

## P0/P1 决策记录
| RISK-ID | 需要谁决定 | 选项 | 已选方案 | 决定日期/证据 |
| --- | --- | --- | --- | --- |

## 本阶段放行结论
- 已满足：
- 未满足：
- 不可接受的风险：
- 下一步：
```

## Examples Of Stop Conditions

- Client requires a fixed total price and deadline but refuses to define scope or acceptance.
- Client asks to use their production database/account but no access, backup, permission, or rollback boundary exists.
- The project handles payment, sensitive personal data, medical/financial decisions, or public compliance claims without a responsible professional/owner.
- A third-party API, store review, payment provider, model output, traffic target, or external approval is promised as guaranteed even though the delivery team cannot control it.
- The client cannot designate an approval person, provide critical materials, or accept a written change process.
