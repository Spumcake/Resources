# [PLACEHOLDER: project name] — architecture

> Project-agnostic template accompanying `AGENTS.md` and `TASK.md`. Replace every `[PLACEHOLDER: ...]` before using this as an implementation reference. Include only structure needed by the agreed scope. Mark optional topics not applicable with a reason or remove them and repair section references. Do not invent subsystems to fill the template. Remove this note after adaptation.

This document owns system structure, data ownership, and technical contracts. `.project/documents/TASK.md` owns product behavior, priorities, environment commands, milestones, and acceptance criteria. Repository `AGENTS.md` owns agent working procedures. Paths here are repository-relative; adjust consistently for the target layout.

**Architecture baseline:** [PLACEHOLDER: date and inspected revision, or new project with no implementation]. Label each significant design **current**, **accepted target**, or **proposed**. Current means evidenced in code, not necessarily verified. Record departures from the implementation explicitly.

## 0. Scope and constraints

System responsibility: [PLACEHOLDER: concise technical responsibility supporting TASK §1].

Inside the boundary: [PLACEHOLDER: applications, libraries, processes, and data owned here].

Outside the boundary: [PLACEHOLDER: callers, external services, other repositories, and responsibilities owned elsewhere].

Design constraints: [PLACEHOLDER: constraints that materially determine structure, with references to TASK or decisions]. Do not repeat the full product brief, stack version list, or roadmap.

## 1. System overview

[PLACEHOLDER: small diagram or concise flow showing callers, major components, data stores, and external systems; label each connection and distinguish in-process calls from process/network boundaries].

| Component | Responsibility | Runtime/process | Status and evidence |
| --- | --- | --- | --- |
| [PLACEHOLDER: component] | [PLACEHOLDER: single owned responsibility] | [PLACEHOLDER: where it runs or library consumer] | [PLACEHOLDER: current/accepted target/proposed and source or decision] |

Do not imply a separate service or package for every responsibility. State which components share a process and which can fail or deploy independently.

## 2. Ownership and dependency rules

| Decision or behavior | Authoritative component | Interface used by consumers | Must not be duplicated in |
| --- | --- | --- | --- |
| [PLACEHOLDER: behavior] | [PLACEHOLDER: owner] | [PLACEHOLDER: contract from §5] | [PLACEHOLDER: other components] |

Allowed dependency direction: [PLACEHOLDER: permitted imports/calls and boundary restrictions].

Shared code versus project-specific code: [PLACEHOLDER: shared responsibilities, consumers, and distribution mechanism; or none].

Enforcement: [PLACEHOLDER: relevant module boundaries, checks, or review procedure]. If an interface is insufficient, extend the owning contract rather than introducing a fallback copy of its decisions in another component.

## 3. Repository map

| Path | Purpose and owner | Entry point or relevant contract |
| --- | --- | --- |
| [PLACEHOLDER: repository-relative path] | [PLACEHOLDER: responsibility] | [PLACEHOLDER: starting file or contract reference] |

Generated artifacts and their source: [PLACEHOLDER: paths, generator, and regeneration authority; or none].

Tests, fixtures, adapters, and configuration locations: [PLACEHOLDER: concise path references]. Mark proposed paths as planned rather than claiming they exist. Task branches/worktrees and current worker assignments belong in AGENTS and working records, not this map.

## 4. Data model and persistence

| Entity/state | Identity and key fields | Relationships and lifecycle | Authoritative owner/store |
| --- | --- | --- | --- |
| [PLACEHOLDER: entity] | [PLACEHOLDER: ID and meaningful fields] | [PLACEHOLDER: ownership versus references, multiplicity, deletion] | [PLACEHOLDER: component and persistence mechanism] |

Canonical schemas: [PLACEHOLDER: schema/type definitions or planned contract location]. Link to exact definitions when available instead of maintaining a second field-by-field schema here.

- Persistent versus transient state: [PLACEHOLDER: what survives restart and what is derived/session-only].
- Mutation boundary: [PLACEHOLDER: writer, validation, transaction/atomic-save behavior, and rollback on failure].
- Concurrent changes: [PLACEHOLDER: revisions, locking, conflict handling, or why there is only one writer].
- Identity and reuse: [PLACEHOLDER: rename, move, copy, deletion, and missing-reference semantics relevant to this project].
- Storage resolution: [PLACEHOLDER: file paths, object locators, database relationships, or other applicable rules].
- Recovery and retention mechanisms: [PLACEHOLDER: how accepted TASK requirements are implemented; or not applicable].

Avoid equating visual nesting, storage nesting, and ownership unless the model explicitly makes them the same.

## 5. Interfaces and contracts

| Contract | Owner → consumers | Transport/call boundary | Canonical definition | Compatibility |
| --- | --- | --- | --- | --- |
| [PLACEHOLDER: contract ID/name] | [PLACEHOLDER: parties] | [PLACEHOLDER: function, event, IPC, HTTP, file, etc.] | [PLACEHOLDER: source path or planned specification] | [PLACEHOLDER: version/reference] |

For each consequential boundary, specify or link:

