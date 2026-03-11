# Outbound Readiness X-RAY: Tool Protocol Package

## Version 1.1

This document contains everything needed to build an automated X-RAY generation tool.

**Changelog v1.1:** Renamed "Buying Path Readiness Sprint" to "Repeatable Sales System sprint" throughout.

---

# 1. Architecture Overview

```
┌─────────────────┐
│     INTAKE      │  Form: company name, URL, target buyer, context
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  HOMEPAGE FETCH │  Fetch and parse homepage content
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│    SCORING      │  Apply question criteria → stage verdicts
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│   GENERATION    │  Populate output schema with findings
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  HTML RENDER    │  Generate final report from template
└─────────────────┘
```

---

# 2. Intake Schema

```json
{
  "company_name": "string, required",
  "homepage_url": "string, required, must be valid URL",
  "target_buyer": "string, required, role title + company type",
  "company_context": {
    "what_they_claim": "string, 1-2 sentences describing their product",
    "stage": "string, e.g., 'Seed', 'Series A', 'Series B'",
    "team_size": "string or number",
    "customer_count": "string or number",
    "outbound_goal": "string, what they want to achieve with outbound"
  },
  "partner": "string, optional, name of referring partner"
}
```

---

# 3. Scoring Protocol

## 3.1 The 6 Buying Path Stages

| Stage           | Core Question            | What Buyer Needs                                             |
| --------------- | ------------------------ | ------------------------------------------------------------ |
| **LAND**        | What is this?            | Recognizable category they can place in a known bucket       |
| **MAKE SENSE**  | Why should I care?       | Clear pain + stakes of inaction                              |
| **SELF-SELECT** | Is this for me?          | ICP boundary that lets them say "yes, this fits my situation" |
| **COMPARE**     | Why you vs. what I use?  | Named alternative + why it fails                             |
| **VALIDATE**    | Does this work for real? | Proof that matches their buying context                      |
| **COMMIT**      | What's the first step?   | Low-risk, specific entry point                               |

## 3.2 Question Bank (18 Questions)

Select 8-10 questions per report based on relevance. Every stage must have at least one question.

### LAND Stage

| Q#   | Question                 | Scoring Criteria                                             |
| ---- | ------------------------ | ------------------------------------------------------------ |
| Q1   | What is this?            | **CLEAR:** Category is named AND buyer can immediately place it in a known bucket (e.g., "CRM", "LIMS", "ERP"). **PARTIAL:** Category is described but uses invented terms or requires explanation. **MISSING:** No category visible, only features or benefits. |
| Q2   | What do you actually do? | **CLEAR:** Core function stated in plain language within 3 seconds of landing. **PARTIAL:** Function requires scrolling or interpretation. **MISSING:** Only abstract claims like "transform" or "empower." |

### MAKE SENSE Stage

| Q#   | Question                             | Scoring Criteria                                             |
| ---- | ------------------------------------ | ------------------------------------------------------------ |
| Q3   | What pain is worth switching for?    | **CLEAR:** Specific, recognizable pain named that buyer has felt. **PARTIAL:** Pain implied through features or benefits. **MISSING:** No pain mentioned, only capabilities. |
| Q4   | What project does this serve?        | **CLEAR:** Buyer's task or project named explicitly (e.g., "preparing for SOC 2 audit"). **PARTIAL:** Task implied but not stated. **MISSING:** Product-centric framing only. |
| Q5   | What are the stakes if I do nothing? | **CLEAR:** Cost of inaction quantified or made visceral. **PARTIAL:** Stakes implied but not explicit. **MISSING:** No consequence of inaction visible. |

### SELF-SELECT Stage

| Q#   | Question                  | Scoring Criteria                                             |
| ---- | ------------------------- | ------------------------------------------------------------ |
| Q6   | Is this for my team?      | **CLEAR:** ICP stated with specifics (industry, company size, role, stage). **PARTIAL:** Audience mentioned but too broad ("data teams"). **MISSING:** No audience specified. |
| Q7   | Is this for my situation? | **CLEAR:** Qualifying conditions visible (e.g., "if you have X problem" or "teams that do Y"). **PARTIAL:** Situations implied through testimonials. **MISSING:** No situation filtering. |

### COMPARE Stage

