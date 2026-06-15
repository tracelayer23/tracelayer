# Claim Safety

Claim safety is one of the core principles of TraceLayer.

TraceLayer is designed to turn raw onchain activity into useful intelligence without making claims that the evidence does not support.

The goal is simple:

```txt
No output should make a stronger claim than the evidence allows.
```

This applies to dashboards, PDF reports, REST APIs, automation workflows, developer tools, and AI-agent-ready context.

## Why Claim Safety Matters

Onchain data is public, but interpretation is not always simple.

A transaction, event, or token transfer can prove that something happened onchain, but it does not always prove the intent or business meaning behind the action.

For example:

```txt
A stablecoin transfer can be confirmed.

But merchant payment attribution may not be confirmed.
```

And:

```txt
A paymaster contract may exist.

But sponsored gas for a specific wallet may not be confirmed.
```

Without claim safety, tools can accidentally overstate what happened.

## The Core Rule

TraceLayer follows this rule:

```txt
Network capability is not wallet-specific evidence.
```

This means that support at the network, protocol, or application level does not automatically prove that a specific wallet used that capability.

Examples:

```txt
USDC as a gas token does not prove sponsored gas.

A protocol supporting swaps does not prove a wallet swapped.

A bridge existing on a network does not prove a wallet bridged.

A payment-related transfer does not prove ecommerce checkout.

AI-agent-ready infrastructure does not prove a wallet is an AI agent.
```

Wallet-specific claims require wallet-specific evidence.

## Claim States

TraceLayer separates claims into clear states.

## CONFIRMED

A claim is confirmed when supporting evidence exists.

Example:

```txt
A stablecoin transfer was observed.
```

This can be confirmed when the system has evidence such as:

* transaction hash
* token transfer event
* sender address
* recipient address
* token contract
* amount
* timestamp

A confirmed claim should be traceable back to evidence.

## NOT_CONFIRMED

A claim is not confirmed when evidence is insufficient.

This does not prove that the activity never happened.

It only means TraceLayer does not have enough evidence to safely claim it.

Example:

```txt
Merchant attribution is not confirmed.
```

This may happen when a stablecoin transfer exists, but there is no reliable merchant, checkout, invoice, or application-specific evidence.

## BLOCKED_UNTIL_EVIDENCE_EXISTS

A claim is blocked when the system should not allow the claim unless additional evidence exists.

Example:

```txt
This wallet completed an ecommerce checkout.
```

This should be blocked unless TraceLayer has evidence such as:

* merchant attribution
* checkout metadata
* invoice reference
* payment intent
* application-specific confirmation
* supporting contract or event context

Blocked claims protect downstream outputs from sounding more certain than they should.

## Examples of Unsafe Claims

The following claims are unsafe unless supported by evidence:

```txt
This wallet paid a merchant.

This wallet completed an ecommerce checkout.

This wallet used sponsored gas.

This wallet used a paymaster.

This wallet used a bundler.

This wallet performed a swap.

This wallet bridged assets.

This wallet acted as an AI agent.

This wallet used a specific application flow.
```

Some of these may be true, but TraceLayer should not claim them unless evidence exists.

## Safer Alternatives

Instead of overclaiming, TraceLayer should use safer wording.

Unsafe:

```txt
This wallet completed an ecommerce payment.
```

Safer:

```txt
A stablecoin transfer was observed.
Merchant or ecommerce attribution is not confirmed.
```

Unsafe:

```txt
This wallet used sponsored gas.
```

Safer:

```txt
Account Abstraction activity was observed.
Wallet-specific sponsorship evidence is not confirmed.
```

Unsafe:

```txt
This wallet performed a swap.
```

Safer:

```txt
A contract interaction was observed.
Swap-specific evidence is not confirmed.
```

Unsafe:

```txt
This wallet acted as an AI agent.
```

Safer:

```txt
Agent-ready context can be generated for this wallet.
Wallet-specific AI-agent identity is not confirmed.
```

