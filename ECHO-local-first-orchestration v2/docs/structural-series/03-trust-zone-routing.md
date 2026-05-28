# Trust-Zone Routing for Local-First AI

**ECHO Structural Series**

**Author:** Michael Burger
**Project:** ECHO - Embodied Companion Orchestrator
**Status:** Public Doctrine Paper
**Version:** v0.1-public
**Date:** May 28, 2026

## Public Scope Notice

This document is part of the public ECHO doctrine. It describes public architectural principles, primitives, and governance patterns for sovereign local-first AI orchestration.

It does **not** include the private ECHO kernel, implementation details, internal workflows, schemas, prompts, command mappings, trust tables, or operational execution logic.

The public documents describe the shape of the architecture, not the private engine.

## Standalone Paper Note

This paper is intentionally self-contained. Some definitions and architectural principles are repeated across the ECHO Structural Series so each primitive can be read independently.

## Hypothetical Case Study Notice

"Echoleak" is a hypothetical teaching scenario used to reason about perception-boundary failure. It is not a claim about any real product, organization, person, or incident.

## Abstract

Local-first AI systems operate beside sensitive personal, creative, and operational data. This proximity creates a unique risk: probabilistic models may infer, combine, or expose information across boundaries that were never meant to intersect. Trust-Zone Routing (TZR) is an architectural pattern that enforces privacy as topology, not preference. It isolates cognition, governance, execution, and reality into discrete trust zones with controlled, state-aware pathways between them. A hypothetical case study - Echoleak, a zero-click perception-boundary failure - is used to illustrate why trust-zone enforcement must precede both perception and execution. This paper defines trust zones, routing rules, and their role in sovereign local-first AI systems.

## 1. Introduction

Local AI systems face a fundamentally different risk profile than cloud agents.

A local model often runs on the same machine that contains:

- personal documents
- business records
- creative drafts
- legal materials
- workflow credentials
- operational logs
This creates a structural tension:

Humans want natural-language automation.

LLMs are non-deterministic.

Privacy boundaries must remain inviolable.

Most agent architectures assume the model can safely see everything.

This assumption is false.

Trust-Zone Routing resolves the tension by enforcing architectural privacy, not preference-based privacy.

The model cannot see everything.

The model cannot infer everything.

The model cannot cross boundaries without explicit governance.

## 2. Privacy as Topology, Not Policy

Traditional privacy models rely on:

- settings
- permissions
- user preferences
- application-level controls
These fail in AI systems because they assume:

- the model can self-regulate visibility
- the model will not infer across boundaries
- the model will not combine unrelated contexts
AI systems require topological privacy, where visibility is determined by:

- zone boundaries
- corridor rules
- state
- intent
- risk tier
Trust-Zone Routing enforces privacy at the architectural level, not the UI level.

## 3. The Trust-Zone Model

ECHO defines five trust zones.

Each zone represents a different level of visibility, authority, and risk.

```text
[Zone 0] Cognition (Model)
```

```text
[Zone 1] Governance (Interpreter)
```

```text
[Zone 2] Execution (Tools & Workflows)
```

```text
[Zone 3] Local Reality (Files, System State)
```

```text
[Zone 4] External Reality (Network, APIs)
```

Each downward step increases risk.

Each upward step increases cognitive load.

## Zone 0 - Cognition (Model)

- Probabilistic
- Non-authoritative
- No direct access to reality
- Receives only filtered, contextual inputs
## Zone 1 - Governance (Interpreter)

- Enforces doctrine
- Applies perception rules
- Validates intent
- Controls visibility
## Zone 2 - Execution (Tools)

- Deterministic
- Reversible
- Corridor-bound
- Cannot escalate privileges
## Zone 3 - Local Reality

- Files
- Data
- Local environment
- High-impact operations
## Zone 4 - External Reality

- Network
- APIs
- Cloud services
- Irreversible consequences
This topology ensures that the model is structurally incapable of perceiving or acting outside its zone.

## 4. Routing Rules

Trust-Zone Routing defines how information and actions move between zones.

