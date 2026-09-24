# FEDUC Nepal

Website for the Foundation for Educational Change (FEDUC), a non-profit,
non-political institution in Nepal working in vocational training, teacher
training, education research, and community welfare.

Live domain: feducnepal.org

## Structure

- `index.html` — Home page
- `about.html` — Vision, mission, objectives, and experience history
- `contact.html` — Office address, phone, email, map, and contact form
- `thank-you.html` — Confirmation page shown after the contact form submits
- `css/style.css` — Shared stylesheet
- `js/script.js` — Mobile navigation toggle
- `assets/` — Site icons (favicon)
- `netlify.toml` — Netlify build/publish config and security headers

The contact form uses [Netlify Forms](https://docs.netlify.com/manage/forms/setup/)
(`data-netlify="true"` on the `<form>` in `contact.html`) — submissions land
in the Netlify dashboard under Forms, no backend required. This only works
once the site is deployed on Netlify; it does nothing on GitHub Pages or a
plain static host.

## Running locally

Static site, no build step required:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser. Note: Netlify Forms won't
capture submissions locally — that only works once deployed on Netlify.

## Deploying to Netlify (www.feducnepal.org)

1. Go to [app.netlify.com](https://app.netlify.com) and sign in with GitHub.
2. **Add new site → Import an existing project → GitHub** → select the
   `dhakalasim/feduc-nepal` repository.
3. Build settings: leave the build command empty and publish directory as
   `.` (already set in `netlify.toml`) → **Deploy site**.
4. Once it deploys to a `*.netlify.app` URL, confirm the site loads and the
   contact form appears under **Site configuration → Forms** after a test
   submission.
5. **Domain management → Add a domain** → enter `feducnepal.org`. Netlify
   will detect the apex + `www` and let you set `www.feducnepal.org` as the
   primary domain (with `feducnepal.org` redirecting to it).
6. At your domain registrar (wherever `feducnepal.org` is registered), add
   the DNS records Netlify shows on that screen — typically:
   - `CNAME` `www` → `<your-site-name>.netlify.app`
   - `A` `@` → the apex load-balancer IP Netlify displays (or delegate to
     Netlify DNS if you'd rather it manage the whole zone)
7. Wait for DNS to propagate (usually minutes, can take up to 24h), then in
   **Domain management → HTTPS**, click **Verify DNS configuration** →
   Netlify auto-provisions a free Let's Encrypt certificate.

Every push to `main` auto-deploys after this is connected.
