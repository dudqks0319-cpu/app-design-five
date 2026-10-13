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

### Connection and artifact handling observed in the demo

The [included demo](https://github.com/dudqks0319-cpu/app-design-five/tree/main/demo) exercised OpenDesign plugin 0.5.2 with application 0.24.1. Treat these observations as version-specific, and follow the installed tool's current schema:

- Keep `collect_brief` → `confirm_brief` → `start_run` in one MCP connection. Brief drafts in this tested version are connection-local; opening a new connection between collection and confirmation loses attribution. A saved draft ID alone does not restore that state. If the installed workflow requires explicit permission to restart a brief, obtain it before recollecting.
- Once `start_run` has accepted the run, keep its exact run and workflow identifiers. Reconnecting and polling that same accepted run worked in this demo; do not start a replacement run because the bridge closed. Closing an owned bridge and cancelling a shared asynchronous job are separate actions.
- Use the returned `artifactRef.entryFile` as the explicit `get_artifact` entry when automatic entry discovery fails. In the demo, the default lookup failed while the explicit `index.html` lookup returned the complete source. Check truncation and actual file contents before exporting.
- A local reference path in a text prompt is not an image attachment. Only report image inspection when the run's evidence establishes it; otherwise describe the written handoff actually supplied.

These are routing instructions, not a bundled MCP client. Use the host's documented, authorized connection lifecycle and approval controls. Preserve the shared app, existing sessions and jobs; close only the task-owned connection.

When the native design tools are absent, use an existing task-authorized on-demand runner only if the workspace documents that route. Read that runner's own guide and the specific tool schema. Do not enable all servers, bypass a denied tool, restart shared sessions or leave an owned bridge running. If no authorized route exists, report the missing capability rather than inventing endpoints or installing another runtime.

Do not enter OpenDesign Cloud or BYOK sign-in/credit flows as an automatic fallback. A route change requires the user's choice. Tool failure is not consent to a different account or billing path.

## Codex → OpenDesign handoff

Install and load this skill in Codex. Codex generates the five concepts with its built-in image tool, then passes the user's selection and confirmed requirements to OpenDesign using Local Codex. OpenDesign is the design application in this sequence, not a skill-installation target.

Installing the Codex skill does not install or authenticate OpenDesign. Check the actual image and design capabilities before their stages. Reuse supplied concepts and an existing selection when resuming. If a required capability is missing, preserve the completed work and report the concrete blocker; do not replace the design stage with another coding tool automatically.

See the [OpenDesign website](https://open-design.ai/) for the design application and the installed OpenDesign skill for the current execution protocol.
