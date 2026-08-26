# workflow-kit 状态

## 2026-08-27 - V3.5 分阶段交付路线（未发布）

- 已将用户确认的交付顺序写入根 Skill、需求发现、架构工程、执行调度、文档模板、公开说明和上架字段：`基础版 -> 进阶版 -> 高阶版 -> 最终版`。
- 基础版现在是可用、可验收的正式核心闭环；当前阶段只创建本阶段 REQ/CARD。阶段验收后，必须写入 `docs/20-阶段复盘与升版决定.md`，并等待真实证据和用户确认，不能自动派发下一阶段。
- `R1-R4` 保持为风险和治理路由；阶段较小不跳过适用的安全、合规、审批和 POC 门禁。旧项目的 `SLICE-001` 标识兼容，新项目首个基础版切片使用 `BASE-001`。
- 已生成 `RELEASE_NOTES_v3.5.0.md`，但没有创建 tag、Release 或上传资产。
- 已重新生成 `project-workflow-skill.zip`：13 个可安装文件与源码逐项 SHA256 一致，zip SHA256 为 `39ED3A01A2D4AB89FCA39D937D4998F970460B9848DD2EFD8ABD9C8A509511E7`，大小 `54438` 字节；`git diff --check` 通过。
- 当前受限环境不写入 `C:\Users\10641\.codex\skills\project-workflow` 与 `C:\Users\10641\.agents\skills\project-workflow`，两个用户级安装目录仍待有权限时同步。

## 2026-08-12 - V3.4 工具派发与自足交接包规则（未发布）

- 已将用户确认的工具分配规则写入根 Skill、执行调度模块、执行清单模板和公开说明：支持子 Agent 且验证可并行的工具可在上限内多派发独立就绪任务；单会话、不可并行或并发未知工具只按实际需要串行派发，不预占。
- 单一工具竞争按功能卡优先级、依赖满足情况和等待顺序决策，并记录占用与释放条件。
- 已同步 `C:\Users\10641\.codex\skills\project-workflow`、`C:\Users\10641\.agents\skills\project-workflow` 和 `project-workflow-skill.zip`；13 个可安装文件逐项哈希一致，zip SHA256 为 `EEFFBF1A4EC54B7400BD648A3EF4428DAB065845C814AB5FC91C7FDB643051BA`，`git diff --check` 通过。
- `v3.1.0` 标签、GitHub Release 和远程已发布内容未改动；尚未创建 `v3.4.0` 标签或发布资产。
- 每个 `PAR-*` 现在必须生成独立、完整的 `docs\并行任务\PAR-XXX-交接包.md`；总控将下一个工具实际需要的资料按原始绝对路径、SHA256 和用途内嵌其中。外部派发时，聊天显示与文件完全一致的可复制交接包及绝对路径。执行清单新增 `PAR` 交接包索引。
- 当前开发版本提升为 `3.4.0`；尚未创建 `v3.4.0` 标签或发布资产。
- 当前受限环境禁止写入 `C:\Users\10641\.codex\skills\project-workflow` 和 `C:\Users\10641\.agents\skills\project-workflow`，因此两个用户级安装目录尚未同步；源码与安装包已更新并完成一致性校验，当前 zip SHA256 为 `ACC8578EEC9AAB29985ACDB301988EC60C6CB3E507BADD08DB5B48FD01E5A89F`。
- 已新增 `RELEASE_NOTES_v3.4.0.md`：按知络发布信息的结构记录 v3.4.0 已包含能力、安全兼容边界、安装包内容、验证要求和已知限制；明确其仍是本地待发布版本。
- 已新增 `docs\marketplace\workflow-kit上架字段.md`：按上架后台字段组织技能包描述、详细功能、安装说明、使用说明、适用范围、真实限制、交付内容和售后边界；未执行任何平台上架操作。

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

## 2026-08-03 - V3.1 开发前复用门禁

- 来源任务已确认：给 project-workflow Skill 增加“开发项目前先查 GitHub/成熟生态是否有可参考或可复用项目”的强制能力。
- 目标版本：`3.1.0`，作为向后兼容功能新增；必须保留 `v3.0.0` 标签和 Release，不移动旧标签，不 force push。
- 新增固定产物：`docs/02-开源参考与复用评估.md`。
- 门禁要求：R1 快速检查或写跳过理由；R2-R4 在正式架构/编码前必须搜索 GitHub、官方模板、包管理生态和成熟核心组件；AI/Agent、UI、部署等项目要补查对应官方 SDK、成熟引擎、设计系统或部署模板。
- 证据要求：每个候选必须记录真实 URL、仓库/包、许可证、版本/commit、检查日期和证据；不能联网或查不到写 `unknown/未完成`，禁止编造。
- 安全边界：采用前检查许可证、NOTICE/署名、维护、安全、供应链和总成本；禁止整库照搬、来源不明复制、许可证不兼容或把高风险停更仓库直接用于生产。
- 合法合规硬门禁：任何项目都必须检查第三方权利、数据/内容/模型授权、隐私、适用法律/行业规则和违法滥用风险；R1 也不能跳过，无法确认时写 `unknown/未完成` 并暂停采用或实现。
- 本次本地验收通过：元数据、引用、R1-R4/AI/UI/部署/拆解/许可证/合法合规场景矩阵、Markdown 代码围栏、ZIP manifest 和逐文件哈希均通过。
- `project-workflow-skill.zip` SHA256：`A80E2FA91272BBBAB3324B52D072CF8906814D714A31713B6699DA6934E1F3D4`，大小 `48287` 字节；源码、`C:\Users\10641\.codex\skills\project-workflow` 和 `C:\Users\10641\.agents\skills\project-workflow` 均为 13 个文件且逐项一致。
- 官方 `codex` CLI validator 当前无法执行：命令返回 Windows `Access is denied`；已用等价本地检查替代并保留该限制。
- 本地提交：`022600e68b010e9fde7727d1a3a6b81814536479`；本地 `v3.1.0` 注释标签已创建并指向该提交，`v3.0.0` 未改变。
- GitHub 连接器已将同一 18 文件变更树同步到远程 `main` 提交 `5492645b4e25fbebfa3ec3db09afb5b57d73c98e`，未使用 force update。
- 发布阻塞：命令行 HTTPS 无法连接 GitHub `443`；SSH 缺少 host key；`gh auth status` 显示未登录；当前连接器没有创建 Git tag/Release/上传 Release asset 的接口。未编造标签或 Release URL。
- 恢复动作：运行 `gh auth login`（或配置 `GH_TOKEN`），然后普通推送 `git push origin v3.1.0`，创建 Release 并上传 `project-workflow-skill.zip`，再复验远程 `main`、tag、Release URL 和资产 SHA256。
- 当前执行状态：源码、安装同步、打包、本地验收和远程 `main` 同步完成；仅 GitHub `v3.1.0` 标签、Release 和资产待外部授权/网络恢复后完成。
