# AGENTS.md — Code quality bundle for Python repositories

Source of truth for Python code-quality checks. Copy `code_quality/` into another repo and follow the checklist.

## Porting a bundle
- **Port checklist:** `code_quality/README.md#19-using-this-bundle-in-another-repository` — questions, file edits, install, first report.
- **CI template:** `code_quality/ci/quality.yml` (copy to `.github/workflows/quality.yml`).

## Operating rules
- **Process:** `code_quality/README.md` — measure → characterise → refactor → verify → ratchet.
- **Banned constructs:** `code_quality/PY-ANTI-PATTERNS.md` — ruff rule per anti-pattern.
- **Conventions:** `code_quality/MANUAL-CONVENTIONS.md` — rules with no ruff rule.
- **Generated artifacts:** never edit `code_quality/QA-REPORT.md` or `code_quality/reports/*` by hand; regenerate via `python code_quality/scripts/qa_report.py`. Change thresholds in `qa_report.py`.
- **Gates:** never weaken to pass (`# noqa` needs reason, no deleted tests/lowered thresholds/`except: pass`), never touch vendored/generated code, never commit unless asked, missing tool/crash = failure, ratchet only shrinks.

## Quick start (this repo)
- **Run gates:** `python code_quality/scripts/qa_report.py` (writes `code_quality/QA-REPORT.md`, `code_quality/reports/qa.json`, updates `code_quality/reports/qa-history.json`)
- **CRAP/hotspots:** `python code_quality/scripts/crap_scores.py --source <package> --top 25`
- **Baseline/plan:** see `code_quality/README.md#18-appendix--measured-baseline`
