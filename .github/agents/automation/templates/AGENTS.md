# AGENTS.md — [PLACEHOLDER: project name]

You are implementing [PLACEHOLDER: project and current objective]. The specification is `.project/documents/TASK.md`; ownership and contracts are in `.project/documents/ARCHITECTURE.md`.

> Before using this as project instructions, replace every `[PLACEHOLDER: ...]`, resolve required decisions, and remove non-applicable optional requirements. Paths are relative to the target repository root; adjust them consistently if the project uses another layout. Do not execute this unfilled template. Remove this note after adaptation.

**Language:** [PLACEHOLDER: language conventions for code, documentation, UI, and communication].

## 1. After every start, restart, or context compaction

Read, in order:

1. This file.
2. `.project/documents/TASK.md` and the relevant sections of `.project/documents/ARCHITECTURE.md` on first entry; on resume, review changed requirements and the current assignment.
3. `.project/documents/PLAN.md` and `.project/documents/TODO.md` for the current milestone and prioritized queue.
4. The last three entries of `.project/documents/DEVLOG.md`, relevant decisions, and `.project/documents/STATS.json` if metrics are enabled.
5. Before appearance- or content-dependent work, the approved references specified in TASK §4.
6. Read the current time using [PLACEHOLDER: available time tool/command]; record checkpoints in UTC.

**First initialization:** follow TASK §16 to create required missing working records. Do not try to read files that have not yet been initialized. On resume, preserve existing records; report or recover missing state instead of silently resetting progress.

Record consequential decisions and handoffs on disk. Read supporting knowledge selectively; do not repeatedly survey the whole repository.

## 2. Autonomy

- Decision authority and human availability: [PLACEHOLDER: what may be decided independently, what requires direction, and how to contact the owner]. Record consequential decisions and their reasons in `.project/documents/DECISIONS.md`; distinguish proposals from accepted decisions.
- Work through the authorized queue. Stop or checkpoint when [PLACEHOLDER: deliverable completion, time/spend limits, or blocking conditions]. An empty queue does not authorize inventing more scope.
- Tool failure policy: [PLACEHOLDER: retry limit, backoff, fallback, and escalation]. Inspect the actual state before retrying operations that may already have succeeded.
- Investigation timebox: [PLACEHOLDER: limit and expected checkpoint]. If exhausted, record evidence and the smallest unresolved question; continue independent authorized work where possible.

## 3. Records and cadence

The coordinator owns shared working records; workers supply concise handoffs. Required records and optional metrics are selected during M0.

| Record | Initialization and maintenance |
| --- | --- |
| `PLAN.md` | Initialize milestones/current milestone from TASK; update after integration and scope changes. |
| `TODO.md` | Initialize bounded assignments and dependencies; update after completion or review. May be merged into PLAN if all references are updated consistently. |
| `DECISIONS.md` | Append consequential decisions with reason and authority. |
| `DEVLOG.md` | Append UTC entries at milestones, handoffs, recovered failures, and [PLACEHOLDER: additional cadence]. |
| `REPORT.md` | Start at M0; update at delivery gates with actual results and limitations. |
| `STATS.json` — optional | [PLACEHOLDER: enable/omit; metrics, units, collection source, update cadence]. Unknown measurements are unknown, not zero. |

These records live under `.project/documents/`. Evidence locations and capture requirements are defined in TASK §18. Preserve history; do not copy the same state into multiple trackers.

## 4. Orchestration

Delegation mechanism and concurrency limit: [PLACEHOLDER: available runner, role definitions, and worker limit; or single-agent execution]. Use only roles justified by the task, with one owner per shared resource.

| Role | Owns | Allowed write scope | Handoff |
| --- | --- | --- | --- |
| Coordinator / integrator | Queue, shared contracts, integration, working records | [PLACEHOLDER: paths and shared resources] | Integrated result and evidence |
| [PLACEHOLDER: implementation role] | [PLACEHOLDER: bounded subsystem/deliverable] | [PLACEHOLDER: checkout and paths] | Changed revision, checks, limitations |
| Reviewer / verifier | Independent acceptance checks | [PLACEHOLDER: evidence location and permitted edits] | Findings tied to tested revision |

