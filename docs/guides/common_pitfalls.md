# Common Pitfalls in Interpreting GR Toy Models

**What NOT to conclude from these computational experiments.**

---

## Overview

These toys are **diagnostic stress tests**, not physical predictions. They are designed to:
- Expose conceptual traps and ambiguities in GR
- Isolate where approximations break down
- Map boundaries between coordinate artifacts and real physics
- Test code paths and interpretation pipelines

This guide catalogs the most common misinterpretations and how to avoid them.

---

## Meta-Level Pitfalls

### Pitfall 1: Treating Toys as Predictions

❌ **Wrong:**
> "Toy 001 predicts the gravitational redshift of signals from GPS satellites."

✓ **Right:**
> "Toy 001 illustrates how Schwarzschild coordinate time freezes at the horizon, which is a coordinate artifact distinct from the physical curvature singularity at $r=0$."

**Why this matters:**
- Toys use geometric units ($G=c=1$)
- Toys assume idealized symmetries (exact spherical, stationary, vacuum)
- Toys ignore astrophysical complications (rotation, accretion, radiation)
- Parameter choices are for diagnostic clarity, not realism

**Rule:** Toys demonstrate principles and expose limitations. They are not calibrated to nature.

---

### Pitfall 2: Assuming Completeness

❌ **Wrong:**
> "If the JSON doesn't mention frame dragging, it's not relevant to this spacetime."

✓ **Right:**
> "The JSON reports diagnostics chosen to stress-test specific failure modes. Other effects may be present but not computed."

**Why this matters:**
- Each toy focuses on 1-3 conceptual targets
- Curvature tensors have 20 independent components; toys report ~3 invariants
- Many observer-dependent effects are not computed
- Global structure may extend beyond reported sample points

**Rule:** Toys are not comprehensive descriptions. They isolate specific features for testing.

---

### Pitfall 3: Forgetting the Goal

❌ **Wrong:**
> "This toy shows GR is wrong because coordinate time diverges at the horizon."

✓ **Right:**
> "This toy exposes how coordinate choices can make regular spacetime look singular, illustrating a failure mode in interpretation rather than a failure of GR."

**Why this matters:**
- The goal is cataloging GR's boundaries, not refuting GR
- Many "failures" are in human intuition or coordinate choices, not in physics
- Toys are designed to probe *where* and *how* GR becomes ill-defined

**Rule:** Toys stress-test understanding. Finding a pathology is success, not failure.

---

## Coordinate & Chart Pitfalls

### Pitfall 4: Mistaking Coordinate Singularities for Physical Ones

❌ **Wrong:**
> "The Schwarzschild metric blows up at $r=2M$, so the horizon is a singularity."

✓ **Right:**
> "Schwarzschild coordinates become singular at $r=2M$, but the Kretschmann scalar is finite there. The horizon is a coordinate artifact; the physical singularity is at $r=0$."

**Diagnostic:**
- Check `curvature_invariants.kretschmann`
- Finite → coordinate singularity
- Diverging → real singularity

**Relevant toys:** 001, 007, 008, 009, 029

---

### Pitfall 5: Trusting Coordinate Time Globally

❌ **Wrong:**
> "An infalling observer never reaches the horizon because $dt/d\tau \to \infty$."

✓ **Right:**
> "Schwarzschild coordinate time $t$ becomes ill-defined at the horizon. The infalling observer crosses in *finite proper time* $\tau$."

**Why this matters:**
- Coordinate time is a chart label, not a physical clock
- Different coordinates give different "rates" for the same event
- Only proper time along worldlines is physically meaningful

**Diagnostic:**
- Compare `dt/dtau` (coordinate rate) vs `tau_total` (physical elapsed time)
- If coordinate time diverges but proper time stays finite → coordinate artifact

**Relevant toys:** 001, 005, 007, 008, 009, 024

---

### Pitfall 6: Assuming One Chart Covers Everything

