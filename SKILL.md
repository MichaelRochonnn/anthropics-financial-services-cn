---
name: financial-services
description: Route broad financial-services requests to the converted Anthropic financial-services specialist skills. Use when a user asks for financial modeling, investment banking, equity research, private equity, wealth management, fund administration, KYC/operations, LSEG, S&P Global, or asks to use the anthropics/financial-services Claude plugin behavior inside Codex.
---

# Financial Services

This is a routing skill for the converted Anthropic financial-services marketplace content. It coordinates the installed specialist skills under `~/.codex/skills` rather than duplicating their detailed instructions.

## Safety Boundary

- Treat all outputs as analyst work product for human review.
- Do not present outputs as investment, legal, tax, accounting, onboarding, trading, or risk approval advice.
- Call out missing data, stale data, assumptions, and unavailable connectors.
- Prefer user-provided files, official filings, audited statements, subscribed market-data connectors, and cited primary sources over generic web results.

## Routing

Use the most specific specialist skill for the user request. Before executing a selected specialist workflow, read its `SKILL.md` completely from `~/.codex/skills/<skill-name>/SKILL.md`, then read only the referenced files needed for the task.

- Financial modeling: `comps-analysis`, `dcf-model`, `lbo-model`, `3-statement-model`, `audit-xls`, `clean-data-xls`, `xlsx-author`
- Presentation and deck work: `pitch-deck`, `ib-check-deck`, `deck-refresh`, `pptx-author`, `ppt-template-creator`
- Investment banking: `strip-profile`, `cim-builder`, `teaser`, `buyer-list`, `merger-model`, `process-letter`, `deal-tracker`, `datapack-builder`
- Equity research: `earnings-analysis`, `earnings-preview`, `initiating-coverage`, `model-update`, `morning-note`, `sector-overview`, `thesis-tracker`, `catalyst-calendar`, `idea-generation`
- Private equity: `deal-sourcing`, `deal-screening`, `dd-checklist`, `dd-meeting-prep`, `unit-economics`, `returns-analysis`, `ic-memo`, `portfolio-monitoring`, `value-creation-plan`, `ai-readiness`
- Wealth management: `client-review`, `client-report`, `financial-plan`, `investment-proposal`, `portfolio-rebalance`, `tax-loss-harvesting`
- Fund administration and finance ops: `gl-recon`, `break-trace`, `accrual-schedule`, `roll-forward`, `variance-commentary`, `nav-tieout`
- Operations and onboarding: `kyc-doc-parse`, `kyc-rules`
- Partner-data workflows: LSEG skills (`bond-relative-value`, `swap-curve-strategy`, `fx-carry-trade`, `option-vol-analysis`, `macro-rates-monitor`, `fixed-income-portfolio`, `bond-futures-basis`, `equity-research`) and S&P Global skills (`tear-sheet`, `earnings-preview-beta`, `funding-digest`)

If the request is broad, decompose it into a short workplan and select the fewest specialist skills needed. If the request maps to a Claude slash command from the original plugin, infer the equivalent specialist skill from the task name.

## Catalog

Read `references/skill-catalog.md` when the user asks what was installed, wants the full menu, or gives a broad workflow that could route to several skills.

## Connector Notes

The converted skills include procedures that may mention MCP/data connectors from the original Claude plugin. Codex does not automatically install those connectors from the Claude marketplace. If a required connector is unavailable, use user-provided data or ask for the needed dataset, and clearly label any fallback.
