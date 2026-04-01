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

## Setup

How this workspace was created, step by step. Every step is a Vexa API call. An operator can reproduce this from scratch.

### Prerequisites

- A running Vexa stack (agent-api, admin-api, runtime-api, Redis, MinIO)
- Admin API token (`$ADMIN_TOKEN`)
- Internal API secret for scheduler (`$INTERNAL_SECRET`)
- A GitHub personal access token with public repo read access (`$GITHUB_TOKEN`) — for the agent to push commits and avoid rate limits

### 1. Create the Vexa user

```bash
curl -X POST http://admin-api:8001/admin/users \
  -H "Content-Type: application/json" \
  -H "X-Admin-API-Key: $ADMIN_TOKEN" \
  -d '{"email": "calm-traderx@vexa.ai", "name": "CALM TraderX Knowledge Agent"}'
```

Save the returned `id` as `$USER_ID`.

### 2. Create an API token

```bash
curl -X POST http://admin-api:8001/admin/users/$USER_ID/tokens \
  -H "X-Admin-API-Key: $ADMIN_TOKEN"
```

Save the returned `token` as `$BOT_TOKEN`.

### 3. Configure workspace and env vars

Set workspace-git config (so the workspace clones from this repo on first container start) and inject `GITHUB_TOKEN` as a per-user env var (so the agent can push commits):

```bash
curl -X PATCH http://admin-api:8001/admin/users/$USER_ID \
  -H "Content-Type: application/json" \
  -H "X-Admin-API-Key: $ADMIN_TOKEN" \
  -d '{
    "data": {
      "workspace_git": {
        "repo": "https://github.com/Vexa-ai/calm-traderx-knowledge.git",
        "branch": "main"
      },
      "env": {
        "GITHUB_TOKEN": "ghp_your_token_here"
      }
    }
  }'
```

### 4. Bootstrap the agent

Send the `[bootstrap]` message. The agent will:
- Clone this repo into `/workspace/`
- Read `.claude/CLAUDE.md`
- Register its own scheduler jobs (daily github-sync, rss-sync, weekly calm-generate, audit)
- Crawl TraderX and architecture-as-code repos via GitHub API
- Populate `knowledge/entities/` with structured entity files
- Generate `calm/traderx-architecture.json` (valid CALM 1.2)
- Commit and push everything to this repo

```bash
curl -X POST http://agent-api:8100/internal/chat \
  -H "Content-Type: application/json" \
  -d '{
    "user_id": "'$USER_ID'",
    "message": "[bootstrap]"
  }'
```

### 5. Verify

Check that the agent populated the workspace:

```bash
# List workspace files
curl "http://agent-api:8100/api/workspace/files?user_id=$USER_ID" \
  -H "X-API-Key: $BOT_TOKEN"

# Check the public repo for agent commits
gh api repos/Vexa-ai/calm-traderx-knowledge/commits --jq '.[0].commit.message'
```

After bootstrap, the scheduler runs daily syncs automatically. No further operator action needed.

### Telegram Bot Setup

The CALM Telegram bot is a separate project (`calm-telegram-bot/`). It routes FINOS users to Vexa with the right workspace config.

**Required env vars:**

| Variable | Description |
|----------|-------------|
| `CALM_TELEGRAM_BOT_TOKEN` | Telegram Bot API token (from @BotFather) |
| `AGENT_API_URL` | Vexa agent-api URL (e.g., `http://host.docker.internal:8100`) |
| `AGENT_API_TOKEN` | Service token for agent-api |
| `ADMIN_API_URL` | Vexa admin-api URL (e.g., `http://host.docker.internal:8001`) |
| `ADMIN_API_TOKEN` | Admin API key for user creation |
| `CALM_REPO_URL` | This repo URL (default: `https://github.com/Vexa-ai/calm-traderx-knowledge.git`) |
| `CALM_REPO_BRANCH` | Branch to clone (default: `main`) |

**Run:**

```bash
cd calm-telegram-bot/
docker compose up -d
```

The bot auto-creates Vexa users for each Telegram user, sets their workspace-git config to clone from this repo, and routes messages to `POST /api/chat`. It connects to Vexa over the network — no shared infrastructure.

## Contributing

This knowledge base is agent-maintained. To suggest improvements:
- Open an issue describing what knowledge is missing or incorrect
- The agent's instructions are in `.claude/CLAUDE.md` — PRs welcome for instruction improvements

## License

Content generated from public data. CALM and TraderX are Apache 2.0 licensed FINOS projects.
