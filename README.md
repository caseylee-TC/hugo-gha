# Hugo GitHub Pages Scaffold

A minimal [Hugo](https://gohugo.io) site — sample pages, a small blog
section, and a live API reference page — that builds and deploys to
GitHub Pages automatically via GitHub Actions. No local Hugo install,
no Node, no build step to run yourself.

## What's inside

```
content/            Markdown pages (home, about, posts/, api.md)
layouts/            Minimal custom HTML templates — no external theme
static/css/         Site stylesheet
static/openapi/     Sample OpenAPI spec, rendered live on /api/ via Redoc (CDN)
.github/workflows/  hugo.yml — installs Hugo, builds, deploys to Pages
hugo.toml           Site config
```

The `/api/` page loads [Redoc](https://redocly.com/redoc) from a CDN
and points it at `static/openapi/openapi.yaml`, so the API reference
renders live in the browser — no build-time processing needed.

## 1. Push this to a new GitHub repo

From inside this folder:

```bash
git init
git add .
git commit -m "Initial Hugo scaffold"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

(Create `YOUR_REPO` on GitHub first — an empty repo, no README/license,
so the push above isn't rejected.)

## 2. Turn on GitHub Pages via Actions

In the repo on GitHub: **Settings → Pages → Build and deployment →
Source → GitHub Actions**. That's it — no branch to pick, no `gh-pages`
branch is created.

## 3. Watch it deploy

Go to the **Actions** tab. The `Build and deploy Hugo site to GitHub
Pages` workflow runs on every push to `main`. When it finishes, the
site is live at:

```
https://YOUR_USERNAME.github.io/YOUR_REPO/
```

(GitHub Actions' `configure-pages` step detects this URL automatically
and passes it to Hugo as `--baseURL`, so you don't need to hand-edit
`hugo.toml` for this to work — though it's worth updating the
`baseURL` placeholder there too, for clarity and for any local
preview.)

## Editing content

- New blog post → add a `.md` file under `content/posts/`
- New standalone page → add a `.md` file under `content/`
- Replace the sample API → edit `static/openapi/openapi.yaml`
  (must stay valid OpenAPI 3.x YAML or JSON)

Every push to `main` rebuilds and redeploys automatically.
