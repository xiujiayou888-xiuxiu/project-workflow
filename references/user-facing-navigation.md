# User-Facing Navigation

## Purpose

Keep the project workflow easy to operate for a non-technical user. The agent carries the architecture, quality, cost, and handoff complexity in project files; the user receives one clear next action at a time.

## Default Reply Rules

For each current step, show only:

1. Current step name and one-sentence outcome.
2. The exact tool to open.
3. One copy-ready prompt or one concrete click/input action.
4. A visible completion signal.
5. The artifact name and absolute save path.
6. The smallest useful report the user should send back.
7. A single approval question before an unexecuted action.

Use plain Chinese. Avoid showing terms such as ADR, risk register, task lock, trace matrix, architecture layers, or model-routing rationale unless the user asks or a decision depends on it.

## What Stays Internal

Keep the following updated but normally out of chat:

- `项目状态.md`
- `项目路径索引.md`
- `AI执行清单-进度表.md`
- `决策记录.md`
- risk, review, evidence, traceability, and handoff documents

Never omit the output path from a cross-AI prompt. The receiving agent must be able to open the listed paths and know exactly where to write its artifact without relying on the conversation.

## When To Expand

Use the full execution map only when one or more conditions apply:

- The user says `展开执行详情`, `给我完整地图`, or asks why a tool/model was selected.
- The task uses parallel agents, branches, or worktrees.
- The task involves production, security, payments, personal data, destructive changes, contracts, a fixed-price client commitment, or another high/very-high-risk decision.
- A handoff fails, the artifact path is unavailable, or the quality gate fails.

Even when expanded, begin with the compact action card, then put the detail under `### 执行详情（可展开）`.

## Handoff Prompt Standard

The handoff prompt must always state:

- current `STEP N` and its sole purpose
- exact absolute input paths
- allowed and prohibited write scope
- exact absolute output path
- completion standard
- five-item report: work done, artifact path, changed files, evidence, blockers

Do not include generic project history, hidden reasoning, or unrelated future steps.

## Completion Behavior

When evidence arrives:

1. Update the step artifact and state records automatically.
2. Check only the current quality gate.
3. If it passes, say that the step is complete in one sentence and immediately show the next compact action card.
4. If it fails, show the smallest repair card for the current step; do not skip ahead.