| Q#   | Question                        | Scoring Criteria                                             |
| ---- | ------------------------------- | ------------------------------------------------------------ |
| Q8   | What am I switching from?       | **CLEAR:** Alternative named explicitly (competitor, tool, or behavior like "Excel"). **PARTIAL:** Generic reference ("manual processes" or "legacy tools"). **MISSING:** No alternative mentioned. |
| Q9   | Why do those alternatives fail? | **CLEAR:** Specific weaknesses of alternatives named. **PARTIAL:** Implied through contrast but not stated. **MISSING:** No alternative weakness visible. |
| Q10  | What makes you different?       | **CLEAR:** Differentiation stated AND tied to a capability competitors lack. **PARTIAL:** Differentiation claimed but generic. **MISSING:** No differentiation visible. |

### VALIDATE Stage

| Q#   | Question                                | Scoring Criteria                                             |
| ---- | --------------------------------------- | ------------------------------------------------------------ |
| Q11  | Does this work for companies like mine? | **CLEAR:** Logos or testimonials from recognizable similar companies. **PARTIAL:** Some proof but not matching buyer's context. **MISSING:** No proof visible. |
| Q12  | What results have others achieved?      | **CLEAR:** Quantified outcomes (numbers, percentages, timeframes). **PARTIAL:** Qualitative testimonials without metrics. **MISSING:** No results visible. |
| Q13  | How much effort is this?                | **CLEAR:** Implementation effort described (timeline, resources, complexity). **PARTIAL:** Effort mentioned but vague. **MISSING:** No effort information. |

### COMMIT Stage

| Q#   | Question                    | Scoring Criteria                                             |
| ---- | --------------------------- | ------------------------------------------------------------ |
| Q14  | What is the first step?     | **CLEAR:** CTA is specific with details (duration, what happens, what buyer gets). **PARTIAL:** CTA exists but vague ("Request Demo"). **MISSING:** No clear next step. |
| Q15  | Does this feel safe to try? | **CLEAR:** Risk reversal present (free trial, pilot, money-back, easy exit). **PARTIAL:** Some safety signals but incomplete. **MISSING:** No risk reversal. |
| Q16  | What happens after I click? | **CLEAR:** Post-click process explained. **PARTIAL:** Process implied. **MISSING:** Unknown what happens next. |

### DEPTH Stage (Optional, for complex sales)

| Q#   | Question                                | Scoring Criteria                                             |
| ---- | --------------------------------------- | ------------------------------------------------------------ |
| Q17  | Can I explore without talking to sales? | **CLEAR:** Self-serve content available (docs, videos, sandbox). **PARTIAL:** Some content but gated. **MISSING:** Must talk to sales for any information. |
| Q18  | Is there ROI documentation?             | **CLEAR:** Business case or ROI calculator available. **PARTIAL:** ROI implied in testimonials. **MISSING:** No ROI documentation. |

## 3.3 Stage Verdict Logic

A stage **PASSES** if:

- All questions evaluated for that stage are CLEAR, OR
- Majority are CLEAR and none are MISSING

A stage is **WEAK** if:

- Any question is PARTIAL and none are MISSING, OR
- Mix of CLEAR and PARTIAL

A stage **BREAKS** if:

- Any question is MISSING, OR
- Majority are PARTIAL with critical gaps

## 3.4 Overall Verdict Logic

| Score           | Verdict                         | Meaning                                      |
| --------------- | ------------------------------- | -------------------------------------------- |
| 0-2 stages pass | **RED: Fix Before Outbound**    | Commercial story not ready to scale          |
| 3-4 stages pass | **AMBER: Proceed with Caution** | Core story present but friction points exist |
| 5-6 stages pass | **GREEN: Ready for Outbound**   | Buying path works, story ready to scale      |

## 3.5 Breakpoint Identification

The **primary breakpoint** is the first stage (in order: Land → Make Sense → Self-Select → Compare → Validate → Commit) that is WEAK or BREAKS.

This is the "moment of insight" in the report.

---

# 4. Voice Protocol

These rules ensure consistent, ESL-accessible, non-AI language.

## 4.1 Terms to Avoid

