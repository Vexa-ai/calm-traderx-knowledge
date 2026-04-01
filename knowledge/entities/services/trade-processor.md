# Trade Processor

- **Repo:** finos/traderX
- **Directory:** trade-processor/
- **Tech:** Java, Spring Boot
- **Port:** 18091
- **Type:** Event Processor

## Purpose

Subscribes to the [[trade-feed]] pub-sub engine and processes trades. Initially stores trades in the database as pending, then marks them as processed, reporting each phase change on the appropriate trade-feed topic as a notification. As trades are settled, it recalculates position changes and persists and broadcasts those changes as well.

## Connections

- **Inbound:** [[trade-feed]] (Socket.IO — subscribe to trade events)
- **Outbound:** [[database]] (JDBC — store and update trades/positions), [[trade-feed]] (Socket.IO — publish trade status updates and position changes)

## Sources

- Code: https://github.com/finos/traderX/tree/main/trade-processor
- Last synced: 2026-04-01
