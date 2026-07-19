---
name: indexedex-overview
description: >
  High-level IndexedEx product model for agents: Standard Exchange, DETF,
  vault registry, manager. Use first when an agent must interact with IndexedEx.
---

# IndexedEx overview (agents)

## Safety
Prefer read-only first; require user confirmation for any write.

## Verify
Re-check state after any write; confirm receipts when broadcasting.


## Goal
Know which surface to call for a user intent.

## Components
| Surface | Purpose | Agent use |
|---------|---------|-----------|
| Vault Registry / Manager | Discover vaults & packages | Always discover before hardcoding vaults |
| Standard Exchange (SE) | Unified vault exchange in/out | Swaps / vault share exchange |
| Balancer V3 SE Router | Router with SE intermediation + Permit2 | Preferred multi-hop / SE-aware swaps |
| DETF | Diamond-as-share ERC20; bond; seigniorage | Mint/burn/bond/claim when live |

## User route defaults
- Prefer vault shares <-> DETF on DETF surface when live
- RateAsset mint usually: deposit into SE first, then use shares
- Do not invent approximate solvers / unsupported routes

## Backend
Default execution: **Foundry cast** (`foundry-agent`). Optional: `bankr-ops` for submit.

## Not in this plugin
Architecture dumps, forge tests, Crane style, deploy orchestration.