❌ **Wrong:**
> "Schwarzschild coordinates describe the entire spacetime."

✓ **Right:**
> "Schwarzschild coordinates only cover the exterior region $r > 2M$. The maximal extension requires multiple patches (Kruskal-Szekeres)."

**Why this matters:**
- Coordinate patches have domains of validity
- Global spacetime may require multiple charts (atlas)
- Horizon is often a coordinate boundary, not a spacetime boundary

**Diagnostic:**
- Where does the chart fail? (Usually where `g_tt = 0` or determinant vanishes)
- Are invariants finite there? → Chart breakdown, not spacetime breakdown
- Does another chart cover the problematic region? → Coordinate artifact confirmed

**Relevant toys:** 007, 008, 029, 031

---

## Observer Dependence Pitfalls

### Pitfall 7: Assuming Observer-Independent "Forces"

❌ **Wrong:**
> "The gravitational acceleration at $r=3M$ is exactly 0.037 in geometric units."

✓ **Right:**
> "A *static observer* hovering at $r=3M$ must fire rockets with proper acceleration 0.037 to avoid falling. A *freely falling* observer feels zero acceleration."

**Why this matters:**
- Proper acceleration is observer-dependent (worldline choice)
- Freely falling frames are inertial (locally)
- "Gravitational force" is reference-frame-dependent

**Diagnostic:**
- Check: is this for a static observer? Freely falling? Other?
- Tidal forces (curvature) are observer-independent
- Accelerations are not

**Relevant toys:** 005, 021, 025, 026

---

### Pitfall 8: Conflating Local and Global Effects

❌ **Wrong:**
> "Redshift measures the local curvature."

✓ **Right:**
> "Redshift is a *global* comparison between clocks at different locations. Local curvature is measured by tidal forces (Riemann tensor components)."

**Why this matters:**
- Redshift: ratio of frequencies *between* two events
- Curvature: derivative structure *at* an event
- Rindler spacetime has redshift but zero curvature

**Diagnostic:**
- Can you produce this effect in flat spacetime with accelerated observers? → Not curvature
- Does the Kretschmann scalar vanish? → Then any "gravity-like" effect is kinematic

**Relevant toys:** 005, 025, 066

---

### Pitfall 9: Ignoring Finite-Size Effects

❌ **Wrong:**
> "Nothing special happens at the Schwarzschild horizon because curvature is finite."

✓ **Right:**
> "For a *point particle*, curvature is modest at large-mass black hole horizons. For an *extended body*, tidal gradients across the body's size can be destructive."

**Why this matters:**
- Equivalence principle applies to point particles in the limit
- Real objects have finite size and feel tidal gradients
- Tidal forces scale with size: $a_{\text{tidal}} \sim (\text{curvature}) \times (\text{length scale})$

**Diagnostic:**
- Check tidal eigenvalues: $\sim M/r^3$
- Multiply by object size: $\Delta a \sim (M/r^3) \ell$
- Small objects survive where large objects don't

**Relevant toys:** 021, 023, 026, 044

---

## Energy & Mass Pitfalls

### Pitfall 10: Assuming Unique Gravitational Energy

❌ **Wrong:**
> "The gravitational energy at this point is 0.43."

✓ **Right:**
> "There are multiple inequivalent definitions of mass/energy in GR. They coincide under special symmetries (e.g., asymptotic flatness + stationarity), but generally disagree."

**Why this matters:**
- No local, covariant gravitational energy density
- ADM, Komar, Hawking, Bondi masses are *different* constructions
- Agreement is a special feature, not a generic expectation

**Diagnostic:**
- Does `observables.mass_definitions` show multiple values?
- Do they agree? → High symmetry case
- Do they disagree? → Generic ambiguity

**Relevant toys:** 006, 035, 046, 065

---

### Pitfall 11: Treating Energy Conditions as Physical Laws

❌ **Wrong:**
> "Energy conditions must hold, so this solution is unphysical."

