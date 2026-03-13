# X-RAY Protocol: 01 — Questions

## v5.3

---

## Overview

The X-RAY diagnostic uses **22 questions** to assess a homepage's outbound readiness:

- **20 Core Questions** (Q1-Q20): Count toward the main 1-10 score
- **2 Depth Questions** (Q21-Q22): Shown separately, do not affect main score

---

## 20 Core Questions by Stage

### Stage 1: LAND (Q1-Q2)

*Can a buyer immediately understand what this is?*

| ID   | Question        | What to Look For                                       |
| ---- | --------------- | ------------------------------------------------------ |
| Q1   | What is this?   | Category claim. Can buyer file this in a known bucket? |
| Q2   | What do you do? | Core function. One-sentence explanation of capability. |

---

### Stage 2: MAKE SENSE (Q3-Q5)

*Can a buyer connect this to their own pain and urgency?*

| ID   | Question              | What to Look For                                             |
| ---- | --------------------- | ------------------------------------------------------------ |
| Q3   | Pain worth switching? | Named pain. Is the problem specific and recognizable?        |
| Q4   | What project?         | Buyer's task. What job/project is buyer trying to complete?  |
| Q5   | Why act now?          | Stakes/urgency. Cost of waiting, timing pressure, trigger moment. |

---

### Stage 3: SELF-SELECT (Q6-Q7)

*Can a buyer determine if this is for them?*

| ID   | Question          | What to Look For                                            |
| ---- | ----------------- | ----------------------------------------------------------- |
| Q6   | For my team?      | ICP signals. Industry, role, team size, segment indicators. |
| Q7   | For my situation? | Qualifying conditions. When this works vs. doesn't work.    |

---

### Stage 4: COMPARE (Q8-Q10)

*Can a buyer evaluate this against alternatives?*

| ID   | Question               | What to Look For                                             |
| ---- | ---------------------- | ------------------------------------------------------------ |
| Q8   | Switching from?        | Named alternative. What is buyer replacing? (status quo, competitor, DIY) |
| Q9   | Why alternatives fail? | Competitive weakness. Why other options don't work.          |
| Q10  | What's different?      | Differentiation. Unique mechanism or approach.               |

---

### Stage 5: VALIDATE (Q11-Q15)

*Can a buyer confirm this works for people like them?*

| ID   | Question            | What to Look For                                             |
| ---- | ------------------- | ------------------------------------------------------------ |
| Q11  | Teams like mine?    | Social proof. Named companies in target ICP.                 |
| Q12  | Results achieved?   | Quantified outcomes. Metrics, numbers, timeframes.           |
| Q13  | How much effort?    | Implementation clarity. Time, resources, complexity.         |
| Q14  | Proof match role?   | Role-specific proof. Testimonials from same role as target buyer. |
| Q15  | Enterprise signals? | Security/compliance. For enterprise targets: security page, compliance badges, enterprise tier. (N/A if SMB target) |

---

### Stage 6: COMMIT (Q16-Q20)

*Can a buyer take the next step safely?*

| ID   | Question             | What to Look For                                             |
| ---- | -------------------- | ------------------------------------------------------------ |
| Q16  | First step?          | CTA clarity. What happens when I click?                      |
| Q17  | Safe to try?         | Risk reversal. Pilot, trial, guarantee, low-commitment option. |
| Q18  | After I click?       | Process visibility. What's the next step after form submit?  |
| Q19  | CTA match readiness? | Motion fit. Is demo/trial/consultation appropriate for motion? |
| Q20  | Offer match motion?  | Pricing/offer alignment. Does offer shape match the sales motion? |

---

## 2 Depth Questions (Separate Assessment)

### DEPTH (Q21-Q22)

*Can a buyer explore without entering the sales funnel?*

| ID   | Question               | What to Look For                                             |
| ---- | ---------------------- | ------------------------------------------------------------ |
| Q21  | Explore without sales? | Self-serve content. Guides, videos, resources, product tours. |
| Q22  | ROI documentation?     | Economic buyer material. ROI calculator, business case, TCO. |

**Note:** Depth questions assess content for research-first buyers. They do NOT break the buying path and are shown as a separate "Depth Content" indicator.

---

## Scoring Each Question

Each question receives one of three statuses:

| Status      | Meaning                                 | Example                                                      |
| ----------- | --------------------------------------- | ------------------------------------------------------------ |
| **Clear**   | Question fully answered by homepage     | "LIMS alternative for R&D teams" clearly states category     |
| **Partial** | Question partially addressed or unclear | Category exists but invented ("Material Intelligence Platform") |
| **Missing** | Question not addressed at all           | No category claim anywhere on page                           |

---

## Evidence Format

For each question, capture:

```json
{
  "id": "Q1",
  "stage": "land",
  "question": "What is this?",
  "quote": "Material Intelligence Platform",
  "inference": "Invented category. Buyers cannot file this.",
  "status": "partial"
}
```

- **quote**: Exact text from homepage (or "Not found" if missing)
- **inference**: What the evidence means for the buyer
- **status**: clear / partial / missing
