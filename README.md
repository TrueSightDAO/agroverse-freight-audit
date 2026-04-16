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

## Filename date convention

Use **`YYYYMMDD`** for the calendar date taken from the **source quotation** (not commit
time). When the quote also includes a time of day, append **`_HHMM_`** using 24-hour clock
(`HHMM`, no colons) after the date, before descriptive slugs.

Pattern:

- `YYYYMMDD_<optional-descriptive-slugs>_…` when only a date is known
- `YYYYMMDD_HHMM_<optional-descriptive-slugs>_…` when date and time are known from the quote

Examples:

- `quotations/20251104_1254_omega-services_not-san-francisco-in-quote_quote.pdf`
- `snapshots/20251104_1254_omega-services_not-san-francisco-in-quote_freight-pricing.json`
- `manifests/20260406_matheus-reis_manifests.json`

When the vendor document does not name a US city (for example San Francisco), include that
fact in the filename slug and in JSON `geographic_scope` so audits stay honest.

If timezone is unknown from source, include `timezone: "unknown"` in JSON metadata and
store the original timestamp text exactly as written in the quote.

## First Baseline Added

The initial baseline is based on Omega / Mega Services quote content and the freight
model originally introduced in `tokenomics` commit `a1a61a86`.