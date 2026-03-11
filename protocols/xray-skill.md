# X-RAY Diagnostic Skill

Use this skill when the user says "run X-RAY on [URL]", "X-RAY this homepage", "diagnose [company]", or any variation of requesting a Buying Path diagnostic.

---

## What This Produces

An **Outbound Readiness X-RAY** report evaluating whether a homepage can support cold outbound sales. Output is a downloadable HTML file.

---

## Workflow

### Step 1: Fetch Homepage

Use web_fetch to retrieve the homepage content. Extract all visible text including:
- Hero/headline
- Subheadline
- Body copy
- Features/benefits
- Testimonials
- CTAs
- Pricing (if visible)
- Footer

### Step 2: Score 15 Buyer Questions

For each question, evaluate against the homepage and assign:
- **CLEAR**: Buyer's question is answered. They can proceed.
- **PARTIAL**: Something present but incomplete. Buyer hesitates.
- **MISSING**: Not addressed. Momentum breaks.

**Every finding MUST quote actual homepage text.**

#### Questions by Stage

**LAND (Can I categorize this in 3 seconds?)**
- Q1: What is this?
- Q2: What category is this in?

**MAKE SENSE (Is this pain worth switching for?)**
- Q3: What pain is worth switching for?
- Q4: What are the stakes if I do nothing?

**SELF-SELECT (Is this for me?)**
- Q5: Is this for my team?
- Q6: Is this for my situation?

**COMPARE (Why this vs. alternatives?)**
- Q7: What am I switching from?
- Q8: Why do those alternatives fail?
- Q9: What makes you different?

**VALIDATE (Does this actually work?)**
- Q10: Does this work for real teams?
- Q11: What results have others achieved?
- Q12: How much effort is this?

