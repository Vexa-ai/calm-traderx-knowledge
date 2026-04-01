# Position Service

- **Repo:** finos/traderX
- **Directory:** position-service/
- **Tech:** Java, Spring Boot
- **Port:** 18090
- **Type:** REST API

## Purpose

Retrieves trades and aggregate positions from the database and returns them to pre-populate a blotter (trades/positions) for a specific accountID. Incremental updates are received in the GUI via the pub-sub [[trade-feed]] service.

## Connections

- **Inbound:** [[web-front-end]] (REST/HTTP)
- **Outbound:** [[database]] (JDBC)

## API

- Swagger UI: `/swagger-ui.html`
- API docs: `/api-docs`
- Trades by account: `/trades/{accountId}`
- Positions by account: `/positions/{accountId}`

## Sources

- Code: https://github.com/finos/traderX/tree/main/position-service
- Last synced: 2026-04-01
