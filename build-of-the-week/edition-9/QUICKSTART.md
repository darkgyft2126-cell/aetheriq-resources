# Build of the Week — Edition 9: Scan your agent setup with safe-anything

safe-anything is a fast, open-source scanner written in Rust. It checks your code for
injection flaws, leaked secrets, and vulnerable dependencies — and it also audits the
AI agent setup around the code: MCP server configs, hooks, skills, and instruction
files for Claude Code, Codex, Cursor, Gemini, and OpenCode.

Repo: https://github.com/erkamyaman/safe-anything (MIT license)

## What you need

- A project folder on your machine, ideally one that uses an AI coding agent
  (look for `.mcp.json`, `.claude/`, hooks, or skill files).
- One of: Rust's `cargo`, or Node.js for the `npx` route. No account, no API key.

## Steps (under one hour)

1. Install it — pick one:
   - `cargo install safe-anything`
   - or skip the install: `npx safe-anything .` runs it directly.
2. Go to your project folder: `cd <your project>`
3. Run an offline scan (no package names leave your machine; the dependency
   check is skipped in this mode):
   - `safe-anything . --offline`
4. Read the findings. Each one gives the file and line, the reason, and the fix.
   The agent-setup checks flag, among others:
   - `bypassPermissions` / `--dangerously-skip-permissions`
   - MCP servers run with unpinned `npx`/`uvx`/`docker` commands
   - MCP tokens stored in plain text, remote MCP over plain `http://`
   - `curl | sh` inside hooks and skills
   - skills that read `~/.ssh` or cloud credentials
   - invisible Unicode characters hidden in instruction files
5. Fix the high and critical findings first. To silence one line on purpose,
   add a `safe-anything:ignore` comment on that line.
6. Optional: use it in CI with the GitHub Action (`erkamyaman/safe-anything@v1.0.2`,
   `fail-on: high`), or add it as an MCP server so your agent scans before it commits:
   - `claude mcp add safe-anything -- safe-anything mcp`

## Honest limits

- It matches known patterns; it does not trace data through your program.
  A clean scan means none of its 74 problems were found — not that the code is safe.
- The makers note the `code.xss-inner-html` rule is the noisiest: it fires on any
  HTML built from a variable, and most hits in local tooling are not reachable
  by an attacker. It stays on because real XSS looks the same.

Source for every claim above: the repo README, read 2026-11-23.
