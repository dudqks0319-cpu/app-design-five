# App Design Five

[한국어](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

**An AI agent skill that shows five real UI image concepts before building an app.**

Five images → your choice or combination → design → requested app implementation

Compare five distinct directions for the same core app screen. Choose one or combine them, such as “option 1's layout with option 4's colors.” The selected direction becomes an OpenDesign design using Local Codex, then an app implementation if requested. Routine bug fixes and status questions do not start this workflow.

## Executed demo

The fictional Korean task app **“오늘 한 걸음” (One Step Today)** exercised five real image generations → selection → OpenDesign with Local Codex → an interactive app. The user delegated selection; Codex chose option 2. **15 checks passed in Aside Browser**, covering interactions, persistence, error handling and two frame sizes.

![Five independently generated concepts for the same app](demo/screenshots/five-concepts.png)

<img src="demo/screenshots/mobile-390x844.png" width="300" alt="Actual app generated from option 2, rendered in a 390×844 browser frame">

[Run the demo and read the evidence](demo/README.md) · [App HTML](demo/app/index.html) · [GeekNews draft in Korean](promotion/geeknews.md) · [Threads draft in Korean](promotion/threads.md)

GitHub displays HTML source. Download the repository and open `demo/app/index.html` in a browser to interact with it. The mobile capture uses a 390×844 browser frame; physical-phone testing remains unverified.

## Workflow

1. Establish the app's purpose, platform, core screen and required features.
2. Generate and show **five separate real images** with Codex's image tool, varying layout and information structure.
3. Let the user choose, combine directions or request changes. Do not start the selected design without a choice.
4. Create the selected design in OpenDesign. The default execution mode is **Local Codex**.
5. Implement real screens and behavior if implementation was requested. A design-only request ends at the design boundary.

## Skill and MCP

| Format | Role | This project |
| --- | --- | --- |
| Skill | Gives an AI agent task instructions and decision criteria. | Distributed as `SKILL.md` and reference documents. |
| MCP | Connects an AI agent to a program's tools or resources. | Uses an existing OpenDesign connection for the design stage. |

This repository is a **skill package**. It does not include a standalone MCP server, image engine, OpenDesign application, API key or generation credits.

## Requirements

| Host | Skill instructions | Image generation | Design and implementation |
| --- | --- | --- | --- |
| Codex | Shared Agent Skills format | Installed `imagegen` skill and a built-in image tool | Installed and authenticated OpenDesign + Local Codex |

**Codex** hosts this skill and generates the images; **OpenDesign with Local Codex** creates the selected design. Installing the skill does not install or authenticate OpenDesign. Missing capabilities remain incomplete; the skill does not automatically switch to a paid API, Cloud or BYOK.

## Installation

Optional installation with the existing `skills` CLI. It requires Node.js/npm and runs an external installer.

```sh
npx skills add dudqks0319-cpu/app-design-five --skill app-design-five -g -a codex
```

To avoid a separate installer, download the repository ZIP or clone the repository, then run the following **from inside the repository folder**. An existing skill with the same name is preserved.

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/app-design-five" ] || [ -L "$HOME/.agents/skills/app-design-five" ]; then
  echo 'A skill with this name already exists. Inspect it before replacing it.'
else
  mkdir "$HOME/.agents/skills/app-design-five" &&
  cp -R SKILL.md LICENSE agents references "$HOME/.agents/skills/app-design-five/"
fi
```

For project-only use, put those files in `.agents/skills/app-design-five/`. Avoid duplicate installations with the same name at user and project scope. Confirm discovery in the current host's skill list.

## Examples

```text
Use $app-design-five to build an expense tracker.
Show five image concepts first. After I choose, continue in OpenDesign.
```

```text
Use $app-design-five for design proposals only. Do not change the app code yet.
```

```text
Combine option 1's list structure with option 4's colors. Make the type larger.
```

Continue in OpenDesign with existing concepts:

```text
Use $app-design-five. I choose option 3 from the existing images.
Create this direction in OpenDesign with Local Codex, then apply it to the app.
```

Preserve the user's choice, execution mode and implementation/verification scope. This skill does not itself authorize additional agents, purchases, deployment or GitHub publication.

## Evidence and limitations

- Skill structure, internal document links and installed-file consistency have been checked; the skill was observed in Codex's skill catalog.
- On 2026-10-13, the fictional example above completed five real images → selection → OpenDesign with Local Codex → exported app → actual browser checks. This is evidence for one case, not a guarantee across apps or environments.
- Brief collection, confirmation and run start needed one MCP connection. After the run was accepted, reconnecting with the same identifiers worked. [Observed connection conditions](references/tool-routing.md#connection-and-artifact-handling-observed-in-the-demo) are now documented.
- The external installation CLI command has not yet been exercised for this project.
- Report images, design results, source implementation, local checks, real-device use and release status separately, based on observed evidence. Disclose skipped verification.

## Files and privacy

One English `SKILL.md` is the canonical agent instruction file; user guides are available in four languages. `agents/openai.yaml` holds Codex UI metadata. `references/` explains tool routing and the selected-design handoff.

Ordinary generated images and personal briefs belong in each target app's local task folder. The explicitly authorized fictional demo includes images, exported app source and sanitized evidence in `demo/`. `.local/` records, personal screenshots and credentials are excluded from distribution. No installer, background script, telemetry or automatic updater is included. The demo contains browser-only JavaScript and local storage.

## License and references

[MIT](LICENSE). This independent skill was inspired by the multiple-direction comparison idea in [oil-ui](https://github.com/oil-oil/oil-ui), introduced by the user. No code, skill text or images from that repository are included.

[Agent Skills](https://agentskills.io/home) · [Codex skills](https://learn.chatgpt.com/docs/build-skills) · [OpenDesign](https://open-design.ai/) · [skills CLI](https://github.com/vercel-labs/skills) · [MCP](https://modelcontextprotocol.io/docs/learn/architecture)
