---
name: personal-website
description: Guide non-technical users through building a personal website. Interview the user to understand their identity and content needs, then generate a complete static site, optionally backed by Feishu Bitable as CMS, and deploy. Use when a user says "帮我建个个人网站", "做个个人主页", "build me a personal website", "create a portfolio site", "搭个主页", or any request to create a personal brand website.
agent_created: true
---

# Personal Website Builder

Guide non-technical users through building a personal website end-to-end: interview, structure design, code generation, and deployment.

## Principles

- Never ask technical questions first. Start with identity and content.
- Default to the simplest option that works. Pure HTML/CSS unless the user explicitly wants a framework.
- The deliverable isn't just a URL — it's a URL plus a clear "how to update" guide.
- When the user struggles to articulate their needs, offer concrete examples and let them pick.

## When NOT to Use This Skill

This skill builds personal portfolio/brand sites. It is NOT suitable for:

- **E-commerce** — shopping carts, payments, order management, inventory systems. Wrong tool.
- **Community / forums** — user registration, commenting systems, real-time chat. Way beyond scope.
- **Real-time collaboration** — Google Docs-style multi-user editing. Static sites can't do this.
- **Complex auth & permissions** — multi-role access control, private member areas. Basic auth at most.
- **High-traffic production apps** — millions of visits, CDN strategy, load balancing. Not the target.

If the user's request falls into any of these, say so directly: "这个我不太适合做，建议用 X 替代。我可以帮你做个人网站，但电商/社区/实时协作这些超出我的能力范围。"

## Workflow

### Phase 1: Identity Interview (3-4 questions)

Ask these questions one at a time. Do not firehose.

**Q1 — Identity:** "先聊聊你是谁——你是做什么的？设计师、工程师、博主、创业者，还是其他？"

Based on the answer, classify into one of the personas in `references/site-structures.md` and note the recommended page structure. Do NOT show the classification to the user yet.

**Q2 — Content goals:** Ask what they want visitors to do after seeing the site. Options: 联系你 / 看你的作品 / 读你的文章 / 了解你的服务 / 关注你的社交媒体. The answer determines the primary CTA and page priority.

**Q3 — Content inventory:** "你现在有哪些可以展示的内容？比如作品图片、写的文章、做过的项目、客户评价……越多越好。"

This determines data volume, which feeds into the CMS decision.

**Q4 — Update frequency:** "你多久会更新一次内容？每天都加新东西、一周一次、还是几个月改一次？"

| Frequency | CMS Recommendation |
|-----------|-------------------|
| Daily / Weekly | Feishu Bitable CMS (dynamic content) |
| Monthly or less | Static (regenerate when needed) |

If "not sure" or unclear, **default to Feishu Bitable CMS** — it's easier to not use the CMS than to retrofit one later.

### Phase 1.5: Structure Confirmation (MANDATORY)

**Do NOT skip this phase.** Before choosing CMS or style, confirm the page structure with the user.

Based on the persona from Q1 and content goals from Q2, propose a navigation + module structure:

1. Map the persona to the recommended structure in `references/site-structures.md`
2. List the proposed sections in order, with Chinese labels
3. Identify the primary CTA placement (hero section, nav button, footer)
4. Ask the user: "基于你的身份和内容，我建议这样排——你确认吗？或者想调整顺序/增删？"

**Default section order convention:**

```
Hero → 项目 → 文章 → 关于 → 联系
```

This order prioritizes what visitors came to see (projects, articles), with personal background (关于) placed later as context for those who scroll deep. Contact is always last as a natural conclusion.

**Exceptions by persona:**
- Designer/Creative: `Hero → 项目 → 关于 → 联系` (no articles by default)
- Writer/Blogger: `Hero → 文章 → 关于 → 联系` (no projects by default)
- Entrepreneur/Service: `Hero → 服务 → 关于 → 联系` (services replace projects)

**Navigation labels:**
Always use Chinese labels: `项目` / `文章` / `关于` / `联系`. Match section IDs: `#projects` / `#articles` / `#about` / `#contact`.

