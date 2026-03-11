---
name: visual-system
description: Product.Zone visual design system for all HTML/SVG outputs. Use this skill BEFORE creating any visual deliverable including positioning cards, workshop cards, pitch slides, diagnostic results, or any HTML/SVG visual. Contains color tokens, font stack, typography scales, canvas sizes, register definitions, and copy-paste code snippets. Trigger whenever creating visuals for Product.Zone or client deliverables. Read this skill first, then apply the appropriate tokens.
---

# Product.Zone Visual System

Single source of truth for all visual outputs. Read before creating any HTML/SVG deliverable.

---

## Quick Start

Copy this into every HTML file:

```html
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  /* Light surfaces */
  --white: #FFFFFF;
  --light: #F5F4EF;
  --light2: #ECEAE3;
  --lborder: #D8D6CF;
  --ltext: #1a1a1a;
  --lmuted: #555555;
  --lmuted2: #888888;
  
  /* Accents */
  --teal: #33C4D9;
  --orange: #F5A623;
  --green: #2ECC71;
  --red: #C0392B;
  
  /* Dark surfaces */
  --black: #0a0a0a;
  --surface: #141414;
  --dtext: #F0EFE9;
  --dmuted: rgba(255,255,255,0.7);
  --dmuted2: rgba(255,255,255,0.4);
  --dborder: rgba(255,255,255,0.1);
  
  /* Fonts */
  --mono: 'Space Mono', monospace;
  --display: 'Barlow Condensed', sans-serif;
  --body: 'Barlow', sans-serif;
}
* { margin: 0; padding: 0; box-sizing: border-box; }
</style>
```

---

## Canvas Sizes

| Format | Dimensions | Use For |
|--------|------------|---------|
| Portrait Card | 1200 × 1500px | Positioning cards, workshop cards, wireframe templates, LinkedIn visuals |
| Landscape Slide | 1920 × 1080px | Pitch slides, presentation decks (16:9) |
| Square | 1080 × 1080px | Social posts, thumbnails |

**Default is 1200×1500 portrait.** Only use landscape for actual presentation slides.

---

## Registers

Two visual registers. Never mix in the same zone.

### Register 1: Editorial (Light)

Default for most content. Approachable, readable.

```css
.editorial {
  background: var(--light);
  color: var(--ltext);
}
.editorial .headline { color: var(--ltext); }
.editorial .muted { color: var(--lmuted); }
.editorial .accent { color: var(--teal); }
.editorial .emphasis { color: var(--orange); }
```

**Use for:** Workshop cards, positioning cards, wireframe annotations, body content.

### Register 2: Technical (Dark)

High-contrast for evidence, data, summaries.

```css
.technical {
  background: var(--black);
  color: var(--dtext);
}
.technical .headline { color: var(--white); }
.technical .muted { color: var(--dmuted); }
.technical .accent { color: var(--teal); }
.technical .emphasis { color: var(--orange); }
```

**Use for:** Rationale boxes, solution sections, proof/evidence sections, data matrices, footers.

---

## Color Tokens

### Primary Palette

| Token | Hex | Use |
|-------|-----|-----|
| `--teal` | #33C4D9 | Primary accent. Labels, section markers, structural elements, links |
| `--orange` | #F5A623 | Singular emphasis. Recommended items, warnings, annotations |
| `--green` | #2ECC71 | Success, chosen options, pros |
| `--red` | #C0392B | Errors, cons, anti-patterns |

### Light Surface Palette

| Token | Hex | Use |
|-------|-----|-----|
| `--white` | #FFFFFF | Card backgrounds, content boxes |
| `--light` | #F5F4EF | Canvas background, secondary surfaces |
| `--light2` | #ECEAE3 | Tertiary surfaces, image placeholders |
| `--lborder` | #D8D6CF | Borders, dividers |
| `--ltext` | #1a1a1a | Primary text |
| `--lmuted` | #555555 | Secondary text, descriptions |
| `--lmuted2` | #888888 | Tertiary text, labels |

### Dark Surface Palette

| Token | Hex | Use |
|-------|-----|-----|
| `--black` | #0a0a0a | Dark backgrounds |
| `--surface` | #141414 | Elevated dark surfaces |
| `--dtext` | #F0EFE9 | Primary text on dark |
| `--dmuted` | rgba(255,255,255,0.7) | Secondary text on dark |
| `--dmuted2` | rgba(255,255,255,0.4) | Tertiary text on dark |
| `--dborder` | rgba(255,255,255,0.1) | Borders on dark |

