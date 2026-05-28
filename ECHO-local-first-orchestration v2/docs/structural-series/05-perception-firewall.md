# The Perception Firewall

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

Execution safety answers the question: What is the AI allowed to do?

Perception safety answers the deeper question: What is the AI allowed to see, retrieve, combine, summarize, or expose?

In local-first AI systems, perception is a security boundary. If a model can see something, it can infer it, transform it, embed it, or leak it - intentionally or unintentionally. The Perception Firewall is an architectural pattern that governs visibility before cognition, not after. It ensures that the model receives only the minimal, contextual, reversible information required for the current task. A hypothetical case study - Echoleak, a zero-click perception-boundary failure - is used to illustrate why perception governance must precede both cognition and execution. This paper defines the Perception Firewall, its components, its adversarial threat model, and its role in sovereign local-first AI systems.

## 1. Introduction

Most AI systems assume:

- more context = better performance
- more visibility = better reasoning
- more data = better alignment
This assumption is false.

Unbounded perception leads to:

- inference leakage
- privacy violations
- context poisoning
- identity drift
- unsafe generalization
- irreversible exposure
The Perception Firewall reframes perception as a governed capability, not an open stream.

The core principle:

The system cannot leak what it was never allowed to see.

## 2. The Problem: Over-Perception

Probabilistic models are associative engines.

If they see something, they can:

- infer relationships
- reconstruct missing details
- combine contexts
- expose sensitive information
- hallucinate based on partial visibility
This creates predictable failure modes.

### 2.1 Inference Leakage

The model infers sensitive information from benign inputs.

### 2.2 Context Poisoning

Irrelevant or harmful data influences reasoning.

### 2.3 Identity Drift

The model's internal representation of the user becomes unstable.

### 2.4 Cognitive Escalation

The model escalates tasks based on information it should not have seen.

### 2.5 Over-Generalization

The model draws conclusions beyond the intended scope.

These failures originate in perception, not execution.

## 3. Training-Time vs. Inference-Time Failures

A critical distinction:

## Training-Time Contamination

- Data enters the model weights
- Cannot be removed
- Not governed by runtime architecture
- Requires dataset hygiene and differential privacy
## Inference-Time Over-Perception

- Data enters the context window
- Can be filtered
- Can be governed
- Can be reversed
- Is exactly what the Perception Firewall addresses
The Perception Firewall governs runtime visibility, not training-time contamination.

This distinction closes the conceptual gap that often confuses discussions of model leakage.

## 4. The Perception Firewall

The Perception Firewall is a deterministic boundary that governs what the model is allowed to perceive.

It sits between reality and cognition, not after.

- Code
```text
[Reality] -> [Perception Firewall] -> [Interpreter] -> [Model]
```

### 4.1 Definition

A visibility governance layer that:

- filters inputs
- restricts exposure
- enforces context
- limits visibility windows
- prevents over-perception
- ensures reversibility
### 4.2 Purpose

To ensure that:

- the model sees only what is necessary
- visibility is contextual
- exposure is reversible
- perception is corridor-bound
- sensitive data is never ingested
### 4.3 Relationship to Trust-Zone Routing

Trust-Zone Routing governs where information can flow.

The Perception Firewall governs what information can flow.

They are complementary primitives.

## 5. Visibility Governance Rules

The Perception Firewall enforces three strict rules.

## Rule 1 - Contextual Visibility

The model sees only what is relevant to the current task.

Example:

If the user asks for a summary of a paragraph, the model should not see the entire document.

## Rule 2 - Reversible Visibility

Exposure must be:

- logged
- bounded
- revocable
The system must be able to "forget" by design.

## Rule 3 - Corridor-Bound Visibility

Visibility is tied to:

- state
- intent
- corridor
- trust zone
The model cannot request additional visibility on its own.

## 6. The Perception Firewall Components (Upgraded)

The critique noted that earlier drafts described these components aspirationally.

This version defines them concretely.

