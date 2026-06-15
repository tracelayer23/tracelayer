# TraceLayer

**TraceLayer** is a claim-safe onchain intelligence layer for Account Abstraction, stablecoin activity, and AI-agent-ready data workflows.

TraceLayer converts raw onchain activity into structured, reusable, evidence-backed intelligence for dashboards, reports, APIs, and AI agents.

<p align="center">
  <img src="assets/images/tracelayer-workflow.png" alt="TraceLayer Workflow" width="100%" />
</p>

## What is TraceLayer?

TraceLayer is built to make complex onchain activity easier to understand.

It focuses on:

* Account Abstraction wallet intelligence
* UserOperation evidence
* Factory, bundler, paymaster, and EntryPoint context
* Stablecoin and token movement interpretation
* Entity profiles and relationship graphs
* Claim-safe reporting
* AI-agent-ready context APIs
* ERC-8004 agent identity, reputation, and validation evidence

TraceLayer is not only a dashboard or PDF report generator. It is designed as a reusable intelligence layer that can serve humans, developer tools, automation systems, and AI agents.

## Why TraceLayer Exists

Raw Account Abstraction data is difficult to interpret.

Wallet activity, UserOperations, paymasters, bundlers, factories, EntryPoint interactions, stablecoin movement, and agent identity signals are often fragmented across explorers, logs, indexers, and protocol-specific sources.

This makes it easy for dashboards or AI systems to overclaim unsupported activity.

TraceLayer solves this by separating:

* confirmed facts
* not-confirmed claims
* evidence references
* relationship context
* network-level capabilities
* wallet-specific behavior
* claim-safe guardrails

## Core Principle

TraceLayer follows an evidence-first rule:

```txt
Network capability is not wallet-specific evidence.
```

Examples:

```txt
USDC as a gas token does not prove sponsored gas.

App or network support for bridge/swap/send does not prove a wallet used those actions.

A token transfer does not prove merchant or ecommerce payment.

AI-agent support does not prove a wallet is a registered agent.

Wallet-specific claims require TraceLayer evidence references.
```

## TraceLayer Workflow

TraceLayer turns raw onchain signals into reusable intelligence:

```txt
Raw Onchain Activity
        ↓
TraceLayer Scanner
        ↓
Evidence & Intelligence Layer
        ↓
Structured Outputs
        ↓
Reusable Context for AI & Automation
```

The same collected data can be reused across:

* dashboards
* PDF reports
* REST APIs
* OpenAPI workflows
* AI-agent context
* automation systems
* developer tools

## AI-Agent-Ready Data Layer

TraceLayer already collects rich Account Abstraction data, including wallet activity, UserOperations, factory evidence, bundler context, paymaster context, EntryPoint interactions, actions, relationships, guardrails, and evidence references.

If this data is only used for dashboards or PDF reports, much of its value remains underused.

The Agent Context API turns existing TraceLayer intelligence into structured, reusable, AI-readable context.

<p align="center">
  <img src="assets/images/tracelayer-agent-data-layer.png" alt="TraceLayer AI Agent Data Layer" width="100%" />
</p>

## Current Capabilities

TraceLayer currently supports:

* Account Abstraction wallet context
* Entity profiles
* Relationship graph
* Human-readable actions
* Label and action classification
* Evidence references
* Confidence and claim policy
* Claim-safe guardrails
* Agent Context API
* Arc network context
* ERC-8004 agent identity, reputation, validation, and evidence endpoints

## API Surface

TraceLayer includes wallet-level context endpoints:

```txt
GET /v1/aa/wallets/{address}/context
GET /v1/aa/wallets/{address}/summary
GET /v1/aa/wallets/{address}/facts
GET /v1/aa/wallets/{address}/guardrails
GET /v1/aa/wallets/{address}/actions
GET /v1/aa/wallets/{address}/relationships
GET /v1/aa/wallets/{address}/evidence
```

TraceLayer also includes agent identity endpoints:

```txt
GET /v1/agents/{agentId}/context
GET /v1/agents/{agentId}/summary
GET /v1/agents/{agentId}/identity
GET /v1/agents/{agentId}/reputation
GET /v1/agents/{agentId}/validation
GET /v1/agents/{agentId}/evidence
```

## Claim-Safe Output

TraceLayer is designed to produce readable intelligence without overclaiming.

<p align="center">
  <img src="assets/images/tracelayer-claim-safe-output.png" alt="TraceLayer Claim Safe Output" width="100%" />
</p>

TraceLayer separates:

```txt
CONFIRMED
Evidence exists and can be referenced.

NOT_CONFIRMED
Evidence is insufficient. This does not prove the activity never happened.

BLOCKED_UNTIL_EVIDENCE_EXISTS
The system should not allow this claim until supporting evidence exists.
```

Examples of blocked claims without evidence:

* merchant payment
* ecommerce checkout attribution
* gas sponsorship
* paymaster usage
* bundler usage
* bridge usage
* swap usage
* App Kit usage

## Proof Status

Current proof commands:

```bash
npm run proof:agent-context
npm run proof:arc-network-context
npm run proof:agent-identity-pack
npm run proof:agent-identity-api
```

Current proof status:

```txt
Agent Context Proof: PASS
Arc Network Context Proof: PASS
ERC-8004 Agent Identity Pack Proof: PASS
ERC-8004 Agent Identity API Proof: PASS
```

## Documentation

* [Problem](docs/01-PROBLEM.md)
* [Why Existing Solutions Fail](docs/02-WHY-EXISTING-SOLUTIONS-FAIL.md)
* [Solution](docs/03-SOLUTION.md)
* [Architecture](docs/04-ARCHITECTURE.md)
* [Agent Context API](docs/05-AGENT-CONTEXT-API.md)
* [ERC-8004 Agent Identity](docs/06-ERC8004-AGENT-IDENTITY.md)
* [Claim Safety](docs/07-CLAIM-SAFETY.md)
* [Proofs](docs/08-PROOFS.md)
* [Roadmap](docs/09-ROADMAP.md)

## Roadmap

TraceLayer is being developed in stages:

```txt
1. Foundation
   Build the core scanner, evidence engine, and report system.

2. Intelligence Layer
   Improve entity profiles, relationships, labels, confidence, and claim policy.

3. API & Ecosystem
   Expand Agent Context API, evidence endpoints, adapters, and developer experience.

4. Scale & Adoption
   Improve performance, add more data depth, and grow ecosystem usage.
```

## Product Direction

TraceLayer turns raw Account Abstraction, stablecoin, and agent identity data into AI-readable, claim-safe intelligence context.

The goal is simple:

```txt
One data layer.
Many reusable outputs.
No unsupported claims.
```

## Status

TraceLayer is currently in active development and private-beta preparation.

The project is focused on building reliable infrastructure for onchain intelligence, evidence-backed reporting, and AI-agent-readable context.
