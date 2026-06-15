# Problem

Onchain activity is becoming more complex.

Modern wallets are no longer only simple externally owned accounts. Account Abstraction, smart accounts, UserOperations, bundlers, paymasters, factories, EntryPoint contracts, stablecoin transfers, and application-specific contract interactions create richer behavior, but also make interpretation harder.

For humans, this activity is difficult to read directly from raw explorers and logs.

For dashboards, it is easy to show incomplete or misleading summaries.

For AI agents, it is risky to turn raw onchain data into conclusions without clear evidence boundaries.

## The Core Problem

Most onchain data is available, but it is not always easy to understand safely.

Raw transaction data often answers questions like:

```txt
What transaction happened?
Which contract was called?
Which address emitted an event?
Which token moved?
```

But it does not always safely answer higher-level questions like:

```txt
Was this a merchant payment?
Was this gas sponsored?
Was this paymaster actually used?
Was this a swap?
Was this a bridge action?
Was this wallet acting as an AI agent?
Was this activity connected to a real application flow?
```

Those higher-level claims require evidence, context, and clear separation between what is confirmed and what is only possible.

## Why This Matters

Without claim-safe interpretation, dashboards and AI systems can easily overstate what happened.

For example:

```txt
A stablecoin transfer does not automatically prove ecommerce activity.

A network supporting sponsored gas does not prove a specific wallet used sponsored gas.

A protocol supporting swaps does not prove a wallet performed a swap.

A contract interaction does not always explain the business intent behind the action.

AI-agent-related infrastructure does not prove that a wallet is a registered or active AI agent.
```

This creates a gap between raw blockchain data and reliable intelligence.

## Fragmented Data Sources

Account Abstraction and stablecoin activity are often spread across many different data sources:

* transaction receipts
* event logs
* UserOperation events
* EntryPoint interactions
* bundler activity
* paymaster context
* factory-created smart accounts
* token transfer events
* contract labels
* protocol-specific metadata
* explorer APIs
* indexer outputs

Each source can provide part of the picture, but none of them alone is always enough to make a safe claim.

## The AI Agent Problem

AI agents need structured context, not raw noise.

If an AI agent receives only raw logs or incomplete summaries, it may produce unsupported conclusions.

For AI-agent-ready onchain intelligence, the system needs to provide:

* confirmed facts
* evidence references
* not-confirmed claims
* confidence boundaries
* wallet-specific behavior
* network-level context
* claim-safe guardrails

Without these boundaries, AI systems may sound confident while making claims that the data does not actually support.

## The Business Reporting Problem

Businesses also need readable reports, not only raw transaction hashes.

However, business-facing reports must avoid unsupported claims.

For example, a report should not say:

```txt
This wallet completed an ecommerce payment.
```

unless there is evidence for merchant attribution, payment intent, or checkout context.

A safer report should say:

```txt
A stablecoin transfer was observed, but merchant or ecommerce attribution is not confirmed.
```

This difference matters because onchain intelligence should be useful without becoming misleading.

## The Infrastructure Gap

Many tools focus on one output:

* dashboards
* explorers
* raw APIs
* wallet views
* PDF reports
* protocol analytics

TraceLayer is built around a different problem:

```txt
How can the same collected onchain evidence be reused safely across dashboards, reports, APIs, automation workflows, developer tools, and AI agents?
```

To solve this, the data layer must be reusable, structured, and claim-safe from the beginning.

## TraceLayer's Problem Statement

TraceLayer exists because raw onchain activity needs a safer intelligence layer.

The goal is not only to display activity, but to explain it with evidence.

TraceLayer is focused on turning complex Account Abstraction and stablecoin activity into structured intelligence that separates:

* what is confirmed
* what is not confirmed
* what evidence supports the claim
* what should be blocked until evidence exists
* what can be reused by humans, tools, and AI agents

## Summary

The problem TraceLayer addresses is simple:

```txt
Onchain data is visible, but safe interpretation is hard.
```

TraceLayer is designed to close the gap between raw blockchain activity and reusable, evidence-backed intelligence.
