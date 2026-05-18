# kemp-hermes — Backup

## What's already backed up
- Memory vault: lives in github.com/kzumpoll/kemp-memory (private). All sessions, skills, wiki entries push automatically via kb-compile.
- Hermes config (`~/.hermes/config.yaml`): trivial to regenerate via `hermes config set`. Document the current values in env-map.md and you can rebuild.
- SOUL.md / MEMORY.md / USER.md: should be copied into kemp-memory repo monthly (todo: add to a cron).

## What's NOT backed up automatically
- `~/.hermes/.env` (secrets). Treat as: if VM dies, mint new tokens and re-add.
- `~/.hermes/sessions/` (sqlite chat history). Not critical; Slack/TG keep the source.
- `~/.codex/auth.json` — sourced from `kemp-claude-operator` via `boxd cp`, can be re-copied.

## Recovery time
End-to-end rebuild from scratch: ~30 min if scripts available, ~90 min if from memory.
