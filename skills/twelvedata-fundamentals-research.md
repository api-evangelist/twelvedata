---
name: Research company fundamentals
description: Build a fundamental picture of a company — profile, statements,
  earnings, dividends, and key statistics — from the Twelve Data Fundamentals API.
api: openapi/twelvedata-fundamentals-api-openapi.yml
operations: [getProfile, getStatistics, getIncomeStatement, getBalanceSheet, getCashFlow, getEarnings, getDividends]
generated: '2026-07-22'
method: generated
---

# Research company fundamentals

1. **Authenticate** with `Authorization: apikey <key>`. Fundamentals endpoints
   carry higher credit weights and may require a paid plan — a 403 means the
   key's plan does not cover the dataset (test first with the trial symbols
   listed at https://twelvedata.com/exchanges; see `sandbox/twelvedata-sandbox.yml`).
2. **Start with identity:** `getProfile` (`GET /profile?symbol=<sym>`) for
   sector, industry, description, and officers.
3. **Pull the statements:** `getIncomeStatement` (`GET /income_statement`),
   `getBalanceSheet` (`GET /balance_sheet`), `getCashFlow` (`GET /cash_flow`) —
   each supports `period=annual|quarterly`.
4. **Add performance context:** `getEarnings` (`GET /earnings`) for reported vs
   estimated EPS, `getDividends` (`GET /dividends`) for payout history, and
   `getStatistics` (`GET /statistics`) for valuation ratios and financial
   highlights.
5. **Expect nulls** for metrics a company does not report — handle them as
   missing data, not errors (`conventions/twelvedata-conventions.yml`), and
   budget the per-minute credit quota across the five-plus calls
   (`rate-limits/twelvedata-rate-limits.yml`).
