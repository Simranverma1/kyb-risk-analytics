# kyb-risk-analytics
Merchant KYB risk analytics on public UK Companies House and beneficial-owner data: a DuckDB + dbt pipeline that flags shell-company risk, screens owners against UK and OFAC sanctions lists, calibrates match thresholds against analyst capacity, and tiers merchants for due diligence in Power BI. Simulated portfolio; no individuals named.

# Merchant KYB Risk & Screening Analytics

**Question:** How should a card network tier its merchants for due diligence, and which
sanctions-screening threshold should it use, given fixed analyst capacity?

**Status:** 🚧 in progress (Day 1: environment and repo set up)

## Data
Public UK Companies House data (company register + PSC beneficial owners), UK Sanctions List,
OFAC SDN. The merchant portfolio is a simulated selection of real companies; the screening
evaluation set is synthetic. Individuals are never named in outputs.

## How to run
pip install -r requirements.txt
(make refresh: coming Day 6)

## Results
Coming soon. Every number here will come from the pipeline.