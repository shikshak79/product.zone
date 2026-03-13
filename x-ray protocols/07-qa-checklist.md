# X-RAY Protocol: 07 — QA Checklist
## v5.3

---

## Overview

Every X-RAY report must pass this QA checklist before delivery. The checklist covers:
1. Calibration (score matches evidence)
2. Completeness (all fields populated)
3. Consistency (no internal contradictions)
4. Voice compliance (no AI tells)
5. Evidence quality (grounded observations)

---

## 1. Calibration Checks

### Score-Evidence Alignment

The score must match the evidence. Run these checks:

| Check | Rule | Red Flag |
|-------|------|----------|
| Score vs. Clear Count | Score 7+ requires 12+ clear questions | Score 8 with only 9 clear |
| Score vs. Breaks | Any break caps score at 4 max | Score 6 with a break stage |
| Score vs. Missing | 3+ missing caps score at 5 max | Score 7 with 4 missing |
| Depth separation | Depth questions don't affect main score | Q21/Q22 counted in main score |

### Stage-Question Alignment

Each stage verdict must match its questions:

| Check | Rule | Red Flag |
|-------|------|----------|
| OK verdict | Requires majority clear, none missing | OK with a missing question |
| Weak verdict | Requires no missing | Weak with missing question |
| Break verdict | Requires at least one missing | Break with all partial/clear |

### Prediction-Signal Alignment

Predictions must be justified by the underlying questions:

| Check | Rule | Red Flag |
|-------|------|----------|
| Reply Rate | Strong requires Q3 + Q6 clear | Strong with Q3 partial |
| Demo Conversion | Strong requires Q13 + (Q11 or Q12) clear | Strong with Q13 missing |
| Internal Sell | Strong requires Q8 + (Q22 or Q14) clear | Strong with Q8 missing |
| Pipeline Speed | Strong requires Q5 + Q17 clear | Strong with Q5 missing |

---

## 2. Completeness Checks

### Required Fields

Every report must include all of these:

```
□ meta.company
□ meta.url
□ meta.target_buyer
□ meta.date
□ meta.version

□ score.value (1-10)
□ score.label
□ score.interpretation
□ score.breakdown.clear
□ score.breakdown.partial
□ score.breakdown.missing
□ score.depth.status
□ score.depth.q21
□ score.depth.q22

□ diagnosis.verdict
□ diagnosis.headline
□ diagnosis.text

□ predictions (all 4 metrics with value + basis)
□ predictions.summary

□ recognition (exactly 4 items)

□ risk_signals (all 7 signals with value + basis + evidence)

□ stages (all 6 stages)

□ breakpoint.stage
□ breakpoint.insight
□ breakpoint.missing_items (3-4 items)

□ decisions (3-4 items with name + status + finding)

□ recommendations.eyebrow
□ recommendations.action
□ recommendations.goals (3-4 items)

□ evidence (all 22 questions with id + stage + question + quote + inference + status)
```

### No Empty Fields

Verify no field contains:
- Empty string ""
- "N/A"
- "Not applicable"
- Placeholder text like "[TO BE FILLED]"

---

## 3. Consistency Checks

### Internal Logic

| Check | Rule | Red Flag |
|-------|------|----------|
| Verdict ↔ Score | Score 7+ = green, 5-6 = amber, 1-4 = red | Score 7 with red verdict |
| Breakpoint ↔ Stages | Breakpoint stage matches worst stage verdict | Breakpoint = "compare" but compare is OK |
| Decisions ↔ Evidence | Decision gaps cite actual missing/partial questions | Decision cites Q8 but Q8 is clear |
| Recommendations ↔ Decisions | Recommendations address the identified decision gaps | Recommendation for something not in decisions |

### Signal Logic

| Check | Rule | Red Flag |
|-------|------|----------|
| Message Priority | Based on Q3, Q4, Q5 | Cites questions outside Make Sense stage |
| Buyer Focus | Based on Q6, Q7 | Cites questions outside Self-Select stage |
| Why Act Now | Based on Q4, Q5 | Cites questions outside Make Sense stage |
| Proof Relevance | Based on Q11, Q12, Q14 | Cites questions outside Validate stage |
| Explanation Burden | Based on Q1, Q2, Q10 | Cites questions outside Land/Compare |
| Internal Sharing | Based on Q11-Q14, Q22 | Cites unrelated questions |
| Mixed Signals | Based on Q15, Q19, Q20 | Cites unrelated questions |

