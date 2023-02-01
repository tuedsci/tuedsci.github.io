---
title: Deploy a Hugo website as a GitHub page
date: 2022-10-20
---

This post summarizes the key steps to create and deploy a Hugo website as a (
free) GitHub page. For the detail instructions, please visit the suggested
links
or Google accordingly.

<!--more-->

## Create a website

I assume that you already created a deployable Hugo website on your local machine. If not, please visit the Hugo website and follow the [instructions here](https://gohugo.io/getting-started/quick-start/).
Basically, you need to follow the steps below.

Step 1: install Hugo

Step 2: create a website

```bash
hugo new site <website-directory>
```

Step 3: add a theme

Step 4: add some contents

Step 5: take a look that your site (locally)

```bash
cd <website-directory>
hugo server -D
```

Step 6: customize your theme

## Create a GitHub repo

After you feel satisfied with the look of your website (hopefully), the next step is to push the code to a remote repo on GitHub. Just follow the steps below.

Step 1: register for a GitHub account (if you haven't had one yet)

Step 2: create a repo for your website, and repo name should
be `<username>.github.io`

## Sync the local and remote repos

Step 1: make your `<website-directory>` a local Git repo

```bash
git init
git add .
git commit -m "Initial commit"
```

Step 2: sync the local and remote repos

```bash
git remote add origin <link-to-remote-repo>
git push -U origin main
```

## Build Hugo with GitHub actions

Step 1: create the following file `.github/workflows/gh-pages.yml`

Step 2: paste the code for `actions-hugo` into the newly created file

It should look like the snippet below, but please check out Hugo's official guideline [here](https://gohugo.io/hosting-and-deployment/hosting-on-github/) for the most updated content.

```yaml
# .github/workflows/gh-pages.yml
name: github pages

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  deploy:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
        with:
          submodules: true
          fetch-depth: 0

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: "latest"
          # extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        if: github.ref == 'refs/heads/main'
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

Step 3: commit and push the changes

Step 4: wait for about 1 minute for the build to be completed

## Finalization

After the build is completed, go to your GitHub account and follow the steps below.

Step 1: go to the repo for your website, i.e., `<username>.github.io`

Step 2: go to `Settings > Pages`

Step 3: on the section `Build and deployment > Branch`, select `gh-pages` (instead of `main`) and save

Step 4: your website should be ready at `https://<username>.github.io`
