---
name: discovery
description: Investigate the existing implementation, ownership, contracts, and development prerequisites relevant to a project pitch or scoped change. Produce evidence for specification work without redesigning or implementing the system.
---

# Discovery

Reduce uncertainty needed to prepare a development pipeline. Investigate the requested scope, not every file in the repository.

## Start from a question

Read the pitch, applicable project instructions, requested outcome, and relevant existing specification. Establish which facts the next stage needs: current behavior, owning code, boundary interfaces, reusable assets, verification entry points, and environmental blockers.

For a new project, say that no implementation exists and focus on supplied constraints and prerequisites. Do not invent a current-state architecture or choose a stack as if the owner had accepted it.

## Inspect economically

Begin with repository maps, manifests, entry points, targeted symbol/file searches, and relevant tests. Follow a representative path through the owning modules. Read full files only where needed to understand that path. Inspect applicable audits for decisions, but distinguish historical proposals from current code and explicit user direction.

Establish:

- What already supports the primary workflow and what does not.
- Which module owns each consequential decision, what interfaces cross boundaries, and where duplication actually appears.
- Relevant data definitions, persistence, external contracts, and compatibility assumptions.
- Local startup, preview, test, and build entry points; required services and credentials by name only.
- Existing fixtures and the limits of their coverage.
- Specific technical unknowns that require a bounded experiment rather than more reading.

Use safe, scoped checks when they materially establish a fact. Inspect commands before running them; do not start unknown setup scripts, migrations, paid calls, or production operations as incidental discovery. Report environmental failures separately from product defects. Do not install dependencies or modify implementation unless requested.

For external facts that materially affect decisions, consult authoritative sources when available and record the date/source. Do not substitute package availability or a vendor claim for verified project integration. If source access is unavailable, state what remains unverified.

## Inspect operational prerequisites

Where relevant, locate actual pre-commit/CI check entry points, runner definitions, preview launch/reset fixtures, and shared-resource configuration. Distinguish documented, configured, and exercised mechanisms. Identify whether checks detect errors or merely produce reports, which security-sensitive boundaries need targeted review, and what prevents isolated concurrent work. Do not install or activate tooling as an incidental audit step; hand off concrete setup gaps and the stages they block.

## Handoff

Produce a concise result containing:

1. Inspected scope and revision when available.
2. Relevant current capabilities and owning paths/interfaces.
3. Reuse opportunities and constraints tied to evidence.
4. Commands/checks actually run and their results; untested prerequisites clearly separated.
5. Unknowns, their consequences, and the smallest next investigation or owner decision.

Label statements as observed, tested, inferred, or proposed where ambiguity matters. Cite local paths and source references so spec can inspect only what it needs. A missing test does not prove missing behavior; a declared type does not prove support.

Return findings to the caller or the requested existing record. Create a supporting knowledge document only when the findings need a durable home; do not repeat the same report in multiple kit documents. Finish once there is enough evidence for the scoped next decision, or identify the exact blocker. The coordinator decides whether further investigation is worth the time.
