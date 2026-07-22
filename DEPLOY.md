# Deploying to GitHub Pages with enrytan.dev

One-time setup. After this, every `git push` to `main` redeploys automatically.

## 1. Push the repo

```bash
git push -u origin main
```

Repo: https://github.com/enrytan/public-site

## 2. Enable GitHub Pages

1. Go to **Settings → Pages** in the `enrytan/public-site` repo.
2. Under **Build and deployment → Source**, choose **Deploy from a branch**.
3. Set **Branch** to `main` and folder to `/ (root)`. Save.
4. GitHub builds the site. The `CNAME` file already in the repo will auto-populate the
   **Custom domain** field as `enrytan.dev`.

## 3. Point DNS at GitHub Pages

At your domain registrar's DNS settings for `enrytan.dev`, add:

**Apex domain (`enrytan.dev`)** — four `A` records pointing to GitHub's Pages IPs:

```
A   @   185.199.108.153
A   @   185.199.109.153
A   @   185.199.110.153
A   @   185.199.111.153
```

(Optionally also add the matching `AAAA` records for IPv6:
`2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153`, `2606:50c0:8003::153`.)

**`www` subdomain (optional but recommended)** — a `CNAME` record:

```
CNAME   www   enrytan.github.io.
```

> Note: the `CNAME` *file* in this repo is what tells GitHub which domain to serve. The
> DNS `CNAME` *record* above is a separate thing that only applies to the `www` subdomain —
> the apex `enrytan.dev` must use `A`/`AAAA` records, not a CNAME.

## 4. Enable HTTPS

Back in **Settings → Pages**, once DNS has propagated (can take minutes to a few hours),
check **Enforce HTTPS**. GitHub provisions a free Let's Encrypt certificate automatically.

## Verifying

- `https://enrytan.dev` should serve the site.
- Check propagation with `nslookup enrytan.dev` — it should resolve to the `185.199.x.x` IPs.
