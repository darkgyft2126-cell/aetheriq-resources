# Build of the Week — Edition 6: Chrome DevTools for your coding agent

**Repo:** https://github.com/ChromeDevTools/chrome-devtools-mcp
**Time:** under one hour. **You need:** Node.js LTS, a current stable Chrome, and npm.

`chrome-devtools-mcp` is an MCP server (and CLI) that lets a coding agent such as Claude, Cursor, or Copilot control and inspect a live Chrome browser: performance traces, network requests, console messages with source-mapped stack traces, and screenshots.

## Step 1 — Add the server to your MCP client

Add this block to your MCP client's server configuration:

```json
{
  "mcpServers": {
    "chrome-devtools": {
      "command": "npx",
      "args": ["-y", "chrome-devtools-mcp@latest"]
    }
  }
}
```

Using `@latest` means your client always starts the newest version.

**Privacy choice:** Google collects usage statistics (tool success rates, latency, environment information) by default. To opt out, add the flag to the args:

```json
"args": ["-y", "chrome-devtools-mcp@latest", "--no-usage-statistics"]
```

Do not skip the README's main warning: the server exposes the content of that browser instance to the MCP client. Do not use it in a browser that holds sensitive or personal data you do not want the client to see. Only Google Chrome and Chrome for Testing are officially supported.

## Step 2 — Restart the client and run the first prompt

Restart your MCP client so it loads the new server. The browser starts only when a tool needs it, not when the server connects.

Enter the README's check prompt:

```text
Check the performance of https://developers.chrome.com
```

Your client should open Chrome and record a performance trace.

## Step 3 — Run it on a page you own

Ask the agent to:

1. Open one of your own pages.
2. List the console errors and failed network requests.
3. Take a screenshot.
4. Record a second performance trace and name the largest cost it finds.

## Step 4 — Optional: use the CLI instead

```bash
npm i chrome-devtools-mcp@latest -g
chrome-devtools navigate_page 1 --url "https://developers.chrome.com"
chrome-devtools take_screenshot 1 --filePath screenshot.png
chrome-devtools stop
```

## Done when

- The performance prompt returns a trace for the test page.
- The agent lists console and network results for your own page.
- You know whether usage statistics are on or off in your configuration.

*Source for every step: the repo README, read Nov 20, 2026. Star count at reading: 58,532. License: Apache-2.0.*
