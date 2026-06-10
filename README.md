# openbot-registry

The official agent and channel registry for [OpenBot](https://github.com/meetopenbot). It defines which agents are available in the app and how they are composed into multi-agent workflows.

## Contents

**`registry.json`** is the single source of truth:

- **`agents`** — Individual agents (e.g. Claude, Firecrawl, Vercel), each with metadata and one or more `@meetopenbot/*` plugins.
- **`channels`** — Pre-built workflows that combine agents for a specific task, such as building a website, creating slides, or generating video.

## Usage

OpenBot fetches this registry at runtime. Changes merged here are reflected in the app once the updated `registry.json` is published.

## Contributing

To add or update an agent or channel, edit `registry.json` and open a pull request. Keep descriptions concise and ensure plugin IDs match published `@meetopenbot/*` packages.
