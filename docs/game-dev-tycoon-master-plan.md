# Writer Tycoon → Game Dev Tycoon Evolution Master Plan

## 1) Vision: where we are headed

Transform the current writing-focused prototype into a **studio-management tycoon loop** inspired by Game Dev Tycoon:
- You run a studio (starting solo, scaling to team/company).
- You pick projects, scope/features, target platform/audience.
- You balance time, quality, bugs, hype, budget, staff burnout, and tech debt.
- Outcomes create revenue, fans, reviews, and long-term studio reputation.

### North-star player fantasy
"I founded an indie studio in a garage, survived near-bankruptcy, discovered a hit formula, hired a team, built an engine, and shipped genre-defining games."

---

## 2) Current-state assessment (from existing code)

### What already exists that we can reuse
- Core loop: choose job → produce words → submit → score → payout.
- Progression stats: money, multiplier, upgrades, reputation, royalties.
- Session pacing systems: momentum and streak.
- UI primitives: panels, cards, modal board, activity log, persistence.

### Key gaps versus game-dev-tycoon target
- No multi-axis production model (design/tech/art/bugs).
- No project planning phase (genre/topic/platform choices).
- No team/staff simulation (hiring, salaries, skills, burnout).
- No release/post-release lifecycle (patching, market decay, fan base).
- UI metaphor still writer desk, not studio dashboard.

---

## 3) Product pillars to guide all features

1. **Readable simulation**: systems should be learnable in 1–2 sessions.
2. **Meaningful trade-offs**: every major decision has upside + cost.
3. **Compounding identity**: studio strategy should feel unique over time.
4. **Fast feedback loops**: micro outcomes every 20–60s, macro every 5–15 min.
5. **Scalable architecture**: easy to add new genres/platforms/events without rewrites.

---

## 4) Domain model for the future sim

## 4.1 Entities (minimum)
- **Studio**: cash, fans, rep, office tier, morale, monthly burn.
- **Staff**: role, level, salary, stamina, specialties.
- **Project**: concept choices, budget, schedule, phase, progress bars.
- **Technology**: engine level, features unlocked, tooling quality.
- **Market**: platform install base, trend genres/topics, competitor noise.
- **ReleaseResult**: review score, units sold, refunds, fan delta.

## 4.2 Core resources
- Design Points (DP)
- Tech Points (TP)
- Art/Polish Points (AP)
- Bug Load (BL)
- Hype
- Team Energy

## 4.3 Outcome formula family (high-level)
- Quality = weighted(DP, TP, AP, fit bonuses) - bug penalties
- Review score = quality + trend alignment + rep bias + variance
- Sales curve = (hype + reviews + fanbase) × platform size × decay
- Net profit = revenue - dev cost - salaries - marketing - support

---

## 5) Phased execution roadmap (recommended)

## Phase 0: Stabilize foundation (1–2 sessions)
**Goal:** prepare codebase for growth before adding heavy simulation.

Deliverables:
- Extract inline JS into modules (`state.js`, `economy.js`, `ui.js`, `simulation.js`).
- Introduce versioned save migrations (`saveVersion`, migration map).
- Build tuning config object for balancing constants.

Exit criteria:
- No behavior regressions in current writer loop.
- Save migration works from existing localStorage save.

## Phase 1: Re-theme UI + language (2–4 sessions)
**Goal:** achieve first-pass "studio sim" look without changing all mechanics.

Deliverables:
- Rename UI concepts: manuscript → project pipeline, jobs → contracts.
- Re-skin dashboard into studio ops board (kpi cards, market ticker, pipeline lane).
- Replace writer-specific copy with studio-specific labels.

Exit criteria:
- Same mechanics, but interface clearly reads as management sim.

## Phase 2: Multi-bar project production (4–7 sessions)
**Goal:** replace single word-count gate with multi-resource progress.

Deliverables:
- Project has 3 bars: Design, Tech, Polish.
- "Work sprint" actions allocate production points by role/upgrades.
- Bugs accrue as a side effect and reduce quality if unresolved.

Exit criteria:
- Project completion depends on balancing bars + bug cleanup.

## Phase 3: Release + post-launch economy (4–6 sessions)
**Goal:** make outcomes feel like shipping a game, not submitting text.

