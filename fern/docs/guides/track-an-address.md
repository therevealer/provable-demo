---
title: Track an Address
description: Get transaction history, earnings, and activity for any Aleo address
---

## Track an Address

This guide shows you how to retrieve all activity for a specific Aleo address — 
transaction history, transitions, and earnings. This is the foundation for building 
wallets, portfolio trackers, and user dashboards.

## What you'll build

By the end of this guide you'll be able to:
- Fetch all transactions for any Aleo address
- Retrieve address earnings and rewards
- Filter transitions by address

## Prerequisites

- Basic familiarity with REST APIs
- An Aleo address to query (or use the example address below)

## Step 1 — Get transactions for an address

Fetch all confirmed transactions associated with an address:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/address/aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut/transactions
```
```javascript title="JavaScript"
const address = "aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut";
const response = await fetch(
  `https://api.provable.com/v2/mainnet/address/${address}/transactions`
);
const transactions = await response.json();
console.log(`Found ${transactions.length} transactions`);
```
</CodeBlocks>

Each transaction in the response includes:
```json
{
  "id": "at1abc...",         // Transaction ID — use to fetch full transaction details
  "type": "execute",         // "execute" for program calls, "deploy" for deployments
  "block_height": 2847291,   // Block this transaction was included in
  "timestamp": 1708901234    // When the transaction was confirmed
}
```

## Step 2 — Get address earnings

Retrieve staking rewards and proving earnings for an address:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/address/aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut/earnings
```
```javascript title="JavaScript"
const address = "aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut";
const response = await fetch(
  `https://api.provable.com/v2/mainnet/address/${address}/earnings`
);
const earnings = await response.json();
console.log(earnings);
```
</CodeBlocks>

## Step 3 — Get transitions by address

Transitions are the individual function calls within a transaction. 
Fetching transitions gives you finer-grained activity data:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/address/aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut/transitions
```
```javascript title="JavaScript"
const address = "aleo1rhgdu77ht36c05y44vl823fkwf56f9fcjfzqxn6mlemc7xujpyqs6c0lut";
const response = await fetch(
  `https://api.provable.com/v2/mainnet/address/${address}/transitions`
);
const transitions = await response.json();
```
</CodeBlocks>

<Callout intent="info">
  Transitions reveal which Leo program functions were called and with what inputs/outputs — 
  useful for building activity feeds or auditing on-chain behaviour.
</Callout>

## What's next?

<Cards>
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