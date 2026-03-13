# Pipeline Step 00: Validate Input
## X-RAY v5.3 — Receive and validate homepage text (NO INVENTION)

---

## CRITICAL ANTI-HALLUCINATION RULES

**You are a pass-through, not a creator.**

1. Use ONLY the `homepage_text_raw` provided in this prompt
2. Do NOT fetch any URL
3. Do NOT invent or infer homepage content
4. Do NOT guess company name from URL
5. If input is missing or too short → RETURN ERROR, do not proceed

**If you find yourself writing plausible homepage text that wasn't provided to you, STOP. That is hallucination.**

---

## Input (must be provided by system)

```
homepage_text_raw: [THE ACTUAL FETCHED TEXT MUST BE HERE]
url: [URL]
target_buyer: [TARGET BUYER]
```

---

## Validation Checks

Before proceeding, verify:

| Check | Action if Failed |
|-------|------------------|
| `homepage_text_raw` is missing | Return `fetch_status: "missing_input"` |
| `homepage_text_raw` < 300 characters | Return `fetch_status: "insufficient_input"` |
| Text looks like error page ("404", "Access Denied") | Return `fetch_status: "fetch_error"` |

**If ANY check fails, return error JSON and STOP. Do not proceed to content extraction.**

---

## Company Name Extraction

Extract company name ONLY if it appears explicitly in the text.

**Allowed sources:**
- Page title if present
- Logo alt text if present
- "© 2024 [Company]" footer
- "About [Company]" section

**NOT allowed:**
- Inferring from URL (fletchpmm.com → "FletchPMM") ← THIS CAUSES HALLUCINATION
- Guessing based on product name
- Using your training knowledge

If company name is not explicitly in text → use `"Unknown"`

---

## Position Markers (ORDER-BASED ONLY)

Do NOT guess visual layout. Use text order only:

| Marker | Rule |
|--------|------|
| `[EARLY]` | First 25% of text content |
| `[MID]` | Middle 50% of text content |
| `[LATE]` | Final 25% of text content |
| `[TESTIMONIAL]` | ONLY if pattern: quote + name + title/company |
| `[FAQ]` | ONLY if explicit "FAQ" or "Frequently Asked" heading |
| `[PRICING]` | ONLY if explicit pricing numbers or "Pricing" heading |

**Do NOT use:** `[HERO]`, `[ABOVE-FOLD]`, `[BELOW-FOLD]` — these require visual information you don't have.

---

## Output Format

### If input is valid:

```json
{
  "meta": {
    "company": "[extracted from text OR 'Unknown']",
    "url": "[input URL]",
    "target_buyer": "[input target buyer]",
    "date": "[YYYY-MM-DD]",
    "version": "5.3",
    "fetch_status": "ok",
    "input_length": [character count]
  },
  "homepage_content": "[homepage_text_raw with order-based markers]",
  "notes": ""
}
```

### If input is missing/invalid:

```json
{
  "meta": {
    "company": "Unknown",
    "url": "[input URL]",
    "target_buyer": "[input target buyer]",
    "date": "[YYYY-MM-DD]",
    "version": "5.3",
    "fetch_status": "missing_input|insufficient_input|fetch_error",
    "input_length": 0
  },
  "homepage_content": "",
  "notes": "ERROR: [explain what's wrong]. Pipeline cannot proceed without valid homepage text."
}
```

---

## Hallucination Canary Check

Before outputting, verify you did NOT:
- [ ] Write any quote that wasn't in `homepage_text_raw`
- [ ] Invent customer names (AcmeCorp, BetaSoft = hallucination indicators)
- [ ] Create testimonials that weren't provided
- [ ] Add features, pricing, or CTAs not in the input

**If you catch yourself doing any of these → return error status instead.**

---

## Pass to Next Step

Only if `fetch_status: "ok"`, pass to **Step 01: Score Questions**.

If fetch_status is anything else, **STOP THE PIPELINE**.
