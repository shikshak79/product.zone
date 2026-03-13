# Pipeline Step 01: Score Questions
## X-RAY v5.3 — Evaluate 22 buying path questions with scoring discipline

---

## Input from Step 00
- `meta` object (company, url, target_buyer, date, version)
- `homepage_content` (full text of homepage)

## Output to Step 02
- `meta` object (unchanged)
- `evidence` array (22 question evaluations)

---

## ⚠️ ANTI-HALLUCINATION RULES (READ FIRST)

### Quote Verification Rule

**Every quote MUST appear VERBATIM in `homepage_content` from Step 00.**

- COPY-PASTE exact text. Do not paraphrase.
- Do not invent plausible-sounding quotes.
- Do not use training knowledge about what homepages "usually say."
- If you cannot find relevant text, use: `quote: "Not found on homepage"`

### If Evidence Not Found

When you cannot find text that answers a question:
```
quote: "Not found on homepage"
inference: "[Explain what's missing and the buyer consequence]"
status: "missing"
```

### Verification Check

Before finalizing each quote, verify:
1. Search `homepage_content` for the exact phrase
2. If not found verbatim, do NOT use it
3. If you're uncertain, mark as MISSING rather than invent

**Hallucination = Failure.** An invented quote invalidates the entire report.

---

## Scoring Discipline

### The Core Rule

**CLEAR requires explicit statement.**

If the buyer must interpret wording, infer meaning, or connect dots, status is PARTIAL.

If there is no relevant content anywhere on the page, status is MISSING.

### Position Matters

- Evidence in `[EARLY]` = prominent, can be CLEAR
- Evidence in `[MID]` = present but not leading
- Evidence only in `[LATE]` or `[FAQ]` = buried, typically PARTIAL
- Evidence only in `[TESTIMONIAL]` = not primary messaging, typically PARTIAL

### Common Scoring Errors

| Error | Example | Correct Status |
|-------|---------|----------------|
| Generous interpretation | "AI-powered platform" → assumes buyer knows the category | PARTIAL |
| Credited implied meaning | Pain mentioned in testimonial, not hero | PARTIAL |
| Missed buried evidence | Category in footer FAQ | PARTIAL (found but buried) |
| Invented evidence | "They probably have this..." | Must cite actual text |

---

## Questions with Precise Scoring Criteria

### LAND (Q1-Q2)

#### Q1: What is this? (Category)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Category is explicitly named AND buyer can immediately place it in a known bucket (e.g., "CRM", "LIMS", "ERP", "Community Engagement Platform"). No interpretation needed. Appears in hero or above-fold. |
| **PARTIAL** | Category is described but uses invented terms, acronyms without definition, or requires explanation. OR category is clear but buried below-fold. |
| **MISSING** | No category visible. Only features, benefits, or vague descriptors ("The future of work"). |

#### Q2: What do you do? (Core Function)

| Status | Criteria |
|--------|----------|
| **CLEAR** | One-sentence explanation of core capability in hero or first screen. Buyer can explain to someone else in 10 seconds. |
| **PARTIAL** | Function is described but scattered across sections, uses jargon, or requires reading multiple paragraphs to understand. |
| **MISSING** | No clear function statement. Only abstract benefits or outcomes without explaining what the product does. |

---

### MAKE SENSE (Q3-Q5)

#### Q3: Pain worth switching? (Named Pain)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Specific pain is explicitly named in hero or above-fold AND it matches target buyer's world. Buyer thinks "that's my problem." Example: "Fragmented tools slow projects down." |
| **PARTIAL** | Pain is mentioned but generic ("save time"), buried below-fold, or stated only in testimonials rather than main messaging. |
| **MISSING** | No pain named. Only positive outcomes or features without acknowledging the problem being solved. |

#### Q4: What project? (Buyer's Task)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Specific task, project, or job buyer is trying to complete is explicitly named. "When you're running community engagement for planning projects..." or "For teams onboarding new hires..." |
| **PARTIAL** | Task is implied but not explicitly stated, or multiple tasks mentioned without clarity on primary use case. |
| **MISSING** | No buyer task visible. Product-centric messaging only ("We do X") without buyer-centric framing ("When you need to Y"). |

#### Q5: Why act now? (Stakes/Urgency)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Cost of waiting is explicitly quantified ("Every month without X costs you Y hours") OR specific trigger moment is named ("When you hit 50 users...", "Before your next RFP..."). |
| **PARTIAL** | Pain acknowledged but no cost of inaction stated. No timing pressure. Buyer can logically defer to next quarter. |
| **MISSING** | No urgency framing anywhere. Product is presented as "nice to have" with no consequence for waiting. |

