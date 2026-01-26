# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static marketing micro-site for "Ideal Customer Profile" - a single-page site about ICP frameworks for B2B SaaS founders. The site is deployed to Vercel.

## Architecture

- **Static HTML files**: Multiple pages (index.html, saas-marketing.html, calculators, etc.)
- **Build process**: Tailwind CLI compiles CSS from `src/input.css` to `dist/output.css`
- **Styling**: Tailwind CSS (built locally, ~22KB minified vs ~300KB CDN)
- **Fonts**: Google Fonts (Crimson Pro for headings, Inter for body text)

## Development

Install dependencies (first time only):
```bash
npm install
```

Build CSS and watch for changes:
```bash
npm run dev
```

Or build minified CSS for production:
```bash
npm run build
```

Run local server with live reload:
```bash
npm run serve
```

**Important**: Always run `npm run build` before committing if you've added new Tailwind classes.

## Deployment

Push to GitHub and the site auto-deploys via Vercel. Cache headers are configured in `vercel.json`.

## Article Date Updates

When creating or updating any article/page, always update these date fields:

1. **Schema markup `dateModified`** in each HTML file's JSON-LD (e.g., `"dateModified": "2026-01-26"`)
2. **Sitemap `<lastmod>`** in `sitemap.xml` for the corresponding URL
3. **`llms.txt` "Last Updated"** field at the top of the file

For new articles, also set `datePublished` in the schema markup.

## Key Components in index.html

- **Structured data/schema.org** (lines ~58-289): Article, VideoObject, WebApplication (calculator), FAQPage, HowTo schemas for SEO
- **Navigation**: Sticky header with logo and CTA (line ~311)
- **Mobile sticky bottom CTA bar** (line ~324): Fixed bottom bar visible only on mobile
- **Video facades**: Click-to-load YouTube embeds using `onclick` inline handlers (multiple sections)
- **Interactive "Bad ICP Calculator"** (lines ~544-595): Vanilla JS calculator with formatted number inputs
- **Table of Contents sidebar** (line ~351): Desktop-only with scroll-spy highlighting
- **Exit intent modal** (lines ~908-956): Shows on mouse leave (desktop only)

## LLM/SEO/AEO Reference

For guidance on LLM optimization, SEO, and Answer Engine Optimization, reference the expert agent at:

- **Strategies**: `~/projects/llm-seo-aeo-agent/strategies/`
  - `llm-optimization.md` - llms.txt, robots.txt, E-E-A-T signals
  - `seo-strategies.md` - Schema.org markup, meta tags, technical SEO
  - `aeo-strategies.md` - FAQ sections, glossaries, case studies for AI extraction

- **Templates**: `~/projects/llm-seo-aeo-agent/templates/`
  - `llms.txt.template` - Template for LLM discovery files
  - `schema-article.json` - Article + VideoObject schema
  - `schema-faq.json` - FAQPage schema
  - `robots.txt.template` - AI-friendly robots.txt

When working on SEO/AEO tasks, read the relevant strategy file first for best practices and implementation patterns.
