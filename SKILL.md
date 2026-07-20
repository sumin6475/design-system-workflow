---
name: design-system-workflow
description: Walk a solo builder through creating a consistent, non-AI-looking design system for an app they're about to build with an AI builder (Lovable, v0, Claude Code, Codex, Cursor). Use this whenever the user wants to design the look and feel of an app, asks "how do I make AI-generated design consistent", wants to define a brand/vibe/color/style from scratch, has a PRD or app concept but no visual direction yet, mentions design tokens, DESIGN.md, a design system for an AI builder, or references "the design-system-workflow", "the 7-step design workflow", or a previous system made this way. Also trigger when the user has an app idea and says they don't know the brand, color, vibe, or feeling yet — this skill discovers it with them. The user supplies the product (PRD or concept); this skill runs the discovery and produces real token + rules files. It never invents the product itself.
---

# Design System Workflow

Turn a vague app concept into a real, consistent, human-feeling design system — one that an AI builder will actually follow. The output is a set of files (tokens + rules) plus a validated look-and-feel, produced by guiding the user through a 7-step workflow.

## Why this skill exists

AI builders produce inconsistent, samey, "AI-smelling" design because the AI makes hundreds of tiny visual decisions with zero constraints. Industry designers absorb those constraints implicitly over ~3 years on the job. This workflow makes the constraints **explicit** so the AI (and the solo builder) get them on day one. The magic is in two places most people skip: (1) a **discovery conversation** that pulls the user's taste out through reactions, and (2) a **rules doc** (not just tokens) that tells the AI *when to use what*.

## The core principle: you guide, they judge

Taste can't be generated for the user — it has to be drawn out of them. So the running style is: **Claude narrows and shows; the user reacts.** Never dump a finished brand on them. Show concrete things (real reference products, rendered cards) and let their yes/no/why converge the direction. Their reactions ARE the research.

Keep each step a real checkpoint: propose → user reacts → lock → move on. One decision at a time. Use tappable option questions for calibration choices rather than open prose questions where possible — it's faster for the user and keeps momentum.

---

## Phase 0 — Intake (do this BEFORE Step 1)

This is the part that makes the whole flow work. Don't skip it.

1. **Get the raw material.** Ask for the PRD (file or paste) or, if none exists, a few sentences on what the app does. Also ask one line on the **user's emotional state when they arrive** (stressed? bored? curious? in a hurry?).

2. **Read the emotional core out loud.** Before any visuals, tell the user what the app *is* emotionally — not what it does. Find the real feeling at the payoff moment. Example from a shadowing-match app: "This isn't a language tool, it's a *find-your-person* tool; the payoff feeling is recognition — 'someone thinks like me.'" This reframing orients every later choice and shows the user you understand the product beneath the features.

3. **Name the central design tension.** Almost every app has one (e.g. "serious ML tech" vs. "intimate human feeling"). State it. It's the thing the design has to resolve.

4. **Lock the emotional target with 1–2 calibration questions.** Ask what the payoff moment should FEEL like, and who the app should feel like it was made by. These two answers eliminate whole design territories immediately (see `references/discovery-guide.md`).

5. **Set expectations for how you'll run it.** Briefly: "Steps 1–2 are your taste (I show, you react); Step 3 onward I structure and you approve." If the user hasn't got a vibe yet, tell them Step 1 will do extra work and to react fast without overthinking.

---

## The 7 Steps

Full facilitation detail — what to say, what to show, how to converge — is in `references/step-playbook.md`. Read it before running the steps. High-level:

**Step 1 — Research.** Put 6–8 *real, named* reference products in front of the user, each chosen for a specific reason tied to their app, spanning the emotional territory so reactions triangulate taste. Give links so they can actually feel the sites. Ask: which 3 survive, which one do you recoil from, any "yes but". Kills and keeps both matter.

**Step 2 — Mood board / directions.** Narrow to 2–3 concrete visual directions that share the locked DNA but differ on one axis (usually how bold the accent is). **Render them as real cards** (HTML artifact showing the SAME screen in each direction) so the user reacts to real type/color/shadow, not adjectives. User picks one; "yes but" welcome.

