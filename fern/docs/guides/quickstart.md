---
title: Your First API Call
description: Make your first request to the Provable API in under 5 minutes
---

## Your First API Call

This guide walks you through making your first request to the Provable API — 
no authentication required, no setup, just a working API call in under 5 minutes.

## What you'll do

By the end of this guide you will have:
- Queried the latest block on Aleo mainnet
- Understood the response structure
- Made a follow-up request using data from the first response

## Step 1 — Choose your network

The Provable API supports two networks. Use `testnet` while developing and 
switch to `mainnet` when you're ready to go live.

| Network | Base URL |
|---|---|
| Mainnet | `https://api.provable.com/v2/mainnet` |
| Testnet | `https://api.provable.com/v2/testnet` |

For this guide we'll use **mainnet**.

## Step 2 — Get the latest block

The simplest possible request — fetch the most recently confirmed block:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/block
```
```javascript title="JavaScript"
const response = await fetch("https://api.provable.com/v2/mainnet/block");
const block = await response.json();
console.log(block);
```
```python title="Python"
import requests
response = requests.get("https://api.provable.com/v2/mainnet/block")
print(response.json())
```
</CodeBlocks>

You'll get back a block object. Here's what the key fields mean:
```json
{
  "block_hash": "ab1qgqh...",       // Unique identifier for this block
  "previous_hash": "ab1xyz...",     // Links this block to the previous one
  "header": {
    "metadata": {
      "height": 2847291,            // Block number — use this to query specific blocks
      "timestamp": 1708901234       // Unix timestamp of when this block was produced
    }
  },
  "transactions": [...]             // All transactions included in this block
}
```

## Step 3 — Query a specific block

Take the `height` from the response above and use it to fetch that exact block:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/block/2847291
```
```javascript title="JavaScript"
const height = 2847291;
const response = await fetch(`https://api.provable.com/v2/mainnet/block/${height}`);
const block = await response.json();
console.log(block);
```
</CodeBlocks>

You can also query by block hash:
```bash
curl https://api.provable.com/v2/mainnet/block/ab1qgqh...
```

## Step 4 — Get transactions from that block

Now fetch all transactions in that block:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/block/2847291/transactions
```
```javascript title="JavaScript"
const response = await fetch(
  "https://api.provable.com/v2/mainnet/block/2847291/transactions"
);
const transactions = await response.json();
console.log(`Found ${transactions.length} transactions in this block`);
```
</CodeBlocks>

## What's next?

You've made your first API calls and understand the block and transaction data model. 

<Cards>
  <Card
    title="Track an Address"
    icon="fa-regular fa-user"
    href="/guides/getting-started/track-an-address"
  />
  <Card
    title="Monitor the Network"
    icon="fa-regular fa-chart-line"
    href="/guides/getting-started/monitor-the-network"
  />
  <Card
    title="API Reference"
    icon="fa-regular fa-code"
    href="/api-reference"
  />
</Cards>