# Financial Services Codex Skill

Codex-compatible routing skill converted from the Anthropic `financial-services` marketplace content.

This repository is intentionally lightweight: it provides a top-level Codex Skill that routes broad financial-services tasks to specialist skills already installed under `~/.codex/skills`.

## What It Does

Use this skill when working on financial-services workflows such as:

- Financial modeling: comps, DCF, LBO, three-statement models, Excel audit
- Investment banking: pitch decks, CIMs, teasers, buyer lists, merger models
- Equity research: earnings analysis, initiations, model updates, sector notes
- Private equity: deal screening, diligence, IC memos, returns analysis
- Wealth management: client reviews, proposals, rebalancing, tax-loss harvesting
- Fund administration: GL reconciliation, NAV tie-out, variance commentary
- Operations: KYC document parsing and rules evaluation
- Partner-data workflows: LSEG and S&P Global-oriented research tasks

## Repository Structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── skill-catalog.md
```

## Installation

Clone or copy this repository into your Codex skills directory:

```bash
git clone https://github.com/MichaelRochonnn/anthropics-financial-services-cn.git \
  ~/.codex/skills/financial-services
```

Then restart Codex so the new skill is picked up.

## Usage

Example prompts:

```text
Use $financial-services to prepare an equity research workflow for PDD.
Use $financial-services to route a DCF and comps analysis for Microsoft.
Use $financial-services to identify which specialist skill should handle a pitch deck request.
```

You can also invoke specialist skills directly if they are installed locally, for example:

```text
Use $equity-research to analyze PDD.
Use $dcf-model to value Apple.
Use $comps-analysis to build trading comps for SaaS companies.
```

## Important Notes

This repo contains the router skill only. The detailed specialist skills are expected to exist locally in `~/.codex/skills`.

The original Claude marketplace package references MCP/data connectors. Installing this Codex skill does not automatically configure those connectors. If a workflow requires data from LSEG, S&P Global, FactSet, Daloopa, or another provider, provide the dataset separately or configure the connector in your Codex environment.

Nothing generated through this skill is investment, legal, tax, accounting, onboarding, trading, or risk approval advice. Treat outputs as analyst work product for qualified human review.
