# INDILA WORLD (independent fan portal)
Static site (GitHub Pages) + Python bot (GitHub Actions + Gemini).

## Setup
1. Push to GitHub. Settings > Secrets > Actions: add `GEMINI_API_KEY`.
2. Settings > Pages > Source: GitHub Actions.
3. Settings > Actions > General > Workflow permissions: Read and write.
4. Run `hourly-bot` manually once to test.

## How it works
- Hourly: reads RSS feeds in `data/sources.json`; Gemini filters new, verifiable news; otherwise writes one editorial from a topic list (never repeats).
- Output in 4 languages in `data/news/<id>.json`; list in `data/index.json`.
- EDITORIAL/FACTS/MUSIC_HISTORY/RETROSPECTIVE publish automatically; NEWS/RUMORS are saved as `NEEDS_REVIEW` (not shown until you add them to `index.json`).
- Limits: max calls per run/day in `data/settings.json`. Check current Gemini free-tier quotas in Google AI Studio.
- External text is passed as `<material>` data, never as instructions.
Add sources by editing `data/sources.json` (type `rss`).
