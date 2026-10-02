---
name: pipeline
description: Assemble or update a project's development pipeline from a PITCH.md, coordinating discovery, specification, agent instructions, capability packaging, and readiness checking. Use for preparing the execution kit, not for implementing or deploying its product.
---

# Pipeline

Turn the owner's pitch into a focused, usable project kit. Coordinate the sibling skills; do not duplicate their procedures or regenerate every document for a narrow change.

## Establish the target

Identify the target directory, applicable instructions, pitch, existing kit, and requested scope. Honor explicit document locations. Otherwise use `.project/documents/` for documents and the repository root for AGENTS.md. If multiple pitches or roots conflict, resolve the ambiguity before writing. Preserve the owner's pitch and unrelated work.

Read the pitch before choosing technology, roles, or capabilities. Keep fixed, preferred, proposed, open, and deferred decisions distinct. Existing code establishes facts, not automatic requirements. Missing technical details can become discovery/spec questions; missing product intent belongs with the owner.

## Route the work

| Need | Skill | Handoff |
| --- | --- | --- |
| Missing/incomplete intent | [pitch](../pitch/SKILL.md) | Owner-input brief with explicit uncertainty |
| Existing implementation or environment facts | [discovery](../discovery/SKILL.md) | Evidence, boundaries, prerequisites, unknowns |
| Behavior, architecture, roadmap, acceptance | [spec](../spec/SKILL.md) | TASK.md and ARCHITECTURE.md |
| Execution rules and applicable agent roles | [agents](../agents/SKILL.md) | Adapted AGENTS.md and supported role definitions |
| Readiness and launch/resume handoff | [checking](../checking/SKILL.md) | Findings and KICKOFF.md |

Load a sibling's instructions when that stage is needed. Run the work sequentially yourself when delegation is unavailable or unwarranted. When authorized and useful, delegate bounded independent investigations/reviews with explicit inputs, write ownership, output, and evidence. Shared contracts must be resolved before dependent parallel work. Skill availability is not proof of multi-agent runtime support.

Discovery informs spec; spec and agents must agree before checking. Route defects back to their owner and recheck affected output. Do not loop indefinitely: stop when ready or when unresolved owner decisions/access block meaningful progress, reporting what is complete and what remains.

## Select and package capabilities

Choose the smallest set of existing skills, scripts, references, and tools needed for the project's milestones. Inspect their instructions and dependencies rather than selecting by name alone. Record source and revision when available, purpose, installation location, availability, and required credentials by name only.

Preserve resource-relative links when copying a skill and its supporting files. Include only necessary dependencies and permitted distributable content. Do not copy secrets, account history, unrelated project material, or the whole resource repository. A skill directory is not automatically discoverable: use the chosen runner's supported locations/configuration, verified from local or authoritative documentation. If the runner is undecided, provide portable role/capability descriptions and mark activation unresolved.

Selecting and copying approved local resources is distinct from installing software, connecting accounts, provisioning infrastructure, or executing paid services. Do not perform those actions merely to make the kit appear ready. Identify unavailable dependencies and the stage they block.

Keep capability inventory and environment requirements in TASK, with source/version details in the appropriate existing inventory if one exists. Do not introduce a separate manifest solely to repeat those facts. This automation skill set need not be copied into every product unless kit regeneration is required there.

## Update safely

Inspect existing documents and resources before modifying them. Preserve accepted human edits, instruction precedence, working history, and local skill customizations. Identify affected sections and conflicts; do not overwrite a fixed decision with a generated recommendation. Keep each requirement in one authoritative location and update references consistently.

Do not initialize fake execution progress. Working records are created by the implementing coordinator at setup. Mark stale verification explicitly when changed requirements invalidate it. Write LESSONS.md only from relevant verified experience; an empty project does not require invented lessons. Record other uncertainty in the specification.

## Completion levels and setup scope

Report readiness per capability and for the named next milestone:

- **Specified:** behavior, ownership, dependencies, procedures, and pass conditions are coherent.
- **Configured:** required scripts, runner definitions, checks, and environment configuration exist for the claimed capability.
- **Verified:** those mechanisms were actually exercised against a recorded revision/environment, with evidence.

A document describing a command is not configuration; a configuration file is not a successful run. Partial readiness is legitimate. For a new project, assign preview/check/runner setup to an explicit milestone and block dependent work until its gates pass. Do not demand future product code during kit preparation or call a specified preview verified.

For a request to prepare documents, deliver specified readiness and explicit setup tasks. When local pipeline configuration is also requested, generate scoped project-local configuration and verify it where authorized. This does not authorize implementing product features, installing system tools, provisioning paid infrastructure, or deployment. External access and unresolved choices remain named prerequisites.

Have checking assess all milestone gates and the mechanisms needed by the next milestone, including concurrency where claimed, pre-commit checks, and reproducible previews. Route deficiencies back to spec/agents. Report verified evidence and gaps without inflating the overall status. Keep the pipeline's own experimental maturity separate from a target project's readiness.

## Finish

Deliver the kit paths, changes, selected capabilities, checking result, and first executable assignment or explicit blockers. Ensure the startup instructions expose required findings before execution. A documentation check is not an integration test, and a ready first milestone is not a completed product. Stay within kit preparation unless implementation was separately requested.
