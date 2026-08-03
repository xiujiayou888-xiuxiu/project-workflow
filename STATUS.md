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
- 阻塞：GitHub CLI 当前未登录。