**COMMIT (What's my first step?)**
- Q13: What is the first step?
- Q14: Does this feel safe to try?
- Q15: What happens after I click?

### Step 3: Compute Stage Verdicts

For each of the 6 stages:
- **OK**: All questions CLEAR, or majority CLEAR with none MISSING
- **WEAK**: Any PARTIAL and none MISSING
- **BREAK**: Any MISSING

### Step 4: Compute Overall Verdict

| Verdict | Rule |
|---------|------|
| **RED** | Any stage BREAKS, OR 3+ stages WEAK, OR ≤2 stages pass |
| **AMBER** | No stage BREAKS, AND 1-2 stages WEAK, AND 3-4 stages pass |
| **GREEN** | ≤1 stage WEAK, AND ≥5 stages pass |

### Step 5: Generate Report Content

**Diagnosis (under 50 words):**
- Predict specific buyer behavior
- Name the exact break point
- Quote observed homepage text

**Breakpoint insight:**
- Name ONE primary stage
- Explain what buyers CAN understand vs. CANNOT find

**Expect to hear (4 objections):**
- Written in buyer voice
- Specific to THIS company's gaps

**Sprint goals (3-4):**
- Reference specific decisions
- Give concrete instructions

### Step 6: Generate HTML Report

Use the template structure with:
- Header: company name, URL, date, target buyer
- Verdict banner: score, status, headline, diagnosis
- Implication box: 4 metrics + expect to hear
- Stage flow: 6 stages with verdicts
- Breakpoint discovery: primary friction + missing signals
- Evidence table: 15 questions with findings
- Next step box: recommended action + goals

Save to `/mnt/user-data/outputs/xray-[company].html`

---

## Quality Standards

### Voice Rules
- Never use "fuzzy" → use "unclear" or "partial"
- Never use em dashes
- ESL accessible
- Quote actual homepage text in findings

### Diagnosis Quality
The diagnosis must:
1. Predict specific buyer behavior ("Outbound will generate interest because...")
2. Name the exact break point
3. Quote observed text as evidence
4. Stay under 50 words
5. Avoid insulting the company

### Reference Example (Product.Zone - AMBER)

**Diagnosis:** "Outbound will work because the pain signals are specific and recognizable: 'founder in every deal,' 'deck on version eleven.' But prospects will hesitate because they cannot tell what category Product.Zone fits in, and they have no frame for comparing it to agencies or positioning consultants."

**Breakpoint:** Compare

**Expect to hear:**
- "So is this like a positioning consultant?"
- "How is this different from hiring an agency?"
- "We were thinking of a fractional CMO. Why this instead?"

---

## HTML Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>X-RAY · {{COMPANY}}</title>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Barlow+Condensed:wght@400;600;700;800;900&family=Barlow:wght@400;500;600&display=swap" rel="stylesheet">
  <style>
    :root { --teal: #33C4D9; --orange: #F5A623; --green: #2ECC71; --red: #C0392B; --black: #0a0a0a; }
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Barlow', sans-serif; background: #333; line-height: 1.5; }
    .report { width: 900px; background: #fff; margin: 40px auto; padding: 48px 56px; box-shadow: 0 4px 24px rgba(0,0,0,0.15); }
    .report-header { margin-bottom: 20px; padding-bottom: 20px; border-bottom: 2px solid #D8D6CF; }
    .report-eyebrow { font-family: 'Space Mono', monospace; font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--teal); margin-bottom: 8px; }
    .report-title { font-family: 'Barlow Condensed', sans-serif; font-size: 36px; font-weight: 800; margin-bottom: 16px; }
    .context-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 16px; }
    .context-item { background: #F5F4EF; border-radius: 6px; padding: 12px 16px; }
    .context-label { font-family: 'Space Mono', monospace; font-size: 9px; letter-spacing: 0.08em; text-transform: uppercase; color: #888; margin-bottom: 4px; }
    .verdict-banner { border-radius: 8px; padding: 24px; margin: 24px 0; }
    .verdict-banner.red { background: rgba(192,57,43,0.06); border: 2px solid var(--red); }
    .verdict-banner.amber { background: rgba(245,166,35,0.06); border: 2px solid var(--orange); }
    .verdict-banner.green { background: rgba(46,204,113,0.06); border: 2px solid var(--green); }
    .verdict-top { display: flex; align-items: flex-start; gap: 24px; margin-bottom: 16px; }
    .verdict-number { font-family: 'Barlow Condensed', sans-serif; font-size: 48px; font-weight: 900; text-align: center; min-width: 100px; }
    .verdict-number.red { color: var(--red); } .verdict-number.amber { color: var(--orange); } .verdict-number.green { color: var(--green); }
    .verdict-breakdown { margin-top: 8px; font-family: 'Space Mono', monospace; font-size: 10px; line-height: 1.6; text-align: center; }
    .verdict-main { flex: 1; }
    .verdict-status { font-family: 'Space Mono', monospace; font-size: 11px; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 4px; }
    .verdict-status.red { color: var(--red); } .verdict-status.amber { color: var(--orange); } .verdict-status.green { color: var(--green); }
    .verdict-headline { font-family: 'Barlow Condensed', sans-serif; font-size: 24px; font-weight: 700; }
    .diagnosis-box { background: var(--black); border-radius: 6px; padding: 20px 24px; margin-top: 16px; }
    .diagnosis-label { font-family: 'Space Mono', monospace; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--teal); margin-bottom: 8px; }
    .diagnosis-text { font-size: 16px; color: #F0EFE9; line-height: 1.5; font-weight: 500; }
    .implication-box { background: #F5F4EF; border-radius: 8px; padding: 20px 24px; margin-bottom: 28px; }
    .implication-header { font-family: 'Space Mono', monospace; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: #888; margin-bottom: 16px; }
    .implication-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px; margin-bottom: 16px; }
    .implication-item { text-align: center; padding: 12px 8px; background: #fff; border-radius: 6px; }
    .implication-metric { font-family: 'Barlow Condensed', sans-serif; font-size: 16px; font-weight: 700; margin-bottom: 4px; }
    .implication-metric.good { color: var(--green); } .implication-metric.weak { color: var(--orange); } .implication-metric.poor { color: var(--red); }
    .implication-label { font-family: 'Space Mono', monospace; font-size: 8px; letter-spacing: 0.05em; text-transform: uppercase; color: #888; }
    .expect-box { margin-top: 12px; padding: 12px 16px; background: #fff; border-radius: 6px; border-left: 3px solid var(--orange); }
    .section { margin-bottom: 28px; }
    .section-header { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; }
    .section-number { width: 24px; height: 24px; background: var(--black); border-radius: 4px; display: flex; align-items: center; justify-content: center; font-family: 'Space Mono', monospace; font-size: 11px; font-weight: 700; color: var(--teal); }
    .section-title { font-family: 'Barlow Condensed', sans-serif; font-size: 18px; font-weight: 700; }
    .stage-flow { display: flex; align-items: center; gap: 4px; margin-bottom: 16px; }
    .stage-cell { flex: 1; border-radius: 6px; padding: 12px 8px; text-align: center; }
    .stage-cell.break { background: rgba(192,57,43,0.10); border: 1px solid var(--red); }
    .stage-cell.weak { background: rgba(245,166,35,0.10); border: 1px solid var(--orange); }
    .stage-cell.ok { background: rgba(46,204,113,0.10); border: 1px solid var(--green); }
    .stage-label { font-family: 'Space Mono', monospace; font-size: 8px; letter-spacing: 0.06em; text-transform: uppercase; color: #888; margin-bottom: 2px; }
    .stage-status { font-family: 'Barlow Condensed', sans-serif; font-size: 13px; font-weight: 700; }
    .stage-cell.break .stage-status { color: var(--red); }
    .stage-cell.weak .stage-status { color: var(--orange); }
    .stage-cell.ok .stage-status { color: var(--green); }
    .stage-arrow { font-size: 14px; color: #888; }
    .breakpoint-box { background: var(--black); border-radius: 8px; padding: 20px 24px; }
    .breakpoint-eyebrow { font-family: 'Space Mono', monospace; font-size: 9px; letter-spacing: 0.1em; text-transform: uppercase; color: rgba(255,255,255,0.4); margin-bottom: 4px; }
    .breakpoint-stage { font-family: 'Barlow Condensed', sans-serif; font-size: 28px; font-weight: 800; margin-bottom: 12px; }
    .breakpoint-stage.red { color: var(--red); } .breakpoint-stage.amber { color: var(--orange); } .breakpoint-stage.green { color: var(--green); }
    .breakpoint-insight { font-size: 15px; color: #F0EFE9; margin-bottom: 16px; line-height: 1.5; }
    .missing-signals { border-top: 1px solid rgba(255,255,255,0.1); padding-top: 16px; }
    .missing-header { font-family: 'Space Mono', monospace; font-size: 9px; color: rgba(255,255,255,0.4); margin-bottom: 8px; }
    .missing-item { color: #F0EFE9; font-size: 13px; margin-bottom: 6px; }
    .missing-x { color: var(--red); margin-right: 8px; }
    .core-divider { margin: 32px 0; padding: 12px 0; border-top: 2px solid #D8D6CF; border-bottom: 1px solid #ECEAE3; text-align: center; }
    .core-divider-text { font-family: 'Space Mono', monospace; font-size: 9px; letter-spacing: 0.12em; text-transform: uppercase; color: #888; }
    .evidence-table { width: 100%; border-collapse: collapse; font-size: 12px; }
    .evidence-table th { background: #F5F4EF; font-family: 'Space Mono', monospace; font-size: 9px; letter-spacing: 0.06em; text-transform: uppercase; color: #888; padding: 8px 10px; text-align: left; border-bottom: 1px solid #D8D6CF; }
    .evidence-table td { padding: 10px; border-bottom: 1px solid #ECEAE3; vertical-align: top; }
    .stage-badge { font-family: 'Space Mono', monospace; font-size: 9px; letter-spacing: 0.04em; text-transform: uppercase; padding: 2px 6px; border-radius: 3px; margin-right: 6px; background: rgba(51,196,217,0.15); color: var(--teal); }
    .status-badge { display: inline-block; padding: 3px 8px; border-radius: 3px; font-family: 'Space Mono', monospace; font-size: 9px; font-weight: 700; letter-spacing: 0.04em; }
    .status-badge.missing { background: rgba(192,57,43,0.12); color: var(--red); }
    .status-badge.partial { background: rgba(245,166,35,0.12); color: var(--orange); }
    .status-badge.clear { background: rgba(46,204,113,0.12); color: var(--green); }
    .next-step-box { background: #F5F4EF; border: 2px solid var(--teal); border-radius: 8px; padding: 20px 24px; }
    .next-step-label { font-family: 'Space Mono', monospace; font-size: 10px; letter-spacing: 0.1em; text-transform: uppercase; color: var(--teal); margin-bottom: 6px; }
    .next-step-action { font-family: 'Barlow Condensed', sans-serif; font-size: 20px; font-weight: 700; margin-bottom: 12px; }
    .goal-item { margin-bottom: 6px; font-size: 14px; }
    .goal-arrow { color: var(--teal); margin-right: 8px; }
    .outcome-section { border-top: 1px solid #D8D6CF; padding-top: 16px; margin-top: 16px; font-size: 14px; color: #555; }
    .report-footer { margin-top: 32px; padding-top: 20px; border-top: 1px solid #D8D6CF; display: flex; justify-content: space-between; align-items: center; }
    .footer-brand { font-family: 'Space Mono', monospace; font-size: 11px; letter-spacing: 0.1em; color: var(--teal); }
    .footer-method { font-family: 'Space Mono', monospace; font-size: 9px; color: #888; }
  </style>
</head>
<body>
<div class="report">
  <!-- Fill in sections per workflow -->
</div>
</body>
</html>
```

---

## Trigger Phrases

- "Run X-RAY on [URL]"
- "X-RAY [company]"
- "Diagnose [URL]"
- "Check outbound readiness for [URL]"
- "Buying path audit for [company]"
- "Score this homepage: [URL]"

---

## Output Location

Save HTML to: `/mnt/user-data/outputs/xray-[company-name].html`

Present file to user with brief summary of verdict and primary breakpoint.
