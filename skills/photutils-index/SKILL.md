---
name: photutils-index
description: This skill should be used when users ask how to use photutils and the correct generated documentation skill must be selected before going deeper into source code.
---

# photutils Skills Index

## Route the request
- Classify the request into one of the generated topic skills listed below.
- Prefer workflow-level guidance first; drop to function-level inspection only when needed.

## Generated topic skills
- `photutils-getting-started`: Getting Started (initial setup, quickstarts, and core analysis workflows)
- `photutils-api-and-scripting`: API and Scripting (public APIs, script construction, symbol-level behavior)
- `photutils-build-and-install`: Build and Install (installation, optional dependencies, source/build validation)
- `photutils-inputs-and-modeling`: Inputs and Modeling (geometry overlap, PSF models, segmentation model controls)
- `photutils-parallel-hpc`: Parallel and HPC (batch throughput, multiprocessing orchestration, scaling checks)
- `photutils-developer-guide`: Developer Guide (contribution workflow, release execution, regression validation)
- `photutils-troubleshooting`: Troubleshooting (runtime failures, diagnostics, reproducibility checks)
- `photutils-whats-new`: Whats New (release migration and version-delta remediation)
- `photutils-advanced-topics`: Advanced Topics (changelog/datasets/index/isophote ancillary routing)

## Documentation-first inputs
- `docs`

## Tutorials and examples roots
- `docs/getting_started`
- `docs/user_guide`

## Test roots for behavior checks
- `photutils/tests`
- `photutils/aperture/tests`
- `photutils/background/tests`
- `photutils/centroids/tests`
- `photutils/datasets/tests`
- `photutils/detection/tests`
- `photutils/geometry/tests`
- `photutils/isophote/tests`
- `photutils/morphology/tests`
- `photutils/profiles/tests`
- `photutils/psf/tests`
- `photutils/psf_matching/tests`
- `photutils/segmentation/tests`
- `photutils/utils/tests`

## Escalate only when needed
- Start from topic skill primary references.
- If those references are insufficient, search the topic skill `references/doc_map.md`.
- If documentation still leaves ambiguity, open `references/source_map.md` in the same topic skill and inspect function-level source/test entry points.
- Use targeted symbol search while inspecting source (e.g., `rg -n "<symbol_or_keyword>" photutils`).

## Source directories for deeper inspection
- `photutils`
