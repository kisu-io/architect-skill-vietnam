# Installation — Architect Skill Vietnam for Hermes Agent

This guide walks you through installing the Vietnamese architecture skill bundle into [Hermes Agent](https://nousresearch.com) (Nous Research). The bundle ships as a **single sub-agent `@architect-vn`** that fronts 17 skills — you install the agent and the skills together, then invoke only `@architect-vn`.

## Prerequisites

- **Hermes Agent** installed and running on your host (laptop, homelab, or VPS).
- **A web-fetching capability** exposed to Hermes. The skills reference "the web search tool" and "the web fetch tool" abstractly — any configured web tool (built-in, community skill, or shell-based via `curl`) will satisfy them.
- (Optional) **Git** if you're cloning rather than downloading.

## Install Paths

Hermes auto-discovers skills from `~/.hermes/skills/` and agents from `~/.hermes/agents/`. The runtime maintains `~/.hermes/skills/.bundled_manifest` as a content-hash index — no per-skill manifest file is required.

For most users, `~/.hermes/skills/` is the right choice.

## Option A — User-scoped install (recommended)

```bash
# Clone (or pull this repo's `hermes/` subfolder)
git clone https://github.com/kisu-io/architect-skill-vietnam.git
cd architect-skill-vietnam/hermes

# Install the @architect-vn sub-agent
mkdir -p ~/.hermes/agents
cp agents/architect-vn.md ~/.hermes/agents/

# Install every skill (flat layout — already flattened in this repo)
mkdir -p ~/.hermes/skills
cp -r skills/* ~/.hermes/skills/
```

Verify:

```bash
ls ~/.hermes/skills/ | grep -E '^(kien-truc-vn-rules|chuyen-gia-|bao-cao-tong-hop|tra-cuu-|phan-tich-|mo-hinh-)' | sort
# Expected output:
#   bao-cao-tong-hop
#   chuyen-gia-phan-khu-vn
#   chuyen-gia-quy-hoach
#   kien-truc-vn-rules
#   mo-hinh-khoi-tich-3d
#   phan-tich-dan-so
#   phan-tich-dat-dai
#   phan-tich-giao-thong
#   phan-tich-lich-su
#   phan-tich-moi-truong
#   phan-tich-quy-hoach-vn
#   tra-cuu-dat-dai
#   tra-cuu-di-tich
#   tra-cuu-giay-phep-xd
#   tra-cuu-pccc
#   tra-cuu-quy-hoach
#   tra-cuu-vi-pham-xd
```

Restart Hermes. It watches `~/.hermes/skills/` and `~/.hermes/agents/` and will pick up the new content on next start (it will also recompute `.bundled_manifest` and `.skills_prompt_snapshot.json`). The `kien-truc-vn-rules` skill is marked `metadata.openclaw.always: true`, so its rules load automatically in every session.

## Option B — Workspace-scoped install

Use this for a single project where you want the skills versioned alongside the code:

```bash
mkdir -p <your-project>/.hermes/skills <your-project>/.hermes/agents
cp -r hermes/skills/* <your-project>/.hermes/skills/
cp hermes/agents/architect-vn.md <your-project>/.hermes/agents/
```

When you launch Hermes inside that workspace, it loads these skills at workspace precedence.

## Option C — Symlink for development

If you're iterating on the skills and want changes reflected without copying:

```bash
ln -s "$PWD/hermes/agents/architect-vn.md" ~/.hermes/agents/architect-vn.md
for d in hermes/skills/*; do
  ln -s "$PWD/$d" "$HOME/.hermes/skills/$(basename "$d")"
done
```

## Verifying the Install

From a Hermes session, invoke the agent:

```
@architect-vn liệt kê các kỹ năng bạn đang có
```

Or trigger directly on a question:

```
@architect-vn phân tích quy hoạch cho 88 Nguyễn Huệ, Quận 1, TP.HCM
```

If install succeeded, the agent responds in Vietnamese following the conventions from `kien-truc-vn-rules` (metric units, QCVN/TCVN citations, mandatory disclaimer) and routes to the right sub-skill.

### Bypassing the agent

You can also invoke individual skills by slug — e.g. `/phan-tich-quy-hoach-vn <địa chỉ>`. The agent is the recommended interface; direct-skill invocation is supported for debugging and power users.

## Web Tool Configuration

The skills perform web lookups against Vietnamese government portals and QCVN text. Make sure one of the following is available to Hermes:

- A built-in web search / web fetch capability
- A community skill such as `web-search` or `web-fetch`
- A shell-based fallback (`curl`, `wget`, `jq`)

If web lookups fail, confirm Hermes has network egress for the relevant domains:

- `gisxaydung.tphcm.gov.vn`
- `moc.gov.vn`
- `monre.gov.vn`
- `tcvn.gov.vn`
- `canhsatpccc.gov.vn`

## Updating

```bash
cd <where-you-cloned>/architect-skill-vietnam
git pull

# Re-copy the changed folders, e.g.:
cp -r hermes/skills/kien-truc-vn-rules ~/.hermes/skills/
```

Hermes re-reads skill folders automatically when `SKILL.md` files change and refreshes `.bundled_manifest` on next start.

## Uninstalling

```bash
rm ~/.hermes/agents/architect-vn.md
rm -rf ~/.hermes/skills/{kien-truc-vn-rules,chuyen-gia-phan-khu-vn,chuyen-gia-quy-hoach}
rm -rf ~/.hermes/skills/{bao-cao-tong-hop,tra-cuu-*,phan-tich-*,mo-hinh-khoi-tich-3d}
```

## Troubleshooting

**`@architect-vn` not recognised.** Confirm `~/.hermes/agents/architect-vn.md` exists. Restart Hermes after installing the agent file so it re-scans the agents dir.

**Agent mounts, but individual skills don't load.** The agent's `skills:` frontmatter references skills by slug — each slug must exist under `~/.hermes/skills/`. Check `ls ~/.hermes/skills/` against the agent's skill list. If a slug is missing, Hermes logs a warning and continues with the rest.

**Skill doesn't trigger.** Hermes matches on name + description to decide relevance. Rephrase your request using vocabulary from the `description` field, or invoke by slug: `/phan-tich-quy-hoach-vn <địa chỉ>`.

**Rules aren't applied.** Confirm `~/.hermes/skills/kien-truc-vn-rules/SKILL.md` exists and that `metadata.openclaw.always: true` is in its frontmatter. Verify `.bundled_manifest` lists `kien-truc-vn-rules`.

**Web lookups fail.** See "Web Tool Configuration" above.

**Slug rejected.** Slugs must match `^[a-z0-9][a-z0-9-]*$`. All slugs in this bundle comply — if you rename one, keep to lowercase + hyphens only.
