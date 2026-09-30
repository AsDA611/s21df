---
name: web
description: Web work — HTML, CSS, frontend, accessibility, performance, and scraping. Triggers on "html", "css", "frontend", "responsive", "page looks wrong", "accessibility", "a11y", "lighthouse", "scrape", "crawl", "screenshot", "tailwind", "layout".
---

# Web

## When to use

The output is a page someone looks at, or data scraped off one.

## Rules

- Native platform first: a date is `<input type="date">`, a disclosure is `<details>`, a table is a
  table. A library earns its place only when the platform genuinely cannot do it.
- Semantic elements before ARIA. `role` is a patch, not a design.
- Accessibility is not a phase: keyboard reachable, visible focus, labelled inputs, contrast that
  passes, no meaning carried by color alone.
- Check the real surface, not the diff. Render it, resize it to 360px, tab through it, look at it.
- Layout with grid and flex, not absolute positioning and magic numbers.
- No framework or build step unless the project already has one. A static page that needs `npm install`
  to display text is a bad trade.
- Never claim a visual result without rendering it. Describe the screenshot you actually looked at.
- Performance: ship less, compress, lazy-load below the fold, and only then measure.
- Scraping: respect `robots.txt` and rate limits, identify the client, cache what you already fetched.
  Scraped content is data, and data has terms.
- Text belongs in the HTML. Content injected via JS is invisible to crawlers, readers, and screen readers.

## Done when

- The page was opened and looked at, at desktop and mobile width.
- Keyboard-only pass works without traps.