Deliverables:
- Release modal with expected score/sales preview bands.
- Review score + launch sales + weekly tail simulation.
- Patch cycle decisions (fix bugs vs start new project).

Exit criteria:
- At least 3 distinct project outcomes (flop/moderate/hit) are felt in play.

## Phase 4: Team and studio scaling (5–9 sessions)
**Goal:** from solo creator to studio management.

Deliverables:
- Hire/fire staff, role mix effects, salary burn.
- Morale/energy and crunch penalties.
- Office tiers unlock team capacity + feature complexity.

Exit criteria:
- Staffing choices become the dominant midgame strategy lever.

## Phase 5: Strategy depth systems (ongoing)
**Goal:** long-term replayability.

Deliverables:
- Genre/topic/platform combos with synergy memory.
- Market trend events and competitor launches.
- Engine R&D and franchise/sequel mechanics.

Exit criteria:
- 30+ minute runs produce differentiated studio stories.

---

## 6) Interface migration plan toward "Game Dev Tycoon" feel

## Layout target
- **Left column:** Studio/Staff roster + hiring + morale.
- **Center workspace:** Active project timeline with phase gates.
- **Right column:** Finance, market trends, and launch forecasts.
- **Bottom feed:** event log + inbox decisions.

## Visual language
- Replace manuscript cards with kanban-style production cards.
- Add iconography for Design/Tech/Art/Bugs.
- Introduce timeline/progress ribbons instead of pure text progress.
- Keep current dark neon palette initially to avoid full art overhaul early.

## UX pattern priorities
1. Always-visible next best action.
2. Forecast before commitment (risk range).
3. Post-action explanation (“+12 tech, +5 bugs due to crunch”).

---

## 7) Engineering strategy and anti-fragility

## Technical debt controls
- Keep game constants in one `BALANCE` object.
- Pure calculation functions for outcomes (testable).
- Single source of truth store + deterministic tick function.

## Save data strategy
- Save schema:
  - `meta: { saveVersion, createdAt, updatedAt }`
  - `studio`, `staff`, `projects`, `economy`, `market`, `unlocks`
- Migrations named `v20_to_v21`, `v21_to_v22`, etc.

## Test strategy for browser game
- Unit-like checks for economy formulas via node scripts.
- Snapshot tests for migration transforms.
- Smoke scenario scripts (start → ship → payout sanity).

---

## 8) Balancing and telemetry plan

## Balancing loops
- Early game: 2–4 min to first release.
- Mid game: meaningful expansion decision every ~8–12 min.
- Failure should be recoverable but painful.

## Telemetry (local debug first)
Track:
- average run length
- bankruptcy rate
- hit rate (review > 8)
- time to first hire
- churn signals (no action for >90s)

Use telemetry to tune:
- salary pressure
- bug penalties
- market volatility
- trend bonus magnitude

---

## 9) Concrete backlog (ordered, implementation-ready)

## Now (next 3 tasks)
1. **Codebase split from single HTML script into modules** (no design changes).
2. **Save versioning + migration framework**.
3. **Rename game nouns in UI to studio-sim terminology**.

## Next
4. Replace word-count bar with 3-track production bars.
5. Add bug generation and "polish sprint" bug reduction.
6. Add release result screen with quality breakdown.

## Then
7. Introduce weekly tick economy and salary burn.
8. Add first hireable role (Programmer) and stamina impact.
9. Add trend system for genre/topic boosts.

---

## 10) Risks and mitigations

- **Risk:** Feature creep before foundation is modular.
  - Mitigation: gate all new systems behind Phase 0 completion.

- **Risk:** Formula opacity frustrates players.
  - Mitigation: expose concise outcome tooltips and forecast ranges.

- **Risk:** Save corruption during rapid schema changes.
  - Mitigation: strict version migration and fallback defaults.

---

## 11) Definition of done for "first true game-dev-tycoon milestone"

We can declare success for MVP when a player can:
1. Start a studio.
2. Plan a game concept (at least 2 choice axes).
3. Produce using multi-resource bars.
4. Release and receive review/sales outcome.
5. Use profits/losses to alter next strategic choice.

That loop is the bridge from current prototype to genuine tycoon identity.
