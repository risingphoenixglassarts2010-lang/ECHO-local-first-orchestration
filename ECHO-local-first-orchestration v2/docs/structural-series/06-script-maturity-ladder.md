# The Script Maturity Ladder

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

AI-driven automation introduces a new class of risk: scripts generated, modified, or executed by probabilistic models. Traditional software engineering treats scripts as static artifacts, but in local-first AI systems they become dynamic, model-influenced, and potentially unsafe. The Script Maturity Ladder (SML) is an architectural governance framework that transforms scripts from ad-hoc utilities into structured, validated, corridor-approved automation assets. This paper defines the ladder, its promotion gates, the deterministic validators that enforce it, and the sandboxing model required to evaluate early-stage scripts safely. A hypothetical case study - Echoleak, a zero-click perception-boundary failure - is used to illustrate why scripts must be governed before they are exposed to AI-driven orchestration.

## 1. Introduction

Local AI systems increasingly assist with:

- file operations
- creative workflows
- business processes
- automation pipelines
- multi-step tasks
But scripts in these environments are dangerous when unmanaged.

Probabilistic models may:

- generate unsafe code
- mutate existing scripts
- escalate privileges
- cross trust-zone boundaries
- perform irreversible actions
The Script Maturity Ladder reframes scripts as governed infrastructure, not utilities.

It ensures that only safe, reversible, bounded scripts ever reach the execution layer.

## 2. The Problem: Unbounded Script Execution

When scripts are treated as disposable or instantly executable, several predictable failure modes emerge.

### 2.1 Improvised Code Paths

The model generates scripts that have never been validated.

### 2.2 Hidden Side Effects

Scripts modify files or system state without visibility.

### 2.3 Irreversible Actions

Scripts perform destructive operations without rollback.

### 2.4 Privilege Escalation

Scripts gain access to tools or directories they should not.

### 2.5 Drift Through Mutation

Scripts evolve unpredictably as the model rewrites them.

These failures are not hypothetical.

They are architectural consequences of letting cognition govern execution.

## 3. The Script Maturity Ladder

The Script Maturity Ladder defines five stages of script evolution.

Each stage represents a higher level of governance, safety, and trust.

### Stage 0 - Raw

### Stage 1 - Structured

### Stage 2 - Governed

### Stage 3 - Corridor-Approved

### Stage 4 - Production

Scripts cannot skip stages.

Promotion requires deterministic validation.

## Stage 0 - Raw

Scripts in this stage are:

- model-generated
- untested
- unreviewed
- unsafe
They cannot be executed in the real environment.

## New in this revision:

### Stage 0 scripts must be evaluated in the Ephemeral Sandbox, an isolated execution environment that:

- has no access to real files
- has no access to real tools
- has no access to trust-zone boundaries
- logs all side effects
- automatically resets after execution
This closes the "how do I evaluate a Stage 0 script?" gap.

## Stage 1 - Structured

Scripts are:

- formatted
- documented
- decomposed into steps
- accompanied by model-assisted documentation (allowed at this stage only)
- conceptually reversible
Still not executable in the real environment.

They must pass structural validation.

## Stage 2 - Governed

Scripts now include:

- safety checks
- boundary conditions
- error handling
- rollback logic
- explicit inputs/outputs
At this stage, scripts may be executed only in the Ephemeral Sandbox.

## Rollback Categories (New)

Scripts must declare which category they fall into:

- Reversible - all actions can be undone
- Conditionally Reversible - some actions require compensating steps
- Irreversible - actions cannot be undone
Irreversible scripts cannot advance beyond Stage 2 without explicit human approval.

## Stage 3 - Corridor-Approved

Scripts are now:

- mapped to specific corridors
- bound to specific tools
- restricted to specific trust zones
- validated by the interpreter
- validated by automated static analysis
- validated by deterministic schema checks
They can be executed only through the Deterministic Orchestration Spine.

## Who performs promotion? (New)

Promotion requires:

- automated validators (linters, static analyzers, schema checkers)
- interpreter-level validation
- human approval for irreversible or high-risk scripts
This closes the "who promotes?" gap.

## Stage 4 - Production

Scripts reach this stage only when:

- they are stable
- they are reversible or explicitly approved
- they are predictable
- they have passed repeated execution tests
- they have human approval
- they have passed adversarial input testing
These scripts become part of the long-term automation infrastructure.

## 4. Deterministic Promotion Gates

Promotion is not subjective.

It is enforced by deterministic validators.

### 4.1 Automated Validators

- static analysis
- schema enforcement
- dependency checks
- trust-zone mapping
- rollback verification
- side-effect detection
### 4.2 Interpreter-Level Validators

- corridor compliance
- trust-zone boundaries
- risk-tier routing
- state alignment
### 4.3 Human Validators

Required only for:

- irreversible scripts
- scripts that modify external reality
- scripts that cross trust zones
- scripts that handle sensitive data
This creates a balanced governance model.

## 5. Case Study: Echoleak (Hypothetical)

Echoleak is a hypothetical zero-click perception-boundary failure used to illustrate architectural risk.

While Echoleak is not a script failure, it reveals a deeper truth:

Ungoverned perception leads to unsafe inference.

Unsafe inference leads to unsafe action.

Unsafe action often manifests through scripts.

The Script Maturity Ladder ensures that even if a model proposes unsafe behavior, the execution layer remains:

- bounded
- reversible
- deterministic
- human-controlled
Scripts become the final line of defense against inference-driven escalation.

## 6. Contemporary Pressure Points

Modern AI coding and agentic automation tools increasingly expose the same pressure points:

### 6.1 Multi-file Code Generation

AI-assisted tools can propose broad multi-file changes faster than humans can inspect them unless corridor boundaries and review gates are defined.

### 6.2 Runnable Script Generation

AI-assisted development systems can generate runnable scripts that require validation before entering a real environment.

### 6.3 Multi-step Automation Planning

Agentic planning systems can produce multi-step automation chains that require visibility controls, rollback logic, and human approval gates.

These pressure points demonstrate the present-day need for script governance without tying the principle to any single vendor or tool.

## 7. Implementation-Agnostic Patterns

The Script Maturity Ladder can be implemented with:

- n8n
- Node-RED
- custom orchestrators
- local-first automation frameworks
The key is the governance pattern, not the tooling.

### 7.1 Promotion Gates

Scripts cannot skip stages.

### 7.2 Versioning

Every script version is immutable.

### 7.3 Rollback Enforcement

Rollback categories determine promotion eligibility.

### 7.4 Auditability

Every execution must be logged.

### 7.5 Adversarial Input Testing

Scripts must be tested against hostile inputs before promotion.

## 8. Conclusion

The Script Maturity Ladder transforms scripts from dangerous, improvisational utilities into governed, reversible, corridor-approved automation assets. It prevents drift, escalation, and unsafe automation by enforcing a structured lifecycle that aligns with the Deterministic Orchestration Spine and the broader ECHO architecture.

This paper defines the ladder as a standalone architectural primitive.

Other papers in the ECHO Structural Series explore related primitives, including:

- Trust-Zone Routing
- The Perception Firewall
- Controlled Visibility Architecture
### Interpreter-First Architecture

- The Deterministic Orchestration Spine
Together, these form the constitutional backbone of sovereign local-first AI systems.
