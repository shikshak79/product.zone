# Pipeline Step 04: Generate Predictions
## X-RAY v5.3 — Predict outbound performance with granular outcomes

---

## Consistency Anchor

**Do NOT change any previous outputs.**

All predictions must be consistent with:
- `evidence` array from Step 01
- `stages` and `score` from Step 02
- `risk_signals` from Step 03

If Q3 is MISSING, Reply Rate cannot be Strong.

---

## Input from Step 03
- `meta` object
- `evidence` array
- `stages` object
- `score` object
- `risk_signals` object

## Output to Step 05
- All previous fields (unchanged — do not modify)
- `predictions` object (4 metrics + summary)

---

## Prediction Labels (5-Level Scale)

Sales outcomes vary more than 3 levels. Use this scale:

| Label | Meaning | Typical Outcome |
|-------|---------|-----------------|
| **Strong** | Conditions are right | Top quartile performance |
| **Good** | Minor gaps, manageable | Above average performance |
| **Moderate** | Meaningful gaps | Average performance |
| **Weak** | Significant gaps | Below average, requires extra effort |
| **Poor** | Critical gaps | Bottom quartile, high friction |

---

## The 4 Prediction Metrics

### Metric 1: Reply Rate
**Driving Questions:** Q3 (Pain), Q6 (ICP), Market Education Burden signal

**What it predicts:** Will cold outreach get responses?

| Label | Criteria |
|-------|----------|
| **Strong** | Q3 CLEAR + Q6 CLEAR + Market Education Burden LOW. Pain resonates, targeting is tight, market knows the category. |
| **Good** | Q3 CLEAR + Q6 CLEAR, but Market Education Burden MEDIUM. Pain works, but some education needed. |
| **Moderate** | Q3 CLEAR but Q6 PARTIAL, OR Q6 CLEAR but Q3 PARTIAL. One of pain/targeting needs work. |
| **Weak** | Both Q3 and Q6 PARTIAL. Neither pain nor targeting is sharp. |
| **Poor** | Q3 MISSING or Q6 MISSING, OR Market Education Burden HIGH. Hard to get attention. |

---

### Metric 2: Demo Conversion
**Driving Questions:** Q13 (Effort), Q11 (Social Proof), Q12 (Results)

**What it predicts:** Will interested prospects convert to demos/meetings?

| Label | Criteria |
|-------|----------|
| **Strong** | Q13 CLEAR + (Q11 CLEAR or Q12 CLEAR). Process is visible and proof exists. |
| **Good** | Q13 CLEAR + both Q11 and Q12 PARTIAL. Process clear, proof needs strengthening. |
| **Moderate** | Q13 PARTIAL + one of Q11/Q12 CLEAR. Some questions about effort or validation. |
| **Weak** | Q13 PARTIAL + both Q11/Q12 PARTIAL. Buyer uncertain about effort AND validation. |
| **Poor** | Q13 MISSING, OR both Q11 and Q12 MISSING. High uncertainty kills conversion. |

---

### Metric 3: Internal Sell
**Driving Questions:** Q8 (Alternative), Q22 (ROI), Q14 (Role-Matched Proof)

**What it predicts:** Can the champion sell this internally?

| Label | Criteria |
|-------|----------|
| **Strong** | Q8 CLEAR + Q22 CLEAR. Champion can name what they're replacing AND has ROI ammunition. |
| **Good** | Q8 CLEAR + Q22 PARTIAL + Q14 CLEAR. Comparison anchor exists, ROI implied, role proof helps. |
| **Moderate** | Q8 CLEAR but Q22 MISSING, OR Q8 PARTIAL + Q22 CLEAR. Either comparison or ROI is weak. |
| **Weak** | Q8 PARTIAL + Q22 PARTIAL. Champion must build case with limited ammunition. |
| **Poor** | Q8 MISSING or Q22 MISSING without compensating strength. Champion cannot build internal case. |

---

### Metric 4: Pipeline Speed
**Driving Questions:** Q5 (Urgency), Q17 (Safe to Try), Q9 (Why Alternatives Fail)

