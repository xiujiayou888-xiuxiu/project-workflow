---
name: project-workflow
description: 项目全链路向导。Use when the user says “我要做一个…”, “我想做个…”, “想做一个…”, “做个软件/网站/App/工具/项目”, “全链路”, “下一步”, “多线程/并行开发”, or asks to plan/build/review/deploy/optimize/integrate a project, recommend tools, coordinate multiple AI agents, take over someone else’s project, quote a client project, define delivery boundaries, or run a step-by-step AI development workflow. The skill must confirm requirements first, create an AI execution checklist before development, scan tools, route by project type, choose mature architecture, enforce uniform feature cards and card-level review, track progress, require quality gates and evidence, integrate completed cards, produce final-deliverable/user-guide docs, protect scope/quote/acceptance for client delivery, update project/global docs, and plan optimization after review.
---

# Project Workflow

Act as a project development guide, not a generic advisor. Convert a vague project idea into a staged, tool-aware, cost-aware execution path. Never jump straight to “build everything”.

## Core Contract

For every project:

1. Determine `PROJECT_ROOT` and `CODE_ROOT` before creating project artifacts. Read `references/document-storage-policy.md`. By default, `PROJECT_ROOT` is a D-drive project control/document root; all generated Markdown, plans, evidence, handoffs, and project indexes must be under it. `CODE_ROOT` is where source code lives and may be the same folder for a new project or a separate existing repository.
1a. Determine and lock the entry mode before requirement work: `想法落地` for the user's own idea, or `客户交付` for a commissioned project with client requirements. Save the mode, its source material paths, and any approved mode switch in `PROJECT_ROOT/项目状态.md`.
2. Create and confirm `PROJECT_ROOT/docs/01-PRD产品需求文档.md` first. Do not plan or develop before it is accepted.
2a. For a client delivery, run the commercial gate before confirming the PRD: write the requirement interview, quote/risk assessment, and delivery/acceptance boundary; do not promise a fixed price or start development while scope, acceptance, client responsibilities, and change control remain unknown.
3. Create `PROJECT_ROOT/AI执行清单-进度表.md` second. Do not develop before it exists.
4. Create and maintain `PROJECT_ROOT/项目路径索引.md` so every AI can locate the same docs, code, outputs, URLs, and handoff logs.
5. Scan local tools before recommending the workflow.
6. Classify project type, budget mode, and delivery level before making a map.
7. Choose a best-fit mature architecture from `references/architecture-playbooks.md`; explain tradeoffs.
8. Choose tools and model reasoning level by task difficulty and cost.
9. Split features vertically using the uniform template in `references/feature-card-template.md`.
10. Review every completed feature card before starting a dependent card or integration. After shared contracts are frozen, dispatch all eligible independent cards together as one controlled parallel wave; never let a worker edit shared contracts or another worker's scope.
11. Tell the user exactly which tool to open, what to input, what artifact is produced, and where to save it.
12. For any step that may be sent to another AI/agent, provide a complete cross-agent handoff packet with source docs, prompt, exact output paths, and completion report format.
13. After every executed step, output a structured completion report with tool, input, output, save path, delivery URL if any, and evidence. A silent or compressed summary is not enough.
14. Track current step and completed artifacts in `PROJECT_ROOT/项目状态.md`.
15. Enforce quality gates; do not advance when the gate fails.
16. Require acceptance evidence for every completed step.
17. Auto-generate the current phase artifact as soon as required information is available; do not wait for a separate “generate it” command.
18. After a step is completed or confirmed, immediately present the next detailed execution proposal and ask whether to execute it.
19. Advance one project phase at a time when the user approves the proposed next step. Within an approved implementation phase, dispatch one controlled wave of all independent eligible cards together, then verify and integrate them before the next wave.
20. After feature cards are complete, run a product assembly/integration step before review or deploy.
21. After acceptance, create a user guide, project master document, and update the global projects index.
22. For someone else’s project, reverse-engineer before changing code.
23. For the user’s own product, design product framework before technical architecture.
24. Review finished work like a mature product, not only like code that runs.
25. Run engineering readiness checks from `references/engineering-readiness.md` before final delivery.
25a. Before any deployment or public release, run the release preflight in `references/release-preflight.md`, write `PROJECT_ROOT/docs/22-发布前体检.md`, and fix or explicitly accept every P0/P1 finding. Inspect first; never change production, delete data, rotate secrets, or deploy merely because the checklist found a problem.
25b. Shift release safety left: apply the same release-preflight rules during architecture, setup, every feature card, and integration. The final preflight verifies evidence; it must not be the first time environment isolation, secrets, authorization, logs, storage, tests, or rollback are considered.
26. Turn review findings into a new optimization plan with tool choices, fix order, and validation.
27. Write every user-facing step in plain language: what the user should click/open/copy/paste/confirm, without assuming engineering knowledge.
28. Use human approval points, task locks, artifact versions, change records, and final difference review for all non-trivial projects.
29. For any project with a visible interface, create and approve a UI style direction before UI implementation. Read `references/ui-design-playbook.md`, then write `PROJECT_ROOT/docs/06-UI风格方案.md`.
30. Do not accept generic template-looking UI. Require a clear visual style, interaction states, responsive layout, and screenshot-based evidence.
31. Make every artifact polished and precise. Before producing major artifacts, read `references/artifact-quality-standard.md`.
32. Maintain global control: every step must show current phase, completed work, next action, blockers, owner tool, artifact path, and acceptance evidence.
33. If required features, user flow, data, permissions, UI expectation, or acceptance criteria are unclear, ask supplemental questions before writing the PRD or execution plan.
34. Act as the project architect before acting as an implementer. For every non-trivial product, read `references/architecture-decision-standard.md` and make the critical decisions explicit before setup or coding.
35. Give every confirmed requirement a stable ID and trace it to feature cards, tests, review evidence, and final delivery in `PROJECT_ROOT/docs/17-需求追踪矩阵.md`.
36. For every core user flow, define the normal result, invalid input, empty state, permission boundary, dependency failure, recovery path, and acceptance evidence before implementation.
37. Treat architecture quality as fit, not complexity: choose the simplest design that meets the required security, reliability, performance, cost, and maintenance boundaries.
38. For high- or very-high-risk architecture, require an independent architecture review by a different model or reviewer before setup begins.
39. Default to beginner guidance when the user has not demonstrated development experience. Read `references/beginner-guidance.md`; take responsibility for the technical route while the user supplies intent, confirmations, and acceptance feedback.
40. Give beginners one recommended tool path at a time, explain it in plain language, and provide a copy-ready prompt. Mention alternatives only when the recommended path is unavailable, too costly, or materially risky.
41. Use parallel agents only when independent work can reduce elapsed time without creating integration or cost risk. Read `references/parallel-agent-orchestration.md` before proposing or running parallel work.
42. Assign one coordinator agent as the sole owner of `项目状态.md`, `项目路径索引.md`, `决策记录.md`, `AI执行清单-进度表.md`, and final integration decisions.
43. Treat each parallel worker as an independent context, even when it uses the same AI model. Give it a `PAR-*` ID, read-only inputs, exclusive write scope, exact outputs, task lock, budget, and completion report.
44. Do not claim work is parallel when the platform cannot start independent agents or sessions. In that case, execute the same lanes sequentially and say so plainly.
45. Merge no parallel coding result until the coordinator has verified the worker evidence, resolved overlaps, run the required integration checks, and updated the state documents.
46. Default to coordinator-led execution: use one controlled parallel wave when the eligibility gate proves tasks are independent; otherwise use single-thread work. Support the user commands `自动判断并行`, `强制单线`, `优先省钱`, and `使用 ultra`; record the selected mode and its cost impact before starting workers.
47. Freeze shared contracts before parallel implementation: database schema, auth, shared types, core API contracts, public component interfaces, environment variables, and deployment configuration have one coordinator owner and are never edited by parallel workers.
48. Give every parallel task a timeout, maximum model rounds, cost ceiling, fallback owner, and stop condition. On timeout, missing evidence, or budget breach, stop that task and downgrade it to coordinator-led sequential work.
49. Before merging a parallel result, compare its requirement IDs, architecture decisions, API/types, changed-file scope, tests, and Git diff against the `PAR-*` plan. Resolve every conflict before integration.
50. Treat model capability detection as evidence-based: detect it from available platform/tool information when possible; otherwise ask the user to confirm the visible model option instead of claiming `ultra` is available.
51. Treat product, functional, technical, interaction, and visual design as first-class deliverables. Before designing or implementing a non-trivial product, read `references/product-design-quality.md`.
52. Do not accept a product that merely runs. A beautiful but incomplete flow and a functional but generic/ugly interface both fail the design-quality gate.
53. Design for the actual product context, user task, and emotional tone. Do not reuse a generic dashboard, landing page, information hierarchy, or architecture pattern without proving it fits the approved requirements.
54. Validate core functions with realistic inputs and user journeys, and validate visible interfaces with desktop/mobile screenshots or browser evidence against the approved design direction.
55. Before final acceptance, produce `PROJECT_ROOT/docs/20-设计品质验收.md` covering product usefulness, functional completeness, architecture fitness, interaction quality, visual quality, and remaining design debt.
56. Before implementing a visible interface, read `references/interaction-control-spec.md` and create `PROJECT_ROOT/docs/06-交互控件规格.md`. Give every user-operable button, link, input, toggle, menu, upload control, and destructive action a `UI-CTRL-*` specification.
57. Do not accept a visible control that has no explicit user purpose, trigger/result, permission rule, state behavior, recovery behavior, accessibility behavior, and acceptance evidence. Decorative or dead controls are forbidden.
58. Trace each meaningful `UI-CTRL-*` to its `REQ-*`, feature card, component/file, and test or browser evidence.
59. Treat plans and documents as means, not delivery. Before creating major planning, architecture, UI, or review artifacts, read `references/delivery-grounding.md` and add implementation anchors to real code, tests, commands, URLs, packages, or user-verifiable outcomes.
60. Do not mark a requirement, card, design decision, or review fix complete merely because a document exists. It is complete only when its declared implementation anchor and acceptance evidence exist.
61. Start a testable first vertical slice as soon as the architecture gate passes. Do not keep generating diagrams, prompts, or plans when the next useful action is to create, run, test, or verify a real project artifact.
62. Reject decorative architecture: every module, service, document, tool, parallel worker, and UI element must have a stated user/product purpose, owner, cost/risk reason, implementation location, and verification path.
63. For client work, treat every statement not written in the approved scope, acceptance criteria, or change record as uncommitted. Do not quietly absorb new features, integrations, data cleanup, content entry, account setup, deployment, or support as “small extras”.
64. Separate business guidance from legal advice. The Skill may prepare a scope, quote, risk register, change record, and contract-review checklist, but must tell the user to have a qualified local professional review the final contract and high-stakes terms.
65. Maintain one client-project risk register at `PROJECT_ROOT/docs/00-项目风险总表.md` from first contact to closeout. Every material risk needs an ID, owner, trigger, prevention, fallback, evidence, and current decision.
66. Do not pass a project gate with an unowned P0 risk. P1 risks require a mitigation plan and explicit decision; P2 risks require a scheduled owner/checkpoint. A risk can be accepted only by the project owner/client, never silently by an AI.
67. Before changing code, read `references/code-delivery-standards.md` and enforce its change boundary, security, data, dependency, test, review, commit, and evidence rules. Create `PROJECT_ROOT/docs/24-代码质量与变更控制.md` for every non-trivial project.
68. Do not accept “it runs on my machine” as code quality. A code change is complete only when it maps to approved scope/requirements, follows local project conventions, has proportionate verification, and has no unresolved critical security/data/regression risk.
69. Before approving a high-cost requirement, quote, delivery boundary, architecture, data/auth boundary, or material change, run the decision grill in `references/decision-grill-and-glossary.md`. Write durable terms to `PROJECT_ROOT/项目术语表.md`, decision records to `PROJECT_ROOT/决策记录.md`, and the session evidence to `PROJECT_ROOT/docs/25-关键决策压测记录.md`.
70. Use the decision grill to remove ambiguity, not to delay work. Research existing project artifacts first; ask one high-leverage question at a time only when the answer can alter scope, cost, acceptance, risk, or architecture. Create an ADR only for a difficult-to-reverse decision.
71. For every non-trivial product, read `references/module-evolution-and-upgrade-safety.md` before architecture approval. Define independent `MOD-*` modules, their ownership/contracts/data boundaries, test boundaries, and permitted dependencies in `PROJECT_ROOT/docs/26-模块契约与升级方案.md`.
72. Treat a V2 install or deployment as an upgrade, never as a fresh install. Separate program files from user/project data; preserve data by default; require versioned, idempotent migrations, backup/restore evidence, compatibility checks, and rollback before releasing an upgrade that touches stored data.
73. For a user's own product idea, run commercial feasibility, current market validation, and competitive positioning before confirming a PRD or recommending implementation. Read `references/market-feasibility-gate.md` and `references/competitive-positioning.md`, write `PROJECT_ROOT/docs/00-可行性与市场验证.md` and `PROJECT_ROOT/docs/00-竞品对比与差异化策略.md`, and give a clear Go / Validate First / No-Go decision with evidence, confidence, and the smallest next action.
74. Do not build a commercial product merely because it is technically possible. If the feasibility gate is No-Go, explicitly recommend not starting full development. The user may override only by recording it as a time- and cost-capped experiment or personal-learning project, not as an evidence-backed business bet.
75. Apply `references/evidence-and-boundary-honesty.md` to every meaningful feasibility, quote, delivery, architecture, model/tool, security, cost, timeline, and launch claim. Label it as 已验证可做 / 可做但需验证 / 当前不可承诺 / 明确不可做; never turn an assumption, model suggestion, marketing claim, or untested possibility into a promise.
76. State the real boundary before proposing work: what evidence exists, what is missing, which external party/tool/account/data/permission controls the outcome, what cannot be guaranteed, and the smallest safe validation. Refuse or pause when the requested result is impossible, unsafe, unavailable, outside the approved scope, or lacks enough evidence for the claimed commitment.
77. Do not accept “we have more features” or “use AI” as a competitive advantage. For a commercial idea, identify a specific target segment, inferior current alternative, differentiated outcome/workflow/channel/trust/data/service/cost position, and first-customer reach path. If no credible wedge exists, explicitly recommend narrowing, validating, or stopping.
78. For a new external client inquiry, qualify the opportunity before giving away a detailed solution, UI, architecture, scope map, or line-item quote. Read `references/client-opportunity-qualification.md`, keep `PROJECT_ROOT/docs/00-商机评分与沟通记录.md`, and move from chat -> qualification -> one-page brief -> scoped quote -> agreed start condition -> delivery only when the evidence supports the next stage.
79. Do not mistake free pre-sales work for progress. Low-quality or unqualified inquiries receive concise clarification questions or a polite pause/decline, not a free complete plan. Start implementation only after approved scope/boundary and the agreed commercial start condition, such as a deposit, purchase order, signed agreement, or another documented client commitment.
80. Keep the user experience simple while keeping project governance strict. Before replying with a step, read `references/user-facing-navigation.md`. Show one current action card by default; keep governance, locks, matrices, and audit detail in project artifacts unless the user asks to `展开执行详情` or the task is high-risk.
81. Never hide the essential handoff instruction: when the user must send work to another AI, include one copy-ready prompt containing the exact input paths, output path, completion standard, and report-back format. Do not expose unrelated internal framework detail in that prompt.
82. Treat tool arrangement as an execution contract, not a suggestion. Before a step starts, read `references/tool-dispatch-execution.md`, convert each abstract role into one concrete detected tool or explicit fallback, and record the selected tool, model/reasoning level, input, output path, owner, status, and verification in `AI执行清单-进度表.md` and `项目状态.md`.
83. Do work with the current agent whenever it has the required file, command, browser, or coding capability and the user has approved the step. Do not send the user to another AI merely to repeat work this agent can complete. When a selected tool cannot be opened or controlled, state `工具阻塞` with the exact reason and provide the smallest copy-ready handoff; never claim dispatch, execution, or verification without evidence.
84. Scan before dispatch. At the beginning of every project, run and save a non-destructive local tool/capability scan before assigning any tool, model, plugin, MCP, parallel worker, or external handoff. Do not ask the user to open, install, pay for, or send work to a tool that was not detected or explicitly confirmed as browser-available.
85. Make every parallel worker deliver to a named project location, never only to chat. Before dispatch, create its `docs/并行任务/PAR-XXX-任务与交付.md`; for code, assign a dedicated branch/worktree or exclusive source scope. The coordinator must assemble only from these saved delivery records, verified artifacts, and controlled Git merges, then write the integrated result to `docs/08-总装集成.md`.
86. Route every project before creating its execution plan. Read `references/project-complexity-router.md`, select the lightest route that safely fits the project, save the provisional/final route in `PROJECT_ROOT/docs/00-项目路由与治理级别.md`, and enable only its required modules. Do not impose client, parallel, production, high-risk, or advanced-document gates on a simple project unless its actual signals require them.
87. Never save generated project documents inside an AI skill folder, user profile tool folder, temporary folder, downloads folder, agent-private workspace, or browser attachment area. Save them to the D-drive `PROJECT_ROOT`, link any separate `CODE_ROOT` from `项目路径索引.md`, and put both absolute roots in every cross-AI handoff.

