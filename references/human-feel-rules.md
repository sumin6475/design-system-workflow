# Human-Feel Rules & AI-Cliché Guardrails

The reusable core of every design system this workflow produces. These are project-independent — bake them into every `DESIGN.md`. They are what actually kill the "AI smell".

---

## Human-feel rules (write these into DESIGN.md §4)

### 1. Headlines are real sentences, not slogans
Write the way a thoughtful person actually talks. Specific beats punchy.
- Bad: "Meet the voice that thinks like you"
- Good: "Turns out someone already speaks English the way you think."

### 2. No em dashes (—)
The single biggest AI writing tell. Use commas, periods, or "then".
- Bad: "We studied how you think — then found your matches."
- Good: "We studied how you think, then found your matches."

### 3. Keep body text short
One tight sentence beats two padded ones. Cut every word not earning its place. Long, hedged, over-explained copy reads as machine-generated.

### 4. Concrete, real-looking data everywhere
Never ship `[Creator name]` / `92% match` placeholders in mockups. Use real names and real example sentences. Placeholder data makes a design look dead and untested.

### 5. Generous spacing
Section gaps ≥ 48px. Don't crowd. Whitespace is what makes a layout feel intentional rather than templated. AI defaults are almost always too tight.

### 6. Strong hierarchy
Big confident headline vs. distinctly smaller support text. Weak contrast between levels is an AI tell; so is repeating the same size everywhere.

---

## AI-cliché guardrails (write these into DESIGN.md §7 as an audit list)

Sourced from design-conference material on common AI design conventions. Audit every screen against these:

- [ ] **Tiny / faint eyebrow labels** — keep eyebrows ≥12px, weight 500+, opacity ≥ ~0.85. A label you squint at reads as AI decoration.
- [ ] **Light-weight, all-caps fonts** — never. All-caps only on small labels at weight 500+.
- [ ] **Light grey as body text** — set a floor grey (e.g. #71717A) for meta/roles only; body/headlines stay dark. Anything a user must read must pass contrast.
- [ ] **Inconsistent vertical rhythm / baseline** — stick to one spacing scale (e.g. 4/8/12/16/24/32/48).
- [ ] **Purple gradients + generic hero layouts** — avoid the default purple-blue gradient cliché; pair a committed accent with real-sentence headlines.
- [ ] **Em dashes in copy** — never (see human-feel rule 2).
- [ ] **Placeholder data in mockups** — never (see human-feel rule 4).

---

## The loop

Every new AI-smell the user catches during audits → add one line to the guardrail list in their DESIGN.md → it never comes back. The list is meant to grow per project. This is the mechanism that lets the system improve with use, the same way an in-house designer accumulates judgment — just written down instead of tacit.
