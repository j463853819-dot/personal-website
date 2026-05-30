# Design Templates

Six visual styles for personal websites, each anchored to real-world references. Apply the chosen style to all generated pages.

## Hard Constraints (ALL styles)

These rules protect aesthetic consistency. Do NOT override them, even if the user asks.

### Color — Presets Only

Each style defines a **fixed color palette**. You may NOT:
- Accept a user's custom hex value (e.g. "用 #FF5733 做主题色")
- Mix colors across styles (e.g. take the accent from Style 5 but use it on a Style 1 page)
- Add new colors not in the style's property table

If the user wants a different color feel, suggest a different style or a natural-language tweak within the style's palette (e.g. "杂志风但暖色再淡一点" → pick the lighter warm white from the editorial palette range).

### Typography — Font Family is Non-Negotiable

Each style specifies exact font families. Do NOT swap them. If the user says "换个字体", ask which style's typography they prefer and switch the whole style — do not patch a single font into another style's system.

### Template is Authoritative

The `assets/template-*.html` file is the single source of truth for CSS, breakpoints, and layout. When filling content:
- Use only CSS classes defined in the template's `<style>` block
- Do NOT add inline styles or new `<style>` blocks
- Do NOT modify responsive breakpoints

If a layout need isn't covered by the template, adapt the content to fit existing structures rather than extending the template.

---

## Style 1: 黑白极简 (Monochrome Minimal)

Reference: 林一 · 独立设计师 & 产品创作者

**Design philosophy:** 不跟风，不花哨。黑与白之间的克制，让作品自己说话。

