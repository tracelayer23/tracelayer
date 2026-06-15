# Agent-Ready Context

TraceLayer is designed to make onchain intelligence reusable by AI agents, automation workflows, developer tools, dashboards, and reports.

Raw onchain data is often too noisy for AI systems to use safely.

An AI agent should not only receive transaction hashes, logs, or token transfers. It needs structured context that explains what is confirmed, what is not confirmed, and what evidence supports each claim.

TraceLayer calls this agent-ready context.

## Why Agent-Ready Context Matters

AI agents can summarize information quickly, but they can also produce unsupported conclusions if the input data is unclear.

For example, if an AI system receives only raw onchain activity, it may incorrectly conclude:

```txt
This wallet completed an ecommerce payment.
This wallet used sponsored gas.
This wallet performed a swap.
This wallet used a bridge.
This wallet acted as an AI agent.
```

Those claims may sound useful, but they are unsafe unless the evidence supports them.

Agent-ready context helps prevent this problem by giving AI systems structured boundaries.

## What Agent-Ready Context Means

Agent-ready context is not just raw data.

It is structured intelligence designed to be readable by both machines and humans.

A good agent-ready context object should include:

* confirmed facts
* evidence references
* not-confirmed claims
* confidence boundaries
* wallet-specific behavior
* network-level context
* relationship context
* claim-safe guardrails
* blocked-claim rules

This allows AI systems to reason with the data without making stronger claims than the evidence supports.

## Raw Data vs Agent-Ready Context

Raw data may look like this:

```txt
transaction hash
from address
to address
token address
event log
contract call
timestamp
```

This is useful, but incomplete.

Agent-ready context turns this into a safer structure:

```txt
Observed:
A stablecoin transfer was detected.

Evidence:
Transaction hash and transfer event reference exist.

Not confirmed:
Merchant attribution is not confirmed.
Ecommerce checkout context is not confirmed.

Blocked:
Do not claim merchant payment unless supporting evidence exists.
```

This makes the output more useful and more reliable.

## Core Context Categories

TraceLayer agent-ready context can be organized into several categories.

## 1. Facts

Facts are statements supported by evidence.

Examples:

```txt
A wallet address was observed.
A token transfer was observed.
A smart account interaction was observed.
A UserOperation-related signal was observed.
A contract interaction was observed.
```

Facts should be traceable back to evidence.

## 2. Evidence References

Evidence references explain where a fact came from.

Examples of evidence references include:

* transaction hash
* log index
* event name
* contract address
* token transfer record
* UserOperation event
* receipt data
* source adapter
* timestamp

Evidence references are important because AI systems and reports should not only say what happened.

They should also preserve why the system reached that conclusion.

## 3. Not-Confirmed Claims

A not-confirmed claim is a claim that may be possible, but is not proven by the available evidence.

Examples:

```txt
Merchant payment is not confirmed.
Ecommerce checkout attribution is not confirmed.
Bridge usage is not confirmed.
Swap usage is not confirmed.
Sponsored gas is not confirmed.
AI-agent identity is not confirmed.
```

This does not mean the activity never happened.

It only means TraceLayer does not have enough evidence to safely claim it.

## 4. Guardrails

Guardrails define what an AI system should not say.

For example:

```txt
Do not claim merchant payment without merchant or checkout evidence.

Do not claim gas sponsorship without paymaster or sponsorship evidence.

Do not claim bridge usage without bridge-specific evidence.

Do not claim swap usage without swap-specific evidence.

Do not claim AI-agent identity without agent-specific evidence.
```

Guardrails help prevent overclaiming.

## 5. Relationship Context

Onchain activity is often relational.

A wallet may interact with a smart account, factory, token, router, paymaster, bundler, or protocol contract.

Agent-ready context should include these relationships where evidence supports them.

Examples:

```txt
wallet → smart account
wallet → token transfer
wallet → contract interaction
smart account → EntryPoint
wallet → possible action
claim → evidence reference
```

Relationship context helps AI systems understand how activity connects together.

## 6. Network Context

Network context describes what the network or environment may support.

However, TraceLayer separates network context from wallet-specific evidence.

The core rule is:

```txt
Network capability is not wallet-specific evidence.
```

For example:

```txt
A network may support stablecoin gas.
A protocol may support swaps.
An app may support sponsored transactions.
A bridge may exist.
```

But those facts do not prove that a specific wallet used those capabilities.

Agent-ready context must preserve this separation.

## Example Agent-Ready Context

A simplified context output could look like this:

```json
{
  "wallet": "0x...",
  "summary": {
    "accountAbstractionActivity": "observed",
    "stablecoinTransfer": "observed",
    "merchantPayment": "not_confirmed",
    "gasSponsorship": "not_confirmed"
  },
  "facts": [
    {
      "type": "stablecoin_transfer",
      "status": "confirmed",
      "evidenceRef": "tx:0x..."
    }
  ],
  "notConfirmed": [
    {
      "claim": "merchant_payment",
      "reason": "No merchant or checkout attribution evidence was found."
    },
    {
      "claim": "gas_sponsorship",
      "reason": "No wallet-specific sponsorship evidence was found."
    }
  ],
  "guardrails": [
    "Do not claim merchant payment without merchant attribution evidence.",
    "Do not claim sponsored gas without wallet-specific sponsorship evidence."
  ]
}
```

This example is intentionally simple.

The important part is not the exact schema.

The important part is the separation between confirmed facts, missing evidence, and blocked claims.

## Why This Helps AI Agents

AI agents need context that is:

* structured
* reusable
* evidence-backed
* readable
* claim-safe
* consistent across outputs

TraceLayer helps by giving AI systems a safer input layer.

Instead of asking an AI agent to infer meaning from raw logs, TraceLayer provides interpreted context with evidence boundaries.

## Why This Helps Developers

Developers can use agent-ready context to build:

* wallet intelligence interfaces
* reporting tools
* automation workflows
* monitoring systems
* developer dashboards
* AI-assisted analysis tools

Because the context is structured, developers do not need to rebuild interpretation logic for every output.

## Why This Helps Reports

Reports can reuse the same context to generate safer summaries.

For example:

```txt
Confirmed:
A stablecoin transfer was observed.

Not confirmed:
Merchant attribution is not confirmed.

Blocked:
Do not describe this as ecommerce checkout activity without additional evidence.
```

This makes reports useful without overstating the data.

## Agent-Ready Does Not Mean Agent-Confirmed

TraceLayer makes an important distinction:

```txt
Agent-ready context does not mean the wallet is confirmed to be an AI agent.
```

Agent-ready means the data is structured so that AI systems can consume it safely.

It does not automatically prove that a wallet is controlled by an AI agent, registered as an agent, or acting autonomously.

Wallet-specific agent claims still require evidence.

## Summary

Agent-ready context is one of the main reasons TraceLayer exists.

TraceLayer turns raw Account Abstraction and stablecoin activity into structured context that can be reused safely by:

* AI systems
* automation workflows
* dashboards
* reports
* REST APIs
* developer tools

The goal is simple:

```txt
Give AI systems better context.
Keep unsupported claims blocked.
Make onchain intelligence reusable.
```
