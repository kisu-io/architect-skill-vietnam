# AGENTS.md

> Cross-agent instructions for this repo. Read by Claude Code, Hermes Agent, and other AGENTS.md-aware tools.

## This Project

- **Name:** Architect Skill Vietnam — Combined
- **Editions:**
  - [`claude-code/`](./claude-code) — Claude Code / Cowork
  - [`hermes/`](./hermes) — Hermes Agent (Nous Research)
- **Upstream:** [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects)

## Working in this repo

When editing a skill, keep the two editions in sync:

1. **Skill body changes (SKILL.md body, reference data):** update both `claude-code/` and `hermes/` copies.
2. **Frontmatter differences are expected:**
   - Claude Code uses `allowed-tools:` and `rules/` directory scanning.
   - Hermes uses `metadata.openclaw.*` (always, emoji, invocation, model, tier) and a flat `skills/` directory; rules ship as a single `kien-truc-vn-rules` skill with `metadata.openclaw.always: true`.
3. **New plugin / skill?** Add to both editions; in the Hermes edition, also list the new slug in `hermes/agents/architect-vn.md` `skills:` frontmatter.

## Output conventions

Always-on rules (loaded automatically in both editions):

- Metric units (SI), with imperial in parentheses only for international counterparts.
- QCVN / TCVN / Luật citations in the format defined by `trich-dan-quy-chuan` / `kien-truc-vn-rules`.
- Mandatory professional disclaimer verbatim from `tuyen-bo-mien-tru`.
- CSI MasterFormat 2018 + TCVN cross-references for technical specifications.
- Preferred Vietnamese AEC terminology — bilingual on first use.
- Tables, headings, and source attribution per `dinh-dang-dau-ra`.
- Show all calculations and cite sources (transparency rule).

## Language

- Skill bodies and outputs: **Vietnamese** (tiếng Việt).
- README / INSTALL / AGENTS.md: English for international accessibility.
- Reference glossary: bilingual Việt–English (234 terms across 12 AEC categories).
