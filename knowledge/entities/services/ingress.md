# Ingress

- **Repo:** finos/traderX
- **Directory:** ingress/
- **Tech:** Nginx
- **Port:** 8080
- **Type:** Reverse Proxy / API Gateway

## Purpose

Acts as the reverse proxy and API gateway for the TraderX environment. Routes all external traffic to the appropriate internal services, providing a single entry point for the application.

## Connections

- **Inbound:** External traffic (HTTP)
- **Outbound:** [[web-front-end]] (HTTP — proxy), [[account-service]] (HTTP — proxy), [[position-service]] (HTTP — proxy), [[trade-service]] (HTTP — proxy), [[reference-data]] (HTTP — proxy), [[people-service]] (HTTP — proxy), [[trade-feed]] (HTTP/WebSocket — proxy)

## Sources

- Code: https://github.com/finos/traderX/tree/main/ingress
- Last synced: 2026-04-01
