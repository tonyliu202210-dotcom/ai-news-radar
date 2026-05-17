# AI News Radar

## 24 小时 AI 更新雷达｜伯乐Skill

**伯乐Skill（Scout Skill）帮你从一堆信源里选出千里马。**

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Live-green?style=flat-square)](https://tonyliu202210-dotcom.github.io/ai-news-radar/)
[![Actions](https://img.shields.io/github/actions/workflow/status/tonyliu202210-dotcom/ai-news-radar/update-news.yml?branch=master&label=update&style=flat-square)](https://github.com/tonyliu202210-dotcom/ai-news-radar/actions/workflows/update-news.yml)
[![License](https://img.shields.io/badge/license-MIT-green.svg?style=flat-square)](LICENSE)

[在线页面](https://tonyliu202210-dotcom.github.io/ai-news-radar/) · [English](README.en.md) · [伯乐Skill](skills/ai-news-radar/README.md) · [信息源策略](docs/SOURCE_COVERAGE.md)

---

## 这是什么

AI News Radar 是一个自动更新的 24 小时 AI 更新雷达。

普通用户直接打开网页，看最近 24 小时 AI、模型、开发者工具和技术生态更新。维护者可以 fork 这个仓库，接入自己的 OPML/RSS、公开 feed、静态页面或 AgentMail 邮箱情报。

## 为什么需要伯乐Skill

好新闻分散在各处，官方博客发一点，更新日志发一点，X 上有人提前爆料，聚合站又把同一个新闻转来转去。

**伯乐Skill先替你完成第一轮判断，哪些信源是千里马，哪些是噪音。**

## 现在能做什么

- 追踪官方 AI 节点：OpenAI News、Anthropic、Google DeepMind、Google AI、Hugging Face、GitHub AI 等
- 读取高信号日报和 Newsletter 公开来源，例如 AI Breakfast
- 读取网页自带的 feed，例如 Follow Builders 的 X builders、Anthropic Engineering、Claude Blog、AI podcasts
- 同时接入多个公开聚合源，例如 AI HOT
- 支持 OPML/RSS 批量导入
- 输出 24 小时双视图，`AI强相关` 和 `全量`
- 中英双语标题和站点分组
- 兼容飞书文档，追加 WaytoAGI 开源社区最近更新日和近7日变化

## 快速开始

```bash
git clone https://github.com/tonyliu202210-dotcom/ai-news-radar.git
cd ai-news-radar
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python scripts/update_news.py --output-dir data --window-hours 24
python -m http.server 8080
```

打开 http://localhost:8080

## GitHub 自动更新

`.github/workflows/update-news.yml` 已配置好定时任务：

- 默认每 30 分钟运行一次
- 自动生成并提交 `data/*.json`
- 如果没有设置 `FOLLOW_OPML_B64`，自动使用公开示例 `feeds/follow.example.opml`
- 默认情况下不需要任何 API Key 就能跑核心流程

## 添加自定义 RSS 源

```bash
cp feeds/follow.example.opml feeds/follow.opml
# 把你的订阅源写进 feeds/follow.opml
python scripts/update_news.py --output-dir data --window-hours 24 --rss-opml feeds/follow.opml
```

## License

[MIT](LICENSE)