# Node Configuration

## General rules

- set every required field explicitly
- assume defaults are unsafe until the docs prove otherwise
- prefer the node that expresses the intent most directly
- validate node wiring before fine-tuning the prompt or expression

## Common node-specific rules

- **Webhook**: set the method, path, and response behavior deliberately.
- **HTTP Request**: set method, URL, auth, headers, query params, response format, and pagination intentionally.
- **IF / Switch**: coerce values before branching; do not rely on loose truthiness.
- **Set / Edit Fields**: use for normalization, renaming, and shape control.
- **Code**: use only when the workflow cannot be modeled cleanly with standard nodes.
- **Wait / Schedule**: make timing and polling explicit.

## Configuration smell

If the workflow depends on an implied default, a hidden credential, or an untyped value, fix that before declaring the workflow stable.
