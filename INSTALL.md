# Installation Guide

Step-by-step instructions for installing the Vietnamese Architecture & Planning Skill.

## Option 1: Claude Desktop (Cowork Mode)

This is the recommended approach for non-developers.

### Step 1: Download the skill files

```bash
git clone https://github.com/YOUR_USERNAME/architect-skill-vietnam.git
```

Or download as ZIP from GitHub and extract.

### Step 2: Open Claude Desktop

1. Open the Claude desktop app
2. Switch to **Cowork mode** (click the Cowork toggle or select it from the mode picker)
3. Click **Select a folder** and choose the `architect-skill-vietnam` directory you just downloaded

### Step 3: Verify

Type any skill command to test:

```
/phan-tich-quy-hoach-vn 123 Nguyễn Huệ, Quận 1, TP.HCM
```

Claude should recognize the skill and begin the zoning analysis workflow.

### How it works

When you select the `architect-skill-vietnam` folder in Cowork mode, Claude automatically reads the `rules/`, `reference/`, `plugins/`, and `agents/` directories. Each `SKILL.md` file inside a `skills/*/` directory becomes an invocable skill.

---

## Option 2: Claude Code CLI

For developers using Claude Code from the terminal.

### Step 1: Clone into your project

```bash
cd your-project-directory
git clone https://github.com/YOUR_USERNAME/architect-skill-vietnam.git .claude/skills/architect-skill-vietnam
```

Or add as a subdirectory:

```bash
mkdir -p .claude/skills
cp -r /path/to/architect-skill-vietnam .claude/skills/architect-skill-vietnam
```

### Step 2: Verify the structure

```bash
ls .claude/skills/architect-skill-vietnam/plugins/*/skills/*/SKILL.md
```

You should see 14 SKILL.md files.

### Step 3: Use in Claude Code

```bash
claude
```

Then type skill commands:

```
/phan-tich-quy-hoach-vn 88 Nguyễn Huệ, Quận 1, TP.HCM
```

### Alternative: Global installation

To make the skills available across all projects:

```bash
cp -r architect-skill-vietnam ~/.claude/skills/architect-skill-vietnam
```

---

## Option 3: As a Plugin (.plugin format)

> **Note:** Plugin packaging format may evolve. This section describes the current approach.

### Step 1: Create plugin manifest

Create a file called `plugin.json` at the project root:

```json
{
  "name": "architect-skill-vietnam",
  "version": "1.0.0",
  "description": "Vietnamese Architecture & Planning Skill for Claude",
  "skills": [
    "plugins/00-tham-dinh/skills/*/SKILL.md",
    "plugins/01-quy-hoach-mat-bang/skills/*/SKILL.md",
    "plugins/02-phan-khu/skills/*/SKILL.md"
  ],
  "agents": [
    "agents/*.md"
  ],
  "rules": [
    "rules/*.md"
  ],
  "references": [
    "reference/*.md"
  ]
}
```

### Step 2: Install via Cowork plugin management

In Cowork mode, use the plugin installer or manually place the directory in your plugins folder.

---

## File Structure Requirements

The skill system expects this exact structure:

```
plugins/
  {plugin-name}/
    skills/
      {skill-name}/
        SKILL.md          ← Required: skill definition with YAML frontmatter
```

Each `SKILL.md` must have YAML frontmatter with at minimum:

```yaml
---
name: skill-name
description: "One-line description"
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
  - Bash
user-invocable: true
---
```

---

## Configuration

### Required: Web search access

Most skills use `WebSearch` and `WebFetch` to query Vietnamese government portals, QCVN databases, and market data. Ensure your Claude instance has web access enabled.

- **Claude Desktop:** Web access is on by default in Cowork mode
- **Claude Code:** Web access is available by default
- **Enterprise:** Check with your admin that network access is enabled in Admin settings → Capabilities

### Optional: File uploads

For best results with zoning analysis, users can upload:

- **Bản đồ quy hoạch 1/500** (PDF or image) — detailed zoning map from local planning authority
- **Sổ đỏ / GCNQSDĐ** (PDF or image) — land use certificate

Skills will automatically prompt for these when relevant.

---

## Troubleshooting

### Skills not recognized

**Symptom:** Claude doesn't respond to `/phan-tich-quy-hoach-vn` or other commands.

**Fix:**
1. Verify the folder is selected in Cowork mode (check the folder name in the sidebar)
2. Check that `SKILL.md` files exist: `ls plugins/*/skills/*/SKILL.md`
3. Ensure YAML frontmatter is valid (no tabs, correct indentation)
4. Try restarting the Claude desktop app

### Web search not working

**Symptom:** Skills return "unable to search" or incomplete results.

**Fix:**
1. Check internet connection
2. In Claude Desktop: Settings → Capabilities → ensure "Web search" is enabled
3. Some Vietnamese government portals may be slow or intermittent — the skills will note this in "Khoảng Trống & Lưu Ý"

### Vietnamese text rendering

**Symptom:** Vietnamese diacritics (ă, ơ, ư, ệ, etc.) display incorrectly.

**Fix:**
1. Ensure your terminal/editor uses UTF-8 encoding
2. Git config: `git config --global core.quotepath false` to display Vietnamese filenames correctly

### Skills produce English output instead of Vietnamese

**Symptom:** Some responses come back in English.

**Fix:**
The rules in `rules/dinh-dang-dau-ra.md` enforce Vietnamese output. If Claude switches to English:
1. Explicitly state: "Trả lời bằng tiếng Việt" in your prompt
2. Check that the `rules/` directory is accessible to Claude
3. Re-select the project folder in Cowork mode

### QCVN values seem outdated

**Symptom:** A QCVN code has been updated since the skill was written.

**Fix:**
1. The reference file `reference/qcvn-tong-hop.md` contains the QCVN versions used
2. Check for updates at [moc.gov.vn](https://moc.gov.vn) (Ministry of Construction)
3. Skills use `WebSearch` to find current versions, but the fallback tables may reference older editions
4. Update `qcvn-tong-hop.md` with new versions as they are published

---

## Uninstallation

Simply remove the skill directory:

```bash
rm -rf ~/.claude/skills/architect-skill-vietnam
# or
rm -rf .claude/skills/architect-skill-vietnam
```

No system-level changes are made. No environment variables or config files are modified outside the skill directory.
