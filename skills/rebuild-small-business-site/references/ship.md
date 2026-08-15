# Optional ship

Path A (local rebuild) is done without this file. Run these steps only when the operator asks to publish.

1. **GitHub** — visibility as they prefer. README says how to change hours and links, and that booking stays on the existing system.
2. **Host** — Vercel when that is the stack. Git-linked. Preview URLs for QA.
3. **Launch-shaped metadata from day one** — `metadataBase` and `og:image` are the **real** domain. Preview the card at `/opengraph-image` or `/api/og` on any host. Do not point tags at `*.vercel.app` so Slack looks nice.
4. **Cutover checklist, then stop**
   - Redirects checked incognito
   - Every Book control lands on the right product
   - Widgets load on the production host
   - Share a URL on the real domain and confirm the card
   - Do not attach DNS until they say so
