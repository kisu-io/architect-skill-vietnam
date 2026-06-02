# AGENTS.md — claude-code edition

> Cross-agent instructions for the Claude Code / Cowork edition of this skill.

See the [top-level AGENTS.md](../AGENTS.md) for project-wide conventions.

## This edition

- **Runtime:** Claude Code / Cowork
- **Layout:** plugin folders under `plugins/`, plus `agents/`, `reference/`, `rules/`, `hooks/`
- **Install target:** `~/.claude/skills/architect-skill-vietnam/`

## Rules

All `rules/*.md` files are loaded implicitly by Claude Code from the rules directory. They define mandatory output conventions (units, citations, disclaimer, CSI format, terminology, output tables, transparency) and are applied to every skill response.

## Skills

Each plugin under `plugins/NN-name/skills/<skill>/SKILL.md` is invoked by slug:

```
/phan-tich-quy-hoach-vn 88 Nguyễn Huệ, Quận 1, TP.HCM
```

Per-skill `allowed-tools:` declared in frontmatter gate WebSearch / WebFetch / Read / Write / Edit / Bash use.

## Agents

`agents/chuyen-gia-*.md` are specialist personas (zoning + site planning). They orchestrate the relevant skills end-to-end when invoked.
