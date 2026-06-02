# Architect Skill Vietnam — Hermes Agent Edition

**Vietnamese Architecture & Planning Skill for Hermes Agent (Nous Research)** — AI-powered research assistant for architects, real estate developers, and consultants operating in the Vietnamese market.

Ported from the Claude Code / Cowork version ([`../claude-code`](../claude-code)) to the Hermes Agent skill format, **unified under a single sub-agent `@architect-vn`** that fronts all 17 skills.

> **Hermes Agent** is the open agent framework from [Nous Research](https://nousresearch.com). This edition uses Hermes's flat skill layout under `~/.hermes/skills/` and a single sub-agent under `~/.hermes/agents/`.

## Quick Start — Call the Agent

```
@architect-vn lô 500m² ở phường 2 quận 3, TP.HCM, xây được bao nhiêu tầng?
```

The `@architect-vn` sub-agent mounts every skill in this bundle and routes each question to the right one. You don't need to know skill names — just ask in Vietnamese.

## What's Included

| Component | Count | Location | Description |
|---|---|---|---|
| **Sub-agent** | 1 | `agents/architect-vn.md` | Single `@architect-vn` entry point; mounts all 17 skills |
| **Always-on rules skill** | 1 | `skills/kien-truc-vn-rules/` | 7 output conventions loaded every session via `metadata.openclaw.always: true` |
| **Reference library** | 4 files | `skills/kien-truc-vn-rules/reference/` | QCVN/TCVN compendium, 234 bilingual terms, data sources, HCM zoning codes |
| **Persona skills** | 2 | `skills/chuyen-gia-*/` | Zoning specialist + site planning specialist |
| **Due Diligence skills** | 7 | `skills/tra-cuu-*`, `skills/bao-cao-tong-hop/` | Permits, violations, land records, zoning status, heritage, fire safety, combined report |
| **Site Planning skills** | 4 | `skills/phan-tich-{moi-truong,giao-thong,dan-so,lich-su}/` | Climate, transit, demographics, neighborhood history |
| **Zoning skills** | 3 | `skills/phan-tich-{quy-hoach-vn,dat-dai}/`, `skills/mo-hinh-khoi-tich-3d/` | Zoning analysis, land law, 3D buildable envelope |

**Total: 1 sub-agent + 17 skills (1 rules + 2 personas + 14 module skills).**

## Key Differences vs. Claude Code Edition

| Claude Code / Cowork | Hermes Agent |
|---|---|
| `allowed-tools:` in frontmatter | Removed. Hermes does not gate tools per-skill. Capabilities described in body and declared via `metadata.openclaw.requires`. |
| `rules/` directory scanned implicitly | One `kien-truc-vn-rules` skill with `metadata.openclaw.always: true`. Loads automatically with every session. |
| `agents/*.md` per persona | Persona files converted to standalone skills with `user-invocable: true`. The single Hermes sub-agent (`agents/architect-vn.md`) mounts the persona skills. |
| `WebSearch` / `WebFetch` tool names | Abstract references: "the web search tool" / "the web fetch tool". Portable across Hermes hosts. |
| Cowork workspace folder conventions | `{baseDir}` placeholder in skill bodies when referencing sibling files. |
| Plugin subdirectories with `openclaw.plugin.json` | **Flat layout** — every skill lives directly under `skills/` and Hermes auto-discovers them via `~/.hermes/skills/.bundled_manifest`. |
| Install to `~/.claude/skills/` | Install to `~/.hermes/skills/` (user-scoped) or `<workspace>/skills/` (project-scoped). |

> **Why `metadata.openclaw.*` and not `metadata.hermes.*`?** Hermes Agent currently consumes the OpenClaw skill spec verbatim — `always`, `emoji`, `invocation`, `model`, `tier`, etc. are all read from `metadata.openclaw`. If/when Hermes diverges, this edition will mirror the change.

## Directory Structure

```
hermes/
├── README.md                          ← You are here
├── INSTALL.md                         ← Hermes install steps
│
├── agents/
│   └── architect-vn.md                ← @architect-vn sub-agent — mounts all 17 skills
│
└── skills/                            ← Flat layout — Hermes auto-discovers each subdir
    ├── kien-truc-vn-rules/            Always-on rules (7 consolidated)
    │   ├── SKILL.md
    │   └── reference/                 Bundled lookup tables
    │       ├── qcvn-tong-hop.md
    │       ├── thuat-ngu-song-ngu.md
    │       ├── nguon-du-lieu.md
    │       └── ma-quy-hoach-hcm.md
    ├── chuyen-gia-phan-khu-vn/        Zoning specialist persona
    ├── chuyen-gia-quy-hoach/          Site planning specialist persona
    ├── bao-cao-tong-hop/              Combined due diligence report
    ├── tra-cuu-giay-phep-xd/          Building permit lookup
    ├── tra-cuu-vi-pham-xd/            Construction violation search
    ├── tra-cuu-dat-dai/               Land record lookup
    ├── tra-cuu-quy-hoach/             Zoning status check
    ├── tra-cuu-di-tich/               Heritage / landmark check
    ├── tra-cuu-pccc/                  Fire safety analysis
    ├── phan-tich-moi-truong/          Climate & environment
    ├── phan-tich-giao-thong/          Transit & mobility
    ├── phan-tich-dan-so/              Demographics & market
    ├── phan-tich-lich-su/             Neighborhood history
    ├── phan-tich-quy-hoach-vn/        Zoning parameter analysis
    ├── phan-tich-dat-dai/             Land law analysis
    └── mo-hinh-khoi-tich-3d/          3D buildable envelope (Three.js)
```

## Prerequisites

- **Hermes Agent** installed on your host. See [Nous Research / Hermes Agent](https://nousresearch.com).
- **A web-fetching capability** exposed to Hermes. The skills reference "the web search tool" and "the web fetch tool" abstractly — any configured web tool (built-in, community skill, or shell-based via `curl`) will satisfy them.

### Optional (enhances results)

- Upload a **bản đồ quy hoạch 1/500** (zoning map) — skills will extract parameters from it.
- Upload a **sổ đỏ / GCNQSDĐ** (land certificate) — for land law analysis.

## Installation

See **[INSTALL.md](INSTALL.md)** for detailed steps. Quick path:

```bash
# From the repo root
mkdir -p ~/.hermes/agents ~/.hermes/skills
cp hermes/agents/architect-vn.md ~/.hermes/agents/
cp -r hermes/skills/* ~/.hermes/skills/
```

Then call the agent:

```
@architect-vn Phân tích quy hoạch cho 88 Nguyễn Huệ, Quận 1, TP.HCM
```

The agent will auto-route to `phan-tich-quy-hoach-vn`.

## Usage Examples

All examples use the single `@architect-vn` entry point. The agent routes each question to the right skill internally.

### Zoning analysis
> `@architect-vn Phân tích quy hoạch cho 88 Nguyễn Huệ, Quận 1, TP.HCM`

### Full due diligence report
> `@architect-vn Làm báo cáo tổng hợp thẩm định cho Lô A5, KĐT Ecopark, Hưng Yên — dự án chung cư 25 tầng`

### Fire safety check
> `@architect-vn Tra cứu yêu cầu PCCC cho tòa nhà hỗn hợp 20 tầng, Quận 7, TP.HCM`

### 3D buildable envelope
> `@architect-vn Tạo mô hình khối tích 3D cho lô 500m², MDXD 60%, 12 tầng, khoảng lùi 6m`

### Full site feasibility (orchestrated)
> `@architect-vn Đánh giá toàn diện vị trí dự án shophouse 2.000m² tại đường Phạm Văn Đồng, Thủ Đức` — agent invokes the `chuyen-gia-quy-hoach` persona which runs 4–5 analysis modules in parallel.

## Regulatory Framework

All skills are built on Vietnam's construction code stack:

| Type | Key Codes | Scope |
|---|---|---|
| **QCVN** (mandatory) | 01, 02, 03, 04, 05, 06, 09 /BXD | Planning, classification, fire safety, energy |
| **TCVN** (voluntary) | 2737, 5574, 9386, 5738, 7336 | Loads, concrete, seismic, fire systems |
| **Laws** | Luật XD 50/2014, Luật ĐĐ 31/2024, Luật QH 21/2017, Luật PCCC 40/2024 | Legal framework |
| **Green** | LOTUS (VGBC), EDGE (IFC) | Sustainability certification |

## Language

All skill outputs are in **Vietnamese** (tiếng Việt). Technical terms include English equivalents in parentheses on first use. README and INSTALL are in English for accessibility.

## Based On

- **Companion edition:** [`../claude-code`](../claude-code) — same content in Claude Code / Cowork format
- **Upstream:** [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) (NYC / Uruguay)

## License

MIT License — see [`../LICENSE`](../LICENSE).
