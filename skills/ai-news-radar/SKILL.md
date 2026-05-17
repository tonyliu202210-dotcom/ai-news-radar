---
name: ai-news-radar
description: "Use when working on AI News Radar, 24 小时 AI 更新雷达, AI 更新雷达, 伯乐Skill, or Scout Skill: finding high-signal AI/tech sources, adding RSS/OPML/GitHub feeds, checking source health, updating the web UI, GitHub Actions, or GitHub Pages deployment."
---

# AI News Radar

## First Reads

When this skill triggers inside the repo, read these files first:

- `skills/ai-news-radar/README.md` for the public-facing 伯乐Skill / Scout Skill positioning.
- `README.md` for project usage and current commands.
- `docs/SOURCE_COVERAGE.md` before changing source strategy.
- `scripts/update_news.py` before changing data generation.
- `assets/app.js`, `assets/styles.css`, and `index.html` before changing the UI.

## Product Direction

Maintain a two-layer product:

- **Default layer**: a simple curated Signal view for ordinary AI enthusiasts.
- **Advanced layer**: custom OPML, source health, GitHub Actions, and maintainer controls.

## Safety Rules

- Never commit private `feeds/follow.opml`.
- Never paste secrets, tokens, cookies, browser exports, or `.env` values into code or logs.
- Keep the public repo runnable without API keys.
- Prefer official RSS/Atom/OPML sources over fragile scraping.
- Treat X API, email, WeChat, private newsletters, and cookies as optional advanced integrations.

## Add Personal Sources

When the user has installed or forked the project but does not know how to start, ask them for a source list first.

Use OPML for private customization:

```bash
cp feeds/follow.example.opml feeds/follow.opml
python scripts/update_news.py --output-dir data --window-hours 24 --rss-opml feeds/follow.opml
```

For GitHub Actions deployment, base64 encode `feeds/follow.opml` and save it as the repository secret `FOLLOW_OPML_B64`.

## Evaluate A New Source

When a user gives a source URL, first classify it:

- RSS/Atom/OPML: add privately through `feeds/follow.opml` unless it should help every public visitor.
- GitHub project with generated feeds: inspect README, workflows, output files, and raw JSON/RSS URLs.
- Official changelog or static page: add a focused fetcher only if stable.
- Newsletter: prefer public archive RSS or archive pages.

## Validate

Run local end-to-end:

```bash
pip install -r requirements.txt
python scripts/update_news.py --output-dir data --window-hours 24 --rss-opml feeds/follow.opml
python -m http.server 8080
```

Open http://localhost:8080 and confirm the Signal view works.