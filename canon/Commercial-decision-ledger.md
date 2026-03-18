# Commercial Decision Ledger
## Product.Zone

**Purpose:** Canonical record of all locked commercial decisions. Human-readable, version-controlled.  
**Operational layer:** Notion K&D database (queryable by client, status, leverage).  
**Sync discipline:** When a decision is locked in Notion, it is added here in the next commit.  
**Version:** 2.0 · March 18, 2026

**What changed in v2.0:** Major strategic shift from sprint-based interventions to journey-based partnership. New offer architecture (Map → Fix → Support → Review), Buyer Journey Canvas as relationship anchor, Situation Library (15 entries), Find stage questions formalized, partner model defined. See changelog at bottom for full diff.

---

## How to Read This Document

Each entry contains:
- **Code** — framework reference (A1–G4, or Strategic)
- **Decision name** — what was decided
- **Answer** — the locked position in external-facing language
- **Decided against** — what was considered and rejected
- **Status** — Locked / Validated / Future Stage

Status definitions:
- **Locked** — decided in this session, not yet validated through multiple client engagements
- **Validated** — held through multiple engagements without revision
- **Future Stage** — mapped but not yet operationally relevant

---

## STRATEGIC DECISIONS

### S1 · Relationship Model
**Status:** Locked (v2.0)

**Answer:** Journey-based partnership, not project-based sprints.

Old model: Client has a problem → diagnose → sprint → deliver → engagement ends. Revenue is project-based.

New model: Map the full buyer journey → fix what's broken → stay on the map → when the next stage breaks, we're already in the conversation. The Buyer Journey Canvas is the through-line. Every engagement creates, updates, or re-scores it.

Revenue compounds across the relationship instead of resetting to zero after each sprint.

Lifecycle: Map (€1,500) → Fix (€5K-15K) → Support (€1,500/mo) → Review (€2K/qtr) → Next Fix → continuing.

**Decided against:** Staying with sprint-only model (one-and-done, low CLV, clients drift away). Open-ended retainer without framework (becomes custom consulting, nothing compounds).

---

### S2 · Buyer Journey Canvas
**Status:** Locked (v2.0)

**Answer:** The canvas is the primary diagnostic, planning, and relationship tool. It replaces the scorecard as the central deliverable.

Format: 11 Revenue Loop stages (Find → Land → Make Sense → Self-Select → Compare → Validate → Commit → Activate → Embed → Expand → Advocate) × 4 layers (Surfaces, Metrics, State, Actions).

Two modes:
- Mode 1 (Quick Assessment): Filled in together during first conversation. Directional, not precise. 30-45 minutes.
- Mode 2 (Evidence-Based): Each stage color derived from scoring buyer questions against surfaces. Defensible, repeatable. Part of The Map diagnostic.

The canvas is created in The Map, updated in every Fix, and re-scored in every Review. It is the persistent reference for the entire client relationship.

**Decided against:** Scorecard-only format (shows individual surface scores but not the system view). Generic journey mapping (no buyer-question-level evidence underneath the colors).

---

### S3 · Situation Library
**Status:** Locked (v2.0)

**Answer:** 15 commercial transitions PZ is built to solve, compressed from 77 PZ-native situations (filtered from 110 total). Scored across 5 dimensions (Stage Fit, Situation Fit, Urgency, Problem Fit, Access) and tiered by hunt priority.

Tier 1 (Active Hunt, 5 situations): Hiring into fog, Story won't travel, First sales stuck, Too many bets, Repositioning.
Tier 2 (Strong Signal, 7 situations): Early journey broken, Pricing friction, Proof gap, Explanation burden, Buyer journey not designed, Message drift, No alternative named.
Tier 3 (Investigate, 3 situations): "Need more leads" (pure volume), Pipeline thin, Reply rates low.

Each situation has: observable signals, outreach hook (voice-aligned, ESL-ready), offer routing, proof match, and Revenue Loop break mapping.

Type classification: A (decisions missing), B (surfaces missing), C (transfer missing), D (not PZ).

