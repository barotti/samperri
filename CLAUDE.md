# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static portfolio site for a photographer/videographer. No build tools, no package manager, no external dependencies — everything is self-contained in plain HTML files served directly via XAMPP.

## Development

Open files directly in a browser via XAMPP (`http://localhost/SAM/`) or by double-clicking the HTML file. There is no build step, no compilation, and no server-side logic.

## Architecture

Two standalone HTML files, each fully self-contained (styles and scripts embedded inline):

- `index.html` — Main portfolio with hash-anchor navigation, scroll-triggered section animations, and a CTA email link
- `portfolio_fotografo_scroll.html` — Scroll-based layout variant

### Styling conventions

- Apple-inspired aesthetic: SF Pro Display font stack, pure black (`#000`) background, gray accents (`#86868b`, `#f5f5f7`)
- All typography uses `clamp()` for fluid scaling — no breakpoint-based font overrides
- Layout via CSS Grid and Flexbox; no CSS framework
- Animations are CSS transitions (`transform` + `opacity`) triggered by an `IntersectionObserver` adding an `.in-view` class

### JavaScript conventions

- Vanilla JS only — no libraries or frameworks
- Animation entry point: `IntersectionObserver` watches `.animate-on-scroll` elements and toggles `.in-view`
- Hero entrance uses a `setTimeout` delay so it fires after page paint
- No module system; all script is in a single `<script>` block at the bottom of `<body>`
