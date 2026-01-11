# GR Diagnostic Toy Commands

This document lists the commands to run every toy in the GR Toy Lab.
All toys are executed directly using Python.

---

## Toys 001–010 — Geometry, Equivalence, and Orbits

### Toy 001 — Schwarzschild spacetime
    python toy_001_schwarzschild.py

Custom example:
    python toy_001_schwarzschild.py \
      --M 1 \
      --r 2.5,3,4,6,10 \
      --redshift_emitters 3,6,10 \
      --round_trip 10:6

---

### Toy 002 — Newtonian point mass
    python toy_002_newtonian_point_mass.py

With heuristic light-time estimate:
    python toy_002_newtonian_point_mass.py \
      --include_heuristic_light_time

---

### Toy 003 — Linearized gravitational waves (TT gauge)
    python toy_003_linearized_gw_tt.py

Higher-frequency example:
    python toy_003_linearized_gw_tt.py \
      --A_plus 1e-4 \
      --omega 10 \
      --t 0,0.05,0.1,0.15,0.2

---

### Toy 004 — Flat FLRW cosmology
    python toy_004_flrw_flat.py --model matter

de Sitter example (event horizon):
    python toy_004_flrw_flat.py \
      --model desitter \
      --H0 0.2 \
      --t 1,2,5,10,20 \
      --t_obs 20 \
      --emit_times 1,2,5,10

---

### Toy 005 — Rindler equivalence
    python toy_005_rindler_equivalence.py

---

### Toy 006 — Quasilocal mass
Schwarzschild:
    python toy_006_quasilocal_mass.py \
      --mode schwarzschild \
      --M 1 \
      --r 3,4,6,10,20

FLRW:
    python toy_006_quasilocal_mass.py \
      --mode flrw \
      --flrw_model matter \
      --t 0.5,1,2,5,10 \
      --rcom 0,0.5,1,2

---

### Toy 007 — Schwarzschild (Eddington–Finkelstein)
    python toy_007_schwarzschild_ef_coordinates.py

Near-horizon sampling:
    python toy_007_schwarzschild_ef_coordinates.py \
      --r 1.9,1.99,2,2.01,2.1,3,10

---

### Toy 008 — Painlevé–Gullstrand slicing
    python toy_008_painleve_gullstrand.py

Near-horizon sampling:
    python toy_008_painleve_gullstrand.py \
      --r 1.9,1.99,2,2.01,2.1,3,10

---

### Toy 009 — Radial infall geodesics
    python toy_009_radial_infall_geodesic.py \
      --M 1 \
      --r0 10

Zoom near the horizon:
    python toy_009_radial_infall_geodesic.py \
      --r 2.1,2.01,2.001,2.0001,2.00001

---

### Toy 010 — Photon sphere and ISCO
    python toy_010_orbits_photonsphere_isco.py

---

## Toys 011–020 — Rotation, Energy, and Consistency Limits

### Toy 011 — Thin-shell backreaction
    python toy_011_thin_shell_backreaction.py

Parameter sweep:
    python toy_011_thin_shell_backreaction.py \
      --M_in 0 \
      --M_out 1 \
      --m_shell 0.8 \
      --R 0.6,0.8,1,1.5,2,3,6,10

---

### Toy 012 — Kerr ergosphere frame dragging
    python toy_012_kerr_ergosphere_framedrag.py

High-spin example:
    python toy_012_kerr_ergosphere_framedrag.py \
      --a 0.99 \
      --r 1.1,1.2,1.3,1.5,2,3,6,10 \
      --theta_deg 0,30,60,90

---

### Toy 013 — Kerr ISCO efficiency
    python toy_013_kerr_isco_efficiency.py

Spin sweep:
    python toy_013_kerr_isco_efficiency.py \
      --a_values -0.999,-0.99,-0.9,-0.5,0,0.5,0.9,0.99,0.999

---

### Toy 014 — Kerr horizon mechanics
    python toy_014_kerr_horizon_mechanics.py

Including super-extremal cases:
    python toy_014_kerr_horizon_mechanics.py \
      --M 1 \
      --a_values -1.5,-1.0,-0.99,-0.5,0,0.5,0.99,1.0,1.5

---

### Toy 015 — Kerr superradiance window
    python toy_015_kerr_superradiance_window.py

