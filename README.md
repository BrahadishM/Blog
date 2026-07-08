# brahadish-site

Portfolio + blog, built as a plain Jekyll site so GitHub Pages builds it for
you automatically — no build step to run locally, no npm, nothing to install
unless you want to preview changes before pushing.

## What's here

```
_config.yml       site settings (title, links, etc.)
index.html        the portfolio homepage (profile, education, experience, projects, skills)
blog.html         the blog list page — pulls automatically from _posts/
_layouts/         page templates (default.html = shell, post.html = blog post page)
_posts/           one markdown file per blog post
assets/css/       all styling in one file, style.css
```

## Publishing it on GitHub Pages

1. Create a new repository on GitHub, e.g. `brahadish-site` (or `yourusername.github.io`
   if you want it at the root of your GitHub Pages domain).
2. Push everything in this folder to that repo:
   ```
   git init
   git add .
   git commit -m "initial site"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**, and under "Build and deployment"
   set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. GitHub will build the site with Jekyll automatically. Give it a minute or
   two, then your site will be live at:
   - `https://YOUR_USERNAME.github.io/YOUR_REPO/` (project repo), or
   - `https://YOUR_USERNAME.github.io/` (if the repo is named `YOUR_USERNAME.github.io`)
5. Open `_config.yml` and set `url` and `baseurl` to match whichever of the
   above applies — this fixes internal links and the RSS feed. For a project
   repo, `baseurl` should be `/YOUR_REPO`.

No Ruby or Jekyll installation is required to publish — GitHub Pages runs the
build for you. You only need Jekyll installed locally if you want to preview
changes before pushing (see below).

## Adding a new blog post

Add a new file to `_posts/` named `YYYY-MM-DD-a-short-title.md`, for example:

```
_posts/2026-08-02-first-week-with-cadence.md
```

With this at the top:

```markdown
---
title: "First week with Cadence"
tags: [vlsi, cadence]
---

Whatever you want to write, in normal markdown.
```

Commit and push — it appears on `/blog.html` automatically, newest first.
No other file needs to change.

## Editing the portfolio content

Everything on the homepage — education, experience, projects, skills — is
plain HTML in `index.html`, organized into `<section>` blocks with matching
IDs used by the nav (`#profile`, `#experience`, `#projects`, `#skills`,
`#contact`). Find the section, edit the text.

A few project cards have a `<div class="todo">` note where details were left
as placeholders (synthesis tool names, quantified results, etc.) — fill
those in and delete the `.todo` div once done.

## Previewing locally (optional)

If you have Ruby installed:

```
gem install bundler jekyll
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000`. Not required — pushing to GitHub is
enough to see changes live.
