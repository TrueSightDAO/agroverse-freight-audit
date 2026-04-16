# agroverse-freight-audit

Historical audit trail for freight quotations, pricing snapshots, and shipping manifests.

## Purpose

This repository preserves immutable historical evidence for freight pricing decisions so
future calculations can be traced to the exact quote and rule set that were active at a
point in time.

## Record Types

- `quotations/`: source vendor quote PDFs (timestamped from quote itself)
- `snapshots/`: machine-readable pricing model snapshots used by modules
- `manifests/`: archived shipping manifest references and normalized metadata

## Timestamp Policy

For quotations and snapshots, filenames must use the timestamp from the source quote
document/email when available (not commit time).

Example:

- `2025-11-04T12-54_omega-services_quote.pdf`
- `2025-11-04T12-54_omega-services_freight-pricing.json`

If timezone is unknown from source, include `timezone: "unknown"` in JSON metadata and
store the original timestamp text exactly as written in the quote.

## First Baseline Added

The initial baseline is based on Omega / Mega Services quote content and the freight
model originally introduced in `tokenomics` commit `a1a61a86`.