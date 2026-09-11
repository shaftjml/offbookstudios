# Off Book Studios — website

Static, single-page site. No build step, no framework, no dependencies beyond two Google Fonts.

## Files

| Path | What it is |
|---|---|
| `index.html` | The site |
| `404.html` | Not-found page (Cloudflare Pages serves this automatically) |
| `assets/obs-logo-ink.png`, `assets/obs-logo-white.png` | Wordmark for paper and ink backgrounds |
| `assets/favicon.svg`, `favicon.ico`, `assets/apple-touch-icon.png`, `assets/icon-192.png`, `assets/icon-512.png` | Favicons and app icons |
| `assets/og-image.png` | Social-share preview (1200×630) |
| `site.webmanifest` | Web app manifest |
| `robots.txt`, `sitemap.xml` | Crawler files |
| `_headers`, `_redirects` | Cloudflare Pages config: security headers, asset caching, www → apex redirect |

## Deploy: GitHub + Cloudflare Pages

1. Create a GitHub repo and push this folder to it (`main` branch).
2. In the Cloudflare dashboard: **Workers & Pages → Create → Pages → Connect to Git**, pick the repo.
3. Build settings:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: `/`
4. Deploy. You get a `*.pages.dev` URL immediately.
5. **Custom domains** tab → add `offbookstudios.com` and `www.offbookstudios.com`. If the DNS zone is already on Cloudflare the records are created for you; `_redirects` sends www to the apex.

Every push to `main` redeploys automatically. Pull requests get preview URLs.

## Before going live

- Confirm the domain: `index.html`, `sitemap.xml`, `robots.txt`, and `_redirects` all assume `https://offbookstudios.com`. Search-and-replace if it's different.
- `info@offbookstudios.com` is used on the contact buttons and in the structured data — make sure the mailbox exists.
- Optional: submit `https://offbookstudios.com/sitemap.xml` in Google Search Console once the domain is live.

## Editing

Everything lives in `index.html`. Colors are CSS variables at the top of the `<style>` block (`--ink`, `--paper`, `--orange`). Copy is plain HTML in each `<section>`. The hero typing sequence reads its lines from the `data-text` attributes on the `#mantra` spans.
