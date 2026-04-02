# Code Node JavaScript

## When to use it

Use a Code node when a standard n8n node cannot express the transform clearly.

## Rules

- keep code item-safe
- return the shape the next node expects
- use explicit guards for missing fields
- keep the code small enough to reason about in one pass
- prefer built-in nodes for simple mapping, filtering, and branching

## Good practice

- use Code node output only for data shaping or logic that really needs code
- log sparingly while debugging
- avoid framework-like abstractions inside a workflow
- do not make assumptions about item count unless the node mode proves it

## Constraint reminder

The Code node is not a place to do file-system work or HTTP requests when a dedicated node exists for that job.