✓ **Right:**
> "Energy conditions are *assumptions* used in theorems. They hold for many classical matter types but can be violated (e.g., Casimir effect, Hawking radiation, exotic cosmologies)."

**Why this matters:**
- Null Energy Condition (NEC): $T_{ab} k^a k^b \ge 0$ for null $k^a$
- Strong/Weak/Dominant conditions are *stronger* assumptions
- Quantum fields, exotic matter, and semiclassical effects can violate all of them

**Diagnostic:**
- Check explicit NEC violation in wormholes (Toy 018), Alcubierre (Toy 017)
- See semiclassical violations (Toys 061-070)

**Relevant toys:** 017, 018, 019, 022, 027, 036, 063

---

### Pitfall 12: Over-Interpreting Horizon Thermodynamics

❌ **Wrong:**
> "Black hole entropy is stored at the horizon at $kT$ per mode."

✓ **Right:**
> "Horizon area and surface gravity combine into temperature-like and entropy-like quantities, but these do not uniquely localize energy or entropy in the spacetime. They are global diagnostics."

**Why this matters:**
- Bekenstein-Hawking entropy $S = A/(4G)$ is a horizon *property*, not a local density
- Temperature $T \propto \kappa$ is defined at the horizon, not "in" the bulk
- These are heuristic guides, not predictions from a fundamental statistical ensemble

**Diagnostic:**
- Does the toy explicitly state "proxy" or "diagnostic"?
- Are these values tied to global horizon geometry?
- Is there a claim about local matter content? → Suspect if curvature is zero there

**Relevant toys:** 030, 071, 080

---

## Invariant & Observable Pitfalls

### Pitfall 13: Assuming Vanishing Invariants Mean Trivial Spacetime

❌ **Wrong:**
> "Plane gravitational waves have zero Kretschmann scalar, so they carry no physical effect."

✓ **Right:**
> "Linearized plane waves have vanishing scalar invariants at linear order, but they still produce measurable tidal forces and detector responses."

**Why this matters:**
- Scalars like $K = R_{abcd}R^{abcd}$ lose information by contracting all indices
- Curvature *tensor* components can be nonzero even if invariants vanish
- Observables depend on tensor components, not just scalars

**Diagnostic:**
- Check tidal tensor components (even if $K=0$)
- Do geodesics deviate? → Physical effect present
- Example: plane waves (Toy 003)

**Relevant toys:** 003, 049, 052

---

### Pitfall 14: Ignoring Gauge and Coordinate Modes

❌ **Wrong:**
> "This metric perturbation $h_{\mu\nu}$ is a gravitational wave because it's nonzero."

✓ **Right:**
> "Metric perturbations include gauge modes (pure coordinate changes). Only gauge-invariant combinations like the Weyl tensor represent physical waves."

**Why this matters:**
- Linearized GR: $h_{\mu\nu} \to h_{\mu\nu} + \partial_\mu \xi_\nu + \partial_\nu \xi_\mu$
- Gauge transformations can add/remove "waves" without changing physics
- Tidal observables and curvature invariants distinguish physical from gauge

**Diagnostic:**
- Check: is the metric in a gauge-fixed form (e.g., TT gauge)?
- Are curvature components reported?
- Can this perturbation be gauged away?

**Relevant toys:** 003, 040, 045, 052

---

## Causality & Horizon Pitfalls

### Pitfall 15: Confusing Horizon Types

❌ **Wrong:**
> "The horizon is where time stops."

✓ **Right:**
> "Event horizons are boundaries of causal past of future infinity. Coordinate horizons are where a chart fails. Apparent horizons are outermost trapped surfaces. These are different concepts."

**Why this matters:**
- Event horizon: global, teleological (requires knowing entire future)
- Coordinate horizon: chart-dependent artifact
- Apparent horizon: local, defined by trapped surfaces
- Killing horizon: requires symmetry

**Diagnostic:**
- Which horizon definition is being used?
- Is the spacetime stationary? (Enables Killing horizon)
- Is the full future evolution known? (Needed for event horizon)

