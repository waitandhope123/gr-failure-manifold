# GR Toy Model Protocol

## Objective

Build one General Relativity toy model per request that:

- produces numerical results derived from physics (not placeholders),
- is implemented in Python,
- exports results to a JSON file,
- uses a shared export schema so toys are directly comparable,
- is designed to probe limits, assumptions, and weak points of GR.

The goal is cataloging GR, not defending or embellishing it.

## General Rules

### 1. One toy per response
- Each response produces exactly one Python toy model.

### 2. Physics must be real
- Use known GR or controlled approximations (Newtonian, linearized, FLRW, etc.).
- Every numerical output must follow from equations.
- If a quantity is undefined in some regime, return null explicitly.

### 3. No symbolic-only toys
- All toys must output numerical values at sample points.

### 4. Units
- Default to geometric units: G = c = 1, unless explicitly stated otherwise.

## Required Toy Structure (Python)

Each toy must include:

### A. Explicit assumptions
- spacetime / metric or equivalent
- symmetry
- matter content
- coordinate or gauge choices
- domain of validity

### B. Core physics implementation
- equations defining the model
- curvature invariants or equivalent diagnostics
- physically interpretable quantities

### C. Experiment-style observables
Examples:
- clock rate comparisons
- redshift
- light travel times
- tidal forces
- causal / horizon diagnostics

## Mandatory JSON Export Schema

Every toy must export exactly these top-level keys:

{
  "toy_id": "string",
  "theory": "string",
  "spacetime": "string",
  "units": { "G": 1, "c": 1 },
  "parameters": {},
  "notes": {},
  "sample_points": [],
  "observables": {}
}

Each entry in sample_points must follow this structure:

{
  "coordinates": {},
  "curvature_invariants": {},
  "local_observables": {},
  "causal_structure": {}
}

- If a quantity is undefined, use null.
- Do NOT omit keys.

## Export Rules (Strict)

- JSON only
- One file per toy
- Output filename MUST match the Python filename

Example:
toy_002_newtonian.py  
toy_002_newtonian.json

- The Python script must automatically derive the JSON filename from __file__
- Deterministic output (no randomness unless requested)

## Allowed Toy Categories

- Exact GR solutions (Schwarzschild, Kerr, FLRW)
- Limits of GR (Newtonian, linearized gravity)
- Equivalence principle tests (Rindler vs gravity)
- Causality stress tests (horizons, CTCs)
- Energy localization diagnostics
- Simplified cosmological models

## What Counts as a “Weak Point”

A toy is valuable if it exposes:
- coordinate dependence vs invariants
- true vs removable singularities
- breakdown of approximations
- ambiguity in observables
- mismatches between limits (e.g., Newtonian vs GR)

## What the Assistant Must Not Do

- invent numerical values
- change the export schema
- output multiple toys at once
- output prose without code
- rely on external data unless explicitly asked

## Expected Output Per Request

1. Short explanation of what the toy probes
2. One complete Python script
3. Script writes a JSON file whose name matches the Python file

## How to Request the Next Toy

Examples:
- "Toy 002: Newtonian limit of gravity, same JSON export"
- "Toy 003: Linearized gravitational wave toy"
- "Toy 004: FLRW cosmology, redshift vs scale factor"
- "Toy 005: Rindler spacetime equivalence principle test"

## End Goal

After many toys, you should be able to:
- diff outputs across models,
- see where GR assumptions matter,
- identify incompleteness or ambiguity,
- separate physical effects from coordinate artifacts.
