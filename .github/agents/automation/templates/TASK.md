# [PLACEHOLDER: project name] — project task

> Adapted from Oldcraft's `Docs/TASK.md`. This is the WHAT; repository `AGENTS.md` is the HOW. Replace every `[PLACEHOLDER: ...]` before execution. Rename domain sections to fit the project; mark optional sections not applicable with a reason or remove them and repair section references. Do not invent requirements to fill a template. Remove this note after adaptation.

Input: `.project/documents/PITCH.md`. Architecture authority: `.project/documents/ARCHITECTURE.md`. Paths below are repository-relative; adapt consistently. Record unresolved consequential decisions explicitly and keep affected tasks unready until resolved.

## 0. Mission

Deliver **[PLACEHOLDER: product and release objective]** for **[PLACEHOLDER: primary users]** so they can **[PLACEHOLDER: central valuable outcome]**.

Starting point: [PLACEHOLDER: existing implementation or new project, reusable components, and constraints].

**Focus:** [PLACEHOLDER: smallest complete outcome and highest-value qualities].

**Boundaries:** [PLACEHOLDER: intended use, deployment surfaces, and explicit non-goals]. Decision authority and stop conditions are defined in AGENTS §2.

## 1. The first complete experience

Describe the primary end-to-end journey, including its starting state and durable result. For a service or library, describe the caller's journey rather than inventing a UI.

1. [PLACEHOLDER: entry/setup and user/caller input].
2. [PLACEHOLDER: primary operation and observable feedback].
3. [PLACEHOLDER: inspect, revise, or recover from a relevant failure].
4. [PLACEHOLDER: save/export/receive result and verify it remains usable].

Representative sample: [PLACEHOLDER: fixture location and known expected outcome].

## 2. Priorities and scope

**Priority order:** [PLACEHOLDER: ranked outcomes and rationale].

**Excluded:** [PLACEHOLDER: capabilities outside this assignment/release].

P0 = required for this release; P1 = planned next priority; P2 = optional. Priority does not authorize scope expansion beyond the assigned work.

| ID | User/caller outcome | Observable pass condition | Tier | Evidence |
| --- | --- | --- | --- | --- |
| A01 | [PLACEHOLDER: outcome] | [PLACEHOLDER: measurable condition] | P0 | [PLACEHOLDER: test/capture/result] |
| A02 | [PLACEHOLDER: outcome] | [PLACEHOLDER: condition] | [PLACEHOLDER: tier] | [PLACEHOLDER: evidence] |

Release completion requires [PLACEHOLDER: required acceptance IDs and review gates]. Full-suite cadence: [PLACEHOLDER: milestones/integration triggers]. Record results in REPORT and checkpoint summaries in DEVLOG.

## 3. Project rules

- Existing behavior to preserve: [PLACEHOLDER: compatibility and migration constraints].
- Dependencies/assets: [PLACEHOLDER: reuse policy, licensing constraints, attribution location].
- References: [PLACEHOLDER: approved versus inspirational material and permitted uses].
- Naming, terminology, and localization: [PLACEHOLDER: project conventions].
- Data/privacy constraints: [PLACEHOLDER: allowed data, storage, retention, and external transmission].
- Open decisions: [PLACEHOLDER: question, affected work, and decision owner; or none].

Working permissions and autonomy belong in AGENTS; tooling limits belong in §15.

## 4. Experience and visual direction — optional

[PLACEHOLDER: applicability; omit visual requirements for projects without them].

- Approved interaction and appearance targets: [PLACEHOLDER: paths and approval status].
- Adopt: [PLACEHOLDER: concrete visual/interaction principles].
- Avoid: [PLACEHOLDER: unacceptable patterns and examples].
- Style guide: [PLACEHOLDER: existing path or M0 deliverable, including typography, colors, controls, and accessibility expectations].

Inspect references relevant to the current task. Do not treat an inspirational screenshot as a complete behavioral specification or claim owner approval for generated exploration.

## 5. Core entities and capabilities

| Entity/concept | User meaning | Required operations | Priority |
| --- | --- | --- | --- |
| [PLACEHOLDER: entity] | [PLACEHOLDER: purpose] | [PLACEHOLDER: create/use/change/remove behavior] | [PLACEHOLDER: tier] |

Variants/configuration: [PLACEHOLDER: supported options, defaults, and exclusions].

Behavioral invariants: [PLACEHOLDER: identity, ownership, timing, or other rules visible to users/callers]. Exact schemas and interface ownership belong in ARCHITECTURE; link relevant sections rather than duplicating them.

## 6. Primary production or processing pipeline

Prove one representative item through the whole path before scaling to variants or volume.

| Stage | Input | Operation/owner | Output and verification | Fallback |
| --- | --- | --- | --- | --- |
| [PLACEHOLDER: stage] | [PLACEHOLDER: input] | [PLACEHOLDER: responsibility] | [PLACEHOLDER: artifact and check] | [PLACEHOLDER: supported fallback] |