**Relevant toys:** 001, 005, 007, 012, 029, 031, 047

---

### Pitfall 16: Assuming Horizons Imply Singularities

❌ **Wrong:**
> "There's a horizon, so there must be a singularity inside."

✓ **Right:**
> "Horizons and singularities are distinct. Rindler spacetime has a horizon but no curvature. Schwarzschild has both, but they're at different locations ($r=2M$ vs $r=0$)."

**Why this matters:**
- Penrose-Hawking singularity theorems require energy conditions + global assumptions
- Not all horizons enclose singularities
- Not all singularities have surrounding horizons

**Diagnostic:**
- Check curvature invariants at and beyond the horizon
- Does $K$ diverge? → Singularity present
- Is $K$ finite everywhere? → No curvature singularity

**Relevant toys:** 001, 005, 007, 028

---

### Pitfall 17: Trusting Closed Timelike Curves Literally

❌ **Wrong:**
> "Gödel spacetime proves time travel is possible."

✓ **Right:**
> "Gödel spacetime is an exact solution with CTCs, demonstrating that Einstein's equation doesn't forbid them. Whether nature allows CTC-containing initial data is unknown."

**Why this matters:**
- Exact solutions don't claim physical realizability
- Initial data for GR is constrained (constraints + topology)
- Chronology protection is conjectured, not proven

**Diagnostic:**
- Does the solution require exotic matter or fine-tuned initial data?
- Are energy conditions violated?
- Is this a vacuum solution or does it need special matter content?

**Relevant toys:** 016, 017, 077

---

## Approximation & Limit Pitfalls

### Pitfall 18: Pushing Weak-Field Formulas Too Far

❌ **Wrong:**
> "Newtonian potential $\Phi = -M/r$ predicts behavior arbitrarily close to $r=0$."

✓ **Right:**
> "Newtonian gravity is the weak-field, slow-velocity limit of GR. It breaks down when $|GM/rc^2| \sim 1$ (near Schwarzschild radius) or $v \sim c$."

**Why this matters:**
- Weak-field: $|h_{\mu\nu}| \ll 1$
- Slow-motion: $v \ll c$
- Far from sources: $r \gg GM/c^2$
- Violating these → perturbative expansion fails

**Diagnostic:**
- Check: is $|\Phi| \ll c^2$?
- For Schwarzschild: $2M/r \ll 1$?
- If not, Newtonian predictions unreliable

**Relevant toys:** 002, 003, 035

---

### Pitfall 19: Assuming Linearization is Always Valid

❌ **Wrong:**
> "I can compute arbitrarily large perturbations with linearized Einstein equations."

✓ **Right:**
> "Linearized gravity is valid only when $|h_{\mu\nu}| \ll 1$ and derivatives $|\partial h| \ll 1$. Beyond this, nonlinear terms dominate."

**Why this matters:**
- Gravitational waves: strain amplitude must be small
- Near sources: large gradients break linearization
- Self-gravity of wave: nonlinear when amplitude $\sim \lambda$

**Diagnostic:**
- Toy 035 explicitly tests linearization breakdown
- Check: are higher-order terms computed?
- Is strain/perturbation kept small?

**Relevant toys:** 003, 035, 040, 045

---

### Pitfall 20: Ignoring Test Particle Limits

❌ **Wrong:**
> "This orbit calculation is exact."

✓ **Right:**
> "Geodesics assume test particles: $m/M \to 0$. Finite mass ratio introduces backreaction (self-force, gravitational radiation, orbital decay)."

**Why this matters:**
- Test particle: $m$ affects $M$ negligibly
- Real binaries: comparable masses, strong backreaction
- Radiation reaction: orbits decay on timescale $\sim M^3/(m M)$

**Diagnostic:**
- Is $m/M$ explicitly treated as small?
- Does toy include radiation reaction? (e.g., Toy 034)
- Orbital parameters: do they change over time?

