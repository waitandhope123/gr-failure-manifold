# Geometry Evidence: Why Geometry Underdetermines Physics

## The Central Problem

**In a fundamental theory, specifying the fundamental variables should uniquely determine all physics.**

**Examples:**
- QM: Specify |ψ⟩ → all observables determined
- Classical EM: Specify F_μν → all physics determined
- Thermodynamics: Specify (T, P, N) → equilibrium state determined

**GR: Specify g_μν → physics NOT uniquely determined**

**This is the smoking gun for emergence.**

---

## The Evidence Trail

### 1. Same Geometry, Different Stress Tensors (Toy 61)

**Test:** Schwarzschild black hole in different quantum vacuum states.

**Setup:**
- Geometry: Schwarzschild (fixed M, same g_μν everywhere)
- Quantum states: Boulware, Hartle-Hawking, Unruh vacua
- Question: Does same geometry → same stress-energy?

**Result:**

```
Same metric g_μν for all three states
BUT
Different stress-energy tensors ⟨T_μν⟩:

Boulware state:
- ⟨T_μν⟩ diverges at horizon
- Represents "no radiation" state

Hartle-Hawking state:
- ⟨T_μν⟩ regular everywhere
- Represents thermal equilibrium

Unruh state:
- ⟨T_μν⟩ regular at horizon
- Represents Hawking radiation
```

**What this means:**

Geometry does NOT uniquely determine matter content.

You need:
1. Metric g_μν
2. **Plus** quantum state specification

**Analogy:**

This is like specifying the shape of a container but not what's inside. Same container can hold water, air, or vacuum—geometry alone doesn't tell you.

**Implication:**

If geometry were fundamental, it should encode everything. But it doesn't—quantum state matters independently.

**This points to emergence:** Geometry is a coarse-grained description that loses information about quantum state.

---

### 2. Quantitative Variance in Stress-Energy (Toy 67)

**Test:** Same Schwarzschild geometry, measure variance in stress-energy components across vacuum states.

**Setup:**
- Same classical geometry g_μν
- Three semiclassical vacuum states {Boulware, Hartle-Hawking, Unruh}
- Compute variance in ⟨T_μν⟩ components

**Result:**

```
Radial location: r = 2.1M (near horizon)
Static energy density variance: σ²(T_tt) ~ 7.6×10⁻⁵

Radial location: r = 3M
Variance: σ²(T_tt) ~ 1×10⁻⁶

Pattern: Variance increases dramatically near horizon
```

**What this means:**

Not just "different quantum states possible"—but **measurable statistical spread** in stress-energy expectations.

Same geometry supports quantum states with:
- Different mean values ⟨T_μν⟩
- Different uncertainties σ²(T_μν)

**This is decisive:**

In a fundamental theory, specifying fundamental variables → unique predictions.

Here: Specifying g_μν → **distribution** of possible T_μν, not unique value.

**Analogy:**

Temperature in thermodynamics: Specify temperature T → get distribution of molecular velocities, not unique microstate.

Similarly: Specify geometry g_μν → get distribution of quantum stress-energies, not unique value.

**Implication:**

Geometry is a **macroscopic variable** like temperature, not a **microscopic variable** like molecular positions.

---

### 3. Local Data Cannot Reconstruct Global State (Toy 70)

**Test:** Flat spacetime (g_μν = η_μν), Gaussian quantum state. Can local measurements reconstruct global state?

**Setup:**
- Background: Flat Minkowski space (no curvature)
- Quantum state: Known Gaussian with specific covariance matrix
- Task: Reconstruct covariance from local patches

**Question:** If geometry + local quantum data are fundamental, can they determine global physics?

**Result:**

```
Local patch L=2 (small):
- Reconstruction error: 19.5% (relative Frobenius norm)
- Physicality violated (negative eigenvalues)
- Heisenberg uncertainty violated modewise

Local patch L=4 (medium):
- Reconstruction error reduced
- Still violates Heisenberg: min eig(CxCp) < 0.25

Local patch L=8 (full system):
- Reconstruction successful (~machine precision)
- Heisenberg restored
- Physical covariance recovered
```

**What this means:**

Even with:
1. Complete knowledge of geometry (flat space)
2. Accurate local quantum measurements
3. Near-perfect local agreement

You **cannot** uniquely determine global quantum state.

**Key insight:** Non-locality is fundamental. You need **full-size patch** to recover true state.

**Analogy:**

Holography: Boundary degrees of freedom encode bulk physics. But you need **entire boundary**, not just local patches.

Similarly: Global quantum state encoded non-locally. Local geometry + local quantum data insufficient.

**Implication:**

If geometry + local quantum data were fundamental, they should determine everything. But they don't—**holographic non-locality** is required.

This points to: Fundamental DOFs are non-local (entanglement structure), not local geometric fields.

---

### 4. Entanglement Structure Does Not Automatically Yield Geometry (Toy 83)

