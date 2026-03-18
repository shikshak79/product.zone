# Situation Library Card — Data Schema v1.0

Template: `situation-library-card-template.html`
Reference: `situation-library-card-pz-v1.html`
Canvas: 1200 × 1500px · Light register

---

## Purpose

Maps the commercial transitions a consultancy (or sales team) is built to solve,
scored by hunt priority. Used by scouts, partners, and internal teams to know
what to look for and how aggressively to pursue it.

---

## Data Structure

### Header

| Slot | Type | Required | Max Length | PZ Example |
|------|------|----------|------------|------------|
| `eyebrow` | string | yes | 60 chars | "Lead Qualification System · Layer 1" |
| `title` | string | yes | 40 chars | "Situation Library" |
| `subtitle` | string | yes | 200 chars | "13 commercial transitions PZ solves, scored by hunt priority..." |

### Legend Types

Array of 2–4 type definitions. Each type categorizes situations by root cause.

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `types[].code` | string | yes | "A" |
| `types[].label` | string | yes | "Decisions" |
| `types[].description` | string | yes | "Positioning/buying path decisions missing" |
| `types[].css_class` | string | yes | "a" (maps to badge color) |

**Design system note:** Three CSS classes are pre-defined: `a` (teal), `b` (orange), `c` (red).
Add more in the template CSS if needed. Maximum 4 types recommended for visual clarity.

### Tiers

Array of 2–4 tiers. Each tier groups situations by priority/confidence.

| Slot | Type | Required | Max Length | PZ Example |
|------|------|----------|------------|------------|
| `tiers[].badge_class` | string | yes | — | "t1" / "t2" / "t3" |
| `tiers[].label` | string | yes | 20 chars | "Tier 1" |
| `tiers[].title` | string | yes | 30 chars | "Active Hunt" |
| `tiers[].description` | string | yes | 120 chars | "Primary targets. Observable from outside. Highest conversion probability." |
| `tiers[].situations` | array | yes | 3–7 items | See Situation schema below |

**Badge classes:** `t1` (green), `t2` (orange), `t3` (red). Maps to tier severity/priority.

### Situations (within each tier)

| Slot | Type | Required | Max Length | PZ Example |
|------|------|----------|------------|------------|
| `situations[].num` | integer | yes | — | 1 |
| `situations[].name` | string | yes | 80 chars | "Hiring first commercial lead with no system to hand over" |
| `situations[].what` | string | yes | 120 chars | "About to bring someone in but the story still lives in founder's head" |
| `situations[].signals` | string[] | yes (2–4) | 60 chars each | ["AE / growth lead job post open", "Founder posting about 'scaling GTM'", "Homepage still vague despite hiring push"] |
| `situations[].type_code` | string | yes | — | "C — Transfer" |
| `situations[].loop_ref` | string | yes | 60 chars | "Land → Commit all founder-dependent" |
| `situations[].score` | integer | yes | 1–15 | 15 |
| `situations[].score_class` | string | yes | — | "high" / "mid" / "low" |

**Score class thresholds (default):**
- `high` (green): 13–15
- `mid` (orange): 10–12
- `low` (red): 1–9

These thresholds can be adjusted per client. Define them in the template config comment.

### Footer

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `brand_name` | string | yes | "Product.Zone" |
| `version_tag` | string | yes | "Situation Library v1.0 · March 2026" |

---

## Scoring Model

The score (1–15) represents hunt priority, not situation severity.
It combines three factors:

| Factor | Weight | What It Measures |
|--------|--------|------------------|
| Observability | High | Can a scout spot this from outside? |
| Conversion probability | High | Does this situation reliably convert to engagement? |
| Problem fit | Medium | How central is this to the consultancy's core offer? |

**Important:** The score is ordinal (ranking), not interval (measurable distance).
A score of 15 is not "3x better" than a score of 5. It means "pursue first."

---

## Capacity Constraints

The 1200×1500 canvas comfortably holds:
- 3 tiers
- 13 total situations (5 + 5 + 3 distribution)
- 2–3 signals per situation

If a client has more than 15 situations, either:
1. Increase canvas height (breaks LinkedIn format)
2. Split into two cards (Tier 1 card + Tier 2–3 card)
3. Reduce to top 13 and note the full list lives in Notion/docs

---

## Fill Sequence

When running a workshop or Sprint, populate in this order:

1. **Types first** — what are the root cause categories? (Usually maps to the consultancy's diagnostic framework)
2. **Situations next** — brainstorm all transitions the consultancy solves, unconstrained
3. **Tiers after** — sort by observability × conversion probability
4. **Scores last** — relative ranking within and across tiers
5. **Signals per situation** — what can a scout actually see from outside?
6. **Loop references** — where does each situation break in the buying/engagement path?

---

## Versioning

| Field | Convention |
|-------|-----------|
| Schema version | `schema.md` header (this file) |
| Template version | Comment in HTML file header |
| Reference version | Filename suffix: `-pz-v1.html` |
| Client versions | Filename: `situation-library-card-[client]-v[N].html` |
