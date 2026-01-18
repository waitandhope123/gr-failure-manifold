# JSON Interpretation Guide

**How to read the structured output from GR toy models.**

---

## Overview

Every toy exports a JSON file with standardized top-level keys:

```json
{
  "toy_id": "toy_001_schwarzschild",
  "theory": "General Relativity",
  "spacetime": "Schwarzschild",
  "units": {"G": 1, "c": 1},
  "parameters": {"M": 1.0},
  "notes": {},
  "sample_points": [...],
  "observables": {}
}
```

This structure enables:
- Direct comparison across toys
- Automated analysis pipelines
- Separation of coordinate artifacts from physical effects
- Explicit handling of undefined quantities

---

## Top-Level Fields

### `toy_id` (string)
Unique identifier matching the Python filename.

**Example:** `"toy_001_schwarzschild"`

**Purpose:** Cross-referencing outputs with source code.

---

### `theory` (string)
Which gravitational theory is being used.

**Common values:**
- `"General Relativity"`
- `"Newtonian Gravity"`
- `"Linearized GR"`
- `"Scalar Gravity"` (in comparison toys)

**Purpose:** Distinguish GR from limits, approximations, or alternative theories.

---

### `spacetime` (string)
Which metric or solution is being evaluated.

**Examples:**
- `"Schwarzschild"`
- `"Kerr"`
- `"FLRW (matter-dominated)"`
- `"Rindler"`
- `"Minkowski"`

**Purpose:** Identify the background geometry.

---

### `units` (object)
Unit conventions for dimensional quantities.

**Standard:**
```json
{"G": 1, "c": 1}
```

**Purpose:** All toys use geometric units unless explicitly stated otherwise. Speeds are dimensionless fractions of $c$, masses are in units where $G=c=1$.

---

### `parameters` (object)
Physical parameters defining this run.

**Examples:**
```json
{"M": 1.0}                    // Schwarzschild mass
{"M": 1.0, "a": 0.9}          // Kerr mass and spin
{"t_0": 1.0, "power": 0.667}  // FLRW scale factor parameters
```

**Purpose:** Specify the model configuration. Changing these parameters should produce predictable scaling in outputs.

---

### `notes` (object)
Human-readable metadata about the run.

**Common fields:**
```json
{
  "approximations": "Weak field, linearized perturbation",
  "validity": "r > 10M for numerical stability",
  "assumptions": "Vacuum exterior, test particle limit"
}
```

**Purpose:** Document limitations, approximations, and applicability ranges.

---

### `sample_points` (array)
Array of diagnostic packets, one per evaluation point.

**Structure:** Each element contains:
```json
{
  "coordinates": {...},
  "curvature_invariants": {...},
  "local_observables": {...},
  "causal_structure": {...}
}
```

**Purpose:** Core output. Most analysis focuses here.

---

### `observables` (object)
Global or aggregate observables not tied to a single point.

**Examples:**
```json
{
  "redshift_and_distances": [...],
  "horizon_crossing_times": {...},
  "mass_definitions": {...}
}
```

**Purpose:** Quantities requiring integration, comparison between points, or global computation.

---

## Sample Point Structure

Each `sample_points[i]` entry has four required subsections:

### 1. `coordinates` (object)

Coordinate values for this evaluation point.

**Examples:**
```json
{"t": 0.0, "r": 10.0, "theta": 1.5708, "phi": 0.0}  // Schwarzschild
{"x": 0.0, "y": 0.0, "z": 5.0}                     // Cartesian
{"rho": 1.0, "eta": 0.0}                           // Rindler
```

**Interpretation:**
- Coordinates are chart-dependent labels, not invariants
- Coordinate singularities (e.g., $r=2M$ in Schwarzschild) may appear
- Multiple coordinates may describe the same physical event

**Key principle:** Never interpret coordinate divergences as physical effects without checking invariants.

---

### 2. `curvature_invariants` (object)

Coordinate-independent scalar curvature quantities.

**Common fields:**
```json
{
  "ricci_scalar": 0.0,           // R
  "kretschmann": 0.048,          // R_{abcd} R^{abcd}
  "weyl_squared": null           // C_{abcd} C^{abcd} if computable
}
```

**Interpretation:**
- **Non-zero Ricci scalar:** Spacetime contains matter/energy or cosmological constant
- **Non-zero Kretschmann:** True curvature present (vacuum or not)
- **Scaling:** For Schwarzschild, $K \sim M^2/r^6$ — diverges at $r \to 0$, finite at $r=2M$

