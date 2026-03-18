# Decision Ledger Kanban — Data Schema v1.0

Template: `decision-ledger-kanban-template.html`
Reference: `decision-ledger-kanban-pz-v1.1.html`
Canvas: 2400px+ wide (scrollable) · Mixed register (light board, dark summary column)

---

## Purpose

Visual kanban showing every commercial decision a business has made (or needs to make),
organized by decision path and sorted by leverage within each column.
Used as a handoff artifact at Sprint completion and as an ongoing alignment tool.

The board answers: "What have we decided, how confident are we, and what's still open?"

---

## Data Structure

### Header

| Slot | Type | Required | Max Length | PZ Example |
|------|------|----------|------------|------------|
| `header.eyebrow` | string | yes | 80 chars | "Product.Zone · Commercial Decision Ledger · March 2026" |
| `header.title` | string | yes | 60 chars | "34 decisions locked." |
| `header.subtitle` | string | yes | 200 chars | "Full architecture: Buying Path (A–D) · Usage (E) · Business (F) · Investment (G) · Channel." |

### Legend

Fixed set of 4 status types. Colors are locked in CSS.

| Status | CSS Class | Color | Meaning |
|--------|-----------|-------|---------|
| Locked | `locked` / `ds-locked` | green | Decision is final. Change requires deliberate revisit. |
| Validated | `validated` / `ds-validated` | teal | Tested with evidence but not yet irreversible. |
| Future Stage | `future` / `ds-future` | purple | Identified but not yet actionable. Placeholder. |
| Open / Pending | `open-item` / `ds-open` | orange | Needs resolution. Blocking or important. |

### Columns

Array of 5–6 columns. The last column is always the dark summary column.

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `columns[].accent_color` | CSS var | yes | `var(--teal)` |
| `columns[].eyebrow` | string | yes | "Layer 1 · Lock First" |
| `columns[].title` | string (HTML, `<br>` allowed) | yes | "North Star<br>+ Positioning" |
| `columns[].count` | string | yes | "1 north star · 9 decisions · A0–A8" |
| `columns[].sections` | array | yes | See Section schema |

### Sections (within each column)

Sections group decisions within a column. A column can have 1–3 sections.

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `sections[].label` | string | no (first section often unlabelled) | "Movement — Type C" |
| `sections[].cards` | array | yes | See Card schema |

### Decision Cards

| Slot | Type | Required | Max Length | PZ Example |
|------|------|----------|------------|------------|
| `cards[].type` | enum | yes | — | `"standard"` / `"north_star"` |
| `cards[].status` | enum | yes | — | `"locked"` / `"validated"` / `"future"` / `"open"` |
| `cards[].leverage` | integer | yes | 1–5 | 4 (renders as 4 filled + 1 empty dot) |
| `cards[].code` | string | yes | 6 chars | "A0" |
| `cards[].name` | string | yes | 60 chars | "Client-Side JTBD" |
| `cards[].answer` | string | yes | 120 chars | "T2 primary: 'Enable others to carry the story without me explaining it every time.'" |
| `cards[].detail` | string | yes | 250 chars | "T1 (make first sales work) + T3 (scale beyond founder) are secondary..." |

**North Star card** uses the same fields but renders with dark background and orange eyebrow.
It has an additional field:

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `cards[].ns_eyebrow` | string | only for north_star | "North Star JTBD" |
| `cards[].ns_status_label` | string | only for north_star | "Strategic" |

### Summary Column (always last, dark register)

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `summary.eyebrow` | string | yes | "Session · March 2026" |
| `summary.title` | string | yes | "What This<br>Session Locked" |

#### Stats Grid (2×2)

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `summary.stats[]` | array of 4 | yes | — |
| `summary.stats[].value` | string | yes | "34" |
| `summary.stats[].label` | string | yes | "Decisions mapped" |
| `summary.stats[].color` | CSS var | yes | `var(--green)` |

#### Summary Sections

