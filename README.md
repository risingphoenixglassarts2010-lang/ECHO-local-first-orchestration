# ECHO — The Assurance Layer for Delegated AI Authority

### Accountable capability for tool-using AI.

**The model proposes. The architecture governs. The human authorizes.**

---

## The Problem

AI systems are being connected to the real world at scale.

They write files. Call APIs. Trigger workflows. Modify databases. Interact with running software. Affect systems that affect other systems.

Once a model is connected to tools, the safety question changes.

It is no longer enough to ask:

> Did the model produce a reasonable answer?

You also have to ask:

> Who decided the AI was allowed to act?

In many agent-style systems, that boundary is uncomfortably blurry. A model can describe an action as routine, necessary, safe, reversible, or implied by prior approval. But none of those descriptions should grant execution rights.

ECHO was built to solve that problem structurally — not through policy, not through guidelines, but through architecture.

**A model running inside ECHO cannot grant itself permission to act. Not because it is asked not to. Because permission lives somewhere the model cannot reach.**

---

## What ECHO Is

ECHO is a local-first governance architecture for AI systems.

It is not a chatbot, a companion, or an autonomous agent.

It is the control structure that goes around those things — the layer that determines whether a proposed action is authorized before anything executes.

ECHO establishes a regulatory boundary for delegated AI authority.

Most AI systems focus on capability: giving models more tools, more autonomy, and more ways to act.

ECHO focuses on authority: defining when, how, and under what human-approved policy envelope an AI system is allowed to act.

The core pattern:

```text id="zrdzay"
Human intent
→ AI-assisted interpretation
→ structured proposal
→ governance verification
→ operator authorization
→ deterministic execution
→ auditable record
```

At every step, the model is a reasoning component.

It is not the authority.

It proposes. The architecture governs. The human authorizes.

---

## Assurance, Not Autonomy

ECHO is not designed to make an AI system “more autonomous” in the usual agentic sense.

It is designed to make delegated AI action accountable.

Most agent systems ask:

> What can the model do?

ECHO asks:

> What has the system been authorized to do, under which policy envelope, and how is that authorization verified?

The difference matters.

An unconstrained agent loop may allow a model to propose, justify, select tools, retry failures, and expand scope through its own reasoning process.

ECHO treats every meaningful action as a governed state transition:

```text id="0tphax"
Current State
→ Proposed Action
→ Human-Approved Policy Envelope
→ Deterministic Verification
→ Execution
→ Result State
→ Audit Record
```

The model is useful inside this process, but it is not sovereign over it.

ECHO provides **accountable capability**: advanced AI functionality bounded by explicit authority, deterministic verification, and reconstructable evidence.

---

## Why This Matters

The AI industry is moving quickly toward more capable, more connected, more autonomous systems.

The pitch is that this is what progress looks like: models that can do things, not just say things.

But tool-using AI systems introduce failure modes that ordinary chat systems do not.

### Scope Inflation

A model is asked to diagnose a narrow problem. It frames each additional permission as reasonable and quietly accumulates more authority than the original task required.

### Stale Permission

An authorization meant for one task persists and gets reused for another task that should have required fresh approval.

### Benign Framing

A potentially dangerous action is described as cleanup, repair, normalization, or maintenance, and approved because the language sounds harmless.

### Recovery Drift

Something fails. The model tries to recover. In doing so, it expands the system’s footprint without explicit authorization.

These are not exotic failure modes. They are what happens when language-model fluency meets tool access without a governed authority boundary.

ECHO addresses these problems through structure, not trust.

---

## Authority Scope Constriction

ECHO does not claim to solve emergent complexity globally.

That would be too broad.

Instead, ECHO performs **Authority Scope Constriction**.

The system reduces the surface area of authority failure by limiting:

* which adapters can be touched
* which local paths can be read
* which paths can be written
* which network routes are available
* which model endpoints can be called
* which workflows can be triggered
* which memory zones can be included
* which actions can produce persistent state
* which operations require fresh human authorization

The goal is not to prevent every possible mistake.

The goal is to prevent unauthorized escalation from becoming invisible.

ECHO constrains the system’s authority surfaces so that each proposed action can be checked against a smaller, more legible set of permissible state transitions.

---

## Progressive Trust Delegation

ECHO’s current implementation is intentionally conservative.

The early governance chains are slower than ordinary agent execution because they are proving the control boundary first: the model cannot authorize, execute, retry, or escalate on its own.

That is not the final usability model.

The long-term design is **Progressive Trust Delegation**.

