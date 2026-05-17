# GPT Handoff

## Project Overview

AI News Radar is a forkable, auto-updating 24-hour AI news radar site. The core is the 伯乐Skill (Scout Skill) which helps evaluate and integrate high-signal AI/tech sources.

## Key Files

| File | Purpose |
|---|---|
| `skills/ai-news-radar/SKILL.md` | Agent skill instructions |
| `scripts/update_news.py` | Main data generation script |
| `assets/app.js` | Frontend JS |
| `assets/styles.css` | Frontend CSS |
| `index.html` | Main HTML |
| `docs/SOURCE_COVERAGE.md` | Source strategy and coverage plan |
| `feeds/follow.example.opml` | Public OPML demo |

## Common Tasks

**Add a new RSS source:**
1. Add entry to `feeds/follow.example.opml`
2. Run local test: `python scripts/update_news.py --output-dir data --window-hours 24 --rss-opml feeds/follow.example.opml`
3. Check `data/source-status.json` for health

**Add a built-in fetcher:**
1. Add `fetch_<source>(session, now)` in `scripts/update_news.py`
2. Register in task list
3. Update `docs/SOURCE_COVERAGE.md`

## Safety Rules

- Never commit private OPML, API keys, cookies, or `.env` files
- Keep public repo runnable without secrets
- Prefer RSS/Atom/OPML over fragile scraping

## Deployment

- GitHub Actions runs every 30 minutes
- Outputs to `data/*.json`
- GitHub Pages serves the static site