High-spin, multi-mode example:
    python toy_015_kerr_superradiance_window.py \
      --a 0.99 \
      --r 1.1,1.2,1.3,1.5,2,3,6 \
      --theta_deg 0,60,90 \
      --m 1,2,3 \
      --omega 0.01,0.05,0.1,0.2,0.3

---

### Toy 016 — Gödel chronology violation
    python toy_016_godel_ctc_chronology.py

Radial sweep:
    python toy_016_godel_ctc_chronology.py \
      --Omega 1 \
      --r 0,0.5,1.0,1.2,1.5,2.0,3.0

---

### Toy 017 — Alcubierre warp proxies
    python toy_017_alcubierre_warp_proxies.py

Superluminal proxy example:
    python toy_017_alcubierre_warp_proxies.py \
      --v 1.5 \
      --R 2 \
      --sigma 3 \
      --t0 0 \
      --x -8,-6,-4,-3,-2,-1,0,1,2,3,4,6,8

---

### Toy 018 — Traversable wormhole NEC
    python toy_018_traversable_wormhole_nec.py

Radial scan:
    python toy_018_traversable_wormhole_nec.py \
      --r0 2 \
      --r 2,2.1,2.2,2.5,3,5,10

---

### Toy 019 — Raychaudhuri focusing
Vacuum:
    python toy_019_raychaudhuri_focusing.py \
      --model vacuum \
      --theta0 -0.2

Matter:
    python toy_019_raychaudhuri_focusing.py \
      --model matter \
      --theta0 -0.2 \
      --R0 0.2

Exotic:
    python toy_019_raychaudhuri_focusing.py \
      --model exotic \
      --theta0 -0.2 \
      --R0 0.2

Piecewise:
    python toy_019_raychaudhuri_focusing.py \
      --model custom_piecewise \
      --theta0 -0.2 \
      --custom_breaks 10,20 \
      --custom_values -0.1,0.0,0.2

---

### Toy 020 — Reissner–Nordström extremality
    python toy_020_reissner_nordstrom_extremality.py

Near-extremal:
    python toy_020_reissner_nordstrom_extremality.py \
      --Q 0.99 \
      --r 0.9,1.0,1.1,1.2,2,5,10

Naked regime:
    python toy_020_reissner_nordstrom_extremality.py \
      --Q 1.2 \
      --r 0.6,0.8,1,2,5,10

---

## Toys 021–030 — Observer Limits and Global Extensions

### Toy 021 — Tidal survivability
    python toy_021_tidal_forces_observer_survival.py

Vary black hole mass and body size:
    python toy_021_tidal_forces_observer_survival.py \
      --M 10 \
      --body_size 1 \
      --r 20,10,6,4,3,2.5

Large black hole comparison:
    python toy_021_tidal_forces_observer_survival.py \
      --M 1000 \
      --body_size 1 \
      --r 2000,1000,500,200,100

---

### Toy 022 — Timelike Raychaudhuri
    python toy_022_raychaudhuri_focusing.py

With positive energy density:
    python toy_022_raychaudhuri_focusing.py \
      --theta0 -0.1 \
      --rho 0.01 \
      --t 0,1,2,3,4,5

With energy condition violation:
    python toy_022_raychaudhuri_focusing.py \
      --theta0 -0.1 \
      --rho -0.01 \
      --t 0,1,2,3,4,5

---

### Toy 023 — Curvature vs minimum length
    python toy_023_quantum_cutoff_proxy.py

Minimum length cutoff:
    python toy_023_quantum_cutoff_proxy.py \
      --l_min 0.1 \
      --r 10,6,4,3,2.5,2

Stellar vs supermassive comparison:
    python toy_023_quantum_cutoff_proxy.py \
      --M 1 \
      --l_min 1 \
      --r 10,6,4,3,2

    python toy_023_quantum_cutoff_proxy.py \
      --M 1000 \
      --l_min 1 \
      --r 2000,1000,500,200,100

---

### Toy 024 — Horizon crossing timescales
    python toy_024_horizon_crossing_timescales.py

Near-horizon comparison:
    python toy_024_horizon_crossing_timescales.py \
      --M 1 \
      --r 10,6,4,3,2.5,2.1,2.01,2.001

Large black hole:
    python toy_024_horizon_crossing_timescales.py \
      --M 1000 \
      --r 2000,1000,500,200,100

---

