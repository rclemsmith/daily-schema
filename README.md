# Daily Schema

A small installable web app: one DWH/DB concept a day (lesson, key points, quiz), plus an optional "why it matters now" note. Static — no backend required.

## Host it on GitHub Pages

1. Create a new repository on GitHub (e.g. `daily-schema`).
2. Add these four files to the repo root: `index.html`, `manifest.json`, `sw.js`, `icon.svg`.
   - Easiest: drag-and-drop them into the GitHub web UI ("Add file" → "Upload files"), or:
     ```bash
     git init
     git add index.html manifest.json sw.js icon.svg
     git commit -m "Daily Schema"
     git branch -M main
     git remote add origin https://github.com/<your-username>/daily-schema.git
     git push -u origin main
     ```
3. In the repo: **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch", branch `main`, folder `/ (root)`. Save.
5. GitHub gives you a URL like `https://<your-username>.github.io/daily-schema/` (takes a minute or two to go live).

## Install it on your phone

Open that URL on your phone, then:
- **iPhone**: Share → "Add to Home Screen"
- **Android**: menu (⋮) → "Add to Home screen" / "Install app"

It'll run full-screen from a home screen icon, and works offline once you've opened it at least once (the service worker caches the core page).

## Notes

- The "live briefing" button (ask Claude for a current update on today's topic) only works inside Claude's own artifact preview — it uses a capability that isn't available on a plain hosted site, so it's automatically hidden here. Everything else (daily rotating lesson + quiz) works fully offline and standalone.
- The topic rotates automatically based on the date (day-of-year modulo the topic list), so it changes once a day with zero setup.
- To add more topics, edit the `LIB` array near the top of the `<script>` block in `index.html` — same shape as the existing entries.
