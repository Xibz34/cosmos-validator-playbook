# Cosmos Validator Playbook

Practical playbook for **Cosmos SDK** validator operations.

Maintained by **Xibz** — independent infrastructure operator focused on early-stage and VC-backed networks.

---

## What this is

A field-tested collection of checklists, runbooks, and operational notes for:

- Uptime and reliability
- Slashing risk reduction
- Key & signing safety
- Incident response (jailed, downtime, desync)
- Mainnet readiness

This is written for operators who treat validators as production infrastructure.

---

## Contents

- `00-overview/` — principles, terminology, quickstart
- `10-setup/` — server + node setup foundations
- `20-operations/` — day-2 ops, monitoring, upgrades
- `30-security/` — key management, hardening, sentries
- `40-incidents/` — postmortems & recovery patterns
- `50-runbooks/` — copy-paste runbooks (jailed fix, restart, upgrade)

---

## Disclaimer

This repository is educational. Always validate commands against your chain’s official docs before running in production.