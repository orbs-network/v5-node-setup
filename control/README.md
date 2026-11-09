# control

The host process that keeps an Orbs validator node running and reports on it. Root's
crontab runs it once a minute through `scripts/run-control.sh poll`.

Each tick it:

- runs the updater, which applies a new commit from the branch the node follows
- checks for image drift and for components that stopped refreshing their status
- resolves the node's eth address from the on-chain topology
- writes everything it found to `.data/control/status.json`, served at
  `http://<node>/service/control/status`

What each part does, and why, is in the [repo README](../README.md#control). The
status contract for consumers is in
[STATUS_PAGE_INTEGRATION.md](../STATUS_PAGE_INTEGRATION.md).

## Developing

```bash
make install     # venv + requirements
make test        # pytest
make lint        # pylint + flake8
make typecheck   # mypy
```

CI runs `pytest` from `requirements-dev.txt` on every pull request to `main`.