### Toy 025 — Redshift vs acceleration
    python toy_025_redshift_vs_acceleration.py

Emitters near the horizon:
    python toy_025_redshift_vs_acceleration.py \
      --r_emit 10,6,4,3,2.5,2.1,2.01

---

### Toy 026 — Extended-body equivalence principle breakdown
    python toy_026_equivalence_principle_breakdown_extended_bodies.py

---

### Toy 027 — Null Raychaudhuri
    python toy_027_null_raychaudhuri_nec.py

---

### Toy 028 — Proper time to singularity
    python toy_028_singularity_approach_timescales.py

---

### Toy 029 — Kruskal extension
    python toy_029_kruskal_extension_horizon_regular.py

---

### Toy 030 — Horizon area scaling
    python toy_030_horizon_area_vs_mass_scaling.py

---

## Toys 031–040 — Determinism and Backreaction

### Toy 031 — Global hyperbolicity
    python toy_031_global_hyperbolicity.py

---

### Toy 032 — Mass inflation
    python toy_032_mass_inflation.py

---

### Toy 033 — Backreaction proxy
    python toy_033_backreaction_proxy.py

---

### Toy 034 — Self-force proxy
    python toy_034_self_force_proxy.py

---

### Toy 035 — Linearization breakdown
    python toy_035_linearized_breakdown.py

---

### Toy 036 — Energy conditions
    python toy_036_energy_conditions.py

---

### Toy 037 — UV classicality
    python toy_037_uv_classicality.py

---

### Toy 038 — Semiclassical backreaction
    python toy_038_semiclassical_backreaction.py

---

### Toy 039 — Cosmological averaging backreaction
    python toy_039_averaging_backreaction.py

---

### Toy 040 — Constraint propagation
    python toy_040_constraint_propagation.py

---

## Toys 041–050 — Verification and Cross-Checks

### Toy 041 — Coordinate invariance
    python toy_041_coordinate_invariance.py

---

### Toy 042 — Numerical stability limits
    python toy_042_numerical_stability_limits.py

---

### Toy 043 — Foliation dependence
    python toy_043_foliation_time.py

---

### Toy 044 — Finite-size observers
    python toy_044_finite_size_observer.py

---

### Toy 045 — Constraint drift
    python toy_045_constraint_drift.py

---

### Toy 046 — Energy comparator
    python toy_046_energy_comparator.py

---

### Toy 047 — Observer-dependent horizons
    python toy_047_observer_horizon.py

---

### Toy 048 — Backreaction threshold
    python toy_048_backreaction_threshold.py

---

### Toy 049 — Broken model
    python toy_049_broken_model.py

---

### Toy 050 — Cross-toy comparator
    python toy_050_compare.py

---

## Toys 051–060 — Boundaries and Relational Physics

### Toy 051 — ADM initial data underdetermination
    python toy_051_adm_initial_data_underdetermination.py

---

### Toy 052 — Gauge mode growth vs physical modes
    python toy_052_gauge_mode_growth_vs_physical_modes.py

---

### Toy 053 — Anisotropic stress (TOV)
    python toy_053_anisotropic_stress_tov.py

---

### Toy 054 — Imperfect fluid entropy
    python toy_054_imperfect_fluid_entropy.py

---

### Toy 055 — Boxed scalar field boundaries
    python toy_055_boxed_boundaries_scalar_schwarzschild.py

---

### Toy 056 — Relational radar distance
    python toy_056_relational_radar_distance.py

---

### Toy 057 — Gravitational-wave memory
    python toy_057_gw_memory_extended_detector.py

---

### Toy 058 — Thin-shell Israel junctions
    python toy_058_thin_shell_israel_junction.py

---

### Toy 059 — Shell crossing
    python toy_059_shell_crossing_multistream.py

---

### Toy 060 — Scalar vs GR comparator
    python toy_060_scalar_vs_gr_comparator.py

---

## Toys 061–064 — Thickened Failure Manifold

### Toy 061 — State-dependent Polyakov stress
    python toy_061_state_dependent_polyakov.py

---

### Toy 062 — Stochastic backreaction
    python toy_062_stochastic_backreaction.py

---

### Toy 063 — Bianchi I anisotropy
    python toy_063_bianchiI_anisotropy.py

---

### Toy 064 — Inhomogeneous shock formation
    python toy_064_inhomogeneous_shock.py