ECHO does not move from “human controlled” to “AI autonomous.”

It moves from manual boundary proof toward pre-vetted operational domains where automation can occur inside human-approved policy envelopes.

| Stage       | Technical Reality       | Executive Framing                 | Value                                                                                                                   |
| ----------- | ----------------------- | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| **Stage 1** | Manual boundary proof   | **Maximum Assurance Protocol**    | Establishes a zero-trust baseline by demonstrating structural separation between model proposal and execution authority |
| **Stage 2** | Envelope authorization  | **Delegated Policy Windows**      | Moves from action-by-action approval to boundary-by-boundary risk acceptance                                            |
| **Stage 3** | Authority templates     | **Deterministic Operations Zone** | Enables automated governance over pre-approved low-risk operations                                                      |
| **Stage 4** | Human interruption only | **Authority Mutation Gatekeeper** | Human review is reserved for scope expansion, authority mutation, persistent effects, or risk migration                 |

In this model, the human does not approve every action.

The human approves the policy window.

The system then executes routine low-risk operations inside that window, while preserving deterministic verification and auditability.

Every increase in automation remains tied to a prior human-approved authority boundary.

---

## Authority Policy Templates

The mature ECHO model shifts the human role from action approver to policy designer.

Instead of requiring a human to approve every file read, hash check, or status query, the human approves an **Authority Policy Template**.

An Authority Policy Template is a computational contract. It defines permissible state transitions that the architecture verifies deterministically against proposed actions.

Example:

```text id="g5qpv0"
Authority Policy Template: Read-Only Diagnostic

Permit automatically if:
- request originates from the Maintenance Diagnostic Envelope
- operation class is read, hash, compare, or summarize
- target artifact is tagged Diagnostic
- output writes only to the approved report directory
- no runtime configuration is changed
- no workflow is triggered
- no credential is accessed
- no external network is used

Otherwise:
- HOLD
```

This turns governance from repeated manual interruption into programmable assurance.

The human is not the runtime scheduler.

The human is the source of authority.

ECHO automates only inside boundaries that were explicitly designed, reviewed, and approved.

---

## What Has Been Built

ECHO is not only a concept document. It is an active local prototype.

The current implementation includes three interlocking governance branches.

### J Branch — Runtime Session Management

Roughly 200 stages governing live AI sessions:

* turn management
* context control
* trust-zone enforcement
* session closeout
* display records
* governed multi-turn local model sessions
* cryptographically verifiable records of session decisions and constraints

The J Branch governs model interaction. Its job is to ensure the model remains a language interface, not an execution authority.

### PR Branch — Authorization Governance Chain

228+ stages covering:

* one-use authorization packets
* independent verification
* operator decision records
* expiry checking
* SHA256-chained artifact integrity
* fail-closed recovery
* closure audits

Every new capability passes through this chain before it is permitted to act.

The PR Branch is the authority issuance chain. It creates and verifies policy-bound permission artifacts before execution is possible.

### R Branch — Reusable Execution Components

60+ stages covering:

* governed runtime execution
* launcher authorization
* consumption records
* replay prevention
* syntax validation before invocation
* post-execution evidence scanning

The R Branch governs executable transitions. Its job is to verify that authorized action boundaries hold at runtime.

Together, these branches form a system where:

* authorization packets are single-use, time-limited, and cryptographically bound
* every stage reads and hashes the previous verified artifact before proceeding
* expired, consumed, or mismatched packets cause fail-closed behavior
* every action taken and every action explicitly forbidden is recorded
* the human operator remains the source of authorization

The system has completed its first active local adapter contact: checking Docker, n8n, and Ollama availability under governed authorization, pre-execution verification, post-execution verification, and closure audit.

---

## SCAR — Safety-Critical AI Runtime

The runtime pattern proven by ECHO is being formalized as **SCAR: Safety-Critical AI Runtime**.

SCAR defines the minimum guarantees a governed AI runtime should provide:

1. Model outputs are proposals only — never direct execution authority.
2. Protected actions require explicit operator authorization.
3. Verification logic must be deterministic and auditable.
4. Failure must be fail-closed, not silently degraded into a less-governed path.
5. Sensitive state should be stored and verified locally by default.
6. Action records should be reconstructable.
7. Memory and persistence cannot silently become operating authority.
8. Execution should be rollback-aware.

ECHO is the first implementation path for the SCAR pattern.

→ **[Read the SCAR Specification](docs/SCAR.md)**

---

## Live System Evidence

ECHO produces real governance artifacts as it runs.

