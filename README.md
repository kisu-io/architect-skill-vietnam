# Architect Skill Vietnam

**Vietnamese Architecture & Planning Skill for Claude** — AI-powered research assistant for architects, real estate developers, and consultants operating in the Vietnamese market.

Localized from [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) (NYC/Uruguay) to Vietnam nationwide.

## What's Included

| Component | Count | Status | Description |
|---|---|---|---|
| **Rules** | 7 | Phase 1 ✅ | Output conventions applied to every response |
| **Reference files** | 3 | Phase 1 ✅ | QCVN/TCVN compendium, 234 bilingual terms, data sources |
| **Plugin 00 — Due Diligence** | 7 skills | Phase 2 ✅ | Permits, violations, land records, zoning status, heritage, fire safety, combined report |
| **Plugin 01 — Site Planning** | 4 skills | Phase 2 ✅ | Climate/environment, transit/mobility, demographics/market, neighborhood history |
| **Plugin 02 — Zoning** | 3 skills | Phase 2 ✅ | Zoning analysis, land law, 3D buildable envelope |
| **Agents** | 2 | Phase 2 ✅ | Zoning specialist, site planning specialist |
| **Plugins 03–08** | 0 skills | Phase 3–4 🔲 | Programming, specs, sustainability, materials, presentations, dispatcher |
| **Test suites** | 2 | ✅ | Phase 1 (47/49 = 97.9%) and Phase 2 (55/55 = 100%) |

**Total: 14 skills + 2 agents + 7 rules + 3 references = 26 files**

## Directory Structure

```
architect-skill-vietnam/
├── README.md                          ← You are here
├── INSTALL.md                         ← Step-by-step installation guide
├── LICENSE                            ← MIT License
├── ke-hoach-ban-dia-hoa-vietnam.md    ← Master localization plan
├── kiem-tra-phase-1.md                ← Phase 1 test results (97.9%)
├── kiem-tra-phase-2.md                ← Phase 2 test results (100%)
│
├── rules/                             ← Output rules (applied to all skills)
│   ├── don-vi-do-luong.md             Metric units, VND, Vietnamese area types
│   ├── trich-dan-quy-chuan.md         QCVN/TCVN/Law citation format
│   ├── tuyen-bo-mien-tru.md           Professional disclaimer (verbatim)
│   ├── dinh-dang-csi.md               CSI MasterFormat 2018 + TCVN cross-refs
│   ├── thuat-ngu.md                   Preferred Vietnamese AEC terminology
│   ├── dinh-dang-dau-ra.md            Tables, headings, source attribution
│   └── minh-bach.md                   Transparency — show calculations, cite sources
│
├── reference/                         ← Lookup tables and data guides
│   ├── qcvn-tong-hop.md              QCVN/TCVN compendium with quick-lookup tables
│   ├── thuat-ngu-song-ngu.md         234 bilingual terms across 12 categories
│   └── nguon-du-lieu.md              Vietnamese data sources + workarounds
│
├── plugins/
│   ├── 00-tham-dinh/skills/           ← Due Diligence (7 skills)
│   │   ├── tra-cuu-giay-phep-xd/     Building permit lookup
│   │   ├── tra-cuu-vi-pham-xd/       Construction violation search
│   │   ├── tra-cuu-dat-dai/          Land record lookup
│   │   ├── tra-cuu-quy-hoach/        Zoning status check
│   │   ├── tra-cuu-di-tich/          Heritage/landmark check
│   │   ├── tra-cuu-pccc/             Fire safety analysis
│   │   └── bao-cao-tong-hop/         Combined due diligence report
│   │
│   ├── 01-quy-hoach-mat-bang/skills/  ← Site Planning (4 skills)
│   │   ├── phan-tich-moi-truong/     Climate & environment analysis
│   │   ├── phan-tich-giao-thong/     Transit & mobility analysis
│   │   ├── phan-tich-dan-so/         Demographics & market analysis
│   │   └── phan-tich-lich-su/        Neighborhood history & context
│   │
│   ├── 02-phan-khu/skills/           ← Zoning Analysis (3 skills)
│   │   ├── phan-tich-quy-hoach-vn/   Zoning parameter analysis
│   │   ├── phan-tich-dat-dai/        Land law analysis
│   │   └── mo-hinh-khoi-tich-3d/     3D buildable envelope (Three.js)
│   │
│   ├── 03-chuong-trinh/skills/       ← Programming (Phase 3 — planned)
│   ├── 04-dac-ta/skills/             ← Specifications (Phase 3 — planned)
│   ├── 05-ben-vung/skills/           ← Sustainability (Phase 3 — planned)
│   ├── 06-vat-lieu/skills/           ← Materials Research (Phase 3 — planned)
│   ├── 07-trinh-bay/skills/          ← Presentations (Phase 4 — planned)
│   └── 08-dieu-phoi/skills/          ← Dispatcher (Phase 4 — planned)
│
└── agents/                            ← Specialist agents
    ├── chuyen-gia-phan-khu-vn.md     Zoning specialist
    └── chuyen-gia-quy-hoach.md       Site planning specialist
```