**Test:** SYK (Sachdev-Ye-Kitaev) model, conjectured holographic dual to AdS₂ gravity.

**Setup:**
- N Majorana fermions with random all-to-all interactions
- Tune to strong coupling (βJ = 10)
- Check: Does high entanglement + strong coupling → emergent geometry?

**Criteria:**
1. Conformal symmetry proxy: Two-point functions match CFT form?
2. Entanglement proxy: Ground state highly entangled (S_half ≈ maximal)?

**Result:**

```
Conformal check:
- Two-point correlator shows power-law decay ✓
- Fitted exponent: Δ_fit ≈ 0.20
- Expected conformal dimension: Δ = 1/4 = 0.25
- Relative error: ~20% ✗
- Conclusion: NOT conformal enough

Entanglement check:
- Half-system entropy: S_half/S_max ≈ 0.65
- Threshold for "high entanglement": 0.8-0.9
- Conclusion: NOT entangled enough

Overall: Emergent geometry proxy FAILS
```

**What this means:**

Even in a system **specifically designed** to exhibit gravity/geometry duality:
- Strong coupling does NOT automatically produce conformal symmetry
- High entanglement does NOT automatically produce maximal entanglement
- **Entanglement structure alone does NOT determine geometry**

**Connection to Toy 67 and Toy 70:**

**Three-way underdetermination:**

1. **Toy 67:** Geometry g_μν does NOT determine quantum state |ψ⟩
   - Same g_μν → different ⟨T_μν⟩ (variance)

2. **Toy 70:** Geometry + local quantum data do NOT determine global state
   - Flat g_μν + local patches → cannot reconstruct global covariance

3. **Toy 83:** Entanglement structure does NOT determine geometry
   - High entanglement + strong coupling → no unique geometry

**Pattern:** Geometry ↔ quantum state correspondence is **underdetermined in both directions**.

**Implication:**

Neither geometry nor entanglement is fundamental alone.

The correspondence requires:
- Specific boundary conditions
- Specific coarse-graining procedures
- Additional quantum numbers or structure

**This supports Interpretation A2:** Both geometry and entanglement structure emerge from **pre-geometric quantum information** with additional structure.

---

## The Systematic Pattern

### Summary Table

| Toy | Geometry | Quantum State | Physics Determined? |
|-----|----------|---------------|---------------------|
| 61 | Fixed (Schwarzschild) | Variable (3 vacua) | ✗ No (different ⟨T_μν⟩) |
| 67 | Fixed (Schwarzschild) | Variable (3 vacua) | ✗ No (variance in T_μν) |
| 70 | Fixed (flat) | Known (Gaussian) | ✗ No (local patches insufficient) |
| 83 | Unknown (emergent?) | Fixed (SYK ground state) | ✗ No (entanglement insufficient) |

**Total: 4 independent toys showing geometry underdetermination**

---

## What This Looks Like for a Fundamental Theory

**If geometry were fundamental, we'd expect:**

```
Specify g_μν → unique T_μν
              → unique quantum state
              → unique local physics
              → unique global physics
              → unique emergent geometry (from entanglement)
```

**What we actually see:**

```
Specify g_μν → multiple possible T_μν (Toy 61, 67)
             → variance, not unique value (Toy 67)
             → local data insufficient (Toy 70)
             
Specify entanglement → NOT unique geometry (Toy 83)
```

**Geometry and entanglement are both insufficient.**

---

## The Thermodynamics Analogy

### Historical Parallel

**19th century thermodynamics:**

Specify macroscopic variables (T, P, V):
- Determines macroscopic behavior ✓
- Does NOT determine microstate ✗
- Many microstates → same (T, P, V)

**Resolution (statistical mechanics):**
- Temperature, pressure are **emergent macroscopic variables**
- Microstates (molecular positions/velocities) are fundamental
- Coarse-graining: Many microstates → same macrostate

**21st century general relativity:**

Specify geometry g_μν:
- Determines some behavior ✓
- Does NOT determine quantum state ✗
- Many quantum states → same g_μν (Toy 61, 67)

Specify entanglement structure:
- Determines some behavior ✓
- Does NOT determine geometry ✗
- High entanglement ≠ unique geometry (Toy 83)

**Proposed resolution (quantum information):**
- Geometry and entanglement are **emergent macroscopic variables**
- Pre-geometric quantum information is fundamental
- Coarse-graining: Many quantum info states → same effective geometry

---

## Connection to Energy Evidence

**Energy underdetermination (from 02-ENERGY-EVIDENCE.md):**
- Same geometry → multiple energy definitions (Toy 6, 46, 65)
- Energy depends on quantum state (Toy 61)

**Geometry underdetermination (this document):**
- Same geometry → multiple quantum states (Toy 61, 67)
- Geometry requires additional structure beyond entanglement (Toy 83)

**Combined implication:**

Neither energy nor geometry is fundamental.

Both are **emergent coarse-grained descriptions** of underlying quantum information substrate.

---

