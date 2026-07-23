# Module Evolution And Upgrade Safety

Use this for every non-trivial project and before any V2+ release, installer update, schema change, data migration, or shared-contract change. It makes modules independently repairable and keeps an upgrade from silently becoming a data-loss event.

## Module Contract

Define modules by responsibility and ownership, not by arbitrary folders. Every `MOD-*` must have:

| Field | Required Decision |
| --- | --- |
| Responsibility | the one product/domain concern it owns |
| Inputs/outputs | public functions, API/events, commands, UI contracts, and error behavior |
| Data ownership | source of truth, schema/entities/files it may write, retention and export rules |
| Allowed dependencies | modules/services it may call; forbidden direct access to other modules' private data |
| Change boundary | files/config/routes it may own and shared contracts requiring coordinator approval |
| Independent verification | focused test, fixture, smoke path, or contract test proving it can be repaired safely |
| Observability | logs/metrics/error signal needed to diagnose it without guessing |

Rules:

- Keep internal implementation private behind a small stable contract.
- Use adapter/compatibility boundaries when replacing a dependency or versioning a public contract.
- A cross-module change requires an approved ADR/change record, updated contract tests, and integration verification.
- Do not let a “quick fix” bypass module ownership or write another module's data directly.

## Data Preservation Rules

### Application And Installer

- Treat the application install directory as replaceable code only. Store user data in an OS-appropriate application-data location, an approved database, object storage, or a user-selected workspace outside the install directory.
- Separate code version from data-schema version. Detect old schema/data on startup and migrate deliberately.
- Do not use uninstall/upgrade cleanup scripts that delete data directories, databases, uploads, exports, backups, or project workspaces by default.
- Require explicit user confirmation, a clear target path, and backup/restore instructions for any deletion/reset action.

### Server And Cloud Data

- Back up or take a verified recovery point before material schema/data migration.
- Prefer expand-migrate-contract: add compatible fields/tables first, deploy readers/writers that tolerate both versions, migrate/backfill, verify, then remove legacy structures only in a later approved release.
- Use transactions, batches, checkpoints, idempotency, and monitoring where the data size/risk needs them.
- Never rely on a migration having run “somewhere”; record exact command, environment, version, result, and recovery path.

## Upgrade Gate

No V2+ release that touches stored data, configuration, file layout, public APIs, or user workflows may pass without:

1. source version and target version recorded;
2. inventory of data/config/assets affected;
3. compatibility decision and user-visible breaking-change note where needed;
4. backup/recovery point and tested restore action;
5. migration code/steps that are idempotent or safely resumable;
6. representative V1-to-V2 upgrade test proving data remains present and usable;
7. rollback decision: safe rollback, forward-only with restore, or an approved limitation;
8. release preflight evidence and an owner for upgrade support.

## Output

Create `PROJECT_ROOT/docs/26-模块契约与升级方案.md`:

```markdown
# 模块契约与升级方案

- 项目：
- 当前应用版本 / 数据版本：
- 目标版本：
- 结论：可独立维护 / 需补契约 / 升级阻塞

## 模块清单
| MOD-ID | 模块与职责 | 数据所有权 | 公共契约 | 允许依赖 | 禁止访问 | 独立验证 | 负责人 |
| --- | --- | --- | --- | --- | --- | --- | --- |

## 共享契约变更
| ADR/CHANGE | 受影响模块 | 兼容方案 | 测试与集成证据 | 批准 |
| --- | --- | --- | --- | --- |

## 用户数据位置与保护
| 数据类型 | 位置 | 是否在安装目录外 | 备份/导出 | 删除规则 |
| --- | --- | --- | --- | --- |

## V1 -> V2 升级计划
| MIG-ID | 源版本 -> 目标版本 | 影响数据 | 迁移/兼容方式 | 可重复执行 | 验证 | 回滚/恢复 |
| --- | --- | --- | --- | --- | --- | --- |

## 升级演练证据
- V1 数据样本：
- 升级命令/安装包：
- 数据保留验证：
- 回滚/恢复验证：
- 未解决风险：
```

## Skill Package Upgrade Policy

This workflow Skill is an instruction package, not a user-data store. Its upgrade must replace only its own `SKILL.md` and bundled reference files. It must never delete or overwrite project roots, generated project documents, user databases, uploads, exports, credentials, or other installed Skills. When an instruction schema changes, preserve existing project documents and add a migration note/compatibility mapping rather than resetting the project.
