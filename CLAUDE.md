# dftf-landing

## What This Is

The source for [dftf.io](https://dftf.io) — Zachary Fowler's personal site. Currently a static HTML/CSS/JS portfolio showcasing film editing, post production, and VFX credits. Deployed to Vercel.

The existing live site is a separate deployment (plain HTML, no git repo). This folder is the new version being built to replace it.

## Project Location

```
/Users/zachfowler/Documents/_CodingProjects/_Top Projects/dftf-landing/
```

## How to Run

No build step. Open directly in a browser:

```bash
open index.html
```

Or use a local server for accurate preview:

```bash
npx serve .
```

The Claude Code preview panel also renders the page live.

## How to Deploy

**Preview (review before going live):**
```bash
cd "/Users/zachfowler/Documents/_CodingProjects/_Top Projects/dftf-landing"
vercel deploy
```
Returns a unique preview URL like `dftf-landing-xyz.vercel.app`.

**Production (replace live dftf.io):**
```bash
vercel deploy --prod
```
Only do this after reviewing the preview URL.

## Architecture

**Stack:** Plain HTML + CSS + JS — no framework, no build step.

| File | Purpose |
|---|---|
| `index.html` | Main portfolio page — all styles and JS inline |
| `images/` | Local image assets (currently unused — posters load from IMDb CDN) |
| `.claude/settings.local.json` | Pre-approved Claude Code permissions |

## Design System

Matches the existing dftf.io aesthetic:

| Token | Value |
|---|---|
| `--warm` | `#e8a948` (gold accent) |
| `--darker` | `#111113` (card bg) |
| `--darkest` | `#0c0c0e` (page bg) |
| `--text` | `#e0ddd5` |
| `--text-dim` | `#5a5855` |
| Font (display) | Bebas Neue |
| Font (body) | IBM Plex Mono |

Background: layered radial gradient + SVG fractal noise grain + no vignette on this page.

## Poster Images

Movie posters load from Amazon's IMDb CDN. Pattern:

```
https://m.media-amazon.com/images/M/{BASE_ID}@._V1_QL75_UX500_.jpg
```

Extract `{BASE_ID}` from any IMDb page img src (the part before `@`), then append `@._V1_QL75_UX500_.jpg`.

If a poster fails to load, the card falls back to a CSS placeholder (dark gradient + gold initials). This is intentional and looks fine.

## Credits Data

All 18 credits from IMDb profile [nm9598594](https://www.imdb.com/name/nm9598594/), organized into three sections:

- **Editor** — 8 credits (2018–2025)
- **Editorial Department** — 7 credits (2019–2025), includes assistant editor and post production supervisor roles
- **Visual Effects** — 3 credits (2019–2024)

## Current Status

- Portfolio page complete with all 18 credits and real poster images
- Missing: door/entrance animation from original site
- Missing: Apps section (Workflow Brain, CompPilot, XML Converter, Change List)
- Future: migrate to React + Vite when those sections are added