**Step 3 — Design language (human-readable).** Draft the actual spec from the pick: typography, color (with what each color is *for*), spacing, radius, shadow, component list, tone of voice. User approves or adjusts. Lock the accent color's exact role here.

**Step 4 — Tokens + rules (machine-readable).** THE key step. Produce two things:
- **Values** → `tokens.json` (source of truth) + framework config (e.g. `tailwind.config.js`).
- **Rules** → `DESIGN.md`: when to use each token, do's/don'ts, the human-feel rules, the AI-cliché guardrails. Tokens alone leave the AI guessing which of 5 blues to use where; the rules doc removes the ambiguity. This is why most people's systems still look inconsistent.

**Step 5 — Delivery.** Choose how the AI receives the system, based on the user's builder:
- *Lovable / v0 / prompt-based* → paste tokens + reference the system each prompt, or publish an npm package for reuse.
- *Claude Code / Codex / Cursor (repo-based)* → put the files in the repo, and add a pointer block to `CLAUDE.md` (or `AGENTS.md` for Codex) that says "always follow DESIGN.md; design files win over conflicting instructions." This is a 5-minute step for repo tools — don't over-engineer it.

**Step 6 — Task prompt template.** A reusable "build [screen] using tokens.json + DESIGN.md, follow the human-feel rules, self-check against the guardrails" prompt. Often already embedded as a section in DESIGN.md — if so, point there instead of duplicating.

**Step 7 — Audit loop.** Check every generated screen against the AI-cliché guardrails. Every new "AI smell" the user catches becomes a written rule appended to DESIGN.md — so it never comes back. Run this audit on your OWN rendered cards too, before moving on.

---

## The human-feel rules (the anti-AI-smell core)

These recur across every project and are the highest-value output. Bake them into every DESIGN.md. Full list with examples in `references/human-feel-rules.md`. The essentials:

- **Headlines are real sentences, not slogans.** "Turns out someone already speaks English the way you think." beats "Meet the voice that thinks like you."
- **No em dashes (—) in copy.** The #1 AI writing tell. Use commas, periods, or "then".
- **Concrete real-looking data, never placeholders.** Real names and real example text in every mockup. `[Creator name] / 92% match` makes a design look dead.
- **Generous spacing.** Section gaps ≥ 48px. Crowding reads as templated.
- **Strong hierarchy.** Big confident headline vs. distinctly smaller support text.

## The AI-cliché guardrails (audit list)

From real design-conference material on "common AI design conventions":
- Tiny, faint eyebrow/subtitle labels (keep ≥12px, weight 500+, not too transparent)
- Light-weight, all-caps fonts
- Light grey used as body text (contrast failure)
- Inconsistent vertical rhythm / baseline
- Purple gradients + generic hero layouts

---

## Rendering cards & mockups

When showing directions or fonts, build a real HTML artifact — it's the honest way to let the user react. Guidance:
- Show the **same screen** across all options so it's an apples-to-apples comparison.
- Use the app's **real content** in the mockup, not lorem ipsum.
- For font comparisons, render the actual headline in each candidate font on the real background.
- Load real fonts from their CDN (Google Fonts, Fontshare). Note in the spec where each font comes from, since a failed font load silently falls back and can mislead the user about what they picked — if a user says "that looks different from what I chose," a fallback font load is the likely cause.
- If a visualizer/mockup tool is unavailable or times out, fall back to a hand-written HTML artifact via file tools.

## Output file set (typical)

```
design-system/
├── DESIGN.md            # the rules — the file the AI reads every session
├── tokens.json          # source of truth for all values
├── tailwind.config.js   # framework output derived from tokens.json
└── CLAUDE.md            # (repo tools) pointer block; or AGENTS.md for Codex
```
Plus a validated look-and-feel artifact (the final rendered card/screen).

## Don't

- Don't invent the product, its features, or its content. The user owns that.
- Don't generate a brand and present it as finished. Draw it out through reactions.
- Don't stop at tokens. The rules doc is the point.
- Don't give investment/financial-style false precision on subjective matches; keep design language honest.
- Don't skip Phase 0. The emotional-core read is what makes the rest land.
