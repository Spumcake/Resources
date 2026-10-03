---
name: systems
description: Create or revise SYSTEMS.md with system boundaries, data ownership, contracts, runtime environments, and targeted findings about existing code. Use for technical design needed to partition implementation, not product code or a full repository audit.
---

# Create the systems document

Adapt [the template](templates/SYSTEMS.md) from the archived ARCHITECTURE procedure. Respect the explicit destination or existing canonical document; default to `<target>/.project/documents/SYSTEMS.md`. If ARCHITECTURE.md exists, use it as source evidence and deliberately migrate its applicable content and references to SYSTEMS.md when authorized. Do not maintain two technical authorities or delete the old file silently.

Read the pitch, relevant INTERFACE.md sections, applicable instructions, and existing technical contracts. Inspect only code needed to answer concrete questions about the requested scope. Search symbols and targeted sections rather than surveying the entire codebase. Existing behavior is evidence, not automatically a requirement. Label current, accepted target, and proposed structure accurately.

Define one authoritative owner for important behavior and state. Describe data identity, persistence, mutation, meaningful failure/recovery, and interfaces sufficiently for independent workers to implement against them. Link canonical schemas rather than duplicating them. Specify only relevant trust boundaries and external integrations; do not invent services, auth, queues, or packages to fill headings.

Map relevant source paths and allowed dependencies. Identify shared contracts that must be settled before parallel assignments start. Keep product intent in PITCH, presentation in DESIGN, milestone sequencing and acceptance in TASK, and working procedures in AGENTS.

Describe the minimal local and preview environment, real versus simulated boundaries, and applicable build/release topology. A preview should be usable without unrelated production services where feasible; fixtures must not become a second implementation of business rules. Leave commands and reproduction steps in TASK.

Remove irrelevant template sections. Record material unknowns with the affected boundary and the next bounded investigation; do not fabricate certainty or block unrelated work. If defining test recommendations, consult [tests](../../tasks/tests/SKILL.md) and identify only meaningful verification seams.

Check ownership, contract consistency, and references needed for the next increment. Save the document and report what can now be partitioned and what remains blocked. Do not implement the product. Return concise outcome/evidence for the Coordinator's consolidated audit when delegated; do not automatically create a separate audit.
