# Workflow Patterns

Use the lightest pattern that fits the request.

## 1. Webhook processing

Use when external systems push data into n8n.

- trigger: Webhook
- normalize payload: Set/Edit Fields or Code
- branch or enrich: IF, Switch, HTTP Request
- respond or forward: Slack, email, database, or API call

## 2. HTTP API call chain

Use when n8n must call an external API.

- trigger: manual, webhook, or schedule
- authenticate explicitly
- shape request data before the HTTP Request node
- paginate and retry deliberately
- validate response mapping before downstream nodes

## 3. Database pipeline

Use when records move through a durable process.

- trigger: schedule or webhook
- read or write database rows
- transform records in a deterministic step
- keep idempotency and retries in mind
- emit an audit or alert step

## 4. AI agent chain

Use when the workflow genuinely needs model reasoning.

- fetch or assemble context first
- keep prompts and tools explicit
- use RAG or lookup steps before generation
- validate the output format before it reaches a production node

## 5. Scheduled trigger

Use for batch jobs, digests, cleanup, or syncs.

- trigger: Schedule
- query only the time window you need
- deduplicate downstream writes
- add a notification on failure or anomaly

## Pattern rule

If a prompt does not fit one of these patterns, ask a clarifying question before the agent starts wiring nodes.
