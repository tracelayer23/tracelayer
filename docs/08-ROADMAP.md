# Roadmap

TraceLayer is being developed as a staged onchain intelligence layer.

The roadmap is organized by product maturity, evidence quality, system reliability, and reusable output design.

TraceLayer development is grouped into stages:

```txt
Foundation
        ↓
Intelligence Layer
        ↓
Context Layer
        ↓
Output Layer
        ↓
Proof & Reliability
        ↓
Developer Experience
        ↓
Ecosystem Adoption
```

Each stage strengthens TraceLayer without weakening the core claim-safe principle.

## Roadmap Principle

TraceLayer follows one roadmap rule:

```txt
Build reliable evidence first.
Then expand outputs.
```

This means TraceLayer expands labels, summaries, context, and integrations only when the evidence model can support them safely.

## Stage 1: Foundation

The foundation stage focuses on building the core system.

Main goals:

* collect wallet activity
* parse onchain signals
* detect Account Abstraction-related activity
* detect token and asset movement
* preserve evidence references
* generate basic activity summaries
* avoid unsupported claims

The goal of this stage is not to classify every possible action.

The goal is to create a reliable base layer for evidence-backed intelligence.

## Stage 2: Intelligence Layer

The intelligence layer focuses on turning raw signals into safer interpretation.

Main goals:

* improve entity profiles
* improve relationship mapping
* improve action labels
* improve confidence policy
* improve claim-state separation
* distinguish confirmed facts from not-confirmed claims
* block unsupported conclusions

This stage makes TraceLayer more useful for dashboards, reports, APIs, automation workflows, developer tools, and AI-agent-ready context.

## Stage 3: Context Layer

The context layer focuses on making TraceLayer intelligence reusable.

Main goals:

* produce structured context outputs
* support agent-ready context
* make evidence references easier to consume
* improve output consistency
* support reusable summaries
* support developer-friendly data shapes
* keep claim-safe guardrails attached to outputs

TraceLayer is not designed for only one dashboard, one report, one chain, or one asset type.

It is designed as a reusable intelligence layer.

## Stage 4: Multi-Environment Context

TraceLayer is designed to understand that different networks, wallets, contracts, and applications may produce different activity patterns.

These differences can include:

* execution models
* asset flows
* native token usage
* contract standards
* account types
* infrastructure behavior
* application-specific logic
* transaction patterns

TraceLayer treats these differences as context that can be compared, separated, and verified through evidence.

The goal is to make TraceLayer flexible across different environments without forcing every activity into the same interpretation model.

## Stage 5: Output Layer

The output layer focuses on making intelligence readable by humans and usable by tools.

Main goals:

* improve dashboard summaries
* improve PDF report structure
* improve claim-safe language
* improve visual explanations
* improve export formats
* improve API-ready output
* improve automation-friendly output
* improve AI-agent-readable context output

The focus is to make TraceLayer outputs useful without making them misleading.

## Stage 6: Proof & Validation Layer

The proof and validation layer focuses on making TraceLayer more trustworthy.

Main goals:

* add reproducible proof checks
* show raw data to label transformation
* validate evidence references
* validate claim-safe rules
* test not-confirmed claim behavior
* test blocked-claim behavior
* keep proof scope clear

Proofs should show what passed without exaggerating what the system can prove.

A good proof should show the flow:

```txt
Raw data
  → Evidence
  → Entity context
  → Relationships
  → Labels
  → Claim-safe output
```

## Stage 7: Performance & Reliability

The performance and reliability stage focuses on making TraceLayer more stable.

Main goals:

* improve scan performance
* reduce unnecessary repeated scans
* improve cache behavior
* improve error handling
* improve partial-result handling
* improve large-wallet processing
* improve output consistency
* improve reliability for repeated usage

This stage is important before broader production usage.

## Stage 8: Developer Experience

The developer experience stage focuses on making TraceLayer easier to understand, use, and extend.

Main goals:

* improve documentation
* improve example outputs
* improve proof examples
* improve adapter structure
* improve integration guidance
* make outputs easier for developers to reuse
* make environment-specific behavior easier to explain safely

The goal is to make TraceLayer understandable for builders, reviewers, and future users.

## Stage 9: Ecosystem Adoption

The ecosystem adoption stage focuses on real-world usage.

Main goals:

* support more wallet examples
* support more token and asset activity examples
* support more Account Abstraction activity examples
* support more report examples
* support more developer workflows
* support more AI-agent-readable context use cases
* collect feedback from early users

This stage should grow after the core evidence and claim-safety model is reliable.

## What Will Not Be Rushed

TraceLayer should not rush:

* unsupported labels
* unverified payment attribution
* unverified gas sponsorship claims
* unverified bridge claims
* unverified swap claims
* unverified AI-agent identity claims
* noisy integrations without evidence
* production claims before reliability is ready

The system should remain useful, but cautious.

## Current Focus

TraceLayer is currently focused on:

* Account Abstraction intelligence
* token and asset movement interpretation
* evidence-backed reporting
* claim-safe outputs
* reusable context
* agent-ready data structure
* proof-oriented validation
* multi-environment activity interpretation

The current focus is to strengthen the base intelligence layer before expanding too broadly.

## Long-Term Direction

The long-term direction of TraceLayer is to become a reusable intelligence layer for onchain activity.

TraceLayer should help different users consume the same evidence-backed data through different outputs:

* dashboards
* reports
* APIs
* automation workflows
* developer tools
* AI-agent-readable context

The long-term goal is:

```txt
One evidence layer.
Many reusable outputs.
No unsupported claims.
```

## Summary

TraceLayer roadmap is stage-based and maturity-based.

The project grows by improving:

* evidence collection
* interpretation quality
* claim safety
* reusable context
* output reliability
* developer experience
* real-world adoption

TraceLayer should expand only when the evidence model can support stronger outputs safely.
