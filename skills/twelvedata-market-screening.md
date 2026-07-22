---
name: Screen markets and instruments
description: Enumerate what is tradable — instrument catalogs, exchanges, market
  hours, movers, and end-of-day closes — from the Twelve Data Reference and Core
  Data APIs.
api: openapi/twelvedata-reference-data-api-openapi.yml
operations: [listStocks, listForexPairs, listCryptocurrencies, listEtfs, listExchanges]
additional_apis:
- api: openapi/twelvedata-core-data-api-openapi.yml
  operations: [getMarketState, getMarketMovers, getEndOfDay]
generated: '2026-07-22'
method: generated
---

# Screen markets and instruments

1. **Authenticate** with `Authorization: apikey <key>`
   (`authentication/twelvedata-authentication.yml`).
2. **Enumerate the universe** with the catalog operations — `listStocks`
   (`GET /stocks`), `listForexPairs` (`GET /forex_pairs`),
   `listCryptocurrencies` (`GET /cryptocurrencies`), `listEtfs` (`GET /etfs`) —
   filtered by `exchange`, `country`, or `type`. These reference calls are
   credit-light.
3. **Know the venues:** `listExchanges` (`GET /exchanges`) for the exchange
   list, then `getMarketState` (`GET /market_state`) to check which markets are
   currently open before requesting real-time data.
4. **Find what moves:** `getMarketMovers` (`GET /market_movers`) for today's
   top gainers and losers (from the Core Data API,
   `openapi/twelvedata-core-data-api-openapi.yml`).
5. **Close the day:** `getEndOfDay` (`GET /eod`) for official closes when
   real-time coverage of an exchange is not in the plan.
6. **Paginate by window** — reference catalogs return full lists; time-bound
   calls use `outputsize` and date ranges (`conventions/twelvedata-conventions.yml`).
