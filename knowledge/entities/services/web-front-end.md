# Web Front End

- **Repo:** finos/traderX
- **Directory:** web-front-end/
- **Tech:** Angular, React
- **Port:** 18093 (Angular), 18094 (React)
- **Type:** Web Client

## Purpose

Provides a UI for users to select an account, view trades and positions, initiate new trades, and administer accounts. For trade and position blotters, it queries the [[position-service]] and subscribes to the [[trade-feed]] for incremental updates. For executing trades, it queries the [[account-service]] to select an account, the [[reference-data]] service to resolve securities, and the [[trade-service]] for submitting trades. For managing accounts, it connects to the [[account-service]] and the [[people-service]] for resolving users.

## Connections

- **Inbound:** Trader (actor — via browser)
- **Outbound:** [[account-service]] (REST/HTTP), [[position-service]] (REST/HTTP), [[trade-service]] (REST/HTTP), [[reference-data]] (REST/HTTP), [[people-service]] (REST/HTTP), [[trade-feed]] (WebSocket — subscribe to live updates)

## Sources

- Code: https://github.com/finos/traderX/tree/main/web-front-end
- Last synced: 2026-04-01
