# X-RAY Protocol: 03 — Risk Signals
## v5.3

---

## Overview

The X-RAY generates **7 Outbound Risk Signals** — meta-patterns that synthesize homepage observations into outbound performance predictions.

Each signal is scored: **Strong / Weak / High Risk**

---

## Signal Definitions

### 1. Message Priority

**What it measures:** Does the homepage lead with buyer pain or product/category claims?

**Based on:** Q3 (Pain), Q4 (Project), Q5 (Stakes)

| Value | Criteria |
|-------|----------|
| Strong | Pain-first hero. Buyer sees their problem immediately. |
| Weak | Mixed priority. Pain present but not leading. |
| High Risk | Capability-first or category-first. Buyer must hunt for relevance. |

---

### 2. Buyer Focus

**What it measures:** Can buyers quickly determine if this is for them?

**Based on:** Q6 (Team fit), Q7 (Situation fit)

| Value | Criteria |
|-------|----------|
| Strong | Clear wedge ICP. Specific industry, role, or situation named. |
| Weak | 2-3 segments addressed. Targeting somewhat diluted. |
| High Risk | 4+ segments or "everyone" positioning. No clear wedge. |

---

### 3. Why Act Now

**What it measures:** Does the homepage create urgency to act?

**Based on:** Q4 (Project), Q5 (Stakes)

| Value | Criteria |
|-------|----------|
| Strong | Clear trigger moment. "When X happens" or quantified cost of waiting. |
| Weak | Pain named but no urgency framing. No cost of inaction. |
| High Risk | No trigger, no stakes. Buyer can defer indefinitely. |

---

### 4. Proof Relevance

**What it measures:** Does the proof match the target buyer?

**Based on:** Q11 (Social proof), Q12 (Results), Q14 (Role match)

| Value | Criteria |
|-------|----------|
| Strong | Same-ICP + same-role + quantified outcomes. |
| Weak | Proof present but misaligned (wrong industry, wrong role, or anonymous). |
| High Risk | No proof, or proof contradicts target ICP. |

---

### 5. Explanation Burden

**What it measures:** How much explaining must sales do?

**Based on:** Q1 (Category), Q2 (Function), Q10 (Differentiation)

| Value | Criteria |
|-------|----------|
| Strong | 10-second clarity. Buyer can explain product to someone else. |
| Weak | Requires discovery. Buyer needs conversation to understand fit. |
| High Risk | Requires education. Sales must explain category from scratch. |

---

### 6. Internal Sharing

**What it measures:** Can the page survive being forwarded internally?

**Based on:** Q11-Q14 (Validate stage), Q22 (ROI documentation)

| Value | Criteria |
|-------|----------|
| Strong | Second reader can understand value without verbal context. |
| Weak | Champion can explain verbally, but page alone is insufficient. |
| High Risk | Page confuses second reader. Kills internal momentum. |

---

### 7. Mixed Signals

**What it measures:** Does the homepage send contradictory signals?

**Based on:** Q15 (Enterprise signals), Q19 (CTA fit), Q20 (Offer fit)

| Value | Criteria |
|-------|----------|
| Strong | Clean alignment between positioning, proof, and offer. |
| Weak | Minor friction. Small inconsistencies between sections. |
| High Risk | Major contradictions. Enterprise logos + startup pricing, or vice versa. |

---

## Signal → Question Mapping (Summary)

| Signal | Based On (Questions) |
|--------|---------------------|
| Message Priority | Q3, Q4, Q5 |
| Buyer Focus | Q6, Q7 |
| Why Act Now | Q4, Q5 |
| Proof Relevance | Q11, Q12, Q14 |
| Explanation Burden | Q1, Q2, Q10 |
| Internal Sharing | Q11, Q12, Q13, Q14, Q22 |
| Mixed Signals | Q15, Q19, Q20 |

---

## Output Format

```json
{
  "risk_signals": {
    "message_priority": {
      "value": "Strong",
      "basis": "Q3, Q4, Q5 (Make Sense)",
      "evidence": "Pain-first hero: 'Let's fix your confusing positioning.' Buyers immediately see the problem."
    },
    "buyer_focus": {
      "value": "Strong",
      "basis": "Q6, Q7 (Self-Select)",
      "evidence": "'B2B software companies' is clear. Pricing by stage helps buyers self-select."
    },
    // ... etc for all 7 signals
  }
}
```

---

## Display Guidelines

- Show signal name + score badge + basis + evidence
- Basis should show question numbers (e.g., "Based on Q3, Q4, Q5")
- Evidence should be one sentence explaining the observation
- Use color-coded badges: Strong=green, Weak=orange, High Risk=red
