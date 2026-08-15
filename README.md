# Rebuild Small Business Site

A free skill and plugin. Paste a small-business URL and a brief. Get a rebuilt and **improved** marketing site. Booking and checkout stay on the system that already takes money.

WordPress → a modern stack is the home case. The skill recommends Next.js, Tailwind, Vercel, and typed `content/` modules, and uses that unless the brief or the money system makes it a bad fit.

## What you get

**Input:** a live URL and some instructions.

**Output (default):** a local marketing-site rebuild — improved IA, DRY config for hours/NAP/links, real Book hrefs, browser-checked.

**Optional, only if you ask:** GitHub repo, Vercel (or the chosen host), launch-shaped metadata, cutover checklist. DNS does not move until you say so.

## Install

Grok:

```text
grok plugin marketplace add mar3co/rebuild-small-business-site
grok plugin install rebuild-small-business-site --trust
```

Claude / Cursor:

```text
claude plugin marketplace add mar3co/rebuild-small-business-site
claude plugin install rebuild-small-business-site@rebuild-small-business-site
```

Or copy `skills/rebuild-small-business-site/` into `~/.grok/skills/` or `.grok/skills/`.

Then paste a URL, or run `/rebuild-small-business-site`.

## Rules the skill enforces

- Rebuild and improve — do not clone the 2015 sitemap
- Do not replace Mindbody, Shopify checkout, Square, Jane, Vagaro, or phone-only booking
- Do not invent reviews, hours, roster, or a fake booking form
- Hours, NAP, and Book links live in `content/`
- Open Graph points at the real domain, not a preview host

## License

MIT
