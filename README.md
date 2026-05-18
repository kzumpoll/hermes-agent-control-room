# kemp-agent-control-room

Side control plane for Kemp's agent fleet. Forked from [shannhk/hermes-agent-control-room](https://github.com/shannhk/hermes-agent-control-room) and customized.

This repo is NOT an agent. It documents and governs the fleet. Live runtime is on the boxd VMs themselves.

## Fleet

| Agent | Host | Role | Bot | Repo focus |
|---|---|---|---|---|
| [kemp-hermes](agents/kemp-hermes/inventory.md) | kemp-hermes.boxd.sh | Hermes orchestrator + memory | Slack #personal #operatorai #within | All (via memory vault) |
| [kemp-orchestrator](agents/kemp-orchestrator/inventory.md) | kemp-orchestrator.boxd.sh | Claude Code multi-repo + refresh-token master | @kemp_orchestrator_bot (TG) | ~/Code (all) |
| [kemp-claude-operator](agents/kemp-claude-operator/inventory.md) | kemp-claude-operator.boxd.sh | Claude Code OperatorAI focus | @Kemp_operatorai_bot (TG) | operator-ai |
| [kemp-claude-within](agents/kemp-claude-within/inventory.md) | kemp-claude-within.boxd.sh | Claude Code Within focus | @Kemp_Within_Bot (TG) | within-tea |

## Three ways to interact
- **Control path** → this repo (add agents, rotate keys, update docs, debug setup)
- **Direct path** → talk to a specialist agent in its channel/bot
- **Orchestrated path** → Slack #personal to Hermes, Hermes delegates

## Conventions
- Storage split: `/home/boxd/...` = live runtime; this repo = governance + no secrets
- Per-agent files: `inventory.md`, `runbook.md`. Add `docker.md`, `env-map.md`, `backup.md` as needed.
- Brand voice rules in [SOUL.md (live on kemp-hermes)](https://github.com/kzumpoll/kemp-memory/blob/main/CLAUDE.md) — applies to all outbound.

## Upstream
Pull updates: `git fetch upstream && git rebase upstream/main`. Skill templates worth tracking.
