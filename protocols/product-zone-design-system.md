# Product.Zone Design System
## Reference Document — February 2026

**Source of truth:** The live Framer homepage at product.zone is the canonical design reference.
All HTML prototypes (xray-landing-v12, partners-v2) are secondary implementations and contain
a known hierarchy inversion — they use dark-first / orange-primary, which is the opposite of
the homepage. Any new page should follow the homepage, not the prototypes.

**The correct hierarchy:**
- Light mode is primary
- Teal (#33C4D9) is the primary brand accent
- Amber/orange is secondary — used for emphasis, pricing, urgency
- Dark sections are used sparingly for contrast and impact, not as the default

---

## 1. Tokens

### Color

```css
:root {
  /* PRIMARY — Light surfaces */
  --white:    #FFFFFF;          /* Page background */
  --light:    #F5F4EF;          /* Warm off-white sections */
  --light2:   #ECEAE3;          /* Alternating card background */
  --lborder:  #D8D6CF;          /* Borders on light sections */
  --ltext:    #1a1a1a;          /* Primary text on light */
  --lmuted:   #555555;          /* Body text on light */
  --lmuted2:  #888888;          /* Labels, captions, timestamps */

  /* PRIMARY ACCENT — Teal */
  --teal:     #33C4D9;          /* Primary CTAs, links, highlights */
  /* Teal is the brand color. It leads. */

  /* SECONDARY ACCENT — Amber/Orange */
  --orange:   #F5A623;          /* Prices, urgency signals, secondary emphasis */
  /* Amber is used for commercial signals (price, offer) and emphasis moments.
     Not the primary color. */

  /* DARK — Used sparingly for contrast sections */
  --black:    #0a0a0a;          /* Dark section backgrounds */
  --dark:     #111111;          /* Slightly lighter dark */
  --surface:  #141414;          /* Cards on dark sections */
  --border:   #2a2a2a;          /* Borders on dark sections */
  --white-text: #F0EFE9;        /* Primary text on dark sections */

  /* STATUS INDICATORS — Fixed meaning, never decorative */
  --green:    #7ED49A;          /* CLEAR — positive/resolved */
  --yellow:   #E8C85A;          /* FUZZY — uncertain/partial */
  --red:      #FF6B6B;          /* MISSING — broken/absent */
}
```

**Hierarchy rules:**
1. Default to light backgrounds. Most sections are white or off-white.
2. Teal for primary actions, links, active states, and brand moments.
3. Amber for prices, offer callouts, urgency. Secondary use only.
4. Dark sections are deliberate contrast moments — problem sections, heavy emphasis, final CTAs. Not the default mode.
5. Green / Yellow / Red are status tokens only. Never used for general decoration.

**On teal vs amber:**
- Teal = the brand color. It signals "this is what Product.Zone does."
- Amber = the commercial signal. It says "this is what it costs / this is urgent."
- When both appear on the same page, teal wins for navigation and CTAs. Amber is secondary.

---

### Typography

```css
:root {
  --mono:    'Space Mono', monospace;         /* Labels, eyebrows, metadata, nav */
  --display: 'Barlow Condensed', sans-serif;  /* Headlines */
  --body:    'Barlow', sans-serif;            /* Body copy */
}
```

**Google Fonts import:**
```
https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap
```

**Observed from live homepage:**

The homepage uses a mixed-case headline style, not pure uppercase. The H1 reads:
> "You have a working product. Buyers still don't fully get it."

This is sentence-case, conversational, direct. The sub-headline switches register:
> "WE FIX THAT SO prospects start saying yes"

Mixed caps is used for emphasis within headlines — not consistent all-caps throughout.

**Font roles:**

| Font | Used for | Notes |
|------|----------|-------|
| Space Mono | Labels, eyebrows, code snippets, numbered steps, nav links, footer | Always uppercase, tracked |
| Barlow Condensed | Section headlines, large numbers, proof stats | Mixed-case or uppercase depending on context |
| Barlow | Body paragraphs, card descriptions, UI text | Normal sentence case |

---

### Type Scale

```css
/* Display headlines — Barlow Condensed */
h1 { font-size: clamp(36px, 6vw, 64px); line-height: 1.05; font-weight: 700; }
h2 { font-size: clamp(28px, 4.5vw, 48px); line-height: 1.1; font-weight: 700; }

/* Section labels — Space Mono */
.label { font-size: 11–13px; letter-spacing: 0.08–0.12em; text-transform: uppercase; color: var(--lmuted2); }

/* Body */
.body-lg { font-size: 17–18px; line-height: 1.75; font-family: var(--body); }
.body-md { font-size: 15px; line-height: 1.7; }
.body-sm { font-size: 13px; line-height: 1.6; }
```

**Headline tone from homepage:**
- H1 is conversational and direct. Addresses "you" specifically.
- Section H2s are declarative statements, not questions.
- Some headlines use a register shift mid-sentence: lowercase then uppercase, or normal case then all-caps for the emphasis phrase. This is intentional.

---

## 2. Layout

### Container

```css
.wrap { max-width: 960px; margin: 0 auto; padding: 0 clamp(20px, 5vw, 48px); }
```

### Section Rhythm

Light sections are the default. Dark sections break the rhythm deliberately.

**Homepage section pattern (observed):**

```
Light   — Hero: H1 + primary CTA
Light   — Familiar pain: numbered situations
Light   — Root cause: editorial section with image
Light   — Two-step offer: X-RAY then Sprint
Light   — How it works: steps 01, 02, 03
Light   — Who built it: founder credibility
Light   — Social proof: testimonials
Light   — Final CTA
```

The homepage is almost entirely light. Dark is a choice made for HTML prototypes to add visual weight — but the brand identity reads as light, clean, editorial.

**For HTML pages (sales pages, partner pages):**
- Use light as the dominant mode.
- Allow 1–2 dark sections for contrast and emphasis (typically the hero and final CTA).
- Do not default to dark-everything the way the v12 prototype did.

---

## 3. Navigation

From the live homepage:
- Logo: Product.Zone wordmark image (Framer-hosted)
- Links: Sales X-RAY, Sales Foundation, Thinking, FAQ
- CTA: "Start with the X-Ray ➜" — this is the primary nav CTA

**CTA arrow style:** `➜` (filled arrow, not `→`)

**Notes:**
- The nav CTA likely uses teal background or teal text, not amber — consistent with teal-primary hierarchy.
- Nav links are plain text, not uppercase monospace — more editorial, less technical.

---

## 4. Buttons

**From homepage:**
- Primary: `"Start with the X-RAY ➜"` — teal background or teal text
- Secondary: `"Book intro call ➜"` — ghost/outline or plain text link

**Hierarchy:**
1. Teal filled = primary conversion action
2. Text link with ➜ = secondary action (call booking, secondary page)
3. Amber is used for pricing CTAs on offer pages: `"Run the X-RAY · €3.000 ➜"`

**Arrow convention:** Always `➜` on the homepage. The HTML prototypes use `→` — this should be harmonised to `➜` on any page meant to match the Framer site.

---

## 5. Section Labels

From the homepage, section labels appear as:
- "Does This Sound Familiar" — plain text, slightly muted
- "HOW TO START" — uppercase, monospace style
- "How it works" — mixed case, editorial
- "WHO DOES THIS" — uppercase
- "What founders say" — rendered in backtick/code style: `` `What founders say` ``

The label style is flexible — the homepage mixes conventions. The consistent element is that every section has a label that names its purpose in plain language before the content starts.

---

## 6. Copy Conventions

These are extracted directly from the live homepage and represent the canonical voice.

**Headline pattern (from H1):**
> "You have a working product. Buyers still don't fully get it."

Direct address ("you"). Present tense. Names the situation precisely. No hyperbole.

**Sub-headline pattern:**
> "WE FIX THAT SO prospects start saying yes"

Uppercase emphasis on the action ("WE FIX THAT"), then lowercase continuation. Creates a rhythm of emphasis → explanation.

**Body copy pattern (from "How it works"):**
> "We assess your company the way a buyer would - not the way you'd explain it internally."

Short sentences. Plain English. The contrast structure ("X - not Y") is used frequently and effectively. ESL-safe — no idioms, no jargon without context.

**CTA copy pattern:**
- `"Run the X-RAY · €3.000 ➜"` — action + price in one line, no separate price callout needed
- `"Book a call first"` — secondary, no arrow, no price, lower commitment signal

**Social proof pattern:**
> "We explain the product every time again." → 15 questions answered and agreed - team-wide.

Before in italics as a quote. After in plain text with result number leading. Arrow `→` as the transition. Attribution always: Name, Title, Company.

**Closing H1 pattern:**
> "You've been building long enough to know something is leaking."

Returns to direct address. Assumes the reader has been thinking about this problem — not explaining it from scratch. Elevates the reader's own intelligence.

---

## 7. Known Inconsistencies

**Inconsistency 1: Dark-first HTML prototypes**
The X-RAY landing page (v12) and partners page (v2) were built dark-first with orange as primary.
This is a prototype decision that doesn't match the homepage hierarchy.
Fix: rebuild or update these pages to be light-dominant, teal-primary, matching the homepage.
Or: treat them as a deliberately distinct design register (more technical, more urgent) for the specific sales context.
Decide which before publishing more pages.

**Inconsistency 2: Font stack on partners page**
The original partners.html draft used Inter, not Barlow/Space Mono.
This is clearly wrong regardless of the light/dark question.
Fix: replace Inter with the canonical font stack.

**Inconsistency 3: Arrow style**
Homepage uses `➜`. HTML prototypes use `→`.
Fix: standardise to `➜` on all external-facing pages.

**Inconsistency 4: CTA color**
Homepage CTAs appear to use teal. Prototype CTAs use orange.
Fix: teal for all primary CTAs. Orange reserved for price display and urgency signals.

---

## 8. The Two Registers

The design system in practice operates in two registers. Both are valid — but they need to be chosen deliberately for each page, not mixed accidentally.

**Register 1: Editorial / Homepage**
- Light dominant
- Teal primary
- Mixed-case headlines
- Conversational copy ("you have a working product")
- Clean, spacious, confident
- Audience: cold traffic, founders discovering Product.Zone for the first time

**Register 2: Technical / Diagnostic**
- Dark dominant
- Orange/amber accents
- All-caps display headlines
- Space Mono structural elements (timelines, scorecards, status tokens)
- Dense, precise, evidence-forward
- Audience: warm traffic — someone who already understands what the X-RAY is, making a purchase decision

The homepage is Register 1. The X-RAY landing page prototypes are Register 2.
The partners page should be Register 1 (outbound agency owners are cold traffic discovering Product.Zone).

---

## 9. Section Architecture

**Standard light-mode sales page (Register 1):**

| Section | Purpose |
|---------|---------|
| Hero | Direct address. Name the situation. One primary CTA. |
| Familiar situations | Numbered. Reader recognises themselves. |
| Root cause reframe | "These aren't X problems. They're Y problems." |
| Two-step offer | Diagnosis first, sprint second. Clear separation. |
| How it works | 3 steps, plain language, outside-in framing. |
| Who built this | Founder credibility. Specific numbers. |
| Social proof | 2–3 client stories. Before → after format. |
| Final CTA | Returns to direct address. Price visible. |

**For dark-mode diagnostic pages (Register 2 — e.g. X-RAY detail page):**
- Zone scorecard display
- Timeline / day grid
- Evidence trail components
- Portfolio comparison table
- These require the darker, denser treatment

---

## 10. Assets

**Logo:** `https://framerusercontent.com/images/Kol567fc7ySfnqjnHG3ZxNDuzBA.png`
Wordmark only. Used in nav and footer.

**OG Image:** Hosted in Framer. Black background, teal eyebrow, white/orange headline.
For new pages: request from Framer or re-generate matching the same template.

**Email:** `hi@product.zone`
**Booking link:** `https://calendar.notion.so/meet/thorstenlampe/30`
**Legal:** `© 2026 Make A Difference Ventures B.V. · KVK: 84021101 · Amsterdam`
**Tagline:** `See it. Fix it. Own it.`

---

*Source: product.zone live homepage, xray-landing-v12.html, partners-v2.html*
*Corrected February 2026 — homepage is primary reference, HTML prototypes are secondary*
