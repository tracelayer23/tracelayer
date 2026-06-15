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

TraceLayer proofs are designed to validate that labels, summaries, and context outputs are supported by evidence, not assumptions.

## Proof Flow

A simplified proof flow looks like this:

```txt
1. Collect raw wallet activity
2. Parse transactions, logs, transfers, native token usage, and Account Abstraction signals
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
asset: token_or_native_asset
amount: ...
```

At this stage, TraceLayer does not treat the activity as a payment flow, swap, bridge, sponsored execution, or automated workflow.

It is only raw evidence.

## Example: Parsed Evidence

TraceLayer converts the raw record into evidence references:

```txt
Evidence detected:
- transaction hash
- event reference
- sender address
- recipient address
- asset or token contract
- amount
- timestamp
```

Example terminal-style output:

```txt
[scanner] wallet activity collected
[parser] asset movement detected
[evidence] transfer evidence reference created
[evidence] tx hash attached
[evidence] asset context attached
```

This means TraceLayer can confirm that asset movement happened.

It does not mean TraceLayer can confirm the purpose of the activity.

## Example: Entity Context

TraceLayer then identifies entities involved in the activity.

```txt
Entity context:
- wallet address observed
- asset context observed
- recipient address observed
- contract interaction observed
```

Example terminal-style output:

```txt
[entity] wallet detected
[entity] asset context detected
[entity] recipient detected
[entity] contract target detected
```

Entity detection helps explain who or what was involved.

## Example: Relationship Mapping

TraceLayer maps relationships between observed entities.

```txt
Relationships:
wallet → asset movement
wallet → recipient
wallet → contract interaction
claim → evidence reference
```

Example terminal-style output:

```txt
[relationship] wallet -> asset_movement
[relationship] wallet -> recipient
[relationship] asset_movement -> evidence_ref
[relationship] claim -> evidence_ref
```

This relationship layer helps explain how raw activity connects together.

## Example: Label Generation

After evidence and relationships are processed, TraceLayer can generate safe labels.

Example safe labels:

```txt
Label: Asset Movement
Status: CONFIRMED
Evidence: transfer event or native asset movement exists
```

Example terminal-style output:

```txt
[label] asset_movement = CONFIRMED
[label] payment_flow = NOT_CONFIRMED
[label] application_intent = NOT_CONFIRMED
[label] sponsored_execution = NOT_CONFIRMED
```

This is the important part:

TraceLayer can confirm the observed asset movement, but it should not automatically claim payment intent, application intent, or sponsored execution.

## Example: Claim-Safe Output

TraceLayer separates what is confirmed from what is not confirmed.

```txt
CONFIRMED:
- asset movement observed

NOT_CONFIRMED:
- payment attribution
- application intent
- sponsored execution

BLOCKED_UNTIL_EVIDENCE_EXISTS:
- payment flow claim
- specific application flow claim
- sponsored execution claim
```

Example terminal-style output:

```txt
[claim] asset_movement: CONFIRMED
[claim] payment_flow: NOT_CONFIRMED
[claim] application_intent: NOT_CONFIRMED
[claim] sponsored_execution: NOT_CONFIRMED
[guardrail] blocked unsupported payment flow claim
[guardrail] blocked unsupported sponsored execution claim
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

Label: Sponsored Execution
Status: NOT_CONFIRMED
Reason: wallet-specific sponsorship evidence was not confirmed
```

TraceLayer should not claim sponsored execution unless supporting evidence exists.

## Example: From Raw Signal to Label

A simplified raw-to-label flow:

```txt
Raw:
Transfer or value movement event detected

Parsed:
Asset movement observed

Evidence:
tx hash + asset context + sender + recipient + amount

Label:
Asset Movement

Claim status:
CONFIRMED

Blocked claims:
Payment flow
Application intent
Sponsored execution
```

Example terminal-style output:

```txt
[raw] event=Transfer asset=token_or_native_asset amount=...
[parse] asset movement detected
[evidence] tx reference created
[label] Asset Movement
[claim] asset_movement = CONFIRMED
[claim] payment_flow = NOT_CONFIRMED
[claim] application_intent = NOT_CONFIRMED
```

## Example: Multi-Environment Context

TraceLayer proofs should also support different execution environments.

Different environments may produce different patterns around:

* asset movement
* native token usage
* account types
* contract standards
* execution models
* infrastructure behavior
* application-specific logic

Example terminal-style output:

```txt
[context] execution model checked
[context] asset movement checked
[context] native token usage checked
[context] infrastructure signals checked
[context] application-specific signals checked
```

TraceLayer treats these differences as context that can be compared, separated, and verified through evidence.

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

It does not mean every possible wallet, protocol, environment, or application behavior is fully classified.

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
