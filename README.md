# django-virtualqueryset

Django library for creating QuerySet-like objects that are not backed by a database.

This is a minimal Django library ready for migration of existing tools.

## Purpose

Create virtual QuerySets for:
- Data from external APIs
- In-memory computed data
- Configuration/settings as models
- Read-only models without database tables

## Installation

```bash
pip install django-virtualqueryset
```

## Quick Start

```python
INSTALLED_APPS = [
    ...
    'virtualqueryset',
]
```

## Development

CI checks the Python/Django test matrix, Ruff, Bandit (medium/high confidence
and severity), runtime dependency advisories, and package builds.

```bash
python dev.py venv
python dev.py install-dev
python dev.py migrate
python dev.py test
```

## License

MIT

## CI packaging check

CI also installs the built wheel(s) in a clean environment and checks their
dependencies and imports without publishing. This installation check is
non-blocking during the initial rollout.

## Local audit

Install the project's development/test dependencies (including both local
packages where applicable), plus the audit tools:

```bash
python -m pip install ruff mypy bandit pip-audit vulture radon xenon pytest pytest-django pytest-cov build twine
make audit
```

Use the activated environment's Python, or pass `make audit PYTHON=/path/to/python`.
On systems without Make, run `python scripts/audit.py` directly. Git is required;
the geoaddress widget tests also require Node.js. The audit reports missing test
suites and runs all available checks even when earlier checks fail.
Xenon checks the absolute C, module B, and average A complexity thresholds. Existing
lint, typing, security, dependency, or test findings can make the audit fail.
CI also runs this audit as a non-blocking job and separately reports Radon maintainability without imposing a threshold.