### 6.1 Local Context Capture Agent (LCCA)

A deterministic summarizer that:

- extracts only the relevant portion of a file or artifact
- enforces strict schemas
- strips metadata
- normalizes formatting
- removes adversarial markup
- produces bounded summaries
- Inputs: raw files, text, media
- Outputs: structured, sanitized context blocks
- Failure Modes: schema violation, adversarial content, trust-zone mismatch
### 6.2 Media Governance Layer (MGL)

A classifier that assigns media to trust-zone categories:

- normal
- sensitive
- private
- restricted
- Inputs: media files, metadata
- Outputs: trust-zone labels, visibility tokens
- Failure Modes: misclassification, ambiguous content
### 6.3 Personal Media Vault (PMV)

A storage boundary for sensitive material.

- encrypted
- access-token gated
- non-indexable
- non-summarizable without explicit approval
- Inputs: sensitive media
- Outputs: controlled access handles
- Failure Modes: unauthorized access attempts
### 6.4 Context Retrieval Gate

Controls what indexed documents or logs can be retrieved.

- enforces corridor rules
- enforces trust-zone boundaries
- enforces visibility windows
### 6.5 Artifact Review Layer

Validates generated outputs before release.

- checks for leakage
- checks for hallucinated sensitive content
- checks for cross-zone contamination
### 6.6 Workflow Governance Spine

Applies policy checks before context reaches the model.

- schema validation
- trust-zone mapping
- risk-tier routing
## 7. Adversarial Input Threat Model (New)

The Perception Firewall assumes hostile inputs, not good-faith ones.

It must defend against:

### 7.1 Prompt Injection

Embedded instructions in documents, filenames, or metadata.

### 7.2 Malicious Filenames

Unicode tricks, escape sequences, or misleading extensions.

### 7.3 Poisoned Documents

Hidden markup, adversarial formatting, or embedded commands.

### 7.4 Cross-Zone Smuggling

Content that attempts to bypass trust-zone boundaries.

### 7.5 Schema-Breaking Payloads

Inputs designed to crash or confuse validators.

Defense mechanisms include:

- MIME-type enforcement
- filename normalization
- adversarial markup stripping
- LCCA sanitization
- interpreter-level injection detection
This closes a major gap in most agent architectures.

## 8. Case Study: Echoleak (Hypothetical)

Echoleak is a hypothetical zero-click perception-boundary failure used to illustrate architectural risk.

In Echoleak, a model inferred and exposed information across trust zones without ever being granted explicit access. The lesson was not about malicious behavior. It was about ungoverned visibility.

Echoleak demonstrates that:

- perception must be governed before cognition
- cognition must be governed before execution
- visibility boundaries must be enforced before any model sees anything
Echoleak is not a real incident.

It is an architectural teaching tool.

## 9. Implementation-Agnostic Patterns

The Perception Firewall can be implemented with:

- n8n
- Node-RED
- custom orchestrators
- local-first automation frameworks
The key is the governance pattern, not the tooling.

### 9.1 Visibility Tokens

Each exposure event generates a token that defines:

- what was exposed
- why it was exposed
- for how long
- under what corridor
### 9.2 Exposure Windows

Visibility is time-bound and state-bound.

### 9.3 State-Aware Perception

The model's visibility changes depending on:

- cognitive state
- pacing state
- execution state
## 10. Conclusion

The Perception Firewall reframes perception as a governed resource rather than an unbounded input stream. By enforcing contextual, reversible, corridor-bound visibility, local-first AI systems become:

- safer
- more predictable
- more private
- more aligned
- more sovereign
This paper defines the Perception Firewall as a standalone architectural primitive.

Other papers in the ECHO Structural Series explore related primitives, including:

- Controlled Visibility Architecture
- Trust-Zone Routing
### Interpreter-First Architecture

- The Script Maturity Ladder
- The Deterministic Orchestration Spine
Together, these form the constitutional backbone of sovereign local-first AI systems.
