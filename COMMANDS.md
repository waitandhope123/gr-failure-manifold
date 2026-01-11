# GR Diagnostic Toy Commands

This file lists the commands to run every toy in the GR Toy Lab.
All toys are executed directly with Python. No executable permissions
or `chmod` steps are required.

---

## Toys 001–010 — Geometry, Equivalence, and Orbits

python toy_001_schwarzschild.py
python toy_001_schwarzschild.py --M 1 --r 2.5,3,4,6,10 --redshift_emitters 3,6,10 --round_trip 10:6

python toy_002_newtonian_point_mass.py
python toy_002_newtonian_point_mass.py --include_heuristic_light_time

python toy_003_linearized_gw_tt.py
python toy_003_linearized_gw_tt.py --A_plus 1e-4 --omega 10 --t 0,0.05,0.1,0.15,0.2

python toy_004_flrw_flat.py --model matter
python toy_004_flrw_flat.py --model desitter --H0 0.2 --t 1,2,5,10,20 --t_obs 20 --emit_times 1,2,5,10

python toy_005_rindler_equivalence.py

python toy_006_quasilocal_mass.py --mode schwarzschild --M 1 --r 3,4,6,10,20
python toy_006_quasilocal_mass.py --mode flrw --flrw_model matter --t 0.5,1,2,5,10 --rcom 0,0.5,1,2

python toy_007_schwarzschild_ef_coordinates.py
python toy_007_schwarzschild_ef_coordinates.py --r 1.9,1.99,2,2.01,2.1,3,10

python toy_008_painleve_gullstrand.py
python toy_008_painleve_gullstrand.py --r 1.9,1.99,2,2.01,2.1,3,10

python toy_009_radial_infall_geodesic.py --M 1 --r0 10
python toy_009_radial_infall_geodesic.py --r 2.1,2.01,2.001,2.0001,2.00001

python toy_010_orbits_photonsphere_isco.py

---

## Toys 011–020 — Rotation, Energy, and Consistency Limits

python toy_011_thin_shell_backreaction.py
python toy_011_thin_shell_backreaction.py --M_in 0 --M_out 1 --m_shell 0.8 --R 0.6,0.8,1,1.5,2,3,6,10

python toy_012_kerr_ergosphere_framedrag.py
python toy_012_kerr_ergosphere_framedrag.py --a 0.99 --r 1.1,1.2,1.3,1.5,2,3,6,10 --theta_deg 0,30,60,90

python toy_013_kerr_isco_efficiency.py
python toy_013_kerr_isco_efficiency.py --a_values -0.999,-0.99,-0.9,-0.5,0,0.5,0.9,0.99,0.999

python toy_014_kerr_horizon_mechanics.py
python toy_014_kerr_horizon_mechanics.py --M 1 --a_values -1.5,-1.0,-0.99,-0.5,0,0.5,0.99,1.0,1.5

python toy_015_kerr_superradiance_window.py
python toy_015_kerr_superradiance_window.py --a 0.99 --r 1.1,1.2,1.3,1.5,2,3,6 --theta_deg 0,60,90 --m 1,2,3 --omega 0.01,0.05,0.1,0.2,0.3

python toy_016_godel_ctc_chronology.py
python toy_016_godel_ctc_chronology.py --Omega 1 --r 0,0.5,1.0,1.2,1.5,2.0,3.0

python toy_017_alcubierre_warp_proxies.py
python toy_017_alcubierre_warp_proxies.py --v 1.5 --R 2 --sigma 3 --t0 0 --x -8,-6,-4,-3,-2,-1,0,1,2,3,4,6,8

python toy_018_traversable_wormhole_nec.py
python toy_018_traversable_wormhole_nec.py --r0 2 --r 2,2.1,2.2,2.5,3,5,10

python toy_019_raychaudhuri_focusing.py --model vacuum --theta0 -0.2
python toy_019_raychaudhuri_focusing.py --model matter --theta0 -0.2 --R0 0.2
python toy_019_raychaudhuri_focusing.py --model exotic --theta0 -0.2 --R0 0.2
python toy_019_raychaudhuri_focusing.py --model custom_piecewise --theta0 -0.2 --custom_breaks 10,20 --custom_values -0.1,0.0,0.2

