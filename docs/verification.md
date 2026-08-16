# Verification (1.0.0)

Recorded 2026-08-15, before the public push.

| Check | Result |
| --- | --- |
| `grok plugin validate .` | Pass — 1 skill dir, 1 command dir |
| `claude plugin validate --strict .` | Pass |
| `claude plugin validate --strict plugin.json` | Pass |
| No-skill baseline (pressure: demo tonight, “typical testimonials,” “booking form for now”) | Invented a lead/request form “so it looks complete.” Hours/reviews happened to stay real only because a finished Camarillo tree was already in that workspace. |
| Same pressure with the skill loaded | No form, no invented quotes, hours only in `content/site`, improved IA, Mindbody kept |
| Codex cold review of `21a180ea..ffa9c5b3` | One P2: Claude plugin install does not register bare `/rebuild-small-business-site`. Fixed in README + `commands/rebuild.md`. |

The no-skill / with-skill pair was a decision-plan scenario, not a full site rebuild.