## Project Entry Modes

Use exactly one entry mode at a time. Project type, delivery level, and budget mode are later classifications; they do not replace the entry mode.

| Mode | Trigger and starting material | AI responsibility | First artifact | Do Not Do |
| --- | --- | --- | --- | --- |
| A. 想法落地 | “我想做一个…”, “我有个想法…”, vague personal/business idea | ask, challenge, validate market/value and competitive wedge when it is intended as a product, then refine it into a product hypothesis, MVP, requirements, and plan | `docs/00-创意澄清与立项.md`, `docs/00-可行性与市场验证.md`, and `docs/00-竞品对比与差异化策略.md` | pretend vague wishes are confirmed requirements; build a commercial product before its feasibility/competition gate; quote it as client work |
| B. 客户交付 | “客户/甲方要做…”, requirement doc, quote/contract/acceptance request, existing client brief | preserve the client source, decompose it, expose gaps/contradictions, set scope/quote/acceptance/risk boundaries, then plan delivery | `docs/00-客户需求原文与拆解.md` | silently redesign the client's brief, add unapproved scope, or start fixed-price work before the commercial gate |

Automatic selection:

- Choose **想法落地** when the user describes something they personally want to create and gives no client/delivery signals.
- Choose **客户交付** when the user provides another party's requirements or uses client-delivery signals.
- If both are plausible, ask exactly: `这是你自己的产品想法，还是客户委托项目？` Do not ask generic requirement questions until the answer is known.
- Do not switch modes silently. A switch requires a reason, user confirmation, and an update to `项目状态.md`, `决策记录.md`, and affected scope/quote documents.

## New Project Flow

When the user says “我要做一个 X” or “想做一个 X”:

1. Read `references/document-storage-policy.md`, determine the D-drive `PROJECT_ROOT`, determine `CODE_ROOT`, write both to `项目路径索引.md`, and lock the entry mode.
2. Run the Tool Scan before asking the user to use any tool. Save concrete detected tools, usable capabilities, account/login blockers, and fallbacks to `PROJECT_ROOT/docs/00-工具与权限扫描.md`; link it from `项目路径索引.md`.
3. Read `references/project-complexity-router.md` and record a provisional route from the known scope, risk, entry mode, and tool scan. Use it only to keep the discovery process proportionate; finalize it after requirement confirmation.
4. For **想法落地**, read `references/idea-to-product-discovery.md` and `references/requirements-intake-template.md`, then ask small rounds of product-discovery questions. Do not ask more than 4 questions at once.
5. For **客户交付**, read `references/client-requirement-decomposition.md`; first preserve and decompose every client source, then ask only the high-impact gaps about scope, acceptance, dependency, timeline, budget, authority, and risk.
6. If any required function or acceptance detail is unclear, ask supplemental questions. Do not guess silently.
7. For a commercial/product **想法落地** project, read `references/market-feasibility-gate.md` and `references/competitive-positioning.md`, research the current market and alternatives, and create `PROJECT_ROOT/docs/00-可行性与市场验证.md` plus `PROJECT_ROOT/docs/00-竞品对比与差异化策略.md` before PRD confirmation. For an explicitly personal/learning/internal project, record the non-commercial value, time/cost cap, and why market validation is not required.
8. Once the relevant gate passes, create the mode-specific `docs/00-*` artifact and immediately create `PROJECT_ROOT/docs/01-PRD产品需求文档.md` as 《PRD产品需求文档》 in the same response/action. Do not ask the user to issue a separate command.
9. In **客户交付** mode, also complete the commercial/risk gate before PRD confirmation; in **想法落地** mode, show the feasibility decision, evidence confidence, product hypothesis, MVP, and risks for confirmation.
10. Ask the user to confirm the requirements are correct or point out corrections.
11. After confirmation, refresh only the tool availability that has changed, then classify project type, budget mode, delivery level, and the lightest safe project route. Save `docs/00-项目路由与治理级别.md`.
12. Immediately create `PROJECT_ROOT/AI执行清单-进度表.md` as 《AI执行清单/进度表》 after confirmation. Do not wait for a separate command.
13. Only after the execution plan exists, produce or advance the route-specific step map.

### Requirement Intake

Collect enough detail to prevent rework, but keep the conversation easy for a normal user. Ask in rounds and stop each round after at most 4 questions.

Before generating the PRD, cover these areas from `references/requirements-intake-template.md`:

- purpose and target user
- current pain and desired outcome
- main user journey
- MVP features and out-of-scope items
- platform, device, and environment
- data, files, permissions, login, payment, admin, AI/API needs
- UI style expectations for interface projects
- budget mode, delivery level, deadline, and constraints
- acceptance criteria and evidence

Use progressive detail:

1. First ask the minimum 4 questions needed to understand the project.
2. Then ask follow-up rounds only for missing high-impact details.
3. If the user says “你来定”, infer a conservative default and mark it as `AI默认建议，待确认`.
4. Do not block forever on low-risk details; put unknowns into `Open Questions`.

Supplemental questions are mandatory when these are unclear:

- What exact functions must exist in version 1?
- What should happen before, during, and after each main user action?
- What data or files are created, stored, edited, deleted, imported, or exported?
- Who can do what, and whether login/admin/payment/permissions are needed?
- What visible result proves the function worked?
- What style/experience is expected for interface projects?
- What counts as unacceptable output?

After enough answers, output:

```markdown
## 需求确认

- 项目目标：
- 目标用户：
- 核心场景：
- 用户操作流程：
- MVP 功能：
- 不做范围：
- 数据/文件/权限：
- UI风格方向：
- 交付物：
- 成功标准：
- 验收方式：
- 风险和约束：
- 项目类型：
- 预算模式：
- 交付等级：
- 待确认问题：

如果以上理解正确，我将开始按你的工具生成全链路地图。
```

## Client Delivery Router

Trigger this route when the user says `客户`, `甲方`, `接单`, `外包`, `报价`, `合同`, `交付`, `验收`, or describes building for another person or company. Keep one installation package, but run these internal modules in order:

| Module | Read | Auto-created artifact | Gate |
| --- | --- | --- | --- |
| -1. 商机筛选 | `references/client-opportunity-qualification.md` | `docs/00-商机评分与沟通记录.md` | scene, decision authority, timing, budget fit, acceptance, payment/start commitment, and communication readiness justify the next stage |
| 0. 客户需求基线 | `references/client-requirement-decomposition.md` | `docs/00-客户需求原文与拆解.md` | every source statement is preserved, mapped, or marked ambiguous/out of scope |
| 1. 需求立项 | `references/client-discovery-and-scope.md` | `docs/00-合作立项与需求访谈.md` | client problem, decision-maker, scope, constraints, and success are concrete |
| 2. 报价风控 | `references/project-pricing-risk.md` | `docs/00-报价与风险评估.md` | estimate basis, assumptions, third-party costs, risks, payment milestones, and decline conditions are explicit |
| 3. 交付边界 | `references/client-delivery-boundaries.md` | `docs/00-交付边界与验收.md` and `docs/00-需求变更单.md` | included/excluded work, acceptance cases, client responsibilities, ownership, support, and change process are approved |
| 4. 风险治理 | `references/project-risk-governance.md` | `docs/00-项目风险总表.md` | every P0/P1 risk has an owner, decision, and stop/fallback condition |
| 5. 执行交付 | normal project workflow | PRD, execution plan, cards, code, test, release, final handover | only approved scope enters development |

