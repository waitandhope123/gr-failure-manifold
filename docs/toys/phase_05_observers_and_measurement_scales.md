# Phase 5 — Observers & Measurement Scales

**Toys 021–027**

---

## Toy 021 — Schwarzschild Tidal Forces and Finite-Size Observer Stress Test

This toy computes the tidal stretching and squeezing that a freely falling, finite-sized observer would *feel* in Schwarzschild spacetime of mass $M$ (with $G=c=1$). The physical setup is an extended body with proper size $\ell$ falling at a radius $r$, and the quantity of interest is the local geodesic-deviation “tidal eigenvalues” and the resulting relative tidal acceleration across the body, conceptually $a_{\rm tidal}\approx |\lambda|\,\ell$ where $\lambda$ is a curvature-driven tidal eigenvalue in an orthonormal free-fall frame.

It exists to illustrate a specific limitation of the slogan “nothing special happens at the horizon.” Geometrically, curvature invariants can remain modest at $r=2M$ for sufficiently large $M$, but operationally a real observer has nonzero size and therefore samples curvature gradients that generate differential acceleration; the toy exposes this mismatch as a stress test of point-particle intuition rather than a physical prediction. The principle being tested is the scaling $a_{\rm tidal}\sim (M/r^3)\,\ell$, which shows how “felt” effects depend not only on spacetime but also on the observer’s extent.

To interpret the JSON, treat each entry in `sample_points` as a radius $r$ with three linked pieces: `curvature_invariants` (e.g., `kretschmann`), `tidal_eigenvalues` (radial positive, tangential negative), and `tidal_accelerations` (magnitudes after multiplying by `body_size` $\ell$). The key trend is the $r^{-3}$ falloff: both eigenvalues and the reported `tidal_accelerations.max` decrease rapidly with increasing `r`, while the sign pattern (radial stretching vs tangential compression) is the qualitative “shape” information you should track; do **not** over-interpret absolute numbers as survivability thresholds, proper-time histories, or horizon drama, since the toy is a local scaling snapshot with no material model or dynamics. Conceptually, the JSON’s `tidal_accelerations` are just $|\lambda_{\rm radial}|\,\ell$ and $|\lambda_{\rm tangential}|\,\ell$ built from the eigenvalues $\lambda_{\rm radial}=2M/r^3$ and $\lambda_{\rm tangential}=-M/r^3$, while `kretschmann` provides a separate “invariant curvature” reference that can remain finite even when finite-size tidal effects are operationally important.

---

## Toy 022 — Raychaudhuri Focusing and Energy-Condition Stress Test

This toy evolves the expansion scalar $\theta(\tau)$ of a timelike geodesic congruence in general relativity under highly simplified conditions. The physical setup assumes zero vorticity and zero shear, with curvature entering only through the Ricci contraction along the flow, so the dynamics reduce to the Raychaudhuri equation $\mathrm{d}\theta/\mathrm{d}\tau = -\tfrac{1}{3}\theta^2 - R_{ab}u^a u^b$, where $\tau$ is proper time. The quantity of interest is the sign and magnitude of $\theta$, which indicates whether nearby geodesics locally converge (focusing) or diverge.

The toy exists to isolate and stress-test the conceptual role of energy conditions in focusing arguments, rather than to model a realistic spacetime. By imposing a perfect-fluid form $R_{ab}u^a u^b = 4\pi\rho(1+3w)$ with constant $\rho$ and equation-of-state parameter $w$, the code exposes how singularity theorems rely on inequalities rather than detailed dynamics. This construction deliberately illustrates a limitation: even when the strong energy condition $\rho(1+3w)\ge 0$ holds formally, the simplified analytic solution can behave counterintuitively, underscoring that focusing guarantees arise from integrated inequalities, not from trusting a particular closed-form expression as a physical prediction.

The JSON output should be read as a sequence of sampled proper times, each reporting the fixed Ricci contraction and the corresponding evolved expansion $\theta$. The boolean `focusing` flag is simply a sign test on $\theta<0$ and should be interpreted qualitatively rather than literally. What matters are trends—whether $\theta$ tends to decrease, cross zero, or grow in magnitude relative to the curvature scale set by $R_{ab}u^a u^b$—and how these relate back to the Raychaudhuri equation’s competing terms. The absolute values, oscillations, or sign reversals in $\theta$ should not be over-interpreted as physical behavior of real congruences; they only demonstrate how sensitive focusing conclusions are to assumptions encoded in the equation and its inputs.

---

