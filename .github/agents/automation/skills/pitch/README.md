# Requesting a project pitch

The `pitch` skill turns your ideas and constraints into a PITCH.md that can guide later specification work. You do not need to know the architecture or answer every template section first.

The skill uses [the shared template](../../templates/PITCH.md). Keep that relative dependency intact when copying this resource, or update the skill's reference. Skill loading depends on the agent runner; the request below is plain language and does not assume a particular slash command.

## Example request

The following is a fictional project example, not a default product or technology choice:

> Use the pitch skill to create `.project/documents/PITCH.md` in my `repair-desk` project.
>
> I want a small application for a bicycle repair shop. Staff currently keep repair notes on paper and call customers whenever they need approval. Notes get lost, and the front desk cannot reliably explain what is happening with a bicycle.
>
> The main workflow should be: register a bicycle and the customer's contact details, record the reported problem, assign a mechanic, request approval for additional work, and mark the repair ready for collection. My priority is that anyone at the desk can find the current status quickly.
>
> As a proposed success criterion, a staff member should locate a job by customer name and explain its status within 30 seconds while the shop has 200 active jobs. We should test that with representative staff; it is not a measured result yet. Done and deployed means the shop can use it from its two front-desk computers, data survives restarts, backups can be restored, and someone is responsible for supporting it.
>
> Trello is an interaction reference for moving work between stages, but I do not want a general project-management tool. Use the sketches in `references/` as explorations, not approved mockups. Large readable controls and keyboard access matter more than elaborate branding.
>
> One recovery case: a mechanic records the wrong status and needs to correct it without losing the earlier repair notes. Another is an unavailable notification service; the repair record must remain usable.
>
> Keep customer payments and inventory management out of the first release. Email notifications are preferred, but I have not selected a provider. Identify any accounts, billing, or infrastructure needed for testing and launch. I have no fixed stack preference. Review the existing prototype only enough to identify what is known and what discovery should inspect later.
>
> I want browser previews for feedback, small reviewable changes, tests for saving and status changes, and private source control. Recommend a version convention and release route, labeling them as proposals. I can review progress twice a week. Budget and hosting are still open decisions.
>
> Draft the pitch now. Ask only the few questions that materially affect the product direction, and record the rest as open questions for discovery or spec. Do not implement the application or generate TASK.md yet.

## Expected result

- A project-specific PITCH.md following the template's topics, without unfilled scaffold placeholders.
- Clear separation of fixed requirements, preferences, proposals, and unknowns.
- Concrete user strategies and success criteria, without fabricated research or approval.
- A short handoff naming the saved file and important open decisions.

For an update, ask the agent to revise the existing pitch, identify the changed requirements, and preserve unrelated accepted decisions. Writing a pitch does not itself install the skill, generate the rest of the pipeline, or deploy software.
