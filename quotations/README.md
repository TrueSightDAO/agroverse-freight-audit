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

## Example (explicit vendor route + operator download filename)

`20260415_0748_ilheus-ba-to-san-francisco-ca94117_omega-services_quote.pdf`

The email timestamp inside the PDF is `Wed, Apr 15, 2026 at 7:48 AM`, so the repository
filename uses `20260415_0748…` even if the operator saved the export locally as
`20260414 Quotation Mega services.pdf`.

## Example (Ilheus to Austin / 3rd Eye Cafe)

`20260324_1035_ilheus-ba-to-austin-tx78704-3rd-eye-cafe_omega-services_quote.pdf`

Email timestamp inside the PDF: `Tue, Mar 24, 2026 at 10:35 AM` → `20260324_1035…`.
