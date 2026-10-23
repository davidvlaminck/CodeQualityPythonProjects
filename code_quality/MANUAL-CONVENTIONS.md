# Manual conventions (no ruff rule)

This file collects conventions that cannot be enforced by a linter. Append a new
entry here whenever a new manual rule is agreed upon.

Each entry here must have a corresponding custom check, and that check's result
must be added to the QA report table.

## Membership tests

- Use a set (or tuple) for `x in {...}` membership checks instead of a list
  literal when there are 4 or more members. No ruff rule; manual convention.