---

### SELF-SELECT (Q6-Q7)

#### Q6: For my team? (ICP Signals)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Specific segment is explicitly named: industry ("planning firms"), company size ("teams of 10-50"), or role ("for DevOps teams"). "For [specific segment]..." appears prominently. |
| **PARTIAL** | Multiple segments mentioned (diluted targeting: "for startups, agencies, and enterprises") or segment implied but not stated explicitly. |
| **MISSING** | No ICP signals. "For everyone" positioning or generic B2B messaging that could apply to any company. |

#### Q7: For my situation? (Qualifying Conditions)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Explicit conditions stated for when this works: "Best for teams that have outgrown spreadsheets", "If you're running 5+ projects per year", "Not right for one-off projects". |
| **PARTIAL** | Some situational hints but not explicit qualifying criteria. Buyer must guess if their situation is a fit. |
| **MISSING** | No qualifying conditions. Buyer cannot determine if their specific situation is appropriate. |

---

### COMPARE (Q8-Q10)

#### Q8: Switching from? (Named Alternative)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Alternatives are explicitly named: "Replace your spreadsheet", "Unlike traditional LIMS", "Switching from manual processes + Survey Monkey + Excel". Buyer can see what they're replacing. |
| **PARTIAL** | Alternatives implied ("traditional tools", "legacy systems", "manual processes") but not specifically named. |
| **MISSING** | No alternatives mentioned. Buyer cannot position this against what they currently use. |

#### Q9: Why alternatives fail? (Competitive Weakness)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Specific weaknesses of alternatives are explicitly stated: "Spreadsheets break when you scale", "Traditional LIMS requires 6-month implementation", "Manual consolidation takes 10+ hours per project". |
| **PARTIAL** | General criticism ("outdated", "complex", "expensive") without specific, verifiable failure points. |
| **MISSING** | No competitive positioning. No explanation of why the buyer's current approach doesn't work. |

#### Q10: What's different? (Differentiation)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Unique mechanism, approach, or capability is explicitly stated AND meaningfully different: "One platform instead of five tools", "AI-generated reports vs. manual analysis", "Map-based vs. form-based". |
| **PARTIAL** | Differentiation claimed but generic ("faster", "easier", "better", "modern") without specific mechanism that buyer can evaluate. |
| **MISSING** | No differentiation visible. Could be any product in the category. |

---

### VALIDATE (Q11-Q15)

#### Q11: Teams like mine? (Social Proof)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Named companies in target ICP with logos AND company names visible. Buyer can recognize peer companies in their industry/segment. |
| **PARTIAL** | Logos present but not in target ICP (wrong industry/size), or testimonials without company identification, or "100+ companies" without names. |
| **MISSING** | No social proof. No named customers, no logos, no recognizable references. |

#### Q12: Results achieved? (Quantified Outcomes)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Specific, quantified outcomes with business impact: "60% faster report generation", "Saved $50K per project", "Reduced consolidation time from 10 hours to 30 minutes". |
| **PARTIAL** | Outcomes mentioned but not quantified ("faster", "better results") OR metrics are vanity/activity (250+ projects, 400K participants) not business outcomes. |
| **MISSING** | No outcomes stated. Only features or capability descriptions. |

#### Q13: How much effort? (Implementation Clarity)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Time, resources, or complexity explicitly stated: "Set up in 2 hours", "No IT required", "3-step onboarding", "Launch your first project this week". |
| **PARTIAL** | Effort mentioned but vague ("easy to set up", "quick implementation", "simple onboarding") without specific timeframe or steps. |
| **MISSING** | No implementation information. Buyer has no idea what adoption requires. |

#### Q14: Proof match role? (Role-Specific Proof)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Testimonials include job title AND title matches or is adjacent to target buyer role. For "Project Manager" target: testimonials from Project Managers, Directors of Planning, etc. |
| **PARTIAL** | Testimonials present but no titles ("Dr. Julian Petrin, urbanista"), or titles don't match target buyer (CEO quote for PM buyer). |
| **MISSING** | No testimonials with any role identification, or no testimonials at all. |

#### Q15: Enterprise signals? (Security/Compliance)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Security, compliance, or procurement requirements explicitly addressed: SOC2, GDPR, SSO, dedicated security page, data residency options. |
| **PARTIAL** | Brief mention of security ("GDPR compliant") without detail, or buried in FAQ only. |
| **MISSING** | No enterprise signals visible. (Note: For explicitly SMB-focused products targeting small teams, mark CLEAR if the absence is intentional and appropriate.) |

