# Client Discovery And Scope

Use this before accepting, quoting, or scheduling a commissioned project. The objective is to turn a client conversation into a bounded project decision, not a vague promise.

## Interview Order

Ask in small rounds, no more than four questions each. Obtain answers for:

1. **Business result:** Who pays, who uses it, what costly or painful task changes, and how success is observed.
2. **Decision rights:** Who can approve scope, design, acceptance, budget, and changes; who supplies final feedback.
3. **Scope:** Required V1 journeys, explicit exclusions, examples of acceptable results, platform/device, and delivery level.
4. **Dependencies:** Content, brand assets, domain, cloud account, payment account, API/AI keys, data, legal text, approvals, and third-party vendors. Mark each as client-provided or delivery-team-provided.
5. **Constraints:** Budget range, target date, fixed events, privacy/security needs, existing systems, and material risks.

## Scope Writing Rules

- Give every accepted deliverable a `SCOPE-*` ID and every acceptance example an `ACC-*` ID.
- Write user-visible results, not technical activities. “One admin login flow with reset password” is scope; “build authentication” is not precise enough.
- Put every unclear item in `Open Questions`; do not turn it into a promise.
- Write exclusions explicitly. Any work absent from the approved scope is a possible change, not a free add-on.
- If discovery is insufficient for an estimate, recommend a paid discovery phase that produces the PRD, architecture outline, estimate, and delivery plan.

## Output

Create `PROJECT_ROOT/docs/00-合作立项与需求访谈.md`:

```markdown
# 合作立项与需求访谈

- 项目：
- 客户/决策人：
- 版本：
- 访谈日期：
- 项目根目录：

## 业务目标与成功标准
## 用户与核心场景
## 已确认范围
| SCOPE-ID | 交付结果 | 优先级 | 示例/限制 | 责任方 |
| --- | --- | --- | --- | --- |

## 明确不包含
## 依赖与客户提供项
| 项目 | 谁提供 | 最晚提供时间 | 未提供的影响 |
| --- | --- | --- | --- |

## 开放问题与风险
## 下一步建议
```

## Stop Conditions

Pause and recommend discovery or refusal when the client will not identify a decision-maker, cannot describe a usable result, requires an exact fixed price with undefined scope, expects unlimited revisions, or withholds a dependency that makes delivery impossible.
