---
setup:
  - [python3, -m, venv, .venv]
  - [.venv/bin/pip, install, --quiet, -e, ., pytest]
---

The library is pure standard library (`setup.py` has no `install_requires`), so the only
dependency is `pytest`, mirroring CI (`.github/workflows/test.yml`: `pip install . pytest`).
The editable install lets tests import `mailparser_reply` from this worktree.

Run the tests with `.venv/bin/python -m pytest test/ -v` (or `python -m unittest discover test`,
as the README says). `.venv` is gitignored.

Relies on outside the worktree: a `python3` (3.7+, for `dataclasses`) on `PATH` — here the
pyenv shim — and network access to PyPI for `pytest`.