There are only three legal movement types.

### 4.1 Downward Movement (Toward Reality)

Examples:

- reading a file
- modifying a directory
- sending a message
- calling an API
Downward movement requires:

- corridor validation
- risk-tier evaluation
- interpreter approval
- sometimes human confirmation
Downward movement increases risk.

Therefore, it must be gated.

### 4.2 Upward Movement (Toward Cognition)

Examples:

- summarizing a file
- retrieving context
- exposing workflow state
Upward movement requires:

- perception filtering
- contextual exposure
- visibility tokens
- state-aware gating
Upward movement increases cognitive load.

Therefore, it must be controlled.

### 4.3 Lateral Movement (Within a Zone)

Examples:

- tool-to-tool communication
- model-to-model reasoning
- workflow-to-workflow routing
Lateral movement requires:

- state alignment
- corridor compliance
- deterministic routing
Lateral movement increases complexity.

Therefore, it must be bounded.

## 5. Zero-Trust Applied to AI

Zero-trust security assumes:

- no implicit permissions
- no implicit trust
- no implicit visibility
Trust-Zone Routing applies this to AI cognition.

### 5.1 No Implicit Perception

The model cannot see anything unless explicitly exposed.

### 5.2 No Implicit Execution

The model cannot act unless routed through the deterministic spine.

### 5.3 No Implicit Authority

The model cannot escalate privileges or visibility.

This is the opposite of cloud agent systems, which assume:

- full visibility
- full context
- full autonomy
Trust-Zone Routing assumes none of these.

## 6. Case Study: Echoleak (Hypothetical)

Echoleak is a hypothetical zero-click perception-boundary failure used to illustrate architectural risk.

In Echoleak, a model inferred and exposed information across trust zones without ever being granted explicit access. The lesson was not about malicious behavior. It was about ungoverned visibility.

Echoleak demonstrates that:

- perception must be governed before cognition
- cognition must be governed before execution
- visibility boundaries must be enforced before any model sees anything
Trust-Zone Routing prevents Echoleak-class failures by ensuring:

- the model cannot access raw system state
- the interpreter filters all perception
- trust-zone boundaries cannot be crossed implicitly
- visibility is always contextual and reversible
Echoleak is not a real incident.

It is an architectural teaching tool.

## 7. Adversarial Input Governance

Trust-Zone Routing assumes hostile inputs, not good-faith ones.

The interpreter must defend against:

- prompt injection
- malicious filenames
- poisoned documents
- adversarial markup
- cross-zone smuggling
- schema-breaking payloads
This is enforced through:

- input sanitization
- MIME-type enforcement
- filename normalization
- LCCA adversarial filters
- interpreter-level injection detection
This closes a major safety gap in most agent architectures.

## 8. Implementation-Agnostic Patterns

Trust-Zone Routing can be implemented with:

- n8n
- Node-RED
- custom orchestrators
- local-first automation frameworks
The key is the topology, not the tooling.

### 8.1 Zone Boundaries

Each zone must be isolated by:

- process boundaries
- permission boundaries
- visibility boundaries
### 8.2 Corridor Intersections

Corridors define the only legal pathways between zones.

### 8.3 Visibility Tokens

Every exposure event must be:

- logged
- contextual
- reversible
### 8.4 State-Aware Routing

Routing decisions depend on:

- cognitive state
- trust zone
- risk tier
- operator intent
## 9. Conclusion

Trust-Zone Routing reframes privacy as an architectural property rather than a user preference. By isolating cognition, governance, execution, and reality into discrete zones with controlled pathways, local-first AI systems become:

- safer
- more predictable
- more private
- more aligned
- more sovereign
This paper defines trust zones as a standalone architectural primitive.

Other papers in the ECHO Structural Series explore related primitives, including:

- The Deterministic Orchestration Spine
- The Script Maturity Ladder
- The Perception Firewall
- Controlled Visibility Architecture
### Interpreter-First Architecture

Together, these form the constitutional backbone of sovereign local-first AI systems.
