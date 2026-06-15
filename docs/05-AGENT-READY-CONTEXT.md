# Agent-Ready Context

TraceLayer is designed to make onchain intelligence reusable by AI systems, automation workflows, developer tools, dashboards, and reports.

Raw onchain data is often too noisy for AI systems to use safely.

An AI system should not only receive transaction hashes, logs, asset movement, or contract calls. It needs structured context that explains what is confirmed, what is not confirmed, and what evidence supports each claim.

TraceLayer calls this agent-ready context.

## Why Agent-Ready Context Matters

AI systems can summarize information quickly, but they can also produce unsupported conclusions if the input data is unclear.

For example, if an AI system receives only raw onchain activity, it may incorrectly conclude:

```txt
This wallet completed a payment flow.
This wallet used sponsored execution.
This wallet performed a swap.
This wallet used a bridge.
This wallet acted through an automated workflow.
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
* environment-level context
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
asset or token address
event log
contract call
timestamp
```

This is useful, but incomplete.

Agent-ready context turns this into a safer structure:

```txt
Observed:
An asset transfer was detected.

Evidence:
Transaction hash and transfer event reference exist.

Not confirmed:
Payment attribution is not confirmed.
Application intent is not confirmed.

Blocked:
Do not claim a specific payment flow unless supporting evidence exists.
```

This makes the output more useful and more reliable.

## Core Context Categories

TraceLayer agent-ready context can be organized into several categories.

## 1. Facts

Facts are statements supported by evidence.

Examples:

```txt
A wallet address was observed.
An asset transfer was observed.
A smart account interaction was observed.
A UserOperation-related signal was observed.
A contract interaction was observed.
A native token usage signal was observed.
```

Facts should be traceable back to evidence.

## 2. Evidence References

Evidence references explain where a fact came from.

Examples of evidence references include:

* transaction hash
* log index
* event name
* contract address
* asset transfer record
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
Payment attribution is not confirmed.
Application intent is not confirmed.
Bridge usage is not confirmed.
Swap usage is not confirmed.
Sponsored execution is not confirmed.
Automated workflow control is not confirmed.
```

This does not mean the activity never happened.

It only means TraceLayer does not have enough evidence to safely claim it.

## 4. Guardrails

Guardrails define what an AI system should not say.

For example:

```txt
Do not claim payment flow without payment attribution evidence.

Do not claim sponsored execution without wallet-specific sponsorship evidence.

Do not claim bridge usage without bridge-specific evidence.

Do not claim swap usage without swap-specific evidence.

Do not claim automated workflow control without supporting evidence.
```

Guardrails help prevent overclaiming.

## 5. Relationship Context

Onchain activity is often relational.

A wallet may interact with a smart account, factory, token contract, routing contract, infrastructure contract, application contract, or other account.

Agent-ready context should include these relationships where evidence supports them.

Examples:

```txt
wallet → smart account
wallet → asset movement
wallet → contract interaction
smart account → EntryPoint
wallet → possible action
claim → evidence reference
```

Relationship context helps AI systems understand how activity connects together.

## 6. Environment Context

Environment context describes what the surrounding network, protocol, contract, or application may support.

However, TraceLayer separates environment context from wallet-specific evidence.

The core rule is:

```txt
Environment capability is not wallet-specific evidence.
```

For example:

```txt
An environment may support a specific execution model.
A protocol may support swaps.
An application may support sponsored execution.
A bridge-like system may exist.
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
    "assetTransfer": "observed",
    "paymentAttribution": "not_confirmed",
    "sponsoredExecution": "not_confirmed"
  },
  "facts": [
    {
      "type": "asset_transfer",
      "status": "confirmed",
      "evidenceRef": "tx:0x..."
    }
  ],
  "notConfirmed": [
    {
      "claim": "payment_attribution",
      "reason": "No payment attribution or application intent evidence was found."
    },
    {
      "claim": "sponsored_execution",
      "reason": "No wallet-specific sponsorship evidence was found."
    }
  ],
  "guardrails": [
    "Do not claim payment flow without attribution evidence.",
    "Do not claim sponsored execution without wallet-specific sponsorship evidence."
  ]
}
```

This example is intentionally simple.

The important part is not the exact schema.

The important part is the separation between confirmed facts, missing evidence, and blocked claims.

## Why This Helps AI Systems

AI systems need context that is:

* structured
* reusable
* evidence-backed
* readable
* claim-safe
* consistent across outputs

TraceLayer helps by giving AI systems a safer input layer.

Instead of asking an AI system to infer meaning from raw logs, TraceLayer provides interpreted context with evidence boundaries.

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
An asset transfer was observed.

Not confirmed:
Payment attribution is not confirmed.

Blocked:
Do not describe this as a specific application flow without additional evidence.
```

This makes reports useful without overstating the data.

## Agent-Ready Does Not Mean Agent-Confirmed

TraceLayer makes an important distinction:

```txt
Agent-ready context does not mean the wallet is confirmed to be controlled by an autonomous agent.
```

Agent-ready means the data is structured so that AI systems can consume it safely.

It does not automatically prove that a wallet is controlled by automation, registered as an agent, or acting autonomously.

Wallet-specific automation or agent-control claims still require evidence.

## Summary

Agent-ready context is one of the main reasons TraceLayer exists.

TraceLayer turns raw Account Abstraction activity, asset movement, native token usage, and application-specific interactions into structured context that can be reused safely by:

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
