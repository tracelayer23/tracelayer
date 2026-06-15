# Why Existing Solutions Fail

Most onchain tools are useful, but they are not designed to solve the full claim-safe intelligence problem.

Explorers, dashboards, indexers, analytics tools, APIs, and reports usually focus on showing what happened at the transaction level.

TraceLayer focuses on a different question:

```txt
What can safely be claimed from the available evidence?
```

This matters because raw onchain activity does not always explain intent, context, relationships, or business meaning.

## Explorers Show Data, But Not Interpretation

Block explorers are good for checking transactions, logs, contracts, and token transfers.

They can answer questions like:

```txt
Was this transaction included?
Which address called a contract?
Which logs were emitted?
Which token moved?
```

But explorers usually do not explain whether a higher-level claim is safe.

For example, an explorer may show a token transfer, but it does not automatically prove:

```txt
merchant payment
ecommerce checkout
gas sponsorship
bridge usage
swap intent
AI-agent activity
```

The raw data is visible, but the interpretation is still left to the user.

## Dashboards Can Over-Simplify

Dashboards make activity easier to view, but they can also hide important uncertainty.

A dashboard might show a label like:

```txt
Payment
Swap
Bridge
Sponsored Gas
AI Agent
```

However, if the label is not tied to specific evidence, it can become misleading.

The problem is not the dashboard itself.

The problem is when the dashboard presents a conclusion without showing:

* what evidence supports it
* what evidence is missing
* whether the claim is confirmed
* whether the claim is only possible
* whether the claim should be blocked

TraceLayer is designed to keep those boundaries visible.

## Raw APIs Are Not Enough

APIs can provide transaction data, logs, balances, token transfers, and contract metadata.

But raw APIs often return low-level data without business or claim context.

For example, an API may return:

```txt
from
to
value
token
contract
event
transaction hash
```

That is useful, but it does not safely answer:

```txt
Was this a user action?
Was this a protocol action?
Was this a paymaster action?
Was this a merchant payment?
Was this wallet using an application flow?
Was this evidence strong enough for a report or AI agent?
```

A raw API gives data access.

TraceLayer adds evidence-aware interpretation.

## Labels Alone Are Risky

Labels are helpful, but labels alone are not enough.

A contract may be labeled as a router, paymaster, factory, bridge, vault, or token contract.

But a wallet-specific claim still requires wallet-specific evidence.

For example:

```txt
A known paymaster contract exists.
```

does not automatically mean:

```txt
This wallet used sponsored gas.
```

And:

```txt
A known bridge contract exists.
```

does not automatically mean:

```txt
This wallet bridged assets.
```

TraceLayer separates network-level capability from wallet-specific activity.

## AI Systems Need Guardrails

AI systems can summarize onchain data quickly, but they can also sound confident when the evidence is weak.

This is especially risky when raw onchain data is passed directly into an AI model without clear claim boundaries.

An AI system may generate statements like:

```txt
This wallet paid a merchant.
This wallet used sponsored gas.
This wallet interacted with a bridge.
This wallet acted as an AI agent.
```

Those claims may sound useful, but they are unsafe unless supported by evidence.

TraceLayer is designed to provide AI-readable context with:

* confirmed facts
* not-confirmed claims
* evidence references
* confidence boundaries
* guardrails
* blocked-claim rules

The goal is not only to make AI outputs more useful, but to make them safer.

## Reports Need Evidence, Not Assumptions

Business reports are different from raw dashboards.

A report should not only show activity. It should explain what the activity means without overstating it.

For example, a weak report might say:

```txt
This wallet completed an ecommerce payment.
```

A claim-safe report should say:

```txt
A stablecoin transfer was observed.
Merchant or ecommerce attribution is not confirmed.
```

The second version is less flashy, but it is more trustworthy.

TraceLayer is built for this kind of evidence-backed reporting.

## Existing Tools Often Optimize for One Output

Many tools are built for one main use case:

* explorers for inspection
* dashboards for visualization
* APIs for data access
* reports for presentation
* analytics tools for metrics
* AI tools for summarization

The problem is that the same evidence is often not reusable across all of these outputs.

A dashboard may have one interpretation.

A report may use another.

An AI agent may receive incomplete context.

An API may expose raw data but not claim policy.

TraceLayer is designed as a reusable intelligence layer so the same collected evidence can support multiple outputs consistently.

## Missing Separation Between Capability and Evidence

One of the biggest problems in onchain interpretation is confusing capability with evidence.

For example:

```txt
A network may support stablecoin gas.
A wallet may hold a stablecoin.
A protocol may support swaps.
A contract may be a paymaster.
A system may support AI-agent flows.
```

But none of those facts alone prove what a specific wallet did.

TraceLayer treats this distinction as a core rule:

```txt
Network capability is not wallet-specific evidence.
```

This rule prevents unsupported conclusions from being shown in dashboards, reports, APIs, and AI-agent context.

## Why TraceLayer Is Different

TraceLayer is not trying to replace explorers, dashboards, APIs, or reports.

It is designed to sit between raw onchain data and higher-level outputs.

TraceLayer adds:

* evidence collection
* entity context
* relationship mapping
* action interpretation
* claim status
* confidence policy
* reusable context
* output guardrails

This makes the same intelligence usable across dashboards, PDF reports, APIs, developer tools, automation workflows, and AI systems.

## Summary

Existing solutions fail when they turn raw data into conclusions without enough evidence context.

The core problem is not data availability.

The core problem is safe interpretation.

TraceLayer exists to make onchain intelligence:

```txt
structured
reusable
evidence-backed
claim-safe
AI-readable
```

Instead of asking only:

```txt
What happened onchain?
```

TraceLayer asks:

```txt
What can safely be claimed from the evidence?
```
