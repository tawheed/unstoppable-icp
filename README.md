# Ideal Customer Profile Micro-Site

A marketing micro-site about TK Kader's Ideal Customer Profile (ICP) framework for B2B AI/SaaS founders.

**Live site:** https://www.idealcustomerprofile.com/

## Tech Stack

- Static HTML (single `index.html`)
- Tailwind CSS via CDN
- Vanilla JavaScript
- Google Fonts (Crimson Pro, Inter)

## Local Development

Run a local server with live reload:

```bash
npx browser-sync start --server --files "*.html"
```

This auto-opens the browser and refreshes when you save changes to `index.html`.

## Deployment

The site auto-deploys to Vercel on push to GitHub. Cache headers are configured in `vercel.json`.

## Project Structure

```
├── index.html      # All markup, styles, and scripts
├── vercel.json     # Vercel cache header configuration
├── CLAUDE.md       # AI assistant guidance
└── README.md
```