**Physical meaning:**
- Diverging invariants → **real singularity**
- Finite invariants → coordinate artifacts (if coordinate expressions diverge)

**Critical rule:** If `kretschmann` is finite but coordinate-dependent quantities diverge, suspect a coordinate singularity.

---

### 3. `local_observables` (object)

Observer-dependent measurements at this point.

**Common fields:**
```json
{
  "lapse_dtau_dt": 0.866,                    // Proper time per coordinate time
  "proper_acceleration": 0.028867,           // |a^μ| for static observer
  "tidal_eigenvalues_static_orthonormal": {  // Geodesic deviation
    "radial": -0.001,
    "transverse": 0.0005
  },
  "redshift_factor": 1.1547                  // (1 - 2M/r)^{-1/2}
}
```

**Interpretation:**

#### Lapse / Time Dilation
- `lapse_dtau_dt` = $d\tau/dt$ for static observers
- Schwarzschild: $\sqrt{1 - 2M/r}$
- Goes to zero at horizon → static observers cease to exist there
- **null means:** "not defined" (inside horizon, or observer frame doesn't exist)

#### Proper Acceleration
- Magnitude of 4-acceleration needed to stay at fixed coordinates
- Diverges as $r \to 2M$ in Schwarzschild
- **Physical meaning:** "Hovering" near horizon requires infinite thrust
- Zero for freely falling observers

#### Tidal Eigenvalues
- Principal components of Riemann curvature felt by local frame
- Signs indicate stretching (negative) vs squeezing (positive)
- Schwarzschild: radial component negative, transverse positive
- **Scaling:** $\sim M/r^3$

**Observer dependence warning:** These quantities depend on which worldline and frame you choose. Different observers at the same event measure different values.

---

### 4. `causal_structure` (object)

Light cone geometry and null geodesic behavior.

**Common fields:**
```json
{
  "radial_null_cone_dr_dt": {
    "outgoing": 0.75,
    "ingoing": -0.75
  },
  "photon_sphere_radius": 3.0,
  "coordinate_horizon_location": 2.0
}
```

**Interpretation:**

#### Null Cone Slopes
- `dr/dt` for outgoing/ingoing radial null rays
- Schwarzschild: $\pm(1 - 2M/r)$
- Both approach zero as $r \to 2M$
- **Meaning:** Coordinate time $t$ is a bad global time coordinate
- **Not physical:** Light doesn't "slow down" — coordinate description fails

#### Horizons
- `null` indicates no coordinate horizon in this chart
- Finite value indicates horizon location in these coordinates
- **Critical:** Horizons are coordinate-dependent surfaces where null rays become tangent to constant-coordinate slices

**Causal structure warning:** Coordinate light-cone "freezing" does not imply physical standstill. Check proper time along geodesics.

---

## Special Values: `null`

The JSON schema requires all keys to exist, but values can be `null` when:

1. **Undefined in this theory**
   - Newtonian gravity: `"kretschmann": null` (no curvature tensors)
   - Linearized GR: curvature invariants often zero or null

2. **Undefined for this observer/frame**
   - Inside horizon: `"lapse_dtau_dt": null` (static observers don't exist)
   - Rindler coordinates beyond horizon: quantities undefined

3. **Numerically inaccessible**
   - Division by zero avoided: `null` instead of `Infinity`
   - Square root of negative number: `null` instead of `NaN`

4. **Computation not applicable**
   - Event horizon in matter-dominated FLRW: `null` (diverges)
   - Quantities requiring global information in local patch

**Interpretation rule:** `null` is intentional metadata, not a bug. It signals "this quantity doesn't make sense here" and prevents misinterpretation.

---

## Observable Patterns

### Pattern 1: Coordinate Artifact Detection

**Symptoms:**
- Coordinate-time rates diverge: `dt/dr → ∞`
- Lapse vanishes: `lapse_dtau_dt → 0`
- Null cone slopes collapse: `dr/dt → 0`

**Check:**
- Is `kretschmann` finite? → Coordinate singularity
- Is `kretschmann` diverging? → Real singularity

**Example (Schwarzschild at $r=2M$):**
```json
{
  "coordinates": {"r": 2.0},
  "curvature_invariants": {"kretschmann": 0.046875},  // Finite!
  "local_observables": {"lapse_dtau_dt": null},       // Undefined
  "causal_structure": {"dr_dt_outgoing": 0.0}         // Coordinate freeze
}
```

**Conclusion:** Horizon is coordinate artifact, not physical singularity.

---

### Pattern 2: Observer Dependence

**Same event, different observers:**

```json
// Static observer
{"proper_acceleration": 0.289}  // Must accelerate to hover

// Freely falling observer
{"proper_acceleration": 0.0}    // Feels no force
```

**Lesson:** "Gravitational force" is observer-dependent. Only tidal effects (curvature invariants) are universal.

---

### Pattern 3: Scaling Laws

**Schwarzschild as $r$ varies:**

| Field | Scaling | Meaning |
|-------|---------|---------|
| `kretschmann` | $\propto r^{-6}$ | Curvature grows rapidly inward |
| `tidal_eigenvalues` | $\propto r^{-3}$ | Tidal forces strengthen |
| `proper_acceleration` | $\propto r^{-2}$ | Hovering cost increases |
| `redshift_factor` | $\propto (1-2M/r)^{-1/2}$ | Time dilation deepens |

**Use scaling laws to:**
- Verify code correctness
- Extrapolate behavior
- Identify coordinate vs physical effects

---

### Pattern 4: Horizon Diagnostics

**Multiple indicators should align:**

| Indicator | Schwarzschild Horizon ($r=2M$) |
|-----------|-------------------------------|
| `lapse_dtau_dt` | null (static frame fails) |
| `kretschmann` | $\sim 0.047$ (finite curvature) |
| `dr_dt_outgoing` | $0$ (coordinate light freeze) |
| `proper_time_to_horizon` | finite (reachable) |

**Consistency check:** If some indicators suggest horizon but others don't, investigate:
- Wrong coordinate chart?
- Numerical error?
- Different type of horizon (Rindler vs event horizon)?

---

## Common Fields Reference

### Curvature Invariants

| Field | Formula | Meaning |
|-------|---------|---------|
| `ricci_scalar` | $R$ | Trace of Ricci tensor; matter content |
| `kretschmann` | $R_{abcd}R^{abcd}$ | Total curvature strength |
| `weyl_squared` | $C_{abcd}C^{abcd}$ | Vacuum/tidal part of curvature |

### Local Observables (Schwarzschild example)

| Field | Formula | Units |
|-------|---------|-------|
| `lapse_dtau_dt` | $\sqrt{1-2M/r}$ | dimensionless |
| `proper_acceleration` | $M/(r^2\sqrt{1-2M/r})$ | $c^2/\text{length}$ |
| `redshift_factor` | $(1-2M/r)^{-1/2}$ | dimensionless |

### Causal Structure

| Field | Meaning |
|-------|---------|
| `dr_dt_outgoing` | Coordinate slope $dr/dt$ for outgoing light |
| `dr_dt_ingoing` | Coordinate slope $dr/dt$ for ingoing light |
| `coordinate_horizon` | Radius where coordinate time freezes |

---

## Red Flags: What NOT to Conclude

### ❌ Don't Over-Interpret Absolute Magnitudes

**Wrong:**
> "The tidal force is 0.001, so it's negligible."

**Right:**
> "The tidal force scales as $M/r^3$. At this $r/M$, the fractional stretch per unit length is 0.001."

**Why:** Geometric units obscure physical scales. Always check dimensional scaling.

---

### ❌ Don't Confuse Coordinates with Physics

**Wrong:**
> "$dr/dt \to 0$ means light stops at the horizon."

**Right:**
> "$dr/dt \to 0$ means Schwarzschild coordinate $t$ becomes a bad time coordinate at the horizon. Infalling observers cross in finite proper time."

**Why:** Coordinate singularities are chart artifacts, not physical effects.

---

### ❌ Don't Trust Single Diagnostics

**Wrong:**
> "`kretschmann` is finite, therefore spacetime is everywhere smooth."

**Right:**
> "`kretschmann` is finite here, but I should check global structure, Cauchy horizons, and boundary conditions."

**Why:** Local smoothness doesn't guarantee global well-posedness.

---

### ❌ Don't Ignore `null` Values

**Wrong:**
> "The code failed to compute this value."

**Right:**
> "`null` signals this quantity is undefined in this context — e.g., static observers inside a horizon."

**Why:** `null` is intentional metadata encoding physical limitations.

---

### ❌ Don't Assume Observer-Independent Measurements

**Wrong:**
> "The gravitational acceleration is 0.289."

**Right:**
> "A static observer at this radius must accelerate at 0.289 to avoid free fall. A freely falling observer feels zero acceleration."

**Why:** Most observables depend on worldline and frame choice.

---

## Workflow: Analyzing a Toy Output

### Step 1: Read Metadata
- Check `toy_id`, `theory`, `spacetime`
- Note `parameters` and `units`
- Read `notes` for approximations and validity

### Step 2: Survey Sample Points
- How many points?
- What coordinate range?
- Any `null` values? (signals boundaries of validity)

### Step 3: Check Curvature Invariants
- Are they finite everywhere?
- Do they diverge? (real singularity)
- Do they scale as expected? (e.g., $\sim r^{-6}$ in Schwarzschild)

### Step 4: Examine Local Observables
- Which observer frame?
- Do quantities diverge where invariants don't? (coordinate artifact)
- Consistent with expected scaling laws?

### Step 5: Verify Causal Structure
- Null cone slopes finite?
- Horizons align with other diagnostics?
- Coordinate time well-behaved?

### Step 6: Cross-Check Global Observables
- Redshifts, distances, horizon integrals
- Consistency between points?
- Do aggregates make sense given local data?

### Step 7: Compare to Theory
- Does output match analytical predictions?
- Where do approximations break down?
- Are limitations documented in `notes` respected?

---

## Advanced Topics

### Energy Ambiguity

Many toys export multiple mass/energy definitions:

```json
"observables": {
  "mass_definitions": {
    "ADM_mass": 1.0,
    "Komar_mass": 1.0,
    "Hawking_mass": 0.95,
    "quasilocal_Misner_Sharp": 0.98
  }
}
```

**Interpretation:**
- Agreement → high symmetry (e.g., spherical + stationary)
- Disagreement → genuine ambiguity in what "energy" means
- Some definitions only work with specific assumptions

**Warning:** There is no unique "gravitational energy density" in GR.

---

### Horizon Types

Different horizon diagnostics may give different answers:

| Type | Definition | When They Exist |
|------|------------|-----------------|
| Coordinate horizon | $g_{tt} = 0$ | Depends on chart |
| Event horizon | Boundary of causal past of future null infinity | Global, teleological |
| Apparent horizon | Outermost trapped surface | Local, gauge-dependent |
| Killing horizon | Where Killing vector becomes null | Requires symmetry |

**Interpretation:** Toys typically report coordinate or Killing horizons. Event horizons require knowing entire future evolution.

---

### Semiclassical Modifications

Toys with quantum fields (Phase X-XI) may show:

```json
"local_observables": {
  "classical_stress_energy": {...},
  "quantum_stress_energy": {...},
  "backreaction_parameter": 0.15
}
```

**Interpretation:**
- Small `backreaction_parameter` → perturbative regime valid
- Order-unity values → semiclassical approximation breaking
- State-dependent stress-energy → observer/vacuum choice matters

---

### Numerical Health Indicators

Some toys include diagnostics for code validity:

```json
"notes": {
  "constraint_violation": 1.2e-10,
  "numerical_damping": "Kreiss-Oliger, order 4",
  "convergence_order": 2.01
}
```

**Interpretation:**
- Small constraint violation → reliable integration
- Documented damping → artificial dissipation present
- Convergence order → refinement behavior

---

## Cross-Toy Comparisons

The standardized schema enables direct comparison:

### Example: Energy Definition Consistency

Compare `mass_definitions` across toys 001, 006, 046, 065:
- Where do definitions agree?
- Where do they diverge?
- What causes divergence? (asymmetry, quantum effects, etc.)

### Example: Horizon Detection

Compare horizon diagnostics across toys 001, 007, 008, 029:
- Same physical horizon, different coordinates
- Do invariants stay finite?
- Do proper-time integrals agree?

---

## Summary: Core Principles

1. **Invariants vs Coordinates**
   - Scalars like `kretschmann` are physical
   - Coordinate-dependent quantities can be artifacts

2. **Observer Dependence**
   - Most measurements require specifying a worldline and frame
   - Only curvature tensors are universal

3. **`null` is Data**
   - Signals "undefined," not "failed to compute"
   - Critical for interpreting limitations

4. **Scaling Laws**
   - Verify expected behavior: $K \sim r^{-6}$, tidal $\sim r^{-3}$
   - Deviations indicate errors or new physics

5. **Global vs Local**
   - Local smoothness doesn't imply global structure
   - Check horizons, topology, boundary conditions

6. **Multiple Diagnostics**
   - Cross-check curvature, observers, causality
   - Single fields can mislead

7. **Documented Limitations**
   - Read `notes` for approximations
   - Respect validity ranges

---

[← Back to Documentation Index](../README.md)
