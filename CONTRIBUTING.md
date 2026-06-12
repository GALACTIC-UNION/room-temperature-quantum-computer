# Contributing to room-temperature-quantum-computer

Welcome! This is a research platform — contributions include new substrate simulators, noise models, benchmarking protocols, and experimental data analysis tools.

## Getting Started

```bash
git clone https://github.com/<your-fork>/room-temperature-quantum-computer.git
cd room-temperature-quantum-computer
python -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"
pre-commit install
```

## Workflow

- Branch: `feature/<description>` | `fix/<description>` | `research/<description>`
- Commits: [Conventional Commits](https://www.conventionalcommits.org/)
- Every new substrate or noise model **must** include a physical reference (paper DOI) in the module docstring.

## Standards

- Python 3.11+, type annotations throughout.
- `black` + `ruff` + `mypy --strict`.
- NumPy-style docstrings with `References` sections citing primary literature.

## Testing

```bash
pytest tests/ -v --cov=rtqc --cov-report=term-missing
```

All new modules require unit tests. Benchmark modules require a reproducible reference output.

## Pull Request Process

1. CI must pass.
2. One maintainer review required; new substrate simulators need two reviewers.
3. Update `CHANGELOG.md`.
4. Squash-merge.
