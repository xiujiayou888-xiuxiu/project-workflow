# Artifact Quality Standard

Use this before creating major artifacts such as PRD, product framework, architecture, execution plan, UI style plan, feature cards, integration plan, review report, deployment notes, user guide, and final deliverable docs.

## Goal

Every artifact must be polished, precise, useful for the next AI, and easy for a normal user to understand.

## Quality Bar

An artifact is acceptable only when it is:

- Precise: no vague phrases such as “完善功能”, “处理逻辑”, “优化一下” without concrete meaning.
- Complete enough: includes objective, scope, inputs, outputs, owner, path, acceptance evidence, and next action.
- Polished: clean structure, readable headings, consistent tables, no messy duplicated sections.
- Actionable: a user or another AI can immediately know what to do next.
- Traceable: links to source docs, output paths, decisions, and evidence.
- Cost-aware: does not recommend expensive tools without reason.
- Risk-aware: names blockers, assumptions, and required approvals.
- Design-complete: for product-facing work, explains why the flow, architecture, interaction, and visual direction fit this specific product rather than a generic template.

## Required Header For Major Docs

```markdown
# [Document Name]

- Project:
- Version:
- Updated:
- Project root:
- Source docs:
- Owner:
- Status:
- Next action:
```

## Global Control Block

Every execution-facing document should include:

```markdown
## 全局掌控

| 项 | 内容 |
| --- | --- |
| 当前阶段 |  |
| 当前步骤 |  |
| 总进度 |  |
| 已完成 |  |
| 正在做 |  |
| 下一步 |  |
| 阻塞项 |  |
| 本步负责人/工具 |  |
| 本步产物路径 |  |
| 验收证据 |  |
```

## Precision Rules

Replace vague instructions:

| Vague | Precise |
| --- | --- |
| 做上传功能 | 实现单张 PNG/JPG 上传，限制 10MB，上传后显示预览 |
| 优化 UI | 按 `06-UI风格方案.md` 调整按钮、间距、色彩、空状态，并提供截图 |
| 写后台 | 实现管理员查看用户上传记录的页面，不包含权限分级 |
| 接 AI | 调用指定模型接口，输入图片，返回处理后图片 URL，失败显示错误状态 |

## Functional Clarity Gate

Before implementation, each core function must define:

- User action
- System response
- Input
- Output
- Data saved or changed
- Error/empty/loading states
- Permission rule
- Acceptance evidence

If any of these are unknown, ask the user a supplemental question or mark an explicit AI default for confirmation.

## Polished Output Checklist

Before returning an artifact:

- Is the document formatted cleanly?
- Are all paths absolute when known?
- Does every task have an owner tool?
- Does every output have a save path?
- Does every step have completion evidence?
- Are assumptions labeled?
- Are open questions separated from confirmed decisions?
- Can another AI continue from this artifact without chat history?