- Give each assignment its outcome, prerequisites, relevant contracts, scope, and verification criteria.
- Only the designated owner may mutate [PLACEHOLDER: exclusive application instances, environments, or other shared resources].
- Isolate task scratch files, ports, and test data. Run independent batch work concurrently only when its resource use permits it.
- Task worktree/branch policy: [PLACEHOLDER: when isolation is required, naming convention, base branch, and lifecycle procedure]. Work inside the assigned checkout; do not alter another worker's checkout.
- Integration handoffs use [PLACEHOLDER: queue/record location]. Record cross-repository revisions when applicable. Retire a checkout only after preserving its work and accounting for remaining changes and processes.

## 5. Keep the primary workflow working

- From [PLACEHOLDER: first functional milestone] onward, TASK §1's primary workflow must remain functional in the integration branch. Run TASK §17's checks after relevant integration batches.
- If integration breaks it, use [PLACEHOLDER: repair timebox and revert/requeue procedure]. Preserve unrelated and uncommitted work; never reset another task to recover your own change.
- Checkpoint policy: [PLACEHOLDER: commit cadence, branch/review rules, and milestone tags]. Do not rewrite or force-push shared history without explicit authorization.

## 6. External services and content discipline

Apply this section only to services and content required by TASK §§3 and 15.

- Use the approved tools/providers and limits; no mass calls or speculative paid work.
- Record paid operations in [PLACEHOLDER: receipt/cost record path]: time, provider, operation, request ID, purpose, cost or credits, result, and output location. Preserve useful inputs and outputs under the retention policy.
- A polling timeout is not proof of failure. Resume by request ID; resolve uncertain submissions before issuing another potentially duplicate operation.
- Attempt limit and fallback: [PLACEHOLDER: limits per operation/content stage].
- External assets/dependencies: record source, version where applicable, and license in [PLACEHOLDER: attribution/dependency record].
- For generated content, validate one representative output against approved references and technical constraints before scaling production. Required stages: [PLACEHOLDER: workflow reference, or not applicable].

## 7. Verification

- Implementers run relevant checks. Independent review policy: [PLACEHOLDER: reviewer scope, gates, and human-review requirements].
- Status words: **implemented**, **automatically verified**, **integration verified**, **pending human review**, **human reviewed**, **released**. State the evidence supporting each claim; do not infer human approval.
- Inspect every capture you describe. Use both observable output and state checks where appropriate; a screenshot alone does not prove persistence or integration.
- Gate requirements come from TASK §§2 and 17. Report failures and skipped checks explicitly. Do not weaken acceptance criteria or update reference outputs merely to hide a regression.

### Before commit and integration

- Required check matrix and command entry point: [PLACEHOLDER: TASK reference, local command, and hook/runner invocation mechanism].
- Before committing, inspect the intended diff and run required pre-commit checks on those changes. Rerun affected checks after further edits. Record the tested revision or input identity and results.
- Failure/unavailable-check handling: [PLACEHOLDER: blocking policy, named existing findings, and explicit exception authority]. No silent skips or bypasses; CI after push does not satisfy a before-commit requirement.
- Integration/release checks: [PLACEHOLDER: references to heavier gates and their triggers]. Security review complements the appropriate executable checks; neither establishes absence of all vulnerabilities.
- Gate activation status: [PLACEHOLDER: specified/configured/verified, with evidence]. A written instruction is not an installed hook.


## 8. Environment and tool practice

- Setup, preview, test, and build commands are authoritative in TASK §14. Verify the target project/instance before controlling an application or service.
- Wait for observable readiness or job status rather than retrying blindly after a timeout. Inspect logs and blocking dialogs where relevant.
- Long-running work: [PLACEHOLDER: background-job procedure, status polling, and output locations]. Stop only task-owned processes by their recorded identity.
- Restore test input devices, temporary configuration, and resources after checks. Keep fixture data outside production behavior.
- Validate packaged/exported results independently of the source development directory when applicable.
- Stack-specific practices and known limitations: [PLACEHOLDER: concise rules or links into LESSONS.md/knowledge; distinguish verified advice from untested approaches].
- Change test harnesses and hooks deliberately, outside active runs; record changes and rerun affected checks. Write completion markers only after actual verification.

## 9. Boundaries

- Authorized repositories, paths, and external resources: [PLACEHOLDER: scope].
- Push, publish, deploy, account-change, and purchase authority: [PLACEHOLDER: permitted actions and approval boundaries]. Role assignment does not itself grant these permissions.
- Keep secrets in [PLACEHOLDER: approved secret mechanism]. Never include values in logs, fixtures, prompts, or committed files.
- Preserve existing user work and project ownership boundaries. If a required interface is insufficient, explain the smallest change needed rather than duplicating behavior across layers.
