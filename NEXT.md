# workflow-kit 下一步

## V3.5 发布收尾

- 已发布 `v3.5.0`；后续仅在出现明确改动后规划下一版本，不移动 `v3.5.0` 标签或覆盖 Release 资产。
- 可使用基础版到最终版的真实项目进行一次端到端验证，确认阶段复盘会在没有用户确认时阻止后续版本派发。
- 如准备平台上架，使用 `docs\marketplace\workflow-kit上架字段.md` 填写后台字段，并由用户确认商品标题、定价、封面与外部发布范围。
- 受限环境中的两个用户级安装目录在获得写入权限后再同步；不影响 GitHub Release 安装包的使用。

## 发布收尾

- 后续维护新版本时，从 `main` 创建正常提交，不使用 force push。
- 如修改安装内容，重新打包 `project-workflow-skill.zip` 并更新 Release 资产。
- 可在 GitHub 仓库说明中补充更短的中文介绍和 topic。

## V3.1 发布前检查

- 确认根 `SKILL.md` metadata 为 `3.1.0`。
- 确认 `docs/02-开源参考与复用评估.md`、相关 `references/`、README、总文档、说明和安装 zip 内容一致。
- 同步 `C:\Users\10641\.codex\skills\project-workflow` 和 `C:\Users\10641\.agents\skills\project-workflow`。
- 运行结构、引用、代码围栏、zip manifest、安装目录一致性和场景矩阵检查。
- 验证所有路由均执行合法合规门禁：权利来源、授权范围、许可证/NOTICE、数据依据、隐私和适用法律/行业规则；疑点必须保留 `unknown/未完成`。
- 外部发布恢复后：完成 `v3.1.0` 标签、GitHub Release 和 `project-workflow-skill.zip` 资产上传；保留 `v3.0.0` 不变，并复验真实 URL、资产 SHA256、远程同步和工作区干净。
