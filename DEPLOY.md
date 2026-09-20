# Deploying to Vercel (static, no backend)

This site is plain HTML/CSS/JS — nothing in the pages actually calls the
`backend/` (Node) or `app.py` (Python) code, so it deploys as a static
site with zero build step.

## What was added
- `vercel.json` — minimal static-site config (no build command, no
  framework detection needed).
- `.vercelignore` — tells Vercel to skip the unused `backend/` folder,
  `app.py`, the leftover `auth.js`/`dashboard.js`/`script.js` files, the
  `.csv` dataset, and `.env`, so nothing server-side is uploaded.

No existing website file was modified.

## Deploy steps

### Option A — Vercel dashboard
1. Push this folder to a GitHub repo (or upload it directly).
2. Go to https://vercel.com/new and import the repo.
3. Framework Preset: **Other**. Build Command: leave empty. Output
   Directory: leave empty (root).
4. Click **Deploy**.

### Option B — Vercel CLI
```bash
npm i -g vercel
cd Ayur-main
vercel        # first deploy, follow prompts
vercel --prod # promote to production
```

## Notes
- All pages (`index.html`, `blogs.html`, `ai-chat-bot.html`, etc.) are
  served as-is at their existing `.html` URLs — no rewrites needed.
- The AI chat / sign-in / contact forms in this repo don't currently
  submit to a live server (they point to `#` or an unset backend URL),
  so there's nothing to reconnect for a static deploy. If you later want
  real backend functionality, that would need to be added separately
  (e.g. as Vercel Serverless/Edge Functions) — out of scope here since
  you asked for no backend.