### Workshop Highlight Colors (Use Sparingly)

| Token | Hex | Use |
|-------|-----|-----|
| `--pink` | #E85A9C | Use case highlights |
| `--yellow` | #F9E79F | ICP column 1 |
| `--cyan` | #AED6F1 | ICP column 3 |
| `--purple` | #D7BDE2 | ICP column 5 |

---

## Typography

### Font Stack

| Font | Variable | Use |
|------|----------|-----|
| Space Mono | `--mono` | Labels, eyebrows, annotations, code, framework text, dimension numbers |
| Barlow Condensed | `--display` | Headlines, titles, section headers, large numbers |
| Barlow | `--body` | Body copy, descriptions, option text, rationale |

### Typography Scales by Card Type

#### Workshop Cards (Client-Facing)
Large, readable. Designed for presentation and handoff.

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Eyebrow | 12px | 400 | Space Mono |
| Title | 56-72px | 800 | Barlow Condensed |
| Statement | 32-38px | 400-600 | Barlow |
| Section header | 24px | 700 | Barlow |
| Body | 18-20px | 400 | Barlow |
| Label | 11-12px | 400 | Space Mono |

#### Decision Cards (Architecture)
Structured, scannable. For documenting choices.

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Eyebrow | 11-12px | 400 | Space Mono |
| Title | 42-64px | 800 | Barlow Condensed |
| Decision number | 64px | 800 | Barlow Condensed (teal) |
| Option header | 17px | 700 | Barlow |
| Option description | 15px | 400 | Barlow |
| Pros/Cons | 14px | 400 | Barlow |

#### Wireframe Cards (Templates)
Mixed scale. Slide preview + annotations.

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Card eyebrow | 11px | 400 | Space Mono |
| Card title | 36-42px | 800 | Barlow Condensed |
| Slide label | 9px | 400 | Space Mono |
| Slide headline | 18-22px | 700 | Barlow Condensed |
| Zone label | 7-8px | 400 | Space Mono |
| Annotation label | 9px | 400 | Space Mono (orange) |
| Annotation text | 11-12px | 400 | Barlow |

#### Dense Cards (Summary/Matrix)
Compressed for high information density.

| Element | Size | Weight | Font |
|---------|------|--------|------|
| Title | 42px | 800 | Barlow Condensed |
| ICP values | 13px | 400 | Barlow |
| Matrix cells | 11px | 400 | Barlow |
| Labels | 9px | 400 | Space Mono |

---

## Spacing

### Canvas Padding

| Card Type | Padding |
|-----------|---------|
| Standard | 80px |
| Dense | 48px |
| Wireframe | 48px |

### Section Gaps

| Context | Gap |
|---------|-----|
| Major sections | 32-48px |
| Card groups | 20-24px |
| List items | 10-16px |
| Inline elements | 8-12px |

### Border Radius

| Element | Radius |
|---------|--------|
| Cards/boxes | 6-8px |
| Chips/tags | 4px |
| Small elements | 2-3px |

---

## Common Patterns

### Eyebrow Label

```html
<div class="eyebrow">Workshop 1 · Messaging Spine</div>
```

```css
.eyebrow {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: var(--teal);
  margin-bottom: 16px;
}
```

### Section Box (Light)

```html
<div class="section-box">
  <div class="section-label">Section Label</div>
  <div class="section-content">Content here</div>
</div>
```

```css
.section-box {
  background: var(--white);
  border: 1px solid var(--lborder);
  border-radius: 8px;
  padding: 24px;
}
.section-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--lmuted2);
  margin-bottom: 12px;
}
```

### Rationale Box (Dark)

```html
<div class="rationale">
  <div class="rationale-label">Why This Works</div>
  <div class="rationale-text">Explanation here.</div>
</div>
```

```css
.rationale {
  background: var(--black);
  border-radius: 8px;
  padding: 24px;
}
.rationale-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--teal);
  margin-bottom: 12px;
}
.rationale-text {
  font-family: var(--body);
  font-size: 15px;
  line-height: 1.6;
  color: var(--dmuted);
}
.rationale-text strong {
  color: var(--dtext);
  font-weight: 600;
}
```

### Chosen/Locked Indicator

```html
<div class="option chosen">
  ...
</div>
```

```css
.option.chosen {
  border: 2px solid var(--green);
  background: rgba(46,204,113,0.04);
  position: relative;
}
.option.chosen::after {
  content: '✓ CHOSEN';
  position: absolute;
  top: 16px;
  right: 16px;
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.08em;
  color: var(--green);
  font-weight: 700;
}
```

