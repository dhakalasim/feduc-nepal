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

## Running locally

Static site, no build step required:

```
python3 -m http.server 8000
```

Then open http://localhost:8000 in a browser.

## Deploying

Point the `feducnepal.org` domain's hosting (e.g. Netlify, Vercel, GitHub
Pages, or any static host) at this repository's root directory.
