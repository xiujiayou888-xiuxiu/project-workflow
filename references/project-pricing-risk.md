# Project Pricing And Risk

Use this only after enough scope is known. It produces a transparent estimate basis and risk decision, not legal, tax, financial, or procurement advice.

## Pricing Rules

1. Quote an **estimate range**, assumptions, validity period, and excluded work. Do not claim certainty where discovery is incomplete.
2. Separate build work from recurring third-party costs: model/API usage, cloud, database, object storage, domain, email/SMS, app-store, payment fees, fonts/assets, and vendor services. State who owns and pays each account.
3. Break work into milestones with concrete outputs and acceptance cases. Tie payment timing to agreed milestones in the user’s final agreement; do not invent enforceable legal terms.
4. Price uncertainty visibly. A fixed price is appropriate only for bounded scope, known dependencies, agreed acceptance, and controlled change. Otherwise recommend paid discovery, phased delivery, or time-and-materials.
5. Never include unlimited revisions, undefined integrations, data migration, content production, compliance approval, production operations, user growth, third-party approval, or performance outcomes unless they are separately scoped and priced.

## Risk Score

For each risk, set likelihood and impact from 1 to 5, then record `score = likelihood × impact`.

| Score | Treatment |
| --- | --- |
| 1-5 | Track; include an owner and check date |
| 6-11 | Reduce before build; state scope/time/cost impact |
| 12-19 | Require a mitigation, milestone, paid discovery, or explicit client decision before commitment |
| 20-25 | Pause or decline until the risk is removed or professionally reviewed |

Assess at least scope certainty, deadline, decision latency, external integrations, data/security, technical novelty, existing-code quality, client dependencies, payment/collection, and ongoing support.

## Output

Create `PROJECT_ROOT/docs/00-报价与风险评估.md`:

```markdown
# 报价与风险评估

- 项目/客户：
- 报价版本与有效期：
- 估算方式：固定范围 / 分阶段 / 工时制 / 先做付费调研
- 结论：可报价 / 先补调研 / 暂缓 / 不建议承接

## 估算基础
| 里程碑 | 交付物 | 范围依据 | 估算区间 | 前提条件 | 验收依据 |
| --- | --- | --- | --- | --- | --- |

## 第三方与持续成本
| 项目 | 费用类型 | 谁开户/付款 | 预计区间 | 不包含说明 |
| --- | --- | --- | --- | --- |

## 不包含范围
## 风险登记
| RISK-ID | 风险 | 可能性 | 影响 | 分数 | 缓解措施 | 决策/责任人 |
| --- | --- | --- | --- | --- | --- | --- |

## 推荐合作方式与下一步
```

## High-Risk Examples

- “先做出来，多少钱以后再说”
- “功能你看着加，效果好就行”
- 目标日期不可移动，但关键账号、内容、接口或审批尚未提供
- 要求保证流量、审核通过、第三方接口稳定、收益、模型绝对准确，或其他不由项目方完全控制的结果
- 个人信息、支付、医疗、金融、未成年人等高风险数据或业务，但责任边界未明确