**Decided against:** Generic ICP filtering (industry, size, stage). ChatGPT's 8-category grouping (grouped by symptom, not by intervention needed).

---

### S4 · Partner Architecture
**Status:** Locked (v2.0)

**Answer:** PZ owns the map. Partners plug into specific journey stages for execution.

PZ core (delivers directly): Find Design (strategy), Land through Commit (positioning, surfaces, motion), System Map.
PZ adjacent (advises, partners execute): Activate (onboarding design).
Partner execution: Content/ad agencies (Find execution), lead gen/outbound (Find → Land execution), product/UX consultants (Activate), CS/success consultants (Embed), growth/RevOps (Expand), community builders (Advocate).

The canvas connects everything. Partners see their stage. Client sees the whole journey. PZ orchestrates.

Named partners: Profitbl/Alex (outbound execution), Emmanuel Mondon (scout/referral).

**Decided against:** PZ doing everything (capability spread too thin). Partners without a shared framework (disconnected interventions, no system view).

---

### S5 · Find Stage Extension
**Status:** Locked (v2.0)

**Answer:** 22 new buyer questions across 4 Find surfaces, extending the Buying Path Diagnostic Framework upstream. Proposed for framework v5.2.

LinkedIn Post (FP1-FP7): Tests whether content activates the right audience.
LinkedIn Profile (FL1-FL6): Tests whether profile converts visitors to homepage.
Ad (FA1-FA5): Tests whether ads earn clicks to the right landing page.
Referral Intro (FR1-FR4): Tests whether partner intros are situation-specific.

Total framework capacity: 71 questions across 8 surface types.

Triggered by Pascal/SENF case: 300 homepage visits/month despite active LinkedIn. The framework had no questions for the Find stage. Now it does.

**Decided against:** Treating Find as outside PZ's scope (Pascal proved it's PZ-native when the problem is audience/situation targeting, not pure volume).

---

### S6 · Situation Lenses
**Status:** Locked (v2.0)

**Answer:** One diagnostic engine, multiple situation-specific lenses. The engine (20+ buyer questions scored against surfaces) stays the same. Each lens changes three things: question weighting, narrative framing, and routing.

8 lenses defined: first_sales_stuck, transfer_ready, segment_focus, repositioning, post_sprint_check, outbound_ready (live from v5.1), price_defense, proof_gap.

Lenses are selected by: scout picks situation (most common), auto-suggest from gap patterns, or founder self-selects (lead magnet version).

**Decided against:** Generic X-RAY without situation context (poor reception, perceived as "just a homepage audit").

---

## NORTH STAR

### Primary JTBD
**Status:** Locked (v2.0 — rewritten)

**Answer:** Design and maintain the client's complete buyer journey system so growth compounds instead of stalling.

Product.Zone is not a sprint vendor. It is the firm that owns the commercial map. The canvas makes the full journey visible. The Fix addresses what's broken. The Review keeps it healthy. Partners plug in for stages outside PZ's core.

