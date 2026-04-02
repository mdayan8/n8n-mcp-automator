# Validation

Validate n8n workflows in layers.

## Layer 1: structure

- every node has a valid type
- connections are complete and point to real nodes
- trigger nodes exist and are wired correctly

## Layer 2: expressions

- expression syntax is valid
- field references point to real keys
- item access is consistent across branches

## Layer 3: node config

- required parameters are present
- credentials are selected where needed
- resource and operation selections are explicit
- pagination, response format, and transforms are set intentionally

## Layer 4: runtime safety

- API URLs are correct
- request payload shape matches the destination
- booleans and numbers are typed correctly
- binary data handling is intentional
- retries and failure handling are present where needed

## Layer 5: deployment readiness

- the workflow can actually be activated or published in the chosen n8n mode
- the required credentials exist
- external systems are reachable
- the workflow is not depending on a guessed default

## Error handling discipline

- fix one class of error at a time
- if the issue is external, say so instead of masking it
- do not keep rewriting the whole workflow when the bug is only one node
