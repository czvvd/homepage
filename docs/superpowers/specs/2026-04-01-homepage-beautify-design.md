# Homepage Beautification Design Spec

## Summary

Comprehensive visual upgrade for Zhe Zhu's academic homepage. Retains existing HTML table layout structure, replaces the blue-teal color scheme with a purple-mint palette, adds colored left-border section identifiers, and refines typography, spacing, and card styles throughout.

## Design Decisions

| Decision | Choice |
|---|---|
| Overall style | Modern academic — refined, clean, professional |
| Layout direction | C: Keep left-right layout, add colored left-border identifiers |
| Color scheme | C: Cold purple + mint (`#6c5ce7` primary, `#00b894` accent) |
| Publication cards | A: Horizontal image+text (current layout, refined) |
| Animation | Near-zero — only subtle hover effects, no scroll animations |

## Color Palette

| Token | Value | Usage |
|---|---|---|
| `--bg` | `#f0f0f5` | Page background base |
| `--bg-soft` | `#f8f7fc` | Soft background variant |
| `--text` | `#1e1e2e` | Primary text |
| `--muted` | `#5e5e72` | Secondary/body text |
| `--line` | `#dddde5` | Borders, dividers |
| `--accent` | `#6c5ce7` | Links, primary accent, left borders |
| `--accent-strong` | `#5a4bd6` | Hover state for links |
| `--accent-secondary` | `#00b894` | Mint green — News border, gradient accent |
| `--card` | `#ffffff` | Card backgrounds |

Background gradient: replace blue/teal radial gradients with purple/mint variants:
- `radial-gradient(circle at 12% -8%, #e4dff8 0, transparent 44%)`
- `radial-gradient(circle at 88% 0%, #d4f5ee 0, transparent 40%)`

h2 underline gradient: `linear-gradient(90deg, #6c5ce7 0%, #00b894 100%)`

## Section-by-Section Changes

### Hero Section
- Keep left-text, right-photo layout
- Name stays center-aligned within the text column
- Card border-left: 3px solid `--accent`
- Background gradient: `linear-gradient(145deg, #ffffff 0%, #f9f8ff 100%)`
- Contact pill buttons: border color → `#d5d0f0`, background → `#f5f3ff`
- Email button: solid `--accent` background with white text (primary CTA)
- Photo border-radius stays 18px, border color → `--line`
- Photo box-shadow → purple-tinted: `rgba(60, 40, 100, 0.14)`

### News Section
- Card with left-border: 3px solid `--accent-secondary` (mint green)
- No other structural changes

### Publications Section
- Toggle buttons: active state → `linear-gradient(90deg, #6c5ce7, #5a4bd6)` with purple box-shadow
- Inactive: border `#d5d0f0`, background `#f5f3ff`, text `#5e5e72`

### Publication Cards (horizontal image+text)
- Paper title (`.papertitle`): color → `--accent`
- Links (Project Page / Code): styled as pill tags with `border: 1px solid #d5d0f0`, `border-radius: 99px`, `padding: 3px 10px`, `background: #f5f3ff`, `color: --accent`, `font-size: 14px`
- Card hover: `translateY(-1px)` + `box-shadow: 0 8px 18px rgba(60, 40, 100, 0.1)` (keep existing, just re-color shadow)
- Teaser image: border color → `#dddde5`
- Card border: `1px solid #dddde5`, border-radius stays 14px

### Services Section
- Card with left-border: 3px solid `--accent-secondary` (mint green)
- No structural changes

## Animation Policy
- Keep existing hover `translateY(-1px)` on publication cards
- Keep `transition` on links (color change) — reduce to `0.15s` for snappier feel
- Remove transition on publication card transform (instant response)
- No scroll-based animations
- No page load animations

## Additional Fixes
- Fix favicon link: `href="images/favicon/favicon.ico"` (currently points to `favicon-missing.ico`)
- Add simple footer: `© 2026 Zhe Zhu` centered, muted color

## Files Modified
- `stylesheet.css` — All color variables, section styles, card styles, button styles
- `index.html` — Fix favicon href, add footer element (minimal HTML changes)

## What Does NOT Change
- HTML table layout structure
- JavaScript `showPublications()` toggle logic
- All publication content, images, and links
- Responsive breakpoint at 860px (only re-color, not restructure)
- Font family (Lato)
