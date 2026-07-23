# Client Delivery Boundaries And Acceptance

Use this after the client scope and estimate are sufficiently clear. It creates a practical delivery boundary and acceptance checklist. It is not a substitute for a lawyer-reviewed contract.

## Boundary Rules

- Define exactly what is delivered: repository/source, deployed URL, package, design/source files, documentation, account transfer, training, and data export where applicable.
- Define exactly what is not delivered: unlisted features, content entry, marketing results, third-party approval, unlimited revisions, ongoing operation, support after the agreed period, and unspecified integrations.
- Write `ACC-*` acceptance cases with precondition, input/action, expected visible result, evidence, and reviewer. “Looks good” alone is not an acceptance standard.
- Record each client-provided dependency and the effect if it is late or unavailable.
- Define who owns cloud/domain/API/payment accounts, source code, data, assets, and credentials. Do not take possession of client-owned credentials in chat; use secure client-controlled configuration.
- Require every requested change to be written in `docs/00-需求变更单.md` with scope, price, schedule, risk, and approval impact before coding starts.

## Output

Create `PROJECT_ROOT/docs/00-交付边界与验收.md`:

```markdown
# 交付边界与验收

- 项目/客户：
- 范围版本：
- 对应报价版本：
- 生效前待确认项：

## 交付清单
| DEL-ID | 交付物 | 包含内容 | 不包含内容 | 交付位置 | 责任方 |
| --- | --- | --- | --- | --- | --- |

## 验收案例
| ACC-ID | 场景/前提 | 客户操作 | 预期结果 | 证据 | 验收人 | 结果 |
| --- | --- | --- | --- | --- | --- |

## 客户提供与配合
| 项目 | 责任方 | 提供时间 | 延迟影响 |
| --- | --- | --- | --- |

## 账户、数据与资产归属
## 支持与维护边界
## 变更流程
```

Create `PROJECT_ROOT/docs/00-需求变更单.md` with this repeatable block:

```markdown
## CHANGE-001 - [request]

- 提出日期/提出人：
- 对应 SCOPE/ACC：
- 新需求与原因：
- 是否原范围：是 / 否 / 待确认
- 对范围、报价、时间、风险、验收的影响：
- 推荐处理：纳入本期 / 新里程碑 / 工时制 / 拒绝或延后
- 批准人、批准日期与证据：
- 实施卡片与验证结果：
```

## Final Handover

Create `PROJECT_ROOT/docs/23-客户交付与结项.md` only after client acceptance. Include accepted `ACC-*`, source/URL/package versions, account and asset transfer record, documentation paths, support end date/boundary, known limitations, and open approved changes. Never list passwords or raw secret values.
