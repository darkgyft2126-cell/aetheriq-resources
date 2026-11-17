# Build of the Week — Edition 2: DeepSeek Harness

An open-source agent harness where everything is a plugin.
From deepseek-ai/deepseek-harness (see the repo for full docs).

## Before you start
- Read the repo's SAFETY.md first. The project is in developer preview.
- Expect compatibility-breaking changes between versions.
- Run it on a test machine or a test project first, not on production work.

## Install / first run
- You need Node.js installed.
- Run: `npx @deepseek-ai/dsh web`
- The Web UI starts at http://127.0.0.1:3080 by default and opens in your browser for a local launch.

## First run (under an hour, no GPU)
1. Read SAFETY.md in the repo.
2. Run the `npx` command above in a clean folder.
3. Open the Web UI at 127.0.0.1:3080.
4. Run one small, safe task end to end. Watch what the harness asks, what plugins it loads, and what it writes.
5. Stop the server and note what files it created.

## Watch-outs
- Developer preview: pin or record the version you tested; do not assume today's steps match next week's build.
- Do not point it at accounts, repos, or files you cannot afford to have changed. Test on copies first.

Source: https://github.com/deepseek-ai/deepseek-harness
