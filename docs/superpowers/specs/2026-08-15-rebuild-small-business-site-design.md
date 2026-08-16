# Rebuild Small Business Site — Design

A free skill and one-plugin marketplace that rebuilds a small-business marketing site from a URL and a brief. The job is **rebuild and improve**, not clone. WordPress → a modern stack is the home case. Camarillo Pilates (`mar3co/camarillo-pilates-web`) is the reference engagement, not a template to copy.

## Goal

An agent given a live URL and some instructions produces a local marketing-site rebuild that:

- reads as this business in the current year, not a 2015 theme and not a SaaS landing page
- keeps whatever already takes money (Mindbody, Shopify checkout, Square, Jane, Vagaro, phone-only)
- puts hours, NAP, nav, and booking links in one DRY config layer
- does not invent facts (quotes, hours, roster, prices)

Shipping to GitHub / Vercel / DNS is optional and only happens if the operator asks.

## Packaging

New **public** repo: `mar3co/rebuild-small-business-site`.

The repo is both the plugin and a one-plugin marketplace — the same pattern as `mar3co/fable-orchestrator`. It is **not** added to the Fable marketplace. Fable’s catalog is the architect/lanes plugin; mixing a site rebuild into it would break that install path and confuse what the plugin is.

```
rebuild-small-business-site/
  .claude-plugin/marketplace.json  # Claude / Cursor catalog (plugin source: ./)
  .claude-plugin/plugin.json
  .grok-plugin/marketplace.json    # Grok catalog (plugin source: ./)
  plugin.json                      # plugin identity at repo root
  LICENSE                          # MIT
  README.md
  commands/rebuild-small-business-site.md
  skills/rebuild-small-business-site/
    SKILL.md
    references/
      content-modules.md
      keep-the-system.md
      improve.md
      ship.md
```

v1 ships **procedure only**: one skill, four short reference files, a `commands/` slash entry, dual marketplace manifests so Grok and Claude/Cursor can install it. No hooks, no agents, no MCP, no site template, no Camarillo copy or photos. Design work uses `frontend-design` when that skill is already loaded; it is not a dependency of this plugin.

Install (after publish):

```text
grok plugin marketplace add mar3co/rebuild-small-business-site
grok plugin install rebuild-small-business-site --trust
```

Claude/Cursor: `claude plugin marketplace add mar3co/rebuild-small-business-site` then install the same plugin name. The skill folder also works if someone copies it into `~/.grok/skills/` or `.grok/skills/`.

**Skill name:** `rebuild-small-business-site`  
**Slash:** `/rebuild-small-business-site` (plugin `commands/` entry; Claude also accepts `/rebuild-small-business-site:rebuild-small-business-site`)

**Description** (when-to-use only, no workflow summary):

> Use when the user pastes a small-business website URL to rebuild or modernize it, wants a WordPress, Wix, or Squarespace marketing site replaced, or asks to improve a studio, salon, gym, clinic, restaurant, or similar site while keeping the existing booking or checkout system. Use when the user runs /rebuild-small-business-site.

## Method

Stack-agnostic procedure. The skill **recommends** Next.js App Router, Tailwind, Vercel, and typed `content/` modules, and uses that unless the brief, the money system, or a hard constraint makes it a bad fit.

### 1. Intake

Treat the request as a rebuild. Read the brief for constraints (keep Shopify, no Vercel, extra pages, brand notes). If the current site *is* the checkout (Shopify storefront, Square online store), say so and keep that system.

### 2. Read the live site

Browse like a competitor, then like a lawyer. Extract:

- platform
- what takes money
- NAP, hours, services, prices, photos, reviews, nav
- the 2–4 facts they actually compete on
- old URLs for redirects
- voice

Anything not on the site or in the brief is **client-open**. Do not fill gaps with invented quotes, hours, roster names, or prices.

### 3. Propose an improved site, then build

Do not clone the old sitemap. State the proposed page list and what stays off-site (booking, cart, login), then build. Do not wait for a second approval unless a client-open fact blocks a page you would otherwise ship.

Recommended defaults to consider (drop any that do not fit):

- a Start / how-to-begin path
- Visit with NAP, hours, and a map
- FAQ
- reviews only if the proof is real
- LocalBusiness JSON-LD
- favicon and share cards from their mark
- mobile-first nav
- one primary CTA

