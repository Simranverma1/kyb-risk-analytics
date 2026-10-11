# Data sources

## 1. Companies House – Basic Company Data
- **Downloaded:** 2026-10-10
- **Snapshot date:** 2026-10-01 (from file name)
- **File:** BasicCompanyDataAsOneFile-2026-10-01.csv
- **Size:** 2,810,066,457 bytes (~2.8 GB unzipped; ZIP ~494 MB)
- **Rows:** _to be measured in profiling_
- **Source:** https://download.companieshouse.gov.uk/en_output.html

### Format observations
- Header row present; 55 columns.
- Comma separated; every value wrapped in double quotes.
- Some column names have a leading space (e.g. " CompanyNumber") and contain dots
  (e.g. RegAddress.PostCode) -> load with normalize_names=true.
- Company numbers are text with leading zeros ("08209948") -> must be read as text.
- Dates are DD/MM/YYYY -> parse explicitly with format '%d/%m/%Y'.
- Empty values are "" (empty string), not NULL -> convert to NULL in staging.

### Findings
- Returns.* columns are obsolete (annual returns replaced by confirmation statements in 2016);
  use ConfStmtNextDueDate / ConfStmtLastMadeUpDate for overdue checks.
- Country field is inconsistent ("ENGLAND" vs "UNITED KINGDOM") -> needs standardising.
- Dormant companies are identifiable via Accounts.AccountCategory = DORMANT and SIC 99999.
- Name changes are recorded in PreviousName_1..10 with change dates (CONDATE).