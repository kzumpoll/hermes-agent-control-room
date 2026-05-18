# kemp-hermes — Runbook

## "Bot not responding"
1. `boxd exec kemp-hermes -- hermes gateway status` — running?
2. `boxd exec kemp-hermes -- tail -50 ~/.hermes/logs/gateway.log`
3. If no events arriving but Bolt session up → check Slack app config for "Reinstall app" banner (often shows up when scopes changed). Reinstall via api.slack.com/apps/A0B5EMLTX2L/install-on-team.
4. If auth expired → run `cc-manual-oauth` from laptop, then `boxd exec kemp-hermes -- hermes gateway restart`.

## "Memory pushes failing"
1. Check `~/.hermes/.env` has GITHUB_TOKEN set with `repo` scope.
2. `boxd exec kemp-hermes -- bash -lc 'cd ~/memory && git push origin main'` — works?
3. If 401: PAT expired, mint new one at github.com/settings/personal-access-tokens/new, swap in `~/.hermes/.env`.

## "Codex brain hits rate limit"
1. Hermes auto-falls-back to Anthropic via ANTHROPIC_TOKEN. Verify `~/.hermes/.env` has it.
2. If Anthropic also fails: `cc-manual-oauth` to mint fresh Claude OAuth, fanout fans to hermes too.

## "Stop the gateway entirely"
`boxd exec kemp-hermes -- hermes gateway stop`

## "Total rebuild (last resort)"
1. Backup ~/.hermes/.env and ~/memory (already in github).
2. `boxd destroy kemp-hermes --confirm && boxd new --name kemp-hermes --auto-suspend-timeout 0 --restart always`
3. Re-run the install: curl install.sh, push ~/.codex, push ~/.claude/.credentials.json, restore .env from backup, clone ~/memory.
4. `hermes gateway install && hermes gateway start`
