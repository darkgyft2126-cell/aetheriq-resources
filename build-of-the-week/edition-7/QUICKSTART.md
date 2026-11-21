# Build of the Week — Edition 7: Research Any Topic Across the Last 30 Days

**Tool:** mvanhorn/last30days-skill — https://github.com/mvanhorn/last30days-skill
**License:** MIT
**Budget:** Under one hour
**What you get:** One grounded research brief on a topic you must decide this week, built from Reddit, X, YouTube, Hacker News, Polymarket, and the web, scored by real engagement.

## What you need

- A supported agent host: Claude Code (recommended by the project), or Codex, Cursor, Copilot, Gemini CLI, or another Agent Skills host.
- No API keys for the first run. Reddit, Hacker News, Polymarket, and GitHub work with zero config.

## Steps

1. **Install the skill.**
   - Claude Code:
     ```
     /plugin marketplace add mvanhorn/last30days-skill
     /plugin install last30days
     ```
   - Other hosts:
     ```
     npx skills add mvanhorn/last30days-skill -g
     ```
     The `-g` flag installs globally for your user. Drop it to scope the install to one project.

2. **Pick one decision topic.** Good first topics: a supplier you may switch to, a competitor, a product you may buy, or a person you will meet. One topic per run gives a cleaner brief.

3. **Run the skill.**
   ```
   /last30days <your topic>
   ```

4. **Read the brief with a critical eye.** The skill scores sources by engagement — upvotes, likes, transcripts, and market odds — not by search rank. High engagement means people care; it does not prove a claim is true.

5. **Verify before you act.** Open two of the brief's top sources yourself. Check the date, the author, and whether the claim matches the source. Do not act on a summary line you cannot trace to a source.

6. **Optional: unlock more sources.** Run the skill once and follow its setup wizard (about 30 seconds, per the README) to add X, YouTube, TikTok, arXiv, Techmeme, and more with your own keys or browser sessions.

## Notes and cautions

- Source availability depends on your credentials, installed tools, the topic, and explicit opt-ins. See the repo's CONFIGURATION.md for source requirements.
- The project states how it handles data in the README's Data handling section. Read it before you research a sensitive topic.
- Engagement is a signal, not proof. Keep the human check in step 5.

## Source

README and install instructions read on the repo page, Nov 21, 2026: https://github.com/mvanhorn/last30days-skill