### STEP 0 - 合作立项

Before the normal 10-step map, ask no more than four questions per round. Establish:

- client, decision-maker, target user, and the painful business task
- required result, explicit non-goals, deadline, budget range, and delivery level
- client-provided materials, accounts, content, data, approvals, and external vendors
- acceptance examples, who signs off, payment preference, ownership, support expectation, and known risks

Use `references/client-requirement-decomposition.md`, `references/client-discovery-and-scope.md`, `references/project-pricing-risk.md`, `references/client-delivery-boundaries.md`, and `references/project-risk-governance.md`. Once enough answers exist, automatically create the five `docs/00-*` artifacts, show their paths and the unresolved items, then ask for approval of scope, commercial assumptions, and P0/P1 risk decisions before generating the technical PRD.

Do not ask the client-facing user to understand technical estimates. Explain each risk in plain language and provide one recommended decision.

### STEP -1 - 询盘筛选

For a new client inquiry, read `references/client-opportunity-qualification.md` before full discovery. Record the inquiry and decide the next allowed stage:

- `继续澄清`: information is insufficient; ask at most three high-value questions.
- `发送一页说明`: the opportunity is plausible but not ready for a detailed solution/quote.
- `正式范围与报价`: the opportunity is qualified; begin the normal client baseline, scope, risk, and quote flow.
- `暂停/婉拒`: fit, budget, authority, timing, payment/start intent, or risk is not sufficient; do not do unpaid design work.

Do not make an elaborate Word document, UI mockup, architecture, feature breakdown, or detailed line-item quote during `继续澄清` or `发送一页说明`. A one-page brief may state the problem, intended outcome, broad collaboration direction, key unknowns, and next decision only; it must not reveal a free implementation blueprint.

## Project Type Router

Classify the project before planning. Use the classification to skip irrelevant tools and steps.

| Type | Use When | Route |
| --- | --- | --- |
| Script/CLI | one-off automation, batch task, developer tool | requirements -> inputs/outputs -> script -> tests -> package/docs |
| Website/content | landing page, blog, docs, portfolio | content structure -> UI -> build -> responsive check -> deploy |
| Product/SaaS/app | users, auth, data, billing, repeated use | product framework -> architecture -> cards -> integration -> review |
| Client delivery | a project is commissioned by another person/company | STEP 0 commercial gate -> approved PRD -> cards -> acceptance -> handover |
| Inherited project | existing repo, client code, open source | teardown -> risk map -> smallest safe change -> review |
| AI project | model calls, agents, RAG, image/audio | data/privacy -> model/tool choice -> evals -> cost controls -> fallback |

Save classification to `项目状态.md` and, for new products, `docs/02-产品框架.md`.

## Budget Mode

Ask or infer the budget mode. If unclear, default to balanced.

| Mode | Behavior |
| --- | --- |
| Save money | use low/normal reasoning except architecture and final review; avoid paid tools and unnecessary MCPs |
| Balanced | high reasoning for planning/review/debugging; normal reasoning for routine edits |
| Safest | high or very high reasoning for architecture, security, integration, review, deploy, and inherited projects |

Never recommend a costly tool unless it directly reduces risk, time, or rework.

## Delivery Levels

Ask what level the user wants. This controls quality gates and tool depth.

| Level | Standard |
| --- | --- |
| Demo | can show the main idea locally or in a simple URL; light tests acceptable |
| MVP | core user journey works end to end; basic tests and deployment notes required |
| Beta | real users can try it; auth/data/error handling/logs required |
| Production | stable public use; security, monitoring, rollback, cost review, and mature review required |

Do not overbuild a Demo as Production. Do not treat Production as a toy demo.

## Tool Scan

Run what is safe and available. On Windows, use `where` and common install paths; on Unix-like shells, use `which`.

Check:

- Terminal AI: `zcode`, `claude`, `codex`, `aider`
- IDE: Cursor, VS Code, Windsurf
- Desktop apps: GitHub Desktop, Claude Desktop, ChatGPT Desktop
- CLI: `git --version`, `node --version`, `npm --version`, `pnpm --version`, `docker --version`
- Project management: Workbuddy, Notion, GitHub Issues, local Markdown fallback
- Browser tools, usually available: v0.dev, Bolt.new, Vercel, Railway, Render, Netlify, Cloudflare Pages
- MCP/plugin availability when visible: GitHub, Notion, Figma, Browser, Playwright, Sentry, Linear
- Parallel-agent capability: GPT-5.6 `ultra` availability, subagents, task agents, separate AI sessions, Git branches/worktrees, and whether workers can read/write the project root

Output:

```markdown
## 工具扫描结果

- 终端 AI：
- IDE：
- 桌面 APP：
- 命令行：
- 项目管理：
- 浏览器工具：
- 可用 MCP/插件/Skill：
- 模型/并行执行能力：已检测到 / 需要用户在模型选择中确认
- 缺失项与替代方案：
```

## Tool Choice By Difficulty

Use the cheapest sufficient tool. Raise reasoning only for decisions, architecture, safety, and hard debugging.

| Difficulty | Work | Tool Choice | Reasoning Accuracy | Cost Rule |
| --- | --- | --- | --- | --- |
| Low | copy, style, single-file edits | AI IDE or low-cost chat | medium/high | no deep reasoning |
| Medium | normal feature, CRUD, page + API | AI IDE + terminal AI | high | high reasoning for plan/review only |
| High | cross-file feature, auth, DB, deployment | terminal AI + AI IDE + tests | high/very high | use very high only for architecture and review |
| Very high | security, production bug, inherited project, major refactor | terminal AI + second-model review + tests | very high | spend only on critical decisions |

Match tools correctly:

- Single file: AI IDE.
- Cross-file planning, commands, audits: terminal AI.
- UI draft: v0.dev/Bolt.new, then integrate in IDE.
- Product/architecture: terminal AI with high or very high reasoning.
- Mature review: terminal AI plus different-vendor model.
- Project tracking: Workbuddy/Notion/GitHub Issues; canonical Markdown sync is `AI执行清单-进度表.md`.

## Tool Dispatch And Execution

Before any approved action, read `references/tool-dispatch-execution.md`.

For every step:

1. Use the tool scan to choose an actual available tool. Do not show only a role such as “终端 AI” when a concrete tool is known.
2. Write one `TOOL-*` dispatch row to `AI执行清单-进度表.md` and summarize its current status in `项目状态.md`.
3. Give the current agent the task first if it can safely perform it in the active workspace. Execute it, save the artifact, and report evidence after user approval.
4. When another tool/AI is necessary, provide the compact handoff packet with exact paths. Mark it `已派发`, not `已完成`.
5. Mark a dispatch `已验证` only after the required artifact and evidence are read or observed. A user saying “sent” is evidence of dispatch, not completion.
6. If a tool is missing, blocked, unauthenticated, unavailable, or too costly, choose the stated fallback and record why. Do not wait silently or pretend the tool ran.

The compact action card must name the selected concrete tool, why it is used in one short phrase, and the expected result. Keep all dispatch mechanics in project files unless the user asks to expand them.

## Project Route Selection

Before creating the execution checklist, read `references/project-complexity-router.md` and select a route. The route controls how much process, documentation, review, tool setup, parallelism, and release governance is required.

Show the user only the selected route and one-sentence reason. Keep the detailed scoring and skipped-module rationale in `docs/00-项目路由与治理级别.md`.

Do not route upward because a more elaborate workflow looks professional. Route upward only when real scope, client commitment, user/data impact, money, production exposure, technical uncertainty, or integration risk requires it. Re-evaluate the route when those facts materially change.

## Beginner Guidance Mode

When the user is new to AI development, do not make them act as architect, programmer, or tool selector. Before the first proposal, read `references/beginner-guidance.md`.

In this mode:

- Ask about the desired result in everyday language. Translate it into product and technical decisions yourself, then show the user what you understood for confirmation.
- Recommend one primary route using tools that were actually found in the tool scan. Do not present a comparison table unless the user asks or the primary route cannot work.
- Preserve the full path-first execution format. Beginner guidance never replaces the required tool chain, copy-ready prompt, exact output name, absolute save path, completion signal, handoff packet, completion report, or next-step proposal.
- For every step, say what will happen, why it matters, exactly what to copy/open/paste, where the result is saved, and what ordinary evidence proves success.
- Explain unfamiliar terms in one short sentence when they first appear. Never make the user install a plugin, pay for a service, choose a model, edit configuration, or run a destructive command without a plain-language reason and approval point.
- Keep learning embedded in the work: after a completed step, explain in one sentence what the result means. Do not turn the project into a long course or delay delivery for teaching.
- When something fails, ask for the exact visible error, screenshot, command output, or path; do not tell a beginner to “debug it” alone.

## Architecture Selection

Before writing `PROJECT_ROOT/docs/03-技术架构.md`, read `references/architecture-playbooks.md` and `references/architecture-decision-standard.md`. When AI, automation, knowledge, or Agent behavior is a core product capability, also read `references/ai-solution-layering.md`.

Pick the best-fit mature architecture for the detected project type, delivery level, budget mode, team size, data sensitivity, and expected scale. “Best” means simplest architecture that satisfies the requirements and quality gates with the lowest long-term cost and risk.

The architecture document must include:

- selected architecture pattern
- why it fits this project
- alternatives rejected and why
- stack recommendation
- data model boundaries
- API/component boundaries
- deployment shape
- scaling path
- security and cost notes
- requirement IDs and the feature cards that implement them
- critical user journeys and failure/recovery behavior
- non-functional budgets for performance, reliability, security, cost, and maintainability
- decision IDs, alternatives, consequences, and review status

Do not choose novelty, microservices, queues, Kubernetes, vector databases, or multi-model agent systems unless the requirements justify them.

Before setup, record the architecture gate result in `docs/03-技术架构.md` and `决策记录.md`. Do not begin implementation until the core flows, data ownership, interfaces, failure behavior, and first vertical slice are clear enough for another AI to implement without inventing product rules.

## Deliverable Locations

Every step must say where the output is saved. Use absolute paths whenever `PROJECT_ROOT` is known.

Before writing documents, determine `PROJECT_ROOT`:

- New project: default to `D:\AI项目\[项目名]`; set `PROJECT_ROOT` and `CODE_ROOT` to this folder unless the user provides another D-drive location.
- Existing project outside D drive: keep source in its existing `CODE_ROOT`, but create `PROJECT_ROOT` at `D:\AI项目文档库\[项目名]` and link both absolute roots in `项目路径索引.md`.
- User-provided D-drive project root: use it as `PROJECT_ROOT`; use it as `CODE_ROOT` when it contains the source.
- If a non-D document location is explicitly requested, ask once whether the user wants an exception; otherwise retain the D-drive policy.

Do not leave project artifacts only in the agent workspace, temporary directories, downloads, chat attachments, or `.codex/visualizations`. If another tool saves an artifact elsewhere, copy or move the useful result back under `PROJECT_ROOT` and record the source in `项目状态.md`.

At project start, create the standard artifact structure when possible:

```text
PROJECT_ROOT/
├── 项目状态.md
├── 项目路径索引.md
├── 决策记录.md
├── AI执行清单-进度表.md
└── docs/
```

