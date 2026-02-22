# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static website for the **Art of Academia Podcast** (https://artofacademia.com/), deployed via GitHub Pages. It is a minimal site — primarily a single homepage with a hero section, host bios, platform links, and an embedded Elfsight podcast player.

## Commands

```bash
# Install dependencies
bundle install

# Run local dev server (available at http://localhost:4000)
bundle exec jekyll serve

# Build static site to _site/
bundle exec jekyll build

# Validate Jekyll config and build
bundle exec jekyll doctor
```

There are no linting or test commands. The CI/CD pipeline (`.github/workflows/jekyll.yml`) runs `bundle exec jekyll build` and `bundle exec jekyll doctor` on every push to `master`.

## Architecture

- **`index.html`** — The entire site content lives here. Uses the `default` layout, contains the hero section, host links, platform icons, and Elfsight widget for the podcast episode list.
- **`_layouts/default.html`** — Single master layout; includes `head.html` and Bootstrap JS bundle via CDN.
- **`_includes/head.html`** — HTML `<head>`: Bootstrap CSS (CDN), Google Fonts (Roboto), `jekyll-seo-tag`, and custom stylesheet.
- **`_sass/main.scss`** — All custom styles. Dark theme (`#202020` background). Bootstrap 5.3.2 is loaded via CDN (not bundled).
- **`assets/css/styles.scss`** — SCSS entry point that imports `main.scss`.
- **`_config.yml`** — Site metadata (title, description, URL) and plugins (`jekyll-sitemap`, `jekyll-seo-tag`).

## Deployment

Pushes to `master` automatically trigger a GitHub Actions workflow that builds and deploys to GitHub Pages. No manual deploy step is needed.
