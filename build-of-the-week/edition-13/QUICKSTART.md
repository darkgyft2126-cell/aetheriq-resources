# Build of the Week — Edition 13: Chrome DevTools MCP

Give your coding agent a live Chrome browser it can inspect and debug. Under one hour.

## What you need
- Node.js / npx, Google Chrome, and an MCP client (Claude Code, Cursor, Copilot, etc.)

## Steps
1. Add the server to your MCP client config:
```json
{ "mcpServers": { "chrome-devtools": { "command": "npx", "args": ["-y", "chrome-devtools-mcp@latest", "--no-usage-statistics"] } } }
```
2. Restart the client and confirm the chrome-devtools tools appear.
3. Ask the agent: open your own site, list console errors, and screenshot the page.
4. Ask for a performance trace and read the top insight together.
5. Close the browser when done.

## Safety
The server exposes the browser's content to the MCP client. Use a clean Chrome profile with no personal logins or data. Commands from the repo README, read 2026-11-27: https://github.com/ChromeDevTools/chrome-devtools-mcp
