# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static marketing micro-site for "Ideal Customer Profile" - a single-page site about ICP frameworks for B2B SaaS founders. The site is deployed to Vercel.

## Architecture

- **Single HTML file**: `index.html` contains all markup, styles, and scripts
- **No build process**: Static HTML served directly
- **Styling**: Tailwind CSS via CDN (`cdn.tailwindcss.com`)
- **Fonts**: Google Fonts (Crimson Pro for headings, Inter for body text)
- **No package.json or dependencies**: Pure static site

## Development

Run a local server with live reload:

```bash
npx browser-sync start --server --files "*.html"
```

## Deployment

Push to GitHub and the site auto-deploys via Vercel. Cache headers are configured in `vercel.json`.

## Key Components in index.html

- Navigation with sticky header (line ~264)
- Mobile sticky bottom CTA bar (line ~277)
- Video facades with click-to-load YouTube embeds (multiple locations)
- Interactive "Bad ICP Calculator" with vanilla JS (line ~408)
- Exit intent modal (line ~637)
- Structured data/schema.org markup in `<head>` for SEO (line ~47)