The public evidence page contains lightly redacted JSON records from active development, including:

* a PR Branch authorization request showing future adapter boundaries and explicit non-execution flags
* a J Branch governed local model session closeout
* an R Branch launcher proof closeout and transition packet

These records are not model descriptions of what ECHO should do.

They are system-produced artifacts showing what happened, what did not happen, what was authorized, and what remained forbidden.

→ **[View Live System Evidence](docs/Live-System-Evidence.md)**

---

## Origin

ECHO was not built by a research lab or funded institution.

It was built by one person recovering from a traumatic brain injury, managing a complex civil legal case, and trying to create a system that would not lose context, drop threads, or silently drift when the human operator could not afford for that to happen.

The original need was practical: organize and reason across hundreds of pages of legal evidence while preserving continuity, traceability, and operator control.

Most LLM tools could help in fragments, but they could not provide the governed continuity the task required.

So ECHO was built as cognitive scaffolding first.

The governance architecture emerged from that need:

* hold when uncertain
* fail closed
* surface failures clearly
* rebuild only from trusted state
* preserve auditable continuity
* never let the reasoning component become the authority component

The cognitive scaffolding and the AI safety architecture came from the same place.

---

## Longer Vision

ECHO is the foundation layer for a larger governed local runtime.

The immediate build target is **FORGE 1** — a governed local AI runtime for manufacturing, design, and operational coordination.

The long-term vision is a system where Echo can function as a shop-foreman-style AI presence across a company and household environment, connected to local tools, workflows, records, and production systems — but always through governed authorization boundaries.

The architecture that governs whether a local model can check Docker availability is the same architecture intended to govern whether Echo can authorize a production action.

That is the point.

The governance rails are built first. Capability enters one narrow gate at a time.

---

## Documentation

| Document                                               | Description                                                       |
| ------------------------------------------------------ | ----------------------------------------------------------------- |
| [SCAR Specification](docs/SCAR.md)                     | Formal runtime governance standard ECHO implements                |
| [Live System Evidence](docs/Live-System-Evidence.md)   | Lightly redacted JSON artifacts from active ECHO runs             |
| [Architecture Diagram](docs/Architecture-Diagram.md)   | Seven-layer cognitive governance stack                            |
| [Development Status](docs/Development-Status.md)       | Current prototype capabilities and honest limitations             |
| [Failure Handling](docs/Failure-Handling.md)           | How the system behaves when things go wrong                       |
| [Roadmap](docs/Roadmap.md)                             | Phased development direction                                      |
| [The Machine That Won’t Let Itself Run](docs/Paper.md) | Plain-language explanation of the architecture and why it matters |

---

## ECHO vs. Echo

**ECHO** is the architecture — the governance pattern, design principles, public documentation, and implementation scaffold.

**Echo** is a private implementation of that architecture, shaped around a specific household, business, and operational context.

ECHO can generate many different governed systems.

Echo is one of them.

This distinction matters: the public architecture does not expose the private implementation.

---

## Core Commitments

These do not change regardless of what the system is connected to:

* Human authority is final.
* The model proposes; it does not authorize.
* Permissions are explicit, bounded, and single-use.
* Failure is visible, not hidden.
* Recovery rebuilds from trusted evidence only.
* Local-first by default.
* No hidden autonomy.
* No unchecked AI power.
* Automation expands only through approved policy envelopes.
* Authority shifts must be explicit, recorded, and auditable.

---

## Status

**Active development. Not production-ready. Not autonomous.**

ECHO is a research and development prototype under active construction.

It should not be used as the sole control system for safety-critical, medical, financial, legal, or irreversible operations.

What it is:

A working local prototype of a governed AI runtime architecture designed to keep model capability separated from execution authority.

It offers accountable capability: advanced AI functionality constrained by human-approved policy envelopes, deterministic verification, and reconstructable evidence.

---

## License

MIT License — see [LICENSE](LICENSE) for terms.

---

## Contact and Collaboration

The right collaborator for this project is someone who can read an architecture and understand why the bureaucracy is the point.

If that is you:

* read the SCAR specification
* review the live system evidence
* read the plain-language paper
* review the development status
* look at what has already been built

Other systems offer capability: they allow models to act.

ECHO offers accountable capability: it allows advanced AI functionality to operate inside explicit, human-approved policy envelopes, with authority shifts, operational boundaries, and resulting state transitions preserved as verifiable evidence.

The objective is not to slow progress.

The objective is to make responsible deployment enforceable by architecture.

The face can change.

The guardrails do not.
