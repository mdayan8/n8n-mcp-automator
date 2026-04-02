---
name: n8n-mcp-automator
description: Build, validate, and debug n8n automations for any agent that can load local skills. Use when creating or repairing n8n workflows, mapping prompts to nodes, writing expressions, configuring Code nodes, validating workflow JSON, or working with n8n MCP tooling and templates. Prefer this skill for Claude Code-first workflows that still need to remain compatible with Codex, OpenCode, Warp, Antigravity, Gemini CLI, Cursor, and similar tools.
---

# n8n MCP Automator

## Overview

Use this skill to turn a plain-language automation request into a valid n8n workflow design with explicit node choices, correct expressions, and a validation pass before anything is considered ready.

Prefer this skill when the task involves:

- designing a new n8n automation from a prompt
- fixing broken expressions, node configs, or workflow JSON
- choosing the right n8n pattern before wiring nodes
- validating a workflow before deployment or activation
- working with the n8n MCP server or the community n8n-mcp toolset

If a simpler expression, Set/Edit Fields node, or built-in node can solve the task, prefer that over a Code node.

Treat Claude Code as the flagship front door, but keep the workflow logic agent-agnostic.

## Execution Model

Start by classifying the request:

1. Identify the workflow pattern.
2. Determine the operating mode.
3. Gather only the missing constraints.
4. Map data with explicit expressions and node settings.
5. Validate before deployment.
6. Repair the first failing class.
7. Re-run validation.
8. Publish or hand off only when the available tools support it.

## Operating Modes

Use the right mode before you recommend actions:

- **n8n built-in MCP server**: use for inspecting or triggering exposed workflows, not for pretending the agent can freely author or edit every workflow from the client side.
- **community n8n-mcp toolset**: use for workflow search, retrieval, validation, creation, update, and test flows when that toolset is available.
- **no MCP available**: produce a workflow plan, node map, and validation checklist instead of inventing a tool capability that does not exist.

## Core Functions

### 1. Expression Syntax Expert

- Prefer explicit `{{ }}` expressions only where dynamic values are needed.
- Use `$json`, `$node`, and time helpers carefully and consistently.
- Keep field paths exact; do not guess nested keys.

### 2. MCP Tools Expert

- Pick the lightest available tool path that actually exists.
- Search for relevant nodes, examples, or templates before inventing a configuration.
- Validate the workflow before claiming it is ready.

### 3. Workflow Pattern Selector

- Choose the architecture before assembling nodes.
- Prefer one of the standard patterns in [references/patterns.md](./references/patterns.md).
- Do not force an AI chain when a webhook, HTTP request, or scheduled pipeline is enough.

### 4. Validation Expert

- Run a structural check, an expression check, and a deployment-readiness check.
- Fix all workflow-internal errors before externalizing the workflow.
- Stop when the remaining issue is credentials, access, or environment setup.
- Use a bounded recursive repair loop when a failure is found:
  1. identify the failure class
  2. fix only that class
  3. re-validate
  4. stop after a few passes if the issue does not change

### 4b. Failure Taxonomy

- **Expression failure**: wrong `$json`, `$node`, or path reference.
- **Node config failure**: required field missing, wrong operation, or unsafe default.
- **Credentials failure**: auth not set or wrong auth selected.
- **Mode failure**: wrong MCP tool path or unsupported capability assumption.
- **Payload failure**: trigger data shape is different from what the workflow expects.
- **External failure**: destination API, environment, or deployment platform is the blocker.
- **Template failure**: a template or example was copied without adapting the field map.

### 5. Node Configuration Expert

- Set required node parameters explicitly.
- Treat defaults as suspect unless the node docs say the default is safe.
- Validate trigger nodes, branching nodes, and transport nodes separately.
- Prefer a standard node, then Set/Edit Fields, then Code, in that order.

### 6. Code JavaScript Expert

- Use Code nodes only when node wiring cannot express the transformation cleanly.
- Write item-safe code and return the expected item shape.
- Prefer the code guidance in [references/code-js.md](./references/code-js.md).
- Keep JavaScript transforms small enough to be revalidated quickly.

### 7. Code Python Expert

- Use Python only when it is a better fit than JavaScript for the task.
- Respect the sandbox and library constraints of the target n8n environment.
- Prefer the code guidance in [references/code-python.md](./references/code-python.md).
- Do not use Python as a workaround for node config or expression mistakes.

## When To Stop And Ask

Ask for missing information when it changes the workflow design:

- which n8n environment is being used
- whether the workflow must be draft-only or production-ready
- whether credentials already exist
- what payload shape the trigger produces
- what destination system the workflow must call
- whether the user wants to use the built-in MCP server, the community n8n-mcp toolset, or both
- whether the user wants Claude Code-first framing or a neutral repo voice

## Validation Order

Validate in this order:

1. trigger and node selection
2. required fields and credentials
3. expressions and field references
4. branching and item flow
5. external API assumptions
6. deployment or activation readiness
7. recursive repair stability
8. stop-condition check

If a failure remains after validation, fix the workflow first. If the failure is environmental or external, report it clearly instead of masking it.

## References

- Read [references/sources.md](./references/sources.md) for the official n8n and n8n-MCP source material.
- Read [references/mcp-tools.md](./references/mcp-tools.md) for tool-selection rules and mode boundaries.
- Read [references/patterns.md](./references/patterns.md) for the five default workflow architectures.
- Read [references/validation.md](./references/validation.md) for the strict validation checklist.
- Read [references/repair-loop.md](./references/repair-loop.md) for the recursive failure-repair loop.
- Read [references/failure-modes.md](./references/failure-modes.md) for the failure taxonomy.
- Read [references/node-configuration.md](./references/node-configuration.md) for common node-setup rules.
- Read [references/expressions.md](./references/expressions.md) for expression syntax reminders.
- Read [references/code-js.md](./references/code-js.md) for Code node JavaScript patterns.
- Read [references/code-python.md](./references/code-python.md) for Code node Python patterns.
