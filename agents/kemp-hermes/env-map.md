# kemp-hermes — Env map

Secrets file: `~/.hermes/.env`. Never commit. This file documents which keys it should hold; no values.

| Var | Purpose | Where to rotate |
|---|---|---|
| ANTHROPIC_TOKEN | Anthropic OAuth fallback brain (Claude Max) | Re-run cc-manual-oauth from laptop |
| SLACK_BOT_TOKEN | Slack bot user OAuth token (xoxb-) | api.slack.com app → OAuth & Permissions |
| SLACK_SIGNING_SECRET | Slack request signing | api.slack.com app → Basic Information |
| SLACK_APP_TOKEN | Slack app-level token for Socket Mode (xapp-) | api.slack.com app → Basic Information → App-Level Tokens |
| SLACK_ALLOWED_USERS | Comma-sep Slack user IDs allowed to DM Hermes | Edit .env directly |
| GITHUB_TOKEN | Fine-grained PAT for pushing to kemp-memory repo | github.com/settings/personal-access-tokens/new |

Codex CLI uses its own `~/.codex/auth.json`, refreshed via `codex login` interactively when needed (uses ChatGPT Pro sub, no API key).

Claude Code uses `~/.claude/.credentials.json`, refreshed by the laptop daemon `cc-refresh-token-laptop` every 15 min (PREFER list includes kemp-hermes since 2026-05-18).
