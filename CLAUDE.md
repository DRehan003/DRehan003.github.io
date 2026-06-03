# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal portfolio website for Danyal Rehan, deployed via GitHub Pages at `www.danyalrehan.com`. Built on the [devportfolio-template](https://github.com/RyanFitzgerald/devportfolio-template) (v1.2.2). Static site — no backend, no framework, no build output needs to be deployed separately (GitHub Pages serves the repo root directly).

## Build Commands

```bash
# Install dependencies (first time)
npm install

# Watch for changes and auto-compile SCSS + JS
npm run watch

# Compile once manually
npx gulp styles    # scss/styles.scss → css/styles.css
npx gulp scripts   # js/scripts.js → js/scripts.min.js
```

**Important:** Never edit `css/styles.css` or `js/scripts.min.js` directly — they are compiled outputs. Edit `scss/styles.scss` and `js/scripts.js` instead.

## Architecture

- **`index.html`** — single-page portfolio with anchor-based navigation (`#about`, `#Certifications`, `#experience`, `#education`, `#projects`, `#skills`, `#contact`). All personal content (bio, experience, projects, skills) lives here.
- **Standalone project pages** — each project has its own HTML file (`chatbot_project_details.html`, `Tesla_GameStop.html`, `Cluster_Analysis_Webacy.html`, `correlation_analysis_webacy.html`, `Frequency_analysis_webacy.html`, `salary_city_comparison_dashboard_7.html`). These are linked from `#projects` in `index.html`.
- **`scss/styles.scss`** — all custom styles. Key SCSS variables at the top: `$base-color: #34a9db` (accent/link color), `$background-alt: #f2f2f5` (alternate section bg), `$heading: #374054`, `$text: #74808a`.
- **`js/scripts.js`** — jQuery-based interactivity (smooth scroll, sticky header, mobile menu, experience timeline animation via `js-scroll-trigger`).
- **`css/bootstrap.min.css`** and **`libs/font-awesome/`** — vendored third-party libraries, do not modify.
- **Contact form** — handled by [Formspree](https://formspree.io/f/xldgnkdw) (no server-side code needed).

## Writing Style

- **No dashes** of any kind (em dashes, en dashes, or hyphens used as dashes) in any written content. Replace with commas, periods, semicolons, or colons as appropriate.

## Adding Content

- **New project:** Add a `.project` div block in `index.html` under `#projects`, add a project image to `images/`, and optionally create a new standalone HTML page for details.
- **New section:** Add a `<div id="new-section">` in `index.html`, add a nav `<li>` in the `<header>`, and style in `scss/styles.scss` (then run `npx gulp styles`).
- **Inline styles** in `index.html` `<head>` override compiled styles for specific overrides — prefer `scss/styles.scss` for anything reusable.