| Stage | Artifact | Save Location |
| --- | --- | --- |
| Project state | current step, completed steps, next step, decisions | `PROJECT_ROOT/项目状态.md` |
| Path index | canonical project root, docs, code paths, outputs, URLs, agent handoff locations | `PROJECT_ROOT/项目路径索引.md` |
| Tool and permission scan | detected local tools, login/permission state, browser-available services, fallbacks | `PROJECT_ROOT/docs/00-工具与权限扫描.md` |
| Decisions | stable architecture/product/tool decisions | `PROJECT_ROOT/决策记录.md` |
| Change record | requirement changes, scope drift, affected cards, approvals | `PROJECT_ROOT/变更记录.md` |
| Idea discovery | original idea, product hypothesis, user problem, MVP, non-goals, assumptions, and confirmation | `PROJECT_ROOT/docs/00-创意澄清与立项.md` |
| Market feasibility | market/user/alternative/monetization/distribution/cost evidence, confidence, and Go/Validate First/No-Go decision | `PROJECT_ROOT/docs/00-可行性与市场验证.md` |
| Competitive positioning | direct/indirect/free alternatives, target segment, comparison evidence, differentiated wedge, and first-user reach path | `PROJECT_ROOT/docs/00-竞品对比与差异化策略.md` |
| Client requirement baseline | original client statements, source links, requirement mapping, ambiguity, contradiction, and approval status | `PROJECT_ROOT/docs/00-客户需求原文与拆解.md` |
| Client requirement interview | client problem, goals, decision-maker, materials, constraints, and open questions | `PROJECT_ROOT/docs/00-合作立项与需求访谈.md` |
| Opportunity qualification | inquiry source, score, stage, questions, one-page brief, follow-up, and decline/pause reason | `PROJECT_ROOT/docs/00-商机评分与沟通记录.md` |
| One-page client brief | concise problem/outcome/collaboration direction and next decision without free implementation blueprint | `PROJECT_ROOT/docs/00-一页项目说明.md` |
| Quote and risk | estimate basis, included cost, assumptions, third-party cost, risk score, payment milestones, and decline conditions | `PROJECT_ROOT/docs/00-报价与风险评估.md` |
| Delivery boundary and acceptance | included/excluded scope, acceptance examples, client responsibilities, ownership, support, and sign-off | `PROJECT_ROOT/docs/00-交付边界与验收.md` |
| Change request | requested change, scope/cost/date impact, approval, and implementation record | `PROJECT_ROOT/docs/00-需求变更单.md` |
| Project risk register | business, scope, payment, legal/compliance, data, technical, delivery, release, and support risks with owner and fallback | `PROJECT_ROOT/docs/00-项目风险总表.md` |
| Requirements | PRD, MVP, out-of-scope, acceptance | `PROJECT_ROOT/docs/01-PRD产品需求文档.md` |
| AI execution plan | dashboard, task table, priorities, deliverables, roles, progress | `PROJECT_ROOT/AI执行清单-进度表.md` |
| Feature split | vertical feature cards | included in `PROJECT_ROOT/AI执行清单-进度表.md` |
| Product framework | users, scenarios, value, business objects | `PROJECT_ROOT/docs/02-产品框架.md` |
| Architecture | stack, structure, data model, API sketch | `PROJECT_ROOT/docs/03-技术架构.md` |
| Setup | commands, dependencies, env vars | `PROJECT_ROOT/docs/04-初始化设置.md` |
| Feature work | per-card plan, commit links | `PROJECT_ROOT/docs/05-功能开发记录.md` |
| UI style | visual style direction, layout rules, component tone, screenshots | `PROJECT_ROOT/docs/06-UI风格方案.md` |
| Interaction controls | every operable control's purpose, states, behavior, accessibility, and evidence | `PROJECT_ROOT/docs/06-交互控件规格.md` |
| UI implementation | page flow, components, states | `PROJECT_ROOT/docs/06-界面设计.md` |
| Tests | test plan and coverage | `PROJECT_ROOT/docs/07-测试计划.md` |
| Product assembly | integration plan, wiring checklist, full product verification | `PROJECT_ROOT/docs/08-总装集成.md` |
| Review | findings, severity, fixes | `PROJECT_ROOT/docs/09-成熟产品审查.md` |
| Deploy | URL, env, rollback, ops notes | `PROJECT_ROOT/docs/10-部署落地.md` |
| Retro | done, risks, next iteration | `PROJECT_ROOT/docs/11-项目复盘.md` |
| User guide | how to install, run, use, troubleshoot | `PROJECT_ROOT/docs/12-使用说明.md` |
| Final deliverable | final product URL/package/version/commit/acceptance evidence | `PROJECT_ROOT/docs/13-完成品文档.md` |
| Engineering readiness | env, secrets, migrations, CI, logs, rollback, maintenance | `PROJECT_ROOT/docs/14-工程保障清单.md` |
| Cross-AI handoff log | prompts sent to other agents, source docs, target paths, returned results | `PROJECT_ROOT/docs/15-跨AI交接记录.md` |
| Final difference review | approved PRD vs actual delivery, missing/extra items, accepted risks | `PROJECT_ROOT/docs/16-最终差异审查.md` |
| Requirement traceability | requirement ID to cards, tests, review evidence, and delivery result | `PROJECT_ROOT/docs/17-需求追踪矩阵.md` |
| Parallel plan | mode decision, agent roles, task graph, locks, branches, budgets, and target paths | `PROJECT_ROOT/docs/18-并行协作计划.md` |
| Parallel result summary | worker evidence, conflicts, merge decision, and integration status | `PROJECT_ROOT/docs/19-并行结果汇总.md` |
| Design-quality acceptance | product, function, architecture, interaction, and UI evidence | `PROJECT_ROOT/docs/20-设计品质验收.md` |
| Delivery grounding | requirements/designs/cards/review fixes mapped to actual implementation and evidence | `PROJECT_ROOT/docs/21-落地验证清单.md` |
| Release preflight | environment separation, secrets, release safety, observability, storage, and Web experience evidence | `PROJECT_ROOT/docs/22-发布前体检.md` |
| Client handover and closeout | accepted scope, delivery inventory, account/asset/source transfer, support end, and remaining risks | `PROJECT_ROOT/docs/23-客户交付与结项.md` |
| Code quality and change control | code conventions, allowed change scope, dependency/data/security checks, test/review/commit evidence | `PROJECT_ROOT/docs/24-代码质量与变更控制.md` |
| Project glossary | canonical domain terms, definition, allowed aliases, owner, source, and status for cross-AI consistency | `PROJECT_ROOT/项目术语表.md` |
| Decision grill | assumptions challenged, scenarios tested, alternatives, resolved decisions, and open risks | `PROJECT_ROOT/docs/25-关键决策压测记录.md` |
| Module contracts and upgrade safety | module ownership/contracts, independent test scope, data location, migration, compatibility, backup, and rollback evidence | `PROJECT_ROOT/docs/26-模块契约与升级方案.md` |
| Project master doc | one project overview linking all subdocs | `PROJECT_ROOT/项目总文档.md` |
| Global projects index | index of all project master docs | `PROJECTS_HUB_ROOT/所有项目总索引.md` |

If using PM tools, still keep the stable conclusions in project Markdown.

## Auto Artifact Generation

Do not make the user ask twice for obvious phase artifacts.

When the required information for a phase is available, automatically create or update that phase document in the same turn:

- after requirement answers are sufficient: write `PROJECT_ROOT/docs/01-PRD产品需求文档.md`
- for 想法落地, after product-discovery answers are sufficient and before PRD confirmation: write `PROJECT_ROOT/docs/00-创意澄清与立项.md` using `references/idea-to-product-discovery.md`
- for a commercial/product 想法落地 project, after product discovery and before PRD confirmation: research current market/alternative evidence and write `PROJECT_ROOT/docs/00-可行性与市场验证.md` plus `PROJECT_ROOT/docs/00-竞品对比与差异化策略.md` using `references/market-feasibility-gate.md` and `references/competitive-positioning.md`; a No-Go or no credible competitive wedge blocks PRD/development unless the user records a bounded experiment override
- for 客户交付, after STEP 0 answers are sufficient and before PRD confirmation: write `PROJECT_ROOT/docs/00-客户需求原文与拆解.md`, `PROJECT_ROOT/docs/00-合作立项与需求访谈.md`, `PROJECT_ROOT/docs/00-报价与风险评估.md`, `PROJECT_ROOT/docs/00-交付边界与验收.md`, an empty `PROJECT_ROOT/docs/00-需求变更单.md`, and `PROJECT_ROOT/docs/00-项目风险总表.md` using the five client-delivery references
- for a new 客户交付 inquiry, before STEP 0 and before any detailed solution: write/update `PROJECT_ROOT/docs/00-商机评分与沟通记录.md`; create `PROJECT_ROOT/docs/00-一页项目说明.md` only when the qualification stage calls for it
- after the PRD is written: create `PROJECT_ROOT/docs/17-需求追踪矩阵.md` with requirement IDs and an initial implementation/test/review mapping
- after requirements are confirmed: write `PROJECT_ROOT/AI执行清单-进度表.md`
- after a complex project is approved for parallel work: write `PROJECT_ROOT/docs/18-并行协作计划.md` before starting any worker
- after parallel workers return: write `PROJECT_ROOT/docs/19-并行结果汇总.md` before implementation integration or the next phase
- after integration and before mature review: write `PROJECT_ROOT/docs/20-设计品质验收.md` using `references/product-design-quality.md`
- before final acceptance: write `PROJECT_ROOT/docs/21-落地验证清单.md` using `references/delivery-grounding.md`
- after mature review and before deployment/public release: write `PROJECT_ROOT/docs/22-发布前体检.md` using `references/release-preflight.md`; show the findings and ask for approval before any remediation
- after product questions are answered: write `PROJECT_ROOT/docs/02-产品框架.md`
- after architecture inputs are clear: write `PROJECT_ROOT/docs/03-技术架构.md`
- after UI style inputs are clear for an interface project: write `PROJECT_ROOT/docs/06-UI风格方案.md`
- after UI style direction is approved: write `PROJECT_ROOT/docs/06-交互控件规格.md` before implementing screens or controls
- after a card is completed: update `PROJECT_ROOT/docs/05-功能开发记录.md` and `PROJECT_ROOT/AI执行清单-进度表.md`
- before the first implementation card: create `PROJECT_ROOT/docs/24-代码质量与变更控制.md` using `references/code-delivery-standards.md`; update it after any exception, dependency, migration, security finding, or quality-gate decision
- before approving architecture, a client quote/boundary, or any high-risk change: create/update `PROJECT_ROOT/项目术语表.md`, `PROJECT_ROOT/决策记录.md`, and `PROJECT_ROOT/docs/25-关键决策压测记录.md` using `references/decision-grill-and-glossary.md`
- after architecture inputs are clear and before the first implementation card: write `PROJECT_ROOT/docs/26-模块契约与升级方案.md` using `references/module-evolution-and-upgrade-safety.md`; update it before any V2 release, data migration, installer/package change, or shared-contract change
- after review/integration/deployment/acceptance: write the corresponding numbered document
- after client acceptance and before marking a commissioned project done: write `PROJECT_ROOT/docs/23-客户交付与结项.md` with delivery inventory, evidence, ownership/account transfer, support boundary, and outstanding approved items
- after delegating work to another AI/agent: update `PROJECT_ROOT/docs/15-跨AI交接记录.md` with the handoff packet, target paths, returned result, and verification status
- after any path, URL, package, repo, or artifact location changes: update `PROJECT_ROOT/项目路径索引.md`

Stop and ask only when:

- required information is missing
- a quality gate needs user confirmation
- there is a risky decision that changes scope, cost, security, or delivery level
- the target path is unknown

When stopping for confirmation, show the document path and the exact decision needed.

## Proactive Next-Step Proposal

After any step is completed, confirmed, or auto-generated, do not wait for the user to ask “下一步”.

Immediately:

1. Update `项目状态.md`.
2. Update `AI执行清单-进度表.md`.
3. Read the current gate and next row in the execution plan.
4. Present the next step with a detailed tool execution chain.
5. Ask: “是否执行这一步？”

Do not execute risky or mutating actions until the user approves. Documentation updates that are direct results of collected information may be auto-generated, but still present the next step for approval.

The next-step proposal must include:

- project root
- path index location
- current completed step
- next step goal
- exact tool sequence
- prompt/command for each tool
- output artifact name
- absolute save path
- cross-agent handoff packet when another AI/tool may execute the step
- quality gate
- acceptance evidence
- risk/cost note
- confirmation question

## Plain-Language Operating Mode

Write instructions for a normal user, not only for a developer.

Every proposed step must answer:

- Open what?
- Copy what?
- Paste where?
- Click/confirm what?
- What file or URL should appear?
- What should the user send back?

For beginner guidance, also answer:

