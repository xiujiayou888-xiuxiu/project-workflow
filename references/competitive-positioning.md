# Competitive Positioning

Use this for a user's own commercial/product idea after basic problem discovery and before PRD confirmation. It answers whether the proposed product has a credible reason to exist beside current choices, and how the first users can discover it.

## Comparison Set

Research and compare at least:

1. **Direct competitors:** products solving the same job for the same target user.
2. **Indirect alternatives:** products solving part of the job, adjacent tools, agencies, freelancers, or existing platforms.
3. **Free/manual workaround:** spreadsheets, chat groups, copy-paste, hiring someone, doing nothing, or users' current process.

Use current public sources for factual claims. Record URLs, source dates, product pricing/features only where verified, and clearly label inference. Do not copy a competitor's marketing claims into the project as facts.

## Where A Real Wedge Can Come From

Select a specific, evidence-backed advantage. It can be one or a combination of:

| Wedge | Example Question |
| --- | --- |
| Narrow segment | Which ignored user group has a distinct workflow or constraint? |
| Better outcome | What measurable time, error, revenue, trust, or completion improvement matters? |
| Workflow integration | What steps can be removed or connected that existing tools leave fragmented? |
| Distribution/channel | What existing audience, community, partner, client base, or sales path reaches the first users? |
| Trust/service | What onboarding, localization, support, privacy, reliability, or domain expertise lowers adoption risk? |
| Unique data/relationship | What lawful, permissioned data or relationship improves the experience and cannot be trivially copied? |
| Cost model | Why is a lower/higher price sustainable and meaningful for the target user? |

“Use AI”, “beautiful interface”, “all-in-one”, generic feature quantity, and unsupported low price are not wedges by themselves.

## Decision Rules

- **Go:** there is a specific first segment, a painful inferior alternative, a testable wedge, and a credible first-user path.
- **Validate First:** the wedge is plausible but requires customer interviews, pricing test, prototype comparison, pilot, or channel test.
- **No-Go:** the product is a feature-for-feature copy with no reachable segment, no credible differentiator, or no sustainable way to acquire initial users; recommend narrowing/reframing or stopping.

## Output

Create `PROJECT_ROOT/docs/00-竞品对比与差异化策略.md`:

```markdown
# 竞品对比与差异化策略

- 项目：
- 目标第一细分人群：
- 研究日期：
- 结论：有竞争切口 / 需验证 / 暂不建议立项
- 证据置信度：高 / 中 / 低

## 当前替代方案
| 类别 | 名称/做法 | 面向谁 | 用户得到什么 | 价格/成本 | 强项 | 痛点/空白 | 证据来源 |
| --- | --- | --- | --- | --- | --- | --- | --- |

## 我们的竞争切口
- 目标人群：
- 他们当前的替代方案：
- 当前方案的具体不足：
- 本项目提供的可验证更好结果：
- 差异来自：细分 / 工作流 / 渠道 / 信任服务 / 数据关系 / 成本
- 第一批用户获得路径：
- 最容易被复制或击败的点：

## MVP 只做什么来验证竞争点
| 假设 | 最小验证 | 成功阈值 | 失败后的处理 |
| --- | --- | --- | --- |

## 不成立的竞争说法
## 能力边界判断
```

## Stop Conditions

Do not enter full product development if the first segment is “everyone”, the alternative is unknown, the advantage has no testable evidence, the first-user path is only “publish it and wait”, or the proposed advantage relies on a third party/model/platform outcome that cannot be controlled.
