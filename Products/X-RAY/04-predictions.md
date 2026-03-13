# X-RAY Protocol: 04 — Predictions
## v5.3

---

## Overview

The X-RAY generates **4 Outbound Performance Predictions** — forecasts of how outbound campaigns will perform based on homepage observations.

Each prediction shows:
- **Value**: Strong / Moderate / Weak (or Slow for pipeline speed)
- **Basis**: Which questions drive the prediction

---

## Prediction Definitions

### 1. Reply Rate

**What it predicts:** Will cold outreach get responses?

**Driving factors:**
- Q3 (Pain worth switching?) — Is pain recognizable?
- Q6 (For my team?) — Is ICP clear enough for targeting?

| Value | Criteria |
|-------|----------|
| Strong | Q3 clear AND Q6 clear. Pain is specific and targeting is defined. |
| Moderate | Q3 clear OR Q6 clear. Either pain or targeting needs work. |
| Weak | Both Q3 and Q6 partial/missing. Hard to get attention. |

---

### 2. Demo Conversion

**What it predicts:** Will interested prospects convert to demos/meetings?

**Driving factors:**
- Q13 (How much effort?) — Is implementation clear?
- Q11 (Teams like mine?) — Is there social proof?
- Q12 (Results achieved?) — Are outcomes quantified?

| Value | Criteria |
|-------|----------|
| Strong | Q13 clear AND (Q11 or Q12 clear). Process is visible and proof exists. |
| Moderate | Q13 partial OR proof gaps. Buyer needs reassurance. |
| Weak | Q13 missing OR both Q11 and Q12 weak. High uncertainty. |

---

### 3. Internal Sell

**What it predicts:** Can the champion sell this internally?

**Driving factors:**
- Q8 (Switching from?) — Can champion explain what this replaces?
- Q22 (ROI documentation?) — Can champion justify the spend?
- Q14 (Proof match role?) — Is there proof for the decision-maker?

| Value | Criteria |
|-------|----------|
| Strong | Q8 clear AND (Q22 clear OR Q14 clear). Champion has ammunition. |
| Moderate | Some gaps in comparison or ROI. Champion needs help. |
| Weak | Q8 missing AND Q22 weak. Champion cannot build internal case. |

---

### 4. Pipeline Speed

**What it predicts:** How fast will deals move through pipeline?

**Driving factors:**
- Q5 (Why act now?) — Is there urgency?
- Q9 (Why alternatives fail?) — Is comparison handled?
- Q17 (Safe to try?) — Is there a low-commitment entry?

| Value | Criteria |
|-------|----------|
| Strong | Q5 clear AND Q9 clear AND Q17 clear. Urgency + clarity + low risk. |
| Moderate | Some urgency or comparison gaps. Deals will move but may stall. |
| Slow | Q5 missing OR Q17 missing. Deals will drag without urgency or safe entry. |

---

## Prediction Logic Summary

| Metric | Primary Questions | What Makes It Weak |
|--------|-------------------|-------------------|
| Reply Rate | Q3, Q6 | Pain unclear or targeting broad |
| Demo Conversion | Q13, Q11, Q12 | Process unclear, proof missing |
| Internal Sell | Q8, Q22, Q14 | No alternative named, no ROI |
| Pipeline Speed | Q5, Q9, Q17 | No urgency, no safe entry |

---

## Output Format

```json
{
  "predictions": {
    "reply_rate": {
      "value": "Strong",
      "basis": "Based on Q3 (pain clear) + Q6 (ICP defined)"
    },
    "demo_conversion": {
      "value": "Strong",
      "basis": "Based on Q13 (process visible) + Q11-12 (proof strong)"
    },
    "internal_sell": {
      "value": "Moderate",
      "basis": "Based on Q8 (alternative unclear) + Q22 (ROI scattered)"
    },
    "pipeline_speed": {
      "value": "Moderate",
      "basis": "Based on Q5 (urgency weak) + Q9 (no why-not-X)"
    },
    "summary": "Buyers will respond and convert to calls. Deals may slow when CFO asks 'why not just hire a freelancer?'"
  }
}
```

---

## Display Guidelines

- Show all 4 metrics in a grid
- Color-code: Strong=green, Moderate=orange, Weak/Slow=red
- Show basis text below each metric (e.g., "Based on Q3 + Q6")
- Include summary sentence at bottom explaining the overall prediction