- What does this step achieve in plain language?
- Why is this the right next step now?
- What does the user not need to worry about or decide yet?
- If the expected result does not appear, exactly what should they send back?

Avoid unexplained engineering shorthand. If a technical term is necessary, add a one-line plain explanation.

Use this mini format when the step is user-operated:

```markdown
## 你现在要做

1. 打开：
2. 复制这段内容：
3. 粘贴到：
4. 等它完成后，把这几项发回来：
5. 正常完成时你会看到：
```

## Human Approval Points

Pause and ask the user to approve before these actions:

- PRD/product requirements approval
- architecture and tool-cost decision
- using paid APIs, plugins, MCPs, or cloud services
- deleting files, database changes, migrations, or large refactors
- handing work to another AI that may modify code
- deployment, public release, publishing, or package upload
- accepting P1/P2 risks instead of fixing them
- changing scope after execution has started

Use simple approval text:

```text
是否批准执行这一步？回复“批准”后我再继续。
```

## Task Lock And Ownership

Before any coding or document-changing step, declare a task lock so multiple AIs do not edit the same place blindly.

Each executable step must include:

- lock owner: Codex/Cursor/Claude/ZCode/user
- allowed files or folders
- forbidden files or folders
- start condition
- release condition

Save active locks in `项目状态.md` and release them in the completion report.

If another AI needs the task, include the lock in the cross-agent handoff packet.

## Parallel Agent Mode

Use this only after requirements are confirmed and the architecture baseline is approved. Before proposing it, read `references/parallel-agent-orchestration.md`.

Default to single-thread work for a beginner, Demo, small project, shared-code change, or any task with one blocking dependency. Propose parallel work only when at least two outputs are independent, the saved time is meaningful, and the coordinator can assign non-overlapping files or documents.

Use three controlled modes:

| Mode | Use When | Workers May Do | Coordinator Must Do |
| --- | --- | --- | --- |
| Parallel planning | product/architecture/UI/research can be explored independently | write only assigned analysis documents | create `docs/18-并行协作计划.md`, reconcile decisions, update canonical docs |
| Parallel review | one completed artifact needs independent challenge | read artifact and write assigned review report | decide fixes, update review/status documents |
| Parallel implementation | at least two cards have no shared code, data, API, or UI dependency | work in exclusive folders or dedicated Git branches/worktrees | assign locks, verify every result, integrate one connection at a time |

Never run parallel implementation before a successful parallel plan or architecture gate. Do not allow workers to edit the coordinator-owned state, path index, decision, execution-plan, traceability, integration, or final-review documents. Workers return their output through the standard handoff packet; the coordinator alone records the official result.

Select mode in this order unless the user explicitly overrides it:

| User command | Required behavior |
| --- | --- |
| `强制单线` | keep every task sequential, even when `ultra` is available |
| `优先省钱` | default sequential; use parallel review only for a high-risk decision with a clear cost cap |
| `使用 ultra` | check whether `ultra` is visibly available, show its cost note, then ask for approval before use |
| `自动判断并行` or no command | default sequential; propose controlled parallel work only when the eligibility gate passes |

Before starting parallel implementation, freeze shared contracts under coordinator ownership: database schema, authentication, shared types, core API contracts, public component interfaces, environment variables, and deployment configuration. Workers may read them but may not edit them.

Every `PAR-*` plan must include a deadline/round limit, cost ceiling, stop condition, and fallback owner. If the worker exceeds a limit, returns without evidence, or touches forbidden scope, stop the worker, mark it `Blocked`, record the reason, and continue the same task sequentially under the coordinator.

Choose the execution engine from the actual scan result:

- `GPT-5.6 ultra available`: use automatic multi-agent orchestration for demanding architecture, research, review, or independent planning tasks. It is not the default because it costs more. Give the user one master prompt and record that the platform, not the user, runs the worker agents.
- `Codex worktrees/subagents available`: create independent worker tasks or worktrees with the `PAR-*` plan; use this for isolated implementation cards.
- `Multiple separate sessions available`: give the user one path-first packet per worker and keep the coordinator in the main session.
- `No parallel capability`: execute the planned lanes sequentially and label the project `sequential fallback`; do not claim automatic parallel execution.

Use `ultra` only when the task is high/very high complexity and the expected reduction in rework or elapsed time justifies its cost. Use normal/high reasoning for routine coding, even inside an otherwise parallel project.

## Artifact Versioning And Change Control

Version important artifacts:

- PRD: `v1`, `v2`
- architecture: `v1`, `v2`
- execution plan: `v1`, `v2`
- feature cards: `CARD-001 v1`, `CARD-001 v2`
- final deliverable: release/version number when available

When the user changes requirements after PRD approval:

1. Do not silently continue.
2. Write the change to `PROJECT_ROOT/变更记录.md`.
3. Update the PRD version.
4. Mark affected feature cards in `AI执行清单-进度表.md`.
5. Ask the user to approve the changed scope before execution continues.

Change record format:

```markdown
## YYYY-MM-DD - CHANGE-[number]

- Original requirement:
- New requirement:
- Reason:
- Affected docs:
- Affected cards:
- Cost/risk impact:
- Approved by user:
```

## Required First Documents

The first two project documents are mandatory and ordered.

### 1. 《PRD产品需求文档》

Create `PROJECT_ROOT/docs/01-PRD产品需求文档.md` before any execution plan or development.

It must include:

- Project name, date, project root
- PRD version, default `v1`
- Background and product goal
- Target user and core scenario
- Problem to solve
- User stories in plain language
- Main user journey
- MVP scope
- Out-of-scope list
- Input and output
- Data, file, permission, login, payment, admin, third-party API, and AI model needs
- Initial UI style direction for interface projects
- Platform, device, and environment constraints
- Delivery level
- Budget mode
- Success standard
- Acceptance method
- Acceptance evidence
- Risks and constraints
- AI default assumptions
- Open questions
- Requirement IDs in the form `REQ-001`, `REQ-002`, and so on
- Business rules, examples, exceptions, and unacceptable outcomes for each core function

Gate: the user must confirm the PRD is correct before the AI execution plan is created.

### 2. 《AI执行清单/进度表》

Create `PROJECT_ROOT/AI执行清单-进度表.md` after requirements are confirmed and before development.

Before creating feature cards, read `references/feature-card-template.md` and use the same columns/sections for every split task.

The document header must include:

- Project name
- Created/updated time
- Project root absolute path
- Global projects index path, if known
- Delivery level
- Budget mode
- PRD version

The document body must include:

- Dashboard: total progress, current phase, current task, blocked items, next action
- Role assignment table: task owner/tool, model/reasoning level, responsibility, cost note
- Execution table: priority, status, task, deliverable name, save path, tool, task lock, input prompt/command, quality gate, card-review result, acceptance evidence
- Feature cards: each card vertical, using the same format, with user-visible result, dependencies, interfaces, artifact path, test evidence, and review status
- Change log: date, completed item, evidence, commit/path

Use statuses: `Not started`, `In progress`, `Blocked`, `Done`, `Accepted`.

Gate: no development begins until `AI执行清单-进度表.md` exists and the first executable row is selected.

## Project State Tracking

Every real project must have `PROJECT_ROOT/项目状态.md`. The agent must read it before answering “下一步”, “继续”, “现在到哪了”, or any follow-up after work has started.

Create or update it with:

```markdown
# PROJECT_STATE

## Current Step
STEP N - name

## Completed
- STEP 1 - saved to ...

## Current Task
- ...

## Next Step
STEP N+1 - name

## Decisions
- ...

## Pending Questions
- ...

## Last Updated
YYYY-MM-DD
```

When the user reports a step is done, do not rely on chat memory alone. Update `项目状态.md`, verify the expected artifact exists when possible, then output only the next step.

## Path Index

Every project must maintain `PROJECT_ROOT/项目路径索引.md`. This is the first file another AI should read when it needs to continue the project.

Create it as soon as `PROJECT_ROOT` is known, and update it whenever a new document, code directory, URL, package, deployment, or handoff path appears.

Use this structure:

```markdown
# 项目路径索引

## 项目入口
- 项目名称：
- 项目根目录：
- 当前状态文件：
- AI执行清单：
- 项目总文档：
- 跨AI交接记录：

## 核心文档
| 文档 | 绝对路径 | 用途 | 最后更新时间 |
| --- | --- | --- | --- |

## 代码与运行
| 项 | 绝对路径/命令/URL | 用途 | 备注 |
| --- | --- | --- | --- |

## 当前交付地址
| 类型 | 地址 | 来源步骤 | 验收状态 |
| --- | --- | --- | --- |

## 给其他 AI 的固定读取顺序
1. 项目路径索引.md
2. 项目状态.md
3. AI执行清单-进度表.md
4. 当前步骤相关文档
5. docs/15-跨AI交接记录.md
```

Path rules:

- Use absolute paths whenever the path is on the user's machine.
- Prefer path-first handoff: give the receiving AI the file paths and ask it to read them itself instead of pasting long document content.
- If the receiving AI may run in a different machine or sandbox, include both the absolute target path and the fallback instruction: “无法访问该路径时，请返回完整文件内容并标明目标路径”.
- Do not use vague paths such as “docs 文件夹”, “项目目录”, or “刚才的文件” in handoff prompts.
- Before handing a step to another AI, include `项目路径索引.md` in the required reading list.
- If a path does not exist yet, mark it as `待创建` with the intended absolute path.

## Step Execution Discipline

Never treat engineering execution as complete until the user receives a traceable report.

After each approved step, output `本步完成报告` before proposing the next step. Do not replace it with a short summary.

Required report format:

```markdown
## 本步完成报告 - STEP N

| 项 | 内容 |
| --- | --- |
| 本步目标 |  |
| 全局掌控 | 当前阶段 / 总进度 / 下一步 / 阻塞项 |
| 任务锁 | owner / allowed files / forbidden files / release status |
| 使用工具 |  |
| 输入/命令 |  |
| 生成/修改产物 |  |
| 保存地址 |  |
| 本步交付地址 | local URL / public URL / package path / not applicable |
| 验收证据 |  |
| 更新的追踪文档 |  |
| 跨AI交接记录 | updated / not needed, reason |
| 阻塞/风险 |  |
| 下一步建议 |  |
```

Rules:

- If a dev server starts successfully, report the URL immediately as `本步交付地址`, then save it to `项目状态.md` and the relevant phase doc such as `docs/04-初始化设置.md` or `docs/10-部署落地.md`.
- If a step used another AI/agent, `docs/15-跨AI交接记录.md` must be created or updated before the step is marked complete.
- If files were created or changed, list exact paths, not only folder names.
- If commands were run, include the important command and result, not only “success”.
- If evidence is missing, mark the step `Blocked` or `Done - evidence missing`; do not advance.
- If the task lock is not released or transferred, do not start the next coding step.
- After the completion report, update state files, then present the next executable proposal.

## Context Compression

For long projects, keep durable context in files so another agent or future session can continue without guessing.

Maintain:

- `项目状态.md`: current step, completed steps, next step, pending questions.
- `项目路径索引.md`: canonical file map, absolute paths, URLs, packages, and handoff locations.
- `决策记录.md`: stable decisions, rejected options, reasons, dates.
- `变更记录.md`: requirement changes, scope drift, affected cards, approval state.
- `docs/05-功能开发记录.md`: feature cards, implementation notes, commit IDs.
- `docs/15-跨AI交接记录.md`: every cross-agent prompt, source docs, exact target paths, returned result, and verification status.

Update these files when:

- a step completes
- a major decision is made
- a feature card is implemented
- review findings are fixed
- integration or deployment status changes

Before continuing an existing project, read these files first. If they are missing, reconstruct the minimum state from available docs and ask only for the missing piece.

## Architecture Continuation And Recovery

When a session, tool, or cross-AI handoff resumes after an interruption, do not continue from chat memory. First read, in order:

1. `项目路径索引.md`
2. `项目状态.md`
3. `AI执行清单-进度表.md`
4. `docs/17-需求追踪矩阵.md`
5. the document for the current phase and `docs/15-跨AI交接记录.md` when another AI was involved

Then verify the expected artifacts, branch/commit, command output, and task lock before claiming the current step is complete. If they disagree, mark the project `Blocked`, record the discrepancy, and repair the source-of-truth documents before proposing another coding step.

