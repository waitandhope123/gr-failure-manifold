# GR Failure Manifold

**Mapping GR's failure manifold: 90 computational experiments stress-testing General Relativity through black holes, rotating spacetimes, exotic geometries, quantum fields, observer superposition, and holographic emergence**

This repository contains a structured collection of minimal computational "toys" designed to **locate, reproduce, and classify failure modes of classical General Relativity (GR)**. Rather than proposing new dynamics or alternatives to GR, the lab systematically probes **where and how GR loses predictive or operational meaning**.

The result is an explicit map of GR treated honestly as an **effective theory**.

---

## What this project is

- A **diagnostic test suite**, not a model or simulator
- A **boundary-mapping exercise**, not a refutation of GR
- A collection of **minimal pressure tests** that isolate specific assumptions
- A reproducible way to classify **failure triggers and failure modes**
- A systematic analysis of what the **pattern of failures** reveals about GR's nature

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

The lab consists of **90 toys**, grouped into phases that reflect increasingly global or subtle limits of the theory:

1. **Foundations & Baselines** — Schwarzschild, Newtonian, waves, FLRW
2. **Horizons & Coordinates** — Rindler, coordinate pathologies, horizon regularity
3. **Kerr & Rotation** — Rotating black holes, energy extraction, superradiance
4. **Exotic Spacetimes** — Gödel, warp drives, wormholes, consistency limits
5. **Observers & Scales** — Tidal forces, measurement limits, equivalence principle
6. **Singularities & Extensions** — Global topology, determinism breakdown
7. **Self-Force & Backreaction** — Test particle limits, radiation reaction
8. **Numerical & Formulation** — Implementation, validation, well-posedness
9. **Boundaries & Relational** — Domain effects, relational measurements
10. **Semiclassical/QFT** — Quantum fields on curved spacetime
11. **Quantum Observers** — Observer superposition, emergent causality
12. **Holography & Emergence** — AdS/CFT, theorem boundaries, EFT limits
13. **Formulation & Topology** — PDE health, cosmic strings, classical chaos

Each toy is classified along four orthogonal axes:

- **Failure Trigger**  
  (geometric, observer, energetic, matter, causal, numerical, boundary, state, global, meta, formulation)

- **Failure Mode**  
  (observer disagreement, predictability loss, energy nonconservation, invariant divergence, operational undefinedness, constraint violation, ensemble spread, observer ontology breakdown)

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
- Observer ontology breakdown (quantum superposition of observers)
- Global theorem boundary violations
- EFT breakdown
- Failure clustering

---

## v1.1.6: Complete Redescription + 5 New Toys

**New in this release:** 

### Complete Documentation Overhaul
All 90 toys have been **completely redescribed** with comprehensive documentation including:
- **Physical setup** — What the toy models and why
- **Stress test purpose** — What conceptual trap or limitation is exposed
- **JSON interpretation guide** — How to read the output fields
- **Mathematical context** — Key equations and scaling laws
- **Over-interpretation warnings** — What NOT to conclude

### Five New Toys (086-090)

**Phase XIII Extended** with formulation health and topological diagnostics:

1. **Toy 086 — Hyperbolicity and Well-Posedness Failure**  
   Jordan-block formulation shows how weakly hyperbolic systems become ill-posed in the high-frequency limit, even without physical instability.

2. **Toy 087 — Cosmic String: Topology Without Local Curvature**  
   Idealized cosmic string demonstrates global topological effects (deficit angle, holonomy) despite vanishing curvature invariants everywhere off-axis.

3. **Toy 088 — Classical Chaos Without Singularities**  
   Two-center gravitational potential exhibits Lyapunov instability and exponential sensitivity to initial conditions in smooth, singularity-free dynamics.

4. **Toy 089 — Birkhoff Boundary via Spherically Symmetric Radiation**  
   Outgoing Vaidya spacetime shows exactly where Birkhoff's theorem fails: when the vacuum assumption is relaxed to allow radiation.