| Avoid                              | Use Instead                |
| ---------------------------------- | -------------------------- |
| "holds" (as in "story holds")      | "works"                    |
| "fuzzy"                            | "unclear" or "partial"     |
| "lock" (as in "lock the decision") | "define" or "set"          |
| "wrong-fit"                        | "mismatched" or "poor-fit" |
| "healthy" (vague)                  | "strong" or "good"         |

## 4.2 AI Tells to Eliminate

- **No negative parallelisms:** Never write "It's not X, it's Y" or split versions
- **No em dashes:** Use periods, commas, or colons instead
- **No hollow transitions:** Cut "It's worth noting," "Interestingly," "Notably"
- **No compulsive summaries:** Cut "In summary," "Ultimately," "Overall"
- **No vague attribution:** Cut "Research suggests," "Many experts believe"
- **No inflated verbs:** "utilizes" → "uses," "leverages" → "uses"

## 4.3 ESL Accessibility

- No US-specific idioms ("boil the ocean," "punt," "ballpark")
- Test: Could a German founder with solid English read this without stopping?
- If uncertain, simplify the term, not the sentence

## 4.4 Tone

- Direct, not aggressive
- Economic, not motivational (frame as "costs you money" or "makes you money")
- Specific, not universal
- Own the opinion (no excessive hedging)

## 4.5 Sentence Structure

- Mix sentence lengths for rhythm
- One idea per sentence
- No sentences that exist only to bridge other sentences

---

# 5. Output Schema

This is the exact JSON structure the tool must produce. HTML generation is a direct template fill from this schema.

```json
{
  "meta": {
    "company_name": "string",
    "homepage_url": "string",
    "target_buyer": "string",
    "prepared_date": "string, YYYY-MM-DD",
    "partner": "string or null",
    "method_version": "string, e.g., 'v4.0'"
  },
  
  "company_context": {
    "what_they_claim": "string, 1-2 sentences",
    "stage": "string",
    "team_size": "string",
    "customer_count": "string",
    "outbound_goal": "string"
  },
  
  "verdict": {
    "score": {
      "passing": "integer, 0-6",
      "weak": "integer, 0-6",
      "breaking": "integer, 0-6"
    },
    "status": "string, one of: 'RED', 'AMBER', 'GREEN'",
    "status_label": "string, e.g., 'Fix Before Outbound'",
    "headline": "string, one sentence summary",
    "diagnosis": "string, 2-3 sentence copyable explanation"
  },
  
  "implication": {
    "metrics": [
      {
        "name": "string, e.g., 'Reply Rate'",
        "prediction": "string, one of: 'Healthy', 'Weak', 'Poor', 'Strong', 'Elevated Risk', 'Slow', 'Moderate', 'Good'",
        "sentiment": "string, one of: 'good', 'weak', 'poor'"
      }
    ],
    "reason": "string, 1-2 sentences explaining why",
    "expect_to_hear": [
      "string, specific objection or response"
    ]
  },
  
  "stages": [
    {
      "name": "string, e.g., 'Land'",
      "status": "string, one of: 'ok', 'weak', 'break'",
      "status_label": "string, e.g., 'OK', 'Weak', 'Breaks'"
    }
  ],
  
  "breakpoint": {
    "stage": "string, stage name",
    "type": "string, one of: 'primary_break', 'friction', 'minor_friction', 'no_major_break'",
    "insight": "string, 2-3 sentences explaining what happens at this stage",
    "missing_signals": [
      "string, what buyers cannot find"
    ]
  },
  
  "observed_hero": {
    "quote": "string, exact text from homepage hero",
    "buyer_question": "string, the question this should answer",
    "verdict": "string, one of: 'CLEAR', 'PARTIAL', 'MISSING', 'NOT ANSWERED'"
  },
  
  "evidence": [
    {
      "stage": "string, stage name",
      "stage_key": "string, lowercase hyphenated, e.g., 'make-sense'",
      "question": "string, buyer question",
      "finding": "string, 2-3 sentences describing what homepage shows",
      "status": "string, one of: 'clear', 'partial', 'missing'"
    }
  ],
  
  "decisions": [
    {
      "name": "string, decision name, e.g., 'Category'",
      "status": "string, one of: 'partial', 'missing'",
      "finding": "string, what is unclear or missing",
      "consequence": "string, what this means for SDR/champion"
    }
  ],
  
  "personas": {
    "target_buyer_intro": "string, describes who the champion is and who they carry to",
    "checks": [
      {
        "type": "string, e.g., 'Champion → Boss'",
        "role": "string, specific role title",
        "question": "string, what we're testing",
        "answer": "string, 2-3 sentences on pass/fail",
        "verdict": "string, one of: 'pass', 'weak', 'fail'",
        "icon": "string, one of: '✓', '△', '✗'"
      }
    ]
  },
  
  "next_step": {
    "label": "string, e.g., 'Recommended Path'",
    "action": "string, main recommendation",
    "goals": [
      {
        "decision": "string, decision name",
        "instruction": "string, what to do"
      }
    ],
    "without_this": "string, consequence of not acting",
    "with_this": "string, benefit of acting"
  }
}
```