**Relevant toys:** 033, 034, 048

---

## Quantum & Semiclassical Pitfalls

### Pitfall 21: Treating Semiclassical Gravity as Fundamental

❌ **Wrong:**
> "Hawking radiation proves black holes evaporate exactly as computed."

✓ **Right:**
> "Semiclassical gravity (quantum fields on classical spacetime) predicts Hawking radiation, but the approximation breaks down near Planck scales or when backreaction becomes order unity."

**Why this matters:**
- Semiclassical: $\langle T_{\mu\nu} \rangle$ sourcing classical $G_{\mu\nu}$
- Neglects graviton loops, quantum spacetime fluctuations
- Breaks when curvature $\sim \ell_{\text{Planck}}^{-2}$ or $\langle T \rangle \sim G_{\mu\nu}$

**Diagnostic:**
- Check backreaction parameter: $\sim \langle T \rangle / G_{\mu\nu}$
- If order unity → semiclassical approximation failing
- Is Planck scale approaching? → Full quantum gravity needed

**Relevant toys:** 038, 061-070

---

### Pitfall 22: Assuming Vacuum Uniqueness

❌ **Wrong:**
> "The vacuum state is unique, so quantum corrections are unambiguous."

✓ **Right:**
> "Curved spacetime has infinitely many vacua (unitarily inequivalent). Observables like $\langle T_{\mu\nu} \rangle$ depend on vacuum choice."

**Why this matters:**
- No preferred vacuum in generic curved spacetime
- Minkowski vacuum $\neq$ Rindler vacuum $\neq$ Hartle-Hawking vacuum
- Different vacua → different physics (e.g., temperature)

**Diagnostic:**
- Does toy specify vacuum state?
- Unruh effect: different temperatures for different observers
- State-dependent stress energy (Toys 061, 067)

**Relevant toys:** 061, 066, 067, 071

---

### Pitfall 23: Ignoring Measurement Problem in Quantum Gravity

❌ **Wrong:**
> "Quantum observers measure spacetime geometry with arbitrary precision."

✓ **Right:**
> "Superposed observers, quantum clocks, and entangled references undermine classical notions of 'measurement' and 'time'."

**Why this matters:**
- Quantum observer in superposition: which branch defines geometry?
- Quantum clock: time is relational, not absolute background
- Entanglement: causal structure may be emergent, not fundamental

**Diagnostic:**
- Does toy put observers in quantum superposition?
- Does geometry depend on measurement outcome?
- Is causal order observer-dependent?

**Relevant toys:** 074, 075, 076, 077, 078, 079

---

## Numerical & Computational Pitfalls

### Pitfall 24: Trusting Numerics Without Validation

❌ **Wrong:**
> "The code outputs a number, so it's correct."

✓ **Right:**
> "Numerical GR requires constraint satisfaction, convergence testing, and cross-validation against known solutions."

**Why this matters:**
- Einstein equations are underdetermined (gauge freedom)
- Constraint equations must hold at all times
- Violations → unphysical evolution
- Convergence: does refinement improve answer?

**Diagnostic:**
- Check constraint violation (Toys 040, 045)
- Test: do results converge under refinement?
- Compare: known analytic limits (weak field, slow motion)

**Relevant toys:** 040-050, 086, 090

---

### Pitfall 25: Ignoring Gauge and Coordinate Effects in Code

❌ **Wrong:**
> "My simulation shows a gravitational wave because $h_{xy} \neq 0$."

✓ **Right:**
> "Metric perturbations include gauge artifacts. Verify with gauge-invariant quantities like the Weyl tensor or constraint satisfaction."

**Why this matters:**
- Numerical relativity: choosing slicing (time coordinate) and spatial gauge
- Bad gauge choices → code crashes or unphysical features
- Gauge modes ≠ physical waves

**Diagnostic:**
- Is gauge fixed explicitly?
- Are constraints preserved during evolution?
- Do gauge-invariant diagnostics confirm the feature?

