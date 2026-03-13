# X-RAY Protocol: 02 — Scoring
## v5.3

---

## Overview

The X-RAY uses a **1-10 scale** calculated from question statuses and stage verdicts.

---

## Step 1: Score Each Question

Evaluate all 22 questions against the homepage:

| Status | Meaning | Criteria |
|--------|---------|----------|
| **Clear** | Fully answered | Buyer can definitively answer the question from homepage content |
| **Partial** | Partially addressed | Some relevant content exists but incomplete, unclear, or buried |
| **Missing** | Not addressed | No relevant content found anywhere on the scanned pages |

---

## Step 2: Calculate Stage Verdicts

For each of the 6 core stages, determine a verdict:

### Stage → Questions Mapping

| Stage | Questions |
|-------|-----------|
| Land | Q1, Q2 |
| Make Sense | Q3, Q4, Q5 |
| Self-Select | Q6, Q7 |
| Compare | Q8, Q9, Q10 |
| Validate | Q11, Q12, Q13, Q14, Q15 |
| Commit | Q16, Q17, Q18, Q19, Q20 |

### Verdict Rules

| Verdict | Rule |
|---------|------|
| **OK** | All questions clear, OR majority clear with none missing |
| **Weak** | Any partial, none missing |
| **Break** | Any missing |

### Examples

- Land: Q1=clear, Q2=clear → **OK**
- Land: Q1=partial, Q2=clear → **Weak**
- Land: Q1=missing, Q2=clear → **Break**
- Make Sense: Q3=clear, Q4=clear, Q5=partial → **Weak**
- Make Sense: Q3=clear, Q4=missing, Q5=partial → **Break**

---

## Step 3: Calculate Overall Score

Count results from the 20 core questions (Q1-Q20):

```
clear_count = count of clear questions
partial_count = count of partial questions
missing_count = count of missing questions

ok_stages = count of stages with OK verdict
weak_stages = count of stages with Weak verdict
break_stages = count of stages with Break verdict
```

### Score Lookup Table

| Score | Label | Criteria |
|-------|-------|----------|
| **10** | Ready to Scale | All 6 stages OK AND 18+ clear |
| **9** | Strong | 6 OK AND 16-17 clear |
| **8** | Solid | 5-6 OK, ≤1 weak, 14-15 clear |
| **7** | Good | 5-6 OK, 1-2 weak, 12-13 clear |
| **6** | Proceed with Caution | 4-5 OK, 2 weak, 10-11 clear |
| **5** | Gaps to Address | 3-4 OK, 2-3 weak, 8-9 clear |
| **4** | Fix Before Outbound | 2-3 OK OR 1 break, 6-7 clear |
| **3** | Major Work Needed | 1-2 OK, 2 breaks, 4-5 clear |
| **2** | Broken | 0-1 OK, 3+ breaks, 2-3 clear |
| **1** | Fundamentally Broken | All weak/break, <2 clear |

### Simplified Algorithm

```python
def calculate_score(clear, partial, missing, ok, weak, breaks):
    # Any breaks drop score significantly
    if breaks >= 3:
        return 2 if clear >= 2 else 1
    if breaks == 2:
        return 3 if clear >= 4 else 2
    if breaks == 1:
        return 4 if clear >= 6 else 3
    
    # No breaks - score by clear count and weak stages
    if clear >= 18 and ok == 6:
        return 10
    if clear >= 16 and ok == 6:
        return 9
    if clear >= 14 and weak <= 1:
        return 8
    if clear >= 12:
        return 7
    if clear >= 10:
        return 6
    if clear >= 8:
        return 5
    if clear >= 6:
        return 4
    if clear >= 4:
        return 3
    return 2
```

---

## Step 4: Calculate Depth Assessment

Depth questions (Q21, Q22) are scored separately:

| Depth Status | Rule |
|--------------|------|
| **Strong** | Both Q21 and Q22 are clear |
| **Partial** | At least one clear, neither missing |
| **Weak** | Any missing |

---

## Step 5: Determine Verdict

Based on score, assign an action verdict:

| Score Range | Verdict | Verdict Class |
|-------------|---------|---------------|
| 7-10 | Ready for Outbound | green |
| 5-6 | Proceed with Caution | amber |
| 1-4 | Fix Before Outbound | red |

---

## Output

```json
{
  "score": {
    "value": 7,
    "max": 10,
    "label": "Good",
    "interpretation": "Good — minor friction in comparison layer",
    "breakdown": {
      "clear": 11,
      "partial": 7,
      "missing": 2
    },
    "depth": {
      "status": "Partial",
      "q21": "partial",
      "q22": "partial"
    }
  }
}
```
