# Architecture

TraceLayer is designed as a reusable onchain intelligence layer.

It sits between raw onchain data and higher-level outputs such as dashboards, reports, APIs, automation workflows, developer tools, and AI-agent-readable context.

The architecture is built around one main principle:

```txt
Collect evidence once.
Interpret it safely.
Reuse it across many outputs.
```

## High-Level Architecture

TraceLayer can be understood as a pipeline:

```txt
Raw Onchain Data
        ↓
TraceLayer Scanner
        ↓
Evidence Layer
        ↓
Entity & Relationship Layer
        ↓
Action Interpretation Layer
        ↓
Claim-Safety Layer
        ↓
Structured Outputs
```

Each layer has a separate responsibility.

This keeps the system easier to audit, easier to improve, and safer for downstream usage.

## 1. Raw Onchain Data

TraceLayer starts with raw onchain activity.

This can include:

* transactions
* receipts
* logs
* token transfers
* contract interactions
* Account Abstraction activity
* UserOperation events
* EntryPoint interactions
* smart account activity
* factory-created accounts
* bundler-related activity
* paymaster-related activity

Raw data is useful, but it is not enough by itself.

TraceLayer does not treat raw data as final intelligence.

It treats raw data as evidence input.

## 2. TraceLayer Scanner

The scanner collects activity from available onchain and indexer sources.

Its job is to gather signals that may be useful for interpretation.

The scanner looks for patterns such as:

* wallet activity
* smart account usage
* UserOperation-related activity
* contract targets
* token movement
* stablecoin transfers
* infrastructure interactions
* possible protocol relationships

The scanner should not overclaim.

At this stage, TraceLayer is collecting signals, not making final business conclusions.

## 3. Evidence Layer

The evidence layer organizes collected signals into reusable evidence references.

This layer answers questions like:

```txt
What evidence exists?
Where did the evidence come from?
Which transaction, log, or event supports it?
Can this evidence be reused in a dashboard, report, or AI context?
```

Evidence references are important because TraceLayer should not only say what it thinks happened.

It should also preserve why the system reached that interpretation.

## 4. Entity & Relationship Layer

Raw activity often involves many entities.

For Account Abstraction and stablecoin workflows, relevant entities may include:

* wallet
* smart account
* factory
* bundler
* paymaster
* EntryPoint
* token contract
* router
* bridge-like contract
* protocol contract
* application contract
* recipient address
* sender address

TraceLayer maps relationships between these entities.

Examples:

```txt
wallet → smart account
wallet → token transfer
wallet → contract interaction
smart account → EntryPoint
UserOperation → bundler context
UserOperation → paymaster context
wallet → action label
claim → evidence reference
```

This relationship layer helps explain how activity connects together.

## 5. Action Interpretation Layer

The action interpretation layer turns low-level signals into safer human-readable actions.

Examples of possible action interpretations include:

* stablecoin transfer observed
* smart account activity observed
* UserOperation-related activity observed
* contract interaction observed
* token movement observed
* possible swap-related activity
* possible bridge-related activity
* paymaster-related signal observed
* bundler-related signal observed

The key word is evidence.

TraceLayer should only mark something as confirmed when supporting evidence exists.

If evidence is not sufficient, the interpretation should remain limited.

## 6. Claim-Safety Layer

The claim-safety layer is the core protection layer.

It separates what can be safely claimed from what should remain unconfirmed.

TraceLayer uses states such as:

```txt
CONFIRMED
Evidence exists and can be referenced.

NOT_CONFIRMED
Evidence is insufficient. This does not prove the activity never happened.

BLOCKED_UNTIL_EVIDENCE_EXISTS
The system should not allow this claim until supporting evidence exists.
```

This prevents unsupported claims from leaking into dashboards, reports, APIs, and AI-agent context.

## 7. Structured Outputs

After evidence, relationships, actions, and claim safety are processed, TraceLayer can produce structured outputs.

These outputs may be used by:

