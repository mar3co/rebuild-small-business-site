---
name: rebuild-small-business-site
description: Use when the user pastes a small-business website URL to rebuild or modernize it, wants a WordPress, Wix, or Squarespace marketing site replaced, or asks to improve a studio, salon, gym, clinic, restaurant, or similar site while keeping the existing booking or checkout system. Use when tempted to add a booking form for later, invent typical testimonials, clone the old sitemap, hardcode hours, or point Open Graph at a preview host. Use when the user runs /rebuild-small-business-site.
license: MIT
metadata:
  author: mar3co
  short-description: Rebuild and improve a small-business marketing site from a URL.
---

# Rebuild a small-business site

Rebuild the **marketing site**. Improve the IA. Keep the system that already takes money. Put every business fact in `content/`. Do not invent facts.

This is a rebuild-and-improve skill, not a clone and not an in-place theme refresh. WordPress → a modern stack is the home case.

Design from **their** identity: mark from their logo, their photography, type that matches the room — not a “more feminine / more premium” default and not a generic small-business template. If a `frontend-design` skill is loaded, use it. If it is not, this floor still applies.

## When not to use

- They want a theme tweak on the current WordPress/Wix/Squarespace site
- The brief is “build us a custom checkout / calendar / membership app”

If the live site **is** the store (Shopify, Square Online), this skill still runs: keep checkout and rebuild only a marketing surface when they asked for that. See `references/keep-the-system.md`.

## Phases

1. **Intake.** Treat it as a rebuild. Read constraints. If the current site is the checkout, say so and keep that system. See `references/keep-the-system.md`.
2. **Read the live site** like a competitor, then like a lawyer: platform, money system, NAP, hours, services, prices, photos, reviews, nav, old URLs, the 2–4 facts they compete on, voice. Missing items are **client-open**.
3. **State the improved page list** and what stays off-site (booking, cart, login), then build. Do not wait for a second approval unless a client-open fact blocks a page. See `references/improve.md`.
4. **Recommend** Next.js App Router, Tailwind, Vercel, typed `content/` modules. Use that unless the brief or the money system makes it a bad fit.
5. **Put facts in `content/`.** Components do not hardcode hours, NAP, or Book hrefs. See `references/content-modules.md`.
6. **Local rebuild is done** when Path A below is true. Tell them which file to edit for hours and links.
7. **Ship only if they ask.** See `references/ship.md`.

## Hard rules

- Do not replace the system that takes money.
- Do not invent quotes, hours, roster, prices, or a lead/booking form that was not on the old site.
- Do not attach the custom domain as a test.
- Do not point `metadataBase` / `og:image` at a preview host.
- Do not add a CMS unless the brief asks.
- Do not copy another studio’s words, colors, or photos into this business.

| Excuse | Reality |
| --- | --- |
| “Booking form for now, wire Mindbody later” | A fake form is a fake checkout. Book controls are real hrefs from `content/`. |
| “It’s a request form, not checkout” | If they did not have a lead form, do not invent one to look finished. |
| “They asked for typical testimonials” | Invented quotes do not ship. Use sourced quotes or omit Reviews. |
| “Clone the sitemap, it’s faster” | Improvement is the job. Propose a tighter IA, then build. |
| “Hardcode hours in the footer, config later” | Hours exist only in `content/site`. |
| “Point OG at the preview host so Slack works” | Tags stay on the real domain. Preview art at `/opengraph-image`. |

**Red flags — stop:** `#` Book buttons · placeholder quotes · hours only in a component · page-for-page WordPress clone · `VERCEL_URL` in `metadataBase` · “we’ll wire booking later” · default stack with no tests on offer URLs / redirects · claiming click-through without a browser or a running dev server

## Done (path A)

- Local site. DRY `content/`. Real booking links. Improved IA.
- On the default stack: tests lock offer URLs and the redirect table. See `references/content-modules.md`.
- Every old path in `redirects` has a destination that exists. Click one leftover URL on the running site (or `curl` it) and confirm the redirect.
- Click through desktop and mobile in a browser if tools allow. Otherwise start the dev server and `curl` each primary route plus every Book href. Do not write “browser-checked” unless one of those happened.
- Operator knows which file changes hours and links.
