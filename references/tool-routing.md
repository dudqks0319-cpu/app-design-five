# Tool routing and portability

Read this before generating images or creating the selected design. Resolve capabilities from the current host, not from a brand name or a previously installed package.

| Stage | Preferred capability | What the skill does not provide |
| --- | --- | --- |
| Five concepts | Codex's installed `imagegen` skill and built-in image generation | Image credits, an API key or a replacement image provider |
| Selected design | Installed `open-design-mode` / `open-design:open-design-mode`, with Local Codex | OpenDesign installation, authentication or a cloud account |
| App implementation | Current coding agent and the authorized project | A new coding-agent process, paid service or deployment approval |

## Codex images

Find the exposed `imagegen` skill and read its current `SKILL.md`. The usual bundled location is `${CODEX_HOME:-$HOME/.codex}/skills/.system/imagegen/SKILL.md`; a host-provided catalog is preferable to guessing paths.

Use the built-in image tool by default, once per distinct concept. Multi-image output does not imply use of the API/CLI batch path. Preserve the actual tool output, then copy project-bound images into the task folder. Do not promise an output-path argument that the tool does not support.

If a local `app-image-batch` skill exists, it can help organize the manifest and files. The current imagegen skill and the user's task/verification constraints still govern generation; do not import unrelated asset insertion or automatic QA rules from an optional helper.

## OpenDesign with Local Codex

Find and read the installed OpenDesign skill through the host's skill catalog. Do not vendor its contents into this package. This workflow's selected default is Local Codex; an already authorized mode does not need another mode-selection question.

Use the installed skill for brief attribution, confirmation, runtime availability/authentication, project selection, generation, polling and delivery. Preserve its workflow/request identifiers and required child-runtime boundary. Explicitly select the authenticated Local Codex runtime in each generation request. Keep the user's configured model and effort unless separately changed.

Pass the brief and the chosen image references into that workflow; do not pretend an image path was attached when the tool received only text. Read back the same run's terminal result and delivery link. Confirm an accessible entry/artifact before reporting a usable design. Preserve successful image work if design creation fails.

When the native design tools are absent, use an existing task-authorized on-demand runner only if the workspace documents that route. Read that runner's own guide and the specific tool schema. Do not enable all servers, bypass a denied tool, restart shared sessions or leave an owned bridge running. If no authorized route exists, report the missing capability rather than inventing endpoints or installing another runtime.

Do not enter OpenDesign Cloud or BYOK sign-in/credit flows as an automatic fallback. A route change requires the user's choice. Tool failure is not consent to a different account or billing path.

## OpenCode

OpenCode reads ordinary Agent Skills folders with `SKILL.md`, including `.agents/skills/app-design-five/` and `~/.agents/skills/app-design-five/`. See the [official skill documentation](https://opencode.ai/docs/skills/) for current discovery and permission rules. A compatible file format is not proof that image generation or OpenDesign works in that host.

1. Load this skill and inspect the current host's image/design capabilities. Do not assume OpenCode can call Codex's built-in image tool.
2. If the user already supplied the five concepts and a selection, reuse them and continue at the selected-design stage.
3. If image generation is missing, retain the five-direction plan and report that the actual images still need a capable image host. Do not count textual prompts as generated images or install a paid provider automatically.
4. If the user explicitly requests direct OpenCode implementation, apply the selected direction there. If the request instead requires OpenDesign, keep that requirement until the user changes it.

This adapter is instruction compatibility. Runtime integration must be demonstrated separately in the user's host.
