# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands
- No specific build steps required as this is a static HTML site
- Local server: `python -m http.server` or `npx serve`

## Lint/Test Commands
- HTML validation: `npx html-validate index.html`
- CSS validation: `npx stylelint "**/*.css"`
- Accessibility check: `npx pa11y index.html`

## Code Style Guidelines
- HTML: Use semantic HTML5 elements
- CSS: 
  - Follow existing CSS custom properties in :root
  - Tailwind CSS for styling via CDN (v2.2.19)
  - Custom styles for effects not easily achievable with Tailwind
- JavaScript:
  - Minimal vanilla JS only
  - Prefer arrow functions and ES6+ syntax
  - Use event delegation where appropriate
- Naming conventions:
  - CSS classes: kebab-case
  - JavaScript variables: camelCase
- Accessibility:
  - Maintain proper contrast ratios
  - Ensure all interactive elements are keyboard accessible
  - Use appropriate ARIA attributes when necessary