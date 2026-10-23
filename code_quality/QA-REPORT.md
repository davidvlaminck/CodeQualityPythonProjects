# QA Report

> GENERATED FILE — produced by `code_quality/scripts/qa_report.py`.
> Do not edit by hand; edit the thresholds in the script instead.

Generated: <date> · commit `<commit>`

## Thresholds (gate)

| Metric | Threshold | Current | Status |
|---|---|---|---|
| ruff issues | ≤ 0 | - | - |
| files needing `ruff format` | ≤ 0 | - | - |
| mypy errors | ≤ 0 | - | - |
| test coverage (lines, owned code) | ≥ 80.0 | - | - |
| test coverage (branches, owned code) | ≥ 75.0 | - | - |
| max CRAP score | ≤ 6.0 | - | - |
| max cyclomatic complexity | ≤ 6 | - | - |
| bandit HIGH issues | ≤ 0 | - | - |
| dead code items | ≤ 0 | - | - |
| god classes | ≤ 0 | - | - |
| files radon cannot parse | ≤ 0 | - | - |

## Scope

The model in this repository is generated: the trees below are rewritten by the daily `auto_update` workflow and are never edited by hand. They are excluded from the lint, type, security, dead-code, complexity and CRAP checks, and from the coverage **gate** — the gate measures the code we own. Their coverage is still measured and reported below, because the model is the product.

- `<generated-tree-1>`
- `<generated-tree-2>`
- `<generated-tree-3>`

## Coverage split — generated vs hand-written

The gate above measures the **hand-written** code: that is the code a refactor touches. The whole package — generated model included — covers <package-line> % of the lines and <package-branch> % of the branches. The generated model lifts the headline number and would hide the gap in the code we own.

| Code | Statements | Line % | Branches | Branch % |
|---|---:|---:|---:|---:|
| generated (excluded) | - | - % | - | - % |
| hand-written | - | - % | - | - % |

## Lead refactor target (highest CRAP)

`<file>:<line>` → `<function>` — CRAP **<crap>** — complexity **<complexity>** — coverage **<coverage> %**

Verify with `code_quality/README.md` §7 before touching it: the behaviour must be pinned by a golden-file test first.

## Change hot spots (churn x complexity)

| Score | Commits | Lines changed | Max complexity | File |
|---:|---:|---:|---:|---|
| - | - | - | - | `<file>` |

## ruff findings per rule

| Rule | Count |
|---|---:|
| `<rule>` | - |

## History

| Date | Coverage % | Branch % | Ruff | MyPy | Max CRAP | Max complexity | Result |
|---|---:|---:|---:|---:|---:|---:|---|
| `<date>` | - | - | - | - | - | - | - |
