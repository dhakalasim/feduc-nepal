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

## Deployment status

Live in production on Vercel: **https://feduc-nepal.vercel.app**
(project `asim-dhakals-projects/feduc-nepal`).

`feducnepal.org` and `www.feducnepal.org` are already added to the Vercel
project but **not yet resolving** — add these records at your domain
registrar (wherever `feducnepal.org` is registered) to finish the cutover:

| Type | Host | Value |
|------|------|-------|
| A    | `@`  | `76.76.21.21` |
| A    | `www`| `76.76.21.21` |

(Alternative: point the domain's nameservers at `ns1.vercel-dns.com` and
`ns2.vercel-dns.com` to let Vercel manage the whole DNS zone instead of
individual records.) Vercel auto-provisions a free TLS certificate once it
verifies the records — check status with `vercel domains inspect
feducnepal.org`.

**GitHub auto-deploy is not yet connected** — `vercel git connect` failed
because the Vercel GitHub App isn't authorized for this repo yet. To fix:
go to [vercel.com/dashboard](https://vercel.com/dashboard) → the
`feduc-nepal` project → Settings → Git → Connect, and authorize/select the
`dhakalasim/feduc-nepal` repository (or check
[github.com/settings/installations](https://github.com/settings/installations)
to confirm the Vercel app has access to this repo). Until that's connected,
deploy manually after pushing:

```
vercel --prod
```

from the repo root (requires `vercel login` once).
