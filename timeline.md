# Timeline

## 2026-04-01: CLI v1.37.0 Released

- CALM CLI v1.37.0 released — includes retirement of oidc-client package in calm-hub-ui (replaced with oidc-client-ts)

## 2026-04-01: TraderX — CycloneDX SBOM Generation Added

- PR #325 merged by @jmolloy421: CycloneDX SBOM generation added across all TraderX services
- Issue #334 opened: Major migration to Spec-Driven repo model proposed by @DovOps
- Issue #331 opened: Add CALM Architecture documentation for TraderX by @jimthompson5802

## 2026-04-01: Bootstrap — Initial Knowledge Base

- Crawled finos/architecture-as-code and finos/traderX via GitHub API
- Created 10 service entities, 4 project entities, 11 contact entities
- Generated CALM 1.2 architecture document (12 nodes, 17 relationships, 7 flows)
- Registered scheduled sync jobs (github-sync daily, rss-sync daily, calm-generate weekly, audit every 3 days)
