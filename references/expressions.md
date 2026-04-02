# Expression Syntax

## Core patterns

- use `{{ }}` only where a parameter needs a dynamic value
- read current input data with `$json`
- reference earlier nodes only by exact node name
- use time helpers for schedule-aware workflows

## Common examples

- current field: `{{$json.body}}`
- nested field: `{{$json.body.city}}`
- earlier node output: `{{$node["HTTP Request"].json}}`
- current time: `{{$now}}`

## Rules

- do not guess nested field names
- keep path references exact
- prefer expressions for mapping, not for large business logic
- move complex transforms into a Code node only when needed

## Common failure mode

Most expression failures come from a wrong path, a wrong node name, or a value that changed shape between nodes.
