# GR Toy Lab — Documentation

**Complete documentation for all 90 computational experiments exploring General Relativity's boundaries.**

---

## Quick Navigation

### By Phase (Thematic Organization)

| Phase | Topic | Toys | File |
|-------|-------|------|------|
| **I** | [Foundations & Baselines](toys/phase_01_foundations_and_baselines.md) | 001-004 | Schwarzschild, Newtonian, waves, FLRW |
| **II** | [Horizons & Coordinates](toys/phase_02_horizons_and_coordinates.md) | 005-010 | Rindler, coordinate pathologies, ISCO |
| **III** | [Kerr & Rotation](toys/phase_03_kerr_and_rotation.md) | 011-015 | Rotating black holes, superradiance |
| **IV** | [Exotic Spacetimes](toys/phase_04_exotic_spacetimes_and_consistency.md) | 016-020 | Gödel, warp drives, wormholes |
| **V** | [Observers & Scales](toys/phase_05_observers_and_measurement_scales.md) | 021-027 | Tidal forces, equivalence principle |
| **VI** | [Singularities & Extensions](toys/phase_06_singularities_and_global_structure.md) | 028-033 | Global topology, Kruskal, mass inflation |
| **VII** | [Self-Force & Backreaction](toys/phase_07_self-force_and_backreaction.md) | 034-040 | Radiation reaction, test particle limits |
| **VIII** | [Numerical & Validation](toys/phase_08_numerical_methods_and_validation.md) | 041-050 | Formulation health, verification |
| **IX** | [Boundaries & Relational](toys/phase_09_boundaries_and_relational_physics.md) | 051-060 | Domain effects, relational measurements |
| **X** | [Semiclassical/QFT](toys/phase_10_semiclassical_and_quantum_fields.md) | 061-070 | Quantum fields on curved spacetime |
| **XI** | [Quantum Observers](toys/phase_11_quantum_observers_and_emergent_causality.md) | 071-080 | Observer superposition, emergent causality |
| **XII** | [Holography & Emergence](toys/phase_12_holography_and_emergence.md) | 081-085 | AdS/CFT, theorem boundaries |
| **XIII** | [Formulation & Topology](toys/phase_13_formulation_health_and_topology.md) | 086-090 | PDE health, cosmic strings, chaos |

---

## Alternative Navigation

### By Index
- [By Toy Number](indices/by_toy_number.md) — Sequential list 001-090
- [By Spacetime](indices/by_spacetime.md) — Schwarzschild, Kerr, FLRW, etc.
- [By Failure Mode](indices/by_failure_mode.md) — Observer disagreement, energy issues, etc.
- [Quick Reference Table](indices/quick_reference.md) — All toys with classifications

### Guides
- [Getting Started](guides/getting_started.md) — How to use this documentation
- [JSON Interpretation](guides/json_interpretation.md) — Reading toy outputs
- [Common Pitfalls](guides/common_pitfalls.md) — What not to conclude

---

## Documentation Structure

Each toy description includes:

1. **Physical Setup** — What is being modeled and why
2. **Stress Test Purpose** — What conceptual trap or limitation is exposed
3. **JSON Interpretation Guide** — How to read the output fields
4. **Mathematical Context** — Key equations and scaling laws
5. **Over-interpretation Warnings** — What NOT to conclude from the results

---

## Philosophy

These toys are **pressure tests**, not predictions. Each is designed to:
- Isolate a specific assumption or limit of GR
- Make failure observable and reproducible
- Classify the type and sharpness of breakdown
- Map where GR transitions from fundamental to effective

**The goal:** Understand precisely where and how General Relativity stops being well-defined.

---

## How to Use This Documentation

### For Learning GR's Limits
Start with **Phase I** (foundations) and work sequentially through the phases. Each builds on concepts from previous phases.

### For Research
Use the **index files** to find toys relevant to your specific question:
- Studying horizons? → See [By Spacetime](indices/by_spacetime.md)
- Energy issues? → See [By Failure Mode](indices/by_failure_mode.md)
- Need quantum examples? → Jump to **Phases X-XI**

### For Implementation
Each toy description includes:
- Expected JSON output structure
- Key diagnostic fields to check
- Common numerical issues
- How to verify correctness

---

## Quick Links

**Main Repository:** [README.md](../../README.md)  
**Toy Implementations:** [toys/](../../toys/)  
**Execution Guide:** [toys/COMMANDS.md](../../toys/COMMANDS.md)

---

*Documentation generated from comprehensive toy descriptions created by ChatGPT and organized by Claude.*
