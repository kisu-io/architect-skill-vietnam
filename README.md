# Architect Skill Vietnam — Combined

**Vietnamese Architecture & Planning Skill** — AI-powered research assistant for architects, real estate developers, and consultants working in the Vietnamese market.

This repository bundles **two editions** of the same skill suite, side-by-side. Pick the edition that matches your runtime.

| Edition | Runtime | Layout | Quick start |
|---|---|---|---|
| [`claude-code/`](./claude-code) | Claude Code / Cowork (Anthropic) | Plugin folders + per-skill `allowed-tools` | `cp -r claude-code/* ~/.claude/skills/architect-skill-vietnam/` |
| [`hermes/`](./hermes) | Hermes Agent (Nous Research) | Flat skills + single `@architect-vn` sub-agent | `cp -r hermes/skills/* ~/.hermes/skills/ && cp hermes/agents/architect-vn.md ~/.hermes/agents/` |

Both editions ship the **same 17 skills** + **2 personas** + **always-on output rules** (metric units, QCVN/TCVN citation format, professional disclaimer, CSI format, AEC terminology, output tables, transparency). The Claude Code edition adds 4 Phase-3 sustainability skills (EDGE / LOTUS / EPD / energy compliance) and 3 Phase-4 plugin scaffolds (materials, presentations, dispatcher).

## What it does

The skills cover the full early-stage workflow for a project in Vietnam:

- **Due Diligence (Thẩm định)** — building permits, construction violations, land records, zoning status, heritage check, fire safety, combined report
- **Site Planning (Quy hoạch mặt bằng)** — climate / environment, transit, demographics, neighborhood history
- **Zoning (Phân khu)** — zoning parameter analysis, land law, 3D buildable envelope (Three.js)
- **Programming, Specifications, Sustainability** (Claude Code edition only) — space program, occupant load / egress, technical spec (CSI + TCVN bilingual), EDGE / LOTUS / EPD / QCVN 09 energy

All outputs are in **Vietnamese**, with English equivalents on first use for technical terms.

## Pick an edition

### Claude Code / Cowork → [`claude-code/`](./claude-code)

Use this if you run Claude Desktop in Cowork mode, or Claude Code CLI.

See [`claude-code/README.md`](./claude-code/README.md) and [`claude-code/INSTALL.md`](./claude-code/INSTALL.md).

### Hermes Agent → [`hermes/`](./hermes)

Use this if you run [Hermes Agent](https://nousresearch.com) (Nous Research). The Hermes edition is a port from the OpenClaw spec, exposed as a single `@architect-vn` sub-agent under flat `~/.hermes/skills/`.

See [`hermes/README.md`](./hermes/README.md) and [`hermes/INSTALL.md`](./hermes/INSTALL.md).

## Regulatory Framework

Both editions are built on Vietnam's construction code stack:

| Type | Key Codes | Scope |
|---|---|---|
| **QCVN** (mandatory) | 01, 02, 03, 04, 05, 06, 09 /BXD | Planning, classification, fire safety, energy |
| **TCVN** (voluntary) | 2737, 5574, 9386, 5738, 7336, 4319, 4601 | Loads, concrete, seismic, fire systems, space standards |
| **Laws** | Luật XD 50/2014, Luật ĐĐ 31/2024, Luật QH 21/2017, Luật PCCC 40/2024 | Legal framework |
| **Green** | LOTUS (VGBC), EDGE (IFC), QCVN 09:2017/BXD | Sustainability certification + mandatory energy compliance |

## Repo layout

```
architect-skill-vietnam/
├── README.md            ← You are here
├── LICENSE              ← MIT
├── AGENTS.md            ← Project metadata for AGENTS.md-aware tools
├── .gitignore
├── claude-code/         ← Edition 1: Claude Code / Cowork
│   ├── README.md
│   ├── INSTALL.md
│   ├── AGENTS.md
│   ├── LICENSE
│   ├── agents/          (2 persona agents)
│   ├── plugins/         (00–08, full 9-plugin layout)
│   ├── reference/       (4 lookup tables)
│   ├── rules/           (7 always-on rules)
│   └── hooks/
└── hermes/              ← Edition 2: Hermes Agent (ported from OpenClaw)
    ├── README.md
    ├── INSTALL.md
    ├── agents/
    │   └── architect-vn.md
    └── skills/          (17 skills, flat layout)
```

## Based On

- **Upstream:** [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) — original Claude Code skill suite for NYC / Uruguay.

## License

MIT — see [LICENSE](./LICENSE).

## Contributing

This is a private working repository. If you'd like to contribute, contact the maintainer.