- Inputs, outputs, validation, and authorization responsibility.
- Error categories and how callers observe them.
- Side effects, ordering, and synchronous versus asynchronous completion.
- Timeout, cancellation, retry, and duplicate-request behavior where applicable.
- Compatibility expectations and contract checks.

[PLACEHOLDER: fill the relevant details for the listed contracts, or link their authoritative definitions]. Do not select a transport or event system merely because this template lists it.

## 6. Primary flow and state transitions

Trace TASK §1 through the components and contracts above. Include the normal path and the most consequential failure path.

| Step | Trigger/input | Owning component and contract | State change/output | Failure handling |
| --- | --- | --- | --- | --- |
| [PLACEHOLDER: step] | [PLACEHOLDER: input] | [PLACEHOLDER: owner/reference] | [PLACEHOLDER: effect] | [PLACEHOLDER: observable result/recovery] |

Lifecycle/state machine: [PLACEHOLDER: meaningful states, valid transitions, and their owner; a diagram or table if useful].

Startup/shutdown and interruption: [PLACEHOLDER: initialization order, readiness, cleanup, and recovery after interruption relevant to this flow]. Product-visible behavior belongs in TASK; this section explains which mechanisms realize it.

## 7. Runtime environments and external integrations

| Environment | Real components | Replaced or simulated boundaries | Configuration/data isolation |
| --- | --- | --- | --- |
| [PLACEHOLDER: local, preview, test, staging, or production as applicable] | [PLACEHOLDER] | [PLACEHOLDER: explicit adapters or none] | [PLACEHOLDER] |

- Configuration ownership and precedence: [PLACEHOLDER: where configuration is loaded, validated, and passed; names only for secrets].
- External integration boundary: [PLACEHOLDER: adapter/provider responsibilities and how vendor details remain contained; or none].
- Deployment units and connectivity: [PLACEHOLDER: process/package topology and required connections].
- Health/readiness and resource lifecycle: [PLACEHOLDER: signals and owners].

Preview fixtures supply representative data and responses; they do not independently implement authoritative business rules. Where possible, use the same portable domain implementation. Installation, startup, build, and deployment commands remain in TASK §14.

## 8. Trust boundaries and access — when applicable

[PLACEHOLDER: exposed surfaces, untrusted inputs, sensitive data, and applicability].

| Boundary/resource | Caller identity | Authorization and validation owner | Protection mechanism |
| --- | --- | --- | --- |
| [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] |

Isolation and secret access: [PLACEHOLDER: tenant/project/process isolation and credential-loading boundaries, without credential values].

Logging/redaction: [PLACEHOLDER: what may be recorded and where sensitive values are excluded]. Specify mechanisms required by the project's risks; do not invent authentication or multi-tenancy for projects that do not need them. Verification requirements belong in TASK §17.

## 9. Reliability, performance, and observability

Quality targets are authoritative in TASK §14. Explain the mechanisms that support them:

| Relevant target/failure | Mechanism | Owner | Evidence/probe |
| --- | --- | --- | --- |
| [PLACEHOLDER: target reference or failure mode] | [PLACEHOLDER: chosen design] | [PLACEHOLDER] | [PLACEHOLDER: observable state/metric] |

Long-running jobs, queues, concurrency limits, caching, or background work: [PLACEHOLDER: only applicable mechanisms, including cancellation/recovery and cache invalidation if used; or none].

Diagnostics: [PLACEHOLDER: structured events, correlation identifiers, error reporting, and inspection interfaces]. Keep successful completion distinguishable from submission or partial progress.

## 10. Verification boundaries

| Architectural rule/contract | Appropriate check | Real versus simulated dependencies | Check/fixture location |
| --- | --- | --- | --- |
| [PLACEHOLDER: invariant or contract] | [PLACEHOLDER: unit, contract, integration, UI, persistence, or packaged-runtime check] | [PLACEHOLDER] | [PLACEHOLDER: existing/planned path] |

Deterministic setup/reset: [PLACEHOLDER: fixture ownership and state-reset mechanism].

Inspection interfaces: [PLACEHOLDER: read-only state, rendering/output capture, and test entry points; or none]. An internal operation check does not prove the UI interaction works; a simulated integration does not prove the external service works.

This section identifies test seams and ownership. Acceptance thresholds, commands, review gates, and recorded results remain in TASK and execution records.

## 11. Evolution and open decisions

Compatibility ownership: [PLACEHOLDER: canonical API/schema/package versions, producer/consumer responsibility, and links to definitions]. Release-number convention remains in TASK §16.

Migration from the current implementation: [PLACEHOLDER: affected data/contracts, transition mechanism, compatibility window, and recovery implications; or not applicable]. Do not present the target design as already implemented.

| Unresolved question | Affected boundary/task | Evidence needed | Decision owner |
| --- | --- | --- | --- |
| [PLACEHOLDER: question or none] | [PLACEHOLDER] | [PLACEHOLDER: bounded investigation] | [PLACEHOLDER] |

Decision history: `.project/documents/DECISIONS.md`. Keep accepted architecture here and rationale/history there. When implementation changes ownership or a contract, update its canonical definition and this map together; record verification separately. Do not copy the roadmap or live work queue into this document.
