# TraderX

- **Repo:** finos/traderX
- **Status:** FINOS Sample Application
- **License:** Apache 2.0
- **Stars:** 93
- **Forks:** 125
- **Language:** TypeScript, Java, JavaScript, C#
- **Website:** https://demo.traderx.finos.org/

## Overview

TraderX is a FINOS sample trading application used as a reference implementation for demonstrating architecture concepts. It consists of 10 microservices covering the full lifecycle of trade submission, processing, and position management. TraderX serves as the primary subject for CALM architecture documents and benchmarks.

## Services

- [[database]] — Java/H2, port 18082-84, SQL database for accounts, trades, positions
- [[reference-data]] — Node.js/NestJS, port 18085, stock ticker lookup (S&P 500 CSV)
- [[trade-feed]] — Node.js/Socket.IO, port 18086, pub-sub message bus for trade events
- [[people-service]] — .NET Core, port 18089, user lookup, validates employee IDs
- [[account-service]] — Java/Spring Boot, port 18088, account CRUD, validates people
- [[position-service]] — Java/Spring Boot, port 18090, queries trades and positions per account
- [[trade-processor]] — Java/Spring Boot, port 18091, subscribes to Trade Feed, processes trades
- [[trade-service]] — Java/Spring Boot, port 18092, accepts trade orders, validates, publishes
- [[web-front-end]] — Angular + React, port 18093/94, trading GUI
- [[ingress]] — Nginx, port 8080, reverse proxy / API gateway

## Key People

- [[DovOps]] — Primary contributor
- [[TheJuanAndOnly99]] — Contributor
- [[maoo]] — FINOS, contributor
- [[rocketstack-matt]] — Contributor

## Sources

- GitHub: https://github.com/finos/traderX
- Last synced: 2026-04-01
