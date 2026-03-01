# Key Management (Cosmos SDK Validators)

Validator key management is the most critical part of operating a Cosmos validator.

A single mistake can result in:
- Double-sign slashing
- Permanent tombstoning
- Loss of reputation
- Loss of delegations

This document outlines operational best practices.

---

## 1. Validator Signing Key Principles

- Never run the same validator key on two machines simultaneously.
- Never restore validator keys without understanding state height alignment.
- Always verify the node is fully synced before enabling signing.
- Treat the validator key as production-critical infrastructure.

---

## 2. Recommended Architecture

### Single-Node Setup (Small Operators)

- Validator node signs directly.
- Strict monitoring in place.
- Backups stored offline.

### Sentry Architecture (Recommended)

- Validator node is private.
- Public nodes act as sentries.
- Validator only communicates with sentries.
- Firewall restricts inbound traffic.

This reduces DDoS and network exposure risks.

---

## 3. Backup Strategy

Minimum requirements:

- Encrypted offline backup of:
  - `priv_validator_key.json`
  - `node_key.json`
  - keyring (if used)

- Store in:
  - Encrypted external storage
  - Password manager (if appropriate)
  - Never in plaintext cloud drives

---

## 4. Double-Sign Prevention

Before restarting or migrating a node:

1. Confirm old node is completely stopped.
2. Confirm no residual process is running.
3. Confirm no duplicate instance exists.
4. Verify latest block height.
5. Start new node only after checks.

Double-sign = permanent slashing in most Cosmos chains.

---

## 5. Migration Checklist

When moving validator to new server:

- Stop old node
- Confirm no signing process remains
- Copy validator key securely
- Sync new node fully
- Confirm no catching_up
- Monitor closely for first 100 blocks

---

## 6. Incident Awareness

If you suspect key compromise:

- Immediately stop validator
- Assess damage
- Review logs
- Notify chain governance (if required)

Document everything.

---

## Operational Rule

Security before uptime.
Uptime before scaling.