---

## 4. Voice Compliance Checks

### AI Tells Scan

Search the entire report for these patterns and REMOVE:

```
□ "It's not X, it's Y" (negative parallelism)
□ "It's worth noting that..."
□ "It's important to understand..."
□ "This highlights..."
□ "Notably..."
□ "Interestingly..."
□ "In summary..."
□ "Ultimately..."
□ "Overall..."
□ "Research suggests..."
□ "Many buyers might..."
□ "—" (em dash)
□ "serves as"
□ "functions as"
□ "leverages"
□ "utilizes"
□ "fascinating"
□ "remarkable"
□ "significant"
□ "crucial"
□ "critical"
```

### Tone Check

| Element | Check | Red Flag |
|---------|-------|----------|
| Headline | Direct, names failures | Hedged ("may have some issues") |
| Evidence inferences | Specific buyer consequence | Vague ("could cause confusion") |
| Recognition signals | Sound like real skeptical buyers | Sound like AI ("I wonder if...") |
| Recommendations | Include specific examples | Abstract advice ("enhance clarity") |

---

## 5. Evidence Quality Checks

### Quote Validity

| Check | Rule | Red Flag |
|-------|------|----------|
| Real quotes | Quotes must appear on actual homepage | Quote not found in source |
| Appropriate length | 5-20 words per quote | Full paragraph quoted |
| Representative | Quote represents the actual content | Quote cherry-picked or out of context |

### Inference Validity

| Check | Rule | Red Flag |
|-------|------|----------|
| Grounded | Inference follows from quote | Inference unrelated to quote |
| Specific | States buyer consequence | Vague ("this is unclear") |
| Consistent | Status matches inference | "Clear" status but inference says "unclear" |

### Status Assignment

| Check | Rule | Red Flag |
|-------|------|----------|
| Clear | Question fully answered | Generous clear on weak evidence |
| Partial | Some evidence but incomplete | Harsh partial on clear evidence |
| Missing | No evidence found | Missing when evidence exists |

---

## 6. Calibration Sanity Checks

### Score Distribution Reality Check

Based on typical homepage quality:
- Score 9-10: Rare (<5%). Only exceptional homepages.
- Score 7-8: Uncommon (~20%). Well-built homepages.
- Score 5-6: Common (~40%). Average with gaps.
- Score 3-4: Common (~25%). Significant work needed.
- Score 1-2: Uncommon (~10%). Fundamentally broken.

If your scores skew heavily toward any extreme, recalibrate.

### Comparison Test

If you have prior reports, compare:
- Does a score-7 homepage look better than a score-5?
- Does the breakpoint match where buyers would actually stall?
- Do the predictions match what you'd expect from sales?

---

## 7. Final Review Questions

Before delivery, answer these:

1. **Would a founder trust this?** Does the diagnosis sound like it came from someone who understands their business, or from a tool?

2. **Is the score fair?** Would you defend this score in a conversation with the founder?

3. **Are recommendations actionable?** Could the founder start on these today without further clarification?

4. **Would sales recognize these objections?** Do the recognition signals match what actually gets asked on calls?

5. **Is there any AI smell?** Read the diagnosis aloud. Does it sound human?

---

## QA Failure Modes

### Common Errors to Catch

| Error | Symptom | Fix |
|-------|---------|-----|
| Score inflation | Score 7+ but multiple missing questions | Recalculate using scoring rules |
| Signal mismatch | "Strong" proof relevance but Q12 is missing | Re-evaluate signal |
| Vague recommendations | "Improve messaging clarity" | Add specific example |
| Generic recognition | "Is this right for us?" | Make buyer-specific and skeptical |
| Evidence invention | Quote not on actual homepage | Re-fetch and verify |
| Hedged diagnosis | "May have some challenges" | Rewrite with direct language |

---

## QA Sign-Off

Before marking a report complete:

```
□ Calibration checks passed
□ Completeness checks passed
□ Consistency checks passed
□ Voice compliance passed
□ Evidence quality verified
□ Sanity check passed
□ Final review questions answered
```

If any check fails, revise and re-run QA.