### Left Border Accent

```css
.locked::before {
  content: '';
  position: absolute;
  left: -16px;
  top: 0;
  bottom: 0;
  width: 4px;
  background: var(--orange);
  border-radius: 2px;
}
```

### Pro/Con Icons

```html
<div class="pro"><span class="icon">✓</span> Benefit text</div>
<div class="con"><span class="icon">✕</span> Tradeoff text</div>
```

```css
.pro, .con { display: flex; align-items: center; gap: 8px; font-size: 14px; }
.pro { color: var(--green); }
.con { color: var(--orange); }
.icon {
  width: 16px;
  height: 16px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 10px;
  color: var(--white);
}
.pro .icon { background: var(--green); }
.con .icon { background: var(--orange); }
```

### Brand Strip

```html
<div class="brand">
  <span class="brand-name">Product.Zone</span>
  <span class="brand-tagline">Workshop Deliverable</span>
</div>
```

```css
.brand {
  margin-top: auto;
  padding-top: 24px;
  border-top: 1px solid var(--lborder);
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.brand-name {
  font-family: var(--mono);
  font-size: 12px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--lmuted2);
}
.brand-tagline {
  font-family: var(--mono);
  font-size: 11px;
  color: var(--lmuted2);
}
```

---

## Image Placeholders

For wireframes and templates:

```html
<div class="image-placeholder">
  <span class="placeholder-icon">◇</span>
  <span class="placeholder-text">[Screenshot: Description]</span>
</div>
```

```css
.image-placeholder {
  background: var(--light2);
  border-radius: 6px;
  height: 120px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 8px;
}
.placeholder-icon {
  font-size: 24px;
  color: var(--lmuted2);
}
.placeholder-text {
  font-family: var(--mono);
  font-size: 9px;
  color: var(--lmuted2);
  text-align: center;
}
```

---

## Zone Labels (Wireframes)

For placeholder content in templates:

```html
<div class="zone">
  <div class="zone-label">Headline Zone</div>
  <div class="zone-content">[Market reality that creates tension]</div>
</div>
```

```css
.zone {
  border: 2px dashed var(--lborder);
  border-radius: 4px;
  padding: 12px 16px;
}
.zone-label {
  font-family: var(--mono);
  font-size: 7px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  color: var(--lmuted2);
  margin-bottom: 4px;
}
.zone-content {
  font-family: var(--display);
  font-size: 18px;
  font-weight: 700;
  color: var(--lmuted);
}
```

---

## Anti-Patterns

**Never:**
- Mix registers in the same zone
- Use more than 2 accent colors per card
- Use em dashes (use commas or periods)
- Use "I help" in any headline
- Use decorative elements without purpose
- Add shadows or gradients (flat design only)

**Always:**
- Start with the appropriate canvas size
- Apply Register 1 or 2 consistently within zones
- Use teal for structure, orange for singular emphasis
- Keep labels uppercase, headlines sentence case
- Test at 100% zoom for screenshot accuracy

---

## Diagnostic Results Cards

For X-RAY and diagnostic outputs, use the same system with these additions:

### Score Indicators

```css
.score-high { color: var(--green); }
.score-medium { color: var(--orange); }
.score-low { color: var(--red); }

.score-badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 4px 10px;
  border-radius: 4px;
  font-family: var(--mono);
  font-size: 11px;
  font-weight: 700;
}
.score-badge.high { background: rgba(46,204,113,0.15); color: var(--green); }
.score-badge.medium { background: rgba(245,166,35,0.15); color: var(--orange); }
.score-badge.low { background: rgba(192,57,43,0.15); color: var(--red); }
```

### Diagnostic Table

```css
.diagnostic-table {
  width: 100%;
  border-collapse: collapse;
}
.diagnostic-table th {
  background: var(--black);
  color: var(--teal);
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 0.1em;
  text-transform: uppercase;
  padding: 12px 16px;
  text-align: left;
}
.diagnostic-table td {
  padding: 14px 16px;
  border-bottom: 1px solid var(--lborder);
  font-family: var(--body);
  font-size: 14px;
}
.diagnostic-table tr:nth-child(odd) { background: var(--light); }
.diagnostic-table tr:nth-child(even) { background: var(--white); }
```

---

## Output Instructions

1. Write HTML file to `/mnt/user-data/outputs/`
2. Use naming convention: `[type]-[name].html`
3. Present using `present_files` tool
4. Screenshot at 100% zoom, exact canvas dimensions
