# Client Opportunity Qualification

Use this before investing substantial unpaid pre-sales work in a new external client inquiry. It is a practical fit-and-readiness workflow, not a manipulation system. The goal is to use time proportionately, give the client enough clarity to decide, and avoid delivering a complete free solution before there is a credible commitment.

## Stages

| Stage | Allowed Work | Do Not Give Away |
| --- | --- | --- |
| `INQ-NEW` | acknowledge, understand the broad scene, record source | solution, UI, architecture, estimate |
| `INQ-QUALIFY` | ask concise high-value questions and score evidence | full PRD, detailed feature map, line-item quote |
| `INQ-ONE-PAGER` | send a one-page problem/outcome/collaboration brief | implementation blueprint, detailed UI/design, technical architecture |
| `INQ-QUOTE` | approved scope/risk/acceptance and formal quote | unbounded revisions or unspecified extras |
| `INQ-COMMITTED` | prepare delivery setup after agreed start condition | production work before commitment |
| `INQ-PAUSED` / `INQ-LOST` | concise follow-up or close note | repeated free revisions or repeated chasing |

## Qualification Signals

Score each item `0 = absent/unclear`, `1 = partial`, `2 = clear/credible`. Score is an aid, not a substitute for judgment.

| Signal | What To Establish |
| --- | --- |
| Scene and pain | a concrete use case and why it matters now |
| Decision authority | who can approve budget, scope, and start |
| Time and version | desired timing and what the first version must achieve |
| Budget fit | a range or at least realistic willingness to discuss investment |
| Acceptance | what result would make the client say it works |
| Payment/start intent | willingness to use a defined commercial start condition |
| Collaboration readiness | client can provide materials, access, feedback, and responsible contact |

## Decision Guide

| Result | Next Action |
| --- | --- |
| 0-5 or a fatal red flag | `暂停/婉拒` or ask only 1-3 missing high-value questions |
| 6-9 with plausible fit | `发送一页说明`; do not prepare detailed solution/quote yet |
| 10-14 with no unresolved P0/P1 | `正式范围与报价`; start client baseline and commercial gates |

Fatal red flags include: no identifiable decision-maker, demand for detailed unpaid plan without intent to proceed, refusal to discuss any budget/start condition, insistence on unlimited revisions, illegal/unsafe request, impossible fixed date, or reliance on unavailable client assets/accounts.

## One-Page Brief

Create `PROJECT_ROOT/docs/00-一页项目说明.md` only for `INQ-ONE-PAGER`:

```markdown
# 一页项目说明

- 客户：
- 当前问题：
- 预期第一版结果：
- 初步合作方向：
- 当前关键未知项：
- 若继续，需要客户确认/提供：
- 下一步建议：进一步沟通 / 正式范围与报价 / 暂停
- 说明：本页不构成完整需求、技术方案、报价承诺或交付承诺。
```

## Opportunity Record

Create or update `PROJECT_ROOT/docs/00-商机评分与沟通记录.md`:

```markdown
# 商机评分与沟通记录

- 客户/线索来源：
- 当前阶段：INQ-NEW / INQ-QUALIFY / INQ-ONE-PAGER / INQ-QUOTE / INQ-COMMITTED / INQ-PAUSED / INQ-LOST
- 最近沟通：
- 结论：继续澄清 / 发送一页说明 / 正式范围与报价 / 暂停/婉拒

## 评分
| 信号 | 分数 0-2 | 证据/原话 | 缺口 |
| --- | --- | --- | --- |

## 已问问题与答复
## 本轮允许交付内容
## 不免费交付的内容
## 下一步、负责人和跟进时间
## 暂停/流失原因
```

## Communication Rules

- Ask clearly and respectfully. Do not pressure a client into exposing private budget or making a commitment.
- Explain that more detailed scope, design, and quote depend on enough information to avoid wasting both sides' time.
- If the client does not reply, record it. Recommend one concise follow-up only when appropriate, then pause rather than continuing unpaid work.
- Existing trusted clients, formal RFP/procurement, or paid discovery may use a different path; record the reason for skipping/adjusting the score.
