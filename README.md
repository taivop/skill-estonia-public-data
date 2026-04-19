# Taivo Agent Marketplace

A Git-based marketplace for reusable agent plugins and skills.

This repo is the place to publish and maintain useful agent capabilities across domains, not only public-data workflows. Current content includes Estonia-focused packages (public sources, building supply search); future packages can include things like self-coaching, productivity, research, engineering, and other reusable agent systems.

➡️ Not sure how to install this? See [this guide](https://www.taivo.ai/how-to-install-a-claude-code-skill-from-github/).

## Distribution Targets

Each package can be distributed through:

1. Anthropic Claude Code plugin marketplace (`.claude-plugin/marketplace.json` + per-package plugin manifests).
2. Codex skill install from Git paths under `skills/.curated` or `skills/.experimental`.

## Repository Layout

```text
.
├── AGENTS.md
├── .claude-plugin/
│   └── marketplace.json
├── skills/
│   ├── .curated/
│   │   └── <package>/
│   └── .experimental/
├── scripts/
│   ├── generate_plugin_manifests.py
│   ├── generate_marketplace.py
│   ├── validate_codex_skills.py
│   └── validate_anthropic_plugins.py
└── .github/workflows/validate-distribution.yml
```

## Current Packages

1. `skills/.curated/estonia-public-sources` — routes questions across 133 official Estonian public sources.
2. `skills/.curated/estonia-building-supply-search` — searches Bauhof, Ehituse ABC, Decora, K-Rauta, Bauhaus, and Depo for products, prices, and stock.

Planned/possible additions:

1. `skill-self-coaching` (from [taivop/skill-self-coaching](https://github.com/taivop/skill-self-coaching))
2. Additional domain packages as they are curated

## Install From Anthropic Marketplace

```bash
claude plugin marketplace add taivop/marketplace
claude plugin install estonia-public-sources@marketplace
claude plugin install estonia-building-supply-search@marketplace
```

## Install In Codex

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo taivop/marketplace \
  --path skills/.curated/estonia-public-sources

python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo taivop/marketplace \
  --path skills/.curated/estonia-building-supply-search
```

## Maintainer Workflow

Use this sequence before committing:

```bash
python3 scripts/generate_plugin_manifests.py
python3 scripts/generate_marketplace.py
python3 scripts/validate_codex_skills.py
python3 scripts/validate_anthropic_plugins.py
python3 scripts/generate_plugin_manifests.py --check
python3 scripts/generate_marketplace.py --check
```

See `AGENTS.md` for full operating rules.
