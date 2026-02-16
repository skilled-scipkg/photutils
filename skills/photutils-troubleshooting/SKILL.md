---
name: photutils-troubleshooting
description: Use this skill for Photutils runtime failures, incorrect measurements, migration regressions, and reproducibility issues. It provides a diagnostic playbook from environment capture to focused source and test inspection.
---

# photutils: Troubleshooting

## High-Signal Playbook
### Route conditions
- Route to `photutils-build-and-install` for dependency/toolchain install failures.
- Route to `photutils-whats-new` when errors appear only after version upgrades.
- Route to `photutils-api-and-scripting` for symbol-level API usage after root cause is found.
- Route to `photutils-parallel-hpc` for scaling throughput or scheduler issues.

### Triage questions
- What exact exception/warning is raised, and in which function?
- Which Photutils, Astropy, NumPy, and Python versions are running?
- Is failure data-specific (one image) or systematic across inputs?
- Are arrays unit-bearing, masked, or WCS-attached?
- Did behavior change after a dependency or Photutils version bump?

### Canonical workflow
1. Capture environment and versions.
2. Reduce to the smallest failing script with synthetic or minimal real data.
3. Reproduce failure with targeted tests (`pytest -q <path> -k <keyword>`).
4. Use `references/doc_map.md` for documented behavior and deprecations.
5. Use `references/source_map.md` for function-level source and test entry points.
6. Apply fix, then re-run minimal script and focused tests.

### Minimal working example
```bash
python - <<'PY'
import sys
import numpy as np
import photutils
from photutils.detection import DAOStarFinder

print('python:', sys.version.split()[0])
print('photutils:', photutils.__version__)

data = np.zeros((25, 25), dtype=float)
data[12, 12] = 100.0
finder = DAOStarFinder(threshold=5.0, fwhm=3.0)
print('n_sources:', len(finder(data)))
PY
```

```bash
pytest -q photutils/detection/tests/test_daofinder.py -k threshold
pytest -q photutils/segmentation/tests/test_detect.py -k mask
```

### Pitfalls and fixes
- Top-level imports from `photutils` may fail after migration: import from subpackages (`docs/getting_started/importing.rst`, `docs/whats_new/2.0.rst`).
- Detection thresholds with units must match data units (`docs/whats_new/1.13.rst`).
- Deblending instability often comes from inconsistent detect/deblend `npixels` and convolution settings (`docs/user_guide/segmentation.rst`).
- Missing optional dependencies disable features (e.g., region conversion or deblending paths): validate extras (`docs/getting_started/install.rst`).
- Isophote failures often trace to geometry initialization and sampling limits (`docs/user_guide/isophote_faq.rst`).

### Convergence/validation checks
- Failing script reproduces pre-fix and passes post-fix.
- Targeted tests for touched modules pass without new warnings.
- Output tables/units/flags are stable across repeated runs.
- Regression checks pass on at least one synthetic dataset and one real-like dataset.

## Scope
- Handle practical diagnosis and repair workflows for Photutils behavior issues.
- Prioritize reproducibility and minimal, test-backed fixes.

## Primary documentation references
- `docs/getting_started/importing.rst`
- `docs/getting_started/install.rst`
- `docs/user_guide/background.rst`
- `docs/user_guide/detection.rst`
- `docs/user_guide/segmentation.rst`
- `docs/user_guide/psf.rst`
- `docs/user_guide/isophote_faq.rst`
- `docs/whats_new/2.0.rst`
- `docs/whats_new/3.0.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use `references/source_map.md` to jump into implementation and matching tests.
- Validate with focused pytest invocations before and after any fix.
- Cite exact documentation/source paths in responses.

## Source entry points for unresolved issues
- `photutils/detection/daofinder.py`
- `photutils/detection/irafstarfinder.py`
- `photutils/segmentation/detect.py`
- `photutils/segmentation/deblend.py`
- `photutils/background/background_2d.py`
- `photutils/aperture/converters.py`
- `photutils/psf/photometry.py`
- `photutils/isophote/ellipse.py`
- `photutils/isophote/fitter.py`
- `photutils/utils/errors.py`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" photutils`).
