---
name: agents
description: Adapt project AGENTS.md and necessary agent-role definitions from an established specification, defining ownership, task coordination, worktree policy, working records, and review procedures. Use for execution guidance, not for changing product requirements.
---

# Agents

Adapt [the AGENTS.md template](../../templates/AGENTS.md) to the target project's actual execution environment. Keep template-relative resources available when distributing this skill.

## Read before writing

Read the pitch, TASK.md, ARCHITECTURE.md, existing applicable instructions, and available runner/tool configuration. Honor explicit destinations; otherwise write repository-root AGENTS.md and the runner's supported role-definition locations.

Preserve existing applicable rules and accepted customizations. Surface contradictions rather than silently replacing them. Do not claim generated instructions supersede higher-priority instructions or grant tool permissions.

## Configure the smallest useful team

Choose roles from the work, not a permanent roster. A coordinator may also perform small investigations or implementation; use independent review where warranted. Establish one integration owner, bounded write scopes, shared-resource owners, and handoff requirements.

Define sequential dependencies before parallel assignments. Workers need relevant contracts and acceptance criteria, not the entire project archive. Assign exclusive interactive application instances to one controller and isolate scratch files, ports, and test data where necessary.

If standalone agent definitions are useful and supported, give each its purpose, inputs, ownership, allowed writes, deliverable, verification, and escalation conditions. Reference shared policy instead of copying it into every role. Verify runner syntax from local or authoritative documentation; if the runner is unknown, retain portable role descriptions in AGENTS.md and mark activation unresolved. Do not install a runner or change global configuration.

## Project operating rules

Fill the template with actual language conventions, relevant references, commands by reference to TASK, delegation availability, review requirements, and authorized scope. Replace placeholders and remove non-applicable rules. Do not import indefinite execution, paid-service limits, or technology choices from a different project.

Keep policy in AGENTS.md, the detailed lifecycle in coordinator instructions when needed, and live branch/path assignments in working records. Define when a task needs a worktree, integration base/naming, preservation of existing work, and cleanup conditions. Do not create worktrees merely to write this policy.

Specify bounded investigation/retry behavior and stopping conditions. A role assignment is not authorization to publish, deploy, purchase, send messages, or modify accounts. Reflect existing user authorization accurately without inventing routine approval gates.

## Make coordination and checks operational

For the selected runner, distinguish portable role descriptions from loadable definitions and exercised delegation. Define a bounded activation trial when multi-agent execution is claimed: launch independent assignments in isolated task locations, collect identifiable handoffs, and perform the combined check. If the runner or delegation is unavailable, record that limitation and use sequential execution where permitted; do not report concurrency verified.

Give each assignment stable identity, prerequisite status, owner, checkout/write scope, shared-resource needs, expected result, and evidence. Keep that state in the existing task record. The coordinator dispatches only ready work, assigns exclusive resources once, checks each handoff's revision, and verifies the integrated result. Worktree isolation does not isolate ports, databases, or external services automatically.

Translate TASK's check matrix into an explicit commit/integration policy. The implementer runs required pre-commit checks on the intended changes, inspects the diff for accidental files/secrets, and records results. New relevant edits require affected checks to run again. Required failures or unavailable checks block the corresponding gate until resolved or handled under an explicit recorded exception policy; never silently bypass a check.

Identify the concrete local check entry point and how it is invoked before commits. When configuration is in scope, wire supported repository-local hooks or runner procedures and complementary CI checks as appropriate. Do not claim a gate is installed merely because AGENTS.md describes it, and do not claim a local hook is impossible to bypass. Heavier security/integration checks retain their own triggers. Agent review supplements executable checks; it is not evidence that no vulnerabilities exist.

## Working records and continuity

Name each required record, its owner, creation trigger, and update trigger. Use PLAN/TODO, DECISIONS, DEVLOG, and REPORT only as needed; a combined plan/queue is acceptable if references remain consistent. Enable statistics only when useful metrics and collection sources exist.

Distinguish first initialization from resume: the implementation coordinator creates missing initial records at setup, but preserves progress and recovers missing state on later runs. Never prefill completed milestones or owner approvals. Separate unknown measurements from zero.

Hooks, if configured later, can remind agents to read or update state; they do not prove records are accurate. Do not add always-running agents, recurring jobs, or never-stop hooks as an incidental part of configuration.

## Check and hand off

Confirm paths and document-section references, role ownership, handoff evidence, first-run behavior, and consistency with TASK/ARCHITECTURE. Ensure routine workers can discover necessary policy without loading every knowledge file.

Deliver AGENTS.md and any requested/supported role definitions, listing unavailable runner capabilities and unresolved policy choices. Do not initialize execution history, alter product code, or modify the pitch/specification to make the rules easier to write.
