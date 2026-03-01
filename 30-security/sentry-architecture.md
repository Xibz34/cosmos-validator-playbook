# Sentry Architecture (Cosmos Validators)

A sentry architecture reduces attack surface by keeping the validator node private.

Instead of exposing your validator to the public internet, you expose *sentry nodes*.
The validator communicates only with sentries.

---

## Why Sentries

Common threats against public validators:

- DDoS / bandwidth saturation
- Targeted peer spam
- Scanner traffic & exploit attempts
- Unstable peer connections causing consensus performance degradation

Sentries help by isolating the signing validator from hostile network conditions.

---

## High-level Topology

Public Internet
    |
    |  (P2P traffic)
    v
+-------------------+         +-------------------+
|   Sentry Node A   | <-----> |   Sentry Node B   |
|  public endpoint  |         |  public endpoint  |
+-------------------+         +-------------------+
          \                          /
           \                        /
            \   (restricted P2P)   /
             v                    v
                +-------------------+
                |  Validator Node   |
                |  PRIVATE / locked |
                +-------------------+

Key idea:
- Sentries are public.
- Validator is private and only peers with sentries.

---

## Access Rules (Concept)

### Validator node

Allow inbound only from:
- Sentry A IP
- Sentry B IP
- Your own admin IP (SSH)

Block everything else.

### Sentry nodes

Allow inbound from:
- Public P2P port (for peers)
- Your admin IP (SSH)

Optionally:
- Allow outbound to validator P2P port only.

---

## Operational Notes

### How many sentries?

Minimum: 2  
Recommended: 2–4

Reason:
- Redundancy
- Better peer diversity
- Better survivability under attack

### What runs where?

Validator node:
- Signs blocks
- Runs private peers only
- No public exposure

Sentry nodes:
- Accept public peer connections
- Relay traffic to validator

---

## Peer Configuration (Concept)

Common approach:

- Validator has `persistent_peers` pointing to sentries.
- Sentries have `persistent_peers` pointing to validator (and optionally to each other).
- Validator uses `addr_book_strict=true` and limited peers.

Exact settings depend on the chain/client.

---

## Monitoring Requirements

A sentry architecture is only as good as its monitoring.

Track:

- Validator missed blocks
- Validator peer count
- Sentry peer count
- P2P connectivity between sentry ↔ validator
- Resource usage (CPU/RAM/disk)

---

## Failure Modes

If a sentry goes down:
- Validator should still have at least one healthy sentry
- Public traffic impact is absorbed at the sentry layer

If validator goes down:
- Sentries can remain online, but signing stops

If both sentries go down:
- Validator becomes isolated and may miss blocks

---

## Final Rule

Sentries are a security and reliability layer.

They do not replace:
- proper key management
- upgrades discipline
- incident response
- strong monitoring