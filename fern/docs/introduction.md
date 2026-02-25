---
title: Introduction
description: Get started with the Provable API for the Aleo blockchain
---

## Provable API

The Provable API gives developers programmatic access to the Aleo blockchain — 
blocks, transactions, programs, staking data, DeFi metrics, and more — through 
clean RESTful endpoints.

It's the fastest way to build applications on Aleo without running your own node.

## What you can do

- **Query the chain** — fetch blocks, transactions, and state roots in real time
- **Inspect programs** — retrieve deployed Leo programs and their mapping values
- **Track addresses** — get transaction history and earnings for any Aleo address
- **Monitor the network** — access validator committee data, staking info, and prover stats
- **Build DeFi** — query TVL, token data, and circulating supply
- **Delegate proving** — submit proofs for delegated execution without running a prover

## Two API surfaces

The Provable API has two distinct sets of endpoints. Understanding the difference 
will help you pick the right one for your use case.

| | SnarkOS API | Public API |
|---|---|---|
| **What it is** | Mirrors the Aleo node RPC directly | Enhanced endpoints built on top of SnarkOS |
| **Best for** | Low-level chain queries, broadcasting transactions | Explorer data, analytics, address history |
| **Response format** | Raw on-chain data | Enriched, human-readable data |
| **Use when** | You need raw block or transaction data | You need aggregated metrics or address activity |

## Base URL
```
https://api.provable.com/v2/{network}
```

Supported networks: `mainnet`, `testnet`

## Next steps

<Cards>
  <Card
    title="Authentication"
    icon="fa-regular fa-key"
    href="/docs/authentication"
  />
  <Card
    title="Base URL & Networks"
    icon="fa-regular fa-globe"
    href="/docs/base-url"
  />
  <Card
    title="Rate Limits"
    icon="fa-regular fa-gauge"
    href="/docs/rate-limits"
  />
  <Card
    title="API Reference"
    icon="fa-regular fa-code"
    href="/api-reference"
  />
</Cards>