# SCAR — Safety-Critical AI Runtime

**Status:** Public Draft
**Date:** 2026-06-19
**Relationship:** SCAR is the runtime governance pattern; ECHO is an early implementation path.

SCAR, or **Safety-Critical AI Runtime**, is a local-first runtime governance pattern for AI systems.

Its core rule is simple:

> **A language model may propose.
> It may not authorize, execute, or escalate.**

SCAR separates model reasoning from operational authority. Models may produce structured proposals, but only operator-supervised deterministic governance can turn those proposals into authorized actions.

---

## Purpose and Scope

**Purpose:**
Ensure AI-generated proposals do not directly cause unmediated effects in safety-critical, regulated, or operator-controlled contexts.

**Scope:**
SCAR is a runtime governance layer beneath agents, planners, workflow engines, model wrappers, and execution systems.

SCAR is not an agent, planner, chatbot, or executor.

SCAR is the control plane that governs when and how those systems may act.

---

## Core Requirements

A SCAR-conformant runtime must provide the following minimum guarantees:

### 1. Model Non-Authority

Model outputs are treated as proposals only.

A model must not directly authorize, execute, escalate, persist protected state, or perform protected actions.

### 2. Operator-Gated Execution

Protected actions require explicit operator authorization or a separately governed delegation mechanism outside the model.

Authorization must be bounded by scope, time, evidence, and permitted action.

### 3. Deterministic Boundaries

Critical acceptance criteria and verification logic must be deterministic, inspectable, and auditable.

The runtime must not rely on model confidence as execution authority.

### 4. Fail-Closed Behavior

On missing, failed, expired, malformed, or unverifiable authorization, the system must refuse execution and record the failure.

Failure must not silently degrade into a less-governed path.

### 5. Local-First Trust Posture

Sensitive actions, secrets, authorization records, and critical decision logs should be stored and verified locally by default.

External network access must be explicitly authorized for protected operations.

### 6. Traceable Action Records

The runtime must maintain reconstructable records of proposals, validation results, operator decisions, execution attempts, failures, and outcomes.

Where appropriate, records should be tamper-evident.

### 7. Controlled Memory and Persistence

Model memory, runtime memory, and persistent state must be bounded, auditable, and prevented from silently becoming operating authority.

### 8. Rollback-Aware Safety Design

Execution systems should support rollback, safe-fail, or containment mechanisms appropriate to the action type.

---

## Responsibilities

### Model

The model may:

* interpret intent
* summarize context
* propose structured outputs
* explain options
* identify risks

The model may not:

* authorize protected actions
* execute protected actions
* escalate privileges
* rewrite governance
* bypass operator authority

### Agent or Workflow Engine

Agents and workflow engines may:

* route proposals
* attach context
* perform preliminary schema validation
* surface proposals for operator review

They do not become authority merely because they routed or organized a model proposal.

### Governance Layer / SCAR

The SCAR governance layer must:

* validate proposals against deterministic rules
* enforce trust boundaries
* manage authorization gates
* record proposal identifiers and audit artifacts where appropriate
* fail closed when required conditions are not met

### Operator

The operator reviews proposals and grants, denies, pauses, or revokes authorization.

Operator decisions must be recorded with sufficient context to reconstruct what was approved and why.

---

## Minimal Adoption Checklist

A minimal SCAR-style runtime should:

1. Define structured proposal formats appropriate to the implementation.
2. Attach provenance metadata outside the model, including model version, input context reference, timestamp, and implementation-defined identifiers where appropriate.
3. Implement deterministic validators for critical fields.
4. Require operator authorization for protected action types.
5. Log the proposal, validation result, operator decision, execution attempt, and final outcome.
6. Default to fail-closed behavior when validators, authorization, or verification are missing.
7. Test failure paths, not only successful execution paths.

---

## Example: ECHO

ECHO is an early working implementation of the SCAR pattern.

ECHO demonstrates local-first governed AI orchestration where model output remains proposal-only while operator authority, deterministic validation, trace records, and fail-closed controls govern whether any protected action may proceed.

ECHO is not the SCAR category itself.

ECHO is the first implementation path proving SCAR principles in a local governed runtime.

---

## How to Use This Spec

To begin adopting SCAR principles:

1. Identify protected actions.
2. Define structured proposal formats.
3. Add deterministic validators.
4. Gate protected operations behind operator authorization.
5. Record proposal, validation, authorization, and outcome artifacts.
6. Test fail-closed behavior.
7. Expand execution authority only after rollback or safe-fail behavior is defined.

---

## Recommended Project Artifacts

Suggested repository artifacts include:

* `docs/ECHO.md` — high-level implementation notes and integration examples
* `SECURITY.md` — threat model and mitigations
* `ORIGIN_STATEMENT.md` — authorship and project origin
* `governance/` — optional private or implementation-specific governance artifacts
* `tests/` — validator and fail-closed behavior tests

---

## Rationale

Modern AI stacks can blur the line between reasoning and authority.

SCAR enforces a clear boundary:

> **Reasoning is not permission.**

This reduces risk from hallucination, self-authorization, hidden network effects, uncontrolled tool use, memory poisoning, and unbounded persistence.

---

## License and Attribution

This specification should be released under my MIT license 

Governance changes should require contributor review, documented rationale, and a traceable change history.
