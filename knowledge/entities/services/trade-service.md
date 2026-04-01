# Trade Service

- **Repo:** finos/traderX
- **Directory:** trade-service/
- **Tech:** Java, Spring Boot
- **Port:** 18092
- **Type:** REST API

## Purpose

Accepts new trade requests (security, quantity, accountID, side), validates the account via [[account-service]] and the ticker via [[reference-data]], then publishes the trade onto the [[trade-feed]] for further processing.

## Connections

- **Inbound:** [[web-front-end]] (REST/HTTP)
- **Outbound:** [[account-service]] (REST/HTTP — validate account), [[reference-data]] (REST/HTTP — validate ticker), [[trade-feed]] (Socket.IO — publish trade events)

## API

- Swagger UI: `/swagger-ui.html`
- API docs: `/api-docs`
- Submit trade: `POST /trade/`

## Sources

- Code: https://github.com/finos/traderX/tree/main/trade-service
- Last synced: 2026-04-01
