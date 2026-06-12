# room-temperature-quantum-computer

> **GALACTIC-UNION** · Room-Temperature Quantum Computing Research Platform

[![CI](https://github.com/GALACTIC-UNION/room-temperature-quantum-computer/actions/workflows/ci.yml/badge.svg)](https://github.com/GALACTIC-UNION/room-temperature-quantum-computer/actions/workflows/ci.yml)
[![Python 3.11+](https://img.shields.io/badge/python-3.11%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Overview

`room-temperature-quantum-computer` (RTQC) is a research and simulation platform for exploring quantum computing substrates that can operate without cryogenic cooling. It provides simulation frameworks, noise models, and benchmarking tools for candidate room-temperature quantum computing modalities, including:

- **NV-center in diamond** — optically addressable electron spins at room temperature.
- **Photonic quantum computing** — linear optical quantum computing (LOQC) using photons.
- **Molecular spin qubits** — organic radical and metal-ion spin systems.
- **Topological insulator surface states** — theoretical exploration of robust edge-mode qubits.

> **Note:** This is a research framework. Practical fault-tolerant quantum computing at room temperature remains an open scientific challenge. This platform enables simulation, benchmarking, and experimental data analysis.

---

## Architecture

```
┌──────────────────────────────────────────────────┐
│              RTQC Framework                          │
├──────────────────────────────────────────────────┤
│  Benchmarking  │  Circuit Compiler  │  Noise Models  │
├──────────────────────────────────────────────────┤
│ NV-Center │ Photonic │ Molecular Spin │ Topological  │
│ Simulator │ LOQC Sim │    Qubit Sim   │   Insulator  │
└──────────────────────────────────────────────────┘
```

---

## Directory Structure

```
room-temperature-quantum-computer/
├── src/
│   └── rtqc/
│       ├── substrates/       # Per-modality qubit simulators
│       ├── noise/            # Decoherence & noise models
│       ├── compiler/         # Circuit-to-native-gate compilation
│       ├── benchmarks/       # RB, XEB, QPT benchmark protocols
│       └── analysis/         # Experimental data import & fitting
├── docs/
│   ├── substrates/           # Per-modality technical notes
│   ├── benchmarking.md       # Benchmark protocol guide
│   └── api/
├── tests/
│   ├── unit/
│   ├── integration/
│   └── benchmarks/
├── config/
│   ├── default.yaml
│   ├── noise_models.yaml
│   └── logging.yaml
├── .github/workflows/ci.yml
├── CONTRIBUTING.md
└── pyproject.toml
```

---

## Modules & API Surface

### `rtqc.substrates`

```python
from rtqc.substrates import NVCenterQubit, PhotonicMode

# NV-center spin qubit simulation
nv = NVCenterQubit(T2_us=2000, T1_ms=6)
nv.initialize()
nv.apply_gate("X")
result = nv.measure(shots=1024)

# Photonic mode
mode = PhotonicMode(fock_truncation=10)
```

### `rtqc.noise`

```python
from rtqc.noise import DephasingModel, AmplitudeDampingModel

noise = DephasingModel(T2_us=2000)
channel = noise.as_kraus_operators()
```

### `rtqc.benchmarks`

```python
from rtqc.benchmarks import RandomizedBenchmarking, CrossEntropyBenchmark

rb = RandomizedBenchmarking(qubit=nv, max_clifford_length=200)
results = rb.run(n_seeds=50)
print(f"Gate fidelity: {results.average_gate_fidelity:.5f}")
```

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

MIT — see [LICENSE](LICENSE).
