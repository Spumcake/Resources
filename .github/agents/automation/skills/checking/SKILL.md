---
name: checking
description: Review a development pipeline kit for consistency, traceability, dependencies, environment readiness, and executable first-task handoff; produce findings and KICKOFF.md. Use for kit readiness, not as a claim that the product itself has passed testing.
---

# Checking

Evaluate whether another agent can undertake the specified next milestone and whether a human can inspect its result. A plausible document set is not enough, but missing future product code is not a defect in a preparation kit.

## Establish scope

Read the pitch, TASK.md, ARCHITECTURE.md, AGENTS.md, selected capability inventory, and relevant findings. Honor explicit paths; default documents live under `.project/documents/`. Inspect the actual target and report the reviewed revision/date when available.

Compare against owner intent independently of the author's completion claims. If performed by the same agent that wrote the kit, disclose self-review; do not present it as independent verification. A fresh reviewer can perform this skill when delegation is authorized.

## Review the kit

- **Intent:** fixed pitch decisions preserved; proposed choices and exclusions visible; no unrequested scope or claimed approvals.
- **Traceability:** primary journey has acceptance evidence; significant features have owners and milestone placement; conditions and measurements are meaningful.
- **Consistency:** terms, data ownership, interfaces, paths, versions, and current/target status agree. No duplicated authoritative behavior or contradictory requirements.
- **Dependencies:** decision/implementation/verification/release prerequisites are explicit and not circular. The first assignment can start or identifies exactly what prevents it.
- **Environment:** setup, preview/reset, testing, build, and applicable release procedures identify prerequisites and distinguish planned commands from verified ones.
- **Capabilities:** selected resources and relative references exist; needed supporting files accompany skills; runner loading and tool/credential availability are stated rather than assumed.
- **Execution:** initialization versus resumption, coordinator/worker handoffs, exclusive resources, budgets, stopping conditions, and preservation of existing work are defined.
- **Review:** real versus simulated evidence is distinct; human review is actionable; delivery and release authority are not conflated.

Search generated documents for unfilled scaffold placeholders, broken references, unsupported completion claims, and copied project-specific residue. Explicit open questions are valid; assess whether they block the next milestone. Template placeholders in the reusable source templates are expected, not defects.

Use safe, relevant read-only or isolated checks to verify setup claims when possible. Inspect commands before executing them. Do not run deployments, migrations, paid requests, installers, or product-changing operations just to review a kit. Report unavailable checks and their impact. Do not label a browser mock as a working desktop/service integration.

## Operational proof and readiness levels

Review every milestone's starting conditions, actions, pass/fail criteria, environment, evidence, dependencies, and required human review. Trace the milestone sequence back to the pitch's central user journey. Flag milestones that add unrelated scope or omit a necessary part of that journey.

For each relevant capability, distinguish **specified**, **configured**, and **verified**. A plan or documented command is specified; actual configuration is configured; only observed execution with recorded evidence is verified. Report self-review honestly. A new project can be ready for setup while its future preview or concurrency remains unverified.

When mechanisms exist and safe execution is authorized, check:

- **Preview reproduction:** follow instructions from a fresh isolated starting state, load the named scenario, exercise the documented interaction, and verify reset/shutdown. Record prerequisites and simulated services. For nonvisual projects exercise the equivalent caller example.
- **Check effectiveness:** inspect the command/trigger and run a clean case plus a controlled relevant failing case in an isolated disposable copy. Confirm the intended failure is detected and prevents the prescribed next step. Never inject failures or secrets into the user's active work; use benign synthetic test inputs. Remove trial changes. A scanner finding no issues is not proof it detects the selected risk.
- **Concurrency:** where claimed, use authorized runner capabilities for a bounded pair of independent assignments, inspect resource isolation and handoffs, and verify their integrated result. Role files alone prove neither activation nor concurrency.
- **Evidence identity:** associate checks with revision or input hashes and environment. Later relevant changes invalidate affected evidence. Distinguish pre-commit, pre-integration, and release checks; do not let success at one trigger stand in for another.

If a mechanism does not yet exist, verify the milestone tasked with creating it and its dependencies instead of fabricating operational evidence. If execution is unavailable or outside scope, state the exact check not performed and whether it blocks the next milestone. Do not expand preparation into product implementation to obtain a green result.

## Findings and correction

Report actionable findings with location, evidence, consequence, and owning skill/decision maker. Distinguish blockers for the next milestone from later prerequisites and optional improvements. Avoid stylistic churn that does not improve execution readiness.

Return product/specification changes to their owner; do not lower acceptance criteria to pass the review. Correct trivial links or formatting only within authorized scope, then recheck affected references. Repeated substantive failures require a concrete unresolved question, not an endless rewrite loop.

Use one concise findings record or the caller's existing report rather than creating overlapping audit files. Keep historical execution evidence unchanged.

## Handoff

Create or update `.project/documents/KICKOFF.md` unless the user requested review-only. Keep it short and derive it from actual paths and verified capabilities:

1. **Kickoff:** target, required reading, first milestone/assignment, prerequisites, and its stopping condition.
2. **Resume:** read existing plan/queue, recent checkpoints and relevant decisions; inspect current state before continuing; never reset progress.
3. **Status:** completed and verified behavior, current work, blockers, and available usage evidence, followed by continuation only within scope.
4. **Wrap-up:** checkpoint authorized work, run relevant checks, report limitations, and stop; do not imply release permission.

If blockers remain, make them prominent before the kickoff prompt. Do not tell an agent to begin dependent implementation until those conditions are resolved. Do not invent special runner commands, hooks, tools, or installed skills.

Conclude with **ready for the named next milestone**, **ready only for named unblocked preparation**, or **blocked pending named decisions/prerequisites**. Explain the evidence and limitations. Kit readiness is not product acceptance, human approval, or release authorization.
