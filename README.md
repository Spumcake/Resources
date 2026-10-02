# Resources

Reusable skills, agent templates, and model utilities for project development and visual production. Clone the collection into a project and use only the capabilities you need.

> **Version 0.2.0-poc.1 — experimental, full pipeline unverified.** See [CHANGELOG.md](CHANGELOG.md) for the version convention, changes, and validation limits.

## Step 0. Clone the resources into your project

For the full collection, run the following from your target project's root directory:

```sh
mkdir -p .project
git clone https://github.com/Spumcake/Resources.git .project/resources
```

This places the resources at `<project>/.project/resources`. Here, `/.project/resources` means relative to your project root, not your computer's filesystem root.

In the example requests below, replace:

- `<project>` with your target project's absolute path.
- `<resources>` with `<project>/.project/resources`.

For example, the pitch skill will be located at `.project/resources/.github/agents/automation/skills/pitch/SKILL.md` inside your project. Make this directory readable to your coding agent; cloning the files does not automatically register skills with every agent runner.

Keep this nested checkout separate from your project's tracked source by adding `/.project/resources/` to the target project's `.gitignore`. If you deliberately manage it as a Git submodule instead, use that workflow rather than ignoring it.

### Download only agent resources

For a fresh checkout, use Git sparse checkout to keep `.github/agents` (including its skills and templates) without checking out model utilities:

```sh
mkdir -p .project
git clone --filter=blob:none --sparse https://github.com/Spumcake/Resources.git .project/resources
git -C .project/resources sparse-checkout set .github/agents
```

