# Intake Guide

Use this guide to understand the user's website needs before choosing a structure or template.

## Core Principle

Ask like a website strategist, not like a developer. Start with identity, audience, and desired visitor action. Technical choices come later.

## Six Core Questions

Ask one question at a time. If the user has already answered a question naturally, do not ask it again.

1. **Identity**  
   "先聊聊你是谁：你是做什么的？比如设计师、工程师、写作者、咨询顾问、创业者，或者其他身份。"

2. **Audience**  
   "这个网站主要给谁看？招聘方、潜在客户、读者、合作伙伴、粉丝，还是朋友和陌生访客？"

3. **Visitor Action**  
   "你希望别人看完网站后做什么？联系你、看作品、读文章、预约咨询、关注社交媒体，还是了解你的经历？"

4. **Content and Assets**  
   "你现在手上有哪些内容？头像、个人介绍、项目、文章链接、作品图、客户评价、联系方式都可以。"

5. **Update Frequency**  
   "你多久会更新一次？基本不改、每月一次、每周一次、还是经常新增文章或项目？"

6. **Visual Direction**  
   "你更喜欢哪种气质？极简、可爱、杂志感、终端极客、赛博科技、还是成长叙事？"

## When the User Is Unsure

Use defaults instead of stalling:

- Audience unclear: assume "people who want to understand and contact the user".
- Visitor action unclear: use "联系我" as the primary CTA.
- Content limited: create a one-page profile with hero, about, selected links, and contact.
- Update frequency unclear: default to static.
- Style unclear: recommend based on persona using `decision-rules.md`.

## Minimum Viable Content

If the user has very little material, ask for only these:

- Name or display name
- One-sentence role
- 2-3 sentence self-introduction
- 1-3 links or contact methods
- Preferred style

With that, generate a simple one-page site. Do not force the user to prepare a full portfolio.

## Content Quality Prompts

Use these prompts when content is thin:

- "你最近做过哪三件最能代表你的事？"
- "别人通常因为什么来找你？"
- "你希望别人记住你的哪一句话？"
- "有没有一个项目、文章或经历，是你最想放在首页的？"
- "如果只能放一个联系方式，你希望别人通过什么找到你？"

## Confirmation Pattern

Before generation, summarize:

```text
我理解你的目标是：
- 身份：
- 主要访客：
- 访客动作：
- 网站结构：
- 风格：
- 更新方式：

我会先做一个静态首版，后续再按你的反馈调细节。这样可以吗？
```
