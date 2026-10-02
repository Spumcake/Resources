---
name: designer
description: Turn a project pitch into a compact view and UX map, model-specific image prompts, and reference-linked UI mockups using available skills under .github/models. Use for visual design exploration and additional views, not product implementation or specification approval.
---

# Designer

Use the target project's pitch to establish user journeys and visual design needs, then discover an appropriate model skill in this Resources checkout. Apply the selected skill's interface, settings, authorization, execution, and recovery rules. Do not implement the application or silently change product requirements.

## Establish the design scope

Find the pitch at the user-specified location, repository-root PITCH.md, or .project/documents/PITCH.md; resolve conflicting versions before relying on them. Read applicable project instructions and existing presentation artifacts selectively. Preserve Fixed/Proposed/Open/Deferred distinctions. Use fictional content in external generation requests; do not send private source records or credentials.

Identify the primary journey, navigation destinations, important UI states, and recovery flows. Reuse existing view IDs, prompt/image pairs, and the user's directory convention. Inspect candidate reference images before selecting them. Existing images are design evidence, not proof of owner approval or functional behavior.

Adapt [the DESIGN.md template](../../templates/DESIGN.md), replacing placeholders and preserving existing project decisions. Write or update one compact `DESIGN.md` in the target project root (unless the user explicitly requests another location), containing:

- Pitch path and relevant requirements, plus unresolved behavior affecting the proposed views.
- Sitemap and primary flows; distinguish pages from filters, panels, and states.
- A view table: stable ID, purpose/state, pitch basis, model skill, base-image dependencies, artifact paths, and generation/review status.
- Shared visual direction and fictional fixtures, without duplicating every prompt.

Scale detail to the request. An extension should add only the requested views and necessary dependency information. Do not design every deferred feature or require clarification about routine visual choices. Ask only when a consequential unresolved product decision blocks the requested depiction; otherwise label the proposed treatment.

## Discover the model capability

Locate this Resources checkout from the skill's own path. Enumerate `SKILL.md` files under its `.github/models/`, inspect their names/descriptions, and read the chosen skill and its linked usage/configuration instructions. Match image output, reference-image support, presentation needs, available credentials, and authorized cost. Do not invent model IDs, API payloads, or command flags. Keep model-specific API behavior owned by that skill's script.

If an agents-only checkout omits model resources, report the missing capability and the README's sparse-checkout add command. Fetch missing resources when authorized; otherwise finish the map/prompts and identify the execution blocker. Do not substitute an unrelated generation service silently.

## Plan bases before derivatives

Construct an acyclic dependency order: existing selected reference or new base view first, dependent views afterward. Record actual image paths, not only prompt IDs. A dependent may use multiple relevant references if supported; avoid chaining through a visibly defective derivative.

When generating a new base, inspect it before proceeding. Respect an explicit human selection gate; otherwise select a suitable result and label it agent-selected, pending human review. Reuse an existing suitable base when extending a design. Sequential API requests do not share visual context: supply each reference explicitly using the chosen model skill.

## Write and execute prompts

Use this default artifact layout, preserving an existing equivalent layout when present:

```text
DESIGN.md
.project/models/<provider>/<model-folder>/
  <view-id>/
    <view-id>.md
    <view-id>.png       # use the actual returned format
    generation.json
  .runs/               # model script's native request/response/status records
```

Each prompt states the purpose, visible state, exact fictional UI copy, layout, reference-preservation instructions, and relevant exclusions. Put generation settings in metadata only if the selected script supports it. Keep bookkeeping out of submitted prompt text. Translate the desired canvas into supported model settings; do not promise exact dimensions from prose alone.

Run the model script's dry run first and inspect resolved settings. Execute within the user-authorized count/spend scope, one ready view at a time, with explicit reference paths. A design-only request does not authorize paid generation; an explicit generation request does, within its stated scope. Do not add variations or retries outside that scope.

Keep the script's native output intact under `.runs`. Copy a completed image into the named view folder without conversion, retaining the actual extension. Record in `generation.json`: model skill path, effective model/settings, prompt/source request identity, reference paths and hashes, native run path, image hash, reported usage/cost (unknown if absent), and visual review outcome. Paths should be relative to the project where practical; never copy keys into artifacts. Preserve previous images/runs on revision; do not overwrite a user-selected image silently.

Follow the model skill's unresolved-request procedure. Never remove failure records or change a prompt just to bypass duplicate-request protection. On resume, reconcile the map, named artifacts, and native run records before sending anything new. If generation completed but copying failed, finish the copy rather than regenerating.

## Review and hand off

Inspect every generated image against its prompt and base: navigation, state consistency, text legibility, layout, and out-of-scope additions. Record concrete discrepancies. Fix prompts or regenerate only within remaining authorization; a failed visual check is not automatic permission for another paid call.

Report the map, prompt/image pairs, reused bases, actual costs where available, and unresolved issues. Distinguish generated, visually inspected, and human-approved. Mockups cannot verify persistence, accessibility interactions, or real application behavior. Leave product code and pitch unchanged unless separately requested.
