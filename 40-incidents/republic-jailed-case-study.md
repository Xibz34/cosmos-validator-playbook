# Case Study: Validator Jailed Incident (Republic Testnet)

This document describes a real validator incident and the operational improvements that followed.

The purpose is transparency and system improvement.

---

## Incident Summary

- Chain: Republic (Testnet)
- Incident Type: Jailed (missed blocks)
- Environment: Single-node validator setup
- Monitoring: Basic service-level checks (no height delta monitoring at the time)

Validator became jailed after a period of missed blocks.

---

## Root Cause

Primary cause:

- RPC misconfiguration led to delayed block processing.
- Node remained technically running, but performance degraded.
- Missed block threshold exceeded before manual detection.

Key issue:

Service-level monitoring alone was insufficient.

The process was active.
Consensus performance was degraded.

---

## Detection

The issue was detected via:

- Explorer validator status check
- Followed by manual log inspection

Detection delay highlighted a monitoring gap.

---

## Resolution

Steps taken:

1. Verified node sync status.
2. Identified RPC configuration issue.
3. Restarted node after correcting configuration.
4. Confirmed full synchronization.
5. Submitted unjail transaction.
6. Monitored closely for next 200 blocks.

Validator returned to active state.

---

## Operational Improvements Implemented

After the incident:

- Added jailed status monitoring.
- Added RPC reachability checks.
- Implemented unified monitoring runner.
- Improved alert visibility via Discord webhook.
- Documented upgrade and incident procedures.

This incident directly led to the creation of the validator monitoring suite.

---

## Lessons Learned

- "Process running" does not equal "validator healthy".
- Monitoring must include consensus-level signals.
- Every incident must produce structural improvement.
- Manual checking is not a strategy.

---

## Final Takeaway

Incidents are inevitable.

Unimproved systems are optional.