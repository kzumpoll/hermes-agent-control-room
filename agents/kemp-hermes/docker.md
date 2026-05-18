# kemp-hermes — Runtime

Not containerized. Hermes runs as a Python venv + systemd user service. Reason: single-user VM, no isolation benefit; simpler ops.

## Service
- Unit: `/home/boxd/.config/systemd/user/hermes-gateway.service`
- Status: `hermes gateway status`
- Logs: `~/.hermes/logs/gateway.log`, `~/.hermes/logs/agent.log`, `~/.hermes/logs/errors.log`
- Linger enabled (survives logout)

## Restart
```
hermes gateway restart
# or
hermes gateway stop && hermes gateway start
```

## Foreground (for debugging)
```
hermes gateway run
```
