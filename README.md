# Resources

Reusable roles and skills for focused development. [AGENTS.md](AGENTS.md) defines the working rules.

## Import only `.github`

The reusable payload is **`.github/` only**. Do not copy Resources' root `AGENTS.md`, `CHANGELOG.md`, or `README.md` into a project. Those describe development and usage of Resources itself. The Coordinator creates or updates the target project's own AGENTS.md from its template, preserving existing project instructions.

From the target project root, use a temporary sparse checkout and copy only the payload:

```sh
resources_checkout="$(mktemp -d)"
git clone --depth 1 --filter=blob:none --sparse https://github.com/Spumcake/Resources.git "$resources_checkout"
git -C "$resources_checkout" sparse-checkout set .github
mkdir -p .github
cp -Ri "$resources_checkout/.github/." .github/
```

The temporary checkout may contain repository-root files; the copy command imports none of them. Review overwrite prompts if the target already has matching files. When updating an older installation, review obsolete Resources files separately—the copy merges files and does not remove stale agent definitions. Keep unrelated project configuration. The temporary checkout can be removed afterwards.

Open the target project in VS Code's built-in **Local** chat, select **Coordinator**, and enable **Run Subagent**. If the roles do not appear, run **Developer: Reload Window**. Keep agents, skills, and templates together under `.github` so their relative links resolve.

## Start the example trial

Import `.github` into the example project using the procedure above. Preserve its existing pitch, interface references, code, and project instructions. Select Coordinator and send:

```text
Prepare the next useful increment for this existing project. Discover the
available roles and delegate prerequisite checks and missing specialist
documents to their owners. Reuse the existing pitch, design references,
and implementation. Create or update TASK.md and this project's AGENTS.md.
Do not implement yet. Stop when the next bounded assignment is ready,
or report the specific blocker.
```

After reviewing that outcome, ask it to implement the named assignment. Observe actual named worker calls; request independent work concurrently where dependencies allow, and distinguish overlapping runs from sequential calls. Preparation does not prove implementation or concurrency works.

## Roles and ownership

| Role | Responsibility |
| --- | --- |
| [Coordinator](.github/agents/coordinator.agent.md) | Discover callable roles, partition work, own TASK.md and project AGENTS.md, consolidate audits. |
| [Product Designer](.github/agents/product-designer.agent.md) | Create PITCH.md and INTERFACE.md; prepare prompts and generate mockups through model skills. |
| [Technical Planner](.github/agents/technical-planner.agent.md) | Create SYSTEMS.md; establish ownership, contracts, and technical prerequisites. |
| [Task Operations](.github/agents/task-operations.agent.md) | Implement bounded changes in an established stack. |
| [Code Review](.github/agents/code-review.agent.md) | Review code or document consistency without fixing it. |
| [Verification](.github/agents/verification.agent.md) | Execute relevant tests/builds and preview acceptance checks without fixing code. |

The coordinator discovers responsibilities from definitions rather than requiring every role on every task. Workers determine which decisions and documents they need. No suitable callable role means **stop and explain the gap**, not do the work in the main chat. A role file alone does not prove activation or execution.

## Example requests to Coordinator

- “Prepare the next increment for [project]. Have the relevant roles establish their prerequisites, then create TASK.md and AGENTS.md. Do not implement yet.”
- “Use an image generator to generate two mockups for [specified views], using the existing interface references.” This goes to Product Designer, which selects a model skill and handles generation prerequisites.
- “Implement [bounded behavior], then have it reviewed and verified against [criteria]. Run independent assignments concurrently where possible.”

If you ask for a task outside the available roles, the coordinator identifies the missing responsibility and suggests adding that role. It must not create one or start a substitute workflow automatically.

## Documents and shared skills

- [Pitch](.github/skills/pipeline/pitch/SKILL.md) → `.project/documents/PITCH.md`.
- [Interface](.github/skills/tasks/interface/SKILL.md) → root `INTERFACE.md` (the successor to DESIGN.md).
- [Systems](.github/skills/pipeline/systems/SKILL.md) → `.project/documents/SYSTEMS.md`.
- Coordinator directly owns `.project/documents/TASK.md` and root `AGENTS.md`; its templates live in `.github/agents/templates/coordinator/`.
- [Audit](.github/skills/pipeline/audit/SKILL.md) → brief timestamped records under `.project/documents/audits/` after substantial project work coordinated by the Coordinator. Workers return evidence; they do not create separate automatic audits.
- [Testing](.github/skills/tasks/tests/SKILL.md) → guidance for purposeful tests and stopping.
- [Image generation](.github/skills/models/openai/image-2-5-sunburst/SKILL.md) → reusable model execution and recovery.

Honor existing canonical paths and explicit user destinations. Do not create both DESIGN.md and INTERFACE.md as competing authorities; migrate an existing document deliberately. Roles are configured here, but runtime routing, generation, and concurrency still require observation in the editor. Browser verification depends on available [VS Code browser tools](https://code.visualstudio.com/docs/agents/run/browser-tools).

## Resources development versus project records

Automatic effort audits belong to the Coordinator workflow in the target project, not to routine maintenance of this Resources repository. Existing local development notes were moved to `resources/documents/audits/`, outside `resources/worktrees/main`; leave them there. That local folder is not part of the imported payload. Target-project coordinator audits still default to `.project/documents/audits/`, unless the project specifies another location.
