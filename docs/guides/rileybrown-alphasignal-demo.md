# AgentMail Digest Demo

This guide demonstrates how to configure AgentMail digest for a single-newsletter demo.

## Configuration

Set these repository secrets / variables:

| Name | Value | Notes |
|---|---|---|
| `EMAIL_DIGEST_ENABLED` | `1` | Enable AgentMail |
| `AGENTMAIL_API_KEY` | Your API key | From agentmail.to |
| `AGENTMAIL_INBOX_ID` | Your inbox ID | Format: inbox_xxxx |
| `AGENTMAIL_ALLOWED_SENDER_DOMAINS` | `alphasignal.ai` | Scope to single newsletter |
| `EMAIL_DIGEST_PUBLISH` | (optional) `1` | Publish to site |

## Demo Scope

With `AGENTMAIL_ALLOWED_SENDER_DOMAINS=alphasignal.ai`, the digest output is scoped to:
- AlphaSignal metadata only
- No raw email bodies
- No full email addresses
- No private inbox contents

## Security Notes

- `AGENTMAIL_API_KEY` and `AGENTMAIL_INBOX_ID` must be stored as repository secrets
- `data/email-digest.json` should not be committed unless `EMAIL_DIGEST_PUBLISH=1`
- Only the list-messages endpoint is called; raw endpoint is never used