Repeating blocks with bullet items. Each section has:

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `summary.sections[].label` | string | yes | "What this session unlocked" |
| `summary.sections[].items[]` | array | yes | — |
| `summary.sections[].items[].bullet` | string | yes | "✓" or "!" or "→" |
| `summary.sections[].items[].bullet_class` | string | yes | `""` (green default) or `"arrow"` (orange) |
| `summary.sections[].items[].text` | string (HTML, `<strong>` allowed) | yes | "<strong>Full 4-path architecture:</strong> Buying, Usage, Business, Investment all mapped" |

#### Validation Tracker

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `summary.validation[]` | array | yes | — |
| `summary.validation[].decision` | string | yes | "B2 Proof Type" |
| `summary.validation[].status_text` | string | yes | "Pending Nader" |
| `summary.validation[].status_class` | enum | yes | `"badge-open"` / `"badge-ok"` |

#### Footer Metadata

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `summary.meta.version` | string | yes | "Decision Ledger v1.0 · March 16, 2026 · Product.Zone" |
| `summary.meta.last_change` | string | yes | "Last change: A0 Client-Side JTBD, A8 Category Maturity..." |
| `summary.meta.next_review` | string | yes | "Next review: April 30, 2026" |

### Board Footer

| Slot | Type | Required | PZ Example |
|------|------|----------|------------|
| `footer.left` | string | yes | "Product.Zone · Commercial Decision Ledger v1.0 · March 2026" |
| `footer.right` | string | yes | "34 decisions · 4 paths · 6 surfaces · 60 questions" |

---

## Card Capacity Per Column

The 2400px canvas with 6 equal columns holds comfortably:

| Column | Recommended Cards | Max Before Overflow |
|--------|-------------------|---------------------|
| Standard column | 6–10 | ~12 |
| With section breaks | 8–12 (breaks add ~30px each) | ~14 |
| Summary column | N/A (custom layout) | — |

If a client has more than ~50 decisions total, consider:
1. Increasing canvas width (already scrollable, no hard limit)
2. Splitting into two boards (Buying Path board + Business/Investment board)
3. Collapsing future-stage decisions into a single "queued" card per column

---

## Status Distribution Guide

Typical healthy distribution after a Positioning Sprint:

| Status | Expected % | Signal |
|--------|-----------|--------|
| Locked | 50–70% | Core decisions made, surfaces can be built |
| Validated | 15–25% | Evidence exists but not yet battle-tested |
| Future | 5–15% | Identified for later stage (Scale/Sustain) |
| Open | 5–15% | Needs resolution before next phase |

If >30% are Open after Sprint completion, the Sprint didn't finish its job.

---

## Leverage Scoring

5-dot scale representing how many downstream decisions depend on this one.

| Dots | Meaning | Example |
|------|---------|---------|
| 5/5 | Foundation — everything depends on this | Customer, JTBD, Difference |
| 4/5 | High — multiple surfaces or decisions reference this | First Step, Proof Type |
| 3/5 | Medium — important but contained scope | Market Bet, Effort Shape |
| 2/5 | Low — operational, few dependencies | Capital Efficiency |
| 1/5 | Isolated — standalone decision | Rare in this framework |

---

## Fill Sequence

When populating during a Sprint:

1. **Column structure first** — define the paths (what's the client's equivalent of A/B/C/D/E/F/G?)
2. **North Star** — what's the single job this business is trying to do?
3. **Positioning decisions (Col 1)** — these unlock everything downstream
4. **Trust + Movement (Col 2)** — what makes buying safe and easy
5. **Activation + Usage (Col 3)** — what happens after yes
6. **Business path (Col 4)** — economics and monetization
7. **Future + Channel (Col 5)** — growth architecture
8. **Summary (Col 6)** — filled last, reflects what the Sprint accomplished
9. **Status assignment** — locked/validated/future/open based on evidence
10. **Leverage scoring** — relative, within and across columns

---

## Versioning

| Field | Convention |
|-------|-----------|
| Schema version | This file header |
| Template version | Comment in HTML file header |
| Reference version | Filename suffix: `-pz-v1.1.html` |
| Client versions | Filename: `decision-ledger-kanban-[client]-v[N].html` |
