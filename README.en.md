# English README

# AI News Radar

## 24 Hour AI Update Radar｜Scout Skill

**Scout Skill helps you find high-signal sources from a pile of feeds.**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-green?style=flat-square)](https://tonyliu202210-dotcom.github.io/ai-news-radar/)
[![Actions](https://img.shields.io/github/actions/workflow/status/tonyliu202210-dotcom/ai-news-radar/update-news.yml?branch=master&label=update&style=flat-square)](https://github.com/tonyliu202210-dotcom/ai-news-radar/actions/workflows/update-news.yml)
[![License](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](LICENSE)

[Live Page](https://tonyliu202210-dotcom.github.io/ai-news-radar/) · [中文](README.md) · [Scout Skill](skills/ai-news-radar/README.md)

---

## What Is This

AI News Radar is an auto-updating 24-hour AI update radar.

普通用户直接打开网页，看最近 24 小时 AI、模型、开发者工具和技术生态更新。维护者可以 fork 这个仓库，接入自己的 OPML/RSS、公开 feed、静态页面或 AgentMail 邮箱情报。

## Quick Start

```bash
git clone https://github.com/tonyliu202210-dotcom/ai-news-radar.git
cd ai-news-radar
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python scripts/update_news.py --output-dir data --window-hours 24
python -m http.server 8080
```

Open http://localhost:8080

## GitHub Auto Update

`.github/workflows/update-news.yml` is pre-configured:

- Runs every 30 minutes by default
- Auto-generates and commits `data/*.json`
- Without `FOLLOW_OPML_B64`, automatically uses public example `feeds/follow.example.opml`
- No API Key required for core functionality

## License

[MIT](LICENSE)