New **pages** are allowed. New **facts** are not. Copy on a new `/start` page must come from how they already tell people to begin, or it stays client-open.

Recommend Next.js / Tailwind / Vercel / typed `content/`. Deviate only when the brief or the money system requires it.

### 4. DRY config

Every studio fact lives under `content/` (or the same keys as JSON if the stack is not TypeScript). Components do not hardcode business facts.

**Always**

| File | Owns |
| --- | --- |
| `site` | Name, tagline, description, canonical URL, email, phone, SMS if they publish one, address, hours, social, geo, primary nav, footer nav |
| `offers` | What they sell as copy plus a real URL. Prices are display only. |
| `redirects` | Old paths → new paths |

**When the live site or brief has them**

| File | Owns |
| --- | --- |
| `services` | Classes, menu, treatments |
| `team` | People you can name. Missing roster stays client-open. |
| `faq` | Existing questions, or ones the brief asks for |
| `reviews` | Existing quotes plus rating aggregates with source and count |
| `booking` | Widget ids, studio ids, product URL helpers |

A Book / Shop / Book now control is a real href from `offers` or `booking`, never `#` and never a fake checkout. Hours, NAP, and the canonical URL exist only in `site`. Reviews without a source do not ship.

When the default stack is used, tests lock offer URLs and the redirect table.

### 5. Local rebuild is done

Click through desktop and mobile. Confirm every Book control lands on the real system. Tell the operator which file to edit for hours and links. That is path A, and it is the focus.

### 6. Optional ship (path B)

Only if they ask:

1. GitHub repo (visibility as they prefer). README explains how to change hours and links, and that booking stays on the existing system.
2. Vercel (or the chosen host), Git-linked, preview URLs for QA.
3. Launch-shaped metadata from day one: `metadataBase` and `og:image` are the **real** domain. Preview the card at `/opengraph-image` on any host. Do not point tags at a preview host so Slack looks nice.
4. Cutover checklist, then stop: redirects incognito, every Book control, widgets on the production host, share on the real domain. Do not attach DNS until they say so.

## Hard rules

- Do not replace the system that takes money.
- Do not invent facts.
- Do not attach the custom domain as a test.
- Do not point Open Graph at a preview host as a workaround.
- Do not add a CMS unless the brief asks for one.
- Do not ship a generic “small business” template look. Design from their identity (mark, photography, voice).
- Do not copy Camarillo’s words, colors, or photos into another business.

## What v1 is not

- Not an in-place Wix/WordPress theme refresh. This skill rebuilds.
- Not a Shopify theme factory. If Shopify is the store, keep checkout; rebuild only the marketing surface if that is the brief.
- Not a page-builder or hosted product.
- Not a VEBA-only internal playbook with private conventions. It is public and free. VEBA is a user of it, not the brand on it.

## Reference split

| File | Holds |
| --- | --- |
| `SKILL.md` | When to use, phases, hard rules, definition of done |
| `references/content-modules.md` | Config file contract and key lists |
| `references/keep-the-system.md` | How to recognize and keep Mindbody, Shopify, Square, Jane, Vagaro, Calendly, phone-only |
| `references/improve.md` | Improvement defaults (IA, proof, SEO/share, a11y) and the facts-vs-pages line |
| `references/ship.md` | Optional GitHub / host / metadata / cutover checklist |

One home per fact. The runbook points at these files; it does not restate their tables.

## Verification of the skill

Before calling the skill done:

- A no-skill baseline on a “here is a URL, rebuild it” prompt should show the failure modes this skill exists to stop (fake checkout, invented testimonials, cloned 2015 sitemap, hardcoded hours, preview-host OG).
- The same prompt with the skill loaded should follow the phases, propose an improved IA, keep the money system, and put facts in `content/`.
- `grok plugin validate` (or the Claude equivalent) passes on the repo.
- README states input (URL + brief), output (local rebuild), and the optional ship path.

## Out of scope for v1

- Helper scripts that scrape a URL into `content/` files
- A starter Next.js template inside this repo
- Extra VEBA skills (deploy, brand, copy) in the same plugin
- A multi-plugin mar3co marketplace catalog
