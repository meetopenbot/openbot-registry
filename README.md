# openbot-registry

The official agent and channel registry for [OpenBot](https://github.com/meetopenbot). It defines which agents are available in the app and how they are composed into multi-agent workflows.

## Contents

**`registry.json`** is the single source of truth:

- **`agents`** — Individual agents (e.g. Claude, Firecrawl, Vercel), each with metadata and one or more `@meetopenbot/*` plugins.
- **`channels`** — Pre-built workflows that combine agents for a specific task, such as building a website, creating slides, or generating video.
- **`providers`** — LLM provider catalogs for agent model pickers. Each model `id` must match the upstream provider API exactly. Use [models.dev](https://models.dev) as the canonical reference (e.g. `gpt-5.6-sol`, not `gpt-5-6-sol`). Each model may include a `pricing` block with `inputPerMTok` and `outputPerMTok` (USD per 1M tokens); cloud credit billing reads these at runtime from the published registry.

## Usage

OpenBot fetches this registry at runtime. Changes merged here are reflected in the app once the updated `registry.json` is published.

## Contributing

To add or update an agent or channel, edit `registry.json` and open a pull request. Keep descriptions concise and ensure plugin IDs match published `@meetopenbot/*` packages.
