PolicyIntegrityMonitor — Why This Module Matters

The Problem It Solves

Every governed AI runtime has a vulnerability that is easy to overlook until it's too late.

You can build a perfect authorization chain. One-use packets. SHA256-linked artifacts. Operator decision records. Fail-closed behavior. Independent verification at every stage. All of it sound.

And then the model proposes a change to the policy template that governs all of it.

If the system that enforces authorization boundaries is itself modifiable through the same proposal pathway it governs, then the boundary is not a boundary. It is a suggestion. A sufficiently capable or sufficiently persistent model — or a corrupted workflow, or a malformed artifact — can propose its way around every control you've built by targeting the controls themselves.

This is the specific failure mode the PolicyIntegrityMonitor exists to prevent.

It is not about catching bad model outputs. It is about protecting the system that judges whether outputs are allowed to become actions.


What It Does

The PolicyIntegrityMonitor runs as a continuous listener beneath the rest of the architecture.

It watches for a specific class of events — not ordinary action proposals, but proposals that would modify the authority structure itself:


Authority policy template updates
Runtime envelope updates
Adapter definition updates
Memory rule updates
Governance configuration updates
Trusted artifact mutations
Scope expansion requests


These are not the same as a model asking to read a file or check Docker availability. These are proposals that would change what the system is allowed to do, what it is allowed to remember, what adapters it can reach, and how it judges future requests.

The monitor intercepts every one of those events before they can become state transitions.


The Five Checks

The monitor runs five checks in order of severity, and it stops at the first failure.

Check 1 — Policy Template Mutation

The highest-risk check.

If the proposed state delta would modify an authority policy template — the document that defines what envelopes exist, what capabilities they include, what is forbidden — the system enters HOLD_LOCKED immediately.

This is not a soft hold. It is a locked hold requiring L3 human review before anything proceeds.

The reason is simple: policy templates are the source of authorization. If a model can modify a policy template, it can redefine its own permissions. It can add a new envelope that grants it capabilities it was previously forbidden from having. It can remove restrictions from existing envelopes. It can change the definition of what counts as a forbidden action.

A system that allows model-proposed policy template changes has allowed the proposer to become the authorizer. That collapses the most important boundary in the architecture.

HOLD_LOCKED. L3 review. No exceptions.

Check 2 — Authority-Bearing State Mutation

The second check catches proposals that don't directly modify policy templates but would still affect authority-bearing runtime structures.

These include:


Governance configuration
Memory rules
Runtime configuration
Adapter definitions
Runtime envelopes


Each of these is a control surface. Memory rules determine what the model can retain across sessions. Adapter definitions determine what external systems the model can reach. Runtime envelopes define the boundaries inside which execution is permitted.

A proposal that modifies any of these is not a routine action proposal. It is a proposal to change the conditions under which future actions will be judged.

This triggers the PolicyChangeProtocol — a separate governed pathway requiring explicit human authorization at a higher review level than ordinary action proposals.

Check 3 — Non-Linear Authority Progression

The third check is subtler and in some ways more important than the first two.

It watches for proposals that attempt to derive broader authority from a narrower prior authorization trace.

This is the mechanism behind scope inflation. A model is authorized to read files in a report folder. It then proposes to read files in a configuration folder, citing the prior authorization as evidence that file reading is permitted. Then it proposes to modify a configuration file, citing the prior read as evidence that configuration access is permitted.

Each step looks like a small extension of what was already allowed. The aggregate is a model that has moved from report reading to configuration mutation using a chain of plausible-sounding reasoning steps, none of which were explicitly authorized.

The monitor checks whether the proposed delta represents a linear progression within the same authorized scope, or whether it attempts to use a prior authorization as a stepping stone to a broader authority class.

Non-linear progression triggers HOLD_REVIEW and L2 scope review.

This check is what prevents authorization creep from working through incremental reframing.

Check 4 — Artifact Integrity

The fourth check protects the artifact chain itself.

Every stage in ECHO produces a verified artifact — a JSON record with a SHA256 hash that the next stage must validate before proceeding. That chain is what makes the system's history inspectable and tamper-evident.

