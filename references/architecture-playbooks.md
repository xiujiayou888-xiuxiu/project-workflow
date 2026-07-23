# Architecture Playbooks

Use these playbooks to choose a mature, best-fit architecture. Prefer the simplest option that meets the delivery level, budget, security, and expected scale.

## Decision Inputs

- Project type
- Delivery level: Demo, MVP, Beta, Production
- Budget mode: save money, balanced, safest
- Users and expected traffic
- Data sensitivity
- Auth/payment/admin requirements
- AI/API/file-processing requirements
- Team size and maintenance ability

## Design Sequence

Before selecting a stack, first define the product boundary, critical user journeys, business rules, source-of-truth data, permissions, failure behavior, and operational limits. Then use the relevant playbook below to select the smallest implementation shape.

For the mandatory decision and review format, read `architecture-decision-standard.md`.

## Defaults

- Demo: single app, local or simple hosted deployment.
- MVP: modular monolith, one database, one deployment path.
- Beta: modular monolith with stronger auth, logging, error handling, backups.
- Production: still prefer modular monolith first; split services only when scale, ownership, or reliability requires it.

## Product/SaaS/App

Best default: modular monolith.

Use:

- Web app framework with server/API routes when possible.
- One primary relational database.
- Clear modules: auth, users, billing, core domain, admin, notifications.
- Background jobs only when tasks are slow or retryable.

Avoid microservices until there are independent teams, independent scaling needs, or hard reliability boundaries.

## Website/Content/Landing

Best default: static or mostly static site.

Use:

- Static site or SSR only when content freshness requires it.
- CMS only when non-developers must edit frequently.
- Forms through managed services or simple serverless endpoints.

Avoid databases and custom backends unless the site has accounts, dynamic content, or business workflows.

## Script/CLI/Automation

Best default: single executable script or small CLI.

Use:

- Config file for inputs.
- Logs and dry-run mode for risky operations.
- Idempotent operations where possible.
- Package only after the script proves useful.

Avoid web UI, database, and queues unless repeated multi-user operation requires them.

## Admin/Dashboard/Internal Tool

Best default: CRUD app with strict permissions.

Use:

- Server-rendered or full-stack framework.
- Relational database.
- Role-based access control.
- Audit log for sensitive changes.
- Tables, filters, exports, bulk actions.

Optimize for clarity and operational safety, not marketing-style UI.

## Ecommerce/Marketplace

Best default: use managed commerce/payment primitives where possible.

Use:

- Product/catalog/order/payment modules.
- Payment provider checkout for MVP.
- Inventory and order state machine.
- Admin dashboard and audit log.

Avoid custom payment flows unless absolutely necessary.

## AI Feature/App

Best default: deterministic app shell plus isolated AI service layer.

Use:

- Explicit prompt/version files.
- Input/output validation.
- Cost limits and rate limits.
- Fallback behavior when model calls fail.
- Evaluation set before production.
- Store user data only when required.

Do not use agent chains, vector databases, or fine-tuning unless retrieval, autonomy, or model behavior requirements justify them.

## RAG/Knowledge Base

Best default: document ingestion pipeline + search/retrieval + answer API.

Use:

- Source registry.
- Chunking strategy.
- Embedding/index metadata.
- Retrieval evaluation set.
- Citation/source display.
- Re-indexing process.

Avoid RAG when a simple SQL/filter/search query solves the need.

## Mobile App

Best default: cross-platform app plus managed backend for MVP.

Use:

- React Native/Expo or Flutter when one team needs iOS and Android.
- Native only for heavy platform-specific requirements.
- Managed auth/storage/push where possible.

Avoid custom backend unless product logic or data ownership requires it.

## Desktop App

Best default: desktop shell around local workflows.

Use:

- Tauri/Electron for web-skilled teams.
- Native desktop stack for deep OS integration.
- Local config and clear update path.

Avoid desktop app if a web app meets the distribution and OS integration needs.

## Browser Extension

Best default: extension as thin UI plus backend/API only if needed.

Use:

- Content script for page interaction.
- Background service worker for coordination.
- Minimal permissions.
- Clear data handling.

Avoid broad host permissions and hidden background behavior.

## API/Backend Service

Best default: modular API service with one database.

Use:

- Clear API contracts.
- Auth middleware.
- Request validation.
- Structured logs.
- Health checks.
- Versioned migrations.

Add queues/caches only when latency, retries, or load justify them.

## Data Pipeline

Best default: batch pipeline first.

Use:

- Extract, transform, load stages.
- Checkpointing.
- Idempotency.
- Data quality checks.
- Run logs and failure replay.

Use streaming only when freshness requirements demand it.

## Architecture Output Template

`PROJECT_ROOT/docs/03-技术架构.md` must include:

- Selected architecture
- Product type and why
- Key modules
- Data model
- API/component boundaries
- External services
- Deployment shape
- Scaling path
- Security and privacy notes
- Cost notes
- `REQ-*` to module/card mapping
- critical journey contracts, including failure and recovery behavior
- non-functional budgets and the first vertical slice
- `ADR-*` decision records and independent-review result when risk is high
- Alternatives rejected
