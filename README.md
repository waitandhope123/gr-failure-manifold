# GR Failure Manifold (Build by ChatGPT and rewritten by Claude for v1.1.0)

**A diagnostic test suite mapping the limits of classical General Relativity.**

This repository contains a structured collection of minimal computational "toys" designed to **locate, reproduce, and classify failure modes of classical General Relativity (GR)**. Rather than proposing new dynamics or alternatives to GR, the lab systematically probes **where and how GR loses predictive or operational meaning**.

The result is an explicit map of GR treated honestly as an **effective theory**.

---

## What this project is

- A **diagnostic test suite**, not a model or simulator
- A **boundary-mapping exercise**, not a refutation of GR
- A collection of **minimal pressure tests** that isolate specific assumptions
- A reproducible way to classify **failure triggers and failure modes**
- **[v1.1.0]** A systematic analysis of what the **pattern of failures** reveals about GR's nature

Each toy is intentionally simple and adversarial: it is designed to make a specific assumption of GR fail cleanly and observably.

---

## What this project is not

- ❌ Not a claim that GR is empirically false  
- ❌ Not a replacement theory  
- ❌ Not a quantum gravity proposal  
- ❌ Not a numerical relativity production code  

Nothing here contradicts the Einstein equations. Instead, the lab shows **where those equations stop being sufficient to define unique, observer-independent physics**.

---

## Structure of the lab

The lab consists of **64 toys**, grouped into phases that reflect increasingly global or subtle limits of the theory:

1. Geometry vs force
2. Horizons, coordinates, and invariants
3. Rotation and energy extraction
4. Consistency limits
5. Observer limitations
6. Global extensions
7. Determinism and backreaction
8. Verification and benchmarking
9. Boundaries and relational physics
10. Thickened (state-dependent) failure manifolds

Each toy is classified along four orthogonal axes:

- **Failure Trigger**  
  (geometric, observer, energetic, matter, causal, numerical, boundary, state)
  
- **Failure Mode**  
  (observer disagreement, predictability loss, energy nonconservation, invariant divergence, operational undefinedness, constraint violation, ensemble spread)
  
- **Failure Sharpness**  
  (sharp, contextual, thick)
  
- **Repairable Within Classical GR**  
  (yes / no / reinterpretation only)

---

## Executed results

All executed toys include **machine-readable JSON outputs** encoding observed results such as:

- Predictability loss
- Observer-dependent disagreements
- Invariant divergences
- Shock formation
- Constraint violations
- Instability thresholds
- Ensemble spread (for stochastic/state-dependent cases)

Toy 50 (cross-toy comparator) is intentionally declared but **not executed**.

---

## v1.1.0: Pattern Analysis & Interpretation

**New in this release:** Systematic analysis of failure manifold structure.

The v1.0 lab documented **where** GR breaks. Version 1.1.0 analyzes **what the pattern of breakage suggests** about GR's fundamental nature.

### Key Findings

Five systematic patterns emerge across the 64 toys:

1. **Energy Non-Existence** (Toys 6, 46, 51, 55, 61)  
   No invariant energy definition exists; multiple formulations disagree

2. **Geometry Underdetermination** (Toy 61 — decisive evidence)  
   Identical geometry → different physics depending on quantum state

3. **Thick Failure Zones** (Phase X: Toys 38, 61, 62 + Category C)  
   Gradual degradation, not sharp boundaries—characteristic of emergent theories

4. **Observer-Dependence** (7 independent toys: 5, 8, 24, 43, 47, 54, 56)  
   Energy, horizons, time, distance all observer-relative beyond coordinate freedom

5. **Entropy-Area Correspondence** (Toy 30)  
   Geometric quantities behave as thermodynamic entropy

### Two Interpretations

**Interpretation A (~70-75% confidence):** GR has the **wrong focus**—geometry itself is emergent from non-geometric fundamental DOFs (entanglement, information, causality, or unknown). Analogous to thermodynamics emerging from statistical mechanics.

**Interpretation B (~25-30% confidence):** GR needs a **new model** at the same geometric level—modified equations (f(R) gravity, scalar-tensor theories) while keeping geometric framework.

**See [`speculation.md`](speculation.md) for detailed analysis, evidence tables, research programs, and experimental predictions.**

---

## Why this is useful

### For Understanding GR (v1.0)
- Clarifies common GR "paradoxes" as observer or coordinate artifacts
- Makes energy ambiguity explicit rather than philosophical
- Separates curvature singularities from predictability breakdown
- Exposes where test-particle and fixed-background approximations fail
- Provides a baseline against which extensions of GR can be compared

### For Theoretical Research (v1.1.0)
- Pattern analysis constrains what kind of theory GR is (fundamental vs. emergent)
- Failure structure suggests research directions (holography, entanglement, causal sets)
- Provides testable signatures for emergent spacetime hypotheses
- Guides where to look for new physics (thick zones, observer-dependence)

This lab is most useful for readers who already know GR and want to understand **its limits, not just its successes**.

---

## How to use this repository

### As a Diagnostic Tool (v1.0)
- **Reference index** of GR failure modes
- **Sanity check** when claiming "GR predicts X"
- **Diagnostic harness** for numerical or theoretical work
- **Baseline** for comparing GR to semiclassical or modified theories

### As a Research Framework (v1.1.0)
- Test whether your theory resolves documented failure modes
- Compare your theory's boundary structure to GR's failure manifold
- Use pattern analysis to guide theoretical development
- Identify experimental signatures to test emergence hypothesis

---

## Repository Contents
```
GR-Toy-Lab/
├── toys/                    # 64 executable pressure tests
│   ├── phase_01/           # Geometry replaces force
│   ├── phase_02/           # Horizons, coordinates, invariants
│   ├── ...
│   └── phase_10/           # Thickened failure manifold
├── outputs/                 # JSON execution results
├── COMPLETE_TOY_INDEX.md   # Full toy catalog with results
├── protocol.md             # Construction and execution methodology
├── speculation.md          # [v1.1.0] Pattern analysis & interpretations
└── README.md               # This file
```

---

## End state

By Toy 64:

- Every major failure trigger is sampled
- Every major failure mode is demonstrated
- Failures range from sharp to contextual to thick
- Classical GR is mapped as an effective theory with a well-defined failure manifold

**[v1.0] This project does not argue against General Relativity.**  
**It shows exactly where and how it stops being a theory.**

**[v1.1.0] The structure of that failure manifold suggests what kind of theory it is:**  
**An emergent effective description rather than a fundamental or nearly-fundamental one.**

---

## Version History

- **v1.1.0** (Current) — Speculative analysis and emergence hypothesis
- **v1.0.1** — Documentation and protocol formalization
- **v1.0.0** — Initial failure manifold mapping (64 toys)

---

## Citation

If using this work in research:
```bibtex
@software{gr_toy_lab,
  title = {GR Failure Manifold: A Diagnostic Test Suite for Classical General Relativity},
  author = {[Sam DeRenzis]},
  year = {2026},
  version = {1.1.0},
  url = {https://github.com/waitandhope123/gr-failure-manifold/},
  note = {Systematic mapping and analysis of General Relativity failure modes}
}
```

---

## License

MIT
