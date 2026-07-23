# Market Feasibility Gate

Use this before turning a user's own commercial/product idea into a PRD or development plan. The purpose is to prevent months of building a technically possible product with no clear user value, reachable market, or credible path to return more value than it costs.

Do not use this gate to reject a personal-learning, hobby, or internal efficiency tool merely because it has no public market. Instead, record its non-commercial value, owner, time/cost cap, and success measure. For a product intended for customers, revenue, audience, or public adoption, this gate is mandatory.

## Research Rules

- Clarify the idea enough to name a target user, painful job, expected result, and intended market before researching.
- Use current web research for market facts, competitors, pricing, regulation, platform rules, and demand signals. Cite direct sources and date-sensitive claims in the output.
- Search for disconfirming evidence: existing free/paid alternatives, entrenched habits, distribution barriers, high switching cost, acquisition cost, legal/platform restrictions, and expensive dependencies.
- Separate facts, user claims, AI hypotheses, and unknowns. Do not make revenue, demand, or market-size claims without an attributable source.
- A competitor proves there may be demand, not that this project will win. Lack of search results does not prove there is no niche; it means the demand hypothesis needs another validation method.

## Decision Dimensions

Assess each dimension with `strong / partial / weak / unknown` evidence and confidence `high / medium / low`:

| Dimension | Question |
| --- | --- |
| Pain and frequency | Does a named user repeatedly lose money, time, opportunity, or confidence on this task? |
| Existing alternatives | What do they use now, what does it cost, and why is it inadequate? |
| Distinct value | What specific faster/cheaper/safer/better result would make them switch or try? |
| Reachability | Where can the first 10 users/customers actually be reached? Existing audience, client channel, community, partner, or sales path? |
| Monetization/value capture | Who pays, why now, and what is the price/cost-saving/revenue logic? |
| Unit economics and cost | What recurring cost, support burden, API/cloud cost, and acquisition effort exist? |
| Execution and risk | Can a small MVP test the hypothesis; are regulation, data, platform, competition, or dependency risks manageable? |

## Decision Rules

### Go

Use only when the critical user, painful job, first-user path, and value hypothesis are all at least partial with no unresolved fatal risk. Start a small MVP that tests the most uncertain but important assumption.

### Validate First

Use when the idea has plausible value but evidence is weak or unknown. Recommend exactly one smallest validation action, with a deadline and success threshold, such as:

- 5-10 target-user interviews that test the current workaround and willingness to try/pay;
- a clickable/prototype test of the core workflow;
- a landing page or waitlist with one clear offer and a defined signup target;
- a paid or unpaid pilot with a named first customer and measurable outcome;
- a concierge/manual service test before automating it.

Do not build a full system during this stage.

### No-Go

Choose No-Go when there is no identified painful user/job, no credible first-user reach path, no differentiated value over accessible alternatives, economics are clearly negative, required external/platform/legal conditions are unavailable, or two or more critical dimensions remain weak with no cheap validation route. Explain the evidence and recommend a stop, a narrower problem, a different customer, or a bounded learning experiment.

## Output

Create `PROJECT_ROOT/docs/00-可行性与市场验证.md`:

```markdown
# 可行性与市场验证

- 原始想法：
- 项目模式：想法落地
- 意图：商业产品 / 内部工具 / 学习实验
- 研究日期：
- 结论：Go / Validate First / No-Go
- 证据置信度：高 / 中 / 低

## 问题、用户与价值假设
## 当前替代方案与竞品
| 替代方案/竞品 | 面向谁 | 解决什么 | 价格/限制 | 对本项目的启发或威胁 | 来源 |
| --- | --- | --- | --- | --- | --- |

## 市场与获客证据
| 证据 | 支持/反驳什么 | 可信度 | 来源/日期 |
| --- | --- | --- | --- |

## 可行性判断
| 维度 | 证据强度 | 结论 | 未知项/风险 |
| --- | --- | --- | --- |

## 成本与价值路径
## 反对立项的证据
## 决定与原因
## 下一步
- Go：最小 MVP 要验证的假设：
- Validate First：验证动作、截止日期、成功阈值：
- No-Go：停止/重构建议：

## 用户坚持继续时的实验边界
- 最大时间：
- 最大预算：
- 成功指标：
- 停止日期：
```
