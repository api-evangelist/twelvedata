# Twelve Data (twelvedata)

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
