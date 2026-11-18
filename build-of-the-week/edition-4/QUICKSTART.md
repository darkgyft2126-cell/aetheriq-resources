# Build of the Week — Edition 4: last30days-skill

An agent skill that researches any topic across Reddit, X, YouTube, Hacker News, Polymarket, and the web — scored by real engagement — and synthesizes one grounded brief.
From mvanhorn/last30days-skill (see the repo for full docs).

## Before you start
- You need a coding agent that supports Agent Skills or plugins: Claude Code (recommended), or Codex, Cursor, Copilot, Gemini CLI, or another of the 50+ supported hosts.
- No API keys are needed for the first run. Reddit, Hacker News, Polymarket, and GitHub work with zero config.
- Pick one real topic you need this week — a person, a company, or a product question. The brief is only useful if the topic is.

## Install

Claude Code (auto-updates via the marketplace):

```
/plugin marketplace add mvanhorn/last30days-skill
/plugin install last30days
```

Other Agent Skills hosts:

```
npx skills add mvanhorn/last30days-skill -g
```

Drop `-g` to scope the install to one project instead of your whole user account.

## First run (under an hour, no GPU)
1. Run the skill with your topic: `/last30days <your topic>`
2. Read the brief. Note which sources carried the signal — upvotes, likes, transcripts, and market odds are shown next to the claims they support.
3. Run it once more in discovery mode to see what is rising in your field: ask `/last30days what's exploding in AI agents?` (or your own field). You get 5–10 velocity-ranked topics with a ready-to-run follow-up for each.
4. Optional, about 30 seconds: run the first-run setup wizard to unlock X, YouTube, TikTok, arXiv, Techmeme, and more with your own keys and browser sessions.

## Watch-outs
- The ranking is social relevancy, not editorial review: a high-upvote post is a strong signal of attention, not proof that a claim is true. Check any fact you plan to act on at its source.
- Sources that need your keys or a logged-in browser session use your accounts and your quotas. Add only the sources you need.
- The repo is MIT licensed. Star counts and source lists in the README change often; the skill spec in `skills/last30days/SKILL.md` is the source of truth for current behavior.

Source: https://github.com/mvanhorn/last30days-skill
