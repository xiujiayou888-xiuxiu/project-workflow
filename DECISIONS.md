# workflow-kit 决策记录

## 2026-08-03 - V3 公开开源发布

- 决策：workflow-kit V3 采用公开 GitHub 仓库发布。
- 原因：用户已明确选择公开开源，不再走低价售卖包作为主路径。
- 边界：不得上传密钥、个人数据、V2 私人归档或其他用户数据；不得删除旧目录和历史归档。

## 2026-08-03 - 许可证选择

- 决策：用户确认 workflow-kit V3 使用 MIT License 公开开源。
- 原因：MIT 简洁宽松，适合该 Skill 仓库作为公开工具分发。
- 当前处理：已补齐 `LICENSE`，README 已指向许可证文件。

## 2026-08-03 - 发布包边界

- 决策：Release 资产只上传 `project-workflow-skill.zip`。
- 原因：该 zip 只包含可安装 Skill 文件，已验证不包含个人归档、V2 私人归档、售卖包或用户数据。

## 2026-08-03 - 接入既有公开仓库

- 决策：目标仓库使用用户提供的 `https://github.com/xiujiayou888-xiuxiu/project-workflow.git`。
- 原因：该仓库已有旧版 `project-workflow v1.0` 历史，应保留而不是覆盖。
- 处理：本地 V3 与远程旧版无共同祖先，因此通过双父合并提交保留双方历史，最终文件树保持 V3，推送使用普通快进，不使用 force push。
