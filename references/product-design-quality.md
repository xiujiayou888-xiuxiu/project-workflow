# Product Design Quality

Use this for every non-trivial product. Good delivery is the overlap of useful product design, reliable function, fitting architecture, intentional interaction, and distinctive visual design. Passing a build command alone is not quality.

## Five Design Layers

| Layer | Must Be Designed | Evidence |
| --- | --- | --- |
| Product | target user, painful task, critical journey, scope, success outcome | `docs/02-产品框架.md` and `REQ-*` |
| Function | real input/output, business rules, defaults, edge cases, recovery | feature cards, tests, realistic examples |
| AI capability (when applicable) | user task to AI capability, context/knowledge, tool permission, output guardrail, evaluation, and human fallback | `docs/03-技术架构.md`, `AI-FLOW-*`, test and review evidence |
| Architecture | data ownership, boundaries, contracts, performance/cost/reliability fit | `docs/03-技术架构.md`, `ADR-*` |
| Interaction | hierarchy, task sequence, feedback, empty/loading/error/success states | page flow, browser evidence |
| Visual | personality, layout, typography, color roles, assets, responsive polish | `docs/06-UI风格方案.md`, screenshots |
| Controls | every action's purpose, state, result, accessibility, and test evidence | `docs/06-交互控件规格.md`, `UI-CTRL-*` |

## Design Questions Before Code

Answer these in the relevant product, architecture, and UI documents:

1. What exact task becomes easier for which person?
2. What is the shortest safe path from opening the product to a useful result?
3. What information, action, and feedback must be most visible at each moment?
4. What should happen with empty data, invalid input, failure, recovery, and repeat use?
5. What makes this product visually and structurally appropriate for its category rather than a copied starter template?
6. What architecture decision protects the experience as the product grows?

## Quality Rules

- Do not use placeholder labels, lorem ipsum, fake charts, dead controls, or decorative screens as acceptance evidence.
- Do not make a dashboard when the user needs a guided workflow, or a marketing page when the user needs a working tool.
- Make the primary action, result, and next safe action obvious.
- Prefer fewer, well-designed flows over many shallow features.
- Use real product content, relevant imagery or assets, and product-specific hierarchy when the visual product needs them.
- Match density and interaction to audience: operational tools favor speed and scanability; consumer tools favor guidance and feedback; creative tools favor expressive but usable composition.
- Treat accessibility, responsive behavior, error recovery, and perceived performance as design, not afterthoughts.

## Design-Quality Acceptance

Create `PROJECT_ROOT/docs/20-设计品质验收.md` after integration and before mature review:

```markdown
# 设计品质验收

- 项目：
- 版本：
- PRD/产品框架/技术架构/UI方案：
- 验收人：
- 结论：通过 / 需修改

| 设计层 | 已验证内容 | 证据路径/URL | 发现的问题 | 结论 |
| --- | --- | --- | --- | --- |
| 产品 |  |  |  |  |
| 功能 |  |  |  |  |
| AI能力（如适用） |  |  |  |  |
| 架构 |  |  |  |  |
| 交互 |  |  |  |  |
| UI视觉 |  |  |  |  |

## 真实关键路径
| 用户任务 | 真实输入 | 预期结果 | 实际证据 | 状态 |
| --- | --- | --- | --- | --- |

## 设计债务与下一步
- 
```

Return a project to the relevant feature card when any critical layer has no evidence, a core journey has a dead end, or the interface does not meet the approved visual direction.
