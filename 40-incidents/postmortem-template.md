# Incident Postmortem Template (Cosmos Validator)

This template is used to document validator-related incidents.

The goal is not blame.
The goal is prevention and operational improvement.

---

## 1. Incident Summary

- Date:
- Chain:
- Validator Address:
- Incident Type:
  - [ ] Downtime
  - [ ] Jailed
  - [ ] Desync
  - [ ] Upgrade failure
  - [ ] Infrastructure outage
  - [ ] Other:

Short description of what happened.

---

## 2. Impact

- Total downtime:
- Blocks missed:
- Slashing occurred: Yes / No
- Delegator impact:
- Ranking impact:

---

## 3. Root Cause Analysis

What was the underlying cause?

Examples:
- RPC misconfiguration
- Disk full
- VPS outage
- Resource exhaustion (CPU/RAM)
- Network instability
- Incorrect upgrade procedure

Be precise.

---

## 4. Detection

How was the issue detected?

- Monitoring alert?
- Manual observation?
- Delegator report?
- Explorer check?

Time between occurrence and detection:

---

## 5. Resolution

What actions were taken to resolve the issue?

Step-by-step summary:

1.
2.
3.

Time to full recovery:

---

## 6. Prevention

What changes were implemented to prevent recurrence?

Examples:

- Added new monitoring threshold
- Improved alert interval
- Increased VPS resources
- Hardened firewall rules
- Updated runbook documentation

---

## 7. Lessons Learned

Operational improvements identified:

- 
- 
- 

---

## Final Rule

Every incident must result in a system improvement.