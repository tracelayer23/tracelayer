# Proofs

TraceLayer uses proof-oriented development to show how raw onchain data becomes structured, claim-safe intelligence.

The goal is not only to show that a script passed.

The goal is to show the flow:

```txt
Raw onchain data
        ↓
Parsed evidence
        ↓
Entity and relationship context
        ↓
Action labels
        ↓
Claim-safe output
```

TraceLayer proofs are designed to validate that labels and summaries are supported by evidence, not assumptions.

## Proof Flow

A simplified proof flow looks like this:

```txt
1. Collect raw wallet activity
2. Parse transactions, logs, transfers, and Account Abstraction signals
3. Extract evidence references
4. Identify involved entities
5. Map relationships
6. Generate action labels
7. Apply claim-safety rules
8. Produce structured output
```

## Example: Raw Data Input

A raw onchain record may start as low-level data:

```txt
txHash: 0x...
from: 0x...
to: 0x...
contract: 0x...
event: Transfer
token: USDC
amount: 1.00
```

At this stage, TraceLayer does not treat the activity as a merchant payment, swap, bridge, or sponsored transaction.

It is only raw evidence.

## Example: Parsed Evidence

TraceLayer converts the raw record into evidence references:

```txt
Evidence detected:
- transaction hash
- token transfer event
- sender address
- recipient address
- token contract
- amount
- timestamp
```

Example terminal-style output:

```txt
[scanner] wallet activity collected
[parser] token transfer detected
[evidence] transfer evidence reference created
[evidence] tx hash attached
[evidence] token contract attached
```

This means TraceLayer can confirm that a token transfer happened.

It does not mean TraceLayer can confirm the business purpose of the transfer.

## Example: Entity Context

TraceLayer then identifies entities involved in the activity.

```txt
Entity context:
- wallet address observed
- token contract observed
- recipient address observed
- contract interaction observed
```

Example terminal-style output:

```txt
[entity] wallet detected
[entity] token contract detected
[entity] recipient detected
[entity] contract target detected
```

Entity detection helps explain who or what was involved.

## Example: Relationship Mapping

TraceLayer maps relationships between observed entities.

```txt
Relationships:
wallet → token transfer
wallet → recipient
wallet → contract interaction
claim → evidence reference
```

Example terminal-style output:

```txt
[relationship] wallet -> token_transfer
[relationship] wallet -> recipient
[relationship] token_transfer -> evidence_ref
[relationship] claim -> evidence_ref
```

This relationship layer helps explain how raw activity connects together.

## Example: Label Generation

After evidence and relationships are processed, TraceLayer can generate safe labels.

Example safe labels:

```txt
Label: Stablecoin Transfer
Status: CONFIRMED
Evidence: token transfer event exists
```

Example terminal-style output:

```txt
[label] stablecoin_transfer = CONFIRMED
[label] merchant_payment = NOT_CONFIRMED
[label] ecommerce_checkout = NOT_CONFIRMED
[label] gas_sponsorship = NOT_CONFIRMED
```

This is the important part:

TraceLayer can confirm the stablecoin transfer, but it should not automatically claim merchant payment or ecommerce checkout.

## Example: Claim-Safe Output

TraceLayer separates what is confirmed from what is not confirmed.

```txt
CONFIRMED:
- stablecoin transfer observed

NOT_CONFIRMED:
- merchant attribution
- ecommerce checkout context
- gas sponsorship

BLOCKED_UNTIL_EVIDENCE_EXISTS:
- merchant payment claim
- ecommerce checkout claim
- sponsored gas claim
```

Example terminal-style output:

```txt
[claim] stablecoin_transfer: CONFIRMED
[claim] merchant_payment: NOT_CONFIRMED
[claim] ecommerce_checkout: NOT_CONFIRMED
[claim] gas_sponsorship: NOT_CONFIRMED
[guardrail] blocked unsupported merchant payment claim
[guardrail] blocked unsupported sponsored gas claim
```

## Example: Account Abstraction Context

For Account Abstraction activity, TraceLayer may collect signals such as:

```txt
- smart account interaction
- UserOperation-related activity
- EntryPoint interaction
- factory context
- bundler-related context
- paymaster-related context
```

Example terminal-style output:

```txt
[aa] smart account activity observed
[aa] UserOperation-related signal observed
[aa] EntryPoint context observed
[aa] bundler-related context checked
[aa] paymaster-related context checked
```

Safe labels may look like:

```txt
Label: Account Abstraction Activity
Status: CONFIRMED

Label: Sponsored Gas
Status: NOT_CONFIRMED
Reason: wallet-specific sponsorship evidence was not confirmed
```

TraceLayer should not claim sponsored gas unless supporting evidence exists.

## Example: From Raw Signal to Label

A simplified raw-to-label flow:

```txt
Raw:
Transfer event detected

Parsed:
USDC transfer observed

Evidence:
tx hash + token contract + sender + recipient + amount

Label:
Stablecoin Transfer

Claim status:
CONFIRMED

Blocked claims:
Merchant payment
Ecommerce checkout
```

Example terminal-style output:

```txt
[raw] event=Transfer token=USDC amount=1.00
[parse] stablecoin transfer detected
[evidence] tx reference created
[label] Stablecoin Transfer
[claim] stablecoin_transfer = CONFIRMED
[claim] merchant_payment = NOT_CONFIRMED
[claim] ecommerce_checkout = NOT_CONFIRMED
```

## Example: Proof Command Format

TraceLayer proof commands should be short and reproducible.

Example:

```bash
npm run proof:agent-context
```

Example output:

```txt
ok: true
proof: agent-context
status: PASS
```

A more detailed proof may show:

```txt
summary:
  evidenceRefs: created
  labels: generated
  guardrails: applied
  unsupportedClaims: blocked
  output: claim-safe context
```

## Proof Scope

A passing proof means that the tested flow worked for the selected case.

It does not mean every possible wallet, protocol, or business action is fully classified.

Safe interpretation:

```txt
This proof shows that TraceLayer can turn selected raw onchain evidence into structured, claim-safe output.
```

Unsafe interpretation:

```txt
This proof shows that TraceLayer can prove all wallet behavior.
```

## What Proofs Should Show

Good TraceLayer proofs should show:

```txt
raw input
parsed evidence
entity context
relationship context
generated labels
claim status
blocked claims
structured output
```

This makes the proof useful without requiring long noisy terminal logs.

## What Proofs Should Avoid

Public proof output should avoid:

```txt
private keys
API keys
secrets
long noisy logs
unsupported claims
overly broad conclusions
```

Proofs should support the claim.

Proofs should not create new unsupported claims.

## Summary

TraceLayer proofs exist to show the transformation from raw activity into safe intelligence.

The most important proof path is:

```txt
Raw data
  → Evidence
  → Entity context
  → Relationships
  → Labels
  → Claim-safe output
```

TraceLayer is not only trying to detect activity.

It is trying to explain what can safely be claimed from the evidence.
