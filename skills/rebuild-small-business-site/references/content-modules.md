# Content modules

Every business fact lives under `content/` (TypeScript modules on the default stack; the same keys as JSON otherwise). Components import these files. They do not hardcode NAP, hours, nav, prices, or Book hrefs.

When the default stack is used, tests lock offer URLs and the redirect table.

## Always

### `site`

Name, tagline, description, canonical URL, email, phone, SMS if they publish one, address, hours, social, geo, primary nav, footer nav.

Hours, NAP, and the canonical URL exist only here.

### `offers`

What they sell as **copy plus a real URL**. Intro special, membership, consult, “call to book” — whatever is true. Prices are display only. The money system is the source of truth for what a client can actually buy.

A Book / Shop / Book now control is a real href from `offers` or `booking`, never `#`. Phone-only: that href is the `tel:` / `sms:` from `site`.

### `redirects`

Old paths → new paths (WordPress `/contact`, `/pricing-2`, `/portfolio_page/…`, Wix leftovers). Permanent.

## When the live site or brief has them

| File | Owns |
| --- | --- |
| `services` | Classes, menu, treatments |
| `team` | People you can name. Missing roster stays client-open. |
| `faq` | Existing questions, or ones the brief asks for |
| `reviews` | Existing quotes plus rating aggregates with **source and count**. No source → do not ship. |
| `booking` | Widget ids, studio ids, product URL helpers (Mindbody, Jane, Vagaro, Calendly, …) |
