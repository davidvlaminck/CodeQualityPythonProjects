# CodeQualityPythonProjects

Python code quality tooling for the `otlmow_model` package. It runs lint, format,
type, test/coverage, complexity, CRAP, security and dead-code checks and renders a
single QA dashboard with thresholds.

## What it does

- `code_quality/scripts/qa_report.py` — collects every quality gate into one
  report: ruff lint and format, mypy, pytest with coverage, radon complexity and
  CRAP, bandit, vulture dead code and god-class detection. Writes the snapshot to
  `code_quality/reports/qa.json` and renders `code_quality/QA-REPORT.md`.
- `code_quality/scripts/crap_scores.py` — ranks functions by CRAP score
  (change-risk anti-patterns: `complexity² × (1 − coverage/100)³ + complexity`) and
  by change hot spots (git churn × complexity).
- `code_quality/PY-ANTI-PATTERNS.md` — banned Python constructs, each mapped to
  the ruff rule that detects it, plus review conventions (`# noqa` with a reason,
  membership-test convention).
- `code_quality/ci/quality.yml` — GitHub Actions quality gate. Copies to
  `.github/workflows/quality.yml` to activate.
- `code_quality/coverage.cfg` — coverage configuration used by the gate.

## Quick start

```bash
python code_quality/scripts/qa_report.py
```

Read the thresholds in `qa_report.py` and adjust them in the script, not in the
generated report.
