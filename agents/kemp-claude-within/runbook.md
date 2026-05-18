# kemp-claude-within — Runbook

## "Bot not responding"
1. `boxd exec kemp-claude-within -- tmux ls` — cc session?
2. `boxd exec kemp-claude-within -- tmux capture-pane -t cc -p -S -30` — visible state?
3. If trust/TOS prompt: `tmux send-keys -t cc Enter` or "2 Enter".
4. If 401: trigger cc-manual-oauth from laptop.

## Path 1 (Claude Code subagent for Hermes)
Hermes' `claude-code-via-vm` skill expects this VM to run `claude -p` cleanly with the credentials it has. Don't touch ~/.claude/.credentials.json manually.

## Codex
Has its own auth.json. Used as a fallback or for tasks where Codex is preferred.
