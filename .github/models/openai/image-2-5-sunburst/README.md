# Image generation from an agent

These resources let a coding agent call OpenRouter without selecting an image model as the agent's own model. They are independent of pipeline preparation. No MCP server or additional Python package is required.

## Setup

Use Python 3.10 or later. Ask the agent to read `SKILL.md`. Copy `config.example.json` to a project-local configuration and adjust the model/settings after checking availability and pricing. Supply `OPENROUTER_API_KEY` through your shell or agent runner's secret environment; never put its value in configuration, prompts, or source control. To load the Resources-local file explicitly, add `--env-file .project/resources/.github/models/.env`. Existing environment credentials take precedence. This reads only `OPENROUTER_API_KEY`, supports plain or quoted values and an optional `export` prefix, and never executes shell expressions. Dry runs do not load credentials. A VS Code extension's stored key is not automatically available to this script.

The implementation follows the [OpenRouter Image API](https://openrouter.ai/docs/guides/overview/multimodal/image-generation): `POST /api/v1/images`, with model discovery at `GET /api/v1/images/models`. Check the selected model's endpoint records for exact parameter and reference support. The example uses the documented `openai/gpt-image-2.5-sunburst`, confirmed in the live image catalogue on 2026-10-02.

## First image

From the target project root, after cloning Resources into `.project/resources`, run:

```bash
python3 .project/resources/.github/models/openai/image-2-5-sunburst/scripts/generate.py \
  --config .project/presentation/image-config.json \
  --prompts .project/presentation/image2-prompts/01-desk-overview.md \
  --output .project/presentation/generated
```

This is an offline dry run. Add `--execute --max-requests 1` to generate the first image when authorized. Prompt files can be plain text or Markdown; when an exact `## Prompt` heading exists, only its following content is sent.

Review the overview image. For each remaining prompt, use the same command with that prompt's path and add `--reference PATH_TO_SELECTED_IMAGE`. Alternatively supply a folder containing only the remaining selected prompts and `--max-requests 3`; files run in filename order and share the explicitly supplied reference. Do not include the overview in that dependent batch. Actual image dimensions depend on the chosen API settings/model, even if a prompt describes a specific canvas size.

## Settings per image

Settings resolve in this order: **config defaults → prompt frontmatter → command-line overrides**. Unspecified optional settings use the provider default. Dry runs show the final model and settings for every selected prompt; metadata is stripped from the text sent to the image model.

```markdown
---
aspect_ratio: "3:2"
quality: high
---
A desktop interface for the workshop lending desk…
```

Place the metadata at the very start of the file. Supported keys are `model`, `aspect_ratio`, `quality`, `size`, `resolution`, `output_format`, `background`, `output_compression`, and `seed`. The dependency-free parser supports a flat YAML subset: plain or quoted scalar values, integers, `null`, and full-line comments. Nested YAML, inline comments, and unknown or duplicate keys are rejected. Integer fields must be integers. Provider-specific supported values must still be checked against the model catalogue.

For a one-off run, append `--aspect-ratio 16:9 --quality low` to the generation command. Other keys have matching flags with hyphens, such as `--output-format png` and `--model openai/gpt-image-2.5-sunburst`. CLI settings apply to every prompt selected for that run.

To remove an inherited optional value, use `null` in metadata or `--unset aspect_ratio` on the command line. Use `size` alone, or `aspect_ratio`/`resolution`; the client rejects combining them rather than silently choosing conflicting dimensions. For example, `--unset aspect_ratio --size 1024x1024` replaces the example config's aspect ratio. Changed effective settings produce a new request identity and may incur a new charge; formatting-only changes do not.

## Results, limits, and recovery

Outputs use a full request-content hash directory. Each includes source paths, the submitted request, response, image, and status/usage records. Changing prompt content, settings, or reference bytes creates a different request identity. These records include prompt/reference content; keep generated output private or ignored by Git as appropriate. API keys are not recorded.

Re-running an identical request skips an intact completed output. The script sends one image request at a time and never automatically retries. `--max-requests` caps new calls for that invocation, not total lifetime spending or dollars. Unknown cost remains unknown. Use OpenRouter account controls when a hard spending limit is required.

A timeout, interrupted process, malformed response, or storage failure leaves a request unresolved. Inspect its saved response and OpenRouter activity before doing anything else; a response may already contain a recoverable image. Do not delete status records or alter prompts to bypass this block. Recover the result where possible; if another paid attempt is authorized, use a separate output directory and retain the old records. There is no automatic recovery or provider-side idempotency guarantee.

An exclusive output-directory lock prevents simultaneous writers. A hard crash may leave `.generation.lock`; remove it only after confirming no process is using that output directory and reconciling in-flight records. Returned PNG/JPEG/WebP bytes are supported; SVG outputs are intentionally unsupported and retained as unresolved responses.

## Validation status

Proof of concept: local mocked tests cover completion/resume, uncertain failure blocking, and request limits. On 2026-10-02, after correcting the local credentials, a live low-quality 1:1 generation with `openai/gpt-image-2.5-sunburst` succeeded. The saved 1024×1024 PNG was visually inspected, usage reported $0.005985, and repeating the request skipped the completed output without another generation. Local tests cover environment-file loading, settings precedence, malformed metadata, request identity, and resume behavior. Two medium-quality 3:2 reference-based UI views were subsequently generated and visually inspected in the workshop example using the designer skill. High-quality settings and independent-agent skill evaluation remain unverified. Run local tests with:

```bash
python3 -m unittest discover -s .project/resources/.github/models/openai/image-2-5-sunburst/scripts -p 'test_*.py'
```