If the user requests different sections or order, update the structure before proceeding.

### Phase 2: CMS Path Selection

Present two paths based on the Q4 answer:

**Path A: 纯静态** — Content is hardcoded in HTML. To update, regenerate the site.
**Path B: 飞书多维表格 CMS** — Content lives in a Feishu table. Update content in Feishu, site refreshes automatically.

Explain the tradeoff:
- Path A is simpler, no Feishu account needed, fewer moving parts. Good for infrequent updates.
- Path B requires a Feishu account and API setup, but lets the user (or their team) update content without touching code — ever.

Ask the user to choose. If they pick Path B, check Feishu readiness: "你有飞书账号吗？需要先在飞书开放平台创建一个应用并开通多维表格权限。现在方便操作吗？"

### Phase 3: Visual Style

Show all six style options as concise Chinese descriptions:

1. **黑白极简** — 不跟风不花哨。黑与白之间的克制，让作品自己说话。适合设计师、工程师。
2. **可爱手绘** — 插画、emoji、圆角、暖色。像"一个可爱的人在做可爱的事"。适合创意行业、自由职业者。
3. **杂志编辑** — 衬线标题、暖纸底色、印刷品质感。让人愿意停留、深度阅读。适合写作者、产品人、咨询师。
4. **终端极客** — 黑底绿字、等宽字体、命令行美学。像一个透明敞亮的个人服务器。适合作品里有代码的人。
5. **赛博霓虹** — 深黑底色、青/紫/品红霓虹发光、科技标签云。像黑客搭建的终端站，酷而不刺眼。适合技术创作者。
6. **旅程叙事** — 大地色系、时间线布局、叙事引导。不是冷冰冰的项目列表，是一条走过的路。适合想讲故事的创作者。

Ask: "这六种风格你喜欢哪个方向？也可以组合描述，比如'黑白极简但带一点旅程叙事的时间线'之类的"

### Phase 4: Tech Stack

Default to pure HTML/CSS/JS (single-file or minimal files). No framework, no build step, no npm.

Only offer React or Vue if the user explicitly mentions wanting a framework or is clearly a developer.

### Phase 5: Generate (Template-First)

**Do NOT generate HTML from scratch.** Use the template for the chosen style:

| Style chosen | Template file |
|-------------|--------------|
| 1. 黑白极简 | `assets/template-monochrome.html` |
| 2. 可爱手绘 | `assets/template-playful.html` |
| 3. 杂志编辑 | `assets/template-editorial.html` |
| 4. 终端极客 | `assets/template-terminal.html` |
| 5. 赛博霓虹 | `assets/template-cyberpunk.html` |
| 6. 旅程叙事 | `assets/template-journey.html` |

**Step 5.0 — Pre-flight check (MANDATORY):**
1. **Read the full template file** — at minimum the `<style>` block and the content placeholder markers
2. **Confirm every CSS class** you plan to use in content blocks exists in the template's `<style>` block
3. **Confirm every placeholder marker** (`<!-- HERO_HERE -->`, `<!-- PROJECTS_HERE -->`, etc.) exists in the template
4. If a needed class is missing, do NOT invent one — adapt your content to use existing classes

**Step 5.1 — Fill content into the template:**

- Copy the template to `dist/index.html`
- Replace each placeholder marker with the actual HTML content:

| Placeholder | Content to fill |
|-------------|----------------|
| `<!-- HERO_HERE -->` | Full hero section: name, tagline, intro text, CTA links, avatar image |
| `<!-- ABOUT_HERE -->` | About content block (text paragraphs + skills/aside column) |
| `<!-- PROJECTS_HERE -->` / `<!-- WORKS_HERE -->` | Project cards grid (image + title + tag + description for each) |
| `<!-- ARTICLES_HERE -->` | Article list (date + title + summary for each, with thumbnails if present) |
| `<!-- CONTACT_HERE -->` | Contact section (see Contact section guidance below) |
| `{{SITE_TITLE}}` | Browser tab title |
| `{{SITE_DESC}}` | Meta description (120-160 chars) |
| `{{FOOTER_TEXT}}` | Footer copyright line |
| `{{DEMO_DATA}}` | JavaScript object with `projects` and `articles` arrays for fallback rendering |

