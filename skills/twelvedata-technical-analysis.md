---
name: Run technical analysis on a symbol
description: Compute server-side technical indicators (RSI, MACD, Bollinger
  Bands, and 100+ more) over any Twelve Data time series without fetching raw
  bars first.
api: openapi/twelvedata-technical-indicators-api-openapi.yml
operations: [listTechnicalIndicators, getRSI, getMACD, getBBands]
generated: '2026-07-22'
method: generated
---

# Run technical analysis on a symbol

1. **Authenticate** with `Authorization: apikey <key>` (see
   `authentication/twelvedata-authentication.yml`).
2. **Discover indicators** with `listTechnicalIndicators`
   (`GET /technical_indicators`) — it returns the full catalog of 100+
   server-side indicators with their parameters and defaults.
3. **Compute directly.** Indicators are endpoints, not client math:
   `getRSI` (`GET /rsi`), `getMACD` (`GET /macd`), `getBBands` (`GET /bbands`).
   Each takes the same core params as a time series: `symbol`, `interval`
   (`1min`…`1month`), plus indicator-specific tuning (e.g. `time_period`).
4. **Combine indicators** by issuing parallel calls for the same
   `symbol`/`interval` — but budget credits: each call consumes API credits and
   the per-minute quota resets every minute (free plan: 8 credits/minute). On
   429, back off to the next minute. See `rate-limits/twelvedata-rate-limits.yml`.
5. **Interpret nulls** as data gaps, not errors, per
   `conventions/twelvedata-conventions.yml`.
