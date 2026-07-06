# AGENTS.md

This file provides guidance to Codex (Codex.ai/code) when working with code in this repository.

## Project Overview

This is a static academic homepage for Zhe Zhu, a Ph.D. student. It is a single-page portfolio website with no build tools, frameworks, or package managers — just plain HTML, CSS, and a small amount of vanilla JavaScript.

## No Build/Lint/Test Commands

There are no build, lint, or test commands. To preview the site, open `index.html` directly in a browser or use any static file server (e.g., `python3 -m http.server`).

## Architecture

The entire site lives in two files:

- **`index.html`** — All content and structure (617 lines). Layout uses nested HTML tables. The main sections are:
  - Hero/intro with photo, bio, and contact links (~lines 20–45)
  - News (~lines 48–61)
  - Publications with a JS toggle between "Selected" and "All" views (~lines 62–590)
  - Services/reviewing (~lines 592–610)

- **`stylesheet.css`** — All styles (331 lines), including CSS custom properties (defined on `:root`) for theming, hover effects, and a single responsive breakpoint at `860px`.

The only JavaScript on the page is an inline `showPublications(type)` function that toggles visibility between the `#selected-pubs` and `#all-pubs` sections.

## Assets

- `images/publication/` — Teaser images for each paper entry
- `images/selfie/` — Profile photo
- `images/favicon/` — Favicon assets in multiple sizes
- `data/CV_Zhe_Zhu.pdf` — Downloadable CV

## CSS Variables (Theming)

Colors and spacing are controlled via CSS custom properties on `:root` in `stylesheet.css`:
`--bg`, `--bg-soft`, `--text`, `--muted`, `--line`, `--accent`, `--accent-strong`, `--card`, `--radius`, `--shadow`

## Common Edit Locations in index.html

| Content | Approximate Lines |
|---|---|
| Bio / contact links | 25–45 |
| News items | 48–61 |
| Selected publications | 80–233 |
| All publications | 235–578 |
