# Reference Data

- **Repo:** finos/traderX
- **Directory:** reference-data/
- **Tech:** Node.js, NestJS
- **Port:** 18085
- **Type:** REST API

## Purpose

Provides a list of stock tickers and their associated company names via a RESTful interface. Serves as the security master for the TraderX environment, sourcing ticker data from a CSV of S&P 500 companies.

## Connections

- **Inbound:** [[web-front-end]] (REST/HTTP), [[trade-service]] (REST/HTTP)
- **Outbound:** None (reads from local CSV data)

## API

- OpenAPI UI: `/api/`
- All stocks: `/stocks`
- Single ticker: `/stocks/:ticker`

## Sources

- Code: https://github.com/finos/traderX/tree/main/reference-data
- Last synced: 2026-04-01