## Toy 023 — Classical curvature versus a minimum length cutoff

This toy illustrates how classical spacetime curvature in a Schwarzschild geometry compares to an imposed minimum length scale. The setup is a non-rotating black hole of mass $M$ (with $G=c=1$), sampled at different radii $r$, and the quantity of interest is a curvature-based length scale derived from the Kretschmann scalar $K$. The toy defines a local curvature length as $L_\mathrm{curv}=K^{-1/4}$, which decreases as curvature grows toward the black hole interior, and compares it to a fixed cutoff length $\ell_\mathrm{min}$.

The purpose of the toy is not to predict quantum gravity effects, but to expose a conceptual pressure point in classical general relativity: the theory contains no intrinsic short-distance cutoff. By juxtaposing $L_\mathrm{curv}$ with $\ell_\mathrm{min}$, the toy demonstrates where classical GR would be expected to lose self-consistency if one assumes that no physical description should probe distances smaller than $\ell_\mathrm{min}$. This comparison acts as a stress test of classical predictivity, highlighting a limitation rather than asserting that any specific new physics occurs when $L_\mathrm{curv}\approx\ell_\mathrm{min}$.

The JSON output should be read point-by-point in radius, focusing on how the curvature length scale changes and on the boolean flag indicating whether $L_\mathrm{curv}>\ell_\mathrm{min}$. Large positive values of $L_\mathrm{curv}$ far outside the horizon indicate weak curvature and unproblematic classical behavior, while a drop of $L_\mathrm{curv}$ below $\ell_\mathrm{min}$ inside the horizon marks where the toy declares classical GR “invalid.” The precise numerical values or the sharpness of the transition should not be over-interpreted; what matters is the trend and sign of the comparison, which conceptually ties the reported numbers back to the defining relation $L_\mathrm{curv}=K^{-1/4}$ and the chosen cutoff $\ell_\mathrm{min}$.

---

## Toy 024 — Horizon Crossing Timescales

This toy illustrates how different notions of time describe the same infalling motion toward a black hole horizon in different ways. The physical setup is radial free fall from rest at infinity in Schwarzschild spacetime, with the radius $r$ decreasing toward the horizon at $r=2M$, where $M$ is the black hole mass. The quantity of interest is how elapsed proper time $\tau$ along the infaller’s worldline compares to the Schwarzschild coordinate time $t$ used by a distant observer, with the contrast anchored by relations like $dr/d\tau=-\sqrt{2M/r}$.

The toy exists to expose an observer-dependent limitation rather than to make a physical prediction about horizons. In Schwarzschild coordinates, the mapping between $t$ and $r$ becomes singular at the horizon, so the same trajectory that reaches $r=2M$ in finite proper time appears to take an infinite amount of coordinate time, as reflected by $dt/dr\propto(1-2M/r)^{-1}$. This is a stress test of coordinate descriptions: it demonstrates how a perfectly regular physical process can look pathological when expressed in a poorly adapted coordinate system, without invoking new dynamics or exotic physics.

The JSON output should be read as a numerical probe of these contrasting behaviors. The per-radius entries show that $d\tau/dr$ remains finite and slowly varying as $r$ approaches $2M$, while $dt/dr$ grows rapidly in magnitude, signaling the coordinate-time divergence; the integrated totals summarize this by giving a finite total proper time and a coordinate-time value whose magnitude is dominated by near-horizon contributions. The sign and precise numerical value of the total coordinate time should not be over-interpreted, as they depend on integration conventions and truncation near the horizon, but the trend—finite versus divergent behavior—connects directly back to the time–radius relations encoded in the equations.

---

## Toy 025 — Gravitational Redshift vs Local Acceleration

This toy illustrates how two commonly associated notions of “gravitational strength” separate in curved spacetime: gravitational redshift and the proper acceleration required to hover at fixed radius. The physical setup is a Schwarzschild spacetime with mass $M$, using static observers at radius $r$ who exchange light signals with a reference observer at radius $r_{\mathrm{obs}}$. The quantity of interest is the gravitational redshift between these observers, defined by the lapse function $f(r)=1-2M/r$ through $z=\sqrt{f(r_{\mathrm{obs}})/f(r_{\mathrm{emit}})}-1$, alongside the proper acceleration needed to remain static.

The toy exists to expose a conceptual failure mode: the intuition that gravitational redshift directly measures the local “force of gravity.” Proper acceleration is a local quantity that depends on how hard an observer must fire rockets to hover, while redshift is a global comparison between clocks at different radii. In this model the proper acceleration $a=M/(r^{2}\sqrt{f(r)})$ diverges as $r$ approaches the horizon, even though redshift between nearby radii can remain finite, demonstrating that these two notions probe different aspects of the geometry rather than providing interchangeable measures of gravity.

