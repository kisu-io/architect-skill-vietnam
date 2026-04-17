# Architect Skill Vietnam

**Vietnamese Architecture & Planning Skill for Claude** — AI-powered research assistant for architects, real estate developers, and consultants operating in the Vietnamese market.

![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)
![Phase](https://img.shields.io/badge/Phase-3%20Complete-brightgreen)
![Skills](https://img.shields.io/badge/Skills-21-informational)
![Claude](https://img.shields.io/badge/Built%20for-Claude%20Code%20%2F%20Cowork-blueviolet)

Localized from [AlpacaLabsLLC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) (NYC/Uruguay) to Vietnam nationwide.

---

## Quick Start

```bash
# Clone the repo
git clone https://github.com/kisu-io/architect-skill-vietnam.git

# Copy to your Claude skills directory
cp -r architect-skill-vietnam ~/.claude/skills/architect-skill-vietnam
```

Then invoke any skill from Claude Desktop (Cowork) or Claude Code:

```
/phan-tich-quy-hoach-vn 88 Nguyễn Huệ, Quận 1, TP.HCM
```

See **[INSTALL.md](INSTALL.md)** for full setup instructions.

---

## What's Included

| Plugin | Skills | Status | Description |
|--------|--------|--------|-------------|
| **Rules** | 7 | ✅ Phase 1 | Output conventions applied to every response |
| **Reference files** | 4 | ✅ Phase 1–3 | QCVN/TCVN compendium, 234 bilingual terms, data sources, HCM zoning codes |
| **00 — Due Diligence** | 7 | ✅ Phase 2 | Permits, violations, land records, zoning, heritage, fire safety, combined report |
| **01 — Site Planning** | 4 | ✅ Phase 2 | Climate/environment, transit, demographics, neighborhood history |
| **02 — Zoning** | 3 | ✅ Phase 2 | Zoning analysis, land law, 3D buildable envelope |
| **03 — Programming** | 2 | ✅ Phase 3 | Space program, occupant load & egress check |
| **04 — Specifications** | 1 | ✅ Phase 3 | Technical spec drafting (CSI + TCVN, bilingual) |
| **05 — Sustainability** | 4 | ✅ Phase 3 | EDGE, LOTUS, EPD/LCA, energy compliance (QCVN 09) |
| **06 — Materials** | — | 🔲 Phase 4 | Material research, local suppliers |
| **07 — Presentations** | — | 🔲 Phase 4 | Slide decks, reports, visualizations |
| **08 — Dispatcher** | — | 🔲 Phase 4 | Smart routing agent for all skills |
| **Agents** | 2 | ✅ Phase 2 | Zoning specialist, site planning specialist |

**Total: 21 skills + 2 agents + 7 rules + 4 references = 34 files**

---

## Prerequisites

- **Claude Desktop App** with Cowork mode, **or** Claude Code CLI
- **Web search access** — skills use `WebSearch` / `WebFetch` for Vietnamese government portals, QCVN text, and market data
- **No external MCP connectors required** — all skills work with built-in tools

**Optional enhancements:**
- Upload a **bản đồ quy hoạch 1/500** — skills extract parameters directly from the image
- Upload a **sổ đỏ / GCNQSDĐ** — for land law and boundary analysis
- Upload **EPD PDFs** — for the `/phan-tich-epd` skill

---

## Usage Examples

### Due Diligence

```
/bao-cao-tong-hop Lô A5, KĐT Ecopark, Hưng Yên — dự án chung cư 25 tầng
```
→ Runs all 6 sub-skills, produces traffic-light executive summary with cross-analysis

```
/tra-cuu-pccc tòa nhà hỗn hợp 20 tầng, Quận 7, TP.HCM
```
→ Fire resistance rating, egress analysis, mandatory systems (TCVN + CSI codes)

### Zoning & Site Planning

```
/phan-tich-quy-hoach-vn 88 Nguyễn Huệ, Quận 1, TP.HCM
```
→ MDXD, HSSDĐ, tầng cao, khoảng lùi — cross-checked against QCVN 01:2021

```
/mo-hinh-khoi-tich-3d lô 500m², MDXD 60%, 12 tầng, khoảng lùi 6m
```
→ Interactive Three.js visualization showing lot, envelope, and setbacks

```
/phan-tich-moi-truong Đà Nẵng, Quận Sơn Trà — resort 5 sao ven biển
```
→ Climate zone, wind/rain/flooding/seismic analysis with design recommendations

### Programming & Specifications

```
/chuong-trinh-khong-gian văn phòng 200 nhân viên Hà Nội
```
→ Room-by-room space program with m² per person, loss factor, total GFA required

```
/kiem-tra-so-nguoi văn phòng 1.500 m² tầng 5
```
→ Occupant load, egress count, exit width, travel distance (QCVN 06:2021)

```
/dac-ta-ky-thuat chung cư cao cấp 30 tầng Quận 2 TP.HCM
```
→ CSI MasterFormat outline spec with TCVN/QCVN cross-references and local suppliers

### Sustainability

```
/danh-gia-lotus dự án văn phòng 15.000 m² Hà Nội — mục tiêu Gold
```
→ LOTUS scorecard by category, certification level forecast, pathway to Gold

```
/danh-gia-edge chung cư 200 căn hộ Bình Dương — vay vốn IFC
```
→ 20/20/20 energy/water/materials calculation, EDGE App checklist, registration steps

```
/tiet-kiem-nang-luong văn phòng 5.000 m² tường curtain wall Hà Nội
```
→ OTTV/RTTV calculation, WWR compliance, QCVN 09:2017 compliance report

```
/phan-tich-epd [upload EPD PDF] bê tông B30 Việt Nam
```
→ GWP (kgCO₂e), Primary Energy extraction, embodied carbon comparison vs. benchmark

---

## Directory Structure

```
architect-skill-vietnam/
├── README.md                          ← You are here
├── INSTALL.md                         ← Step-by-step installation guide
├── LICENSE                            ← MIT License
├── ke-hoach-ban-dia-hoa-vietnam.md    ← Master localization plan
├── ke-hoach-tich-hop-du-lieu-hcm.md   ← HCM data integration plan
├── kiem-tra-phase-1.md                ← Phase 1 test results (97.9%)
├── kiem-tra-phase-2.md                ← Phase 2 test results (100%)
│
├── rules/                             ← Output rules (applied to all responses)
│   ├── don-vi-do-luong.md             Metric units, VND, Vietnamese area types
│   ├── trich-dan-quy-chuan.md         QCVN/TCVN/Law citation format
│   ├── tuyen-bo-mien-tru.md           Professional disclaimer (verbatim)
│   ├── dinh-dang-csi.md               CSI MasterFormat 2018 + TCVN cross-refs
│   ├── thuat-ngu.md                   Preferred Vietnamese AEC terminology
│   ├── dinh-dang-dau-ra.md            Tables, headings, source attribution
│   └── minh-bach.md                   Transparency — show calculations, cite sources
│
├── reference/                         ← Lookup tables and data guides
│   ├── qcvn-tong-hop.md               QCVN/TCVN compendium with quick-lookup tables
│   ├── thuat-ngu-song-ngu.md          234 bilingual terms across 12 AEC categories
│   ├── nguon-du-lieu.md               Vietnamese data sources + access workarounds
│   └── ma-quy-hoach-hcm.md            HCM zoning map codes (gisxaydung.tphcm.gov.vn)
│
├── plugins/
│   ├── 00-tham-dinh/skills/           ← Due Diligence (7 skills) ✅
│   │   ├── tra-cuu-giay-phep-xd/      Building permit lookup
│   │   ├── tra-cuu-vi-pham-xd/        Construction violation search
│   │   ├── tra-cuu-dat-dai/           Land record lookup
│   │   ├── tra-cuu-quy-hoach/         Zoning status check
│   │   ├── tra-cuu-di-tich/           Heritage/landmark check
│   │   ├── tra-cuu-pccc/              Fire safety analysis
│   │   └── bao-cao-tong-hop/          Combined due diligence report
│   │
│   ├── 01-quy-hoach-mat-bang/skills/  ← Site Planning (4 skills) ✅
│   │   ├── phan-tich-moi-truong/      Climate & environment analysis
│   │   ├── phan-tich-giao-thong/      Transit & mobility analysis
│   │   ├── phan-tich-dan-so/          Demographics & market analysis
│   │   └── phan-tich-lich-su/         Neighborhood history & context
│   │
│   ├── 02-phan-khu/skills/            ← Zoning Analysis (3 skills) ✅
│   │   ├── phan-tich-quy-hoach-vn/    Zoning parameter analysis
│   │   ├── phan-tich-dat-dai/         Land law analysis
│   │   └── mo-hinh-khoi-tich-3d/      3D buildable envelope (Three.js)
│   │
│   ├── 03-chuong-trinh/skills/        ← Programming (2 skills) ✅
│   │   ├── chuong-trinh-khong-gian/   Space program (m² per type, GFA)
│   │   └── kiem-tra-so-nguoi/         Occupant load & egress (QCVN 06:2021)
│   │
│   ├── 04-dac-ta/skills/              ← Specifications (1 skill) ✅
│   │   └── dac-ta-ky-thuat/           Technical spec (CSI + TCVN, bilingual)
│   │
│   ├── 05-ben-vung/skills/            ← Sustainability (4 skills) ✅
│   │   ├── danh-gia-edge/             EDGE (IFC) certification assessment
│   │   ├── danh-gia-lotus/            LOTUS (VGBC) scorecard & pathway
│   │   ├── phan-tich-epd/             EPD / embodied carbon analysis
│   │   └── tiet-kiem-nang-luong/      Energy compliance (QCVN 09:2017/BXD)
│   │
│   ├── 06-vat-lieu/skills/            ← Materials Research (Phase 4 — planned)
│   ├── 07-trinh-bay/skills/           ← Presentations (Phase 4 — planned)
│   └── 08-dieu-phoi/skills/           ← Dispatcher agent (Phase 4 — planned)
│
└── agents/                            ← Specialist agents
    ├── chuyen-gia-phan-khu-vn.md      Zoning specialist
    └── chuyen-gia-quy-hoach.md        Site planning specialist
```

---

## Regulatory Framework

All skills are built on Vietnam's construction code stack:

| Type | Key Codes | Scope |
|------|-----------|-------|
| **QCVN** (mandatory) | 01, 02, 03, 04, 05, 06, 09 /BXD | Planning, classification, fire safety, energy efficiency |
| **TCVN** (voluntary) | 2737, 5574, 9386, 5738, 7336, 4319, 4601 | Loads, concrete, seismic, fire systems, space standards |
| **Laws** | Luật XD 50/2014, Luật ĐĐ 31/2024, Luật QH 21/2017, Luật PCCC 40/2024 | Legal framework |
| **Green** | LOTUS (VGBC), EDGE (IFC), QCVN 09:2017/BXD | Sustainability certification + mandatory energy compliance |

---

## Testing

| Test Suite | Scope | Score |
|------------|-------|-------|
| `kiem-tra-phase-1.md` | Rules layer: MDXD calculation, setback comparison, fire safety | **47/49 (97.9%)** |
| `kiem-tra-phase-2.md` | Skills: Tuần Châu villa, Thảo Điền due diligence, Phú Quốc resort | **55/55 (100%)** |

To re-run: paste each test prompt into Claude with the skills loaded and compare against the scorecard criteria.

---

## Roadmap

| Phase | Content | Status |
|-------|---------|--------|
| Phase 1 | Rules foundation (7 rules + 4 references) | ✅ Complete |
| Phase 2 | Due diligence, site planning, zoning plugins + 2 agents | ✅ Complete |
| Phase 3 | Programming, specifications, sustainability (EDGE/LOTUS/EPD/energy) | ✅ Complete |
| Phase 4 | Materials research, presentations, dispatcher, integration testing | 🔲 In planning |

---

## Language

All skill outputs are in **Vietnamese** (tiếng Việt). Technical terms include English equivalents in parentheses on first use. The `/dac-ta-ky-thuat` skill supports **bilingual (Việt–English)** output for FDI projects.

The bilingual glossary (`reference/thuat-ngu-song-ngu.md`) covers 234 terms across 12 AEC categories.

README and INSTALL are in English for international accessibility.

---

## Based On

Localized from [AlpacaLabsLCC/skills-for-architects](https://github.com/AlpacaLabsLLC/skills-for-architects) — a Claude Code skill suite for architecture professionals, originally focused on NYC and Uruguay.

## License

MIT License — see [LICENSE](LICENSE).

## Contributing

Contributions welcome, especially:
- Additional QCVN/TCVN reference data
- Provincial-specific zoning datasets (Hà Nội, Đà Nẵng, Bình Dương, etc.)
- MCP connectors for Vietnamese government portals (CTTĐT, QHVN, GIS portals)
- Phase 4 skill implementations (materials, presentations, dispatcher)
- Test cases for edge scenarios and regional variations
