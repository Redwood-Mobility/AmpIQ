# Repository Guidelines

## Project Structure & Module Organization

This repository is a static marketing site with no build system. `index.html` is the primary source file and contains the HTML, inline CSS, and inline JavaScript. `assets/` stores shared brand images such as `ampiq-logo.png` and `ampiq-icon.png`. `index-old.html` is a legacy reference, not the active page. `CNAME` supports GitHub Pages and should not be removed or renamed.

## Build, Test, and Development Commands

There is no compile step or dependency install.

- `python3 -m http.server 8000` serves the site locally at `http://localhost:8000`.
- `npx serve .` is an alternative local static server if `serve` is available.

Open the site in a browser and test directly against `index.html`.

## Coding Style & Naming Conventions

Use 2-space indentation in HTML, CSS, and JavaScript to match the existing file. Keep markup semantic and prefer descriptive, kebab-case class names such as `hero-inner` or `nav-links`. Reuse the CSS custom properties in `:root` before introducing new colors or spacing values. Preserve the current single-file architecture unless a change clearly justifies restructuring. When updating visuals, maintain the existing dark/light section rhythm and responsive breakpoints at `1024px`, `768px`, and `480px`.

## Testing Guidelines

This project does not include an automated test suite. Validate changes manually in current desktop and mobile browser widths. At minimum, verify navigation scroll behavior, the mobile menu toggle, external CTA links, image loading from `assets/`, dark-mode appearance, and scroll-reveal animations. If content or layout changes, compare against the live design intent rather than only checking for broken markup.

## Commit & Pull Request Guidelines

Recent history uses short, title-case commit messages such as `Font Update`, `Refresh`, and `Year Update`. Follow that pattern for focused content or styling changes. Pull requests should include a brief summary, note any manual browser checks performed, and attach before/after screenshots for visible UI updates. Link related issues when applicable and call out any change that affects deployment or the custom domain.