Required skills/procedures: [PLACEHOLDER: selected references, or none].

## 7. Supporting entities and integrations

[PLACEHOLDER: secondary actors, services, or content needed for the primary journey; reuse strategy, boundaries, and priorities. Omit unrelated future systems.]

## 8. Product structure and navigation

[PLACEHOLDER: screens/routes, workflow stages, modules, or service topology as appropriate; entry points, transitions, boundaries, and representative scale.]

Navigation/workflow reference: [PLACEHOLDER: diagram or concise description]. Establish the complete path before polishing individual parts.

## 9. Core interaction and behavior

### 9.1 Inputs and controls

[PLACEHOLDER: user controls or API/CLI inputs; validation, selection, keyboard/accessibility behavior where applicable].

### 9.2 State and lifecycle

[PLACEHOLDER: meaningful states, transitions, persistence, cancellation, retry, and failure semantics].

### 9.3 Feedback and results

[PLACEHOLDER: observable progress, success, errors, and resulting artifacts].

## 10. Entry points and surfaces

| Surface/entry point | Main operations | Empty/loading/error behavior | Acceptance IDs |
| --- | --- | --- | --- |
| [PLACEHOLDER: screen, command, or endpoint] | [PLACEHOLDER: behavior] | [PLACEHOLDER: states] | [PLACEHOLDER: IDs from §2] |

Include authentication/onboarding only if required by the pitch. Detailed service contracts belong in ARCHITECTURE.

## 11. Working interface and observability

[PLACEHOLDER: persistent controls, status indicators, inspectors, or service diagnostics needed while work is underway].

Testability: [PLACEHOLDER: semantic controls/stable identifiers, read-only state inspection, readiness signals, and logs appropriate to this project]. Do not substitute internal calls for UI interaction when the UI itself is under test.

## 12. Media, content, and accessibility — optional

[PLACEHOLDER: required text/audio/media, supported formats, accessibility expectations, source/production route, and validation; or not applicable].

## 13. Optional extensions

[PLACEHOLDER: named P1/P2 extensions, prerequisites, and acceptance IDs; or none]. Do not begin these until authorized and their prerequisites pass.

## 14. Technical architecture and development environment

Architecture reference: `.project/documents/ARCHITECTURE.md` — [PLACEHOLDER: relevant ownership, contract, and repository-map sections].

- Stack and supported versions: [PLACEHOLDER: runtime, framework, OS, dependencies].
- Cross-project compatibility: [PLACEHOLDER: contract versions and owners, or none].
- Quality budgets: [PLACEHOLDER: measurable latency, memory, throughput, responsiveness, or other limits and measurement environment].

| Operation | Command/procedure | Prerequisites | Ready/success signal |
| --- | --- | --- | --- |
| Install/setup | [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] |
| Local development | [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] |
| Standalone preview or sandbox | [PLACEHOLDER: command or not applicable] | [PLACEHOLDER: fixtures/services] | [PLACEHOLDER] |
| Relevant tests | [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] |
| Build/package | [PLACEHOLDER: command or not applicable] | [PLACEHOLDER] | [PLACEHOLDER: artifact and launch check] |

Preview fixtures and reset: [PLACEHOLDER: locations, scenarios, simulated versus real behavior]. Keep sample data separate from production decisions.

CI, staging, deployment, and recovery: [PLACEHOLDER: applicable checks, environments, promotion/rollback procedure, and release authority reference]. Identify unverified setup steps rather than presenting them as working.

## 15. Tools, services, and budget

| Need | Preferred tool/skill and version | Alternative | Availability/verification |
| --- | --- | --- | --- |
| [PLACEHOLDER: task] | [PLACEHOLDER: selected capability] | [PLACEHOLDER: fallback or none] | [PLACEHOLDER: verified, unavailable, or untested] |

- Setup/authentication method: [PLACEHOLDER: instructions and secret names, never values].
- Time, concurrency, and paid-service limits: [PLACEHOLDER: authorized limits and units; no paid calls if not authorized].
- Warning/stop thresholds: [PLACEHOLDER: thresholds and response].
- Job receipts, cost records, and resumption: [PLACEHOLDER: locations/procedure or not applicable].
- Known limitations: [PLACEHOLDER: verified LESSONS references and unsupported routes].

## 16. Work plan: versions, milestones, and gates

Version convention: [PLACEHOLDER: scheme, breaking-change rules, prereleases, and release identifiers]. Distinguish product, document-format, and API versions where applicable. A milestone need not equal a release.

| Milestone | Complete outcome | Target version | Dependencies | Gate |
| --- | --- | --- | --- | --- |
| M0 Setup | Initialize required records; verify tools, local environment, and evidence capture. | [PLACEHOLDER] | [PLACEHOLDER: access/decisions] | [PLACEHOLDER: setup checks and ready first assignment] |
| M1 First functional path | Prove §1 with minimal scope; identify any simulated boundary explicitly. | [PLACEHOLDER] | M0; [PLACEHOLDER] | [PLACEHOLDER: acceptance IDs and evidence] |
| [PLACEHOLDER: next milestone] | [PLACEHOLDER: user outcome] | [PLACEHOLDER] | [PLACEHOLDER] | [PLACEHOLDER] |
| [PLACEHOLDER: delivery milestone] | Verify the release candidate and hand over deliverables. | [PLACEHOLDER] | [PLACEHOLDER] | §19 complete; [PLACEHOLDER: review gates] |

