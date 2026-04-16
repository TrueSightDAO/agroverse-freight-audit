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
- `quotations/20260415_0748_ilheus-ba-to-san-francisco-ca94117_omega-services_quote.pdf`
- `snapshots/20260415_0748_ilheus-ba-to-san-francisco-ca94117_omega-services_freight-pricing.json`
- `quotations/20260324_1035_ilheus-ba-to-austin-tx78704-3rd-eye-cafe_omega-services_quote.pdf`
- `snapshots/20260324_1035_ilheus-ba-to-austin-tx78704-3rd-eye-cafe_omega-services_freight-pricing.json`
- `manifests/20260406_matheus-reis_manifests.json`

When the vendor document does not name a US city (for example San Francisco), include that
fact in the filename slug and in JSON `geographic_scope` so audits stay honest.

If timezone is unknown from source, include `timezone: "unknown"` in JSON metadata and
store the original timestamp text exactly as written in the quote.

If the vendor PDF is silent on the city pair but the operator knows the intended lane,
record that under JSON `operator_shipment_context` (and keep `geographic_scope` faithful
to what the vendor PDF actually prints).

## First Baseline Added

The initial baseline is based on Omega / Mega Services quote content and the freight
model originally introduced in `tokenomics` commit `a1a61a86`.

## Latest vendor quotation (explicit route)

`quotations/20260415_0748_ilheus-ba-to-san-francisco-ca94117_omega-services_quote.pdf`
names **Ilheus, BA, Brazil** to **San Francisco, CA 94117** in the vendor email text, and
is archived alongside
`snapshots/20260415_0748_ilheus-ba-to-san-francisco-ca94117_omega-services_freight-pricing.json`.

Note: the operator download filename may use `YYYYMMDD` (for example `20260414 …`) while
the email timestamp inside the PDF is `2026-04-15 07:48`; repository filenames follow the
**email timestamp** when present, per the timestamp policy above.

## Vendor quotation (Ilheus to Austin / 3rd Eye Cafe)

`quotations/20260324_1035_ilheus-ba-to-austin-tx78704-3rd-eye-cafe_omega-services_quote.pdf`
covers **Matheus pickup in Ilheus, BA** to **Austin, TX 78704** (operator destination:
**3rd Eye Cafe**), archived alongside
`snapshots/20260324_1035_ilheus-ba-to-austin-tx78704-3rd-eye-cafe_omega-services_freight-pricing.json`.