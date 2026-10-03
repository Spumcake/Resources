---
name: interface
description: Create or revise INTERFACE.md, mapping user flows, views, states, and visual references from a pitch. Optionally prepare prompts and use a model skill for authorized image generation; not application implementation.
---

# Create the interface document

Read the requested pitch, relevant existing design decisions, and supplied references. Adapt [the template](templates/INTERFACE.md). Honor explicit paths and existing canonical documents; otherwise write `<target>/INTERFACE.md`. Do not create a competing copy. Ask for the target only if ambiguous. If the project already has DESIGN.md, treat it as the existing interface source; migrate its content and incoming references when that rename is authorized, rather than creating two competing documents. Do not rename unrelated project files merely by loading this skill.

Define the central journey, sitemap, necessary views and states, and relevant recovery paths. Distinguish a page from a panel, filter, or dialog. Scope the design to the requested increment; an API-only project may need caller examples instead of screens. Do not invent a GUI to fill the template.

Preserve Fixed, Preferred, Open, Proposed, and Deferred distinctions from the pitch. Ask only about decisions that materially alter behavior; label routine visual choices as proposals. Reference the pitch rather than repeating it. Remove unused template sections and replace placeholders with supported decisions or explicit unknowns.

## Optional prompts and images

Inspect existing reference images before selecting them. A design document does not require image generation. When prompts or images are requested, discover relevant `SKILL.md` files under this checkout's `.github/skills/models/`, then read only the selected capability and required usage instructions. The current [image skill](../../models/openai/image-2-5-sunburst/SKILL.md) is one available capability, not a permanent model requirement.

Use the model skill's supported settings, reference inputs, execution, cost, and recovery procedures. Do not invent API flags or duplicate its implementation here. Planning a design does not authorize paid image calls. Use fictional sample content, not private source records.

Keep prompts and outputs under the target's existing convention, otherwise `.project/models/<provider>/<model>/<view-id>/`. Link the prompt, actual image, and native generation record from INTERFACE.md. Preserve existing outputs and unresolved request records on resume.

Plan base images before derivatives. Inspect a base before reusing it; pass its actual path explicitly to dependent generations. Independent API calls do not share image context. Respect requested human selection points and authorized generation limits. Do not regenerate automatically to obtain a perfect result.

## Finish

Check the requested flows, consistent state/copy, artifact links, and unresolved decisions. Distinguish proposed, generated, visually inspected, and human-approved. Static mockups do not verify application behavior. Report document/artifact paths and concrete limitations, then stop.

Return concise outcome/evidence for the Coordinator's consolidated audit when delegated. Do not automatically create a separate audit. Do not change the pitch or product code as a side effect.
