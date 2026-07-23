# Engineering Readiness

Use this before final delivery. Scale depth by delivery level: Demo needs essentials; MVP needs repeatable setup; Beta/Production need operational safety.

## Checklist

| Area | Check |
| --- | --- |
| Repository | Git initialized, meaningful commits, clean working tree or known pending changes |
| Environment | `.env.example` or equivalent exists; required variables are documented |
| Secrets | no secrets committed; API keys stored in env/provider secrets |
| Dependencies | lockfile present when applicable; unused risky dependencies removed |
| Build | build command documented and passes for MVP/Beta/Production |
| Tests | test command documented; core happy path and failure path covered |
| Database | migrations exist; seed/reset path documented; backup/restore noted when needed |
| Files/storage | upload limits, file type validation, cleanup policy documented |
| API contracts | request/response shape stable; errors are explicit |
| Auth/permissions | roles and access boundaries documented when auth exists |
| Logging | useful app/server logs exist; sensitive data not logged |
| Monitoring | health check or smoke test exists for Beta/Production |
| Observability | key user journey, failures, latency, and cost signals can be inspected for Beta/Production |
| Recovery | backup restore or data-recovery procedure is tested when user data is material |
| Deployment | platform, URL, env vars, deploy command, and rollback path documented |
| Release | version/tag/final commit, go/no-go decision, and post-release smoke test recorded |
| Maintenance | owner, known risks, next action, and support notes documented |

## Output

Create `PROJECT_ROOT/docs/14-工程保障清单.md` with:

- delivery level
- checked items
- skipped items and reason
- unresolved risks
- accepted risks
- final commit/version
- next maintenance action
- release decision, smoke-test evidence, and recovery owner for Beta/Production

For any deployment or public release, also use `release-preflight.md` and create `PROJECT_ROOT/docs/22-发布前体检.md`. Engineering readiness records whether the project can be operated; release preflight is the final risk check before exposing it to users.
