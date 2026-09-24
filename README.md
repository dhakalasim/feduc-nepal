# FEDUC Nepal

Website for the Foundation for Educational Change (FEDUC), a non-profit,
non-political institution in Nepal working in vocational training, teacher
training, education research, and community welfare.

Live domain: feducnepal.org

## Structure

- `index.html` — Home page
- `about.html` — Vision, mission, objectives, and experience history
- `contact.html` — Office address, phone, email, map, and contact form
- `css/style.css` — Shared stylesheet
- `js/script.js` — Mobile navigation toggle
- `assets/` — Site icons (favicon)
- `vercel.json` — Vercel security headers config

The contact form submits via `mailto:` — it opens the visitor's email
client addressed to feduc.ktm@gmail.com. This works on any static host
with no backend required.

## Running locally

Static site, no build step required:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser.

## Deploying to Vercel (www.feducnepal.org)

1. Go to [vercel.com](https://vercel.com) and sign in with GitHub.
2. **Add New → Project** → import the `dhakalasim/feduc-nepal` repository.
3. Framework preset: **Other** (no build command, no output directory
   override needed) → **Deploy**.
4. Once it deploys to a `*.vercel.app` URL, confirm the site loads and the
   contact form opens an email draft correctly.
5. **Project → Settings → Domains** → add `feducnepal.org` and
   `www.feducnepal.org`, setting `www.feducnepal.org` as the primary (Vercel
   will offer to redirect the apex to it).
6. At your domain registrar (wherever `feducnepal.org` is registered), add
   the DNS records Vercel shows on that screen — typically:
   - `CNAME` `www` → `cname.vercel-dns.com`
   - `A` `@` → `76.76.21.21` (or delegate to Vercel's nameservers if you'd
     rather it manage the whole zone)
7. Wait for DNS to propagate (usually minutes, can take up to 24h) — Vercel
   auto-provisions a free TLS certificate once it verifies.

Every push to `main` auto-deploys after this is connected. The CLI can also
deploy directly: `vercel --prod` from the repo root (requires `vercel login`
first).
