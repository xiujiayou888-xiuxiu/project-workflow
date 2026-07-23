# Cross-Agent Handoff Template

Use this template whenever a step is delegated to another AI, CLI agent, IDE agent, desktop app, or browser AI. The handoff must be self-contained because the receiving agent may not know the current chat, project state, or file locations.

## Path-First Copy-Ready Packet

```text
你现在接手一个项目步骤，请只完成本步骤，不要扩大范围。

重要规则：
- 请优先根据下面的路径自己读取文件。
- 不要要求用户粘贴整篇文档，除非你明确无法访问某个路径。
- 如果无法访问路径，请告诉用户具体哪个路径无法读取，并继续按“目标路径 + 完整文件内容”的方式返回结果。

项目名称：
当前日期：
项目根目录：
项目路径索引：
当前步骤：
上一步结果：

你正在做的是：
STEP [N] - [阶段名]

本步一句话说明：
[说明本步要完成什么，让普通用户也能看懂]

你需要先读取这些文档：
1. 项目路径索引：
2.
3.

本步骤目标：

产物必须保存到：

完成标志：

不要做的事：
- 不要一次性做后续步骤。
- 不要改动与本步骤无关的文件。
- 不要只把结果保存在你的私有工作区、临时目录、下载目录或聊天附件里。

请使用的工具/模型：
- 工具：
- 推理准确度：
- 成本限制：

请执行：
1.
2.
3.

产物路径规划图：
| 产物名称 | 必须保存到的绝对路径 | 用途 | 下一个 AI 如何使用 |
| --- | --- | --- | --- |
|  |  |  |  |

本步骤路径地图：
| 类型 | 绝对路径/URL/命令 | 状态 | 说明 |
| --- | --- | --- | --- |
| 项目根目录 |  | 已存在/待创建 |  |
| 路径索引 |  | 已存在/待创建 | 每个 AI 先读 |
| 状态文件 |  | 已存在/待创建 | 记录当前步骤 |
| 执行清单 |  | 已存在/待创建 | 记录任务进度 |
| 输入文档 |  | 已存在/待创建 | 本步必须读取 |
| 输出文档 |  | 已存在/待创建 | 本步必须写入 |
| 代码文件 |  | 已存在/待创建 | 本步可能修改 |
| 交接记录 |  | 已存在/待创建 | 记录跨 AI 结果 |
| 交付地址 |  | 已有/待生成/不适用 | local URL / public URL / package path |

如果你可以直接写入文件：
- 请把产物写到上表的绝对路径。
- 完成后回报实际修改/创建的文件路径。

如果你不能直接写入这些路径：
- 请按“目标路径 + 完整文件内容”的格式返回。
- 不要只返回摘要。
- 如果你无法访问某个绝对路径，不要自行换路径；请说明无法访问，并返回要写入该路径的完整内容。

验收证据：

完成后请按这个格式回报：
1. 当前完成的是：
2. 使用工具：
3. 输入/命令：
4. 写入/返回的产物：
5. 实际路径：
6. 本步交付地址：
7. 验收证据：
8. 未完成/阻塞：
9. 给下一个 AI 的上下文：
10. 是否已更新或需要主 AI 更新 项目路径索引.md：
```

## Logging Rule

After using the packet, append a record to `PROJECT_ROOT/docs/15-跨AI交接记录.md`:

```markdown
## YYYY-MM-DD - STEP N - [name]

- Sent to:
- Reason:
- Source documents:
- Required outputs:
- Target paths:
- Path index:
- Returned files/content:
- Verification evidence:
- Delivery URL/path:
- Result:
- Next-agent context:
```

## Minimum Gate

A cross-agent step cannot start unless the packet includes:

- project root
- current step
- path-first instruction
- source documents
- exact task
- exact output path for every artifact
- fallback if file writing is unavailable
- completion report format
- handoff log path
