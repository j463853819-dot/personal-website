# Site Structures by Persona

Map the user's identity to a recommended page structure. Use this as a starting point, then customize based on their specific content inventory.

## Persona → Structure

### Designer / Creative

Pages: 首页, 项目, 关于, 联系

| Page | Purpose | Key Elements |
|------|---------|-------------|
| Home | Hero section with best 3 works, immediate visual impact | Large hero image, 3-4 featured works with images, brief tagline |
| 项目 | Full portfolio grid | Image grid, project titles, categories/tags, click to view detail |
| About | Personal story and services | Photo, bio (2-3 paragraphs), services offered, client logos if any |
| Contact | Get in touch | Contact form or email link, social links, location if relevant |

Primary CTA: View works or contact for hire.

### Developer / Engineer

Pages: 首页, 项目, 文章 (可选), 关于

| Page | Purpose | Key Elements |
|------|---------|-------------|
| Home | Who you are and what you build | Brief intro, 3-4 featured projects, tech stack tags, GitHub link |
| Projects | Technical portfolio | Project cards with description, tech stack, links (demo + repo) |
| 文章 | Technical writing (optional) | Article list with dates and tags |
| About | Background and interests | Bio, experience timeline, skills, interests outside code |

Primary CTA: View projects or GitHub.

### Writer / Blogger / Content Creator

Pages: 首页, 文章列表, 关于

| Page | Purpose | Key Elements |
|------|---------|-------------|
| Home | Latest posts, subscribe | Hero with latest 3-5 posts, newsletter signup, categories |
| 文章列表 | All posts, searchable | Post list with dates, tags, search or filter |
| About | Who you are as a writer | Photo, bio, topics you cover, where else to find your work |

Primary CTA: Read latest post or subscribe.

### Entrepreneur / Service Provider

Pages: 首页, 服务, 关于, 联系

| Page | Purpose | Key Elements |
|------|---------|-------------|
| Home | Value proposition, trust building | Hero with value prop, service overview, testimonials, client logos |
| Services | What you offer | Service cards with descriptions and pricing (optional) |
| About | Your story and credibility | Founder story, team (if any), credentials, mission |
| Contact | Convert interest to lead | Contact form, calendar booking link, WeChat QR code |

Primary CTA: Book a call or get in touch.

### General / Multi-hyphenate

Pages: 首页, 关于, 联系

| Page | Purpose | Key Elements |
|------|---------|-------------|
| Home | Everything in one place | Bio snippet, link sections (projects, writing, speaking, etc.), social links |
| About | Full story | Extended bio, timeline, interests, what you're currently working on |
| Contact | Connect | Email, social links, newsletter signup |

Primary CTA: Follow or connect.

## Navigation Conventions

- Max 4-5 nav items. Use dropdowns only if absolutely necessary.
- Nav order: Home | [Primary content page] | About | [Contact or CTA]
- CTA button in nav: e.g., "联系我", "看作品", "订阅"
- Footer: copyright, social links, back to top

## Content Types & Data Modeling

For Feishu Bitable CMS, map content types to table fields:

### Works / Projects table
| Field | Type | Notes |
|-------|------|-------|
| 标题 | 文本 | Project name |
| 描述 | 多行文本 | 1-2 sentence description |
| 封面图 | 附件 | Hero image |
| 分类 | 单选 | e.g., UI Design, Branding, Web Dev |
| 链接 | URL | Live demo or case study |
| 排序 | 数字 | For custom ordering |
| 状态 | 单选 | 草稿 / 已发布 |

### Articles / Blog posts table
| Field | Type | Notes |
|-------|------|-------|
| 标题 | 文本 | Post title |
| 摘要 | 多行文本 | Excerpt for cards |
| 封面图 | 附件 | Card image |
| 标签 | 多选 | Topic tags |
| 发布日期 | 日期 | For sorting |
| 原文链接 | URL | Link to full post (e.g., WeChat article) |
| 状态 | 单选 | 草稿 / 已发布 |

## JS Demo Data → Template Field Mapping

When filling `{{DEMO_DATA}}` or wiring Feishu API, use these field names in the JavaScript object. The template's JS rendering loop expects these exact keys:

### Projects object (used in `.project-grid` rendering)
```js
{ title: "项目名称", tag: "分类标签", desc: "项目描述", image: "图片URL" }
```
Template renders: `p.title` → `.project-card .title`, `p.tag` → `.project-card .tag`, `p.desc` → `.project-card .desc`, `p.image` → `<img src>`

### Articles object (used in `.article-list` or `.article-card` rendering)
```js
{ date: "2026 · 05 · 29", title: "文章标题", summary: "摘要", image: "缩略图URL" }
```
Template renders: `a.date` → `.article-card .date`, `a.title` → `.article-card .title`, `a.summary` → `.article-card .desc`, `a.image` → `<img src>`

**Bitable CMS mapping:** When configuring the Feishu Bitable API, map the table column names to these JS keys — the API response must be transformed to match these field names before feeding into the template's render loop.
