# Pipeline Step 03: Generate Risk Signals
## X-RAY v5.3 — Synthesize 8 outbound risk signals with operational definitions

---

## Consistency Anchor

**Do NOT change any previous outputs.**

All signal evaluations must be consistent with:
- `evidence` array from Step 01
- `stages` and `score` from Step 02

If Q5 is MISSING in evidence, "Why Act Now" signal cannot be Strong.

---

## Input from Step 02
- `meta` object
- `evidence` array
- `stages` object
- `score` object

## Output to Step 04
- All previous fields (unchanged — do not modify)
- `risk_signals` object (8 signals)

---

## Operational Definitions

Before evaluating signals, understand these terms:

| Term | Operational Definition |
|------|------------------------|
| **Buried** | Evidence exists only in `[BELOW-FOLD]`, `[FAQ]`, or `[FOOTER]`. Requires scrolling or hunting to find. |
| **Prominent** | Evidence in `[HERO]` or `[ABOVE-FOLD]`. Visible immediately without scrolling. |
| **Explicit** | Directly stated in text. No interpretation required. |
| **Implied** | Must be inferred from context. Requires buyer to connect dots. |
| **Mixed** | Multiple conflicting signals present. Buyer receives contradictory messages. |

---

## The 8 Risk Signals

### Signal 1: Message Priority
**Based on:** Q3, Q4, Q5 (Make Sense stage)

**What it predicts:** Will outbound messages resonate immediately?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q3 is CLEAR AND pain appears in `[HERO]` or `[ABOVE-FOLD]`. Buyer sees their problem in first 3 seconds. |
| **Weak** | Q3 is CLEAR but pain is BURIED (below-fold only), OR Q3 is PARTIAL. Buyer can find relevance but must work for it. |
| **High Risk** | Q3 is PARTIAL with pain only implied, OR Q3 is MISSING. Outbound must create pain awareness from scratch. |

---

### Signal 2: Buyer Focus
**Based on:** Q6, Q7 (Self-Select stage)

**What it predicts:** Will the right buyers self-identify?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q6 is CLEAR with single specific segment named prominently ("For planning firms"). Buyer immediately knows if they're the target. |
| **Weak** | Q6 mentions 2-3 segments (diluted), OR Q6 is PARTIAL (segment implied not stated), OR segment is BURIED. |
| **High Risk** | Q6 mentions 4+ segments, OR Q6 is MISSING. "For everyone" positioning. Wrong buyers will engage, wasting pipeline. |

---

### Signal 3: Why Act Now
**Based on:** Q4, Q5 (Make Sense stage)

**What it predicts:** Will deals move or stall?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q5 is CLEAR with explicit trigger moment OR quantified cost of waiting. Urgency is built into the homepage. |
| **Weak** | Q5 is PARTIAL — pain is acknowledged but no cost of inaction stated. Buyer can logically defer. |
| **High Risk** | Q5 is MISSING. No urgency anywhere. Every deal will stall at "not right now." |

---

### Signal 4: Proof Relevance
**Based on:** Q11, Q12, Q14 (Validate stage)

**What it predicts:** Will proof accelerate or slow decisions?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q11 CLEAR (named companies in ICP) AND Q12 CLEAR (quantified outcomes) AND Q14 CLEAR (role-matched testimonials). Full proof stack. |
| **Moderate** | Two of three are CLEAR, OR all three are PARTIAL. Proof exists but has gaps. |
| **Weak** | Only one CLEAR or any MISSING. Buyer cannot validate fit with people like them. |

---

### Signal 5: Explanation Burden
**Based on:** Q1, Q2, Q10 (Land + Compare stages)

**What it predicts:** How much work must sales do to explain the product?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q1 CLEAR with recognizable category AND Q2 CLEAR. Buyer can explain product to someone else in 10 seconds. |
| **Moderate** | Q1 CLEAR but Q2 PARTIAL, OR Q1 PARTIAL with Q2 CLEAR. Some explaining needed. |
| **High Risk** | Q1 PARTIAL or MISSING. Category unclear. Sales must educate before selling. |

---

### Signal 6: Market Education Burden ← NEW
**Based on:** Q1 (Land) + category recognition

**What it predicts:** Does the market already understand this category, or must you teach them?

| Value | Operational Criteria |
|-------|---------------------|
| **Low** | Q1 CLEAR with well-known category (CRM, LIMS, project management, email marketing). Market has existing mental model. |
| **Medium** | Q1 CLEAR but category is emerging or niche. Some buyers know it, others need orientation. |
| **High** | Q1 PARTIAL or MISSING, OR category is invented ("Revenue Intelligence Platform", "Developer Experience OS"). Market has no mental model. Outbound must create the category before selling the product. |

