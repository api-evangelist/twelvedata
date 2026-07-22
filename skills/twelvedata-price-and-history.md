---
name: Fetch a price and its history
description: Resolve any instrument to a Twelve Data symbol, then pull the live
  quote and historical OHLCV bars, respecting the credit-based rate limits.
api: openapi/twelvedata-core-data-api-openapi.yml
operations: [getPrice, getQuote]
additional_apis:
- api: openapi/twelvedata-reference-data-api-openapi.yml
  operations: [symbolSearch, getEarliestTimestamp]
- api: openapi/twelvedata-time-series-api-openapi.yml
  operations: [getTimeSeries]
generated: '2026-07-22'
method: generated
---

# Fetch a price and its history

1. **Authenticate.** Every call needs an API key — send `Authorization: apikey <key>`
   (recommended) or append `?apikey=<key>`. A free Basic key (800 credits/day,
   8/minute) comes from https://twelvedata.com/register; `apikey=demo` works for
   demo requests. See `authentication/twelvedata-authentication.yml`.
2. **Resolve the symbol** with `symbolSearch` (`GET /symbol_search?symbol=<query>`)
   when the user gives a company name or ambiguous ticker. Symbol formats:
   stocks `AAPL`, crypto `BTC/USD`, forex `EUR/USD`. Disambiguate multi-listing
   hits with `exchange` or `mic_code`.
3. **Latest value:** `getPrice` (`GET /price`) for just the number,
   `getQuote` (`GET /quote`) for OHLC, volume, and change.
4. **History:** `getTimeSeries` (`GET /time_series`) with `interval`
   (`1min`…`1month`) and `outputsize` or `start_date`/`end_date`. Call
   `getEarliestTimestamp` first when you need to know how far back data goes.
5. **Handle the envelope.** Errors return `{code, message, status:"error"}` —
   400 means a bad parameter (the message names it), 429 means the per-minute
   credit window is exhausted: wait for the minute to reset, do not tight-loop.
   Null fields are expected when data is unavailable. See
   `errors/twelvedata-problem-types.yml` and `conventions/twelvedata-conventions.yml`.