Use this instead of the full clone command, not afterward at the same destination. Root files such as this README and CHANGELOG remain visible in cone mode. The clone is still a Git repository; filtering avoids fetching unneeded file contents when supported by the server. See [Git sparse checkout](https://git-scm.com/docs/git-sparse-checkout) and [clone options](https://git-scm.com/docs/git-clone).

To add model resources later:

```sh
git -C .project/resources sparse-checkout add .github/models
```

To restore the entire checkout, use `git -C .project/resources sparse-checkout disable`. To update an unchanged checkout, use `git -C .project/resources pull --ff-only`; preserve any local edits first. These commands do not install agent definitions into VS Code automatically. Retaining the agents subtree together preserves relative links between skills and templates.

## Choose a workflow

| Need | Start here |
| --- | --- |
| Turn an idea into a specification and development pipeline | Steps 1–5 below |
| Prepare project-specific execution roles | [Agents skill](.github/agents/automation/skills/agents/SKILL.md) and its linked templates |
| Design views and UX from a pitch | [Designer skill](.github/agents/designer/SKILL.md) |
| Generate images from reviewed prompt files | [Sunburst image guide](.github/models/openai/image-2-5-sunburst/README.md) |

Model resources are optional and operate independently of pipeline preparation. Their links are unavailable in an agents-only checkout until you add `.github/models`. Model utilities and the designer skill are included from version 0.2.0-poc.1.

For image generation, a request can be as simple as:

```text
Read <resources>/.github/models/openai/image-2-5-sunburst/SKILL.md.
Generate one image from <project>/prompts/overview.md, using the project's
image configuration and local OpenRouter environment file. Save the result
under <project>/outputs. Use the prompt's aspect ratio and quality settings.
Do not generate additional variations.
```

The image script defaults to a dry run and supports config defaults, per-prompt settings, command-line overrides, reference images, and resumable output records. Keep API keys out of source control. See its guide for setup and the exact commands.

## Design a UI from the pitch

The designer skill reads the pitch, maps the relevant views and flows, discovers a suitable skill under `.github/models`, and uses that skill to generate related images. It records base-image dependencies so new views can retain the same visual language.

```text
Read <resources>/.github/agents/designer/SKILL.md.
Use <project>/PITCH.md to map the main views and UX. Generate one base view
and two related views using an appropriate model skill in Resources.
Reuse existing suitable images. Keep proposals distinct from fixed requirements,
use fictional data, and save prompt/image pairs under <project>/.project/models.
```

For planning only, say “produce the view map and prompts; do not generate images.” To extend an existing design, name the additional views or bound the number to generate. By default, the map is `.project/presentation/DESIGN.md`; each view has a named folder containing its prompt, image, and provenance. Native API records stay under the model's `.runs` folder. See the [designer skill](.github/agents/designer/SKILL.md) for review and resume behavior.

## Step 1. Define your idea

Use the **pitch** tool to concieve a full pitch for the project. Describe the problem in ordinary language; you do not need to know the stack or architecture.

```text
Read and follow <resources>/.github/agents/automation/skills/pitch/SKILL.md.

Create a pitch for <project>.

I want an application for a bicycle repair shop. Staff lose paper notes,
and the front desk cannot reliably tell customers the status of a repair.
Staff should register a bicycle, record its problem, assign a mechanic,
and mark it ready for collection.

The first release should let someone find a repair by customer name and
understand its status quickly. It must retain records after restarting.
Keep inventory management and customer payments out of scope.

I want a simple browser interface. Hosting and the technology stack are
undecided. Ask the few questions that materially affect the product;
record other unknowns for later investigation.

Write <project>/.project/documents/PITCH.md. Do not implement the app yet.
```

**What the resulting PITCH.md contains:** a document describing users, workflows, success criteria, constraints, references, and open questions.

**Your next action:** read it and correct the intent. Pay particular attention to requirements marked fixed, proposals, and excluded features. You can say:

```text
Revise the pitch: this is for one shop, not a multi-tenant service.
Email notifications are deferred. Staff need to correct mistakes without
losing the previous repair notes. Preserve the other decisions.
```

See [a more detailed pitch request](.github/agents/automation/skills/pitch/README.md) if you want to supply more context upfront.

## Step 2. Prepare automation pipeline

Use **pipeline**. This is the main entry point; you do not need to run the other preparation skills individually.

```text
Read and follow <resources>/.github/agents/automation/skills/pipeline/SKILL.md.

Prepare the development pipeline for <project> from
<project>/.project/documents/PITCH.md.

Inspect relevant existing work, produce the specification and architecture,
and define the execution roles and verification process. I want local
browser previews so I can review the interface during development.

The agent runner I intend to use is [name your runner, or say undecided].
Preserve the pitch's fixed decisions. Report the first ready milestone
and any prerequisites I need to supply. Prepare the kit only; do not
start implementing the application.
```

**You get:** normally `TASK.md`, `ARCHITECTURE.md`, `AGENTS.md`, and `KICKOFF.md`, plus relevant supporting resources. The agent uses discovery, spec, agents, and checking as needed.

**Your next action:** inspect the first milestone, its acceptance criteria, and any blockers. For example, a live email test may require credentials, while a local record-editing milestone can proceed without them. A “blocked” result should name the missing decision or prerequisite, not simply ask you to approve everything.

If your project already has code, add:

```text
This is an existing application. Preserve working behavior and inspect
only the areas needed for the pitch. Identify what can be reused before
proposing replacements.
```

## Step 3. Start implementing a milestone

This is an **implementation request**, not another pipeline-generation request. Work in the target project and use its generated instructions.

```text
Work in <project>. Read AGENTS.md and .project/documents/KICKOFF.md.
Implement the first ready milestone defined in TASK.md.

Coordinate the task using the project's configured roles. Delegate
independent work where supported and useful. Follow the worktree policy,
run the required acceptance checks, and give me the preview instructions
and evidence of what works. Stop at this milestone's completion boundary.
```

**You get:** implementation changes, relevant checks, and a handoff you can inspect.

The coordinator initializes working records such as PLAN, TODO, and DEVLOG as required by the generated rules. It selects workers for this assignment; it does not recreate the role definitions every time. If the runner does not support subagents, work can proceed sequentially where the kit permits it.

## Step 4. Test and give feedback

Give concrete feedback against the working milestone:

```text
In the repair list, I cannot distinguish waiting-for-approval jobs from
jobs already being worked on. Add a clear status label and verify that
changing a job's status updates the list. Keep the existing scope and
record-saving behavior. Show me the updated preview.
```

Use ordinary implementation requests for changes within the agreed scope. You do not need to regenerate the pitch or kit for every bug fix.

For the next milestone:

```text
The current milestone's preview meets my expectations. Check its remaining
acceptance conditions, update its status accurately, and continue with
the next ready milestone. Report anything that still blocks it.
```

A human's visual approval does not replace outstanding functional checks.

## Step 5. “Check whether this kit is actually usable.”

Use **checking** when you want a readiness review without regenerating the documents:

```text
Read and follow <resources>/.github/agents/automation/skills/checking/SKILL.md.
Review the existing kit in <project> in review-only mode.

Can another agent start the first milestone and can I verify its result?
Identify blocking contradictions, missing prerequisites, and broken
references. Separate blockers from optional improvements. Do not modify
the kit or claim checks passed if you could not run them.
```

**You get:** actionable findings and a readiness assessment. This checks the development kit; it does not certify the finished application.

## Which file should I look at?

| Your question | Project file |
| --- | --- |
| Are we building the right thing? | `.project/documents/PITCH.md` |
| What should it do, and what comes next? | `.project/documents/TASK.md` |
| Which part owns this behavior or data? | `.project/documents/ARCHITECTURE.md` |
| How should agents work together? | `AGENTS.md` |
| What do I tell the agent to start or resume? | `.project/documents/KICKOFF.md` |
| What is happening in the current execution? | Working records selected by AGENTS.md, usually PLAN/TODO and DEVLOG |
| What was actually delivered and verified? | `.project/documents/REPORT.md` once execution creates it |

These are default locations. Explicit project-specific locations take precedence.

## When would I use the other skills directly?

Usually pipeline selects them. Invoke one directly for a narrow preparation task:

| Skill | Example request |
| --- | --- |
| [discovery](.github/agents/automation/skills/discovery/SKILL.md) | “Inspect how this repository currently saves records and what tests cover it. Report evidence; don't redesign it.” |
| [spec](.github/agents/automation/skills/spec/SKILL.md) | “Update TASK.md and ARCHITECTURE.md from this revised pitch and the existing discovery findings.” |
| [agents](.github/agents/automation/skills/agents/SKILL.md) | “Adapt the execution rules and necessary specialist roles to our selected runner and stack.” |

Other entry points: [pitch](.github/agents/automation/skills/pitch/SKILL.md), [pipeline](.github/agents/automation/skills/pipeline/SKILL.md), and [checking](.github/agents/automation/skills/checking/SKILL.md).

## How to continue from an interrupted session

Use the target's resume instructions, not pipeline generation:

```text
Resume work in <project> using the resume instructions in
.project/documents/KICKOFF.md. Read the existing working records and
inspect the current changes before continuing. Preserve completed work
and continue the next unblocked assignment. Do not recreate the kit or
reset the plan.
```

**You get:** continuation from recorded state, with any missing state or unresolved work identified.

## What to do if requirements change

When product intent changes, revise the pitch and then update the affected pipeline documents:

```text
Use the pitch skill to revise <project>'s existing PITCH.md: the shop now
needs email approval requests. Preserve the other accepted requirements.

Then use the pipeline skill to update the affected specification,
architecture, dependencies, and verification guidance. Identify the
provider/account decisions needed before real integration testing.
Preserve existing implementation and execution history. Do not implement
the new feature yet.
```

**You get:** a targeted plan update, explicit new prerequisites, and an indication of which earlier evidence is no longer sufficient. Once the updated task is ready, request its implementation separately.

## What to expect from this version

The six skills and four templates are written and structurally validated. A full sample-project trial is still needed. These are instructions followed by an agent, not a standalone scheduler or background service.

Five reusable role templates are available: coordinator, implementation specialist, user experience reviewer, acceptance verifier, and test/build runner. Automatic dependency scheduling is not implemented. The agents skill can prepare project-specific role definitions for a supported runner; an unspecified runner leaves activation unresolved. Requesting kit preparation alone does not launch workers, provision services, or deploy a product.

Start with one small project and carry one milestone through to a result you can inspect. That exercises the workflow without committing to a large autonomous run.

The model utilities have local automated tests and a successful low-quality Sunburst generation/resume smoke test. Reference-image generation and the full image skill workflow remain unverified. Local unpublished changes are recorded under Unreleased in the changelog.