---

### COMMIT (Q16-Q20)

#### Q16: First step? (CTA Clarity)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Primary CTA is visible above fold AND action is unambiguous ("Start Free Trial", "Book Demo", "Get Started Free"). One dominant CTA. |
| **PARTIAL** | CTA present but multiple competing CTAs with equal prominence, or CTA only below-fold, or action is unclear ("Learn More", "Contact Us" without context). |
| **MISSING** | No clear CTA visible. Buyer doesn't know what action to take. |

#### Q17: Safe to try? (Risk Reversal)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Explicit risk reversal stated prominently: "Free trial, no credit card", "30-day money-back guarantee", "Start with one project free", "Cancel anytime". |
| **PARTIAL** | Low commitment implied but not explicit, or risk reversal buried in fine print/FAQ, or only visible after clicking CTA. |
| **MISSING** | No risk reversal visible. Buyer perceives high commitment required to try. |

#### Q18: After I click? (Process Visibility)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Next steps after CTA are explicitly stated: "Fill out form → we'll respond in 24h", "Instant access, no demo required", "Book a 15-minute call". |
| **PARTIAL** | Some process hints but not explicit timeline or steps. Buyer has partial visibility. |
| **MISSING** | No process information. Buyer has no idea what happens after clicking. |

#### Q19: CTA match readiness? (Motion Fit)

| Status | Criteria |
|--------|----------|
| **CLEAR** | CTA type matches buyer's likely readiness level: cold traffic = trial/content, warm traffic = demo, enterprise = consultation. Appropriate for the target buyer. |
| **PARTIAL** | CTA somewhat appropriate but could be better matched (e.g., only "Book Demo" for PLG product). |
| **MISSING** | CTA mismatch: demanding demo from cold traffic with no alternative, or only self-serve trial for clearly enterprise product. |

#### Q20: Offer match motion? (Pricing/Offer Alignment)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Pricing or offer structure visible AND matches sales motion. Self-serve = transparent pricing page. Enterprise = "contact us" appropriate with clear signal. Buyer can self-qualify on budget. |
| **PARTIAL** | Pricing mentioned but incomplete (no tiers, no range), or pricing model unclear, or "contact us" for clearly SMB product that should have visible pricing. |
| **MISSING** | No pricing information anywhere. Buyer cannot self-qualify on budget before engaging sales. |

---

### DEPTH (Q21-Q22)

#### Q21: Explore without sales? (Self-Serve Content)

| Status | Criteria |
|--------|----------|
| **CLEAR** | Ungated content available for deep exploration: documentation, guides, video tours, interactive demos, product screenshots, case studies. Buyer can learn extensively without sales. |
| **PARTIAL** | Some content exists but limited (only a few screenshots), gated (requires email), or hard to find (buried navigation). |
| **MISSING** | No self-serve content. All meaningful learning requires booking a sales conversation. |

#### Q22: ROI documentation? (Economic Buyer Material)

| Status | Criteria |
|--------|----------|
| **CLEAR** | ROI calculator, business case template, TCO comparison, or detailed economic justification available. Champion has ammunition for the CFO conversation. |
| **PARTIAL** | ROI mentioned or implied ("save money", "recover margin") but not documented with specifics. No calculator or business case. |
| **MISSING** | No ROI material. Champion has no economic ammunition to justify spend to decision-makers. |

---

## Output Format

```json
{
  "meta": { ... from Step 00 ... },
  "evidence": [
    {
      "id": "Q1",
      "stage": "land",
      "question": "What is this?",
      "quote": "[exact text from homepage]",
      "inference": "[what it means for buyer decision]",
      "status": "clear"
    },
    // ... all 22 questions
  ]
}
```

---

## Final Check Before Passing to Step 02

Before outputting, verify:
- [ ] Every quote is exact text (copy-pasted, not paraphrased)
- [ ] CLEAR status means explicit statement, no interpretation required
- [ ] PARTIAL status used whenever buyer must infer meaning or evidence is buried
- [ ] MISSING status only when no relevant content exists anywhere
- [ ] All 22 questions scored

---

## Pass to Next Step

After scoring all 22 questions, pass the output JSON to **Step 02: Calculate Verdicts**.

**CRITICAL CONSISTENCY RULE:** Do NOT change these scores in later steps. All subsequent reasoning must remain consistent with this evidence. If Step 01 says Q5 is MISSING, no later step can claim urgency is "Strong".