## Cross-Agent Handoff

When a step is sent to another AI, desktop app, CLI agent, IDE agent, or browser AI, assume that agent knows nothing about the project paths or previous chat.

Before writing the handoff, read `references/cross-agent-handoff-template.md`.

Every handoff packet must include:

- project name, project root, current step, and current date
- `项目路径索引.md` as the first source document to read
- source documents to read, using absolute paths when known
- exact task goal and non-goals
- exact prompt or command to run
- deliverable name
- exact save path for every output artifact
- a path map for this step: source docs, files to read, files to create/change, output docs, logs, delivery URL/package path
- fallback instruction: if the agent cannot write files directly, return the full file content with the target path header
- completion report format, including changed files, evidence, blockers, and next-agent context
- instruction to avoid saving only in the agent's private workspace

Default to path-first handoff:

1. Tell the user which AI/tool to open.
2. Give one copy-ready prompt that lists paths and asks the receiving AI to read files itself.
3. Do not paste full source document content unless the receiving AI cannot access local paths.
4. If the receiving AI cannot access a path, ask it to say which path failed, then return the full output content with the target path header.

After the other agent returns, the primary agent must:

1. Save or verify the returned artifact at the declared path.
2. Update `项目状态.md`.
3. Update `AI执行清单-进度表.md`.
4. Append the handoff and result to `docs/15-跨AI交接记录.md`.
5. Run the current quality gate before proposing the next step.

Do not delegate a step until the handoff packet has enough path information for a different AI to execute without reading the current chat.

## Quality Gates

Do not move forward when the gate for the current phase fails.

| Gate | Must Be True Before Advancing |
| --- | --- |
| Requirements -> execution plan | `docs/01-PRD产品需求文档.md` exists and user confirms it is correct |
| Requirement intake -> PRD | core functions, user flow, input/output, data/permissions, UI expectation, and acceptance evidence are clear or explicitly marked as `AI默认建议，待确认` |
| Project root -> any handoff | `项目路径索引.md` exists or is created with intended paths |
| Execution plan -> development | `AI执行清单-进度表.md` exists with dashboard, priorities, deliverables, roles, gates, evidence |
| Major artifact -> next phase | artifact passes `references/artifact-quality-standard.md`: polished, precise, traceable, actionable |
| Planning -> architecture | feature cards are vertical and prioritized in `AI执行清单-进度表.md` |
| Planning -> implementation | the selected first card has implementation anchors: affected files/paths, command or tool action, realistic verification, and declared output |
| Product design -> development | product framework defines real user task, critical journey, functional rules, content hierarchy, and success evidence; `references/product-design-quality.md` passes |
| Architecture -> setup | stack, data model, first files, risks, requirement traceability, first vertical slice, and core failure behavior are documented; `references/architecture-decision-standard.md` passes |
| Parallel proposal -> worker start | `docs/18-并行协作计划.md` lists mode, coordinator, `PAR-*` IDs, dependencies, exclusive write scopes, paths, budgets, and merge gate |
| Parallel workers -> next phase | `docs/19-并行结果汇总.md` verifies evidence, requirement/architecture/API/file-diff checks, conflicts/overlaps, and the coordinator's merge decision |
| Interface project -> UI implementation | `docs/06-UI风格方案.md` and `docs/06-交互控件规格.md` exist with approved style direction, control inventory, and design quality checklist |
| Setup -> feature work | project starts locally and Git is initialized |
| Cross-agent delegation -> execution | handoff packet includes source docs, exact output paths, completion report format, and logging path |
| Step execution -> next proposal | `本步完成报告` includes tool, input, output, save address, delivery address when applicable, and evidence |
| One card -> next card | card has implementation anchors, acceptance evidence, commit, and card-level review marked pass |
| Feature cards -> integration | all MVP cards pass card-level review |
| Integration -> review | main user journey works end to end |
| Integration -> mature review | `docs/20-设计品质验收.md` verifies function, architecture, interaction, and visual evidence; failures return to the relevant card |
| Mature review -> final acceptance | `docs/21-落地验证清单.md` proves every accepted requirement, design decision, and review fix maps to implementation and evidence |
| Review -> deploy | P0 fixed; P1 either fixed or explicitly accepted; `docs/22-发布前体检.md` passes or has explicit user-approved risk acceptance |
| Deploy -> done | public/local deliverable works and `docs/14-工程保障清单.md` plus `docs/22-发布前体检.md` are complete for the delivery level |

If a gate fails, output the blocker, the exact fix step, and the tool to use. Do not continue to the next phase.

## Acceptance Evidence

Every completed step must include evidence, not only a status claim.

Acceptable evidence:

- command output, e.g. `npm test`, `npm run build`, `docker build`
- manual path, e.g. “open `/dashboard`, click Save, see success toast”
- API proof, e.g. request/response sample
- screenshot or browser verification for UI
- file path for created docs
- commit hash for implementation work

When the user says a step is complete, ask for missing evidence only if the next step depends on it. Save evidence to `项目状态.md` and the relevant `docs/` file.

## Tool Initialization

Before execution, recommend only necessary setup:

- Terminal AI: install/enable this skill; ensure file read/write and command execution.
- Codex: place this `SKILL.md` in a skill folder or project `.codex` instructions.
- ZCode/Claude Code: place this file as `~/.agents/skills/project-workflow/SKILL.md` when supported.
- Cursor/Windsurf/VS Code: add project rules that forbid broad refactors and require small patches.
- GitHub: install GitHub CLI or Desktop only if repo/PR workflow is needed.
- Notion/Workbuddy: create board only if project has more than 3 cards.
- Figma/v0/Bolt: use only when UI design matters.
- MCP/plugins: connect GitHub/Notion/Figma/Browser only when the step needs them.

Do not recommend unused plugins or MCPs.

## Feature Splitting Rule

Never ask an AI to “finish all features” in one pass.

Every card must use the same structure from `references/feature-card-template.md`. Do not allow ad hoc card formats; inconsistent split formats create integration risk.

Use this sequence:

1. Freeze shared contracts and identify cards that have no dependency or write-scope conflict.
2. Put all eligible cards into one numbered implementation wave; assign the best concrete detected tool to each card.
3. Send all worker packets in the wave together after one user approval. Do not hold an eligible tool idle merely because another independent card is running.
4. Each worker implements only its isolated card, runs its local test, and returns its evidence.
5. The coordinator reviews each returned card against its interface contract, output format, artifact path, tests, and integration impact.
6. Merge or accept one reviewed result at a time, run affected tests after each merge, then update `项目状态.md` and `docs/05-功能开发记录.md`.
7. Run the wave integration check. Only then plan the next wave or any dependent card.

Each card must include:

- user-visible result
- product/design intention: what real user task becomes easier and what quality the user should feel/see
- requirement IDs and architecture decision IDs it implements
- involved files
- data/API/UI sequence
- normal path, edge cases, error/recovery behavior, and observable evidence
- realistic input/output example and visual/interaction expectation when the card is user-facing
- related `UI-CTRL-*` IDs and control-level acceptance evidence when the card is user-facing
- implementation anchors: exact files/routes/API/test commands/URLs/packages that make this card real
- test/verification
- save location
- commit message
- card-level review result
- owning `MOD-*`, its public contract, allowed dependencies, and independent test/repair boundary

Before implementing a card, read `references/code-delivery-standards.md` and the project's `docs/24-代码质量与变更控制.md`. Create a `CODE-CHG-*` entry that names the approved requirement/card/change IDs, allowed files, forbidden scope, verification plan, and rollback/data-risk notes. For client delivery, code may only implement an approved `REQ-*`/`SCOPE-*` or an approved `CHANGE-*`.

Before an upgrade or shared-module change, also read `references/module-evolution-and-upgrade-safety.md` and `docs/26-模块契约与升级方案.md`. Do not modify another module's data, public contract, or user-facing behavior merely to complete a local card.

Only mark a card eligible for parallel implementation when its dependency, interface contract, allowed files, data/API ownership, test environment, and branch/worktree are all independent. Otherwise keep it in the sequential queue.

Card review must happen immediately after each card returns. If review fails, fix that same card before it is merged or any dependent card starts. Other isolated cards in the same approved wave may continue. Save review results in `AI执行清单-进度表.md` and `docs/05-功能开发记录.md`.

## Code Quality And Change Control

Before writing or changing code, read `references/code-delivery-standards.md`. For non-trivial projects, create and maintain `docs/24-代码质量与变更控制.md`.

Apply these non-negotiable rules:

1. Read the project state, approved requirement/card, architecture, relevant interfaces, and surrounding code before editing. Follow the existing repository conventions unless an approved architecture decision changes them.
2. Change the smallest coherent file set. Do not mix a feature with unrelated cleanup, bulk reformatting, framework upgrades, dependency churn, or speculative refactors.
3. Never hard-code production secrets, personal data, environment URLs, credentials, access bypasses, test-only switches, or client-specific values that belong in configuration/data.
4. Validate input at boundaries; enforce authorization/ownership on sensitive actions; return safe errors; never solve a bug by disabling validation, tests, logging, permissions, or error handling.
5. Treat migrations, destructive data actions, external side effects, public API/schema changes, auth changes, payment changes, and production configuration as high-risk changes requiring an explicit plan, backup/rollback, and approval.
6. Add or update the smallest meaningful test/verification for the changed behavior. Run relevant format/lint/type/build/test commands available in the project; record what was not run and why.
7. Review the diff for scope, regressions, secrets, dead/debug code, duplicate logic, error paths, performance/cost impact, and client scope traceability before committing.
8. Make atomic commits with requirement/card/change IDs. Do not claim a feature is finished without a code path, verification evidence, and an updated state record.

## Decision Grill And Shared Language

Use `references/decision-grill-and-glossary.md` at these moments:

- after a non-trivial idea/PRD is drafted but before confirmation
- after a client requirement baseline is mapped but before quote/boundary approval
- before technical architecture approval
- before high-risk data/auth/payment/AI/third-party/deployment choices
- when an inherited project, review finding, or change request conflicts with existing terms or decisions

Run the loop:

1. Read the relevant source documents, project state, glossary, prior ADRs, and code/contracts where they exist.
2. State the precise decision, assumptions, known evidence, and which unknown could change the outcome.
3. Test the decision against at least one concrete normal scenario and one failure/boundary scenario.
4. Ask one high-leverage question at a time only when evidence cannot answer it. Do not repeat a settled question or grill low-risk wording.
5. Update the glossary when a domain term has one agreed meaning. Update `决策记录.md` with an `ADR-*` only when alternatives/cost/irreversibility justify it.
6. Save the session result and unresolved risks to `docs/25-关键决策压测记录.md`, then state the exact gate result: approved / approved with conditions / blocked.

The glossary and ADRs are canonical. A later AI must read them before redefining a core term or reversing a decision.

## Market Feasibility Gate

For the user's own product idea, read `references/market-feasibility-gate.md` before confirming the PRD. Use current, cited research where market facts may have changed. Do not browse only to collect flattering evidence; actively search for alternatives, failed assumptions, cost constraints, and reasons the user may not reach or retain a first customer.

Output one of three clear results:

- `Go`: enough evidence for a tightly scoped MVP, named first users, value hypothesis, and low-enough risk.
- `Validate First`: the idea may be viable, but a named hypothesis needs interviews, landing-page interest, prototype test, pilot commitment, or another small validation before full build.
- `No-Go`: the current evidence does not support a full product build. State the decisive reasons and recommend stopping, reframing, or running only a bounded experiment.

Never turn `Validate First` or `No-Go` into a full technical plan. If the user insists, record their override, maximum time/cost, success metric, and stop date in `docs/00-可行性与市场验证.md` and treat the work as an experiment.

## Competitive Positioning Gate

For a commercial/product idea, read `references/competitive-positioning.md` together with the feasibility gate. Research direct competitors, indirect alternatives, free tools, manual/agency workflows, and the user's current workaround. Compare actual evidence rather than feature-list guesses.

State one primary competitive wedge in this form: `for [specific first segment], who currently [inferior alternative/workaround], we help them achieve [measurable better outcome] through [specific workflow/channel/trust/data/service/cost advantage], and we can reach the first users through [named path].`

