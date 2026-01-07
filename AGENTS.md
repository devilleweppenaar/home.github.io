# AI agent guidelines

Guidelines for AI agents working on this personal website repository.

## Overview

- Personal site hosted on GitHub Pages with Cloudflare DNS
- Deployed automatically on commits to main branch
- Live site: https://devilleweppenaar.ca
- Minimal dependencies, Jekyll-based static site

## Commit conventions

- Lowercase, past tense, descriptive, under 50 characters
- No prefixes, no emojis
- All commits must be signed
- See CONTRIBUTING.md for examples

### Committing changes

**Always ask for permission before committing.** Do not automatically run `git commit` after making changes. Present the changes and ask if it's okay to commit them.

### Rebasing and commit organization

Rebasing is encouraged to organize commits into logical sets of changes. Prefer clear, well-organized commit history over chronological accuracy. Feel free to:
- Squash related changes into single commits
- Reorder commits to group related work
- Split commits that contain unrelated changes
- Rewrite commit messages for clarity

The goal is a readable history where each commit represents a logical unit of work.

## Performance requirements

**Maintain 100/100 PageSpeed Insights score** on both desktop and mobile.

- Test at: https://pagespeed.web.dev
- Test URL: https://devilleweppenaar.ca
- Prioritize: performance, accessibility, best practices, SEO

## Code style

### HTML/Markdown
- Semantic HTML elements
- Accessibility first: use `aria-label`, `role`, descriptive `alt` text
- Inline SVGs preferred over icon libraries
- Responsive images: WebP with JPEG fallback, 2x variants
- Use `fetchpriority="high"` for above-the-fold images
- Include `aspect-ratio` CSS to prevent layout shift

### CSS/SCSS
- Use CSS custom properties (variables) in `:root`
- Descriptive class names (kebab-case, no abbreviations)
- Add comments explaining non-obvious design decisions
- Focus states: explicit `outline` and `outline-offset`
- Smooth transitions with intentional durations
- Mobile-first responsive approach

### Accessibility checklist
- Descriptive alt text (detailed descriptions, not generic)
- Aria-labels on interactive elements
- Keyboard navigation support (`focus-visible`)
- Semantic HTML structure
- Sufficient color contrast

## Image optimization

- Format: WebP with JPEG fallback using `<picture>` element
- Resolution: provide 1x and 2x variants for Retina displays
- Location: `/assets/images/`
- Optimize file sizes before committing
- Test: images should load quickly and not impact PageSpeed score

## Jekyll/GitHub Pages compatibility

- Stick to Jekyll features supported by GitHub Pages
- Theme: `jekyll-theme-hacker`
- No custom plugins (GitHub Pages has limited plugin support)
- SCSS compilation handled automatically by Jekyll
- Test locally with `bundle exec jekyll serve` if making structural changes

## File organization

- Keep structure minimal and logical
- Assets organized by type: `/assets/css/`, `/assets/images/`
- No build tools beyond Jekyll
- Avoid creating unnecessary files or directories

## Privacy

- Avoid including email addresses in documentation or code comments
- Be mindful of what is committed to public repository
- Git commits use GitHub noreply email: `11049609+devilleweppenaar@users.noreply.github.com`
- Never commit personal email addresses in git history or file contents

## When in doubt

- Prioritize accessibility and performance
- Keep it simple and maintainable
- Follow existing patterns in the codebase
- Ask for clarification rather than assuming
