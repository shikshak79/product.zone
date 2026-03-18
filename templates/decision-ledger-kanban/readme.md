# Decision Ledger Kanban

A wide-format kanban showing every commercial decision a business has made or needs to make,
organized by decision path and sorted by leverage. The definitive Sprint handoff artifact.

**Canvas:** 2400px+ wide (scrollable) · Mixed register (light board + dark summary)
**Design system:** Product.Zone Visual System v1

---

## Files

| File | Role |
|------|------|
| `decision-ledger-kanban-template.html` | Structural shell. All CSS locked. Handlebars slots for all content. |
| `schema.md` | Data schema: every slot, card types, leverage scoring, fill sequence, capacity guide. |
| `decision-ledger-kanban-pz-v1.1.html` | Reference example: Product.Zone's own 34-decision ledger. Quality bar. |

---

## Structure

```
┌─────────────────────────────────────────────────────────────────────┐
│ HEADER: eyebrow · title · subtitle · legend                       │
├──────────┬──────────┬──────────┬──────────┬──────────┬─────────────┤
│ COL 1    │ COL 2    │ COL 3    │ COL 4    │ COL 5    │ COL 6       │
│ (light)  │ (light)  │ (light)  │ (light)  │ (light)  │ (DARK)      │
│          │          │          │          │          │             │
│ North    │ Trust +  │ Activate │ Business │ Future + │ Session     │
│ Star +   │ Movement │ + Usage  │ Path     │ Channel  │ Summary     │
│ Position │          │          │          │          │             │
│          │          │          │          │          │ Stats       │
│ [cards]  │ [cards]  │ [cards]  │ [cards]  │ [cards]  │ Unlocked    │
│          │          │          │          │          │ Validation  │
│          │          │          │          │          │ Open items  │
│          │          │          │          │          │ Next agenda │
├──────────┴──────────┴──────────┴──────────┴──────────┴─────────────┤
│ FOOTER: version · stats                                            │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Card Types

| Type | CSS Class | Visual | Use |
|------|-----------|--------|-----|
| North Star | `.dc-ns` | Dark card, orange eyebrow | One per board. The overarching JTBD. |
| Locked | `.dc.locked` | Green left border | Final decision. Change requires deliberate revisit. |
| Validated | `.dc.validated` | Teal left border | Evidence exists but not battle-tested. |
| Future Stage | `.dc.future` | Purple left border | Identified for later. Placeholder. |
| Open | `.dc.open-item` | Orange left border | Needs resolution. Blocking or important. |

---

## How to Use

### Manual (Sprint delivery)

1. Open the template HTML
2. Replace `{{slots}}` following `schema.md` constraints
3. For columns: duplicate the column block per path, adjust accent/title/cards
4. For cards: duplicate the card block per decision, set status/leverage/content
5. Leverage dots: set N filled (`lf`) + (5-N) empty (`le`) divs
6. Summary: fill stats, sections, validation, metadata
7. Save as `decision-ledger-kanban-[client]-v1.html`

### Automated (future)

Feed a JSON object matching the schema into a handlebars renderer.
The card/column repeating blocks compile directly.

---

## Customization Rules

**What you CAN change:**
- Number of columns (4–6 content columns + 1 summary)
- Number of cards per column
- Section groupings within columns
- All card content (code, name, answer, detail, status, leverage)
- Summary sections, stats, validation items
- Column accent colors (use design system vars)

**What you MUST NOT change:**
- CSS tokens (colors, fonts, spacing)
- Card component structure (top row → name → answer → detail)
- Legend status types and their color mapping
- Summary column position (always last, always dark)
- Leverage dot count (always 5 total: filled + empty)
- Board grid layout (equal columns)

---

## Version History

| Version | Date | Change |
|---------|------|--------|
| v1.0 | March 2026 | Initial template extracted from PZ Decision Ledger v1.1 |
