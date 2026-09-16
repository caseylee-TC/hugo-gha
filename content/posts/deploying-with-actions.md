---
title: "Deploying with GitHub Actions"
date: 2026-09-17
summary: "How the build-and-deploy pipeline in this scaffold works."
---

On every push to `main`, the workflow in
`.github/workflows/hugo.yml` does three things:

1. Checks out the repo and installs the Hugo **extended** binary
2. Runs `hugo --minify` to build the static site into `public/`
3. Uploads `public/` as a Pages artifact and deploys it with
   GitHub's official Pages deploy action

No Node, no local build step, no committed `public/` folder — the
built site never touches your git history.