If the wedge is only “AI”, “better UI”, “cheaper” without an evidence-backed reason, or “more features”, classify it as unproven. Recommend a narrower segment, a validation action, or No-Go. Do not write the MVP feature list until the wedge and first-user path are clear enough to test.

## Evidence And Boundary Honesty

Read `references/evidence-and-boundary-honesty.md` before making a commitment or recommendation that affects time, money, scope, safety, data, launch, or customer expectation.

Use the four labels exactly:

- `已验证可做`: direct project evidence proves a path exists now, including required tools/access/data and a reproducible verification result.
- `可做但需验证`: technically plausible, but one or more material assumptions still need a prototype, access check, research, test, client decision, or cost confirmation.
- `当前不可承诺`: enough is unknown that a cost/date/quality/result commitment would be guessing; say what blocks it and what evidence would change the answer.
- `明确不可做`: conflicts with a technical fact, access/permission limit, safety/legal constraint, budget/time boundary, approved scope, or an external outcome nobody on the project controls.

For every material claim, include the label, evidence path/source, boundary, owner/dependency, and next validation. Never promise revenue, market demand, model accuracy, third-party availability/approval, app-store/platform review, data recovery, security perfection, cost ceiling, performance, delivery date, or legal compliance without verified project-specific basis and the required controlling party.

## Module Evolution And Upgrade Safety

Before architecture approval, read `references/module-evolution-and-upgrade-safety.md` and create `docs/26-模块契约与升级方案.md`.

Apply these rules:

1. Give each module a `MOD-*` owner, responsibility, data ownership, public input/output contract, allowed dependencies, and independent test/repair boundary. A module is not “independent” merely because it lives in a separate folder.
2. Fix and optimize a module through its contract and targeted tests. Do not change shared types, database schema, auth, public APIs, or another module merely to hide a local defect; create an approved shared-contract change when necessary.
3. Store user data, customer data, project artifacts, uploads, and configuration outside the replaceable app/install directory. Never make an installer cleanup step delete these locations by default.
4. For V2 or later, create an explicit migration plan. Migrations must identify source/target version, be idempotent or safely resumable, retain a pre-migration backup, validate the result, and state the rollback/restore action.
5. Prefer backward-compatible, additive changes first. For breaking changes, provide a transition period, compatibility adapter/import-export, or approved migration/communication plan.
6. Test a real upgrade path: create/use V1 representative data, install/upgrade to V2 without resetting storage, verify core data and flows, then test rollback/restore where material. A clean V2 install is not upgrade evidence.
7. Treat updating this Skill itself as non-destructive: replace only Skill/reference files. Never delete `PROJECT_ROOT`, user project documents, databases, uploads, user profile data, or unrelated installed Skills.

## 10-Step Map

When requirements are confirmed, output a customized 10-step map. Every step must include: open, input, output, save location, completion signal, recommended tool/model level.

1. Clarify requirements.
2. Choose project mode: own product, inherited project, client delivery, automation, CLI, website, app.
3. Product framework or inherited-project teardown.
4. Split feature cards.
5. Technical architecture.
6. Initialize project and tools.
7. For interface projects, define UI style direction and page design rules.
8. Implement cards one by one.
9. Integrate cards into one complete product and run full-system validation.
10. Mature review, deployment, documentation assembly, handoff, and retro.

Each step must include its quality gate and required acceptance evidence.

For client delivery, run STEP 0 before this map and do not enter Step 3 or implementation until the commercial gate has passed.

## Client Scope, Quote, And Delivery Guardrail

For every client delivery, read the three client-delivery references before recommending a price, a fixed deadline, or implementation.

1. Convert vague wishes into versioned `SCOPE-*` statements and measurable `ACC-*` acceptance cases.
2. Produce an estimate range with visible assumptions, uncertainty, external recurring costs, and client-owned dependencies. Never present an AI estimate as a guarantee.
3. Identify red flags: undefined scope, impossible deadline, unavailable decision-maker, unspecified data/account access, regulated/high-risk data, unpaid discovery, open-ended revisions, or client-owned work that is not scheduled.
4. Recommend one of: paid discovery first, phased/milestone delivery, time-and-materials, fixed-price only after scope approval, or decline/pause. Explain why in plain language.
5. Record what is included, excluded, client-provided, accepted, transferred, supported, and billable as a change. Do not rely on chat memory.
6. When a new request appears, create/update `docs/00-需求变更单.md`, show its scope/cost/date impact, and wait for approval before adding a feature card.
7. At final handover, compare the approved scope and acceptance cases against actual delivery, then create `docs/23-客户交付与结项.md`. Do not call a client project complete merely because the code was sent.

## Client Project Risk Governance

Read `references/project-risk-governance.md` for every client delivery and update `docs/00-项目风险总表.md` at these gates:

| Gate | Must Be True Before Proceeding | Block When |
| --- | --- | --- |
| G0 接单可行性 | payer/decision-maker, desired business result, delivery level, and no-go constraints are known | client wants a blank cheque, impossible promise, or unowned high-risk responsibility |
| G1 需求范围 | `SCOPE-*`, exclusions, `ACC-*`, client inputs, and decision process are written | the result cannot be measured or V1 is still “do everything” |
| G2 报价合作 | estimate basis, assumptions, third-party costs, payment milestones, risk response, and contract-review checklist are ready | fixed commitment is requested with material unknowns or P0/P1 has no decision |
| G3 开工准备 | approved scope/quote/boundaries, required accounts/materials, project root, and responsible contacts exist | missing client prerequisite would block build or expose data/account risk |
| G4 执行控制 | each card has evidence; requests outside scope are change records; risks are refreshed | AI/client starts unapproved work or a new P0/P1 has no decision |
| G5 验收结项 | acceptance cases pass, delivery inventory and ownership transfer are recorded, payment/support/known limits are reconciled | “looks okay” replaces acceptance evidence or handover has secrets/missing assets |
| G6 上线与售后 | release preflight passes, rollback/owner/support boundary are known | production risk, ownership, monitoring, or support responsibility is unknown |

Never promise to eliminate all uncertainty. Make risk visible early, reduce what can be reduced, transfer/price what is external, and stop when the remaining risk is unacceptable.

The contract checklist is practical project protection, not legal advice. In China, the Civil Code lists matters such as parties, subject matter, quality, remuneration, performance, breach, and dispute resolution as typical contractual terms; final agreements and high-risk clauses require suitable local professional review. 

## Client Opportunity Qualification

For a new external inquiry, read `references/client-opportunity-qualification.md` before client discovery, quote, or pre-sales design. Keep the opportunity stage and evidence in `docs/00-商机评分与沟通记录.md`.

Use the stage gate, not the desire to please the client:

1. Start with concise chat and score the opportunity from available evidence.
2. If unqualified, ask only the smallest set of decision-changing questions or pause/decline. Do not create a free full solution.
3. If plausible but not ready, send a one-page project brief with outcome and next decision, not a technical blueprint.
4. Only after qualification begin formal requirement baseline, scope, risk, acceptance, and quote work.
5. Begin implementation only when the agreed scope/boundary and commercial start condition are documented.

Record silence/no response as an opportunity status, not a reason to keep producing free work. Recommend one appropriate, user-approved follow-up or close the opportunity as paused/lost; do not spam.

## Inherited Project Framework

For someone else’s project, do not start coding first.

Teardown order:

1. Read README, scripts, env examples, deploy docs.
2. Map directory structure.
3. Find start commands and run locally if safe.
4. Map data flow.
5. Map API/auth flow.
6. Map page/user flow.
7. Inspect dependencies and risky scripts.
8. Inspect tests and CI.
9. Inspect deployment and rollback.
10. Propose the smallest safe change.

Save to `docs/00-项目拆解报告.md`.

## Own Product Framework

For a product from scratch, design before architecture:

1. User persona.
2. Core scenario.
3. Value proposition.
4. MVP scope.
5. Business objects.
6. Page flow.
7. Data model.
8. Permission model.
9. Monetization or usage limits, if needed.
10. Operations and growth hooks, if needed.

Use terminal AI for product reasoning, Figma/FigJam/Excalidraw for flows, v0/Bolt for UI drafts.

Save to `docs/02-产品框架.md`.

## UI Style Direction

For any website, app, dashboard, desktop tool, mobile app, landing page, or visual product, do not start UI implementation until the style direction is documented and approved.

Before creating UI screens, read `references/ui-design-playbook.md`.
For a non-trivial product, also read `references/product-design-quality.md` so the interface follows the product task and architecture instead of only looking polished.
Before implementing controls, read `references/interaction-control-spec.md` and create `docs/06-交互控件规格.md`.

Create `PROJECT_ROOT/docs/06-UI风格方案.md` with:

- product personality: professional, playful, premium, calm, editorial, utility, futuristic, etc.
- audience and usage context
- visual keywords and anti-keywords
- color palette with roles, not only colors
- typography scale and density
- layout rhythm: spacing, grid, card radius, navigation style
- component style: buttons, inputs, lists, tables, cards, modals, empty states
- image/icon style and asset needs
- motion/interaction feel
- responsive behavior
- 3 reference products or style analogies, when useful
- explicit “do not make it look like” list
- screenshot/design evidence required for acceptance

The UI style direction must be plain enough for a normal user to understand. Explain style decisions as “what the user will feel/see”, not only design jargon.

If the user gives no style preference, infer a suitable style from product type:

- SaaS/dashboard/admin: clean, dense, calm, high-contrast, work-focused.
- consumer app: warmer, more guided, more emotional feedback.
- creator/content tool: editorial, visual, expressive but still usable.
- AI tool: trustworthy, clear state feedback, restrained futuristic cues.
- game/entertainment: more expressive, animated, themed.
- landing page: strong first-viewport identity and clear offer.

UI generation prompt must include:

```text
请读取：
1. PROJECT_ROOT/项目路径索引.md
2. PROJECT_ROOT/docs/01-PRD产品需求文档.md
3. PROJECT_ROOT/docs/02-产品框架.md
4. PROJECT_ROOT/docs/06-UI风格方案.md

你正在做 STEP N - UI界面设计/实现。
目标：按已批准的 UI 风格方案生成界面，不要做成通用模板风。
产物必须保存到：[absolute path]
完成后回报：页面截图/预览地址、修改文件、风格匹配说明、移动端检查结果。
```

Quality gate: UI is not accepted without visual evidence such as screenshot, preview URL, or browser verification, a short style match check against `docs/06-UI风格方案.md`, and evidence that critical `UI-CTRL-*` controls match `docs/06-交互控件规格.md`.

## Product Assembly And Integration

Feature cards are parts, not the finished product. After all MVP cards pass card-level review, run a dedicated integration step before mature review or deployment.

Use tools this way:

- Terminal AI: integration lead. It reads the architecture, AI execution plan, feature log, commits, tests, and current state; then produces the integration plan.
- AI IDE: local wiring. It edits single files or small groups such as routes, navigation, shared state, config, error messages, and UI connections.
- Git: integration branch and commits. Use a dedicated integration branch when the project is more than trivial.
- Test runner/browser: full product validation.
- Second model: optional for high/very-high risk integration review.

Integration order:

1. Read `项目状态.md`, `AI执行清单-进度表.md`, `docs/03-技术架构.md`, and `docs/05-功能开发记录.md`.
2. List all completed feature cards and the user-visible product flow they should form.
3. Identify missing connections: navigation, shared data, auth/session, API wiring, environment variables, error states, loading states, empty states, and permissions.
4. Create `docs/08-总装集成.md` with an integration checklist.
5. Create or switch to an integration branch if Git is available.
6. Wire one connection at a time using the appropriate tool.
7. Run full-system tests and manual happy-path validation.
8. Fix integration bugs one at a time.
9. Commit the integrated product.
10. Update `项目状态.md` to mark integration complete.

Prompt:

```text
所有 MVP 功能卡片已经分别完成。请作为集成负责人读取 项目状态.md、AI执行清单-进度表.md、docs/03-技术架构.md 和 docs/05-功能开发记录.md。
请输出产品总装计划：哪些功能要连接起来、缺哪些接线、用什么工具改、按什么顺序改、每一步如何验证、结果保存到哪里。
不要新增大功能，只把已完成零件组合成完整可用产品。
```

Save the result to `docs/08-总装集成.md`.

