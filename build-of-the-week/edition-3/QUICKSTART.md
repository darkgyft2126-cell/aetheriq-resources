# Build of the Week — Edition 3: Alibaba Open Code Review

An AI code review CLI that pairs deterministic pipelines with an LLM agent and writes comments at the exact line.
From alibaba/open-code-review (see the repo for full docs).

## Before you start
- You need Git 2.41 or later and Node.js / npm.
- Native mode needs one model provider you configure in the tool. Delegation mode does not: your existing coding agent runs the review with its own login.
- Run it first on a test repo or a small change, not on a release branch.

## Install
- Run: `npm install -g @alibaba-group/open-code-review`
- The `ocr` command is then available globally.

## First run (under an hour, no GPU)
1. Native mode only: run `ocr config provider` and pick a built-in provider or add a custom one.
2. Native mode only: run `ocr config model` and pick the model for that provider. The tool tests the connection.
3. Go to a repo with changes: `cd your-project`
4. Review your work: `ocr review` — this covers staged, unstaged, and untracked changes.
5. Read the line-level comments. Save a copy for your records: `ocr review --format json --output result.json`
6. Optional: audit whole files with no diff: `ocr scan` or `ocr scan --path internal/agent`

## No separate key? Use delegation mode
- Run `ocr delegate preview` to see the file selection and rules the pipeline picks.
- Your current coding agent (Claude Code, Codex, Cursor, and others) then does the review inside that pipeline. No OCR provider setup is needed; your agent's own subscription and limits apply.

## Watch-outs
- The review is only as good as the model you connect. Check a few comments by hand before you trust the run.
- The repo's own benchmark claims higher precision than a general-purpose agent at about one-ninth of the tokens, with lower recall by design — it favors fewer false alarms over catching everything. Those are Alibaba's figures.
- Keep API keys in the tool's provider config, not in the repo you review.

Source: https://github.com/alibaba/open-code-review
