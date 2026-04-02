# Recursive Repair Loop

Use this loop whenever a workflow fails validation or behaves differently than expected.

## Loop

1. identify the failing class
2. change only the minimum required part
3. re-run validation
4. compare the new failure to the previous one
5. continue only if the failure class changed or a real fix was applied

## Stop conditions

- the same failure repeats after a bounded number of passes
- the blocker is credentials, permissions, or environment access
- the user must choose the MCP mode or deployment target
- the workflow depends on data that cannot be inferred safely

## Rule

Do not rebuild the whole workflow unless the structure is actually wrong. Repair the smallest layer that explains the failure first.