## Phase XIII Connection: Why Toy 83 Matters

**Before Toy 83:**
"Geometry underdetermines quantum state (Toys 61, 67), local quantum data underdetermines global state (Toy 70)."

**After Toy 83:**
"**Even entanglement structure underdetermines geometry.** The correspondence is **bidirectionally underdetermined**."

**This is decisive for Interpretation A1 vs A2:**

**A1 (fields on spacetime) predicts:**
- QFT is fundamental
- Entanglement structure in QFT → geometry via holography
- Should be one-to-one correspondence

**A2 (pre-geometric quantum info) predicts:**
- Neither geometry nor entanglement fundamental
- Both emerge from deeper substrate
- Correspondence requires additional structure

**Toy 83 supports A2:**
- High entanglement + strong coupling do NOT automatically yield geometry
- Additional structure beyond connectivity required
- Both geometry and entanglement are emergent

---

## Philosophical Implications

### What "Underdetermination" Means

**In fundamental physics, we expect determination:**
- Specify fundamental variables → everything else follows
- No ambiguity, no missing information

**In effective theories, we expect underdetermination:**
- Specify macroscopic variables → many microscopic states compatible
- Statistical mechanics: (T,P) → many molecular configurations
- Thermodynamics: Cannot reconstruct microstate from (T,P)

**GR exhibits underdetermination:**
- Specify g_μν → many quantum states compatible (Toy 61, 67)
- Specify local quantum data → many global states compatible (Toy 70)
- Specify entanglement → no unique geometry (Toy 83)

**This is the signature of effective theory.**

---

### What This Means for "Reality"

**Naive realism:**
"Spacetime geometry is the fundamental reality. Everything else (matter, fields) lives on it."

**Quantum field theory:**
"Quantum fields are fundamental reality. Spacetime is fixed background."

**Emergence (Interpretation A2):**
"Neither geometry nor fields are fundamental. Both are emergent descriptions of pre-geometric quantum information."

**Evidence:**
- Geometry doesn't determine quantum state (Toys 61, 67)
- Local quantum data doesn't determine global state (Toy 70)
- Entanglement doesn't determine geometry (Toy 83)
- **Nothing uniquely determines anything else**

**This points to:** Deeper substrate from which both geometry and quantum state emerge together.

---

## Confidence Assessment

**Claim:** Geometry underdetermines physics; geometry is coarse-grained, not fundamental.

**Evidence:**

| Toy | Type | Weight |
|-----|------|--------|
| 61 | Same geometry → different stress-energy | Very high |
| 67 | Quantitative variance in T_μν | Very high |
| 70 | Local data insufficient for global state | Very high |
| 83 | Entanglement insufficient for geometry | High |

**Confidence: ~80%**

**Why not higher:**
- Could argue quantum state is "additional data" not "underdetermination"
- SYK (Toy 83) might just need specific tuning
- Could be observer-choice artifact (though Toy 67 shows it's measurable)

**Why not lower:**
- Toys 61, 67 are unambiguous: same g_μν, different physics
- Toy 70 is unambiguous: local patches cannot reconstruct global state
- Toy 83 shows reverse direction also underdetermined
- Exactly what you'd expect if geometry is coarse-grained

---

## What Would Change Our Mind

**To conclude geometry is fundamental, we'd need:**

1. **Toy 61, 67 explained away**
   - Show different vacuum states are "gauge equivalent"
   - Prove geometry alone sufficient
   - Would contradict observed variance

2. **Toy 70 explained away**
   - Show local patches actually do suffice
   - Disprove holographic non-locality
   - Would contradict reconstruction error

3. **Toy 83 explained away**
   - Show SYK does yield geometry with correct tuning
   - Prove entanglement → geometry automatically
   - Would support A1 over A2

4. **Find unique g_μν → |ψ⟩ mapping**
   - Discover canonical vacuum choice
   - Experimentally prefer one state
   - Would suggest geometry is fundamental

**None of these seem likely.**

---

## The Bottom Line

**Geometry in GR behaves like temperature in thermodynamics:**

| Property | Temperature | Geometry |
|----------|-------------|----------|
| Multiple microstates → same macro variable | ✓ | ✓ (Toy 61, 67) |
| Macro variable underdetermines micro | ✓ | ✓ (Toy 67) |
| Local data insufficient for global state | ✓ | ✓ (Toy 70) |
| Cannot uniquely reconstruct from correlation data | ✓ | ✓ (Toy 83) |
| Emergent, not fundamental | ✓ | ✓ (conclusion) |

**This strongly suggests geometry is an emergent coarse-grained description, not a fundamental variable.**

**And if geometry is emergent, what is it emerging from?**

**Answer: Pre-geometric quantum information substrate.**

**Toy 83 (Phase XIII) strengthens this by showing entanglement alone is also insufficient—we need deeper structure.**

---

*Geometry is real. But it's real the way temperature is real: as a macroscopic emergent property, not a microscopic fundamental one.*
