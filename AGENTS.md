# AGENTS.md — Code quality bundle for Python repositories

This repository is the **source of truth** for Python code-quality checks.
Copy `code_quality/` (scripts, config, anti-patterns, CI template) into another
Python repository, then follow this file exactly. Do not improvise.

## After copying into a target repository — required sequence

An agent that has just copied this bundle into a target repository MUST, in order:

1. **Ask the user these questions before touching anything** (do not guess):
   - What is the **source package name** (import root, e.g. `otlmow_model`)?
   - What is the **test directory** (e.g. `UnitTests`)?
   - Are there **generated code trees** that must be excluded (e.g.
     `Classes/`, `Datatypes/`, `Helpers/all_classes.py`)? If none, say so.
   - Which **Python versions** must be supported (lowest supported version)?
   - Which **quality gates** should block the merge on day one (`bandit`,
     `dead-code`, …)? Default: report only, block nothing.
   - Is there an existing **coverage configuration / badge workflow** that must
     not be disturbed?
2. **Edit the copied files** per section 19 of `code_quality/README.md`:
   - `code_quality/coverage.cfg`: `source = <package>`, fix `omit`.
   - `code_quality/ci/quality.yml`: the four path arguments, Python version,
     tool pins, `--exclude`, `--fail-on`.
   - `pyproject.toml`: `[tool.ruff*]` and `[tool.mypy]` paths (`src`,
     `extend-exclude`, `per-file-ignores`).
   - `DEFAULT_EXCLUDES` in both scripts: the generated trees (empty list if none).
   - Delete `code_quality/QA-REPORT.md` and `code_quality/reports/` (generated).
3. **Install the quality tools into the project virtualenv** (never `uv sync`
   afterwards — it removes them):
   ```bash
    uv pip install ruff==0.17.0 mypy radon bandit vulture
    uv pip install mutmut pip-audit jscpd   # optional
    ```
    This bundle supports Python 3.10 and higher only.
4. **Create the first quality report**, in this exact order:
   ```bash
   python -m pytest --cov=<package> --cov-report=json:code_quality/reports/coverage.json -q
   python code_quality/scripts/crap_scores.py --source <package> --exclude <generated trees>
   python code_quality/scripts/qa_report.py --source <package> --tests <tests> --tooling <tooling>
   ```
   The first two must print a CRAP table; the third must print the ten metrics
   and write `code_quality/QA-REPORT.md`. A missing tool is a failed gate, never
   a clean run.
5. **Report the resulting numbers** to the user and stop. Do not start
   refactoring.

## Non-negotiable rules

- Never edit `code_quality/QA-REPORT.md` or anything under `code_quality/reports/`
  by hand — they are generated. Change thresholds in `qa_report.py`.
- Never weaken a gate to make something pass: no `# noqa` without a reason, no
  deleted test, no lowered threshold, no `except: pass`.
- Never touch vendored/generated code.
- Never commit unless explicitly asked.
- A missing tool or a crashed gate is a failure, not a pass.
- The ratchet may only shrink: lint counts and thresholds never increase.

## Source of truth

- `code_quality/README.md` section 19 — full porting checklist.
- `code_quality/PY-ANTI-PATTERNS.md` — banned constructs and their ruff rules.
- `code_quality/ci/quality.yml` — CI template; copy to `.github/workflows/quality.yml`.
