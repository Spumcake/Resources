# Changelog

## Version convention

Resources uses `MAJOR.MINOR.PATCH` with proof-of-concept prereleases named `MAJOR.MINOR.PATCH-poc.N`.

- `0.x` is experimental: workflows and generated-document conventions may change. No compatibility guarantee is implied; migration-impacting changes are called out here.
- During the proof of concept, increment `poc.N` for the next published iteration of the same intended release.
- Increment MINOR for a new capability set or a material workflow/template contract change; PATCH for compatible corrections after a base release.
- After 1.0, increment MAJOR for incompatible public resource/workflow contracts, MINOR for compatible additions, and PATCH for compatible fixes.
- Git release tags, when created, use `v` followed by the version. A changelog entry or tag does not establish operational verification.

Version applies to the resources bundle, not the applications it prepares. Project readiness is reported separately as **specified**, **configured**, or **verified**, tied to evidence. No stable release or 1.0 claim will be based on structural validation alone.

## 0.1.0-poc.1 — 2026-10-02

**Status: proof of concept; full pipeline unverified.** Initial publication for a subsequent example-project trial. No complete pitch-to-implementation run has been demonstrated.

### Added

- Six project-agnostic skills: pitch, pipeline, discovery, spec, agents, and checking.
- PITCH.md, TASK.md, ARCHITECTURE.md, and AGENTS.md templates with contextual placeholders.
- Pitch example and README usage instructions, including cloning resources into a target project's `.project/resources`.

### Strengthened before initial publication

- Separate specified, configured, and verified readiness; report missing setup without inventing evidence.
- Require observable acceptance conditions for every milestone and trace the roadmap to the central user journey.
- Identify operational concurrency prerequisites, runner activation, isolated resources, and integration evidence.
- Define pre-commit versus integration/release checks, blocking failures/unavailable checks, and evidence identity.
- Require reproducible preview recipes and controlled failure checks when mechanisms exist and execution is authorized.
- Preserve the boundary between kit preparation and product implementation while allowing explicitly requested local pipeline configuration.

### Validation and limitations

- Skill frontmatter and names validated; local resource references and template section references checked.
- Pitch and PITCH/ARCHITECTURE templates retain their prior content in this iteration.
- Operational preview, check effectiveness, concurrent execution, and complete example-project acceptance remain unverified.
- No default reusable subagent roster or executable dependency scheduler is included.
