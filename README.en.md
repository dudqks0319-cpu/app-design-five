# App Design Five

[한국어](README.md) · [English](README.en.md) · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

**An AI agent skill that shows five real UI image concepts before building an app.**

Five images → your choice or combination → design → requested app implementation

Compare five distinct directions for the same core app screen. Choose one or combine them, such as “option 1's layout with option 4's colors.” The selected direction becomes an OpenDesign design using Local Codex, then an app implementation if requested. Routine bug fixes and status questions do not start this workflow.

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
| OpenCode | Same `SKILL.md` format | An image tool available in that host; existing concepts can be reused | An available OpenDesign connection, or direct implementation explicitly chosen by the user |

Installing this skill in OpenCode does not connect Codex's image tool. Missing capabilities remain incomplete; the skill does not automatically switch to a paid API, Cloud or BYOK.

## Installation

Optional installation with the existing `skills` CLI. It requires Node.js/npm and runs an external installer.

```sh
npx skills add dudqks0319-cpu/app-design-five --skill app-design-five -g -a codex -a opencode
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

OpenCode with existing concepts:

```text
Use the app-design-five skill. I choose option 3 from the existing images.
For this task, implement it in the current OpenCode project instead of OpenDesign.
```

Preserve the user's choice, execution mode and implementation/verification scope. This skill does not itself authorize additional agents, purchases, deployment or GitHub publication.

## Evidence and limitations

- Skill structure, internal document links and installed-file consistency have been checked; the skill was observed in Codex's skill catalog.
- The complete five-image → OpenDesign → app implementation workflow using this skill has not yet been exercised.
- OpenCode runtime behavior and the external installation CLI command have not yet been exercised for this project.
- Report images, design results, source implementation, local checks, real-device use and release status separately, based on observed evidence. Disclose skipped verification.

## Files and privacy

One English `SKILL.md` is the canonical agent instruction file; user guides are available in four languages. `agents/openai.yaml` holds Codex UI metadata. `references/` explains tool routing and the selected-design handoff.

Generated images and private briefs belong in the target app's local task folder. `.local/` records, personal screenshots and credentials are excluded from distribution. This package includes no executable scripts, telemetry or automatic updater.

## License and references

[MIT](LICENSE). This independent skill was inspired by the multiple-direction comparison idea in [oil-ui](https://github.com/oil-oil/oil-ui), introduced by the user. No code, skill text or images from that repository are included.

[Agent Skills](https://agentskills.io/home) · [Codex skills](https://learn.chatgpt.com/docs/build-skills) · [OpenCode skills](https://opencode.ai/docs/skills/) · [skills CLI](https://github.com/vercel-labs/skills) · [MCP](https://modelcontextprotocol.io/docs/learn/architecture)
