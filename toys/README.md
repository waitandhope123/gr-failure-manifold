# Toys Directory

This directory contains the executed diagnostic artifacts for the
**GR Failure Manifold**.

## Contents

- **TOYS.md**  
  Canonical index of all toys, their classification, and observed results.
  This is the authoritative mapping of the failure manifold.

- **COMMANDS.md**  
  Exact commands used to execute each toy and generate its JSON output.

- **TOY_PROTOCOL.md**  
  Formal protocol defining how each toy is constructed, what constraints
  it must satisfy, and how results are exported.

- **PROCESS.md**  
  Documentation of the overall workflow used to build, validate, and
  curate the toy suite.

- **Toys.zip**  
  Archive containing all executed toy JSON files.
  Each JSON encodes parameters, observables, and detected failure signals
  for a single toy.

Toy numbering matches the index exactly.  
Toy 50 is intentionally absent (declared but not executed).

## Why a ZIP?

The ZIP is provided to keep the repository lightweight while preserving
machine-readable execution data. This project is diagnostic and archival,
not a live simulation framework.
