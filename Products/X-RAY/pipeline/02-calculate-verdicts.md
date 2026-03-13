# Pipeline Step 02: Calculate Verdicts & Score
## X-RAY v5.3 — Derive stage verdicts and overall score

---

## Consistency Anchor

**Do NOT change any evidence from Step 01.**

All reasoning in this step must be consistent with the `evidence` array from Step 01. If the evidence says Q5 is MISSING, this step cannot treat urgency as present.

---

## Input from Step 01
- `meta` object
- `evidence` array (22 scored questions)

## Output to Step 03
- `meta` object (unchanged)
- `evidence` array (unchanged — do not modify)
- `stages` object (6 stage verdicts)
- `score` object (overall score + breakdown)

---

## Step 2A: Count Question Statuses

Count across the **20 core questions (Q1-Q20)** only:

```
clear_count = number of questions with status "clear"
partial_count = number of questions with status "partial"
missing_count = number of questions with status "missing"
```

For **depth questions (Q21-Q22)**, track separately:
```
depth_q21 = status of Q21
depth_q22 = status of Q22
```

---

## Step 2B: Calculate Stage Verdicts

For each stage, apply these rules strictly:

### Verdict Rules

| Verdict | Rule |
|---------|------|
| **OK** | Majority of stage questions are CLEAR, AND none are MISSING |
| **WEAK** | Any question is PARTIAL, AND none are MISSING |
| **BREAK** | Any question is MISSING |

### Stage Composition

| Stage | Questions | Verdict Calculation |
|-------|-----------|---------------------|
| **land** | Q1, Q2 | OK if both clear; WEAK if any partial; BREAK if any missing |
| **make_sense** | Q3, Q4, Q5 | OK if 2+ clear and none missing; WEAK if any partial and none missing; BREAK if any missing |
| **self_select** | Q6, Q7 | OK if both clear; WEAK if any partial; BREAK if any missing |
| **compare** | Q8, Q9, Q10 | OK if 2+ clear and none missing; WEAK if any partial and none missing; BREAK if any missing |
| **validate** | Q11, Q12, Q13, Q14, Q15 | OK if 3+ clear and none missing; WEAK if any partial and none missing; BREAK if any missing |
| **commit** | Q16, Q17, Q18, Q19, Q20 | OK if 3+ clear and none missing; WEAK if any partial and none missing; BREAK if any missing |

---

## Step 2C: Calculate Overall Score (1-10)

Count stage verdicts:
```
ok_count = number of stages with "ok"
weak_count = number of stages with "weak"
break_count = number of stages with "break"
```

### Scoring Algorithm

```
# Breaks cap the score severely
if break_count >= 3:
    score = 2 if clear_count >= 2 else 1
elif break_count == 2:
    score = 3 if clear_count >= 4 else 2
elif break_count == 1:
    score = 4 if clear_count >= 6 else 3

# No breaks — score by clear count and weak stages
elif clear_count >= 18 and ok_count == 6:
    score = 10
elif clear_count >= 16 and ok_count == 6:
    score = 9
elif clear_count >= 14 and weak_count <= 1:
    score = 8
elif clear_count >= 12:
    score = 7
elif clear_count >= 10:
    score = 6
elif clear_count >= 8:
    score = 5
elif clear_count >= 6:
    score = 4
elif clear_count >= 4:
    score = 3
else:
    score = 2
```

---

## Step 2D: Map Score to Label

| Score | Label |
|-------|-------|
| 10 | Ready to Scale |
| 9 | Strong |
| 8 | Solid |
| 7 | Good |
| 6 | Proceed with Caution |
| 5 | Gaps to Address |
| 4 | Fix Before Outbound |
| 3 | Major Work Needed |
| 2 | Broken |
| 1 | Fundamentally Broken |

### Score Class (for styling)

| Score Range | Class |
|-------------|-------|
| 9-10 | high |
| 7-8 | good |
| 5-6 | mid |
| 3-4 | low |
| 1-2 | critical |

---

## Step 2E: Calculate Depth Status

Depth is reported separately, not included in main score.

| Depth Status | Rule |
|--------------|------|
| **Strong** | Both Q21 and Q22 are CLEAR |
| **Partial** | At least one is CLEAR or both are PARTIAL, neither is MISSING |
| **Weak** | Any MISSING |

---

## Step 2F: Generate Interpretation

Write a one-line interpretation that names:
1. The label
2. The primary issue (which stage or gap)

**Format:** `"[Label] — [primary issue description]"`

**Examples:**
- `"Good — minor friction in comparison layer"`
- `"Proceed with Caution — validation and urgency gaps"`
- `"Major Work Needed — multiple stages breaking buyer journey"`
- `"Fix Before Outbound — category unclear and no safe entry point"`

---

## Output Format

```json
{
  "meta": { ... unchanged ... },
  "evidence": [ ... unchanged from Step 01 ... ],
  "stages": {
    "land": "ok",
    "make_sense": "weak",
    "self_select": "ok",
    "compare": "ok",
    "validate": "weak",
    "commit": "ok"
  },
  "score": {
    "value": 6,
    "max": 10,
    "label": "Proceed with Caution",
    "class": "mid",
    "interpretation": "Proceed with Caution — validation and urgency gaps",
    "breakdown": {
      "clear": 13,
      "partial": 6,
      "missing": 1
    },
    "depth": {
      "status": "Partial",
      "status_class": "partial",
      "q21": "partial",
      "q22": "partial"
    }
  }
}
```

---

## Calibration Check

Before proceeding, verify these constraints:

| Constraint | Check |
|------------|-------|
| Score 7+ requires | 12+ clear questions |
| Score > 4 requires | No break stages |
| Break stage requires | At least one MISSING question in that stage |
| OK stage requires | No MISSING questions in that stage |

If any constraint is violated, recheck your calculations.

---

## Pass to Next Step

After calculating verdicts and score, pass the output JSON to **Step 03: Generate Risk Signals**.

**CRITICAL CONSISTENCY RULE:** Do NOT modify `evidence` array. All subsequent steps must use the same evidence. Your stage verdicts and score are now fixed — later steps cannot contradict them.
