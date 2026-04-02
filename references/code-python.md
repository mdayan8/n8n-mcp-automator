# Code Node Python

## When to use it

Use Python only when it is a better fit than JavaScript for the workflow task.

## Rules

- keep logic short and deterministic
- assume a constrained environment
- return the expected item structure
- avoid imports unless the environment supports them
- prefer standard library patterns when possible

## Good practice

- use Python for compact data transforms or text handling
- keep the flow readable for future edits
- do not depend on runtime features that are not guaranteed by the n8n environment

## Constraint reminder

Do not use the Code node to replace dedicated file or HTTP nodes.
