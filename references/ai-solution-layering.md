# AI Solution Layering

Use this only when AI, automation, knowledge, or Agent behavior is central to the product. It prevents a project from confusing a fast prompt or Skill with a complete product.

## Five Layers

| Layer | Decision to Make | Minimum Evidence |
| --- | --- | --- |
| Business result | Whose costly/risky task changes, what outcome matters, and what must not be optimized away | `REQ-*`, success metric, out-of-scope boundary |
| User workflow | Trigger, supplied inputs, approval points, visible result, retry and handoff path | `JOURNEY-*`, UI flow or CLI flow |
| AI capability | Which model/Skill/tool/knowledge is needed, its input contract, output schema, permissions, confidence rule, and human fallback | `AI-FLOW-*`, test cases, representative real inputs |
| Engineering system | Data source of truth, storage, APIs, queues only when justified, observability, cost/rate limits, and deployment | `ADR-*`, `SLICE-001`, runnable implementation |
| Operations and governance | Ownership, access, audit, prompt/knowledge versioning, evaluation cadence, incident and rollback plan | runbook, logs, review evidence |

## AI Flow Contract

Create one contract for every core AI-powered user action before implementation:

```markdown
### AI-FLOW-001 - [user outcome]

- Related requirement and journey:
- User trigger and accepted input:
- Context/knowledge source and freshness rule:
- Model/tool/Skill role and permission boundary:
- Expected output schema and user-visible result:
- Confidence or quality threshold:
- Invalid, unavailable, unsafe, or low-confidence behavior:
- Human approval or manual fallback:
- Cost/latency ceiling and degradation path:
- Evaluation set, test evidence, and observability:
- Real implementation files/routes and verification command or URL:
```

## Build Order

1. Start with one `AI-FLOW-*` connected to a real critical journey.
2. Implement the smallest end-to-end slice: real input, bounded context, one capability call, visible result, failure path, and evidence.
3. Evaluate it with representative normal, boundary, adversarial, and unavailable-dependency cases.
4. Add more agents, retrieval, workflow steps, or models only after the previous layer is measured and stable.

## Architecture Gate

Do not approve an AI-centered architecture until all answers are concrete:

- Does each AI capability serve a named user task instead of existing because a model is available?
- Can a user understand, correct, retry, or bypass a bad result?
- Is knowledge provenance, freshness, and permission boundary known?
- Are output shape, evaluation method, cost/latency limit, and fallback testable?
- Can another AI find the exact files, contracts, and evidence without guessing?

If a capability cannot pass these checks, keep it out of the MVP or mark it as an experiment rather than claiming it as a finished feature.
