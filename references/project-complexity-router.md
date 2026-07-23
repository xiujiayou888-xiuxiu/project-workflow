# Project Complexity Router

## Purpose

Use the minimum process that can safely deliver the actual project. The router reduces cognitive load, tool cost, and document burden without removing necessary safety or quality checks.

## Routing Moment

Run a provisional route after the first requirement round and tool scan. Run the final route after requirements are confirmed, before `AI执行清单-进度表.md` is created. Save both decisions to:

`PROJECT_ROOT/docs/00-项目路由与治理级别.md`

Re-route only when scope, data, money, client commitment, deployment target, or integration risk materially changes.

## Signals

Assess these observable signals. Do not invent risk to force a higher route.

| Signal | Low | Raises Route |
| --- | --- | --- |
| Scope | one clear user journey, 1-2 screens/cards | multiple roles, 3+ connected cards, complex rules |
| Data and identity | no account or disposable local data | login, permissions, personal/client data, shared database |
| Money and commitments | learning/personal experiment | payment, paid customers, fixed price, SLA, acceptance obligation |
| External dependency | no or one low-impact service | multiple APIs, automation, hardware, platform approval |
| Release exposure | local demo only | public users, production deployment, app store, domain |
| Technical change | new isolated project | legacy repo, migration, shared services, production defect |
| Coordination | one agent, one owner | parallel agents, multiple tools, handoffs, contributors |

## Routes

| Route | Typical Project | Required Modules | Normally Skipped | Tool Pattern |
| --- | --- | --- | --- | --- |
| R1 快速验证 | personal prototype, learning exercise, one-flow demo | brief requirement, one vertical slice, local run/visual check, simple state and path index | market deep dive, parallel plan, formal architecture, client documents, production preflight | one detected primary AI; sequential |
| R2 标准 MVP | small usable app, 2-6 cards, limited real users | PRD, product/architecture baseline, cards, card review, integration, tests/visual check, user guide | client quote/contract unless commissioned; parallel only when proven useful | primary AI + IDE/browser as needed; one controlled wave if eligible |
| R3 交付与上线 | client project, paid product, public release, user accounts/data | R2 plus scope/acceptance/risk, code controls, release readiness/preflight, monitoring/rollback level, final difference review | high-risk independent review unless trigger exists | concrete tool dispatch, Git, tests, deployment/review tools; parallel waves when isolated |
| R4 高风险治理 | payment, sensitive data, regulated domain, security incident, legacy production change, material fixed-price obligation | R3 plus threat/security review, independent second review, explicit rollback/backup, decision grill, strict change control | none of the relevant safety gates | high/very-high reasoning only where required; sequential shared changes, limited independent review lanes |

## Route Overrides

- A client requirement automatically starts at least R3 once it reaches a committed delivery/price stage. An early inquiry may remain a lightweight R1/R2 qualification flow until commitment.
- Payment, sensitive personal data, destructive operations, production migration, or security-sensitive access automatically triggers R4 for the affected scope, not necessarily for unrelated project work.
- A small project may use one R4 review card without turning every document and feature into R4.
- The user may request a lighter route, but the agent must state the specific risk being accepted. The agent may not lower a legal/safety/production gate silently.

## Route-Specific Conversation

Default user-visible wording:

```markdown
**本项目路线：** R2 标准 MVP
**原因：** 有多个功能需要最后组合，但暂不涉及支付、敏感数据或正式客户交付。
**本次只启用：** 需求、架构、功能卡、测试、总装和使用说明。
```

Do not show a list of skipped advanced modules unless the user asks. The user should feel the route is a simpler path, not a reduced-quality path.

## Required Route Record

```markdown
# 项目路由与治理级别

- 项目：
- 初步路由 / 最终路由：R1 / R2 / R3 / R4
- 决定时间：
- 证据和信号：
- 本次启用模块：
- 本次不启用模块及原因：
- 具体工具约束：
- 成本策略：
- 升级触发条件：
- 已接受风险：
```

## Tool Routing

Use tool scan results and route together:

- R1: one detected primary AI; do not require external UI, project management, MCP, premium model, or parallel tool unless it is the simplest available route.
- R2: add only the IDE, browser/test tool, or UI tool needed for the actual product surface.
- R3: add Git, deployment verification, and appropriate review tools. Use an external service only when the project needs it.
- R4: reserve independent review and very-high reasoning for the affected high-risk decisions; do not spend it on ordinary formatting or isolated UI edits.

Never make a user install tools merely to satisfy a route label. Choose the route around available capabilities and declare any real blocker plainly.