## Evidence References

Claim-safe intelligence needs evidence references.

An evidence reference explains why a claim exists.

Examples of evidence references include:

* transaction hash
* log index
* event name
* token transfer record
* receipt data
* UserOperation event
* contract address
* source adapter
* timestamp

A claim without an evidence reference should not be treated as strong.

## Claim Safety in Dashboards

Dashboards should avoid showing strong labels when evidence is weak.

For example, a dashboard should not label an activity as:

```txt
Payment
```

unless the evidence supports payment interpretation.

A safer dashboard label may be:

```txt
Stablecoin Transfer
```

with a note:

```txt
Merchant attribution not confirmed.
```

This keeps the dashboard useful without misleading users.

## Claim Safety in Reports

Reports must be especially careful because they may be read as business conclusions.

A report should clearly separate:

* observed activity
* confirmed facts
* not-confirmed claims
* blocked claims
* evidence references

Example report language:

```txt
A stablecoin transfer was observed.

The transfer involved a known token contract and wallet-level activity.

Merchant or ecommerce attribution is not confirmed from the available evidence.
```

This is safer than claiming a full business payment flow without proof.

## Claim Safety in AI Context

AI systems need strong guardrails.

If an AI agent receives unclear onchain data, it may produce unsupported conclusions.

TraceLayer agent-ready context should include instructions such as:

```txt
Do not claim merchant payment without merchant attribution evidence.

Do not claim sponsored gas without wallet-specific sponsorship evidence.

Do not claim swap usage without swap-specific evidence.

Do not claim bridge usage without bridge-specific evidence.

Do not claim AI-agent identity without wallet-specific agent evidence.
```

These guardrails help AI systems produce safer outputs.

## Claim Safety in APIs

API responses should expose claim status clearly.

A structured response should separate:

```txt
confirmed
not_confirmed
blocked_until_evidence_exists
evidence_refs
guardrails
```

This allows downstream developers to build interfaces without guessing whether a claim is safe.

## Capability vs Evidence

One of the most important claim-safety distinctions is capability versus evidence.

Capability means:

```txt
The network, protocol, or application supports something.
```

Evidence means:

```txt
A specific wallet activity supports a specific claim.
```

Examples:

```txt
Capability:
A network supports stablecoin gas.

Evidence:
A wallet-specific transaction shows sponsorship evidence.
```

```txt
Capability:
A protocol supports swaps.

Evidence:
A wallet-specific interaction and event pattern confirms swap activity.
```

```txt
Capability:
A system supports agent-ready context.

Evidence:
A wallet-specific agent identity claim is supported by agent-specific evidence.
```

TraceLayer keeps these separate.

## Claim Safety Policy

TraceLayer should follow these policies:

```txt
1. Do not convert possibility into fact.

2. Do not treat network support as wallet behavior.

3. Do not treat token transfer as business intent.

4. Do not treat contract interaction as action meaning without context.

5. Do not treat AI-agent-ready data as proof of AI-agent identity.

6. Do not hide missing evidence.

7. Always preserve evidence references when making claims.

8. Use NOT_CONFIRMED when evidence is insufficient.

9. Use BLOCKED_UNTIL_EVIDENCE_EXISTS for claims that should not be made yet.

10. Prefer safe wording over flashy unsupported claims.
```

## Why This Makes TraceLayer Useful

Claim safety makes TraceLayer more trustworthy.

It allows the system to say useful things without pretending to know more than the data proves.

This is important for:

* business reports
* compliance-sensitive summaries
* AI-agent workflows
* developer tools
* protocol research
* wallet intelligence
* stablecoin activity interpretation

The value is not only in detecting activity.

The value is in explaining activity safely.

## Summary

TraceLayer claim safety exists to prevent unsupported conclusions.

The system should always ask:

```txt
What evidence exists?
What can be safely claimed?
What is not confirmed?
What should be blocked until evidence exists?
```

TraceLayer is designed to make onchain intelligence useful without making it misleading.
