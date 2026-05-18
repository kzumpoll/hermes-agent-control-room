# kemp-hermes — Inventory

## Role
Hermes Agent orchestrator. Owns the personal memory vault (kemp-memory). Routes coding/research work to Claude Code sub-agents on other VMs via the `claude-code-via-vm` skill. Talks to Kemp via Slack (#personal, #operatorai, #within) and can also be addressed via SSH.

## Where It Runs
- Host: kemp-hermes.boxd.sh (boxd VM, gh-kzumpoll account)
- Deployment style: native (Python venv + systemd user service)
- Container name: n/a
- Image: n/a
- Host data dir: /home/boxd/.hermes
- Hermes install: /home/boxd/.hermes/hermes-agent
- Memory vault: /home/boxd/memory (clone of github.com/kzumpoll/kemp-memory)

## Ports
| Host port | Container port | Purpose | Exposure |
|---|---:|---|---|
| n/a | n/a | Socket Mode (outbound) | n/a — uses Slack Socket Mode, no inbound port required |

## Messaging Integrations
- Telegram: (none — orchestrator role; TG is on other VMs)
- Slack: OperatorAI workspace, channels #personal #operatorai #within. require_mention=false in those channels.
- Discord: (none)
- Other: (none)

## Credentials (see env-map.md for details, no values here)
- ANTHROPIC_TOKEN (fallback brain, from Claude Code OAuth)
- Codex CLI auth (~/.codex/auth.json) — primary brain via ChatGPT Pro
- SLACK_BOT_TOKEN, SLACK_SIGNING_SECRET, SLACK_APP_TOKEN
- SLACK_ALLOWED_USERS (U05E2RGSEKB)
- GITHUB_TOKEN (PAT, repo scope, for pushing to kemp-memory)

## Memory & Skills
- Memory provider: ~/.hermes/memories/ (MEMORY.md + USER.md) + ~/.hermes/SOUL.md
- Big memory: ~/memory (kemp-memory repo)
- Skills: ~/.hermes/skills/ — symlinks into ~/memory/skills/ for: claude-code-via-vm, kb-compile, kb-report, kb-lint, ingest-url. Plus the 123 bundled Hermes skills.
- Crons: weekly Sunday review prompt, monthly review prompt (last day), quarterly review prompt (end of quarter)
- Sessions: ~/.hermes/sessions/ (sqlite)

## Allowed Work
- Memory writes to kemp-memory repo
- Delegating coding work to other VMs via `boxd exec ... claude -p`
- Reading Notion/Gmail/Calendar through bundled Hermes skills (with Kemp's individual provider auth)
- Posting to Slack channels Kemp is in

## Forbidden Work
- Pushing anything publicly (LinkedIn, X, Threads, blog, marketing channels)
- Anything destructive without explicit "yes, do it"

## Owner
Kemp Zumpolle.