**Relevant toys:** 040, 041, 042, 043, 045, 052

---

## Global Structure Pitfalls

### Pitfall 26: Assuming Local Smoothness Implies Global Smoothness

❌ **Wrong:**
> "All curvature invariants are finite, so the spacetime is globally smooth."

✓ **Right:**
> "Local regularity doesn't guarantee global well-posedness, uniqueness of evolution, or absence of Cauchy horizons."

**Why this matters:**
- Global hyperbolicity: determinism requires no closed causal curves, no Cauchy horizons
- Topology: smoothness doesn't constrain global identifications
- Boundaries: initial/boundary data must be consistent

**Diagnostic:**
- Does spacetime have a Cauchy surface?
- Are there CTCs? (Check $g_{\mu\nu} v^\mu v^\nu$ for timelike closed curves)
- Is evolution unique everywhere?

**Relevant toys:** 016, 031, 070, 076

---

### Pitfall 27: Forgetting Boundary Conditions Matter

❌ **Wrong:**
> "I solved the equations, so the solution is unique."

✓ **Right:**
> "Einstein's equations are underdetermined without specifying boundary/asymptotic conditions. Different boundaries → different physics."

**Why this matters:**
- Boundary data: what enters/leaves spacetime?
- Asymptotic flatness: ADM mass well-defined
- Compact domain: reflections, standing waves, resonances

**Diagnostic:**
- What are boundary conditions? (Dirichlet, Neumann, periodic?)
- Is domain compact or infinite?
- Does solution depend on boundary placement?

**Relevant toys:** 051, 055, 058, 081, 089

---

## Interpretation Workflow

### How to Avoid Pitfalls: Checklist

For any toy output, systematically check:

**1. Metadata**
- [ ] Units: $G=c=1$?
- [ ] Theory: GR, Newtonian, linearized?
- [ ] Approximations listed?

**2. Coordinates**
- [ ] Which chart?
- [ ] Where does it break down?
- [ ] Are singularities coordinate or physical?

**3. Curvature**
- [ ] Invariants finite or diverging?
- [ ] Zero invariants → check tensor components
- [ ] Scaling consistent with expectations?

**4. Observers**
- [ ] Which worldline/frame?
- [ ] Freely falling or accelerated?
- [ ] Local vs global measurement?

**5. Approximations**
- [ ] Weak field? ($|h| \ll 1$)
- [ ] Test particle? ($m/M \to 0$)
- [ ] Semiclassical? (backreaction small?)

**6. Numerics**
- [ ] Constraint violations reported?
- [ ] Convergence tested?
- [ ] Known limits reproduced?

**7. Cross-Checks**
- [ ] Do multiple diagnostics agree?
- [ ] Consistent with analytical predictions?
- [ ] `null` values understood?

---

## Summary: The Golden Rules

### Rule 1: Distinguish Coordinates from Physics
**Coordinate singularities ≠ physical singularities.**  
Check curvature invariants before concluding anything about spacetime.

### Rule 2: Respect Observer Dependence
**Most quantities depend on who's measuring.**  
Always specify: which worldline? Which frame? Only curvature is universal.

### Rule 3: Never Trust Single Diagnostics
**Cross-check everything.**  
Invariants, coordinates, observers, causality, energy — all must be consistent.

### Rule 4: Know Your Limits
**Every approximation has a domain of validity.**  
Weak field, linearized, test particle, semiclassical — all break down somewhere.

### Rule 5: `null` is Data
**Undefined ≠ failed to compute.**  
`null` values signal "this doesn't make sense here" — crucial information.

### Rule 6: Read the Documentation
**Toys are designed tests, not predictions.**  
Check `notes`, assumptions, validity ranges before interpreting.

### Rule 7: Embrace the Ambiguity
**GR has genuine ambiguities (energy, horizons, vacuum states).**  
When definitions disagree, that's often the point of the toy.

---

[← Back to Documentation Index](../README.md)
