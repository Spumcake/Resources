---
name: spec
description: Create or revise TASK.md and ARCHITECTURE.md from a project pitch and discovery evidence, defining behavior, ownership, contracts, environments, roadmap, and acceptance criteria. Use for implementation specifications, not product code or deployment.
---

# Spec

Produce a coherent execution specification with one authoritative home for each requirement. Adapt [TASK.md](../../templates/TASK.md) and [ARCHITECTURE.md](../../templates/ARCHITECTURE.md); resolve template links relative to this skill. Preserve these dependencies when distributing it.

## Inputs and authority

Read the pitch, applicable instructions, relevant discovery findings, and existing specifications. Respect explicit destinations; otherwise write both files under `<target>/.project/documents/`. Ask for a target when ambiguous.

Preserve fixed owner decisions. Label preferences, proposals, unknowns, and deferred work. Use supplied discovery evidence or perform a narrowly scoped check if needed; request [discovery](../discovery/SKILL.md) for substantive investigation rather than inventing implementation facts. A sibling reference is not permission to spawn agents automatically.

Resolve consequential contradictions with the owner. Continue independent sections and explicitly block affected tasks when a decision is missing. Do not fill gaps with assumptions that change the product's purpose, external commitments, or accepted architecture.

## Divide the documents

**TASK.md owns:** user/caller journeys, required behavior, priorities/exclusions, presentation targets, environment commands, budgets, version conventions, milestone dependencies, acceptance criteria, human review, and delivery conditions.

**ARCHITECTURE.md owns:** current and target structure, repository map, authoritative components, data and persistence, interfaces, runtime flows, trust boundaries, and verification seams.

Keep the documents consistent through references rather than duplicate schemas or requirements. Operational authority and agent procedures belong in AGENTS.md, which the [agents](../agents/SKILL.md) skill prepares. Do not replace that file during specification work.

## Make the specification usable

- Scale the templates to the project. Rename domain headings, remove irrelevant optional topics, and repair section references. Replace scaffold placeholders with concrete content or explicit open/not-applicable statements. Do not require UI, auth, billing, hosted services, or multi-agent execution for every project.
- Trace the first complete journey to its owning operations and acceptance evidence. Specify meaningful failure/recovery cases and preserve required existing behavior.
- Identify one authority for each important decision and state store. Distinguish references from ownership, transient state from persistence, and current code from accepted/proposed changes.
- Link canonical schemas and interfaces where they exist. Specify missing contracts sufficiently for independent work; mark unsettled contracts before dependent tasks start.
- Define local development and representative preview/sandbox scenarios, including what is simulated. Keep fixture data out of production decision logic. State which checks require real services or the packaged application.
- Identify setup, testing, build, staging, release, and recovery procedures only where applicable. Verify available commands when safe and useful; otherwise label them planned or untested. Do not provision infrastructure or expose secrets.
- Express performance/security requirements appropriate to actual risks and user constraints. Unknown thresholds remain decisions, not fabricated measurements.
- Define the project's version convention and compatibility promises. Distinguish release, API, and document-format versions where needed.

## Roadmap and first assignment

Use bounded milestones delivering observable outcomes. Label dependencies as decision, implementation, verification, or release; check that their order is possible. Do not let simulated success satisfy a real-integration gate.

Define setup responsibilities and the first functional slice. The first assignment needs an owner role, relevant paths/contracts, prerequisites, allowed scope, exclusions, acceptance checks, and expected handoff evidence. Plan later milestones at useful resolution without manufacturing every future task.

Acceptance conditions should name starting state, action, expected result, evidence, and required environment. Separate implemented, verified, human-reviewed, and released status. Define human previews for subjective decisions and ordinary startup checks for distributed applications.

## Operational acceptance, not just descriptions

For **every** milestone, identify the outcome, dependency IDs, starting fixture/state, actions, observable pass/fail conditions, verification environment, evidence artifact, and required human review. Map milestones to the central journey or explain their enabling role. Reject vague gates such as “UI complete,” “secure,” or “tests pass” without the relevant checks and conditions. Detailed future commands may remain planned, but unresolved conditions must have an owner and a resolving prerequisite.

Define a project check matrix: check ID, purpose/risk, command or procedure, trigger, failure condition, evidence, and behavior when unavailable. Include appropriate syntax/type checks, focused tests, build checks, secret detection, and risk-specific security review. Select tools for the actual stack; do not invent universal scanner requirements. Separate checks required **before commit** from heavier pre-integration and pre-release checks. A later CI run does not satisfy a pre-commit requirement. Name existing known findings and their disposition rather than silently treating them as passes.

Define preview reproduction as an acceptance scenario: clean starting state, prerequisites, exact launch procedure, readiness signal, sample data, user steps, expected result, reset and shutdown. State simulated boundaries, external-service requirements, and resource isolation. For nonvisual projects use a caller sandbox or reproducible example. The first environment milestone must prove this before dependent review work is called ready.

Where parallel implementation is intended, specify independent assignments, shared-contract prerequisites, exclusive resources, integration owner/order, and the combined regression check. A dependency list alone does not establish safe concurrency.

## Revision and delivery

Preserve accepted human edits and execution history. Update affected cross-references and flag changed requirements that invalidate prior evidence; do not rewrite historical test results. Review both documents together for incompatible terminology, ownership, versioning, or milestone claims.

Deliver their locations, the first ready task or blocking questions, and material proposals still awaiting a decision. A specification may be useful while not yet execution-ready. Do not mark proposals approved or start product implementation as part of writing it.
