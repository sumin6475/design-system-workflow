# Step Playbook

Detailed facilitation for each of the 7 steps. Read before running. The throughline: **show concrete things, let the user react, lock, move on.** One decision at a time.

---

## Step 1 — Research

Goal: find what "good" means for this app, through the user's reactions to real products.

- Curate **6–8 real, named** reference products (not vague image searches). Each must have a **reason tied to the app** — what it tests about the user's taste.
- **Span the territory.** Put references at different points (very minimal ↔ rich; restrained accent ↔ bold accent; type-driven ↔ image-driven) so reactions triangulate rather than all pulling one way.
- Group them (e.g. "editorial warmth", "the reveal moment", "boutique craft") so the user can see what each cluster tests.
- **Give links.** Screenshots lie about how a site breathes. Ask the user to glance at the 2–3 that intrigue them.
- Ask for: which **3 survive**, which **one they recoil from** most (as useful as keeps), and any **"yes but"**.
- Synthesize their reactions into a one-sentence taste statement and reflect it back. Note what got eliminated and why.

Convergence often happens faster than expected — if the user gives sharp reactions, you may lock the direction here.

---

## Step 2 — Directions (mood board, made real)

Goal: turn the taste statement into 2–3 concrete directions and let the user pick.

- All directions share the locked DNA; they **differ on one axis**, usually how far the accent color goes (restrained accent → accent as full character → typographic-editorial).
- **Render them.** Build an HTML artifact with one card per direction, each showing the **same screen** (ideally the app's payoff screen) so it's apples-to-apples. Real color, real type, real shadow.
- Give each card a short name and a one-line "what this is / the risk" note.
- Ask which number feels most like their app; accept "yes but" and mixes ("2's headline + 3's type").
- If the user references an external template as "similar", fetch it and audit: what matches their DNA, what differs (often the accent color or a gradient that collides with the guardrails). Use it for **structure/layout/depth**, not mood, if the mood conflicts.

---

## Step 3 — Design language

Goal: the actual human-readable spec.

Draft all of:
- **Typography** — display font + body font, size scale, weights, letter-spacing, line-height. Name where each font loads from.
- **Color** — background(s), text tiers, accent tiers, border — each with *what it's for*.
- **Spacing / radius / shadow** — the scales, with notes (e.g. "section-gap floor 48px").
- **Component inventory** — only what the MVP needs; name the ONE core component (e.g. MatchCard).
- **Tone of voice** — 1–2 example lines in the app's real voice.

Present it, take edits, lock. Decide the accent color's exact role here (where it may and may not appear).

If the user is unsatisfied with a font, run a **font comparison card** (same headline in 3–4 candidate fonts on the real background) before locking. If a rendered font later "looks different" than the user's pick, suspect a failed CDN font load falling back to a default.

---

## Step 4 — Tokens + rules

Goal: machine-readable system. Two parts, both required.

**Values:**
- `tokens.json` — structured source of truth. Group by color/font/space/radius/shadow. Every value carries a `use` note.
- Framework config (e.g. `tailwind.config.js`) — **derived** from tokens.json. Note the derive direction: change tokens.json first, mirror to config.

**Rules — `DESIGN.md`:** the highest-value file. Include:
1. What the app feels like (1 paragraph, from Phase 0).
2. Color rules — where the accent may/may not go; "never invent colors".
3. Typography rules — weight floors, label size floor, no thin/all-caps.
4. Human-feel rules (see `human-feel-rules.md`).
5. Shape & depth rules.
6. Component inventory.
7. AI-cliché guardrails (audit list).
8. How to reference this when prompting.

Format choice: offer JSON-only, framework-only, or both. "Both" (JSON source + framework output) is the sensible default because the JSON stays portable across tools.

---

## Step 5 — Delivery

Goal: the AI receives the system reliably. Tailor to the builder.

- **Prompt-based tools (Lovable, v0):** paste tokens and reference the system every prompt; or publish an npm package to reuse foundations across projects. Higher value here because these tools don't persist context.
- **Repo-based tools (Claude Code, Codex, Cursor):** the files live in the repo and the agent reads them automatically. Add a pointer block to `CLAUDE.md` (or `AGENTS.md` for Codex) that: points at DESIGN.md and tokens.json, forbids inventing values, and states **"when instructions and design files disagree, the design files win."** That last line stops improvisation. This is a ~5-minute step — don't over-build it.

If the user is on a repo tool, be honest that Steps 5–6 are lightweight for them (vs. Lovable) and compress accordingly — still worth doing once to complete the loop.

---

## Step 6 — Task prompt template

Goal: a reusable build prompt. Usually already present as the last section of DESIGN.md — if so, point there rather than duplicating. The template says: build [screen] using tokens.json + DESIGN.md, follow the human-feel rules, self-check against the guardrails before finishing.

---

## Step 7 — Audit loop

Goal: keep output clean and grow the ruleset.

- Run the guardrail checklist against every generated screen — **including your own rendered cards** before you present them.
- Mark each item pass / minor-risk / fail.
- For every real "AI smell" caught, **append a written rule to DESIGN.md** so it never recurs. This is the loop that makes the system get better with use.
- Minor risks the user chooses to pass on still get logged as rules — capturing them is the point even if you don't re-render.
