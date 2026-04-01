# Trade Feed

- **Repo:** finos/traderX
- **Directory:** trade-feed/
- **Tech:** Node.js, Socket.IO
- **Port:** 18086
- **Type:** Pub-Sub Message Bus

## Purpose

A simple pub-sub server that acts as the message bus for the TraderX environment. Supports subscription/unsubscription and event dispatching into recipient groups (Socket.IO rooms). Natively supports the web UI via WebSockets as well as server-side components. Publishes JSON objects with `{topic, payload}` structure. Also broadcasts to the `*` topic for global inspection.

## Connections

- **Inbound:** [[trade-service]] (Socket.IO — publish trade events), [[trade-processor]] (Socket.IO — subscribe to trades, publish status updates)
- **Outbound:** [[web-front-end]] (WebSocket — push live updates), [[trade-processor]] (Socket.IO — deliver trade events)

## Sources

- Code: https://github.com/finos/traderX/tree/main/trade-feed
- Last synced: 2026-04-01