5. **Toy 090 — Hyperbolicity via Principal Symbol**  
   Abstract PDE analysis demonstrates how eigenvalue structure of the principal symbol controls well-posedness, independent of physical content.

### Structural Changes

- **Toy descriptions**: All 90 toys completely rewritten for clarity and pedagogy
- **File organization**: Python scripts, JSON outputs, and execution logs now organized in `toys/` folder
  - `py.zip` — All Python source files
  - `json.zip` — All JSON output files  
  - `logs.zip` — All execution logs
- **Phase structure**: Refined thematic organization across 13 phases
- **Version**: Updated to v1.1.6

---

## Why this is useful

### For Understanding GR
- Clarifies common GR "paradoxes" as observer or coordinate artifacts
- Makes energy ambiguity explicit rather than philosophical
- Separates curvature singularities from predictability breakdown
- Exposes where test-particle and fixed-background approximations fail
- Provides a baseline against which extensions of GR can be compared

### For Theoretical Research
- Pattern analysis constrains what kind of theory GR is (fundamental vs. emergent)
- Provides testable signatures for emergent spacetime hypotheses
- Guides where to look for new physics:
  - Pre-geometric quantum information theory
  - Quantum reference frames / relational quantum mechanics
  - Emergent causality frameworks
  - Resolution of cosmological constant problem
  - Understanding of global theorem preconditions

This lab is most useful for readers who already know GR and want to understand **its limits, not just its successes**.

---

## How to use this repository

### As a Diagnostic Tool
- **Reference index** of GR failure modes
- **Sanity check** when claiming "GR predicts X"
- **Diagnostic harness** for numerical or theoretical work
- **Baseline** for comparing GR to semiclassical or modified theories

### As a Research Framework
- Test whether your theory resolves documented failure modes
- Compare your theory's boundary structure to GR's failure manifold
- Assess whether your theory handles quantum observers
- Check if your theory addresses causality emergence
- Verify compatibility with QFT-GR incompatibility
- Evaluate whether your theory treats global theorems as conditional
- Confirm your theory has smooth EFT breakdown, not sharp cutoff
- Verify systematic failure structure matches effective theory
- Identify experimental signatures to test emergence hypothesis

---

## Repository Contents

```text
GR-Toy-Lab/
├── SPECULATION/                 # ⚠️ LEGACY - Historical speculative framework
│   ├── README.md                # (Retained for reference, not updated for v1.1.6)
│   ├── 00-OVERVIEW.md           # Executive summary through v1.1.5
│   ├── 01-INTERPRETATIONS.md   # A1/A2/B interpretations
│   ├── 02-ENERGY-EVIDENCE.md   # Energy emergence evidence
│   ├── 03-GEOMETRY-EVIDENCE.md # Geometry underdetermination
│   ├── 04-OBSERVER-EVIDENCE.md # Observer-dependence evidence
│   ├── 05-QUANTUM-BREAKDOWN.md # Quantum observer ontology
│   ├── 06-PHASE-XIII-EVIDENCE.md # Global theorems & EFT
│   ├── 07-ANALOGIES.md         # Thermodynamics parallel
│   ├── 08-IMPLICATIONS.md      # Research implications
│   ├── 09-CONFIDENCE.md        # Evidence strength
│   ├── 10-NATURE-OF-REALITY.md # Philosophical synthesis
│   ├── SPECULATION_v1_64.md    # Legacy: Through Phase X
│   ├── SPECULATION_v1_70.md    # Legacy: Through Phase XI
│   └── SPECULATION_v1_80.md    # Legacy: Through Phase XII
├── docs/                        # 📚 Complete toy documentation (NEW in v1.1.6)
│   ├── README.md                # Documentation landing page
│   ├── toys/                    # 13 phase files with full descriptions
│   │   ├── phase_01_foundations_and_baselines.md
│   │   ├── phase_02_horizons_and_coordinates.md
│   │   ├── phase_03_kerr_and_rotation.md
│   │   ├── phase_04_exotic_spacetimes_and_consistency.md
│   │   ├── phase_05_observers_and_measurement_scales.md
│   │   ├── phase_06_singularities_and_global_structure.md
│   │   ├── phase_07_self-force_and_backreaction.md
│   │   ├── phase_08_numerical_methods_and_validation.md
│   │   ├── phase_09_boundaries_and_relational_physics.md
│   │   ├── phase_10_semiclassical_and_quantum_fields.md
│   │   ├── phase_11_quantum_observers_and_emergent_causality.md
│   │   ├── phase_12_holography_and_emergence.md
│   │   └── phase_13_formulation_health_and_topology.md
│   ├── indices/                 # Navigation indices
│   │   ├── by_spacetime.md
│   │   ├── by_toy_number.md
│   │   └── quick_reference.md
│   └── guides/                  # User guides
│       └── getting_started.md
├── toys/                        # Toy implementations and outputs
│   ├── py.zip                   # All 90 Python source files
│   ├── json.zip                 # All 90 JSON output files
│   ├── logs.zip                 # All execution logs
│   ├── COMMANDS.md              # Execution commands / usage
│   ├── README.md                # Toys folder overview
│   ├── TOYS_LEGACY.md           # Legacy toy index
│   └── TOY_PROTOCOL.md          # Toy-specific execution protocol
├── LICENSE                      # MIT License
├── PROCESS.md                   # Construction and execution methodology
└── README.md                    # This file
```

