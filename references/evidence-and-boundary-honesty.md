# Evidence And Boundary Honesty

Use this whenever an AI may be tempted to sound certain about feasibility, market value, quote, delivery date, model/tool capability, security, data, cost, performance, deployment, or an external outcome. Honest boundaries are a project safety feature, not a lack of ability.

## Claim Labels

Every material conclusion must use one label:

| Label | Meaning | Required Evidence/Action |
| --- | --- | --- |
| 已验证可做 | A working path is proven in the relevant environment | cite files/commands/tests/URL/provider setting and its operating boundary |
| 可做但需验证 | Plausible but material assumptions remain | name assumptions, owner/dependency, cheapest validation, success/failure threshold |
| 当前不可承诺 | The available evidence cannot justify a promise | say exactly what is unknown/missing and do not quote/schedule/claim success as if known |
| 明确不可做 | Conflicts with known constraints or depends on an unavailable/uncontrollable condition | explain the constraint plainly; propose a lawful/safe/scoped alternative only if one exists |

Do not substitute optimistic language such as “应该可以”, “大概率”, “AI 能搞定”, or “上线就行” for one of these labels.

## What Is Not Evidence

- a model's confidence, a generic tutorial, a marketing page, an uncited market-size statement, or a code snippet that has not run in the project
- a clean local demo when production access/data/security/scale is untested
- a competitor's existence as proof that this project will acquire users or make money
- a client desire as proof that a third-party API, platform, app store, model, regulator, or payment provider will approve/behave as requested
- a technical possibility as proof that it fits the approved budget, date, legal obligations, maintenance capacity, or user value

## Required Boundary Statement

Before committing a material result, state:

1. **What is proven:** exact evidence and where it can be checked.
2. **What is only assumed:** unverified condition or estimate.
3. **Who/what controls it:** project owner, client, provider, platform, user data, legal reviewer, or other external dependency.
4. **What cannot be promised:** result outside the project's control.
5. **Smallest validation:** action, cost/time cap, expected pass/fail result, and stop condition.

## Stop Rules

Pause or explicitly refuse the commitment when:

- needed access, API, data, account, hardware, budget, decision-maker, or permission is not available;
- the request requires bypassing security, terms, law, privacy, safety, or another party's control;
- a delivery/quote/market claim would be based only on assumption;
- the accepted scope, risk gate, or feasibility decision does not support the request;
- the user asks for a guarantee that depends on model behavior, user behavior, third-party availability, market response, or platform approval.

## Output Format

Use this concise block in relevant documents and responses:

```markdown
### 能力边界判断
- 结论：已验证可做 / 可做但需验证 / 当前不可承诺 / 明确不可做
- 已有证据：
- 未验证假设：
- 外部依赖/责任方：
- 不能承诺的结果：
- 最小验证与停止条件：
```

For client work, link this block to the quote, delivery boundary, risk register, and change record. For own-product work, link it to the feasibility decision and PRD. For code work, link it to the relevant `CODE-CHG-*` and test evidence.
