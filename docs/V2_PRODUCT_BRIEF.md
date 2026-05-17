# V2 Product Brief

## Vision

AI News Radar is a forkable public site plus a reusable agent Skill (伯乐Skill / Scout Skill). The public-facing skill name is **伯乐Skill** in Chinese and **Scout Skill** in English. It should feel concrete and easy to use: a scout that helps choose high-signal sources worth tracking, instead of implying that the system knows everything or blindly adding every noisy feed.

## Two-Layer Product

- **Default layer**: a simple curated Signal view for ordinary AI enthusiasts.
- **Advanced layer**: custom OPML/source configuration and source health details for maintainers.

## Goal

Ordinary users should be able to browse the hosted page. Maintainers should be able to add their own sources with OPML, public generated feeds, or secret-backed optional adapters without changing the public default.

## Source Strategy

Default source priority:

1. Official RSS/Atom feeds and OPML collections.
2. Stable public JSON APIs or static pages with timestamps.
3. Curated newsletters or changelogs with public feeds.
4. Manual/custom adapters only when the source is high-signal and stable.

## Safety

- Never commit private `feeds/follow.opml`.
- Never paste secrets, tokens, cookies, browser exports, or `.env` values into code or logs.
- Keep the public repo runnable without API keys.
- Prefer official RSS/Atom/OPML sources over fragile scraping.
- Avoid account-bound social timelines as defaults.