# Jailed Recovery (Cosmos SDK)

## Symptoms
- Validator shows `jailed=true`
- Signing stops, ranking drops

## Safety checks (before doing anything)
- Confirm your node is fully synced
- Confirm your validator key is the correct one
- Identify why you got jailed (missed blocks vs double-sign)

## Standard recovery flow
1. Fix the root cause (RPC issues, CPU/RAM, disk, process crash, connectivity)
2. Wait for your node to be stable (no catching up)
3. Submit unjail transaction (chain-specific)

## After-action
- Add/adjust monitoring thresholds
- Document what happened (timestamp, cause, fix, prevention)