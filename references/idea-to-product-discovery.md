# Idea To Product Discovery

Use this only in `想法落地` mode. The user supplies an intention; the AI helps turn it into a bounded product decision before architecture or code exists.

## Discovery Rules

- Preserve the original idea, then distinguish it from AI hypotheses and confirmed decisions.
- Start with the user pain, target user, desired before/after result, and one critical journey. Do not start with a technology or a feature list.
- Reduce V1 to the smallest useful outcome. Mark attractive but nonessential ideas as later candidates, not hidden commitments.
- Challenge unclear claims with examples: what users do today, what input they provide, what result they see, what would make the result unacceptable.
- Treat budget, deadline, privacy, data, login, payment, AI/API, and delivery level as design constraints, not afterthoughts.

## Output

Create `PROJECT_ROOT/docs/00-创意澄清与立项.md`:

```markdown
# 创意澄清与立项

- 原始想法：
- 项目模式：想法落地
- 项目根目录：
- 当前结论：待确认 / 可进入 PRD

## 用户问题与目标用户
## 产品假设
## 核心使用路径
## MVP 已确认范围
| SCOPE-ID | 用户结果 | 为什么是 V1 | 验收证据 |
| --- | --- | --- | --- |

## 暂不做与以后再说
## AI 默认建议，待确认
## 风险、限制与开放问题
## 用户确认记录
```
