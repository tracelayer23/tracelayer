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

A transaction, event, asset transfer, native token usage, or contract interaction can prove that something happened onchain, but it does not always prove the intent or meaning behind the action.

For example:

```txt
An asset transfer can be confirmed.

But payment attribution or application intent may not be confirmed.
```

And:

```txt
An infrastructure contract may exist.

But wallet-specific usage of that infrastructure may not be confirmed.
```

Without claim safety, tools can accidentally overstate what happened.

## The Core Rule

TraceLayer follows this rule:

```txt
Environment capability is not wallet-specific evidence.
```

This means that support at the environment, protocol, contract, or application level does not automatically prove that a specific wallet used that capability.

Examples:

```txt
Native token usage does not fully explain the execution path.

A protocol supporting swaps does not prove a wallet swapped.

A bridge-like system existing in an environment does not prove a wallet bridged assets.

A payment-related transfer does not prove payment attribution.

Agent-ready infrastructure does not prove autonomous wallet control.
```

Wallet-specific claims require wallet-specific evidence.

## Claim States

TraceLayer separates claims into clear states.

## CONFIRMED

A claim is confirmed when supporting evidence exists.

Example:

```txt
An asset transfer was observed.
```

This can be confirmed when the system has evidence such as:

* transaction hash
* transfer event
* sender address
* recipient address
* asset or token contract
* amount
* timestamp

A confirmed claim should be traceable back to evidence.

## NOT_CONFIRMED

A claim is not confirmed when evidence is insufficient.

This does not prove that the activity never happened.

It only means TraceLayer does not have enough evidence to safely claim it.

Example:

```txt
Payment attribution is not confirmed.
```

This may happen when an asset transfer exists, but there is no reliable attribution, intent, application-specific evidence, or supporting context.

## BLOCKED_UNTIL_EVIDENCE_EXISTS

A claim is blocked when the system should not allow the claim unless additional evidence exists.

Example:

```txt
This wallet completed a specific application flow.
```

This should be blocked unless TraceLayer has evidence such as:

* application-specific confirmation
* supporting contract context
* supporting event context
* intent evidence
* attribution evidence
* workflow-specific evidence

Blocked claims protect downstream outputs from sounding more certain than they should.

## Examples of Unsafe Claims

The following claims are unsafe unless supported by evidence:

```txt
This wallet completed a payment flow.

This wallet used sponsored execution.

This wallet used a paymaster.

This wallet used a bundler.

This wallet performed a swap.

This wallet bridged assets.

This wallet was controlled by an automated workflow.

This wallet used a specific application flow.
```

Some of these may be true, but TraceLayer should not claim them unless evidence exists.

## Safer Alternatives

Instead of overclaiming, TraceLayer should use safer wording.

Unsafe:

```txt
This wallet completed a payment flow.
```

Safer:

```txt
An asset transfer was observed.
Payment attribution or application intent is not confirmed.
```

Unsafe:

```txt
This wallet used sponsored execution.
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
This wallet was controlled by an automated workflow.
```

Safer:

```txt
Agent-ready context can be generated for this wallet.
Wallet-specific automated control is not confirmed.
```

## Evidence References

Claim-safe intelligence needs evidence references.

An evidence reference explains why a claim exists.

Examples of evidence references include:

* transaction hash
* log index
* event name
* asset transfer record
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
Asset Transfer
```

with a note:

```txt
Payment attribution not confirmed.
```

This keeps the dashboard useful without misleading users.

## Claim Safety in Reports

Reports must be especially careful because they may be read as business or technical conclusions.

A report should clearly separate:

* observed activity
* confirmed facts
* not-confirmed claims
* blocked claims
* evidence references

Example report language:

```txt
An asset transfer was observed.

The transfer involved a known asset and wallet-level activity.

Payment attribution or application intent is not confirmed from the available evidence.
```

This is safer than claiming a full application or payment flow without proof.

## Claim Safety in AI Context

AI systems need strong guardrails.

If an AI system receives unclear onchain data, it may produce unsupported conclusions.

TraceLayer agent-ready context should include instructions such as:

```txt
Do not claim payment flow without attribution or intent evidence.

Do not claim sponsored execution without wallet-specific sponsorship evidence.

Do not claim swap usage without swap-specific evidence.

Do not claim bridge usage without bridge-specific evidence.

Do not claim automated workflow control without supporting evidence.
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
An environment, protocol, contract, or application supports something.
```

Evidence means:

```txt
A specific wallet activity supports a specific claim.
```

Examples:

```txt
Capability:
An environment supports a specific execution model.

Evidence:
A wallet-specific transaction shows evidence of that execution behavior.
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
A wallet-specific automation claim is supported by wallet-specific evidence.
```

TraceLayer keeps these separate.

## Claim Safety Policy

TraceLayer follows these policies:

```txt
1. Do not convert possibility into fact.

2. Do not treat environment support as wallet behavior.

3. Do not treat asset movement as intent.

4. Do not treat contract interaction as action meaning without context.

5. Do not treat agent-ready data as proof of autonomous control.

6. Do not hide missing evidence.

7. Always preserve evidence references when making claims.

8. Use NOT_CONFIRMED when evidence is insufficient.

9. Use BLOCKED_UNTIL_EVIDENCE_EXISTS for claims that should not be made yet.

10. Prefer safe wording over unsupported claims.
```

## Why This Makes TraceLayer Useful

Claim safety makes TraceLayer more trustworthy.

It allows the system to say useful things without pretending to know more than the data proves.

This is important for:

* reports
* AI-agent-ready context
* developer tools
* protocol research
* wallet intelligence
* asset movement interpretation
* automation workflows
* environment-specific activity analysis

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

