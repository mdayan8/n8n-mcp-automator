# Failure Modes

## Expression failure

- wrong path
- wrong node reference
- wrong type in a branch condition

## Node configuration failure

- missing required property
- wrong resource/operation pairing
- unsafe or misleading default

## Credentials failure

- missing auth
- wrong auth scheme
- credential exists but does not match the endpoint

## Payload failure

- trigger data shape changed
- nested property missing
- binary data expected but text received

## Mode failure

- built-in MCP server treated like a workflow authoring API
- community toolset assumed when only inspection exists

## External failure

- destination API rejected the call
- n8n environment is not reachable
- deployment path is unavailable

## Rule

Repair the first real failure, not every hypothetical failure.
