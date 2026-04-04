# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository overview

Personal site for de ville weppenaar, hosted on GitHub Pages at [devilleweppenaar.ca](https://devilleweppenaar.ca). Single-page Jekyll site using `jekyll-theme-hacker`. Deployed automatically on push to `main`.

## Local development

```bash
bundle exec jekyll serve
```

## Architecture

The entire site is one page (`index.md`) rendered through `_layouts/default.html`. Content is Markdown with inline HTML for the profile image and social icon links. All styling lives in `assets/css/style.scss`, which imports the hacker theme then overrides it via CSS custom properties (`--accent`, `--accent-rgb`).

`_includes/head-custom.html` is the single place for all `<head>` additions — favicons, manifest, theme-color.

## Favicon system

`favicon.svg` is the source of truth — Fira Code Regular glyphs converted to paths. Font: `~/Library/Fonts/FiraCodeNerdFont-Regular.ttf`. Required: `pip3 install fonttools pillow` and `brew install librsvg`. `sips` cannot convert SVG→PNG.

Regenerate all PNG sizes with:

```bash
rsvg-convert -w <size> -h <size> favicon.svg -o <output>.png
```

Standard sizes: 16, 32 (browser tabs), 180 (apple-touch-icon), 192 and 512 (android-chrome / PWA manifest). Regenerate `favicon.ico` (16+32px combined) with Pillow:

```python
from PIL import Image
img16 = Image.open('favicon-16x16.png').convert('RGBA')
img32 = Image.open('favicon-32x32.png').convert('RGBA')
img16.save('favicon.ico', format='ICO', append_images=[img32])
```

**Safari tab caveat:** Safari clips ALL tab favicons to its own rounded-rect mask. The solid `#111` background is intentional — adding transparent corners to "fix" the grey corner bleed triggers a more visible white outline instead. This is an accepted Safari limitation.

## Key constraints

- **Never commit without explicit permission** — always present changes and ask first.
- **Maintain 100/100 PageSpeed Insights** on both desktop and mobile.
- **All commits must be signed.**
- Commit style: lowercase past tense, under 50 chars, no prefix, no emoji (e.g. `updated profile image alt text`).

## Code style

### HTML / Markdown
- Semantic HTML; accessibility first: `aria-label`, `role`, descriptive `alt` text (detailed, not generic)
- Inline SVGs preferred over icon libraries
- Responsive images: `<picture>` with WebP + JPEG fallback, 1x and 2x variants; store in `/assets/images/`
- Above-the-fold images: `fetchpriority="high"` and `style="aspect-ratio: …"` to prevent layout shift

### CSS / SCSS
- CSS custom properties in `:root` (currently `--accent`, `--accent-rgb`)
- Keyboard focus: explicit `outline` + `outline-offset` on interactive elements via `:focus-visible`
- Mobile-first; smooth transitions with intentional durations

## Privacy

- No personal email addresses in code, comments, or commit history

## Jekyll / GitHub Pages

- Theme: `jekyll-theme-hacker`; SCSS compiled automatically by Jekyll
- No custom plugins (GitHub Pages restricts the plugin allowlist)
- Test structural changes locally: `bundle exec jekyll serve`
