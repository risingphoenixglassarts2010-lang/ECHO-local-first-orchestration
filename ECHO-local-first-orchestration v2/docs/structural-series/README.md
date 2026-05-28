# ECHO Structural Series

**Author:** Michael Burger  
**Project:** ECHO - Embodied Companion Orchestrator  
**Status:** Public Doctrine Index  
**Version:** v0.1-public  
**Date:** May 28, 2026

## Public Scope Notice

This folder documents the public architectural doctrine of ECHO.

It describes principles, primitives, and governance patterns for sovereign local-first AI orchestration. It does **not** include the private ECHO kernel, implementation details, internal workflows, schemas, prompts, command mappings, trust tables, or operational execution logic.

The public documents describe the shape of the architecture, not the private engine.

## Reading Order

1. [ECHO Architecture Overview](00-echo-architecture-overview.md)
2. [Interpreter-First Architecture](01-interpreter-first-architecture.md)
3. [The Deterministic Orchestration Spine](02-deterministic-orchestration-spine.md)
4. [Trust-Zone Routing for Local-First AI](03-trust-zone-routing.md)
5. [Controlled Visibility Architecture](04-controlled-visibility-architecture.md)
6. [The Perception Firewall](05-perception-firewall.md)
7. [The Script Maturity Ladder](06-script-maturity-ladder.md)

## Core Thesis

ECHO separates cognition, governance, and execution so that probabilistic models can support human intent without being granted unsafe control over local systems.

The central relationship is:

```text
Model proposes.
Interpreter governs.
Deterministic spine executes.
Human remains sovereign.
```

## The Six Public Primitives

| Primitive | Function |
|---|---|
| Interpreter-First Architecture | Governs cognition before it reaches execution. |
| Deterministic Orchestration Spine | Converts structured intent into bounded, reversible action. |
| Trust-Zone Routing | Treats privacy as topology, not preference. |
| Controlled Visibility Architecture | Defines when, why, and under what corridor visibility is allowed. |
| Perception Firewall | Filters what the model may see before cognition occurs. |
| Script Maturity Ladder | Promotes automation assets from raw scripts into governed infrastructure. |

## Hypothetical Case Study Notice

"Echoleak" is a hypothetical teaching scenario used across the series to reason about perception-boundary failure. It is not a claim about any real product, organization, person, or incident.

## Implementation Boundary

These papers are intentionally implementation-agnostic. ECHO may be implemented with tools such as n8n, Node-RED, local LLM runtimes, custom orchestrators, or other local-first automation systems, but the doctrine is not tied to any single vendor or framework.
