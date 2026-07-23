# Code Delivery Standards

Use this before every implementation or code review. It protects a project from AI-driven scope creep, fragile shortcuts, unsafe changes, and untraceable code. Respect the repository's existing conventions first; do not introduce a new style merely because it is familiar.

## Change Authorization

Every non-trivial code change needs a `CODE-CHG-*` record in `PROJECT_ROOT/docs/24-代码质量与变更控制.md`.

| Field | Required Content |
| --- | --- |
| Scope link | `REQ-*`, `CARD-*`, and for client work `SCOPE-*` or approved `CHANGE-*` |
| Intended result | user-visible or system-visible behavior and acceptance evidence |
| Allowed files | exact expected files/directories; note why each is needed |
| Forbidden scope | unrelated files, refactors, APIs, data, config, and dependencies that must not change |
| Risk level | low / medium / high with data/auth/deploy impact |
| Verification | targeted tests, manual path, command, and expected result |
| Rollback/data plan | required for migrations, destructive actions, external side effects, public contracts, or production changes |

Stop and ask before expanding beyond this boundary.

## Code Rules

### Structure And Maintainability

- Keep modules responsible for one clear concern. Do not create a shared abstraction until repeated, stable duplication proves it is needed.
- Keep business rules out of presentation-only code and isolate external integrations behind a small boundary.
- Preserve public contracts and compatible behavior unless an approved ADR/change record says otherwise.
- Use names that reveal domain intent. Comment only non-obvious decisions, invariants, or tradeoffs.
- Remove temporary code, debug output, mock bypasses, dead routes, and unused dependencies before a card can pass.

### Inputs, Data, And Side Effects

- Validate untrusted input where it enters the system; use the project's structured validation/parsing approach.
- Apply authentication, authorization, and ownership checks server-side for every sensitive action. Do not trust UI visibility as permission control.
- Use explicit transactions/idempotency/retry/timeout behavior where the architecture requires it; avoid duplicate writes and irreversible partial operations.
- Do not run destructive migrations, delete/overwrite data, or change production schema/configuration without a tested recovery path and explicit approval.
- Keep test data out of production paths. Record migrations, seed/reset procedures, and data retention decisions.

### Secrets, Dependencies, And External Services

- Load secrets and environment-specific values from approved configuration. Commit only examples/placeholders, never live values.
- Minimize dependencies. Before adding one, record purpose, maintenance/security risk, license fit when relevant, version strategy, and removal alternative.
- Give external calls validation, timeout, error handling, observable failure, and a user-safe fallback where the product needs one.
- Do not promise model/API/third-party output, availability, review approval, or cost without a documented degradation path.

### Tests And Verification

- Add/update tests for changed normal behavior and the most relevant failure/edge behavior. Use unit, integration, contract, browser, or manual proof proportionate to risk.
- Re-run affected regression tests after fixes. Run build/lint/type checks when the project provides them.
- For UI changes, verify real interaction states and responsive behavior; for API changes, verify response/error/permission cases; for data/auth/payment changes, use an isolated safe environment.
- Record actual commands and results. “Not tested” is a visible risk, never an implicit pass.

### Review And Commit

- Review the final diff against allowed files, scope IDs, secret scan, debug/dead code, duplicate logic, error paths, compatibility, performance/cost, and test evidence.
- Require a second-model or independent reviewer for high-risk auth, data, payment, security, production, or inherited-code changes when available.
- Commit one coherent verified change at a time. Suggested format: `feat(CARD-001): [result]`, `fix(CHANGE-003): [result]`, or follow the repository convention.

## High-Risk Stop Conditions

Pause for explicit approval and a rollback plan when a change affects:

- production data, migrations, deletion, import/export, retention, or backups
- authentication, permissions, payment, billing, privacy, secrets, or external credentials
- public APIs, shared schemas/types, integrations, deployment, DNS, environment configuration, or customer accounts
- a broad refactor, framework/runtime upgrade, many unrelated files, or a dependency with unclear maintenance/security fit

## Output

Create `PROJECT_ROOT/docs/24-代码质量与变更控制.md`:

```markdown
# 代码质量与变更控制

- 项目：
- 代码规范来源：
- 构建/测试命令：
- 分支与提交规则：
- 当前质量结论：通过 / 有条件通过 / 阻塞

## 全局约束
- 配置与密钥：
- 数据与迁移：
- 权限与安全：
- 依赖与许可证：
- 日志与隐私：

## 变更记录
### CODE-CHG-001 - [title]
- 对应范围/需求/卡片/变更：
- 允许文件：
- 禁止范围：
- 风险与回滚：
- 验证命令与实际结果：
- 审查结论：
- 提交：

## 未解决质量风险
| ID | 风险 | 影响 | 负责人 | 下一步 | 状态 |
| --- | --- | --- | --- | --- | --- |
```
