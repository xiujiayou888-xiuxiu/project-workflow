# Requirements Intake Template

Use this before writing `PROJECT_ROOT/docs/01-PRD产品需求文档.md`.

Ask in small rounds. Never ask more than 4 questions at once. Each round should make the next artifact more accurate.

## Round 1 - Project Core

Ask first:

1. 这个项目给谁用？
2. 它要解决什么痛点或完成什么任务？
3. 用户最终看到什么结果，才算有用？
4. 这是自用、客户交付、公开产品，还是练手 Demo？

Do not ask beginners to name a framework, model, database, or architecture. If technical choices affect the result, make a conservative recommendation later and explain it in plain language.

## Round 2 - User Journey

Ask when the goal is clear:

1. 用户从打开产品到完成目标，理想流程是哪几步？
2. 输入是什么？文字、图片、文件、表格、链接、账号数据，还是别的？
3. 输出是什么？页面结果、下载文件、通知、报告、API、自动动作？
4. 哪一步最重要，必须第一版做好？

## Round 3 - MVP Scope

Ask to prevent scope drift:

1. 第一版必须有哪 1-3 个功能？
2. 哪些功能这版明确不做？
3. 有没有类似产品或参考对象？
4. 如果时间只够做一个功能，先做哪个？

## Round 4 - Platform And Environment

Ask only what applies:

1. 做成网页、桌面软件、手机 App、浏览器插件、CLI、自动化脚本，还是 API？
2. 主要在电脑、手机、平板，还是服务器上用？
3. 是否需要本地运行、局域网使用、还是公网访问？
4. 用户电脑上已有的工具或环境限制是什么？

## Round 5 - Data, Permissions, Integration

Ask for product/app projects:

1. 是否需要登录、用户权限、管理员后台？
2. 是否需要数据库、文件上传、导入导出、历史记录？
3. 是否需要支付、会员、额度、订阅？
4. 是否接第三方 API、AI 模型、微信/飞书/Notion/GitHub 等服务？

## Round 6 - UI And Experience

Ask for interface projects:

1. 你希望界面给人的感觉是什么？专业、极简、高级、可爱、科技感、工具感、内容感？
2. 有没有喜欢或不喜欢的参考产品？
3. 主要用户是频繁操作还是偶尔使用？
4. 移动端是否必须好用？

## Round 7 - Delivery, Cost, Acceptance

Ask before PRD confirmation:

1. 交付等级是 Demo、MVP、Beta，还是 Production？
2. 预算模式是省钱、平衡，还是最稳？
3. 什么结果算第一版验收通过？
4. 交付物是什么：源码、URL、安装包、CLI、文档、视频演示，还是部署好的服务？

## Round 8 - Business Rules And Failure Boundaries

Ask after the MVP functions are known. Ask only the missing questions, at most four in one round:

1. 每个核心功能有什么不能做错的规则？例如金额、次数、状态顺序、审批条件、数据归属。
2. 用户输错、重复提交、文件不合格、没有数据、网络或第三方服务失败时，产品分别应该怎样处理？
3. 有没有一两条真实的输入和期望输出示例？什么结果属于绝对不能接受？
4. 哪些指标有硬要求：响应时间、可同时使用人数、费用上限、数据保存时间、可恢复性？

## PRD Required Fields

The PRD must include:

- 项目名称
- PRD 版本
- 项目根目录
- 背景和目标
- 目标用户
- 用户痛点
- 核心场景
- 用户操作流程
- MVP 功能
- 不做范围
- 输入与输出
- 数据和文件需求
- 登录、权限、支付、管理后台需求
- 第三方服务/API/AI 模型需求
- UI 风格初始方向
- 平台和设备要求
- 预算模式
- 交付等级
- 验收标准
- 验收证据
- 风险与限制
- AI 默认建议
- 待确认问题
- `REQ-001` 起的需求编号
- 核心功能的业务规则、正常流程、异常流程和不可接受结果
- 核心功能的真实输入/输出示例
- 性能、可靠性、成本、隐私和维护约束（适用时）

## Defaulting Rule

If the user does not know an answer, choose a conservative default and label it:

```text
AI默认建议，待确认：[default]
```

Do not hide assumptions.
