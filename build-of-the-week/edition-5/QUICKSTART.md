# Build of the Week — Edition 5: Plannotator

A local, browser-based review surface for coding agents: review the plan before the agent runs it, annotate the diff after, and send your feedback back to the agent as its next message.
From backnotprop/plannotator (see the repo for full docs).

## Before you start
- You need a coding agent Plannotator supports: Claude Code, Codex, Copilot CLI, Gemini CLI, OpenCode, Kiro, Droid, Amp, DeepSeek Harness, or Pi.
- Everything runs locally in your browser. No account, no GPU, no model download.
- Pick one real task you plan to give your agent this week. The review step is only useful on work you actually care about.

## Install

One installer covers almost every agent. It installs the `plannotator` binary, auto-detects your installed agents, and configures hooks, skills, and slash commands for each:

```
# macOS / Linux / WSL
curl -fsSL https://plannotator.ai/install.sh | bash
```

```
# Windows PowerShell
irm https://plannotator.ai/install.ps1 | iex
```

Want just the binary and nothing else? Add `--minimal` (or set `PLANNOTATOR_MINIMAL=1`) to skip every skill, hook, and per-agent config:

```
curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal
```

On Claude Code, you can also add it as a plugin: `/plugin marketplace add backnotprop/plannotator`, then `/plugin install plannotator@plannotator`, then restart Claude Code.

## First run (under an hour)
1. Give your agent a real task and let it draft a plan. The plan opens in your browser in Plannotator's review surface.
2. Annotate the lines you want changed — scope, order, risks, anything. Press Send: your comments arrive at the agent as its next turn, and it revises the plan.
3. Approve the revised plan and let the agent build. When it finishes, review the diff the same way: `/plannotator-review` for uncommitted changes, or pass a GitHub PR or GitLab MR URL.
4. Optional: run `plannotator inbox` to open the Inbox, where several agents can leave questions and reviews in one window without holding a session open while you answer.

## Watch-outs
- Sharing sends a plan as a link. Small shares live in the link itself, so anyone with the full link can read the plan. Turn sharing off with `PLANNOTATOR_SHARE=disabled` if your plans hold anything sensitive.
- The full installer wires hooks into each agent it finds. Use `--minimal` if you want to test the binary first and add the integrations one by one.
- The repo is Apache-2.0 licensed and ships releases often. Run the installer again to update the binary and commands; Claude Code plugin users also run `claude plugin marketplace update plannotator` and `claude plugin update plannotator@plannotator`.

Source: https://github.com/backnotprop/plannotator
