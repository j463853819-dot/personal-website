---
name: personal-website
description: Guide non-technical users through building a personal website. Interview the user to understand their identity and content needs, generate a complete static site from one of several curated templates, and optionally add a safe CMS or deployment path. Use when a user says "帮我建个个人网站", "做个个人主页", "build me a personal website", "create a portfolio site", "搭个主页", or any request to create a personal brand website.
---

# Personal Website Builder

Guide non-technical users through building a personal website end-to-end: interview, structure design, code generation, and deployment.

## Principles

- Never ask technical questions first. Start with identity and content.
- Default to the simplest option that works. Pure HTML/CSS unless the user explicitly wants a framework.
- Default to a static site. CMS and hosted deployment are optional enhancements, not prerequisites.
- The deliverable isn't just a page — it's a working site plus a clear "how to update" guide.
- When the user struggles to articulate their needs, offer concrete examples and let them pick.
- For the first version, keep one coherent template style instead of mixing palettes, fonts, and layouts. Users can ask for later iterations after the first version is working.

## When NOT to Use This Workflow

This workflow builds personal portfolio/brand sites. It is NOT suitable for:

- **E-commerce** — shopping carts, payments, order management, inventory systems. Wrong tool.
- **Community / forums** — user registration, commenting systems, real-time chat. Way beyond scope.
- **Real-time collaboration** — Google Docs-style multi-user editing. Static sites can't do this.
- **Complex auth & permissions** — multi-role access control, private member areas. Basic auth at most.
- **High-traffic production apps** — millions of visits, CDN strategy, load balancing. Not the target.

If the user's request falls into any of these, say so directly: "这个我不太适合做，建议用 X 替代。我可以帮你做个人网站，但电商/社区/实时协作这些超出我的能力范围。"

## Workflow

### Phase 0: Triage and Fit

First decide whether this workflow is the right fit.

Good fits:
- Personal homepage / internet business card
- Portfolio / works showcase
- Developer profile
- Writer or creator homepage
- Consultant / freelancer service page
- Lightweight personal brand site

Poor fits are listed in "When NOT to Use This Workflow". If the request is out of scope, explain the boundary and offer a simpler personal-site version if useful.

### Phase 1: Intake Interview

Read `references/intake.md` before asking questions.

Ask questions one at a time. Do not firehose. Start with the six core questions:

1. Who are you?
2. Who is the site for?
3. What should visitors do after viewing it?
4. What content and assets do you already have?
5. How often will you update it?
6. Which visual direction do you prefer?

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
| Not sure | Static first, with CMS noted as a later upgrade |

If "not sure" or unclear, **default to Static**. Non-technical users should get a working first version with zero account setup. Mention that CMS can be added later if frequent updates become real.

If the user already provides enough information, infer reasonable defaults and continue. Do not block on perfect answers.

### Phase 1.2: Decision Mapping

Read `references/decision-rules.md`.

Map the user's answers to:

- Site type: business card, portfolio, developer profile, writer homepage, service page, narrative profile, or mixed general site
- Recommended structure
- Recommended template style
- Update path: static first or optional CMS
- Deployment suggestion

If the mapping is ambiguous, propose one recommended path and one alternative. Keep the recommendation concrete.

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
- Path A is simpler, no Feishu account needed, no secrets, fewer moving parts. Best default for a first version.
- Path B is for frequent updates and requires Feishu account setup, an app or integration, permissions, and a safe API access layer.

Ask the user to choose. If they pick Path B, check Feishu readiness: "你有飞书账号吗？需要先在飞书开放平台创建一个应用并开通多维表格权限。现在方便操作吗？"

**CMS safety rule:** Never put Feishu `app_secret`, access tokens, or other private credentials into browser-side HTML/JS. If using Feishu Bitable as CMS, use a serverless function, backend proxy, prebuild script, or another safe read layer. If no safe layer is available, deliver the static version and a CMS setup guide instead.

### Phase 2.5: Asset Plan

Read `references/assets.md`.

Inventory the user's materials:

- Avatar or profile photo
- Project images or screenshots
- Article covers
- Logos or client marks
- Contact links
- QR codes, only if the user provides them

If assets are missing, use the chosen template's no-image layout or tasteful placeholders. Do not invent real photos, logos, client marks, or QR codes.

### Phase 3: Visual Style

Show all six style options as concise Chinese descriptions:

