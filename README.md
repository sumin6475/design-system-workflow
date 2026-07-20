# Design System Workflow

A Claude skill that turns a vague app idea into a real, consistent, human-feeling design system, one that an AI builder will actually follow.

AI builders (Lovable, v0, Claude Code, Codex, Cursor) make hundreds of tiny visual decisions with no constraints, so their output looks inconsistent and "AI-smelling." This skill makes the constraints explicit on day one. It guides you through a discovery conversation, then produces the two things most people skip: design tokens *and* a rules doc that tells the AI when to use what.

**Version 0.1.0 · License MIT · Built by Sumin**

## Who it's for

Solo and indie builders who have an app concept or a PRD but no visual direction yet. You bring the product. This skill draws the taste out of you and writes it down.

## The core idea: you guide, they judge

Taste cannot be generated for you. It has to be pulled out through reactions. So the skill never dumps a finished brand on you. It shows real reference products and rendered cards, and your yes / no / why converges the direction. Your reactions are the research.

## How it works

A short Phase 0 intake reads the emotional core of your app, then a 7-step workflow:

1. **Research** — react to 6 to 8 real, named reference products
2. **Mood board** — pick from 2 to 3 directions rendered as real cards
3. **Design language** — the human-readable spec (type, color, spacing, tone)
4. **Tokens + rules** — `tokens.json` plus `DESIGN.md`, the key step
5. **Delivery** — how your specific AI builder receives the system
6. **Task prompt** — a reusable "build this screen" prompt
7. **Audit loop** — every new "AI smell" you catch becomes a written rule

## What it produces

```
design-system/
├── DESIGN.md            # the rules the AI reads every session
├── tokens.json          # source of truth for all values
├── tailwind.config.js   # framework output derived from tokens.json
└── CLAUDE.md            # (repo tools) pointer block, or AGENTS.md for Codex
```

## Install and use

This is a [Claude Agent Skill](https://docs.claude.com). To use it:

1. Clone this repo, or download `design-system-workflow.skill` and unzip it.
2. Place the `design-system-workflow/` folder where your Claude reads skills (Claude Code, or a Cowork skills folder), or paste `SKILL.md` into your session.
3. Say something like "design the look and feel of my app" and share your PRD or a few sentences about what it does.

Claude runs the workflow with you and hands back the token and rules files.

## What's inside this repo

| File | What it is |
|------|-----------|
| `SKILL.md` | The skill definition (the file Claude reads) |
| `references/discovery-guide.md` | How to run the Phase 0 discovery conversation |
| `references/step-playbook.md` | Full facilitation detail for the 7 steps |
| `references/human-feel-rules.md` | The anti-AI-smell rules, with examples |
| `design-system-workflow.skill` | Installable archive |

## The highest-value output: human-feel rules

These recur across every project and are baked into every `DESIGN.md`:

- Headlines are real sentences, not slogans.
- No em dashes in copy. It is the number one AI writing tell.
- Concrete real-looking data, never placeholders.
- Generous spacing. Section gaps of 48px or more.
- Strong hierarchy. A big confident headline against distinctly smaller support text.

## License

MIT. See [LICENSE](LICENSE). Use it, fork it, adapt it.
