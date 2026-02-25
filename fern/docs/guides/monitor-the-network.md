---
title: Monitor the Network
description: Query block data, validator committee, and staking information
---

## Monitor the Network

This guide shows you how to monitor the Aleo network in real time — 
current block height, validator committee, staking data, and network metrics. 
Useful for building dashboards, alerting systems, or network explorers.

## Step 1 — Poll the latest block height

The lightest possible network check — just the current block height as an integer:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/block/height/latest
```
```javascript title="JavaScript"
// Poll every 10 seconds
setInterval(async () => {
  const response = await fetch(
    "https://api.provable.com/v2/mainnet/block/height/latest"
  );
  const height = await response.json();
  console.log(`Current block height: ${height}`);
}, 10000);
```
</CodeBlocks>

<Callout intent="info">
  Aleo produces a new block approximately every 10 seconds. 
  Polling more frequently than this will not return new data and counts against your rate limit.
</Callout>

## Step 2 — Get the current validator committee

The committee is the set of active validators participating in AleoBFT consensus. 
Query it to see who is validating, their stake, and whether they accept new delegations:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/committee/latest
```
```javascript title="JavaScript"
const response = await fetch(
  "https://api.provable.com/v2/mainnet/committee/latest"
);
const committee = await response.json();

// List all validators and their stake
Object.entries(committee.members).forEach(([address, info]) => {
  console.log(`Validator: ${address}`);
  console.log(`Stake: ${info.stake} microcredits`);
  console.log(`Open for delegation: ${info.is_open}`);
});
```
</CodeBlocks>

## Step 3 — Get network supply metrics

Query total and circulating ALEO supply:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/supply/latest/total
```
```javascript title="JavaScript"
const [total, circulating] = await Promise.all([
  fetch("https://api.provable.com/v2/mainnet/supply/latest/total").then(r => r.json()),
  fetch("https://api.provable.com/v2/mainnet/supply/latest/circulating").then(r => r.json()),
]);

console.log(`Total supply: ${total} microcredits`);
console.log(`Circulating supply: ${circulating} microcredits`);
```
</CodeBlocks>

## Step 4 — Get DeFi metrics

Query total value locked and token data across Aleo DeFi protocols:

<CodeBlocks>
```bash title="cURL"
curl https://api.provable.com/v2/mainnet/defi/total-value
```
```javascript title="JavaScript"
const response = await fetch(
  "https://api.provable.com/v2/mainnet/defi/total-value"
);
const defi = await response.json();
console.log(defi);
```
</CodeBlocks>

## What's next?

<Cards>
  <Card
    title="API Reference"
    icon="fa-regular fa-code"
    href="/api-reference"
  />
  <Card
    title="Track an Address"
    icon="fa-regular fa-user"
    href="/guides/getting-started/track-an-address"
  />
</Cards>