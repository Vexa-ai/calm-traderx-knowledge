# Database

- **Repo:** finos/traderX
- **Directory:** database/
- **Tech:** Java, H2
- **Port:** 18082 (TCP), 18083 (PG), 18084 (HTTP)
- **Type:** SQL Database

## Purpose

Plays the role of a standalone SQL database for the TraderX environment. Uses H2 Java-based database as a standalone server with no authentication by default. Initializes with an empty SQL schema every time it is started. Other services interact with it via SQL/JDBC drivers, so this component can be swapped out for a production RDBMS.

## Connections

- **Inbound:** [[account-service]] (JDBC), [[position-service]] (JDBC), [[trade-processor]] (JDBC)
- **Outbound:** None

## API

- Web Console: `http://localhost:18084`
- JDBC URL: `jdbc:h2:tcp://localhost:18082/traderx`
- Default credentials: `sa` / `sa`

## Sources

- Code: https://github.com/finos/traderX/tree/main/database
- Last synced: 2026-04-01
