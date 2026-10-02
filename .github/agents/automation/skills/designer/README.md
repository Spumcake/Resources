# Designing views from a pitch

The designer skill turns a pitch into a view/UX map, image prompts, and optionally generated mockups. It uses [the DESIGN.md template](../../templates/DESIGN.md), discovers model skills under the same Resources checkout's `.github/models/`, and follows the selected model skill's generation interface. It does not implement the application or create the development pipeline.

Replace `<project>` with your project directory and `<resources>` with its Resources checkout, normally `<project>/.project/resources`. Explicitly ask your coding agent to read the skill; the folder alone does not register it with every runner.

## Plan without generating images

```text
Read <resources>/.github/agents/automation/skills/designer/SKILL.md.
Use <project>/PITCH.md to map the main user journey, navigation, and relevant
UI states. Write <project>/DESIGN.md and prepare prompts for the main views.
Keep proposed design choices distinct from fixed requirements.
Do not call a paid model or generate images yet.
```

You get a root-level DESIGN.md and named prompt files. Missing credentials should not prevent this planning work. The designer asks about consequential blockers, not every visual detail.

## Generate a base and related views

```text
Read <resources>/.github/agents/automation/skills/designer/SKILL.md.
Use <project>/PITCH.md and existing design references. Create one base view
and two dependent views, with at most three image-generation requests.
Discover a suitable model skill under Resources' .github/models and use
the configured local credentials. Inspect the base before using it as a
reference. Save DESIGN.md at the project root and prompt/image pairs under
.project/models. Do not implement the application.
```

If you want to choose the base yourself, add: “Generate only the base first and wait for my selection before creating dependent views.” A request limit is not a hard dollar cap; the model guide explains supported spending controls and settings.

## Extend an existing design

```text
Use the designer skill to add two views to <project>: the overdue-tool
filter and the member list. Reuse the existing desk overview as their
visual base and preserve the existing images. Update root-level DESIGN.md.
Generate one image for each new view; do not create additional variations.
```

The designer inspects the existing image, supplies its path explicitly as a reference, and preserves the established artifact layout. Every dependent request needs its own reference input; generation order alone does not preserve style.

## Outputs and review

- `DESIGN.md`: sitemap, flows, view states, dependencies, proposals, and review status.
- `.project/models/<provider>/<model>/<view-id>/<view-id>.md`: prompt and supported generation metadata.
- The image beside its prompt, using the actual returned format.
- `generation.json`: request identity, references, effective settings, provenance, usage, and visual review.
- `.runs/`: original model-script request, response, and completion records.

On resume, ask the designer to reconcile DESIGN.md with existing artifacts and continue only unfinished authorized views. It should recover completed images rather than regenerate them. Failed or uncertain requests follow the selected model skill's recovery rules.

Inspect the images and correct the design before treating them as implementation references. Human approval is recorded only when supplied. Static images do not test the application's actual behavior.

## Missing model resources

An agents-only sparse checkout includes this skill and its DESIGN template but omits image-model capabilities. From the project root, add those files with:

```sh
git -C .project/resources sparse-checkout add .github/models
```

Follow the chosen model guide for credentials and configuration. Do not place secrets in the pitch, DESIGN.md, prompts, or committed files. Keep the template-relative paths intact when copying the skill.