The JSON output should be read as a collection of sample radii with associated local and relational observables. The `gravitational_redshift_to_r_obs` values show how clock rates compare to the observer at $r_{\mathrm{obs}}$, changing sign and growing in magnitude depending on whether the emitter lies deeper or higher in the potential, while `proper_acceleration_static` increases sharply as the horizon is approached. What matters are the contrasting trends—finite redshift versus rapidly growing acceleration—not the precise numerical values, which depend on chosen parameters and units. The curvature scalars and metric factors provide context but should not be over-interpreted as predictions; they simply connect the reported numbers back to the defining expressions for $f(r)$, $z$, and $a$ without implying any direct physical equivalence between them.

---

## Toy 026 — Equivalence principle limits for extended bodies

This toy illustrates free fall in Schwarzschild spacetime while contrasting an ideal point particle with a finite-sized body. The physical setup is a non-rotating black hole of mass $M$, with a body of proper size $\ell$ dropped radially at various Schwarzschild radii $r$. The quantity of interest is the relative acceleration across the body induced by spacetime curvature, estimated by the tidal scaling $\Delta a \sim (M/r^3)\,\ell$, while the center-of-mass motion remains that of geodesic free fall.

The toy exists to expose a limitation in the operational meaning of the equivalence principle. Locally, a point particle in free fall has zero proper acceleration and cannot distinguish gravity from inertial motion, but an extended body samples curvature gradients across its size. This creates a stress test for the statement “gravity can always be transformed away,” showing that the principle applies only in the limit $\ell \to 0$ rather than as a literal claim about finite objects, even though the underlying spacetime remains a valid solution of general relativity.

The JSON results should be read as radius-by-radius diagnostics rather than predictions. The field `point_particle_proper_acceleration` is identically zero, while `extended_body_relative_acceleration` increases rapidly as $r$ decreases, tracking the listed `tidal_gradient` and reflecting the $1/r^3$ dependence; the rising Kretschmann scalar provides a curvature context for this trend. The sign and magnitude of these values indicate growing differential stretching near the horizon, but they should not be over-interpreted as forces on rigid objects or signals of equivalence-principle violation, only as numerical illustrations of how the tidal estimate connects the curvature invariants to the relative-acceleration formula.

---

## Toy 027 — Null Raychaudhuri Equation and NEC Diagnostic

This toy illustrates the evolution of the expansion scalar $\theta$ for a bundle of null geodesics in general relativity, with twist and shear deliberately set to zero so that only curvature sourced by matter enters. The physical setup is a generic null congruence parametrized by an affine parameter $\lambda$, and the quantity of interest is whether the congruence focuses or defocuses as it propagates. The behavior is governed by the null Raychaudhuri equation $d\theta/d\lambda = -\tfrac{1}{2}\theta^2 - R_{ab}k^a k^b$, where $\theta$ measures local cross-sectional expansion and $R_{ab}k^a k^b$ encodes curvature along the null direction $k^a$.

The toy exists to expose a conceptual pressure point in how energy conditions control geometric behavior, rather than to make any physical prediction. By fixing shear to zero and treating $T_{ab}k^a k^b$ as a constant input, it stress-tests the idea that null focusing is “guaranteed” when the null energy condition (NEC) holds, using $R_{ab}k^a k^b = 8\pi T_{ab}k^a k^b$ as the only source term. Any unexpected sign changes, divergences, or pathologies in $\theta(\lambda)$ should be read as illustrating limitations of simplified analytic treatments or numerical branches, not as violations or confirmations of real spacetime dynamics.

The JSON output should be read pointwise along the affine parameter values listed under `sample_points`. The key trends are the sign and reality of `expansion_theta`, the constant value of `ricci_contraction_Rab_kk`, and the boolean flags indicating whether focusing ($\theta<0$) is detected and whether $\theta$ is real at that point. Null or missing values of $\theta$ indicate branch or domain issues in the closed-form solution and should not be over-interpreted as physical singularities. Conceptually, the reported numbers tie back to the Raychaudhuri equation by showing how a fixed positive $R_{ab}k^a k^b$ term competes with the nonlinear $-\tfrac{1}{2}\theta^2$ term, while the JSON structure itself is only a diagnostic snapshot of this competition, not a claim about actual spacetime evolution.

---

