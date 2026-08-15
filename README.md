# OpenBot registry

The canonical registry lives at `packages/openbot-registry` in the private `meetopenbot/openbot-monorepo`. This README and `registry.json` are automatically mirrored to the public `meetopenbot/openbot-registry` compatibility repository after successful `main` CI.

## Contents

**`registry.json`** is the single source of truth:

- **`agents`** — Individual agents (e.g. Claude, Firecrawl, Vercel), each with metadata and one or more `@meetopenbot/*` plugins.
- **`channels`** — Pre-built workflows that combine agents for a specific task, such as building a website, creating slides, or generating video.
- **`providers`** — LLM provider catalogs for agent model pickers. Each model `id` must match the upstream provider API exactly. Use [models.dev](https://models.dev) as the canonical reference (e.g. `gpt-5.6-sol`, not `gpt-5-6-sol`). Each model may include a `pricing` block with `inputPerMTok` and `outputPerMTok` (USD per 1M tokens); cloud credit billing reads these at runtime from the published registry.

## Usage

OpenBot continues to fetch the public raw URL at runtime. Do not edit the public mirror directly; changes merged in the monorepo are reflected there by the registry sync workflow.

## Contributing

To add or update an agent or channel, edit this `registry.json` in the monorepo. Run `pnpm registry:validate`, keep descriptions concise, and ensure first-party plugin IDs match workspace packages.
