# Publish the VCG AI 2027 decks — link-based (artifact style)

Goal: a shareable URL that anyone with the link can open (no login). Open it in Safari on the iPad → AirPlay/mirror to the screen. Touch-ready (swipe + on-screen ‹ › ) and keyboard-ready.

> **Access model:** link = access. The URL is effectively the password — share it deliberately and treat it as sensitive (these decks are VCG-confidential). You can add a gate later (Cloudflare Access / Azure Entra) without changing the files — reversible.

## Fastest — instant link, no account  ⟵ artifact style
1. Use the prepared **`vcg-ai-2027-site.zip`** in this folder.
2. Go to **app.netlify.com/drop** and drag the ZIP in.
3. You get a live `https://<random>.netlify.app` link immediately. (Create a free account to keep it permanent + rename it.)
The bare link opens the landing hub (`_redirects` routes `/` → `home.html`); from there: Board Deck / Vault / Teaser.

## Permanent — your own account (free)
- **Cloudflare Pages:** `npx wrangler pages deploy . --project-name vcg-ai-2027` (after `npx wrangler login`). Clean permanent `*.pages.dev` URL, fast global CDN.
- **Netlify CLI:** `npx netlify deploy --dir . --prod` (after `npx netlify login`).

## Own cloud — Azure Static Web Apps (public)
`staticwebapp.config.json` is set to public and lands on `home.html`. Deploy via the VS Code *Azure Static Web Apps* extension (app location `/`, no build) or the SWA CLI. Best if you'd rather keep it inside VCG's own tenant.

## Notes
- Publish the **whole folder** (all `.html` + `lib/` + `_redirects` + `staticwebapp.config.json`). Relative paths to `lib/` must stay intact — the ZIP already has the right structure.
- Entry point: `home.html` (landing). `_redirects` + the Azure config both route the bare URL there.
- `tasks/` (planning notes) and the `.md` files are **excluded** from the ZIP.
- iPad: open the URL in Safari → swipe to advance → Share/AirPlay to the screen (or USB-C→HDMI).