Label dependencies as **decision**, **implementation**, **verification**, or **release**. Passing a simulated path does not satisfy a real-integration prerequisite.

At M0, the coordinator initializes PLAN, TODO (or combined queue), DECISIONS, DEVLOG, and REPORT under `.project/documents/`, without overwriting existing state. Enable STATS only if useful metrics and collection sources are defined in AGENTS §3. Create the style guide only if §4 requires it.

For every milestone, provide or link its starting state, action sequence, observable pass/fail conditions, environment, evidence, and required human review. Explain how it delivers or enables the central journey. Unresolved verification details must have an owning prerequisite.

First assignment: [PLACEHOLDER: outcome, relevant paths/contracts, owner, allowed scope, prerequisites, acceptance checks, exclusions, and handoff]. Refine later assignments as their prerequisites become known. Completion and continuation follow AGENTS §2, not an indefinite keep-working loop.

## 17. Verification and review

- **Primary-path test:** [PLACEHOLDER: executable procedure, starting fixture, reset, observable assertions, and result location].
- **Independent review:** [PLACEHOLDER: reviewer, evaluation criteria, cadence, and findings location].
- **Human preview/review:** [PLACEHOLDER: launch instructions, scenario, questions to assess, and required approval points].
- **Real integration:** [PLACEHOLDER: checks requiring actual services/runtime; distinguish simulated checks].
- **Release test:** [PLACEHOLDER: ordinary installation/startup of the actual candidate, clean environment/VM if appropriate, and artifact identity].
- **Security and failure checks:** [PLACEHOLDER: checks warranted by this project's exposed surfaces and risks].

Record tested revision, environment, results, and skipped checks. Pair output inspection with state checks where relevant. Fix failed required gates before declaring the milestone complete; never substitute a reviewer score for human acceptance.

### Operational gate matrix

| Check ID / purpose | Command or procedure | Trigger | Failure condition | Evidence | If unavailable |
| --- | --- | --- | --- | --- | --- |
| [PLACEHOLDER: relevant correctness/security check] | [PLACEHOLDER] | [PLACEHOLDER: pre-commit, integration, or release] | [PLACEHOLDER] | [PLACEHOLDER: result and input identity] | [PLACEHOLDER: blocker/explicit exception policy] |

Select checks for the actual stack and risks, including secret detection and targeted security review where relevant. A pre-commit requirement needs a local execution mechanism; later CI is complementary. Gate setup acceptance includes a clean case and a controlled failing case in an isolated fixture, proving the selected check detects failure.

### Reproducible preview and concurrency proof

- Preview/sandbox recipe: [PLACEHOLDER: fresh starting state, prerequisites, launch/readiness, sample, human steps, expected result, reset/shutdown, and simulated boundaries].
- Parallel-work trial, if applicable: [PLACEHOLDER: independent assignments, stable contract, isolated checkouts/data/ports, runner activation, handoffs, integration owner, and combined check].
- Readiness per mechanism: [PLACEHOLDER: specified/configured/verified and supporting evidence or blocking setup milestone]. Do not require nonexistent future code to pass setup review; do not call it verified either.


## 18. Progress documentation

Capture useful evidence, not documentation for its own sake.

- Evidence root: [PLACEHOLDER: repository-relative location].
- Fixed scenarios/views: [PLACEHOLDER: repeatable starting states, dimensions/time where relevant, or nonvisual probes].
- Capture triggers/cadence: [PLACEHOLDER: significant changes and milestone gates].
- Each record identifies UTC time, feature/task, revision, procedure, result, and artifact location.
- Demonstration output: [PLACEHOLDER: screenshots, recordings, example responses, or other appropriate evidence; omit unnecessary timelapses].
- Retention/storage limits: [PLACEHOLDER: what to preserve and when cleanup is permitted].

Set up the necessary capture/result collection during M0. Preserve relevant failure evidence. Check that recordings or exports actually completed before referencing them.

## 19. Deliverables

1. Implemented scope and reviewable version history under the repository policy.
2. [PLACEHOLDER: executable package, deployed candidate, library, or other concrete output and destination].
3. `.project/documents/REPORT.md`: implemented/verified behavior, remaining limitations, actual evidence, human-review status, and measured usage where available. Missing measurements are reported as not recorded.
4. Evidence demonstrating the primary journey and required gates from §17.
5. [PLACEHOLDER: setup, usage, support, or operational handoff material].
6. [PLACEHOLDER: applicable dependency/license/cost records, or not applicable].

Stop condition: [PLACEHOLDER: precisely what completes this assignment, distinct from permission to publish or deploy].
