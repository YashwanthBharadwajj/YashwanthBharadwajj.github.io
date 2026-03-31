# Portfolio – CLAUDE.md

## Running locally

No build step. Open directly in a browser or serve with a simple HTTP server:

```bash
# Python
python -m http.server 8080
# Node
npx serve .
```

Then visit `http://localhost:8080/portfolio%20(2).html`.

## Architecture

Single file: `portfolio (2).html`
All CSS and JS are inline. No external dependencies except Google Fonts.

### Sections (in order)

| Section ID   | Content                        |
|--------------|--------------------------------|
| `#hero`      | Name, title, CTA buttons       |
| `#experience`| Work history (2 entries)       |
| `#projects`  | Project cards (4 entries)      |
| `#skills`    | Skill category cards (9 groups)|
| `#education` | Education cards (3 entries)    |
| `#contact`   | Contact links / social         |

Navigation links in the `<nav>` use `href="#<section-id>"` anchors; `html { scroll-behavior: smooth }` handles the scroll.

## Key JS patterns

**Scroll animations** – Elements start hidden via `.fade-in-up` (opacity 0, translateY 60px). An `IntersectionObserver` (threshold 0.1, rootMargin `-100px` bottom) adds `.visible` when they enter the viewport, triggering the CSS transition.

**Cursor trail** – `mousemove` listener creates a 5 px purple dot at the cursor position. Throttled to one dot per 50 ms (`trailDelay`). Each dot fades out and self-removes after 500 ms.

## Design tokens (CSS custom properties)

| Variable           | Value      | Role               |
|--------------------|------------|--------------------|
| `--bg-primary`     | `#050505`  | Page background    |
| `--bg-secondary`   | `#0d0d12`  | Alternate sections |
| `--bg-card`        | `#12121a`  | Card backgrounds   |
| `--accent-purple`  | `#a855f7`  | Primary accent     |
| `--accent-cyan`    | `#22d3ee`  | Secondary accent   |
| `--accent-pink`    | `#f472b6`  | Tertiary accent    |
| `--text-primary`   | `#ffffff`  | Body text          |
| `--text-secondary` | `#94a3b8`  | Subdued text       |
| `--text-muted`     | `#64748b`  | Placeholder/muted  |
| `--border-color`   | `#1e1e2e`  | Card borders       |

**Fonts:** `Outfit` (headings/body, weights 300–900) · `Fira Code` (monospace accents, weights 400–600)
