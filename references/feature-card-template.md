# Feature Card Template

Use this same structure for every split task. Do not invent ad hoc card formats.

## Execution Table Columns

| Priority | Status | Card ID | Parallel Eligibility | Requirement IDs | Architecture Decision IDs | Task Name | User Result | Deliverable Name | Save Path | Owner Tool | Task Lock | Model/Reasoning | Dependencies | Interface Contract | Failure/Recovery Contract | Prompt/Command | Cross-Agent Handoff | Quality Gate | Acceptance Evidence | Card Review | Commit |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

Required status values:

- Not started
- In progress
- Blocked
- Done
- Review failed
- Review passed
- Accepted

## Card Detail Template

```markdown
### CARD-[number] - [name]

- Priority:
- Status:
- Parallel eligibility: sequential by default / PAR-[number] after coordinator approval
- Requirement IDs:
- Architecture decision IDs:
- User-visible result:
- Product/design intention:
- Why this card exists:
- Dependencies:
- Input contract:
- Output contract:
- Normal user flow:
- Invalid/empty/error/permission behavior:
- Dependency failure and recovery behavior:
- Realistic input/output example:
- Visual/interaction expectation, if user-facing:
- Related UI control IDs:
- Implementation anchors:
  - Files/components/routes/API:
  - Command/tool action:
  - Test/manual verification:
  - User-visible URL/package/output:
- Data changes:
- API/component changes:
- UI changes:
- Files likely involved:
- Deliverable name:
- Save path:
- Owner tool:
- Task lock:
  - Owner:
  - Allowed files:
  - Forbidden files:
  - Release condition:
- Parallel assignment, if approved:
  - PAR-ID:
  - Exclusive files/folders:
  - Branch/worktree:
  - Coordinator merge condition:
  - Timeout/round limit:
  - Cost ceiling:
  - Fallback owner:
- Model/reasoning:
- Prompt/command:
- Cross-agent handoff:
  - Send to:
  - Source docs:
  - Output paths:
  - Return format:
- Quality gate:
- Acceptance evidence:
- Card-level review checklist:
  - Requirement match:
  - Interface contract respected:
  - Output format consistent:
  - Error/empty/loading states handled:
  - Failure/recovery contract handled:
  - Requirement and architecture IDs remain traceable:
  - Product/design intention is visible in the result:
  - Realistic journey works without placeholder or dead-end:
  - Every related UI-CTRL has correct states and evidence:
  - Implementation anchors exist and match the card claim:
  - Tests or manual verification done:
  - No unrelated refactor:
  - Integration risk:
- Review result:
- Commit:
```

## Card-Level Review Rule

After each card is implemented, review it before moving on.

Review must check:

- It satisfies the card user result.
- It respects input/output contracts.
- It saves artifacts to the declared path.
- It does not change unrelated behavior.
- It has acceptance evidence.
- It can integrate with previous cards.
- It updates shared types, APIs, or docs when needed.

If review fails, mark the card `Review failed`, fix it, and review again. Do not start the next card until review passes.
