# D Drive Document Storage Policy

## Purpose

Keep every AI-readable project document in one stable D-drive location. Agents change, chats disappear, and tool-private folders are not reliable project archives.

## Roots

Use two explicit absolute roots:

| Root | Purpose | Default |
| --- | --- | --- |
| `PROJECT_ROOT` | project control root: all Markdown, plans, state, evidence, handoffs, project master document, and `docs/` | `D:\AI项目\[项目名]` for a new project; `D:\AI项目文档库\[项目名]` for an existing project outside D |
| `CODE_ROOT` | source repository, package, worktree, and executable files | same as `PROJECT_ROOT` for a new project; existing repository path for inherited/existing code |
| `PROJECTS_HUB_ROOT` | global index of all projects | `D:\AI项目文档库` unless the user configures another D-drive root |

For a new project, prefer one D-drive folder so source and documents stay together:

```text
D:\AI项目\项目名\
├── docs\
├── 项目状态.md
├── 项目路径索引.md
├── AI执行清单-进度表.md
└── source files...
```

For an existing repository that must not be moved, keep code where it is and create a D-drive control root:

```text
D:\AI项目文档库\项目名\
├── docs\
├── 项目状态.md
├── 项目路径索引.md
└── AI执行清单-进度表.md

CODE_ROOT = [existing repository absolute path]
```

## Path Index Requirement

At the top of `PROJECT_ROOT/项目路径索引.md`, record:

```markdown
# 项目路径索引

- 文档总控根目录（PROJECT_ROOT）：D:\...
- 代码根目录（CODE_ROOT）：D:\... 或其他已存在路径
- 全局项目索引（PROJECTS_HUB_ROOT）：D:\AI项目文档库\所有项目总索引.md
- 工具扫描：D:\...\docs\00-工具与权限扫描.md
```

Every worker handoff must include `PROJECT_ROOT`, `CODE_ROOT`, and the exact input/output paths. Documents always go under `PROJECT_ROOT`; code changes always name `CODE_ROOT` or its dedicated worktree/branch.

## Never Use As Canonical Storage

Do not use these as the only saved location:

- `C:\Users\...\.codex\skills\...` or `C:\Users\...\.agents\skills\...`
- temporary folders, browser downloads, desktop screenshots, chat attachments
- agent-private workspaces, worktrees without a recorded branch/path, or tool-generated cloud drafts

Copy stable outputs into `PROJECT_ROOT` and record any original external URL/source in the path index or relevant delivery record.

## Exceptions

Respect an explicit user-selected D-drive path. For a non-D path, warn once that it breaks the default centralized archive, record the exception, and continue only after the user confirms. Never silently move an existing repository or user data.
