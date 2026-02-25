# Writer Tycoon Growth Plan (Game-Dev-Style Flow, Writer Theme)

## 1) Product direction

We are **not** building a game-development simulator clone.
We are building **Writer Tycoon** with a similar management cadence:
- plan work,
- execute milestones,
- handle market shifts and operating pressure,
- publish,
- reinvest and scale.

The fantasy is a writer building a publishing business over time.

---

## 2) Core identity guardrails

1. **Writer-first fantasy**: chapters, drafts, edits, manuscripts, publication runs.
2. **Tycoon structure**: strategic decisions, resource pressure, growth trade-offs.
3. **Readable systems**: every modifier should be legible in UI.
4. **No reskin-only drift**: mechanics must reinforce writing/publishing, not studio-dev jargon.

---

## 3) Target loop (inspired by management sims)

1. Choose assignment / milestone.
2. Choose writing mode (steady / fast draft / editorial polish).
3. Produce text to target.
4. Receive quality + earnings outcome.
5. Pay operating burn, react to demand trend.
6. Reinvest in tools/reputation and continue.

---

## 4) Current systems (already present)

- Assignment board + milestone progression.
- Momentum + streak bonuses.
- Market trend bonus and timer.
- Operating burn + debt pressure.
- Save versioning and migration pipeline.
- Balance constants centralization (`BALANCE`).

These are strong foundations for deeper Writer Tycoon systems.

---

## 5) Next Writer-Tycoon systems (priority order)

## Phase A — Writing craft layers
- Add 3 writing tracks per milestone:
  - **Draft Strength**
  - **Voice/Style**
  - **Editing Pass**
- Final quality uses weighted blend by assignment type.
- Risk choice: publish early vs spend more time editing.

## Phase B — Audience + catalog economy
- Add audience segments (literary, commercial, niche fandom).
- Add backlist/catalog decay + rediscovery spikes.
- Add launch window events (festival mention, critic roundup, social buzz).

## Phase C — Team and outsourcing
- Hire editor, proofreader, marketer, ghost collaborator.
- Each role modifies quality, speed, burn, and trend exploitation.
- Add burnout and morale to avoid one dominant strategy.

## Phase D — IP strategy
- Introduce standalone vs series choices.
- Sequel bonuses from existing fanbase.
- Penalty for over-milking weak IP.

---

## 6) UI direction (Writer Tycoon tone)

Keep the current dark management panel style, but keep labels writer-native:
- Manuscript Pipeline
- Assignment Board
- Writer Brief
- Editor Debrief
- Publication Run

Avoid game-dev-only terms like engine, vertical slice, sprint unless contextualized to writing.

---

## 7) Economy tuning principles

- Early game: player should survive with average play.
- Mid game: poor strategic fit (mode/trend mismatch) should be felt within 2–4 cycles.
- Debt should be recoverable but scary.
- Streak + trend + mode should be additive but capped and understandable.

---

## 8) Technical roadmap

1. Split `WriterTycoon.html` script into modules.
2. Keep `BALANCE` as single tuning source of truth.
3. Keep deterministic tick loop behavior.
4. Continue schema migrations with explicit save versions.
5. Add lightweight formula tests for payout/quality/burn.

---

## 9) Done definition for the next major milestone

Writer Tycoon is on-track when a player can:
1. choose a writing strategy,
2. feel trade-offs between quality/speed/cost,
3. react to audience demand shifts,
4. sustain or grow a catalog business across multiple publications,
5. tell a distinct "writer career" story by the end of a run.

