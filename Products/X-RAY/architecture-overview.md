# X-RAY Tool Architecture Overview
## v5.3 — March 2026

---

## System Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                        USER INTERFACE                            │
│                    (pzaudit.up.railway.app)                      │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ POST /xray
                              │ { url, target_buyer }
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                         HUROZO API                               │
│                      (Claude-powered)                            │
│                                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐          │
│  │  1. FETCH    │→ │  2. SCORE    │→ │  3. GENERATE │          │
│  │  Homepage    │  │  20 Core Qs  │  │  Report JSON │          │
│  │  + subpages  │  │  + 2 Depth   │  │              │          │
│  └──────────────┘  └──────────────┘  └──────────────┘          │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ JSON Response
                              │ (xray-output-schema-v5.3.json)
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                        FRONTEND RENDER                           │
│               Populates HTML template with JSON data             │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                      RENDERED REPORT                             │
│                    (xray-report.html)                            │
└─────────────────────────────────────────────────────────────────┘
```

---

## Data Flow

### 1. Input (User → Frontend → Hurozo)

```json
{
  "url": "https://example.com",
  "target_buyer": "VP Engineering"
}
```

### 2. Processing (Hurozo Internal)

1. **Fetch** homepage HTML
2. **Score** each of 20 core questions (Clear / Partial / Missing)
3. **Score** 2 Depth questions (separate from main score)
4. **Calculate** stage verdicts (OK / Weak / Break)
5. **Calculate** overall score (1-10)
6. **Generate** 7 Risk Signal assessments
7. **Generate** 4 Prediction metrics with basis
8. **Generate** Recognition signals (4 expected objections)
9. **Identify** primary breakpoint
10. **Identify** decision gaps
11. **Generate** recommendations

### 3. Output (Hurozo → Frontend)

JSON matching `xray-output-schema-v5.3.json`

### 4. Render (Frontend)

Frontend populates HTML template with JSON data and displays to user.

---

## Scoring System

### 1-10 Scale

| Score | Label | Criteria |
|-------|-------|----------|
| 10 | Ready to Scale | All 6 stages OK, 18+ clear |
| 9 | Strong | 6 OK, 16-17 clear |
| 8 | Solid | 5-6 OK, ≤1 weak, 14-15 clear |
| 7 | Good | 5-6 OK, 1-2 weak, 12-13 clear |
| 6 | Proceed with Caution | 4-5 OK, 2 weak, 10-11 clear |
| 5 | Gaps to Address | 3-4 OK, 2-3 weak, 8-9 clear |
| 4 | Fix Before Outbound | 2-3 OK or 1 break, 6-7 clear |
| 3 | Major Work Needed | 1-2 OK, 2 breaks, 4-5 clear |
| 2 | Broken | 0-1 OK, 3+ breaks, 2-3 clear |
| 1 | Fundamentally Broken | All weak/break, <2 clear |

### Question Status

- **Clear**: Question is fully answered by homepage
- **Partial**: Question is partially addressed or unclear
- **Missing**: Question is not addressed at all

### Stage Verdict Rules

- **OK**: All questions clear, OR majority clear with none missing
- **Weak**: Any partial, none missing
- **Break**: Any missing

### Depth Questions

Q21 and Q22 are scored separately and shown as "Depth Content: Strong/Partial/Weak"
They do NOT affect the main 1-10 score.

---

## File Structure

```
xray-dima-package-v5.3/
├── README.md (this file)
├── architecture-overview.md
├── schemas/
│   └── xray-output-schema-v5.3.json
├── templates/
│   └── xray-report-template-v5.3.html
├── protocols/
│   ├── 01-questions.md (20 core + 2 depth questions)
│   ├── 02-scoring.md (how to score)
│   ├── 03-risk-signals.md (7 signals + composition)
│   ├── 04-predictions.md (4 metrics + basis logic)
│   └── 05-generation.md (how to generate report content)
└── examples/
    ├── xray-fletchpmm-v5.3.html
    ├── xray-fletchpmm-v5.3.json
    ├── xray-labv-v5.3.html
    └── xray-labv-v5.3.json
```

---

## Key Contracts

### Frontend ↔ Hurozo

The JSON schema (`xray-output-schema-v5.3.json`) is the contract.
Frontend should NOT assume any fields beyond what's in the schema.
Hurozo should ALWAYS return all required fields.

### Question IDs

Questions are numbered Q1-Q22.
- Q1-Q20: Core (counted in main score)
- Q21-Q22: Depth (shown separately)

### Stage IDs

Stages are: `land`, `make_sense`, `self_select`, `compare`, `validate`, `commit`

### Risk Signal IDs

Signals are: `message_priority`, `buyer_focus`, `why_act_now`, `proof_relevance`, `explanation_burden`, `internal_sharing`, `mixed_signals`

---

## Implementation Notes

### Frontend Responsibilities

1. Accept URL and target buyer from user
2. POST to Hurozo API
3. Show loading state
4. Receive JSON response
5. Populate HTML template
6. Render report
7. Provide download/share options

### Error Handling

If Hurozo returns error, frontend should display:
- "Unable to fetch homepage" (if URL unreachable)
- "Unable to generate report" (if processing fails)
- Provide retry option

### Caching

Consider caching reports for 24h by URL+target_buyer hash.
User can request fresh scan.
