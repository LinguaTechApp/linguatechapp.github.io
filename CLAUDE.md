# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static marketing website for **LinguaTech** (linguatech.app), promoting the **LinguaLoop** iOS language learning app. Built with Astro 5, deployed to GitHub Pages.

## Commands

```bash
npm run dev       # Dev server at localhost:4321
npm run build     # Production build to ./dist/
npm run preview   # Preview production build locally
```

Deployment is automatic via GitHub Actions on push to `main`.

## Architecture

- **Framework:** Astro 5 (static site generator) — sole dependency
- **Styling:** Scoped `<style>` blocks per component, no CSS framework, system fonts
- **JS:** Vanilla JavaScript only (mobile menu toggle, FAQ accordion)
- **TypeScript:** Strict mode via `astro/tsconfigs/strict`

### Layout

Single global layout at `src/layouts/Layout.astro` wraps all pages via `<slot />`. Contains:
- Sticky nav with responsive hamburger menu (breakpoint: 768px)
- Footer with legal links

### Routing

File-based routing in `src/pages/`:
- `/` — Home (index.astro)
- `/products` — LinguaLoop features + App Store link
- `/about` — Company info
- `/contact` — Contact info (contact@linguatech.app)
- `/lingualoop/privacy-policy` — Privacy policy
- `/lingualoop/terms-of-use` — Terms of service
- `/lingualoop/support` — FAQ accordion + support info

### Key Conventions

- All pages import and wrap content in `<Layout>` from `src/layouts/Layout.astro`
- No React/Vue/Svelte — pure `.astro` components only
- No `@apply` in CSS (per project cursor rules)
- Minimize client-side JavaScript; prefer static generation
- Color palette: background `#F3F4F9`, text `#111827`, accent `#3B82F6`
