# Toys Directory

This directory contains the executed diagnostic artifacts for the **GR Failure Manifold**.

## Contents

### Documentation
- **TOYS_LEGACY.md**  
  Legacy toy index from v1.1.5 with classifications and observed results.
  *Note: Toy descriptions have been completely rewritten for v1.1.6 and are now in `/docs/`*

- **COMMANDS.md**  
  Exact commands used to execute each toy and generate its JSON output.

- **TOY_PROTOCOL.md**  
  Formal protocol defining how each toy is constructed, what constraints it must satisfy, and how results are exported.

### Implementation & Results (Archives)

- **py.zip** (NEW in v1.1.6)  
  Archive containing all 90 Python source files (toy_001_*.py through toy_090_*.py).
  Each implements one computational experiment.

- **json.zip** (NEW in v1.1.6)  
  Archive containing all 90 JSON output files (toy_001_*.json through toy_090_*.json).
  Each JSON encodes parameters, observables, and detected failure signals for a single toy.

- **logs.zip** (NEW in v1.1.6)  
  Archive containing execution logs for all toys.

## What Changed in v1.1.6

**Previously (v1.1.5):**
- Single `Toys.zip` containing JSON outputs
- 85 toys total

**Now (v1.1.6):**
- Separate archives: `py.zip` (source), `json.zip` (outputs), `logs.zip` (execution logs)
- **90 toys total** (added toys 086-090)
- Complete redescription of all toys
- Comprehensive documentation in `/docs/` folder

## Toy Numbering

- Toys are numbered **001-090** (90 total)
- Toy 050 (cross-toy comparator) is declared but has limited execution
- All other toys have complete implementations and JSON outputs

## Why ZIP Archives?

The archives keep the repository lightweight while preserving machine-readable execution data. This project is diagnostic and archival, not a live simulation framework.

## Finding Toy Documentation

**Complete toy descriptions** are now in the `/docs/` folder:
- Navigate by phase: `/docs/toys/phase_01_foundations_and_baselines.md` (etc.)
- Sequential index: `/docs/indices/by_toy_number.md`
- Quick reference: `/docs/indices/quick_reference.md`
- Getting started: `/docs/guides/getting_started.md`

See `/docs/README.md` for full navigation.

---

**For the legacy toy index with failure classifications, see `TOYS_LEGACY.md` in this directory.**