---

# 6. Prompt Architecture

## 6.1 System Prompt (Orchestration)

```
You are generating an Outbound Readiness X-RAY report for a B2B company.

Your task is to evaluate a homepage against the Buying Path framework and produce a structured diagnostic report.

## INPUTS YOU WILL RECEIVE
1. Intake data (company name, URL, target buyer, context)
2. Homepage content (fetched HTML/text)
3. This scoring protocol (reference)

## YOUR PROCESS
1. Read the homepage content carefully
2. For each of the 6 buying path stages, select 1-2 relevant questions from the question bank
3. For each question, find evidence on the homepage and apply scoring criteria
4. Determine stage verdicts based on question scores
5. Calculate overall verdict (RED/AMBER/GREEN)
6. Identify primary breakpoint
7. Generate all output fields per the schema

## OUTPUT REQUIREMENTS
- Return valid JSON matching the output schema exactly
- All text fields must follow the voice protocol (no AI tells, ESL accessible)
- Findings must be specific and evidence-based, not generic
- Diagnosis must be copyable (one sentence someone can paste into Slack)
- "Expect to hear" must be realistic objections, not generic pushback

## CRITICAL RULES
- Never use em dashes
- Never use "It's not X, it's Y" constructions
- Never say "fuzzy" (use "unclear" or "partial")
- Never say "holds" for story/path (use "works")
- Every finding must reference specific homepage content
- If something is not visible on the homepage, mark it MISSING, do not infer
```

## 6.2 Question Selection Prompt

```
Given the homepage content and company context, select 8-10 questions from the question bank that are most relevant to evaluating this company's outbound readiness.

Selection criteria:
- Every stage must have at least one question
- Prioritize questions where the homepage has visible evidence (positive or negative)
- Include questions that test the company's claimed positioning
- Skip questions that are not applicable (e.g., Q17 self-serve if clearly enterprise-only)

Return a list of question IDs (Q1-Q18) to evaluate.
```

## 6.3 Scoring Prompt (per question)

```
Evaluate the following question for [COMPANY NAME]:

Stage: [STAGE]
Question: [QUESTION TEXT]
Scoring Criteria:
- CLEAR: [CLEAR CRITERIA]
- PARTIAL: [PARTIAL CRITERIA]  
- MISSING: [MISSING CRITERIA]

Homepage Evidence:
[RELEVANT SECTION OF HOMEPAGE]

Return:
{
  "status": "clear|partial|missing",
  "finding": "2-3 sentence description of what the homepage shows, with specific quotes or references"
}

Rules:
- Be specific. Quote actual text from the homepage.
- If the element exists but is weak, score PARTIAL and explain why.
- If the element is completely absent, score MISSING.
- Do not infer or assume. Only score what is visible.
```

## 6.4 Generation Prompt (final assembly)

```
Given the scoring results, generate the complete X-RAY report.

Scoring Summary:
[STAGE VERDICTS AND QUESTION SCORES]

Company Context:
[INTAKE DATA]

Generate the following:

1. VERDICT
- Calculate passing/weak/breaking counts
- Determine RED/AMBER/GREEN status
- Write a headline (one sentence, direct)
- Write a diagnosis (2-3 sentences, copyable, specific to this company)

2. IMPLICATION
- Predict: Reply Rate, Demo Conversion, Internal Sell, Pipeline Speed
- Explain why in 1-2 sentences
- List 3-4 specific objections prospects will voice

3. BREAKPOINT
- Identify the first stage that is WEAK or BREAKS
- Write an insight explaining what happens at this stage
- List 3-4 specific signals buyers cannot find

4. PERSONAS
- Identify who the champion is (from target_buyer)
- Check: Can champion sell to boss? Can champion sell to users? Can economic buyer see ROI?
- Write specific answers based on homepage evidence

5. NEXT STEP
- Recommend path based on verdict
- List specific decisions to define (from the decisions array)
- Write "without this" and "with this" consequences

Voice Rules:
[INSERT VOICE PROTOCOL]

Output the complete JSON per schema.
```

