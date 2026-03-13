# X-RAY Protocol: 05 — Generation
## v5.3

---

## Overview

This document describes how to generate the narrative content in an X-RAY report: diagnosis, recognition signals, breakpoint analysis, decision gaps, and recommendations.

---

## 1. Diagnosis Generation

The diagnosis has three parts: **verdict**, **headline**, and **text**.

### Verdict
Map the score to an action verdict:
- Score 7-10 → "Ready for Outbound" (green)
- Score 5-6 → "Proceed with Caution" (amber)
- Score 1-4 → "Fix Before Outbound" (red)

### Headline
One sentence that names the **core finding** and **2-3 specific failures**.

**Pattern:**
`[What's working], but [failure 1], [failure 2], and [failure 3]`

**Examples:**
- "Homepage is strong — but buyers cannot compare Fletch to alternatives or explore depth without booking a call"
- "Pain resonates, but buyers cannot place LabV, justify the switch, or take a safe first step"

### Text
2-3 sentences expanding on the headline:
1. What will happen when outbound starts
2. Why buyers will stall (specific causes)
3. What's missing or unclear

---

## 2. Recognition Signals Generation

Generate **4 expected objections** that buyers will raise on sales calls.

### Rules:
- Phrase as direct quotes (in quotation marks)
- Tie each objection to a specific gap in the evidence
- Cover different concerns: category confusion, comparison, risk, timing

### Pattern:
Look at missing/partial questions and convert to buyer objections:

| Gap | Objection Pattern |
|-----|-------------------|
| Q1 unclear | "So is this like [known category]? How is it different?" |
| Q8 missing | "We already have [alternative]. Why would we switch?" |
| Q5 missing | "Is this the right time, or should we wait?" |
| Q17 missing | "This sounds like a big project. What's the minimum commitment?" |
| Q11-12 weak | "Who else in our industry uses this? Can we talk to them?" |

---

## 3. Breakpoint Analysis

Identify the **first stage** where momentum breaks (verdict = "break").

If no breaks exist, identify the **weakest stage** (verdict = "weak").

### Breakpoint Object:
- **stage**: The stage name (or "none" if no issues)
- **stage_class**: red (break) or amber (weak)
- **insight**: 2-3 sentences explaining why buyers stall here
- **missing_items**: 3-4 specific things buyers cannot find

### Insight Pattern:
`Buyers [understand/do X] but cannot [do Y]. The homepage [does Z] but never [does A].`

### Missing Items Pattern:
- What project this serves
- Cost of inaction / timing pressure
- Proof from customers like them
- A safe first step

---

## 4. Decision Gaps Generation

Identify **3-4 strategic decisions** that are unclear or missing.

### Common Decision Gaps:

| Decision | What It Means | Signs It's Missing |
|----------|---------------|-------------------|
| Category | What bucket does this fit in? | Q1 partial/missing, invented terminology |
| Alternative | What am I switching from? | Q8 partial/missing, competitor not named |
| Why Act Now | Why not wait? | Q5 partial/missing, no cost of inaction |
| First Step | How do I try this safely? | Q17 missing, high-commitment CTA only |
| Differentiation | Why this vs. alternatives? | Q9-Q10 partial, generic claims |
| Risk Reversal | What if it doesn't work? | Q17 partial, no guarantee/pilot |

### Status Labels:
- **Missing** → "Missing"
- **Partial** → "Unclear", "Implicit", "Weak", or "Scattered" (choose based on nature)

---

## 5. Recommendations Generation

Generate a **sprint recommendation** with:
- **Eyebrow**: Framing phrase
- **Action**: Main action headline
- **Goals**: 3-4 specific actions

### Eyebrow Options:
- "Recommended Path" (for major work needed)
- "Light Refinement — Not a Major Rebuild" (for minor gaps)
- "Quick Wins" (for polishing)

### Action Pattern:
`[Intervention type] before [milestone]`

Examples:
- "Buying Path Readiness Sprint before outbound begins"
- "This homepage is already strong. Three targeted additions would close the gaps:"

### Goals Pattern:
Each goal has a **label** (bold) and **description**:

```
→ **Define Category:** Position against a buyer-recognized bucket — "LIMS alternative" or own "R&D operating system" with clear boundaries.
```

### Common Goal Types:
- **Define Category**: Fix Q1
- **Define Alternative**: Fix Q8-Q9
- **Define Why Now**: Fix Q5
- **Define First Step**: Fix Q17
- **Add Proof**: Fix Q11-Q14
- **Add Risk Reversal**: Fix Q17

---

## 6. Progress Indicators

Generate **3-4 leading indicators** to track after implementing fixes.

### Pattern:
| What to Track | Direction |
|---------------|-----------|
| [Observable behavior] | Should [increase/decrease] after [fix] |

### Examples:
- "What is this?" asked on sales calls → Should decrease after category clarity
- Demo-to-qualified conversion rate → Should improve as proof match strengthens
- Time from first touch to internal champion → Should shorten as internal sharing improves

---

## Output Quality Checklist

Before returning the report, verify:

- [ ] Headline names specific failures (not generic "unclear messaging")
- [ ] Recognition signals are phrased as buyer quotes
- [ ] Breakpoint insight explains causality (why buyers stall)
- [ ] Decision gaps map to specific questions
- [ ] Recommendations are actionable and specific
- [ ] All evidence quotes come from the actual homepage
- [ ] Score matches the evidence (calibration check)
