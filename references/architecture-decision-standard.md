# Architecture Decision Standard

Use this before creating or approving `PROJECT_ROOT/docs/03-技术架构.md` for any non-trivial product. The goal is not maximum complexity. The goal is a product that can be built, verified, changed, operated, and handed to another AI without hidden assumptions.

## Architect's Order Of Work

Decide in this order. Do not select a framework before the earlier decisions are clear.

1. Define the product outcome and the 1-3 critical user journeys.
2. Assign `REQ-*` IDs and define each journey's input, output, business rule, and acceptance evidence.
3. Define domain objects, ownership, lifecycle states, and source of truth.
4. Define user roles, permissions, privacy boundaries, and audit needs.
5. Define module, API, event, and UI contracts.
6. Define normal flow, invalid input, empty state, dependency failure, timeout, retry, and recovery behavior.
7. Set non-functional budgets that match delivery level: latency, availability, data loss tolerance, security, cost, and maintenance effort.
8. Choose the simplest stack and deployment shape that satisfies the above.
9. Define the first vertical slice and its verification path.
10. Record decisions, alternatives, risks, and review result before setup.

## Required Architecture Decisions

Record decisions in `PROJECT_ROOT/docs/03-技术架构.md` and `PROJECT_ROOT/决策记录.md`. Use IDs such as `ADR-001`.

| Decision Area | Must Be Explicit |
| --- | --- |
| Product boundary | What the product does and deliberately does not do |
| Critical journeys | Entry, user action, success result, and completion evidence |
| Domain and data | Entities, owner, lifecycle, storage, retention, import/export, source of truth |
| Access control | Roles, permissions, sensitive operations, audit requirement |
| Module boundaries | Responsibilities, allowed dependencies, shared contracts |
| API/integration | Request/response shape, validation, timeouts, retries, idempotency, fallback |
| UI behavior | Loading, empty, invalid, error, success, and recovery states |
| Experience protection | Which data, performance, reliability, and boundary decisions preserve the critical user journey |
| Operational boundary | Logs, health checks, backups, rollback, alerts, support owner |
| Cost boundary | Paid services, quota, rate limits, budget ceiling, degradation path |
| Evolution path | What can grow later and what must not be prematurely built |

For AI-, automation-, knowledge-, or Agent-centered products, also complete the five-layer solution map in `references/ai-solution-layering.md`. Do not treat a model, prompt, Skill, or automation as a product architecture by itself.

## Decision Record Template

```markdown
## ADR-001 - [decision]

- Status: proposed / approved / superseded
- Context: which `REQ-*`, risk, or constraint requires this decision
- Decision: what will be built
- Why: why it fits the product and delivery level
- Alternatives rejected: option and reason
- Consequences: benefits, limitations, cost, and migration risk
- Affected modules/cards:
- Validation: command, test, manual path, or review evidence
- Owner/reviewer:
```

## Critical Journey Contract

For every core journey, write a concise contract before code:

```markdown
### JOURNEY-001 - [name]

- Related requirements: REQ-001, REQ-003
- Preconditions and permissions:
- User action and input:
- System response and stored data:
- Success result and evidence:
- Invalid/empty/duplicate behavior:
- Dependency failure, timeout, retry, and recovery:
- Observability: what log, event, or test proves it happened:
```

## Architecture Quality Gate

Approve architecture only when all answers are concrete:

- Can another AI identify the first files to create and why?
- Does every MVP `REQ-*` map to a journey and feature card?
- Is there one clear source of truth for each important data item?
- Are module and API contracts specific enough to prevent accidental coupling?
- Are permission, invalid input, duplicate action, service failure, and recovery behavior known for core flows?
- Do performance, reliability, security, and cost expectations match the delivery level?
- Is there a minimal vertical slice that proves the architecture early?
- Are unnecessary services and dependencies explicitly rejected?
- Does the architecture support the intended product flow and interaction quality rather than forcing the UI into technical compromises?

If any answer is unknown, ask a focused question or label an `AI默认建议，待确认`; do not hide the gap behind generic architecture language.

## Delivery Anchor

Before approving architecture, define `SLICE-001`, the smallest real vertical slice that proves the architecture inside the actual project:

| Requirement/Card | Real files/routes/API | User action | Command/test/browser proof | Output path/URL | Owner |
| --- | --- | --- | --- | --- | --- |

Start `SLICE-001` immediately after the architecture gate. A diagram, stack list, or folder tree is not architecture evidence until the selected slice can run or produce its declared result.

## Independent Review

For high- or very-high-risk work, use a different model or reviewer before setup. Ask it to challenge only the architecture against the PRD, traceability matrix, critical journeys, and cost/security constraints. Record findings as `ARCH-RISK-*` in `决策记录.md`, then resolve or obtain user acceptance before coding.