---

# 7. Reference Chain

For the tool to work, it needs access to:

| Document                         | Location                                                   | Purpose                                   |
| -------------------------------- | ---------------------------------------------------------- | ----------------------------------------- |
| Buying Path X-RAY Architecture   | `/canon/buying-path-xray-architecture.md`                  | Method background, 15 decisions, 7 stages |
| Buying Path Diagnostic Framework | `/canon/buying-path-diagnostic-framework-v3.2-complete.md` | 18 questions, stage definitions           |
| Voice Reference                  | `/protocols/voice-reference.md`                            | Language rules, AI tells, ESL rules       |
| Output Schema                    | `/protocols/xray-output-schema.json`                       | Exact JSON structure                      |
| HTML Template                    | `/templates/xray-report-template.html`                     | Report rendering                          |
| This Protocol                    | `/protocols/xray-tool-protocol.md`                         | Scoring logic, prompts                    |

---

# 8. Validation Checklist

Before a report is delivered, validate:

## Content Validation

- [ ] All 6 stages have at least one question scored
- [ ] Every finding references specific homepage content
- [ ] Diagnosis is under 50 words and copyable
- [ ] "Expect to hear" contains realistic objections
- [ ] Sprint goals reference specific decisions

## Voice Validation

- [ ] No em dashes anywhere
- [ ] No "It's not X, it's Y" constructions
- [ ] No "fuzzy," "holds," "leverage," "utilize"
- [ ] No hollow transitions or compulsive summaries
- [ ] ESL accessible (no US-only idioms)

## Schema Validation

- [ ] JSON is valid and parseable
- [ ] All required fields present
- [ ] Status values match allowed enums
- [ ] Score counts sum to 6

---

# 9. Example: LabV Scoring

## Intake

```json
{
  "company_name": "LabV",
  "homepage_url": "https://www.labv.io/en",
  "target_buyer": "Head of R&D / Lab Manager at industrial companies"
}
```

## Question Selection

Q1 (Land), Q3 (Make Sense), Q5 (Make Sense), Q6 (Self-Select), Q8 (Compare), Q9 (Compare), Q11 (Validate), Q14 (Commit), Q15 (Commit)

## Stage Verdicts

| Stage       | Questions | Results          | Verdict             |
| ----------- | --------- | ---------------- | ------------------- |
| Land        | Q1        | PARTIAL          | WEAK                |
| Make Sense  | Q3, Q5    | CLEAR, PARTIAL   | OK (majority CLEAR) |
| Self-Select | Q6        | PARTIAL          | WEAK                |
| Compare     | Q8, Q9    | CLEAR, CLEAR     | OK                  |
| Validate    | Q11       | PARTIAL          | WEAK                |
| Commit      | Q14, Q15  | PARTIAL, PARTIAL | WEAK                |

## Overall

- Passing: 2 (Make Sense, Compare)
- Weak: 4 (Land, Self-Select, Validate, Commit)
- Breaking: 0

**Verdict: RED (2/6 stages pass)**

---

# 10. Deployment Notes

## For Cursor Implementation

1. **Fetch Layer**: Use a headless browser or fetch API to get homepage content. Parse to text, keeping structure (headers, CTAs, testimonials).

2. **LLM Layer**: Use Claude or GPT-4 with the prompts above. Chain: Question Selection → Scoring (per question) → Generation.

3. **Validation Layer**: JSON schema validation + voice pattern regex checks.

4. **Render Layer**: HTML template with slot injection. Use the v4 template structure.

## Rate Limiting

- One LLM call for question selection
- 8-10 LLM calls for scoring (parallelize)
- One LLM call for generation
- Total: ~12 calls per report

## Caching

- Cache homepage content for 24 hours
- Cache question selection per URL
- Do not cache scoring or generation (may need updates)

---

End of Protocol Package.
