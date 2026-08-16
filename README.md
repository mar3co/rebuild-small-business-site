# Rebuild Small Business Site

Paste a small-business URL and a brief. Get a rebuilt and **improved** marketing site. Booking and checkout stay on the system that already takes money.

WordPress → a modern stack is the home case. The skill **recommends** Next.js, Tailwind, Vercel, and typed `content/` modules, and uses that unless the brief or the money system makes it a bad fit.

This repo is the plugin and a one-plugin marketplace for [Grok](https://x.ai/cli) and [Claude Code](https://claude.ai/code) / Cursor.

## What you get

**Input:** a live URL and some instructions.

**Output (default):** a local marketing-site rebuild — improved information architecture, DRY config for hours / NAP / links, real Book hrefs, checked in a browser or against a running dev server.

**Optional, only if you ask:** GitHub repo, Vercel (or the chosen host), launch-shaped metadata, cutover checklist. DNS does not move until you say so.

## Install

**Grok**

```text
grok plugin marketplace add mar3co/rebuild-small-business-site
grok plugin install rebuild-small-business-site --trust
```

Then paste a URL, or run `/rebuild-small-business-site`.

**Claude / Cursor**

```text
claude plugin marketplace add mar3co/rebuild-small-business-site
claude plugin install rebuild-small-business-site@rebuild-small-business-site
```

Then paste a URL, or run `/rebuild-small-business-site:rebuild`. The skill also appears as `/rebuild-small-business-site:rebuild-small-business-site`. Claude does not register the bare `/rebuild-small-business-site` after a plugin install.

**Manual**

Copy `skills/rebuild-small-business-site/` into `~/.grok/skills/`, `.grok/skills/`, `~/.claude/skills/`, or `.claude/skills/`. A copied skill is `/rebuild-small-business-site` on both hosts.

## What it does

1. Reads the live site (platform, money system, NAP, hours, services, old URLs).
2. Proposes an improved page list. Does not clone the 2015 sitemap.
3. Puts every business fact in `content/`.
4. Builds a local marketing site. Book controls are real URLs into the existing system.
5. Stops. Ship / DNS only if you ask.

Rules it will not break: no fake checkout or “booking form for later,” no invented testimonials, no hardcoded hours, no Open Graph pointed at a preview host.

## Layout

```text
commands/rebuild.md                         Claude slash: /rebuild-small-business-site:rebuild
skills/rebuild-small-business-site/         Runbook + references
  SKILL.md
  references/content-modules.md             DRY config contract
  references/keep-the-system.md             Keep Mindbody / Shopify / Square / Jane / …
  references/improve.md                     IA, design floor, accessibility
  references/ship.md                        Optional publish / cutover
plugin.json                                 Plugin identity (keep in sync with .claude-plugin/plugin.json)
.claude-plugin/                             Claude / Cursor marketplace
.grok-plugin/                               Grok marketplace
docs/design.md                              Design spec
docs/verification.md                        What was checked before 1.0.0
```

## Maintain

- Bump `"version"` in **both** `plugin.json` and `.claude-plugin/plugin.json`.
- After changing the skill, run `grok plugin validate .` and `claude plugin validate --strict .`.
- Design decisions live in [docs/design.md](docs/design.md).

## License

MIT