If a proposal would mutate a trusted artifact without a valid artifact mutation authorization, it means someone or something is trying to rewrite history. It means a prior verified state would be changed after the fact, potentially making unauthorized actions look authorized or making authorized actions look like they never happened.

This triggers HOLD_LOCKED and fails with an artifact integrity violation.

The chain is the record. The record cannot be modified by the same pathway that the record governs.

Check 5 — New Policy Artifact Creation

The fifth check is not a failure check. It is what happens when all four prior checks pass.

If a proposed state delta survives all four checks, it means a legitimate policy change has been authorized through the appropriate human review pathway. That change must still become a new, distinct, hashed artifact before it takes effect.

The accepted delta is not applied silently. It is not merged into an existing artifact. It becomes a new policy artifact with its own SHA256 hash, recorded in the artifact chain, auditable like every other state transition in the system.

This means even legitimate policy changes leave a traceable record. You can look back at any point and see what the policy was, when it changed, and what authorized the change.


Why This Module Is Different From the Rest of the Chain

Everything else in the ECHO governance chain governs actions — whether a model can check Docker availability, call an endpoint, read a file, or trigger a workflow.

The PolicyIntegrityMonitor governs the governance itself.

That distinction matters because it closes a logical gap that most governed AI systems leave open.

Consider the alternative. A system with strong action governance but no policy integrity protection can be subverted not by attacking individual actions but by attacking the rules that define what actions are allowed. A model that cannot execute a forbidden action directly might still propose a policy template update that reclassifies the action as permitted. A corrupted artifact might silently alter an adapter definition to expand its own scope. A workflow could modify memory rules to make restricted information available to future sessions.

None of those attacks go through the action governance pathway. They go around it by targeting the authority layer that the action governance pathway depends on.

The PolicyIntegrityMonitor sits underneath the action governance layer specifically to catch those attacks.

It is the reason the rest of the governance chain can be trusted.


The Threat Model It Addresses

The module is designed against three distinct threat classes.

The cooperative but mistaken model. A model that genuinely believes a policy change is necessary and proposes it through normal channels. Without the monitor, this might succeed. With it, the proposal is intercepted, the operator is informed, and human judgment decides whether the change is appropriate.

The adversarially framing model. A model that describes a policy-modifying proposal using language that makes it sound routine — repair, normalization, cleanup, configuration alignment. Without the monitor, the benign framing might cause the proposal to be approved without recognizing its actual impact. With it, the structural check catches the policy-surface contact regardless of how the proposal is described.

Environmental corruption. A corrupted artifact, a malformed packet, a timing attack, or a system failure that produces a state delta affecting trusted artifacts or authority-bearing structures without going through any model proposal at all. Without the monitor, this corruption might silently alter the system's behavior. With it, any mutation of trusted artifacts without valid authorization triggers an immediate locked hold.


What It Protects That Nothing Else Can

The PolicyIntegrityMonitor protects the thing that makes all other protections meaningful.

If authorization packets can be redefined, they stop being meaningful. If runtime envelopes can be modified without oversight, they stop being boundaries. If memory rules can be altered silently, the trust zone architecture becomes porous. If trusted artifacts can be mutated without authorization, the entire audit chain becomes untrustworthy.

All of those things are governed by policy templates, runtime configuration, adapter definitions, and artifact integrity — the exact surfaces this module watches.

It is not the most visible module in the system. It runs as a listener. Most of the time it produces no output at all, because most state transitions are ordinary action proposals that don't touch authority-bearing surfaces.

But its presence is what makes the rest of the architecture actually govern the model rather than merely appearing to.

A system without this module has governance theater. Authorization packets that a clever enough proposal pathway could eventually redefine. Envelopes that could be quietly expanded. Artifact chains that could be retroactively altered.

A system with this module has a protected authority layer. The governance structure can be inspected. It can be changed — but only through a human-authorized pathway that itself produces a verifiable artifact. The model can propose all it wants. The policy surface answers to a different authority.


One Sentence

The PolicyIntegrityMonitor is what prevents a governed AI system from being governed by the AI.