**What it predicts:** How fast will deals move through pipeline?

| Label | Criteria |
|-------|----------|
| **Strong** | Q5 CLEAR + Q17 CLEAR. Urgency built in AND low-risk entry. Deals move fast. |
| **Good** | Q5 CLEAR + Q17 PARTIAL, OR Q5 PARTIAL + Q17 CLEAR. Either urgency or safety is strong. |
| **Moderate** | Q5 PARTIAL + Q17 PARTIAL. Some urgency, some safety, but neither strong. Deals move but may stall. |
| **Slow** | Q5 MISSING + Q17 CLEAR. Safe to try but no urgency. Deals drift. |
| **Stalled** | Q5 MISSING + Q17 PARTIAL or MISSING. No urgency AND high perceived risk. Deals stuck. |

Note: Pipeline Speed uses "Slow" and "Stalled" instead of "Weak" and "Poor" for clarity.

---

## Generating the Basis Text

For each metric, write the basis showing the question statuses that drove the prediction:

**Format:** `"Based on Q[n] ([status]) + Q[n] ([status])"`

**Examples:**
- `"Based on Q3 (pain clear, prominent) + Q6 (ICP clear)"`
- `"Based on Q5 (missing — no urgency) + Q17 (partial — trial mentioned but no details)"`
- `"Based on Q8 (alternatives named) + Q22 (no ROI documentation)"`

---

## Generating the Summary

Write one sentence that:
1. States what will happen when outbound starts
2. Identifies where deals will stall or slow
3. Names the specific objection that will surface

**Pattern:** `"[What will happen]. [Where it will stall/why]. [Specific objection/consequence]."`

**Examples:**
- `"Buyers will respond and convert to trials. Deals may slow when partners ask 'what's the ROI?' or 'why not stick with current tools until we're busier?'"`
- `"Replies will be below average — market doesn't know the category yet. Outbound must educate before selling."`
- `"Strong top-of-funnel, but internal approval will stall without ROI ammunition for the CFO conversation."`

---

## Output Format

```json
{
  "meta": { ... unchanged ... },
  "evidence": [ ... unchanged ... ],
  "stages": { ... unchanged ... },
  "score": { ... unchanged ... },
  "risk_signals": { ... unchanged ... },
  "predictions": {
    "reply_rate": {
      "value": "Good",
      "class": "good",
      "basis": "Based on Q3 (pain clear) + Q6 (ICP clear) + Market Education (medium)"
    },
    "demo_conversion": {
      "value": "Strong",
      "class": "strong",
      "basis": "Based on Q13 (effort clear) + Q11 (social proof clear)"
    },
    "internal_sell": {
      "value": "Moderate",
      "class": "moderate",
      "basis": "Based on Q8 (alternatives named) + Q22 (no ROI documentation)"
    },
    "pipeline_speed": {
      "value": "Slow",
      "class": "slow",
      "basis": "Based on Q5 (no urgency) + Q17 (trial available)"
    },
    "summary": "Buyers will respond and convert to trials. Deals will slow when partners ask 'what's the ROI?' or 'why switch now?' No urgency + no ROI = drift."
  }
}
```

### Value Classes (for styling)

| Value | Class |
|-------|-------|
| Strong | strong |
| Good | good |
| Moderate | moderate |
| Weak, Slow | weak |
| Poor, Stalled | poor |

---

## Calibration Check

Before outputting, verify predictions match evidence:

| If Evidence Shows... | Prediction Cannot Be... |
|---------------------|-------------------------|
| Q3 MISSING | Reply Rate: Strong or Good |
| Q5 MISSING | Pipeline Speed: Strong or Good |
| Q13 MISSING | Demo Conversion: Strong or Good |
| Q22 MISSING + Q8 MISSING | Internal Sell: Strong or Good |

---

## Pass to Next Step

After generating all 4 predictions with summary, pass the output JSON to **Step 05: Generate Content**.

**CRITICAL CONSISTENCY RULE:** Do NOT modify any previous fields. Predictions must align with evidence already scored.
