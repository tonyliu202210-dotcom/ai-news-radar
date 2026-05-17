# AI News Radar Skill

> 从一堆信源里选出千里马。

## 它解决什么问题

好新闻分散在各处，官方博客发一点，更新日志发一点，X 上有人提前爆料，聚合站又把同一个新闻转来转去。

**伯乐Skill只做一件事：从乱七八糟的信源里，选出值得长期追踪的千里马。**

## 在线示例

https://tonyliu202210-dotcom.github.io/ai-news-radar/

## 快速开始

如果你想让 Agent 帮你搭自己的版本，直接说：

```text
请使用伯乐Skill，先问我要信息源清单，然后帮我判断每个信源该用 RSS、OPML、公开 feed、静态页面、Jina 兜底、AgentMail 邮箱还是跳过。目标是部署一个不需要服务器、能用 GitHub Actions 自动更新的 AI 日报网站。不要把任何 API Key、cookies、token、私有邮件内容写入仓库。
```

## 支持的信息源类型

| 类型 | 推荐程度 | 说明 |
|---|---|---|
| 官方 RSS / Atom | 高 | 最稳定，优先使用 |
| OPML | 高 | 适合批量导入个人 RSS 订阅 |
| 公开 GitHub 生成 Feed | 高 | 适合 Follow Builders 这类公开数据源 |
| 公开 Newsletter 归档 | 中 | 优先用公开页面或公开 feed |
| X / Twitter | 中低 | 优先使用稳定的公开中间 feed |
| AgentMail 邮箱 | 进阶 | 适合 newsletter、产品周报；默认关闭 |

## 工作原理

伯乐Skill处理信息源时，做四步：

1. **来源分类** — 判断来源属于哪一类
2. **抓取适配** — RSS 直接解析；静态页面用 BeautifulSoup；公开 JSON 直接读取
3. **去重过滤** — 按 URL 归一化去重 + AI 相关性评分
4. **输出结构化 JSON** — 供 GitHub Pages 网页使用

不依赖 API Key，GitHub Actions 自动定时运行。