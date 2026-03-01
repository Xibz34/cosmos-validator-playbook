# Chain Upgrade Process (Cosmos SDK)

Upgrades are the highest-risk operational events for validators.

A controlled and documented upgrade process is mandatory.

---

## 1. Pre-Upgrade Preparation

### Monitor Governance

- Track upgrade proposal height.
- Confirm voting outcome.
- Record scheduled upgrade height.

### Confirm Upgrade Type

- Binary-only upgrade?
- State migration?
- Parameter change?

Read official release notes carefully.

---

## 2. Pre-Upgrade Checklist

Before the upgrade height:

- Confirm node is fully synced.
- Confirm no disk space issues.
- Confirm monitoring alerts are active.
- Confirm validator key is safe.
- Backup:
  - priv_validator_key.json
  - node_key.json
  - config directory (optional)

Optional but recommended:

- Snapshot current data directory.
- Record current block height.

---

## 3. Upgrade Execution (Cosmovisor)

If using Cosmovisor:

1. Download new binary.
2. Verify checksum (if provided).
3. Place binary in correct upgrade directory.
4. Confirm permissions are correct.
5. Restart service if required.

If NOT using Cosmovisor:

1. Stop node before upgrade height.
2. Replace binary.
3. Start node after upgrade height.

---

## 4. Post-Upgrade Verification

Immediately after restart:

- Confirm service is active.
- Confirm node is producing blocks.
- Confirm not catching_up.
- Confirm no consensus errors in logs.

Check:

- Signing resumes
- No missed blocks spike
- Explorer shows validator active

---

## 5. Incident Response During Upgrade

If node fails to start:

- Check logs immediately.
- Confirm binary version.
- Confirm config compatibility.
- Verify database integrity.

If upgrade halts the chain:

- Follow official validator coordination channels.
- Do not experiment blindly.

---

## 6. Post-Upgrade Monitoring Window

For the first 100–300 blocks:

- Monitor missed blocks closely.
- Watch for unusual CPU/memory usage.
- Confirm validator ranking stability.

---

## Operational Rule

Never upgrade casually.
Treat every chain upgrade as a production deployment.