Three entry triggers (updated, situation-library-aligned):
1. "Deals keep stalling and I can't figure out which part of the journey is broken." (First sales stuck, Too many bets)
2. "I'm about to hire someone for sales and I need the story to work without me." (Hiring into fog, Story won't travel)
3. "We're active on LinkedIn and running ads but traffic isn't converting." (Early journey broken, Pascal pattern)

**Decided against:** "Install commercial foundation before the next move breaks" (v1 framing, too sprint-focused, doesn't capture the ongoing relationship). "Improve GTM" (too abstract).

---

## BUYING PATH — TYPE A: POSITIONING

### A0 · Client-Side JTBD
**Status:** Locked (v2.0 — updated)

**Answer:** Three jobs buyers think they are hiring for, each mapping to one transition. T2 remains primary entry.

Three-layer JTBD architecture (updated with Situation Library mapping):

| Layer | T1 — First Sales | T2 — Bringing Others In (PRIMARY) | T3 — Scaling Beyond You |
|-------|-----------------|-----------------------------------|-------------------------|
| **Situation Library** | #3 First sales stuck, #4 Too many bets, #5 Repositioning | #1 Hiring into fog, #2 Story won't travel, #9 Message drift | #14 Early journey broken, #15 Journey not designed, #6 Pricing friction, #7 Proof gap |
| **Observable patterns** | Pitch different every time, no clear wedge, interest but no conversion | About to hire rep, deck needs voiceover, board asks questions founder can't surface-answer | Spending on ads without knowing what converts, "need more leads" but can't say where journey breaks |
| **Product.Zone framing** | "Buyers can finally say yes" | "Others can carry it without you" | "The whole journey is designed and measured" |

New: T3 now includes the Pascal pattern (early journey broken, journey not designed). These were not visible in v1 because the framework didn't cover Find stage.

**Decided against:** Single primary JTBD (too narrow). Full list of 110 projects (overwhelming).

---

### A1 · Category
**Status:** Locked (v2.0 — updated)

**Answer:** Two-level frame (updated).

Level 1 (borrowed shelf): Go-to-market strategy and sales enablement. Existing category, no explanation required.

Level 2 (own language): "We design and maintain buyer journey systems for B2B software companies." Updated from "design and install commercial buying paths" to reflect the ongoing relationship model and the full journey scope (Find through Advocate, not just Land through Commit).

**Decided against:** Single new-category label only. Generic "GTM consultant." "Journey consultant" (too abstract, no contrast).

---

### A2 · Customer
**Status:** Validated (unchanged from v1)

**Answer:** Situation-based ICP covering four profiles. "Responsible for making a new software product convert in a market where the buying path hasn't been built yet."

Four valid profiles: startup founder-CEO, corporate venture commercial lead, SME leader expanding into new software product space, scale-up GTM lead entering new region or JTBD.

Sharp disqualifier: "If your main problem is getting attention rather than making interested buyers actually buy, we're not the right first call." Note: with Find Design now in scope, this disqualifier is softening. If the problem is audience targeting (PZ) vs. pure volume (not PZ), PZ is relevant.

---

### A3 · Alternative
**Status:** Validated (unchanged from v1)

**Answer:** Six named alternatives, each with its failure pattern.

| Alternative | Why they hire it | Why it fails |
|-------------|-----------------|--------------|
| AI + templates | Need better words fast | Format without foundation |
| Push outbound | More pipeline | Volume on a broken path |
| Hire a coach | Need a better mindset | Insight without installation |
| Fractional VP/CMO | Need experienced direction | Direction without delivery |
| Hire a rep | Need someone to sell | Execution without transfer |
| Agency | Need awareness/reach | Amplification without clarity |

Pattern line: "None of these build the commercial path itself."

Note for v2.0: "Run LinkedIn ads" is an emerging 7th alternative (Pascal pattern). Failure: amplification of a broken Find stage.

---

### A4 · Difference
**Status:** Validated (updated with canvas)

**Answer:** DFY not advisory, fixed scope, decisions-first sequencing, handoff-ready output, canvas-based system view.

Five differentiators (was four):
1. We produce artifacts, not recommendations.
2. Fixed scope at every tier.
3. Decisions locked before any surface is built.
4. A first sales rep could be onboarded from the Notion workspace alone.
5. **New:** The canvas gives the founder a system view of their full buyer journey that no other firm produces. Every engagement updates it. The founder can always see where they are.

---

### A5 · Outcome
**Status:** Validated (updated)

**Answer:** Two-level outcome.

Level 1 (original, still primary): The commercial story travels and converts without the founder in the room.

Level 2 (new): The founder can see their full buyer journey, know where it breaks, and fix it in sequence. System visibility is now part of the promise, not just "the story works."

Test (updated): Could a first sales rep be onboarded from the Notion workspace alone? AND: Can the founder point at the canvas and say "the bottleneck is here, and here's why"?

---

### A6 · Wedge Use Case
**Status:** Locked (v2.0 — rewritten)

**Answer:** The scored canvas. Founder sees their full buyer journey on one page for the first time.

Old wedge: lost-deals forensic + homepage mirror. Still valuable as a diagnostic technique within The Map, but no longer the entry wedge.

New wedge: "We'll map your full buyer journey in one week. You'll see every stage scored: where buyers find you, where they land, where they understand, where they commit, where they stick. Most founders have never seen this on one page. The canvas shows you exactly where the path breaks."

The canvas is the wedge because it creates immediate value (system visibility) and natural forward motion (the broken stages are obvious, the Fix scopes itself).

**Decided against:** Homepage audit only (too narrow, no system view). Generic diagnostic (no visual anchor, no persistent deliverable).

---

### A7 · Market Bet
**Status:** Validated (unchanged from v1)

**Answer:** European B2B SaaS early revenue, DACH/Benelux/Nordics.

---

### A8 · Category Maturity
**Status:** Validated (unchanged from v1)

**Answer:** Emerging market. Problem education comes before differentiation.

---

## BUYING PATH — TYPE B: TRUST

### B1 · Owner / Champion
**Status:** Validated (unchanged from v1)

**Answer:** The person personally accountable for commercial outcomes. Startup: founder-CEO. Corporate venture: commercial lead or venture owner. Must be in every session themselves.

---

### B2 · Proof Type
**Status:** Locked (v2.0 — updated)

**Answer:** Three-layer proof matched to buyer profile, now with canvas-stage anchoring.

Layer 1: Before/after story with conversion metrics (primary).
Layer 2: Reference calls matched to profile and stage.
Layer 3: Testimonials for warm leads.

New: Each proof is anchored to a specific canvas stage:
- Lyrasense: Land → Self-Select (positioning locked, decisions from 7/9 missing to 15 locked)
- VirGeo: Land → Commit (0 → 18 qualified conversations in 6 weeks)
- VYGR: Compare → Commit (founder-dependent → transferable motion)
- SENF/Pascal: Find → Land (journey mapping revealed Find/Land disconnect, 300 visits/month diagnosed)

Outstanding: Confirm Lyrasense before/after metric with Nader.

---

### B3 · Effort Shape
**Status:** Locked (v2.0 — rewritten)

**Answer:** Phase-based effort, not single-sprint shape.

The Map: 4 hours founder time across 1 week. 90-minute session + 30-minute walkthrough. All analytical work done by PZ beforehand.

The Fix: varies by module count. 1 module = 2-3 sessions over 2-3 weeks. 2 modules = 3-4 sessions over 3-4 weeks. 3 modules = 4-5 sessions over 4-5 weeks. Same principle as v1: sessions are decision-making moments, all building work happens between sessions.

Support: bi-weekly 60-minute sessions + async availability. Pause/resume anytime.

Review: quarterly 90-minute session + re-scored canvas.

Starter Bundle (Map + Positioning Lock): 2 weeks total, 3 sessions, ~5 hours founder time.

**Decided against:** Intensive bootcamp format. Single-shape engagement regardless of scope.

---

### B4 · Primary Risk
**Status:** Validated (unchanged from v1)

**Answer:** Fit + timing combo. "I'm worried this will be a smart, well-crafted system that doesn't quite fit our specific context at this moment."

Note for v2.0: The canvas reduces this risk because the founder sees the diagnostic evidence before committing to The Fix. The Map (€1,500) is the risk-reduction step: "See the evidence first. Then decide."

---

## BUYING PATH — TYPE C: MOVEMENT

### C1 · First Step
**Status:** Locked (v2.0 — updated)

**Answer:** Two-path entry, both leading to The Map.

Path 1 (warm): 30-minute Buying Path Triage call → leads to The Map booking. Same structure as v1: min 0-10 how they sell today, min 10-20 map buying path live, min 20-30 name the primary constraint.

Path 2 (self-serve): Free X-RAY Buyability Scan → results page shows gaps → CTA to book The Map. "Your homepage scored X/20. The full journey diagnostic covers all 11 stages."

Both paths converge on The Map (€1,500) as the first paid commitment. The Map is low enough commitment that it doesn't need heavy selling. The evidence sells.

**Decided against:** Sprint as first paid step (too high commitment for first engagement). X-RAY only (lacks the system view).

---

### C2 · Start Recipe
**Status:** Locked (v2.0 — rewritten)

**Answer:** Map week starts within 5 business days of booking.

Sequence: (1) Booking confirmed, access shared (homepage URL, deck, outbound samples). (2) PZ team runs surface audits: homepage 20 questions, Find stage audit, deck/outbound if available. (3) 90-minute founder session (canvas walk-through, fill in what PZ can't see from outside, identify bottleneck). (4) PZ finalizes scored canvas + decision ledger + action plan. (5) 30-minute walkthrough call to present findings and scope The Fix.

PZ arrives to the founder session with a point of view already formed. The session confirms or challenges it.

---

### C3 · Risk Reversal
**Status:** Validated (updated)

**Answer:** The Map is the risk reversal. €1,500, one week, the canvas is yours regardless.

Updated framing: "The Map shows you exactly where your buyer journey breaks. Even if you don't proceed to The Fix, you keep the canvas, the decision ledger, and the action plan. Those are yours."

The low price point of The Map makes risk reversal almost unnecessary. The bigger risk reversal is structural: the canvas gives the founder something valuable before they commit to the larger engagement.

---

### C4 · Entry Motion
**Status:** Locked (v2.0 — rewritten)

**Answer:** Free scan → Map → Starter Bundle.

Primary path: Free X-RAY scan (self-serve, automated) → results show gaps → founder books The Map (€1,500) → Map identifies bottleneck → Starter Bundle: Map + Positioning Lock (€5,000 introductory, 2 weeks).

Secondary path: Warm intro from scout/partner → triage call → The Map.

The Starter Bundle (Map + Positioning Lock at €5,000) is the most common first engagement. Introductory pricing: standalone would be €6,500 (Map €1,500 + Positioning Lock module €5,000). Bundled at €5,000 to match the old Entry Product price point and minimize conversion friction.

**Decided against:** Sprint as primary entry (too high commitment). X-RAY as sole entry without human conversation (tool use signals curiosity, not buying intent, still true from v1). Map only without bundling option (misses the natural momentum from diagnostic to first fix).

---

## BUYING PATH — TYPE D: ACTIVATION

### D1 · Activation Moment
**Status:** Locked (v2.0 — rewritten)

**Answer:** The scored canvas. Founder sees their full buyer journey with evidence-based scoring for the first time.

The canvas is the activation moment because: (1) it makes the invisible visible (most founders have never seen their complete journey on one page), (2) the broken stages are immediately obvious (red/yellow), (3) the founder can point at the screen and say "the problem is here," (4) the action plan writes itself from the evidence.

Secondary activation (within The Fix): lost-deals mapped with red breakpoints, same as v1. This happens in the first Fix session if the Positioning Lock module is part of the engagement.

**Decided against:** Report delivery only (document, not visual). Dashboard (too complex for the first moment).

---

### D2 · First Value Path
**Status:** Locked (v2.0 — rewritten)

**Answer:** Map week delivers the canvas in 5 business days.

Day 1-3: PZ audits all available surfaces (homepage, deck, outbound, LinkedIn, ads). Scores buyer questions. Drafts canvas.
Day 3 (or 4): 90-minute founder session. Walk through canvas together. Fill in Activate through Advocate. Confirm scoring. Identify bottleneck.
Day 4-5: Finalize scored canvas, decision ledger, action plan. Package deliverables.
Day 5 (or early Week 2): 30-minute walkthrough. Present findings. Scope The Fix.

First value: the scored canvas, delivered at the walkthrough. The founder walks away seeing their full system for the first time.

If Starter Bundle: Week 2 begins the Positioning Lock module immediately. Decisions locked by end of Week 2.

---

### D3 · Time to Value
**Status:** Locked (v2.0 — updated)

**Answer:** 5 business days to scored canvas. 10 business days to locked decisions (if Starter Bundle).

Surface language: "Your full journey scored in one week. Positioning locked in two."

---

## USAGE PATH — TYPE E: POST-YES

### E1 · Onboarding Motion
**Status:** Locked (v2.0 — updated)

**Answer:** Map week IS the onboarding. No separate onboarding sequence needed.

The Map intake (share homepage URL, deck, outbound samples) is the onboarding. The Map session is the kickoff. The walkthrough is the activation. The Fix begins immediately after.

---

### E2 · Habit / Embed Loop
**Status:** Locked (v2.0 — updated)

**Answer:** Canvas as operational anchor, supplementing the decision ledger.

Three repeatable micro-behaviours (updated):
1. Canvas check before any commercial move: "Which stage does this affect? Is that stage green?"
2. Ledger sign-off before surface updates: new hires, agencies, partners pre-cleared against locked decisions.
3. Quarterly Review: re-score the canvas, catch drift, plan next intervention.

Cancellation pain (updated): the canvas + decision ledger become external commercial memory. Stopping feels like losing both the system view and the institutional knowledge.

Key client language that signals embed: "Let's check the canvas" / "Which stage is this?" / "Run it by the ledger" / "When's our next Review?"

---

### E3 · Expansion Trigger
**Status:** Locked (v2.0 — rewritten)

**Answer:** The Review naturally surfaces the next Fix.

Old trigger: first rep closes first deal independently. That's still a meaningful milestone, but expansion is no longer event-triggered. It's built into the relationship model.

The quarterly Review re-scores the canvas. When a stage drifts from green to yellow, the next Fix scopes itself from the evidence. No re-selling needed. The canvas is the sales tool.

Expansion paths:
- Map → Fix (most common, immediate)
- Fix → Support (3-6 months of testing and adjusting)
- Support → Review (quarterly ongoing)
- Review → Next Fix (when a stage drifts, evidence-based)
- Fix on core stages → Fix on adjacent stages (e.g., after positioning locked, now Find Design needed)

---

### E4 · Advocate Story
**Status:** Validated (unchanged from v1)

**Answer:** "First rep closes first deal independently."

Three-beat anatomy: diagnostic moment, concrete build, rep independence.

Kitchen-table version: "Mapped our lost deals Week 1. Hired a rep three weeks later. They closed their first deal without me."

Note for v2.0: Add canvas-based advocate story: "They mapped our full journey. Turned out the problem wasn't the pitch, it was that nobody was reaching our homepage. Fixed Find in two weeks. Traffic tripled." (Pascal/SENF pattern, when validated.)

---

## BUSINESS PATH — TYPE F: ECONOMICS

### F1 · Value Metric
**Status:** Validated (unchanged from v1)

**Answer:** Deals closed by non-founders per month.

---

### F2 · Unit Economics
**Status:** Locked (v2.0 — rewritten)

**Answer:** Journey-based economics. Estimated until validated with first 3-5 clients on new model.

Starter Bundle (Map + Positioning Lock):
- Price: €5,000 (introductory)
- Delivery: ~30 hours (Map 10h + Positioning Lock 20h)
- CAC estimate: €1,200 (from existing channels)
- Payback: immediate (single engagement covers CAC)

Typical first-year client value:
- Map: €1,500 (if standalone) or €5,000 (Starter Bundle)
- Fix (2 modules average): €8,000
- Support (3 months average): €4,500
- Review (2 quarters): €4,000
- Total Year 1: €16,000-22,000

Typical ongoing (Year 2+):
- Fix (1-2 modules): €5,000-12,000
- Reviews (4 quarters): €8,000
- Total ongoing: €13,000-20,000/year

Estimated 3-year CLV: €45,000-55,000

Comparison to v1: old model LTV was €28,000 (with optimistic retention). New model LTV is €45K+ because the relationship is designed to continue.

What breaks first at scale: at 10+ active clients, delivery overload requires second full-time practitioner (Dima is already full-time, but focused on product/engineering, not client delivery).

**Decided against:** Old economics (€28K LTV, sprint-only, high churn risk).

---

### F3 · Monetization Architecture
**Status:** Locked (v2.0 — rewritten)

**Answer:** Journey-led, modular, fixed scope at every tier.

Product ladder:

| Product | Price | Duration | Scope |
|---|---|---|---|
| X-RAY Scan | Free | Self-serve, 2 min | Automated buyability scan, 10 questions, situation-framed |
| The Map | €1,500 | 1 week | Full journey diagnostic: scored canvas, decision ledger, surface review, action plan |
| The Fix (1 module) | €5,000 | 2-3 weeks | One module: Positioning Lock, Surface Build, Motion Install, Find Design, Proof System, or System Map |
| The Fix (2 modules) | €8,000 | 3-4 weeks | Two modules combined |
| The Fix (3 modules) | €12,000 | 4-5 weeks | Three modules combined |
| The Fix (4+ modules) | €15,000 | 5-6 weeks | Four or more modules |
| Support | €1,500/month | Monthly, pause/resume | Bi-weekly sessions + async, copy adjustments, test plans |
| Review | €2,000/quarter | Quarterly | Re-scored canvas, drift report, next Fix scope |
| Starter Bundle | €5,000 (introductory) | 2 weeks | Map + Positioning Lock (normally €6,500) |

Pricing philosophy: The Map is priced to install widely (low barrier). The Fix is where revenue comes from. Support and Review create the ongoing relationship. The Starter Bundle at €5,000 matches the old Entry Product price point but delivers more (canvas + positioning).

**Decided against:** Hourly billing. Custom-scoped pricing. Single-product model. Open-ended retainer without canvas framework.

---

### F4 · Margin & Scalability Guardrails
**Status:** Locked (v2.0 — updated)

**Answer:** Module-based delivery caps. 65% gross margin floor maintained.

Delivery caps per module:
- Map: 10-12 hours
- Positioning Lock: 18-22 hours
- Surface Build: 18-22 hours
- Motion Install: 15-18 hours
- Find Design: 15-18 hours
- Proof System: 10-12 hours
- System Map: 8-10 hours
- Support: 6-8 hours/month
- Review: 4-5 hours/quarter

Total Starter Bundle: ~30 hours. Total 3-module Fix: ~55 hours.

At scale: canvas scoring and Find stage audits are automatable via Hurozo pipeline. Homepage audit (existing pzaudit) already semi-automated. Target: 60-70% of Map delivery automated within 6 months.

---

## INVESTMENT PATH — TYPE G: INVESTABILITY

### G1 · Compounding Growth Story
**Status:** Future Stage (updated)

**Answer:** Three compounding loops (same as v1), plus canvas creates switching costs.

The canvas accumulates client history. Every engagement adds to it. Switching to another firm means losing the baseline data and the system view. This creates natural retention without lock-in (the canvas is the client's, but the scoring methodology is PZ's).

---

### G2 · Capital Efficiency
**Status:** Future Stage (unchanged)

**Answer:** Model designed to be self-funding from client revenue before external capital is required.

---

### G3 · Exit / Scale Path
**Status:** Future Stage (updated)

**Answer:** Three paths (was two).

(1) Self-sustaining cash flow: build to €1M ARR with small team, canvas-led growth, certified practitioners.
(2) Strategic acquisition: GTM platform acquires methodology and client base.
(3) **New:** Platform play via Hurozo. The canvas + diagnostic engine becomes a SaaS product. PZ is the first customer. Other consultancies use the same infrastructure with their own frameworks. Hurozo becomes the "diagnostic lead magnet builder" platform.

---

### G4 · Founder / Team Investability
**Status:** Future Stage (unchanged)

**Answer:** Methodology documented and transferable. Key-person risk mitigation: certify 1-2 practitioners.

---

## CHANNEL ARCHITECTURE

### Marketing Channels
**Status:** Locked (v2.0 — updated)

Three active channels (same structure, updated mechanics):

1. **LinkedIn content engine** — primary. Now informed by Find Stage Questions (FP1-FP7). PZ's own content should score well on the same questions we use to diagnose clients.

2. **Lead gen agency partnerships** — agencies qualify using Outbound Readiness lens (live from v5.1). Low-scoring prospects routed to PZ for The Map. Agency gets a better client after PZ fixes the foundations.

3. **Scout/referral network** — Emmanuel Mondon and future scouts use the Situation Library (15 situations, 3 tiers) and Scout Scorecard (5 dimensions) to identify and qualify prospects. Prospect Log in Notion tracks every intro with hypothesis accuracy feedback.

New channel (v2.0): **Free X-RAY Buyability Scan** — self-serve lead magnet. Founder picks situation, enters URL, gets situation-framed diagnostic. Routes to The Map. Runs on Hurozo.

---

### Sales Process
**Status:** Locked (v2.0 — updated)

Updated flow:

```
PRE-CALL
  Free X-RAY scan run on prospect's homepage (by scout or prospect themselves)
  Situation hypothesis formed from Situation Library
  ↓
TRIAGE CALL (30 min, same as v1)
  Confirm scope, stage, current situation
  ↓
BOOK THE MAP (€1,500)
  "One week. Full journey scored. Canvas is yours regardless."
  ↓
MAP WEEK
  Surface audits → Founder session → Scored canvas + action plan
  ↓
FIX PROPOSAL
  "The canvas shows [stage] is broken. Here's the Fix scope."
  ↓
THE FIX (€5K-15K, modular)
  Sprint on broken stages, canvas updated
  ↓
SUPPORT + REVIEW (ongoing)
  Stay on the map. Catch drift. Plan next Fix.
```

---

## CHANGELOG v1.0 → v2.0

| Code | Change Type | Summary |
|---|---|---|
| S1-S6 | **New** | 6 new strategic decisions (relationship model, canvas, situation library, partner architecture, Find stage, situation lenses) |
| North Star | **Rewritten** | "Install foundation" → "Design and maintain buyer journey system" |
| A0 | **Updated** | JTBD layers mapped to Situation Library, T3 expanded with Pascal pattern |
| A1 | **Updated** | Level 2 category updated: "design and maintain buyer journey systems" |
| A2 | Unchanged | — |
| A3 | Unchanged | Note added: "Run LinkedIn ads" as emerging 7th alternative |
| A4 | **Updated** | 5th differentiator added: canvas-based system view |
| A5 | **Updated** | Two-level outcome: story travels + system visibility |
| A6 | **Rewritten** | Lost-deals forensic → scored canvas as entry wedge |
| A7 | Unchanged | — |
| A8 | Unchanged | — |
| B1 | Unchanged | — |
| B2 | **Updated** | Proof anchored to canvas stages, SENF added |
| B3 | **Rewritten** | Single sprint shape → phase-based effort |
| B4 | Unchanged | Note added: canvas reduces primary risk |
| C1 | **Updated** | Two-path entry, both leading to The Map |
| C2 | **Rewritten** | Sprint kickoff → Map week sequence |
| C3 | **Updated** | Map as risk reversal |
| C4 | **Rewritten** | Triage primary → Free scan → Map → Starter Bundle |
| D1 | **Rewritten** | Day 3 lost deals → scored canvas as activation moment |
| D2 | **Rewritten** | Day 1-5 sequence → Map week sequence |
| D3 | **Updated** | 3 days → 5 days (Map), 10 days (Starter Bundle) |
| E1 | **Updated** | Map week IS the onboarding |
| E2 | **Updated** | Canvas as operational anchor alongside ledger |
| E3 | **Rewritten** | Event-triggered → Review-triggered, built into relationship |
| E4 | Unchanged | Note added: canvas-based advocate story |
| F1 | Unchanged | — |
| F2 | **Rewritten** | Sprint economics → journey-based CLV model |
| F3 | **Rewritten** | Sprint-led → journey-led modular pricing |
| F4 | **Updated** | Module-based hour caps |
| G1 | **Updated** | Canvas creates switching costs |
| G3 | **Updated** | Added platform play via Hurozo |
| Channels | **Updated** | Free scan as new channel, scout system formalized |
| Sales Process | **Updated** | New flow: scan → triage → Map → Fix → Support → Review |

---

*Product.Zone — Commercial Decision Ledger v2.0*
*March 18, 2026*
*Replaces v1.0 (March 16, 2026)*
