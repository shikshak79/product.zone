# Pipeline Step 06: QA & Final Output
## X-RAY v5.3 — Validate consistency and output final JSON

---

## Consistency Anchor — Final Check

This is the final step. Before outputting, verify the entire report is internally consistent. No field should contradict another.

---

## Input from Step 05

Complete JSON object with all fields:
- `meta`
- `evidence`
- `stages`
- `score`
- `risk_signals`
- `predictions`
- `diagnosis`
- `recognition`
- `breakpoint`
- `decisions`
- `recommendations`

## Output

Validated JSON matching X-RAY v5.3 schema, ready for rendering.

---

## QA Checklist

Run ALL checks. If any check fails, fix before outputting.

### 1. Cross-Step Consistency Checks

These are the most important. LLMs sometimes drift between steps.

| Check | How to Verify | Fix If Failed |
|-------|---------------|---------------|
| Evidence → Verdicts | If a stage has a MISSING question, verdict must be "break" | Recalculate verdict |
| Evidence → Score | Score 7+ requires 12+ CLEAR questions | Recalculate score |
| Evidence → Signals | If Q5 is MISSING, "Why Act Now" cannot be Strong | Recalculate signal |
| Evidence → Predictions | If Q3 is MISSING, Reply Rate cannot be Strong | Recalculate prediction |
| Signals → Content | If signal is "High Risk", diagnosis must mention it | Revise diagnosis |
| Verdicts → Breakpoint | Breakpoint stage must match first break/weak stage | Fix breakpoint |

### 2. Calibration Checks

| Check | Rule | Red Flag |
|-------|------|----------|
| Score vs. Clear Count | Score 7+ requires 12+ clear | Score 8 with 10 clear |
| Score vs. Breaks | Any break caps score at 4 | Score 6 with a break stage |
| Verdict vs. Score | 7+ = green, 5-6 = amber, 1-4 = red | Mismatch |
| Predictions vs. Questions | Strong requires driving Qs clear | Strong with driving Q missing |

### 3. Completeness Checks

Verify all required fields are present and non-empty:

```
□ meta: company, url, target_buyer, date, version
□ score: value, max, label, class, interpretation
□ score.breakdown: clear, partial, missing (must sum to 20)
□ score.depth: status, status_class, q21, q22
□ diagnosis: verdict, verdict_class, headline, text
□ predictions: all 4 with value, class, basis + summary
□ recognition: exactly 4 items, all non-empty strings
□ risk_signals: all 8 with value, basis, evidence
□ stages: all 6 (land, make_sense, self_select, compare, validate, commit)
□ breakpoint: stage, stage_class, insight, missing_items (3-4 items)
□ decisions: 3-4 items, each with name, status, status_label, finding
□ recommendations: eyebrow, action, goals (3-4 items)
□ evidence: all 22 questions with id, stage, question, quote, inference, status
```

### 4. Voice Compliance — Careful Scan

Scan the following text fields for banned phrases. Read each field carefully:
- `diagnosis.headline`
- `diagnosis.text`
- `breakpoint.insight`
- Each `decisions[].finding`
- Each `recommendations.goals[].description`
- Each `recognition[]` item
- Each `risk_signals[].evidence`
- `predictions.summary`

**Banned phrases to find and remove:**

| Category | Phrases to Remove |
|----------|------------------|
| Negative parallelism | "It's not X, it's Y", "This isn't about X", "not X, but Y" |
| Hollow transitions | "It's worth noting", "It's important to understand", "This highlights", "Notably", "Interestingly", "In summary", "Ultimately", "Overall" |
| Vague attribution | "Many buyers might", "Research suggests", "Most prospects" |
| Punctuation | Em dashes (—) |
| Inflated verbs | "serves as", "functions as", "leverages", "utilizes" |
| Promotional words | "fascinating", "remarkable", "significant", "crucial", "critical" |

**Replacement strategy:**
- Negative parallelism → State the positive directly
- Hollow transitions → Delete, start with the substance
- Em dashes → Use periods or commas
- Inflated verbs → Use simple equivalents (is, uses)

### 5. Evidence Quality

| Check | Rule | Red Flag |
|-------|------|----------|
| Quotes are real | Every quote should appear on actual homepage | Quote not from source |
| Inferences are grounded | Inference must follow from quote | Inference unrelated to quote |
| Status matches evidence | CLEAR = explicitly stated, no interpretation | CLEAR when evidence is weak |

---

## Add Indicators

Generate 3-4 progress indicators for the company to track:

Each indicator:
- `what`: A measurable signal (conversation pattern, metric, behavior)
- `direction`: Expected change direction if recommendations implemented

**Good examples:**
```json
{
  "what": "'What does this cost?' asked before demo",
  "direction": "Should decrease after pricing visibility added"
}
```
```json
{
  "what": "Trial-to-paid conversion rate",
  "direction": "Should improve as outcome metrics replace vanity metrics"
}
```
```json
{
  "what": "Time from first touch to signed contract",
  "direction": "Should shorten with urgency framing"
}
```

