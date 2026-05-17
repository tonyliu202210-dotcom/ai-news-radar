# X API Demo Config

This guide demonstrates how to configure X (Twitter) API for the news radar.

## Configuration

Set these repository secrets / variables:

| Name | Value | Notes |
|---|---|---|
| `X_API_ENABLED` | `1` | Enable X API |
| `X_BEARER_TOKEN` | Your bearer token | From developer.x.com |
| `X_API_QUERY` | `(AI OR "artificial intelligence" OR "large language model" OR LLM) lang:en -is:retweet has:links` | Search query |
| `X_API_MAX_RESULTS` | `20` | Max results per run |
| `X_API_DAILY_POST_LIMIT` | `50` | Daily budget cap |
| `X_API_RUN_UTC_HOUR` | `14` | UTC hour to run |
| `X_API_RUN_UTC_MINUTE_MAX` | `30` | Minute window |

## Budget

- X API charges per post read: ~$0.005 per post
- Default query: 20 results × $0.005 = ~$0.10 per run
- Daily limit: 50 posts × $0.005 = ~$0.25/day

## Security Notes

- `X_BEARER_TOKEN` must be stored as a repository secret
- Never commit tokens or cookies
- Keep X API disabled unless explicitly configured

## Default Off

X API is **disabled by default**. You must explicitly set `X_API_ENABLED=1` and provide the bearer token to activate it.