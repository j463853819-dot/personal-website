# Decision Rules

Use these rules to map user intent to site structure, template style, update path, and deployment suggestion.

## Site Type Mapping

| User Says / Implies | Site Type | Recommended Structure | Primary CTA |
| --- | --- | --- | --- |
| "我想找工作", "展示项目", "作品集" | Portfolio | Hero → 项目 → 关于 → 联系 | 看项目 |
| "我是工程师", "我有 GitHub", "技术博客" | Developer Profile | Hero → 项目 → 文章 → 关于 → 联系 | 看 GitHub / 看项目 |
| "我写文章", "公众号", "博客", "内容创作者" | Writer Homepage | Hero → 文章 → 关于 → 联系 | 读文章 / 订阅 |
| "我接咨询", "自由职业", "服务客户" | Service Page | Hero → 服务 → 案例/项目 → 关于 → 联系 | 联系我 / 预约沟通 |
| "我想有个个人主页", "互联网名片" | Personal Card | Hero → 关于 → 链接 → 联系 | 联系我 / 关注 |
| "我想讲经历", "个人成长", "转型故事" | Narrative Profile | Hero → 旅程 → 项目/文章 → 关于 → 联系 | 了解经历 / 联系 |
| Mixed identity, unclear goal | General Site | Hero → 项目 → 文章 → 关于 → 联系 | 联系我 |

## Template Recommendation

| User Profile | Best Template | Alternative |
| --- | --- | --- |
| Designer / visual creator | 黑白极简 | 杂志编辑 |
| Illustrator / friendly creator | 可爱手绘 | 旅程叙事 |
| Writer / product thinker / consultant | 杂志编辑 | 旅程叙事 |
| Developer / engineer | 终端极客 | 黑白极简 |
| AI builder / creative technologist | 赛博霓虹 | 终端极客 |
| Career transition / personal story | 旅程叙事 | 杂志编辑 |
| Unsure, wants professional | 黑白极简 | 杂志编辑 |

## Update Path

| Update Need | Recommendation |
| --- | --- |
| No idea yet | Static first |
| Basic profile, rarely changes | Static |
| Adds projects monthly | Static, regenerate when needed |
| Publishes weekly articles | Static first; CMS optional |
| Publishes daily or has a team updating content | CMS candidate |
| Needs private drafts and review workflow | CMS candidate with safe backend |

Never choose CMS just because the user is unsure. CMS is useful only when update frequency is real.

## Deployment Suggestion

| User Need | Suggested Target |
| --- | --- |
| Wants a local preview only | `dist/index.html` |
| Wants simplest public hosting | GitHub Pages |
| Already uses GitHub | GitHub Pages |
| Wants custom domain and simple deploy | Vercel or Netlify |
| Uses a platform with built-in deployment tools | Use that platform |
| No deployment tool available | Deliver local files and hosting guide |

## Recommendation Format

When proposing a path, be decisive:

```text
我建议先做：
- 类型：开发者个人主页
- 结构：Hero → 项目 → 文章 → 关于 → 联系
- 风格：终端极客
- 更新方式：纯静态
- 部署：先本地交付，确认后可上 GitHub Pages
```

Offer one alternative only when it genuinely helps:

```text
如果你想更像独立杂志，而不是极客终端，也可以选「杂志编辑」。
```

## Conflict Resolution

- User wants "very creative" but has no images: choose typography-heavy styles such as terminal, editorial, or monochrome.
- User wants "professional" and "cute": choose one as first version; recommend playful only if warmth matters more than corporate trust.
- User wants lots of sections: keep nav to 4-5 items and group content.
- User wants custom colors before first version: choose closest template and defer color tuning to iteration.
- User wants CMS but has no safe backend path: deliver static version plus CMS setup guide.
