# Quotations Folder

Store vendor quote PDFs here using the repository **source-quote** filename convention.

## Naming Rule

`YYYYMMDD[_HHMM]_vendor_<scope-or-slug>_quote.pdf`

- **`YYYYMMDD`**: date from the quotation (not git commit date).
- **`_HHMM_`**: optional; include when the quote text includes a time (24-hour `HHMM`).

For the Omega / Mega Services quote discussed, the vendor PDF does **not** name San
Francisco or any US destination city. Use an explicit slug in the filename:

`20251104_1254_omega-services_not-san-francisco-in-quote_quote.pdf`

The source timestamp comes from quote text:

`Tue, Nov 4, 2025 at 12:54 PM`

If timezone is unknown in source material, keep timezone unknown in related JSON metadata.
