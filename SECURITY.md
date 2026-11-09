# Security policy

This repository installs and runs Orbs validator nodes, so a vulnerability here can
reach guardians' keys and the nodes they operate. Please report it privately.

## Reporting a vulnerability

Use GitHub's private vulnerability reporting: open the **Security** tab of this
repository and choose **Report a vulnerability**. The report is visible only to the
maintainers.

Please do **not** open a public pull request, discussion or any other public post about
a vulnerability before it is fixed.

A useful report says:

- what is affected - a file, endpoint or script, and the commit you looked at
- how to reproduce it, or why you believe it is exploitable
- what an attacker gains

**Never include a private key, mnemonic or any other live secret**, yours or anyone
else's. If a secret is involved, describe where it is exposed, not what it is.

We will acknowledge your report, keep you informed while we work on it, and credit you
when the fix is published unless you prefer otherwise.

## Scope

In scope - the code in this repository:

- the installer (`install.sh`, `scripts/`), including key generation and how keys are
  stored on the node
- control and the updater (`control/`), including how a node decides what to deploy
- the logger (`logging/`)
- the nginx configuration (`nginx/`) and the HTTP surface it exposes on port 80
- `docker-compose.yml`

Out of scope:

- vulnerabilities inside the container images the stack runs, which are built from other
  repositories - report those to the project that builds the image
- a guardian's own infrastructure, host hardening or cloud configuration
- information that is public by design: node IP addresses, RPC endpoints, node and
  guardian addresses, and the status and log endpoints a node serves
