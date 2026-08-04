# Twelve Data (twelvedata)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Twelve Data is a financial market data provider offering real-time and historical data for stocks, forex, cryptocurrencies, ETFs, indices, commodities, and funds through a single REST API and a real-time WebSocket. Coverage spans time series (OHLCV), quotes and prices, 100-plus technical indicators, reference and catalog data, and company fundamentals.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/twelvedata/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/twelvedata/refs/heads/main/apis.yml)

## Access Model

Twelve Data is public and self-service. You register for a free API key and every request is authenticated with that `apikey` — supplied either as a query parameter (`?apikey=YOUR_API_KEY`) or via the `Authorization: apikey YOUR_API_KEY` header. Usage is metered as **API credits**: each endpoint has a data weight, and the per-minute credit quota resets each minute. The free **Basic** plan grants 8 API credits per minute and 800 per day; paid **Grow**, **Pro**, **Ultra**, and **Enterprise** plans raise the ceilings and add markets, real-time exchange coverage, fundamentals, and larger WebSocket allotments.

## Real-Time WebSocket

In addition to the REST API, Twelve Data operates a genuine bidirectional **WebSocket** for real-time price streaming at `wss://ws.twelvedata.com/v1/quotes/price`. You authenticate by appending `?apikey=YOUR_API_KEY` to the connection URL, then send JSON control messages such as `{"action":"subscribe","params":{"symbols":"AAPL,EUR/USD,BTC/USD"}}`. The server pushes `price` events (average latency ~170 ms) alongside `subscribe-status` acknowledgements and periodic `heartbeat` events. WebSocket usage is metered separately from REST credits — one WebSocket credit per successfully subscribed symbol.

## Tags

- Market Data
- Financial Data
- Stocks
- Forex
- Crypto
- Real-Time Data
- Technical Indicators
- Fundamentals

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Twelve Data Time Series API

Historical and intraday OHLCV time series for stocks, forex, crypto, ETFs, indices, and commodities across intervals from 1min to 1month, including end-of-day prices and cross-rate time series for exotic pairs.

- **Human URL:** [https://twelvedata.com/docs#time-series](https://twelvedata.com/docs#time-series)
- **Base URL:** `https://api.twelvedata.com`

#### Tags

- Time Series
- Market Data
- Financial Data
- Stocks
- Forex

#### Properties

- [Documentation](https://twelvedata.com/docs#time-series)
- [OpenAPI](openapi/twelvedata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/twelvedata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/twelvedata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Twelve Data Quotes and Price API

Real-time quotes and latest prices, market movers (top gainers and losers), and exchange market state for any supported instrument via the /quote, /price, /market_movers, and /market_state endpoints.

- **Human URL:** [https://twelvedata.com/docs#core-data](https://twelvedata.com/docs#core-data)
- **Base URL:** `https://api.twelvedata.com`

#### Tags

- Quotes
- Real-Time Data
- Stocks
- Market Data

#### Properties

- [Documentation](https://twelvedata.com/docs#core-data)
- [OpenAPI](openapi/twelvedata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/twelvedata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/twelvedata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Twelve Data Technical Indicators API

More than 100 technical analysis indicators computed server-side over time series data, including RSI, MACD, Bollinger Bands, moving averages, ADX, stochastics, and ATR, each sharing the same symbol and interval conventions.

- **Human URL:** [https://twelvedata.com/docs#technical-indicators](https://twelvedata.com/docs#technical-indicators)
- **Base URL:** `https://api.twelvedata.com`

#### Tags

- Technical Indicators
- Market Data
- Analysis

#### Properties

- [Documentation](https://twelvedata.com/docs#technical-indicators)
- [OpenAPI](openapi/twelvedata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/twelvedata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/twelvedata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Twelve Data Reference Data API

Catalogs of tradable instruments and market metadata — stocks, forex pairs, cryptocurrencies, ETFs, indices, commodities, exchanges, and symbol search by name, ISIN, or FIGI — used to discover symbols before requesting data.

- **Human URL:** [https://twelvedata.com/docs#reference-data](https://twelvedata.com/docs#reference-data)
- **Base URL:** `https://api.twelvedata.com`

#### Tags

- Reference Data
- Stocks
- Forex
- Crypto

#### Properties

- [Documentation](https://twelvedata.com/docs#reference-data)
- [OpenAPI](openapi/twelvedata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/twelvedata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/twelvedata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Twelve Data Fundamentals API

Company fundamentals including profiles, dividends, earnings, income statements, balance sheets, cash flow statements, and key valuation statistics for equities.

- **Human URL:** [https://twelvedata.com/docs#fundamentals](https://twelvedata.com/docs#fundamentals)
- **Base URL:** `https://api.twelvedata.com`

#### Tags

- Fundamentals
- Financial Data
- Stocks

#### Properties

- [Documentation](https://twelvedata.com/docs#fundamentals)
- [OpenAPI](openapi/twelvedata-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/twelvedata.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/twelvedata.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Twelve Data WebSocket Streaming API

Real-time price streaming over a persistent, bidirectional WebSocket at `wss://ws.twelvedata.com/v1/quotes/price`. Clients authenticate with an apikey query parameter, send JSON subscribe / unsubscribe / reset control messages, and receive pushed price events (roughly 170 ms average latency), subscribe-status acknowledgements, and heartbeats.

- **Human URL:** [https://twelvedata.com/docs/websocket/ws-real-time-price](https://twelvedata.com/docs/websocket/ws-real-time-price)
- **Base URL:** `wss://ws.twelvedata.com/v1/quotes/price`

#### Tags

- Real-Time Data
- WebSocket
- Streaming
- Market Data

#### Properties

- [Documentation](https://twelvedata.com/docs/websocket/ws-real-time-price)
- [AsyncAPI](asyncapi/twelvedata-asyncapi.yml) — [AsyncAPI Specification](https://www.asyncapi.com/docs/reference/specification/latest)

## Common Properties

- [Authentication](authentication/twelvedata-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/twelve-data)
- [Website](https://twelvedata.com)
- [Documentation](https://twelvedata.com/docs)
- [Plans](plans/twelvedata-plans-pricing.yml)
- [Rate Limits](rate-limits/twelvedata-rate-limits.yml)
- [Fin Ops](finops/twelvedata-finops.yml)
- [Support](https://support.twelvedata.com)
- [Blog](https://twelvedata.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