python toy_020_reissner_nordstrom_extremality.py
python toy_020_reissner_nordstrom_extremality.py --Q 0.99 --r 0.9,1.0,1.1,1.2,2,5,10
python toy_020_reissner_nordstrom_extremality.py --Q 1.2 --r 0.6,0.8,1,2,5,10

---

## Toys 021–030 — Observer Limits and Global Extensions

python toy_021_tidal_forces_observer_survival.py
python toy_021_tidal_forces_observer_survival.py --M 10 --body_size 1 --r 20,10,6,4,3,2.5
python toy_021_tidal_forces_observer_survival.py --M 1000 --body_size 1 --r 2000,1000,500,200,100

python toy_022_raychaudhuri_focusing.py
python toy_022_raychaudhuri_focusing.py --theta0 -0.1 --rho 0.01 --t 0,1,2,3,4,5
python toy_022_raychaudhuri_focusing.py --theta0 -0.1 --rho -0.01 --t 0,1,2,3,4,5

python toy_023_quantum_cutoff_proxy.py
python toy_023_quantum_cutoff_proxy.py --l_min 0.1 --r 10,6,4,3,2.5,2
python toy_023_quantum_cutoff_proxy.py --M 1 --l_min 1 --r 10,6,4,3,2
python toy_023_quantum_cutoff_proxy.py --M 1000 --l_min 1 --r 2000,1000,500,200,100

python toy_024_horizon_crossing_timescales.py
python toy_024_horizon_crossing_timescales.py --M 1 --r 10,6,4,3,2.5,2.1,2.01,2.001
python toy_024_horizon_crossing_timescales.py --M 1000 --r 2000,1000,500,200,100

python toy_025_redshift_vs_acceleration.py

python toy_026_equivalence_principle_breakdown_extended_bodies.py

python toy_027_null_raychaudhuri_nec.py

python toy_028_singularity_approach_timescales.py

python toy_029_kruskal_extension_horizon_regular.py

python toy_030_horizon_area_vs_mass_scaling.py

---

## Toys 031–040 — Determinism and Backreaction

python toy_031_global_hyperbolicity.py
python toy_032_mass_inflation.py
python toy_033_backreaction_proxy.py
python toy_034_self_force_proxy.py
python toy_035_linearized_breakdown.py
python toy_036_energy_conditions.py
python toy_037_uv_classicality.py
python toy_038_semiclassical_backreaction.py
python toy_039_averaging_backreaction.py
python toy_040_constraint_propagation.py

---

## Toys 041–050 — Verification and Cross-Checks

python toy_041_coordinate_invariance.py
python toy_042_numerical_stability_limits.py
python toy_043_foliation_time.py
python toy_044_finite_size_observer.py
python toy_045_constraint_drift.py
python toy_046_energy_comparator.py
python toy_047_observer_horizon.py
python toy_048_backreaction_threshold.py
python toy_049_broken_model.py
python toy_050_compare.py

---

## Toys 051–060 — Boundaries and Relational Physics

python toy_051_adm_initial_data_underdetermination.py
python toy_052_gauge_mode_growth_vs_physical_modes.py
python toy_053_anisotropic_stress_tov.py
python toy_054_imperfect_fluid_entropy.py
python toy_055_boxed_boundaries_scalar_schwarzschild.py
python toy_056_relational_radar_distance.py
python toy_057_gw_memory_extended_detector.py
python toy_058_thin_shell_israel_junction.py
python toy_059_shell_crossing_multistream.py
python toy_060_scalar_vs_gr_comparator.py

---

## Toys 061–064 — Thickened Failure Manifold

python toy_061_state_dependent_polyakov.py
python toy_062_stochastic_backreaction.py
python toy_063_bianchiI_anisotropy.py
python toy_064_inhomogeneous_shock.py
