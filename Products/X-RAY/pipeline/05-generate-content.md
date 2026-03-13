# Pipeline Step 05: Generate Content
## X-RAY v5.3 — Write narrative content with voice discipline

---

## Consistency Anchor

**Do NOT change any previous outputs.**

All narrative content must be consistent with:
- `evidence` array (the facts)
- `stages` and `score` (the calculation)
- `risk_signals` and `predictions` (the analysis)

If evidence says Q5 is MISSING, content cannot claim urgency exists.

---

## Input from Step 04
- `meta` object
- `evidence` array
- `stages` object
- `score` object
- `risk_signals` object
- `predictions` object

## Output to Step 06
- All previous fields (unchanged — do not modify)
- `diagnosis` object
- `recognition` array (4 items)
- `breakpoint` object
- `decisions` array (3-4 items)
- `recommendations` object

---

## Voice Rules

### The Core Voice Standard

**Direct, not hedged.** Name the problem plainly.
**Economic framing.** Costs money / makes money.
**Specific, not vague.** Include examples.
**ESL-accessible.** No US idioms.

### Banned Phrases — Scan and Remove

Before finalizing any content, carefully scan for and remove:

**Negative parallelisms:**
- "It's not X, it's Y"
- "This isn't about X. It's about Y."
- Any "not X, but Y" construction

**Hollow transitions:**
- "It's worth noting that..."
- "It's important to understand..."
- "This highlights..."
- "Notably..."
- "Interestingly..."
- "In summary..."
- "Ultimately..."
- "Overall..."

**Vague attribution:**
- "Many buyers might..."
- "Research suggests..."
- "Most prospects..."

**Punctuation:**
- Em dashes (—) — replace with periods or commas

**Inflated verbs:**
- "serves as" → is
- "functions as" → is
- "leverages" → uses
- "utilizes" → uses

**Promotional inflation:**
- "fascinating"
- "remarkable"
- "significant"
- "crucial"
- "critical"

---

## Part 1: Diagnosis

### 1A: Verdict

Map score to verdict:
- Score 7-10 → "Ready for Outbound" (verdict_class: green)
- Score 5-6 → "Proceed with Caution" (verdict_class: amber)
- Score 1-4 → "Fix Before Outbound" (verdict_class: red)

### 1B: Headline

Write one sentence (20-40 words) that names:
1. What's working (if anything)
2. 2-3 specific failures

**Pattern:** `[What's working], but [failure 1], [failure 2], and [failure 3]`

**Good examples:**
- "Homepage is well-built, but urgency is missing and proof shows activity, not outcomes"
- "Pain resonates, but buyers cannot place LabV in a known category, justify the switch, or take a safe first step"
- "Category is clear and targeting is tight, but no cost of waiting and no ROI ammunition for the champion"

**Bad examples (avoid):**
- "There may be some opportunities to improve" (hedged)
- "The homepage has challenges in several areas" (vague)
- "It's not a copy problem. It's a structure problem." (negative parallelism)

### 1C: Text

Write 2-3 sentences explaining:
1. What will happen when outbound starts
2. Why buyers will stall (specific causes from evidence)
3. The consequence if not fixed

**Good example:**
"This is a strong homepage. Category is clear, pain is specific, alternatives are named. The gaps are in urgency (no cost of waiting) and validation (metrics show activity not results). Buyers will respond but deals may drift without urgency framing, and champions will struggle to justify spend without ROI ammunition."

---

## Part 2: Recognition Signals

Generate exactly 4 expected objections that buyers will raise on sales calls.

### Rules
- Phrase as direct quotes (in quotation marks)
- Sound like real skeptical buyers, not polite inquiries
- Tie each to a specific gap in the evidence
- Cover different concerns: category, comparison, risk, timing, budget

### Pattern — Convert Evidence Gaps to Objections

| Gap (from evidence) | Objection Pattern |
|---------------------|-------------------|
| Q1 partial/missing | "So is this like [category]? How is it different from [known thing]?" |
| Q5 missing | "This sounds interesting for next quarter. What's the rush?" |
| Q8 missing | "We already have [current tool]. Why would we switch?" |
| Q12 partial | "Do you have customers like us? What results did they actually get?" |
| Q17 missing | "This sounds like a big commitment. What's the minimum we can try?" |
| Q20 missing | "What does this actually cost? We need to know before booking a demo." |
| Q22 missing | "My boss will ask about ROI. What can I show them?" |

**Good examples:**
- "What does this actually cost? We need to know if this fits our budget before a demo."
- "We already have a data management system. Why would we switch?"
- "Do you have planning firms like us? Same size, same project types?"
- "We're not launching a project right now. Can we look at this when we win the next RFP?"

**Bad examples (avoid):**
- "I wonder if this solution might be appropriate for our organization" (too soft)
- "Could you explain more about your value proposition?" (AI-sounding)

---

## Part 3: Breakpoint

### 3A: Identify Breakpoint Stage

Find the **first** stage with verdict "break". If no breaks, find the **first** stage with verdict "weak".

Order: land → make_sense → self_select → compare → validate → commit

### 3B: Stage Class
- Break → stage_class: red
- Weak → stage_class: amber

### 3C: Insight

Write 2-3 sentences explaining:
1. What buyers understand at this point in the journey
2. Why they stall at this specific stage
3. What's missing that would keep them moving

**Must be grounded in evidence.** Cite specific missing questions.

### 3D: Missing Items

List 3-4 specific things buyers cannot find. Each item:
- `text`: Specific thing missing
- `status`: "missing" or "partial"