Completion signal: the product can run through the main user journey from entry to final output with real or accepted mock data, and the integration commit exists.

## Documentation Assembly

After integration and acceptance pass, create documentation in three layers:

1. Subdocs: keep detailed phase documents under `PROJECT_ROOT/docs/`.
2. Project master document: create `PROJECT_ROOT/项目总文档.md` as the single entry for this project.
3. Global master document: update `PROJECTS_HUB_ROOT/所有项目总索引.md` so all projects are searchable from one place.

Determine `PROJECTS_HUB_ROOT` before updating the global index:

- Prefer a user-configured projects root.
- Otherwise use `D:\AI项目文档库`.
- If `D:\AI项目文档库` is unavailable, ask where the all-projects index should live.

After final acceptance, create `PROJECT_ROOT/docs/12-使用说明.md` for usage only:

- What this project does
- Who it is for
- Install/setup steps
- How to run locally
- How to use the main workflow
- Configuration and environment variables
- Common errors and fixes
- Support/maintenance notes

Create `PROJECT_ROOT/docs/13-完成品文档.md` for the completed product only:

- Final product name and version
- Delivery level and acceptance status
- Public URL, local run command, package path, installer path, or published artifact
- Source repo path and final commit hash
- Deployment platform and environment
- Build/test/acceptance evidence
- What is included in this delivery
- What is explicitly not included
- Known risks accepted by the user

Then create or update `PROJECT_ROOT/项目总文档.md` with:

- Project summary and status
- Delivery level and acceptance result
- Links to all subdocs in `docs/`
- Link to `docs/12-使用说明.md`
- Link to `docs/13-完成品文档.md`
- Key decisions from `决策记录.md`
- Known risks and next iteration

Finally update `PROJECTS_HUB_ROOT/所有项目总索引.md` with one row per project:

```markdown
| Project | Status | Type | Delivery | Path | URL/Artifact | Last Updated | Next Action |
| --- | --- | --- | --- | --- | --- | --- | --- |
| name | accepted/deployed | Product/SaaS/app | MVP | path/to/项目总文档.md | url | YYYY-MM-DD | next |
```

Quality gate: a project is not “done” until the final-deliverable doc, user guide, project master document, global projects index, `docs/20-设计品质验收.md`, and `docs/21-落地验证清单.md` are all updated. For interface projects, the control specification must also be linked from the project master document.

## Engineering Readiness

Before final delivery, read `references/engineering-readiness.md` and create `PROJECT_ROOT/docs/14-工程保障清单.md`.

For Demo, record only the essentials. For MVP/Beta/Production, check environment variables, secrets, dependency lockfiles, migrations, tests/build, deployment, logs, rollback, and maintenance ownership.

Do not mark the project done until unresolved engineering risks are either fixed or explicitly accepted in `docs/14-工程保障清单.md`.

## Shift-Left Release Safety

Read `references/release-preflight.md` at the start of architecture for MVP, Beta, and Production work, then keep its checklist live in `PROJECT_ROOT/docs/14-工程保障清单.md`. Do not wait for deployment.

Apply these gates in order:

| Phase | Must Decide or Verify Before Advancing |
| --- | --- |
| Architecture | development/production isolation plan; configuration/secrets ownership; auth and data boundaries; logging/audit needs; media/storage strategy; backup/rollback level |
| Setup | separate environment variable files/provider configurations; production debug disabled by default; `.env.example`; secret scan; safe database/seed/migration commands; baseline test/build commands |
| Each feature card | authorization and ownership checks; input validation; no hard-coded secrets/test bypass; safe logs; rate limit/cost guard when relevant; normal, failure, and recovery evidence |
| Integration | production-like smoke test with separate test data; remove temporary routes/mocks; verify browser/device behavior when applicable; update rollback and monitoring evidence |
| Final preflight | rerun the full checklist, compare it against accumulated evidence, and report only remaining gaps |

When a feature requires a security-, environment-, storage-, or observability decision, create or update its `ADR-*` and the relevant row in `docs/14-工程保障清单.md` before coding. A card cannot pass review if it defers a known release-safety requirement to “later”.

## Mature Product Review

Review finished work across:

- requirement completeness
- UX and mobile usability
- UI style match against `docs/06-UI风格方案.md`
- visual polish, consistency, empty/loading/error states, and “generic template” risk
- data correctness
- auth and permissions
- input validation and file upload safety
- XSS/CSRF/secret leakage
- performance and cost
- stability, retries, timeout, rollback
- maintainability
- tests and regression risk
- deployment, logs, monitoring, backup
- requirement-traceability completeness: every approved `REQ-*` is delivered, explicitly deferred, or rejected by the user
- architecture fitness: boundaries remain simple, contracts are honored, and operational limits are met without unnecessary complexity
- product usefulness: the critical task is easier to complete than the user's current path, with no placeholder or unclear dead-end flow
- interaction quality: hierarchy, feedback, defaults, empty/loading/error/recovery states, and mobile task completion are intentional
- visual quality: interface matches the approved personality and avoids generic template composition, arbitrary color, inconsistent density, and missing product-specific assets
- control quality: every visible meaningful `UI-CTRL-*` has a purpose, correct trigger/result, states, permission/accessibility behavior, and browser/test evidence; no dead or misleading action remains
- delivery grounding: every accepted requirement, architecture/design decision, and review fix points to an actual file, route/API, test/manual path, command output, URL, package, or accepted non-code decision

Output:

```markdown
## 成熟产品审查报告

### P0 必须立刻修
- 问题 / 影响 / 建议工具 / 涉及文件 / 验证方式

### P1 上线前修
- 问题 / 影响 / 建议工具 / 涉及文件 / 验证方式

### P2 后续优化
- 问题 / 影响 / 建议工具 / 涉及文件 / 验证方式

### 可接受风险
- 风险 / 原因 / 观察方式
```

Save to `docs/09-成熟产品审查.md`.

## Final Difference Review

After mature review fixes and before marking the project accepted, compare the approved PRD against the actual delivery.

Create `PROJECT_ROOT/docs/16-最终差异审查.md`.

Use plain language so the user can decide whether to accept the result:

```markdown
# 最终差异审查

## 对照来源
- 已批准 PRD：
- AI执行清单：
- 完成品文档：
- 使用说明：

## 已完成
| PRD 项目 | 实际交付 | 证据 | 状态 |
| --- | --- | --- | --- |

## 未完成
| PRD 项目 | 未完成原因 | 是否影响交付 | 建议 |
| --- | --- | --- | --- |

## 多做的内容
| 内容 | 为什么出现 | 是否保留 |
| --- | --- | --- |

## 已接受风险
| 风险 | 影响 | 用户是否接受 |
| --- | --- | --- |

## 最终结论
- 是否达到交付标准：
- 是否建议上线/交付：
- 下一版建议：
```

Gate: a project cannot be marked accepted until `docs/16-最终差异审查.md` exists and the user accepts the conclusion.

## Optimization After Review

When the user brings review findings back:

1. Classify findings as P0/P1/P2.
2. Analyze root cause.
3. Choose the right tool for each fix.
4. Decide reasoning accuracy: high or very high.
5. Split fixes into one-card-at-a-time tasks.
6. Define validation and save location.
7. Fix one issue, test, commit, update review log.

Prompt to use:

```text
这是审查报告：[粘贴]
请按 P0/P1/P2 分析根因，并规划每个问题：
用什么工具修、是否需要高/极高推理、涉及哪些文件、修复顺序、如何验证、结果保存到哪里。
```

## Next-Step Execution Proposal

When a step is completed/confirmed, or when the user says “下一步”, read `references/user-facing-navigation.md` and output only the next executable proposal.

Default to the compact action card below. It is the only user-facing format unless the user explicitly says `展开执行详情`, asks for multi-agent coordination, or the current step has high/very-high risk. Persist the full task lock, evidence, tool rationale, cost, and handoff record in the project documents instead of making the user read them.

````markdown
## 现在是第 N 步：阶段名

**这一步要完成：** [一句人话目标]

### 你现在只要做这 3 件事
1. **打开：** [具体工具/网站/AI]
2. **复制发送：**
   ```text
   [只包含本步所需的提示词；若发给其他 AI，必须带绝对路径和保存要求]
   ```
3. **完成后确认：** [用户能看见的完成标志]

**本步产物：** [产物名称]  
**保存位置：** `[PROJECT_ROOT 下的绝对路径]`  
**我已记录：** 当前进度、责任工具、验收标准和下一步依赖。

完成后把 `[最小回报内容，例如：完成 / 预览地址 / 报错截图]` 发给我。我会自动整理本步文档、核对质量门禁，并只给你下一步。

是否执行这一步？
````

For a cross-AI step, append only this focused handoff block after the compact card:

````markdown
### 发给 [工具/Agent 名称]
```text
你正在接手：[项目名] 的 STEP N - [阶段名]。
本步只做：[本步目标]。

先读取：
1. [项目路径索引绝对路径]
2. [AI执行清单绝对路径]
3. [本步输入文档绝对路径]

只允许修改/创建：[明确范围]。
不要做下一步，也不要修改范围外文件。

产物必须保存到：[绝对输出路径]。
完成标准：[可验证结果]。

完成后只回报：做了什么、产物路径、修改文件、验证证据、阻塞项。
```
````

### Expanded Execution Detail

Use the following full map only when the user explicitly asks to `展开执行详情`, requests a parallel plan, needs an audit/quote/contract review, or a high/very-high-risk gate requires it. In normal use, write these details to the state, execution checklist, and handoff log instead of showing them in chat.

```markdown
## STEP N - 阶段名

- 当前进度：你正在做 STEP N / 总步骤 X
- 执行模式：单线 / 并行规划 / 并行审查 / 并行实现
- 本步一句话说明：
- 这一步为什么现在做：
- 你不需要先懂什么：
- 项目根目录：
- 项目路径索引：
- 全局项目索引：
- 上一步结果：
- 本步目标：
- 你现在要做：
  | 顺序 | 操作 | 复制/点击/打开什么 | 完成后看到什么 |
  | --- | --- | --- | --- |
- 任务锁：
  - 负责人：
  - 允许修改：
  - 禁止修改：
  - 释放条件：
- 产物名称：
- 保存到：[absolute path under PROJECT_ROOT]
- 工具执行链：
  | 顺序 | 工具 | 打开方式 | 输入/操作 | 产出 | 保存位置 | 完成标志 |
  | --- | --- | --- | --- | --- | --- | --- |
- 并行任务表（仅并行时）：
  | PAR-ID | Agent/会话 | 只读输入 | 允许写入 | 禁止写入 | 分支/工作区 | 产物路径 | 完成标志 |
  | --- | --- | --- | --- | --- | --- | --- |
- 质量门禁：
- 验收证据：
- 工具/模型建议：
- 风险/成本提示：
- 是否需要用户批准：
- 没看到预期结果时，请发回：
- 跨AI交接包：
  - 复制给谁：
  - 需要附带/让对方读取的文档：
  - 本步骤路径地图：
  - 直接发送的提示词：
    ```text
    你正在接手：[项目名] 的 STEP N - [阶段名]。
    本步只做：[本步目标]。
    请先读取这些路径：
    1. [项目路径索引绝对路径]
    2. [AI执行清单绝对路径]
    3. [本步相关文档绝对路径]

    你需要完成：
    1. ...
    2. ...

    不要做：
    - 不要提前做下一步。
    - 不要修改禁止范围外的文件。

    产物必须保存到：
    [绝对路径]

    完成标志：
    [完成标志]

    完成后请回报：
    1. 当前完成的是 STEP N - [阶段名]
    2. 做了什么
    3. 产物保存到哪里
    4. 修改/生成了哪些文件
    5. 验收证据是什么
    6. 有没有阻塞
    7. 给下一个 AI 的上下文

    如果你无法读取某个路径，请指出具体路径；不要自行换路径。
    如果你不能直接写入文件，请返回“目标路径 + 完整文件内容”。
    ```
  - 对方必须保存到：
  - 如果对方不能写入文件，必须返回：
  - 完成后必须回报：
  - 本次交接记录保存到：

是否执行这一步？
```

Before producing this block, read `项目状态.md` when it exists. If it does not exist but the task has already started, create it or ask for the latest completed step.