1. **黑白极简** — 不跟风不花哨。黑与白之间的克制，让作品自己说话。适合设计师、工程师。
2. **可爱手绘** — 插画、emoji、圆角、暖色。像"一个可爱的人在做可爱的事"。适合创意行业、自由职业者。
3. **杂志编辑** — 衬线标题、暖纸底色、印刷品质感。让人愿意停留、深度阅读。适合写作者、产品人、咨询师。
4. **终端极客** — 黑底绿字、等宽字体、命令行美学。像一个透明敞亮的个人服务器。适合作品里有代码的人。
5. **赛博霓虹** — 深黑底色、青/紫/品红霓虹发光、科技标签云。像黑客搭建的终端站，酷而不刺眼。适合技术创作者。
6. **旅程叙事** — 大地色系、时间线布局、叙事引导。不是冷冰冰的项目列表，是一条走过的路。适合想讲故事的创作者。

Ask: "这六种风格你喜欢哪个方向？第一版建议先选一种完整风格，保证能快速做出稳定版本。上线后你还可以继续让我调配色、换细节。"

If the user asks to mix styles before the first version exists, choose the closest single template and say: "我先用这个方向出第一版，保证页面完整可用。第一版出来后，我们再微调配色和细节。"

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
| `<!-- CONTACT_HERE -->` | Optional extra contact content when the template exposes this marker |
| `{{SITE_TITLE}}` | Browser tab title |
| `{{SITE_DESC}}` | Meta description (120-160 chars) |
| `{{FOOTER_TEXT}}` | Footer copyright line |
| `{{DEMO_DATA}}` | JavaScript object with `projects` and `articles` arrays for fallback rendering |

**Template-specific placeholders:**
- Terminal style: additional `<!-- SKILLS_HERE -->` placeholder for skill tags
- Journey style: additional `<!-- NARRATIVE_HERE -->` placeholder for the narrative intro paragraph
- Some templates include a built-in contact card grid after `<!-- CONTACT_HERE -->`. In that case, fill only the marker with a short intro or leave it empty, then replace the built-in card labels/data with the user's real contact channels.
- Terminal style uses `#writing` for the article section instead of `#articles`; keep internal navigation consistent with the chosen template.

**Contact section guidance:**

Default approach: **contact card grid** using the channels the user actually provides. Common options:
- Email
- GitHub
- X / Twitter
- LinkedIn
- 微信 / 微信公众号
- 小红书
- 飞书知识库
- Newsletter

Use `.contact-grid` + `.contact-card` classes when the template provides them. Each card has:
- Platform icon (emoji)
- Platform name
- Hint text ("发邮件", "查看 GitHub", "扫码关注", "阅读文章", etc.)

If the contact channel has a QR code, clicking a card can open a modal (`.qr-overlay` + `.qr-modal`) showing:
- Platform title + subtitle
- QR code image placeholder (swap when user provides real QR images)
- Descriptive label

The modal supports: click-to-close, X button close, Escape key close.

If the user has no QR-based channels, use normal links and do not show QR modal behavior.

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
- Do NOT expose Feishu credentials in frontend code
- If a safe serverless/backend/proxy layer is available, wire the frontend to that public read endpoint
- If no safe layer is available, keep the generated site static and include a `setup.md` describing how to add CMS later
- Include a `setup.md` that explains required values such as app_id, app_secret, base_id, table_id, and where those values must be stored safely
- Keep the demo block as fallback when the CMS endpoint is unreachable

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
- No leftover placeholders such as `your-name@example.com`, `github.com/your-name`, `{{SITE_TITLE}}`, or `{{DEMO_DATA}}`

Do NOT skip this. Fix P0 issues before proceeding to deploy.

### Phase 6: Deploy

Deployment is optional. Always make sure the site works locally first.

1. Create a deployment directory (e.g., `dist/` or `build/`)
2. Place all site files there
3. If a deployment tool is available, deploy to the user's preferred target: CloudStudio, GitHub Pages, Vercel, Netlify, or another static host
4. If no deployment tool is available, provide the local `dist/index.html` path and simple hosting guidance
5. Provide the URL when deployment succeeds

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
- How the safe CMS read layer works
- How quickly changes appear on the site, depending on the chosen integration

### Phase 8: Summary

After deployment, present a summary:

- Live URL
- Local output path
- CMS path chosen (if Bitable: table name and key fields)
- How to update content (brief)
- One thing they should do next (e.g., "换掉那张示例头像", "填上真实的联系方式")
