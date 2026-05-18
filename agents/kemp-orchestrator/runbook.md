# kemp-orchestrator — Runbook

## "Bot not responding"
1. `boxd exec kemp-orchestrator -- tmux ls` — `cc` session running?
2. `boxd exec kemp-orchestrator -- tmux capture-pane -t cc -p -S -30` — what's on screen?
3. If auth 401 in pane: `cc-manual-oauth` from laptop.
4. Watchdog cron (*/1 * * * *) auto-respawns claude if missing; if it's stuck on a prompt (trust, TOS), send `tmux send-keys -t cc Enter` to dismiss.

## Refresh-token master role
This VM is the source-of-truth for ~/.claude/.credentials.json. Laptop's cc-refresh-token-laptop daemon polls every 15 min, runs `claude -p` here to refresh, then fans out to forks. Don't touch the creds file manually unless re-running cc-manual-oauth.

## Scripts
~/.claude/bin/ has cc-launch (hostname-aware), cc-watchdog, cc-bootstrap, cc-refresh-token, plus telegram-typing helpers. Source of truth lives in /tmp/vm-cc-scripts/ on Kemp's laptop (snapshot taken before destroy+new operations).