| Property | Value |
|----------|-------|
| Background | #FFFFFF |
| Primary text | #111111 |
| Secondary text | #888888 |
| Accent | 无独立 accent —— 仅用黑色 (#000) 做极少数强调（如链接下划线、分隔线），更多靠粗细对比和控制留白来建立层级 |
| Heading font | 无衬线，加粗。建议 `system-ui, -apple-system, sans-serif`，权重 700-800 |
| Body font | 同上，权重 400 |
| Max content width | 720px，居中（读起来像一篇排版考究的文章） |
| Section spacing | 120-160px，大量留白 |
| Hero layout | **左文右图**。左边大标题 + 一句简介 + 链接按钮；右边一张方形肖像，灰度处理 |
| Cards | 项目卡片用大图为视觉重心，标题 + 一行描述在下方，无边框无阴影，仅靠间距区分 |
| 文章列表 | 左侧缩略图 + 右侧标题/日期，极简分隔线 |
| Navigation | 顶部纯文字导航，右对齐，无底色，无阴影 |
| Images | 大面积、高画质，黑白或低饱和处理 |
| Overall feel | 不讨好任何人，不解释太多。像一个认真对待作品的人放在互联网角落的一盏灯。 |

Key rules:
- 绝不用渐变色、不用 box-shadow、不搞圆角卡片
- 排版靠对比：粗体标题 vs 细体正文，大号数字 vs 小字标注
- 图片是唯一的视觉调味剂——如果没有好照片，宁可不上图片，用大字排版撑场面

---

## Style 2: 可爱手绘 (Playful/Illustrated)

Reference: 小满的设计屋

**Design philosophy:** 治愈感。用插画和颜色传递温暖，让人一打开就想往下翻。

| Property | Value |
|----------|-------|
| Background | 暖奶油色 #FFFBF0，或淡米粉 #FFF5F0 |
| Primary text | #3D3226 (暖棕色，不是冷黑) |
| Secondary text | #8B7E74 |
| Accent colors | 柔和调：鹅黄 #F9D56E、嫩绿 #A8D8A8、淡橙 #F5A97F、天蓝 #A0C4E8。每种只用 1-2 次 |
| Heading font | 圆体 / 卡通体，如 `"Noto Sans SC"` 中等粗细，或手动引入 Google Fonts 的圆体 |
| Body font | 圆体或无衬线，权重 400，行距 1.8 |
| Max content width | 800px，居中 |
| Section spacing | 80-100px，用插画或分隔线装饰 section 分界 |
| Hero layout | **上图下文 / 环绕式**。顶部或左侧是一张卡通头像/插画，旁边是大标题 + emoji 点缀 |
| Cards | 大圆角 16-20px，浅色背景或淡奶油底色，hover 时轻微放大 (scale: 1.02)，有柔软的 box-shadow |
| Icon language | **大量使用 emoji** 作为段落标记和功能入口图标（📮 ✏️ ⚡ 📌 🌸 💌） |
| Decorative elements | CSS 绘制或 emoji 组成的点缀：星形、云朵、小植物、小动物，分布在 section 边角 |
| Navigation | 简洁居中导航，logo 位可放 emoji 或头像 |
| Images | 圆角 12-16px，项目卡片用彩色缩略图 |
| Overall feel | 不是设计师网站，是"一个可爱的人在做可爱的事"。 |

Key rules:
- 颜色控制在 4 种以内，整体保持温暖柔和
- 每个 section 必须至少有一个视觉装饰：emoji、插画、或装饰线
- 圆角多用 12-20px，避免尖锐直角
- CTA 用实心圆角按钮，颜色取自 accent 调色板

---

## Style 3: 杂志编辑 (Editorial/Magazine)

Reference: LinZhiyu

**Design philosophy:** 深度感。像翻一本设计精良的独立杂志，让人愿意停留、阅读、收藏。

| Property | Value |
|----------|-------|
| Background | 暖白 / 米黄 #FAF7F2 或 #F5F0E8（印刷纸质感） |
| Primary text | #1C1C1C |
| Secondary text | #6B6B6B |
| Accent color | 不设固定 accent，靠字体对比和留白建立层级。可选暗红 #C44D4D 或墨绿 #2D5A3D 做极少量强调（链接、标签） |
| Heading font | **衬线体**。中文用 `"Noto Serif SC"` 或 `"Source Han Serif SC"`（Google Fonts CDN），英文用 `"Playfair Display"`。标题权重大（700+），正文用无衬线 |
| Body font | 无衬线 `system-ui`，权重 400，行距 1.8 |
| Max content width | 860px，居中 |
| Section spacing | 100-140px |
| Hero layout | **左文右图**。大号衬线标题占左半（可跨 2-3 行断句），右半是人物照片，灰度处理。标题下方一小段英文或拼音作为装饰 |
| Cards | 网格布局，每卡带一张全宽图（2:3 或 16:9），图下是标题 + 日期 + 标签。卡片无边框，hover 时图片微暗 |
| 文章列表 | 大图缩略图 + 日期 + 标签行 + 标题，紧凑排版 |
| Tool/Resource section | 图标网格（6-8 个工具），每个工具一个图标 + 名称 |
| Navigation | 顶部简洁导航，右对齐文字链接，可选暗色模式切换 |
| Footer | 一句话签名或 CTA（如"一起合作？"），配插画装饰（植物、几何线条） |
| Overall feel | 你打开了某个独立设计师的 Notion 页面，安静、有品位、信息密度刚好。 |

Key rules:
- 衬线标题是灵魂——字号要大（48-72px），字间距适当放宽
- 背景色必须带暖调（纯白太冷），模仿纸张质感
- 照片灰度或低饱和处理，统一色调
- 页面节奏感：大标题 block → 图片 grid → 文字列表 → 图标 grid，交替出现避免视觉疲劳

---

## Style 4: 终端极客 (Terminal Hacker)

Reference: LIN · 命令行个人页

**Design philosophy:** 互联网最原始的美学——黑底绿字，一切靠文字。极客不需要花哨，一个终端界面就是你全部的自白。

| Property | Value |
|----------|-------|
| Background | 纯黑 #0A0A0A 或深墨绿 #0D1117 |
| Primary text | 终端绿 #00FF41 或琥珀色 #FFB000 |
| Secondary text | 暗绿 #1A7A2E 或暗灰 #555555 |
| Accent | 亮白 #FFFFFF 用于高亮（如光标位置、选中态），仅极少量出现 |
| Heading font | 等宽字体 `"JetBrains Mono", "Fira Code", "Courier New", monospace`，权重 400-700 |
| Body font | 同上，权重 400，行距 1.6 |
| Max content width | 680px，左对齐（不是居中）——模拟终端窗口 |
| Section spacing | 60-80px，用分隔线 `---` 或空行区分 section |
| Hero layout | **命令行自我介绍**。顶部一行 `$ whoami` 命令，下面是系统信息风格的简介（Name / Role / Location / Status 逐行列出）。可加一个逼真的闪烁光标 ▋ |
| Cards | 不是卡片。用 `ls` 或目录结构风格展示项目：`├── project-name / 年份 / 一行描述` |
| 文章列表 | 文件列表风格：`[2026-05-29] AI时代，用飞书多维表格做你的后端.md` 每条一行 |
| Terminal prompt | 每个 section 以模拟命令开头（如 `$ cat projects.txt`、`$ ls articles/`），命令本身是灰色半透明 |
| Navigation | 顶部模拟 shell 提示符 `$ cd /about` `$ cd /works` `$ cd /contact`，点击即跳转 |
| Decorative elements | ASCII art logo（可选）、进度条风格的技能展示、命令行 tab 补全风格的小动效 |
| Images | 原则上不用图片。如果有，用 ASCII art 替代或用字符画边框包裹 |
| Animations | 打字机逐字输出效果（页面加载时）、光标持续闪烁、hover 时文字高亮变亮 |
| Overall feel | 你闯进了一个程序员的个人服务器。没有视觉负担，全是内容。 |

Key rules:
- 非等宽字体是死罪——全站必须统一用等宽字体
- 所有颜色取自终端配色方案（黑底 + 绿字/琥珀字 + 白高亮），不引入其他颜色
- 模拟命令只是装饰，不能变成功能 bug——`$ ls projects/` 下面就是静态 HTML 内容，不需要真的可输入
- 打字机效果控制在 800ms 内完成，不要让用户等
- 每个 section 必须有一个"命令提示符"作为视觉锚点

---

## Style 5: 赛博霓虹 (Cyberpunk/Neon)

Reference: ZEAL.EXE · 创意技术工作室

**Design philosophy:** 像一个黑客在霓虹灯管闪烁的地下室写的代码。深黑底色 + 青/紫/品红电光，科技感而不失精致。

| Property | Value |
|----------|-------|
| Background | 深黑 #08080F，极微弱网格纹理（CSS background-image dot pattern） |
| Primary text | 纯白 #F0F0F5 |
| Secondary text | 暗灰 #6B6B80 |
| Accent colors | 三色霓虹系统：电光青 #00F0FF、霓虹紫 #8B5CF6、品红 #FF00E5。每种用途严格分工：青 = 链接/高亮，紫 = 标签/边框，品红 = CTA/强调 |
| Heading font | 无衬线 `"Space Grotesk", "Inter", system-ui`，权重 700-800，可加 text-shadow 霓虹发光 |
| Body font | 无衬线，权重 400，行距 1.7 |
| Max content width | 880px，居中 |
| Section spacing | 100-140px，每个 section 之间可加一条微妙的霓虹发光分隔线 |
| Hero layout | **中心大字报**。超大名字居中，下方一行角色描述，名字可加青色 text-shadow 发光。最下面是 6-8 个技能标签（霓虹边框的 pill button，hover 时 glow 增强） |
| Cards | 深色背景卡片 #111122，极细霓虹紫边框 1px solid rgba(139, 92, 246, 0.3)，hover 时边框变亮 + 内部微光。圆角 8-12px |
| Skill tags | 胶囊型 pill button，镂空：透明底 + 霓虹紫边框 + 白字。hover 时边框变电光青 + text-shadow 发光 |
| Grid layout | 服务/项目用 2×2 或 2×3 网格，每个格子里是 icon + 服务名 + 一行描述 |
| Navigation | 顶部居中或右对齐，纯文字链接，hover 时变电光青并加微弱 text-shadow |
| Glow effects | 核心视觉手段：关键文字用 `text-shadow: 0 0 10px #00F0FF`，卡片边框用 `box-shadow: 0 0 15px rgba(139, 92, 246, 0.15)` |
| Images | 可用深色处理的项目截图，边框加微弱的霓虹紫 |
| Overall feel | 走进赛博空间。你是一个搞科技创作的人，这个网站就是你搭建的终端站。酷，但不刺眼。 |

Key rules:
- 霓虹发光效果要点到为止——text-shadow 模糊值控制在 8-15px，不要大面积使用否则刺眼
- 三色系统严格执行：青 = 链接，紫 = 边框/标签，品红 = CTA。不乱用
- 背景不是纯黑，带微弱纹理/噪点增加质感
- 卡片/标签的边框发亮是主要视觉引擎，不是颜色填充
- 动效克制：hover 时边框变色 + 微光增强，不要旋转/缩放

---

## Style 6: 旅程叙事 (Journey/Narrative)

Reference: Roads · 设计师作品集

**Design philosophy:** "Roads" 不只是项目列表，是一条路。你的作品不是彼此孤立的产物，而是一条连续的成长轨迹。

| Property | Value |
|----------|-------|
| Background | 暖白 #FAFAF8，或极淡灰 #F5F5F3 |
| Primary text | 接近黑 #1A1A1A |
| Secondary text | 中灰 #707070 |
| Accent | 大地色系选一个：陶土红 #C4735A、橄榄绿 #6B8E5A、或灰蓝 #5A7D8E。只用一种，作为链接色和时间线标记 |
| Heading font | 衬线体 `"Noto Serif SC"` 或 `"Playfair Display"`，权重 500-700 |
| Body font | 无衬线 `system-ui`，权重 400，行距 1.8 |
| Max content width | 680px（窄宽营造沉浸感） |
| Section spacing | 80-100px |
| Hero layout | **一句话定位**。顶部居中的一句话宣言（字号 32-40px），下方是简短自我介绍。整体如同书的扉页——简洁、郑重。底部可放一个向下箭头引导 scroll |
| 项目展示 | 这是 Style 6 的灵魂。**不用网格，用时间线叙事**：每个项目沿一条垂直中轴线排列，左侧是年份/日期标记，右侧是项目卡片。每张卡片包含：项目名 + 一句话描述 + 标签。卡片之间用细线连接（`border-left`），形成一个连续的"路" |
| Work cards | 极简：无边框，左侧一根 accent 色的竖线（2px），标题 + 一行描述。hover 时竖线变粗（4px）+ 背景微亮 |
| Connective narrative | 项目列表开头有一段 2-3 句话的叙事引导："这条路从 X 年开始，从 A 项目走到 B 项目……"——把项目之间的关系讲出来，不是冷冰冰的列表 |
| Navigation | 顶部简洁右对齐文字链接 |
| Images | 可配大幅横图作为 section 之间的分隔（header image），色调统一为大地色系或低饱和 |
| Timeline markers | 时间节点用 accent 色小圆点（8px）+ 年份标注 |
| Overall feel | 像在翻一个人的职业自传。不是"我做了这些"，而是"我是这样走过来的"。 |

Key rules:
- 时间线竖线是核心视觉锚点——所有项目卡片必须对齐同一根竖线
- 叙事引导文字是区隔于其他风格的灵魂——不是"Projects"，而是"这条路"
- 图片要克制，不让视觉盖过文字的叙事感
- 每个项目卡片的信息密度不要高：标题 + 一句话 + 年份，够了
- accent 色只用在大地色系里挑一种——保持自然、温润的调子
