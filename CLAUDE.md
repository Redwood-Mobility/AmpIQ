# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AmpIQ (ampiq.tech) is a single-page marketing website for an EV charging consulting firm. The entire site is a single `index.html` file with inline CSS and JS — no build tools, no frameworks, no dependencies.

## Development

```bash
npx serve .
# or
python3 -m http.server 8000
```

No build step. No `npm install`. Just serve the directory and open in a browser.

## Deployment

GitHub Pages, push to `main`. Custom domain mapped via `CNAME` file (`ampiq.tech`). Do not modify or delete the CNAME file.

## Architecture

Everything lives in `index.html`:

- **CSS** (~650 lines): All in a single `<style>` block. Uses CSS custom properties (`:root` vars) with a dual-surface system — dark sections use hardcoded navy values (constant in both modes), light sections use `--surface`/`--surface-card` vars that flip in dark mode. Responsive breakpoints at 1024px, 768px, and 480px.
- **HTML**: Alternating dark/light sections — hero (dark, gradient orbs + grid), services (light, 3-col grid), process (dark, 3x2 numbered cards), why (light, 2-col with gradient left borders), verticals (dark, dual-row marquee), about (light, 2-col), CTA (gradient bg), footer (dark).
- **JS** (~30 lines): Inline `<script>` at bottom. Handles copyright year, nav glassmorphic scroll effect, mobile fullscreen menu with hamburger→X animation, and IntersectionObserver scroll-reveal (`.reveal` → `.visible`).

## Design System

- **Colors**: Pink `#ED4E93`, Purple `#A855F7`, Blue `#3B82F6`, Navy `#070D1F`
- **Gradient**: `linear-gradient(135deg, var(--pink), var(--purple), var(--blue))` — used for buttons, icons, text highlights, CTA background, process numbers, and card accent borders
- **Typography**: Montserrat (display headings h1/h2, `--font-display`), Outfit (body/sub-headings, `--font-body`) via Google Fonts
- **Icons**: Inline SVGs from Heroicons (outline style, stroke-width 2)

## Key Patterns

- Dark/light alternation: sections alternate between dark navy and light surface backgrounds, creating visual rhythm without explicit dividers
- Dark mode flips only the light sections via `prefers-color-scheme: dark` overriding `--surface`, `--surface-card`, `--text-*`, `--border` vars. Dark sections stay unchanged.
- Hero atmosphere: animated gradient orbs (`filter: blur(120px)` with float keyframes) + subtle CSS grid pattern with radial mask
- Nav: always white text — transparent over dark hero, glassmorphic dark glass when scrolled (`backdrop-filter: blur(24px)`)
- Mobile menu: fullscreen overlay with hamburger→X transform animation
- Verticals section uses CSS-only marquee (two rows scrolling opposite directions, pauses on hover)
- Scroll animations use `.reveal` class + IntersectionObserver with CSS `transition-delay` for card staggering
- All CTAs link to `https://cal.com/zakwinnick/ampiq`
- `index-old.html` is a previous version kept for reference

## Assets

- `assets/ampiq-logo.png` — full wordmark
- `assets/ampiq-icon.png` — icon/mark only
