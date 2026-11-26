# Build of the Week — Edition 12: Firecrawl Local

**Goal:** Turn a web page into clean markdown your AI agent can read, on your own machine. No account, no API key for the local path. Under one hour.

Source project: https://github.com/firecrawl/firecrawl (AGPL-3.0). Commands below are from the repo README, read on Nov 26, 2026.

## Path A — no install (fastest first win)

You need Node.js. Run one scrape with the CLI:

```
npx -y firecrawl-cli@latest scrape https://firecrawl.dev
```

You get the page back as markdown. That is the whole first win: a page an agent can read with far fewer tokens than raw HTML.

## Path B — Firecrawl Local (everything on your machine)

You need Rust and a C compiler (on macOS: `xcode-select --install`; on Debian/Ubuntu: `build-essential`).

1. Install:

```
cargo install firecrawl-local
```

2. Scrape a page and print its markdown:

```
firecrawl-local scrape https://firecrawl.dev --markdown
```

3. Crawl a small site and save one markdown file per page (keep the limit small for the first run):

```
firecrawl-local crawl https://docs.firecrawl.dev --limit 50 --out ./pages
```

4. List every URL on a site:

```
firecrawl-local map https://firecrawl.dev
```

Notes from the README: pages that need JavaScript render in the Chrome or Chromium already on your machine; PDFs and Office documents are parsed locally too. By default, a single-page scrape that will not load locally is fetched by Firecrawl Cloud instead and marked `"source": "firecrawl-cloud"`. Set `FIRECRAWL_CLOUD=off` to keep everything on your machine.

## Path C — serve the API locally

```
firecrawl-local serve
```

This answers the Firecrawl v2 API on port 3002, so code written for Firecrawl runs against it unchanged, and local routes need no API key:

```python
from firecrawl import Firecrawl

app = Firecrawl(api_url="http://localhost:3002")

print(app.scrape("https://firecrawl.dev").markdown)
```

## Connect it to your agent

```
firecrawl-local init
```

`init` finds Claude Code, Claude Desktop, Cursor, Windsurf, Gemini CLI and Codex on your machine and adds Firecrawl Local to each one as an MCP server. It backs up every config file first. The MCP server needs Node.js 22 or newer. Restart your AI tool afterwards.

## Check your work

- The scrape output is markdown, not HTML, and contains the page's main text.
- The crawl wrote one file per page into `./pages`, at or under your limit.
- With `FIRECRAWL_CLOUD=off`, a scrape still succeeds for a static page — proof the work stayed local.
