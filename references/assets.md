# Asset Guide

Use this guide when collecting, naming, and placing user-provided assets.

## Principle

Assets should support the user's credibility. Do not invent real photos, logos, testimonials, client marks, QR codes, or screenshots.

## Recommended Folder

For generated sites, place local assets under:

```text
dist/
├── index.html
├── HOW_TO_UPDATE.md
└── images/
    ├── avatar.jpg
    ├── project-01.jpg
    ├── project-02.jpg
    ├── article-01.jpg
    └── qr-wechat.png
```

Use lowercase names, hyphens, and stable numbering.

## Asset Types

| Asset | Recommended Size | Use |
| --- | --- | --- |
| Avatar / profile photo | Square, 800x800 or larger | Hero, About |
| Project cover | 1600px wide if possible | Project cards |
| Article cover | 1200x630 or 16:9 | Article cards, social sharing |
| Logo / client mark | SVG or transparent PNG | Trust section |
| QR code | PNG, clear and uncropped | Contact modal |
| Screenshot | 1440px wide if possible | Portfolio detail or project card |

## If Assets Are Missing

- No avatar: use typography-only hero or initials; do not use a fake person photo.
- No project images: use text-based project cards or simple placeholders matching the template style.
- No article covers: use article list layout without images.
- No QR code: use normal links or text instructions.
- No client logos: omit the trust section.

## Image Handling

- Keep images lightweight. Prefer compressed JPG/WebP for photos and PNG/SVG for logos or QR codes.
- Add meaningful `alt` text.
- Ensure CSS prevents overflow: `max-width: 100%`.
- Do not hotlink private local files. Copy needed assets into `dist/images/`.
- If the user provides huge images, resize or compress before delivery when possible.

## Contact Assets

Only show QR modals for channels with actual QR codes or when the user explicitly wants QR placeholders.

Common contact data:

```text
Email: name@example.com
GitHub: https://github.com/name
LinkedIn: https://linkedin.com/in/name
X/Twitter: https://x.com/name
微信公众号: QR image required for scan flow
小红书: profile link or QR image
Newsletter: subscribe URL
```

## Final Placeholder Check

Before delivery, search the generated site for:

- `your-name@example.com`
- `github.com/your-name`
- `your newsletter link`
- `二维码待上传`
- `{{SITE_TITLE}}`
- `{{SITE_DESC}}`
- `{{DEMO_DATA}}`

If any remain, replace them or remove the corresponding block.
