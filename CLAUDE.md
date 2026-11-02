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

**CSS is cached for a year.** Whenever `npm run build` changes `dist/output.css`, bump `?v=` on the stylesheet link on every page, or returning visitors keep the old styles.

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
- **Table of Contents sidebar** (line ~351): Desktop-only with scroll-spy highlighting
- **Exit intent modal** (lines ~908-956): Shows on mouse leave (desktop only)

## ICP Builder

Part 5 of `index.html` holds the free ICP Builder and the Google Doc template link. The builder runs entirely in the browser (localStorage only, no email, nothing sent anywhere). The Doc URL is in the `#template-doc` link.

## SEO Check-Ins

The site was rebuilt on 2026-11-02. Goal: place for "ideal customer profile" and win the template searches on the homepage.

**Schedule:** quick read Monday 2026-11-16, full review Monday 2026-11-30, second full review Monday 2026-12-28. Rankings take weeks to respond, so don't judge before 2026-11-30. Search Console data lags about 3 days.

**Pull the data** from `/Users/tk/projects/charlie`:

```bash
S=sc-domain:idealcustomerprofile.com
scripts/gsc.py inspect --site $S --url https://www.idealcustomerprofile.com/
scripts/gsc.py query --site $S --by date --days 90 --limit 100
scripts/gsc.py query --site $S --by page --days 28
scripts/gsc.py query --site $S --by query --country usa --term "ideal customer profile" --days 28
scripts/gsc.py query --site $S --by query --country usa --term "icp template" --days 28
```

**Baselines (before the rebuild):**

| Metric | Baseline |
|---|---|
| Monthly search clicks | Jul 190, Aug 176, Sep 159, Oct 79 (to Oct 30) |
| Homepage clicks and average position | Jul 161 at 7.4, Oct 60 at 10.9 |
| "ideal customer profile" (US) | Position 16.1 |
| "ideal customer profile template" (US) | Position 17.1 |
| "icp template" (US) | Position 9.2 |
| "cac payback formula" (US) | Position 4.5 |
| "tam sam som calculator" (US) | Position 17.7 |
| "b2b saas lead generation" (US) | Position 23.4 |
| Template-search clicks | About 50 in the 90 days to Oct 30 |
| "ideal customer profile" clicks | 14 in the 90 days to Oct 30 |
| Domain Rating | 11 (Ahrefs) |

US positions are for Sep 15 to Oct 30.

**What to look for:**

1. **Recrawl:** Google's `lastCrawlTime` for the homepage is after 2026-11-02. It was 2026-10-29 at launch, so nothing below counts until this happens.
2. **Trend:** did the slide since mid-September stop? Compare clicks and homepage position against the table.
3. **Template searches:** did clicks hold after the template table returned to Part 5 with the builder?
4. **"ideal customer profile":** is position moving toward page 1? Expect slow progress at DR 11. Links matter more than on-page changes here.
5. **On-page fixes:** did the CAC, TAM and LTV pages move? The LTV page now targets "customer lifetime value calculator" and "saas ltv calculator", not "ltv calculator", which means loan-to-value.
6. **Builder use (GA4):** `icp_builder_started`, `icp_builder_completed` and `icp_gtm_clicked`, split by `location`.
7. **Business result:** do GTM applications arrive from `utm_source=icp`? Confirm the tags survive from `getunstoppable.com` to the application. Compare Guide opt-ins too, since most Guide CTAs were removed.
8. **Removed URL:** `/ideal-customer-profile-template.html` returns a 404 by design. Ignore it in Search Console reports.

**How to respond:**

- **Clicks and positions still falling on 2026-11-30, with the page recrawled:** on-page work isn't the constraint. Prioritize backlinks and look into the mid-September drop.
- **Template clicks recovering:** add more ICP examples to the homepage, then consider retitling it to lead with "ideal customer profile".
- **Builder used but few GTM clicks:** the upsell or `getunstoppable.com` is the weak link, not SEO.
- **Don't** change dates without real content changes, or chase "saas marketing" (its results are DR 76 to 95) or "ltv calculator".

**Biggest lever outside the page:** links to the homepage from TK's YouTube video descriptions, `tkkader.com` and `getunstoppable.com`.

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
