# Interpreter-First Architecture

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

Most AI systems follow a model-first paradigm: the model interprets, decides, and executes. This architecture is unsafe in local-first environments where models operate beside private files, workflows, and system capabilities. Interpreter-First Architecture (IFA) reverses this relationship. The model becomes a proposer of structured intent; the interpreter becomes the authoritative governor of perception, state, and execution. The interpreter enforces schemas, trust-zone boundaries, visibility constraints, adversarial input defenses, and risk-tier routing before any action reaches the deterministic spine. A hypothetical case study - Echoleak, a zero-click perception-boundary failure - is used to illustrate why governance must precede cognition, not follow it. This paper defines IFA and its role as the constitutional layer of sovereign local-first AI systems.

## 1. Introduction

Local AI systems face a unique challenge:

Humans want natural-language automation.

LLMs are probabilistic and non-deterministic.

Operating systems require deterministic control.

Privacy boundaries must remain inviolable.

Inputs may be adversarial, not benign.

Most agent architectures solve this incorrectly by giving the model too much authority:

- too much visibility
- too much autonomy
- too much control over tools
- too much influence over system state
Interpreter-First Architecture solves this by placing a deterministic interpreter between the model and the world.

The interpreter - not the model - governs:

- perception
- state
- trust zones
- schema validation
- adversarial input filtering
- execution authority
This is the foundation of safe local-first AI.

## 2. The Problem: Model-First Systems Are Unsafe

Model-first systems assume:

- the model can self-regulate
- the model will not cross boundaries
- the model will not infer across contexts
- the model will not hallucinate tools
- the model will not escalate privileges
- the model will not be tricked by adversarial inputs
These assumptions are false.

Model-first systems exhibit predictable failure modes:

### 2.1 Over-Perception

The model sees more than the task requires.

### 2.2 Unsafe Inference

The model infers sensitive information from benign inputs.

### 2.3 Schema Drift

The model produces malformed or incomplete payloads.

### 2.4 Execution Drift

The model escalates tasks beyond the user's intent.

### 2.5 Boundary Collapse

The model crosses trust zones without authorization.

### 2.6 Adversarial Input Vulnerability

The model is manipulated by poisoned documents, filenames, or embedded instructions.

The Echoleak case study demonstrates that ungoverned perception leads to unsafe inference, and unsafe inference leads to unsafe action.

Interpreter-First Architecture prevents this by ensuring the model never interacts with the system directly.

## 3. Interpreter-First Architecture

Interpreter-First Architecture places a deterministic interpreter between the model and all system capabilities.

- User Intent
- ↓
- Model (Proposes)
- ↓
- Interpreter (Governs)
- ↓
- Deterministic Spine (Executes)
- ↓
- Tools / System
### 3.1 Definition

A governance layer that:

- validates structured intent
- enforces schemas
- applies trust-zone rules
- controls perception
- filters adversarial inputs
- routes tasks
- manages risk tiers
- authorizes execution
### 3.2 Purpose

To ensure that:

- cognition remains probabilistic
- governance remains deterministic
- execution remains bounded
### 3.3 Relationship to the Model

The model is a reasoning engine, not an executor.

The interpreter is the constitutional authority.

## 4. Responsibilities of the Interpreter

The interpreter governs six domains.

### 4.1 Perception Governance

The interpreter decides:

- what the model is allowed to see
- when it is allowed to see it
- under what corridor
- with what visibility window
This prevents over-perception and inference leakage.

### 4.2 Schema Enforcement

All model outputs must be:

- structured
- complete
- valid
- bounded
Malformed payloads fail closed.

### 4.3 Trust-Zone Enforcement

The interpreter ensures:

- no unauthorized boundary crossing
- no implicit visibility
- no implicit authority
- no escalation
Trust zones remain inviolable.

### 4.4 Adversarial Input Filtering (New)

The interpreter defends against:

- prompt injection
- malicious filenames
- poisoned documents
- adversarial markup
- cross-zone smuggling
This is enforced through:

- MIME-type enforcement
- filename normalization
- LCCA sanitization
- schema-level validation
- injection detection
This closes a major gap in most agent architectures.

### 4.5 Risk-Tier Routing

The interpreter assigns actions to risk tiers:

- Tier 0 - auto-execute
- Tier 1 - clarification
- Tier 2 - dry run
- Tier 3 - human approval
- Tier 4 - refusal
High-risk actions require explicit operator confirmation.

### 4.6 Execution Authorization

The interpreter decides:

- what executes
- when it executes
- how it executes
- whether it executes at all
The model never touches the OS directly.

## 5. Case Study: Echoleak (Hypothetical)

Echoleak is a hypothetical zero-click perception-boundary failure used to illustrate architectural risk.

In Echoleak, a model inferred and exposed information across trust zones without ever being granted explicit access. The lesson was not about malicious behavior. It was about ungoverned cognition.

Echoleak demonstrates that:

- perception must be filtered before cognition
- cognition must be validated before execution
- trust zones must be enforced before visibility
- the interpreter must govern all model interactions
Echoleak is not a real incident.

It is an architectural teaching tool.

## 6. Interpreter-First vs. Model-First

## Model-First Architecture

- model sees everything
- model decides everything
- model executes everything
- vulnerable to adversarial inputs
- unsafe
- unpredictable
- irreversible
- model sees only what is allowed
- model proposes structured intent
- interpreter governs all decisions
- deterministic spine executes
- adversarial inputs are filtered
- safe
- reversible
- inspectable
Within ECHO, Interpreter-First Architecture is the required constitutional pattern for sovereign local-first AI. Other architectures may approach the problem differently, but ECHO treats interpreter-governed cognition as non-negotiable.

## 7. Implementation-Agnostic Patterns

Interpreter-First Architecture can be implemented with:

- n8n
- Node-RED
- custom orchestrators
- local-first automation frameworks
The key is the governance pattern, not the tooling.

### 7.1 Interpreter as Gatekeeper

The interpreter is the only authority that can approve execution.

### 7.2 Interpreter as Router

The interpreter routes tasks to the correct workflows and tools.

### 7.3 Interpreter as Validator

The interpreter enforces schemas and corridor rules.

### 7.4 Interpreter as Firewall

The interpreter filters perception before it reaches the model.

### 7.5 Interpreter as Adversarial Shield

The interpreter sanitizes and validates all inputs before they reach cognition.

## 8. Conclusion

Interpreter-First Architecture is the constitutional layer of sovereign local-first AI systems. It ensures that:

- perception is governed
- cognition is bounded
- execution is deterministic
- trust zones remain intact
- adversarial inputs are neutralized
- the operator remains sovereign
This paper defines IFA as a standalone architectural primitive.

Other papers in the ECHO Structural Series explore related primitives, including:

- The Deterministic Orchestration Spine
- Trust-Zone Routing
- The Script Maturity Ladder
- The Perception Firewall
- Controlled Visibility Architecture
Together, these form the constitutional backbone of safe, local-first AI orchestration.