**Why this matters:** High market education burden predicts low reply rates and long sales cycles regardless of product quality.

---

### Signal 7: Internal Sharing
**Based on:** Q11, Q12, Q13, Q14, Q22 (Validate + Depth)

**What it predicts:** Can the homepage survive being forwarded to a decision-maker?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | Q22 CLEAR (ROI documentation) AND at least 2 of Q11/Q12/Q14 CLEAR. Second reader can understand value without verbal context. |
| **Moderate** | Q22 PARTIAL AND Validate stage is WEAK. Champion can explain verbally, but page alone is incomplete. |
| **Weak** | Q22 MISSING OR multiple Validate questions MISSING. Page confuses second reader. Champion must do heavy lifting. |

---

### Signal 8: Mixed Signals
**Based on:** Q15, Q19, Q20 (Enterprise + Commit stages)

**What it predicts:** Does the homepage send coherent or contradictory signals?

| Value | Operational Criteria |
|-------|---------------------|
| **Strong** | All commit-stage questions consistent. CTA matches motion, pricing matches target, enterprise signals appropriate for ICP. Clean alignment. |
| **Weak** | Minor inconsistencies. Example: "Try free" AND "Book demo" with equal prominence. Buyer slightly confused about next step. |
| **High Risk** | Major contradictions. Examples: Enterprise testimonials + no security page. "Self-serve" messaging + "contact us for pricing." SMB language + enterprise-only CTA. |

---

## Evidence Writing Rules

For each signal, write evidence as:
1. One sentence stating the observation
2. Cite specific text from homepage
3. Name the buyer consequence

**Pattern:** `"[Observation based on evidence]. [Buyer consequence]."`

**Example:**
- `"Pain-first hero: 'Fragmented tools slow projects down.' Buyers immediately see relevance to their world."`
- `"Category uses invented term ('Community Engagement Platform') not widely known. Sales must explain what this is before discussing fit."`

---

## Output Format

```json
{
  "meta": { ... unchanged ... },
  "evidence": [ ... unchanged ... ],
  "stages": { ... unchanged ... },
  "score": { ... unchanged ... },
  "risk_signals": {
    "message_priority": {
      "value": "Strong",
      "basis": "Q3, Q4, Q5 (Make Sense)",
      "evidence": "Pain-first hero: 'Fragmented tools slow projects down.' Buyers immediately see relevance."
    },
    "buyer_focus": {
      "value": "Strong",
      "basis": "Q6, Q7 (Self-Select)",
      "evidence": "'Trusted by 100+ planning firms' names specific segment. Buyers self-identify immediately."
    },
    "why_act_now": {
      "value": "Weak",
      "basis": "Q4, Q5 (Make Sense)",
      "evidence": "Pain is named but no cost of waiting. No trigger moment. Buyers can defer to next quarter."
    },
    "proof_relevance": {
      "value": "Moderate",
      "basis": "Q11, Q12, Q14 (Validate)",
      "evidence": "Named companies exist but metrics are activity (250+ projects) not outcomes. Testimonials lack titles."
    },
    "explanation_burden": {
      "value": "Strong",
      "basis": "Q1, Q2, Q10 (Land + Compare)",
      "evidence": "'Community Engagement Platform for Planning Projects' is clear. 10-second explainability achieved."
    },
    "market_education_burden": {
      "value": "Medium",
      "basis": "Q1 (Category Recognition)",
      "evidence": "'Community Engagement Platform' is emerging category. Some buyers know it, others will need orientation."
    },
    "internal_sharing": {
      "value": "Weak",
      "basis": "Q11-Q14, Q22 (Validate + Depth)",
      "evidence": "No ROI documentation. When champion forwards to partner, partner sees process but not business case."
    },
    "mixed_signals": {
      "value": "Strong",
      "basis": "Q15, Q19, Q20 (Enterprise + Commit)",
      "evidence": "Consistent SaaS motion. 'Try for free' matches product-led approach. GDPR addressed. No contradictions."
    }
  }
}
```

---

## Calibration Check

Before outputting, verify signal values match evidence:

| If Evidence Shows... | Signal Cannot Be... |
|---------------------|---------------------|
| Q3 MISSING | Message Priority: Strong |
| Q5 MISSING | Why Act Now: Strong or Weak (must be High Risk) |
| Q6 MISSING | Buyer Focus: Strong |
| Q1 MISSING | Explanation Burden: Strong |
| Q22 MISSING | Internal Sharing: Strong |

---

## Pass to Next Step

After generating all 8 risk signals, pass the output JSON to **Step 04: Generate Predictions**.

**CRITICAL CONSISTENCY RULE:** Do NOT modify any previous fields. Your signal values must align with the evidence already scored.
