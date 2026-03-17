# Commercial Decision Ledger
## Product.Zone

**Purpose:** Canonical record of all locked commercial decisions. Human-readable, version-controlled.  
**Operational layer:** Notion K&D database (queryable by client, status, leverage).  
**Sync discipline:** When a decision is locked in Notion, it is added here in the next commit.  
**Version:** 1.0 · March 16, 2026

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

## NORTH STAR

### Primary JTBD
**Status:** Locked

**Answer:** Install commercial foundation before the next move breaks the same way.

Product.Zone is prerequisite infrastructure, not one project among many. Almost every commercial capability project a B2B software team must run — hiring a rep, building outbound, entering a new market, creating proof, briefing an agency — fails or stalls without a working buying path underneath it.

Three entry triggers (different situations, same underlying job):
1. "I'm about to hire my first sales rep and genuinely don't know how to hand this over."
2. "We're getting meetings but not converting. Changed the deck, the site, the pitch. Nothing sticks."
3. "Expanding into a new segment or region. Need to start the story fresh for this context."

**Decided against:** Single primary JTBD framing (too narrow). Generic "improve GTM" (too abstract).

---

## BUYING PATH — TYPE A: POSITIONING

### A0 · Client-Side JTBD
**Status:** Locked

**Answer:** Three jobs buyers think they are hiring for, each mapping to one transition. Distinct from the supplier-side North Star JTBD ("install commercial foundation — that's how we see the job. Clients arrive describing one of these three.

**Primary entry JTBD: T2** — "Enable others to carry the commercial story without me explaining it every time." The rep hire moment is the most concrete, most time-pressured, and creates the clearest before/after story. T1 tends to be too early (founders unsure they need this yet). T3 tends to be too late (already burned out). T2 has urgency, specificity, and a clear forcing event. Homepage hero, primary outbound, and LinkedIn L3 lead with T2.

All three JTBDs lead to the same Sprint. S02 catches all three — no buyer should reach it without recognising their moment.

**Three-layer JTBD architecture** (per ChatGPT recommendation — keeps internal model clean):

| Layer | T1 — First Sales | T2 — Bringing Others In (PRIMARY) | T3 — Scaling Beyond You |
|-------|-----------------|-----------------------------------|-------------------------|
| **Layer 1: Unavoidable projects** | Make first sales work / define buyer and wedge / sharpen the pitch / package the first offer | Hire and onboard first commercial lead / make the story transferable / build repeatable sales surfaces / grow through outbound / build early pipeline | Defend price and package clearly / create proof that reduces switch risk / systemize the commercial motion / scale beyond founder-led selling / improve adoption / turn customers into proof |
| **Layer 2: Observable founder patterns** | Pitching every call, deck different every time, no clear wedge, interest but no conversions | About to hire rep, briefing agencies badly, deck needs voiceover, board asks questions founder can't surface-answer | Stepped back once, conversion dropped, stepped back in. Every rep tells a different story. |
| **Layer 3: Product.Zone framing** | "First sales become repeatable" | "Others can now carry it" | "The system runs without you" |

**Decided against:** Single primary JTBD only (too narrow). Full list of 100 projects as framing (overwhelming, not actionable for surface design).

---

### A1 · Category
**Status:** Locked

**Answer:** Two-level frame.

Level 1 (borrowed shelf): Go-to-market strategy & sales enablement. Existing category, no explanation required. Used for recognition.

Level 2 (own language): "We design and install commercial buying paths for B2B software." Used immediately after Level 1 for contrast.

**Decided against:** Single new-category label only (explanation burden). Generic "GTM consultant" (too broad, no contrast).

---

### A2 · Customer
**Status:** Locked

**Answer:** Situation-based ICP covering four profiles. "Responsible for making a new software product convert in a market where the buying path hasn't been built yet."

Four valid profiles: startup founder-CEO, corporate venture commercial lead, SME leader expanding into new software product space, scale-up GTM lead entering new region or JTBD.

Positive conditions: B2B software with at least one paying customer or pilot. Personally accountable for commercial outcomes. Has tried "just do more" and it didn't scale.

Sharp disqualifier: "If your main problem is getting attention rather than making interested buyers actually buy — we're not the right first call."

Explicit disqualifiers: hardware-first products, pure B2G, lead generation as primary problem, pre-product stage, advisory-only without co-building.

**Decided against:** "Founder" as primary identity label (excludes equivalent profiles). No disqualifiers (vague ICP signals insufficient confidence).

---

### A3 · Alternative
**Status:** Locked

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

**Decided against:** No named alternative (leaves buyer with no urgency frame, Q9 Missing).

---

### A4 · Difference
**Status:** Validated

**Answer:** DFY not advisory, fixed scope, decisions-first sequencing, handoff-ready output.

Four differentiators: (1) We produce artifacts, not recommendations. (2) Fixed scope at every tier — buyer knows exactly what they're getting before signing. (3) Decisions locked before any surface is built. (4) A first sales rep could be onboarded from the Notion workspace alone.

**Decided against:** Advisory/coaching model (Estner model). Custom-scoped DFY (every engagement built from scratch).

---

### A5 · Outcome
**Status:** Validated

**Answer:** The commercial story travels and converts without the founder in the room.

Prospects can say yes without the founder explaining it. Reps carry the pitch. The deck works without voiceover. The motion runs after the founder steps back.

Test: Could a first sales rep be onboarded from the Notion workspace alone, without the founder present?

**Decided against:** "Better positioning" (too abstract). "More leads" (wrong category — demand generation).

---

### A6 · Wedge Use Case
**Status:** Locked

**Answer:** Lost deals forensic + homepage mirror in the kickoff session.

Part 1: "Bring your last three lost deals — we map where the buying path broke in each one." Part 2: Mirror the same gaps against the live homepage. The cause of deal failures is sitting visibly on the surface right now.

Makes the problem personal (real deals) and immediately actionable (evidence is on their homepage today).

**Decided against:** Homepage audit only (too abstract without deal context). First 5 minutes pitch rebuild (too narrow).

---

### A7 · Market Bet
**Status:** Locked

**Answer:** European B2B SaaS early revenue, DACH/Benelux/Nordics.

One sentence: "If you own revenue for a B2B SaaS product in Europe, have a handful of customers, and sales only work when you're in the room — you're my list."

Space/geo = channel bet, not market bet. Does not narrow public positioning.

**Decided against:** Lead with space/geo as named vertical (narrows too early). Global English-speaking SaaS market (loses local trust advantage and referral density).

---

### A8 · Category Maturity
**Status:** Locked

**Answer:** Emerging market — problem education comes before differentiation.

Product.Zone is in an emerging category. The alternative is "doing nothing" or manual workarounds, not a named competitor. Messaging leads with problem education: "here's why you need this category at all" before "here's why we're better than X."

| Market State | Alternative Expression | Messaging Lead |
|--------------|------------------------|----------------|
| Educated | Named competitor | Differentiation |
| Emerging | "Doing nothing" / manual workaround | Problem education |

**Decided against:** Leading with differentiation on an emerging market (assumes buyer awareness that doesn't yet exist).

---

## BUYING PATH — TYPE B: TRUST

### B1 · Owner / Champion
**Status:** Validated

**Answer:** The person personally accountable for commercial outcomes — not "marketing" or "brand."

Startup context: founder-CEO. Corporate venture: commercial lead or venture owner.

Qualification criterion: must be in every session themselves. Cannot delegate to a team member.

**Decided against:** VP Sales or CMO as primary champion (too execution-focused, less likely to own the positioning bet).

---

### B2 · Proof Type
**Status:** Locked (Lyrasense metric pending confirmation)

**Answer:** Three-layer proof matched to buyer profile.

Layer 1: Before/after story with conversion metrics — primary format.
Layer 2: Reference calls matched to profile — Lyrasense/Senf for conversion proof, Fugro/VirGeo for corporate venture and space/geo.
Layer 3: Four testimonials — credible for warm leads, insufficient for cold surfaces.

Outstanding: Confirm Lyrasense before/after metric with Nader before using in live deck.

**Decided against:** Metrics only (no narrative). Testimonials only (insufficient for cold). Reference calls only (too late-stage as primary proof).

---

### B3 · Effort Shape
**Status:** Validated

**Answer:** Fixed scope, weekly sessions, 5–7 hours total founder time.

Entry Product: ~5–7 hours across 3 weeks. Sprint: ~5–6 hours across 3–4 additional weeks. Between sessions: no deliverables required. All analytical prep done by Product.Zone — founder arrives to find analysis done and options visible.

Surface language: "No prep beyond a link to your homepage and one recent deal."

**Decided against:** Intensive bootcamp format (reduces absorption time between sessions).

---

### B4 · Primary Risk
**Status:** Locked

**Answer:** Fit + timing combo — three-part objection.

Crisp articulation: "I'm worried this will be a smart, well-crafted system that doesn't quite fit our specific context at this moment — and then it becomes just another deck instead of a change in how we actually sell."

Three underlying worries:
1. Fit: "Our buyers are different / our deals are complex / we're in a niche vertical."
2. Timing: "Too early or too late? Shouldn't we wait until after X?"
3. Behaviour change: "Will we end up with clever language and no change in how we actually sell?"

**Decided against:** Framing as price/budget objection (secondary). "Does the methodology work?" (buyers don't doubt the framework, they doubt applicability).

---

## BUYING PATH — TYPE C: MOVEMENT

### C1 · First Step
**Status:** Locked

**Answer:** 30-minute Buying Path Triage call.

Promise: "In 30 minutes, we'll tell you exactly where your buying path is breaking and whether now is the right moment to fix it with us."

Structure: Min 0–10 how they sell today. Min 10–20 map buying path live on virtual whiteboard. Min 20–30 name the primary constraint and outline the fix (or why now is not the moment).

After call: 1-pager with where it breaks, what to install, recommended next step.

Surface CTA: "Schedule a 30-minute Buying Path Triage — no prep beyond a link to your homepage and one recent deal. No commitment to work together."

**Decided against:** Generic "book a call" (no specific promise, no defined agenda). X-RAY as sole first step (lacks the live mapping moment that creates strongest conviction).

---

### C2 · Start Recipe
**Status:** Locked

**Answer:** Intake survey immediately, kickoff call within 72 hours.

Sequence after yes: (1) Intake survey sent immediately — homepage URL, sales deck, outbound samples, call transcripts, questionnaire. (2) 30-min kickoff call — materials check, first impressions shared, calendar locked, Notion workspace created.

Product.Zone arrives to kickoff having already scanned surfaces and formed first impressions.

Note: Legacy intake survey needs refresh before next engagement.

**Decided against:** No pre-work (wastes kickoff on logistics). Async-only onboarding (loses the "first impressions shared" signal).

---

### C3 · Risk Reversal
**Status:** Locked

**Answer:** Timing validation built into the entry product.

The entry product explicitly outputs a timing verdict. Buyer wins either way: story is rep-ready (proceed to hire) or they know exactly what to fix before hiring.

Four-step reframe for timing objection:
1. Validate: "Timing matters more than most think."
2. Diagnose: "Too early = product still pivoting. Too late = burning out on every demo. Which are you?"
3. Flip: "Real risk is hiring a rep with no path to run — they improvise, you rescue, vicious cycle."
4. Test: "Sprint tells you both: is story rep-ready now, and if not, what are the 2–3 blockers?"

Key line: "Smart to think about timing. The real risk isn't doing this Sprint — it's hiring your rep with no path for them to run."

**Decided against:** Discount as risk reversal (reduces perceived value). Money-back guarantee (wrong category for a strategic intervention).

---

### C4 · Entry Motion
**Status:** Locked

**Answer:** Direct triage booking primary (80%), X-RAY supporting (20%).

Primary path: Homepage → Schedule Buying Path Triage → 30-min live session → €5K Sprint.
Secondary path: Homepage → Free X-RAY → results page prompts triage booking → Sprint.

X-RAY three supporting functions: self-qualifier (filters wrong-stage visitors), async warmer (gets lukewarm leads into system), call prep (triage caller has X-RAY results upfront).

Principle: Live human conversation is always the conversion lever. X-RAY warms and qualifies but never leads.

**Decided against:** X-RAY as primary entry (tool use signals curiosity, not buying intent). Triage as sole entry without X-RAY (loses self-qualification function).

---

## BUYING PATH — TYPE D: ACTIVATION

### D1 · Activation Moment
**Status:** Locked

**Answer:** Day 3 live review — lost deals mapped with red breakpoints showing exactly where the buying path snapped.

Specific, visual, uses their actual deals — not theory. Emotional shift: "They get it. This isn't generic advice — it's our deals."

Surface language: "Day 3, you'll see your lost deals on screen with red X's showing exactly where the buying path snapped."

**Decided against:** Homepage audit as primary activation (feels like a website critique). Diagnostic report (too document-heavy). Decision ledger (internal tool, not emotional enough).

---

### D2 · First Value Path
**Status:** Locked

**Answer:** Day 1 kickoff → Day 2 Product.Zone builds → Day 3 live review → Day 5 Decision Ledger v1.

Day 1: Kickoff call, they bring 3 lost deals + homepage/deck, first draft buying path drawn together.
Day 2: Product.Zone finalises Buying Path Failure Map with 3–5 specific breakpoints.
Day 3: Live review — red X's on their buyer journey, named breaks, missing surfaces identified.
Day 5: Decision Ledger v1 delivered — 18 positioning decisions with current status.

**Decided against:** Async-only delivery (loses the activation moment impact).

---

### D3 · Time to Value
**Status:** Locked

**Answer:** 3 days. Zero ambiguity.

First value: Buying Path Failure Map — their deals diagnosed, 3–5 fixes identified, language for the problem. Secondary value: Decision Ledger v1 on Day 5.

Surface language: "First value: Day 3. Zero ambiguity."

---

## USAGE PATH — TYPE E: POST-YES

### E1 · Onboarding Motion
**Status:** Locked

**Answer:** Intake + kickoff + Day 3 activation sequence. (See also C2 Start Recipe and D1 Activation Moment — these three decisions describe the same sequence from different perspectives.)

Buyer promise: "You'll see your problem named and visualised by Day 3 — mapped from your actual deals, not a generic framework."

**Decided against:** Generic onboarding checklist (no designed activation moment). Async-only start (loses the live impact of Day 3).

---

### E2 · Habit / Embed Loop
**Status:** Locked

**Answer:** Ledger sign-off before any commercial move.

Three repeatable micro-behaviours:
1. New hires/agencies ledger-tested — every rep, agency, partner pre-cleared against 18 decisions before briefing.
2. Surface updates ledger sign-off — homepage refresh, deck v2, new landing page all ledger-tested before publish.
3. Lost deal post-mortem — weekly deal review mapped against the buying path.

Cancellation pain: the decision ledger becomes external commercial memory. Stopping feels like losing institutional knowledge.

Key client language that signals embed: "Run it by Product.Zone first" / "Does this pass the ledger?" / "Let's map that lost deal."

**Decided against:** Outcome-tracking retainer (measures results but doesn't create operational dependency). Content retainer (generates output but doesn't embed the decision system).

---

### E3 · Expansion Trigger
**Status:** Locked

**Answer:** Stabilisation Retainer when positioning is tested and stable. Next Sprint when a clear hypothesis for the next path exists.

Trigger signal: client's first rep closes first deal independently. That moment triggers the retainer conversation.

Expansion thresholds by non-founder deal count:
- 0–2/mo → Sales Motion Sprint
- 3–5/mo → Stabilisation Retainer
- 6–10/mo → New segment path

**Decided against:** Time-based upsell ("after 3 months, buy next thing") — not tied to value signal.

---

### E4 · Advocate Story
**Status:** Locked

**Answer:** "First rep closes first deal independently." That's the moment clients become evangelists.

Three-beat anatomy in every advocate story:
1. Diagnostic moment: "Week 1 they mapped our lost deals."
2. Concrete build: "Built the deck/homepage/surfaces."
3. Rep independence: "Rep closed first deal solo."

Kitchen-table version: "Mapped our lost deals Week 1. Hired a rep three weeks later. They closed their first deal without me. Sales ramp is now 3 weeks, not 3 months."

Systematic capture: post-Sprint Week 4 survey asking "did your first rep run a call without you yet?"

**Decided against:** Logo/testimonial only (no emotional hook, doesn't travel naturally). Formal case study (too structured for kitchen-table referral spread).

---

## BUSINESS PATH — TYPE F: ECONOMICS

### F1 · Value Metric
**Status:** Locked

**Answer:** Deals closed by non-founders per month.

Tracks founder liberation (core desire), compounds as team grows, justifies pricing (ROI per deal created), drives expansion (each threshold unlocks next offer).

Phase caveat: for clients still in "story isn't buyable yet" phase, the leading metric is self-selection rate and clarity score — can the story be repeated without the founder? Non-founder close rate becomes measurable from Week 4 onward.

**Decided against:** Conversion rate improvement (too abstract). Revenue growth (too many variables). "Feels better" (not measurable).

---

### F2 · Unit Economics
**Status:** Locked

**Answer:** €28K average LTV · 23x LTV:CAC · 12-day payback · 83 hours total delivery · €337/hour effective rate.

Full arc (100 clients):
- Entry Product €5K: 100% take rate, 25 hrs delivery, €1.2K CAC, 12-day payback
- Sales Motion Sprint €10K: 40% convert, 50 hrs delivery
- Stabilisation Retainer €2K/mo × 6 avg: 25% of Sprint clients
- Second Sprint €10K: 15% of Sprint clients

Key ratios: LTV:CAC 23x (target 3x minimum), payback 12 days (target <45), hours per €1K: 6.5 hrs (target <10). Math works without volume. What breaks first at scale: at 12 clients/mo delivery overload requires second full-timer.

---

### F3 · Monetization Architecture
**Status:** Locked

**Answer:** Sprint-led, fixed scope at every tier, retainer upsell.

Tier ladder: Entry Product €5K / 3 weeks → Full Sprint €10K / 6 weeks → Stabilisation Retainer €2K/mo. No minimum commitment beyond current product. No custom pricing. Fixed scope is itself a signal of the methodology — we practice what we diagnose.

**Decided against:** Custom-scoped pricing (destroys margin predictability). Hourly billing (misaligns incentives, punishes efficiency).

---

### F4 · Margin & Scalability Guardrails
**Status:** Locked

**Answer:** 83-hour arc cap, no custom scope, 65% gross margin floor.

Delivery caps: Entry 25 hrs, Sprint 50 hrs, Retainer 8 hrs/mo. Total arc: 83 hours. Gross margin floor: 65%. Rules: out-of-scope requests either declined with redirect to next product tier, or explicitly re-scoped as a new engagement at a new price.

At scale: 80% of prep work automatable (homepage audit, decision inference, competitive landscape) — preserves margin as volume increases.

**Decided against:** Flexible scope per client (destroys margin predictability, models the failure we diagnose in clients).

---

## INVESTMENT PATH — TYPE G: INVESTABILITY

*All four decisions mapped. Currently future stage — not operationally relevant until fundraising or significant partnership structuring.*

### G1 · Compounding Growth Story
**Status:** Future Stage

**Answer:** Revenue loop flywheel — three compounding loops.

Proof loop: client results become Validate proof for next buyer. Reputation loop: advocate story (E4) warms new buyers before they land. Channel loop: satisfied clients refer to their sector network, creating sector-specific proof density over time.

---

### G2 · Capital Efficiency
**Status:** Future Stage

**Answer:** 23x LTV:CAC is the foundation. Model is designed to be self-funding from client revenue before external capital is required.

Burn multiple and rule-of-40 calculations become relevant at scale (€500K+ ARR).

---

### G3 · Exit / Scale Path
**Status:** Future Stage

**Answer:** Two plausible paths. (1) Self-sustaining cash flow — build to €1M ARR with small team, product-led growth via automated X-RAY, certified practitioners extending delivery. (2) Strategic acquisition — GTM platform acquires the methodology and client base. Decision point approximately 24–36 months out.

---

### G4 · Founder / Team Investability
**Status:** Future Stage

**Answer:** Methodology documented and transferable — not locked in the founder's head. (Same promise made to clients.)

Key-person risk mitigation strategy: certify 1–2 practitioners who can deliver independently. The methodology codified in engagement playbooks and canonical framework documents.

---

## CHANNEL ARCHITECTURE

### Marketing Channels (how leads are generated)
**Status:** Locked

Three active channels:
1. **LinkedIn content engine** — primary, inbound + warmed-up outbound. Builds authority, warms prospects before contact.
2. **Lead gen agency partnerships** — agencies qualify prospects using Outbound Readiness Diagnostics. Low-scoring prospects are natural Product.Zone referrals.
3. **Emmanuel Mondon scout channel** — space/geo/Earth Observation sector. Warm introductions to qualified commercial leads.

### Sector Doors (which profiles are served through which relationship paths)
**Status:** Locked (architecture), Partially active (execution)

| Door | Status | Credential | Domain signals |
|------|--------|-----------|----------------|
| Space / Geo / EO | Active | Fugro/VirGeo proof, Emmanuel channel | Dual use, B2G, upstream/downstream |
| AI / Cloud | Available | Hurozo founder background | Platform layer, dev-led growth |
| Chemtech / Healthtech | Available | Chem-pharma background | Regulatory, scientific validation, committee procurement |
| Marketplaces / Sales Channels | Available | Asellion founder background | Multi-sided, GMV-based, channel conflict |
| Corporate Venture | Future | Identified, no active channel | Internal stakeholders, portfolio dynamics |

**Architecture decision:** Marketing channels and sector doors are formally separated. Market bet determines what surfaces say. Sector doors determine how specific relationship paths are opened. LinkedIn content speaks to all doors simultaneously; sector-specific language is deployed in each door's context.

---

## STRATEGIC DECISIONS

### S02 · Slide Design: Three-Transition Self-Selection Frame
**Status:** Locked

**Answer:** Keep the three-transition structure (T1 First Sales, T2 Bringing Others In, T3 Scaling Beyond You) as the organising frame. Function: help prospects articulate where they are using a simple 3-fold model.

Replace "you want to" aspiration language with visceral trigger moments per transition. Board alignment and outbound/collab briefing failure sit under T2. New market entry sits under T3.

**Decided against:** Lead with trigger moments, reveal transition pattern underneath (loses diagnostic simplicity). Split across two slides (adds a slide without proportionate value).

---

## OPEN ITEMS

| Item | Priority | Context |
|------|----------|---------|
| Confirm Lyrasense before/after metric with Nader | High — before next deck use | B2 Proof Type — most credible case study, needs exact numbers |
| Refresh intake survey | Before next engagement | Legacy version exists, needs update for current playbook + 4 profiles + new wedge framing |
| Fix S06 resolution copy in Figma | Figma production | "Nothing changed about the product/market" is wrong — the bet gets clearer, segment chosen |
| Add Day 3 activation moment to homepage and deck | Figma production | Highest-leverage missing surface element |
| Replace generic CTA with Buying Path Triage language | Figma production | C1 decided, not yet on surfaces |
| Add timing validation framing to S12 self-selection slide | Figma production | C3 decided, not yet on surfaces |
| Add S01b Core Insight slide | Figma production | "Building is solved. The hard question moved." |
| Develop sector door language for AI/Cloud and Chemtech | Channel development | Background exists, surface language not built |
| Build Client Diagnostic View | Next artifact | Derived from master ledger — Locked/Fuzzy/Missing only, smallest viable wedge, business consequence, next 3 decisions |

---

## VERSION HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | March 16, 2026 | Initial commit. All 30 commercial decisions mapped across Buying Path (A–D, 19 decisions), Usage Path (E, 4 decisions), Business Path (F, 4 decisions), Investment Path (G, 4 decisions). Channel architecture and strategic decisions added. Open items documented. |

---

*canonical/commercial-decision-ledger.md*  
*Product.Zone · Hurozo*  
*Sync with Notion K&D database (d7131da5-62d8-4e59-ab42-3b5760ad960d)*
