# [PLACEHOLDER: project name] — design map

> Adapt this template into `DESIGN.md` at the target project root. Replace placeholders with project facts, proposals, or explicit unknowns; remove non-applicable sections. Keep this document compact and link to prompts and provenance rather than duplicating them. Do not execute this unfilled template. Remove this note after adaptation.

**Source pitch:** [PLACEHOLDER: path/link and revision or date].
**Status:** [PLACEHOLDER: draft, generated, visually inspected, or human-reviewed; date and evidence].
**Scope:** [PLACEHOLDER: requested journeys/views and generation limits; distinguish planning-only from authorized generation].

Use **Fixed**, **Preferred**, **Open**, **Proposed**, and **Deferred** consistently with the pitch. A generated image does not establish approval or change a product requirement. Resolve relative artifact links from this root-level document.

## 1. User journey and scope

- Primary user and outcome: [PLACEHOLDER: pitch reference and observable task].
- Primary flow: [PLACEHOLDER: starting state → actions → result].
- Supporting/recovery flows: [PLACEHOLDER: relevant flows, or none for this slice].
- Exclusions: [PLACEHOLDER: deferred features and views not being designed].

## 2. Sitemap and states

[PLACEHOLDER: compact tree or list of navigation destinations; distinguish pages from filters, panels, dialogs, and loading/empty/error/success states. Include only relevant states.]

## 3. Shared visual direction

- Reference images: [PLACEHOLDER: actual paths, inspected suitability, and selection/approval status].
- Layout and presentation: [PLACEHOLDER: viewport/aspect ratio, hierarchy, typography, colours, spacing, and relevant accessibility expectations; label proposals].
- Fictional fixtures: [PLACEHOLDER: consistent sample entities, dates, and state across views; no private source data].
- Open product decisions affecting appearance: [PLACEHOLDER: question, proposed depiction if possible, decision owner, and what remains blocked].

## 4. Views and dependencies

| View ID | Purpose / visible state | Pitch basis | Base image dependencies | Model skill | Prompt / image / provenance | Status |
| --- | --- | --- | --- | --- | --- | --- |
| [PLACEHOLDER: stable ID] | [PLACEHOLDER: outcome and state] | [PLACEHOLDER: section] | [PLACEHOLDER: actual image paths, pending base ID, or none] | [PLACEHOLDER: discovered skill path] | [PLACEHOLDER: project-relative artifact links; mark planned paths] | [PLACEHOLDER: planned/generated/inspected/pending human review] |

**Generation order:** [PLACEHOLDER: acyclic base → dependent sequence; reuse suitable existing images].
**Review gates:** [PLACEHOLDER: any requested human selection before derivatives; otherwise agent selection status].

## 5. Artifacts and execution

Default layout (adapt the provider/model and view IDs):

```text
DESIGN.md
.project/models/<provider>/<model-folder>/
  <view-id>/
    <view-id>.md
    <view-id>.<actual-image-extension>
    generation.json
  .runs/
```

- Selected capability: [PLACEHOLDER: discovered model skill, resource revision, supported reference input, and relevant settings].
- Request limits: [PLACEHOLDER: authorized count/spend scope; do not invent a budget].
- Provenance: [PLACEHOLDER: links to generation.json/native records containing effective settings, prompt identity, reference paths/hashes, output hash, usage/cost, and review]. Never record secrets here.
- Resume state: [PLACEHOLDER: completed artifacts, unresolved requests, and next ready view; reference the model skill's recovery procedure].

## 6. Review and handoff

| View ID | Visual checks and findings | Evidence | Remaining action |
| --- | --- | --- | --- |
| [PLACEHOLDER: ID] | [PLACEHOLDER: observed layout, copy, state, reference consistency, and discrepancies] | [PLACEHOLDER: inspected image/provenance links] | [PLACEHOLDER: human review, bounded correction, or none] |

**Reported cost:** [PLACEHOLDER: actual provider-reported total or unknown; identify excluded/unknown requests].
**Next handoff:** [PLACEHOLDER: selected design references and unresolved choices for pipeline/spec work].
**Verification limits:** Static mockups do not prove interaction, persistence, keyboard accessibility, or implemented application behavior. Do not infer human approval from agent review.
