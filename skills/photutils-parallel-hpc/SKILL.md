---
name: photutils-parallel-hpc
description: Use this skill for Photutils throughput and scaling work (batch simulations, multiprocessing orchestration, memory/performance tuning, and scheduler-ready pipelines). It clarifies what to parallelize around Photutils and how to validate numerical equivalence.
---

# photutils: Parallel and HPC

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` for compiler/environment setup issues.
- Route to `photutils-getting-started` for first-pass analysis workflow design.
- Route to `photutils-api-and-scripting` for symbol-level API behavior questions.
- Route to `photutils-whats-new` when scaling regressions appear after version upgrades.

### Triage questions
- Is the bottleneck CPU time, memory pressure, I/O throughput, or all three?
- Are you parallelizing many images, many catalogs, or parameter sweeps?
- Do runs need strict bitwise reproducibility across workers?
- Are optional dependencies (`scikit-image`, `tqdm`) available in worker environments?
- Is workload executed on local cores, Slurm, or another scheduler?

### Canonical workflow
1. Build a serial baseline script for one representative image (`docs/user_guide/segmentation.rst`, `docs/user_guide/psf.rst`).
2. Generate synthetic image batches with stable seeds (`docs/user_guide/datasets.rst`).
3. Parallelize at the job level (image/task batches), not inside single Photutils calls.
4. Keep worker payloads small and explicit (input array, config, seed).
5. Compare serial vs parallel outputs for label counts, fluxes, and fit flags.
6. Run focused tests for touched subsystems before scaling job size.

### Minimal working example
```bash
python - <<'PY'
import time
import numpy as np
from photutils.datasets import make_100gaussians_image
from photutils.segmentation import detect_threshold, detect_sources


def run_once(seed):
    rng = np.random.default_rng(seed)
    data = make_100gaussians_image() + rng.normal(0.0, 2.0, (300, 500))
    threshold = detect_threshold(data, 1.5)
    segm = detect_sources(data, threshold, npixels=10)
    return 0 if segm is None else int(segm.nlabels)


t0 = time.perf_counter()
counts = [run_once(seed) for seed in range(8)]
print('label_counts:', counts)
print('elapsed_s:', round(time.perf_counter() - t0, 3))
PY
```

```bash
pytest -q photutils/segmentation/tests/test_detect.py -k detect_sources
pytest -q photutils/psf/tests/test_photometry.py -k basic
```

### Pitfalls and fixes
- Photutils does not provide built-in MPI/OpenMP kernels for most workflows: parallelize outer loops (image batches, simulation runs).
- Mixing worker environments (missing optional deps) creates non-reproducible behavior: pin and verify package sets per worker.
- Deblending and detection thresholds are data-sensitive: compare outputs against a serial baseline before scaling.
- Large gridded PSF models can dominate memory: chunk workloads and profile resident memory.

### Convergence/validation checks
- Serial and parallel runs agree on source counts and key table columns within tolerance.
- Per-worker logs show identical dependency/runtime versions.
- Memory growth remains bounded as batch size increases.
- Regression tests for touched modules pass before scheduler submission.

## Scope
- Handle Photutils performance, batch execution, and simulation throughput strategy.
- Focus on practical runbooks for reliable scaling, not low-level distributed runtime internals.

## Primary documentation references
- `docs/user_guide/datasets.rst`
- `docs/user_guide/segmentation.rst`
- `docs/user_guide/psf.rst`
- `docs/user_guide/background.rst`
- `docs/whats_new/2.3.rst`
- `docs/whats_new/1.5.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use `references/source_map.md` for function-level source and test entry points.
- Validate with targeted `pytest -q <path> -k <keyword>` checks before scale-up.
- Cite exact documentation/source file paths in responses.

## Source entry points for unresolved issues
- `photutils/segmentation/detect.py`
- `photutils/segmentation/deblend.py`
- `photutils/segmentation/finder.py`
- `photutils/background/background_2d.py`
- `photutils/psf/photometry.py`
- `photutils/psf/iterative.py`
- `photutils/psf/gridded_models.py`
- `photutils/psf/simulation.py`
- `photutils/datasets/images.py`
- `photutils/datasets/noise.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
