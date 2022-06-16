+++
title = "Pages Setup"
date = 2022-06-14T23:03:20-04:00
weight = 3
chapter = true
pre = "<b>III. </b>"
+++

### GitHub Pages

# Setup Guide

## I.) use GitHub actions for build + deploy

We can configure a github actions workflow to build and deploy our site. Create a file named **.github/workflows/gh-pages.yaml** that looks something like this:

```yaml
name: github pages

on:
  push:
    branches:
      - main  # Set a branch to deploy
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v2
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive)
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          # extended: true

      - name: Build
        run: hugo --minify
        working-directory: ./web

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./web/public
```

Now, when we merge to **main**, a github action will be run that builds the hugo site in **_web/_** and deploys the dist files to a new branch, **gh-pages**

## II.) deploy site with GitHub

Now all we have to do is navigate to **settings** **->** **pages** and deploy our **gh-pages** branch from the **/(root)** dir. And that's it! Our page will automatically deploy to the corresponding URL. 

_for example:_ if we were working in a repo called **some-data-service**, our site would deploy at:

```string
https://weave-lab.github.io/some-data-service
```

