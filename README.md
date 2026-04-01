# CALM TraderX Knowledge

A living, structured knowledge base for the [FINOS CALM](https://calm.finos.org) ecosystem — maintained by an AI agent.

## What Is This?

This repository is a [Vexa](https://vexa.ai) workspace that continuously crawls public data about the CALM (Common Architecture Language Model) project and the TraderX reference application. It extracts structured knowledge and generates valid CALM 1.2 architecture documents.

**The agent does the work.** Every file in `knowledge/` and `calm/` was created by an AI agent crawling GitHub, RSS feeds, and public documentation. No manual authoring.

## Architecture

```
This repo (workspace)
  ├── .claude/CLAUDE.md    ← Agent instructions (the brain)
  ├── knowledge/           ← Structured entities (people, projects, services)
  ├── calm/                ← Generated CALM 1.2 JSON artifacts
  ├── streams/             ← Active topics, news, blog items
  └── .state.json          ← Sync timestamps
```

**Daily automation:**
- **08:00 UTC** — GitHub sync: crawl commits, PRs, issues, releases from finos/architecture-as-code and finos/traderX
- **09:00 UTC** — RSS sync: fetch FINOS blog, extract CALM-relevant items
- **10:00 UTC Fridays** — CALM generate: rebuild architecture JSON from knowledge graph
- **Every 3 days** — Audit: check for stale content, broken links

## What's in the Knowledge Base?

- **Contacts** — Key contributors to CALM and TraderX, extracted from GitHub
- **Projects** — CALM sub-projects (CLI, Hub, Server, VSCode, AI integration)
- **Services** — TraderX microservices with connection maps and tech stacks
- **CALM Artifacts** — Valid CALM 1.2 JSON architecture document for TraderX
- **Streams** — Recent blog posts, releases, notable PRs

## Using This Knowledge Base

### Via Telegram Bot

Message the CALM Knowledge Bot on Telegram. Your workspace is cloned from this repo, and the agent answers your questions grounded in the knowledge base.

### Clone and Chat

Clone this repo as a Vexa workspace. The CLAUDE.md teaches the agent everything about CALM and TraderX.

The agent automatically pulls upstream updates on each session:
- `knowledge/` and `calm/` update from this repo
- Your `soul.md` and `notes.md` are preserved (your personal context)

## Data Sources

All data is from public sources:
- GitHub API (public repos: finos/architecture-as-code, finos/traderX)
- FINOS blog RSS feed
- calm.finos.org documentation
- Public YouTube talks about CALM

## Contributing

This knowledge base is agent-maintained. To suggest improvements:
- Open an issue describing what knowledge is missing or incorrect
- The agent's instructions are in `.claude/CLAUDE.md` — PRs welcome for instruction improvements

## License

Content generated from public data. CALM and TraderX are Apache 2.0 licensed FINOS projects.
