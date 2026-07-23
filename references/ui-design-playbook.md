# UI Design Playbook

Use this reference before planning or implementing any visible interface.

## Goal

The UI must look intentional, not like a default template. It should match the product category, user mood, and usage context.

## Required Style Decisions

Document these before UI implementation:

- Product personality: what should the product feel like?
- Audience: who will use it and how often?
- Visual keywords: 3-6 words such as calm, precise, premium, playful, editorial.
- Anti-keywords: what it must not feel like, e.g. generic SaaS, childish, dark-only, cluttered.
- Palette: primary, secondary, background, surface, border, success, warning, danger.
- Typography: heading/body sizes, density, font feeling.
- Layout: navigation, page width, spacing rhythm, grid, information density.
- Components: buttons, inputs, tables, cards, tabs, modals, empty states.
- Assets: icons, product images, illustrations, screenshots, generated images if needed.
- Motion: none, subtle, expressive, or game-like.
- Responsive behavior: what changes on mobile.
- Task hierarchy: the primary user task, primary action, result area, and next safe action on each key screen.
- Product-specific content: the real labels, realistic data shape, assets, and information hierarchy that make this product recognizable.
- Control inventory: every meaningful button, link, input, menu, toggle, upload, and destructive action must be documented in `06-交互控件规格.md` before implementation.

## Style Routes

Pick one clear route instead of mixing everything.

| Route | Use For | Visual Feel |
| --- | --- | --- |
| Quiet Utility | admin, CRM, workflow, internal tools | dense, calm, scan-friendly |
| Premium Minimal | paid SaaS, portfolio, boutique product | refined spacing, restrained color |
| Editorial Creator | content tools, writing, media, personal brands | expressive type, strong imagery |
| Playful Consumer | habit apps, social, casual tools | friendly color, soft interactions |
| Technical Console | dev tools, AI ops, dashboards | precise, high contrast, status-rich |
| Immersive Product | landing pages, games, visual products | strong first viewport, media-led |

## Quality Checklist

Before accepting UI:

- The first screen clearly tells what product this is.
- The first screen exposes the main user task instead of only decorative marketing or a generic dashboard shell.
- It has a recognizable style direction.
- It does not look like a random starter template.
- It uses product-specific content, hierarchy, and assets rather than lorem ipsum, fake charts, or dead controls.
- Text fits containers on desktop and mobile.
- Buttons and controls use familiar patterns.
- Important states exist: loading, empty, error, success.
- Mobile layout is usable.
- Colors have roles and enough contrast.
- Keyboard focus, readable text size, and non-color status cues work for important actions.
- Spacing and alignment are consistent.
- Screenshots or preview URL are provided as evidence.
- A real critical path is verified on desktop and mobile: enter -> act -> receive result -> recover or continue.
- Every meaningful control has intentional default, hover/focus, pressed, disabled, loading, success, and error behavior where applicable.

## Product-To-UI Translation

For each key screen, document:

| Screen | User task | Primary action | Result/feedback | Empty/error/recovery | Design intention |
| --- | --- | --- | --- | --- | --- |

Do not start with a gallery of components. Start with the user's task and information hierarchy, then use components to support it.

## Prompt Snippet

```text
请先定义 UI 风格路线，再设计页面。
不要直接套通用模板。
请说明：视觉关键词、颜色角色、布局节奏、组件风格、移动端策略。
完成后保存到指定路径，并提供截图或预览地址作为验收证据。
```
