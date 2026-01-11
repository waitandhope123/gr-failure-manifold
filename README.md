# GR Failure Manifold

**A diagnostic test suite mapping the limits of classical General Relativity.**

This repository contains a structured collection of minimal computational “toys” designed to **locate, reproduce, and classify failure modes of classical General Relativity (GR)**. Rather than proposing new dynamics or alternatives to GR, the lab systematically probes **where and how GR loses predictive or operational meaning**.

The result is an explicit map of GR treated honestly as an **effective theory**.

---

## What this project is

- A **diagnostic test suite**, not a model or simulator
- A **boundary-mapping exercise**, not a refutation of GR
- A collection of **minimal pressure tests** that isolate specific assumptions
- A reproducible way to classify **failure triggers and failure modes**

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

- predictability loss
- observer-dependent disagreements
- invariant divergences
- shock formation
- constraint violations
- instability thresholds
- ensemble spread (for stochastic/state-dependent cases)

Toy 50 (cross-toy comparator) is intentionally declared but **not executed**.

---

## Why this is useful

- Clarifies common GR “paradoxes” as observer or coordinate artifacts
- Makes energy ambiguity explicit rather than philosophical
- Separates curvature singularities from predictability breakdown
- Exposes where test-particle and fixed-background approximations fail
- Provides a baseline against which extensions of GR can be compared

This lab is most useful for readers who already know GR and want to understand **its limits, not just its successes**.

---

## How to use this repository

- As a **reference index** of GR failure modes
- As a **sanity check** when claiming “GR predicts X”
- As a **diagnostic harness** for numerical or theoretical work
- As a **baseline** for comparing GR to semiclassical or modified theories

---

## End state

By Toy 64:

- Every major failure trigger is sampled
- Every major failure mode is demonstrated
- Failures range from sharp to contextual to thick
- Classical GR is mapped as an effective theory with a well-defined failure manifold

**This project does not argue against General Relativity.  
It shows exactly where and how it stops being a theory.**

---

## License

MIT (or specify if different)
