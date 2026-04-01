# TraderX Architecture Summary

Generated: 2026-04-01

## Overview

TraderX is a FINOS sample trading application modeled using CALM 1.2. The architecture document captures the complete system topology including all services, their connections, and key operational flows.

## Counts

- **Nodes:** 14
- **Relationships:** 17
- **Flows:** 7

## Nodes

| ID | Type | Name |
|----|------|------|
| trader | actor | Trader |
| web-front-end | webclient | Web Front End |
| trade-service | service | Trade Service |
| account-service | service | Account Service |
| position-service | service | Position Service |
| trade-processor | service | Trade Processor |
| reference-data | service | Reference Data Service |
| people-service | service | People Service |
| trade-feed | service | Trade Feed |
| database | database | TraderX Database |
| ingress | network | Ingress |
| user-directory | ldap | User Directory |
| traderx-system | system | TraderX System |
| internal-bank-network | network | Internal Bank Network |

## Relationships

- 1 interacts (trader to web front end)
- 14 connects (service-to-service, service-to-database, and LDAP connections)
- 1 composed-of (TraderX system composition)
- 1 deployed-in (internal bank network deployment)

## Flows

1. **Submit Trade** — Trader submits a trade order via Web GUI through Trade Service with account and ticker validation
2. **Process Trade** — Trade Processor receives events from Trade Feed, processes trades, updates database, publishes status
3. **Load Accounts** — Trader loads account list via Account Service from database
4. **Bootstrap Blotter** — Trader loads positions and subscribes to live Trade Feed updates
5. **Manage Account** — Trader creates/updates accounts via Account Service with People Service validation
6. **Manage Account Users** — Trader associates employees with accounts via People Service and LDAP directory lookup
7. **Security Master Bootstrap** — Reference Data provides ticker symbol lookup for trade submission

## Source

Generated from knowledge entities in `knowledge/entities/services/` following CALM 1.2 specification.
