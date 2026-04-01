# Account Service

- **Repo:** finos/traderX
- **Directory:** account-service/
- **Tech:** Java, Spring Boot
- **Port:** 18088
- **Type:** REST API

## Purpose

Exposes CRUD functionality over trading accounts. Connects to the H2 database for account persistence and to the People Service for validating user associations with accounts.

## Connections

- **Inbound:** [[web-front-end]] (REST/HTTP), [[trade-service]] (REST/HTTP — validate account)
- **Outbound:** [[database]] (JDBC), [[people-service]] (REST/HTTP — validate people)

## API

- Swagger UI: `/swagger-ui.html`
- API docs: `/api-docs`
- Example: `/account/` (list), `/account/22141` (by ID)

## Sources

- Code: https://github.com/finos/traderX/tree/main/account-service
- Last synced: 2026-04-01