---

**Note:** The `SPECULATION/` folder contains interpretive analysis and emergence hypotheses from versions 1.1.2–1.1.5. It is retained for historical reference but is not being updated for v1.1.6. The current release focuses on comprehensive toy documentation without interpretive claims.

---

## End state

By Toy 090:

- Every major failure trigger is sampled (geometric, observer, energetic, matter, causal, numerical, boundary, state, global, meta, formulation)
- Every major failure mode is demonstrated (observer disagreement, predictability loss, energy nonconservation, invariant divergence, operational undefinedness, constraint violation, observer ontology breakdown)
- Failures range from sharp to contextual to thick
- Classical GR is mapped as an effective theory with a well-defined failure manifold
- Observers, time, and causality shown to be emergent alongside spacetime
- Even global theorems, EFT validity, and foundational assumptions shown to be conditional
- Formulation health and topological structure demonstrated as independent failure modes

**This project does not argue against General Relativity.**  
**It shows exactly where and how it stops being a theory.**

The structure of that failure manifold suggests what kind of theory it is:  
**An emergent effective description rather than a fundamental or nearly-fundamental one.**

---

## Version History

- **v1.1.6** — Complete redescription of all 90 toys; 5 new toys (086-090): formulation health, cosmic strings, classical chaos, Birkhoff boundary, PDE hyperbolicity; file reorganization (py.zip, json.zip, logs.zip)
- **v1.1.5** — Phase XIII (Toys 81-85): Global theorems, EFT boundaries, meta-structure; complete speculation refactor
- **v1.1.4** — Phase XII (Toys 71-80): Quantum observers & emergent causality
- **v1.1.3** — Phase XI evidence (Toys 65-70); information-theoretic investigations
- **v1.1.2** — Addition of Toys 65-70; Phase XI empirical extension
- **v1.1.1** — Fixes README repository structure and case-sensitive links
- **v1.1.0** — Speculative analysis and emergence hypothesis
- **v1.0.1** — Documentation and protocol formalization
- **v1.0.0** — Initial failure manifold mapping (64 toys)

---

## Citation

```bibtex
@software{gr_toy_lab,
  title   = {GR Failure Manifold: A Diagnostic Test Suite for Classical General Relativity},
  author  = {DeRenzis, Sam},
  year    = {2026},
  version = {1.1.6},
  url     = {https://github.com/waitandhope123/gr-failure-manifold},
  note    = {Systematic mapping and analysis of general relativity failure modes through 90 computational experiments across 13 phases}
}
```

## License

MIT
