---
title: Base URL & Networks
description: Base URL structure and supported networks
---

# Base URL & Networks

## Base URL

All API requests are made to the following base URL:
```
https://api.provable.com/v2/{network}
```

Replace `{network}` with the network you want to query.

## Supported networks

| Network | Value | Description |
|---|---|---|
| Mainnet | `mainnet` | The live Aleo production network |
| Testnet | `testnet` | The Aleo test network for development |

## Example

Fetching the latest block on mainnet:
```bash
curl https://api.provable.com/v2/mainnet/block
```

Fetching the latest block on testnet:
```bash
curl https://api.provable.com/v2/testnet/block
```

<Tip>
  Always develop and test against testnet before switching to mainnet. 
  Testnet tokens have no real value and are freely available from the Aleo faucet.
</Tip>