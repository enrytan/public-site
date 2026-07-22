# enrytan.dev — Personal Site

A single-page developer portfolio for **Enry Christanto** (Senior Full Stack Developer).
Static HTML/CSS, no build step, hosted on GitHub Pages at [enrytan.dev](https://enrytan.dev).

## Structure

```
.
├── index.html          # The site (all content + styles inline)
├── resume.pdf          # Résumé, linked from the hero "Download résumé" button
├── CNAME               # Custom domain for GitHub Pages (enrytan.dev)
├── .nojekyll           # Serve files as-is; skip Jekyll processing
└── design/
    └── Portfolio.dc.html   # Original design-tool source (reference only, not served)
```

## Local preview

No dependencies. Either open `index.html` directly, or serve it:

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Editing content

All copy lives directly in `index.html` (hero, about, principles, the three case
studies, experience timeline, education, skills, contact). Edit the markup and commit —
GitHub Pages redeploys automatically on push to `main`.

Design tokens (colors, fonts) are CSS custom properties in the `:root` block at the top
of the `<style>` section.

## Hosting

Served by **GitHub Pages** from the `main` branch. See [DEPLOY.md](DEPLOY.md) for the
one-time Pages + custom-domain (DNS) setup.
