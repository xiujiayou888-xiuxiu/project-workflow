# Release Preflight

Use this after mature review and before every deployment, public release, store submission, package publish, or production migration. Also read it at architecture time and apply the relevant rows continuously during setup, feature work, and integration. Scale the checks to the delivery level, but do not skip environment separation, secrets, test status, and production-safe configuration for MVP, Beta, or Production.

## Rules

- Inspect first. List findings, severity, evidence, owner, and proposed fix. Ask the user before changing production configuration, deleting data, rotating secrets, changing DNS, or deploying.
- Explain every failed check in plain language: what it means, why it matters, what could happen, and the smallest safe next action.
- Do not mark a release ready when a P0 exists. P1 requires a fix or explicit user risk acceptance. P2 can be scheduled with an owner and date.
- Use actual files, command output, provider settings, browser evidence, or URLs. An AI statement is not evidence.

## Shift-Left Gates

| When | Apply These Rows Now | Required Project Record |
| --- | --- | --- |
| Architecture | environment isolation, secrets/configuration, authorization, privacy, logging, storage, operations | `docs/03-技术架构.md`, `决策记录.md`, `docs/14-工程保障清单.md` |
| Setup | isolated configuration, no committed secrets, debug defaults, safe migration/seed/reset, baseline build/test | `docs/04-初始化设置.md`, `docs/14-工程保障清单.md` |
| Feature card | authorization, validation, API privacy, rate/cost guard, safe logs, upload handling | feature-card review, `docs/05-功能开发记录.md`, tests |
| Integration | remove temporary exposure, production-like data separation, compatibility/performance, smoke/rollback evidence | `docs/08-总装集成.md`, `docs/14-工程保障清单.md` |

Record each check as `Planned`, `Implemented`, `Verified`, `Blocked`, or `Not applicable` with evidence. The release preflight may not change a `Planned` item to `Verified` without real implementation and validation.

## Required Checks

| Area | Check | Evidence | Default Severity if Failed |
| --- | --- | --- | --- |
| Environment isolation | Development and production use separate database, secrets, domains/configuration; production debug mode is off | environment inventory, provider settings, config names | P0 |
| Secrets | No password, API key, token, connection string, or private credential is committed, hard-coded, logged, or returned by an API | secret scan, Git scan, API sample, log sample | P0 |
| Release configuration | Production variables are documented, validated, least-privilege, and loaded only from provider secrets or secure configuration | `.env.example`, deployment settings, startup validation | P0/P1 |
| Build and tests | Lockfile, build, lint/type check where applicable, migrations, and core normal/failure-path tests pass | command output and test report | P0/P1 |
| Temporary exposure | Debug output, mock data, test accounts, temporary routes, bypasses, admin backdoors, and unprotected debug endpoints are removed or blocked | code/API route review, browser/API evidence | P0 |
| Production data | Production database has migration/backup/restore plan and contains no accidental development seed/test data | migration record, backup test, approved cleanup plan | P0/P1 |
| Authorization and abuse | Sensitive actions enforce identity and ownership; common injection defenses exist; login, SMS, payment, upload, and expensive actions have appropriate rate limits | review findings, tests, manual/API checks | P0/P1 |
| Privacy | Responses, browser errors, and logs do not disclose passwords, tokens, full personal identifiers, internal stack traces, or other users' data | API samples, error test, log sample | P0 |
| Logging and recovery | Important account, money, permission, and important-data changes log time, actor ID, action, result, and safe error reason; no sensitive values are logged | log specification, sample, retention/owner | P1 |
| Files and media | Projects with user uploads validate type/size and store scalable media in approved object storage or have an explicit capacity/backup decision | upload test, storage configuration, retention policy | P1 |
| Web experience | Web products pass critical-flow checks in relevant browsers and desktop/mobile; heavy effects are justified and do not break the main task on ordinary devices | browser screenshots, performance/flow evidence | P1/P2 |
| Operations | Health/smoke test, monitoring or at least actionable logs, rollback method, release owner, and support path exist for the delivery level | runbook, URL, rollback command, owner | P1 |

## Output Template

Create `PROJECT_ROOT/docs/22-发布前体检.md`:

```markdown
# 发布前体检

- 项目/版本：
- 项目根目录：
- 目标环境与发布地址：
- 检查时间与执行人：
- 交付等级：Demo / MVP / Beta / Production
- 结论：可发布 / 修复后发布 / 暂不发布

## 环境清单
| 环境 | 域名/入口 | 数据库标识 | 配置/密钥位置 | 调试状态 | 证据 |
| --- | --- | --- | --- | --- | --- |
| 开发 |  |  |  |  |  |
| 生产 |  |  |  |  |  |

## 检查结果
| ID | 检查项 | 结果 | 风险 | 证据路径/命令/URL | 影响说明 | 建议下一步 | 是否需用户确认 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| REL-001 | 环境隔离 | 通过 / 失败 / 不适用 | P0/P1/P2 |  |  |  | 是/否 |

## 待修复项
| 风险 ID | 问题 | 涉及文件/平台 | 推荐工具 | 修复后验证 | 状态 |
| --- | --- | --- | --- | --- | --- |

## 发布决定
- P0：
- P1：
- 用户已接受的风险：
- 批准发布人：
- 发布后冒烟测试：
- 回滚条件与动作：
```

## Beginner Prompt

Use this only after the user confirms they want the inspection:

```text
请作为发布前质量与安全检查员，只检查、不自动修改。读取 [项目根目录] 下的项目状态、架构、测试、审查、部署和环境配置说明，生成并保存 [项目根目录]/docs/22-发布前体检.md。

逐项检查环境隔离、密钥泄露、生产调试模式、构建和测试、临时接口和测试数据、权限/注入/限流、隐私和日志、上传媒体存储、Web兼容与性能、监控和回滚。每项必须给出证据路径或命令、P0/P1/P2 风险、白话解释和最小修复建议。先把问题清单发我确认，未经确认不要改生产配置、删除数据、轮换密钥或部署。
```