**Each indicator should:**
- Name a measurable signal
- Connect to a specific recommendation
- State expected direction of change

---

## Final Consistency Matrix

Before outputting, verify this matrix:

| If this is true... | Then this must also be true... |
|-------------------|-------------------------------|
| Q5 status = "missing" | Why Act Now signal ≠ "Strong" |
| Q5 status = "missing" | Pipeline Speed ≠ "Strong" or "Good" |
| Q3 status = "missing" | Message Priority ≠ "Strong" |
| Q3 status = "missing" | Reply Rate ≠ "Strong" or "Good" |
| make_sense verdict = "break" | Score ≤ 4 |
| Any verdict = "break" | Score ≤ 4 |
| score.value ≥ 7 | diagnosis.verdict_class = "green" |
| score.value 5-6 | diagnosis.verdict_class = "amber" |
| score.value ≤ 4 | diagnosis.verdict_class = "red" |
| Q22 status = "missing" | Internal Sharing ≠ "Strong" |
| Q1 status = "missing" | Market Education Burden = "High" |

If any row is violated, go back and fix the inconsistency.

---

## Final JSON Structure

```json
{
  "meta": {
    "company": "string",
    "url": "string",
    "target_buyer": "string",
    "date": "YYYY-MM-DD",
    "version": "5.3"
  },
  "score": {
    "value": 1-10,
    "max": 10,
    "label": "string",
    "class": "high|good|mid|low|critical",
    "interpretation": "string",
    "breakdown": { "clear": n, "partial": n, "missing": n },
    "depth": { "status": "Strong|Partial|Weak", "status_class": "string", "q21": "status", "q22": "status" }
  },
  "diagnosis": {
    "verdict": "Ready for Outbound|Proceed with Caution|Fix Before Outbound",
    "verdict_class": "green|amber|red",
    "headline": "string (20-40 words, no AI tells)",
    "text": "string (2-3 sentences)"
  },
  "predictions": {
    "reply_rate": { "value": "Strong|Good|Moderate|Weak|Poor", "class": "string", "basis": "string" },
    "demo_conversion": { "value": "...", "class": "...", "basis": "..." },
    "internal_sell": { "value": "...", "class": "...", "basis": "..." },
    "pipeline_speed": { "value": "Strong|Good|Moderate|Slow|Stalled", "class": "...", "basis": "..." },
    "summary": "string"
  },
  "recognition": ["string", "string", "string", "string"],
  "risk_signals": {
    "message_priority": { "value": "Strong|Weak|High Risk", "basis": "string", "evidence": "string" },
    "buyer_focus": { ... },
    "why_act_now": { ... },
    "proof_relevance": { "value": "Strong|Moderate|Weak", ... },
    "explanation_burden": { "value": "Strong|Moderate|High Risk", ... },
    "market_education_burden": { "value": "Low|Medium|High", ... },
    "internal_sharing": { "value": "Strong|Moderate|Weak", ... },
    "mixed_signals": { "value": "Strong|Weak|High Risk", ... }
  },
  "stages": {
    "land": "ok|weak|break",
    "make_sense": "ok|weak|break",
    "self_select": "ok|weak|break",
    "compare": "ok|weak|break",
    "validate": "ok|weak|break",
    "commit": "ok|weak|break"
  },
  "breakpoint": {
    "stage": "string",
    "stage_class": "red|amber",
    "insight": "string",
    "missing_items": [{ "text": "string", "status": "missing|partial" }]
  },
  "decisions": [{
    "name": "string",
    "status": "clear|partial|missing",
    "status_label": "string",
    "finding": "string"
  }],
  "recommendations": {
    "eyebrow": "string",
    "action": "string",
    "goals": [{ "label": "string", "description": "string" }]
  },
  "evidence": [{
    "id": "Q1-Q22",
    "stage": "land|make_sense|self_select|compare|validate|commit|depth",
    "question": "string",
    "quote": "string",
    "inference": "string",
    "status": "clear|partial|missing"
  }],
  "indicators": [{ "what": "string", "direction": "string" }]
}
```

---

## Output

Return the complete, validated JSON object.

This is the final step. The JSON is now ready to be:
1. Stored in database
2. Rendered via HTML template
3. Returned via API

---

## Pipeline Complete

The 7-step pipeline:
```
00-context-and-fetch.md   → System context + fetch homepage
01-score-questions.md     → Score 22 questions with precise criteria
02-calculate-verdicts.md  → Calculate stage verdicts + overall score
03-generate-signals.md    → Generate 8 risk signals with operational definitions
04-generate-predictions.md → Generate 4 predictions with 5-level scale
05-generate-content.md    → Generate narrative content with voice discipline
06-qa-output.md           → Cross-step consistency check + final output
```
