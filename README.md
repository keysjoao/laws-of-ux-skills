# Laws of UX — Claude Code Skills

Three Claude Code skills that bring the **30 Laws of UX** ([lawsofux.com](https://lawsofux.com)) into your frontend workflow as actionable, code-level guidance.

Built and used in production at [Core Educação](https://corestudio.ai) — battle-tested across audits of multi-tenant SaaS admin apps with real "leigo" (non-technical) users.

## What's inside

| Skill | When to invoke | What it does |
|-------|---------------|--------------|
| [`laws-of-ux`](./laws-of-ux/) | Before/while building a component | Analyzes what you're building → recommends which of the 30 laws apply + specific code fixes. Works proactively alongside `frontend-design`. |
| [`laws-of-ux-review`](./laws-of-ux-review/) | After a feature is built | Full audit of existing UI → scores 0-60, classifies findings as Critical/Warning/Suggestion, gives prioritized code-level action plan. |
| [`laws-of-ux-checklist`](./laws-of-ux-checklist/) | Before merging / shipping | 12-point pass/fail pre-ship check covering Fitts, Doherty, Hick, Jakob, Cognitive Load, etc. Returns clear ship/don't-ship verdict. |

## Why these are useful

Most "UX audit" tools either:
- Stay vague ("improve discoverability") with no code attached
- Or score against a checklist with no Why

These skills do both — every finding includes:
- **Which Law of UX is being violated**
- **Where in the code** (file:line)
- **What to change** (concrete diff or rewrite)
- **Why it matters** (one sentence linking back to behavior)

Used to ship ~50 fixes across a B2B WhatsApp SaaS in one week, raising estimated UX score from C+ (38/60) to A (58/60). The skills caught issues like:
- 8 native `window.confirm()` blocking modals → unified `ConfirmModal` component
- Period picker that cycled instead of segmented → 1 click anywhere
- Audit log raw `event_type: "provider_fallback_used"` → "Provedor principal falhou — usamos backup"
- Onboarding state lost on F5 → localStorage persistence
- Kbd shortcuts hint shown to leigos who'd never use it → reveal after first power-keypress

## Installation

### Option A — Personal, single-user (your own Claude Code)

```bash
git clone https://github.com/keysjoao/laws-of-ux-skills.git
cp -r laws-of-ux-skills/laws-of-ux* ~/.claude/skills/
```

That's it. Restart Claude Code and the skills become available.

### Option B — Team / project-scoped

```bash
cd your-project
git submodule add https://github.com/keysjoao/laws-of-ux-skills.git .claude/skills/_laws-of-ux
# or just: cp -r the 3 dirs into .claude/skills/
```

Now anyone running Claude Code inside the project can invoke them.

## Usage

Once installed, in Claude Code:

```
/laws-of-ux                           # advisor mode — pick laws for what you're building
/laws-of-ux-review src/components/X   # full audit of a file/page
/laws-of-ux-checklist                 # quick pre-ship verdict
```

The skills auto-trigger when you mention things like "UX audit", "review UX", "check UX", "ready to ship?", "design review" — you usually don't need to remember the exact slash command.

## The 30 Laws (reference inside `laws-of-ux/references/ux-laws-complete.md`)

Aesthetic-Usability · Chunking · Cognitive Bias · Cognitive Load · Common Region · Doherty Threshold · Fitts's Law · Flow · Goal-Gradient · Hick's Law · Jakob's Law · Law of Common Region · Law of Pragnanz · Law of Proximity · Law of Similarity · Law of Uniform Connectedness · Mental Model · Miller's Law · Occam's Razor · Paradox of Choice · Pareto Principle · Parkinson's Law · Peak-End Rule · Postel's Law · Selective Attention · Serial Position Effect · Tesler's Law · Von Restorff Effect · Working Memory · Zeigarnik Effect

## Contributing

Found a case the skill missed? PR welcome. The skills themselves are markdown — no code to compile.

If you ship UX fixes that wouldn't have happened without these skills, mention them in an issue. Helps tune the triggers.

## License

MIT — see [LICENSE](./LICENSE). Use freely in commercial and personal projects.

## Credits

- 30 laws and their formulations: [Jon Yablonski](https://lawsofux.com)
- Skills format: [Anthropic Agent Skills standard](https://docs.claude.com/en/docs/claude-code/skills)
- Author: [@keysjoao](https://github.com/keysjoao)
