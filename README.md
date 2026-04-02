# Claude Code n8n MCP Automator

<p align="center">
  <img src="assets/banner.svg" alt="n8n MCP Automator banner" width="960" />
</p>

`n8n-mcp-automator` is a Claude Code-first skill for n8n workflow automation, n8n MCP server workflows, and production-shaped automations. It helps an agent turn a plain prompt into a valid workflow plan, then validate expressions, node configuration, and failure recovery before the workflow ships. It is still agent-agnostic under the hood and works for tools that can load local skill folders, including Codex, Warp, Antigravity, Gemini CLI, Cursor, OpenCode, and similar systems.

This repo is for people who want:

- faster n8n workflow design from a plain prompt
- fewer broken expressions and node configs
- better validation before deployment
- a reusable skill for Claude Code and other local-skill agents

## About

This is a focused, opinionated skill for building and validating n8n workflows correctly the first time. It is built around the failure modes that matter most in practice: wrong node selection, invalid expressions, missing credentials, bad field mapping, and validation loops that never resolve.

If you are searching for `Claude Code n8n skill`, `n8n workflow validation`, `n8n expression debugging`, or `n8n MCP server automation`, this repo is designed to surface for those queries and give a direct answer.

<p align="center">
  <img alt="n8n" src="https://img.shields.io/badge/topic-n8n%20%26%20MCP-fd5f00?logo=n8n&logoColor=white" />
  <img alt="agents" src="https://img.shields.io/badge/agents-multi--agent%20skill-111827?logo=github&logoColor=white" />
  <img alt="Claude Code" src="https://img.shields.io/badge/flagship-Claude%20Code-1f2937?logo=anthropic&logoColor=white" />
  <a href="https://x.com/mdayan24X" aria-label="Open X profile for mdayan24X">
    <img alt="X" src="https://img.shields.io/badge/follow-%40mdayan24X-000000?logo=x&logoColor=white" />
  </a>
</p>

<p align="center">
  <img src="assets/logo.svg" alt="n8n MCP Automator logo" width="144" />
</p>

## Table of Contents

- [Why This Repo Exists](#why-this-repo-exists)
- [About](#about)
- [Highlights](#highlights)
- [What It Covers](#what-it-covers)
- [Compatibility](#compatibility)
- [What You Get](#what-you-get)
- [Install](#install)
- [Example Requests](#example-requests)
- [Repository Structure](#repository-structure)
- [Related Sources](#related-sources)
- [Search Phrases](#search-phrases)
- [Contributing](#contributing)
- [Maintainer](#maintainer)
- [License](#license)
- [Safety Note](#safety-note)

Use this skill when an agent needs to:

- design a new n8n workflow from a prompt
- repair broken node configs or expressions
- choose a workflow pattern before wiring nodes
- validate workflow JSON before activation or deployment
- work with the n8n MCP server or the community n8n-mcp toolset

## Highlights

- Claude Code-first n8n workflow automation
- recursive workflow repair
- expression debugging
- node configuration sanity checks
- production-shaped workflow planning
- keeping Claude Code useful without losing multi-agent portability
- recursive repair loops for broken workflows
- validation-first workflow design

## What It Covers

- n8n workflow automation
- n8n MCP server usage
- Claude Code skill packaging
- expression syntax and field mapping
- MCP tool selection and mode boundaries
- workflow pattern selection
- validation and error recovery
- recursive repair loops
- failure classification
- node configuration rules
- Code node JavaScript
- Code node Python
- common n8n failure recovery

## Compatibility

| Agent | Common skill path | Notes |
| --- | --- | --- |
| Antigravity | `.agent/skills/` | Project-local skill path |
| Claude Code | `.claude/skills/` | Project-local skill path |
| Codex | `.codex/skills/` | Project-local skill path |
| Cursor | `.cursor/skills/` | Project-local skill path |
| Gemini CLI | `.gemini/skills/` | Project-local skill path |
| GitHub Copilot | `.github/skills/` | Project-local skill path |
| OpenCode | `.opencode/skills/` | Project-local skill path |
| Warp | `.warp/skills/` or agent-specific skill folders | Check the local skill path used by your setup |

## Why This Repo Exists

Most workflow prompts fail for the same reasons: wrong node choice, weak expressions, missing credentials, and validation loops that never resolve. This skill is meant to reduce that failure rate by giving the agent a strict n8n playbook and a recursive repair loop.

If you want a fast answer to questions like “How do I build this n8n workflow correctly?” or “Why is this expression breaking?”, this is the repo to start with.

## What You Get

- Claude Code-first branding with multi-agent compatibility
- a recursive repair loop for workflow failures
- a failure taxonomy that explains what broke
- a validation order that matches how n8n actually fails
- concise references for expressions, node config, patterns, and Code nodes

## Install

Copy the folder into the skill directory your agent reads. For example:

```bash
SKILLS_DIR="${SKILLS_DIR:-$HOME/.codex/skills}" && mkdir -p "$SKILLS_DIR" && rsync -a --exclude '.git' ./ "$SKILLS_DIR/n8n-mcp-automator/"
```

If your agent uses a different local skill path, copy the folder there instead.

## Example Requests

- `Build a webhook -> Slack notification workflow`
- `Fix this n8n expression and explain why it broke`
- `Turn this API spec into an n8n workflow`
- `Validate this workflow JSON before I deploy it`
- `Create a scheduled content pipeline with retries and alerts`

## Repository Structure

- `SKILL.md` contains the workflow rules and trigger guidance
- `references/` contains the syntax, validation, and pattern guides
- `references/repair-loop.md` contains the recursive recovery loop
- `references/failure-modes.md` contains the failure taxonomy
- `assets/` contains small visual assets for the README
- `agents/openai.yaml` contains the skill metadata used by Codex-style tooling

## Related Sources

- [n8n MCP server docs](https://docs.n8n.io/advanced-ai/accessing-n8n-mcp-server/)
- [n8n AI Workflow Builder docs](https://docs.n8n.io/advanced-ai/ai-workflow-builder/)
- [n8n workflow docs](https://docs.n8n.io/workflows/)
- [n8n Code node docs](https://docs.n8n.io/code/code-node/)
- [community n8n-mcp toolset](https://github.com/czlonkowski/n8n-mcp)

## Search Phrases

- n8n workflow automation
- n8n MCP server
- Claude Code n8n skill
- n8n workflow validation
- n8n expression debugging
- n8n node configuration
- Claude Code n8n workflow automation
- build n8n workflows with Claude Code
- n8n automation skill for Claude Code
- validate n8n workflows with MCP

## Contributing

- keep changes small and specific
- add a reference file only when it reduces repeated reasoning
- prefer explicit workflow rules over broad claims
- keep the skill agent-agnostic unless a rule is truly tool-specific

## Maintainer

X: [@mdayan24X](https://x.com/mdayan24X)

## License

MIT License.

## Safety Note

This repository can influence workflow automation, credentials handling, and deployment behavior. Review it before using it in production.