## Prerequisites

- **Claude Desktop App** with Cowork mode enabled, **or** Claude Code CLI
- **Web search access** — most skills use `WebSearch` / `WebFetch` to look up Vietnamese government portals, QCVN text, and market data
- **No external MCP connectors required** — all skills work with built-in tools

### Optional (enhances results)

- Upload a **bản đồ quy hoạch 1/500** (zoning map) — skills will extract parameters from it
- Upload a **sổ đỏ / GCNQSDĐ** (land certificate) — for land law analysis

## Installation

See **[INSTALL.md](INSTALL.md)** for detailed step-by-step instructions. Quick start:

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/architect-skill-vietnam.git

# Copy to your Claude skills directory
cp -r architect-skill-vietnam ~/.claude/skills/architect-skill-vietnam
```

Then in Claude Desktop or Claude Code, the skills will be available as slash commands (e.g., `/phan-tich-quy-hoach-vn`).

## Usage Examples

### 1. Zoning Analysis
```
/phan-tich-quy-hoach-vn 88 Nguyễn Huệ, Quận 1, TP.HCM
```
→ Returns MDXD, HSSDĐ, tầng cao, khoảng lùi with QCVN 01:2021 cross-check

### 2. Full Due Diligence Report
```
/bao-cao-tong-hop Lô A5, KĐT Ecopark, Hưng Yên — dự án chung cư 25 tầng
```
→ Runs all 6 sub-skills, produces traffic-light executive summary with cross-analysis

### 3. Climate & Environmental Analysis
```
/phan-tich-moi-truong Đà Nẵng, Quận Sơn Trà — resort 5 sao ven biển
```
→ Climate zone, wind, rain, flooding, seismic, with design recommendations

### 4. Fire Safety Check
```
/tra-cuu-pccc tòa nhà hỗn hợp 20 tầng, Quận 7, TP.HCM
```
→ Fire resistance rating, egress analysis, mandatory systems with TCVN + CSI codes

### 5. 3D Buildable Envelope
```
/mo-hinh-khoi-tich-3d lô 500m², MDXD 60%, 12 tầng, khoảng lùi 6m
```
→ Interactive Three.js visualization showing lot, envelope, setbacks

## Regulatory Framework

All skills are built on Vietnam's construction code stack:

| Type | Key Codes | Scope |
|---|---|---|
| **QCVN** (mandatory) | 01, 02, 03, 04, 05, 06, 09 /BXD | Planning, classification, fire safety, energy |
| **TCVN** (voluntary) | 2737, 5574, 9386, 5738, 7336 | Loads, concrete, seismic, fire systems |
| **Laws** | Luật XD 50/2014, Luật ĐĐ 31/2024, Luật QH 21/2017, Luật PCCC 40/2024 | Legal framework |
| **Green** | LOTUS (VGBC), EDGE (IFC) | Sustainability certification |

## Testing

Two test suites are included:

- **`kiem-tra-phase-1.md`** — 3 test prompts validating rules layer: MDXD calculation, setback comparison, fire safety for 10-floor mixed-use. Score: **47/49 (97.9%)**
- **`kiem-tra-phase-2.md`** — 3 test prompts validating skills: Tuần Châu villa zoning, Thảo Điền due diligence, Phú Quốc resort environment. Score: **55/55 (100%)**

To re-run tests: paste each test prompt into Claude with the skills loaded and compare the response against the scorecard criteria.

## Roadmap

| Phase | Content | Status |
|---|---|---|
| Phase 1 | Rules foundation (7 rules + 3 references) | ✅ Complete |
| Phase 2 | High-priority plugins (zoning, due diligence, site planning) + 2 agents | ✅ Complete |
| Phase 3 | Remaining plugins (programming, specifications, sustainability, materials) | 🔲 Planned |
| Phase 4 | Presentation, dispatcher, hooks, integration testing, documentation | 🔲 Planned |

## Language

All skill outputs are in **Vietnamese** (tiếng Việt). Technical terms include English equivalents in parentheses on first use. The bilingual glossary (`reference/thuat-ngu-song-ngu.md`) contains 234 terms across 12 AEC categories.

README and INSTALL are in English for international accessibility.

## Based On

Localized from [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) — a Claude Code skill suite for architecture professionals, originally focused on NYC and Uruguay.

## License

MIT License — see [LICENSE](LICENSE).

## Contributing

This project is in active development (Phase 3–4 planned). Contributions welcome for:
- Additional QCVN/TCVN references
- Provincial-specific zoning data
- MCP connectors for Vietnamese government portals
- Test cases for edge scenarios
