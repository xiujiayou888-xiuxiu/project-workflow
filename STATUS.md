# workflow-kit 状态

## 2026-08-03

- 来源任务已确认 workflow-kit V3 改为公开开源发布，不再按低价售卖路径推进。
- 项目已迁移到 `D:\AI项目\workflow-kit`；旧目录 `D:\Projects\workflow-kit` 保留不动。
- 迁移校验：18 个项目文件一致；树摘要 `0C2573F05922C527EF1208149BB2CF79F20CFE771DD2B49154A84DADE415A3C7`。
- 迁移时 Git HEAD：`4ca4ee7abe29e9ef140f12b50560e2a6dc8db423`。
- 本地 Git 已初始化，V3 改动正在发布前整理，尚未推送远程。
- 敏感信息初扫未发现密钥、token、个人路径或个人联系方式。
- 发布入口已补齐：`README.md`、`CONTRIBUTING.md`、`SECURITY.md`、`.gitignore`、`.gitattributes`。
- 安装包 `project-workflow-skill.zip` SHA256：`849F2F5850AC2E0989C6E14224920AA7BAE64F5B04084328D8A6B7A1AD54DC7B`。
- zip 与源码中的 `SKILL.md`、`agents/openai.yaml`、10 个 `references/` 文件逐项 SHA256 一致。
- Skill 结构校验通过：`project-workflow` 元数据为 `3.0.0`，10 个 reference 模块存在，`allow_implicit_invocation: true`，zip manifest 仅包含可安装 Skill 文件。
- `git diff --check` 通过。
- GitHub CLI 版本：`2.95.0`。
- 许可证已由用户确认为 MIT，并已补齐 `LICENSE`。
- 目标公开仓库：`https://github.com/xiujiayou888-xiuxiu/project-workflow.git`。
- 远程旧版已确认：`origin/main` 原为 `c46a49eb0fc8b7053847cb56e1d3953bde29ffcb`，提交信息为 `project-workflow v1.0 — AI项目全链路开发工作流，30+参考模板`。
- 本地 V3 提交：`d1fa4fca12d91e183d27101574fd81b5fc254784`。
- 远程旧历史与本地 V3 无共同祖先；已用保留双方历史的合并提交接入远程旧版，不使用 force push。
- 当前发布提交：`1c0c4b8987107231ea400bbc9a7751770a5ade79`，已推送到 `origin/main`。
- `v3.0.0` 标签已创建并推送。
- 发布状态记录提交：`bdc125c31087b7db51f297a61dd674bfa4d83085`，已推送到 `origin/main`。
- GitHub Release 已创建：`https://github.com/xiujiayou888-xiuxiu/project-workflow/releases/tag/v3.0.0`。
- Release 资产已上传：`project-workflow-skill.zip`，大小 `38565` 字节，GitHub digest `sha256:849f2f5850ac2e0989c6e14224920aa7bae64f5b04084328d8a6b7a1ad54dc7b`。
- 远程复验：`origin/main` 为 `bdc125c31087b7db51f297a61dd674bfa4d83085`；`v3.0.0^{}` 为 `1c0c4b8987107231ea400bbc9a7751770a5ade79`；本地与远程 ahead/behind 为 `0/0`。
