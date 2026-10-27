# QA Report — codequalitypythonprojects

> GENERATED FILE — produced by `code_quality/scripts/qa_report.py`.
> Do not edit by hand; edit the thresholds in the script instead.

Generated: 2026-10-27 · commit `8998c3b`

## Thresholds (gate)

| Metric | Threshold | Current | Status |
|---|---|---|---|
| ruff issues | ≤ 0 | 0 | 🟢 |
| files needing `ruff format` | ≤ 0 | 0 | 🟢 |
| mypy errors | ≤ 0 | 1 | 🔴 |
| test coverage (lines, owned code) | ≥ 80.0 | 0.0 % | 🔴 |
| test coverage (branches, owned code) | ≥ 75.0 | 0.0 % | 🔴 |
| max CRAP score | ≤ 6.0 | 0.0 | 🟢 |
| max cyclomatic complexity | ≤ 6 | 0 | 🟢 |
| bandit HIGH issues | ≤ 0 | 0 | 🟢 |
| dead code items | ≤ 0 | 0 | 🟢 |
| pip-audit vulnerabilities | ≤ 0 | 0 | 🟢 |
| god classes | ≤ 0 | 0 | 🟢 |
| files radon cannot parse | ≤ 0 | 0 | 🟢 |
| manual conventions | ≤ 0 | 0 | 🟢 |
| import cycles/architecture | ≤ — | not enabled | ⚪ |

## Tools not available

The metrics of these tools are **not measured**: a missing tool reports 0 findings, which looks like a clean run. Install them before trusting the numbers above.

- `bandit`
- `lint-imports`
- `pip-audit`
- `pytest`
- `radon`
- `ruff`
- `vulture`

## Lead refactor target (highest CRAP)

_No CRAP data available._

## Change hot spots (churn x complexity)

| Score | Commits | Lines changed | Max complexity | File |
|---:|---:|---:|---:|---|

## History

| Date | Coverage % | Branch % | Ruff | MyPy | Max CRAP | Max complexity | Result |
|---|---:|---:|---:|---:|---:|---:|---|
| 2026-10-27 | 0.0 | 0.0 | 0 | 1 | 0.0 | 0 | red |
