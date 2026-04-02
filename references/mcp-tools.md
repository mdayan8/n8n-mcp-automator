# MCP Tool Selection

## First split: built-in n8n MCP server vs community n8n-mcp toolset

- Use the built-in n8n MCP server when the task is about inspecting or triggering workflows that are already exposed through n8n.
- Use the community `n8n-mcp` toolset when the task is about workflow creation, validation, retrieval, updates, or test runs.
- If neither is available, produce a workflow spec and validation checklist instead of inventing a tool path.

## Built-in n8n MCP server

Use it for:

- reading workflow context
- triggering exposed workflows
- working with n8n as a system that already exists

Do not claim it can freely author or edit every workflow from the client side.

## Community n8n-mcp toolset

Use it for the workflow lifecycle:

- discover or get workflow structure
- validate node configs, connections, and expressions
- create a workflow from a validated plan
- update a workflow in one batch when possible
- test execution before calling it done

Common validation flow from the toolset:

1. validate the workflow structure
2. validate connections
3. validate expressions
4. fix all issues before deployment
5. create or update the workflow
6. run a test execution if supported

## Tooling rules

- prefer the smallest tool that proves the next step
- do not loop on validation without changing the workflow
- do not trust missing node parameters
- do not guess a node config if the node docs or examples can be inspected first

## Important warning

The client should never imply that the workflow is production-ready until validation passes and the deployment path is actually available.