**Template-specific placeholders:**
- Terminal style: additional `<!-- SKILLS_HERE -->` placeholder for skill tags
- Journey style: additional `<!-- NARRATIVE_HERE -->` placeholder for the narrative intro paragraph

**Contact section guidance:**

Default approach: **card grid + QR code modal** (three cards: 微信公众号 / 小红书 / 飞书知识库). Use `.contact-grid` + `.contact-card` classes. Each card has:
- Platform icon (emoji)
- Platform name
- Hint text ("扫码关注")

Clicking a card opens a modal (`.qr-overlay` + `.qr-modal`) showing:
- Platform title + subtitle
- QR code image placeholder (swap when user provides real QR images)
- Descriptive label

The modal supports: click-to-close, X button close, Escape key close.

If the user has NO Chinese social platforms, fall back to a simple `.contact-links` approach with email and other links.

- Replace `{{SITE_TITLE}}`, `{{SITE_DESC}}`, `{{FOOTER_TEXT}}`, `{{DEMO_DATA}}` with actual values
- Template's CSS is the authoritative design source — do NOT add custom inline styles
- Template's responsive breakpoints are pre-tested — do NOT modify them

**Step 5.2 — Static path (Path A):**
- All content hardcoded in the HTML
- Fill `{{DEMO_DATA}}` with the user's actual projects & articles as demo data
- The CTA from Q2 should be prominent
- Output as a single `index.html`

**Step 5.3 — Bitable CMS path (Path B):**
- Fill `{{DEMO_DATA}}` with sample data for fallback display
- Also create a Feishu Bitable with the appropriate fields matching the content inventory from Q3
- Wire the API: the template's JS demo block serves as a reference for field names and rendering
- Include a `setup.md` that explains how to configure app_id, app_secret, base_id, table_id
- Modify the JS to fetch from Bitable API, with the demo block as fallback when API is unreachable

**Design rules (built into templates — do NOT override):**
- Mobile-first responsive design
- Fast loading (no heavy libraries, no framework)
- Clean typography
- Accessible (alt text, semantic HTML, sufficient contrast)
- Must work as a single static deploy (no server-side rendering)

### Phase 5.4: Self-Check (MANDATORY)

Before deploying, run through `references/checklist.md`. Focus on P0 items:

- Meta tags complete (title, description, charset, viewport)
- No horizontal scroll on mobile (test mentally at 375px)
- Images have `max-width: 100%`
- CTA visible above fold on mobile
- No broken internal anchor links
- If site is in Chinese, no stray English labels

Do NOT skip this. Fix P0 issues before proceeding to deploy.

### Phase 6: Deploy

Deploy using the cloudstudio-deploy skill:

1. Create a deployment directory (e.g., `dist/` or `build/`)
2. Place all site files there
3. Deploy via CloudStudio
4. Provide the URL to the user

### Phase 7: Handoff Guide

Generate a concise `HOW_TO_UPDATE.md` file and deliver it alongside the site URL.

**For Path A (Static):**
- Explain that to update, they should come back and describe what to change
- List what content is where (e.g., "about section is in the `<section id='about'>` block")

**For Path B (Feishu CMS):**
- How to open the Feishu Bitable
- Which columns map to which parts of the website
- How to add/edit/delete records
- How the "状态" or "published" field controls visibility on the site
- That changes appear on the site within seconds (API reads on page load)

### Phase 8: Summary

After deployment, present a summary:

- Live URL
- CMS path chosen (if Bitable: table name and key fields)
- How to update content (brief)
- One thing they should do next (e.g., "换掉那张示例头像", "填上真实的联系方式")
