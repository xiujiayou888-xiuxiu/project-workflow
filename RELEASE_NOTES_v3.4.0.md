# workflow-kit v3.4.0 - Tool Dispatch and Self-Contained Handoff Packs

Release date: 2026-08-12

Release status: local package prepared; not tagged, published, or uploaded.

## Included

- Tool allocation based on verified concurrency: a tool with verified sub-Agent support, independent context, real parallelism, and required write isolation can receive multiple non-conflicting ready tasks within its concurrency limit.
- On-demand serial allocation for single-session, non-parallel, or concurrency-unknown tools. These tools are not reserved in advance.
- A deterministic conflict order for a single tool: `CARD-*` priority, satisfied dependencies, then waiting order. Occupancy and release conditions are recorded in the execution plan.
- One self-contained handoff pack per dispatched task: `docs/并行任务/PAR-XXX-交接包.md`.
- Each handoff pack contains the task objective, allowed and prohibited changes, acceptance criteria, and the complete text of files the next AI actually needs. Each embedded source records its original absolute path, SHA256, and purpose.
- The external-handoff chat block must match the corresponding handoff-pack file exactly. Users can reopen it with `查看交接包 / 打开 PAR-XXX`.

## Safety and Compatibility

- Existing R1-R4 routing, A0-A4 capability checks, confirmation rules, reuse gates, compliance gates, and high-risk confirmations remain in effect.
- A saved handoff pack is an audit and transfer artifact; it is not evidence that an external tool was started or completed work.
- Binary, large, or context-limited materials are not silently omitted. The handoff pack records their path, SHA256, retrieval method, and reason they were not embedded.
- No account login, payment, production release, data migration, deletion, or execution of unfamiliar code is enabled by these changes.

## Package Contents

- `project-workflow-skill.zip` contains 13 installable files: the root `SKILL.md`, `agents/openai.yaml`, the reuse-evaluation document, and ten `references/` modules.
- The archive excludes project status files, decision records, source examples, local archives, user project data, private material, secrets, and personal configuration.
- Install by extracting `project-workflow/` into the target AI tool's Skill directory, then start a new session with `$project-workflow`.

## Verification Required for This Build

- Root metadata is `3.4.0` and all ten reference modules are present.
- All 13 installable files in the archive match the repository source by SHA256.
- `git diff --check` passes.
- Archive SHA256: `ACC8578EEC9AAB29985ACDB301988EC60C6CB3E507BADD08DB5B48FD01E5A89F`.
- Archive size: `50,610` bytes.

## Known Limits

- `v3.4.0` is not yet a Git tag or GitHub Release. The currently published release remains `v3.1.0`.
- This package defines how a compatible host should create and display handoff packs. Actual sub-Agent creation, parallelism, external-tool control, and context limits still depend on the host's verified capabilities.
- The current package verification covers source and archive consistency. User-level Skill-directory synchronization must be rechecked in the target runtime before distribution.
