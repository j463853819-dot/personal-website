# Self-Check Checklist

After generating the site and before deploying, run through this checklist. P0 items **must** pass; P1 items should pass unless the chosen style explicitly overrides them.

---

## P0 — Blockers (must fix before deploy)

- [ ] **User goal reflected**: hero, CTA, and first content section match the user's stated audience and visitor action
- [ ] **Structure confirmed**: generated sections match the structure confirmed with the user
- [ ] **Meta tags complete**: `<title>`, `<meta name="description">`, `<meta charset="utf-8">`, `<meta name="viewport">` all present
- [ ] **Mobile renders correctly**: tested at 375px wide. No horizontal scroll, no text overflow, no elements wider than viewport
- [ ] **Images don't break layout**: all `<img>` have explicit `width`/`height` or CSS `max-width: 100%`. No image exceeds container
- [ ] **CTA is visible above fold on mobile**: the primary CTA button/link from Phase 1 Q2 is visible without scrolling on a phone
- [ ] **No broken links**: all internal anchor links (`href="#projects"`, etc.) point to valid section IDs
- [ ] **No English on a Chinese site**: check for stray "Projects", "About", "Contact" labels on sites meant to be in Chinese
- [ ] **No placeholders left**: no `your-name@example.com`, `github.com/your-name`, `your newsletter link`, `二维码待上传`, `{{SITE_TITLE}}`, `{{SITE_DESC}}`, or `{{DEMO_DATA}}`

## P1 — Quality (should fix before deploy)

- [ ] **Font hierarchy is clear**: headings are visually distinct from body text. Not just different sizes — different weights
- [ ] **Line height is readable**: body text `line-height` ≥ 1.6. Not cramped
- [ ] **Color contrast passes**: text on background has sufficient contrast. Light gray text on white = invisible
- [ ] **No orphan words**: single-word lines at the end of paragraphs. Adjust text or width slightly
- [ ] **Spacing is consistent**: section margins follow the template's rules. No random 20px gaps next to 120px gaps
- [ ] **Emoji render**: test on at least 2 platforms (macOS Chrome + iOS Safari). Emoji in page titles and headings appear correctly
- [ ] **Loading state**: if using Bitable CMS path, there's a visible loading state while API fetches. Demo data kicks in within 3 seconds if API fails
- [ ] **No private data in frontend**: if using CMS, frontend code contains no app secrets, access tokens, private document URLs, or personal credentials
- [ ] **Print-friendly**: `@media print` hides navigation and shows clean content (built into templates, just verify)

## P2 — Polish (nice to have)

- [ ] **Hover states feel intentional**: cards, links, buttons all have a hover effect. No element changes on hover that shouldn't
- [ ] **Focus states for keyboard nav**: `:focus-visible` outlines present on interactive elements
- [ ] **Favicon**: at least a solid-color square. Better than the default browser icon
- [ ] **OG tags**: `og:title`, `og:description`, `og:image` for social sharing previews
- [ ] **Page load under 2 seconds**: no heavy images, no blocking scripts

## Bitable CMS Path — Extra Checks

- [ ] **setup.md is clear**: explains app_id, app_secret, base_id, table_id in plain Chinese, and says where secrets must be stored safely
- [ ] **No direct secret exposure**: app_secret and tokens are stored in a serverless/backend/proxy/prebuild environment, never in `index.html`
- [ ] **Field names match**: JS fetch code or the safe data endpoint uses the exact field names from the Bitable. No typos in JSON keys
- [ ] **Demo data reflects real content**: the fallback demo data in `{{DEMO_DATA}}` matches the user's actual profile, not generic placeholders
- [ ] **Error state handled**: if API returns 401/403/500, the page doesn't break — falls back to demo data gracefully
