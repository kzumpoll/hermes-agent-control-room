# kemp-orchestrator — Inventory

## Role
Claude Code session host for the orchestrator role. Multi-repo workspace (all repos cloned into ~/Code). Talks via Telegram bot @kemp_orchestrator_bot. Refresh-token master: laptop daemon pulls fresh creds from here and fans out to forks.

## Where It Runs
- Host: kemp-orchestrator.boxd.sh
- Deployment: native, tmux session "cc" running `cc-launch` → claude with telegram plugin
- Code dir: /home/boxd/Code (workspace root, multi-repo)
- Channel: ~/.claude/channels/telegram-orchestrator/

## Messaging Integrations
- Telegram: @kemp_orchestrator_bot (token 8788573275:...)
- Slack: n/a

## Credentials
- ~/.claude/.credentials.json (Claude Max OAuth, refreshed via cc-refresh-token cron)

## Allowed Work
- Cross-repo coding (operator-ai, lifeai, within-tea, kz-workspace-docs)
- Personal stuff via @kemp_orchestrator_bot
- Refresh-token master for the fleet

## Forbidden Work
- Same as kemp-hermes (no public posts without explicit go)

## Owner
Kemp Zumpolle.
