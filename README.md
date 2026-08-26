# OpenBot registry

The canonical registry lives at `packages/openbot-registry` in the private `meetopenbot/openbot-monorepo`. This README and `registry.json` are automatically mirrored to the public `meetopenbot/openbot-registry` compatibility repository after successful `main` CI.

## Contents

**`registry.json`** is the single source of truth:

- **`agents`** — Individual agents (e.g. Claude, Firecrawl, GitHub), each with metadata and one or more `@meetopenbot/*` plugins.
- **`channels`** — Pre-built workflows that combine agents for a specific task, such as building a website or creating slides.
- **`providers`** — LLM catalog for agent model pickers **and** cloud credit billing. Each model `id` must match the upstream provider API exactly ([models.dev](https://models.dev)). Each model **must** include `pricing.inputPerMTok` and `pricing.outputPerMTok` (USD per 1M tokens). Agents that take a model declare `models.providers` (and optional `models.default` as `provider/id`); the picker is that slice of this catalog. Unknown model ids are rejected by the integrations gateway.

## Usage

OpenBot continues to fetch the public raw URL at runtime. Do not edit the public mirror directly; changes merged in the monorepo are reflected there by the registry sync workflow.

## Contributing

To add or update an agent or channel, edit this `registry.json` in the monorepo. Run `pnpm registry:validate`, keep descriptions concise, and ensure first-party plugin IDs match workspace packages.
