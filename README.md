# X-RAY Dima Package v5.3.1

## Product.Zone Outbound Readiness Diagnostic

---

## What's in This Package

```
xray-dima-package-v5.3/
├── README.md                    ← You are here
├── architecture-overview.md     ← System architecture and data flow
│
├── schemas/
│   └── xray-output-schema-v5.3.json   ← JSON contract (Hurozo ↔ Frontend)
│
├── templates/
│   └── xray-report-template-v5.3.html ← HTML template with full CSS
│
├── pipeline/                    ← ★ FOR CURSOR: 7-step pipeline prompts
│   ├── 00-context-and-fetch.md  ← System context + fetch homepage
│   ├── 01-score-questions.md    ← Score 22 questions (PRECISE CRITERIA)
│   ├── 02-calculate-verdicts.md ← Calculate stage verdicts + overall score
│   ├── 03-generate-signals.md   ← Generate 8 risk signals (OPERATIONAL DEFS)
│   ├── 04-generate-predictions.md ← Generate 4 predictions (5-LEVEL SCALE)
│   ├── 05-generate-content.md   ← Generate narrative content (VOICE DISCIPLINE)
│   └── 06-qa-output.md          ← Cross-step consistency check + final output
│
├── protocols/                   ← Reference documentation
│   └── ... (same as before)
│
├── testing/
│   └── master-generation-prompt.md  ← Single prompt for manual testing
│
└── examples/
    └── ... (3 calibrated reports)
```

---

## Key Improvements in v5.3.1

| Issue              | v5.3                  | v5.3.1                                                       |
| ------------------ | --------------------- | ------------------------------------------------------------ |
| Scoring criteria   | Vague ("look for")    | **Precise CLEAR/PARTIAL/MISSING definitions for each question** |
| Scoring discipline | Implicit              | **"CLEAR requires explicit statement. If buyer must interpret → PARTIAL"** |
| Risk signal logic  | Subjective ("buried") | **Operational definitions: "BURIED = below-fold or FAQ only"** |
| Prediction labels  | 3 levels (coarse)     | **5 levels: Strong, Good, Moderate, Weak, Poor**             |
| QA instruction     | "search for patterns" | **"Scan carefully and remove banned phrases"**               |
| Pipeline drift     | No safeguards         | **Consistency anchors at start of each step**                |
| Risk signals       | 7 signals             | **8 signals: added Market Education Burden**                 |

---

## Critical Pipeline Features

### 1. Scoring Discipline

Every question has precise criteria. Example:

```
Q5: Why act now?
CLEAR: Cost of waiting explicitly quantified OR specific trigger moment named
PARTIAL: Pain acknowledged but no cost of inaction stated
MISSING: No urgency framing anywhere
```

### 2. Operational Definitions

Subjective terms are now defined:

| Term      | Definition                               |
| --------- | ---------------------------------------- |
| Buried    | Only in [BELOW-FOLD], [FAQ], or [FOOTER] |
| Prominent | In [HERO] or [ABOVE-FOLD]                |
| Explicit  | Directly stated, no interpretation       |
| Implied   | Must be inferred from context            |

### 3. Consistency Anchors

Each step starts with:

```
Do NOT change any evidence from previous steps.
All reasoning must remain consistent with earlier steps.
```

### 4. 5-Level Prediction Scale

```
Strong → Good → Moderate → Weak → Poor
```

(Pipeline Speed uses: Strong → Good → Moderate → Slow → Stalled)

### 5. Market Education Burden (New Signal)

```
LOW: Well-known category (CRM, LIMS, email marketing)
MEDIUM: Emerging or niche category
HIGH: Invented category, market has no mental model
```

Predicts reply rates and sales cycle length.

### Option A: Cursor Pipeline (Recommended for Dima)

Use the `pipeline/` folder for consecutive LLM calls:

```
Step 00 → 01 → 02 → 03 → 04 → 05 → 06
```

Each step:

1. Receives output from previous step
2. Adds its own output
3. Passes combined JSON to next step

**Pipeline Flow:**

```
[Input: URL + Target Buyer]
     ↓
00-context-and-fetch → homepage_content + meta
     ↓
01-score-questions   → evidence (22 questions)
     ↓
02-calculate-verdicts → stages + score
     ↓
03-generate-signals  → risk_signals (7)
     ↓
04-generate-predictions → predictions (4)
     ↓
05-generate-content  → diagnosis + recognition + breakpoint + decisions + recommendations
     ↓
06-qa-output         → validated final JSON
     ↓
[Output: Complete X-RAY JSON]
```

### Option B: Single Prompt Testing

Use `testing/master-generation-prompt.md` for manual testing in Claude.

---

## Quick Start for Cursor Implementation

### 1. Set Up Pipeline

Create 7 pipeline steps in Cursor, each using the corresponding `pipeline/*.md` file as the system prompt.

### 2. Connect Steps

Each step receives the JSON output from the previous step and adds to it:

- Step 00: Creates initial JSON with `meta` and `homepage_content`
- Step 01-05: Adds their section to the JSON
- Step 06: Validates and outputs final JSON

### 3. Render Output

Use `templates/xray-report-template-v5.3.html` to render the JSON.
Template uses `{{variable}}` Handlebars-style placeholders.

### 4. Validate Against Schema

Check output against `schemas/xray-output-schema-v5.3.json`.

---

## Protocol vs. Pipeline

| Folder       | Purpose                 | Use When                       |
| ------------ | ----------------------- | ------------------------------ |
| `protocols/` | Reference documentation | Understanding the methodology  |
| `pipeline/`  | Executable prompts      | Building consecutive LLM calls |
| `testing/`   | Single-prompt testing   | Manual validation              |

The **protocols** explain the logic.
The **pipeline** is the executable version of that logic.

---

## Key Changes in v5.3

| Change         | v5.2                   | v5.3                          |
| -------------- | ---------------------- | ----------------------------- |
| Scoring        | A-F letter grade       | **1-10 numeric scale**        |
| Depth          | Included in main score | **Separated as indicator**    |
| Predictions    | No visible logic       | **Show basis (Q numbers)**    |
| Risk Signals   | No visible provenance  | **Show "Based on" Q numbers** |
| Voice          | No formal protocol     | **Voice protocol 06**         |
| QA             | Thin checklist         | **Full QA protocol 07**       |
| Implementation | Ad hoc                 | **7-step pipeline**           |

---

## API Endpoint (Target)

```
POST /xray
Content-Type: application/json

Request:
{
  "url": "https://example.com",
  "target_buyer": "VP Engineering"
}

Response:
{
  ... see xray-output-schema-v5.3.json ...
}
```

---

## Testing Checklist

- [ ] Pipeline Step 00 fetches homepage correctly
- [ ] Pipeline Step 01 scores all 22 questions
- [ ] Score calculation matches clear/partial/missing counts
- [ ] Risk signals cite correct questions
- [ ] No AI tells in generated content
- [ ] Output JSON validates against schema
- [ ] Rendered HTML shows proper styling

---

## Contact

Questions? Reach out to Thorsten at Product.Zone.