* dashboards
* PDF reports
* REST APIs
* automation workflows
* developer tools
* AI-agent-ready context

The same source evidence can be reused across different output formats.

This avoids rebuilding separate interpretations for each surface.

## Architecture Diagram

A simplified TraceLayer architecture looks like this:

```txt
┌──────────────────────┐
│ Raw Onchain Activity │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ TraceLayer Scanner   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Evidence Layer       │
└──────────┬───────────┘
           │
           ▼
┌────────────────────────────┐
│ Entity & Relationship Layer│
└──────────┬─────────────────┘
           │
           ▼
┌────────────────────────────┐
│ Action Interpretation Layer│
└──────────┬─────────────────┘
           │
           ▼
┌──────────────────────┐
│ Claim-Safety Layer   │
└──────────┬───────────┘
           │
           ▼
┌──────────────────────┐
│ Structured Outputs   │
└──────────────────────┘
```

## Output Surfaces

TraceLayer is designed so one intelligence layer can support many outputs.

```txt
                         ┌──────────────┐
                         │ Dashboards   │
                         └──────────────┘
                                ▲
                                │
┌──────────────┐        ┌───────┴────────┐        ┌──────────────┐
│ PDF Reports  │◄──────►│ TraceLayer     │◄──────►│ REST APIs    │
└──────────────┘        │ Intelligence   │        └──────────────┘
                        │ Layer          │
┌──────────────┐        └───────┬────────┘       ┌──────────────┐
│ Automation   │◄───────────────┼───────────────►│ Developer    │
│ Workflows    │                │                │ Tools        │
└──────────────┘                ▼                └──────────────┘
                         ┌──────────────┐
                         │ AI Context   │
                         └──────────────┘
```

## Separation of Concerns

TraceLayer separates system responsibilities to avoid mixing raw collection, interpretation, and output formatting.

A clean separation looks like this:

```txt
Scanner
  collects raw signals

Evidence Layer
  stores what supports a claim

Entity Layer
  identifies involved actors and contracts

Relationship Layer
  maps how entities connect

Action Layer
  interprets wallet behavior

Claim-Safety Layer
  decides what can and cannot be claimed

Output Layer
  formats the result for humans, tools, or AI systems
```

This makes the system easier to extend without weakening the claim-safety model.

## Why This Architecture Matters

A single dashboard can show useful information.

A single report can explain one wallet.

A raw API can expose data.

But TraceLayer is designed to do something broader:

```txt
Create reusable, evidence-backed intelligence that can safely power many outputs.
```

This architecture helps TraceLayer avoid a common problem:

```txt
Different outputs making different claims from the same data.
```

Instead, the same evidence and claim policy can be reused consistently.

## Claim-Safe Architecture Rule

TraceLayer architecture follows this rule:

```txt
No output should make a stronger claim than the evidence supports.
```

This applies to:

* dashboard labels
* report summaries
* API responses
* automation decisions
* AI-agent context
* developer tooling

If evidence is not enough, the output should say so clearly.

## Example Flow

A simplified flow may look like this:

```txt
1. A wallet performs onchain activity.

2. TraceLayer scanner collects transactions, logs, and related signals.

3. Evidence layer stores references to the supporting data.

4. Entity layer identifies involved contracts and addresses.

5. Relationship layer maps wallet, smart account, token, and infrastructure relationships.

6. Action layer interprets what appears to have happened.

7. Claim-safety layer decides whether the claim is confirmed, not confirmed, or blocked.

8. Output layer formats the result for dashboards, reports, APIs, automation, or AI context.
```

## Summary

TraceLayer architecture is built to turn complex onchain activity into reusable intelligence.

The system is designed around:

* raw data collection
* evidence preservation
* entity context
* relationship mapping
* action interpretation
* claim-safe output
* reusable structured context

TraceLayer does not only ask:

```txt
What happened?
```

It also asks:

```txt
What can safely be claimed from the evidence?
```

That is the core purpose of the architecture.