**Good examples:**
- "Cost of inaction if they wait another 6 months" (missing)
- "Outcome metrics: hours saved per project, margin improvement" (partial)
- "Role titles on testimonials: Partner vs. Project Manager" (partial)
- "Indicative pricing: budget qualification without booking a call" (missing)

**Bad examples (avoid):**
- "Clear value proposition" (too vague)
- "Better messaging" (not specific)

---

## Part 4: Decision Gaps

Identify 3-4 strategic decisions that are unclear or missing.

### Decision Mapping

| Decision Name | Evidence Question | Signs It's Missing |
|---------------|-------------------|-------------------|
| Category Clarity | Q1 | Partial or missing |
| Named Alternative | Q8 | Partial or missing |
| Why Act Now | Q5 | Partial or missing |
| Safe First Step | Q17 | Missing |
| Risk Reversal | Q17 | Partial |
| Pricing Visibility | Q20 | Partial or missing |
| Outcome Results | Q12 | Partial or missing |
| ROI Ammunition | Q22 | Partial or missing |

### For Each Decision

- `name`: Decision name
- `status`: clear / partial / missing (from evidence)
- `status_label`: Human-readable label (Clear, Unclear, Implicit, Weak, Missing, Scattered, Vanity)
- `finding`: One sentence explaining the gap with specific example of what's needed

**Good finding example:**
"Pain is clear but no cost of waiting. 'Every RFP without structured engagement costs X hours of consolidation' would create urgency."

**Bad finding example:**
"Could be improved with better urgency messaging" (too vague, no example)

---

## Part 5: Recommendations

### 5A: Eyebrow

Choose based on severity:
- Score 7+: "Light Refinement — Not a Major Rebuild"
- Score 5-6: "Recommended Path"
- Score 1-4: "Critical Fix Required"

### 5B: Action

Write the main action headline:
- Score 7+: "This homepage is already strong. [N] targeted additions would close the gaps:"
- Score 5-6: "Before scaling outbound, address these [N] gaps:"
- Score 1-4: "Buying Path Readiness Sprint before outbound begins"

### 5C: Goals

Generate 3-4 specific actions. Each goal:
- `label`: Verb-noun format ("Add Urgency Framing", "Name the Alternative")
- `description`: Specific action with example text the founder could actually use

**Good examples:**
```
label: "Add Urgency Framing"
description: "Quantify the cost of manual engagement. 'Every project without structured engagement costs X hours of consolidation' or 'RFPs without digital methodology win Y% less often.'"
```

```
label: "Swap Vanity for Outcome Metrics"
description: "Replace '250+ projects' with customer outcomes: '60% less time from feedback to report' or 'X hours saved per project on average.'"
```

**Bad examples:**
```
label: "Improve Messaging"
description: "Make the messaging clearer and more compelling." (no specific example)
```

---

## Output Format

```json
{
  "meta": { ... unchanged ... },
  "evidence": [ ... unchanged ... ],
  "stages": { ... unchanged ... },
  "score": { ... unchanged ... },
  "risk_signals": { ... unchanged ... },
  "predictions": { ... unchanged ... },
  "diagnosis": {
    "verdict": "Proceed with Caution",
    "verdict_class": "amber",
    "headline": "Homepage is well-built, but urgency is missing and proof shows activity, not outcomes",
    "text": "This is a strong homepage. Category is clear, pain is specific, alternatives are named. The gaps are in urgency (no cost of waiting) and validation (metrics show activity not results). Buyers will respond but deals may drift."
  },
  "recognition": [
    "What does this actually cost? We need to know if this fits our budget before a demo.",
    "Our current tools work okay. What would we actually save by switching?",
    "Do you have planning firms like us — same size, same project types?",
    "We're not launching a project right now. Can we look at this when we win the next RFP?"
  ],
  "breakpoint": {
    "stage": "validate",
    "stage_class": "amber",
    "insight": "Buyers understand the value and want to believe, but the proof doesn't give them ammunition. Testimonials lack role titles. Metrics show activity not outcomes. When the partner asks 'what will this save us?' the project manager has no answer.",
    "missing_items": [
      { "text": "Outcome metrics: hours saved per project, margin improvement", "status": "partial" },
      { "text": "Role titles on testimonials: Partner vs. Project Manager", "status": "partial" },
      { "text": "Indicative pricing: budget qualification without booking a call", "status": "missing" }
    ]
  },
  "decisions": [
    {
      "name": "Why Act Now",
      "status": "partial",
      "status_label": "Weak",
      "finding": "Pain is clear but no cost of waiting. 'Every RFP without structured engagement is a competitive disadvantage' would create urgency."
    }
  ],
  "recommendations": {
    "eyebrow": "Light Refinement — Not a Major Rebuild",
    "action": "This homepage is already strong. Four targeted additions would close the gaps:",
    "goals": [
      {
        "label": "Add Urgency Framing",
        "description": "Quantify the cost of manual engagement. 'Every project without structured engagement costs X hours of consolidation.'"
      }
    ]
  }
}
```

---

## Voice Check Before Output

Carefully scan all generated content for banned phrases:

- [ ] No "It's not X, it's Y" anywhere
- [ ] No "It's worth noting", "Notably", "Interestingly"
- [ ] No em dashes (—)
- [ ] All recommendations have specific examples
- [ ] Recognition signals sound like real skeptical buyers
- [ ] All findings cite evidence, not assumptions

---

## Pass to Next Step

After generating all narrative content, pass the output JSON to **Step 06: QA & Output**.

**CRITICAL CONSISTENCY RULE:** All content must be grounded in evidence from Step 01. Do not claim things that aren't in the evidence.
